---
title: Envío de recursos de Dynamic Media
seo-title: Envío de recursos de Dynamic Media
description: Aprenda a distribuir recursos de medios dinámicos
seo-description: Aprenda a distribuir recursos de medios dinámicos
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 23%

---


# Envío de recursos de Dynamic Media {#delivering-dynamic-media-assets}

El modo de distribuir los recursos de medios dinámicos, tanto de vídeo como de imágenes, depende de cómo se implemente el sitio web.

Con Dynamic Media dispone de varias opciones:

* Si el sitio web se aloja en AEM, lo más recomendable es añadir recursos de Dynamic Media directamente a la página.
* Si su sitio web no está en AEM, puede elegir entre:

   * Incrustación de vídeo o imagen en el sitio web.
   * Vincular direcciones URL a la aplicación web. Utilice la vinculación cuando desee distribuir un reproductor de vídeo como ventana emergente o modal.
   * Si el sitio responde, puede [entregar imágenes optimizadas.](responsive-site.md)

>[!NOTE]
>
>Las imágenes inteligentes funcionan con los ajustes preestablecidos de imagen existentes y utilizan la inteligencia en el último milisegundo de envío para reducir aún más el tamaño del archivo de imagen en función de la velocidad de conexión de red o del navegador. Consulte [Imágenes inteligentes](imaging-faq.md) para obtener más información.

Para obtener más información, consulte los temas siguientes:

* [Añadir Dynamic Media Assets a páginas web](adding-dynamic-media-assets-to-pages.md)
* [Incrustación del visor de imágenes o vídeos en una página web](embed-code.md)
* [Activar la protección de los vínculos interactivos de Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* Integración de la marca de agua digital no visible (Digimarc) con Dynamic Media (próximamente)
* [Vincular URL en la aplicación web](linking-urls-to-yourwebapplication.md)
* [Distribución de imágenes adaptables para un sitio interactivo](responsive-site.md)
* [Entrega HTTP2 de contenido](http2.md)
* [Invalidar el contenido en caché de CDN](invalidate-cdn-cached-content.md)
* [Usar conjuntos de reglas para transformar URL](using-rulesets-to-transform-urls.md)

## ENVÍO HTTP/2 de los recursos de Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ahora admite el envío de todo el contenido de Dynamic Media (imágenes y vídeo) a través de HTTP/2. Es decir, una URL publicada o código incrustado para la imagen o el vídeo está disponible para integrarse con cualquier aplicación que acepte un recurso alojado. Ese recurso publicado se entrega a través del protocolo HTTP/2. Este método de envío mejora la forma en que se comunican los exploradores y los servidores, lo que permite una mejor respuesta y tiempos de carga de todos los recursos de Dynamic Media.

Consulte [HTTP/2 Envío de las preguntas más frecuentes sobre el contenido](/help/sites-administering/scene7-http2faq.md) para obtener más información.
