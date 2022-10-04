---
title: Pantalla principal
seo-title: Home screen
description: Descripción de los componentes de la pantalla principal de la aplicación AEM Forms
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Pantalla principal {#home-screen}

Al iniciar sesión en la aplicación de AEM Forms, se le redirige a la pantalla principal.

## Pantalla principal predeterminada {#default-home-screen}

De forma predeterminada, la pantalla Inicio muestra todos los formularios, incluidos los puntos de inicio y las tareas (si el servidor conectado está habilitado para AEM Forms Workflow), junto con las miniaturas asociadas. Puede especificar las miniaturas en el servidor de AEM Forms.

La siguiente figura está anotada con llamadas a los componentes esenciales en la pantalla principal predeterminada.
![Pantalla de inicio de la aplicación Forms](assets/home-screen-1.png)
[Haga clic para ampliar](assets/home-screen-1-1.png)

1. **Botón Menú**: Toque . **Menú** para ir a Tareas, Forms, Bandeja de salida y Configuración. Si la aplicación de AEM Forms está conectada a un servidor JEE de AEM Forms, puede ver la opción Tareas . La opción Tareas también almacena los borradores creados a partir de tareas en un proceso. Para los servidores OSGi de AEM Forms, la opción Tareas está oculta. La bandeja de salida almacena los formularios guardados y borradores antes de que se sincronice con el servidor. Todos los formularios y borradores guardados en la bandeja de salida se cargan en el servidor de AEM Forms cuando la aplicación [sincronizada con el servidor](/help/forms/using/sync-app.md). Para obtener información sobre la configuración, consulte [Actualizar configuración general](/help/forms/using/update-general-settings.md).
1. **Tarea o formulario**: Pulse la tarea o el formulario de la lista con los que desee trabajar.
1. **Elipsis horizontal**: Indica que hay acciones disponibles para el formulario. Al tocar los puntos suspensivos, se muestran las acciones y la descripción que ha proporcionado el autor. La variable **Eliminar borrador** y **Completar** está visible al tocar los puntos suspensivos.
1. **Actualizar icono**: Pulse el icono de actualización para sincronizar la aplicación con el servidor de AEM Forms.

## Personalización de la pantalla principal {#customizing-the-home-screen}

![Configuración general](assets/gen-settings.png)

Puede cambiar la pantalla principal predeterminada de la aplicación desde la **[Configuración general](/help/forms/using/update-general-settings.md)** de la aplicación o de la **Preferencia** en HTML Workspace.

El cambio realizado en la configuración de la pantalla principal de la aplicación afecta a la pantalla principal del usuario registrado o del dispositivo móvil actual.

Sin embargo, el cambio realizado en HTML Workspace afecta a todos los usuarios de aplicaciones de AEM Forms que han iniciado sesión en el servidor de AEM Forms.
