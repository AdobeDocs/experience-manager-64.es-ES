---
title: Directrices de formación de Smart Content Service
description: Formación del servicio de AI para aplicar etiquetas inteligentes a los recursos
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
translation-type: tm+mt
source-git-commit: dc779a0d89dc4c044ca4f3e3f92c4a9b651d09a8
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 12%

---


# Pautas de capacitación de Smart Content Service {#smart-content-service-training-guidelines}

Para poder etiquetar eficazmente las imágenes de su marca, el servicio de contenido inteligente requiere que las imágenes de formación se ajusten a determinadas directrices.

## Pautas para capacitación {#guidelines-for-training}

Para obtener los mejores resultados, las imágenes del conjunto de formación deben cumplir las siguientes directrices:

**Cantidad y tamaño:****Mínimo de 30 imágenes por etiqueta**. Mínimo de 500 píxeles en el lado más largo.

**Coherencia**: Las imágenes de una etiqueta deben ser visualmente similares.

Por ejemplo, no es recomendable etiquetar todas estas imágenes como *my-party* (para formación) porque no son visualmente similares.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/coherence.png)

**Cobertura**: Las imágenes de la formación deben ser suficientemente variadas. La idea es dar algunos ejemplos, pero razonablemente diversos, para que AEM aprenda a centrarse en las cosas correctas. Si está aplicando la misma etiqueta en imágenes visualmente diferentes, incluya al menos cinco ejemplos de cada tipo.

Por ejemplo, para la etiqueta *model-down-pose*, incluya más imágenes de capacitación similares a la imagen resaltada a continuación para que el servicio identifique imágenes similares con mayor precisión durante el etiquetado.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/coverage_1.png)

**Distracción/obstrucción**: El servicio entrena mejor en imágenes que tienen menos distracción (fondos destacados, acompañamientos no relacionados, como objetos/personas con el tema principal).

Por ejemplo, para la etiqueta *casual-shoe*, la segunda imagen no es un buen candidato para la formación.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/distraction.png)

**Complejidad:** Si una imagen cumple los requisitos para más de una etiqueta, agregue todas las etiquetas aplicables antes de incluir la imagen para formación. Por ejemplo, para las etiquetas, como *impermeable* y *vista del lado del modelo*, agregue ambas etiquetas en el recurso que cumple los requisitos antes de incluirlo para formación.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/completeness.png)

## Restricciones     {#limitations}

Las etiquetas inteligentes mejoradas se basan en modelos de aprendizaje de imágenes de marca y sus etiquetas. Estos modelos no siempre son perfectos para identificar etiquetas. La versión actual de Smart Content Service tiene las siguientes limitaciones:

* Incapacidad para reconocer diferencias sutiles en las imágenes. Por ejemplo, camisas delgadas contra las tradicionales.
* Imposibilidad de identificar etiquetas basadas en pequeños patrones o partes de una imagen. Por ejemplo, logotipos en camisetas.
* El etiquetado se admite en las configuraciones regionales en las que se AEM. Para obtener una lista de idiomas, consulte [Notas de la versión de los servicios de contenido inteligente](/help/release-notes/smart-content-service-release-notes.md).

Para buscar recursos con etiquetas inteligentes (normal o mejorada), utilice la búsqueda Omni-search de recursos (búsqueda de texto completo). No hay ningún predicado de búsqueda independiente para las etiquetas inteligentes.

>[!NOTE]
>
>La capacidad del servicio de contenido inteligente para formarse en sus etiquetas y aplicarlas en otras imágenes depende de la calidad de las imágenes que utilice para la formación.
>
>Para obtener los mejores resultados, Adobe recomienda que utilice imágenes visualmente similares para entrenar el servicio de cada etiqueta.

