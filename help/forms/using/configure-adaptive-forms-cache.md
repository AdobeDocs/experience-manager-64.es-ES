---
title: Configuración de la caché de formularios adaptables
seo-title: Configuración de la caché de formularios adaptables
description: 'La caché de formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios adaptables y documentos adaptables con el objetivo de reducir el tiempo necesario para presentar una forma adaptable o un documento en el cliente. '
seo-description: 'La caché de formularios adaptables está diseñada específicamente para formularios y documentos adaptables. Almacena en caché formularios adaptables y documentos adaptables con el objetivo de reducir el tiempo necesario para presentar una forma adaptable o un documento en el cliente. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---


# Configurar la caché de formularios adaptables {#configure-adaptive-forms-cache}

Una caché es un mecanismo para reducir los tiempos de acceso a los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de formularios adaptables almacena solo el contenido HTML y la estructura JSON de un formulario adaptable sin guardar datos precargados. Ayuda a reducir el tiempo necesario para procesar un formulario o documento adaptable en el cliente. Está diseñado específicamente para formularios adaptables y también admite documentos adaptables.

>[!NOTE]
>
>Cuando utilice la caché de formularios adaptables, utilice el despachante de AEM para almacenar en caché las bibliotecas cliente (CSS y JavaScript) de un formulario o documento adaptable.

>[!NOTE]
>
>Al desarrollar componentes personalizados, en el servidor utilizado para el desarrollo, mantenga deshabilitada la caché de formularios adaptables.

## Configurar la caché {#configure-the-cache}

Realice los siguientes pasos para configurar la caché de formularios adaptables:

1. Vaya a AEM administrador de configuración de consola web en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **Configuración del Canal Web de comunicación interactiva y formulario adaptable** para editar sus valores de configuración.
1. En el cuadro de diálogo Editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en el campo **Número de Forms adaptable**. El valor predeterminado es 100.

   >[!NOTE]
   >
   >Para deshabilitar la caché, establezca el valor en el campo Número de Forms adaptable en **0**. La caché se restablece y todos los formularios y documentos se eliminan de la caché cuando se deshabilita o cambia la configuración de la caché.

   ![Cuadro de diálogo de configuración para la caché HTML de formularios adaptables](assets/cache-configuration-edit.png)

1. Haga clic en **Guardar** para guardar la configuración.

