---
title: Configuración de la caché de formularios adaptables
seo-title: Configuración de la caché de formularios adaptables
description: 'La caché de formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios adaptables y documentos adaptables con el objetivo de reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. '
seo-description: 'La caché de formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios adaptables y documentos adaptables con el objetivo de reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---


# Configuración de la caché de formularios adaptables {#configure-adaptive-forms-cache}

Una caché es un mecanismo para acortar los tiempos de acceso a los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de formularios adaptables almacena únicamente contenido HTML y estructura JSON de un formulario adaptable sin guardar datos precargados. Ayuda a reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. Está diseñado específicamente para formularios adaptables y también admite documentos adaptables.

>[!NOTE]
>
>Cuando utilice la caché de formularios adaptables, utilice el AEM Dispatcher para almacenar en caché las bibliotecas de cliente (CSS y JavaScript) de un formulario o documento adaptable.

>[!NOTE]
>
>Durante el desarrollo de componentes personalizados, en el servidor utilizado para el desarrollo, mantenga deshabilitada la caché de formularios adaptables.

## Configuración de la caché {#configure-the-cache}

Realice los siguientes pasos para configurar la caché de formularios adaptables:

1. Vaya a AEM administrador de configuración de la consola web en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **Configuración del canal web de formulario adaptable y comunicación interactiva** para editar sus valores de configuración.
1. En el cuadro de diálogo editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en el campo **Number of Adaptive Forms**. El valor predeterminado es 100.

   >[!NOTE]
   >
   >Para deshabilitar la caché, establezca el valor en el campo Número de Forms adaptable en **0**. La caché se restablece y todos los formularios y documentos se eliminan de la caché cuando se desactiva o cambia la configuración de la caché.

   ![Cuadro de diálogo Configuración para la caché HTML de formularios adaptables](assets/cache-configuration-edit.png)

1. Haga clic en **Save** para guardar la configuración.

