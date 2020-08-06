---
title: 'Flujo de trabajo centrado en Forms en OSGi: referencia de pasos'
seo-title: 'Flujo de trabajo centrado en Forms en OSGi: referencia de pasos'
description: El flujo de trabajo centrado en Forms en los pasos de OSGi le permite crear rápidamente flujos de trabajo basados en formularios adaptables.
seo-description: El flujo de trabajo centrado en Forms en los pasos de OSGi le permite crear rápidamente flujos de trabajo basados en formularios adaptables.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: aheimoz
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '4561'
ht-degree: 0%

---


# Flujo de trabajo centrado en Forms en OSGi: referencia de pasos {#forms-centric-workflow-on-osgi-step-reference}

## Pasos del Forms Workflow {#forms-workflow-steps}

Los pasos del flujo de trabajo de Forms realizan operaciones específicas de AEM Forms en un flujo de trabajo AEM. Estos pasos le permiten crear rápidamente formularios adaptables basados en un flujo de trabajo centrado en Forms en OSGi. Estos flujos de trabajo se pueden utilizar para desarrollar flujos de trabajo básicos de revisión y aprobación, procesos comerciales internos y entre servidores de seguridad. También puede utilizar los pasos de Forms Workflow para inicio de servicios de documento, integrarlos con el flujo de trabajo de firma de Adobe Sign y realizar otras operaciones de AEM Forms. Debe utilizar [AEM Forms Add-on](https://www.adobe.com/go/learn_aemforms_documentation_63) para utilizar estos pasos en un flujo de trabajo.

## Assign task step {#assign-task-step}

El paso de asignación de tarea crea una tarea y la asigna a un usuario o grupo. Junto con la asignación de la tarea, el componente también especifica el formulario adaptable o PDF no interactivo para la tarea. El formulario adaptable es necesario para aceptar datos introducidos por los usuarios y se utiliza un PDF no interactivo o un formulario adaptable de sólo lectura para flujos de trabajo solo de revisión.

También puede utilizar el componente para controlar el comportamiento de la tarea. Por ejemplo, crear un documento de registro automático, asignar la tarea a un usuario o grupo específico, especificar la ruta de los datos enviados, especificar la ruta de los datos que se van a rellenar previamente y especificar las acciones predeterminadas. El paso Asignar Tarea tiene las siguientes propiedades:

* **Título:** Título de la tarea. El título se muestra en AEM Bandeja de entrada.
* **Descripción:** Explicación de las operaciones que se realizan en la tarea. Esta información resulta útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

* **Ruta de miniaturas:** Ruta de la miniatura de la tarea. Si no se especifica ninguna ruta, se muestra una miniatura predeterminada de formulario adaptable y, en Documento de Grabar, se muestra un icono predeterminado.
* **Etapa de flujo de trabajo:** Un flujo de trabajo puede tener varias etapas. Estas etapas se muestran en la Bandeja de entrada AEM. Puede definir estas etapas en las propiedades del modelo (barra de tareas > Página > Propiedades de la página > Fases).
* **Prioridad:** La prioridad seleccionada se muestra en la Bandeja de entrada AEM. Las opciones disponibles son Alta, Media y Baja. El valor predeterminado es Medio.
* **Fecha de vencimiento:** Especifique el número de días u horas después de los cuales se marca la tarea como retrasada. Si selecciona **Desactivado**, la tarea nunca se marca como vencida. También puede especificar un controlador de tiempo de espera para realizar tareas específicas después de que la tarea haya vencido.

* **Días:** Número de días antes de los cuales se completará la tarea. El número de días se contabiliza después de que la tarea se asigne a un usuario. Si una tarea no está completa y sobrepasa el número de días especificado en el campo Días, se activa un controlador de tiempo de espera después de la fecha de vencimiento.
* **Horas:** Número de horas antes de las cuales se completará la tarea. El número de horas se contabiliza después de que la tarea se asigne a un usuario. Si una tarea no está completa y sobrepasa el número de horas especificado en el campo Horas, si se selecciona, se activa un controlador de tiempo de espera después de las horas de vencimiento.
* **Tiempo de espera después de la fecha de vencimiento:** Seleccione esta opción para activar el campo de selección Controlador de tiempo de espera.
* **Controlador de tiempo de espera:** Seleccione la secuencia de comandos que se va a ejecutar cuando el paso de asignación de tarea sobrepase la fecha de vencimiento. Los scripts colocados en el repositorio de CRX en [apps]/fd/panel/scripts/timeoutHandler están disponibles para su selección. La ruta especificada no existe en crx-repository. Un administrador crea la ruta antes de utilizarla.
* **Resalte la acción y el comentario de la última tarea en Detalles de Tarea:** Seleccione esta opción para mostrar la última acción realizada y los comentarios recibidos en la sección de detalles de tarea de una tarea.
* **Tipo:** Elija el tipo de documento que se va a rellenar al iniciar el flujo de trabajo. Puede elegir un formulario adaptable, un formulario adaptable de solo lectura o un documento PDF no interactivo.
* **Utilizar formulario adaptable:** Especifique el método para localizar el formulario adaptable de entrada. Puede utilizar el formulario adaptable disponible en una ruta absoluta, enviado como carga útil al flujo de trabajo o disponible en una ruta calculada mediante una variable. Puede utilizar una variable de tipo String para especificar la ruta.
* **Ruta** de formulario adaptable: Especifique la ruta del formulario adaptable. El campo está disponible cuando se utiliza una opción de formulario adaptable o de solo lectura en el campo Tipo junto con la opción de ruta absoluta en el campo Usar formulario adaptable.
* **Ruta de PDF:** Especifique la ruta de un documento PDF no interactivo. El campo está disponible cuando se selecciona un documento PDF no interactivo en el campo Tipo. La ruta siempre es relativa a la carga útil. Por ejemplo, [Payload_Directory]/Workflow/PDF/credit-card.pdf. La ruta no existe en crx-repository. Un administrador crea la ruta antes de utilizarla. Se requiere una opción Documento de registro activada o formularios adaptables basados en plantillas de formulario para utilizar la opción Ruta de PDF.
* **Para la tarea completada, procese el formulario adaptable como**: Cuando se marca una tarea como completa, el formulario adaptable se puede representar como un formulario adaptable de sólo lectura o como un documento PDF. Se requiere un Documento de la opción Registro activado o formularios adaptables basados en plantilla para procesar el formulario adaptable como Documento de registro.
* **Información que debe rellenarse previamente:** Los siguientes campos que se enumeran a continuación sirven como entradas para la tarea:

   * **Ruta del archivo de datos:** Ruta del archivo de datos de entrada (.json o .xml). La ruta siempre es relativa a la carga útil. Por ejemplo, el archivo contiene los datos enviados para el formulario a través de una aplicación Bandeja de entrada AEM. Una ruta de ejemplo es [Payload_Directory]/workflow/data.
   * **Ruta de datos adjuntos:** Los datos adjuntos disponibles en la ubicación se adjuntan al formulario asociado a la tarea. La ruta siempre es relativa a la carga útil. Una ruta de ejemplo es [Payload_Directory]/attachments/

* **Información enviada:** Los siguientes campos sirven como ubicaciones de salida para la tarea:

   * **Ruta del archivo de datos:** Ruta del archivo de datos (.json o .xml). El archivo de datos contiene información enviada a través del formulario asociado. La ruta siempre es relativa a la carga útil. Por ejemplo, [Payload_Directory]/Workflow/data, donde los datos son un archivo.
   * **Ruta de datos adjuntos:** Ruta para guardar los datos adjuntos del formulario proporcionados en una tarea.
   * **Documento de la ruta de registro:** Ruta para guardar un Documento del archivo de registro. Por ejemplo, [Payload_Directory]/DocumentofRecord/credit-card.pdf. El Documento de registro no se genera si el campo de ruta se deja vacío. La ruta siempre es relativa a la carga útil.

* **Asignar opciones:** Especifique el método para asignar la tarea a un usuario. Puede asignar dinámicamente la tarea a un usuario o grupo mediante la secuencia de comandos Selector de participantes o asignar la tarea a un usuario o grupo de AEM específico.
* **Selector de participantes:** La opción está disponible cuando se selecciona la opción **Dinámicamente para un usuario o grupo** en el campo Opciones de asignación. Puede utilizar un ECMAScript o un servicio para seleccionar dinámicamente un usuario o un grupo. Para obtener más información, consulte Asignación [dinámica de un flujo de trabajo a los usuarios](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) y [Creación de un paso de participante dinámico de Adobe Experience Manager personalizado.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Participantes:** El campo está disponible cuando se selecciona la opción **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** en el campo Selector de participantes. El campo permite seleccionar usuarios o grupos para la opción SelectorParticipanteAleatorio.

* **Argumentos:** El campo está disponible cuando se selecciona una secuencia de comandos que no sea RandomParticipantChoose en el campo Selector de participantes. El campo permite proporcionar una lista de argumentos separados por coma para la secuencia de comandos seleccionada en el campo Selector de participantes.

* **Usuario o grupo:** La tarea se asigna al usuario o grupo seleccionado. La opción está disponible cuando se selecciona la opción **** Para un usuario o grupo específico en el campo Opciones de asignación. El campo lista a todos los usuarios y grupos del grupo de usuarios del flujo de trabajo.

* **Notificar al usuario asignado por correo electrónico:** Seleccione esta opción para enviar notificaciones por correo electrónico al usuario asignado. Estas notificaciones se envían cuando se asigna una tarea a un usuario. Antes de utilizar la opción, habilite las notificaciones desde AEM consola web. Para obtener instrucciones paso a paso, consulte [Configuración de las notificaciones por correo electrónico para el paso de asignación de tareas](/help/forms/using/aem-forms-workflow.md)

* **Plantilla** de correo electrónico HTML: Seleccione la plantilla de correo electrónico para el correo electrónico de notificación. Para editar una plantilla, modifique el archivo ubicado en /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt en crx-repository.
* **Permitir delegación a:** AEM bandeja de entrada ofrece una opción al usuario que ha iniciado sesión para delegar el flujo de trabajo asignado a otro usuario. Puede delegar en el mismo grupo o en el usuario del flujo de trabajo de otro grupo. Si la tarea se asigna a un solo usuario y se selecciona **permitir delegación a miembros del grupo** asignado, no es posible delegar la tarea a otro usuario o grupo.

* **Acciones predeterminadas:** Las acciones Enviar, Guardar y Restablecer están disponibles de forma predeterminada. De forma predeterminada, todas las acciones predeterminadas están activadas.
* **Variable de ruta:** Nombre de la variable route. La variable route captura las acciones personalizadas que un usuario selecciona en AEM Bandeja de entrada.
* **Rutas:** Una tarea puede ramificar a diferentes rutas. Cuando se selecciona en AEM Bandeja de entrada, la ruta devuelve un valor y las ramas del flujo de trabajo se basan en la ruta seleccionada.
* **Título**: Especifique el título de la ruta. Se muestra en AEM Bandeja de entrada.
* **Icono** de coral: Especifique el atributo HTML de un icono de coral. La biblioteca CorelUI de Adobe proporciona un amplio conjunto de iconos que se utilizan para el primer toque. Puede elegir y utilizar un icono para la ruta. Se muestra junto con el título en AEM Bandeja de entrada.
* **Permitir que el usuario asignado agregue un comentario**: Seleccione esta opción para activar los comentarios de la tarea. Un usuario asignado puede agregar los comentarios desde AEM Bandeja de entrada en el momento del envío de la tarea.
* **Permitir que el usuario asignado agregue datos adjuntos a la tarea**: Seleccione esta opción para activar los datos adjuntos para la tarea. Un usuario asignado puede agregar los datos adjuntos desde AEM Bandeja de entrada en el momento del envío de la tarea.
* **Ruta de salida de los archivos adjuntos** de tarea: Especifique la ubicación de la carpeta de datos adjuntos. La ubicación es relativa a la carga útil.
* **Utilizar metadatos personalizados:** Seleccione esta opción para habilitar el campo de metadatos personalizado. Los metadatos personalizados se utilizan en plantillas de correo electrónico.
* **Metadatos personalizados:** Seleccione metadatos personalizados para las plantillas de correo electrónico. Los metadatos personalizados están disponibles en el repositorio crx en apps/fd/panel/scripts/metadataScripts. La ruta especificada no existe en crx-repository. Un administrador crea la ruta antes de utilizarla. También puede utilizar un servicio para los metadatos personalizados. También puede ampliar la `WorkitemUserMetadataService` interfaz para proporcionar metadatos personalizados.

* **Mostrar datos de pasos** anteriores: Seleccione esta opción para habilitar a los cesionarios para la vista de los anteriores cesionarios, las medidas ya adoptadas en la tarea, los comentarios agregados a la tarea y el documento del registro de la tarea completada, si está disponible.
* **Mostrar datos de pasos subsiguientes:** Seleccione esta opción para permitir que el usuario asignado actual vista la acción realizada y los comentarios agregados a la tarea por los siguientes cesionarios. También permite que el cesionario actual vista un documento del registro de la tarea finalizada, si está disponible.
* **Visibilidad del tipo de datos:** De forma predeterminada, un usuario asignado puede realizar la vista de un Documento de registro, de los usuarios asignados, de las medidas adoptadas y de los comentarios que hayan agregado los usuarios asignados anteriores y posteriores. Utilice la opción de visibilidad de tipo de datos para limitar el tipo de datos visibles para los usuarios asignados.

## Enviar paso de correo electrónico {#send-email-step}

Utilice el paso de correo electrónico para enviar un correo electrónico, por ejemplo, un correo electrónico con un documento de registro, un vínculo de un formulario adaptable, un vínculo de una comunicación interactiva o un documento PDF adjunto. El paso Enviar correo electrónico es compatible con el correo electrónico [](https://en.wikipedia.org/wiki/HTML_email)HTML. Los correos electrónicos HTML responden y se adaptan al cliente de correo electrónico y al tamaño de pantalla de los destinatarios. Puede utilizar una plantilla de correo electrónico HTML para definir el aspecto, el esquema de colores y el comportamiento del contenido del correo electrónico.

El paso de correo electrónico utiliza Day CQ Mail Service para enviar correos electrónicos. Antes de utilizar el paso de correo electrónico, asegúrese de que el servicio [de](/help/forms/using/aem-forms-workflow.md) correo electrónico está configurado. El paso de correo electrónico tiene las siguientes propiedades:

**Título:** El título del paso ayuda a identificar el paso en el editor de flujo de trabajo.

**Descripción:** La explicación es útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

**Asunto del correo electrónico:** El asunto se puede recuperar de los metadatos de un flujo de trabajo o especificarse manualmente. Seleccione la opción **Literal** para especificar manualmente un asunto o seleccione la opción **Recuperar metadatos** del flujo de trabajo para recuperar el asunto de una propiedad de metadatos.

**Plantilla** de correo electrónico HTML: Plantilla HTML para el correo electrónico. Puede especificar variables en una plantilla de correo electrónico. El paso Correo electrónico extrae y muestra todas las variables incluidas en una plantilla para entradas.

**Metadatos de plantilla de correo electrónico:** El valor de las variables de plantilla de correo electrónico puede ser un valor especificado por el usuario, la ruta de un recurso en el autor o en el servidor de publicación, la imagen o una propiedad de metadatos del flujo de trabajo.

* **Literal:** Utilice la opción cuando sepa el valor exacto que desea especificar. Por ejemplo, [example@example.com](mailto:example@example.com).

* **Metadatos del flujo de trabajo:** Utilice la opción cuando el valor que se va a utilizar se guarde en una propiedad de metadatos de flujo de trabajo. Después de seleccionar la opción, introduzca el nombre de la propiedad de metadatos en el cuadro de texto vacío debajo de la opción Metadatos del flujo de trabajo. Por ejemplo, emailAddress.
* **Dirección URL del recurso:** Utilice la opción para incrustar un vínculo web de una comunicación interactiva en el correo electrónico. Después de seleccionar la opción, busque y elija la comunicación interactiva que desea incrustar. El recurso puede residir en el autor o en el servidor de publicación.
* **Imagen:** Utilice la opción para incrustar una imagen en el correo electrónico. Después de seleccionar la opción, busque y elija la imagen. La opción de imagen solo está disponible para las etiquetas de imagen (&lt;img src=&quot;&amp;ast;&quot;/>) disponibles en la plantilla de correo electrónico.

**Dirección de correo electrónico del remitente/Destinatario:** Seleccione la opción **Literal** para especificar manualmente una dirección de correo electrónico o seleccione la opción **Recuperar de metadatos** del flujo de trabajo para recuperar la dirección de correo electrónico de una propiedad de metadatos. También puede especificar una lista de matrices de propiedades de metadatos para la opción **Recuperar de metadatos** del flujo de trabajo.

**Ruta de archivo adjunto:** El recurso disponible en la ubicación especificada se adjunta al correo electrónico. La ruta del recurso puede ser relativa a la carga útil o a la ruta absoluta. Una ruta de ejemplo es [Payload_Directory]/attachments/

**Nombre del archivo:** Nombre del archivo adjunto de correo electrónico. El paso de correo electrónico cambia el nombre de archivo original del archivo adjunto al nombre de archivo especificado. El nombre se puede especificar manualmente o recuperar desde una propiedad de metadatos de flujo de trabajo. Utilice la opción **Literal** cuando sepa el valor exacto que desea especificar. Utilice la opción **Recuperar de metadatos** de flujo de trabajo cuando el valor que se va a utilizar se guarde en una propiedad de metadatos de flujo de trabajo.

## Generate Document of Record step {#generate-document-of-record-step}

Cuando se rellena o envía un formulario, puede guardarlo, en formato impreso o en documento. Esto se denomina Documento de registro (DoR). Puede utilizar el paso Generar Documento de registro para crear una versión PDF interactiva o de solo lectura de un formulario adaptable. La versión PDF contiene información rellenada en el formulario junto con la presentación del formulario adaptable.

El paso Documento de registro tiene las siguientes propiedades:

**Utilizar formulario** adaptable: Especifique el método para localizar el formulario adaptable de entrada. Puede utilizar el formulario adaptable disponible en una ruta absoluta, enviado como carga útil al flujo de trabajo o disponible en una ruta calculada mediante una variable. Puede utilizar una variable de tipo String para especificar la ruta.

**Ruta** de formulario adaptable: Especifique la ruta del formulario adaptable. El campo está disponible cuando se utiliza una opción de formulario adaptable o de solo lectura en el campo Tipo junto con la opción de ruta absoluta en el campo Usar formulario adaptable.

**Ruta de datos de entrada:** Ruta de los datos de entrada para el formulario adaptable. Puede mantener los datos en una ubicación relativa a la carga útil o especificar una ruta absoluta de los datos. Los datos de entrada se combinan con el formulario adaptable para crear un documento de registro.

**Ruta de acceso de datos adjuntos de entrada:** Ruta de datos adjuntos de entrada: Ruta de los archivos adjuntos. Estos anexos se incluyen en el Documento de registro. Puede mantener los datos adjuntos en una ubicación relativa a la carga útil o especificar una ruta absoluta de los datos adjuntos.

Si especifica la ruta de una carpeta, por ejemplo, los archivos adjuntos, todos los archivos disponibles directamente en la carpeta se adjuntan al Documento de registro. Si hay algún archivo disponible en las carpetas directamente disponibles en la ruta de datos adjuntos especificada, los archivos se incluyen en el Documento de Grabar como archivos adjuntos. Si hay carpetas en carpetas disponibles directamente, se omitirán.

**Documento generado de ruta de registro:** Especifique la ubicación en la que desea guardar un documento del archivo de registro. Puede sobrescribir la carpeta de carga útil o colocar el documento de registro en una ubicación del directorio de carga útil.

**Configuración regional**: Especifique el idioma del documento del registro.

## Invoke Form Data Model Service step {#invoke-form-data-model-service-step}

Puede utilizar la integración [de datos de](/help/forms/using/data-integration.md) AEM Forms para configurar y conectarse a orígenes de datos dispares. Estas fuentes de datos pueden ser una base de datos, servicio Web, servicio REST, servicio OData y solución CRM. La integración de datos de AEM Forms le permite crear un modelo de datos de formulario que incluye varios servicios para realizar operaciones de recuperación de datos, además de actualizar en la base de datos configurada. Puede utilizar el paso **** Invocar servicio de modelo de datos para seleccionar un modelo de datos de formulario (FDM) y utilizar los servicios de FDM para recuperar, actualizar o agregar datos a orígenes de datos dispares.

Para explicar las entradas de los campos del paso, se utiliza como ejemplo la siguiente tabla de base de datos y el archivo JSON:

**Tabla CustomerDetails de muestra**

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Value<br /> </td> 
  </tr> 
  <tr> 
   <td>Nombre<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Apellidos</td> 
   <td>Rosa</td> 
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

El paso Invocar el servicio del modelo de datos de formulario tiene los campos siguientes para facilitar las operaciones del modelo de datos de formulario:

* **Título:** Título del paso. Ayuda a identificar el paso en el editor de flujo de trabajo.
* **Descripción:** Explicación útil para otros desarrolladores de procesos cuando trabaja en un entorno de desarrollo compartido.

* **Ruta** del modelo de datos de formulario: Busque y seleccione un modelo de datos de formulario presente en el servidor.

* **Servicio**: Lista de los servicios que proporciona el modelo de datos de formulario seleccionado.
* **Entrada para servicios > Proporcionar datos de entrada utilizando literales, metadatos de flujo de trabajo y un archivo** JSON: Un servicio puede tener varios argumentos. Seleccione la opción para obtener el valor de los argumentos de servicio de una propiedad de metadatos de flujo de trabajo, un objeto JSON o introduzca directamente el valor en el cuadro de texto proporcionado:

   * **Literal:** Utilice la opción cuando sepa el valor exacto que desea especificar. Por ejemplo, srose@we.info.
   * **Recuperar de metadatos de flujo de trabajo:** Utilice la opción cuando el valor que se va a utilizar se guarde en una propiedad de metadatos de flujo de trabajo. Por ejemplo, emailAddress.
   * **Notación de punto JSON:** Utilice la opción cuando el valor que desee utilizar esté en un archivo JSON. Por ejemplo, seguro.customerDetails.emailAddress.La opción Anotación de punto JSON solo está disponible si está seleccionada la opción Asignar campos de entrada de la opción JSON de entrada.
   * **Asignar campos de entrada desde JSON de entrada:** Especifique la ruta de un archivo JSON para obtener el valor de entrada de algunos argumentos de servicio del archivo JSON. La ruta del archivo JSON puede ser relativa a la carga útil o a una ruta absoluta.

* **Entrada para servicios > Proporcionar datos de entrada mediante un archivo JSON:** Seleccione la opción para obtener valores para todos los argumentos de un archivo JSON.
* **Ruta** del archivo JSON de entrada: Ruta del archivo JSON que contiene valores para todos los argumentos de servicio. La ruta del archivo JSON puede ser **relativa a la carga útil** o a una ruta **** absoluta.

* **Notación de punto JSON:** Deje el campo en blanco para utilizar todos los objetos del archivo JSON especificado como entrada para los argumentos de servicio. Para leer un objeto JSON específico del archivo JSON especificado como entrada para argumentos de servicio, especifique la notación de puntos para el objeto JSON; por ejemplo, si tiene un JSON similar al que aparece en el inicio de la sección, especifique seguro.customerDetails para proporcionar todos los detalles de un cliente como entrada al servicio.
* **Salida del servicio > Asignar y escribir valores de salida en metadatos:** Seleccione la opción para guardar los valores de salida como propiedades del nodo de metadatos de instancia de flujo de trabajo en crx-repository. Especifique el nombre de la propiedad metadata y seleccione el atributo de salida de servicio correspondiente que se va a asignar con la propiedad metadata; por ejemplo, asigne el número_teléfono devuelto por el servicio de salida con la propiedad phone_number de los metadatos del flujo de trabajo.
* **Salida del servicio > Guardar salida como JSON:** Seleccione la opción para guardar los valores de salida en un archivo JSON.
* **Ruta del archivo JSON de salida:** Ruta para guardar el archivo JSON de salida. La ruta del archivo JSON de salida puede ser relativa a la carga útil o a una ruta absoluta.

## Paso de Documento de firma {#sign-document-step}

El paso Firmar Documento le permite utilizar Adobe Sign para firmar documentos. El paso Firmar Documento tiene las siguientes propiedades:

* **Nombre del acuerdo:** Especifique el título del acuerdo. El nombre del acuerdo pasa a formar parte del asunto y del texto principal del correo electrónico enviado a los firmantes.
* **Configuración regional:** Especifique el idioma para las opciones de correo electrónico y verificación.
* **Configuración** de Adobe Sign Cloud: Elija una configuración de Adobe Sign Cloud. Si no ha configurado Adobe Sign para AEM Forms, consulte [Integración de Adobe Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento que se firmará:** Puede elegir un documento de una ubicación relativa a la carga útil, utilizar la carga útil como documento o especificar una ruta absoluta del documento.
* **Días hasta la fecha límite:** Un documento se marca con vencimiento (fecha límite superada) después de que no haya actividad en la tarea del número de días especificado en el campo **Días hasta la fecha límite** . El número de días se contabiliza después de que el documento se asigne a un usuario para firmar.

* **Frecuencia de correo electrónico del recordatorio:** Puede enviar un mensaje de correo electrónico de recordatorio a intervalos diarios o semanales. La semana se cuenta a partir del día en que se asigna el documento a un usuario para firmar.
* **Proceso de firma:** Puede firmar un documento en un orden secuencial o paralelo. En orden secuencial, un firmante recibe el documento por vez para firmar. Una vez que el primer firmante haya terminado de firmar el documento, el documento se enviará al segundo firmante, etc. En orden paralelo, varios firmantes pueden firmar un documento a la vez.

* **Dirección URL de redirección:** Especifique una dirección URL de redirección. Una vez firmado el documento, puede redirigir al usuario asignado a una dirección URL. Normalmente, esta dirección URL contiene un mensaje de agradecimiento o instrucciones adicionales.
* **Etapa de flujo de trabajo:** Un flujo de trabajo puede tener varias etapas. Estas etapas se muestran en la Bandeja de entrada AEM. Puede definir estas etapas en las propiedades del modelo (barra de tareas > Página > Propiedades de la página > Fases).
* **Seleccionar firmantes:** Especifique el método para elegir firmantes para el documento. Puede asignar dinámicamente el flujo de trabajo a un usuario o grupo, o bien agregar manualmente los detalles de un firmante.
* **Secuencia de comandos o servicio para seleccionar firmantes:** La opción solo está disponible si la opción Dinámicamente está seleccionada en el campo Seleccionar firmantes. Puede especificar un ECMAScript o un servicio para elegir los firmantes y las opciones de verificación de un documento.

* **Detalles del firmante:** La opción solo está disponible si la opción Manualmente está seleccionada en el campo Seleccionar firmantes. Especifique la dirección de correo electrónico y elija un mecanismo de verificación opcional. Antes de seleccionar un mecanismo de verificación de 2 pasos, asegúrese de que la opción de verificación correspondiente está activada para la cuenta de Adobe Sign configurada.
* **Variable de estado:** Un documento habilitado para Adobe Sign almacena el estado de firma del documento en una variable. Especifique el nombre de la variable de estado (adobeSignStatus). Hay una variable de estado de una instancia disponible en CRXDE en /etc/workflow/instance/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData que contiene el estado de una variable.
* **Ruta de Documento firmada:** Especifique la ubicación en la que desea mantener los documentos firmados. Puede sobrescribir el archivo de carga útil o colocar el documento firmado en una ubicación del directorio de carga útil.

## Pasos de Documento Services {#document-services-steps}

AEM servicios de Documento son un conjunto de servicios para crear, montar y asegurar Documentos PDF. AEM Forms proporciona un paso independiente AEM Flujo de trabajo para cada servicio de documento:

### Apply Document Time Stamp step {#apply-document-time-stamp-step}

Añada la marca de hora en un documento. Puede proporcionar detalles de documento, como ruta de documento de entrada, nombre del documento de entrada y ubicación para almacenar los datos exportados. Puede elegir sobrescribir el archivo de carga útil existente o elegir un nombre de archivo diferente para almacenar datos en otro archivo en la carpeta de carga útil.

### Convertir en paso de imagen {#convert-to-image-step}

Convierte un documento PDF en un archivo de imagen. Los formatos de imagen admitidos son JPEG, JPEG2000, PNG y TIFF. La siguiente información se aplica a las conversiones a imágenes TIFF:

* Se genera un archivo TIFF de varias páginas.
* Algunas anotaciones no se incluyen en las imágenes TIFF. No se incluyen las anotaciones que requieren Acrobat para generar su apariencia.

### Convert to PDF/A step {#convert-to-pdf-a-step}

Convierte un documento PDF a formato PDF/A con las opciones proporcionadas. La versión PDF/A de Formato de Documento portátil (PDF) está especializada en archivar y preservar documentos a largo plazo.

### Paso Convertir a PS {#convert-to-ps-step}

Convertir documentos PDF a PostScript. Al convertir a PostScript, puede utilizar la operación de conversión para especificar el documento de origen y si desea convertir a PostScript nivel 2 o 3. El documento PDF que se convierte en un archivo PostScript debe ser no interactivo.

### Create PDF from specified type step {#create-pdf-from-specified-type-step}

Genere un documento PDF a partir de un archivo de entrada. El documento de entrada puede ser relativo a la carga útil, tener una ruta absoluta o puede ser una carga útil.

### Create PDF from URL/HTML/ZIP step {#create-pdf-from-url-html-zip-step}

Genera un documento PDF a partir de la dirección URL, el HTML y el archivo ZIP proporcionados.

### Paso Exportar datos {#export-data-step}

Exporta datos de un archivo PDF forms o XDP. Requiere que introduzca la ruta de acceso de archivo del Documento de entrada y del formato de datos de exportación. Las opciones para Exportar formato de datos son Automático, XDP y XmlData.

### Export PDF to specified type step {#export-pdf-to-specified-type-step}

Convierte un documento PDF a un formato seleccionado.

### Generar paso de PDF no interactivo {#generate-non-interactive-pdf-step}

Generar un PDF no interactivo. Proporciona varias opciones de personalización.

### Paso de importación de datos {#import-data-step}

Combina datos de formulario en un formulario PDF. Puede importar datos de formulario en un formulario PDF.

### Invocar paso DDX {#invoke-ddx-step}

Ejecuta el archivo DDX en el mapa especificado de documentos de entrada y devuelve los documentos PDF manipulados.

### Paso del Optimize PDF {#optimize-pdf-step}

Optimiza los archivos PDF reduciendo su tamaño. El resultado de esta conversión son archivos PDF que pueden ser menores que sus versiones originales. Esta operación también convierte documentos PDF a la versión PDF especificada en los parámetros de optimización.

La configuración de optimización especifica cómo se optimizan los archivos. A continuación se muestran los ajustes de ejemplo:

* Versión de Destinatario PDF
* Descartar objetos como acciones de JavaScript y miniaturas de página incrustadas
* Descartar datos de usuario, como comentarios y archivos adjuntos
* Descartar configuración no válida o no utilizada
* Compresión de datos sin comprimir o uso de algoritmos de compresión más eficientes
* Eliminación de fuentes incrustadas
* Configuración de los valores de transparencia

### Paso de procesamiento de formulario PDF {#render-pdf-form-step}

Procesa un formulario creado en el Diseñador de formularios (XDP) en un formulario PDF.

### Paso Documento seguro {#secure-document-step}

Codificar, firmar y certificar un documento. AEM Forms admite el cifrado basado en contraseña y en certificado. También puede elegir entre varios algoritmos para firmar documentos. Por ejemplo, SHA-256 y SH-512. También puede utilizar el paso del flujo de trabajo para que el lector pueda ampliar los documentos PDF. El paso del flujo de trabajo proporciona una opción para habilitar la descodificación de códigos de barras, las firmas digitales, la importación y exportación de datos PDF y otras opciones.

### Paso Enviar a la impresora {#send-to-printer-step}

Enviar un documento directamente a una impresora. Admite los siguientes mecanismos de acceso a la impresión:

* **Impresora** accesible directa: Una impresora instalada en el mismo equipo se denomina impresora directa accesible y el equipo se denomina host de impresora. Este tipo de impresora puede ser una impresora local que esté conectada directamente al equipo.
* **Impresora** accesible indirecta: A la impresora instalada en un servidor de impresión se accede desde otros equipos. Tecnologías como el sistema de impresión UNIX® (CUPS) común y el protocolo Line Printer Daemon (LPD) están disponibles para conectarse a una impresora en red. Para obtener acceso a una impresora accesible indirecta, especifique la dirección IP o el nombre de host del servidor de impresión. Con este mecanismo, puede enviar un documento a un URI LPD cuando la red tenga un LPD en ejecución. Este mecanismo le permite enrutar el documento a cualquier impresora conectada a la red que tenga un LPD en ejecución.

