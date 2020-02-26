---
title: Diseño de plantillas de formulario para formularios HTML5
seo-title: Diseño de plantillas de formulario para formularios HTML5
description: 'AEM Forms ofrece la representación de una plantilla de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con Designer y utilizar la capacidad de representación HTML5. '
seo-description: 'AEM Forms ofrece la representación de una plantilla de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con Designer y utilizar la capacidad de representación HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Diseño de plantillas de formulario para formularios HTML5 {#designing-form-templates-for-html-forms}

El componente de formularios HTML5 de AEM ofrece la representación de una plantilla de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) y utilizar la función de representación HTML5. Estas plantillas de formulario, junto con sus recursos, pueden residir en el repositorio, el sistema de archivos de AEM o exponerse mediante http. Sin embargo, si planea administrar los formularios con Forms Manager, las plantillas y los recursos deben residir en el repositorio de AEM.

Aunque los formularios HTML5 coinciden en gran medida con el comportamiento de los formularios PDF, hay algunas funciones en ambos formatos que no se pueden aplicar al otro. Por ejemplo, la forma en que se aplican los códigos de barras en un formulario PDF en Adobe Reader varía según el formulario móvil o la forma en que se firma digitalmente un formulario también varía según el formato. Para obtener más información sobre estas variaciones, consulte Diferenciación de [funciones entre formularios HTML5 y formularios](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)PDF.

Para ver las funciones XFA comunes, consulte las siguientes optimizaciones y directrices para diseñar un formulario que funcione en ambos formatos.

## Capacidades de AEM Forms Designer para formularios HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Vista previa de HTML {#preview-html}

La ficha Vista previa de HTML se agrega en el modo Diseño para que los diseñadores de formularios obtengan una vista previa de los formularios en formato HTML5 durante el proceso de diseño. Para obtener más información sobre cómo habilitar y configurar esta capacidad en AEM Forms Designer, consulte [Vista previa de HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma manuscrita {#scribble-signature}

El destino clave para los formularios HTML5 son los dispositivos táctiles. Por lo tanto, se agrega un nuevo control de firma de garabatos en AEM Forms Designer. Puede hacer clic o arrastrar y soltar el control de firma de garabatos en la plantilla de formulario y configurarlo. Se procesa como un campo de garabatos en la representación HTML5 y se puede utilizar para garabatear la firma en dispositivos táctiles. En equipos de escritorio, se puede utilizar como campo de garabateo mediante el control del ratón. Para obtener más información sobre cómo utilizar esta función, consulte Campo [de garabatos](/help/forms/using/scribble-signature.md)XFA.

![4](assets/4.png)

[Comuníquese con la asistencia técnica](https://www.adobe.com/account/sign-in.supportportal.html)
