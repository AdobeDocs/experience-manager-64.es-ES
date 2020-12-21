---
title: Personalización de fichas para una tarea
seo-title: Personalización de fichas para una tarea
description: Cómo personalizar los nombres de las fichas de sus tareas, en el espacio de trabajo de LiveCycle AEM Forms.
seo-description: Cómo personalizar los nombres de las fichas de sus tareas, en el espacio de trabajo de LiveCycle AEM Forms.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Personalización de fichas para una tarea {#customizing-tabs-for-a-task}

Puede personalizar los nombres de fichas para el componente `Start Process` en la vista `Start Process` Uber y el componente `Task Details` en la vista `ToDo` Uber.

1. Siga los [pasos genéricos para la personalización del espacio de trabajo de AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Cambie el valor de `tabname`en el archivo `translation.json`.

   Por ejemplo, cambie `/apps/ws/locales/en-US/translation.json` para inglés por el siguiente.

   * Para tareas iniciadas en el proceso de inicio, utilice el siguiente fragmento del bloque `"startprocess" : {}`.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Para tareas en Tareas pendientes, utilice el siguiente fragmento del bloque `"todo" : {}`.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Añada el par clave-valor correspondiente para todos los idiomas admitidos.
