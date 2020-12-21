---
title: Envío de un acuse de recibo de envío de formulario por correo electrónico
seo-title: Envío de un acuse de recibo de envío de formulario por correo electrónico
description: AEM Forms permite configurar la acción de envío por correo electrónico que envía una confirmación a un usuario al enviar el formulario.
seo-description: AEM Forms permite configurar la acción de envío por correo electrónico que envía una confirmación a un usuario al enviar el formulario.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---


# Envío de confirmación de envío de formulario por correo electrónico {#sending-a-form-submission-acknowledgement-via-email}

## Envío de datos de formulario adaptable {#adaptive-form-data-submission}

Los formularios adaptables proporcionan varios flujos de trabajo predeterminados [acciones de envío](/help/forms/using/configuring-submit-actions.md) para enviar los datos del formulario a diferentes extremos.

Por ejemplo, la acción de envío **acción de correo electrónico** envía un mensaje de correo electrónico cuando se envía correctamente un formulario adaptable. También se puede configurar para enviar los datos del formulario y el PDF en el correo electrónico.

Este artículo detalla los pasos para habilitar la acción Correo electrónico en un formulario adaptable y las diferentes configuraciones que proporciona.

>[!NOTE]
>
>También puede utilizar la acción **Enviar archivo PDF por correo electrónico** para enviar el formulario completado por correo electrónico como archivo adjunto en PDF. Las opciones de configuración disponibles para esta acción son las mismas que las opciones disponibles para la acción Correo electrónico. La acción Enviar un PDF por correo electrónico solo está disponible para formularios adaptables basados en XFA

## Acción por correo electrónico {#email-action}

La acción Correo electrónico permite a un autor enviar correos electrónicos automáticamente a uno o varios destinatarios cuando se envía correctamente un formulario adaptable.

>[!NOTE]
>
>Para utilizar la acción Correo electrónico, debe configurar el servicio de correo AEM como se describe en [Configuración del servicio de correo](/help/sites-administering/notification.md#configuring-the-mail-service).

### Activación de la acción de correo electrónico en un formulario adaptable {#enabling-email-action-on-an-adaptive-form}

1. Abra un formulario adaptable en modo de edición.

1. Haga clic en **Editar** junto al Inicio **de una barra de herramientas Formulario adaptable**.

   Se abre el cuadro de diálogo Editar componente.

   ![Cuadro de diálogo Editar componente para un formulario adaptable](assets/start_of_adp_form.png)

1. Seleccione la ficha **Enviar acciones** y elija **Acción por correo electrónico** en la lista desplegable de acción Enviar.

   La ficha muestra las opciones para configurar la acción Correo electrónico del formulario actual.

   ![Ficha Enviar acciones](assets/dialog.png)

1. Especifique ID de correo electrónico válidos en los campos Mailto, CC y BCC.

   Especifique el asunto y el cuerpo del correo electrónico en los campos de plantilla Asunto y Correo electrónico, respectivamente.

   También puede especificar marcadores de posición de variables en los campos, en cuyo caso, los valores de los campos se procesan cuando un usuario final envía correctamente el formulario. Para obtener más información, consulte [Uso de nombres de campo de formulario adaptables para crear dinámicamente contenido de correo electrónico](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Seleccione Incluir archivos adjuntos si el formulario incluye archivos adjuntos y desea adjuntarlos en el correo electrónico.

   >[!NOTE]
   >
   >Si elige la acción **Enviar archivo PDF**, debe seleccionar la opción Incluir archivos adjuntos.

1. Haga clic en **Aceptar** para guardar los cambios.

### Uso de nombres de campo de formulario adaptables para crear dinámicamente contenido de correo electrónico {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Los nombres de campo de un formulario adaptable se denominan marcadores de posición que se sustituyen por el valor de dicho campo después de que un usuario envía el formulario.

En la ficha de acción Correo electrónico, puede utilizar marcadores de posición que se procesan cuando se realiza la acción. Significa que los encabezados del correo electrónico (como Mailto, CC, BCC, subject) se generan cuando el usuario envía el formulario.

Para definir un marcador de posición, especifique `${<field name>}` en un campo de la ficha Enviar acciones.

Por ejemplo, si el formulario contiene el campo **Dirección de correo electrónico**, denominado `email_addr`, para capturar el ID de correo electrónico de un usuario, puede especificar lo siguiente en los campos Mailto, CC o BCC.

`${email_addr}`

Cuando un usuario envía el formulario, se envía un correo electrónico al ID de correo electrónico introducido en el campo `email_addr` del formulario.

>[!NOTE]
>
>Puede encontrar el nombre de un campo en el cuadro de diálogo **Editar** del campo.

Los marcadores de posición de variables también se pueden utilizar en los campos **Subject** y **Email template**.

Por ejemplo:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Los campos de los paneles repetitivos no se pueden usar como marcadores de posición de variables.

