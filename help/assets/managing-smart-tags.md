---
title: Administrar etiquetas inteligentes
description: Actualice o elimine las etiquetas inteligentes imprecisas para mejorar la relevancia de las etiquetas
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# Administración de etiquetas inteligentes {#managing-smart-tags}

Puede depurar las etiquetas inteligentes para eliminar cualquier etiqueta incorrecta que se haya asignado a las imágenes de su marca, de modo que solo se muestren las etiquetas más relevantes.

La moderación de las etiquetas inteligentes también ayuda a restringir las búsquedas de imágenes basadas en etiquetas, ya que garantiza que la imagen aparezca en los resultados de búsqueda de las etiquetas más relevantes. Básicamente, ayuda a eliminar las posibilidades de que las imágenes no relacionadas aparezcan en los resultados de búsqueda.

También puede asignar una clasificación superior a una etiqueta para aumentar su relevancia con respecto a una imagen. La promoción de una etiqueta para una imagen aumenta las posibilidades de que la imagen aparezca en los resultados de búsqueda cuando se realiza una búsqueda en función de la etiqueta en particular.

1. En el cuadro OmniSearch, busque recursos basados en una etiqueta.
1. Inspect muestra los resultados de la búsqueda para identificar una imagen que no le parece relevante para la búsqueda.
1. Seleccione la imagen y, a continuación, toque o haga clic en el icono **[!UICONTROL Administrar etiquetas]** de la barra de herramientas.
1. En la página **[!UICONTROL Administrar etiquetas]** , inspeccione las etiquetas. Si no desea buscar la imagen en función de una etiqueta específica, seleccione la etiqueta y toque o haga clic en el icono **[!UICONTROL Eliminar]** de la barra de herramientas. O bien, toque o haga clic en el símbolo (**[!UICONTROL X]**) que aparece junto a la etiqueta.
1. Para asignar una clasificación superior a una etiqueta, selecciónela y toque o haga clic en el icono **[!UICONTROL Promocionar]** de la barra de herramientas. La etiqueta promocionada se mueve a la sección **[!UICONTROL Etiquetas]** .
1. Pulse o haga clic en **[!UICONTROL Guardar]** y, a continuación, pulse o haga clic en **[!UICONTROL Aceptar]** para cerrar el cuadro de diálogo de éxito.
1. Vaya a la página de propiedades de la imagen. Observe que la etiqueta promocionada tiene una alta relevancia y, por lo tanto, aparece más arriba en los resultados de búsqueda.

## Comprender AEM resultados de búsqueda con etiquetas inteligentes {#understand-search-results-with-smart-tags}

De forma predeterminada, AEM búsqueda combina los términos de búsqueda con una `AND` cláusula. El uso de etiquetas inteligentes no cambia este comportamiento predeterminado. El uso de etiquetas inteligentes agrega una `OR` cláusula adicional para encontrar cualquiera de los términos de búsqueda en las etiquetas inteligentes de aplicación. For example, consider searching for `woman running`. Los recursos con solo `woman` o solamente `running` palabra clave en los metadatos no aparecen en los resultados de búsqueda de forma predeterminada. Sin embargo, un recurso etiquetado con etiquetas inteligentes `woman` o `running` con etiquetas inteligentes aparece en una consulta de búsqueda de este tipo. Los resultados de la búsqueda son una combinación de:

* recursos con palabras clave `woman` y `running` en los metadatos.
* los recursos se etiquetaron de forma inteligente con cualquiera de las palabras clave.

Los resultados de búsqueda que coinciden con todos los términos de búsqueda en los campos de metadatos se muestran primero, seguidos de los resultados de búsqueda que coinciden con cualquiera de los términos de búsqueda en las etiquetas inteligentes. En el ejemplo anterior, el orden aproximado de visualización de los resultados de búsqueda es:

1. coincidencias de en `woman running` los distintos campos de metadatos.
1. coincidencias de `woman running` en etiquetas inteligentes.
1. coincidencias de `woman` o de `running` en etiquetas inteligentes.
