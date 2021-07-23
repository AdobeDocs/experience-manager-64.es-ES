---
title: Administre metadatos de sus recursos digitales en [!DNL Adobe Experience Manager].
description: Obtenga información sobre los tipos de metadatos y cómo [!DNL Adobe Experience Manager Assets] helps manage metadata for assets to allow easier categorization and organization of assets. [!DNL Experience Manager] permite organizar y procesar automáticamente los recursos en función de sus metadatos.
contentOwner: AG
feature: Etiquetado, metadatos
role: Architect, Leader
exl-id: 05bbf89a-4cf5-49bb-aea8-a585c641eda2
source-git-commit: fc725206728e238ab9da1fb30cee8fb407257b62
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 0%

---

# Administrar metadatos de los recursos digitales {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] conserva los metadatos de cada recurso. Permite una categorización y organización más sencillas de los recursos, y ayuda a las personas que buscan un recurso específico. Con la capacidad de extraer metadatos de archivos cargados en [!DNL Experience Manager Assets], la administración de metadatos se integra con el flujo de trabajo creativo. Con la capacidad de mantener y administrar metadatos con los recursos, puede organizar y procesar automáticamente los recursos en función de sus metadatos.

* [Metadatos XMP](xmp.md).
* [Cómo editar o añadir metadatos](meta-edit.md).
* [Referencia de esquemas de metadatos](meta-ref.md).

## ¿Por qué necesitamos metadatos? {#why-we-need-metadata}

Metadatos significa datos sobre los datos. A este respecto, los datos hacen referencia a su recurso digital, por ejemplo una imagen. Los metadatos son esenciales para una administración eficiente de los recursos.

Los metadatos son la recopilación de todos los datos disponibles para un recurso, pero no necesariamente están contenidos en esa imagen. Algunos ejemplos de metadatos son:

* Nombre del recurso.
* Hora y fecha de la última modificación.
* Tamaño del recurso tal como se almacenó en el repositorio.
* Nombre de la carpeta en la que está contenido.
* Recursos relacionados o etiquetas aplicadas.

Lo anterior son las propiedades de metadatos básicas que [!DNL Experience Manager] puede administrar para los recursos, lo que permite a los usuarios ver todos los recursos. Por ejemplo, ordenar recursos por fecha de la última modificación resulta útil cuando se intenta descubrir los recursos añadidos recientemente.

Puede agregar más datos de alto nivel a los recursos digitales, por ejemplo:

* Tipo de recurso (¿es una imagen, un vídeo, un clip de audio o un documento?).
* Propietario del recurso.
* Título del recurso.
* Descripción del recurso.
* Etiquetas asignadas a un recurso.

Más metadatos le ayudan a categorizar los recursos y resulta útil a medida que aumenta la cantidad de información digital. Es posible administrar algunos cientos de archivos basados en solo los nombres de archivo. Sin embargo, este enfoque no es escalable. Se queda corto cuando aumenta el número de personas involucradas y el número de activos gestionados.

Con la adición de metadatos, el valor de un recurso digital aumenta, ya que el recurso se convierte en,

* Más accesible: los sistemas y usuarios pueden encontrarlo fácilmente.
* Más fácil de administrar: puede encontrar recursos con el mismo conjunto de propiedades más fácilmente y aplicarles cambios.
* Completado : el recurso conlleva más información y contexto con más metadatos.

Por estos motivos, [!DNL Assets] le proporciona los medios adecuados para crear, administrar e intercambiar metadatos para sus recursos digitales.

## Tipos de metadatos {#types-of-metadata}

Los dos tipos básicos de metadatos son metadatos técnicos y metadatos descriptivos.

Los metadatos técnicos son útiles para las aplicaciones de software que se ocupan de recursos digitales y no deben mantenerse manualmente. [!DNL Experience Manager Assets] y otro software determinan automáticamente los metadatos técnicos, y los metadatos pueden cambiar cuando se modifica el recurso. Los metadatos técnicos disponibles de un recurso dependen en gran medida del tipo de archivo del recurso. Algunos ejemplos de metadatos técnicos son:

* Tamaño de un archivo.
* Dimension (altura y anchura) de una imagen.
* Velocidad de bits de un archivo de audio o vídeo.
* Resolución (nivel de detalle) de una imagen.

Los metadatos descriptivos son metadatos relacionados con el dominio de la aplicación, por ejemplo, el negocio del que proviene un recurso. Los metadatos descriptivos no se pueden determinar automáticamente. Se crea de forma manual o semiautomática. Por ejemplo, una cámara con GPS puede rastrear automáticamente la latitud y la longitud y añadir la etiqueta geográfica de la imagen.

El coste de crear manualmente información de metadatos descriptivos es alto. Por lo tanto, se establecen estándares para facilitar el intercambio de metadatos entre sistemas y organizaciones de software. [!DNL Experience Manager Assets] admite todas las normas pertinentes para la gestión de metadatos.

## Normas de codificación {#encoding-standards}

Existen varias formas de incrustar metadatos en archivos. Se admite una selección de estándares de codificación:

* XMP: utilizado por [!DNL Assets] para almacenar los metadatos extraídos dentro del repositorio.
* ID3: para archivos de audio y vídeo.
* Exif: para archivos de imagen.
* Otros/Heredados: desde [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) es un estándar abierto que utiliza  [!DNL Experience Manager Assets] para toda la administración de metadatos. El estándar ofrece una codificación de metadatos universal que se puede incrustar en todos los formatos de archivo. Adobe y otras empresas admiten XMP estándar, ya que proporciona un modelo de contenido enriquecido. Los usuarios de XMP estándar y de [!DNL Experience Manager Assets] tienen una potente plataforma en la que basarse. Para obtener más información, consulte [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Los datos almacenados en estas etiquetas ID3 se muestran al reproducir un archivo de audio digital en el equipo o en un reproductor MP3 portátil.

Las etiquetas ID3 están diseñadas para el formato de archivo MP3. Información adicional sobre formatos:

* Las etiquetas ID3 funcionan en archivos MP3 y mp3PRO.
* WAV no tiene etiquetas.
* WMA tiene etiquetas propietarias que no permiten la implementación de código abierto.
* Ogg Vorbis utiliza Comentarios Xiph incrustados en el contenedor Ogg.
* AAC utiliza un formato de etiquetado propietario.

### Exif {#exif}

El formato de archivo de imagen intercambiable (Exif) es el formato de metadatos más utilizado en la fotografía digital. Proporciona una forma de integrar un vocabulario fijo de propiedades de metadatos en muchos formatos de archivo, como JPEG, TIFF, RIFF y WAV. Exif almacena metadatos como pares de un nombre de metadatos y un valor de metadatos. Estos pares de metadatos nombre-valor también se denominan etiquetas, no confundirlos con el etiquetado de [!DNL Experience Manager]. Las cámaras digitales modernas crean metadatos Exif y el software de gráficos moderno lo admite. El formato Exif es el denominador común más bajo para la administración de metadatos, especialmente para imágenes.

Una limitación importante de Exif es que algunos formatos de archivo de imagen populares como BMP, GIF o PNG no los admiten.

Los campos de metadatos definidos por Exif suelen ser de naturaleza técnica y su uso es limitado para la administración de metadatos descriptivos. Por este motivo, [!DNL Experience Manager Assets] ofrece la asignación de propiedades Exif en [esquemas de metadatos comunes](metadata-schemas.md) y en [XMP](xmp-writeback.md).

### Otros metadatos {#other-metadata}

Otros metadatos que se pueden incrustar desde archivos son [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], etc.

## Esquemas de metadatos {#metadata-schemata}

Los esquemas de metadatos son conjuntos predefinidos de definiciones de propiedades de metadatos que se pueden utilizar en varias aplicaciones. Las propiedades siempre están asociadas a un recurso, lo que significa que las propiedades son &quot;about&quot; el recurso.

También puede diseñar sus propios esquemas de metadatos si no existe ninguno que se ajuste a sus necesidades. No duplique la información existente. Dentro de una organización, la separación de esquemas facilita el uso compartido de metadatos. [!DNL Experience Manager] proporciona una lista predeterminada de los esquemas de metadatos más populares. La lista le ayuda a poner en marcha su estrategia de metadatos y a elegir rápidamente las propiedades de metadatos que necesita.

A continuación se enumeran los esquemas de metadatos admitidos.

### Metadatos estándar {#standard-metadata}

* DC - [!DNL Dublin Core] es un conjunto importante y ampliamente utilizado de metadatos.
* DICOM - Imágenes digitales y comunicaciones en medicina.
* `Iptc4xmpCore` y  `iptc4xmpExt` - International Press Communications Standard contiene muchos metadatos específicos de cada tema.
* RDF - Marco de descripción de recursos - para metadatos web semánticos genéricos.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - Entradas de trabajo básicas.

### Metadatos específicos de la aplicación {#application-specific-metadata}

Los metadatos específicos de la aplicación incluyen metadatos técnicos y descriptivos. Si utiliza estos metadatos, es posible que otras aplicaciones no puedan utilizarlos. Por ejemplo, es posible que una aplicación de renderización de imágenes diferente no pueda acceder a los metadatos [!DNL Adobe Photoshop]. Puede crear un paso de flujo de trabajo que cambie una propiedad específica de la aplicación a una propiedad estándar.

* ACDSee: metadatos administrados por el programa [!DNL ACDSee]. Consulte [www.acdsee.com/](https://www.acdsee.com/).
* Álbum - [!DNL Adobe Photoshop Album].
* CQ - Utilizado por [!DNL Experience Manager Assets].
* DAM - Utilizado por [!DNL Experience Manager Assets].
* DEX - [Optima SC Description explorer](http://www.optimasc.com/products/dex/index.html) es una colección de herramientas para la administración de metadatos y archivos para sistemas operativos Windows.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto y MP - Microsoft Photo.
* PDF y PDF/X.
* Photoshop y psAux: [!DNL Adobe Photoshop].

### Metadatos de Digital Rights Management {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* ADEMÁS: [Picture Licensing Universal System](https://www.useplus.com).
* PRISM - [Requisitos de publicación para metadatos estándar del sector](https://www.idealliance.org/prism-metadata).
* PRL - lenguaje de derechos PRISM.
* PUR - Derechos de uso de PRISM.
* `xmpPlus` - Integración de PLUS con XMP.

### Metadatos específicos de la fotografía {#photography-specific-metadata}

* Exif - Información técnica de la cámara, incluida la posición GPS.
* CRS - [!DNL Camera Raw] esquema.
* `iptc4xmpCore` y `iptc4xmpExt`.
* TIFF: metadatos de imagen (no solo para imágenes TIFF).

### Metadatos específicos de impresión {#print-specific-metadata}

* PDF y PDF/X - Adobe PDF y aplicaciones de terceros.
* PRISM - [Requisitos de publicación para metadatos estándar del sector](http://www.prismstandard.org/specifications/).
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - XMP metadatos para texto paginado.

### Metadatos específicos de multimedia {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - Administración de medios.

## Flujos de trabajo impulsados por metadatos {#metadata-driven-workflows}

La creación de flujos de trabajo impulsados por metadatos ayuda a automatizar algunos procesos, lo que mejora la eficacia. En un flujo de trabajo impulsado por metadatos, el sistema de administración del flujo de trabajo lee el flujo de trabajo y, como resultado, realiza alguna acción predefinida. Por ejemplo, algunas de las formas en que puede utilizar flujos de trabajo basados en metadatos:

* El flujo de trabajo puede comprobar si una imagen tiene un título o no. Si no es así, el sistema notifica que debe añadir un título.
* El flujo de trabajo puede comprobar si un aviso de copyright de un recurso permite la distribución o no. Por lo tanto, el sistema envía el recurso a un servidor o a otro.
* Un flujo de trabajo puede comprobar los recursos sin metadatos predefinidos obligatorios ni con metadatos *no válidos*.
