---
title: Configuración de la acción Enviar
seo-title: Configuración de la acción Enviar
description: AEM Forms permite configurar una acción de envío para definir cómo se procesa un formulario adaptable después del envío. Puede utilizar acciones de envío integradas o escribir las suyas propias desde cero.
seo-description: AEM Forms permite configurar una acción de envío para definir cómo se procesa un formulario adaptable después del envío. Puede utilizar acciones de envío integradas o escribir las suyas propias desde cero.
uuid: aa261e65-a1ec-402b-80de-0ba8a294e315
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: fea76f90-22d5-4836-9901-a35229401eb0
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 1%

---


# Configuración de la acción Enviar {#configuring-the-submit-action}

## Introducción al envío de acciones {#introduction-to-submit-actions}

Una acción de envío se activa cuando un usuario hace clic en el botón Enviar de un formulario adaptable. Puede configurar la acción de envío en el formulario adaptable. Los formularios adaptables proporcionan algunas acciones de envío listas para usar. Puede copiar y ampliar las acciones de envío predeterminadas para crear su propia acción de envío. Sin embargo, según sus necesidades, puede escribir y registrar su propia acción de envío para procesar los datos en el formulario enviado.

Cuando un formulario se rellena previamente o se envía, los datos enviados se redirigen a través de AEM para el tratamiento de datos en formatos intermedios. Los datos no se guardan en una instancia de AEM, excepto cuando el formulario adaptable utiliza Adobe Sign, verifica, el borrador o el envío del portal de formularios o AEM Flujos de trabajo

Puede configurar una acción de envío en la sección **[!UICONTROL Envío]** de las propiedades del contenedor del formulario adaptable, en la barra lateral.

![Configurar Enviar ](assets/thank-you-setting.png)
**ActionFigura:** *Configurar acción de envío*

Las acciones de envío predeterminadas disponibles con los formularios adaptables son:

* Enviar al extremo REST
* Enviar correo electrónico
* Enviar PDF por correo electrónico
* Invocar un Forms Workflow
* Enviar mediante modelo de datos de formulario
* Acción de envío del portal de Forms
* Invocar un flujo de trabajo AEM

>[!NOTE]
>
>La acción Enviar PDF mediante envío por correo electrónico solo se aplica a formularios adaptables que utilizan plantilla XFA como modelo de formulario.

>[!NOTE]
>
>Asegúrese de que [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder exists. El directorio es necesario para almacenar los archivos adjuntos temporalmente. Si el directorio no existe, créelo.

>[!CAUTION]
>
>Si [prefill](/help/forms/using/prepopulate-adaptive-form-fields.md) es una plantilla de formulario, un modelo de datos de formulario o un formulario adaptable basado en esquema con etiquetas XML o JSON a un esquema (esquema XML, esquema JSON, plantilla de formulario o modelo de datos de formulario) que sea datos que no contenga etiquetas &lt;afData>, &lt;afBoundData> ni &lt;/afUnboundData>, los datos de campos no enlazados (campos no enlazados) son campos de formulario adaptables sin [bindref](/help/forms/using/prepopulate-adaptive-form-fields.md) propiedad) del formulario adaptable se pierde.

Puede escribir una acción de envío personalizada para formularios adaptables para que cumplan con su caso de uso. Para obtener más información, consulte [Escritura de acción de envío personalizada para formularios adaptables](/help/forms/using/custom-submit-action-form.md).

## Enviar al extremo REST {#submit-to-rest-endpoint}

La opción de envío **[!UICONTROL Submit to REST endpoint]** pasa los datos rellenados en el formulario a una página de confirmación configurada como parte de la solicitud de GET HTTP. Puede añadir el nombre de los campos que desea solicitar. El formato de la solicitud es:

`{fieldName}={request parameter name}`

Como se muestra en la imagen siguiente, `param1` y `param2` se pasan como parámetros con valores copiados de los campos **[!UICONTROL textbox]** y **[!UICONTROL numericbox]** para la siguiente acción.

También puede **[!UICONTROL Habilitar solicitud de POST]** y proporcionar una URL para publicar la solicitud. Para enviar datos al servidor de AEM que aloja el formulario, utilice una ruta relativa correspondiente a la ruta raíz del servidor de AEM. Por ejemplo, /content/forms/af/SampleForm.html. Para enviar datos a cualquier otro servidor, utilice la ruta absoluta.

![Configuración de la acción de envío de extremo de resto](assets/action-config.png)

Configuración de la acción de envío de extremo de resto

>[!NOTE]
Para pasar los campos como parámetros en una URL REST, todos los campos deben tener nombres de elementos diferentes, incluso si los campos se colocan en paneles diferentes.

### Publicar datos enviados en un recurso o punto final de reposo externo  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Utilice la acción **[!UICONTROL Submit to REST Endpoint]** para publicar los datos enviados en una URL de reposo. La URL puede ser de un servidor interno (el servidor en el que se representa el formulario) o externo.

Para enviar datos a un servidor interno, proporcione la ruta del recurso. Los datos se publican en la ruta del recurso. Por ejemplo, /content/restEndPoint. Para esas solicitudes posteriores se utiliza la información de autenticación de la solicitud de envío.

Para enviar datos a un servidor externo, proporcione una URL. El formato de la URL es https:// host:port/path_to_rest_end_point. Asegúrese de configurar la ruta para gestionar la solicitud del POST de forma anónima.

![Asignación de valores de campo pasados como parámetros de página de agradecimiento](assets/post-enabled-actionconfig.png)

En el ejemplo anterior, la información introducida por el usuario en `textbox` se captura usando el parámetro `param1`. La sintaxis para anunciar datos capturados mediante `param1` es:

`String data=request.getParameter("param1");`

Del mismo modo, los parámetros que se utilizan para publicar datos XML y archivos adjuntos son `dataXml` y `attachments`.

Por ejemplo, se utilizan estos dos parámetros en la secuencia de comandos para analizar los datos en un punto final de descanso. Se utiliza la siguiente sintaxis para almacenar y analizar los datos:

`String data=request.getParameter("dataXml");`\
`String att=request.getParameter("attachments");`

En este ejemplo, `data` almacena los datos XML y `att` almacena los datos adjuntos.

## Enviar correo electrónico {#send-email}

La acción **[!UICONTROL Send Email]** submit envía un correo electrónico a uno o varios destinatarios cuando el formulario se envía correctamente. El correo electrónico generado puede contener datos de formulario en un formato predefinido.

>[!NOTE]
Todos los campos del formulario deben tener nombres de elemento diferentes, incluso si se colocan en paneles diferentes), para incluir los datos del formulario en un mensaje de correo electrónico.

## Enviar PDF por correo electrónico {#send-pdf-via-email}

La acción de envío **[!UICONTROL Send PDF via Email]** envía un correo electrónico con un PDF que contiene datos del formulario a uno o varios destinatarios cuando el formulario se envía correctamente.

**Nota:** *Esta acción de envío está disponible para formularios adaptables basados en XFA y formularios de adaptación basados en XSD que tienen la plantilla Documento de registro.*

## Invocar un flujo de trabajo de formularios {#invoke-a-forms-workflow}

La opción **[!UICONTROL Submit to Forms workflow]** submit envía un xml de datos y archivos adjuntos (si los hay) a un LiveCycle de Adobe existente o a AEM Forms en un proceso JEE.

Para obtener información sobre cómo configurar la acción de envío del flujo de trabajo Enviar a formularios , consulte [Envío y procesamiento de los datos del formulario mediante flujos de trabajo de formularios](/help/forms/using/submit-form-data-livecycle-process.md).

## Enviar mediante modelo de datos de formulario {#submit-using-form-data-model}

La acción de envío **[!UICONTROL Submit using Form Data Model]** escribe los datos de formulario adaptables enviados para el objeto de modelo de datos especificado en un modelo de datos de formulario en su origen de datos. Al configurar la acción de envío, puede elegir un objeto de modelo de datos cuyos datos enviados desee volver a escribir en su origen de datos.

Además, se puede enviar un archivo adjunto de formulario mediante un modelo de datos de formulario y un documento de registro (DoR) al origen de datos.

Para obtener información sobre el modelo de datos de formulario, consulte [AEM Forms Data Integration](/help/forms/using/data-integration.md).

## Acción de envío del portal de Forms {#forms-portal-submit-action}

La opción **[!UICONTROL Forms Portal Submit Action]** hace que los datos del formulario estén disponibles a través de un portal de AEM Forms.

Para obtener más información sobre el portal de Forms y la acción de envío, consulte [Borradores y componentes de envío](/help/forms/using/draft-submission-component.md).

## Invocar un flujo de trabajo AEM {#invoke-an-aem-workflow}

La acción de envío **[!UICONTROL Invocar un flujo de trabajo AEM]** asocia un formulario adaptable con un flujo de trabajo AEM. Cuando se envía un formulario, el flujo de trabajo asociado se inicia automáticamente en el nodo de procesamiento. Además, coloca el archivo de datos, los archivos adjuntos y el documento de registro, si corresponde, en la ubicación de carga útil del flujo de trabajo.

Antes de utilizar la acción de envío **[!UICONTROL Invocar un flujo de trabajo AEM]**, [configure los AEM DS](/help/forms/using/configuring-the-processing-server-url-.md). Para obtener información sobre la creación de un flujo de trabajo AEM, consulte [Flujos de trabajo centrados en formularios en OSGi](/help/forms/using/aem-forms-workflow.md).

## Revalidación del lado del servidor en formato adaptable {#server-side-revalidation-in-adaptive-form}

Normalmente, en cualquier sistema de captura de datos en línea, los desarrolladores colocan algunas validaciones de JavaScript en el lado del cliente para aplicar algunas reglas comerciales. Sin embargo, en los navegadores modernos, los usuarios finales tienen la forma de evitar esas validaciones y realizar envíos manualmente utilizando diversas técnicas, como la consola de desarrolladores del explorador web. Estas técnicas también son válidas para los formularios adaptables. Un desarrollador de formularios puede crear varias lógicas de validación, pero técnicamente, los usuarios finales pueden omitir esas lógicas de validación y enviar datos no válidos al servidor. Los datos no válidos romperían las reglas comerciales que ha impuesto un autor de formularios.

La función de revalidación del lado del servidor permite ejecutar también las validaciones que ha proporcionado un autor de formularios adaptables al diseñar un formulario adaptable en el servidor. Evita cualquier posible compromiso de envíos de datos y violaciones de reglas comerciales representadas en términos de validaciones de formularios.

### ¿Qué se debe validar en el servidor? {#what-to-validate-on-server-br}

Todas las validaciones de campo predeterminadas (OOTB) de un formulario adaptable que se vuelven a ejecutar en el servidor son:

* Requerido
* Cláusula de imagen de validación
* Expresión de validación

### Habilitación de la validación del lado del servidor {#enabling-server-side-validation-br}

Utilice **Revalidate on server** en Contenedor de formulario adaptable en la barra lateral para habilitar o deshabilitar la validación del lado del servidor para el formulario actual.

![Activación de la ](assets/revalidate-on-server.png)
**validación del lado del servidorFigura:** *Habilitación de la validación del lado del servidor*

Si el usuario final omite esas validaciones y envía los formularios, el servidor vuelve a realizar la validación. Si la validación falla al final del servidor, se detiene la transacción de envío. Al usuario final se le vuelve a presentar el formulario original. Los datos capturados y enviados se presentan al usuario como un error.

### Compatibilidad con funciones personalizadas en expresiones de validación {#supporting-custom-functions-in-validation-expressions-br}

En ocasiones, en el caso de **reglas de validación complejas**, la secuencia de comandos de validación exacta reside en funciones personalizadas y la llamada de autor realiza estas funciones personalizadas desde la expresión de validación de campo. Para que esta biblioteca de funciones personalizada sea conocida y esté disponible mientras se realizan las validaciones del lado del servidor, el autor del formulario puede configurar el nombre de AEM biblioteca de cliente en la pestaña **[!UICONTROL Basic]** de las propiedades del contenedor de formularios adaptables, como se muestra a continuación.

![Compatibilidad con funciones personalizadas en las ](assets/clientlib-cat.png)
**expresiones de validaciónFigura:** *Compatibilidad con funciones personalizadas en las expresiones de validación*

El autor puede configurar la biblioteca de javascript personalizada según el formulario adaptable. En la biblioteca, mantenga solo las funciones reutilizables, que dependen de las bibliotecas de terceros jquery y underscore.js .

## Gestión de errores en la acción de envío {#error-handling-on-submit-action}

Como parte de AEM directrices de seguridad y endurecimiento, configure páginas de error personalizadas como 404.jsp y 500.jsp. Se llama a estos controladores cuando aparecen errores al enviar un formulario 404 o 500. También se llama a los controladores cuando estos códigos de error se activan en el nodo Publish .

Para obtener más información, consulte [Personalización de páginas que muestra el Controlador de errores](/help/sites-developing/customizing-errorhandler-pages.md).
