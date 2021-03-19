---
title: Diseño de plantillas de formulario para formularios HTML5
seo-title: Diseño de plantillas de formulario para formularios HTML5
description: 'AEM Forms ofrece la renderización de plantillas de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con Designer y utilizar la capacidad de representación HTML5. '
seo-description: 'AEM Forms ofrece la renderización de plantillas de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con Designer y utilizar la capacidad de representación HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# Diseño de plantillas de formulario para formularios HTML5 {#designing-form-templates-for-html-forms}

El componente de formularios HTML5 de AEM ofrece la renderización de una plantilla de formulario XFA al formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario utilizando [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) y utilizar la capacidad de representación HTML5. Estas plantillas de formulario, junto con sus recursos, pueden residir en AEM repositorio, sistema de archivos o exponerse a través de http. Sin embargo, si planea administrar los formularios con Forms Manager, las plantillas y los recursos deben residir en el repositorio de AEM.

Aunque los formularios HTML5 coinciden en buena medida con el comportamiento de los PDF forms, hay algunas funciones en ambos formatos que no se pueden aplicar al otro formato. Por ejemplo, la forma en que se aplican los códigos de barras en un formulario PDF en Adobe Reader varía según el formulario móvil o la forma en que se firma digitalmente un formulario también varía según el formato. Para obtener más información sobre estas variaciones, consulte [Distinción de características entre formularios HTML5 y PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Para ver las funciones comunes de XFA, consulte las siguientes prácticas recomendadas y directrices para diseñar un formulario que funcione en ambos formatos.

## Funciones en AEM Forms Designer para HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### Vista previa de HTML {#preview-html}

La ficha Vista previa de HTML se agrega en el modo Diseño para que los diseñadores de formularios obtengan una vista previa de los formularios en formato HTML5 durante el proceso de diseño. Para obtener más información sobre cómo habilitar y configurar esta capacidad en AEM Forms Designer, consulte [Vista previa de HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma manuscrita {#scribble-signature}

El destino principal de los formularios HTML5 son los dispositivos táctiles. Por lo tanto, se agrega un nuevo control de firma de anotaciones en AEM Forms Designer. Puede hacer clic o arrastrar y soltar el control de firma de anotaciones en la plantilla de formulario y configurarlo. Se representa como un campo de anotaciones en una representación HTML5 y se puede utilizar para garabatear firmas en dispositivos táctiles. En equipos de escritorio, se puede utilizar como campo de secuencia de comandos utilizando el control del ratón. Para obtener más información sobre cómo utilizar esta función, consulte [Campo de análisis XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
