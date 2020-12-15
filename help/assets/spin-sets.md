---
title: Conjuntos de giros
seo-title: Conjuntos de giros
description: Aprenda a trabajar con conjuntos de giros en medios dinámicos
seo-description: Aprenda a trabajar con conjuntos de giros en medios dinámicos
uuid: a80a0491-6500-463a-83c4-ff4b90a88182
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: afacb3ad-e4ad-4d06-a898-f3f2da8bbb64
translation-type: tm+mt
source-git-commit: f86765084981cda1e255834bf83be0ff8a7a2a02
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 6%

---


# Conjuntos de giros {#spin-sets}

Un conjunto de giros simula el acto real de girar un objeto para examinarlo. Los conjuntos de giros permiten la vista de elementos desde cualquier ángulo, obteniendo los detalles visuales clave desde cualquier ángulo.

Un conjunto de giros simula una experiencia de visualización de 360 grados. Dynamic Media oferta conjuntos de giros de un solo eje en los que los visores pueden rotar un elemento. Además, los usuarios pueden aplicar zoom &quot;de forma libre&quot; y desplazarse por cualquiera de las vistas con unos pocos clics simples del ratón. De este modo, los usuarios pueden examinar un elemento más de cerca desde un punto de vista concreto.

Los conjuntos de giros se designan mediante una pancarta con la palabra **[!UICONTROL SPINSET]**. Además, si se publica el conjunto de giros, se muestra la fecha de publicación, indicada por el icono **[!UICONTROL Mundo]**, junto con la fecha de la última modificación, indicada por el icono **[!UICONTROL Lápiz]**.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Para obtener información sobre la interfaz de usuario de Assets, consulte [Administración de recursos con la IU táctil](managing-assets-touch-ui.md).

## Inicio rápido: Conjuntos de giros {#quick-start-spin-sets}

Para ayudarle en el uso inicial de los conjuntos de giros, siga este flujo de trabajo:

1. [Cargue las imágenes para varias vistas.](#uploading-assets-for-spin-sets)

   Como mínimo, necesitará entre 8 y 12 tomas de un elemento para un conjunto de giros unidimensional y entre 16 y 24 para un conjunto de giros bidimensional. Las tomas deben realizarse a intervalos regulares para dar la impresión de que el elemento está rotando y volteando. Por ejemplo, si un conjunto de giros unidimensional incluye 12 tomas, gire el elemento 30 grados (360/12) para cada toma.

1. [Crear conjuntos de giros.](#creating-spin-sets)

   Para crear un conjunto de giros, seleccione **[!UICONTROL Crear > Conjunto de giros]** y, a continuación, asigne un nombre al conjunto, elija los recursos y, a continuación, ordene las imágenes en el orden en que aparecerán.

   Consulte [Uso de selectores](working-with-selectors.md).

   >[!NOTE]
   >
   >También puede crear conjuntos de giros automáticamente mediante [ajustes preestablecidos de conjunto de lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*Los conjuntos de lotes son creados por IPS (Image Production System) como parte de la ingesta de recursos y solo están disponibles en el modo* Dynamic Media - Scene7.

1. Configure [ajustes preestablecidos del visor de conjuntos de giros](managing-viewer-presets.md) según sea necesario.

   Los administradores pueden crear o modificar ajustes preestablecidos del visor de conjuntos de giros. Para ver el conjunto de giros con un ajuste preestablecido de visor, seleccione el conjunto de giros y, en el menú desplegable del carril izquierdo, seleccione **[!UICONTROL Visores]**.

   Consulte **[!UICONTROL Herramientas > Recursos > Ajustes preestablecidos de visor]** para crear o editar ajustes preestablecidos de visor.

   Consulte [Añadir y editar ajustes preestablecidos de visor.](managing-viewer-presets.md)

1. [Visualización de conjuntos](#viewing-spin-sets) de giros.

   Puede vista y acceder a los conjuntos creados mediante ajustes preestablecidos de conjunto de lotes de tres formas diferentes. (Los conjuntos creados con ajustes preestablecidos de conjunto de lotes, no *a1/> aparecen en la interfaz de usuario).*

1. [Conjuntos de giros de previsualización.](previewing-assets.md)

   Seleccione el conjunto de giros y puede previsualización. Girar el conjunto de giros. Puede elegir diferentes visores en el menú **[!UICONTROL Visores]**, disponible en el menú desplegable del carril izquierdo.

1. [Publicar conjuntos de giros.](publishing-dynamicmedia-assets.md)

   Al publicar un conjunto de giros, se activa el orden en que aparecen las imágenes en un conjunto de giros. Asegúrese de ordenarlos para que el giro sea una vista suave de 360 grados.**** URL y  **** cadena de incrustación. Además, debe [publicar el ajuste preestablecido de visor](managing-viewer-presets.md).

1. [Vincule las direcciones URL a la ](linking-urls-to-yourwebapplication.md) aplicación web o  [incruste el visor](embed-code.md) de vídeo o de imágenes.

   AEM Assets crea llamadas mediante URL para conjuntos de giros y los activa después de publicar los conjuntos de giros. Puede copiar estas direcciones URL cuando previsualización recursos. Como alternativa, puede incrustarlos en su sitio Web.

   Seleccione el conjunto de giros y, a continuación, en el menú desplegable del carril izquierdo, seleccione **[!UICONTROL Visualizadores]**.

   Consulte [Vinculación de un conjunto de giros a una página web](linking-urls-to-yourwebapplication.md) e [Incrustación del visualizador de imágenes o vídeos](embed-code.md).

Si lo necesita, puede [editar conjuntos de giros](#editing-spin-sets). Además, puede vista y editar [propiedades del conjunto de giros](managing-assets-touch-ui.md#editing-properties).

## Carga de recursos para conjuntos de giros {#uploading-assets-for-spin-sets}

Como mínimo, necesitará entre 8 y 12 tomas de un elemento para un conjunto de giros unidimensional y entre 16 y 24 para un conjunto de giros bidimensional. Las tomas deben realizarse a intervalos regulares para dar la impresión de que el elemento está rotando y volteando. Por ejemplo, si un conjunto de giros unidimensional incluye 12 tomas, gire el elemento 30 grados (360/12) para cada toma.

Puede cargar imágenes para los conjuntos de giros del mismo modo que [carga cualquier otro recurso en AEM Assets](managing-assets-touch-ui.md).

### Pautas para grabar imágenes de conjuntos de giros {#guidelines-for-shooting-spin-set-images}

A continuación se indican algunas prácticas recomendadas en relación con las imágenes de conjuntos de giros. En general, cuantas más imágenes haya en un conjunto de giros, mejor será el efecto de giro de la imagen. Sin embargo, incluir muchas imágenes en el conjunto también aumenta el tiempo que tardan las imágenes en cargarse. AEM recomienda estas directrices para la toma de imágenes para su uso en conjuntos de giros:

* Como mínimo, utilice entre 8 y 12 imágenes en un conjunto de giros unidimensional y entre 16 y 24 imágenes en un conjunto de giros bidimensional. Se necesita un mínimo de 8 imágenes para poder girar 360 grados. Los conjuntos de giros unidimensionales son más comunes ya que la creación de conjuntos de giros bidimensionales requiere mucho trabajo.
* Utilizar un formato sin pérdida; Se recomiendan TIFF y PNG.
* Enmascara todas las imágenes para que el elemento aparezca sobre un fondo blanco puro u otro de alto contraste. De forma opcional, agregue sombras.
* Asegúrese de que los detalles del producto están bien iluminados y enfocados.
* Tome imágenes de giro para ropa de moda con un maniquí o modelo. A menudo, el maniquí está completamente enmascarado (con un maniquí de vidrio) o se muestra en la imagen un maniquí o una forma de vestir estilizada. Puede crear un conjunto de giros en modelo definiendo el número de ángulos. Marque cada ángulo con cinta en el suelo para guiar al modelo hacia el paso y mirar en la dirección de cada toma.

## Creación de conjuntos de giros {#creating-spin-sets}

El orden en que aparecen las imágenes en un conjunto de giros es importante. Asegúrese de ordenarlos para que el giro sea una vista suave de 360 grados.

>[!NOTE]
>
>También puede crear conjuntos de giros automáticamente mediante los [ajustes preestablecidos de conjuntos de lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>
>Los conjuntos de lotes son creados por IPS (Image Production System) como parte de la ingesta de recursos y solo están disponibles en el modo Dynamic Media - Scene7.
>
>Consulte &quot;Creación de ajustes preestablecidos de conjunto de lotes para generar automáticamente conjuntos de imágenes y conjuntos de giros&quot; en [Configuración de Dynamic Media - modo Scene7](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**Para crear conjuntos de giros:**

1. En Recursos, desplácese hasta donde desee crear un conjunto de giros, toque **[!UICONTROL Crear]** y seleccione **[!UICONTROL Conjunto de giros]**. También puede crear el conjunto desde una carpeta que contenga los recursos.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. En la página **[!UICONTROL Editor de conjuntos de giros]**, en el campo **[!UICONTROL Título]**, introduzca un nombre para el conjunto de giros. El nombre aparece en la pancarta del conjunto de giros. De forma opcional, introduzca una descripción.

   ![chlimage_1-382](assets/chlimage_1-382.png)

   Al crear el conjunto de giros, puede cambiar la miniatura del conjunto de giros o permitir que AEM seleccione la miniatura automáticamente en función de los recursos del conjunto de giros. Para seleccionar una miniatura, toque **[!UICONTROL Cambiar miniatura]**. Seleccione cualquier imagen (puede desplazarse a otras carpetas para buscar imágenes también). Si ha seleccionado una miniatura y luego decide que AEM generar una del conjunto de giros, seleccione **[!UICONTROL Cambiar a miniatura automática]**.

1. Realice una de las siguientes acciones:

   * Cerca de la esquina superior izquierda de la página **[!UICONTROL Editor de conjuntos de giros]**, toque **[!UICONTROL Añadir recurso]**.
   * Cerca del centro de la página **[!UICONTROL Editor de conjuntos de giros]**, toque **[!UICONTROL Tocar para abrir el Selector de recursos]**.

   Toque para seleccionar los recursos que desea incluir en el conjunto de giros. Los recursos seleccionados tienen un icono de marca de verificación sobre ellos. Cuando haya terminado, toque **[!UICONTROL Seleccionar]** cerca de la esquina superior derecha de la página.

   Con el Selector de recursos, puede buscar recursos escribiendo una palabra clave y pulsando **[!UICONTROL Retorno]**. También puede aplicar filtros para restringir los resultados de búsqueda. Puede filtrar por ruta, colección, tipo de archivo y etiqueta. Seleccione el filtro y, a continuación, pulse el icono **[!UICONTROL Filtro]** en la barra de herramientas. Para cambiar la vista, cerca de la esquina superior derecha de la página, toque el icono **[!UICONTROL Vista]** y luego toque **[!UICONTROL Vista de columna]**, **[!UICONTROL Vista de tarjeta]** o **[!UICONTROL Vista de Lista]**.

   Consulte [Uso de selectores](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Cuando se agregan recursos al conjunto, se añaden automáticamente en orden alfanumérico. Después de agregarlos, puede reordenar o ordenar manualmente los recursos. Si es necesario, arrastre el icono **[!UICONTROL Reordenar]** de un recurso a la derecha del nombre del archivo del recurso para reordenar las imágenes hacia arriba o hacia abajo en la lista establecida.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Opcional) Realice cualquiera de las siguientes acciones:

   * Para eliminar una imagen, selecciónela y toque **[!UICONTROL Eliminar recurso]**.
   * Para aplicar un ajuste preestablecido, cerca de la esquina superior derecha de la página, toque **[!UICONTROL Ajuste preestablecido]** y, a continuación, seleccione un ajuste preestablecido para aplicar a todos los recursos a la vez.

1. Toque **[!UICONTROL Guardar]**. El conjunto de giros recién creado aparece en la carpeta en la que lo creó.

## Visualización de conjuntos de giros {#viewing-spin-sets}

Puede crear conjuntos de giros en la interfaz de usuario o automáticamente mediante [ajustes preestablecidos de conjunto de lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). Sin embargo, los conjuntos creados con ajustes preestablecidos de conjunto de lotes, no *a1/> aparecen en la interfaz de usuario.* Puede acceder a los conjuntos creados mediante ajustes preestablecidos de conjuntos de lotes de tres formas diferentes. (Estos métodos están disponibles aunque haya creado los conjuntos de giros en la interfaz de usuario).

También puede realizar vistas de conjuntos mediante la interfaz de usuario como se describe en [Edición de conjuntos de giros](#editing-spin-sets).

**Para vista de conjuntos de giros:**

1. Al abrir las propiedades de un recurso individual. Las propiedades indican los conjuntos de los que el recurso seleccionado es miembro (en **[!UICONTROL Miembro de conjuntos]**). Toque el nombre del conjunto para ver el conjunto completo.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. Desde una imagen de miembro de cualquier conjunto. Seleccione el menú **[!UICONTROL Conjuntos]** para mostrar los conjuntos de los que es miembro el recurso.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. Desde la búsqueda, puede seleccionar **[!UICONTROL Filtros]**, luego expandir **[!UICONTROL Dynamic Media]** y seleccionar **[!UICONTROL Conjuntos]**.

   La búsqueda devuelve conjuntos coincidentes creados manualmente en la interfaz de usuario o creados automáticamente mediante ajustes preestablecidos de conjunto de lotes. Para los conjuntos automatizados, la consulta de búsqueda se lleva a cabo utilizando **[!UICONTROL Inicios con]** criterios de búsqueda que difieren de AEM búsqueda basada en el uso de **[!UICONTROL Contiene]** criterios de búsqueda. La configuración del filtro en **[!UICONTROL Sets]** es la única manera de buscar conjuntos automatizados.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Edición de conjuntos de giros {#editing-spin-sets}

Puede realizar varias tareas de edición en los conjuntos de giros, como las siguientes:

* Añada imágenes al conjunto de giros.
* Vuelva a ordenar las imágenes en el conjunto de giros.
* Eliminar recursos del conjunto de giros.
* Aplicación de ajustes preestablecidos de visor.
* Elimine el conjunto de giros.

**Para editar un conjunto de giros:**

1. Realice una de las siguientes acciones:

   * Pase el ratón sobre un recurso de conjunto de giros y, a continuación, toque **[!UICONTROL Editar]** (icono de lápiz).
   * Pase el ratón sobre un recurso de conjunto de giros, toque **[!UICONTROL Seleccionar]** (icono de marca de verificación) y, a continuación, toque **[!UICONTROL Editar]** en la barra de herramientas.
   * Toque en un recurso de conjunto de giros y, a continuación, toque **[!UICONTROL Editar]** (icono de lápiz) en la barra de herramientas.

1. Para editar el conjunto de giros, realice una de las siguientes acciones:

   * Para reordenar imágenes, arrastre una imagen a una nueva ubicación (seleccione el icono de reordenar para mover elementos).
   * Para ordenar los elementos en orden ascendente o descendente, toque el encabezado de la columna.
   * Para agregar un recurso o actualizar uno existente, toque **[!UICONTROL Añadir recurso]**. Vaya a un recurso, selecciónelo y toque **[!UICONTROL Seleccionar]** cerca de la esquina superior derecha.
Si elimina la imagen que AEM utiliza para la miniatura reemplazándola por otra imagen, el recurso original seguirá mostrándose.
   * Para eliminar un recurso, selecciónelo y toque **[!UICONTROL Eliminar recurso]**.
   * Para aplicar un ajuste preestablecido, toque el icono **[!UICONTROL Ajuste preestablecido]** y seleccione un ajuste preestablecido.
   * Para eliminar un conjunto de giros completo, vaya al conjunto de giros, selecciónelo y seleccione **[!UICONTROL Eliminar]**

      >[!NOTE]
      >* Puede editar las imágenes de un conjunto de giros navegando hasta el conjunto, tocando **[!UICONTROL Establecer miembros]** en el carril izquierdo y, a continuación, tocando el **[!UICONTROL Editar]** (icono de lápiz) en un recurso individual para abrir la ventana de edición.


1. Haga clic en **[!UICONTROL Guardar]** cuando termine de editar.

## Vista previa de conjuntos de giros {#previewing-spin-sets}

Consulte [Vista previa de recursos](previewing-assets.md).

## Publicación de conjuntos de giros {#publishing-spin-sets}

Consulte [Publishing Assets](publishing-dynamicmedia-assets.md).
