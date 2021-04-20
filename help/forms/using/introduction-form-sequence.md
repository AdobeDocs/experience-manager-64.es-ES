---
title: Introducción a la secuencia de formularios en varios pasos
seo-title: Introducción a la secuencia de formularios en varios pasos
description: Con AEM Forms, puede definir una secuencia de panel de formulario en la que desea que los usuarios naveguen y rellenen un formulario adaptable.
seo-description: Con AEM Forms, puede definir una secuencia de panel de formulario en la que desea que los usuarios naveguen y rellenen un formulario adaptable.
uuid: b2b94e4c-0c28-47ba-8e23-fd8742baf71c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 4a51ebc4-e019-4fc5-93a1-d97f695126f5
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Introducción a la secuencia de formularios de varios pasos {#introduction-to-multi-step-form-sequence}

Los formularios adaptables permiten a los autores de formularios crear experiencias de captura de datos en varios pasos con buena facilidad. Incorpora compatibilidad para crear varios paneles y asociar cada uno con diferentes patrones de navegación. Los autores de formularios pueden agrupar los campos de formulario en secciones lógicas y representar un grupo como un panel. La navegación general entre paneles se controla mediante el diseño del panel. Los autores pueden elegir organizar los paneles en diferentes diseños, por ejemplo, colocándolos secuencialmente utilizando el diseño del asistente o de forma ad hoc utilizando el diseño en Pestaña. Para obtener información sobre los diseños de panel, consulte [Diseño de las capacidades de los formularios adaptables](/help/forms/using/layout-capabilities-adaptive-forms.md).

En una experiencia típica de rellenado de formularios, hay que seguir más pasos que capturar los datos. Un envío de formulario completo puede incluir otros pasos, como firmar el formulario digitalmente, verificar la información rellenada en el formulario, procesar pagos, etc. Difiere de un caso a otro.

Si el caso de uso requiere un conjunto de pasos para la captura de datos o hay regulaciones que necesitan seguir ciertos pasos, AEM Forms proporciona una forma de aplicar esa estructura común en todos los formularios. La implementación premeditada de la estructura del formulario define la secuencia de pasos de un formulario. ![Ejemplo de secuencia de formulario de varios pasos](assets/formpipeline.png)

Veamos un caso de uso en el que necesita crear una secuencia para rellenar, verificar, firmar y pasos de confirmación de un formulario. Los pasos para crear una secuencia de este tipo son los siguientes:

1. Defina una plantilla de formulario y añada el panel requerido. Tenga en cuenta que debe haber un panel para cada paso de la secuencia. Sin embargo, puede incluir subpaneles dentro de un panel.

   En este ejemplo, se pueden añadir los paneles siguientes:

   * **Relleno**: Contiene campos de formulario para capturar datos. Aquí puede incluir subpaneles anidados para crear secciones para distintos tipos de información, como personal, familia, finanzas, etc.
   * **Verificar**: Contiene el  **** componente Verifycomponent que se puede utilizar en un formulario adaptable basado en XFA. Muestra la información capturada en el panel Relleno en modo de solo lectura para la verificación.
   * **Signo** electrónico: Contiene el  **** componente Signcomponent que se puede utilizar en un formulario adaptable basado en XFA. proporciona los siguientes servicios de firma:

      * Servicios de Adobe Document Cloud eSign
      * Firma manuscrita
   * **Confirmación**: Contiene el componente  **** Resumen que muestra un mensaje que confirma el envío del formulario después de que un usuario firma el formulario y llega al paso Confirmación (Resumen) de la secuencia. Los autores pueden configurar el texto del componente Resumen, mostrar un mensaje de agradecimiento, mostrar un vínculo al PDF generado, etc.


1. Seleccione el diseño del panel raíz como **[!UICONTROL Wizard]**.
1. Complete los pasos restantes para crear la plantilla de formulario. Para obtener más información, consulte [Creación de una plantilla de formulario adaptable personalizada](/help/forms/using/custom-adaptive-forms-templates.md).

Después de definir la secuencia del formulario en la plantilla de formulario, puede utilizarla para crear formularios que tengan la estructura básica definida como la secuencia en su lugar, aunque siempre puede personalizar el formulario para adaptarlo a sus necesidades.

