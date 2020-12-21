---
title: Actualización de la configuración general
seo-title: Actualización de la configuración general
description: Actualice la configuración de la aplicación de AEM Forms, como la pantalla de inicio, y recupere las opciones de puntos de inicio y datos adjuntos
seo-description: Actualice la configuración de la aplicación de AEM Forms, como la pantalla de inicio, y recupere las opciones de puntos de inicio y datos adjuntos
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---


# Actualizando configuración general {#updating-general-settings}

La configuración general de la aplicación de AEM Forms le permite especificar opciones de configuración como la captura de archivos adjuntos, el modo sin conexión, la pantalla de aterrizaje, la categoría predeterminada y la frecuencia de guardado automático.

## Actualización de la configuración general en la aplicación {#working-with-the-form}

Al sincronizar la aplicación con el servidor de AEM Forms, todos los formularios y tareas definidas se descargan en el dispositivo móvil.

La solución integrada de aplicaciones de AEM Forms no descarga los archivos adjuntos asociados a cada formulario cuando la aplicación está sincronizada.

En la ficha General, cambie los datos adjuntos de descarga, el modo sin conexión, la pantalla de aterrizaje, el guardado automático y la configuración de sincronización. Puede cambiar la [pantalla principal](/help/forms/using/home-screen.md) de la aplicación.

**Vaya a la ficha General de la pantalla Configuración**

1. Para ir a la pantalla Configuración, toque el botón Menú en la esquina superior izquierda de la pantalla Inicio y, a continuación, toque **Configuración**.
1. En la pantalla Configuración, toque la ficha General.

   ![Configuración general en la aplicación de AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Las opciones pueden mostrarse de forma diferente en distintos dispositivos móviles.

### Configuración general {#general-settings}

Puede realizar los siguientes cambios en la configuración de la aplicación.

* **Buscar adjuntos** de tarea: Para especificar si desea descargar o no los archivos adjuntos asociados cuando se descargue cada tarea en la aplicación.

* **Modo** sin conexión: Para activar o desactivar el servicio sin conexión para la aplicación de AEM Forms. Consulte [Uso del modo sin conexión](/help/forms/using/work-offline-mode.md) para obtener más información.

* **Pantalla** de aterrizaje: Para definir la ubicación del inicio (pantalla [de inicio](/help/forms/using/home-screen.md)) para la aplicación.

   Opciones disponibles:

   * Forms
   * Tareas
   * Favoritos

* **Categoría** predeterminada: Permite seleccionar la categoría de los formularios que se mostrarán en la pantalla de inicio. Cuando selecciona Todo, puede ver todos los formularios en la pantalla de inicio. Las categorías se rellenan en función de los formularios cargados en la aplicación. Forms está disponible en la aplicación en función de la configuración de formulario especificada en el servidor de AEM Forms.

* **Frecuencia** de guardado automático: Para definir la frecuencia con la que la aplicación  [móvil guarda los datos ](/help/forms/using/autosave-data-app.md) de forma local.

* **Frecuencia** de sincronización: Para definir la frecuencia con la que la aplicación  [móvil se ](/help/forms/using/sync-app.md) sincroniza con el servidor de AEM Forms en modo en línea.

**Borrar datos** locales: Borre la base de datos, incluida la configuración y los datos locales de todos los usuarios y el almacenamiento de archivos desde el dispositivo.

>[!NOTE]
>
>Al borrar la caché, se cerrará la sesión de inmediato en la aplicación.
>
>Sin embargo, se le pedirá que confirme la operación de borrado de caché.
