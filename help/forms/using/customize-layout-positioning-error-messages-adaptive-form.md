---
title: Personalización de la presentación y la colocación de los mensajes de error de un formulario adaptable
seo-title: Customize layout and positioning of error messages of an adaptive form
description: Puede personalizar el diseño y la posición de los mensajes de error de una adaptación para.
seo-description: You can customize layout and positioning of the error messages of an adaptive for.
uuid: 18b6d770-8b68-4aa0-b866-6325a6ceabcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: e1431ad9-3bae-4ac3-97e2-96dcbfce1f71
exl-id: a57bd3c4-2d50-4089-8279-1e403e9469bf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 5%

---

# Personalización de la presentación y la colocación de los mensajes de error de un formulario adaptable {#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

Se puede personalizar la presentación y el posicionamiento de los mensajes de error de un formulario adaptable. Puede realizar las siguientes personalizaciones:

* Personalice la ubicación y el diseño del rótulo de un campo sin realizar ningún cambio en las propiedades CSS correspondientes
* Personalización de la posición de los mensajes de error en línea
* Personalización del contenido del indicador de ayuda dinámica
* Personalice la posición de los componentes del campo (rótulo, widget, descripción breve, descripción larga y componentes del indicador de ayuda) sin realizar ningún cambio en las propiedades CSS correspondientes

## Personalización del diseño de los campos {#customize-layout-of-fields}

Puede personalizar el diseño de un único campo o de todos los campos para cambiar la posición del rótulo y los mensajes de error. Siga los siguientes pasos para aplicar un diseño personalizado a un campo:

### Personalización del diseño de un único campo {#customize-layout-of-a-single-field}

Siga los siguientes pasos para aplicar un diseño personalizado a un único campo:

1. Abra el formulario en **Estilo** en el menú contextual. Para abrir el formulario en modo de estilo, en la barra de herramientas de la página, pulse ![lista desplegable de lienzo](assets/canvas-drop-down.png) > **Estilo**.
1. En la barra lateral, debajo de **Objetos de formulario**, seleccione el campo y pulse el botón editar ![editar-botón](assets/edit-button.png).
1. Seleccione el estado del campo que desea personalizar y especifique el estilo para ese estado.

   ![Especificación del estilo en línea de un campo](assets/edit-error-state.png)

### Personalización de la presentación de todos los campos de un formulario {#customize-layout-of-all-the-fields-of-a-form}

Con AEM Forms, ahora puede crear un tema y aplicarlo al formulario. El editor de temas permite especificar el estilo de los componentes del formulario en un lugar. Al crear un tema, se especifica el estilo en un nivel de componente. Para obtener más información sobre los temas, consulte [Temas en AEM Forms](/help/forms/using/themes.md).

Cree un tema con el Editor de temas para personalizar la presentación de todos los campos del formulario. Después de crear un tema, realice los siguientes pasos para aplicarlo a un formulario:

1. Abra el formulario en modo de edición. 

1. En el modo de edición, seleccione un componente y, a continuación, pulse ![field-level](assets/field-level.png) > **Contenedor de formulario adaptable** y haga clic en ![cmppr](assets/cmppr.png).
1. En la barra lateral, en Tema de formulario adaptable, seleccione el tema que ha creado con el Editor de temas.

## Creación de un diseño de campo personalizado {#create-a-custom-field-layout}

1. Abra CRXDE lite. El URL predeterminado es `https://[Server]:[Port]/crx/de`.
1. Copie un diseño de campo del nodo /libs/fd/af/layouts/field (por ejemplo, defaultFieldLayout) al nodo /apps (por ejemplo, /apps/af-field-layout).
1. Cambie el nombre del nodo copiado y el archivo defaultFieldLayout.jsp . Por ejemplo, errorOnRight.jsp.

1. Cambie el valor de las propiedades qtip y jcr:description del nodo copiado. Por ejemplo, cambie el valor de las propiedades a Error On Right

1. Para añadir nuevos estilos y comportamiento, cree una biblioteca de cliente en el nodo /etc.

   Por ejemplo, en la ubicación /etc/af-field-layout-clientlib, cree el nodo client-library. Agregue la propiedad categories con el valor af.field.errorOnRight y el archivo style.less con el siguiente código:

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. Para mejorar el aspecto y el comportamiento, incluya la biblioteca de cliente creada en el archivo de diseño (errorOnRight.jsp).
1. Abra el cuadro de diálogo de edición del campo y seleccione la opción **Estilo** pestaña . En el **Configuración del diseño de campo** cuadro desplegable, seleccione el diseño recién creado y haga clic en **OK**.

El paquete ErrorOnRight.zip contiene código para mostrar mensajes de error en el lado derecho de los campos.

[Obtener archivo](assets/erroronright.zip)
