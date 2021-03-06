---
title: Diseño de formularios HTML5 accesibles
seo-title: Diseño de formularios HTML5 accesibles
description: Los formularios HTML5 utilizan el estándar de accesibilidad ARIA HTML5. Estos formularios admiten la navegación con pestañas y están certificados para ser compatibles con lectores de pantalla comunes.
seo-description: Los formularios HTML5 utilizan el estándar de accesibilidad ARIA HTML5. Estos formularios admiten la navegación con pestañas y están certificados para ser compatibles con lectores de pantalla comunes.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Diseño de formularios HTML5 accesibles {#designing-accessible-html-forms}

Los formularios HTML5 utilizan el estándar de accesibilidad ARIA HTML5 para generar formularios HTML accesibles. Estos formularios admiten la navegación con pestañas (excepto Mozilla FireFox) y están certificados para ser compatibles con lectores de pantalla comunes. Para generar un formulario HTML5 con buenas funciones de accesibilidad, diseñe la plantilla de formulario XFA basada en algunas [directrices de diseño básicas](/help/forms/using/best-practices-for-html5-forms.md). Las directrices de diseño incluyen configurar el orden de tabulación correcto y proporcionar el contenido Texto hablado para cada control de formulario. AEM Forms Designer admite la configuración de estos atributos de control de formulario para generar un formulario PDF y HTML5 accesible.

*Nota:La navegación con fichas no cubre campos protegidos, como los campos de cálculo que muestran la suma de los valores. Para que el lector de pantalla lea el valor de un campo protegido, coloque un campo vacío de solo lectura encima o junto al campo protegido. Asigne el valor del campo protegido al nuevo campo de solo lectura. El lector de pantalla o la navegación con pestañas pueden elegir este campo de solo lectura y expresarlo como el valor del campo protegido.*

AEM Forms Designer incluye varias opciones de Texto hablado que se pueden pasar a los lectores de pantalla. Para cada objeto de un formulario, el usuario puede especificar una de varias opciones de configuración para el texto del lector de pantalla:

* Texto personalizado del lector de pantalla, que se puede configurar con la paleta Accesibilidad. Los autores pueden anotar los nombres de los botones y campos, así como su propósito.
* Información del objeto, que se puede establecer en la paleta Accesibilidad.
* Subtítulos para los campos del formulario.
* Nombres de objetos, tal como se especifica en la opción Nombre de la ficha Enlace.

![accesibilidad](assets/accessibility.png)

Cuando hay varias opciones disponibles en un control de formulario, como información del objeto, Texto del Reader de pantalla y Rótulo, el Reader de pantalla solo utiliza una de estas propiedades. El orden predeterminado es Texto personalizado del Reader de pantalla, información del objeto, Rótulo y Nombre. Puede anular el orden predeterminado utilizando la opción Reader de pantalla **Prioridad** de la paleta Accesibilidad.
