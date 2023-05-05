---
title: Integrar [!DNL Experience Manager] Recursos con Adobe InDesign Server
description: Aprenda a integrar [!DNL Experience Manager] Recursos con InDesign Server.
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 4%

---

# Integración de recursos con Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets utiliza:

* Un proxy para distribuir la carga de ciertas tareas de procesamiento. Un proxy es un [!DNL Experience Manager] instancia que se comunica con un trabajador proxy para realizar una tarea específica, y [!DNL Experience Manager] instancias para entregar los resultados.
* Trabajador de proxy para definir y administrar una tarea específica.

Pueden abarcar una amplia variedad de tareas; por ejemplo, usar un Adobe InDesign Server para procesar archivos.

Para cargar archivos por completo en [!DNL Experience Manager] Se utilizan los recursos que ha creado con Adobe InDesign y un proxy. Utiliza un trabajador proxy para comunicarse con Adobe InDesign Server, donde [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) se ejecutan para extraer metadatos y generar varias representaciones para [!DNL Experience Manager] Recursos. El trabajador proxy permite la comunicación bidireccional entre el InDesign Server y el [!DNL Experience Manager] instancias en una configuración de nube.

>[!NOTE]
>
>Adobe InDesign incluye dos productos:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Esto le permite diseñar diseños de página para impresión o distribución digital.
>
>* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Este motor le permite crear mediante programación documentos automatizados basados en lo que haya creado con el InDesign. Funciona como un servicio que ofrece una interfaz con su [ExtendScript](https://www.adobe.com/devnet/scripting.html) motor.\
   >  Las secuencias de comandos se escriben en ExtendScript de forma similar a JavaScript. Para obtener información sobre los scripts de Adobe InDesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## Cómo funciona la extracción {#how-the-extraction-works}

El InDesign Server se puede integrar con [!DNL Experience Manager] Recursos para que los archivos creados con InDesign ( `.indd`), se pueden cargar y generar representaciones, *all* medios extraídos (por ejemplo, vídeo) y almacenados como recursos:

>[!NOTE]
>
>Versiones anteriores de [!DNL Experience Manager] fueron capaces de extraer XMP y la miniatura, ahora se pueden extraer todos los medios.

1. Cargue su `.indd` a [!DNL Experience Manager] Recursos.
1. Un marco envía secuencias de comandos de comandos al InDesign Server mediante SOAP (Simple Object Access Protocol).

   Este script de comando:

   * Recupere el `.indd` archivo.
   * Ejecutar comandos de InDesign Server:

      * Se extraen la estructura, el texto y los archivos multimedia.
      * Se generan representaciones de PDF y JPG.
      * Se generan representaciones de HTML e IDML.
   * Volver a anunciar los archivos resultantes en [!DNL Experience Manager] Recursos.

   >[!NOTE]
   >
   >IDML es un formato basado en XML que se procesa *todo* en el archivo de InDesign. Se almacena como un paquete comprimido mediante [Zip](https://www.techterms.com/definition/zip) compresión.
   >
   >Consulte [Formatos de intercambio de Adobe InDesign INX e IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) para obtener más información.

   >[!CAUTION]
   >
   >Si el InDesign Server no está instalado o no está configurado, puede seguir cargando un `.indd` a [!DNL Experience Manager]. Sin embargo, las representaciones generadas se limitarán a `png` y `jpeg`, no podrá generar `html`, `idml` o las representaciones de página.

1. Después de la generación de extracción y representación:

   * La estructura se duplica en un `cq:Page` (tipo de representación).
   * El texto extraído y los archivos se almacenan en [!DNL Experience Manager] Recursos.
   * Todas las representaciones se almacenan en [!DNL Experience Manager] Recursos, en el propio recurso.

## Integración del InDesign Server con [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

Para integrar el InDesign Server de uso con [!DNL Experience Manager] Recursos y después de configurar el proxy, debe:

1. [Instalación del InDesign Server](#installing-the-indesign-server).
1. Si es necesario, [configure el [!DNL Experience Manager] Flujo de trabajo de recursos](#configuring-the-aem-assets-workflow).

   Esto solo es necesario si los valores predeterminados no son adecuados para su instancia.

1. Configure un [trabajador proxy para el InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Instalación del InDesign Server {#installing-the-indesign-server}

Para instalar e iniciar el InDesign Server para utilizarlo con [!DNL Experience Manager]:

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

### Configuración de la variable [!DNL Experience Manager] Flujo de trabajo de recursos {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] Assets tiene un flujo de trabajo preconfigurado **Recurso de actualización DAM**, que tiene varios pasos de proceso específicos para el InDesign:

* [Extracción de medios](#media-extraction)
* [Extracción de página](#page-extraction)

Este flujo de trabajo está configurado con valores predeterminados que pueden adaptarse para su configuración en las distintas instancias de creación (se trata de un flujo de trabajo estándar, por lo que puede obtener más información en [Edición de un flujo de trabajo](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Si está utilizando los valores predeterminados (incluido el puerto SOAP), no se necesita ninguna configuración.

Después de la configuración, cargue los archivos de InDesign en [!DNL Experience Manager] Los recursos (por cualquiera de los métodos habituales) almacenarán en déclencheur el flujo de trabajo necesario para procesar el recurso y preparar las distintas representaciones. Pruebe la configuración cargando un `.indd` a [!DNL Experience Manager] Recursos para confirmar que ve las diferentes representaciones creadas por ID en `<*your_asset*>.indd/Renditions`

#### Extracción de medios {#media-extraction}

Este paso controla la extracción de medios desde el `.indd` archivo.

Para personalizar, puede editar la pestaña **[!UICONTROL Argumentos]** del paso **[!UICONTROL Extracción de medios]**.

![Argumentos de extracción de medios y rutas de secuencias de comandos](assets/media_extraction_arguments_scripts.png)

Argumentos de extracción de medios y rutas de secuencias de comandos

* **Biblioteca ExtendScript**: Esta es una sencilla biblioteca de métodos http get/post , requerida por las otras secuencias de comandos.

* **Ampliar secuencias de comandos**: Aquí puede especificar diferentes combinaciones de scripts. Si desea ejecutar sus propias secuencias de comandos en el InDesign Server, guarde las secuencias de comandos en `/apps/settings/dam/indesign/scripts`.

   Para obtener información sobre los scripts de InDesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>No cambie la biblioteca ExtendScript. La biblioteca proporciona la funcionalidad HTTP necesaria para comunicarse con Sling. Esta configuración especifica la biblioteca que se enviará a Adobe InDesign Server para su uso allí.

La variable `ThumbnailExport.jsx` la secuencia de comandos ejecutada por el paso del flujo de trabajo Extracción de medios genera una representación en miniatura en formato de JPG. Esta representación la utiliza el paso del flujo de trabajo Procesar miniaturas para generar las representaciones estáticas requeridas por [!DNL Experience Manager].

Puede configurar el paso del flujo de trabajo Procesar miniaturas para generar representaciones estáticas de diferentes tamaños. Asegúrese de que no elimina los valores predeterminados, ya que los necesita el [!DNL Experience Manager] IU de recursos. Por último, el paso Eliminar representación de vista previa de imagen del flujo de trabajo elimina la representación de miniaturas .jpg, ya que ya no es necesaria.

#### Extracción de página {#page-extraction}

Esto crea un [!DNL Experience Manager] de los elementos extraídos. Un controlador de extracción se utiliza para extraer datos de una representación (actualmente HTML o IDML). Estos datos se utilizan para crear una página con PageBuilder.

Para personalizar, puede editar la pestaña **[!UICONTROL Argumentos]** del paso **Extracción de página**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Controlador de extracción de página**: En la lista desplegable, seleccione el controlador que desee utilizar. Un controlador de extracción funciona en una representación específica, elegida por un elemento relacionado `RenditionPicker` (consulte la API `ExtractionHandler`).
De forma predeterminada, el controlador de extracción de exportación IDML está disponible. Funciona en el `IDML` representación generada en el paso MediaExtract .

* **Nombre de la página**: Especifique el nombre que desea asignar a la página resultante. Si se deja en blanco, el nombre es &quot;página&quot; (o una derivada si ya existe &quot;página&quot;).

* **Título de página**: Especifique el título que desea asignar a la página resultante.

* **Ruta raíz de página**: Ruta a la ubicación raíz de la página resultante. Si se deja en blanco, se utiliza el nodo que contiene las representaciones del recurso.

* **Plantilla de página**: La plantilla que se utilizará al generar la página resultante.

* **Diseño de página**: El diseño de página que se utilizará al generar la página resultante.

### Configuración del trabajo del proxy para el InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>El trabajador reside en la instancia de proxy.

1. En la consola Herramientas , expanda **[!UICONTROL Configuraciones de Cloud Services]** en el panel izquierdo. A continuación, expanda **[!UICONTROL Configuración de proxy en la nube]**.

1. Haga doble clic en el programa de **[!UICONTROL IDS de trabajo]** para abrirlo y configurarlo.

1. Haga clic en **[!UICONTROL Editar]** para abrir el cuadro de diálogo de configuración y definir los ajustes necesarios:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Grupo de ID**: Los puntos de conexión SOAP que se utilizarán para la comunicación con el InDesign Server. Puede agregar, quitar y ordenar los elementos que sean necesarios.

1. Haga clic en **[!UICONTROL OK]** para guardar.

### Configuración del externalizador de vínculos de CQ de día {#configuring-day-cq-link-externalizer}

Si el InDesign Server y [!DNL Experience Manager] están en diferentes hosts o una o ambas aplicaciones no funcionan en puertos predeterminados, configure **Externalizador de vínculos de CQ de día** para establecer el nombre de host, el puerto y la ruta de contenido del InDesign Server.

1. Acceso al Administrador de configuración en la dirección URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Localizar la configuración **[!UICONTROL Externalizador de vínculos de CQ de día]**. Haga clic en **[!UICONTROL Editar]** para abrir.
1. La configuración del externalizador de vínculos ayuda a crear direcciones URL absolutas para [!DNL Experience Manager] implementación y para [!DNL InDesign Server]. Uso **[!UICONTROL Dominios]** para especificar el nombre de host y la ruta de contexto para la variable [!DNL Adobe InDesign Server]. Siga las instrucciones que aparecen en la pantalla. Haga clic en **[!UICONTROL Guardar]**.

   ![Vincular configuración del externalizador](assets/link-externalizer-config.png)

### Activación del procesamiento de trabajos en paralelo para InDesigns Server {#enabling-parallel-job-processing-for-indesign-server}

Ahora puede habilitar el procesamiento paralelo de trabajos para IDS.

En primer lugar, debe determinar el número máximo de trabajos paralelos ( `x`) un InDesign Server puede procesar:

* En una sola máquina multiprocesador, el número máximo de trabajos paralelos (x) que puede procesar un InDesign Server es inferior al número de procesadores que ejecutan IDS.
* Cuando ejecute IDS en varios equipos, deberá contar el número total de procesadores disponibles (es decir, en todos los equipos) y restar el número total de equipos.

Para configurar el número de trabajos de ID paralelos:

1. Abra el **[!UICONTROL Configuraciones]** ficha de la Consola Felix; por ejemplo:

   `http://localhost:4502/system/console/configMgr`

1. Seleccione la cola de procesamiento de IDS en:

   `Apache Sling Job Queue Configuration`

1. Establecer:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Trabajos paralelos máximos]** - `<*x*>` (tal como se ha calculado anteriormente)

1. Guarde estos cambios.
1. Para habilitar la compatibilidad con varias sesiones para Adobe CS6 y versiones posteriores, marque la casilla de verificación `enable.multisession.name` casilla de verificación en `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Cree un [grupo de &lt; `*x*>` Trabajadores de IDS añadiendo extremos SOAP a la configuración de IDS Worker](#configuring-the-proxy-worker-for-indesign-server).

   Si hay varios equipos que ejecutan InDesigns Server, añada extremos SOAP (número de procesadores por equipo -1) para cada equipo.

   >[!NOTE]
   >
   >Al trabajar con un grupo de trabajadores, puede habilitar la lista de bloqueados de los trabajadores de IDS.
   >
   >Para ello, active la casilla de verificación &quot;enable.retry.name&quot;, en la sección `com.day.cq.dam.ids.impl.IDSJobProcessor.name` , que habilita las recuperaciones de trabajos de IDS.
   >
   >Además, en la sección `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuración, establezca un valor positivo para `max.errors.to.blacklist` que determina el número de recuperaciones de trabajos antes de prohibir un ID en la lista de gestores de trabajos
   >
   >De forma predeterminada, después de la etiqueta configurable (`retry.interval.to.whitelist.name`) tiempo en minutos en que se vuelve a validar el programa de trabajo de IDS. Si el trabajador se encuentra en línea, se elimina de la lista de bloqueados.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Habilitación de la compatibilidad con el servidor Adobe InDesign 10.0 o posterior {#enabling-support-for-indesign-server-or-higher}

Para el servidor de InDesign 10.0 o superior, realice los siguientes pasos para habilitar la compatibilidad con varias sesiones.

1. Abra el Administrador de configuración desde su [!DNL Assets] instancia `https://[aem_server]:[port]/system/console/configMgr`.
1. Editar la configuración `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Select **[!UICONTROL ids.cc.enable]** y haga clic en **[!UICONTROL Guardar]**.

>[!NOTE]
>
>Para [!DNL InDesign Server] integración con [!DNL Assets], utilice un procesador multi-core porque la función de soporte de sesión necesaria para la integración no es compatible con sistemas de un solo núcleo.

## Configuración de las credenciales del Experience Manager {#configure-aem-credentials}

Puede cambiar las credenciales predeterminadas del administrador (nombre de usuario y contraseña) para acceder al servidor de InDesign desde su [!DNL Experience Manager] sin romper la integración con el servidor de Adobe InDesign.

1. Vaya a `/etc/cloudservices/proxy.html`.
1. En el cuadro de diálogo, especifique el nuevo nombre de usuario y contraseña.
1. Guarde las credenciales.
