---
title: Formatos de archivo admitidos en AEM Assets
description: Lista de formatos de archivo y tipos MIME admitidos por AEM Assets y las características admitidas para cada formato.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2baa172088f646752e85168d432d46942ac8244e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 9%

---


# Formatos de archivo admitidos en AEM Assets {#assets-supported-formats}

AEM Assets admite una amplia gama de formatos de archivo y cada funcionalidad admite distintos tipos MIME.

Para integrar AEM Assets con otras soluciones de administración de activos digitales (DAM) compatibles con estándares y software de escritorio, utilice la Extensible Metadata Platform (XMP) de Adobe.

Utilice la leyenda para comprender el nivel de asistencia.

| Nivel de asistencia | Descripción |
|:---:|---|
| xib | Compatible |
| * | Compatible con funciones de complemento |
| - | No aplicable |

## Formatos de imagen rasterizados {#supported-raster-image-formats}

Los formatos de imagen rasterizados admitidos para las funciones de administración de recursos son los siguientes:

| Formato | Almacenamiento | Gestión de metadatos | Extracción de metadatos | Generación de miniaturas | Edición interactiva | Reescritura de metadatos | Perspectivas |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | xib | xib | xib | xib | xib | xib | xib |
| GIF | xib | xib | xib | xib | xib |  | xib |
| TIFF | xib | xib | xib | xib |  | xib | xib |
| JPEG | xib | xib | xib | xib | xib | xib | xib |
| BMP | xib | xib | xib | xib | xib |  | xib |
| PNM | xib | xib |  |  |  |  | xib |
| PGM | xib | xib |  |  |  |  | xib |
| PBM | xib | xib |  |  |  |  | xib |
| PPM | xib | xib |  |  |  |  | xib |
| PSD **‡** | xib | xib | xib | xib |  |  | xib |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib | xib | xib | xib |  | xib |  |
| PICT |  |  |  |  |  |  | xib |
| PSB | xib | xib | xib | xib |  |  |  |

**La imagen combinada se extrae** del archivo PSD. Se trata de una imagen generada por Adobe Photoshop y incluida en el archivo PSD. Según la configuración, la imagen combinada puede ser o no la imagen real.

Los formatos de imagen rasterizados compatibles con las funciones de Dynamic Media son los siguientes:

| Formato | Cargar<br> (formato de entrada) | Crear<br> ajuste preestablecido de imagen<br><br> (formato de salida) | Previsualización<br> representación dinámica<br> | Entregar<br> representación dinámica<br> | Descargar<br> representación dinámica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | xib | xib | xib | xib | xib |
| GIF | xib | xib | xib | xib | xib |
| TIFF | xib | xib | xib | xib | xib |
| JPEG | xib | xib | xib | xib | xib |
| BMP | xib |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | xib |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib | xib | xib | xib | xib |
| PICT | xib |  |  |  |  |
| PSB |  |  |  |  |  |

**La imagen combinada se extrae** del archivo PSD. Se trata de una imagen generada por Adobe Photoshop y incluida en el archivo PSD. Según la configuración, la imagen combinada puede ser o no la imagen real.

Además de la información anterior, considere lo siguiente:

* La compatibilidad con archivos EPS se aplica solo a imágenes rasterizadas. Por ejemplo, la generación de miniaturas para imágenes vectoriales EPS no es compatible de forma predeterminada. Para agregar compatibilidad, [configure ImageMagick](best-practices-for-imagemagick.md). Para integrar herramientas de terceros para habilitar capacidades adicionales, consulte [Controlador de medios basado en línea de comandos](media-handlers.md#command-line-based-media-handler).

* La reescritura de metadatos funciona para el formato de archivo PSB cuando se agrega al controlador `NComm`.

* Para utilizar Dynamic Media para la previsualización y generación de representaciones dinámicas para archivos EPS, consulte los formatos de archivo [Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para archivos EPS, la reescritura de metadatos se admite en la versión 3.0 o posterior del Convenio de estructura de Documento PostScript (PS-Adobe).

## Formatos de imagen rasterizada no admitidos en Dynamic Media {#unsupported-image-formats-dynamic-media}

La siguiente lista describe los subtipos de formatos de archivo de imagen rasterizada que *no* son compatibles con Dynamic Media.

Consulte también [Detectar formatos de archivo no admitidos para Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* Archivos PNG con un tamaño de fragmento IDAT bueno de 100 MB.
* Archivos PSB.
* Los archivos PSD con un espacio de color distinto de CMYK, RGB, escala de grises o mapa de bits no son compatibles. No se admiten los espacios de color DuoTone, Lab e Indexed.
* Archivos PSD con una profundidad buena de 16.
* Archivos TIFF que tienen datos de coma flotante.
* Archivos TIFF que tienen espacio de color Lab.

## Biblioteca de Rasterizadores PDF {#supported-pdf-rasterizer-library}

La biblioteca Rasterizer de Adobe PDF genera previsualizaciones y miniaturas de alta calidad para archivos Adobe Illustrator y PDF grandes y con gran contenido. Adobe recomienda utilizar la biblioteca Rasterizer de PDF para lo siguiente:

* Archivos AI/PDF con gran cantidad de contenido que requieren muchos recursos para procesarlos.
* Archivos AI/PDF para los que no se generan miniaturas de forma predeterminada.
* Archivos AI con colores Pantone Matching System (PMS).

Consulte [Uso del rasterizador de PDF](aem-pdf-rasterizer.md).

## Biblioteca de transcodificación de imágenes {#supported-image-transcoding-library}

La biblioteca de transcodificación de imágenes de Adobe es una solución de procesamiento de imágenes que realiza funciones básicas de gestión de imágenes, como codificación, transcodificación, remuestreo y cambio de tamaño.

La biblioteca de transcodificación de imágenes admite los tipos MIME JPG/JPEG, PNG (8 y 16 bits), GIF, BMP, TIFF/Comprimido (excepto los archivos TIFF de 32 bits y PTIFF), ICO e ICN.

Consulte [Biblioteca de transcodificación de imágenes](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

La biblioteca de Adobe Camera Raw permite a AEM Assets ingestar imágenes sin procesar. Consulte [Soporte Camera Raw](camera-raw.md).

## Formatos de documento {#supported-document-formats}

Los formatos de documento admitidos para las funciones de administración de recursos son los siguientes:

| Formato | Almacenamiento | Administración de metadatos<br> | Extracción de texto completo<br> | Extracción de metadatos<br> | Generación de miniaturas<br> | Extracción de subconjunto<br> | Reescritura de metadatos<br> |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib | xib |  | xib | xib | xib | xib |
| DOC | xib | xib | xib | xib |  |  |  |
| DOCX | xib | xib | xib | xib |  |  |  |
| ODT | xib | xib | xib |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib | xib | xib | xib | xib | xib | xib |
| HTML | xib | xib | xib |  |  |  |  |
| RTF | xib | xib | xib |  |  |  |  |
| TXT | xib | xib | xib |  |  |  |  |
| XLS | xib | xib | xib |  |  |  |  |
| XLSX | xib | xib | xib | xib |  |  |  |
| ODS | xib | xib | xib |  |  |  |  |
| PPT | xib | xib | xib | xib | xib | xib |  |
| PPTX | xib | xib | xib | xib | xib | xib |  |
| ODP | xib | xib | xib |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | xib | xib |  | xib | xib | xib | xib |
| PS | xib | xib |  |  |  |  |  |
| QXP | xib | xib |  |  |  |  |  |
| EPUB | xib | xib |  | xib | xib |  |  |

Los formatos de documento compatibles con las funciones de Dynamic Media son los siguientes:

| Formato | Cargar<br> (formato de entrada) | Crear<br> ajuste preestablecido de imagen<br><br> (formato de salida) | Previsualización<br> representación dinámica<br> | Entregar<br> representación dinámica<br> | Descargar<br> representación dinámica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | xib | xib | xib | xib | xib |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | xib |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Además de la funcionalidad anterior, considere lo siguiente:

* Para utilizar Dynamic Media para generar representaciones dinámicas para archivos PDF, consulte [Formatos de archivo Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para utilizar Dynamic Media para la previsualización y generación de representaciones dinámicas para archivos AI, consulte [Formatos de archivo Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para utilizar Dynamic Media para generar representaciones dinámicas para archivos INDD, consulte [Formato de archivo InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formatos multimedia {#supported-multimedia-formats}

| Formato | Almacenamiento | Gestión de metadatos | Extracción de metadatos | Generación de miniaturas | Transcodificación FFMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | xib | xib |  | - | * |
| MIDI | xib | xib |  | - | * |
| 3GP | xib | xib |  | - | * |
| MP3 | xib | xib | xib | - | * |
| MPG | xib | xib |  | - | * |
| OGA | xib | xib |  | - | * |
| OGG | xib | xib |  | - | * |
| RA | xib | xib |  | - | * |
| WAV | xib | xib |  | - | * |
| WMA | xib | xib |  | - | * |
| DVI | xib | xib |  | * | * |
| FLV | xib | xib |  | * | * |
| M4V | xib | xib |  | * | * |
| MPEG | xib | xib |  | * | * |
| OGV | xib | xib |  | * | * |
| MOV | xib | xib |  | * | * |
| WMV | xib | xib |  | * | * |
| SWF | xib | xib |  |  |  |

## Formatos de vídeo de entrada para Dynamic Media Transcoding {#supported-input-video-formats-for-dynamic-media-transcoding}

| Extensión de archivo de vídeo | Contenedor | Códecs de vídeo recomendados | Códecs de vídeo no compatibles |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (todos los perfiles) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 y HQ, XDCAM de Sony, DVCAM de Sony, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, animación de Apple |
| FLV, F4V | Flash Adobe | H264/AVC, Flix VP6, H263, Sorenson | SWF (archivos de animación vectorial) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | Intercalación A/V | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Vídeo rojo sin formato | MJPEG 2000 |  |
| RAM, RM | RealVideo | No admitido | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Flac nativo | Códec de audio sin pérdida gratuito |  |
| MJ2 | Motion JPEG 2000 | Códec Motion JPEG 2000 |  |

## Formatos de archivo {#supported-archive-formats}

Los formatos de archivo admitidos y la aplicabilidad de los flujos de trabajo DAM comunes se tratan en la siguiente tabla.

| Formato | Almacenamiento | Versiones | Flujo de trabajo | Publicación | Control de acceso | Dynamic Media Envío |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | xib | xib | xib | xib | xib |  |
| JAR | xib | xib | xib | xib | xib |  |
| RAR | xib | xib | xib | xib | xib |  |
| TAR | xib | xib | xib | xib | xib |  |
| ZIP **†** | xib | xib | xib | xib | xib | xib |

**†** La imagen combinada se extrae del archivo PSD. Se trata de una imagen generada por Adobe Photoshop y incluida en el archivo PSD. Según la configuración, la imagen combinada puede ser o no la imagen real. Los archivos ZIP creados con el algoritmo `Deflate64` tienen soporte limitado en AEM. No se admiten las operaciones de archivado y desarchivado. Sin embargo, se admiten operaciones como cargar, explorar y descargar.

## Otros formatos admitidos {#other-supported-formats}

La aplicabilidad de flujos de trabajo DAM comunes para algunos otros formatos de archivo se describe en la tabla siguiente.

| Formato | Almacenamiento | Versiones | Flujo de trabajo | Publicación | Control de acceso | Dynamic Media Envío |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | xib | xib | xib | xib | xib |  |
| SVG | xib | xib | xib | xib | xib |  |
| CSS | xib | xib | xib | xib | xib | xib |
| VTT | xib | xib | xib | xib | xib | xib |
| XML | xib | xib | xib | xib | xib | xib |
| JavaScript (cuando se configura con su propio dominio de envío) |  |  |  |  |  | xib |

**#** Los otros formatos se admiten en DAM para almacenamiento, control de versiones, ACL, flujo de trabajo, publicación y administración de metadatos.

## Tipos MIME admitidos {#supported-mime-types}

De forma predeterminada, AEM detecta el tipo de archivo con la extensión. AEM detectarlo desde el contenido de los archivos. Para esto último, seleccione la opción [!UICONTROL Detectar MIME del contenido] en [!UICONTROL Servicio de tipo de MIME DAM de CQ de día] en la consola web de AEM.

Una lista de tipos MIME admitidos está disponible en CRXDE Lite en `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Extensión de archivo | Tipo MIME/tipo de medio de Internet | Valor de jobParam predeterminado | Valor de jobParam permitido |
|---|---|---|---|
| Imagen | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | El jobParam predeterminado se aplica a todos los recursos de tipo MIME de imagen.<ul><li>[knockoutBackgroundOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>aplicación/postscript</li><li>aplicación/pasos</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | vídeo/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | vídeo/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | aplicación/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| TTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | vídeo/dvd |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Habilite la compatibilidad](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) con los parámetros de trabajo de carga de Recursos/Scene7 basados en tipos MIME.
>* [Configure la compatibilidad](config-dynamic.md) de los parámetros de trabajo de carga según el tipo MIME.

