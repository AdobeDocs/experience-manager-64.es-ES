---
title: Administrar etiquetas inteligentes
description: Actualizar o eliminar las etiquetas inteligentes inexactas para mejorar la relevancia de las etiquetas
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 3%

---


# Administración de etiquetas inteligentes {#managing-smart-tags}

Puede depurar las etiquetas inteligentes para eliminar cualquier etiqueta incorrecta que se haya asignado a las imágenes de marca, de modo que solo se muestren las etiquetas más relevantes.

Moderar las etiquetas inteligentes también ayuda a refinar las búsquedas basadas en etiquetas de imágenes, ya que garantiza que la imagen aparezca en los resultados de búsqueda de las etiquetas más relevantes. Esencialmente, ayuda a eliminar las posibilidades de que las imágenes no relacionadas aparezcan en los resultados de búsqueda.

También puede asignar una clasificación superior a una etiqueta para aumentar su relevancia con respecto a una imagen. La promoción de una etiqueta para una imagen aumenta las posibilidades de que la imagen aparezca en los resultados de búsqueda cuando se realiza una búsqueda basada en la etiqueta en particular.

1. En el cuadro OmniSearch, busque recursos basados en una etiqueta .
1. Inspect muestra los resultados de búsqueda para identificar una imagen que no le parezca relevante para la búsqueda.
1. Seleccione la imagen y, a continuación, pulse o haga clic en el icono **[!UICONTROL Administrar etiquetas]** de la barra de herramientas.
1. En la página **[!UICONTROL Administrar etiquetas]**, inspeccione las etiquetas. Si no desea que se busque la imagen en función de una etiqueta específica, seleccione la etiqueta y, a continuación, toque o haga clic en el icono **[!UICONTROL Eliminar]** de la barra de herramientas. También puede tocar o hacer clic en el símbolo (**[!UICONTROL X]**) que aparece junto a la etiqueta.
1. Para asignar una clasificación superior a una etiqueta, seleccione la etiqueta y pulse o haga clic en el icono **[!UICONTROL Promocionar]** de la barra de herramientas. La etiqueta que promocione se moverá a la sección **[!UICONTROL Etiquetas]**.
1. Pulse o haga clic en **[!UICONTROL Guardar]** y, a continuación, pulse o haga clic en **[!UICONTROL Aceptar]** para cerrar el cuadro de diálogo de éxito.
1. Vaya a la página de propiedades de la imagen. Observe que a la etiqueta que promocionó se le asigna una alta relevancia y, por lo tanto, aparece más arriba en los resultados de búsqueda.

## Comprender AEM resultados de búsqueda con etiquetas inteligentes {#understand-search-results-with-smart-tags}

De forma predeterminada, AEM búsqueda combina los términos de búsqueda con una cláusula `AND`. El uso de etiquetas inteligentes no cambia este comportamiento predeterminado. El uso de etiquetas inteligentes agrega una cláusula `OR` adicional para encontrar cualquiera de los términos de búsqueda en aplica etiquetas inteligentes. Por ejemplo, considere la búsqueda de `woman running`. Los recursos con solo `woman` o con `running` palabra clave en los metadatos no aparecen en los resultados de búsqueda de forma predeterminada. Sin embargo, en una consulta de búsqueda aparece un recurso etiquetado con `woman` o `running` mediante etiquetas inteligentes. Así que los resultados de la búsqueda son una combinación de:

* activos con ambas palabras clave, `woman` y `running` en los metadatos.
* activos con etiquetas inteligentes con cualquiera de las palabras clave.

Los resultados de búsqueda que coinciden con todos los términos de búsqueda en los campos de metadatos se muestran primero, seguidos de los resultados de búsqueda que coinciden con cualquiera de los términos de búsqueda en las etiquetas inteligentes. En el ejemplo anterior, el orden aproximado de visualización de los resultados de búsqueda es:

1. coincidencias de `woman running` en los distintos campos de metadatos.
1. coincidencias de `woman running` en etiquetas inteligentes.
1. coincidencias de `woman` o de `running` en las etiquetas inteligentes.
