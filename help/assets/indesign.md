---
title: Integración de AEM Assets con Adobe InDesign Server
description: Aprenda a integrar AEM Assets con InDesign Server.
contentOwner: AG
feature: Publicación
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 4%

---

# Integración de AEM Assets con Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets utiliza:

* Un proxy para distribuir la carga de ciertas tareas de procesamiento. Un proxy es una instancia de AEM que se comunica con un trabajador proxy para realizar una tarea específica y otras instancias de AEM para ofrecer los resultados.
* Trabajador de proxy para definir y administrar una tarea específica.

Pueden abarcar una amplia variedad de tareas; por ejemplo, usar un Adobe InDesign Server para procesar archivos.

Para cargar por completo archivos en AEM Assets que haya creado con Adobe InDesign, se utiliza un proxy. Esto utiliza un trabajador proxy para comunicarse con Adobe InDesign Server, donde [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) se ejecutan para extraer metadatos y generar varias representaciones para AEM Assets. El programa de trabajo del proxy habilita la comunicación bidireccional entre el InDesign Server y las instancias de AEM en una configuración de nube.

>[!NOTE]
>
>Adobe InDesign incluye dos productos:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Esto le permite diseñar diseños de página para impresión o distribución digital.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Este motor le permite crear mediante programación documentos automatizados basados en lo que haya creado con el InDesign. Funciona como un servicio que ofrece una interfaz con su motor [ExtendScript](https://www.adobe.com/devnet/scripting.html).\
   >  Las secuencias de comandos se escriben en ExtendScript, que es similar a javascript. Para obtener información sobre los scripts de Indesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>



## Cómo funciona la extracción {#how-the-extraction-works}

El InDesign Server se puede integrar con AEM Assets para que los archivos creados con el InDesign ( `.indd`) se puedan cargar, generar representaciones, *todos los medios* extraídos (por ejemplo, vídeo) y almacenarse como recursos:

>[!NOTE]
>
>Las versiones anteriores de AEM fueron capaces de extraer XMP y la miniatura, ahora todos los medios se pueden extraer.

1. Cargue el archivo `.indd` en AEM Assets.
1. Un marco envía secuencias de comandos de comandos al InDesign Server mediante SOAP (Simple Object Access Protocol).

   Este script de comando:

   * Recupere el archivo `.indd`.
   * Ejecutar comandos de InDesign Server:

      * Se extraen la estructura, el texto y los archivos multimedia.
      * Se generan representaciones de PDF y JPG.
      * Se generan representaciones HTML e IDML.
   * Vuelva a publicar los archivos resultantes en AEM Assets.

   >[!NOTE]
   >
   >IDML es un formato basado en XML que representa *todo* en el archivo de InDesign. Se almacena como un paquete comprimido usando la compresión [Zip](https://www.techterms.com/definition/zip).
   >
   >Consulte [Formatos de intercambio de Adobe InDesign INX e IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) para obtener más información.

   >[!CAUTION]
   >
   >Si el InDesign Server no está instalado o no está configurado, puede cargar un archivo `.indd` en AEM. Sin embargo, las representaciones generadas se limitarán a `png` y `jpeg`, no podrá generar `html`, `idml` ni las representaciones de página.

1. Después de la generación de extracción y representación:

   * La estructura se replica en `cq:Page` (tipo de representación).
   * El texto extraído y los archivos se almacenan en AEM Assets.
   * Todas las representaciones se almacenan en AEM Assets, en el propio recurso.

## Integración del InDesign Server con AEM {#integrating-the-indesign-server-with-aem}

Para integrar el InDesign Server para usar con AEM Assets y después de configurar el proxy, debe:

1. [Instale el InDesign Server](#installing-the-indesign-server).
1. Si es necesario, [configure el flujo de trabajo de AEM Assets](#configuring-the-aem-assets-workflow).

   Esto solo es necesario si los valores predeterminados no son adecuados para su instancia.

1. Configure un [trabajador proxy para el InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Instalación del InDesign Server {#installing-the-indesign-server}

Para instalar e iniciar el InDesign Server para utilizarlo con AEM:

1. Descargue e instale Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 y posterior).

1. Si es necesario, puede personalizar la configuración de la instancia de InDesign Server.

1. Desde la línea de comandos, inicie el servidor:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Esto iniciará el servidor con el complemento SOAP escuchando en el puerto 8080. Todos los mensajes de registro y los resultados se escriben directamente en la ventana de comandos.

   >[!NOTE]
   >
   >Si desea guardar los mensajes de salida en un archivo, utilice la redirección; por ejemplo, en Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configuración del flujo de trabajo de AEM Assets {#configuring-the-aem-assets-workflow}

AEM Assets tiene un flujo de trabajo preconfigurado **DAM Update Asset**, que tiene varios pasos de proceso específicos para el InDesign:

* [Extracción de medios](#media-extraction)
* [Extracción de páginas](#page-extraction)

Este flujo de trabajo está configurado con valores predeterminados que se pueden adaptar para su configuración en las distintas instancias de autor (se trata de un flujo de trabajo estándar, por lo que hay más información disponible en [Edición de un flujo de trabajo](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Si está utilizando los valores predeterminados (incluido el puerto SOAP), no se necesita ninguna configuración.

Tras la configuración, la carga de archivos de InDesign en AEM Assets (mediante cualquiera de los métodos habituales) almacenará en déclencheur el flujo de trabajo necesario para procesar el recurso y preparar las distintas representaciones. Pruebe la configuración cargando un archivo `.indd` en AEM Assets para confirmar que ve las diferentes representaciones creadas por ID en `<*your_asset*>.indd/Renditions`

#### Extracción de medios {#media-extraction}

Este paso controla la extracción de medios desde el archivo `.indd`.

Para personalizar, puede editar la pestaña **[!UICONTROL Argumentos]** del paso **[!UICONTROL Extracción de medios]**.

![Argumentos de extracción de medios y rutas de secuencias de comandos](assets/media_extraction_arguments_scripts.png)

Argumentos de extracción de medios y rutas de secuencias de comandos

* **Biblioteca** de ExtendScript: Esta es una sencilla biblioteca de métodos http get/post , requerida por las otras secuencias de comandos.

* **Ampliar secuencias de comandos**: Aquí puede especificar diferentes combinaciones de scripts. Si desea que sus propios scripts se ejecuten en el InDesign Server, guarde los scripts en `/apps/settings/dam/indesign/scripts`.

   Para obtener información sobre los scripts de InDesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>No cambie la biblioteca ExtendScript. La biblioteca proporciona la funcionalidad HTTP necesaria para comunicarse con Sling. Esta configuración especifica la biblioteca que se enviará a Adobe InDesign Server para su uso allí.

El script `ThumbnailExport.jsx` ejecutado por el paso del flujo de trabajo de extracción de medios genera una representación en miniatura en formato JPG. Esta representación la utiliza el paso del flujo de trabajo Procesar miniaturas para generar las representaciones estáticas necesarias para AEM.

Puede configurar el paso del flujo de trabajo Procesar miniaturas para generar representaciones estáticas de diferentes tamaños. Asegúrese de no eliminar los valores predeterminados, ya que son necesarios para la interfaz de usuario de AEM Assets. Por último, el paso Eliminar representación de vista previa de imagen del flujo de trabajo elimina la representación de miniaturas .jpg, ya que ya no es necesaria.

#### Extracción de páginas {#page-extraction}

Esto crea una página AEM a partir de los elementos extraídos. Un controlador de extracción se utiliza para extraer datos de una representación (actualmente HTML o IDML). Estos datos se utilizan para crear una página con PageBuilder.

Para personalizar, puede editar la pestaña **[!UICONTROL Argumentos]** del paso **Extracción de página**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Controlador de extracción de página**: En la lista desplegable, seleccione el controlador que desee utilizar. Un controlador de extracción funciona en una representación específica, elegida por un elemento relacionado `RenditionPicker` (consulte la API `ExtractionHandler`).
De forma predeterminada, el controlador de extracción de exportación IDML está disponible. Funciona en la representación `IDML` generada en el paso MediaExtract.

* **Nombre** de página: Especifique el nombre que desea asignar a la página resultante. Si se deja en blanco, el nombre es &quot;página&quot; (o una derivada si ya existe &quot;página&quot;).

* **Título** de página: Especifique el título que desea asignar a la página resultante.

* **Ruta** raíz de página: Ruta a la ubicación raíz de la página resultante. Si se deja en blanco, se utiliza el nodo que contiene las representaciones del recurso.

* **Plantilla** de página: La plantilla que se utilizará al generar la página resultante.

* **Diseño** de página: El diseño de página que se utilizará al generar la página resultante.

### Configuración del trabajo del proxy para el InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>El trabajador reside en la instancia de proxy.

1. En la consola Herramientas, expanda **[!UICONTROL Configuraciones de Cloud Services]** en el panel izquierdo. A continuación, expanda **[!UICONTROL Cloud Proxy Configuration]**.

1. Haga doble clic en el programa de **[!UICONTROL IDS de trabajo]** para abrirlo y configurarlo.

1. Haga clic en **[!UICONTROL Editar]** para abrir el cuadro de diálogo de configuración y definir la configuración necesaria:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Grupo de ID**: Los puntos de conexión SOAP que se utilizarán para la comunicación con el InDesign Server. Puede agregar, quitar y ordenar los elementos que sean necesarios.

1. Haga clic en **[!UICONTROL Aceptar]** para guardar.

### Configuración del externalizador de vínculos de CQ de día {#configuring-day-cq-link-externalizer}

Si el InDesign Server y las AEM están en diferentes hosts o si una o ambas aplicaciones no funcionan en puertos predeterminados, configure **Day CQ Link Externalizer** para establecer el nombre de host, el puerto y la ruta de contenido para el InDesign Server.

1. Acceda al Administrador de configuración en la dirección URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Busque la configuración **[!UICONTROL Day CQ Link Externalizer]**. Haga clic en **[!UICONTROL Editar]** para abrirlo.
1. La configuración del externalizador de vínculos ayuda a crear direcciones URL absolutas para la implementación [!DNL Experience Manager] y para [!DNL InDesign Server]. Utilice el campo **[!UICONTROL Domains]** para especificar el nombre de host y la ruta de contexto para [!DNL Adobe InDesign Server]. Siga las instrucciones que aparecen en la pantalla. Haga clic en **[!UICONTROL Guardar]**.

   ![Vincular configuración del externalizador](assets/link-externalizer-config.png)

### Activación del procesamiento de trabajos en paralelo para InDesigns Server {#enabling-parallel-job-processing-for-indesign-server}

Ahora puede habilitar el procesamiento paralelo de trabajos para IDS.

En primer lugar, debe determinar el número máximo de trabajos paralelos ( `x`) que un InDesign Server puede procesar:

* En una sola máquina multiprocesador, el número máximo de trabajos paralelos (x) que puede procesar un InDesign Server es inferior al número de procesadores que ejecutan IDS.
* Cuando ejecute IDS en varios equipos, deberá contar el número total de procesadores disponibles (es decir, en todos los equipos) y restar el número total de equipos.

Para configurar el número de trabajos de ID paralelos:

1. Abra la pestaña **[!UICONTROL Configurations]** de la Consola Felix; por ejemplo:

   `http://localhost:4502/system/console/configMgr`

1. Seleccione la cola de procesamiento de IDS en:

   `Apache Sling Job Queue Configuration`

1. Configurar:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Máximo de trabajos paralelos]** :  `<*x*>` (según se ha calculado anteriormente)

1. Guarde estos cambios.
1. Para habilitar la compatibilidad con varias sesiones para Adobe CS6 y versiones posteriores, marque la casilla `enable.multisession.name` en `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Cree un [grupo de &lt; `*x*>` trabajadores de IDS añadiendo extremos SOAP a la configuración de IDS Worker](#configuring-the-proxy-worker-for-indesign-server).

   Si hay varios equipos que ejecutan InDesigns Server, añada extremos SOAP (número de procesadores por máquina -1) para cada equipo.

   >[!NOTE]
   >
   >Al trabajar con un grupo de trabajadores, puede habilitar la lista de bloqueados de los trabajadores de IDS.
   >
   >Para ello, active la casilla &quot;enable.retry.name&quot;, en la configuración `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, que habilita las recuperaciones de trabajos de IDS.
   >
   >Además, en la configuración `com.day.cq.dam.ids.impl.IDSPoolImpl.name`, establezca un valor positivo para el parámetro `max.errors.to.blacklist` que determina el número de recuperaciones de trabajos antes de prohibir un ID en la lista de gestores de trabajos
   >
   >De forma predeterminada, después del tiempo configurable (`retry.interval.to.whitelist.name`) en minutos, el programa de trabajo de IDS se vuelve a validar. Si el trabajador se encuentra en línea, se elimina de la lista de bloqueados.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Habilitación de la compatibilidad con el servidor Adobe InDesign 10.0 o posterior {#enabling-support-for-indesign-server-or-higher}

Para el servidor de InDesign 10.0 o superior, realice los siguientes pasos para habilitar la compatibilidad con varias sesiones.

1. Abra el Administrador de configuración desde la instancia [!DNL Assets] `https://[aem_server]:[port]/system/console/configMgr`.
1. Edite la configuración `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Seleccione la opción **[!UICONTROL ids.cc.enable]** y haga clic en **[!UICONTROL Guardar]**.

>[!NOTE]
>
>Para la integración [!DNL InDesign Server] con [!DNL Assets], utilice un procesador de varios núcleos porque la función de soporte de sesión necesaria para la integración no es compatible con sistemas de un solo núcleo.

## Configuración de las credenciales del Experience Manager {#configure-aem-credentials}

Puede cambiar las credenciales de administrador predeterminadas (nombre de usuario y contraseña) para acceder al servidor de InDesign desde la instancia de AEM sin interrumpir la integración con el servidor de Adobe InDesign.

1. Ir a `/etc/cloudservices/proxy.html`.
1. En el cuadro de diálogo, especifique el nuevo nombre de usuario y contraseña.
1. Guarde las credenciales.
