---
title: Activación de componentes del portal de formularios
seo-title: Activación de componentes del portal de formularios
description: Los componentes de Forms Portal están desactivados de forma predeterminada. Habilite los grupos Servicios de Documento y Predicados de servicios de Documento para habilitar los componentes de Forms Portal.
seo-description: Los componentes de Forms Portal están desactivados de forma predeterminada. Habilite los grupos Servicios de Documento y Predicados de servicios de Documento para habilitar los componentes de Forms Portal.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
translation-type: tm+mt
source-git-commit: 2abf448e0231eb6fcd9295f498a24e81e1ead11a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# Activación de componentes del portal de formularios {#enabling-forms-portal-components}

De forma predeterminada, los componentes del portal de formularios no están disponibles para su uso. Para que los componentes aparezcan en la lista de los componentes disponibles en AEM barra de tareas, lleve a cabo los siguientes pasos:

1. Inicie sesión en la instancia de creación del sitio web y abra una página de AEM Sites.

1. Para las páginas que utilizan una plantilla estática, realice los siguientes pasos:

   1. En el encabezado de página, toque ![lienzo-desplegable](assets/canvas-drop-down.png) > **Diseño** para abrir la página en modo Diseño.
   1. Toque cualquier componente (con un borde azul) y, a continuación, toque el nivel ![de](assets/field-level.png) campo para seleccionar el sistema de párrafos que contiene el componente actual.
   1. En el sistema de párrafos, toque ![settings_icon](assets/settings_icon.png) para abrir el cuadro de diálogo Editar del sistema de párrafos.
   1. Desde la lista de componentes **** permitidos, active las casillas de verificación de los componentes de Predicados de servicios **[!UICONTROL de]** Documento y servicios de **[!UICONTROL Documento]** . Toque **[!UICONTROL Aceptar]**.

1. Para las páginas que utilizan una plantilla dinámica, lleve a cabo los siguientes pasos:

   1. En el encabezado de página, toque ![propiedades](assets/properties.png) > **Editar plantilla** para abrir la plantilla de la página.
   1. Toque **Diseño Contenedor** y toque ![Administración de fuentes](assets/FeedManagement.png). En la ficha Componentes **** permitidos, habilite las opciones Servicios de **Documento y Predicados** de Servicios de Documento y toque ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>También puede activar componentes específicos de estas categorías seleccionando los componentes. Para obtener más información sobre los componentes y su uso, consulte [Creación de una página](/help/forms/using/creating-form-portal-page.md) de portal de formularios y [Incorporación del componente de vínculo en una página](/help/forms/using/embedding-link-component-page.md).

Ahora, las categorías de componentes de Documento Services y Documento Services Predicates están disponibles en el navegador de componentes. Los componentes están habilitados para todas las páginas que utilizan la misma plantilla.

## Artículos relacionados

* [Habilitar componentes del portal de formularios](/help/forms/using/enabling-forms-portal-components.md)
* [Crear página del portal de formularios](/help/forms/using/creating-form-portal-page.md)
* [Lista de formularios en una página web mediante API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Uso del componente Borradores y envíos](/help/forms/using/draft-submission-component.md)
* [Personalización del almacenamiento de borradores y formularios enviados](/help/forms/using/draft-submission-component.md)
* [Ejemplo para integrar el componente de borradores y envíos con la base de datos](/help/forms/using/integrate-draft-submission-database.md)
* [Personalización de plantillas para componentes del portal de formularios](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Introducción a la publicación de formularios en un portal](/help/forms/using/introduction-publishing-forms.md)
