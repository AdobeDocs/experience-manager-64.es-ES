---
title: Ordenación mejorada de los recursos en AEM
description: Descubra cómo [!DNL Experience Manager] Assets implementa la ordenación del lado del servidor para ordenar los recursos de las carpetas o una consulta de búsqueda de una sola vez, en lugar de ordenarlos por lotes en el lado del cliente.
contentOwner: AG
feature: Search
role: User
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 4%

---

# Ordenación mejorada de los recursos en [!DNL Experience Manager] {#enhanced-sorting-of-assets-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Descubra cómo [!DNL Experience Manager] Assets implementa la ordenación del lado del servidor para ordenar los recursos de las carpetas o una consulta de búsqueda de una sola vez, en lugar de ordenarlos por lotes en el lado del cliente.

La capacidad de búsqueda de Adobe Experience Manager Assets se ha mejorado para ordenar de forma eficaz un gran número de recursos en las páginas de resultados de búsqueda y vista de lista de carpetas. También puede ordenar las entradas de la línea de tiempo.

[!DNL Experience Manager] Assets implementa la ordenación del lado del servidor para ordenar todo el conjunto de recursos (aunque sean grandes) dentro de una carpeta o una consulta de búsqueda de una sola vez, en lugar de ordenarlos por lotes en el lado del cliente. De este modo, los resultados recuperados previamente se pueden mostrar rápidamente en la interfaz de usuario, lo que hace que la operación de ordenación sea más flexible y ágil.

## Clasificación de recursos en la vista de lista {#sorting-assets-in-list-view}

[!DNL Experience Manager] Assets permite ordenar los recursos de las carpetas en función de los campos siguientes:

* Configuración regional
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
>Para ordenar los valores en la variable `Name` o `Title`columnas, superposición `/libs/dam/gui/content/commons/availablecolumns` y cambiar el valor de `sortable` a `True`.

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

[!DNL Assets] permite ordenar cronológicamente entradas de cronología, como anotaciones, versiones, flujos de trabajo y actividades.

1. En la interfaz de usuario de Assets, seleccione un recurso para el que desee mostrar la línea de tiempo.
1. Pulse o haga clic en el icono de navegación global y seleccione **[!UICONTROL Cronología]**.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. En la línea de tiempo, seleccione una entrada de la lista. Por ejemplo, seleccione **[!UICONTROL Comentarios]** para mostrar la lista de anotaciones asociadas al recurso.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Toque o haga clic en **[!UICONTROL Ordenar]** junto a **[!UICONTROL Fecha]** etiqueta. Según la selección, las anotaciones se muestran en el orden cronológico cronológico o inverso en el que se agregaron al recurso.

   ![chlimage_1-401](assets/chlimage_1-401.png)
