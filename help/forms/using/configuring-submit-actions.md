---
title: Configuración de la acción Enviar
seo-title: Configuring the Submit action
description: AEM Forms permite configurar una acción de envío para definir cómo se procesa un formulario adaptable después del envío. Puede utilizar acciones de envío integradas o escribir las suyas propias desde cero.
seo-description: AEM Forms allows you to configure a submit action to define how an adaptive form is processed after submission. You can use built-in submit actions or write your own from scratch.
uuid: aa261e65-a1ec-402b-80de-0ba8a294e315
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: fea76f90-22d5-4836-9901-a35229401eb0
feature: Adaptive Forms
exl-id: 2a842bdc-6dcf-42cc-9a45-57ac15b79eb7
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 37%

---

# Configuración de la acción Enviar {#configuring-the-submit-action}

## Introducción al envío de acciones {#introduction-to-submit-actions}

Una acción de envío se activa cuando un usuario hace clic en el botón Enviar de un formulario adaptable. Puede configurar la acción de envío en el formulario adaptable. Los formularios adaptables proporcionan algunas acciones de envío listas para usar. Puede copiar y ampliar las acciones de envío predeterminadas para crear su propia acción de envío. Sin embargo, según sus necesidades, puede escribir y registrar su propia acción de envío para procesar los datos en el formulario enviado.

Cuando un formulario se rellena previamente o se envía, los datos enviados se redirigen a través de AEM para el tratamiento de datos en formatos intermedios. Los datos no se guardan en una instancia de AEM, excepto cuando el formulario adaptable utiliza Acrobat Sign, verifica, el borrador o el envío del portal de formularios o AEM Flujos de trabajo

Puede configurar una acción de envío en la variable **[!UICONTROL Envío]** de las propiedades del contenedor del formulario adaptable, en la barra lateral.

![Configurar acción de envío](assets/thank-you-setting.png)
**Figura:** *Configurar acción de envío*

Las acciones de envío predeterminadas disponibles con los formularios adaptables son:

* Enviar al punto final REST
* Enviar correo electrónico
* Enviar PDF por correo electrónico
* Invocar un Forms Workflow
* Enviar mediante modelo de datos de formulario
* Acción de envío de portal de formularios
* Invocar un flujo de trabajo de AEM

>[!NOTE]
>
>La acción Enviar PDF por correo electrónico solo se aplica a los formularios adaptables que utilizan plantilla XFA como modelo de formulario.

>[!NOTE]
>
>Asegúrese de que la variable [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder exists. El directorio es necesario para almacenar los archivos adjuntos temporalmente. Si el directorio no existe, créelo.

>[!CAUTION]
>
>Si [prefill](/help/forms/using/prepopulate-adaptive-form-fields.md) una plantilla de formulario, un modelo de datos de formulario o un formulario adaptable basado en esquemas con datos XML o JSON reclamados a un esquema (esquema XML, esquema JSON, plantilla de formulario o modelo de datos de formulario) que sea datos que no contenga &lt;afdata>, &lt;afbounddata>y &lt;/afunbounddata> etiquetas, los datos de los campos no enlazados (los campos no enlazados son campos de formulario adaptables sin [bindref](/help/forms/using/prepopulate-adaptive-form-fields.md) ) del formulario adaptable se pierde.

Puede escribir una acción de envío personalizada para formularios adaptables para que cumplan con su caso de uso. Para obtener más información, consulte [Escritura de una acción de envío personalizada para formularios adaptables](/help/forms/using/custom-submit-action-form.md).

## Enviar al punto final REST {#submit-to-rest-endpoint}

La variable **[!UICONTROL Enviar al extremo REST]** la opción enviar pasa los datos rellenados en el formulario a una página de confirmación configurada como parte de la solicitud de GET HTTP. Puede agregar el nombre de los campos que desea solicitar. El formato de la solicitud es el siguiente:

`{fieldName}={request parameter name}`

Como se muestra en la siguiente imagen, `param1` y `param2` se pasan como parámetros con valores copiados de los campos **[!UICONTROL cuadro de texto]** y **[!UICONTROL del cuadro numérico]** para la siguiente acción.

También puede **[!UICONTROL Habilitar la petición POST]** y proporcionar una URL para publicar la solicitud. Para enviar datos al servidor de AEM que aloja el formulario, utilice una ruta relativa correspondiente a la ruta raíz del servidor de AEM. Por ejemplo, /content/forms/af/SampleForm.html. Para enviar datos a cualquier otro servidor, utilice la ruta absoluta.

![Configurar la acción de envío del punto final de REST.](assets/action-config.png)

Configurar la acción de envío del punto final de REST.

>[!NOTE]
Para pasar los campos como parámetros en una URL REST, todos los campos deben tener nombres de elementos diferentes, incluso si se colocan en paneles diferentes.

### Publicar datos enviados en un recurso o punto final de reposo externo  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Utilice la acción **[!UICONTROL Enviar al punto final REST]** para publicar los datos enviados en una URL de REST. La URL puede ser de un servidor interno (el servidor en el que se procesa el formulario) o externo.

Para enviar datos a un servidor interno, proporcione la ruta del recurso. Los datos se publican en la ruta del recurso. Por ejemplo, /content/restEndPoint. Para esas peticiones POST se utiliza la información de autenticación de la solicitud de envío.

Para enviar datos a un servidor externo, proporcione una URL. El formato de la URL es https:// host:port/path_to_rest_end_point. Asegúrese de configurar la ruta para controlar la petición POST de forma anónima.

![Asignación de valores de campo pasados como parámetros de la página de agradecimiento](assets/post-enabled-actionconfig.png)

En el ejemplo anterior, el usuario ha escrito información en `textbox` y se captura mediante el parámetro `param1`. La sintaxis para anunciar datos capturados con `param1` es la siguiente:

`String data=request.getParameter("param1");`

Del mismo modo, los parámetros que se utilizan para publicar datos XML y archivos adjuntos son `dataXml` y `attachments`.

Por ejemplo, utiliza estos dos parámetros en el script para analizar los datos en un punto final de REST. Se utiliza la siguiente sintaxis para almacenar y analizar los datos:

`String data=request.getParameter("dataXml");`\
`String att=request.getParameter("attachments");`

En este ejemplo, `data` almacena los datos XML y `att` almacena datos adjuntos.

## Enviar correo electrónico {#send-email}

La variable **[!UICONTROL Enviar correo electrónico]** la acción submit envía un correo electrónico a uno o varios destinatarios cuando el formulario se envía correctamente. El correo electrónico generado puede contener datos de formulario en un formato predefinido.

>[!NOTE]
Todos los campos del formulario deben tener nombres de elemento diferentes, incluso si se colocan en paneles diferentes), para incluir los datos del formulario en un mensaje de correo electrónico.

## Enviar PDF por correo electrónico {#send-pdf-via-email}

La variable **[!UICONTROL Enviar PDF por correo electrónico]** la acción submit envía un mensaje de correo electrónico con un PDF que contiene datos del formulario a uno o varios destinatarios cuando el formulario se envía correctamente.

**Nota:** *Esta acción de envío está disponible para formularios adaptables basados en XFA y formularios de adaptación basados en XSD que tienen la plantilla Documento de registro.*

## Invocar un flujo de trabajo de formularios {#invoke-a-forms-workflow}

La variable **[!UICONTROL Enviar al flujo de trabajo de Forms]** la opción submit envía un xml de datos y archivos adjuntos (si los hay) a un LiveCycle de Adobe existente o a AEM Forms en un proceso JEE.

Para obtener información sobre cómo configurar la acción Enviar a envío de flujo de trabajo de formularios, consulte [Envío y procesamiento de los datos del formulario mediante flujos de trabajo de formulario](/help/forms/using/submit-form-data-livecycle-process.md).

## Enviar mediante modelo de datos de formulario {#submit-using-form-data-model}

La variable **[!UICONTROL Enviar mediante el modelo de datos de formulario]** enviar escrituras de acción enviar datos de formulario adaptables enviados para el objeto de modelo de datos especificado en un modelo de datos de formulario a su origen de datos. Al configurar la acción de envío, puede elegir un objeto de modelo de datos cuyos datos enviados desee volver a escribir en su origen de datos.

Además, se puede enviar un archivo adjunto de formulario mediante un modelo de datos de formulario y un documento de registro (DoR) al origen de datos.

Para obtener información sobre el modelo de datos de formulario, consulte [Integración de datos de AEM Forms](/help/forms/using/data-integration.md).

## Acción de envío de portal de formularios {#forms-portal-submit-action}

La variable **[!UICONTROL Acción de envío del portal de Forms]** hace que los datos de formulario estén disponibles a través de un portal de AEM Forms.

Para obtener más información sobre el portal de Forms y la acción de envío, consulte [Componente Borradores y presentaciones](/help/forms/using/draft-submission-component.md).

## Invocar un flujo de trabajo de AEM {#invoke-an-aem-workflow}

La variable **[!UICONTROL Invocar un flujo de trabajo AEM]** la acción submit asocia un formulario adaptable con un flujo de trabajo AEM. Cuando se envía un formulario, el flujo de trabajo asociado se inicia automáticamente en el nodo de procesamiento. Además, coloca el archivo de datos, los archivos adjuntos y el documento de registro, si corresponde, en la ubicación de carga útil del flujo de trabajo.

Antes de usar la variable **[!UICONTROL Invocar un flujo de trabajo AEM]** enviar acción, [configuración de la configuración de AEM DS](/help/forms/using/configuring-the-processing-server-url-.md). Para obtener información sobre la creación de un flujo de trabajo AEM, consulte [Flujos de trabajo centrados en formularios en OSGi](/help/forms/using/aem-forms-workflow.md).

## Revalidación del lado del servidor en formularios adaptables {#server-side-revalidation-in-adaptive-form}

Normalmente, en cualquier sistema de captura de datos en línea, los desarrolladores colocan algunas validaciones de JavaScript en el lado del cliente para aplicar algunas reglas comerciales. Sin embargo, en los exploradores modernos, los usuarios finales tienen la forma de evitar esas validaciones y realizar envíos manualmente mediante diversas técnicas, como la consola de desarrolladores del explorador web. Estas técnicas también son válidas para los formularios adaptables. Un desarrollador de formularios puede crear varias lógicas de validación, pero técnicamente, los usuarios finales pueden omitir esas lógicas de validación y enviar datos no válidos al servidor. Los datos no válidos romperían las reglas empresariales que ha impuesto un autor de formularios.

La función de revalidación del lado del servidor permite ejecutar también las validaciones que ha proporcionado un autor de formularios adaptables al diseñar un formulario adaptable en el servidor. Evita cualquier posible compromiso en el envíos de datos y violaciones de reglas empresariales representadas en términos de validaciones de formularios.

### ¿Qué se debe validar en el servidor? {#what-to-validate-on-server-br}

Todas las validaciones de campo predeterminadas (OOTB) de un formulario adaptable que se vuelven a ejecutar en el servidor son:

* Requerido
* Cláusula de imagen de validación
* Expresión de validación

### Habilitar la validación del lado del servidor {#enabling-server-side-validation-br}

Utilice **Revalidar en el servidor** en el contenedor de formularios adaptables en la barra lateral para habilitar o deshabilitar la validación del lado del servidor para el formulario actual.

![Habilitar la validación del lado del servidor](assets/revalidate-on-server.png)
**Figura:** *Activación de la validación del lado del servidor*

Si el usuario final omite esas validaciones y envía los formularios, el servidor volverá a realizar la validación. Si la validación falla al final del servidor, se detendrá la transacción del envío. Al usuario final se le vuelve a presentar el formulario original. Los datos capturados y enviados se presentarán al usuario como un error.

### Compatibilidad con funciones personalizadas en expresiones de validación {#supporting-custom-functions-in-validation-expressions-br}

A veces, en el caso de **reglas de validación complejas**, la secuencia de comandos de validación exacta reside en funciones personalizadas y la llamada de autor llama a estas funciones personalizadas desde la expresión de validación de campo. Para que esta biblioteca de funciones personalizadas sea conocida y esté disponible mientras se realizan las validaciones del lado del servidor, el autor del formulario puede configurar el nombre de la biblioteca de cliente de AEM en la pestaña **[!UICONTROL Básico]** de las propiedades del contenedor del formulario adaptable como se muestra a continuación.

![Compatibilidad con funciones personalizadas en expresiones de validación](assets/clientlib-cat.png)
**Figura:** *Compatibilidad con funciones personalizadas en expresiones de validación*

El autor puede configurar la biblioteca de javascript personalizada según el formulario adaptable. En la biblioteca, mantenga solo las funciones reutilizables, que dependen de las bibliotecas de terceros jquery y underscore.js .

## Gestión de errores en la acción de envío {#error-handling-on-submit-action}

Como parte de AEM directrices de seguridad y endurecimiento, configure páginas de error personalizadas como 404.jsp y 500.jsp. Se llama a estos controladores cuando aparecen errores al enviar un formulario 404 o 500. También se llama a los controladores cuando estos códigos de error se activan en el nodo Publish.

Para obtener más información, consulte [Personalización de páginas que muestra el Controlador de errores](/help/sites-developing/customizing-errorhandler-pages.md).
