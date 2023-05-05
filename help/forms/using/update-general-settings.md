---
title: Actualizar la configuración general
seo-title: Updating general settings
description: Actualizar la configuración de la aplicación de AEM Forms, como la pantalla de inicio y recuperar las opciones de puntos de inicio y archivos adjuntos
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 88%

---

# Actualizar la configuración general {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La configuración general de la aplicación de AEM Forms le permite especificar configuraciones, como recuperar archivos adjuntos, modo sin conexión, pantalla de aterrizaje, categoría predeterminada y frecuencia de guardado automático.

## Actualizar la configuración general en su aplicación {#working-with-the-form}

Al sincronizar su aplicación con el servidor de AEM Forms, todos los formularios y las tareas definidas se descargan en el dispositivo móvil.

La solución predeterminada de la aplicación de AEM Forms no descarga los archivos adjuntos asociados a cada formulario cuando la aplicación está sincronizada.

En la pestaña General, cambie la configuración de descarga de archivos adjuntos, modo sin conexión, pantalla de aterrizaje, guardado automático y sincronización. Puede cambiar la [pantalla Inicio](/help/forms/using/home-screen.md) de su aplicación.

**Ir a la pestaña General en la pantalla Configuración**

1. Para ir a la pantalla Configuración, pulse el botón Menú en la esquina superior izquierda de la pantalla Inicio y, a continuación, pulse **Configuración**.
1. En la pantalla Configuración, pulse la pestaña General.

   ![Configuración general en la aplicación de AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Las opciones pueden mostrarse de forma diferente en distintos dispositivos móviles.

### Configuración general {#general-settings}

Puede realizar los siguientes cambios en la configuración de su aplicación.

* **Recuperar archivos adjuntos de tareas**: Para especificar si desea descargar o no los archivos adjuntos asociados cuando se descarga cada tarea en la aplicación.

* **Modo sin conexión**: Para habilitar o deshabilitar el servicio sin conexión para la aplicación de AEM Forms. Consulte [Trabajar en modo sin conexión](/help/forms/using/work-offline-mode.md) para obtener más información.

* **Pantalla de aterrizaje**: Para establecer la ubicación de inicio ([pantalla Inicio](/help/forms/using/home-screen.md)) para la aplicación.

   Opciones disponibles:

   * Formularios
   * Tareas
   * Favoritos

* **Categoría predeterminada**: Permite seleccionar la categoría de formularios que se va a mostrar en la pantalla de inicio. Al seleccionar Todos, puede ver todos los formularios en la pantalla de inicio. Las categorías se rellenan en función de los formularios cargados en la aplicación. Los formularios están disponibles en la aplicación en función de la configuración de formulario especificada en el servidor de AEM Forms.

* **Frecuencia de guardado automático**: Para definir la frecuencia con la que su [aplicación móvil guarda datos de formulario](/help/forms/using/autosave-data-app.md) de forma local.

* **Frecuencia de sincronización**: Para definir la frecuencia con la que [la aplicación móvil está sincronizada](/help/forms/using/sync-app.md) con el servidor de AEM Forms en modo en línea.

**Borrar datos locales**: Borrar la base de datos, incluida la configuración y los datos locales de todos los usuarios y el almacenamiento de archivos del dispositivo.

>[!NOTE]
>
>Al borrar la caché, se cerrará la sesión inmediatamente de la aplicación.
>
>Sin embargo, se le pedirá que confirme la operación de borrado de caché.
