---
title: Agregar recursos de Dynamic Media a páginas
description: Cómo añadir componentes de Dynamic Media a páginas en Adobe Experience Manager
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2845'
ht-degree: 4%

---

# Adición de Dynamic Media Assets a las páginas {#adding-dynamic-media-assets-to-pages}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para añadir la funcionalidad de Dynamic Media a los recursos que utilice en sus sitios web, puede agregar la variable **Dynamic Media** o **Medios interactivos** directamente en la página. Para ello, introduzca el modo Diseño y active los componentes de Dynamic Media. A continuación, puede añadir estos componentes a la página y añadir recursos al componente. Los componentes de Dynamic Media y Medios interactivos son inteligentes: saben si va a añadir una imagen o un vídeo y las opciones disponibles cambian en consecuencia.

Los recursos de Dynamic Media se agregan directamente a la página si utiliza AEM como WCM. Si utiliza un tercero para su WCM, [vincule](linking-urls-to-yourwebapplication.md) o [incruste](embed-code.md) los recursos. Para ver un sitio web interactivo de terceros, consulte [Distribución de imágenes optimizadas en un sitio interactivo](responsive-site.md).

>[!NOTE]
>
>Debe publicar los recursos antes de agregarlos a las páginas de AEM. Consulte [Publicación de recursos de Dynamic Media](publishing-dynamicmedia-assets.md).

## Adición de un componente de Dynamic Media a una página {#adding-a-dynamic-media-component-to-a-page}

Añadir un componente Dynamic Media a una página es lo mismo que añadir un componente a cualquier página. Los componentes de Dynamic Media se describen en detalle en las secciones siguientes.

>[!NOTE]
>
>Si hay un componente Dynamic Media en una página web a la que un usuario con permisos de solo lectura accede, la página se rompe y los componentes no se representan correctamente. El motivo es que la página se reconstruye para garantizar que las propiedades de los componentes sean correctas y que los recursos y configuraciones a los que se hace referencia sean accesibles. A continuación, la página se vuelve a procesar provocando que los componentes se rompan; el código de componente respectivo de la página no se puede volver a procesar debido al acceso de solo lectura del usuario.
>  
>Para evitar este problema, asegúrese de que los usuarios de AEM Sites tengan los permisos necesarios para acceder a los recursos.

1. En AEM, abra la página a la que desee añadir el componente Dynamic Media.
1. En el panel del lado izquierdo de la página (es posible que tenga que alternar la visualización del panel lateral), haga clic en el botón **[!UICONTROL Componentes]** icono.
1. En el **[!UICONTROL Componentes]** , en la lista desplegable , seleccione **[!UICONTROL Dynamic Media]**. Si no hay ninguna lista de componentes de Dynamic Media disponible, es probable que deba habilitar los componentes de Dynamic Media que desee utilizar. Consulte [Habilitación de componentes de Dynamic Media](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Arrastre un componente de Dynamic Media que desee usar a la página en la ubicación deseada.
1. Pase el puntero del ratón directamente sobre el componente. Cuando el componente esté rodeado por un cuadro azul, pulse una vez para mostrar la barra de herramientas del componente. Toque . **[!UICONTROL Configuración]** (llave inglesa).
1. [Editar los componentes](#dynamic-media-components) según sea necesario y haga clic en la marca de verificación para guardar los cambios.

### Habilitación de componentes de Dynamic Media {#enabling-dynamic-media-components}

Si no hay componentes de Dynamic Media disponibles para agregarlos a una página, es probable que deba habilitar primero los componentes que desee utilizar.

1. En AEM, abra la página a la que desee añadir el componente Dynamic Media.
1. En el lado izquierdo de la barra de herramientas, cerca de la parte superior de la página, pulse el icono Información de página y, a continuación, pulse **[!UICONTROL Editar plantilla]** en la lista desplegable.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. En el lado derecho de la barra de herramientas, cerca de la parte superior de la página, en la lista desplegable, pulse **[!UICONTROL Estructura]**.

   ![Directiva](/help/assets/assets-dm/structure-mode.png)

1. Cerca de la parte inferior de la página, pulse **[!UICONTROL Contenedor de diseño]** para abrir su barra de herramientas, pulse el icono Política .
1. En el **[!UICONTROL Contenedor de diseño]** en el **[!UICONTROL Propiedades]** , asegúrese de que **[!UICONTROL Componentes permitidos]** está seleccionada.

   ![Componentes permitidos](/help/assets/assets-dm/allowed-components.png)

1. Desplácese hasta que vea **[!UICONTROL Dynamic Media]**.
1. Pulse el icono > a la izquierda de **[!UICONTROL Dynamic Media]** para expandir la lista, seleccione los componentes de Dynamic Media que desea activar.

   ![Lista de componentes de Dynamic Media](/help/assets/assets-dm/dm-components-select.png)

1. Cerca de la esquina superior derecha de la **[!UICONTROL Contenedor de diseño]** , pulse el icono Listo (marca de verificación).

1. En el lado derecho de la barra de herramientas, cerca de la parte superior de la página, en la lista desplegable, pulse **[!UICONTROL Contenido inicial]**, luego [añadir un componente de Dynamic Media a una página](#adding-a-dynamic-media-component-to-a-page) como de costumbre.

## Localización de componentes de Dynamic Media {#localizing-dynamic-media-components}

Puede localizar los componentes de Dynamic Media de una de las dos maneras siguientes:

* En una página web de Sites, abra **[!UICONTROL Propiedades]** y seleccione la pestaña **[!UICONTROL Avanzadas]**. Seleccione el idioma que desee para la localización.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* En el selector de sitio, seleccione la página o el grupo de páginas que desee. Toque **[!UICONTROL Propiedades]** y seleccione **[!UICONTROL Avanzadas]** pestaña . Seleccione el idioma que desee para la localización.

   >[!NOTE]
   >
   >Tenga en cuenta que no todos los idiomas están disponibles en el **[!UICONTROL Idioma]** tiene actualmente asignados tokens.

## Componentes de Dynamic Media {#dynamic-media-components}

Dynamic Media y Medios interactivos están disponibles en la sección [!UICONTROL Dynamic Media] en [!UICONTROL Componentes]. Utilice la variable [!UICONTROL Medios interactivos] para cualquier recurso interactivo, como vídeo interactivo, imágenes interactivas o conjuntos de carrusel. Para todos los demás componentes de Dynamic Media, utilice el componente Dynamic Media .

>[!NOTE]
>
>Estos componentes no están disponibles de forma predeterminada y deben estar disponibles mediante el editor de plantillas antes de utilizarlos. [Una vez que estén disponibles](/help/sites-authoring/templates.md#editing-templates-template-authors) en el editor de plantillas, puede añadir los componentes a la página como lo haría con cualquier otro componente AEM.

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
>Al añadir el componente Dynamic Media, y **[!UICONTROL Configuración de Dynamic Media]** está en blanco o no puede agregar un recurso correctamente, compruebe lo siguiente:
>
>* Tiene [habilitado para Dynamic Media](config-dynamic.md). Dynamic Media está desactivado de forma predeterminada.
>* La imagen tiene un archivo tiff piramidal. Las imágenes importadas antes de que los medios dinámicos estén activados no tienen un archivo tiff piramidal.
>


#### Uso de imágenes {#when-working-with-images}

El componente Dynamic Media permite añadir imágenes dinámicas, incluidos conjuntos de imágenes, conjuntos de giros y conjuntos de medios mixtos. Puede acercar, alejar y, si corresponde, girar una imagen dentro de un conjunto de giros o seleccionar una imagen de otro tipo de conjunto.

También puede configurar el ajuste preestablecido de visualizador, el ajuste preestablecido de imagen o el formato de imagen directamente en el componente. Para que una imagen sea interactiva, puede establecer puntos de interrupción o aplicar un ajuste preestablecido de imagen interactivo.

Para editar las siguientes opciones de configuración de Dynamic Media, haga clic en el botón **[!UICONTROL Editar]** en el componente y, a continuación, **[!UICONTROL Configuración de Dynamic Media]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>De forma predeterminada, el componente de imagen Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente de la variable **[!UICONTROL Avanzadas]** con el **[!UICONTROL Anchura]** y **[!UICONTROL Altura]** configuración.

* **[!UICONTROL Ajuste preestablecido del visor]**
Seleccione un ajuste preestablecido de visualizador existente en el menú desplegable. Si el ajuste preestablecido de visualizador que está buscando no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de visualizador. No puede seleccionar un ajuste preestablecido de visualizador si utiliza un ajuste preestablecido de imagen y viceversa.
Esta es la única opción disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos. Los ajustes preestablecidos de visor que se muestran también son inteligentes: solo aparecen los ajustes preestablecidos de visor relevantes.

* **[!UICONTROL Modificadores del visor]**
Los modificadores del visualizador toman la forma de par name=value con un delimitador &amp; y permiten cambiar los visualizadores como se describe en la Guía de referencia del visualizador. Un ejemplo de modificador de visor es posterimage=img.jpg&amp;caption=text.vtt,1 que establece una imagen diferente para la miniatura del vídeo y asocia un archivo de subtítulo/subtítulo/subtítulo cerrado con el vídeo.

* **[!UICONTROL Ajuste preestablecido de imagen]**
Seleccione un ajuste preestablecido de imagen existente en el menú desplegable. Si el ajuste preestablecido de imagen que está buscando no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de imagen. No puede seleccionar un ajuste preestablecido de visualizador si utiliza un ajuste preestablecido de imagen y viceversa.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL Modificadores de imagen]**
Puede aplicar efectos de imagen suministrando comandos de imagen adicionales. Estos se describen en Ajustes preestablecidos de imagen y en la referencia del comando de servicio de imágenes.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL Puntos de interrupción]**
Si utiliza este recurso en un sitio interactivo, debe añadir los puntos de interrupción de la imagen. Los puntos de interrupción de la imagen deben separarse con comas (,). Esta opción funciona cuando no hay ninguna altura o anchura definidas en un ajuste preestablecido de imagen.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.
Puede editar la siguiente Configuración avanzada haciendo clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Título]**
Cambie el título de la imagen.

* **[!UICONTROL Texto alternativo]**
Agregue un título a la imagen para los usuarios que tengan los gráficos desactivados.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL URL, Abrir en]**
Puede configurar un recurso para abrir un vínculo. Defina la dirección URL y, en Abrir en , indique si desea que se abra en la misma ventana o en una nueva ventana.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL Anchura]** y **[!UICONTROL Altura]**
Introduzca el valor en píxeles si desea que la imagen tenga un tamaño fijo. Si deja estos valores en blanco, el recurso se adapta.

#### Al trabajar con vídeo {#when-working-with-video}

Utilice el componente Dynamic Media para añadir vídeo dinámico a las páginas web. Al editar el componente, puede elegir utilizar un ajuste preestablecido de visualizador de vídeo predefinido para reproducir el vídeo en la página.

![chlimage_1-540](assets/chlimage_1-540.png)

Debe editar las siguientes opciones de configuración de Dynamic Media haciendo clic en **[!UICONTROL Editar]** en el componente.

>[!NOTE]
>
>De forma predeterminada, el componente de vídeo de Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente con la variable **[!UICONTROL Anchura]** y **[!UICONTROL Altura]** en el [!UICONTROL Avanzadas] pestaña .

* **[!UICONTROL Ajuste preestablecido del visor]**
Seleccione un ajuste preestablecido de visualizador de vídeo existente en el menú desplegable. Si el ajuste preestablecido de visualizador que está buscando no está visible, es posible que tenga que hacerlo visible. Consulte Administración de ajustes preestablecidos de visualizador.

* **[!UICONTROL Modificadores del visor]**
Los modificadores del visor toman la forma de par name=value con un delimitador &amp; y permiten cambiar los visualizadores como se describe en la Guía de referencia de visores de Adobe. Un ejemplo de modificador de visor es posterimage=img.jpg&amp;caption=text.vtt,1

   Con los modificadores del visor, por ejemplo, puede hacer lo siguiente:

   * Asociación de un archivo de rótulo a un vídeo [caption.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Asociación de un archivo de navegación con un vídeo [navegación.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

Puede editar lo siguiente [!UICONTROL Configuración avanzada] haciendo clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Título]**
Cambie el título del vídeo.

* **[!UICONTROL Anchura]** y **[!UICONTROL Altura]**
Introduzca el valor en píxeles si desea que el vídeo sea de un tamaño fijo. Dejar estos valores en blanco lo hace adaptable.

#### Trabajar con Recorte inteligente {#when-working-with-smart-crop}

Utilice el componente Dynamic Media para añadir recursos de imagen de recorte inteligente a sus páginas web. Al editar el componente, puede elegir utilizar un ajuste preestablecido de visualizador de vídeo predefinido para reproducir el vídeo en la página.

Consulte también [Perfiles de imagen](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

Puede editar lo siguiente [!UICONTROL Configuración de Dynamic Media] haciendo clic en **[!UICONTROL Editar]** en el componente.

>[!NOTE]
>
>De forma predeterminada, el componente de imagen Dynamic Media es adaptable. Si desea que tenga un tamaño fijo, configúrelo en el componente de la pestaña [!UICONTROL Avanzado] con la **[!UICONTROL anchura]** y la **[!UICONTROL altura]** apropiadas.

* **[!UICONTROL Modificadores de imagen]**
Puede aplicar efectos de imagen suministrando comandos de imagen adicionales. Estos se describen en Ajustes preestablecidos de imagen y en la referencia del comando de servicio de imágenes.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

Puede editar lo siguiente **[!UICONTROL Avanzadas]** configuración haciendo clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Título]**
Cambie el título de la imagen de recorte inteligente.

* **[!UICONTROL Texto alternativo]**
Agregue un título a la imagen de recorte inteligente para los usuarios que tengan los gráficos desactivados.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL URL, Abrir en]**
Puede configurar un recurso para abrir un vínculo. Defina la dirección URL y, en Abrir en , indique si desea que se abra en la misma ventana o en una nueva ventana.
Esta opción no está disponible si visualiza conjuntos de imágenes, conjuntos de giros o conjuntos de medios mixtos.

* **[!UICONTROL Altura]** y **[!UICONTROL Anchura]**
Introduzca el valor en píxeles si desea que la imagen de recorte inteligente sea de un tamaño fijo. Dejar estos valores en blanco lo hace adaptable.

### Componente de Medios interactivos {#interactive-media-component}

El componente de Medios interactivos es para los recursos que tienen interactividad en ellos, como puntos interactivos o mapas de imágenes. Si tiene una imagen interactiva, un vídeo interactivo o un titular de carrusel, utilice el componente Medios interactivos .

El componente de Medios interactivos es inteligente: en función de si agrega una imagen o un vídeo, tiene varias opciones. Además, el visor es interactivo: el tamaño de la pantalla cambia automáticamente en función del tamaño de la pantalla. Todos los visores son visores HTML5.

>[!NOTE]
>
>Si hay un componente Dynamic Media, un componente de Medios interactivos o ambos en una página web a la que accede un usuario con permisos de solo lectura, los saltos de página y los componentes no se representan correctamente. El motivo es que la página se reconstruye para garantizar que las propiedades de los componentes sean correctas y que los recursos y configuraciones a los que se hace referencia sean accesibles. A continuación, la página se vuelve a procesar provocando que los componentes se rompan; el código de componente respectivo de la página no se puede volver a procesar debido al acceso de solo lectura del usuario.
> 
>Para evitar este problema, asegúrese de que los usuarios de AEM Sites tengan los permisos necesarios para acceder a los recursos.

![chlimage_1-541](assets/chlimage_1-541.png)

Puede editar lo siguiente **[!UICONTROL General]** configuración haciendo clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Ajuste preestablecido del visor]**
Seleccione un ajuste preestablecido de visualizador existente en el menú desplegable. Si el ajuste preestablecido de visualizador que está buscando no está visible, es posible que tenga que hacerlo visible. Los ajustes preestablecidos de visor deben publicarse antes de poder utilizarse. Consulte Administración de ajustes preestablecidos de visualizador.

* **[!UICONTROL Título]**
Cambie el título del vídeo.

* **[!UICONTROL Anchura]** y **[!UICONTROL Altura]**
Introduzca el valor en píxeles si desea que el vídeo sea de un tamaño fijo. Dejar estos valores en blanco lo hace adaptable.

Puede editar lo siguiente **[!UICONTROL Agregar al carro]** configuración haciendo clic en **[!UICONTROL Editar]** en el componente.

* **[!UICONTROL Mostrar recurso del producto]**
De forma predeterminada, este valor está seleccionado. El recurso de producto muestra una imagen del producto según se define en el módulo Comercio . Desactive la marca de verificación para no mostrar el recurso del producto.

* **[!UICONTROL Mostrar precio del producto]**
De forma predeterminada, este valor está seleccionado. El precio del producto muestra el precio del artículo tal como se define en el módulo Comercio. Desactive la marca de verificación para no mostrar el precio del producto.

* **[!UICONTROL Mostrar formulario de producto]**
De forma predeterminada, este valor no está seleccionado. El formulario de producto incluye variantes de producto como tamaño y color. Desactive la marca de verificación para no mostrar las variantes del producto.

### Componente de medios panorámicos {#panoramic-media-component}

El componente Panoramic Media es para aquellos recursos que son imágenes panorámicas esféricas. Estas imágenes proporcionan una experiencia de visualización de 360° de una habitación, propiedad, ubicación o paisaje. Para que una imagen pueda calificarse como panorama esférico, debe tener una o ambas de las siguientes opciones:

* Una relación de aspecto de 2:1.
* Etiquetada con las palabras clave &quot;equirectangular&quot; o (&quot;esférica&quot; + &quot;panorámica&quot;) o (&quot;esférica&quot; + &quot;panorámica&quot;). Consulte [Uso de etiquetas](/help/sites-authoring/tags.md).

Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente WCM &quot;Medios panorámicas&quot;.

![panorámico-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Para editar la siguiente configuración, pulse **[!UICONTROL Configurar]** en el componente.

* **[!UICONTROL Ajuste preestablecido de visor]**
Seleccione un visor existente en el menú desplegable Ajuste preestablecido de visor .

Si el ajuste preestablecido de visualizador que está buscando no está visible, compruebe que se ha publicado. Debe publicar ajustes preestablecidos de visualizador para poder utilizarlos. Consulte [Administración de ajustes preestablecidos de visor](managing-viewer-presets.md).

### Uso de HTTP/2 para enviar recursos de Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 es el nuevo protocolo web actualizado que mejora la forma en que se comunican los exploradores y los servidores. Proporciona una transferencia de información más rápida y reduce la cantidad de potencia de procesamiento necesaria. La entrega de recursos de Dynamic Media ahora puede realizarse a través de HTTP/2, lo que proporciona una mejor respuesta y tiempos de carga.

Consulte [Entrega HTTP2 de contenido](http2.md) para obtener información detallada sobre cómo empezar a usar HTTP/2 con su cuenta de Dynamic Media.

>[!MORELIKETHIS]
>
>* [Explicación de la administración de color con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Uso de miniaturas de vídeo personalizadas con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Explicación del visualizador de recursos con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Uso de vídeo interactivo con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Uso del reproductor de vídeo en AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Uso del enfoque de imagen con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

