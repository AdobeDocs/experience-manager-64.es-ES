---
title: Publicación de Dynamic Media Assets
description: Cómo publicar recursos de Dynamic Media, incluido el envío HTTP/2 de dichos recursos.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 8%

---


# Publicación de Dynamic Media Assets {#publishing-dynamic-media-assets}

Para publicar los recursos de Dynamic Media, selecciónelos y toque **[!UICONTROL Publicar]**. Una vez publicados los recursos de medios dinámicos, estarán disponibles para incluirlos en una página web mediante URL o mediante incrustación.

También puede publicar instantáneamente recursos que cargue, sin intervención del usuario. Consulte [Configuración de Dynamic Media - modo Scene7](config-dms7.md).

En la **[!UICONTROL vista de tarjeta]**, aparece un pequeño icono de globo terráqueo directamente debajo del nombre de un recurso para indicar que se ha publicado. En la **[!UICONTROL vista de lista]**, una columna **[!UICONTROL Publicada]** indica qué recursos se publican o cuáles no.

>[!NOTE]
>
>Si un recurso ya está publicado, utilice AEM para moverlo a otra carpeta y volver a publicarlo desde su nueva ubicación, la ubicación del recurso publicado original seguirá estando disponible, junto con el recurso recién republicado. Sin embargo, el recurso publicado original se &quot;pierde&quot; por AEM y no se puede cancelar su publicación. Por lo tanto, se recomienda cancelar la publicación de los recursos antes de moverlos a una carpeta diferente.

Si tiene intención de publicar recursos de vídeo inmediatamente después de codificarlos, asegúrese de que la codificación está completa. Cuando se siguen codificando los vídeos, el sistema le permite saber que hay un flujo de trabajo de procesamiento de vídeo en curso. Cuando haya terminado la codificación de vídeo, debería poder realizar la previsualización de las representaciones de vídeo. En ese momento, puede publicar los vídeos sin incurrir en errores de publicación.

Consulte también [Vinculación de direcciones URL a su Aplicación web](linking-urls-to-yourwebapplication.md).

Consulte también [Incrustación del visor de vídeos en una página Web.](embed-code.md)

>[!NOTE]
>
>* Los recursos deben publicarse para poder utilizar la dirección URL. Si no se publican los recursos, no funcionará copiar y pegar la URL en un explorador web.
>* Los ajustes preestablecidos de imagen y los ajustes preestablecidos de visor deben activarse y publicarse para el envío en directo.

>



Para obtener información detallada sobre la publicación de un conjunto o recurso, consulte [Publishing Assets.](managing-assets-touch-ui.md)

## ENVÍO HTTP/2 de los recursos de Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ahora admite el envío de todo el contenido de Dynamic Media (imágenes y vídeo) a través de HTTP/2. Es decir, una URL publicada o código incrustado para la imagen o el vídeo está disponible para integrarse con cualquier aplicación que acepte un recurso alojado. Ese recurso publicado se entrega a través del protocolo HTTP/2. Este método de envío mejora la forma en que se comunican los exploradores y los servidores, lo que permite una mejor respuesta y tiempos de carga de todos los recursos de Dynamic Media.

Consulte [HTTP/2 envío de contenido de preguntas más frecuentes](/help/sites-administering/scene7-http2faq.md) para obtener más información.
