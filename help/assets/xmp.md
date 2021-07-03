---
title: Metadatos de XMP
description: Obtenga información sobre el estándar de metadatos XMP (Extensible Metadata Platform) que utiliza AEM Assets para la administración de metadatos. XMP proporciona un formato estándar para la creación, el procesamiento y el intercambio de metadatos para una amplia variedad de aplicaciones.
contentOwner: AG
feature: Metadatos
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 19%

---

# Metadatos XMP {#xmp-metadata}

XMP (Extensible Metadata Platform) es el estándar de metadatos que AEM Assets utiliza para la administración de todos los metadatos. XMP proporciona un formato estándar para la creación, el procesamiento y el intercambio de metadatos para una amplia variedad de aplicaciones.

Además de ofrecer codificación de metadatos universal que se puede incrustar en todos los formatos de archivo, XMP proporciona un [modelo de contenido enriquecido](xmp.md#xmp-core-concepts) y es [compatible con Adobe](xmp.md#advantages-of-xmp) y otras empresas, de modo que los usuarios de XMP en combinación con AEM Assets tengan una potente plataforma en la que basarse.

La [especificación de XMP](https://www.adobe.com/devnet/xmp.html) está disponible en el Adobe.

## ¿Qué es XMP? {#what-is-xmp}

AEM Assets es compatible de forma nativa con la XMP: la plataforma de metadatos extensible encabezada por el Adobe. XMP es un estándar para procesar y almacenar metadatos estandarizados y de propiedad en recursos digitales. XMP está diseñado para ser el estándar común que permite que varias aplicaciones funcionen eficazmente con metadatos.

Los profesionales de producción, por ejemplo, utilizan la compatibilidad XMP integrada en las aplicaciones de Adobe para pasar información a través de varios formatos de archivo. El repositorio de AEM Assets extrae los metadatos de XMP y los utiliza para administrar el ciclo de vida del contenido y ofrece la capacidad de crear flujos de trabajo de automatización.

XMP estandariza la forma en que se definen, crean y procesan los metadatos proporcionando un modelo de datos, un modelo de almacenamiento y esquemas. Todos estos conceptos se tratan en esta sección.

Todos los metadatos heredados de EXIF, ID3 o Microsoft Office se traducen automáticamente a XMP, lo que se puede ampliar para admitir esquemas de metadatos específicos del cliente, como catálogos de productos.

Los metadatos de XMP constan de un conjunto de propiedades. Estas propiedades siempre están asociadas con un\
entidad concreta denominada recurso; es decir, las propiedades son &quot;about&quot; el recurso. En el caso de XMP, el recurso siempre es el recurso.

### Adobe {#adobe}

Adobe introdujo primero el XMP estándar como parte del producto de software de Adobe Acrobat. Desde entonces, la norma XMP ha sido ampliamente adoptada.

### XMP ecosistema {#xmp-ecosystem}

XMP define un modelo de [metadatos](https://es.wikipedia.org/wiki/Metadatos) que se puede utilizar con cualquier conjunto definido de elementos de metadatos. XMP también define [esquemas](https://en.wikipedia.org/wiki/XML_schema) específicos para propiedades básicas útiles para registrar el historial de un recurso a medida que pasa por varios pasos de procesamiento, desde ser fotografiado, [escaneado](https://es.wikipedia.org/wiki/Esc%C3%A1ner_inform%C3%A1tico) o creado como texto, pasando por etapas de edición fotográfica (como [recorte](https://en.wikipedia.org/wiki/Cropping_%28image%29) o ajuste de color), hasta ensamblarse en una imagen final. XMP permite a cada programa o dispositivo de software añadir su propia información a un recurso digital, que se puede retener en el archivo digital final.

XMP se serializa y almacena con mayor frecuencia mediante un subconjunto del [W3C](https://es.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF), que a su vez se expresa en [XML](https://en.wikipedia.org/wiki/XML).

## Ventajas de XMP {#advantages-of-xmp}

XMP tiene las siguientes ventajas sobre otros estándares y esquemas de codificación:

* Los metadatos basados en XMP son muy potentes y detallados.
* XMP permite tener varios valores para una propiedad.
* XMP tiene codificación estandarizada, lo que permite intercambiar fácilmente metadatos.
* XMP es extensible. Puede añadir información adicional a los recursos.

### Extensible {#extensible}

El XMP estándar está diseñado para ser extensible, lo que le permite añadir tipos de metadatos personalizados a los datos de XMP. EXIF, por otro lado, no tiene - tiene una lista fija de propiedades que no se pueden ampliar.

>[!NOTE]
>
>XMP generalmente no permite incrustar tipos de datos binarios. Para cargar datos binarios en XMP, por ejemplo, imágenes en miniatura, deben codificarse en un formato compatible con XML, como Base64.

## XMP Conceptos principales {#xmp-core-concepts}

Las secciones siguientes describen los conceptos principales de XMP, incluidos los espacios de nombres y esquemas, las propiedades y los valores, y las alternativas de idioma.

### Espacios de nombres y esquemas {#namespaces-and-schemata}

Un esquema XMP es un conjunto de nombres de propiedades en un espacio de nombres XML común que incluye\
el tipo de datos y la información descriptiva. Un esquema XMP se identifica mediante su URI de área de nombres XML. El uso de áreas de nombres evita conflictos entre propiedades en distintos esquemas que tienen el mismo nombre pero un significado diferente.

Por ejemplo, la propiedad **Creator** en dos esquemas diseñados de forma independiente puede significar la persona que creó el recurso o puede significar la aplicación que lo creó (por ejemplo, Adobe Photoshop).

### Propiedades y valores {#properties-and-values}

XMP incluir propiedades de uno o varios esquemas.

Por ejemplo, un subconjunto típico utilizado por muchas aplicaciones de Adobe puede incluir lo siguiente:

* Esquema central de Dublín: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP esquema básico: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* esquema de administración de derechos de XMP: xmpRights:WebStatement, xmpRights:Marked
* esquema XMP media management: xmpMM:DocumentID

### Alternativas de idioma {#language-alternatives}

XMP le ofrece la posibilidad de agregar una propiedad **xml:lang** a las propiedades de texto para especificar el idioma del texto.
