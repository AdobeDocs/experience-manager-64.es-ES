---
title: Configuración de la caché de formularios adaptables
seo-title: Configure adaptive forms cache
description: La caché de formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios adaptables y documentos adaptables con el objetivo de reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 32%

---

# Configuración de la caché de formularios adaptables {#configure-adaptive-forms-cache}

Una caché es un mecanismo para acortar los tiempos de acceso a los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de formularios adaptables almacena únicamente el contenido del HTML y la estructura JSON de un formulario adaptable sin guardar ningún dato prerellenado. Ayuda a reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. Está diseñado específicamente para formularios adaptables y también admite documentos adaptables.

>[!NOTE]
>
>Cuando utilice la caché de formularios adaptables, utilice el AEM Dispatcher para almacenar en caché las bibliotecas de cliente (CSS y JavaScript) de un formulario o documento adaptable.

>[!NOTE]
>
>Durante el desarrollo de componentes personalizados, en el servidor utilizado para el desarrollo, mantenga deshabilitada la caché de formularios adaptables.

## Configuración de la caché {#configure-the-cache}

Realice los siguientes pasos para configurar la caché de formularios adaptables:

1. Vaya al Administrador de configuración de la consola web de AEM en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **Configuración del canal web de comunicaciones interactivas y formularios adaptables** para editar sus valores de configuración.
1. En el cuadro de diálogo editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en la variable **Número de Forms adaptable** campo . El valor predeterminado es 100.

   >[!NOTE]
   >
   >Para desactivar la caché, establezca el valor del campo Número de formularios adaptables en **0**. La caché se restablece y todos los formularios y documentos se eliminan de ella cuando se desactiva o cambia su configuración.

   ![Cuadro de diálogo de configuración para la caché del HTML de formularios adaptables](assets/cache-configuration-edit.png)

1. Haga clic en **Guardar** para guardar la configuración.
