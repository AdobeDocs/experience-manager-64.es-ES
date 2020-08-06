---
title: Componente Comentarios de superposición
seo-title: Componente Comentarios de superposición
description: Información general del componente Comentarios de superposición
seo-description: Información general del componente Comentarios de superposición
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Componente Comentarios de superposición {#overlay-comments-component}

La intención de [superponer](client-customize.md#overlays) un componente predeterminado es alterar el aspecto o el comportamiento de un componente globalmente, para todas las referencias relativas al componente. Depende de la naturaleza de sling para resolver en la carpeta /apps antes de buscar en la carpeta /libs. Por lo tanto, la ruta del componente es idéntica a la ruta del componente predeterminado, excepto que se encuentra en la carpeta /apps y no en la carpeta /libs.

## Ejemplo {#example}

Supongamos que desea modificar la función de comentarios para que coincida con el diseño de su sitio web, cambiando el encabezado de comentario para que ya no muestre el avatar de ningún comentario. Las soluciones para ocultar el avatar utilizan CSS o, como se describe aquí, superponen header.jsp en la carpeta de aplicaciones para que el HTML que contiene el avatar nunca se envíe al cliente.

Para superponer comentarios, deberá:

1. [Página de comentarios](overlay-create-comments-page.md)
1. [Crear nodos](overlay-create-nodes.md)
1. [Modificar el aspecto](overlay-alter-appearance.md)

