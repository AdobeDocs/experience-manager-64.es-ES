---
title: Incrustar un formulario adaptable o una comunicación interactiva en la página de AEM Sites
seo-title: Embed an adaptive form or interactive communication in AEM sites page
description: Puede incrustar formularios adaptables en páginas de AEM Sites. Los usuarios pueden rellenar y enviar formularios sin salir de las páginas de Sites.
seo-description: You can embed adaptive forms in AEM sites pages. Users can fill and submit forms without leaving the site pages.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications, author
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
exl-id: ba5d21a4-231c-4e1e-b172-4d700cb9696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 97%

---

# Incrustar un formulario adaptable o una comunicación interactiva en la página de AEM Sites {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

AEM Forms permite a los desarrolladores de formularios incrustar sin problemas formularios adaptables en una página de AEM Sites o en una página web hospedada fuera de AEM. El formulario adaptable y las comunicaciones interactivas incrustados son completamente funcionales y los usuarios pueden rellenarlos y enviarlos sin abandonar la página. Esto permite al usuario mantenerse en el contexto de otros elementos de la página web e interactuar simultáneamente con el formulario o la comunicación interactiva.

Para obtener información sobre la incrustación de un formulario adaptable en una página web externa, consulte [Incrustar formulario adaptable en una página web externa](/help/forms/using/embed-adaptive-form-external-web-page.md).

Puede agregar un formulario adaptable o una comunicación interactiva en la página de AEM Sites mediante los siguientes elementos:

* **[Componente Contenedor de AEM Forms](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms proporciona un componente que puede agregar a las páginas de Sites. El componente Contenedor de AEM Forms permite incrustar un formulario adaptable y una comunicación interactiva.

* **[Explorador de recursos](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Todos los formularios y las comunicaciones interactivas que cree estarán disponibles en Recursos. Puede arrastrar y colocar el formulario como un recurso en su página.

## Requisitos previos {#prerequisites}

Para incrustar un formulario adaptable o una comunicación interactiva en una página de AEM Sites que usa una plantilla editable, asegúrese de que el componente de AEM Forms esté configurado como un componente permitido en la plantilla asociada. Para obtener más información, consulte la sección **directiva y propiedades (Contenedor de diseño)** en [Creación de plantillas de página](/help/sites-authoring/templates.md).

En el caso de las páginas de Sites que usan una plantilla estática, deberá configurarlo en el sistema de párrafos de la página de Sites. Consulte [Configuración de componentes en el modo Diseño](/help/sites-authoring/default-components-designmode.md) para obtener más información.

## Incrustar un formulario adaptable o comunicación interactiva {#af-component}

Para incrustar un formulario adaptable o una comunicación interactiva mediante el componente Contenedor de AEM Forms:

1. Abra la página de AEM Sites, en el modo de edición, en la que desee incrustar un formulario adaptable o comunicación interactiva.
1. En el panel Explorador de componentes, arrastre y coloque el componente Contenedor de AEM Forms en la página.

   También puede buscar un formulario adaptable o una comunicación interactiva en el explorador de recursos y arrastrarlo y colocarlo en la página de Sites. Esto incrustará el formulario en un contenedor de AEM Forms.

   >[!NOTE]
   >
   >No se admiten varios componentes de contenedor de AEM Forms en una misma página.

1. Pulse el componente Contenedor de AEM Forms incrustado en la página de Sites y, a continuación, pulse ![settings_icon](assets/settings_icon.png) en la barra de acciones. Se abre el cuadro de diálogo **[!UICONTROL Editar contenedor de AEM Forms]**.
1. En el cuadro de diálogo Editar contenedor de AEM Forms, especifique lo siguiente.

   * **Tipo de recurso:** seleccione el tipo de recurso que desea incrustar. Las opciones son formulario adaptable y comunicación interactiva
   * **Ruta del recurso**: busque y seleccione el formulario adaptable que desea incrustar. Se rellenará automáticamente si ha sacado el formulario del explorador de recursos.
   * (Solo formulario adaptable) **Publicar envío**: seleccione la acción para habilitar el envío del formulario. Puede elegir mostrar un mensaje o una página de agradecimiento.

      * **Mensaje de agradecimiento**: escriba un mensaje con el editor de texto enriquecido para mostrarlo después del envío del formulario. Esta opción solo está disponible cuando elige mostrar un mensaje de agradecimiento.
      * **Página de agradecimiento**: examine y seleccione la página que desea mostrar después del envío del formulario. Esta opción solo está disponible cuando elige mostrar una página de agradecimiento.
      * **Actualizar página en envío**: habilítelo para actualizar la página que contiene el formulario adaptable incrustado para mostrar la página de agradecimiento. De lo contrario, la página de agradecimiento reemplazará al formulario adaptable en el contenedor de AEM Forms sin actualizar la página de Sites subyacente. Esta opción solo está disponible cuando elige mostrar una página de agradecimiento.
   * **Temática**: seleccione una temática que defina el estilo de los componentes del formulario adaptable o de la comunicación interactiva. El estilo incluye propiedades de apariencia, como el estilo de fuente, el color de fondo, las dimensiones y la alineación.
   * **Altura**: especifique la altura del contenedor. Déjelo en blanco para cambiar automáticamente el tamaño del contenedor.
   * **Biblioteca de cliente CSS**: especifique la ruta a una biblioteca de cliente CSS.


1. Guarde la configuración. El formulario adaptable o la comunicación interactiva están incrustados en la página.

## Publicar formularios adaptables y comunicaciones interactivas incrustados {#publishing-embedded-adaptive-form-and-interactive-communication}

Consideremos los siguientes escenarios para publicar un recurso incrustado (formulario adaptable o comunicación interactiva) en la página de AEM Sites:

* Si publica la página de AEM Sites por primera vez y esta incluye un formulario adaptable o una comunicación interactiva incrustados, publique la página de Sites y el recurso incrustado.
* Si ha modificado únicamente el formulario adaptable o la comunicación interactiva incrustados en una página de Sites ya publicada, publique el recurso original y los cambios se reflejarán en la página de Sites publicada. La página de Sites publicada incluye una referencia al recurso y no requiere que vuelva a publicar la página.
* Si ha modificado la página de Sites y el formulario adaptable integrado o la comunicación interactiva, vuelva a publicar la página y el recurso incrustado.

## Modificar el formulario adaptable y la comunicación interactiva incrustados {#modifying-embedded-adaptive-form-and-interactive-communication}

La página de AEM Sites mantiene una referencia al formulario adaptable y a la comunicación interactiva en el contenedor de AEM Forms. Por lo tanto, todas las configuraciones y propiedades configuradas en el formulario adaptable original, como la temática, los estilos y la acción de envío, se mantienen en el formulario adaptable o la comunicación interactiva incrustados.

Para modificar cualquier configuración o propiedad del formulario adaptable o de la comunicación interactiva incrustados, realice una de las siguientes acciones.

* Abra el formulario original en formularios adaptables o comunicaciones interactivas en sus respectivos editores y modifíquelos.
* Pulse el formulario adaptable o la comunicación interactiva desde la página de Sites en el modo Edición y, a continuación, pulse **[!UICONTROL Editar en una nueva ventana]**. El formulario original se abrirá en el modo de edición, donde puede modificarlo.

>[!NOTE]
>
>Los cambios realizados en el formulario adaptable o comunicación interactiva originales se reflejarán automáticamente en el formulario incrustado. Sin embargo, vuelva a publicar el formulario adaptable, la comunicación interactiva o la página de Sites para reflejar los cambios en la página publicada.

## Consideraciones y prácticas recomendadas {#considerations-and-best-practices}

Tenga en cuenta los siguientes puntos al incrustar formularios adaptables en páginas de AEM Sites:

* El encabezado y el pie de página del formulario original no se incluyen en el formulario incrustado.
* Los borradores de los usuarios y los envíos de formularios incrustados son compatibles y visibles en las pestañas Borradores y Formularios enviados del portal de formularios.
* La acción de envío configurada en el formulario original se mantiene en el formulario incrustado.
* La segmentación de experiencias y las pruebas A/B configuradas en el formulario original no funcionan en el formulario incrustado. Sin embargo, puede utilizar la segmentación de experiencias en la página de Sites para presentar diferentes formularios basados en perfiles de usuario.
* Si Adobe Analytics está configurado para el formulario original, los datos de análisis del formulario incrustado se capturan en esta aplicación. Sin embargo, no está disponible en el informe de análisis de Forms.
