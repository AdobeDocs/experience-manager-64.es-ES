---
title: Envío de recursos de Dynamic Media
seo-title: Envío de recursos de Dynamic Media
description: Aprenda a distribuir recursos de Dynamic Media
seo-description: Aprenda a distribuir recursos de Dynamic Media
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Administración de activos
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 25%

---

# Envío de recursos de Dynamic Media {#delivering-dynamic-media-assets}

La forma de distribuir los recursos de Dynamic Media, tanto de vídeo como de imágenes, depende de cómo se implemente el sitio web.

Con Dynamic Media dispone de varias opciones:

* Si el sitio web se aloja en AEM, lo más recomendable es añadir recursos de Dynamic Media directamente a la página.
* Si el sitio web no está AEM, puede elegir una de las opciones siguientes:

   * Incrustar el vídeo o la imagen en el sitio web.
   * Vincule las URL a la aplicación web. Utilice la vinculación cuando desee enviar un reproductor de vídeo como ventana emergente o modal.
   * Si el sitio es interactivo, puede [entregar imágenes optimizadas.](responsive-site.md)

>[!NOTE]
>
>Las imágenes inteligentes funcionan con los ajustes preestablecidos de imagen existentes y utilizan la inteligencia en el último milisegundo de envío para reducir aún más el tamaño del archivo de imagen en función de la velocidad de conexión de red o del explorador. Consulte [Imágenes inteligentes](imaging-faq.md) para obtener más información.

Para obtener más información, consulte los temas siguientes:

* [Adición de recursos de Dynamic Media a páginas web](adding-dynamic-media-assets-to-pages.md)
* [Incrustación del visualizador de imágenes o vídeos en una página web](embed-code.md)
* [Activar la protección de los vínculos interactivos de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-64/assets/dynamic/hotlink-protection.html?lang=es#dynamic)
* Integración de la marca de agua digital no visible (Digimarc) con Dynamic Media (próximamente)
* [Vincular URL en la aplicación web](linking-urls-to-yourwebapplication.md)
* [Distribución de imágenes adaptables para un sitio interactivo](responsive-site.md)
* [Entrega HTTP2 de contenido](http2.md)
* [Invalidar el contenido en caché de CDN](invalidate-cdn-cached-content.md)
* [Usar conjuntos de reglas para transformar URL](using-rulesets-to-transform-urls.md)

## Entrega HTTP/2 de recursos de Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ahora admite la entrega de todo el contenido de Dynamic Media (imágenes y vídeo) a través de HTTP/2. Es decir, una URL publicada o un código incrustado para la imagen o el vídeo están disponibles para integrarse con cualquier aplicación que acepte un recurso alojado. Ese recurso publicado se entrega mediante el protocolo HTTP/2. Este método de envío mejora la forma en que se comunican los exploradores y los servidores, lo que permite mejorar los tiempos de respuesta y carga de todos los recursos de Dynamic Media.

Consulte [HTTP/2 Entrega de contenido preguntas más frecuentes](/help/sites-administering/scene7-http2faq.md) para obtener más información.
