---
title: Administrar etiquetas inteligentes
description: Actualizar o eliminar las etiquetas inteligentes inexactas para mejorar la relevancia de las etiquetas
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 4%

---

# Administración de etiquetas inteligentes {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede depurar las etiquetas inteligentes para eliminar cualquier etiqueta incorrecta que se haya asignado a las imágenes de marca, de modo que solo se muestren las etiquetas más relevantes.

Moderar las etiquetas inteligentes también ayuda a refinar las búsquedas basadas en etiquetas de imágenes, ya que garantiza que la imagen aparezca en los resultados de búsqueda de las etiquetas más relevantes. Esencialmente, ayuda a eliminar las posibilidades de que las imágenes no relacionadas aparezcan en los resultados de búsqueda.

También puede asignar una clasificación superior a una etiqueta para aumentar su relevancia con respecto a una imagen. La promoción de una etiqueta para una imagen aumenta las posibilidades de que la imagen aparezca en los resultados de búsqueda cuando se realiza una búsqueda basada en la etiqueta en particular.

1. En el cuadro OmniSearch, busque recursos basados en una etiqueta .
1. Inspect muestra los resultados de búsqueda para identificar una imagen que no le parezca relevante para la búsqueda.
1. Seleccione la imagen y, a continuación, toque o haga clic en el **[!UICONTROL Administrar etiquetas]** de la barra de herramientas.
1. En el **[!UICONTROL Administrar etiquetas]** , inspeccione las etiquetas . Si no desea que se busque la imagen en función de una etiqueta específica, seleccione la etiqueta y, a continuación, toque o haga clic en el **[!UICONTROL Eliminar]** de la barra de herramientas. También puede tocar o hacer clic en el (**[!UICONTROL X]**) que aparece junto a la etiqueta.
1. Para asignar una clasificación superior a una etiqueta, seleccione la etiqueta y toque o haga clic en el **[!UICONTROL Promocionar]** de la barra de herramientas. La etiqueta que promocione se moverá a la variable **[!UICONTROL Etiquetas]** para obtener más información.
1. Pulse o haga clic en **[!UICONTROL Guardar]** y, a continuación, pulse o haga clic en **[!UICONTROL Aceptar]** para cerrar el cuadro de diálogo de éxito.
1. Vaya a la página de propiedades de la imagen. Observe que a la etiqueta que promocionó se le asigna una alta relevancia y, por lo tanto, aparece más arriba en los resultados de búsqueda.

## Comprender [!DNL Experience Manager] resultados de búsqueda con etiquetas inteligentes {#understand-search-results-with-smart-tags}

De forma predeterminada, [!DNL Experience Manager] la búsqueda combina los términos de búsqueda con un `AND` cláusula. El uso de etiquetas inteligentes no cambia este comportamiento predeterminado. El uso de etiquetas inteligentes agrega un `OR` para encontrar cualquiera de los términos de búsqueda en aplica etiquetas inteligentes. Por ejemplo, piense en buscar `woman running`. Recursos con solo `woman` o solo `running` de forma predeterminada, las palabras clave de los metadatos no aparecen en los resultados de búsqueda. Sin embargo, un recurso etiquetado con `woman` o `running` el uso de etiquetas inteligentes aparece en una consulta de búsqueda de este tipo. Así que los resultados de la búsqueda son una combinación de:

* recursos con ambas palabras clave, `woman` y `running` en los metadatos.
* activos con etiquetas inteligentes con cualquiera de las palabras clave.

Los resultados de búsqueda que coinciden con todos los términos de búsqueda en los campos de metadatos se muestran primero, seguidos de los resultados de búsqueda que coinciden con cualquiera de los términos de búsqueda en las etiquetas inteligentes. En el ejemplo anterior, el orden aproximado de visualización de los resultados de búsqueda es:

1. coincidencias de `woman running` en los distintos campos de metadatos.
1. coincidencias de `woman running` en etiquetas inteligentes.
1. coincidencias de `woman` o `running` en etiquetas inteligentes.
