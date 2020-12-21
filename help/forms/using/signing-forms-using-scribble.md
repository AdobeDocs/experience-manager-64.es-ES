---
title: Aplicar firmas electrónicas a un formulario mediante firmas de garabatos
seo-title: Aplicar firmas electrónicas a un formulario mediante firmas de garabatos
description: Firma de formularios mediante garabatos
seo-description: Firma de formularios mediante garabatos
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---


# Aplicar firmas electrónicas a un formulario utilizando firmas de garabatos {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

Puede utilizar el componente **Firma de garabatos** y el componente **Paso de firma** para dibujar la firma (Garabato) en un formulario adaptable. El componente de paso Firma muestra una versión PDF del formulario adaptable. Se requiere un Documento de la opción Registro activado o formularios adaptables basados en plantillas de formulario para utilizar el componente de paso Firma.

Ambos componentes proporcionan una ventana, como se muestra a continuación, para firmar un formulario. También puede hacer clic en el icono de geolocalización ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) para agregar geolocalización a la firma.

![Cuadro de diálogo de firma manuscrita](assets/scribble-signature.png)

## Configure un formulario adaptable para utilizar la firma manuscrita {#configure-an-adaptive-form-to-use-scribble-signature}

1. Cree un Documento de la opción Registro activada o un formulario adaptable basado en plantilla de formulario. Para obtener información paso a paso, consulte [Creación de un formulario adaptable](/help/forms/using/creating-adaptive-form.md).
1. Arrastre y suelte el componente **Firma de garabatos** desde el navegador de componentes al formulario adaptable.
1. Toque el icono **Configurar** ![configurar](assets/configure.png). Abre el navegador de propiedades y muestra las propiedades del componente Firma de garabatos. Configure las propiedades del componente Firma de garabatos.
1. Arrastre y suelte el componente Paso de firma desde el navegador de componentes al formulario adaptable.

   >[!NOTE]
   >
   >El componente Paso de firma ocupa toda la anchura disponible para el formulario. Se recomienda no tener ningún otro componente en la sección que contenga el componente Paso de firma.

1. En el navegador de contenido, toque **Contenedor de formulario** y el icono **Configurar** ![configurar](assets/configure.png). Abre el navegador de propiedades y muestra las propiedades del contenedor de formulario adaptable. Vaya a **Contenedor de formulario adaptable** > **Firma electrónica** y anule la selección de la opción **Habilitar Adobe Sign**. Toque el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios.

   >[!NOTE]
   >
   >Cuando se agrega un componente Paso de firma a un formulario adaptable, la opción Activar Adobe Sign se selecciona automáticamente.

1. Toque el icono **Configurar** ![configurar](assets/configure.png). Abre el navegador de propiedades y muestra las propiedades del paso Firma. Configure las siguientes propiedades:

   * **Nombre** del elemento: Especifique el nombre del componente.
   * **Título:** especifique un título único del componente.
   * **Mensaje de plantilla:** especifique el mensaje que se mostrará mientras se carga el PDF de firma. Los servicios de Adobe Sign tardan algún tiempo en preparar y cargar archivos PDF de firma.
   * **Servicio de firma:** seleccione la opción  **Firma** de garabatos.
   * **Clase** CSS: Especifique la clase CSS de la biblioteca del cliente, si la hay. Se recomienda utilizar [temáticas](/help/forms/using/themes.md) y [estilos en línea](/help/forms/using/inline-style-adaptive-forms.md) en lugar de Clase CSS.

   Toque el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios. La firma se ha configurado correctamente.

   Ahora, al rellenar un formulario, se muestra una versión PDF del formulario adaptable y se proporcionan opciones para firmar el documento PDF. Para obtener información detallada, consulte [Firmar un formulario adaptable con firma manuscrita](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## Firmar un formulario adaptable con la firma manuscrita {#sign-an-adaptive-form-using-scribble-signature}

1. Después de rellenar un formulario adaptable y llegar a la página Paso de firma, se muestra la pantalla de firma.

   ![Pantalla de firma para la página EchoSign](assets/esignscribblesign.jpg)

1. Haga clic en **[!UICONTROL Firmar]**. Aparecerá el cuadro de diálogo de firma de garabatos. Firme el formulario y haga clic en el icono Listo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar la firma.

   ![Cuadro de diálogo de firma manuscrita](assets/scribblewidget.jpg)

1. Haga clic en Finalizar para finalizar el proceso de firma.

   ![Completar el proceso de firma](assets/scribblecomplete.jpg)

Las firmas se agregan al formulario y el control del formulario se desplaza al panel siguiente.

