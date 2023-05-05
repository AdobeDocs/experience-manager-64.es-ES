---
title: Pantalla principal
seo-title: Home screen
description: Descripción de los componentes de la pantalla Inicio de la aplicación AEM Forms
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 90%

---

# Pantalla principal {#home-screen}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Al iniciar sesión en la aplicación AEM Forms, se le redirige a la pantalla Inicio.

## Pantalla Inicio predeterminada {#default-home-screen}

De forma predeterminada, la pantalla Inicio muestra todos los formularios, incluidos los puntos de inicio y las tareas (si el servidor conectado está habilitado para AEM Forms Workflow), junto con las miniaturas asociadas. Puede especificar las miniaturas en el servidor de AEM Forms.

La siguiente figura muestra anotaciones con llamadas a los componentes esenciales en la pantalla Inicio predeterminada.
![Pantalla de inicio de la aplicación Forms](assets/home-screen-1.png)
[Haga clic para ampliar](assets/home-screen-1-1.png)

1. **Botón Menú**: pulse el botón **Menú** para ir a Tareas, Forms, Bandeja de salida y Configuración. Si la aplicación AEM Forms está conectada a un servidor de AEM Forms JEE, puede ver la opción Tareas. La opción Tareas también almacena los borradores creados a partir de las tareas de un proceso. En los servidores OSGi de AEM Forms, la opción Tareas está oculta. La Bandeja de salida almacena los formularios y los borradores guardados antes de sincronizarse con el servidor. Todos los formularios y borradores guardados en la Bandeja de salida se cargan en el servidor de AEM Forms cuando la aplicación [se sincroniza con el servidor](/help/forms/using/sync-app.md). Para obtener información sobre la configuración, consulte [Actualización de la configuración general](/help/forms/using/update-general-settings.md).
1. **Tarea o formulario**: pulse la tarea o el formulario de la lista con los que desea trabajar.
1. **Puntos suspensivos horizontales**: indican que hay acciones disponibles en el formulario. Al pulsar los puntos suspensivos, se muestran las acciones y la descripción que ha proporcionado el autor. Las opciones **Eliminar borrador** y **Completar** se muestran al pulsar los puntos suspensivos.
1. **Icono Actualizar**: pulse el icono Actualizar para sincronizar la aplicación con el servidor de AEM Forms.

## Personalización de la pantalla Inicio {#customizing-the-home-screen}

![Configuración general](assets/gen-settings.png)

Puede cambiar la pantalla Inicio predeterminada de la aplicación desde la **[Configuración general](/help/forms/using/update-general-settings.md)** de la aplicación o desde la pestaña **Preferencia** de HTML Workspace.

Los cambios realizados en la configuración de la pantalla Inicio de la aplicación afectan a la pantalla Inicio del usuario que ha iniciado sesión o el usuario que utiliza el dispositivo móvil actual.

Sin embargo, los cambios realizado en HTML Workspace afectan a todos los usuarios de la aplicación de AEM Forms que han iniciado sesión en el servidor de AEM Forms.
