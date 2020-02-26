---
title: Transición de ContentSync a SmartSync
seo-title: Transición de ContentSync a SmartSync
description: Siga esta página para conocer la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
seo-description: Siga esta página para conocer la función SmartSync y cómo puede realizar la transición de ContentSync a SmartSync.
page-status-flag: never-activated
uuid: f2097a23-f21b-45e0-8ce2-7faa3cf0ed86
contentOwner: jsyal
discoiquuid: 4e502b86-bdf5-44eb-8e04-ba8062e12fa0
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Transición de ContentSync a SmartSync{#transitioning-from-contentsync-to-smartsync}

Esta sección proporciona información general sobre la función SmartSync y cómo minimiza la carga/almacenamiento del servidor y el tráfico de red para reducir los costes.

## Información general {#overview}

SmartSync es el mecanismo más reciente utilizado por AEM Screens. Sirve como reemplazo del método actual utilizado para almacenar en caché los canales sin conexión y entregarlos al reproductor.

Se ejecuta tanto en el lado del servidor como en el lado del cliente.

**En el servidor**:

* El contenido de los canales, incluidos los recursos, se almacena en caché en */var/contentsync*.
* La caché se expone a los reproductores mediante un manifiesto que describe el contenido disponible para una visualización.

**En el lado** del cliente:

* Player actualiza su contenido en función del manifiesto generado anteriormente.

### Ventajas de utilizar SmartSync {#benefits-of-using-smartsync}

La función SmartSync ofrece una serie de ventajas para el proyecto de AEM Screens. Permite

* Reducción drástica de los requerimientos de tráfico de red y almacenamiento de información en el lado del servidor
* El reproductor descarga los recursos de forma inteligente solo si el recurso falta o se cambia
* Optimizaciones de almacenamiento de información del lado del servidor y del lado del cliente

>[!NOTE]
>
>Adobe recomienda encarecidamente utilizar los proyectos de SmartSync para AEM Screens.

## Migración de ContentSync a SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Si ya ha instalado AEM 6.3 Feature Pack 5 y AEM 6.4 Feature Pack 3, puede activar SmartSync para los recursos para mejorar el uso del espacio en disco. Para habilitar SmartSync, siga la sección siguiente para realizar la transición de ContentSync a SmartSync, habilitando SmartSync.
>
>SmartSync está disponible para Screens Player con servidores compatibles con AEM 6.4.3 FP3. Consulte Descargas [](https://download.macromedia.com/screens/) de AEM Screens Player para descargar el último reproductor.

Siga los pasos a continuación para realizar la transición de ContentSync a SmartSync si no tiene instalado el paquete de funciones y los reproductores más recientes (AEM 6.4 Feature Pack 3):

1. La migración de ContentSync a SmartSync requiere borrar la caché de ContentSync antes de activar SmartSync.

   Vaya a la consola ContentSync desde su instancia mediante el vínculo ***http://localhost:4502/libs/cq/contentsync/content/console.html*** y haga clic en **Borrar caché**, como se muestra en la figura siguiente:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Se debe borrar toda la caché de contenido antes de utilizar SmartSync por primera vez.

1. Vaya a **Configuración de la consola web de Adobe Experience Manager **mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Configuración de la consola web de Adobe Experience Manager **se abre. Busque *offlinecontentservices*.

   Para buscar la propiedad **Screens Offline Content Service** , pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Haga clic en **Guardar** para activar la propiedad **Screens Offline Content Services* ***y, por tanto, utilice SmartSync para AEM Screens.
1. Una vez que haya habilitado SmartSync, debe navegar hasta el proyecto y hacer clic en **Actualizar contenido** sin conexión *(en la barra de acciones),* como se muestra en la figura siguiente.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)

