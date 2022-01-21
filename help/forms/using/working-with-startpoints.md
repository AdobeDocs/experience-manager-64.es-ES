---
title: Uso de puntos de inicio
seo-title: Working with Startpoints
description: Pasos para trabajar con un proceso AEM Forms desde su dispositivo móvil definido en Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: 977ada5fefe476c7cd2fe1470eb024a517a681d2
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Uso de puntos de inicio {#working-with-startpoints}

Un punto de inicio invoca un proceso creado en Workbench. Está asociado a un formulario que invoca el proceso cuando se envía el formulario. Consulte [Recorrido por el sitio web de referencia de Geometrixx Finance](/help/forms/using/finance-reference-site-walkthrough.md) para comprender los procesos.

>[!NOTE]
>
>Los puntos de inicio, el proceso de inicio y el formulario de los términos se utilizan de forma intercambiable al hacer referencia a este concepto.

Para iniciar un proceso desde la aplicación de AEM Forms, debe tener un punto de inicio de tipo **Espacio de trabajo** en su proceso. Además, debe seleccionar la variable **[!UICONTROL Visible en Mobile Workspace]** para el punto de inicio.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Inicio de un proceso definido en Workbench**

1. Para ver los puntos de inicio disponibles en la aplicación de AEM Forms, vaya a [Pantalla principal](/help/forms/using/home-screen.md).
1. En el **[!UICONTROL Página principal]** de forma predeterminada, la variable **[!UICONTROL Todas las Forms]** se muestra.

   El punto de inicio está asociado a un formulario. Pulse el formulario asociado de punto de inicio en la lista para abrirlo.

   Se abre el formulario asociado al punto de inicio.

1. Introduzca los detalles en la **[!UICONTROL Punto de inicio]** formulario.

   Puede añadir anotaciones a esta tarea utilizando el [archivo](/help/forms/using/add-attachments.md) botón.

1. Después de rellenar el formulario, pulse la tecla **Submit** botón.

Si la aplicación está sin conexión, el formulario y sus datos se guardan en la carpeta Bandeja de salida.

Si la aplicación está en línea, la tarea se sincroniza con el servidor de AEM Forms y se asigna al usuario especificado en el proceso.

Para trabajar con la tarea en la lista de tareas, consulte [Apertura de una tarea](/help/forms/using/open-task.md).
