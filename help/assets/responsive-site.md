---
title: Entrega de imágenes optimizadas para un sitio interactivo
description: Cómo utilizar la función de código interactivo de Dynamic Media para ofrecer imágenes optimizadas
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
exl-id: 36bb526c-a6d9-4296-8318-97ac72d6b3ba
feature: Publishing
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 12%

---

# Distribución de imágenes adaptables para un sitio interactivo {#delivering-optimized-images-for-a-responsive-site}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Utilice la función de código interactivo cuando desee compartir el código para la entrega interactiva con su desarrollador web. Copia el mensaje interactivo (**[!UICONTROL RESS]**) en el portapapeles para poder compartirlo con el desarrollador web.

Esta función tiene sentido utilizarla si el sitio web se encuentra en un WCM de terceros. Sin embargo, si el sitio web está en AEM, un servidor de imágenes externos procesa la imagen y la suministra a la página web.

Consulte también [Incrustación del visualizador de vídeo en una página web.](embed-code.md)

Consulte también [Vinculación de URL a la aplicación web.](linking-urls-to-yourwebapplication.md)

**Para ofrecer imágenes optimizadas para un sitio interactivo**:

1. Vaya a la imagen para la que desee proporcionar código interactivo y, en el menú desplegable, pulse **[!UICONTROL Representaciones]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Seleccione un ajuste preestablecido de imagen interactivo. Aparecerán los botones **[!UICONTROL URL]** y **[!UICONTROL RESS]**.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >El recurso seleccionado *y* el ajuste preestablecido de imagen o visualizador seleccionado deben publicarse para que los botones **[!UICONTROL URL]** o **[!UICONTROL RESS]** estén disponibles.
   >
   >Dynamic Media: el modo híbrido requiere que publique los ajustes preestablecidos de imagen; Dynamic Media: el modo Scene7 publica automáticamente ajustes preestablecidos de imagen.

1. Toque **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. En el **[!UICONTROL Incrustar imagen interactiva]** , seleccione y copie el texto del código interactivo y péguelo en el sitio web para acceder al recurso interactivo.
1. Edite los puntos de interrupción predeterminados en el código incrustado para que coincidan con los del sitio web interactivo directamente en el código. Además, pruebe las distintas resoluciones de imagen que se proporcionan en diferentes puntos de interrupción de página.

## Uso de HTTP/2 para enviar los recursos de Dynamic Media {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 es el nuevo protocolo web actualizado que mejora la forma en que se comunican los exploradores y los servidores. Proporciona una transferencia de información más rápida y reduce la cantidad de potencia de procesamiento necesaria. La entrega de recursos de Dynamic Media se admite mediante HTTP/2, que proporciona una mejor respuesta y tiempos de carga.

Consulte [Entrega HTTP2 de contenido](http2.md) para obtener información detallada sobre cómo empezar a usar HTTP/2 con su cuenta de Dynamic Media.
