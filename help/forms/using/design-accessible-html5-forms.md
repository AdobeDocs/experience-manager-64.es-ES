---
title: Diseñar formularios HTML5 accesibles
seo-title: Designing accessible HTML5 forms
description: Los formularios HTML5 utilizan el estándar de accesibilidad ARIA HTML5. Estos formularios admiten la navegación con pestañas y están certificados para ser compatibles con lectores de pantalla comunes.
seo-description: HTML5 forms use the ARIA HTML5 accessibility standard. These forms support tabbed navigation and are certified to be compatible with common screen readers.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: Mobile Forms
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 87%

---

# Diseñar formularios HTML5 accesibles {#designing-accessible-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los formularios HTML5 utilizan el estándar de accesibilidad ARIA HTML5 para generar formularios HTML accesibles. Estos formularios admiten la navegación con pestañas (excepto Mozilla FireFox) y están certificados para ser compatibles con lectores de pantalla comunes. Para generar un formulario HTML 5 con buenas funciones de accesibilidad, diseñe la plantilla de formulario XFA basándose en algunas [directrices básicas de diseño](/help/forms/using/best-practices-for-html5-forms.md). Las directrices de diseño incluyen configurar el orden de pestañas correcto y proporcionar el contenido Texto hablado para cada control de formulario. AEM Forms Designer admite la configuración de estos atributos de control de formulario para generar un formulario PDF y HTML5 accesible.

*Nota: La navegación con pestañas no cubre campos protegidos, como los campos de cálculo que muestran la suma de los valores. Para que el lector de pantalla lea el valor de un campo protegido, coloque un campo vacío de solo lectura encima o junto al campo protegido. Asigne el valor del campo protegido al nuevo campo de solo lectura. El lector de pantalla o la navegación con pestañas pueden elegir este campo de solo lectura y expresarlo como el valor del campo protegido.*

AEM Forms Designer incluye varias opciones de Texto hablado que se pueden pasar a los lectores de pantalla. Para cada objeto de un formulario, el usuario puede especificar una de varias opciones de configuración para el texto del lector de pantalla:

* Texto personalizado del lector de pantalla, que se puede configurar con la paleta Accesibilidad. Los autores pueden anotar los nombres de los botones y campos, así como su propósito.
* Información del objeto, que se puede establecer en la paleta Accesibilidad.
* Pies de ilustración para los campos del formulario.
* Nombres de objetos, como se especifican en la opción Nombre de la pestaña Enlace.

![accesibilidad](assets/accessibility.png)

Cuando hay varias opciones disponibles en un control de formulario, como información del objeto, Lector de texto en pantalla y Pie de ilustración, el Lector de pantalla solo utilizará una de estas propiedades. El orden predeterminado es Lector de texto en pantalla, información del objeto, Pie de ilustración y Nombre. Puede ignorar este orden predeterminado si utiliza la opción **Prioridad** de Lector de pantalla en la paleta Accesibilidad.
