---
title: Uso de Acrobat Sign en un formulario adaptable
seo-title: Using Acrobat Sign in an adaptive form
description: Habilite los flujos de trabajo de firma electrónica (Acrobat Sign) para un formulario adaptable a fin de automatizar los flujos de trabajo de firma, simplificar los procesos de firma única y múltiple y firmar electrónicamente formularios desde dispositivos móviles.
seo-description: Enable e-signature (Acrobat Sign) workflows for an adaptive form to automate signing workflows, simplify single and multi-signature processes, and to electronically sign forms from mobile devices.
uuid: 9c65dc44-c1a5-44df-8659-6efbe347575b
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29fc297e-0a95-4d2a-bfe6-5676d53624db
noindex: true
feature: Adaptive Forms, Acrobat Sign
exl-id: 5922ea6e-8be9-4e65-89a6-67b6cc12c4ee
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '3562'
ht-degree: 16%

---

# Uso de Acrobat Sign en un formulario adaptable {#using-adobe-sign-in-an-adaptive-form}

Habilite los flujos de trabajo de firma electrónica (Acrobat Sign) para un formulario adaptable a fin de automatizar los flujos de trabajo de firma, simplificar los procesos de firma única y múltiple y firmar electrónicamente formularios desde dispositivos móviles.

Acrobat Sign permite los flujos de trabajo de firma electrónica para formularios adaptables. Las firmas electrónicas mejoran los flujos de trabajo para procesar documentos para áreas legales, de ventas, de nómina, de administración de recursos humanos y más.

En un escenario típico de Acrobat Sign y formularios adaptables, un usuario rellena un formulario adaptable para solicitar un servicio. Por ejemplo, una solicitud de hipoteca y tarjeta de crédito requiere firmas legales de todos los prestatarios y cosolicitantes. Para habilitar los flujos de trabajo de firma electrónica para situaciones similares, puede integrar Acrobat Sign con AEM Forms. Algunos ejemplos más son:

* Cerrar acuerdos desde cualquier dispositivo con procesos de propuesta, presupuesto y contrato totalmente automatizados.
* Finalizar los procesos de Recursos Humanos más rápido y ofrecer a sus empleados las experiencias digitales.
* Reducir los tiempos de ciclo de contrato e incorporar a sus proveedores más rápido.
* Crear flujos de trabajo digitales que automaticen procesos comunes.

La integración de Acrobat Sign con AEM Forms admite:

* Flujos de trabajo de firma de usuarios únicos y múltiples
* Flujos de trabajo de firma secuenciales y simultáneos
* Experiencias de firma dentro y fuera de formulario
* Firma de formularios como usuario anónimo o con sesión iniciada
* Procesos de firma dinámica (integración con el flujo de trabajo de AEM Forms)
* Autenticación a través de una base de conocimiento, un teléfono y perfiles sociales

Conozca las [prácticas recomendadas de uso de Acrobat Sign con formularios adaptables](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) para crear mejores experiencias de firma.

## Requisitos previos {#prerequisites}

Antes de usar Acrobat Sign en un formulario adaptable:

* Asegúrese de que el servicio en la nube de AEM Forms esté configurado para utilizar Acrobat Sign. Para obtener más información, consulte [Integración de Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).
* Mantenga lista de firmantes lista. Se requiere al menos una dirección de correo electrónico para cada firmante.

## Configuración de Acrobat Sign para un formulario adaptable {#configure-adobe-sign-for-an-adaptive-form}

Siga estos pasos para configurar Acrobat Sign para un formulario adaptable:

1. [Edición de las propiedades de formulario adaptables para Acrobat Sign](#enableadobesign)
1. [Adición de campos de Acrobat Sign a un formulario adaptable](#addadobesignfieldstoanadaptiveform)
1. [Habilitar Acrobat Sign para un formulario adaptable](#enableadobsignforanadaptiveform)
1. [Seleccione el Cloud Service de Acrobat Sign para un formulario adaptable](#selectadobesigncloudserviceforanadaptiveform)

1. [Agregar firmantes de Acrobat Sign a un formulario adaptable](#addsignerstoanadaptiveform)
1. [Seleccione Enviar acción para un formulario adaptable](#selectsubmitactionforanadaptiveform)

![signer-details](assets/signer-details.png)

### Edición de las propiedades de formulario adaptables para Acrobat Sign {#enableadobesign}

Configure las propiedades de formulario adaptables para Acrobat Sign en un formulario adaptable existente o nuevo.

[Creación de un formulario adaptable para Acrobat Sign](/help/forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) describe los pasos para crear un formulario adaptable básico. Consulte [Creación de un formulario adaptable](/help/forms/using/creating-adaptive-form.md) para otras opciones disponibles al crear un formulario adaptable.

#### Creación de un formulario adaptable para Acrobat Sign {#create-an-adaptive-form-for-adobe-sign}

Siga estos pasos para crear un formulario adaptable para Acrobat Sign:

1. Vaya a **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formularios y documentos]**.
1. Pulse **[!UICONTROL Crear]** y seleccione **[!UICONTROL Formulario adaptable]**. Aparecerá una lista de plantillas. Seleccione la plantilla y pulse **[!UICONTROL Siguiente]**.
1. En la pestaña **[!UICONTROL Básico]**:

   1. Especifique la variable **Nombre** y **Título** para el formulario adaptable.
   1. Seleccione el [contenedor de configuración](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) creado al configurar Acrobat Sign con AEM Forms.

      >[!NOTE]
      >
      >La variable **[!UICONTROL Cloud Service de Acrobat Sign]** la lista desplegable muestra los servicios de nube que están configurados en el contenedor de configuración que seleccione en este campo. La variable **[!UICONTROL Cloud Service de Acrobat Sign]** la lista desplegable está disponible en la **[!UICONTROL Firma electrónica]** de las propiedades del formulario adaptable al seleccionar la **[!UICONTROL Habilitar Acrobat Sign]** .

1. En la pestaña **[!UICONTROL Modelo de formulario]**, seleccione una de las siguientes opciones:

   * Seleccione el **[!UICONTROL Asociar plantilla de formulario como la plantilla Documento de registro]** y seleccione una plantilla Documento de registro. Si utiliza un formulario adaptable basado en una plantilla de formulario, los documentos enviados para firmar sólo mostrarán aquellos campos basados en la plantilla de formulario asociada. No muestra todos los campos del formulario adaptable.
   * Seleccione el **[!UICONTROL Generar documento de registro]** . Si utiliza la opción Documento de registro habilitado para el formulario adaptable, el documento enviado para firmar muestra todos los campos del formulario adaptable.

1. Pulse **[!UICONTROL Crear.]** Se crea un formulario adaptable con firma habilitada, que se puede utilizar para agregar campos de Acrobat Sign.

#### Edición de un formulario adaptable para Acrobat Sign {#editafsign}

Siga estos pasos para utilizar Acrobat Sign en un formulario adaptable existente:

1. Vaya a **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formularios y documentos]**.
1. Seleccione el formulario adaptable y pulse **[!UICONTROL Propiedades]**.
1. En el **[!UICONTROL Básico]** , seleccione [contenedor de configuración](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) creado al configurar Acrobat Sign con AEM Forms.
1. En la pestaña **[!UICONTROL Modelo de formulario]**, seleccione una de las siguientes opciones:

   * Seleccione el **[!UICONTROL Asociar plantilla de formulario como la plantilla Documento de registro]** y seleccione una plantilla Documento de registro. Si utiliza un formulario adaptable basado en una plantilla de formulario, los documentos enviados para firmar sólo mostrarán aquellos campos basados en la plantilla de formulario asociada. No muestra todos los campos del formulario adaptable.
   * Seleccione el **[!UICONTROL Generar documento de registro]** . Si utiliza la opción Documento de registro habilitado para el formulario adaptable, el documento enviado para firmar muestra todos los campos del formulario adaptable.

1. Pulse **[!UICONTROL Guardar y cerrar]**. El formulario adaptable está habilitado para Acrobat Sign.

### Adición de campos de Acrobat Sign a un formulario adaptable {#addadobesignfieldstoanadaptiveform}

Acrobat Sign tiene varios campos que se pueden colocar en un formulario adaptable. Estos campos aceptan varios tipos de datos, como firmas, iniciales, empresa o título, y ayudan a recopilar información adicional durante la firma, junto con las firmas. Puede utilizar el componente Bloque de Acrobat Sign para colocar campos de Acrobat Sign en varias ubicaciones de un formulario adaptable.

Siga estos pasos para agregar campos a un formulario adaptable y personalizar diversas opciones relacionadas con estos campos:

1. Arrastrar y soltar **Bloque de Acrobat Sign** del navegador de componentes al formulario adaptable. El componente Bloque de Acrobat Sign tiene todos los campos de Acrobat Sign compatibles. De forma predeterminada, agrega un **Firma** al formulario adaptable.

   ![sign-block](assets/sign-block.png)

   De forma predeterminada, el bloque de Acrobat Sign no está visible en el formulario adaptable publicado. Solo se ve en los documentos de firma. Puede cambiar la visibilidad del bloque de Acrobat Sign desde las propiedades del componente Bloque de Acrobat Sign.

   >[!NOTE]
   >
   >* El uso del bloque Acrobat Sign no es obligatorio para utilizar Acrobat Sign en un formulario adaptable. Si no utiliza el bloque Acrobat Sign y agrega campos para los firmantes, el campo de firma predeterminado se muestra en la parte inferior de los documentos de firma.
   >* Utilice el bloque Acrobat Sign solo para los formularios adaptables que generan automáticamente el documento de registro. Si utiliza un XDP personalizado para generar un documento de registro o un formulario adaptable basado en una plantilla de formulario, no es necesario el bloque Acrobat Sign.


1. Seleccione el **Bloque de Acrobat Sign** y toque el **Editar** ![aem_6_3_edit](assets/aem_6_3_edit.png) icono. Muestra las opciones para agregar campos y formatear la apariencia de un campo.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Seleccione y añada campos de Acrobat Sign . **B.** Expanda el bloque Acrobat Sign a la vista de pantalla completa

1. Toque . **Campo Acrobat Sign** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) icono. Muestra las opciones para seleccionar y añadir campos de Acrobat Sign.

   Expanda el **Tipo** campo desplegable para seleccionar un campo de Acrobat Sign y pulsar el botón Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para añadir el campo seleccionado al bloque de Acrobat Sign. La variable **Tipo** el campo desplegable incluye los tipos de campo Firma, Información del firmante y Datos. Integración de Acrobat Sign con los campos de asistencia de AEM Forms enumerados solo en el cuadro desplegable Tipo . Para obtener información detallada sobre los campos de Acrobat Sign, consulte [Documentación de Acrobat Sign](https://helpx.adobe.com/es/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   Es obligatorio proporcionar un nombre único para un campo. También puede seleccionar la opción necesaria para marcar un campo como obligatorio. Además del **Nombre** y **Requerido** , algunos campos de Acrobat Sign tienen más opciones. Por ejemplo, máscara y líneas múltiples. Además, especifique un nombre único para cada campo de Acrobat Sign, independientemente de si los campos residen en bloques de Acrobat Sign iguales o diferentes.

### Habilitar Acrobat Sign para un formulario adaptable {#enableadobsignforanadaptiveform}

De serie, Acrobat Sign no está habilitado para un formulario adaptable. Siga estos pasos para habilitarlo:

1. En el navegador de contenido, pulse **Contenedor de formulario** y haga clic en el icono **Configurar** ![configure](assets/configure.png). Se abrirá el explorador de propiedades, donde verá las propiedades del contenedor de formularios adaptables.
1. En el navegador de propiedades, expanda el **Firma electrónica** y seleccione el **Habilitar Acrobat Sign** . Habilita Acrobat Sign para un formulario adaptable.

### Seleccione el Cloud Service de Acrobat Sign y el orden de firma {#selectadobesigncloudserviceforanadaptiveform}

Puede configurar varios servicios de Acrobat Sign para una instancia de AEM Forms. Es aconsejable tener un conjunto de servicios separados para cada función (Recursos Humanos, Finanzas, etc.). Facilita el seguimiento y la creación de informes de documentos firmados. Por ejemplo, un banco tiene varios departamentos. Puede tener una configuración separada para cada departamento para realizar un mejor seguimiento de los documentos.

Un documento también puede tener varios firmantes. Por ejemplo, una solicitud de tarjeta de crédito puede tener varios solicitantes. Un banco requiere firmas de todos los solicitantes antes de iniciar la solicitud de procesamiento. En el caso de los casos de multifirmante, puede seleccionar firmar el documento en orden secuencial o simultáneo.

Siga estos pasos para seleccionar un servicio en la nube y el orden de firma:

![cloud-service](assets/cloud-service.png)

1. En el navegador de contenido, pulse **Contenedor de formulario** y haga clic en el icono **Configurar** ![configure](assets/configure.png). Se abrirá el explorador de propiedades, donde verá las propiedades del contenedor de formularios adaptables.
1. En el navegador de propiedades, expanda el **Firma electrónica** y seleccione el **Habilitar Acrobat Sign** . Habilita Acrobat Sign para un formulario adaptable.
1. Seleccione un servicio de nube de la lista de Cloud Services de Acrobat Sign ya configurada.

   Si la variable **Cloud Service de Acrobat Sign** está vacía, siga la [Configuración de Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) Artículo para configurar el servicio.

   La lista desplegable muestra los servicios de nube que existen en la `global` carpeta en Herramientas > **[!UICONTROL Cloud Services]** > **[!UICONTROL Acrobat Sign]**. Además, la lista desplegable también enumera los servicios de nube que existen en la carpeta seleccionada en la **[!UICONTROL Contenedor de configuración]** al crear un formulario adaptable.

1. Seleccione el orden de firma de la lista **Los firmantes pueden firmar** para abrir el Navegador. Los cantantes de Acrobat Sign pueden firmar un formulario adaptable **Secuencialmente** - uno tras otro firmante, o **Simultáneamente** - en cualquier orden.

   En orden secuencial, un firmante recibe el formulario para firmar a la vez. Una vez que un firmante completa la firma del documento, el formulario se envía al siguiente firmante, etc.

   En orden simultáneo, varios firmantes pueden firmar un formulario a la vez.

1. [Agregar firmantes a un formulario adaptable](#addsignerstoanadaptiveform) y pulse el icono Listo para guardar los cambios.

### Agregar firmantes a un formulario adaptable {#addsignerstoanadaptiveform}

Solo se puede tener un firmante o varios firmantes para un formulario adaptable. Al agregar un firmante, también puede configurar los detalles de autenticación del firmante. También puede seleccionar si el usuario que rellena el formulario y el cantante son la misma persona. Realice los siguientes pasos para agregar y proporcionar varios detalles sobre un firmante:

1. En el navegador de contenido, pulse **Contenedor de formulario** y haga clic en el icono **Configurar** ![configure](assets/configure.png). Se abrirá el explorador de propiedades con las propiedades del contenedor de formularios adaptables.
1. En el navegador de propiedades, expanda el **Firma electrónica** y seleccione el **Habilitar Acrobat Sign** . Habilita Acrobat Sign para un formulario adaptable.
1. Toque **Agregar firmante** under **Configuración del firmante.** Agrega un firmante al formulario adaptable. Puede agregar varios firmantes de Acrobat Sign a un formulario adaptable.
1. ![phone-details](assets/phone-details.png)

   Haga clic en el **Editar** ![aem_6_3_edit](assets/aem_6_3_edit.png) para especificar la siguiente información sobre el firmante:

   * **Título:** Especifique un título para identificar de forma exclusiva a un firmante.
   * **¿Son iguales el firmante y la persona que rellena el formulario?:** Select **Sí**, si el usuario que rellena el formulario y el primer firmante son la misma persona. Si la opción está definida en **No,** a continuación, no utilice el componente paso de firma en el formulario adaptable. Si el formulario contiene un componente Paso de firma, el campo se establece automáticamente como Sí.
   * **Dirección de correo electrónico del firmante:** Especifique la dirección de correo electrónico del firmante. El firmante recibe los documentos o formularios firmados en la dirección de correo electrónico especificada. Puede elegir utilizar una dirección de correo electrónico proporcionada en un campo de formulario, en AEM perfil de usuario del usuario que ha iniciado sesión o escribir manualmente una dirección de correo electrónico. Es un paso obligatorio. Además, tenga en cuenta que si solo ha configurado un firmante, asegúrese de que la dirección de correo electrónico del firmante no sea idéntica a la cuenta de Acrobat Sign utilizada para configurar los servicios en la nube de AEM.
   * **Método de autenticación del firmante:** Especifique el método para autenticar a un usuario antes de abrir un formulario para firmar. Puede elegir entre teléfono, base de conocimientos y autenticación social basada en identidad.

   >[!NOTE]
   >
   >* De forma predeterminada, la autenticación basada en la identidad social proporciona una opción para autenticarse con Facebook, Google y LinkedIn. Puede ponerse en contacto con el servicio de asistencia técnica de Acrobat Sign para habilitar otros proveedores de autenticación social.


   * **Campos Acrobat Sign para rellenar o firmar:** Seleccione los campos de Acrobat Sign para el firmante. Un formulario adaptable puede tener varios campos de Acrobat Sign. Puede elegir habilitar campos específicos para un firmante. El campo muestra todos los bloques de Acrobat Sign disponibles. Al seleccionar un bloque, se seleccionan todos los campos del bloque. Puede utilizar el icono X para anular la selección de un campo.

   ![signer-details-1](assets/signer-details-1.png)

   La imagen anterior tiene dos ejemplos de bloques de Acrobat Sign: Información personal y detalles de Office

   Puntee en Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) icono. Se agrega y configura el firmante.

### Seleccione Enviar acción para un formulario adaptable {#selectsubmitactionforanadaptiveform}

Después de agregar los campos de Acrobat Sign a un formulario adaptable, activar Acrobat Sign desde el contenedor de formularios, seleccionar el Cloud Service de Acrobat Sign y agregar firmantes de Acrobat Sign, seleccionar una acción de envío adecuada para el formulario adaptable. Para obtener información detallada sobre las acciones de envío de formularios adaptables, consulte [Configuración de la acción Enviar](/help/forms/using/configuring-submit-actions.md).

Además, un formulario adaptable habilitado para Acrobat Sign solo se envía después de que todos los firmantes firmen el formulario. Puede encontrar formularios parcialmente firmados en la sección Firma pendiente del portal de formularios. El servicio de configuración de Acrobat Sign sigue sondeando el servidor de Acrobat Sign en [intervalos regulares](/help/forms/using/adobe-sign-integration-adaptive-forms.md) para verificar el estado de las firmas. Si todos los firmantes completan la firma del formulario, se inicia el servicio de acción de envío y se envía el formulario. Si utiliza una acción de envío personalizada y el formulario utiliza Acrobat Sign, actualice la acción de envío personalizada para utilizar el servicio de envío.

>[!NOTE]
>
>Los datos del formulario adaptable se almacenan temporalmente en Forms Portal. Se recomienda utilizar [almacenamiento personalizado para Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). Garantiza que los datos PII (información de identificación personal) no se almacenen en servidores AEM.

La experiencia de firma de formularios está lista. Puede obtener una vista previa del formulario para comprobar la experiencia de firma. En el formulario publicado, los campos Bloque de Acrobat Sign se muestran cuando un firmante recibe el formulario para firmar por correo electrónico. Esta experiencia también se conoce como experiencia de firma fuera de formulario. También puede configurar una experiencia de firma en el formulario para el primer firmante; para ver los pasos detallados, consulte [Crear experiencia de firma en formularios](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Configuración de firmas de nube para un formulario adaptable {#configure-cloud-signatures-for-an-adaptive-form}

Las firmas digitales o remotas basadas en la nube son una nueva generación de firmas digitales que funcionan en equipos de escritorio, dispositivos móviles y la web, y cumplen con los niveles más altos de cumplimiento y seguridad para la autenticación de firmantes. Puede firmar un formulario adaptable con firmas digitales basadas en la nube.

Después [edición de propiedades de formulario adaptables para Acrobat Sign](#enableadobesign), realice los siguientes pasos para agregar el campo de firma en la nube a un formulario adaptable:

1. Arrastrar y soltar **Bloque de Acrobat Sign** del navegador de componentes al formulario adaptable. El componente Bloque de Acrobat Sign tiene todos los campos de Acrobat Sign compatibles. De forma predeterminada, agrega un **Firma** al formulario adaptable.

   ![sign-block](assets/sign-block.png)

1. Seleccione el **Bloque de Acrobat Sign** y toque el **Editar** ![aem_6_3_edit](assets/aem_6_3_edit.png) icono. Muestra las opciones para agregar campos y formatear la apariencia de un campo.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Seleccione y añada campos de Acrobat Sign . **B.** Expanda el bloque Acrobat Sign a la vista de pantalla completa

1. Toque . **Campo Acrobat Sign** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) icono. Muestra las opciones para seleccionar y añadir campos de Acrobat Sign.

   Expanda el **Tipo** campo desplegable que desea seleccionar **Firma digital** y pulse Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para añadir el campo seleccionado al bloque de Acrobat Sign.

   ![digital_signatures](assets/digital_signatures.png)

   Es obligatorio proporcionar un nombre único para un campo.

   Aplique firmas digitales al formulario adaptable utilizando:

   * Firmas en la nube: firme con un [ID digital](https://helpx.adobe.com/es/sign/kb/digital-certificate-providers.html) alojado por un proveedor de servicios de confianza.
   * Adobe Acrobat o Reader: descargue y abra el documento con Adobe Acrobat o Reader para firmarlo con una tarjeta inteligente, un token USB o un ID digital basado en archivos.

   Después de agregar el campo de firma de nube al formulario adaptable, realice los siguientes pasos para completar el proceso de configuración:

   * [Habilitar Acrobat Sign para un formulario adaptable](#enableadobsignforanadaptiveform)
   * [Seleccione el Cloud Service de Acrobat Sign para un formulario adaptable](#selectadobesigncloudserviceforanadaptiveform)
   * [Agregar firmantes de Acrobat Sign a un formulario adaptable](#addsignerstoanadaptiveform)
   * [Seleccione Enviar acción para un formulario adaptable](#selectsubmitactionforanadaptiveform)


## Crear experiencia de firma en formularios {#create-in-form-signing-experience}

Un usuario también puede firmar un formulario adaptable mientras lo rellena. Esta experiencia también se conoce como experiencia de firma en formularios. La experiencia de firma en el formulario solo está disponible para el primer cantante en un entorno de varios firmantes. Siga estos pasos para crear una experiencia de firma en formularios para un formulario adaptable:

1. [Añadir y configurar el componente Paso de firma](#add-and-configure-the-signature-step-component).
1. [Añadir el componente Paso de resumen](#configure-the-thank-you-page-or-summary-step-component).

![in-form-signing-experience](assets/in-form-signing-experience.png)

### Añadir y configurar el componente Paso de firma {#add-and-configure-the-signature-step-component}

Utilice el componente Paso de firma para proporcionar un área donde firmar electrónicamente el formulario rellenado. Cuando se representa la sección que contiene el componente Paso de firma, muestra una versión PDF identificable del formulario rellenado. El componente Paso de firma ocupa el ancho completo disponible en el formulario. Se recomienda no colocar ningún otro componente en la sección que contiene el componente Paso de firma.

Realice los siguientes pasos para configurar el componente Paso de firma:

1. Arrastre y suelte la **Paso de firma** del explorador de componentes al formulario.
1. Seleccione el componente del paso Firma recién agregado y pulse el botón **Configurar** ![configure](assets/configure.png) icono. Se abrirá el explorador de propiedades, donde verá las propiedades del Paso de firma. Configure las siguientes propiedades:

   * **Nombre del elemento**: Especifique el nombre del componente.
   * **Título:** Especifique el título único del componente.
   * **Mensaje de plantilla:** especifique el mensaje que se mostrará mientras se carga el PDF de firma. Los servicios de Acrobat Sign tardan algún tiempo en preparar y cargar el PDF de firma.
   * **Servicio de firma:** Seleccione el **Acrobat Sign** .
   * **Uso del componente de firma electrónica heredado**: Si utiliza el formulario adaptable correspondiente en [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md), la aplicación de AEM Forms o el formulario adaptable subyacente tiene un componente de firma electrónica heredado, seleccione la opción **Uso del componente de firma electrónica heredado** .
   * **Configuración**: Seleccione una configuración (Cloud Service de Acrobat Sign). El cuadro desplegable solo está disponible si la variable **Uso del componente de firma electrónica heredado** está activada.

   Puntee en Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios.

   ![signature-step](assets/signature-step.png)

   >[!NOTE]
   >
   >* Cuando arrastra y suelta la variable **[!UICONTROL Paso de firma]** al formulario, la variable **[!UICONTROL ¿Son iguales el firmante y la persona que rellena el formulario?]** se configura automáticamente como **Sí**. Es necesario mantener el formulario en funcionamiento.
   >* Los formularios adaptables activados por Acrobat Sign no son compatibles con el uso del botón Enviar de la sección o panel que utiliza el componente Paso de firma. Puede añadir un paso de resumen después del paso Firma para el envío manual o después de activar un envío automático después del conjunto de intervalos utilizando el [Servicio de configuración de Acrobat Sign](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).


### Configurar la página de agradecimiento o el componente de paso de resumen {#configure-the-thank-you-page-or-summary-step-component}

El componente **Paso de resumen** envía automáticamente el formulario, rellena la información dentro de la página Resumen personalizada y muestra el resumen del formulario enviado. También obtiene la información necesaria en el mapa de retorno. El componente Paso de resumen ocupa el ancho completo disponible para el formulario. Se recomienda no tener ningún otro componente en la sección que contenga el componente Paso de resumen.

Ahora, la experiencia de firma de formularios en está lista. Puede obtener una vista previa del formulario para comprobar la experiencia de firma.

## Preguntas frecuentes {#frequently-asked-questions}

**P: Puede incrustar un formulario adaptable en otro formulario adaptable. ¿Puede habilitarse Acrobat Sign en el formulario adaptable incrustado?**

**Ans:** No, AEM Forms no admite el uso de un formulario adaptable que incruste un formulario adaptable habilitado para Acrobat Sign para firmar.

**P: Cuando creo un formulario adaptable utilizando la plantilla avanzada y lo abro para editarlo, aparece un mensaje de error &quot;Las firmas electrónicas o los firmantes no están correctamente configurados&quot;. . ¿Cómo se resuelve el mensaje de error?**

**Ans:** El formulario adaptable creado con la plantilla avanzada está configurado para utilizar Acrobat Sign. Para resolver el error, cree y seleccione una configuración de nube de Acrobat Sign y configure un firmante de Acrobat Sign para el formulario adaptable.

**P: ¿Puedo utilizar etiquetas de texto de Acrobat Sign en un componente de texto estático de un formulario adaptable?**

**Ans:** Sí, puede utilizar etiquetas de texto en un componente de texto para añadir campos de Acrobat Sign a un [Documento de registro](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) (Solo la opción de documento de registro generado automáticamente) se ha habilitado el formulario adaptable. Para obtener más información sobre el procedimiento y las reglas para crear una etiqueta de texto, consulte [Documentación de Acrobat Sign](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/advanced-tasks-admins/adobe-sign-text-tagging.html). Tenga en cuenta también que los formularios adaptables tienen una compatibilidad limitada con las etiquetas de texto. Puede utilizar las etiquetas de texto para crear solo los campos que admite Acrobat Sign Block.

**P: AEM Forms proporciona componentes de paso de bloque y firma de Acrobat Sign. ¿Se pueden utilizar simultáneamente en una forma adaptativa?**

**Ans:** Puede utilizar ambos componentes simultáneamente en un formulario. Estas son algunas recomendaciones para utilizar estos componentes:

**Bloque de Acrobat Sign:** Puede utilizar el bloque de Acrobat Sign para agregar campos de Acrobat Sign en cualquier parte del formulario adaptable. También ayuda a asignar campos específicos a los firmantes. De forma predeterminada, cuando un formulario adaptable se previsualiza o se publica, Acrobat Sign Block no está visible. Estos bloques solo están habilitados en el documento de firma. En el documento de firma, solo se activan los campos asignados a un firmante. El bloque Acrobat Sign se puede utilizar con los firmantes primero y siguientes.

**Componente del paso de firma:** Puede utilizar el componente paso de firma para crear una experiencia de firma en el formulario. Solo permite que el primer firmante firme mientras se rellena el formulario. Cuando se representa la sección que contiene el componente Paso de firma, muestra una versión del formulario con PDF que se puede firmar. Generalmente es la última o la penúltima sección seguida del componente de resumen de un formulario.
