---
title: Administración de ajustes preestablecidos de visor de Dynamic Media
seo-title: Managing Dynamic Media viewer presets
description: Creación y administración de ajustes preestablecidos de visor de Dynamic Media
seo-description: How to create and manage Dynamic Media viewer presets
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Viewer Presets
role: Admin,User
source-git-commit: 877eade71c2ec57ff534ba2649275111c5326d75
workflow-type: tm+mt
source-wordcount: '4220'
ht-degree: 11%

---

# Administración de ajustes preestablecidos de visor de Dynamic Media {#managing-viewer-presets}

Un ajuste preestablecido de visualizador de Dynamic Media es una colección de ajustes que determinan cómo ven los usuarios los recursos de medios enriquecidos en sus pantallas de equipos y dispositivos móviles. Si es un administrador, puede crear ajustes preestablecidos de visor. La configuración está disponible para una matriz de opciones de configuración del visor. Por ejemplo, puede cambiar el tamaño de visualización del visor o el comportamiento de zoom.

Para obtener instrucciones sobre la creación y personalización de sus propios ajustes preestablecidos de visor de HTML5, consulte la documentación de la API del SDK de visor de Dynamic Media *HTML5* de Adobe. El SDK está disponible en el servidor de publicación IS incrustado en el propio SDK. Cada versión de la biblioteca tiene su propia documentación de SDK incluida.

Ruta: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
Por ejemplo, SDK 3.10: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

Consulte también la [Guía de referencia de visores de Dynamic Media de Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

En esta sección se describe cómo crear, editar y administrar ajustes preestablecidos de visualizador. Puede aplicar un ajuste preestablecido de visualizador a un recurso cada vez que lo previsualice. Consulte [Aplicación de ajustes preestablecidos de visor](viewer-presets.md).

>[!NOTE]
>
>Tenga en cuenta que no se admite la edición de *ajustes preestablecidos de visor predefinidos y listos para usar*. Si intenta editar un ajuste preestablecido de visualizador listo para usar, se le pedirá que guarde el ajuste preestablecido de visualizador con un nuevo nombre.

## Accesibilidad de teclado para visualizadores {#keyboard-accessibility-for-viewers}

Todos los visores integrados admiten la accesibilidad del teclado.

Consulte también [Accesibilidad y navegación del teclado](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Administración de ajustes preestablecidos de visor de Dynamic Media {#managing-presets}

Puede agregar, editar, eliminar, publicar, cancelar la publicación y previsualizar ajustes preestablecidos de visualizador en AEM tocando **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visualizador]**.

![herramientas-recursos](assets/tools-assets.png)

>[!NOTE]
>
>De forma predeterminada, el sistema muestra 15 ajustes preestablecidos de visualizador al seleccionar Visualizadores en la vista de detalles de un recurso. Puede aumentar este límite. Consulte [Aumento del número de ajustes preestablecidos de visor que se muestran](#increasing-the-number-of-viewer-presets-that-display).

## Compatibilidad del visor con páginas web diseñadas para adaptarse {#viewer-support-for-responsive-designed-web-pages}

Las diferentes páginas Web tienen diferentes necesidades. Por ejemplo, a veces se desea una página web que proporcione un vínculo que abra el visor de HTML5 en una ventana independiente del explorador. En otros casos, puede ser necesario incrustar el visor de HTML5 directamente en la página de alojamiento. En este último caso, la página web puede tener un diseño estático. O puede ser *adaptable* y mostrarse de forma diferente en diferentes dispositivos o en diferentes tamaños de ventana del navegador. Para satisfacer estas necesidades, todos los visores predefinidos y listos para usar del HTML5 que se incluyen con Dynamic Media admiten tanto páginas web estáticas como páginas web diseñadas con capacidad de respuesta.

Consulte [Biblioteca de imágenes interactivas](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) en la *Ayuda de API de servicio de imágenes* para obtener más información sobre cómo incrustar visores interactivos en sus páginas web.

>[!NOTE]
>
>Tenga en cuenta que debe publicar todos los visores integrados antes de usarlos por primera vez.\
>Consulte [Ajustes preestablecidos del visualizador de publicaciones.](#publishing-viewer-presets)

## Compatibilidad del sistema con ajustes preestablecidos del visor  {#viewer-preset-system-compatibility}

Todos los ajustes preestablecidos de visor integrados que se incluyen con Dynamic Media son totalmente compatibles con los siguientes sistemas:

* Computadoras de escritorio
* Apple iPhone
* Apple iPad
* Smartphone de Android
* Android Tablet
* Para vídeo, se proporciona compatibilidad adicional con la reproducción de MP4 para [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) y [Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### Tipos de medios enriquecidos para ajustes preestablecidos de visor {#rich-media-types-for-viewer-presets}

Los administradores pueden agregar y personalizar los siguientes tipos de medios enriquecidos al crear nuevos ajustes preestablecidos de visor.

| Tipos de medios enriquecidos | Descripción |
|:---|:---|
| **Conjunto de carrusel** | Las zonas interactivas, los mapas de imágenes o ambas se añaden a una serie de dos o más imágenes. Un cliente puede obtener una panorámica de las imágenes a la izquierda o a la derecha y, a continuación, hacer clic en un punto interactivo de una imagen para obtener más detalles o para realizar compras directamente desde las páginas de categoría, de inicio o de aterrizaje de un sitio web. |
| **Zoom flotante** | Muestra una segunda imagen del área ampliada junto a la imagen original. No hay controles que utilizar: los usuarios mueven la selección sobre el área que desean ver. |
|  | Al determinar el uso completo del ancho de banda para este visor, tenga en cuenta que tanto la imagen principal como la imagen flotante se proporcionan en el visor. El tamaño de la imagen principal (ancho y alto del escenario) y el factor de zoom determinan el tamaño de la imagen flotante. Para evitar que el tamaño del archivo flotante sea demasiado grande, equilibre estos dos valores: si tiene un tamaño de imagen principal grande, reduzca el valor del factor de zoom. (La anchura flotante y la altura flotante determinan el tamaño de la ventana flotante, pero no el tamaño de la imagen flotante que se proporciona al visor). |
|  | Por ejemplo, si el tamaño de la imagen principal es de 350 por 350 píxeles, con un factor de zoom de 3, la imagen flotante resultante es de 1050 por 1050 píxeles. Si el tamaño de la imagen principal es de 300 por 300 píxeles, con un factor de zoom de 4, la imagen flotante es de 1200 por 1200 píxeles. Según la configuración de calidad del JPEG (la configuración recomendada está entre 80 y 90), puede reducir el tamaño del archivo de forma significativa. Los factores de zoom recomendados son de 2,5 a 4, dependiendo del tamaño de la imagen principal. |
| **Zoom en línea** | Muestra una imagen del área ampliada dentro del visor original. No hay controles que usar. Es decir, los usuarios mueven la selección sobre el área que desean ver. |
| **Conjunto de imágenes** | En el visor de conjuntos de imágenes, los usuarios pueden ver diferentes vistas o variaciones de color de un elemento haciendo clic en una imagen en miniatura. Este visor también ofrece herramientas de zoom para examinar las imágenes de cerca. |
| **Imagen interactiva** | Las zonas interactivas se añaden a partes de una imagen en las que un cliente puede hacer clic para obtener más información o para realizar compras directamente desde las páginas de aterrizaje, de inicio o de categoría de un sitio web. |
| **Vídeo interactivo** | Las miniaturas se añaden a los segmentos de cronología de un vídeo en los que un cliente puede hacer clic para obtener más información o para realizar compras directamente desde las páginas de aterrizaje, inicio o categoría de un sitio web. |
| **Medios mixtos** | Muestra diferentes tipos de medios en un visualizador. Puede incluir conjuntos de giros, conjuntos de imágenes, imágenes y vídeos. |
| **Imagen panorámica** | Los visores Panoramic Image y PanoramicVR representan imágenes panorámicas esféricas para sumergir a los usuarios en una experiencia de visualización de 360° de una habitación, propiedad, ubicación o paisaje. |
|  | Para que una imagen cargada se califique como un panorama esférico, debe tener una o ambas de las siguientes opciones: <ul><li>Una relación de aspecto de 2:1.</li><li>Etiquetado con las palabras clave equirectangulares, o esféricas y panorámicas, o esféricas y panorámicas. Consulte [Uso de etiquetas](../sites-authoring/tags.md).</li></ul> |
|  | Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente WCM &quot;Medios panorámicas&quot;. |
|  | Importante: Este visor solo está disponible en el modo Dynamic Media - Scene7 . |
| **Conjunto de giros** | Proporciona varias vistas de una imagen para que los usuarios puedan girar el objeto para examinar los diferentes lados y ángulos. |
| **Vídeo** | Reproduce el vídeo mediante flujo continuo de velocidad de bits progresiva o adaptable. La transmisión de velocidad de bits adaptable realiza automáticamente la detección de dispositivos y ancho de banda para ofrecer el vídeo de calidad adecuada en el formato correcto. |
| **Zoom vertical** | El visor de zoom vertical le permite maximizar una experiencia de visualización de imágenes de producto para ofrecer a los usuarios la mejor representación de un producto. La ubicación vertical de las muestras hace lo siguiente: <ul><li>Garantiza que las muestras estén por encima del pliegue. Con las muestras horizontales, según el tamaño de la pantalla del escritorio  usuario, las muestras no eran visibles hasta que el usuario se desplazaba hacia abajo por la página. Al colocar las muestras verticalmente en el visor, se garantiza que sean visibles independientemente del tamaño de pantalla del usuario.</li><li>Maximiza el tamaño de la imagen principal. Con las muestras horizontales, es necesario reservar espacio en la página para garantizar que sean visibles. Esta posición redujo el tamaño de la imagen principal. Sin embargo, con un diseño de muestra vertical, no es necesario asignar este espacio. Como tal, puede maximizar el tamaño de la imagen principal.</li></ul> |
| **Zoom** | Permite a los usuarios acercarse al área haciendo clic en ella. Los usuarios pueden hacer clic en los controles para acercar, alejar y restablecer la imagen a su tamaño predeterminado. |

## Lista de ajustes preestablecidos de visor integrados {#list-of-out-of-the-box-viewer-presets}

La siguiente tabla identifica todos los ajustes preestablecidos de visualizador predefinidos y listos para usar que se incluyen con Dynamic Media.

Consulte también [Demostraciones en directo](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Para obtener información sobre las versiones compatibles del navegador web y del sistema operativo de los visores, consulte las Notas de la versión de los visores.

Consulte *Notas de la versión de los visores* en la tabla de contenido de la [Guía de referencia de visores](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

>[!NOTE]
>
>Todos los ajustes preestablecidos de visualizador integrados en Dynamic Media ya están activados (activados), pero debe publicarlos.\
>Consulte [Ajustes preestablecidos del visualizador de publicaciones](#publishing-viewer-presets).
>
>Los ajustes preestablecidos de visor nuevos que cree y agregue deben activarse *y* publicarse.\
>Consulte [Activación o desactivación de ajustes preestablecidos de visualizador](#activating-or-deactivating-viewer-presets) y [Ajustes preestablecidos de visualizador de publicaciones](#publishing-viewer-presets).

| Título preestablecido del visor | Tipo | Nombre de archivo CSS |
|:---|:---|:---|
| Carrusel_Dotted_dark | Carousel_Set | html5_carouselviewer_dotted_dark.css |
| Carrusel_Dotted_light | Carousel_Set | html5_carouselviewer_dotted_light.css |
| Carrusel_Numeric_dark | Carousel_Set | html5_carouselviewer_numeric_dark.css |
| Carrusel_Numeric_light | Carousel_Set | html5_carouselviewer_numeric_light.css |
| Flotante | Zoom flotante | html5_flyoutviewer.css |
| ImageSet_dark | Conjunto de imágenes | html5_zoomviewer_dark.css |
| ImageSet_light | Conjunto de imágenes | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | Mixed_Media | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | Mixed_Media | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | Zoom flotante | html5_inlinezoomviewer.css |
| MixedMedia_dark | Mixed_Media | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | Mixed_Media | html5_mixedmediaviewer_light.css |
| PanoramicImage | Panoramic_Image | html5_panoramicimage.css |
| PanoramicImageVR | Panoramic_Image | html5_panoramicimage.css |
| Shoppable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shoppable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Interactive_Video | html5_interactivevideover_light.css |
| SpinSet_dark | Conjunto de giros | html5_spinviewer_dark.css |
| SpinSet_light | Conjunto de giros | html5_spinviewer_light.css |
| Vídeo (incluye compatibilidad con subtítulos) | Vídeo | html5_videoviewer.css |
| Video_social (incluye compatibilidad con subtítulos y medios sociales) | Vídeo | html5_videoviewersocial.css |
| Zoom_dark | Zoom | html5_basiczoomviewer_dark.css |
| Zoom_light | Zoom | html5_basiczoomviewer_light.css |
| ZoomVertical_oscuro | Vertical_Zoom | html5_zoomverticalviewer_dark.css |
| ZoomVertical_light | Vertical_Zoom | html5_zoomverticalviewer_light.css |

### Matriz de gestos de visores móviles compatibles {#supported-mobile-viewers-gestures-matrix}

La tabla siguiente identifica los gestos del visor móvil compatibles con los dispositivos iOS, Android 2.x y Android 3.x.

| Gesto | Zoom flotante  | Zoom | Giro |
|---|---|---|---|
| **Arrastrar** | Pans | Pans | Pans |
| **Tocar** | Muestra la ventana flotante | Muestra u oculta la interfaz de usuario | Muestra u oculta la interfaz de usuario |
| **Pulsar dos veces** | No se aplica | Amplía o restablece | Amplía o restablece |
| **Abrir el lápiz** | No se aplica | Amplía (solo iOS y Android 3x) | Amplía (solo iOS y Android 3x) |
| **Pellizque** | No se aplica | Reduce el tamaño de la página (solo iOS y Android 3x) | Reduce el tamaño de la página (solo iOS y Android 3x) |
| **Deslizar** | Scrolls swatch bar | Scrolls images | Spins |
| **Flick** | Desplaza la barra de muestra | Desplazamiento por imágenes | Giros |

## Aumento del número de ajustes preestablecidos de visor de Dynamic Media que se muestran {#increasing-the-number-of-viewer-presets-that-display}

AEM muestra una amplia variedad de ajustes preestablecidos de visor al ver un recurso desde **[!UICONTROL Vista de detalles > Visualizadores]**. Puede aumentar o disminuir el número de visualizadores que se muestran.

**Para aumentar el número de ajustes preestablecidos de visor de Dynamic Media que se muestran**:

1. Vaya a **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Vaya al nodo de listado de ajustes preestablecidos de visor en `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. En la propiedad **[!UICONTROL limit]**, cambie el **[!UICONTROL valor]**, que se establece en 15 de forma predeterminada, por el número deseado.
1. Vaya a la fuente de datos del ajuste preestablecido de visor en `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. En la propiedad **[!UICONTROL limit]** , cambie el número por el número deseado, por ejemplo `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Toque **[!UICONTROL Guardar todo]**.

## Creación de un nuevo ajuste preestablecido de visualizador de Dynamic Media {#creating-a-new-viewer-preset}

La creación de ajustes preestablecidos de visualizador le permite aplicar distintos ajustes para ver e interactuar con los recursos. Sin embargo, no es necesario crear nuevos ajustes preestablecidos de visor. Si lo prefiere, puede utilizar los ajustes preestablecidos de visualizador predeterminados que ya se incluyen con AEM Assets.

Si elige crear un nuevo ajuste preestablecido de visualizador, después de guardarlo, el estado del visualizador se activa automáticamente (establecido en **On**) en la página **[!UICONTROL Ajustes preestablecidos de visualizador]**. Este estado significa que está visible en el componente **[!UICONTROL Dynamic Media]** y en el componente **[!UICONTROL Medios interactivos]** y siempre que se obtiene una vista previa de una imagen o vídeo.

Algunos ajustes preestablecidos de visualizador tienen una configuración exclusiva que puede afectar al uso y al comportamiento general del visualizador. En función del ajuste preestablecido de visualizador que esté creando, es posible que desee tener en cuenta estas consideraciones especiales.

Consulte [Consideraciones especiales para crear un ajuste preestablecido de visualizador interactivo](#special-considerations-for-creating-an-interactive-viewer-preset).

Consulte [Consideraciones especiales para crear un ajuste preestablecido de visor de banners de carrusel](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**Para crear un nuevo ajuste preestablecido** de visualizador de Dynamic Media:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.

   ![ajustes preestablecidos de visor](assets/viewerpresets.png)

1. En la página **[!UICONTROL Ajustes preestablecidos de visor]**, en la barra de herramientas, pulse **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Nuevo ajuste preestablecido de visualizador]**, en el campo **[!UICONTROL Nombre de ajuste preestablecido]**, introduzca el nombre del nuevo ajuste preestablecido. Elija un nombre con cuidado; no se pueden editar después de pulsar **[!UICONTROL Crear]**.

   Cuando guarde el ajuste preestablecido más adelante en estos pasos, el nombre aparecerá en la página Ajustes preestablecidos de visor en el encabezado de columna **[!UICONTROL Título preestablecido]**.

1. En el menú desplegable **[!UICONTROL Tipo de medio enriquecido]**, seleccione el tipo de ajuste preestablecido de visualizador que desea crear y, en la esquina superior derecha de la página, pulse **[!UICONTROL Crear]**.

   Consulte [Tipos de medios enriquecidos para ajustes preestablecidos de visor](#rich-media-types-for-viewer-presets).

1. En la página **Editar ajuste preestablecido de visualizador**, pulse la pestaña **[!UICONTROL Aspecto]**.
1. Realice una de las acciones siguientes:

   * En el menú desplegable **[!UICONTROL Tipo seleccionado]**, seleccione un componente cuyo diseño visual desee personalizar. Como alternativa, puede tocar cualquier elemento visual en el visualizador para seleccionarlo para su configuración.

      El editor visual permite ver qué efecto tiene una propiedad determinada en un estilo. Solo tiene que configurar o ajustar cualquier propiedad para ver instantáneamente qué efecto tiene en el visor con la muestra a la izquierda del editor.

      Las propiedades de estilo CSS para cada tipo de ajuste preestablecido de visualizador se describen en el tema de ayuda &quot;Personalización del *&lt;viewer_name>* Visor&quot; de la [Guía de referencia del visualizador](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

      Por ejemplo, si está creando un ajuste preestablecido de visualizador del tipo `Mixed_Media`, consulte [Personalización del visualizador de medios mixtos](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) para obtener una lista y una descripción de cada propiedad.

   * Si ha definido la configuración de estilo en un archivo CSS independiente, puede cargar el archivo CSS en AEM Assets. Pulse **[!UICONTROL Importar CSS]** debajo del menú desplegable **[!UICONTROL Tipo seleccionado]** (puede que necesite desplazar el editor visual hacia arriba para verlo) para encontrar el archivo CSS cargado y asociarlo al ajuste preestablecido de visor.

      Al importar un archivo CSS, el editor visual comprueba si el CSS utiliza los marcadores de visor correctos. Por ejemplo, si está creando un visor de zoom, todas las reglas CSS que importe deben definirse con su nombre de clase de visor `.s7mixedmediaviewer` definido en un elemento de visor principal.

      Puede importar CSS arbitraria hecha a mano siempre y cuando defina correctamente los marcadores CSS de un visor determinado. (Los marcadores CSS se describen en cualquier tema de ayuda &quot;Personalización del *&lt;nombre del visor>* Visor&quot; en la [Guía de referencia de visores](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html). Por ejemplo, si desea obtener información sobre los marcadores de CSS para el visor de zoom, consulte [Personalización del visor de zoom](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html)). Sin embargo, es posible que el editor visual no entienda algunos valores de CSS. En estos casos, el editor visual intenta anular los errores para que el CSS pueda seguir funcionando.
   >[!NOTE]
   >
   >Si prefiere editar la CSS directamente en su formulario sin procesar, pulse **[!UICONTROL Mostrar/Ocultar CSS]** debajo del menú desplegable Tipo seleccionado (puede que necesite desplazar el editor visual hacia arriba para verlo).****
   >
   >Like the visual editor, when you make a change to a property directly in the CSS, you can instantly see what effect it has on the viewer sample. Y, esa misma propiedad se actualiza automáticamente al mismo tiempo en el editor visual. As such, you can use the raw CSS editor, or the visual editor, or use both interchangeably.

   >[!NOTE]
   >
   >Para las ilustraciones de botones, elija la imagen 2x y cargue las ilustraciones de alta resolución. Al trabajar con imágenes interactivas y banners de ventas, también puede seleccionar entre una variedad de botones de puntos interactivos predeterminados.

1. (Opcional) Cerca de la parte superior de la página **[!UICONTROL Editar ajuste preestablecido de visualizador]**, pulse **[!UICONTROL Escritorio]**, **[!UICONTROL Tablet]** o **[!UICONTROL Teléfono]** para definir de forma exclusiva estilos visuales para distintos tipos de dispositivos y pantallas.
1. En la página **[!UICONTROL Editar ajuste preestablecido de visualizador]**, pulse la pestaña **Comportamiento**. Como alternativa, puede tocar o hacer clic en cualquier elemento visual del visualizador y seleccionarlo para su configuración.
1. En el menú desplegable **[!UICONTROL Tipo seleccionado]**, seleccione un componente cuyos comportamientos desee cambiar.

   Many components in the visual editor have a detailed description associated with it. Estas descripciones aparecen en cuadros azules al expandir un componente para mostrar sus parámetros asociados.

   Algunos tipos de visualizador tienen componentes que permiten especificar comandos del servicio de imágenes en un campo de texto **Comando IS**. Para obtener una lista de los comandos que puede utilizar, consulte la [Referencia de API del servicio de imágenes](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html).

   >[!NOTE]
   >
   >**Si utiliza un dispositivo táctil, como un teléfono o una tableta...**
   >
   >Después de escribir un valor en el campo de texto, pulse en cualquier parte de la interfaz de usuario para enviar el cambio y cerrar el teclado virtual. Si pulsa **[!UICONTROL Entrar]**, no se producirá ninguna acción.

1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**.
1. Publique el nuevo ajuste preestablecido de visor. Debe publicar el ajuste preestablecido para poder utilizarlo en el sitio web.

   Consulte [Ajustes preestablecidos del visualizador de publicaciones](#publishing-viewer-presets).

## Consideraciones especiales para crear un ajuste preestablecido de visualizador interactivo {#special-considerations-for-creating-an-interactive-viewer-preset}

**Acerca de los modos de visualización de las miniaturas de imágenes en el panel**

Cuando se crea o edita un ajuste preestablecido de visualizador de vídeo interactivo, se puede elegir qué ajuste **[!UICONTROL Modo de visualización]** se utilizará al seleccionar `InteractiveSwatches` en el menú desplegable **[!UICONTROL Componente seleccionado]** en la pestaña **[!UICONTROL Comportamiento]**. El modo de visualización que elija afecta a cómo y cuándo aparecerán las miniaturas mientras se reproduce el vídeo. Puede elegir un modo de `segment`visualización (predeterminado) o un modo de `continuous`visualización.

| Modo de visualización | Descripción |
|---|---|
| [!UICONTROL Segmento] |  Los segmentos son el modo de visualización predeterminado para los ajustes preestablecidos de visualizador de vídeo interactivo preestablecidos de Shoppable_Video_light y Shoppable_Video_dark y cualquier ajuste preestablecido de visualizador de vídeo interactivo que cree usted mismo. |
|  | En este modo, cuando hay menos miniaturas asignadas a un segmento de vídeo que el número de puntos visibles en el panel de visualización, las miniaturas de los subsegmentos siguientes o anteriores no se extraen para rellenar ninguna zona vacía del panel. Es decir, conserva la visualización de muestras asignadas al segmento de vídeo concreto. |
| [!UICONTROL Continuo] | En el modo de visualización [!UICONTROL Continuous], si el número de miniaturas de un segmento es menor que el número visible en el panel, el visor incluye automáticamente la visualización de miniaturas del siguiente segmento o del segmento anterior, en los casos en que se muestre la última miniatura. |

**Comportamiento del desplazamiento automático en el visualizador de vídeo interactivo**

El comportamiento de desplazamiento automático de las miniaturas del visor de vídeo interactivo funciona independientemente del modo de visualización que haya elegido.

Cuando se crea o edita un ajuste preestablecido de visualizador de vídeo interactivo, se accede a **[!UICONTROL Desplazamiento automático]** desde la pestaña **[!UICONTROL Funcionamiento]**. En la pestaña Comportamiento, en el menú desplegable **[!UICONTROL Componentes seleccionados]**, pulse **[!UICONTROL Muestras interactivas]**. La casilla de verificación **[!UICONTROL Desplazamiento automático]** aparece debajo del campo de texto Comando IS.

Si desactiva el **[!UICONTROL desplazamiento automático]** (desactive la casilla de verificación) en el ajuste preestablecido de visualizador, durante la reproducción del vídeo por parte del usuario, el panel solo muestra la primera imagen en miniatura durante toda la duración del vídeo. Sin embargo, un usuario puede desplazarse manualmente por las miniaturas utilizando los iconos de flecha arriba y abajo, si lo desea.

Al activar (seleccionar) **[!UICONTROL Desplazamiento automático]** en el ajuste preestablecido de visualizador, durante la reproducción de vídeo, las imágenes en miniatura asignadas a un segmento de vídeo se desplazan hasta la vista al principio de un segmento. Sin embargo, hay instancias en las que ciertas miniaturas de un segmento se muestran el doble de tiempo que otras miniaturas antes o después de este segmento. Este comportamiento se produce porque el número de miniaturas de un segmento es mayor que el número visible en el panel y no se puede dividir de manera uniforme.

Como ejemplo, supongamos que tiene un segmento de vídeo de 30 segundos. Además, hay un total de nueve miniaturas para mostrar durante los 30 segundos. El tamaño del navegador es tal que hay cuatro posiciones de miniaturas visibles en el panel de visualización. El segmento de vídeo de 30 segundos se divide en tres subsegmentos. La tabla siguiente muestra el desglose de las miniaturas que se muestran para un subsegmento de tiempo determinado:

| **Subsegmento de vídeo** | **Tiempo de subsegmento en segundos** | **Miniaturas visibles en el panel** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

El subsegmento de vídeo 3 no se extiende más allá de las miniaturas asignadas a él. También observe que las miniaturas 4, 6 y 7 son visibles en el panel el doble de tiempo que las demás miniaturas.

La lógica que utiliza el visor para ver cuántas miniaturas se muestran en el panel en función del número de posiciones disponibles es la siguiente:

* Número de subsegmentos = redondear al subsegmento siguiente (número de miniaturas/número de espacios visibles en el panel de miniaturas, según el tamaño de la ventana del navegador).

   Con el ejemplo de la tabla anterior, 9 miniaturas / 4 ranuras = 2,25; la lógica del visor lo redondea a tres subsegmentos.

* Número de miniaturas = redondear a la siguiente miniatura (número de miniaturas/número de subsegmentos de vídeo).

   Con el ejemplo de la tabla anterior, 9 miniaturas / 3 subsegmentos de vídeo = 3 miniaturas.

* Duración del subsegmento = duración total del vídeo/número de subsegmentos de vídeo.

   Con el ejemplo de la tabla anterior, 30 segundos / 3 subsegmentos de vídeo = 10 segundos de visualización de cada subsegmento de vídeo.

### Consideraciones especiales para crear un ajuste preestablecido de visor de titular de carrusel {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Al crear ajustes preestablecidos de visor de titular de carrusel, se puede acceder a cambiar el estilo de las zonas interactivas de la siguiente manera:

|  | **Descripción** | **Acciones** |
|---|---|---|
| **Icono de zona interactiva** | Cambiar el icono utilizado para la zona interactiva | Para cambiar la imagen del icono de zona interactiva, en la pestaña **[!UICONTROL Aspecto]**, en **[!UICONTROL Componente seleccionado]**, pulse **[!UICONTROL ImageMapEffect]**. En **[!UICONTROL Icono]**, seleccione **[!UICONTROL Fondo]** y, en el campo **[!UICONTROL Imagen]**, vaya a la imagen de fondo que desee. |

## Activación o desactivación de ajustes preestablecidos de visor de Dynamic Media {#activating-or-deactivating-viewer-presets}

Los ajustes preestablecidos de visor disponibles en la interfaz de usuario dependen de los que estén activos en el modo Autor. By default, a viewer preset is *On* after you create it. Si desactiva el ajuste preestablecido, no lo verá en modo Autor. If the preset is published. it will always be published regardless of whether it is toggled on or off. You may want to deactivate viwer presets if the list becomes too unwieldy or you do not want a viewer preset made available to use.

**Para activar o desactivar los ajustes preestablecidos** del visor de Dynamic Media:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.
1. En la página **[!UICONTROL Ajuste preestablecido de visualizador]**, en el encabezado de columna **[!UICONTROL Estado]**, pulse el botón de alternancia para activar o desactivar un ajuste preestablecido de visualizador.

   Viewer presets that are activated have the toggle appear on the right, inside a blue box; deactivated viewer presets have the toggle appear on the left, inside a light grey box.

## Publicación de ajustes preestablecidos de visualizador de Dynamic Media {#publishing-viewer-presets}

Activar (o activar *On*) el estado de un ajuste preestablecido de visualizador significa que está visible en el componente Dynamic Media, en el componente Medios interactivos y siempre que se vea un recurso.

However, to deliver an asset with a viewer preset, the viewer preset must be published as well. All viewer presets must be activated *and* published to obtain URL or embed code for an asset. Debe activar y publicar todos los ajustes preestablecidos de visualizador integrados que se incluyen con Dynamic Media. Los ajustes preestablecidos de visualizador personalizado que cree y agregue se activan automáticamente, pero también se deben publicar.

Consulte [Activación o desactivación de ajustes preestablecidos de visor](#activating-or-deactivating-viewer-presets).

Consulte también [Vista previa de recursos](previewing-assets.md).

**Para publicar ajustes preestablecidos de visualizador de Dynamic Media**:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.
1. Seleccione uno o varios ajustes preestablecidos de visor que desee publicar.
1. En la barra de herramientas, pulse el icono **[!UICONTROL Publicar]**.

## Clasificación de ajustes preestablecidos de visor de Dynamic Media {#sorting-viewer-presets}

**Para ordenar los ajustes preestablecidos** del visor de Dynamic Media:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **Herramientas** (icono de martillo) **[!UICONTROL > Assets > Ajustes preestablecidos de visualizador]**.
1. Haga clic en **[!UICONTROL Título preestablecido]**, **[!UICONTROL Tipo]**, **[!UICONTROL Publicado]** o **[!UICONTROL Estado]** para ordenar por ese encabezado de la columna. Por ejemplo, haga clic en **[!UICONTROL Tipo]** para ordenar los tipos de ajustes preestablecidos de visualizador en orden alfabético o alfabético inverso.

## Edición de ajustes preestablecidos de visor de Dynamic Media {#editing-viewer-presets}

Tenga en cuenta que no se admite la edición de *ajustes preestablecidos de visor predefinidos y listos para usar*. Si edita un ajuste preestablecido de visualizador incorporado, se le pedirá que lo guarde con un nuevo nombre.

**Para editar los ajustes preestablecidos** del visor de Dynamic Media:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.
1. Seleccione un ajuste preestablecido marcando la casilla a la izquierda del título del ajuste preestablecido de visualizador.
1. En la barra de herramientas, pulse **[!UICONTROL Editar]**.
1. En la página **[!UICONTROL Editar ajuste preestablecido de visualizador]**, realice los cambios que desee en el ajuste preestablecido de visualizador.
1. Realice una de las acciones siguientes:

   * Pulse **[!UICONTROL Guardar]** para guardar los cambios y volver a la página **[!UICONTROL Ajuste preestablecido de visor]**.
   * Toque **[!UICONTROL Cancelar]** para anular los cambios realizados y volver a la página **[!UICONTROL Ajuste preestablecido de visor]**.

## Eliminación de ajustes preestablecidos de visualizador de Dynamic Media personalizados {#deleting-custom-viewer-presets}

Puede eliminar los ajustes preestablecidos de visor que haya creado y agregado a Dynamic Media.

**Para eliminar ajustes preestablecidos** del visor de Dynamic Media personalizado:

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.
1. En la página **[!UICONTROL Ajustes preestablecidos de visor]**, marque un **[!UICONTROL Título preestablecido]** y, a continuación, pulse el icono **[!UICONTROL Papelera]**.
1. Toque **[!UICONTROL Eliminar]**.

## Aplicación de un ajuste preestablecido de visualizador de Dynamic Media a un recurso {#applying-a-viewer-preset-to-an-asset}

Si ya ha publicado el recurso y el visualizador seleccionado, los botones **[!UICONTROL URL]** e **[!UICONTROL Incrustar]** aparecerán después de seleccionar un ajuste preestablecido de visualizador.

**Para aplicar un ajuste preestablecido de visualizador de Dynamic Media a un recurso**:

1. Abra el recurso y, cerca de la esquina superior izquierda de la página, pulse el menú desplegable y, a continuación, seleccione **[!UICONTROL Visualizadores]**.

   >[!NOTE]
   >
   >Si ya ha publicado el recurso y el visualizador seleccionado, los botones **[!UICONTROL URL]** e **[!UICONTROL Incrustar]** aparecerán después de seleccionar un ajuste preestablecido de visualizador.

1. Seleccione un ajuste preestablecido de visualizador en el panel izquierdo para aplicarlo al recurso.

   Puede [copiar la dirección URL para compartir](linking-urls-to-yourwebapplication.md) con otros usuarios.

## Entrega de recursos con ajustes preestablecidos del visor de Dynamic Media {#delivering-assets-with-viewer-presets}

Para obtener las direcciones URL de los ajustes preestablecidos de visor, consulte [Vinculación de direcciones URL a la aplicación web](linking-urls-to-yourwebapplication.md). Consulte también [Incrustación del visualizador de vídeo en una página web](embed-code.md).

Si utiliza AEM como WCM, puede añadir recursos utilizando los ajustes preestablecidos de visor directamente en la página. Consulte [Adición de recursos de Dynamic Media a páginas](adding-dynamic-media-assets-to-pages.md).
