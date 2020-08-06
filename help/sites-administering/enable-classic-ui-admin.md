---
title: Admin Console
seo-title: Admin Console
description: Obtenga información sobre cómo utilizar los Admin Console disponibles en AEM.
seo-description: Obtenga información sobre cómo utilizar los Admin Console disponibles en AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 2%

---


# Admin Console{#admin-consoles}

De forma predeterminada, se ha deshabilitado la capacidad de cambiar a la IU clásica a través de las consolas de administración. Por lo tanto, ya no se muestran los iconos emergentes que se vieron al pasar el ratón sobre determinados iconos de la consola, lo que permite acceder a la IU clásica.

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

Cada consola que tenga una versión de IU clásica en `/libs/cq/core/content/nav` puede volver a activarse individualmente para que la opción de IU **** clásica aparezca una vez más sobre el icono de la consola cuando se pase el ratón por encima.

En este ejemplo, estamos volviendo a habilitar la IU clásica para la consola Sitios.

1. Con CRXDE Lite, busque el nodo correspondiente a la consola de administración para la que desea volver a habilitar la IU clásica. Se encuentran en:

   `/libs/cq/core/content/nav`

   Por ejemplo

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Seleccione el nodo correspondiente a la consola para la que desea volver a habilitar la IU clásica. Para nuestro ejemplo, reactivaremos la IU clásica para la consola Sitios.

   `/libs/cq/core/content/nav/sites`

1. Crear una superposición con la opción Nodo **de** superposición; por ejemplo:

   * **Ruta**: `/apps/cq/core/content/nav/sites`
   * **Ubicación de la superposición**: `/apps/`
   * **Coincidir tipos** de nodos: activo (seleccione la casilla de verificación)

1. Añada la siguiente propiedad booleana al nodo superpuesto:

   `enableDesktopOnly = {Boolean}true`

1. La opción de IU **** clásica está disponible de nuevo como opción emergente en la consola de administración.

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

Repita estos pasos para cada consola para la que desee volver a habilitar el acceso a la versión de la IU clásica.
