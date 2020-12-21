---
title: Usar plantillas de correo electrónico personalizadas en un paso Asignar Tarea
seo-title: Usar plantillas de correo electrónico personalizadas en un paso Asignar Tarea
description: 'Plantillas de correo electrónico personalizadas para notificaciones de correo electrónico del flujo de trabajo de formularios '
seo-description: 'Plantillas de correo electrónico personalizadas para notificaciones de correo electrónico del flujo de trabajo de formularios '
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
translation-type: tm+mt
source-git-commit: 8b5a3e1f6616c3a07da91e4347596961ac4a8e22
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Utilice plantillas de correo electrónico personalizadas en un paso Asignar Tarea {#use-custom-email-templates-in-an-assign-task-step}

Plantillas de correo electrónico personalizadas para notificaciones de correo electrónico del flujo de trabajo de formularios

Puede utilizar el paso Asignar Tarea para crear y asignar tareas a un usuario o grupo. Cuando se asigna una tarea a un usuario o grupo, se envía una notificación por correo electrónico al usuario definido o a cada miembro del grupo definido. Una notificación típica por correo electrónico contiene un vínculo de la tarea asignada e información relacionada con la tarea. La siguiente imagen muestra una notificación por correo electrónico de muestra:

![Notificación por correo electrónico sin plantilla predeterminada](do-not-localize/default-email-template.png)

Puede personalizar el aspecto y utilizar metadatos personalizados en una notificación por correo electrónico. AEM Forms proporciona una plantilla lista para usar para las notificaciones por correo electrónico. Puede personalizar la plantilla lista para usar o crear una nueva plantilla desde cero.

Las plantillas de notificación de correo electrónico se basan en [correo electrónico HTML](https://en.wikipedia.org/wiki/HTML_email). Estos correos electrónicos se adaptan a diferentes clientes de correo electrónico y tamaños de pantalla. Además, el estilo del correo electrónico se define en la plantilla.

La siguiente imagen muestra una notificación de correo electrónico personalizada:

![Notificación por correo electrónico con plantilla personalizada](do-not-localize/customized-email.png)

## Personalizar la plantilla existente {#customize-the-existing-template}

De forma predeterminada, AEM Forms proporciona una plantilla para las notificaciones por correo electrónico. La plantilla proporciona la descripción del título, la fecha de vencimiento, la prioridad, el nombre del flujo de trabajo y el vínculo de la tarea asignada. Puede personalizar la plantilla para cambiar el aspecto. Siga estos pasos para personalizar la plantilla:

1. Inicie sesión en CRXDE con la cuenta de administrador.

1. Vaya a /libs/fd/panel/templates/email.

1. Abra el archivo htmlEmailTemplate.txt. Contiene la plantilla predeterminada.

1. Reemplace el contenido del archivo htmlEmailTemplate.txt con contenido personalizado.

   Una plantilla de notificación de correo electrónico es un [correo electrónico HTML](https://en.wikipedia.org/wiki/HTML_email). Puede reemplazar el código HTML existente por el código personalizado para cambiar el aspecto de la plantilla.

1. Guarde el archivo. Ahora, la plantilla personalizada está lista para su uso.

## Crear una plantilla de correo electrónico {#create-an-email-template}

De forma predeterminada, AEM Forms proporciona una plantilla para las notificaciones por correo electrónico. La plantilla proporciona la descripción del título, la fecha de vencimiento, la prioridad, el nombre del flujo de trabajo y el vínculo de la tarea asignada. También puede agregar una plantilla de correo electrónico personalizada (su propia plantilla) para asignar pasos de tarea. Siga estos pasos para agregar una plantilla de correo electrónico personalizada:

1. Inicie sesión en CRXDE con la cuenta de administrador.

1. Vaya a /libs/fd/panel/templates/email.

1. Cree un archivo .txt. Por ejemplo, EmailOnTaskAsignar.txt.

1. Añada el código HTML personalizado en el archivo.

   Una plantilla de notificación de correo electrónico es un [correo electrónico HTML](https://en.wikipedia.org/wiki/HTML_email). Puede agregar código HTML personalizado al archivo para crear una nueva plantilla.

1. Guarde el archivo. La plantilla está lista para utilizarse en el paso Asignar Tarea.

## Usar una plantilla de correo electrónico en un paso Asignar Tarea {#use-an-email-template-in-an-assign-task-step}

De forma predeterminada, el paso Asignar tarea está configurado para utilizar la plantilla predeterminada, htmlEmailTemplate.txt. Puede elegir utilizar una plantilla personalizada. Para cambiar la plantilla:

1. Abra el paso **[!UICONTROL Asignar Tarea]**.

1. Vaya a **[!UICONTROL Usuario asignado > Plantilla de correo electrónico HTML]**.

1. Seleccione la plantilla de correo electrónico HTML recién creada.

1. Haga clic en **[!UICONTROL Aceptar]**. Se cambia la plantilla.

Una notificación por correo electrónico también utiliza [metadatos](/help/forms/using/use-metadata-in-email-notifications.md). Por ejemplo, fecha de vencimiento, prioridad, nombre del flujo de trabajo, etc. También puede configurar la plantilla para que utilice [metadatos personalizados](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification).
