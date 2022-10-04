---
title: Uso de plantillas de correo electrónico personalizadas en un paso Asignar tarea
seo-title: Use custom email templates in an Assign Task step
description: Plantillas de correo electrónico personalizadas para notificaciones de correo electrónico de flujo de trabajo de formularios
seo-description: Custom email templates for forms workflow email notifications
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 4%

---

# Uso de plantillas de correo electrónico personalizadas en un paso Asignar tarea {#use-custom-email-templates-in-an-assign-task-step}

Plantillas de correo electrónico personalizadas para notificaciones de correo electrónico de flujo de trabajo de formularios

Puede utilizar el paso Asignar tarea para crear y asignar tareas a un usuario o grupo. Cuando se asigna una tarea a un usuario o grupo, se envía una notificación por correo electrónico al usuario definido o a cada miembro del grupo definido. Una notificación típica por correo electrónico contiene un vínculo de la tarea asignada y una información relacionada con la tarea. La siguiente imagen muestra un ejemplo de notificación por correo electrónico:

![Notificación por correo electrónico con plantilla predeterminada](do-not-localize/default-email-template.png)

Puede personalizar el aspecto y utilizar metadatos personalizados en una notificación por correo electrónico. AEM Forms proporciona una plantilla predeterminada para las notificaciones por correo electrónico. Puede personalizar la plantilla predeterminada o crear una nueva desde cero.

Las plantillas de notificación de correo electrónico se basan en [correo electrónico del HTML](https://es.wikipedia.org/wiki/Correo_HTML). Estos correos electrónicos se adaptan a diferentes clientes de correo electrónico y tamaños de pantalla. Además, el estilo del correo electrónico se define dentro de la plantilla.

La siguiente imagen muestra una notificación por correo electrónico personalizada:

![Notificación por correo electrónico con plantilla personalizada](do-not-localize/customized-email.png)

## Personalización de la plantilla existente {#customize-the-existing-template}

De forma predeterminada, AEM Forms proporciona una plantilla para las notificaciones por correo electrónico. La plantilla proporciona la descripción del título, la fecha de vencimiento, la prioridad, el nombre del flujo de trabajo y el vínculo de la tarea asignada. Puede personalizar la plantilla para cambiar el aspecto. Siga estos pasos para personalizar la plantilla:

1. Inicie sesión en CRXDE con cuenta de administrador.

1. Vaya a /libs/fd/dashboard/templates/email.

1. Abra el archivo htmlEmailTemplate.txt . Contiene la plantilla predeterminada.

1. Reemplace el contenido del archivo htmlEmailTemplate.txt por contenido personalizado.

   Una plantilla de notificación de correo electrónico es una [correo electrónico del HTML](https://en.wikipedia.org/wiki/HTML_email). Puede reemplazar el código HTML existente con el código personalizado para cambiar el aspecto de la plantilla.

1. Guarde el archivo. Ahora, la plantilla personalizada está lista para su uso.

## Creación de una plantilla de correo electrónico {#create-an-email-template}

De forma predeterminada, AEM Forms proporciona una plantilla para las notificaciones por correo electrónico. La plantilla proporciona la descripción del título, la fecha de vencimiento, la prioridad, el nombre del flujo de trabajo y el vínculo de la tarea asignada. También puede añadir una plantilla de correo electrónico personalizada (su propia plantilla) para los pasos de asignación de tareas. Siga estos pasos para agregar una plantilla de correo electrónico personalizada:

1. Inicie sesión en CRXDE con cuenta de administrador.

1. Vaya a /libs/fd/dashboard/templates/email.

1. Cree un archivo .txt. Por ejemplo, EmailOnTaskAssign.txt.

1. Agregue código de HTML personalizado al archivo .

   Una plantilla de notificación de correo electrónico es una [correo electrónico del HTML](https://en.wikipedia.org/wiki/HTML_email). Puede agregar código de HTML personalizado al archivo para crear una plantilla nueva.

1. Guarde el archivo. La plantilla está lista para utilizarse en el paso Asignar tarea .

## Uso de una plantilla de correo electrónico en un paso Asignar tarea {#use-an-email-template-in-an-assign-task-step}

De forma predeterminada, el paso Asignar tarea está configurado para utilizar la plantilla predeterminada, htmlEmailTemplate.txt. Puede elegir utilizar una plantilla personalizada. Para cambiar la plantilla:

1. Abra el **[!UICONTROL Asignar tarea]** paso a paso.

1. Vaya a **[!UICONTROL Usuario asignado > Plantilla de correo electrónico del HTML]**.

1. Seleccione la plantilla de correo electrónico del HTML recién creada.

1. Haga clic en **[!UICONTROL Aceptar]**. La plantilla se cambia.

Una notificación por correo electrónico también utiliza [metadata](/help/forms/using/use-metadata-in-email-notifications.md). Por ejemplo, fecha de vencimiento, prioridad, nombre del flujo de trabajo, etc. También puede configurar la plantilla para usar [metadatos personalizados](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification).
