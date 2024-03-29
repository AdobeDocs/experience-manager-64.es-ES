---
title: Aplicar estilo a un formulario adaptable
seo-title: Style your adaptive form
description: Aprenda a crear una temática personalizada, a aplicar estilo a componentes individuales y a utilizar fuentes web en una temática
seo-description: Learn to create a custom theme, style individual components, and use web fonts in a theme
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
exl-id: 0ccf43eb-f0c6-4204-8325-f891caa8f5af
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 89%

---

# Aplicar estilo a un formulario adaptable {#do-not-publish-style-your-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Aprenda a crear una temática personalizada, a aplicar estilo a componentes individuales y a utilizar fuentes web en una temática

![](do-not-localize/08-style_your_adaptiveformmain.png)

Este tutorial es un paso en la serie [Crear su primer formulario adaptable](create-your-first-adaptive-form.md). Se recomienda seguir la serie en orden cronológico para comprender, realizar y mostrar el caso de uso del tutorial completo.

## Información sobre el tutorial  {#about-the-tutorial}

Puede utilizar temáticas para proporcionar una apariencia y un estilo únicos a un formulario adaptable. Puede aplicar temáticas predeterminadas con el editor de formularios adaptables o crear temáticas personalizadas propias. AEM Forms proporciona un [editor de temas](themes.md) para crear temas personalizados. Una sola temática puede proporcionar una apariencia diferente al mismo formulario adaptable abierto en dispositivos móviles, tabletas o de escritorio. No es necesario tener conocimientos previos de CSS o LESS para utilizar el editor de temáticas, pero es preferible tenerlos.

Al final del tutorial, aprenderá a hacer lo siguiente:

* Aplicar una temática predeterminada a un formulario adaptable
* Crear una temática para un formulario adaptable mediante el editor de temáticas
* Aplicar estilo a los componentes individuales
* Sección Bonus: usar fuentes web en una temática personalizada

El formulario será similar al siguiente después de completar el tutorial:

![Formulario con una temática personalizada](assets/styled-adaptive-form.png)

## Antes de comenzar {#before-you-start}

Descargue las siguientes imágenes de estilo de encabezado y logotipo en su equipo local. El encabezado del formulario adaptable `shipping-address-add-update-form` utiliza las imágenes de estilo de encabezado y logotipo. La imagen de estilo de encabezado aparece a la derecha del encabezado.

[Obtener archivo](assets/header-style.png)

[Obtener archivo](assets/logo-1.png)

## Paso 1: Aplicar una temática a un formulario adaptable {#step-apply-a-theme-to-your-adaptive-form}

El editor de formularios adaptables proporciona varias temáticas predeterminadas. Si no pretende utilizar un estilo personalizado para el formulario adaptable, también puede publicar los formularios adaptables con una temática incorporada. Las temáticas son independientes de los formularios adaptables. Puede aplicar la misma temática a varios formularios adaptables. Para aplicar una temática a un formulario adaptable, haga lo siguiente:

1. Abra el formulario adaptable para editarlo.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Abra las propiedades del **Contenedor de formularios adaptables**. En el explorador de propiedades, navegue hasta **Básico** > **Temática del formulario adaptable**. El campo **Temática del formulario adaptable** enumera todas las temáticas predeterminadas y personalizadas. De forma predeterminada, se aplica la temática Lienzo.
1. Seleccione una temática del campo **Temática del formulario adaptable**. Por ejemplo, **Temática de encuesta**. Pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para aplicar la temática seleccionada.

![Formulario adaptable con la temática predeterminada](assets/default-adaptive-form.png)

**Figura:** *formulario adaptable con la temática predeterminada*

![Formulario adaptable con la temática de encuesta](assets/adaptive-form-with-survey-theme.png)

**Figura:** *formulario adaptable con la temática de encuesta*

## Paso 2: Actualizar el formulario adaptable {#step-update-your-adaptive-form}

El diseño que se muestra más arriba requiere cambios en el texto del marcador de posición y en el logotipo de su formulario adaptable. Realice los siguientes pasos para realizar los cambios necesarios:

1. Cambie el logotipo y el texto existentes del encabezado. Para eliminar el logotipo, haga lo siguiente:

   1. Abra el formulario en el editor de formularios.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Pulse la imagen de logotipo en el componente encabezado y pulse las propiedades ![cmppr](assets/cmppr.png). En la propiedad imagen, pulse X para eliminar la imagen del logotipo existente.
   1. Pulse cargar, seleccione el logo.png y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios. La imagen se descargó en la sección [Antes de comenzar](/help/forms/using/style-your-adaptive-form.md#before-you-start).
   1. Pulse el texto del encabezado. `We.Retail` y pulse ![aem_6_3_edit](assets/aem_6_3_edit.png) **Editar**. Cambie el texto del encabezado a `we retail`. Aplique formato de negrita solo a `we`en `we retail`.

   ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Elimine el título y agregue un texto de marcador de posición:

   1. Pulse el campo ID de cliente y pulse las propiedades ![cmppr](assets/cmppr.png).
   1. Copie el contenido del campo **Título** en el campo **Texto del marcador de posición**.
   1. Elimine el contenido del campo **Título** y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Repita los tres pasos anteriores para todos los cuadros de texto, cuadros numéricos y campos de correo electrónico del formulario.

   ![updated-adaptive-form](assets/updated-adaptive-form.png)

## Paso 3: Crear una temática personalizada para el formulario adaptable {#step-create-a-custom-theme-for-your-adaptive-form}

Puede usar el [Editor de temáticas](/help/forms/using/themes.md) para crear temáticas personalizadas. El editor de temáticas es un poderoso editor WYSIWYG. Es un método visual para aplicar CSS a varios componentes de un formulario adaptable. Proporciona controles más precisos para aplicar estilo a los componentes y los paneles de un formulario adaptable.

Una temática es una entidad independiente como los formularios adaptables. Contiene estilos (CSS) para los componentes y paneles de un formulario adaptable. Los estilos incluyen propiedades CSS como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar una temática, el estilo especificado se aplica a los componentes correspondientes de un formulario adaptable.

En este tutorial, aplicará estilo al encabezado y al pie de página, a los componentes numéricos y de texto, al componente de datos adjuntos y a los botones. Empecemos por crear una temática:

### Crear una temática {#create-a-theme}

1. Inicie sesión en la instancia de autor de AEM y navegue hasta **Adobe Experience Manager** > **Formularios** > **Temáticas**. La dirección URL predeterminada es [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Pulse **[!UICONTROL Crear]** y seleccione **[!UICONTROL Temática]**. Aparecerá la página Crear temática con los campos necesarios para crear una temática. Los campos Título y Nombre son obligatorios:

   * **Título:** especifique un título para la temática. Por ejemplo, **Temática Global.** El título le ayuda a identificar la temática en la lista de temáticas.
   * **Nombre:** especifique el nombre de la temática. Por ejemplo, **Temática Global.** Se crea un nodo con el nombre especificado en el repositorio. A medida que empieza a escribir un título, el valor del campo de nombre se genera automáticamente. Puede cambiar el valor sugerido. El campo de nombre solo puede incluir caracteres alfanuméricos, guiones y guiones bajos. Todas las entradas no válidas se sustituyen por guiones.

1. Pulse **Crear**. Se crea una temática y aparece un cuadro de diálogo para abrir el formulario y editarlo. Pulse **Abrir** para abrir la temática recién creada en una pestaña nueva. La temática se abre en el editor de temáticas. Para el estilo, el editor de temas utiliza un formulario adaptable incorporado que se incluye con AEM Forms.

   Para obtener información sobre el uso de la interfaz de usuario del editor de temáticas, consulte [Acerca del editor de temáticas](/help/forms/using/themes.md#aboutthethemeeditor).

1. Pulse **Opciones de temática** ![theme-options](assets/theme-options.png) > **Configurar**. En el campo **Vista previa del formulario**, seleccione el formulario adaptable **shipping-address-add-update-form**, pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), pulse **Guardar**. Ahora, el editor de temáticas está configurado para usar su propio formulario adaptable en lugar del formulario adaptable predeterminado. Pulse **Cancelar** para volver al editor de temáticas.

   ![custom-theme](assets/custom-theme.png)

   **Figura:** *editor de temáticas con el formulario adaptable shipping-address-add-update-form*

   ![create-a-theme](assets/create-a-theme.png)

   **Figura:** *formulario adaptable con el formulario predeterminado*

### Aplicar estilo al encabezado y al pie de página {#style-header-and-footer}

El encabezado y el pie de página proporcionan una apariencia coherente y distintiva a un formulario adaptable. Por lo general, el encabezado contiene el logotipo y el nombre de la organización, el pie de página contiene información sobre los derechos de autor y estos datos son idénticos en varias formas de organización. Para aplicar estilo al encabezado y al pie de página del formulario adaptable shipping-address-add-update-form, haga lo siguiente:

1. Navegue hasta la opción **Encabezado** > **Texto** en el panel Selectores. El panel Selectores se encuentra a la izquierda del editor de temáticas. Si el panel no está visible, pulse ![Alternar panel lateral](assets/toggle-side-panel.png) Alternar panel lateral.

1. Establezca las siguientes propiedades en el acordeón **Texto** y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Valor |
   |---|---|
   | Familia de fuentes | Arial |
   | Color de fuente | FFFFFF |
   | Tamaño de fuente | 54 px |

1. Pulse el widget encabezado y pulse **Encabezado**. Las opciones para aplicar estilo al widget de encabezado aparecen a la izquierda. Expanda el acordeón **Dimensiones y posición**, establezca la **Altura** a `120px` y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Expanda el acordeón del widget de encabezado Fondo, establezca el **Color de fondo** a `F6921E.`

   Pase el ratón sobre **Imagen y degradado** > **+ Agregar** y pulse **Imagen**. Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Valor |
   |---|---|
   | image | Cargue header-style.png. La imagen se descargó en la sección [Antes de comenzar](/help/forms/using/style-your-adaptive-form.md#before-you-start). |
   | Posición | Inferior Derecha |
   | Mosaico | No repetir |

1. En el editor de temáticas, pulse el logotipo en el encabezado y pulse **Logotipo de encabezado**. Expanda el acordeón Dimensiones y posición, defina las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Margen</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Margen</td> 
   <td> 
    <ul> 
     <li>Superior: 1,5 rem</li> 
     <li>Inferior: -35 px</li> 
     <li>Izquierda: 1rem<strong><br /> </strong></li> 
    </ul> <p><strong>Sugerencia:</strong> Pulse el icono de vínculo <img src="assets/link.png"> para proporcionar un valor diferente a cada campo.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Altura</td> 
   <td>4,75 rem</td> 
  </tr> 
 </tbody> 
</table>

1. Pulse el widget de pie de página y pulse **Pie de página**. Expanda el acordeón **Fondo**, establezca el **Color de fondo** a `F6921E` y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Aplicar un estilo al componente de captura de datos y un fondo al formulario adaptable {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

Puede utilizar varios componentes en un formulario adaptable para capturar datos. Por ejemplo, cuadro de texto y cuadro numérico. Puede proporcionar un estilo idéntico a todos los componentes de captura de datos o a todos los estilos independientes para cada componente. En este tutorial, se aplica un estilo idéntico a los cuadros numéricos (ID de cliente, código postal) y los cuadros de texto (ID de cliente, nombre, dirección de envío, estado, correo electrónico). Para aplicar estilo a los componentes de captura de datos, haga lo siguiente:

1. Pulse ID de cliente y pulse la opción **Widget de campo**. Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Acordeón</td> 
   <td>Propiedad</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Color del borde</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Radio de borde </td> 
   <td> 
    <ul> 
     <li>Superior: 7 px<br /> </li> 
     <li>Derecha: 7 px<br /> </li> 
     <li>Inferior: 7 px<br /> </li> 
     <li>Izquierda: 7 px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Familia de fuentes</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Color de fuente</td> 
   <td>939598<br /> </td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Tamaño de fuente</td> 
   <td>18 px</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Anchura</td> 
   <td>60 %</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Margen</td> 
   <td> 
    <ul> 
     <li>Izquierda: 10 rem</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

1. Pulse en el área vacía encima del campo ID de cliente y pulse **Contenedor del panel interactivo**. Configure el **Contexto** > **Color de fondo** a F1F2F2. Pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### Aplicar estilo a los botones {#style-the-buttons}

Puede utilizar una temática personalizada para aplicar un estilo idéntico a todos los botones del formulario adaptable y [aplicar estilo dentro de la línea](/help/forms/using/inline-style-adaptive-forms.md) para aplicar un estilo a un botón específico. Para aplicar estilo a los botones, haga lo siguiente:

1. Pulse el botón **Enviar** y pulse la opción **Botón**. Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Acordeón</td> 
   <td>Propiedad</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Fondo</td> 
   <td>Color de fondo</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Borde<br /> </td> 
   <td>Color del borde</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Radio de borde </td> 
   <td> 
    <ul> 
     <li>Superior: 7 px<br /> </li> 
     <li>Derecha: 7 px<br /> </li> 
     <li>Inferior: 7 px<br /> </li> 
     <li>Izquierda: 7 px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Texto<br /> </td> 
   <td>Familia de fuentes</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Color de fuente</td> 
   <td>FFFFFF</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Tamaño de fuente</td> 
   <td>18 px</td> 
  </tr> 
 </tbody> 
</table>

1. [Aplicar la temática personalizada](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Temática global, a su formulario adaptable. Si el estilo no se refleja en el formulario adaptable, limpie la memoria caché del explorador y vuelva a intentarlo.

   ![style-data-capture-components](assets/style-data-capture-components.png)

## Paso 4: Aplicar estilo a componentes individuales {#step-style-individual-components}

Algunos estilos solo se aplican a un componente específico. Estos componentes están diseñados en el editor de formularios adaptables.

1. Abra el formulario adaptable para editarlo. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. En la barra superior, seleccione la opción **Estilo**.

   ![style-option](assets/style-option.png)

1. Pulse el botón **Adjuntar** y pulse el icono ![aem_6_3_edit](assets/aem_6_3_edit.png). Establezca las siguientes propiedades en el acordeón **Dimensiones y posición**:

   | Propiedad | Valor |
   |---|---|
   | Flotante | Izquierda |
   | Anchura | 10 % |

1. Pulse **Prueba de dirección aprobada por el gobierno** y pulse el icono ![aem_6_3_edit](assets/aem_6_3_edit.png). Establezca las siguientes propiedades:

<table> 
 <tbody> 
  <tr> 
   <td>Acordeón</td> 
   <td>Propiedad</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Flotante</td> 
   <td>Izquierda</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Anchura</td> 
   <td>73 %</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Espacio</td> 
   <td> 
    <ul> 
     <li>Izquierda: 10 px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Altura</td> 
   <td>40 px</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición<br /> </td> 
   <td>Margen</td> 
   <td><br /> 
    <ul> 
     <li>Derecha: 2 rem</li> 
     <li>Izquierda: 10 rem </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Fondo</td> 
   <td>Color de fondo</td> 
   <td>FFFFFF</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Anchura de borde</td> 
   <td>1 px</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Estilo de borde</td> 
   <td>Sólido</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Color del borde</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Radio de borde</td> 
   <td>7 px</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Familia de fuentes</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Color de fuente</td> 
   <td>BCBEC0</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Tamaño de fuente</td> 
   <td>18 px</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Altura de la línea</td> 
   <td>2</td> 
  </tr> 
 </tbody> 
</table>

1. Pulse el botón **Enviar** y pulse el icono ![aem_6_3_edit](assets/aem_6_3_edit.png). Establezca las siguientes propiedades:

<table> 
 <tbody> 
  <tr> 
   <td>Acordeón</td> 
   <td>Propiedad</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Flotante</td> 
   <td>Derecha</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Margen</td> 
   <td> 
    <ul> 
     <li>Superior: 5 rem</li> 
     <li>Derecha: 14 rem</li> 
     <li>Inferior: 20 px</li> 
     <li>Izquierda: 20 px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Fondo</td> 
   <td>Color de fondo</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Borde</td> 
   <td>Color del borde</td> 
   <td>F6921E</td> 
  </tr> 
 </tbody> 
</table>

![styled-adaptive-form-1](assets/styled-adaptive-form-1.png)

## Paso 5: Sección Bonus: usar fuentes web en una temática personalizada {#step-bonus-section-using-web-fonts-in-a-custom-theme}

Puede utilizar varias fuentes para diseñar un formulario adaptable. Es posible que no todos los dispositivos en los que se visualiza el formulario adaptable tengan las fuentes utilizadas para diseñar el formulario adaptable. Puede utilizar un servicio de fuentes web para enviar las fuentes necesarias al dispositivo de destino.

Adobe Typekit es un servicio de fuentes web. Puede configurar y utilizar el servicio con formularios adaptables. Para utilizar Adobe Typekit en un formulario adaptable:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) Typekit ahora se denomina Adobe Fonts y se incluye con el Creative Cloud y otras suscripciones. [Más información](https://fonts.adobe.com/).

1. Cree un [Adobe Typekit](https://typekit.com/) , cree un kit, añada la fuente Myriad Pro al kit, publique el kit y obtenga el ID del kit. Es necesario utilizar fuentes Adobe Typekit (fuentes web) en un formulario adaptable.
1. En el servidor de AEM Forms, vaya a ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **Adobe Experience Manager** > **Herramientas** ![martillo](assets/hammer.png) > **Implementación** > **Cloud Services**. En la página Cloud Services, vaya a **Servicios de terceros** > **Typekit** y haga clic en **Configurar** Ahora en Typekit. Si una configuración ya está disponible, haga clic en el botón + para crear una nueva instancia.

   En el cuadro de diálogo Crear configuración, especifique un **título** para la configuración y haga clic en **Crear**. Se le redirigirá a la página de configuración. En el cuadro de diálogo Editar componente que aparece, proporcione el **ID del kit** y haga clic en **Aceptar**.

1. Configure el tema para utilizar la configuración TypeKit. En la instancia de autor, abra la **Temática global** en el editor de temáticas. En el editor de temáticas, vaya a Opciones de temática![ theme-options](assets/theme-options.png) > Configurar. En **Configuración de Typekit** , seleccione el kit y haga clic en **Guardar**.

   Las fuentes agregadas a Typekit están disponibles para su selección en la **Texto** acordeón de todos los componentes.
