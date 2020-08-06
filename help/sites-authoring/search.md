---
title: 'Búsqueda  '
seo-title: 'Búsqueda  '
description: Encuentre contenido más rápidamente con una búsqueda detallada
seo-description: Encuentre contenido más rápidamente con una búsqueda detallada
uuid: 1e80cf85-653f-4dde-930a-de05415b994f
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: cd87e1e8-5329-4e60-ac9d-2705f54d0da6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 94%

---


# Búsqueda{#search-features}

El entorno de autor AEM ofrece varios mecanismos para buscar contenido, en función del tipo de recurso.

>[!NOTE]
>
>Fuera del entorno de creación también hay otros mecanismos disponibles para buscar, como [Query Builder](/help/sites-developing/querybuilder-api.md) y [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Conceptos básicos de búsqueda {#search-basics}

La función de búsqueda está disponible en la barra de herramientas superior:

![](do-not-localize/chlimage_1-17.png)

Con el carril de búsqueda puede:

* Busque una palabra clave, una ruta o una etiqueta específicas..
* Filtre según los criterios específicos del recurso, como fechas de modificación, estados de página, tamaño de archivo, etc.
* Defina y utilice una [búsqueda guardada](#saved-searches) según los criterios anteriores.

>[!NOTE]
>
>También se puede iniciar una búsqueda con la tecla de función `/` (barra diagonal) cuando el carril de búsqueda esté visible.

## Buscar y filtrar {#search-and-filter}

Para buscar y filtrar sus recursos: 

1. Abra **Buscar** (con la lupa de la barra de herramientas) y escriba el término de búsqueda. Se muestran sugerencias que puede seleccionar:

   ![screen_shot_2018-03-23at101404](assets/screen_shot_2018-03-23at101404.png)

   De forma predeterminada, los resultados de la búsqueda estarán limitados a su ubicación actual (es decir, la consola y el tipo de recurso relacionado): 

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Si es necesario, puede quitar el filtro de ubicación (seleccione **X** en el filtro que desea eliminar) para buscar en todas las consolas/tipos de recurso.
1. Los resultados se muestran agrupados según la consola y el tipo de recurso relacionado.

   Puede seleccionar un recurso específico (para realizar más acciones), o profundizar seleccionando el tipo de recurso necesario; por ejemplo **Ver todos los sitios**: 

   ![screen_shot_2018-03-23at101523](assets/screen_shot_2018-03-23at101523.png)

1. Si desea explorar más en profundidad, seleccione el símbolo de carril (parte superior izquierda) para abrir el panel lateral **Filtros y opciones**.

   ![](do-not-localize/screen_shot_2018-03-23at101542.png)

   Según el tipo de recurso, la búsqueda mostrará una selección predefinida de criterios de búsqueda o de filtro.

   El panel lateral permite seleccionar:

   * Búsquedas guardadas
   * Directorio de búsqueda
   * Etiquetas
   * Criterios de búsqueda; por ejemplo, fechas de modificación, estado de publicación o estado de Live Copy

   >[!NOTE]
   >
   >Los criterios de búsqueda pueden variar:
   >
   >* Según el tipo de recurso que haya seleccionado; por ejemplo, los criterios de comunidades y recursos son comprensivamente especializados.
   >* Su instancia, al igual que los [formularios de búsqueda](/help/sites-administering/search-forms.md), se puede personalizar (según la ubicación en AEM).


   ![screen_shot_2018-03-23at101619](assets/screen_shot_2018-03-23at101619.png)

1. También se pueden agregar términos de búsqueda adicionales:

   ![screen_shot_2018-03-23at101710](assets/screen_shot_2018-03-23at101710.png)

1. Cierre **Buscar** con la **X** (parte superior derecha).

>[!NOTE]
>
>Los criterios de búsqueda se mantienen al seleccionar un elemento en los resultados de la búsqueda.
>
>Cuando se selecciona un elemento en la página de resultados de la búsqueda, al volver a la página de búsqueda después de usar el botón Atrás del explorador, los criterios de búsqueda se mantienen. 

## Búsquedas guardadas {#saved-searches}

Además de buscar aplicando una amplia gama de criterios, también puede guardar una configuración de búsqueda determinada para recuperarla y utilizarla en otro momento:

1. Defina sus criterios de búsqueda y seleccione **Guardar**.

   ![screen_shot_2018-03-23at101710-1](assets/screen_shot_2018-03-23at101710-1.png)

1. Asigne un nombre y luego utilice **Guardar** para confirmar la acción:

   ![screen_shot_2018-03-23at101852](assets/screen_shot_2018-03-23at101852.png)

1. La próxima vez que acceda al panel de búsqueda, la búsqueda guardada estará disponible en el selector:

   ![screen_shot_2018-03-23at102128](assets/screen_shot_2018-03-23at102128.png)

1. Una vez guardada, podrá:

   * Use **x** (con el nombre de la búsqueda guardada) para iniciar una nueva consulta (la búsqueda guardada en sí no se eliminará).
   * Use la opción **Editar búsqueda guardada**, cambie las condiciones de búsqueda y luego utilice **Guardar** nuevamente.

Las búsquedas guardadas se pueden modificar seleccionando la búsqueda guardada y haciendo clic en **Editar búsqueda guardada** en la parte inferior del panel de búsqueda.

![screen_shot_2018-03-23at102213](assets/screen_shot_2018-03-23at102213.png)

