---
title: 'Flujo de trabajo centrado en Forms en OSGi: referencia de los pasos'
seo-title: Forms-centric workflow on OSGi - Step Reference
description: El flujo de trabajo centrado en Forms sobre los pasos de OSGi le permite crear rápidamente flujos de trabajo basados en formularios adaptables.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4673'
ht-degree: 77%

---

# Flujo de trabajo centrado en Forms en OSGi: referencia de los pasos {#forms-centric-workflow-on-osgi-step-reference}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Pasos de Forms Workflow {#forms-workflow-steps}

Los pasos de AEM Forms Workflow realizan operaciones específicas en un flujo de trabajo de AEM. Estos pasos le permiten generar rápidamente formularios adaptables basados en flujos de trabajo centrados en Forms en OSGi. Estos flujos de trabajo se pueden utilizar para desarrollar flujos de trabajo básicos de revisión y aprobación, procesos empresariales internos y entre cortafuegos. También puede utilizar los pasos del Forms Workflow para iniciar document services, integrar con el flujo de trabajo de firma de Acrobat Sign y realizar otras operaciones de AEM Forms. Necesita el [complemento de AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=es) para utilizar estos pasos en un flujo de trabajo.

## Paso de tarea de asignación {#assign-task-step}

El paso para asignar una tarea crea una tarea y la asigna a un usuario o grupo. Además de asignar la tarea, el componente también especifica el formulario adaptable o el PDF no interactivo para la tarea. El formulario adaptable es necesario para aceptar los datos que han introducido los usuarios y un PDF no interactivo o un formulario adaptable de solo lectura solo se utiliza para revisar los flujos de trabajo.

También puede utilizar el componente para controlar el comportamiento de la tarea. Por ejemplo, crear un documento de registro automático, asignar la tarea a un usuario o grupo específico, especificar la ruta de los datos enviados, especificar la ruta de los datos que se van a rellenar previamente y especificar las acciones predeterminadas. El paso para asignar una tarea tiene las siguientes propiedades:

* **Título:** título de la tarea. El título se muestra en la bandeja de entrada de AEM.
* **Descripción:** explicación de las operaciones que se realizan en la tarea. Esta información resulta útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

* **Ruta de la vista en miniatura:** ruta de la miniatura de la tarea. Si no se especifica ninguna ruta, se mostrará la miniatura predeterminada de un formulario adaptable y, para el documento de registro, se mostrará un icono predeterminado.
* **Fase del flujo de trabajo:** un flujo de trabajo puede tener varias fases. Estas fases se muestran en la bandeja de entrada AEM. Puede definir estas fases en las propiedades del modelo (Barra de tareas > Página > Propiedades de la página > Fases).
* **Prioridad:** la prioridad seleccionada se muestra en la bandeja de entrada de AEM. Las opciones disponibles son Alta, Media y Baja. El valor predeterminado es Media.
* **Fecha de vencimiento:** especifica el número de días u horas después de los cuales se marcará la tarea con retraso. Si selecciona **No**, la tarea nunca se marca como con retraso. También puede especificar un controlador de tiempo de espera para realizar tareas específicas después de que la tarea haya llegado a la fecha de vencimiento.

* **Días:** número de días antes de los cuales se completará la tarea. El número de días se cuenta después de que la tarea se asigne a un usuario. Si una tarea no está completa y sobrepasa el número de días especificado en el campo Días, si se selecciona, se activa un controlador de tiempo de espera después de la fecha de vencimiento.
* **Horas:** número de horas antes de las cuales se completará la tarea. El número de horas se cuenta después de que la tarea se asigne a un usuario. Si una tarea no está completa y sobrepasa el número de horas especificado en el campo Horas, si se selecciona, se activa un controlador de tiempo de espera después de las horas de vencimiento.
* **Tiempo de espera después de la fecha de vencimiento:** seleccione esta opción para habilitar el campo de selección Controlador de tiempo de espera.
* **Controlador de tiempo de espera:** seleccione el script que se ejecutará cuando el paso para asignar tareas sobrepase la fecha de vencimiento. Scripts colocados en el repositorio CRX en [apps]/fd/dashboard/scripts/timeoutHandler están disponibles para su selección. La ruta especificada no existe en el repositorio CRX. Un administrador crea la ruta antes de utilizarla.
* **Resaltar la acción y el comentario de la última tarea en Detalles de la tarea:** seleccione esta opción para mostrar la última acción realizada y el comentario recibido en la sección de detalles de una tarea.
* **Tipo:** elija el tipo de documento que desea rellenar al iniciar el flujo de trabajo. Puede elegir un formulario adaptable, un formulario adaptable de solo lectura o un documento PDF no interactivo.
* **Utilizar formulario adaptable:** especifica el método para localizar el formulario adaptable de entrada. Puede utilizar el formulario adaptable disponible en una ruta absoluta, enviado como carga útil al flujo de trabajo o disponible en una ruta calculada mediante una variable. Puede utilizar una variable de tipo cadena para especificar la ruta.
* **Ruta de formulario adaptable:** especifica la ruta del formulario adaptable. El campo está disponible cuando se utiliza la opción de formulario adaptable o de formulario adaptable de solo lectura en el campo Tipo junto con la opción de ruta absoluta en el campo Usar formulario adaptable .
* **Ruta del PDF:** Especifique la ruta de un documento de PDF no interactivo. El campo está disponible cuando se elige un documento PDF no interactivo en el campo Tipo. La ruta siempre es relativa a la carga útil. Por ejemplo, [Payload_Directory]/Workflow/PDF/credit-card.pdf. La ruta no existe en el repositorio CRX. Un administrador crea la ruta antes de utilizarla. Se necesita habilitar una opción de documento de registro o formulario adaptable basado en plantillas de formulario para usar la opción Ruta del PDF.
* **Para las tareas completadas, procese el formulario adaptable como:** cuando se marca una tarea como completada, puede procesar el formulario adaptable como un formulario adaptable de solo lectura o un documento PDF. Se necesita habilitar una opción de documento de registro o formulario adaptable basado en plantillas de formulario para procesar el formulario adaptable como documento de registro.
* **Información que se rellenará previamente:** Los siguientes campos sirven como entradas para la tarea:

   * **Ruta del archivo de datos:** Ruta del archivo de datos de entrada (.json o .xml). La ruta siempre es relativa a la carga útil. Por ejemplo, el archivo contiene los datos enviados para el formulario a través de una aplicación de bandeja de entrada AEM. Una ruta de ejemplo es [Payload_Directory]/workflow/data.
   * **Ruta de acceso de datos adjuntos:** Los archivos adjuntos disponibles en la ubicación se adjuntan al formulario asociado a la tarea. La ruta siempre es relativa a la carga útil. Una ruta de ejemplo es [Payload_Directory]/attachments/

* **Información enviada:** los siguientes campos sirven como ubicaciones de salida para la tarea:

   * **Ruta del archivo de datos:** Ruta del archivo de datos (.json o .xml). El archivo de datos contiene información enviada a través del formulario asociado. La ruta siempre es relativa a la carga útil. Por ejemplo, [Payload_Directory]/Workflow/data, donde los datos son un archivo.
   * **Ruta de acceso de datos adjuntos:** Ruta para guardar los archivos adjuntos del formulario proporcionados en una tarea.
   * **Documento de ruta de registro:** Ruta para guardar un archivo de documento de registro. Por ejemplo, [Payload_Directory]/DocumentofRecord/credit-card.pdf. El documento de registro no se genera si el campo de ruta se deja vacío. La ruta siempre es relativa a la carga útil.

* **Asignar opciones:** Especifique el método para asignar la tarea a un usuario. Puede asignar dinámicamente la tarea a un usuario o grupo mediante el script del selector de participantes o asignar la tarea a un usuario o grupo AEM específico.
* **Selector de participantes:** la opción estará disponible cuando la opción **Dinámicamente a un usuario o grupo** esté seleccionada en el campo Asignar opciones. Puede utilizar un ECMAScript o un servicio para seleccionar dinámicamente un usuario o un grupo. Para obtener más información, consulte [Asignar dinámicamente un flujo de trabajo a los usuarios](https://helpx.adobe.com/es/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) y [Crear un paso de participante dinámico de Adobe Experience Manager personalizado.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Participantes:** el campo estará disponible cuando la opción **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** esté seleccionada en el campo Selector de participantes. El campo permite seleccionar usuarios o grupos para la opción RandomParticipantChooser.

* **Argumentos:** el campo estará disponible cuando se seleccione un script que no sea RandomParticipantChoose en el campo Selector de participantes. El campo permite proporcionar una lista de un argumento separado por comas para el script seleccionado en el campo Selector de participantes.

* **Usuario o grupo:** la tarea se asigna al usuario o grupo seleccionado. La opción estará disponible cuando la opción **Para un usuario o grupo específico** esté seleccionada en el campo Asignar opciones. El campo enumera todos los usuarios y grupos del grupo de usuarios del flujo de trabajo.

* **Notificar al usuario asignado por correo electrónico:** Seleccione esta opción para enviar notificaciones por correo electrónico al usuario asignado. Estas notificaciones se envían cuando se asigna una tarea a un usuario. Antes de utilizar la opción , habilite las notificaciones desde AEM consola web. Para obtener instrucciones paso a paso, consulte [configurar las notificaciones de correo electrónico para el paso asignar tarea](/help/forms/using/aem-forms-workflow.md)

* **Plantilla de correo electrónico HTML**: seleccione la plantilla de correo electrónico para el correo electrónico de notificación. Para editar una plantilla, modifique el archivo ubicado en /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt en el repositorio CRX.
* **Permitir delegación en:** la bandeja de entrada de AEM proporciona una opción al usuario que ha iniciado sesión para delegar el flujo de trabajo asignado a otro usuario. Se le permite delegar dentro del mismo grupo o al usuario del flujo de trabajo de otro grupo. Si la tarea está asignada a un único usuario y la opción **Permitir la delegación a los miembros del grupo de asignados** está seleccionada, no es posible delegar la tarea a otro usuario o grupo.

* **Acciones predeterminadas:** Las acciones Enviar, Guardar y Restablecer están disponibles de forma predeterminada. De forma predeterminada, todas estas acciones están habilitadas.
* **Variable de ruta:** nombre de la variable de ruta. La variable de ruta captura las acciones personalizadas que selecciona un usuario en la bandeja de entrada de AEM.
* **Rutas:** una tarea puede ramificarse en diferentes rutas. Cuando se selecciona en la bandeja de entrada AEM, la ruta devuelve un valor y las ramas del flujo de trabajo se basan en la ruta seleccionada.
* **Título** especifica el título de la ruta. Se muestra en la bandeja de entrada AEM.
* **Icono coral**: especifique el atributo HTML de un icono coral. La biblioteca CorelUI de Adobe proporciona un amplio conjunto de iconos táctiles. Puede elegir y utilizar un icono para la ruta. Se muestra junto con el título en la bandeja de entrada AEM.
* **Permitir que el usuario asignado añada un comentario**: seleccione esta opción para habilitar los comentarios en la tarea. Un usuario asignado puede agregar los comentarios desde la bandeja de entrada AEM en el momento del envío de la tarea.
* **Permitir que el usuario asignado agregue archivos adjuntos a la tarea**: seleccione esta opción para habilitar los archivos adjuntos en la tarea. Un usuario asignado puede agregar los archivos adjuntos desde la bandeja de entrada de AEM en el momento del envío de la tarea.
* **Ruta de salida de archivos adjuntos de tareas**: Especifique la ubicación de la carpeta de archivos adjuntos. La ubicación es relativa a la carga útil.
* **Usar metadatos personalizados:** seleccione esta opción para habilitar el campo de metadatos personalizado. Los metadatos personalizados se utilizan en plantillas de correo electrónico.
* **Metadatos personalizados:** seleccione metadatos personalizados para las plantillas de correo electrónico. Los metadatos personalizados están disponibles en el repositorio CRX en apps/fd/dashboard/scripts/metadataScripts. La ruta especificada no existe en el repositorio CRX. Un administrador crea la ruta antes de utilizarla. También puede utilizar un servicio para los metadatos personalizados. También puede ampliar la interfaz de `WorkitemUserMetadataService` para proporcionar metadatos personalizados.

* **Mostrar datos de pasos anteriores:** seleccione esta opción para permitir que los usuarios asignados vean los destinatarios anteriores, las acciones ya realizadas en la tarea, los comentarios agregados a la tarea y el documento de registro de la tarea completada, si está disponible.
* **Mostrar datos de pasos siguientes:** seleccione esta opción para permitir que el usuario asignado actual vea las acciones que realicen y los comentarios que agreguen a la tarea los usuarios asignados posteriores. También permite al usuario asignado actual ver un documento de registro de la tarea finalizada, si está disponible.
* **Visibilidad del tipo de datos:** de forma predeterminada, un usuario asignado puede ver un documento de registro, los usuarios asignados, las medidas adoptadas y los comentarios que hayan agregado los usuarios asignados anteriores y posteriores. Utilice la opción del tipo de visibilidad de datos para limitar el tipo de datos visibles para los usuarios asignados.

## Paso para enviar correo electrónico {#send-email-step}

Utilice este paso para enviar un correo electrónico, por ejemplo, con un documento de registro, un vínculo de un formulario adaptable o con un documento PDF adjunto. Este paso es compatible con el [correo electrónico HTML](https://es.wikipedia.org/wiki/Correo_HTML). Los correos electrónicos HTML responden y se adaptan al cliente de correo electrónico y al tamaño de pantalla de los destinatarios. Puede utilizar una plantilla HTML de correo electrónico para definir el aspecto, el esquema de colores y el comportamiento del correo electrónico.

El paso de correo electrónico utiliza el servicio de correo de Day CQ para enviar correos electrónicos. Antes de utilizar el paso de correo electrónico, asegúrese de que el [servicio de correo electrónico ](/help/forms/using/aem-forms-workflow.md)esté configurado. El paso de correo electrónico tiene las siguientes propiedades:

**Título:** el título ayuda a identificar el paso en el editor de flujo de trabajo.

**Descripción:** la explicación es útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

**Asunto del correo electrónico:** El asunto se puede recuperar de los metadatos de un flujo de trabajo o especificarse manualmente. Seleccione el **Literal** para especificar manualmente un asunto o seleccionar la opción **Recuperar de metadatos del flujo de trabajo** para recuperar el asunto de una propiedad de metadatos.

**Plantilla de correo electrónico HTML**. Plantilla HTML para el correo electrónico. Puede especificar variables en una plantilla de correo electrónico. El paso de correo electrónico extrae y muestra todas las variables incluidas en una plantilla para las entradas.

**Metadatos de las plantillas de correo electrónico:** el valor de las variables de la plantilla de correo electrónico puede ser un valor especificado por el usuario, la ruta de un recurso de parte del autor o en el servidor de publicación, una imagen o una propiedad de metadatos de flujo de trabajo.

* **Literal:** utilice la opción cuando conozca el valor exacto que desea especificar. Por ejemplo, [example@example.com](mailto:example@example.com).

* **Metadatos del flujo de trabajo:** utilice esta opción cuando el valor que desea utilizar se guarde en una propiedad de metadatos de flujo de trabajo. Después de seleccionar la opción, indique el nombre de la propiedad de metadatos en el cuadro de texto vacío debajo de la opción Metadatos del flujo de trabajo. Por ejemplo, emailAddress.
* **Dirección URL del recurso:** utilice la opción para incrustar un vínculo web de una comunicación interactiva al correo electrónico. Después de seleccionar la opción, busque y elija la comunicación interactiva que desea incrustar. El recurso puede residir en el autor o en el servidor de publicación.
* **Imagen:** utilice esta opción para incrustar una imagen en el correo electrónico. Después de seleccionar la opción, busque y elija la imagen. La opción de imagen solo está disponible para las etiquetas de imagen (&lt;img src=&quot;&amp;ast;&quot; />) disponibles en la plantilla de correo electrónico.

**Dirección de correo electrónico del remitente/destinatario:** Seleccione el **Literal** para especificar manualmente una dirección de correo electrónico o seleccionar la opción **Recuperar de metadatos del flujo de trabajo** para recuperar la dirección de correo electrónico de una propiedad de metadatos. También puede especificar una lista de matrices de propiedades de metadatos para la opción **Recuperar a partir de metadatos del flujo de trabajo.**

**Ruta de archivo adjunto:** El recurso disponible en la ubicación especificada se adjunta al correo electrónico. La ruta del recurso puede ser relativa a la carga útil o a la ruta de acceso absoluta. Una ruta de ejemplo es [Payload_Directory]/attachments/

**Nombre del archivo:** nombre del archivo adjunto del correo electrónico. El paso de correo electrónico cambia el nombre de archivo original del archivo adjunto al nombre de archivo especificado. El nombre se puede especificar manualmente o recuperar desde una propiedad de metadatos de flujo de trabajo. Utilice la opción **Literal** cuando sepa el valor exacto que desea especificar. Utilice la variable **Recuperar a partir de metadatos de flujo de trabajo** cuando el valor que se va a utilizar se guarde en una propiedad de metadatos de flujo de trabajo.

## Paso para generar documentos de registro {#generate-document-of-record-step}

Cuando se rellena o se envía un formulario, se puede guardar un registro del formulario, en formato impreso o en formato de documento. Este registro se denomina Documento de registro (DoR). Puede utilizar el paso Generar documento de registro para crear una versión PDF de solo lectura o interactiva de un formulario adaptable. La versión en PDF contiene información rellenada en el formulario junto con la presentación del formulario adaptable.

El paso Documento de registro tiene las siguientes propiedades:

**Utilizar formulario adaptable:** especifica el método para localizar el formulario adaptable de entrada. Puede utilizar el formulario adaptable disponible en una ruta absoluta, enviado como carga útil al flujo de trabajo o disponible en una ruta calculada mediante una variable. Puede utilizar una variable de tipo cadena para especificar la ruta.

**Ruta de formulario adaptable:** especifica la ruta del formulario adaptable. El campo está disponible cuando se utiliza la opción de formulario adaptable o de formulario adaptable de solo lectura en el campo Tipo junto con la opción de ruta absoluta en el campo Usar formulario adaptable .

**Ruta de datos de entrada:** Ruta de los datos de entrada para el formulario adaptable. Puede mantener los datos en una ubicación relativa a la carga útil o especificar una ruta absoluta de los datos. Los datos de entrada se combinan con el formulario adaptable para crear un documento de registro.

**Ruta de datos adjuntos de entrada:** Ruta de datos adjuntos de entrada: Ruta de los archivos adjuntos. Estos archivos adjuntos se incluyen en el documento de registro. Puede mantener los archivos adjuntos en una ubicación relativa a la carga útil o especificar una ruta absoluta de los archivos adjuntos.

Si especifica la ruta de una carpeta, por ejemplo, los archivos adjuntos, todos los archivos disponibles directamente en la carpeta se adjuntan al documento de registro. Si hay archivos disponibles en las carpetas accesibles directamente en la ruta de datos de los archivos adjuntos especificada, los archivos se incluyen en el documento de registro como archivos adjuntos. Si hay carpetas en carpetas accesibles directamente, esas carpetas se omiten.

**Documento generado de ruta de registro:** Especifique la ubicación para mantener un archivo de documento de registro. Puede sobrescribir la carpeta de carga útil o colocar el documento de registro en una ubicación del directorio de carga útil.

**Configuración regional:** especifique el idioma del documento de registro.

## Paso para invocar el servicio de modelo de datos de formulario {#invoke-form-data-model-service-step}

Puede usar la [integración de datos de AEM Forms](/help/forms/using/data-integration.md) para configurar y conectarse a fuentes de datos dispares. Estas fuentes de datos pueden ser una base de datos, un servicio web, un servicio REST, un servicio OData y una solución CRM. La integración de datos de AEM Forms le permite crear un modelo de datos de formulario que incluya varios servicios para realizar operaciones de recuperación, adición y actualización de datos en la base de datos configurada. Puede usar el **paso para invocar el servicio de modelo de datos** para seleccionar un modelo de datos de formulario (FDM) y utilizar los servicios del FDM para recuperar, actualizar o agregar datos a distintas fuentes de datos.

Para explicar las entradas de los campos del paso, se utilizan como ejemplo la siguiente tabla de base de datos y el archivo JSON:

**Tabla de detalles del cliente de muestra**

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Valor<br /> </td> 
  </tr> 
  <tr> 
   <td>FirstName<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>LastName</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>ID de cliente</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Dirección de correo electrónico<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Archivo JSON de muestra**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

El paso para invocar el servicio de modelo de datos de formulario tiene los siguientes campos para facilitar las operaciones del modelo de datos de formulario:

* **Título:** título del paso. Ayuda a identificar el paso en el editor de flujo de trabajo.
* **Descripción:** explicación útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

* **Ruta del modelo de datos del formulario:** busca y selecciona un modelo de datos de formulario presente en el servidor.

* **Servicio:** lista de los servicios que proporciona el modelo de datos de formulario seleccionado.
* **Entrada para servicios > Proporcionar datos de entrada utilizando literal, metadatos de flujo de trabajo y un archivo JSON**: Un servicio puede tener varios argumentos. Seleccione la opción para obtener el valor de los argumentos de servicio de una propiedad de metadatos de flujo de trabajo, un objeto JSON o introduzca directamente el valor en el cuadro de texto proporcionado:

   * **Literal:** utilice la opción cuando conozca el valor exacto que desea especificar. Por ejemplo, srose@we.info.
   * **Recuperar a partir de metadatos de flujo de trabajo:** utilice la opción cuando el valor que desea utilizar se guarde en una propiedad de metadatos de flujo de trabajo. Por ejemplo, emailAddress.
   * **Notación de puntos JSON:** utiliza la opción cuando el valor que desea utilizar esté en un archivo JSON. Por ejemplo, insurance.customerDetails.emailAddress.La opción Anotación de datos JSON solo está disponible si está seleccionada la opción Asignar campos de entrada de JSON .
   * **Asignar campos de entrada desde la entrada JSON:** especifica la ruta de un archivo JSON para obtener el valor de entrada de algunos argumentos de servicio del archivo JSON. La ruta del archivo JSON puede ser relativa a la carga útil o una ruta de acceso absoluta.

* **Entrada para servicios > Proporcionar datos de entrada mediante un archivo JSON:** Seleccione la opción para obtener valores para todos los argumentos de un archivo JSON.
* **Ruta de archivo JSON de entrada**: Ruta del archivo JSON que contiene valores para todos los argumentos de servicio. La ruta del archivo JSON puede ser **relativa a la carga útil** o **ruta de acceso absoluta**.

* **Notación de puntos JSON:** deja el campo en blanco para utilizar todos los objetos del archivo JSON especificado como entrada para argumentos de servicio. Para leer un objeto JSON específico del archivo JSON especificado como entrada para los argumentos del servicio, especifique la notación de puntos para el objeto JSON. Por ejemplo, si tiene un archivo JSON similar al listado al principio de la sección, especifique insurance.customerDetails para proporcionar todos los detalles de un cliente como entrada al servicio.
* **Salida del servicio > Asignar y escribir valores de salida en metadatos:** Seleccione la opción para guardar los valores de salida como propiedades del nodo de metadatos de instancia de flujo de trabajo en crx-repository. Especifique el nombre de la propiedad de metadatos y seleccione el atributo de salida del servicio correspondiente que se va a asignar con la propiedad de metadatos. Por ejemplo, asigne el número de teléfono devuelto por el servicio de salida con la propiedad phone_number (número de teléfono) de los metadatos del flujo de trabajo.
* **Salida del servicio > Guardar salida como JSON:** Seleccione la opción para guardar los valores de salida en un archivo JSON.
* **Ruta del archivo JSON de salida:** Ruta para guardar el archivo JSON de salida. La ruta del archivo JSON de salida puede ser relativa a la carga útil o a una ruta de acceso absoluta.

## Paso para firmar el documento {#sign-document-step}

El paso Firmar documento le permite utilizar Acrobat Sign para firmar documentos. El paso Firmar documento tiene las siguientes propiedades:

* **Nombre del contrato:** especifica el título del contrato. El nombre del acuerdo forma parte del asunto y del texto del cuerpo del correo electrónico enviado a los firmantes.
* **Configuración regional:** especifica el idioma para las opciones de correo electrónico y de verificación.
* **Configuración de Acrobat Sign Cloud**: Elija una configuración de Acrobat Sign Cloud . Si no ha configurado Acrobat Sign para AEM Forms, consulte [Integración de Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento a firmar:** Puede elegir un documento de una ubicación relativa a la carga útil, utilizar la carga útil como documento o especificar una ruta absoluta del documento.
* **Ruta de datos adjuntos de entrada:** Seleccione un archivo adjunto. Estos archivos adjuntos se incluyen en el documento de firma. Puede mantener los archivos adjuntos en una ubicación relativa a la carga útil o especificar una ruta absoluta de los archivos adjuntos.

   Si especifica la ruta de una carpeta, por ejemplo, los archivos adjuntos, todos los archivos disponibles directamente en la carpeta se adjuntan al documento de registro. Si hay archivos disponibles en las carpetas accesibles directamente en la ruta de datos de los archivos adjuntos especificada, los archivos se incluirán en el documento de firma como archivos adjuntos. Si hay carpetas en carpetas accesibles directamente, esas carpetas se omiten.
* **Días hasta la fecha límite:** un documento se marca como vencido (fecha límite superada) después de que no haya actividad en la tarea durante el número de días especificado en el campo **Días hasta la fecha límite**. El número de días se cuenta después de que el documento se asigne a un usuario para su firma.

* **Frecuencia del correo electrónico de recordatorio:** puede enviar un correo electrónico de recordatorio a intervalos diarios o semanales. La semana se cuenta desde el día en que se asigna el documento a un usuario para su firma.
* **Proceso de firma:** puede optar por firmar un documento en orden secuencial o paralelo. En orden secuencial, un solo firmante a la vez recibe el documento para su firma. Una vez que el primer firmante completa la firma del documento, el documento se envía al segundo firmante, y así sucesivamente. En orden paralelo, varios firmantes pueden firmar un documento a la vez.

* **URL de redireccionamiento:** especifica una URL de redireccionamiento. Una vez firmado el documento, puede redirigir al usuario asignado a una dirección URL. Normalmente, esta URL contiene un mensaje de agradecimiento o instrucciones adicionales.
* **Fase del flujo de trabajo:** un flujo de trabajo puede tener varias fases. Estas fases se muestran en la bandeja de entrada AEM. Puede definir estas fases en las propiedades del modelo (Barra de tareas > Página > Propiedades de la página > Fases).
* **Seleccionar firmantes:** especifica el método para elegir firmantes para el documento. Puede asignar dinámicamente el flujo de trabajo a un usuario o grupo, o agregar manualmente los detalles de un firmante.
* **Script o servicio para seleccionar firmantes:** la opción solo estará disponible si la opción Dinámicamente está seleccionada en el campo Seleccionar firmantes. Puede especificar un ECMAScript o un servicio para elegir los firmantes y las opciones de verificación de un documento.

* **Detalles del firmante:** la opción solo estará disponible si la opción Manualmente está seleccionada en el campo Seleccionar firmantes. Especifique la dirección de correo electrónico y elija un mecanismo de verificación opcional. Antes de seleccionar un mecanismo de verificación de 2 pasos, asegúrese de que la opción de verificación correspondiente esté habilitada para la cuenta de Acrobat Sign configurada.
* **Variable de estado:** Un documento habilitado para Acrobat Sign almacena el estado de firma del documento en una variable. Especifique el nombre de la variable de estado (adobeSignStatus). Una variable de estado de una instancia está disponible en CRXDE en /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData contiene el estado de una variable.
* **Ruta del documento firmado:** Especifique la ubicación para conservar los documentos firmados. Puede sobrescribir el archivo de carga útil o colocar el documento firmado en una ubicación del directorio de carga útil.

## Pasos de Servicios de documentos {#document-services-steps}

Los Servicios de documentos de AEM son un conjunto de servicios para crear, combinar y asegurar documentos PDF. AEM Forms proporciona un paso AEM flujo de trabajo independiente para cada servicio de documentos:

### Paso Aplicar marca de fecha y hora a un documento {#apply-document-time-stamp-step}

Agregar una marca de hora a un documento. Proporcione detalles del documento, como la ruta y el nombre del documento de entrada y la ubicación para almacenar los datos exportados. Puede sobrescribir el archivo de carga útil existente o elegir un nombre de archivo diferente para almacenar los datos en un archivo diferente en la carpeta de carga útil.

### Paso Convertir en imagen {#convert-to-image-step}

Convierte un documento PDF en un archivo de imagen. Los formatos de imagen compatibles son JPEG, JPEG2000, PNG y TIFF. La siguiente información se aplica a las conversiones a imágenes de TIFF:

* Se genera un archivo TIFF de varias páginas.
* Algunas anotaciones no se incluyen en las imágenes de TIFF. No se incluyen las anotaciones que requieren que Acrobat genere su apariencia.

### Paso para convertir a PDF/A {#convert-to-pdf-a-step}

Convierte un documento PDF a formato PDF/A mediante las opciones proporcionadas. La versión del PDF/A de Portable Document Format (PDF) está especializada en archivar y conservar documentos a largo plazo.

### Paso Convertir a PS {#convert-to-ps-step}

Convertir documentos PDF a PostScript. Al convertir a PostScript, puede utilizar la operación de conversión para especificar el documento de origen y si desea convertir a PostScript de nivel 2 o 3. El documento PDF que convierta a un archivo PostScript no debe ser interactivo.

### Paso Crear PDF a partir del tipo especificado {#create-pdf-from-specified-type-step}

Genere un documento PDF a partir de un archivo de entrada. El documento de entrada puede ser relativo a la carga útil, tener una ruta absoluta o ser carga útil en sí.

### Paso Crear PDF desde URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Genera un documento PDF a partir de la dirección URL, el HTML y el archivo ZIP proporcionados.

### Paso Exportar datos {#export-data-step}

Exporta datos de un archivo de formularios PDF o de un XDP. Es necesario que introduzca la ruta de archivo del documento de entrada y el formato de datos de exportación. Las opciones de formato de datos de exportación son Auto, XDP y XmlData.

### Paso Exportar PDF al tipo especificado {#export-pdf-to-specified-type-step}

Convierte un documento PDF en un formato seleccionado.

### Paso Generar PDF no interactivo {#generate-non-interactive-pdf-step}

Genera un PDF no interactivo. Proporciona varias opciones de personalización.

### Paso Importar datos {#import-data-step}

Combina datos de formulario en un formulario PDF. Puede importar datos de formulario en un formulario PDF.

### Paso para invocar DDX {#invoke-ddx-step}

Ejecuta el archivo DDX en el mapa especificado de documentos de entrada y devuelve los documentos PDF manipulados.

### Paso Optimizar PDF {#optimize-pdf-step}

Optimiza los archivos PDF al reducir su tamaño. El resultado de esta conversión son archivos PDF que pueden ser menores que sus versiones originales. Esta operación también convierte los documentos PDF a la versión PDF especificada en los parámetros de optimización.

La configuración de optimización especifica cómo se optimizan los archivos. A continuación se muestra un ejemplo de configuración:

* Versión del PDF objetivo
* Descartar objetos, como acciones de JavaScript y miniaturas de páginas incrustadas
* Descartar datos de usuario, como comentarios y archivos adjuntos
* Descartar configuración no válida o no utilizada
* Comprimir datos sin comprimir o usar algoritmos de compresión más eficientes
* Eliminar fuentes incrustadas
* Configurar valores de transparencia

### Paso Procesar formulario PDF {#render-pdf-form-step}

Procesa un formulario creado en Forms Designer (XDP) en un formulario de PDF.

### Paso Proteger documento {#secure-document-step}

Codificar, firmar y certificar un documento. AEM Forms admite el cifrado basado en contraseña y en certificado. También puede elegir entre varios algoritmos para firmar documentos. Por ejemplo, SHA-256 y SH-512. También puede utilizar el paso del flujo de trabajo para ampliar los documentos PDF. El paso del flujo de trabajo ofrece la opción de habilitar la descodificación de código de barras, las firmas digitales, la importación y exportación de datos de PDF y otras opciones.

### Paso Enviar a la impresora {#send-to-printer-step}

Envíe un documento directamente a una impresora. Admite los siguientes mecanismos de acceso a la impresión:

* **Impresora de acceso directo:** una impresora instalada en el mismo equipo se denomina impresora de acceso directo y el equipo se denomina host de impresora. Este tipo de impresora puede ser una impresora local que esté conectada al equipo directamente.
* **Impresora de acceso indirecto:** se accede a la impresora instalada en un servidor de impresión desde otros equipos. Tecnologías como el sistema de impresión común UNIX® (CUPS) y el protocolo Line Printer Daemon (LPD) están disponibles para conectarlos a una impresora de la red. Para acceder a una impresora de acceso indirecto, especifique la IP o el nombre de host del servidor de impresión. Con este mecanismo, puede enviar un documento a un URI LPD cuando la red tenga un LPD en ejecución. El mecanismo permite enrutar el documento a cualquier impresora que esté conectada a la red que tenga una LPD en ejecución.
