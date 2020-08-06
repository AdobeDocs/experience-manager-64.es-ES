---
title: Conjuntos de medios mixtos
seo-title: Conjuntos de medios mixtos
description: Aprenda a trabajar con conjuntos de medios mixtos en medios dinámicos
seo-description: Aprenda a trabajar con conjuntos de medios mixtos en medios dinámicos
uuid: e37fa648-74e2-42e3-8611-8509c92ec00d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 599c316e-b6a7-4a28-bc4b-75d48409bde0
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 18%

---


# Conjuntos de medios mixtos {#mixed-media-sets}

Los conjuntos de medios mixtos le permiten proporcionar una combinación de imágenes, conjuntos de imágenes, conjuntos de giros y vídeos en una presentación.

Los conjuntos de medios mixtos se designan mediante un banner con la palabra **[!UICONTROL MixedMediaSet]**. Además, si se publica el conjunto de medios mixtos, se muestra la fecha de publicación, indicada por el icono **[!UICONTROL Mundo]**, junto a la fecha de la última modificación, indicada por el icono **[!UICONTROL Lápiz]**.

![chlimage_1-347](assets/chlimage_1-348.png)

>[!NOTE]
>
>Para obtener información sobre la interfaz de usuario de Recursos, consulte [Gestión de recursos con la IU](managing-assets-touch-ui.md)táctil.

## Inicio rápido: Conjuntos de medios mixtos {#quick-start-mixed-media-sets}

Para ayudarle en el uso inicial de los conjuntos de medios mixtos, siga estos pasos:

1. [Cargue los recursos](#uploading-assets).

   Comience por cargar las imágenes y los vídeos de los conjuntos de medios mixtos. Si es necesario, cree los [conjuntos de imágenes](image-sets.md) y los [conjuntos de giros](spin-sets.md). Dado que los usuarios pueden aplicar zoom a las imágenes en el visualizador de conjuntos de medios mixtos, tenga en cuenta el zoom al elegir las imágenes. Compruebe que las imágenes tengan al menos 2000 píxeles en la dimensión más grande.

1. [Crear conjuntos de medios mixtos.](#creating-mixed-media-sets)

   Para crear un conjunto de medios mixtos, en la página **[!UICONTROL Recursos]** , toque **[!UICONTROL Crear > Conjunto]** de medios mixtos y asigne un nombre al conjunto. Elija los recursos y, a continuación, elija el orden en que aparecen las imágenes.

   See [Working with Selectors.](working-with-selectors.md)

1. Configure los ajustes preestablecidos [del visor de medios](managing-viewer-presets.md)mixtos según sea necesario.

   Los administradores pueden crear o modificar ajustes preestablecidos del visualizador de conjuntos de medios mixtos. Para ver los medios mixtos con un ajuste preestablecido del visualizador, seleccione el conjunto de medios mixtos y, en el menú desplegable del carril izquierdo, seleccione **[!UICONTROL Visualizadores]**.

   Consulte **[!UICONTROL Herramientas > Recursos > Ajustes preestablecidos]** de visor para crear o editar ajustes preestablecidos de visor.

   Consulte [Añadir y editar ajustes preestablecidos de visor.](managing-viewer-presets.md)

1. [Conjuntos de medios mixtos de Previsualización.](#previewing-mixed-media-sets)

   Seleccione el conjunto de medios mixtos y puede previsualización. Haga clic en los iconos de miniaturas para examinar el conjunto de medios mixtos en el visor seleccionado. Puede elegir diferentes visores en el menú **[!UICONTROL Visores]** , disponible en el menú desplegable del carril izquierdo.

1. [Publicar conjuntos de medios mixtos.](#publishing-mixed-media-sets)

   Al publicar un conjunto de medios mixtos, se activa la URL y la cadena Incrustar. Además, debe [publicar el ajuste preestablecido](managing-viewer-presets.md#publishing-viewer-presets)de visor.

1. [Vincule las direcciones URL a la Aplicación web](linking-urls-to-yourwebapplication.md) o [incruste el visor](embed-code.md)de vídeo o de imágenes.

   AEM Assets crea llamadas mediante URL para conjuntos de medios mixtos y los activa después de publicar los conjuntos de medios mixtos. Puede copiar estas direcciones URL cuando previsualización recursos. Como alternativa, puede incrustarlos en su sitio Web.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Consulte [Vinculación de un conjunto de medios mixtos a una página web](linking-urls-to-yourwebapplication.md) e [Incrustación del visualizador de imágenes o vídeos](embed-code.md).

Si lo necesita, puede editar los conjuntos [de medios](#editing-mixed-media-sets)mixtos. Además, puede realizar vistas y modificar propiedades [de conjuntos de medios](managing-assets-touch-ui.md#editing-properties)mixtos.

>[!NOTE]
>
>Si tiene problemas al crear conjuntos, consulte [Resolución de problemas de Dynamic Media: modo](troubleshoot-dms7.md)Scene7.

## Carga de recursos {#uploading-assets}

Comience por cargar las imágenes y los vídeos de los conjuntos de medios mixtos. Dado que los usuarios pueden aplicar zoom a las imágenes en el visor de conjuntos de medios mixtos, asegúrese de tener en cuenta el zoom al elegir las imágenes. Compruebe que las imágenes tengan al menos 2000 píxeles en la dimensión más grande.

Además, si desea agregar conjuntos de giros o conjuntos de imágenes al conjunto de medios mixtos, cree también estos conjuntos.

## Creación de conjuntos de medios mixtos {#creating-mixed-media-sets}

Puede agregar imágenes, conjuntos de imágenes, conjuntos de giros y vídeos al conjunto de medios mixtos. Asegúrese de que los archivos, conjuntos de imágenes y conjuntos de giros están listos para publicarse antes de agregarlos al conjunto de medios mixtos.

Cuando se agregan recursos al conjunto, se añaden automáticamente en orden alfanumérico. Puede volver a ordenar o ordenar manualmente los recursos después de agregarlos.

**Para crear un conjunto** de medios mixtos:

1. En Assets, desplácese hasta donde desee crear un conjunto de medios mixtos, haga clic en **Crear** y seleccione **[!UICONTROL Conjunto de medios mixtos]**. También puede crear el conjunto desde una carpeta que contenga los recursos.

   ![chlimage_1-347](assets/chlimage_1-349.png)

1. En la página Editor **[!UICONTROL de conjuntos de medios]** mixtos, en **[!UICONTROL Título]**, introduzca un nombre para el conjunto de medios mixtos. El nombre aparece en la pancarta del conjunto de medios mixtos. De forma opcional, introduzca una descripción.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Al crear el conjunto de medios mixtos, puede cambiar la miniatura del conjunto de medios mixtos o permitir que AEM seleccione la miniatura automáticamente en función de los recursos del conjunto de medios mixtos. Para seleccionar una miniatura, haga clic en **[!UICONTROL Cambiar miniatura]** y seleccione cualquier imagen (también puede desplazarse a otras carpetas para buscar imágenes). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Toque el Selector **[!UICONTROL de]** recursos para seleccionar los recursos que desee incluir en el conjunto de medios mixtos. Selecciónelos y toque **[!UICONTROL Seleccionar]**.

   With the **[!UICONTROL Asset Selector]**, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. También puede aplicar filtros para restringir los resultados de búsqueda. Puede filtrar por ruta, colección, tipo de archivo y etiqueta. Seleccione el filtro y, a continuación, pulse el icono **[!UICONTROL Filtro]** en la barra de herramientas. Change the view by selecting the View icon and selecting **[!UICONTROL List]**, **[!UICONTROL Column]**, or **[!UICONTROL Card]** view.

   See [Working with Selectors](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Vuelva a ordenar los recursos arrastrándolos hacia arriba o hacia abajo en la lista (debe seleccionar el icono de reordenación), según sea necesario.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   If you want to add thumbnails, click the **[!UICONTROL +]** icon next to the image and navigate to the thumbnail you want. Cuando haya terminado de seleccionar todas las imágenes en miniatura, toque **[!UICONTROL Guardar]**.

   >[!NOTE]
   >
   >Si desea agregar recursos, toque **[!UICONTROL Añadir recurso]**.

1. Para eliminar un recurso, seleccione la casilla de verificación correspondiente y toque **[!UICONTROL Eliminar recurso]**.
1. Para aplicar un ajuste preestablecido, toque **[!UICONTROL Ajuste preestablecido]** en la esquina superior derecha y seleccione un ajuste preestablecido para aplicarlo a los recursos.
1. Haga clic en **[!UICONTROL Guardar.]** El conjunto de medios mixtos recién creado aparece en la carpeta en la que lo creó.

## Edición de conjuntos de medios mixtos {#editing-mixed-media-sets}

Puede realizar varias tareas de edición de recursos en conjuntos de medios mixtos directamente en la interfaz de usuario, [como lo haría con cualquier recurso de Recursos](managing-assets-touch-ui.md). También puede realizar las siguientes acciones en los conjuntos de medios mixtos:

* Añada recursos al conjunto de medios mixtos.
* Vuelva a ordenar los recursos en el conjunto de medios mixtos.
* Elimine recursos del conjunto de medios mixtos.
* Aplicación de ajustes preestablecidos de visor.
* Cambie la miniatura predeterminada.

**Para editar conjuntos** de medios mixtos:

1. Realice una de las siguientes acciones:

   * Pase el ratón sobre un recurso de conjunto de medios mixtos y, a continuación, toque **[!UICONTROL Editar]** (icono de lápiz).
   * Pase el ratón sobre un recurso de conjunto de medios mixtos, toque **[!UICONTROL Seleccionar]** (icono de marca de verificación) y, a continuación, toque **[!UICONTROL Editar]** en la barra de herramientas.
   * Toque en un recurso de conjunto de medios mixtos y, a continuación, toque **[!UICONTROL Editar]** (icono de lápiz) en la barra de herramientas.

1. En el Editor de conjuntos de medios mixtos, realice una de las siguientes acciones:

   * Para reordenar recursos: en el panel izquierdo, toque **[!UICONTROL Recursos]** (icono de imagen) y arrastre un recurso a una nueva ubicación.
   * Para agregar recursos: en la barra de herramientas, toque **[!UICONTROL Añadir recurso]**. Vaya a los recursos. Para cada recurso que desee agregar, pase el ratón sobre la imagen del recurso (no el nombre del recurso) y toque el icono de marca de verificación. En la esquina superior derecha, toque **[!UICONTROL Seleccionar]**.
   * Para eliminar un recurso: en el panel izquierdo, toque **[!UICONTROL Recursos]** (icono de imagen) y, a continuación, seleccione el recurso. En la barra de herramientas, toque **[!UICONTROL Eliminar recurso]**.
   * Para ordenar los recursos por su nombre en orden ascendente o descendente, en el panel izquierdo, toque **[!UICONTROL Recursos]** (icono de imagen). A la derecha del encabezado de **[!UICONTROL Recursos]** , toque los iconos de los caracteres de intercalación hacia arriba o hacia abajo.

   >[!NOTE]
   >
   >* To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view) navigate to the Mixed Media Set. Pase el ratón sobre el recurso y pulse el icono de marca de verificación para seleccionarlo. Press **[!UICONTROL Backspace]** on the keyboard, or tap **[!UICONTROL More]** (three dots) on the toolbar, then tap **[!UICONTROL Delete]**.
   >* You can edit the assets in a Mixed Media Set by navigating to the set, tapping **[!UICONTROL Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Toque **[!UICONTROL Guardar** cuando haya terminado de editar.

   >[!NOTE]
   >
   >* Para editar los recursos de un conjunto de medios mixtos, vaya al conjunto de medios mixtos. Tap (do not select) the set to open it in the AEM **[!UICONTROL Set Preview]** page. In the left rail, tap the down caret to open the drop-down list, then tap **[!UICONTROL Set Members]**. In the **[!UICONTROL Set Members]** page, hover on an asset, then tap **[!UICONTROL Edit]** (pencil icon) to open the editing page.
   >* To delete an entire Mixed Media Set - From any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view), navigate to the Mixed Media Set. Hover on the set, then tap **[!UICONTROL Select]** (checkmark icon). Press **[!UICONTROL Backspace]** on your keyboard, or tap **[!UICONTROL More]** (row of three dots), then tap **[!UICONTROL Delete]**.


## Vista previa de conjuntos de medios mixtos {#previewing-mixed-media-sets}

Consulte [Vista previa de recursos](previewing-assets.md) para obtener más información sobre cómo previsualización de conjuntos de medios mixtos.

## Publicación de conjuntos de medios mixtos {#publishing-mixed-media-sets}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md) para obtener más información sobre cómo publicar conjuntos de medios mixtos.

>[!NOTE]
>
>Si la Det de medios mixtos no termina por completo en el servicio de envío la primera vez que lo publica, es posible que tenga que publicar el conjunto de medios mixtos por segunda vez.

