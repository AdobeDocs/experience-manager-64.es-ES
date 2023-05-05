---
title: Conceptos básicos de los componentes de Communities
seo-title: Communities Components Basics
description: Agregar funciones de Communities a sitios AEM en modo de edición y configurar componentes
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: 17fbee1c-5657-442a-8c9d-1456b853f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 3%

---

# Conceptos básicos de los componentes de Communities {#communities-components-basics}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

La sección de creación de la documentación describe la adición de funciones de Communities a sitios AEM en modo de edición de autor, así como la descripción de configuraciones de componentes.

Los componentes se pueden explorar mediante una instancia de AEM y la [Guía de componentes de comunidad](components-guide.md).

## Acceso a componentes de Communities {#accessing-communities-components}

Al crear contenido de página, si la plantilla subyacente permite realizar cambios en el diseño de la página, es posible habilitar componentes que no están disponibles en el explorador de componentes como parte del diseño del sitio.

Se muestran los componentes de Communities disponibles [here](author-communities.md#available-communities-components).

>[!NOTE]
>
>Para obtener información general sobre la creación, consulte [guía rápida para la creación de páginas](../../help/sites-authoring/qg-page-authoring.md).
>
>Si no está familiarizado con AEM, consulte la documentación de [tratamiento básico](../../help/sites-authoring/basic-handling.md).

### Introducción al modo de diseño {#entering-design-mode}

Si **Comunidades** no se encuentra en el navegador de componentes (barra de tareas), será necesario introducir `Design Mode` para agregar otros componentes de Communities. [Bibliotecas de cliente necesarias](#required-clientlibs) (clientlibs) también puede ser necesario añadirlo.

Para obtener más información, consulte [Configuración de componentes en modo de diseño](../../help/sites-authoring/default-components-designmode.md).

A continuación se muestran imágenes de la selección de algunos componentes de Communities y su visualización en el navegador de componentes:

![chlimage_1-424](assets/chlimage_1-424.png)

Los componentes seleccionados ya están disponibles en el navegador de componentes:

![chlimage_1-425](assets/chlimage_1-425.png)

## Clientlibs requeridos {#required-clientlibs}

[Bibliotecas del lado cliente](../../help/sites-developing/clientlibs.md) (clientlibs) son necesarios para el correcto funcionamiento (JavaScript) y estilo (CSS) de un componente.

Al añadir un componente Comunidades a una página, si el resultado es un error o un aspecto inesperado, lo primero que hay que intentar es añadir los clientlibs necesarios para el componente Comunidades. Para obtener más información, consulte [Clientlibs para componentes de Communities](clientlibs.md).

### Ejemplo: Revisiones colocadas inicialmente sin bibliotecas de cliente... {#example-initially-placed-reviews-without-client-libraries}

![chlimage_1-426](assets/chlimage_1-426.png)

### ... Y con bibliotecas de cliente {#and-with-client-libraries}

![chlimage_1-427](assets/chlimage_1-427.png)

## Etiquetado {#tagging}

Se pueden configurar muchas funciones de Communities para permitir que los miembros etiqueten el contenido introducido (publicado) en el entorno de publicación.

Si se permite el etiquetado, la configuración del sitio de la comunidad se puede establecer para limitar las áreas de nombres presentadas a los miembros en el entorno de publicación. Consulte la [Consola Sitios de comunidad](sites-console.md#tagging).

Funciones que permiten el etiquetado: [blog](blog-feature.md), [calendario](calendar.md), [biblioteca de archivos](file-library.md), [foro](forum.md)

Funciones que utilizan etiquetas: [catálogo](catalog.md), [búsqueda](search.md), [nube de etiquetas sociales](tagcloud.md)

Para obtener información sobre la creación:

* [Uso de etiquetas](../../help/sites-authoring/tags.md)

Para información administrativa:

* Creación de espacios de nombres de etiquetas (taxonomía): [Administración de etiquetas](../../help/sites-administering/tags.md)
* Configuración del sitio de la comunidad: see [ETIQUETADO](sites-console.md#tagging)
* [Etiquetado del contenido generado por el usuario](../../help/sites-authoring/tags.md)
* [Etiquetado de recursos de habilitación](tag-resources.md)

Para obtener información del desarrollador:

* [Marco de trabajo de etiquetado de AEM](../../help/sites-developing/framework.md)
* [Aspectos básicos del etiquetado](tag.md)
