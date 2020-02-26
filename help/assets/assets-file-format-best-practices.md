---
title: Prácticas recomendadas sobre el formato del archivo de recursos
description: Prácticas recomendadas para la compatibilidad con archivos en Recursos AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Assets file format best practices {#assets-file-format-best-practices}

AEM Assets admite muchas bibliotecas de formato de archivos de propiedad y de terceros para satisfacer los distintos requisitos de compatibilidad de archivos de los usuarios. Las bibliotecas de Adobe admitidas son Adobe Camera Raw, Gibson, Adobe PDF Rasterizer y Adobe InDesign Server. Además, Recursos AEM admite bibliotecas de terceros, como ImageMagick, DoceMonos, etc.

For the supported file formats, see [Assets supported formats](assets-formats.md).

## Biblioteca Adobe Camera Raw {#adobe-camera-raw-library}

Para obtener un rendimiento óptimo, Adobe recomienda utilizar la biblioteca RAW de cámara de Adobe para:

* RAW
* DNG

La biblioteca de Adobe Camera Raw admite el perfil de color CMYK como entrada. Sin embargo, genera la salida en espacio de color RGB y admite la salida en formato JPEG solamente. No conserva el espacio de color del archivo de origen (por ejemplo, CMYK) en las miniaturas.

Para obtener más información, consulte Compatibilidad con [Camera Raw](camera-raw.md) en Recursos AEM.

## Biblioteca de Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obtener los mejores resultados, Adobe recomienda utilizar la biblioteca Rasterizer de Adobe PDF para los siguientes archivos:

* Archivos PDF pesados y con gran contenido
* Archivos AI con miniaturas no generados de forma predeterminada
* Para archivos AI con colores SPOT (PMS)

Las miniaturas y las vistas previas generadas con el rasterizador de PDF son de mejor calidad en comparación con la salida de rasterizado lista para usar. La biblioteca Rasterizer de Adobe PDF no admite conversión de espacio de color. Independientemente del espacio de color del archivo PDF de origen, Adobe PDF Rasterizer genera sólo salida RGB.

## Adobe InDesign Server {#adobe-indesign-cc-server}

Adobe recomienda utilizar Adobe InDesign Server para extraer representaciones específicas de Adobe InDesign, como IDML y HTML. Para obtener más información, consulte [AEM assets as reference in Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media genera y ofrece múltiples variaciones de contenido enriquecido en tiempo real a través de su red global, escalable y optimizada para el rendimiento. Ofrece experiencias de visualización interactivas y optimiza el proceso de administración de campañas digitales. Para obtener más información sobre cómo activar Dynamic Media, consulte [Configuración de Dynamic Media](config-dynamic.md).

Actualmente, Dynamic Media puede admitir vídeos de hasta 20 GB de contenido por archivo.

## Biblioteca ImageMagick {#imagemagick-library}

Adobe recomienda utilizar la biblioteca ImageMagick en los siguientes casos:

* Generación de representaciones en miniatura para archivos EPS
* Para conservar la información del perfil de imagen
* Para preservar la transparencia
* Para procesar archivos PSD y PSB

Para obtener información sobre cómo configurar la biblioteca ImageMagic en AEM, consulte [Uso de ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obtener un uso óptimo, consulte [Prácticas recomendadas para configurar ImageMagick](best-practices-for-imagemagick.md).

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

Para obtener más información, consulte Biblioteca [de transcodificación de imágenes](imaging-transcoding-library.md).
