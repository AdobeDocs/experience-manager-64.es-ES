---
title: Directrices de formación del servicio de contenido inteligente
description: Capacite el servicio de IA para aplicar etiquetas inteligentes a los recursos
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 13%

---

# Directrices de formación del servicio de contenido inteligente {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para poder etiquetar de forma eficaz las imágenes de marca, el servicio de contenido inteligente requiere que las imágenes de formación se ajusten a determinadas directrices.

## Directrices para la formación {#guidelines-for-training}

Para obtener mejores resultados, las imágenes del conjunto de formación deben cumplir las siguientes directrices:

**Cantidad y tamaño:****Mínimo de 30 imágenes por etiqueta**. Mínimo de 500 píxeles en el lado más largo.

**Coherencia**: Las imágenes de una etiqueta deben ser visualmente similares.

Por ejemplo, no es buena idea etiquetar todas estas imágenes como *my-party* (para formación) porque no son visualmente similares.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/coherence.png)

**Cobertura**: Debería haber suficiente variedad en las imágenes de la formación. La idea es dar algunos ejemplos, pero razonablemente diversos, para que [!DNL Experience Manager] aprende a centrarse en las cosas correctas. Si está aplicando la misma etiqueta en imágenes visualmente diferentes, incluya al menos cinco ejemplos de cada tipo.

Por ejemplo, para la etiqueta *modelo-descendente-pose*, incluya más imágenes de formación similares a la imagen resaltada a continuación para que el servicio identifique imágenes similares con mayor precisión durante el etiquetado.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/coverage_1.png)

**Distracción/obstrucción**: El servicio forma mejor con imágenes que tienen menos distracción (fondos destacados, acompañamientos no relacionados, como objetos/personas con el tema principal).

Por ejemplo, para la etiqueta *zapato casual*, la segunda imagen no es un buen candidato para la formación.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/distraction.png)

**Complejidad:** Si una imagen cumple los requisitos para más de una etiqueta, agregue todas las etiquetas aplicables antes de incluir la imagen para formación. Por ejemplo, para las etiquetas, como *impermeable* y *vista del lado del modelo*, agregue ambas etiquetas en el recurso que cumple los requisitos antes de incluirlo para formación.

![Imágenes ilustrativas para ejemplificar las directrices de formación](assets/do-not-localize/completeness.png)

## Restricciones {#limitations}

Las etiquetas inteligentes mejoradas se basan en modelos de aprendizaje de imágenes de marca y sus etiquetas. Estos modelos no siempre son perfectos para identificar etiquetas. La versión actual del servicio de contenido inteligente tiene las siguientes limitaciones:

* Incapacidad para reconocer sutiles diferencias en imágenes. Por ejemplo, camisas delgadas contra las vestidas regulares.
* Incapacidad para identificar etiquetas basadas en pequeños patrones o partes de una imagen. Por ejemplo, logotipos en camisetas.
* El etiquetado es compatible con las configuraciones regionales que [!DNL Experience Manager] es compatible con . Para obtener una lista de idiomas, consulte [Notas de la versión de Servicios de contenido inteligente](/help/release-notes/smart-content-service-release-notes.md).

Para buscar recursos con etiquetas inteligentes (normales o mejoradas), utilice la búsqueda Omni-search de Assets (búsqueda de texto completo). No hay predicado de búsqueda independiente para las etiquetas inteligentes.

>[!NOTE]
>
>La capacidad del servicio de contenido inteligente para formarse sobre sus etiquetas y aplicarlas en otras imágenes depende de la calidad de las imágenes que utilice para la formación.
>
>Para obtener mejores resultados, Adobe recomienda utilizar imágenes visualmente similares para entrenar el servicio para cada etiqueta.
