---
title: Editor
seo-title: Editor
description: Obtenga información sobre cómo volver al Editor de IU clásica.
seo-description: Obtenga información sobre cómo volver al Editor de IU clásica.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
translation-type: tm+mt
source-git-commit: 9fa15a44cf83a50538cea3fb37bcccf405f66738
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 7%

---


# Editor{#editor}

De forma predeterminada, la capacidad de cambiar a la IU clásica desde el editor está deshabilitada.

![chlimage_1-9](assets/chlimage_1-9.png)

Para volver a habilitar la opción **Abrir en la IU** clásica en el menú Información **de** página, siga estos pasos.

1. Con CRXDE Lite, busque el nodo siguiente:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Por ejemplo

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. Crear una superposición con la opción Nodo **de** superposición; por ejemplo:

   * **Ruta**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Ubicación de la superposición**: `/apps/`
   * **Coincidir tipos** de nodos: activo (seleccione la casilla de verificación)

1. Añada la siguiente propiedad de texto de varios valores al nodo superpuesto:

   `sling:hideProperties = ["granite:hidden"]`

1. La opción **Abrir en la IU** clásica vuelve a estar disponible en el menú Información **de** página al editar páginas.

   ![chlimage_1-10](assets/chlimage_1-10.png)

