---
title: Visualizar datos adicionales en la lista de tareas pendientes
seo-title: Displaying additional data in ToDo list
description: Personalización de la visualización de la lista Tareas pendientes de AEM Forms Workspace de LiveCycle para mostrar más información además de la predeterminada.
seo-description: How-to customize the display of the To-do list of LiveCycle AEM Forms workspace to show more information besides the default.
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
exl-id: 42d8472d-0eab-4cf9-a7c3-bf2775ee6bec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 91%

---

# Visualizar datos adicionales en la lista de tareas pendientes {#displaying-additional-data-in-todo-list}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

De forma predeterminada, la lista Tareas pendientes de AEM Forms Workspace muestra el nombre y la descripción de la tarea. Sin embargo, puede agregar otra información, como la fecha de creación o la fecha límite. También puede agregar iconos y cambiar el estilo de la pantalla.

![Un vistazo a la pestaña Tareas pendientes del espacio de trabajo HTML que muestra la configuración predeterminada](assets/html-todo-list.png)

Este artículo detalla los pasos para agregar información para mostrar para cada tarea en la lista Tareas pendientes.

## Qué se puede agregar {#what-can-be-added}

Puede agregar la información disponible en `task.json` enviada por el servidor. La información se puede agregar como texto sin formato o puede utilizar estilos para dar formato a la información.

Para obtener más información sobre la descripción del objeto JSON, consulte [este](/help/forms/using/html-workspace-json-object-description.md) artículo.

## Visualizar información sobre una tarea {#displaying-information-on-a-task}

1. Siga los [Pasos genéricos para personalizar AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Para mostrar información adicional para una tarea, se deben agregar los pares clave-valor correspondientes dentro del bloque de tareas de `translation.json`.

   Por ejemplo, cambiar `/apps/ws/locales/en-US/translation.json` a inglés:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Agregar los pares clave-valor correspondientes para todos los idiomas compatibles.

1. Por ejemplo, agregar información dentro del bloque de tareas:

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## Definir CSS para la propiedad nueva {#defining-css-for-the-new-property}

1. Puede aplicar un estilo a la información (propiedad) agregada a una tarea. Para ello, debe agregar información del estilo para la propiedad agregada nueva a `/apps/ws/css/newStyle.css`.

   Por ejemplo, agregue:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Agregar una entrada en la plantilla HTML {#adding-entry-in-the-html-template}

Finalmente, debe incluir una entrada en el paquete dev para cada propiedad que desee agregar a la tarea. Para crear una, consulte Crear el código de AEM Forms Workspace.

1. Copiar `task.html`:

   * de: `/libs/ws/js/runtime/templates/`
   * hasta: `/apps/ws/js/runtime/templates/`

1. Agregue la información nueva a `/apps/ws/js/runtime/templates/task.html`.

   Por ejemplo, agréguela debajo de `div class="taskProperties"`:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
