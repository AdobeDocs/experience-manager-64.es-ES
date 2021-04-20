---
title: Uso de expresiones SOM en formularios adaptables
seo-title: Uso de expresiones SOM en formularios adaptables
description: Obtenga información sobre cómo extraer expresiones SOM de un panel de un formulario adaptable.
seo-description: Obtenga información sobre cómo extraer expresiones SOM de un panel de un formulario adaptable.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# Uso de expresiones SOM en formularios adaptables {#using-som-expressions-in-adaptive-forms}

Los formularios adaptables se modelan como AEM Página que se representa como estructura de contenido JCR en AEM repositorio. El elemento clave de la estructura de contenido es el nodo guideContainer . Debajo de guideContainer, hay rootPanel que puede contener paneles y campos anidados.

Puede utilizar un modelo de objetos de secuencias de comandos (SOM) para hacer referencia a valores, propiedades y métodos dentro de un modelo de objetos de documento (DOM) concreto. Un DOM organiza los objetos de memoria y las propiedades en una jerarquía de árbol. Una expresión SOM hace referencia a los elementos y paneles Campos/Dibujar.

La siguiente imagen representa una estructura de nodos a la que se traduce un formulario adaptable cuando se agregan componentes a un formulario. Por ejemplo, puede agregar un panel al panel raíz y un botón de opción del panel que se transforme en DOM durante la ejecución. La expresión SOM para el campo del botón de radio en forma adaptable se especifica como `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![Árbol DOM](assets/hierarchy-1.png)

La expresión SOM de cualquier elemento de un formulario adaptable lleva el prefijo `guide[0].guide1[0]`. La posición de un componente en la jerarquía de estructura de nodos se utiliza para derivar su expresión SOM.

![Árbol DOM con dos botones de opción](assets/hierarchy_radio_button.png)

La expresión SOM cambia al cambiar la posición de los botones de opción en el formulario adaptable. En el modo de creación, puede ver la expresión SOM de un campo o elemento dentro de AEM Forms mediante la opción Ver expresión SOM. La opción aparece en el panel y al hacer clic con el botón derecho en el campo o elemento.

![Extracción de expresiones SOM en un formulario adaptable](assets/som-expressions.png)

En los paneles, puede acceder a la función desde la barra de herramientas del panel. La función facilita las secuencias de comandos de los autores de formularios adaptables.

![Extracción de expresiones SOM mediante la barra de herramientas del panel](assets/som-expression.png)

Algunas API enumeradas en [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) utilizan la expresión SOM de un elemento. Por ejemplo, para centrar la atención en un campo concreto de una forma adaptativa, pase la expresión SOM correspondiente a la API `getFocus`en `guideBridge`.

