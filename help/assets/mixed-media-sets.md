---
title: Conjuntos de medios mixtos
description: Aprenda a trabajar con conjuntos de medios mixtos (imágenes, conjuntos de imágenes, conjuntos de giros y vídeos) en Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 252c1a50-17ac-4412-88d6-49bb6850658d
feature: Combinar conjuntos de medios
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 18%

---

# Conjuntos de medios mixtos {#mixed-media-sets}

Los conjuntos de medios mixtos permiten proporcionar una combinación de imágenes, conjuntos de imágenes, conjuntos de giros y vídeos en una presentación.

Los conjuntos de medios mixtos se designan mediante un banner con la palabra **[!UICONTROL MixedMediaSet]**. Además, si se publica el conjunto de medios mixtos, se muestra la fecha de publicación, indicada por el icono **[!UICONTROL Mundo]**, junto a la fecha de la última modificación, indicada por el icono **[!UICONTROL Lápiz]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Para obtener información sobre la interfaz de usuario de Assets, consulte [Administración de recursos con la IU táctil](managing-assets-touch-ui.md).

## Inicio rápido: Conjuntos de medios mixtos {#quick-start-mixed-media-sets}

Para poner en marcha rápidamente los conjuntos de medios mixtos, siga estos pasos:

1. [Cargue los recursos](#uploading-assets).

   Comience por cargar las imágenes y los vídeos de los conjuntos de medios mixtos. Si es necesario, cree los [conjuntos de imágenes](image-sets.md) y los [conjuntos de giros](spin-sets.md). Dado que los usuarios pueden aplicar zoom a las imágenes en el visualizador de conjuntos de medios mixtos, tenga en cuenta el zoom al elegir las imágenes. Compruebe que las imágenes tengan al menos 2000 píxeles en la dimensión más grande.

1. [Crear conjuntos de medios mixtos.](#creating-mixed-media-sets)

   Para crear un conjunto de medios mixtos, en la página **[!UICONTROL Assets]**, pulse **[!UICONTROL Crear > Conjunto de medios mixtos]** y asigne un nombre al conjunto. Elija los recursos y, a continuación, elija el orden en que aparecen las imágenes.

   Consulte [Uso de selectores.](working-with-selectors.md)

1. Configure los [ajustes preestablecidos del visualizador de medios mixtos](managing-viewer-presets.md) según sea necesario.

   Los administradores pueden crear o modificar ajustes preestablecidos del visualizador de conjuntos de medios mixtos. Para ver los medios mixtos con un ajuste preestablecido del visualizador, seleccione el conjunto de medios mixtos y, en el menú desplegable del carril izquierdo, seleccione **[!UICONTROL Visualizadores]**.

   Consulte **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]** para crear o editar ajustes preestablecidos de visor.

   Consulte [Adición y edición de ajustes preestablecidos de visualizador.](managing-viewer-presets.md)

1. [Vista previa de conjuntos de medios mixtos.](#previewing-mixed-media-sets)

   Seleccione el conjunto de medios mixtos y podrá previsualizarlo. Haga clic en los iconos de miniaturas para examinar el conjunto de medios mixtos en el visualizador seleccionado. Puede elegir diferentes visores desde el menú **[!UICONTROL Visualizadores]**, disponible en el menú desplegable del carril izquierdo.

1. [Publicar Conjuntos De Medios Mixtos.](#publishing-mixed-media-sets)

   Al publicar un conjunto de medios mixtos, se activa la dirección URL y la cadena de incrustación. Además, debe [publicar el ajuste preestablecido de visor](managing-viewer-presets.md#publishing-viewer-presets).

1. [Vincule las URL a su ](linking-urls-to-yourwebapplication.md) aplicación web o  [incruste el visualizador de imágenes o vídeos](embed-code.md).

   AEM Assets crea llamadas de URL para conjuntos de medios mixtos y los activa después de publicar los conjuntos de medios mixtos. Puede copiar estas direcciones URL cuando obtiene una vista previa de los recursos. También puede incrustarlos en el sitio web.

   Seleccione el conjunto de medios mixtos y, a continuación, en el menú desplegable del carril izquierdo, seleccione **[!UICONTROL Visualizadores]**.

   Consulte [Vinculación de un conjunto de medios mixtos a una página web](linking-urls-to-yourwebapplication.md) e [Incrustación del visualizador de imágenes o vídeos](embed-code.md).

Si lo necesita, puede editar [Conjuntos de medios mixtos](#editing-mixed-media-sets). Además, puede ver y modificar [Propiedades de conjuntos de medios mixtos](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>Si tiene problemas al crear conjuntos, consulte [Solución de problemas de Dynamic Media - modo Scene7](troubleshoot-dms7.md).

## Carga de recursos {#uploading-assets}

Comience por cargar las imágenes y los vídeos de los conjuntos de medios mixtos. Dado que los usuarios pueden hacer zoom en las imágenes en el visualizador de conjuntos de medios mixtos, asegúrese de tener en cuenta el zoom al elegir las imágenes. Compruebe que las imágenes tengan al menos 2000 píxeles en la dimensión más grande.

Además, si desea agregar conjuntos de giros o conjuntos de imágenes al conjunto de medios mixtos, créelos también.

## Creación de conjuntos de medios mixtos {#creating-mixed-media-sets}

Puede agregar imágenes, conjuntos de imágenes, conjuntos de giros y vídeos al conjunto de medios mixtos. Asegúrese de que los archivos, conjuntos de imágenes y conjuntos de giros estén listos para publicarse antes de agregarlos al conjunto de medios mixtos.

Cuando se añaden recursos al conjunto, estos se añaden automáticamente en orden alfanumérico. Puede volver a ordenar u ordenar manualmente los recursos una vez añadidos.

**Para crear un conjunto de medios mixtos**:

1. En Assets, desplácese hasta donde desee crear un conjunto de medios mixtos, haga clic en **Crear** y seleccione **[!UICONTROL Conjunto de medios mixtos]**. También puede crear el conjunto desde una carpeta que contenga los recursos.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. En la página **[!UICONTROL Editor de conjuntos de medios mixtos]**, en **[!UICONTROL Título]**, introduzca un nombre para el conjunto de medios mixtos. El nombre aparece en el banner del conjunto de medios mixtos. De forma opcional, introduzca una descripción.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Al crear el conjunto de medios mixtos, puede cambiar la miniatura del conjunto de medios mixtos o permitir que AEM seleccione la miniatura automáticamente en función de los recursos del conjunto de medios mixtos. Para seleccionar una miniatura, haga clic en **[!UICONTROL Cambiar miniatura]** y seleccione cualquier imagen (puede navegar también a otras carpetas para buscar imágenes). Si ha seleccionado una miniatura y, a continuación, decide que AEM generar una del conjunto de medios mixtos, seleccione **[!UICONTROL Cambiar a miniatura automática]**.

1. Pulse **[!UICONTROL Selector de recursos]** para seleccionar los recursos que desea incluir en su conjunto de medios mixtos. Selecciónelos y pulse **[!UICONTROL Seleccionar]**.

   Con el **[!UICONTROL Selector de recursos]**, puede buscar recursos escribiendo una palabra clave y pulsando **[!UICONTROL Retorno]**. También puede aplicar filtros para restringir los resultados de búsqueda. Puede filtrar por ruta, colección, tipo de archivo y etiqueta. Seleccione el filtro y, a continuación, pulse el icono **[!UICONTROL Filtro]** en la barra de herramientas. Para cambiar la vista, seleccione el icono Ver y seleccione la vista **[!UICONTROL Lista]**, **[!UICONTROL Columna]** o **[!UICONTROL Tarjeta]**.

   Consulte [Uso de selectores](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Vuelva a ordenar los recursos arrastrándolos hacia arriba o hacia abajo en la lista (debe seleccionar el icono de reordenar), según sea necesario.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   Si desea agregar miniaturas, haga clic en el icono **[!UICONTROL +]** situado junto a la imagen y vaya a la miniatura que desee. Cuando haya terminado de seleccionar todas las imágenes en miniatura, pulse **[!UICONTROL Guardar]**.

   >[!NOTE]
   >
   >Si desea agregar recursos, pulse **[!UICONTROL Agregar recurso]**.

1. Para eliminar un recurso, seleccione la casilla de verificación correspondiente y pulse **[!UICONTROL Eliminar recurso]**.
1. Para aplicar un ajuste preestablecido, pulse **[!UICONTROL Ajuste preestablecido]** en la esquina superior derecha y seleccione un ajuste preestablecido para aplicar a los recursos.
1. Haga clic en **[!UICONTROL Guardar]**. El conjunto de medios mixtos recién creado aparece en la carpeta en la que lo creó.

## Edición de conjuntos de medios mixtos {#editing-mixed-media-sets}

Puede realizar diversas tareas de edición en los recursos de los conjuntos de medios mixtos directamente en la interfaz de usuario [como lo haría con cualquier recurso de Assets](managing-assets-touch-ui.md). También puede realizar las siguientes acciones en conjuntos de medios mixtos:

* Agregue recursos al conjunto de medios mixtos.
* Vuelva a ordenar los recursos en el conjunto de medios mixtos.
* Eliminar recursos del conjunto de medios mixtos.
* Aplicar ajustes preestablecidos de visor.
* Cambie la miniatura predeterminada.

**Para editar conjuntos** de medios mixtos:

1. Realice una de las siguientes acciones:

   * Pase el ratón sobre un recurso de conjunto de medios mixtos y, a continuación, pulse **[!UICONTROL Editar]** (icono de lápiz).
   * Pase el ratón sobre un recurso de conjunto de medios mixtos, pulse **[!UICONTROL Seleccionar]** (icono de marca de verificación) y, a continuación, pulse **[!UICONTROL Editar]** en la barra de herramientas.
   * Pulse en un recurso de conjunto de medios mixtos y, a continuación, pulse **[!UICONTROL Editar]** (icono de lápiz) en la barra de herramientas.

1. En el Editor de conjuntos de medios mixtos, realice una de las acciones siguientes:

   * Para reordenar los recursos: en el panel izquierdo, pulse **[!UICONTROL Assets]** (icono de imagen) y arrastre un recurso a una nueva ubicación.
   * Para agregar recursos: en la barra de herramientas, pulse **[!UICONTROL Agregar recurso]**. Vaya a los recursos. Para cada recurso que desee agregar, pase el ratón sobre la imagen del recurso (no el nombre del recurso) y, a continuación, pulse el icono de marca de verificación. En la esquina superior derecha, pulse **[!UICONTROL Seleccionar]**.
   * Para eliminar un recurso: en el panel izquierdo, pulse **[!UICONTROL Assets]** (icono de imagen) y, a continuación, seleccione el recurso. En la barra de herramientas, pulse **[!UICONTROL Eliminar recurso]**.
   * Para ordenar los recursos por su nombre en orden ascendente o descendente, en el panel izquierdo, pulse **[!UICONTROL Assets]** (icono de imagen). A la derecha del encabezado **[!UICONTROL Assets]**, pulse los iconos del acento circunflejo arriba o abajo.

   >[!NOTE]
   >
   >* Para eliminar un conjunto de medios mixtos completo, en cualquier modo de visualización (como la vista **[!UICONTROL Tarjeta]** o la vista **[!UICONTROL Columna]**) vaya al conjunto de medios mixtos. Pase el ratón sobre el recurso y pulse el icono de marca de verificación para seleccionarlo. Pulse **[!UICONTROL Retroceso]** en el teclado o pulse **[!UICONTROL Más]** (tres puntos) en la barra de herramientas y, a continuación, pulse **[!UICONTROL Eliminar]**.
   >* Para editar los recursos de un conjunto de medios mixtos, vaya al conjunto, pulse **[!UICONTROL Definir miembros]** en el carril izquierdo y, a continuación, pulse el icono **[!UICONTROL Lápiz]** de un recurso individual para abrir la ventana de edición.


1. Toque **[!UICONTROL Guardar]** cuando haya terminado de editar.

   >[!NOTE]
   >
   >* Para editar los recursos de un conjunto de medios mixtos, vaya al conjunto de medios mixtos. Toque (no seleccione) el conjunto para abrirlo en la página AEM **[!UICONTROL Establecer vista previa]**. En el carril izquierdo, pulse el circunflejo invertido para abrir la lista desplegable y, a continuación, pulse **[!UICONTROL Definir miembros]**. En la página **[!UICONTROL Definir miembros]**, coloque el puntero sobre un recurso y pulse **[!UICONTROL Editar]** (icono de lápiz) para abrir la página de edición.
   >* Para eliminar un conjunto de medios mixtos completo, en cualquier modo de visualización (como la vista **[!UICONTROL Tarjeta]** o la vista **[!UICONTROL Columna]**), vaya al conjunto de medios mixtos. Pase el ratón sobre el conjunto y, a continuación, pulse **[!UICONTROL Seleccionar]** (icono de marca de verificación). Pulse **[!UICONTROL Retroceso]** en el teclado o pulse **[!UICONTROL Más]** (fila de tres puntos) y, a continuación, pulse **[!UICONTROL Eliminar]**.


## Vista previa de conjuntos de medios mixtos {#previewing-mixed-media-sets}

Consulte [Vista previa de recursos](previewing-assets.md) para obtener más información sobre cómo previsualizar conjuntos de medios mixtos.

## Publicación de conjuntos de medios mixtos {#publishing-mixed-media-sets}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md) para obtener más información sobre cómo publicar conjuntos de medios mixtos.

>[!NOTE]
>
>Si la fecha de medios mixtos no termina completamente en el servicio de envío la primera vez que lo publica, es posible que tenga que publicar el conjunto de medios mixtos por segunda vez.
