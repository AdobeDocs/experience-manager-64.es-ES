---
title: Publicación de recursos de Dynamic Media
description: Cómo publicar recursos de Dynamic Media, incluida la entrega HTTP/2 de esos recursos.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Administración de activos
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 8%

---

# Publicación de recursos de Dynamic Media {#publishing-dynamic-media-assets}

Para publicar los recursos de Dynamic Media, seleccione los recursos y pulse **[!UICONTROL Publicar]**. Una vez publicados los recursos de Dynamic Media, estos se encuentran disponibles para su inclusión en una página web a través de una URL o mediante la incrustación.

También puede publicar instantáneamente los recursos que cargue, sin intervención del usuario. Consulte [Configuración de Dynamic Media - Modo Scene7](config-dms7.md).

En la **[!UICONTROL vista de tarjeta]**, aparece un pequeño icono de globo terráqueo directamente debajo del nombre de un recurso para indicar que se ha publicado. En la **[!UICONTROL vista de lista]**, una columna **[!UICONTROL Publicada]** indica qué recursos se publican o cuáles no.

>[!NOTE]
>
>Si un recurso ya está publicado, utilice AEM para moverlo a otra carpeta y volver a publicar desde su nueva ubicación, la ubicación del recurso publicado original seguirá estando disponible, junto con el recurso recién republicado. Sin embargo, el recurso publicado original se &quot;pierde&quot; por AEM y no se puede cancelar su publicación. Por lo tanto, se recomienda cancelar la publicación de los recursos primero antes de moverlos a una carpeta diferente.

Si tiene intención de publicar recursos de vídeo inmediatamente después de codificarlos, asegúrese de que la codificación esté completa. Cuando los vídeos siguen codificándose, el sistema le permite saber que hay un flujo de trabajo de procesamiento de vídeo en curso. Cuando haya terminado la codificación de vídeo, debería poder previsualizar las representaciones de vídeo. En este punto, es seguro que publique los vídeos sin incurrir en errores de publicación.

Consulte también [Vinculación de URL a su aplicación web](linking-urls-to-yourwebapplication.md).

Consulte también [Incrustación del visualizador de vídeo en una página web.](embed-code.md)

>[!NOTE]
>
>* Los recursos deben publicarse para poder utilizar la dirección URL. Si los recursos no se publican, copiar y pegar la URL en un explorador web no funcionará.
>* Los ajustes preestablecidos de imagen y los ajustes preestablecidos de visualizador deben activarse y publicarse para que se puedan publicar en directo.

>



Para obtener información detallada sobre la publicación de un conjunto o recurso, consulte [Publicación de recursos.](managing-assets-touch-ui.md)

## Entrega HTTP/2 de recursos de Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ahora admite la entrega de todo el contenido de Dynamic Media (imágenes y vídeo) a través de HTTP/2. Es decir, una URL publicada o un código incrustado para la imagen o el vídeo están disponibles para integrarse con cualquier aplicación que acepte un recurso alojado. Ese recurso publicado se entrega mediante el protocolo HTTP/2. Este método de envío mejora la forma en que se comunican los exploradores y los servidores, lo que permite mejorar los tiempos de respuesta y carga de todos los recursos de Dynamic Media.

Consulte [HTTP/2 entrega de contenido preguntas más frecuentes](/help/sites-administering/scene7-http2faq.md) para obtener más información.
