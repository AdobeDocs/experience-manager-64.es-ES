---
title: '"Tutorial: Create an adaptive form"'
seo-title: '"Create an adaptive form"'
description: Aprenda a crear, diseñar y previsualización un formulario adaptable. Además, aprenda a configurar acciones de envío.
seo-description: Aprenda a crear, diseñar y previsualización un formulario adaptable. Además, aprenda a configurar acciones de envío.
page-status-flag: de-activated
uuid: 0010d274-a683-499e-9fa6-ce355d7898a0
discoiquuid: 55c08940-8c25-4938-8e49-25bce20aaf22
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 3%

---


# Tutorial: Creación de un formulario adaptable {#do-not-publish-tutorial-create-an-adaptive-form}

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

This tutorial is a step in the [Create Your First Adaptive Form](/help/forms/using/create-your-first-adaptive-form.md) series. It is recommended to follow the series in chronological sequence to understand, perform, and demonstrate the complete tutorial use case.

## About the tutorial {#about-the-tutorial}

Adaptive forms are new-generation forms that are dynamic and responsive. You can use Adaptive forms to deliver personalized experiences. You can also integrate adaptive forms with Adobe Analytics for usage statistics and Adobe Campaign for campaign management. Para obtener más información sobre las capacidades de los formularios adaptables, consulte [Introducción a la creación de formularios](/help/forms/using/introduction-forms-authoring.md)adaptables.

Es más fácil crear y administrar formularios cuando se sigue un proceso adecuado. En este artículo, aprenderá a:

* [Crear un formulario adaptable que permita al cliente agregar una dirección de envío](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Campos de diseño de un formulario adaptable para mostrar y aceptar información de un cliente](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Crear una acción de envío para enviar un correo electrónico con contenido de formulario](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Previsualización y envío de un formulario adaptable](/help/forms/using/create-adaptive-form.md)

Al final del artículo tendrá un formulario similar al siguiente:

    [ ![](do-not-localize/form-preview-mobile.gif)](assets/form-preview-mobile.gif)

## Paso 1: Creación del formulario adaptable {#step-create-the-adaptive-form}

1. Inicie sesión en la instancia de creación de AEM y vaya a **Adobe Experience Manager** > **Forms** > **Forms y Documentos**. La dirección URL predeterminada es [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Toque **Crear** y seleccione Formulario **** adaptable. An option to select a template appears. Tap the **Blank** template to select it and tap **Next**.

1. An option to **Add Properties** appears. The **Title** and **Name** fields are mandatory:

   * **Title:** Specify `Add new or update shipping address` in the Title field. The title field specifies the display name of the form. The title helps you identify the form in the AEM Forms user interface.
   * **Name:** Specify `shipping-address-add-update-form` in the Name field. El campo Nombre especifica el nombre del formulario. A node with the specified name is created in the repository. Al escribir un título con inicio, se genera automáticamente el valor del campo de nombre. You can change the suggested value. The name field can include only alphanumeric characters, hyphens, and underscores. Todas las entradas no válidas se reemplazan con un guión.

1. Toque **Crear**. Se crea un formulario adaptable y aparece un cuadro de diálogo para abrir el formulario y editarlo. Toque **Abrir** para abrir el formulario recién creado en una nueva ficha. The form opens for editing. También muestra la barra lateral para personalizar el formulario recién creado según las necesidades.

   Para obtener información sobre la interfaz de creación de formularios adaptables y los componentes disponibles, consulte [Introducción a la creación de formularios](/help/forms/using/creating-adaptive-form.md)adaptables.

   ![newly-created-adaptive-form](assets/newly-created-adaptive-form.png)

## Paso 2: Añadir encabezado y pie de página {#step-add-header-and-footer}

AEM Forms provides many components to display information on an adaptive form. Header and Footer components help provide a consistent look and feel to a form. A header typically includes the logo of a corporation, the title of the form, and summary. A footer typically includes copyright information and links to other pages.

1. Toque ![toggle-side-panel](assets/toggle-side-panel.png) > ![treeexpandall](assets/treeexpandall.png). The component browser opens. Arrastre el componente **Encabezado** desde el navegador de componentes al formulario adaptable.
1. Tap **Logo**. The toolbar appears. Tap ![aem_6_3_edit](assets/aem_6_3_edit.png) on the toolbar, type **We.Retail**, and tap ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

1. Tap Image. Aparece la barra de herramientas. Toque ![cmppr](assets/cmppr.png). The properties browser opens on the left of the screen. **Browse** and upload the logo image. Toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). The image appears on the header.

   You can tap Get file to download the logo used in this article if you don&#39;t have one.

   [Obtener archivo](assets/logo.png)

1. Drag the **Footer** component from ![treeexpandall](assets/treeexpandall.png) to the adaptive form. At this stage, the form looks like the following:

   ![adaptive-form-with-headers-and-footers](assets/adaptive-form-with-headers-and-footers.png)

## Step 3: Add components to capture and display information {#step-add-components-to-capture-and-display-information}

Components are building blocks of an adaptive form. AEM Forms provides many components to capture and display information in an adaptive form. Puede arrastrar los componentes de ![treeexpandall](assets/treeexpandall.png) a un formulario. Para obtener más información sobre los componentes disponibles y la funcionalidad correspondiente, consulte [Introducción a la creación de formularios](/help/forms/using/introduction-forms-authoring.md)adaptables.

1. Arrastre el componente Cuadro numérico al formulario adaptable. Colóquelo antes del componente de pie de página. Abra las propiedades del componente, cambie el **Título** del componente a **`Customer ID`**, cambie el Nombre **del** elemento a **`customer_ID`**, habilite la opción Campo **** requerido, active la opción **Usar tipo** ![](assets/aem_6_3_forms_save.png)de entrada de número HTML5 y toque aem_6_3_forms_save.
1. Arrastre tres componentes de Cuadro de texto al formulario adaptable. Colóquelas antes del componente de pie de página. Defina las siguientes propiedades para estos cuadros de texto.:

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Text Box 1<br /> </td> 
   <td>Text Box 2<br /> </td> 
   <td>Cuadro de texto 3</td> 
  </tr> 
  <tr> 
   <td>Título</td> 
   <td>Nombre<br /> </td> 
   <td>Dirección de envío</td> 
   <td>Estado</td> 
  </tr> 
  <tr> 
   <td>Nombre de elemento</td> 
   <td>customer_Name<br /> </td> 
   <td>customer_Shipping_Address</td> 
   <td>customer_State</td> 
  </tr> 
  <tr> 
   <td>Campo requerido</td> 
   <td>Activado</td> 
   <td>Activado</td> 
   <td>Activado</td> 
  </tr> 
  <tr> 
   <td>Allow multiple lines<br /> </td> 
   <td>Deshabilitado</td> 
   <td>Activado</td> 
   <td>Deshabilitado</td> 
  </tr> 
 </tbody> 
</table>

1. Arrastre un componente Cuadro **** numérico antes del componente de pie de página. Abra las propiedades del componente, defina los valores enumerados en la tabla siguiente, Toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Value |
   |---|---|
   | Título | Código postal |
   | Nombre de elemento | customer_ZIPCode |
   | Número máximo de dígitos | 6 |
   | Campo requerido | Activado |
   | Tipo de patrón de visualización | Sin patrón |

1. Arrastre un componente **Correo electrónico** antes del componente de pie de página. Abra las propiedades del componente, defina los valores enumerados en la tabla siguiente y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Value |
   |---|---|
   | Título | Correo electrónico |
   | Nombre de elemento | customer_Email |
   | Campo requerido | Activado |

1. Arrastre un componente **Archivo adjunto** antes del componente de pie de página. Abra las propiedades del componente, defina los valores enumerados en la tabla siguiente y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Value</td> 
  </tr> 
  <tr> 
   <td>Título</td> 
   <td>prueba de direcciones aprobada por el gobierno<br /> </td> 
  </tr> 
  <tr> 
   <td>Nombre de elemento</td> 
   <td>customer_Address_Prueba</td> 
  </tr> 
  <tr> 
   <td>Campo requerido</td> 
   <td>Activado</td> 
  </tr> 
 </tbody> 
</table>

1. Arrastre un componente Botón **de** envío al formulario adaptable. Colóquelo antes del componente de pie de página. Abra las propiedades del componente, cambie Nombre del elemento a **address_addin_submit**, toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). La presentación del formulario es completa y el formulario tiene el siguiente aspecto:

   ![adaptable-form-with-all-the-components](assets/adaptive-form-with-all-the-components.png)

## Paso 4: Configurar la acción de envío para el formulario adaptable {#step-configure-submit-action-for-the-adaptive-form}

Una acción de envío se activa cuando un usuario toca el botón Enviar en un formulario adaptable. Puede utilizar una acción de envío para guardar datos de formulario en el repositorio local, enviar datos de formulario a un extremo REST, enviar datos de formulario como correo electrónico, etc. Los formularios adaptables proporcionan algunas acciones de envío integradas más. Para obtener información detallada, consulte [Configuración de la acción](/help/forms/using/configuring-submit-actions.md)Enviar.

Mediante los siguientes pasos, puede configurar la acción de envío por correo electrónico y la acción de envío de demostración del formulario:

1. Configure el servidor de correo electrónico. Para obtener más información, consulte [Configuración de notificaciones](/help/sites-administering/notification.md)por correo electrónico.

   /content/help/en/experience-manager/6-4/sites-administering/notification.html

1. Toque **Formulario Contenedor** en el navegador de contenido y toque ![cmppr](assets/cmppr.png). El navegador de propiedades se abre a la izquierda.
1. Vaya a **Envío** > **Enviar acción**. Seleccione **Enviar correo electrónico**. Especifique los siguientes valores y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Value |
   |--- |--- |
   | De | `donotreply@weretail.com` |
   | A | `${customer_Email}` |
   | Asunto | Reconocimiento: Ha agregado la dirección de envío en el sitio web de We.Retail. |
   | Plantilla de correo electrónico | Hola `${customer_Name}`, se agrega la siguiente dirección como dirección de envío de su cuenta: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Regalos, We.Retail |
   | Incluir datos adjuntos | Activado |

   El formulario está listo. Ahora puede realizar la previsualización del formulario y probar la funcionalidad. Si ha utilizado el nombre mencionado en el tutorial y ha accedido al formulario en el equipo que ejecuta el servidor de AEM Forms, el formulario estará disponible en [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Paso 5: Previsualización y envío del formulario adaptable {#step-preview-and-submit-the-adaptive-form}

Puede utilizar la opción **** Previsualización para evaluar el aspecto y el comportamiento de un formulario. Puede enviar un formulario en modo de previsualización y también comprobar las validaciones aplicadas a un formulario. Por ejemplo, si se muestra un error cuando un campo obligatorio se deja vacío.

Los formularios adaptables también proporcionan una opción para emular la experiencia de un formulario para varios dispositivos. Por ejemplo, iPhone, iPad y Escritorio. Puede utilizar las opciones de **Previsualización** y de **regla del emulador** de forma conjunta ![](assets/ruler.png) para previsualización de un formulario para dispositivos de diferentes tamaños de pantalla.

1. Toque la opción de **Previsualización** en la parte derecha del editor de formularios. El formulario se abre en el modo de previsualización. Si ha utilizado el nombre mencionado en el tutorial, la dirección URL de previsualización del formulario es [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Utilice la ![regla](assets/ruler.png) para vista del aspecto del formulario en varios dispositivos.
1. Rellene los campos del formulario y toque **Enviar**. El formulario se envía y se le redirige a la página de **agradecimiento** predeterminada. También puede especificar una página de agradecimiento personalizada. Para obtener más información, consulte [Configuración de la página](/help/forms/using/configuring-redirect-page.md)de redireccionamiento.

El formulario adaptable para agregar una dirección está listo. Si ha utilizado el nombre mencionado en el tutorial y ha accedido al formulario en el equipo que ejecuta el servidor de AEM Forms, el formulario estará disponible en [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
