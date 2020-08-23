---
title: Notas de la versión de AEM 6.4 Cumulative Fix Pack
description: Notas de la versión específicas de los paquetes de correcciones acumulativas de Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2158'
ht-degree: 21%

---


# Notas de la versión de AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Información de la versión {#release-information}

| Productos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versión | 6.4.8.1 |
| Tipo | Paquete de correcciones acumulativas |
| Fecha | 04 de junio de 2020 |
| Requisitos previos | [Paquete de servicio 8 de AEM 6.4 (6.4.8.0)](sp-release-notes.md) |
| Descargar URL | AEM 6.4.8.1 en distribución [de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## Novedades de AEM 6.4.8.1 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1 es una actualización importante que incluye varias correcciones internas y de cliente desde la disponibilidad general de AEM 6.4 Service Pack 8 (6.4.8.0) en marzo de 2020.

AEM Cumulative Fix Pack 6.4.8.1 depende de AEM 6.4 Service Pack 8. Por lo tanto, debe instalar el paquete AEM Cumulative Fix Pack 6.4.8.1 después de instalar AEM 6.4 Service Pack 8.

Algunos de los aspectos destacados de la AEM 6.4.8.1 son:

* Se ha eliminado la integración de Package Share con Adobe Experience Manager.
* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.21.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## Lista de cambios {#list-of-changes}

Adobe Experience Manager 6.4.8.1 proporciona correcciones a los siguientes problemas.

### Sites {#sites-6481}

* Cuando el nombre de un componente local de una LiveCopy es idéntico al nombre de un componente del modelo y el componente se despliega desde el plano, el término _msm_move no se agrega al nombre del componente local (NPR-33207).
* Los parámetros anexados a la solicitud original no se incluyen en la dirección URL de redireccionamiento (NPR-33174).
* Cuando la opción Coral.Select establece emptyOption=true o contiene un elemento predeterminado con valor = &quot;&quot;, el archivo dropdownshowhide.js encuentra un error: Error TypeError no capturado: component.getValue no es una función (NPR-33163).
* Cuando un componente incluye otro componente como recurso de suavizado de datos, el marcador de posición del componente de contenedor principal se reemplaza por el marcador de posición de componentes internos (NPR-33119).
* Cuando se basa un fragmento de contenido en un esquema y contiene un área de texto obligatoria o un campo de ruta, el fragmento de contenido no se guarda (NPR-33007)
* Cuando se crea un componente personalizado con el componente de fragmento de experiencia lista para usar y se utiliza en páginas de AEM Sites, AEM no muestra referencias (uso) para el componente personalizado (NPR-32852).
* Cuando una página de AEM Sites forma parte de un conjunto de contenido grande con varias Live Copy, la previsualización del historial de versiones de la página no se carga (NPR-32772).
* Cuando promociona un lanzamiento, agrega la combinación &quot;cq:LiveRelationship&quot; a todos los componentes agregados en el lanzamiento. Afecta a todos los lanzamientos independientemente de si se crea un lanzamiento con o sin seleccionar el —  Heredar datos activos de la página de origen —  (NPR-32664).
* Cuando se producen inicios de paginación, el selector de fragmentos de experiencia no carga todos los elementos (NPR-32605).
* No se puede crear un inicio para una página de AEM Sites. La creación de inicios produce un error (NPR-32544).
* Administrar publicación no incluye los recursos a los que se hace referencia en la solicitud de flujo de trabajo de activación (NPR-32463).
* La comprobación de estado del despachante muestra `Invalid cookie header` un mensaje de advertencia en los archivos de registro (NPR-33630).
* La integración de Salesforce es vulnerable al SSRF (NPR-32671).
* Se refleja XSS en PreferencesServlet (NPR-33439).

### Assets {#assets-6481}

* El recuento de recursos no cambia según el cambio en la selección en la Vista de Listas (NPR-33285).

* El botón siguiente no está activado al seleccionar el nodo principal (donde se puede ver una sola carpeta secundaria) y, a continuación, seleccionar la carpeta secundaria (NPR-33284).

* La IU táctil no se procesa (con error) para los usuarios que no tienen acceso de lectura en la raíz del repositorio, cuando el modo DMS7 o Híbrido está activado (NPR-33175).

* Los caracteres GB18030 que aparecen en los nombres de carpetas y recursos cambian a blanco en los archivos zip descargados (NPR-33150).

* La carpeta adicional se crea al recortar de forma inteligente un recurso que se encuentra dentro de una carpeta principal con caracteres de punto `.` en su nombre (NPR-32755).

* La carga diferida no se activa y no se muestran más de 100 recursos al seleccionar para revisar las tareas de la bandeja de entrada de notificaciones (NPR-32749).

* La página de vínculos para compartir la colección se ha interrumpido debido al cambio en coral-info (NPR-32510).

* Procesamiento de recursos mientras la carga masiva se queda atascada (CQ-4293916).

* Vulnerabilidad del SSRF en Experience Manager (NPR-33437).

### Plataforma {#platform-6481}

* No se llama al [!DNL Sling] filtro si la entrada del `sling:match` mapa se crea en `/etc/maps` (NPR-33308).
* Todos los agentes de vaciado se activan al desactivar una página (NPR-32941).
* Cuando se utiliza la `ScriptProcessor` API para minimizar una biblioteca JavaScript, el archivo de registro muestra un mensaje de error que indica que el código JavaScript no es compatible con el modo estricto. La API no proporciona una opción para habilitar o deshabilitar el modo estricto. (NPR-32746).
* Cuando una consulta SQL se ejecuta durante más tiempo, por ejemplo 7 horas, AEM deja de responder (NPR-33043).

### Interfaz de usuario {#ui-6481}

* Al buscar o examinar una ruta mediante un cuadro de diálogo de selección, el cuadro de diálogo de selección muestra todo el contenido del nodo JCR seleccionado en lugar de mostrar únicamente las imágenes (NPR-32712).

### Proyectos de traducción {#tranlation-6481}

* Se muestra un `NullPointerException` error en los registros de ejecución de un trabajo de traducción (NPR-32220).

### Integraciones {#integrations-6481}

* Secuencias de comandos entre sitios para JSON (NPR-32745).

### Communities {#communities-6481}

* Después de crear un nuevo grupo, los autores no se redirigen a la sección Grupo [!UICONTROL de] comunidad del [!DNL Internet Explorer] 11 (NPR-33202).
* Se produce un error al acceder a la página Flujo [!UICONTROL de] Actividad (NPR-33152).
* Editar un [!DNL Communities] grupo y cambiar la imagen en miniatura no actualiza la imagen en miniatura del grupo (NPR-32603).
* Al crear una versión de las notificaciones y suscripciones de contenido generado por el usuario (UGC), se almacena un ID incorrecto de la página de origen (CQ-4289703).
* Problema de secuencia de comandos entre sitios (NPR-33212).

### Flujo de trabajo {#workflow-6481}

* Algunos componentes no se muestran en el cuadro de diálogo que aparece cuando un usuario completa un flujo de trabajo que incluye un paso [!UICONTROL de participante en el] cuadro de diálogo (NPR-32989).

* La opción [!UICONTROL Línea de tiempo] del carril izquierdo tarda más tiempo en cargarse de lo esperado (NPR-32850).

### Forms {#forms-6481}

>[!NOTE]
>
>AEM paquete de correcciones acumulativas no incluye correcciones para AEM Forms. Estas se entregan mediante un paquete independiente de complementos de Forms. Asimismo, se ha publicado un instalador acumulativo que incluye correcciones para AEM Forms en JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Administración de correspondencia: Cuando un usuario pega contenido de un [!DNL Word] documento, el fragmento de documento de texto no conserva el formato (NPR-33213).
* Forms adaptable: Una nueva línea de una cadena en un diccionario de formularios adaptables agrega `&#xa;` caracteres al diccionario (NPR-33265).
* Forms adaptable: El usuario no puede guardar un formulario adaptable con más de un archivo adjunto (NPR-33214).
* Forms adaptable: `AddInstance` y `RemoveInstance` los métodos de la clase Instance Manager no agregan un número dinámico de instancias para fragmentos de carga diferida en [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptable: Analytics habilitado en un formulario adaptable incrustado en una [!DNL Sites] página no registra datos para eventos de envío y abandono (NPR-31359).
* Forms adaptable: Cuando un usuario pega el contenido de un [!DNL Word] documento en un formulario adaptable y lo envía, el formulario adaptable enviado incluye caracteres Unicode. Además, la conversión de PDF a PDF/A falla debido a caracteres Unicode (NPR-33348).
* BackendIntegration: Las solicitudes del modelo de datos de formulario fallan al caducar el token de actualización debido a un estado inactivo incorrecto (NPR-33168).
* Servicios de documento: El servicio de conversión de PDF no puede convertir documentos PDF a PostScript debido a que faltan tarros Gibson para [!DNL WebLogic] el servidor [!DNL Linux] (NPR-33515, CQ-4292239).
* Servicios de documento: Cuando un usuario convierte un archivo de texto a un PDF, los caracteres japoneses no se representan correctamente (NPR-33239).
* XSS almacenado con GuideSOMProviderServlet (NPR-32701).


## Install 6.4.8.1 {#install}

### Requisitos de configuración {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para clientes con Feature Packs instalados en AEM 6.4. Los paquetes de funciones opcionales proporcionados por Adobe dependen de la versión de lanzamiento y de los Service Packs. Si tiene instalado algún Feature Pack, póngase en contacto con el equipo AEM de atención al cliente para validar la compatibilidad de dichos paquetes de funciones con este paquete de correcciones acumulativas para AEM 6.4.

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* En una implementación con MongoDB y varias instancias, instale AEM 6.4.8.1 en una de las instancias de creación mediante el Administrador de paquetes.
* Antes de instalar el paquete de correcciones acumulativas, asegúrese de tener una instantánea o una copia de seguridad nueva de la instancia de AEM.
* Reinicie la instancia antes de la instalación. Aunque esto solo es necesario cuando la instancia sigue en modo de actualización (y este es el caso cuando la instancia se acaba de actualizar desde una versión anterior), generalmente se recomienda si la instancia se ejecutó durante un período de tiempo más largo.

>[!NOTE]
>
>Adobe no recomienda quitar o desinstalar el paquete AEM 6.4.8.1.

### Instalación del paquete de correcciones acumulativas {#install-cumulative-fix-pack}

Siga estos pasos para instalar el paquete de correcciones acumulativas en una instancia de AEM 6.4.8.0 existente:

1. Haga clic en el vínculo [Distribución](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) de software para descargar el paquete.

1. Abra el Administrador [de paquetes](http://localhost:4502/crx/packmgr/index.jsp) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.

1. Seleccione el nombre del paquete y haga clic en **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**El cuadro de diálogo en la IU del administrador de paquetes a veces se cierra de forma precipitada durante la instalación de 6.4.8.1**
>
>Por lo tanto, se recomienda esperar a que los registros de errores se estabilicen antes de acceder a la instancia. El usuario tiene que esperar a que se produzcan registros específicos relacionados con la desinstalación del paquete de actualización antes de asegurarse de que la instalación se realiza correctamente. Suele suceder en Safari, pero puede suceder de forma intermitente en cualquier navegador.

### Instalación automática {#auto-installation}

Existen dos formas de instalar automáticamente AEM 6.4.8.1 en una instancia en ejecución:

A. Coloque el paquete en ..Carpeta */crx-quickstart/install* mientras se ejecuta el servidor. El paquete se instala automáticamente.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.1 no admite la instalación de Bootstrap.

### Validar la instalación {#validate-install}

1. La página Información del producto (*/system/console/productinfo*) ahora debe mostrar la cadena de versión actualizada &quot;Adobe Experience Manager, versión 6.4.8.1&quot; en Productos instalados.
1. Todos los paquetes OSGI tienen el valor ACTIVO o FRAGMENTO en la consola OSGI (utilice la consola web:/system/console/bundles).
1. El paquete OSGI org.apache.jackrabbit.oak-core está en la versión 1.8.17 o superior (utilice la consola web: /system/console/buncles).

Para determinar la plataforma certificada para la ejecución con esta versión de AEM Sites y Assets, consulte Requisitos [técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Actualización de visores de Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.1 contiene una nueva versión de visores de Dynamic Media (5.10.1) que permite comprobar los nombres de duplicados en la página Ajustes preestablecidos de imagen. Se aconseja a los clientes de Dynamic Media que ejecuten el siguiente comando para actualizar los ajustes preestablecidos del visor del equipo.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará los nuevos ajustes preestablecidos de visor en la ubicación /conf.

### Instalación del paquete de complementos para AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms. Las correcciones en AEM Forms se entregan mediante un paquete de complementos independiente.

1. Asegúrese de que ha instalado el AEM paquete de correcciones acumulativas.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms en JEE. Las correcciones en el instalador JEE de AEM Forms se entregan mediante un instalador independiente.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0016](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Funciones eliminadas u obsoletas {#removed-deprecated-features}

Esta sección enumera las funciones y capacidades que se han eliminado o dejado de utilizar en AEM 6.4.

| Área | Función | Reemplazo | Versión |
|---|---|---|---|
| Assets | Administrar acción de etiqueta para subrecursos | Sin reemplazo | AEM 6.4.2.0   |
| Integración de Assets y Adobe Creative Cloud | [En la AEM 6.2 se introdujo la AEM al uso compartido](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) de carpetas de Creative Cloud como forma de dar acceso a los usuarios creativos a los recursos de AEM. Adobe Asset Link, la nueva capacidad de la aplicación Creative Cloud, proporciona experiencia de usuario mejorada y un acceso más eficaz a los recursos de AEM directamente desde Photoshop, InDesign e Illustrator. Adobe no realizará más mejoras en la funcionalidad de uso compartido de carpetas. Aunque la función está incluida en AEM, se recomienda encarecidamente a los clientes que utilicen la sustitución. | Vínculo de recurso de Adobe o aplicación de escritorio. Para obtener más información, consulte el artículo sobre la [integración de AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0   |

## Problemas conocidos {#known-issues}

* Durante la instalación de AEM 6.4.8.1, la actualización de la [!DNL Chrome] versión 83 está causando problemas al compilar los paquetes. Use otros exploradores disponibles, como [!DNL Internet Explorer] y [!DNL Firefox], u otras opciones de instalación de paquetes estándar AEM para resolver el problema. El problema se resuelve después de instalar AEM 6.4.8.1.

* No se puede enviar un correo electrónico al servidor SMTP remoto mediante el remitente de correo predeterminado AEM, ya que solo permite la comunicación mediante TLS v1.2. Quite el paquete `javax.mail:mail:1.5.0-b01` de `system/console` y actualice los paquetes para resolver el problema.

Para obtener información sobre los problemas conocidos de AEM 6.4.8.0 Service Pack, consulte [AEM Notas](sp-release-notes.md)de la versión de Service Pack 6.4.8.0.

## Paquetes de contenido y paquetes OSGi incluidos {#osgi-bundles-and-content-packages-included}

Los siguientes documentos de texto enumeran los paquetes OSGi y los paquetes de contenido incluidos en AEM 6.4.8.1.

Lista de paquetes OSGi incluidos en AEM 6.4.8.1

[Obtener archivo](assets/6.4.8.1_osgi_bundles.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.8.1

[Obtener archivo](assets/6.4.8.1_content_packages.txt)

## Recursos útiles {#helpful-resources}

* [Notas de la versión de AEM 6.4](../release-notes/release-notes.md)
* [Página de productos AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentación de AEM 6.4](https://helpx.adobe.com/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Sitios restringidos {#restricted-sites-new}

Estos sitios solo están disponibles para los clientes. Si es un cliente y requiere acceso, póngase en contacto con su administrador de cuentas de Adobe.

* [Descarga de productos en licensing.adobe.com](https://licensing.adobe.com/)
* [Póngase en contacto con atención al cliente](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
