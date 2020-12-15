---
title: Prácticas recomendadas sobre el formato del archivo de recursos
description: Prácticas recomendadas para la compatibilidad con archivos en AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a892ef7ab018aca715693125808d7ade540c8242
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Prácticas recomendadas sobre el formato de archivo de recursos {#assets-file-format-best-practices}

AEM Assets admite muchas bibliotecas de formato de archivos de propiedad y de terceros para satisfacer los diversos requisitos de compatibilidad de archivos de los usuarios. Las bibliotecas de Adobe admitidas son Adobe Camera Raw, Gibson, Adobe PDF Rasterizer y Adobe InDesign Server. Además, AEM Assets admite bibliotecas de terceros, como ImageMagick, DoceMonos, etc.

Para ver los formatos de archivo admitidos, consulte [Formatos admitidos por los recursos](assets-formats.md).

## Biblioteca de Adobe Camera Raw {#adobe-camera-raw-library}

Para un rendimiento óptimo, Adobe recomienda utilizar la biblioteca de Adobe Camera Raw para:

* RAW
* DNG

La biblioteca de Adobe Camera Raw admite el perfil de color CMYK como entrada. Sin embargo, genera la salida en espacio de color RGB y admite la salida en formato JPEG solamente. No conserva el espacio de color del archivo de origen (por ejemplo, CMYK) en las miniaturas.

Para obtener más información, consulte [Soporte Camera Raw](camera-raw.md) en AEM Assets.

## Biblioteca Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obtener los mejores resultados, Adobe recomienda utilizar la biblioteca Adobe PDF Rasterizer para los siguientes archivos:

* Archivos PDF pesados y con gran contenido
* Archivos AI con miniaturas no generados de forma predeterminada
* Para archivos AI con colores SPOT (PMS)

Las miniaturas y previsualizaciones que se generan con el rasterizador de PDF son de mejor calidad en comparación con la salida de rasterizado lista para usar. La biblioteca Rasterizer de Adobe PDF no admite conversión de espacio de color. Independientemente del espacio de color del archivo PDF de origen, Adobe PDF Rasterizer genera sólo salida RGB.

## Servidor Adobe InDesign {#adobe-indesign-cc-server}

Adobe recomienda utilizar el servidor de Adobe InDesign para extraer representaciones específicas de Adobe InDesign, como IDML y HTML. Para obtener más información, consulte [Añadir AEM recursos como referencias en Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media genera y ofrece múltiples variaciones de contenido enriquecido en tiempo real a través de su red global, escalable y optimizada para el rendimiento. Ofrece experiencias de visualización interactivas y optimiza el proceso de gestión de la campaña digital. Para obtener más información sobre cómo habilitar Dynamic Media, consulte [Configuración de Dynamic Media](config-dynamic.md).

Actualmente, Dynamic Media puede admitir vídeos de hasta 15 GB de contenido por archivo.

## Biblioteca ImageMagick {#imagemagick-library}

Adobe recomienda utilizar la biblioteca ImageMagick en los siguientes casos:

* Generación de representaciones en miniatura para archivos EPS
* Conservación de la información del perfil de imagen
* Para preservar la transparencia
* Para procesar archivos PSD y PSB

Para saber cómo configurar la biblioteca ImageMagic en AEM, consulte [Uso de ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obtener un uso óptimo, consulte [Prácticas recomendadas para configurar ImageMagick](best-practices-for-imagemagick.md).

## Biblioteca de transcodificación de imágenes {#image-transcoding-library}

La biblioteca de transcodificación de imágenes de Adobe es una solución de procesamiento de imágenes que realiza funciones básicas de gestión de imágenes, como codificación, transcodificación, remuestreo, cambio de tamaño, etc.

La biblioteca de transcodificación de imágenes admite los siguientes tipos MIME:

* JPG/JPEG
* PNG (8 y 16 bits)
* GIF
* BMP
* TIFF/TIFF comprimido (excepto Tiffs de 32 bits y PTiffs).
* ICO
* ICN

Para obtener más información, consulte [Biblioteca de transcodificación de imágenes](imaging-transcoding-library.md).
