---
title: Prácticas recomendadas del formato de los archivos de recursos
description: Prácticas recomendadas para la compatibilidad con archivos en AEM Assets.
contentOwner: AG
feature: Administración de recursos,Herramientas para desarrolladores
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Prácticas recomendadas del formato de los archivos de recursos {#assets-file-format-best-practices}

AEM Assets admite muchas bibliotecas de formato de archivos propietarias y de terceros para satisfacer los distintos requisitos de compatibilidad de archivos de los usuarios. Las bibliotecas de Adobe admitidas son Adobe Camera Raw, Gibson, Adobe PDF Rasterizer y Adobe InDesign Server. Además, AEM Assets admite bibliotecas de terceros, como ImageMagick, TwelveMonkeys, etc.

Para ver los formatos de archivo compatibles, consulte [Formatos compatibles con Assets](assets-formats.md).

## Biblioteca Adobe Camera Raw {#adobe-camera-raw-library}

Para obtener un rendimiento óptimo, Adobe recomienda utilizar la biblioteca de Adobe Camera Raw para:

* RAW
* DNG

La biblioteca de Adobe Camera Raw admite el perfil de color CMYK como entrada. Sin embargo, genera la salida en espacio de color RGB y sólo admite la salida en formato JPEG. No conserva el espacio de color del archivo de origen (por ejemplo, CMYK) en las miniaturas.

Para obtener más información, consulte [Soporte Camera Raw](camera-raw.md) en AEM Assets.

## Biblioteca Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obtener mejores resultados, Adobe recomienda utilizar la biblioteca Adobe PDF Rasterizer para los siguientes archivos:

* Archivos PDF pesados y con gran contenido
* Los archivos AI con miniaturas no se generan de forma predeterminada
* Para archivos AI con colores SPOT (PMS)

Las miniaturas y vistas previas generadas con el rasterizador de PDF son de mejor calidad en comparación con los resultados de raster predeterminados. La biblioteca Rasterizer de Adobe PDF no admite conversión de espacios de color. Independientemente del espacio de color del archivo PDF de origen, Adobe PDF Rasterizer genera sólo salida RGB.

## Servidor de Adobe InDesign {#adobe-indesign-cc-server}

Adobe recomienda utilizar el servidor de Adobe InDesign para extraer representaciones específicas de Adobe InDesign, como IDML y HTML. Para obtener más información, consulte [Adición de AEM como referencias en Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media genera y ofrece múltiples variaciones de contenido enriquecido en tiempo real a través de su red global, escalable y optimizada para el rendimiento. Proporciona experiencias de visualización interactivas y optimiza el proceso de administración de campañas digitales. Para obtener más información sobre la activación de Dynamic Media, consulte [Configuración de Dynamic Media](config-dynamic.md).

Actualmente, Dynamic Media puede admitir vídeos de hasta 15 GB de contenido por archivo.

## Biblioteca ImageMagick {#imagemagick-library}

Adobe recomienda utilizar la biblioteca ImageMagick en los siguientes escenarios:

* Generación de representaciones en miniatura para archivos EPS
* Conservar la información del perfil de imagen
* Para preservar la transparencia
* Procesamiento de archivos PSD y PSB

Para saber cómo configurar la biblioteca ImageMagic en AEM, consulte [Uso de ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obtener un uso óptimo, consulte [Prácticas recomendadas para configurar ImageMagick](best-practices-for-imagemagick.md).

## Biblioteca de transcodificación de imágenes {#image-transcoding-library}

La biblioteca de transcodificación de imágenes de Adobe es una solución de procesamiento de imágenes que realiza funciones básicas de gestión de imágenes, como codificación, transcodificación, remuestreo, cambio de tamaño, etc.

La biblioteca de transcodificación de imágenes admite los siguientes tipos de MIME:

* JPG/JPEG
* PNG (8 bits y 16 bits)
* GIF
* BMP
* TIFF/TIFF comprimido (excepto Tiffs de 32 bits y PTiffs).
* ICO
* ICN

Para obtener más información, consulte [Biblioteca de transcodificación de imágenes](imaging-transcoding-library.md).
