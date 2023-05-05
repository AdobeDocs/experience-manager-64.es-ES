---
title: Componente Comentarios de superposición
seo-title: Overlay Comments Component
description: Información general del componente Comentarios de superposición
seo-description: Overlay Comments component overview
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---

# Componente Comentarios de superposición {#overlay-comments-component}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La intención de [superposición](client-customize.md#overlays) un componente predeterminado es modificar el aspecto o el comportamiento de un componente globalmente, para todas las referencias relativas al componente. Depende de la naturaleza de sling para resolver la carpeta /apps antes de buscar en la carpeta /libs. Por lo tanto, la ruta al componente es idéntica a la ruta al componente predeterminado, excepto que está en la carpeta /apps y no en la carpeta /libs.

## Ejemplo {#example}

Supongamos que desea modificar la función de comentarios para que coincida con el diseño del sitio web, cambiando el encabezado de los comentarios para que ya no muestre el avatar de ningún comentario. Las soluciones para ocultar el avatar utilizan CSS o, como se describe aquí, superponen header.jsp en la carpeta de aplicaciones para que el HTML que contiene el avatar no se envíe nunca al cliente.

Para superponer comentarios, deberá:

1. [Página Comentarios](overlay-create-comments-page.md)
1. [Crear nodos](overlay-create-nodes.md)
1. [Modificar el aspecto](overlay-alter-appearance.md)
