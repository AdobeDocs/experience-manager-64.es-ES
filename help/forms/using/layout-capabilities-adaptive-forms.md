---
title: Funciones de diseño de los formularios adaptables
seo-title: Layout capabilities of adaptive forms
description: El diseño y el aspecto visual de los formularios adaptables en diferentes dispositivos se rigen por la configuración de diseño. Obtenga información sobre los distintos diseños y cómo aplicarlos.
seo-description: Layout and appearances of adaptive forms on various devices are governed by the layout settings. Understand the various layouts and how to apply them.
uuid: 7df2d234-e2e3-432a-9720-e73296424302
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 10bf1d44-9660-44d9-b2c3-dd9a252efc3a
feature: Adaptive Forms
exl-id: 887e88c6-4c2b-4ef3-b268-8956fdb4535f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 87%

---

# Funciones de diseño de los formularios adaptables {#layout-capabilities-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager (AEM) permite crear formularios adaptables fáciles de usar que ofrecen experiencias dinámicas a los usuarios finales. El diseño del formulario controla cómo se muestran los elementos o los componentes de un formulario adaptable.

## Conocimientos previos requeridos {#prerequisite-knowledge}

Antes de familiarizarse con las diferentes funciones de diseño de los formularios adaptables, lea los siguientes artículos para obtener más información sobre los formularios adaptables.

[Introducción a AEM Forms](/help/forms/using/introduction-aem-forms.md)

[Introducción a la creación de formularios](/help/forms/using/introduction-forms-authoring.md)

## Tipos de diseños {#types-of-layouts}

Un formulario adaptable proporciona los siguientes tipos de diseños:

**Diseño de panel**: controla cómo se muestran los elementos o componentes de un panel en un dispositivo.

**Diseño móvil**: controla la navegación de un formulario en un dispositivo móvil. Si la anchura del dispositivo es de 768 píxeles o más, el diseño se considera un diseño para móviles y se optimiza para un dispositivo móvil.

**Diseño de barra de herramientas**: controla la ubicación de los botones de acción en la barra de herramientas o la barra de herramientas del panel de un formulario.

Todos estos diseños de panel se definen en la siguiente ubicación:

`/libs/fd/af/layouts`.

>[!NOTE]
>
>Para cambiar el diseño de un formulario adaptable, utilice el modo Autor de AEM.

![Ubicación de los diseños en el repositorio CRX](assets/layouts_location_in_crx.png)

## Diseño de panel {#panel-layout}

Un autor de formularios puede asociar un diseño a cada uno de los paneles de un formulario adaptable, incluido el panel raíz.

Los diseños de panel están disponibles en la ubicación `/libs/fd/af/layouts/panel`. 

![Lista de diseños de panel del panel raíz de un formulario adaptable](assets/layouts.png)
**Figura:** *Lista de diseños de panel en formularios adaptables*

### Adaptable: todo en una página sin navegación {#responsive-everything-on-one-page-without-navigation-br}

Utilice este diseño de panel para crear un diseño adaptable que se ajuste al tamaño de pantalla del dispositivo sin necesidad de utilizar ningún tipo de navegación especializada.

Con este diseño, puede colocar varios componentes **[!UICONTROL Formulario adaptable con panel]** uno tras otro en el panel.

![Un formulario con diseño adaptable, tal como se ve en una pantalla pequeña](assets/responsive_layout_seen_on_small_screen.png)

**Figura:** *Un formulario con presentación interactiva, tal como se ve en una pantalla pequeña*

![Un formulario con diseño adaptable, tal como se ve en una pantalla grande](assets/responsive_layout_seen_on_large_screen.png)

**Figura:** *Un formulario con presentación interactiva, tal como se ve en una pantalla grande*

### Asistente: un formulario con varios pasos que se muestra paso por paso {#wizard-a-multi-step-form-showing-one-step-at-a-time}

Utilice este diseño de panel para proporcionar navegación guiada dentro de un formulario. Por ejemplo, utilice este diseño cuando desee capturar información obligatoria en un formulario y guiar a los usuarios paso a paso.

Utilice el componente `Panel adaptive form` para proporcionar navegación paso a paso dentro de un panel. Cuando se utiliza este diseño, el usuario solo puede pasar al siguiente paso una vez que ha completado el paso actual.

```
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![Expresión de finalización de los pasos en el diseño Asistente de un formulario de varios pasos](assets/layout-sidebar.png)

**Figura:** *Expresión de finalización de pasos en la presentación del Asistente para un formulario de varios pasos*

![Un formulario con el diseño Asistente](assets/wizard-layout.png)

**Figura:** *Un formulario con el Asistente*

### Diseño de acordeón {#layout-for-accordion-design}

Con este diseño, puede colocar el componente `Panel adaptive form` en un panel con navegación de estilo acordeón. Este diseño también permite crear paneles repetibles. Los paneles repetibles permiten agregar o quitar paneles de forma dinámica según sea necesario. Puede definir el número mínimo y máximo de veces que se repite un panel. Además, el título del panel se puede determinar dinámicamente en función de la información proporcionada en los elementos del panel.

La expresión de resumen se puede utilizar para mostrar los valores proporcionados por el usuario final en el título del panel minimizado.

![Paneles repetibles con el diseño Acordeón en un formulario adaptable](assets/repeatable_panels_using_accordion_layout.png)

**Figura:** *Paneles repetibles creados con el diseño Acordeón*

### Diseño con pestañas: las pestañas aparecen a la izquierda {#tabbed-layout-tabs-appear-on-the-left}

Con este diseño, puede colocar el componente `Panel adaptive form` en un panel con navegación basada en pestañas. Las pestañas se colocan a la izquierda del contenido del panel.

![En el Diseño con pestañas, las pestañas aparecen a la izquierda](assets/tabbed_layout_left.png)

**Figura:** *Pestañas que aparecen a la izquierda de un panel*

### Diseño con pestañas: las pestañas aparecen en la parte superior {#tabbed-layout-tabs-appear-on-the-top}

Con este diseño, puede colocar el componente `Panel adaptive form` en un panel con navegación basada en pestañas. Las pestañas se colocan sobre el contenido del panel.

![Diseño con pestañas en un formulario adaptable con pestañas en la parte superior](assets/tabbed_layout_top.png)

**Figura:** *Pestañas que aparecen en la parte superior de un panel*

## Diseños móviles {#mobile-layouts}

Los diseños móviles proporcionan una navegación fácil de usar en los dispositivos móviles con pantallas relativamente más pequeñas. Los diseños móviles utilizan estilos con pestañas o de asistente para la navegación del formulario. La aplicación de un diseño para móvil proporciona un diseño único para todo el formulario.

Este diseño controla la navegación mediante una barra y un menú de navegación. La barra de navegación muestra los iconos **&lt;** y **>** para indicar los pasos de navegación **Siguiente** y **Anterior** en el formulario.

Los diseños móviles están disponibles en la ubicación `/libs/fd/af/layouts/mobile/`. Los siguientes diseños móviles están disponibles en los formularios adaptables de forma predeterminada.

![Lista de diseños móviles de un formulario adaptable](assets/mobile-navigation.png)

**Figura:** *Lista de diseños móviles en formularios adaptables*

Cuando se utiliza un diseño móvil, el menú del formulario está disponible para acceder a los diferentes paneles del formulario pulsando el icono ![aem6forms_menú_formulario](assets/aem6forms_form_menu.png).

### Diseño con títulos de panel en el encabezado del formulario {#layout-with-panel-titles-in-the-form-header}

Este diseño, como su nombre indica, muestra los títulos de los paneles junto con el menú y la barra de navegación. También incluye los iconos Siguiente y Anterior para la navegación.

![Diseños móviles con títulos de panel en los encabezados del formulario](assets/mobile_layout_with.png)

**Figura:** *Presentaciones móviles con títulos de panel en los encabezados de formulario*

### Diseño sin títulos de panel en el encabezado del formulario {#layout-without-panel-titles-in-the-form-header}

Este diseño, como su nombre indica, muestra únicamente el menú y la barra de navegación, sin títulos de panel. También incluye los iconos Siguiente y Anterior para la navegación.

![Diseños móviles sin títulos de panel en los encabezados del formulario](assets/mobile_layout_without.png)

**Figura:** *Presentaciones móviles sin títulos de panel en los encabezados de formulario*

## Diseños de barra de herramientas {#toolbar-layouts}

El diseño de barra de herramientas controla la colocación y la visualización de cualquier botón de acción que agregue a los formularios adaptables. El diseño se puede agregar en el nivel de formulario o de panel.

![Una lista de diseños de barra de herramientas en formularios adaptables para controlar el diseño de los botones](assets/toolbar-layouts.png)

**Figura:** *Una lista de diseños de barra de herramientas en formularios adaptables*

Los diseños de barra de herramientas están disponibles en la ubicación `/libs/fd/af/layouts/toolbar`. Los formularios adaptables proporcionan los siguientes diseños de barra de herramientas de forma predeterminada.

### Diseño predeterminado para la barra de herramientas {#default-layout-for-toolbar}

Este diseño está seleccionado como el diseño predeterminado cuando se añaden botones de acción a un formulario adaptable. Al seleccionar este diseño, se muestra el mismo diseño tanto para los equipos de escritorio como para los dispositivos móviles.

Además, puede agregar varias barras de herramientas que contengan botones de acción configurados con este diseño. Un botón de acción está asociado a un control de formulario. Puede configurar las barras de herramientas para que aparezcan antes o después de un panel.

![Vista predeterminada de la barra de herramientas](assets/toolbar_layout_default.png)

**Figura:** *Vista predeterminada de la barra de herramientas*

### Diseño fijo móvil para la barra de herramientas {#mobile-fixed-layout-for-toolbar}

Seleccione este diseño para proporcionar diseños alternativos para los equipos de escritorio y los dispositivos móviles.

En el caso del diseño de escritorio, puede agregar botones de acción utilizando una serie de etiquetas específicas. Solo se puede configurar una barra de herramientas con este diseño. Si hay más de una barra de herramientas configurada con este diseño, se produce una superposición en los dispositivos móviles y se muestra únicamente una barra de herramientas. Por ejemplo, puede colocar una barra de herramientas en la parte inferior o superior del formulario, o antes o después de los paneles.

En el caso del diseño móvil, puede añadir botones de acción mediante iconos.

![Diseño fijo móvil para la barra de herramientas](assets/toolbar_layout_mobile_fixed.png)

**Figura:** *Diseño fijo móvil para la barra de herramientas*
