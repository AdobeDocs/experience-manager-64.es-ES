---
title: Trabajo con Dynamic Media
seo-title: Working with Dynamic Media
description: Aprenda a utilizar Dynamic Media para distribuir recursos para consumo en sitios web, móviles y sociales.
seo-description: Learn how to use Dynamic Media to deliver assets for consumption on web, mobile, and social sites.
uuid: 4dc0f436-d20e-4e8b-aeff-5515380fa44d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: a8063d43-923a-42ac-9a16-0c7fadd8f73f
exl-id: f8a3936e-82b5-46c7-9614-b97162e27d6a
feature: Asset Management,Renditions
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# Trabajo con Dynamic Media {#working-with-dynamic-media}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) ayuda a ofrecer bajo demanda recursos de marketing y comercialización de rico contenido visual, escalados automáticamente para el consumo en sitios web, móviles y sociales. Con un conjunto de recursos principales, Dynamic Media genera y ofrece varias variaciones de contenido enriquecido en tiempo real a través de su red global, escalable y optimizada para el rendimiento.

Dynamic Media proporciona experiencias de visualización interactivas, como zoom, giro de 360 grados y vídeo. Dynamic Media incorpora de forma exclusiva los flujos de trabajo de la solución de administración de recursos digitales (Assets) de Adobe Experience Manager para simplificar y optimizar el proceso de administración de campañas digitales.

<!-- DEAD ARTICLE >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Qué puede hacer con Dynamic Media {#what-you-can-do-with-dynamic-media}

Dynamic Media permite administrar los recursos antes de publicarlos. Cómo trabajar con recursos en general se explica en detalle en [Uso de recursos digitales](managing-assets-touch-ui.md). Los temas generales incluyen la carga, descarga, edición y publicación de recursos; ver y editar propiedades, y buscar recursos.

Las funciones solo de Dynamic Media incluyen lo siguiente:

* [Banner de carrusel](carousel-banners.md)
* [Conjuntos de imágenes](image-sets.md)
* [Imágenes interactivas](interactive-images.md)
* [Vídeos interactivos](interactive-videos.md)
* [Conjuntos de medios mixtos](mixed-media-sets.md)
* [Imágenes panorámicas](panoramic-images.md)

* [Conjuntos de giros](spin-sets.md)
* [Vídeo](video.md)
* [Entrega de recursos de Dynamic Media](delivering-dynamic-media-assets.md)
* [Administración de recursos](managing-assets.md)
* [Uso de las vistas rápidas para crear ventanas emergentes personalizadas](custom-pop-ups.md)

Consulte también [Configuración de Dynamic Media](administering-dynamic-media.md).

>[!NOTE]
>
>Para comprender las diferencias entre usar Dynamic Media e integrar Dynamic Media Classic con AEM, consulte [Integración de Dynamic Media Classic con Dynamic Media](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media).

## Dynamic Media habilitado frente a Dynamic Media deshabilitado {#dynamic-media-on-versus-dynamic-media-off}

Puede saber si Dynamic Media está habilitado (activado) por las siguientes características:

* Las representaciones dinámicas están disponibles al descargar o previsualizar recursos.
* Hay disponibles conjuntos de imágenes, conjuntos de giros y conjuntos de medios mixtos.
* Se crean representaciones PTIFF.

Al hacer clic en un recurso de imagen, la vista del recurso es diferente con Dynamic Media [enabled](config-dynamic.md#enabling-dynamic-media). Dynamic Media utiliza los visores HTML5 bajo demanda.

### Representaciones dinámicas {#dynamic-renditions}

Representaciones dinámicas, como ajustes preestablecidos de imágenes y visualizadores (en **[!UICONTROL Dinámica]**) están disponibles cuando Dynamic Media está habilitado.

![chlimage_1-358](assets/chlimage_1-358.png)

### Conjuntos de imágenes, conjuntos de giros, conjuntos de medios mixtos {#image-sets-spins-sets-mixed-media-sets}

Los conjuntos de imágenes, los conjuntos de giros y los conjuntos de medios mixtos están disponibles si Dynamic Media está activado.

![chlimage_1-359](assets/chlimage_1-359.png)

### Representaciones PTIFF {#ptiff-renditions}

Los recursos habilitados para Dynamic Media incluyen `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Cambio de vistas de recursos {#asset-views-change}

Con Dynamic Media habilitado, puede hacer clic en el botón `+` y `-` botones. También puede tocar o hacer clic en para acercar cierta área. Revertir le lleva a la versión original y puede crear la imagen a pantalla completa haciendo clic en las flechas diagonales. Dynamic Media habilitado tiene este aspecto:

![chlimage_1-361](assets/chlimage_1-361.png)

Con Dynamic Media desactivado, puede acercar y alejar y revertir al tamaño original:

![chlimage_1-362](assets/chlimage_1-362.png)
