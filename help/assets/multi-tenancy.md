---
title: Varios alquileres para colecciones, fragmentos y plantillas de fragmentos
description: Segregar contenido en el repositorio CRX en función de la organización del cliente para evitar el acceso no autorizado.
contentOwner: AG
feature: Collections
role: Architect,Administrator,Leader
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 1%

---


# Varios alquileres para colecciones, fragmentos y plantillas de fragmentos {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La función de inquilinos múltiples le permite segregar contenido en CRX en función del prefijo de organización y el ID de organización para proteger el contenido del acceso no autorizado por parte de los usuarios de otras organizaciones.

Adobe Experience Manager (AEM) Assets almacena datos de cada organización en una ruta diferente. Cada ruta específica de la organización se identifica mediante el prefijo de organización y el ID de organización.
que se incluye en la ubicación tradicional donde se almacenan distintos tipos de activos en CRX.

Por ejemplo, si crea una carpeta denominada `Demo`, AEM assets almacena de forma predeterminada la carpeta en la ubicación `../content/dam/Demo` en CRX. Con la función de inquilino múltiple habilitada, puede almacenar los datos en `../content/dam/<organization prefix>/<organization id>Demo`.

Por ejemplo, para los usuarios de Adobe Marketing Cloud de AEM Assets (On-demand) asignados a la organización `aodpremium`, puede utilizar la función de varios inquilinos para configurar la siguiente ruta como `../content/dam/mac/aodpremiumDemo` y segregar el contenido. En este ejemplo, `mac` es el prefijo de organización y `aodpremium` es el ID de organización.

En función de la organización y el ID del usuario, esta ruta cualificada se muestra en la interfaz de AEM Assets y en varios asistentes, incluidos los asistentes de creación Mover y Fragmentar para aplicar la agregación.

La función de inquilino múltiple permite segmentar los siguientes tipos de activos y componentes:

* Colecciones
* Colecciones públicas
* Catálogos (incluido el asistente Agregar/Seleccionar página )
* Plantillas
* Plantillas de recorte
* Lightbox
