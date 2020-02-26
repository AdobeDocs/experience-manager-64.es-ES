---
title: Varias ofertas para colecciones, fragmentos y plantillas de fragmentos
description: Segregar el contenido en el repositorio de CRX según la organización del cliente para evitar el acceso no autorizado.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Varias ofertas para colecciones, fragmentos y plantillas de fragmentos {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La función de varios alquileres le permite segregar contenido en CRX en función del prefijo de organización y el ID de organización para proteger el contenido del acceso no autorizado por parte de usuarios de otras organizaciones.

Recursos Adobe Experience Manager (AEM) almacena datos para cada organización en una ruta diferente. Cada ruta específica de la organización se identifica mediante el prefijo de la organización y el identificador de la organización.
que se incluye en la ubicación tradicional en la que se almacenan distintos tipos de activos en CRX.

Por ejemplo, si crea una carpeta con el nombre `Demo`, Recursos AEM almacena la carpeta en la ubicación `../content/dam/Demo` de CRX de forma predeterminada. Con la función de varios alquileres activada, puede almacenar los datos en `../content/dam/<organization prefix>/<organization id>Demo`.

Por ejemplo, para los usuarios de Adobe Marketing Cloud de Recursos AEM (On-demand) asignados a `aodpremium` la organización, puede utilizar la función de varios alquileres para configurar la siguiente ruta de acceso a `../content/dam/mac/aodpremiumDemo`, segregar el contenido. En este ejemplo `mac` es el prefijo de organización y `aodpremium` es el identificador de organización.

En función de la organización y el ID del usuario, esta ruta de acceso cualificada se muestra en la interfaz de Recursos AEM y en varios asistentes, incluidos los asistentes para la creación de movimiento y de fragmentos para aplicar la segmentación.

La función de varios alquileres le permite segmentar los siguientes tipos de recursos y componentes:

* Colecciones
* Colecciones públicas
* Catálogos (incluido el asistente Agregar o seleccionar página)
* Plantillas
* Plantillas de fragmento
* Lightbox
