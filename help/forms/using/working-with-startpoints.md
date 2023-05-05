---
title: Trabajar con puntos de inicio
seo-title: Working with Startpoints
description: Pasos para trabajar con un proceso de AEM Forms desde su dispositivo móvil definido en Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 81%

---

# Trabajar con puntos de inicio {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Un punto de inicio invoca un proceso creado en Workbench. Está asociado a un formulario que invoca el proceso cuando se envía el formulario. Consulte [Recorrido por el sitio web de referencia de Geometrixx Finance](/help/forms/using/finance-reference-site-walkthrough.md) para comprender los procesos.

>[!NOTE]
>
>Los puntos de inicio, el proceso de inicio y el formulario de los términos se utilizan de forma intercambiable al hacer referencia a este concepto.

Para iniciar un proceso desde la aplicación de AEM Forms, debe tener un punto de inicio de tipo **Espacio de trabajo** en su proceso. Además, debe seleccionar la variable **[!UICONTROL Visible en Mobile Workspace]** para el punto de inicio.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Para iniciar un proceso definido en Workbench**

1. Para ver los puntos de inicio disponibles en la aplicación de AEM Forms, vaya a la [Pantalla de inicio](/help/forms/using/home-screen.md).
1. En la pantalla **[!UICONTROL Inicio]**, de forma predeterminada, se muestra la lista **[!UICONTROL Todos los formularios]**.

   El punto de inicio está asociado a un formulario. Pulse el formulario asociado al punto de inicio en la lista para abrirlo.

   Se abre el formulario asociado al punto de inicio.

1. Introduzca los detalles en el formulario **[!UICONTROL Punto de inicio]**.

   Puede agregar anotaciones a esta tarea con el botón [Archivo adjunto](/help/forms/using/add-attachments.md).

1. Después de rellenar el formulario, pulse el botón **Enviar**.

Si la aplicación está sin conexión, el formulario y sus datos se guardan en la carpeta Bandeja de salida.

Si la aplicación está en línea, la tarea se sincroniza con el servidor de AEM Forms y se asigna al usuario especificado en el proceso.

Para trabajar con la tarea en la lista de tareas, consulte [Abrir una tarea](/help/forms/using/open-task.md).
