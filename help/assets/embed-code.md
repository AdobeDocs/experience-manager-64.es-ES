---
title: Incrustación del visualizador de imágenes o vídeos de Dynamic Media en una página web
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: Aprenda a incrustar vídeo o imágenes de Dynamic Media en una página web
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 21%

---

# Incrustación del visualizador de imágenes o vídeos de Dynamic Media en una página web {#embedding-the-video-or-image-viewer-on-a-web-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Utilice la función **[!UICONTROL Código incrustado]** cuando desee reproducir el vídeo o ver un recurso incrustado en una página web. El código incrustado se copia en el portapapeles para pegarlo en las páginas web. No se permite la edición del código en el cuadro de diálogo **[!UICONTROL Código incrustado]**.

Las direcciones URL incrustadas solo se pueden incrustar si _not_ using [!DNL Experience Manager] como WCM. Si está utilizando [!DNL Experience Manager] como WCM, [los recursos se añaden directamente en la página.](adding-dynamic-media-assets-to-pages.md)

Consulte [Vinculación de URL a la aplicación web.](linking-urls-to-yourwebapplication.md)

Consulte [Entrega de imágenes optimizadas para un sitio interactivo.](responsive-site.md)

>[!NOTE]
>
>El código incrustado no está disponible para copiar hasta que no haya publicado el recurso seleccionado. Además, también debe publicar el ajuste preestablecido de visualizador o de imagen.
>
>Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md).
>
>Consulte [Ajustes preestablecidos del visualizador de publicaciones](managing-viewer-presets.md#publishing-viewer-presets).
>
>Consulte [Publicar ajustes preestablecidos de imagen](managing-image-presets.md#publishing-image-presets).

**Incrustación del visualizador de imágenes o vídeos de Dynamic Media en una página web**:

1. Vaya a la *publicado* recurso de imagen o vídeo cuyo código incrustado desee copiar.

   Recuerde que el código incrustado solo está disponible para copiar *después* de *publicar* los recursos por primera vez. Además, también se debe publicar el ajuste preestablecido de visualizador o de imagen.

   Consulte [Publicación de recursos.](publishing-dynamicmedia-assets.md)

   Consulte [Ajustes preestablecidos del visualizador de publicaciones](managing-viewer-presets.md#publishing-viewer-presets).

   Consulte [Publicar ajustes preestablecidos de imagen](managing-image-presets.md#publishing-image-presets).

1. En el carril izquierdo, seleccione el menú desplegable y pulse **[!UICONTROL Visualizadores]**.
1. En el carril izquierdo, pulse un nombre de ajuste preestablecido de visualizador. El ajuste preestablecido de visualizador se aplica al recurso.
1. Toque **[!UICONTROL Incrustar]**.
1. En el **[!UICONTROL Código incrustado]** , copie todo el código en el portapapeles y, a continuación, pulse **[!UICONTROL Cerrar]**.
1. Pegue el código incrustado en las páginas web.

## Uso de HTTP/2 para distribuir los recursos de Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 es el nuevo protocolo web actualizado que mejora la forma en que se comunican los exploradores y los servidores. Proporciona una transferencia de información más rápida y reduce la cantidad de potencia de procesamiento necesaria. La entrega de recursos de Dynamic Media ahora puede realizarse a través de HTTP/2, lo que proporciona una mejor respuesta y tiempos de carga.

Consulte [Entrega HTTP2 de contenido](http2.md) para obtener información detallada sobre cómo empezar a usar HTTP/2 con su cuenta de Dynamic Media.
