---
title: Pantalla principal
seo-title: Pantalla principal
description: Descripción de los componentes de la pantalla de inicio de la aplicación de AEM Forms
seo-description: Descripción de los componentes de la pantalla de inicio de la aplicación de AEM Forms
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Pantalla principal {#home-screen}

Al iniciar sesión en la aplicación de AEM Forms, se le redirige a la pantalla de inicio.

## Pantalla principal predeterminada {#default-home-screen}

De forma predeterminada, la pantalla Inicio muestra todos los formularios, incluidos los puntos de inicio y las tareas (si el servidor conectado está habilitado para AEM Forms Workflow), junto con las miniaturas asociadas. Puede especificar las miniaturas en el servidor de AEM Forms.

La siguiente figura está anotada con llamadas a los componentes esenciales en la pantalla de inicio predeterminada.
![Pantalla](assets/home-screen-1.png)principal de la aplicación de Forms[Haga clic para ampliar](assets/home-screen-1-1.png)

1. **Botón** de menú: Toque el botón **Menú** para desplazarse a Tareas, Forms, Bandeja de salida y Configuración. Si la aplicación de AEM Forms está conectada a un servidor AEM Forms JEE, puede ver la opción Tareas. La opción Tareas también almacena los borradores creados a partir de tareas en un proceso. Para los servidores OSGi de AEM Forms, la opción Tareas está oculta. Outbox almacena los formularios y borradores guardados antes de que se sincronicen con el servidor. Todos los formularios y borradores guardados en la Bandeja de salida se cargan en el servidor de AEM Forms cuando la aplicación se [sincroniza con el servidor](/help/forms/using/sync-app.md). Para obtener información sobre la configuración, consulte [Actualización de la configuración](/help/forms/using/update-general-settings.md)general.
1. **Tarea o formulario**: Toque la tarea o el formulario de la lista con los que desee trabajar.
1. **Puntos suspensivos** horizontales: Indica que hay acciones disponibles para el formulario. Al tocar los puntos suspensivos se muestran las acciones y la descripción que ha proporcionado el autor. La opción **Eliminar borrador** y **completar** está visible al tocar los puntos suspensivos.
1. **Icono** Actualizar: Toque el icono de actualización para sincronizar la aplicación con el servidor de AEM Forms.

## Personalización de la pantalla principal {#customizing-the-home-screen}

![Configuración general](assets/gen-settings.png)

Puede cambiar la pantalla de inicio predeterminada de la aplicación desde la configuración **[](/help/forms/using/update-general-settings.md)**general de la aplicación o desde la ficha **Preferencias**de HTML Workspace.

El cambio realizado en la configuración de la pantalla de inicio de la aplicación afecta a la pantalla de inicio del usuario registrado o del dispositivo móvil actual.

Sin embargo, el cambio realizado en el espacio de trabajo HTML afecta a todos los usuarios de la aplicación de AEM Forms que iniciaron sesión en el servidor de AEM Forms.

