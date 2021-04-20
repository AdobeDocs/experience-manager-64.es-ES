---
title: Adición de recursos de Dynamic Media a las páginas
seo-title: Adición de recursos de Dynamic Media a las páginas
description: Cómo añadir componentes de Dynamic Media a una página en AEM
seo-description: Cómo añadir componentes de Dynamic Media a una página en AEM
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: Components
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '2826'
ht-degree: 34%

---

# Agregar recursos de Dynamic Media a las páginas {#adding-dynamic-media-assets-to-pages}

Para añadir la funcionalidad de Dynamic Media a los recursos que utilice en sus sitios web, puede añadir el componente **Dynamic Media** o **Interactive Media** directamente en la página. Para ello, introduzca el modo Diseño y active los componentes de Dynamic Media. A continuación, puede añadir estos componentes a la página y añadir recursos al componente. Los componentes de Dynamic Media y Medios interactivos son inteligentes; es decir, saben si va a añadir una imagen o un vídeo, y las opciones disponibles cambian según corresponda.

Los recursos de Dynamic Media se agregan directamente a la página si utiliza AEM como WCM. Si utiliza un tercero para su WCM, [vincule](linking-urls-to-yourwebapplication.md) o [incruste](embed-code.md) los recursos. Para ver un sitio web interactivo de terceros, consulte [Distribución de imágenes optimizadas en un sitio interactivo](responsive-site.md).

>[!NOTE]
>
>Debe publicar los recursos antes de agregarlos a las páginas de AEM. Consulte [Publicación de recursos de Dynamic Media](publishing-dynamicmedia-assets.md).

## Adición de un componente Dynamic Media a una página {#adding-a-dynamic-media-component-to-a-page}

Añadir un componente Dynamic Media a una página es lo mismo que añadir un componente a cualquier página. Los componentes de Dynamic Media se describen en detalle en las secciones siguientes.

>[!NOTE]
>
>Si hay un componente Dynamic Media en una página web a la que un usuario con permisos de solo lectura accede, la página se rompe y los componentes no se representan correctamente. El motivo es que la página se reconstruye para garantizar que las propiedades de los componentes sean correctas y que los recursos y configuraciones a los que se hace referencia sean accesibles. A continuación, la página se vuelve a procesar provocando que los componentes se rompan; el código de componente respectivo de la página no se puede volver a procesar debido al acceso de solo lectura del usuario.
>  
>Para evitar este problema, asegúrese de que los usuarios de AEM Sites tengan los permisos necesarios para acceder a los recursos.

1. En AEM, abra la página a la que desea añadir el componente de Dynamic Media.
1. En el panel del lado izquierdo de la página (es posible que deba alternar la visualización del panel lateral), haga clic en el icono **[!UICONTROL Componentes]**.
1. En el encabezado **[!UICONTROL Componentes]**, en la lista desplegable, seleccione **[!UICONTROL Dynamic Media]**. Si no hay ninguna lista de componentes de Dynamic Media disponible, es probable que deba habilitar los componentes de Dynamic Media que desee utilizar. Consulte [Habilitación de componentes de Dynamic Media](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Arrastre un componente de Dynamic Media que desee usar a la página en la ubicación deseada.
1. Pase el puntero del ratón directamente sobre el componente. Cuando el componente esté rodeado por un cuadro azul, pulse una vez para mostrar la barra de herramientas del componente. Pulse el icono **[!UICONTROL Configuration]** (llave inglesa).
1. [Edite los ](#dynamic-media-components) componentes según sea necesario y haga clic en la marca de verificación para guardar los cambios.

### Habilitación de componentes de Dynamic Media {#enabling-dynamic-media-components}

Si no hay componentes de Dynamic Media disponibles para agregarlos a una página, es probable que deba habilitar primero los componentes que desee utilizar.

1. En AEM, abra la página a la que desea añadir el componente de Dynamic Media.
1. En el lado izquierdo de la barra de herramientas, cerca de la parte superior de la página, pulse el icono Información de página y, a continuación, pulse **[!UICONTROL Editar plantilla]** en la lista desplegable.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. En el lado derecho de la barra de herramientas, cerca de la parte superior de la página, en la lista desplegable, pulse **[!UICONTROL Estructura]**.

   ![Política](/help/assets/assets-dm/structure-mode.png)

1. Cerca de la parte inferior de la página, pulse **[!UICONTROL Contenedor de diseño]** para abrir su barra de herramientas y, a continuación, pulse el icono Política .
1. En la página **[!UICONTROL Contenedor de diseño]**, en el encabezado **[!UICONTROL Propiedades]**, asegúrese de que la pestaña **[!UICONTROL Componentes permitidos]** está seleccionada.

   ![Componentes permitidos](/help/assets/assets-dm/allowed-components.png)

1. Desplácese hasta que vea **[!UICONTROL Dynamic Media]**.
1. Pulse el icono > a la izquierda de **[!UICONTROL Dynamic Media]** para expandir la lista, seleccione los componentes de Dynamic Media que desea habilitar.

   ![Lista de componentes de Dynamic Media](/help/assets/assets-dm/dm-components-select.png)

1. Cerca de la esquina superior derecha de la página **[!UICONTROL Contenedor de diseño]**, pulse el icono Listo (marca de verificación).

1. En el lado derecho de la barra de herramientas, cerca de la parte superior de la página, en la lista desplegable, pulse **[!UICONTROL Contenido inicial]** y, a continuación, [añada un componente de Dynamic Media a una página](#adding-a-dynamic-media-component-to-a-page) como de costumbre.

## Localización de componentes de Dynamic Media {#localizing-dynamic-media-components}

Puede localizar los componentes de Dynamic Media de una de las dos maneras siguientes:

* En una página web de Sites, abra **[!UICONTROL Propiedades]** y seleccione la pestaña **[!UICONTROL Avanzadas]**. Seleccione el idioma que desee para la localización.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* En el selector de sitio, seleccione la página o el grupo de páginas que desee. Pulse **[!UICONTROL Properties]** y seleccione la pestaña **[!UICONTROL Advanced]**. Seleccione el idioma que desee para la localización.

   >[!NOTE]
   >
   >Tenga en cuenta que actualmente no todos los idiomas disponibles en el menú **[!UICONTROL Language]** tienen tokens asignados.

## Componentes de Dynamic Media {#dynamic-media-components}

Dynamic Media y Medios interactivos están disponibles en la pestaña [!UICONTROL Dynamic Media] en [!UICONTROL Componentes]. El componente de [!UICONTROL Medios interactivos] se utiliza para cualquier recurso interactivo, como vídeo interactivo, imágenes interactivas o conjuntos de carrusel. Para todos los demás componentes de Dynamic Media, utilice el componente de Dynamic Media.

>[!NOTE]
>
>Estos componentes no están disponibles de forma predeterminada y deben estar disponibles mediante el editor de plantillas antes de utilizarlos. [Una vez que estén ](/help/sites-authoring/templates.md#editing-templates-template-authors) disponibles en el editor de plantillas, puede añadir los componentes a la página como lo haría con cualquier otro componente de AEM.

![chlimage_1-539](assets/chlimage_1-539.png)

### Componente de Dynamic Media {#dynamic-media-component}

El componente Dynamic Media es inteligente: en función de si se añade una imagen o un vídeo, hay varias opciones. El componente admite ajustes preestablecidos de imagen, visores basados en imágenes, como conjuntos de imágenes, conjuntos de giros, conjuntos de medios mixtos y vídeo. Además, el visor es interactivo. Es decir, el tamaño de la pantalla cambia automáticamente en función del tamaño de la pantalla. Todos los visores son visores HTML5.

>[!NOTE]
>
>Si hay un componente Dynamic Media, un componente de Medios interactivos o ambos en una página web a la que accede un usuario con permisos de solo lectura, los saltos de página y los componentes no se representan correctamente. El motivo es que la página se reconstruye para garantizar que las propiedades de los componentes sean correctas y que los recursos y configuraciones a los que se hace referencia sean accesibles. A continuación, la página se vuelve a procesar provocando que los componentes se rompan; el código de componente respectivo de la página no se puede volver a procesar debido al acceso de solo lectura del usuario.
>  
>Para evitar este problema, asegúrese de que los usuarios de AEM Sites tengan los permisos necesarios para acceder a los recursos.

>[!NOTE]
>
>Cuando se añade el componente de Dynamic Media y la opción **[!UICONTROL Configuración de Dynamic Media]** está vacía o no puede añadir un recurso correctamente, compruebe lo siguiente:
>
>* [Dynamic Media](config-dynamic.md) se ha activado. Dynamic Media está desactivado de forma predeterminada.
>* La imagen tiene un archivo TIFF piramidal. Las imágenes importadas antes de la activación de Dynamic Media no tienen un archivo TIFF piramidal.

>



#### Uso de imágenes {#when-working-with-images}

El componente de Dynamic Media permite añadir imágenes dinámicas, como conjuntos de imágenes, conjuntos de giros y conjuntos de medios mixtos. Puede acercar, alejar y, si procede, girar una imagen en un conjunto de giros o seleccionar una imagen de otro tipo de conjunto.

También puede configurar el ajuste preestablecido de visor, el ajuste preestablecido de imagen o el formato de imagen directamente en el componente. Para hacer que en una imagen sea interactiva, puede establecer puntos de interrupción o aplicar un ajuste preestablecido de imagen interactiva.

Debe editar la siguiente Configuración de Dynamic Media haciendo clic en el icono **[!UICONTROL Editar]** del componente y luego en **[!UICONTROL Configuración de Dynamic Media]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>De forma predeterminada, el componente de imagen Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente de la pestaña **[!UICONTROL Avanzado]** con las opciones **[!UICONTROL Anchura]** y **[!UICONTROL Altura]**.

* **[!UICONTROL Ajuste]**
preestablecido de visualizadorSeleccione un ajuste preestablecido de visualizador existente en el menú desplegable. Si el ajuste preestablecido de visor que busca no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de visor. No es posible seleccionar un ajuste preestablecido de visor si utiliza un ajuste preestablecido de imagen, y viceversa.
Esta es la única opción disponible al visualizar conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos. Los ajustes preestablecidos de visor que se muestran también son inteligentes: solo aparecen los ajustes preestablecidos del visor pertinente.

* **[!UICONTROL Modificadores]**
del visorLos modificadores del visualizador toman la forma de par nombre=valor con un delimitador &amp; y permiten cambiar los visualizadores como se describe en la Guía de referencia del visualizador. Un ejemplo de modificador de visor es posterimage=img.jpg&amp;caption=text.vtt,1 que establece una imagen diferente para la miniatura del vídeo y asocia un archivo de subtítulo/subtítulo/subtítulo cerrado con el vídeo.

* **[!UICONTROL Ajuste]**
preestablecido de imagenSeleccione un ajuste preestablecido de imagen existente en el menú desplegable. Si el ajuste preestablecido de imagen que busca no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de imagen. No es posible seleccionar un ajuste preestablecido de visor si utiliza un ajuste preestablecido de imagen, y viceversa.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL Modificadores de]**
imagenPuede aplicar efectos de imagen suministrando comandos de imagen adicionales. Estos se describen en Ajustes preestablecidos de imagen y en la referencia del comando de servicio de imágenes.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* ****
Puntos de interrupciónSi utiliza este recurso en un sitio interactivo, debe agregar los puntos de interrupción de la imagen. Los puntos de interrupción de imagen deben separarse por comas (,). Esta opción funciona cuando no se ha definido ninguna altura o anchura en el ajuste preestablecido de una imagen.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.
Puede editar la siguiente Configuración avanzada haciendo clic en **[!UICONTROL Editar]** en el componente.

* ****
TítuloCambiar el título de la imagen.

* **[!UICONTROL Texto alternativoAñada un título a la imagen para los usuarios que tengan los gráficos desactivados.]**
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL URL, Abrir]**
enPuede configurar un recurso para abrir un vínculo. Defina la dirección URL y, en Abrir en, indique si quiere que se abra en la misma ventana o en una nueva.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **** Anchura y  ****
alturaIntroduzca el valor en píxeles si desea que la imagen tenga un tamaño fijo. Si deja estos valores en blanco, hace que el recurso sea adaptable.

#### Uso de vídeos {#when-working-with-video}

Utilice el componente Dynamic Media para añadir vídeo dinámico a las páginas web. Cuando edita el componente, tiene la opción de usar un ajuste preestablecido de visor de vídeo predefinido para reproducir el vídeo en la página.

![chlimage_1-540](assets/chlimage_1-540.png)

Debe editar la siguiente Configuración de Dynamic Media haciendo clic en **[!UICONTROL Editar]** en el componente.

>[!NOTE]
>
>De forma predeterminada, el componente de vídeo de Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente con la **[!UICONTROL Anchura]** y **[!UICONTROL Altura]** en la pestaña [!UICONTROL Avanzado].

* **[!UICONTROL Ajuste]**
preestablecido de visualizadorSeleccione un ajuste preestablecido de visualizador de vídeo existente en el menú desplegable. Si el ajuste preestablecido de visor que busca no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de visor. 

* **[!UICONTROL Modificadores]**
del visorLos modificadores del visualizador toman la forma de par nombre=valor con un delimitador &amp; y permiten cambiar los visualizadores como se describe en la Guía de referencia del visualizador de Adobe. Un ejemplo de modificador de visor es posterimage=img.jpg&amp;caption=text.vtt,1

   Con los modificadores del visor, por ejemplo, puede hacer lo siguiente:

   * Asocie un archivo de subtítulos a un subtítulo de vídeo [](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Asocie un archivo de navegación con un vídeo de [navegación.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

Puede editar la siguiente [!UICONTROL Configuración avanzada] haciendo clic en **[!UICONTROL Editar]** en el componente.

* ****
TítuloCambie el título del vídeo.

* **** Anchura y  ****
alturaIntroduzca el valor en píxeles si desea que el vídeo sea de un tamaño fijo. Si deja estos valores en blanco, hace que el vídeo sea adaptable.

#### Al trabajar con Recorte inteligente {#when-working-with-smart-crop}

Utilice el componente Dynamic Media para añadir recursos de imagen de recorte inteligente a sus páginas web. Cuando edita el componente, tiene la opción de usar un ajuste preestablecido de visor de vídeo predefinido para reproducir el vídeo en la página.

Consulte también [Perfiles de imagen](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

Puede editar la siguiente [!UICONTROL Configuración de Dynamic Media] haciendo clic en **[!UICONTROL Editar]** en el componente.

>[!NOTE]
>
>De forma predeterminada, el componente de imagen Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente de la pestaña [!UICONTROL Avanzado] con la **[!UICONTROL anchura]** y la **[!UICONTROL altura]** apropiadas.

* **[!UICONTROL Modificadores de]**
imagenPuede aplicar efectos de imagen suministrando comandos de imagen adicionales. Estos se describen en Ajustes preestablecidos de imagen y en la referencia del comando de servicio de imágenes.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

Puede editar las siguientes opciones de configuración **[!UICONTROL Advanced]** haciendo clic en **[!UICONTROL Editar]** en el componente.

* ****
TítuloCambiar el título de la imagen de recorte inteligente.

* **[!UICONTROL Texto alternativoAñada un título a la imagen de recorte inteligente para los usuarios que tengan los gráficos desactivados.]**
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL URL, Abrir]**
enPuede configurar un recurso para abrir un vínculo. Defina la dirección URL y, en Abrir en, indique si quiere que se abra en la misma ventana o en una nueva.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **** Altura y  ****
anchuraIntroduzca el valor en píxeles si desea que la imagen de recorte inteligente sea de un tamaño fijo. Si deja estos valores en blanco, hace que el vídeo sea adaptable.

### Componente de Medios interactivos {#interactive-media-component}

El componente de Medios interactivos es para los recursos que tienen elementos interactivos integrados en ellos, como puntos interactivos o mapas de imágenes. Si tiene una imagen interactiva, un vídeo interactivo o un titular de carrusel, utilice el componente de Medios interactivos.

El componente de Medios interactivos es inteligente: en función de si agrega una imagen o un vídeo, tiene varias opciones. Además, el visor es interactivo: el tamaño de la pantalla cambia automáticamente en función del tamaño de la pantalla. Todos los visores son visores HTML5.

>[!NOTE]
>
>Si hay un componente Dynamic Media, un componente de Medios interactivos o ambos en una página web a la que accede un usuario con permisos de solo lectura, los saltos de página y los componentes no se representan correctamente. El motivo es que la página se reconstruye para garantizar que las propiedades de los componentes sean correctas y que los recursos y configuraciones a los que se hace referencia sean accesibles. A continuación, la página se vuelve a procesar provocando que los componentes se rompan; el código de componente respectivo de la página no se puede volver a procesar debido al acceso de solo lectura del usuario.
> 
>Para evitar este problema, asegúrese de que los usuarios de AEM Sites tengan los permisos necesarios para acceder a los recursos.

![chlimage_1-541](assets/chlimage_1-541.png)

Puede editar las siguientes opciones de configuración **[!UICONTROL General]** al hacer clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Ajuste]**
preestablecido de visualizadorSeleccione un ajuste preestablecido de visualizador existente en el menú desplegable. Si el ajuste preestablecido de visor que busca no está visible, es posible que tenga que hacerlo visible. Los ajustes preestablecidos de visor se deben publicar para que se puedan usar. Consulte Administración de ajustes preestablecidos de visor. 

* ****
TítuloCambie el título del vídeo.

* **** Anchura y  ****
alturaIntroduzca el valor en píxeles si desea que el vídeo sea de un tamaño fijo. Si deja estos valores en blanco, hace que el vídeo sea adaptable.

Puede editar las siguientes opciones de configuración **[!UICONTROL Añadir a carro]** al hacer clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Mostrar]**
recurso de productoDe forma predeterminada, este valor está seleccionado. El recurso del producto muestra una imagen del producto, según se ha definido en el módulo Commerce. Desactive la casilla para no mostrar el recurso del producto.

* **[!UICONTROL Mostrar]**
precio del productoDe forma predeterminada, se selecciona este valor. El precio del producto muestra el precio del artículo, según se ha definido en el módulo Commerce. Desactive la casilla para no mostrar el precio del producto.

* **[!UICONTROL Mostrar]**
formulario de producto De forma predeterminada, este valor no está seleccionado. En el formulario del producto se incluye las variantes de producto, como talla y color. Desactive la casilla para no mostrar las variantes del producto.

### Componente de medios panorámicos {#panoramic-media-component}

El componente Panoramic Media es para aquellos recursos que son imágenes panorámicas esféricas. Estas imágenes proporcionan una experiencia de visualización de 360° de una habitación, propiedad, ubicación o paisaje. Para que una imagen pueda calificarse como panorama esférico, debe tener una o ambas de las siguientes opciones:

* Una relación de aspecto de 2:1.
* Etiquetada con las palabras clave &quot;equirectangular&quot; o (&quot;esférica&quot; + &quot;panorámica&quot;) o (&quot;esférica&quot; + &quot;panorámica&quot;). Consulte [Uso de etiquetas](/help/sites-authoring/tags.md).

Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente WCM &quot;Medios panorámicas&quot;.

![panorámico-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Puede editar la siguiente configuración tocando **[!UICONTROL Configurar]** en el componente.

* **[!UICONTROL Ajuste]**
preestablecido de visualizadorSeleccione un visualizador existente en el menú desplegable Ajuste preestablecido de visualizador.

Si el ajuste preestablecido de visualizador que está buscando no está visible, compruebe que se ha publicado. Debe publicar ajustes preestablecidos de visualizador para poder utilizarlos. Consulte [Administración de ajustes preestablecidos de visor](managing-viewer-presets.md). 

### Uso de HTTP/2 para enviar recursos de Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 es el nuevo protocolo web actualizado que mejora la forma en que se comunican los exploradores y los servidores. Proporciona una transferencia de información más rápida y reduce la cantidad de potencia de procesamiento necesaria. La entrega de recursos de Dynamic Media ahora puede realizarse a través de HTTP/2, lo que proporciona una mejor respuesta y tiempos de carga.

Consulte [Entrega HTTP2 de contenido](http2.md) para obtener información detallada sobre cómo empezar a utilizar HTTP/2 con su cuenta de Dynamic Media.

>[!MORELIKETHIS]
>
>* [Explicación de la administración de color con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Uso de miniaturas de vídeo personalizadas con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Explicación del visualizador de recursos con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Uso de vídeo interactivo con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Uso del reproductor de vídeo en AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Uso del enfoque de imagen con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

