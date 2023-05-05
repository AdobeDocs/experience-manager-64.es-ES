---
title: Enviar una confirmación de envío de formulario por correo electrónico
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms permite configurar una acción de envío por correo electrónico que envía una confirmación a un usuario al enviar el formulario.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 44%

---

# Enviar una confirmación de envío de formulario por correo electrónico {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Envío de datos de formularios adaptables {#adaptive-form-data-submission}

Los formularios adaptables proporcionan varios flujos de trabajo de [acciones de envío](/help/forms/using/configuring-submit-actions.md) predeterminados para enviar los datos del formulario a diferentes extremos.

Por ejemplo, la variable **Acción de correo electrónico** la acción enviar envía un correo electrónico cuando se envía correctamente un formulario adaptable. También se puede configurar el envío de los datos del formulario y el PDF en el correo electrónico.

Este artículo detalla los pasos para habilitar la acción Enviar por correo electrónico en un formulario adaptable y las diferentes configuraciones que proporciona.

>[!NOTE]
>
>También puede usar la variable **Acción del PDF de correo electrónico** para enviar el formulario completado por correo electrónico como archivo adjunto de PDF. Las opciones de configuración disponibles para esta acción son las mismas que las opciones disponibles para la acción Correo electrónico . La acción Enviar PDF por correo electrónico solo está disponible para formularios adaptables basados en XFA.

## Acción de correo electrónico {#email-action}

La acción Correo electrónico permite a un autor enviar correos electrónicos automáticamente a uno o varios destinatarios cuando se envía correctamente un formulario adaptable.

>[!NOTE]
>
>Para utilizar la acción Correo electrónico , debe configurar el servicio de correo AEM como se describe en [Configuración del servicio de correo](/help/sites-administering/notification.md#configuring-the-mail-service).

### Activación de la acción Correo electrónico en un formulario adaptable {#enabling-email-action-on-an-adaptive-form}

1. Abra un formulario adaptable en modo Edición.

1. Haga clic en **Editar** junto a la variable **Inicio de un formulario adaptable** barra de herramientas.

   Se abrirá el cuadro de diálogo Editar componente .

   ![Cuadro de diálogo Editar componente para un formulario adaptable](assets/start_of_adp_form.png)

1. Seleccione el **Enviar acciones** y elija **Acción de correo electrónico** en la lista desplegable Acción de envío .

   La pestaña muestra las opciones para configurar la acción Correo electrónico del formulario actual.

   ![Ficha Enviar acciones](assets/dialog.png)

1. Especifique ID de correo electrónico válidos en los campos Mailto, CC y BCC.

   Especifique el asunto y el cuerpo del correo electrónico en los campos Subject y Email template , respectivamente.

   También puede especificar marcadores de posición de variables en los campos, en cuyo caso, los valores de los campos se procesarán cuando un usuario final envíe correctamente el formulario. Para obtener más información, consulte [Uso de nombres de campos de formulario adaptables para crear contenido de correo electrónico de forma dinámica](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Seleccione Incluir datos adjuntos si el formulario incluye archivos adjuntos y desea adjuntarlos al correo electrónico.

   >[!NOTE]
   >
   >Si elige la opción **Acción del PDF de correo electrónico**, debe seleccionar la opción Include attachment .

1. Haga clic en **OK** para guardar los cambios.

### Usar nombres de campo de formulario adaptable para crear contenido de correo electrónico de forma dinámica {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Los nombres de campo de un formulario adaptable se denominan marcadores de posición, y se reemplazan por el valor de ese campo una vez que un usuario envía el formulario.

En la pestaña Email action , puede utilizar marcadores de posición que se procesan cuando se realiza la acción. Esto implica que los encabezados del correo electrónico (como Mailto, CC, BCC, subject) se generan cuando el usuario envía el formulario.

Para definir un marcador de posición, especifique `${<field name>}` en un campo de la ficha Enviar acciones .

Por ejemplo, si el formulario contiene la variable **Dirección de correo electrónico** campo, con nombre `email_addr`, para capturar el ID de correo electrónico de un usuario, puede especificar lo siguiente en los campos Mailto, CC o BCC.

`${email_addr}`

Cuando un usuario envía el formulario, se envía un correo electrónico al ID de correo electrónico introducido en el campo `email_addr` del formulario.

>[!NOTE]
>
>Puede encontrar el nombre de un campo en el cuadro de diálogo **Editar** del campo.

Los marcadores de posición de variables también se pueden usar en la variable **Asunto** y **Plantilla de correo electrónico** campos.

Por ejemplo:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Los campos de los paneles repetibles no se pueden usar como marcadores de posición variables.
