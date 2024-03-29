---
title: Formatos de archivo compatibles con [!DNL Experience Manager] Recursos
description: Lista de formatos de archivo y tipos MIME admitidos por Assets y las funciones admitidas para cada formato.
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 11%

---

# Formatos de archivo compatibles con [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager Assets] admite una amplia gama de formatos de archivo y cada funcionalidad tiene compatibilidad variada con distintos tipos de MIME.

Para integrar [!DNL Assets] con otras soluciones de gestión de recursos digitales (DAM) compatibles con los estándares y software de escritorio, utilice la Extensible Metadata Platform (XMP) de Adobe.

Utilice la leyenda para comprender el nivel de compatibilidad.

| Nivel de soporte | Descripción |
|:---:|---|
| ✓ | Compatibilidad |
| &#42; | Compatible con funciones de complemento |
| − | No aplicable |

## Formatos de imagen rasterizados {#supported-raster-image-formats}

Los formatos de imagen rasterizados admitidos para las funciones de administración de recursos son los siguientes:

| Formato | Almacenamiento | Gestión de metadatos | Extracción de metadatos | Generación de miniaturas | Edición interactiva | Reescritura de metadatos | Perspectivas |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD **‡** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**}** La imagen combinada se extrae del archivo PSD. Es una imagen que genera Adobe Photoshop y que se incluye en el archivo PSD. Dependiendo de la configuración, la imagen combinada puede ser o no la imagen real.

Los formatos de imagen rasterizados admitidos para las funciones de Dynamic Media son los siguientes:

| Formato | Cargar<br> (Formato de entrada) | Crear<br> image<br> ajuste preestablecido<br> (Formato de salida) | Vista previa<br> dinámico<br> representación | Entrega<br> dinámico<br> representación | Descargar<br> dinámico<br> representación |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**}** La imagen combinada se extrae del archivo PSD. Es una imagen que genera Adobe Photoshop y que se incluye en el archivo PSD. Dependiendo de la configuración, la imagen combinada puede ser o no la imagen real.

Además de la información anterior, considere lo siguiente:

* La compatibilidad con archivos EPS se aplica solo a imágenes de trama. Por ejemplo, la generación de miniaturas para imágenes vectoriales de EPS no es compatible de forma predeterminada. Para agregar compatibilidad, [configurar ImageMagick](best-practices-for-imagemagick.md). Para integrar herramientas de terceros para habilitar funciones adicionales, consulte [Controlador de medios basado en líneas de comandos](media-handlers.md#command-line-based-media-handler).

* La reescritura de metadatos funciona para el formato de archivo PSB cuando se agrega al `NComm` controlador.

* Para utilizar Dynamic Media para obtener una vista previa y generar representaciones dinámicas de archivos EPS, consulte [Formatos de archivo Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para los archivos EPS, la reescritura de metadatos es compatible con la versión 3.0 o posterior del Convenio de estructura de documentos de PostScript (PS-Adobe).

## Formatos de imagen de trama no admitidos en Dynamic Media {#unsupported-image-formats-dynamic-media}

La siguiente lista describe los subtipos de formatos de archivo de imagen de trama que se *not* compatible con Dynamic Media.

Consulte también [Detectar formatos de archivo no compatibles para Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* Los archivos PNG que tienen un tamaño de fragmento IDAT tienen un tamaño bueno de más de 100 MB.
* Archivos PSB.
* Los archivos PSD con un espacio de color distinto de CMYK, RGB, escala de grises o mapa de bits no son compatibles. Los espacios de color DuoTone, Lab e Indexed no son compatibles.
* archivos PSD con una profundidad buena superior a 16.
* archivos TIFF que tienen datos de coma flotante.
* Archivos TIFF que tienen espacio de color Lab.

## Biblioteca PDF Rasterizer {#supported-pdf-rasterizer-library}

La biblioteca Adobe PDF Rasterizer genera miniaturas y previsualizaciones de alta calidad para archivos Adobe Illustrator y PDF grandes y con gran contenido. Adobe recomienda utilizar la biblioteca PDF Rasterizer para lo siguiente:

* Archivos AI/PDF con gran cantidad de contenido que requieren muchos recursos para su procesamiento.
* Archivos AI/PDF para los que no se generan miniaturas de forma predeterminada.
* Archivos AI con colores del sistema de coincidencia de Pantone (PMS).

Consulte [Uso del rasterizador del PDF](aem-pdf-rasterizer.md).

## Biblioteca de transcodificación de imágenes {#supported-image-transcoding-library}

La biblioteca de transcodificación de imágenes de Adobe es una solución de procesamiento de imágenes que realiza funciones básicas de gestión de imágenes, como codificación, transcodificación, remuestreo y cambio de tamaño.

La biblioteca de transcodificación de imágenes admite los tipos MIME JPG/JPEG, PNG (8 y 16 bits), GIF, BMP, TIFF/comprimido (excepto los archivos TIFF de 32 bits y los archivos PTIFF), ICO e ICN.

Consulte [Biblioteca de transcodificación de imágenes](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

La biblioteca de Adobe Camera Raw habilita [!DNL Assets] para ingerir imágenes sin procesar. Consulte [Compatibilidad Camera Raw](camera-raw.md).

## Formatos de documento {#supported-document-formats}

Los formatos de documento admitidos para las funciones de administración de recursos son los siguientes:

| Formato | Almacenamiento | Metadatos<br> administración | Texto completo<br> extracción | Metadatos<br> extracción | Miniatura<br> generación | Subconjunto<br> extracción | Metadatos<br> reescritura |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODT | ✓ | ✓ | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  |
| RTF | ✓ | ✓ | ✓ |  |  |  |  |
| TXT | ✓ | ✓ | ✓ |  |  |  |  |
| XLS | ✓ | ✓ | ✓ |  |  |  |  |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| ePub | ✓ | ✓ |  | ✓ | ✓ |  |  |

Los formatos de documento admitidos para las funciones de Dynamic Media son los siguientes:

| Formato | Cargar<br> (Formato de entrada) | Crear<br> image<br> ajuste preestablecido<br> (Formato de salida) | Vista previa<br> dinámico<br> representación | Entrega<br> dinámico<br> representación | Descargar<br> dinámico<br> representación |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) (Consulte la nota siguiente) | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| ePub |  |  |  |  |  |

>[!NOTE]
>
>Para PDF seguros, solo se admite Cargar .

Además de la funcionalidad anterior, considere lo siguiente:

* Para utilizar Dynamic Media para generar representaciones dinámicas para archivos PDF, consulte [Formatos de archivo Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para utilizar Dynamic Media para obtener una vista previa y generar representaciones dinámicas para archivos AI, consulte [Formatos de archivo Adobe Illustrator (AI), Postscript (EPS) y PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para utilizar Dynamic Media para generar representaciones dinámicas para archivos INDD, consulte [Formato del archivo InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formatos multimedia {#supported-multimedia-formats}

| Formato | Almacenamiento | Gestión de metadatos | Extracción de metadatos | Generación de miniaturas | Transcodificación FFMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | − | &#42; |
| MIDI | ✓ | ✓ |  | − | &#42; |
| 3GP | ✓ | ✓ |  | − | &#42; |
| MP3 | ✓ | ✓ | ✓ | − | &#42; |
| MPG | ✓ | ✓ |  | − | &#42; |
| OGA | ✓ | ✓ |  | − | &#42; |
| OGG | ✓ | ✓ |  | − | &#42; |
| RA | ✓ | ✓ |  | − | &#42; |
| WAV | ✓ | ✓ |  | − | &#42; |
| WMA | ✓ | ✓ |  | − | &#42; |
| DVI | ✓ | ✓ |  | &#42; | &#42; |
| FLV | ✓ | ✓ |  | &#42; | &#42; |
| M4V | ✓ | ✓ |  | &#42; | &#42; |
| MPEG | ✓ | ✓ |  | &#42; | &#42; |
| OGV | ✓ | ✓ |  | &#42; | &#42; |
| MOV | ✓ | ✓ |  | &#42; | &#42; |
| WMV | ✓ | ✓ |  | &#42; | &#42; |
| SWF | ✓ | ✓ |  |  |  |

## Formatos de vídeo de entrada para la transcodificación de Dynamic Media {#supported-input-video-formats-for-dynamic-media-transcoding}

| Extensión de archivo de vídeo | Contenedor | Códecs de vídeo recomendados | Códecs de vídeo no compatibles |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (todos los perfiles) |  |
| MOV, QT | QuickTime de Apple | H264/AVC, Apple ProRes422 &amp; HQ, XDCAM de Sony, DVCAM de Sony, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermedio, animación de Apple |
| FLV, F4V | Flash de Adobe | H264/AVC, Flix VP6, H263, Sorenson | SWF (archivos de animación vectoriales) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Pantalla de Microsoft (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | Intercalación A/V | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | XDCAM de Sony, MPEG-2, MPEG-4, DVCP de Panasonic |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Vídeo rojo sin procesar | MJPEG 2000 |  |
| RAM, RM | RealVideo | No admitido | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Flac nativo | Códec de audio sin pérdidas gratuito |  |
| MJ2 | JPEG de movimiento 2000 | Códec Motion JPEG 2000 |  |

## Formatos de archivo {#supported-archive-formats}

Los formatos de archivo compatibles y la aplicabilidad de los flujos de trabajo DAM comunes se tratan en la siguiente tabla.

| Formato | Almacenamiento | Versiones | Flujo de trabajo | Publicación | Control de acceso | Entrega en Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** La imagen combinada se extrae del archivo PSD. Es una imagen que genera Adobe Photoshop y que se incluye en el archivo PSD. Dependiendo de la configuración, la imagen combinada puede ser o no la imagen real. Los archivos ZIP creados con `Deflate64` tiene compatibilidad limitada en AEM. No se admiten las operaciones de archivado y desarchivado. Sin embargo, se admiten operaciones como la carga, la navegación y la descarga.

## Otros formatos admitidos {#other-supported-formats}

La aplicabilidad de los flujos de trabajo DAM comunes para otros formatos de archivo se describe en la siguiente tabla.

| Formato | Almacenamiento | Versiones | Flujo de trabajo | Publicación | Control de acceso | Entrega en Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript (cuando se configura con su propio dominio de envío) |  |  |  |  |  | ✓ |

**#** Los demás formatos son compatibles con DAM para almacenamiento, versiones, ACL, flujo de trabajo, publicación y administración de metadatos.

## Tipos MIME admitidos {#supported-mime-types}

De forma predeterminada, [!DNL Experience Manager] detecta el tipo de archivo con la extensión de archivo . [!DNL Experience Manager] puede detectarlo a partir del contenido de los archivos. Para este último, seleccione [!UICONTROL Detectar MIME del contenido] en [!UICONTROL Servicio Day CQ DAM Mime Type] en el [!DNL Experience Manager] Consola web.

Una lista de tipos MIME admitidos está disponible en CRXDE Lite en `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Extensión de archivo | Tipo MIME/ Tipo de medio de Internet | Valor predeterminado de jobParam | Valor de jobParam permitido |
|---|---|---|---|
| Imagen | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | El jobParam predeterminado se aplica a todos los recursos de tipo mime de imagen.<ul><li>[knockoutBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unSharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>aplicación/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Habilite la compatibilidad con los parámetros de trabajo de carga de recursos/Dynamic Media Classic basados en tipos MIME](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).
>* [Configuración de la compatibilidad con los parámetros de trabajo de carga basada en tipos MIME](config-dynamic.md).

