---
title: Aplicar firmas electrónicas a un formulario utilizando firmas de anotaciones
seo-title: Aplicar firmas electrónicas a un formulario utilizando firmas de anotaciones
description: Firma de formularios mediante anotaciones
seo-description: Firma de formularios mediante anotaciones
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# Aplicar firmas electrónicas a un formulario usando firmas de anotaciones {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

Puede utilizar el componente **Scribble Signature** y el componente **Signature Step** para dibujar la firma (Scribble) en un formulario adaptable. El componente Paso de firma muestra una versión PDF del formulario adaptable. Se necesita una opción Documento de registro activada o formularios adaptables basados en plantillas de formulario para utilizar el componente de paso Firma.

Ambos componentes proporcionan una ventana, como se muestra a continuación, para firmar un formulario. También puede hacer clic en el icono de geolocalización ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) para añadir geolocalización a la firma.

![Cuadro de diálogo de signo de almohadilla](assets/scribble-signature.png)

## Configure un formulario adaptable para utilizar Scribble Signature {#configure-an-adaptive-form-to-use-scribble-signature}

1. Crear un documento de registro activado o un formulario adaptable basado en una plantilla de formulario. Para obtener información paso a paso, consulte [Creación de un formulario adaptable](/help/forms/using/creating-adaptive-form.md).
1. Arrastre y suelte el componente **Scribble Signature** desde el navegador de componentes al formulario adaptable.
1. Pulse el icono **Configure** ![configure](assets/configure.png). Abre el navegador de propiedades y muestra las propiedades del componente Firma de anotaciones. Configure las propiedades del componente Scribble Signature.
1. Arrastre y suelte el componente Paso de firma desde el navegador de componentes al formulario adaptable.

   >[!NOTE]
   >
   >El componente Paso de firma ocupa el ancho completo disponible para el formulario. Se recomienda no tener ningún otro componente en la sección que contenga el componente Paso de firma.

1. En el navegador de contenido, pulse **Contenedor de formulario** y pulse el icono **Configurar** ![configurar](assets/configure.png). Abre el explorador de propiedades y muestra las propiedades del contenedor de formularios adaptables. Vaya a **Contenedor de formulario adaptable** > **Firma electrónica** y anule la selección de la opción **Habilitar Adobe Sign**. Pulse el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios.

   >[!NOTE]
   >
   >Cuando se añade un componente Paso de firma a un formulario adaptable, la opción Habilitar Adobe Sign se selecciona automáticamente.

1. Pulse el icono **Configure** ![configure](assets/configure.png). Abre el navegador de propiedades y muestra las propiedades del paso Firma. Configure las siguientes propiedades:

   * **Nombre** del elemento: Especifique el nombre del componente.
   * **Título:** especifique un título único para el componente.
   * **Mensaje de plantilla:** especifique el mensaje que se mostrará mientras se carga el PDF de firma. Los servicios de Adobe Sign tardan algún tiempo en preparar y cargar el PDF de firma.
   * **Servicio de firma:** seleccione la  **opción** Firma manuscrita.
   * **Clase** CSS: Especifique la clase CSS de la biblioteca de cliente, si la hay. Se recomienda utilizar [themes](/help/forms/using/themes.md) y [estilos en línea](/help/forms/using/inline-style-adaptive-forms.md) en lugar de CSS Class.

   Pulse el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios. La firma se ha configurado correctamente.

   Ahora, al rellenar un formulario, se muestra una versión PDF de un formulario adaptable y se proporcionan las opciones para firmarlo. Para obtener información detallada, consulte [Firmar un formulario adaptable utilizando Scribble Signature](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## Firmar un formulario adaptable con firma manuscrita {#sign-an-adaptive-form-using-scribble-signature}

1. Después de rellenar un formulario adaptable y llegar a la página Paso de firma, se muestra la pantalla de firma.

   ![Pantalla de firma para la página EchoSign](assets/esignscribblesign.jpg)

1. Haga clic en **[!UICONTROL Sign]**. Aparecerá el cuadro de diálogo del signo de garabateo. Firme el formulario y haga clic en el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar la firma.

   ![Cuadro de diálogo de signo de almohadilla](assets/scribblewidget.jpg)

1. Haga clic en Completar para finalizar el proceso de firma.

   ![Completar el proceso de firma](assets/scribblecomplete.jpg)

Las firmas se agregan al formulario y el control de formulario se mueve al panel siguiente.

