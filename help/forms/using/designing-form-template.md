---
title: Diseñar plantillas de formulario para formularios HTML5
seo-title: Designing form templates for HTML5 forms
description: AEM Forms ofrece el procesamiento de plantillas de formulario XFA en formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario con Designer y utilizar la capacidad de representación de HTML5.
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 92%

---

# Diseñar plantillas de formulario para formularios HTML5 {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El componente de formularios HTML5 en AEM ofrece el procesamiento de la plantilla de formulario XFA al formato HTML5. Los diseñadores de formularios pueden diseñar plantillas de formulario mediante [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) y utilizar la capacidad de representación de HTML5. Estas plantillas de formulario, junto con sus recursos, pueden residir en el repositorio de AEM, el sistema de archivos o exponerse a través de http. Sin embargo, si planea administrar los formularios con Forms Manager, las plantillas y los recursos deben residir en el repositorio de AEM.

Aunque los formularios HTML5 coinciden en buena medida con el comportamiento de los formularios PDF, hay algunas características en ambos formatos que no se pueden aplicar al otro. Por ejemplo, la forma en que se aplican los códigos de barras en un formulario PDF en Adobe Reader varía según el formulario de Mobile o la forma en que el formulario se firma digitalmente también varía según el formato. Para obtener más información sobre estas variaciones, consulte [Diferenciar las características entre formularios HTML5 y los formularios PDF](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Para ver las características comunes de XFA, consulte las siguientes prácticas recomendadas y directrices para diseñar un formulario que funcione en ambos formatos.

## Funciones en AEM Forms Designer para formularios HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Previsualizar HTML {#preview-html}

La pestaña Previsualizar HTML se agrega en el modo Diseño para que los diseñadores de formularios obtengan una vista previa de los formularios en formato HTML5 durante el proceso de diseño. Para obtener más información sobre cómo habilitar y configurar esta capacidad en AEM Forms Designer, consulte [Previsualizar HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma manuscrita {#scribble-signature}

El objetivo principal de los formularios HTML5 son los dispositivos táctiles. Por lo tanto, se agrega un nuevo control de firma de anotaciones en AEM Forms Designer. Puede hacer clic o arrastrar y soltar el control de firma de anotaciones en la plantilla de formulario y configurarlo. Se representa como un campo de anotaciones en la representación HTML5 y se puede utilizar para garabatear la firma en dispositivos táctiles. En equipos de escritorio, se puede utilizar como campo de garabato mediante el control del ratón. Para obtener más información sobre cómo utilizar esta función, consulte [Campo de garabato XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
