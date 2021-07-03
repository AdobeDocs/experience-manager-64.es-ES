---
title: Ordenación mejorada de los recursos en AEM
description: Descubra cómo AEM Assets implementa la ordenación del lado del servidor para ordenar los recursos de carpetas o una consulta de búsqueda de una sola vez en lugar de ordenarlos por lotes en el lado del cliente.
contentOwner: AG
feature: 'Búsqueda  '
role: User
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---

# Ordenación mejorada de los recursos en AEM {#enhanced-sorting-of-assets-in-aem}

Descubra cómo AEM Assets implementa la ordenación del lado del servidor para ordenar los recursos de carpetas o una consulta de búsqueda de una sola vez en lugar de ordenarlos por lotes en el lado del cliente.

La capacidad de búsqueda de Adobe Experience Manager (AEM) Assets se ha mejorado para ordenar de forma eficaz un gran número de recursos en las páginas de resultados de búsqueda y vista de lista de carpetas. También puede ordenar las entradas de la línea de tiempo.

AEM Assets implementa la ordenación del lado del servidor para ordenar todo el conjunto de recursos (aunque sean grandes) dentro de una carpeta o una consulta de búsqueda de una sola vez, en lugar de ordenarlos por lotes en el lado del cliente. De este modo, los resultados recuperados previamente se pueden mostrar rápidamente en la interfaz de usuario, lo que hace que la operación de ordenación sea más flexible y ágil.

## Clasificación de recursos en la vista de lista {#sorting-assets-in-list-view}

AEM Assets permite ordenar los recursos de las carpetas en función de los campos siguientes:

* Conf. regional
* Estado
* Tipo
* Tamaño
* Clasificación
* Fecha de modificación
* Fecha de publicación
* Uso
* Clics
* Impresiones
* Extraído

1. Vaya a una carpeta que contenga un gran número de recursos.
1. Toque o haga clic en el icono Diseño y cambie a la vista de lista.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. Toque o haga clic en el icono Ordenar situado junto al encabezado de cualquier columna de la lista de recursos.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   La lista de recursos se ordena según los valores de los campos.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Para ordenar los valores en las columnas `Name` o `Title`, superponga `/libs/dam/gui/content/commons/availablecolumns` y cambie el valor de `sortable` a `True`.

## Clasificación de recursos en resultados de búsqueda {#sorting-assets-in-search-results}

Puede ordenar los resultados de la búsqueda según los campos siguientes:

* Título
* Estado
* Tipo
* Tamaño
* Fecha de modificación
* Fecha de publicación

1. En el cuadro OmniSearch, busque recursos en función de los criterios deseados.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Toque o haga clic en el icono Diseño y cambie a la vista de lista. Si los resultados de la búsqueda ya se muestran en la vista de lista, omita este paso.
1. Toque o haga clic en el icono Ordenar situado junto al encabezado de cualquier columna de la lista de recursos. La lista de recursos se ordena según los valores de los campos.

   ![chlimage_1-398](assets/chlimage_1-398.png)

## Clasificación de recursos en la cronología {#sorting-assets-in-timeline}

AEM Assets permite ordenar cronológicamente las entradas de la cronología, como anotaciones, versiones, flujos de trabajo y actividades.

1. En la interfaz de usuario de Assets, seleccione un recurso para el que desee mostrar la línea de tiempo.
1. Pulse o haga clic en el icono de navegación global y seleccione **[!UICONTROL Línea de tiempo]**.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. En la línea de tiempo, seleccione una entrada de la lista. Por ejemplo, seleccione **[!UICONTROL Comentarios]** para mostrar la lista de anotaciones asociadas al recurso.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Toque o haga clic en el icono **[!UICONTROL Sort]** situado junto a la etiqueta **[!UICONTROL Date]**. Según la selección, las anotaciones se muestran en el orden cronológico cronológico o inverso en el que se agregaron al recurso.

   ![chlimage_1-401](assets/chlimage_1-401.png)
