---
title: Buscar recursos en AEM
description: Obtenga información sobre cómo encontrar los recursos necesarios en AEM mediante el panel Filtros y cómo utilizar los recursos que aparecen en la búsqueda.
contentOwner: AG
feature: Buscar,Metadatos
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 2%

---

# Buscar recursos en AEM {#search-assets-in-aem}

Obtenga información sobre cómo encontrar los recursos necesarios en AEM mediante el panel Filtros y cómo utilizar los recursos que aparecen en la búsqueda.

Utilice el panel Filtros para buscar recursos, carpetas, etiquetas y metadatos. Puede buscar partes de una cadena utilizando el asterisco comodín.

El panel Filtros ofrece varias opciones para buscar recursos y carpetas de varias formas en lugar de hacerlo en un orden taxonómico genérico.

Puede buscar en función de las siguientes opciones (predicados):

* Tipo de archivo
* Tamaño de archivo
* Nombre del campo
* Fecha de última modificación
* Estado
* Orientación
* Estilo
* Perspectivas

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

Puede personalizar el panel Filtros y agregar o eliminar predicados de búsqueda mediante [facetas de búsqueda](search-facets.md). Para mostrar el panel Filtros , realice estos pasos:

1. En la interfaz de usuario de Assets, pulse o haga clic en ![search_icon](assets/search_icon.png) en la barra de herramientas para mostrar el cuadro Omnisearch.
1. Escriba el término de búsqueda y pulse Intro. Como alternativa, simplemente pulse Intro sin introducir ningún término de búsqueda. No introduzca ningún espacio inicial, de lo contrario la búsqueda no funcionará.

1. Toque o haga clic en el icono de navegación global. Se muestra el panel Filtros .

   ![filters_panel-1](assets/filters_panel-1.png)

   Según el tipo de elementos que busque, el número de coincidencias se indica en la parte superior de los resultados de búsqueda.

   ![number_of_searches](assets/number_of_searches.png)

## Buscar tipos de archivo {#search-for-file-types}

El panel Filtros ayuda a añadir más granularidad a la experiencia de búsqueda y hace que la funcionalidad de búsqueda sea más versátil. Puede desplazarse fácilmente hasta el nivel de detalle deseado.

Por ejemplo, si está buscando una imagen, utilice el predicado **[!UICONTROL Tipo de archivo]** para elegir si desea una imagen de mapa de bits o una imagen vectorial.

![image_type](assets/image_type.png)

Puede reducir aún más el ámbito de búsqueda especificando el tipo MIME de la imagen.

![mime_type](assets/mime_type.png)

Del mismo modo, al buscar documentos, puede especificar el formato, por ejemplo PDF o MS Word.

![documentos](assets/documents.png)

## Buscar según el tamaño del archivo {#search-based-on-file-size}

Utilice el predicado **Tamaño de archivo** para buscar recursos en función de su tamaño. Puede especificar los límites inferior y superior del intervalo de tamaño para limitar la búsqueda. También puede especificar la unidad de medida, por ejemplo Kilobytes, Megabytes, etc.

![unit_of_measure](assets/unit_of_measure.png)

## Buscar en función de la última modificación de los recursos {#search-based-on-when-assets-are-last-modified}

Si administra recursos en curso o supervisa un flujo de trabajo de revisión, puede buscar cuándo se modificó un recurso por última vez en función de marcas de hora precisas. Por ejemplo, especifique las fechas antes o después de las cuales se modificaron los recursos.

![last_modified_dates](assets/last_modified_dates.png)

También puede utilizar las siguientes opciones para lograr un nivel de granularidad más alto en la búsqueda:

![timestamp](assets/timestamp.png)

## Búsqueda basada en el estado {#search-based-on-status}

Utilice el predicado **Status** para buscar recursos en función de varios tipos de estado, como Publicar, Aprobación, Cierre de compra y Caducidad.

![estado](assets/status.png)

Por ejemplo, al supervisar la publicación de recursos, puede utilizar la opción adecuada para buscar qué recursos se publican.

![instancias de publicación](assets/publish.png)

Cuando supervise el estado de revisión de los activos, utilice la opción adecuada para encontrar qué activos están aprobados o qué activos están pendientes de aprobación.

![aprobación](assets/approval.png)

## Búsqueda basada en datos de perspectivas {#search-based-on-insights-data}

Utilice el predicado **Insights** para buscar recursos en función de las estadísticas de uso que obtengan de varias aplicaciones Creative. Los datos de uso se agrupan en las siguientes categorías:

* Puntuación de uso
* Impresiones
* Clics
* Canales de medios en los que aparecen los recursos

![perspectivas](assets/insights.png)
