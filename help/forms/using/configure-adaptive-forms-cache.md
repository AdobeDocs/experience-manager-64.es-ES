---
title: Configurar la caché de los formularios adaptables
seo-title: Configure adaptive forms cache
description: La memoria caché de los formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios y documentos adaptables con el objetivo de reducir el tiempo necesario para procesar un formulario o un documento adaptable en el cliente.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 72%

---

# Configurar la caché de los formularios adaptables {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Una caché es un mecanismo para acortar los tiempos de acceso a los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de los formularios adaptables almacena únicamente el contenido HTML y la estructura JSON de un formulario adaptable sin guardar los datos rellenados previamente. Ayuda a reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. Está diseñado específicamente para formularios adaptables y también admite documentos adaptables.

>[!NOTE]
>
>Cuando utilice la caché de formularios adaptables, utilice el AEM Dispatcher para almacenar en caché las bibliotecas de cliente (CSS y JavaScript) de un formulario o documento adaptable.

>[!NOTE]
>
>Cuando desarrolle componentes personalizados, mantenga deshabilitada la memoria caché de los formularios adaptables en el servidor utilizado para el desarrollo.

## Configuración de la caché {#configure-the-cache}

Realice los siguientes pasos para configurar la caché de los formularios adaptables:

1. Vaya al Administrador de configuración de la consola web de AEM en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **Configuración del canal Web de comunicaciones interactivas y formularios adaptables** para editar sus valores de configuración.
1. En el cuadro de diálogo Editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en el campo **Número de formularios adaptables**. El valor predeterminado es 100.

   >[!NOTE]
   >
   >Para deshabilitar la caché, establezca el valor del campo Número de formularios adaptables en **0**. La caché se restablece y todos los formularios y documentos se eliminan de ella cuando se desactiva o cambia su configuración.

   ![Cuadro de diálogo de configuración para la memoria caché del HTML de los formularios adaptables](assets/cache-configuration-edit.png)

1. Haga clic en **Guardar** para guardar la configuración.
