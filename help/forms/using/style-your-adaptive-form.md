---
title: Estilo del formulario adaptable
seo-title: Style your adaptive form
description: Aprenda a crear un tema personalizado, aplicar estilo a componentes individuales y utilizar fuentes web en un tema
seo-description: Learn to create a custom theme, style individual components, and use web fonts in a theme
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
exl-id: 0ccf43eb-f0c6-4204-8325-f891caa8f5af
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2049'
ht-degree: 11%

---

# Estilo del formulario adaptable {#do-not-publish-style-your-adaptive-form}

Aprenda a crear un tema personalizado, aplicar estilo a componentes individuales y utilizar fuentes web en un tema

![](do-not-localize/08-style_your_adaptiveformmain.png)

Este tutorial es un paso en la [Crear el primer formulario adaptable](create-your-first-adaptive-form.md) serie. Se recomienda seguir la serie en secuencia cronológica para comprender, realizar y demostrar el caso de uso completo del tutorial.

## Acerca del tutorial  {#about-the-tutorial}

Puede utilizar temas para proporcionar un aspecto y un estilo únicos a un formulario adaptable. Puede aplicar temas predeterminados con el editor de formularios adaptables o crear temas personalizados propios. AEM Forms proporciona un [editor de temas](themes.md) para crear temas personalizados. Un solo tema puede proporcionar un aspecto diferente al mismo formulario adaptable abierto en dispositivos móviles, tabletas o de escritorio. No es necesario tener conocimientos previos de CSS o LESS para utilizar el editor de temas, pero se desea.

Al final del tutorial, aprenderá a:

* Aplicación de un tema predeterminado a un formulario adaptable
* Creación de un tema para un formulario adaptable mediante el editor de temas
* Estilo de los componentes individuales
* Sección Bonos: Usar fuentes web en un tema personalizado

El formulario será similar al siguiente después de completar el tutorial:

![Formulario con un tema personalizado](assets/styled-adaptive-form.png)

## Antes de comenzar {#before-you-start}

Descargue las imágenes de estilo de encabezado y logotipo, a continuación, en su equipo local. El encabezado de la variable `shipping-address-add-update-form` el formulario adaptable utiliza las imágenes de estilo de encabezado y logotipo. La imagen de estilo de encabezado aparece a la derecha del encabezado.

[Obtener archivo](assets/header-style.png)

[Obtener archivo](assets/logo-1.png)

## Paso 1: Aplicar un tema a un formulario adaptable {#step-apply-a-theme-to-your-adaptive-form}

El editor de formularios adaptables proporciona varios temas predeterminados. Si planea no utilizar un estilo personalizado para el formulario adaptable, también puede publicar los formularios adaptables con un tema incorporado. Los temas son independientes de las formas adaptables. Puede aplicar el mismo tema a varios formularios adaptables. Para aplicar un tema a un formulario adaptable:

1. Abra el formulario adaptable para editarlo.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Abrir propiedades de **Contenedor de formulario adaptable**. En el navegador de propiedades, vaya a **Básico** > **Tema del formulario adaptable**. La variable **Tema del formulario adaptable** enumera todos los temas predeterminados y personalizados. De forma predeterminada, se aplica el tema Lienzo .
1. Seleccione un tema de la **Tema del formulario adaptable** campo . Por ejemplo, **Tema de encuesta**. Toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para aplicar el tema seleccionado.

![Formulario adaptable con el tema predeterminado](assets/default-adaptive-form.png)

**Figura:** *Formulario adaptable con el tema predeterminado*

![Formulario adaptable con el tema de Survey](assets/adaptive-form-with-survey-theme.png)

**Figura:** *Formulario adaptable con el tema de Survey*

## Paso 2: Actualizar el formulario adaptable {#step-update-your-adaptive-form}

El diseño mostrado arriba requiere cambios en el texto del marcador de posición y en el logotipo de su formulario adaptable existente. Realice los siguientes pasos para realizar los cambios necesarios:

1. Cambie el logotipo y el texto existentes del encabezado. Para eliminar el logotipo:

   1. Abra el formulario en el editor de formularios.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Pulse la imagen del logotipo en el componente del encabezado y pulse ![cmppr](assets/cmppr.png) propiedades. En la propiedad de imagen, pulse X para eliminar la imagen del logotipo existente.
   1. Pulse cargar, seleccione el logotipo.png y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para guardar los cambios. La imagen se descargó en el [Antes de comenzar](/help/forms/using/style-your-adaptive-form.md#before-you-start) para obtener más información.
   1. Toque el texto del encabezado. `We.Retail`y toque ![aem_6_3_edit](assets/aem_6_3_edit.png) **editar**. Cambiar el texto del encabezado a `we retail`. Aplicar formato de negrita solo a `we`en `we retail`.

   ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Elimine el título y añada texto de marcador de posición:

   1. Pulse el campo ID de cliente y pulse ![cmppr](assets/cmppr.png) propiedades.
   1. Copie el contenido del **Título** para **Texto del marcador de posición** campo .
   1. Elimine el contenido del **Título** toque y campo ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Repita los tres pasos anteriores para todos los cuadros de texto, cuadros numéricos y campos de correo electrónico del formulario.

   ![formulario adaptable actualizado](assets/updated-adaptive-form.png)

## Paso 3: Crear un tema personalizado para el formulario adaptable {#step-create-a-custom-theme-for-your-adaptive-form}

Puede usar [editor de temas](/help/forms/using/themes.md) para crear temas personalizados. El editor de temas es un poderoso editor WYSIWYG. Es un método visual aplicar CSS a varios componentes de un formulario adaptable. Proporciona controles más precisos para aplicar estilo a los componentes y paneles de un formulario adaptable.

Un tema es una entidad independiente como los formularios adaptables. Contiene estilos (CSS) para los componentes y paneles de un formulario adaptable. Los estilos incluyen propiedades CSS como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar un tema, el estilo especificado se aplica a los componentes correspondientes de un formulario adaptable.

En este tutorial, aplicará estilo al encabezado y al pie de página, a los componentes numéricos y de texto, al componente de datos adjuntos y a los botones. Empecemos por crear un tema:

### Creación de un tema {#create-a-theme}

1. Inicie sesión en la instancia de autor de AEM y vaya a **Adobe Experience Manager** > **Forms** > **Temas**. La dirección URL predeterminada es [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Toque **[!UICONTROL Crear]** y seleccione **[!UICONTROL Tema]**. Aparece la página Crear tema con los campos necesarios para crear un tema. Los campos Título y Nombre son obligatorios:

   * **Título:** Especifique un título para el tema. Por ejemplo, **Tema Global.** El título le ayuda a identificar el tema en la lista de temas.
   * **Nombre:** Especifique el nombre del tema. Por ejemplo, **Tema Global.** Se crea un nodo con el nombre especificado en el repositorio. A medida que empieza a escribir un título, el valor del campo de nombre se genera automáticamente. Puede cambiar el valor sugerido. El campo de nombre solo puede incluir caracteres alfanuméricos, guiones y guiones bajos. Todas las entradas no válidas se sustituyen por guiones.

1. Pulse **Crear**. Se crea un tema y aparece un cuadro de diálogo para abrir el formulario y editarlo. Toque **Apertura** para abrir el tema recién creado en una pestaña nueva. El tema se abre en el editor de temas. Para el estilo, el editor de temas utiliza un formulario adaptable incorporado que se incluye con AEM Forms.

   Para obtener información sobre el uso de la IU del editor de temas, consulte [Acerca del editor de temas](/help/forms/using/themes.md#aboutthethemeeditor).

1. Toque **Opciones de tema** ![tema-opciones](assets/theme-options.png) > **Configurar**. En el **Vista previa del formulario** , seleccione **Shipping-address-add-update-form** formulario adaptable, pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), toque **Guardar**. Ahora, el editor de temas está configurado para usar su propio formulario adaptable en lugar del formulario adaptable predeterminado. Toque **Cancelar** para volver al editor de temas.

   ![custom-theme](assets/custom-theme.png)

   **Figura:** *Editor de temas con el formulario adaptable Shipping-address-add-update-form*

   ![create-a-theme](assets/create-a-theme.png)

   **Figura:** *Formulario adaptable con el formulario predeterminado*

### Encabezado y pie de página de estilo {#style-header-and-footer}

El encabezado y el pie de página proporcionan un aspecto coherente y distintivo a un formulario adaptable. Por lo general, el encabezado contiene el logotipo y el nombre de la organización, el pie de página contiene información sobre los derechos de autor y estos datos siguen siendo idénticos en varias formas de organización. Para aplicar estilo al encabezado y al pie de página del formulario adaptable Shipping-address-add-update-form:

1. Vaya a la **Encabezado** > **Texto** en el panel Selectores. El panel Selectores se encuentra a la izquierda del editor de temas. Si el panel no está visible, pulse ![Alternar panel lateral](assets/toggle-side-panel.png) Alternar panel lateral.

1. Establezca las siguientes propiedades en la variable **Texto** acordeón y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Valor |
   |---|---|
   | Familia de fuentes | Arial |
   | Color de fuente | FFFFFF |
   | Tamaño de fuente | 54px |

1. Pulse el widget de encabezado y pulse **Encabezado**. Las opciones para aplicar estilo al widget de encabezado aparecen a la izquierda. Expanda el **Dimension y posición** el acordeón, establezca la variable **Altura** a `120px`y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Expanda el acordeón Fondo del widget de encabezado, establezca la variable **Color de fondo** a `F6921E.`

   Pase el ratón **Imagen y degradado** > **+ Agregar**, toque **Imagen**. Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propiedad | Valor |
   |---|---|
   | imagen | Cargue header-style.png. La imagen se descargó en el [Antes de comenzar](/help/forms/using/style-your-adaptive-form.md#before-you-start) para obtener más información. |
   | Posición | Inferior Derecha |
   | Mosaico | No repetir |

1. En el editor de temas, pulse el logotipo en el encabezado y pulse **Logotipo de encabezado**. Expanda el acordeón Dimension y posición , defina las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
     <li>Superior: 1,5 rem</li> 
     <li>Abajo: -35 px</li> 
     <li>Izquierda: 1rem<strong><br /> </strong></li> 
    </ul> <p><strong>Sugerencia:</strong> Toque . <img src="assets/link.png"> icono de vínculo para proporcionar un valor diferente a cada campo.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Altura</td> 
   <td>4,75 rem</td> 
  </tr> 
 </tbody> 
</table>

1. Pulse el widget de pie de página y pulse **Pie de página**. Expanda el **Contexto** el acordeón, establezca la variable **Color de fondo** a `F6921E`y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Ajuste el estilo del componente de captura de datos y aplique un fondo al formulario adaptable {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

Puede utilizar varios componentes en un formulario adaptable para capturar datos. Por ejemplo, cuadro de texto y cuadro numérico. Puede proporcionar un estilo idéntico a todos los componentes de captura de datos o a todos los estilos independientes para cada componente. En este tutorial, se aplica un estilo idéntico a los cuadros numéricos (ID de cliente, código postal) y los cuadros de texto (ID de cliente, nombre, dirección de envío, estado, correo electrónico). Para aplicar estilo a los componentes de captura de datos:

1. Pulse el campo ID de cliente y pulse el botón **Widget de campos** . Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
     <li>Superior: 7px<br /> </li> 
     <li>Derecha: 7px<br /> </li> 
     <li>Abajo: 7px<br /> </li> 
     <li>Izquierda: 7px<br /> </li> 
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
   <td>18px</td> 
  </tr> 
  <tr> 
   <td>Dimension y posición</td> 
   <td>Anchura</td> 
   <td>60%</td> 
  </tr> 
  <tr> 
   <td>Dimension y posición</td> 
   <td>Margen</td> 
   <td> 
    <ul> 
     <li>Izquierda: 10 rem</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

1. Pulse en el área vacía encima del campo ID de cliente y pulse **Contenedor de panel interactivo**. Configure las variables **Contexto** > **Color de fondo** a F1F2F2. Toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### Estilo de los botones {#style-the-buttons}

Puede utilizar un tema personalizado para aplicar un estilo idéntico a todos los botones del formulario adaptable y [estilo en línea](/help/forms/using/inline-style-adaptive-forms.md) para aplicar un estilo a un botón específico. Para aplicar estilo a los botones:

1. Toque . **Submit** y pulse el botón **Botón** . Establezca las siguientes propiedades y pulse ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
     <li>Superior: 7px<br /> </li> 
     <li>Derecha: 7px<br /> </li> 
     <li>Abajo: 7px<br /> </li> 
     <li>Izquierda: 7px</li> 
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
   <td>18px</td> 
  </tr> 
 </tbody> 
</table>

1. [Aplicar el tema personalizado](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Tema global, a su forma adaptativa. Si el estilo no se refleja en el formulario adaptable, limpie la caché del explorador y vuelva a intentarlo.

   ![style-data-capture-components](assets/style-data-capture-components.png)

## Paso 4: Estilo de los componentes individuales {#step-style-individual-components}

Algunos estilos solo se aplican a un componente específico. Estos componentes están diseñados en el editor de formularios adaptables.

1. Abra el formulario adaptable para editarlo. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. En la barra superior, seleccione la opción **Estilo** .

   ![style-option](assets/style-option.png)

1. Toque . **Adjuntar** y pulse el botón ![aem_6_3_edit](assets/aem_6_3_edit.png)icono. Establezca las siguientes propiedades en la variable **Dimension y posición** acordeón:

   | Propiedad | Valor |
   |---|---|
   | Flotante | Izquierda |
   | Anchura | 10% |

1. Toque . **Prueba de dirección aprobada por el gobierno** y pulse la opción ![aem_6_3_edit](assets/aem_6_3_edit.png)icono. Establezca las siguientes propiedades:

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
   <td>73 %</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Espacio</td> 
   <td> 
    <ul> 
     <li>Izquierda: 10px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición</td> 
   <td>Altura</td> 
   <td>40px</td> 
  </tr> 
  <tr> 
   <td>Dimensiones y posición<br /> </td> 
   <td>Margen</td> 
   <td><br /> 
    <ul> 
     <li>Derecha: 2 rem</li> 
     <li>Izquierda: 10 rem </li> 
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
   <td>1px</td> 
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
   <td>7px</td> 
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
   <td>18px</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Altura de la línea</td> 
   <td>2</td> 
  </tr> 
 </tbody> 
</table>

1. Toque . **Submit** y pulse el botón ![aem_6_3_edit](assets/aem_6_3_edit.png) icono. Establezca las siguientes propiedades:

<table> 
 <tbody> 
  <tr> 
   <td>Acordeón</td> 
   <td>Propiedad</td> 
   <td>Valor</td> 
  </tr> 
  <tr> 
   <td>Dimension y posición</td> 
   <td>Flotante</td> 
   <td>Derecha</td> 
  </tr> 
  <tr> 
   <td>Dimension y posición</td> 
   <td>Margen</td> 
   <td> 
    <ul> 
     <li>Superior: 5 rem</li> 
     <li>Derecha: 14 rem</li> 
     <li>Abajo: 20px</li> 
     <li>Izquierda: 20px<br /> </li> 
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

## Paso 5: Sección Bonos: Uso de fuentes web en un tema personalizado {#step-bonus-section-using-web-fonts-in-a-custom-theme}

Puede utilizar varias fuentes para diseñar un formulario adaptable. Es posible que todos los dispositivos en los que se visualiza el formulario adaptable no tengan las fuentes utilizadas para diseñar el formulario adaptable. Puede utilizar un servicio de fuentes web para enviar las fuentes necesarias al dispositivo de destino.

Adobe Typekit es un servicio de fuentes web. Puede configurar y utilizar el servicio con formularios adaptables. Para utilizar Adobe Typekit en un formulario adaptable:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) Typekit ahora se denomina Adobe Fonts y se incluye con el Creative Cloud y otras suscripciones. [Más información](https://fonts.adobe.com/).

1. Cree un [Adobe Typekit](https://typekit.com/) , cree un kit, añada la fuente Myriad Pro al kit, publique el kit y obtenga el ID del kit. Es necesario utilizar fuentes Adobe Typekit (fuentes web) en un formulario adaptable.
1. En el servidor de AEM Forms, vaya a ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **Adobe Experience Manager** > **Herramientas** ![martillo](assets/hammer.png) > **Implementación** > **Cloud Services**. En la página Cloud Services, vaya a **Servicios de terceros** > **Typekit** y haga clic en **Configurar** Ahora en Typekit. Si una configuración ya está disponible, haga clic en el botón + para crear una nueva instancia.

   En el cuadro de diálogo Crear configuración, especifique un **Título** para la configuración y haga clic en **Crear**. Se le redirigirá a la página de configuración. En el cuadro de diálogo Editar componente que aparece, proporcione la **ID del kit** y haga clic en **OK**.

1. Configure el tema para utilizar la configuración TypeKit. En la instancia de autor, abra **Tema global** en el editor de temas. En el editor de temáticas, vaya a Opciones de temática![ theme-options](assets/theme-options.png) > Configurar. En **Configuración de Typekit** , seleccione el kit y haga clic en **Guardar**.

   Las fuentes agregadas a Typekit están disponibles para su selección en la **Texto** acordeón de todos los componentes.
