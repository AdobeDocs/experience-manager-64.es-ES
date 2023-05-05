---
title: Admin Console
seo-title: Admin Consoles
description: Aprenda a utilizar los Admin Console disponibles en AEM.
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# Admin Console{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

De forma predeterminada, se ha deshabilitado la capacidad de cambiar a la IU clásica a través de las consolas de administración. Por lo tanto, ya no se muestran los iconos emergentes que se veían al pasar el ratón por encima de determinados iconos de la consola, lo que permite acceder a la IU clásica.

![screen_shot_2018-03-23at11956](assets/screen_shot_2018-03-23at111956.png)

Todas las consolas que tengan una versión de IU clásica en `/libs/cq/core/content/nav` se puede volver a habilitar de forma individual para que la variable **IU clásica** una vez más aparece sobre el icono de la consola cuando se pasa el ratón por encima.

En este ejemplo, se vuelve a habilitar la IU clásica para la consola Sitios .

1. Con CRXDE Lite, busque el nodo correspondiente a la consola de administración para la que desea volver a habilitar la IU clásica. Se encuentran en:

   `/libs/cq/core/content/nav`

   Por ejemplo

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Seleccione el nodo correspondiente a la consola para la que desea volver a habilitar la IU clásica. Para nuestro ejemplo, volveremos a habilitar la IU clásica para la consola Sitios .

   `/libs/cq/core/content/nav/sites`

1. Creación de una superposición con la variable **Nodo de superposición** , por ejemplo:

   * **Ruta**: `/apps/cq/core/content/nav/sites`
   * **Ubicación de la superposición**: `/apps/`
   * **Coincidir tipos de nodo**: activo (seleccione la casilla de verificación)

1. Agregue la siguiente propiedad booleana al nodo superpuesto:

   `enableDesktopOnly = {Boolean}true`

1. La variable **IU clásica** está disponible de nuevo como opción de ampliación en admin console.

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

Repita estos pasos para cada consola para la que desee volver a habilitar el acceso a la versión de la IU clásica.
