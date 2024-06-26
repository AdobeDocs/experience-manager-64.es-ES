---
title: Imágenes interactivas
seo-title: Interactive Images
description: Aprenda a trabajar con imágenes interactivas en Dynamic Media
seo-description: Learn how to work with interactive images in dynamic media
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
exl-id: 4d3299e2-269b-4a41-a979-c884c707666d
feature: Interactive Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4283'
ht-degree: 1%

---

# Imágenes interactivas {#interactive-images}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede hacer que las imágenes estáticas sean ricas y atractivas para los clientes arrastrando y soltando puntos interactivos &quot;de ventas&quot; en una imagen. Los hotspots de ventas combinan información adicional sobre un producto o servicio con una capacidad directa y de punto de venta &quot;Añadir al carro&quot; o &quot;Comprar&quot;. Los clientes pueden pulsar estas zonas interactivas y estar vinculados directamente al producto o servicio, agregarlo a un carro de compras o estar vinculados a una página web. Las experiencias directas como estas aumentan la participación de los clientes y la conversión en el sitio web.

El siguiente es un banner de ventas con una ventana emergente de vista rápida. Un usuario activa la vista rápida tocando el círculo o la &quot;zona interactiva&quot; del modelo.

![chlimage_1-368](assets/chlimage_1-368.png)

Consulte imágenes interactivas en acción en la página web anterior. Para ello, vaya a:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Ver cómo se crean los titulares de imagen interactivos {#watch-how-interactive-image-banners-are-created}

Mire un recorrido de 10 minutos y 33 segundos en [creación de letreros de imagen interactivos](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). También aprenderá a previsualizar, editar y distribuir banners de imagen interactivos.

## Inicio rápido: Imágenes interactivas {#quick-start-interactive-images}

La siguiente descripción paso a paso del flujo de trabajo está diseñada para ayudarle a poner en marcha las imágenes interactivas con rapidez en AEM Assets.

Busque la variable **Ejemplo** dentro de algunas de las tareas de inicio rápido. Contiene un breve tutorial basado en el siguiente ejemplo de página web que aún no tiene imágenes interactivas agregadas:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

El tutorial ayuda a ilustrar los pasos para integrar imágenes interactivas en su propio sitio web.

**Flujo de trabajo de imágenes interactivas**:

1. **(Opcional) Identificación de variables de puntos interactivos** - Si utiliza AEM Assets y Dynamic Media de forma independiente, comience por identificar las variables dinámicas que se usan en la implementación de vista rápida existente de modo que pueda introducir datos de puntos interactivos al crear la imagen interactiva. Consulte [(Opcional) Identificación de variables de puntos interactivos](#optional-identifying-hotspot-variables).

   Sin embargo, si utiliza AEM Sites, AEM comercio electrónico o ambos, este paso no es necesario.

   Consulte [Conceptos de comercio electrónico en AEM Assets](/help/sites-administering/concepts.md).

1. **(Opcional) Creación de un ajuste preestablecido de visualizador de imagen interactivo** - Personalice la imagen gráfica que se utiliza para representar zonas interactivas. No es necesario crear su propio ajuste preestablecido de visualizador de imágenes interactivo si quiere utilizar el ajuste preestablecido de visualizador de imágenes interactivo preestablecido denominado `Shoppable_Banner` en su lugar.

   Consulte [(Opcional) Creación de un ajuste preestablecido de visualizador de imagen interactivo](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Carga de un banner de imagen** - Cargue banners de imagen que desee hacer interactivos.

   Consulte [Carga de un banner de imagen](#uploading-an-image-banner).

1. **Adición de zonas interactivas a un titular de imagen** : agregue una o varias zonas interactivas a un banner de imagen y asocie cada una de ellas a una acción como un hipervínculo, una vista rápida o un fragmento de experiencia. Después de agregar zonas interactivas, terminará esta tarea publicando la imagen interactiva.

   * Consulte [Adición de zonas interactivas a un titular de imagen](#adding-hotspots-to-an-image-banner).
   * Consulte [Vista previa de imágenes interactivas](#optional-previewing-interactive-images) - Opcional. Si lo desea, puede ver una representación del banner de ventas y probar su interactividad.
   * Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md) para obtener más información sobre cómo publicar recursos de imagen interactivos.

1. **Añadir una imagen interactiva al sitio web o al sitio web en AEM**

   * Si utiliza AEM Sites, AEM comercio electrónico o ambos, puede agregar la imagen interactiva directamente a una página web en AEM arrastrando el componente Medios interactivos a la página. Consulte [Adición de recursos de Dynamic Media a las páginas](adding-dynamic-media-assets-to-pages.md).
   * Si utiliza AEM Assets y Dynamic Media de forma independiente, debe copiar el código incrustado en el sitio web y, a continuación, integrarlo con la vista rápida existente. Consulte [Integración de una imagen interactiva con el sitio web](#integrating-an-interactive-image-with-your-website).
   * Si utiliza un WCM de terceros (Web Content Manager), debe integrar el nuevo vídeo interactivo con la implementación de vista rápida existente que se utiliza en el sitio web. Consulte [Integración de una imagen interactiva con una vista rápida existente](#integrating-an-interactive-image-with-an-existing-quickview).

## (Opcional) Identificación de variables de puntos interactivos {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Esta tarea solo es necesaria si los siguientes son verdaderos:
>
>* Desea agregar interactividad a la imagen activando las vistas rápidas.
>* La implementación de AEM sí lo hace *not* utilice un marco de integración de comercio electrónico para extraer datos de productos a AEM desde cualquier solución de comercio electrónico, como IBM Websphere Commerce, Elastic Path, hybris o Intershop. Consulte [Conceptos de comercio electrónico en AEM Assets](/help/sites-administering/concepts.md).
>
>Si la implementación de AEM utiliza eCommerce, puede omitir esta tarea y continuar con la siguiente tarea.

Comience por identificar las variables dinámicas que usa la implementación de vista rápida existente, de modo que pueda introducir datos de zona interactiva para crear la imagen interactiva.

Al agregar zonas interactivas a una imagen de banner en AEM Assets, debe asignar un SKU (unidad de mantenimiento de stock; un identificador único para cada producto o servicio distinto que ofrezca) y variables adicionales opcionales para cada zona interactiva. Estas variables de puntos interactivos se utilizan más adelante para hacer coincidir puntos interactivos con contenido de vista rápida.

Es importante identificar correctamente el número y el tipo de variables que se asociarán con los datos de puntos interactivos. Cada zona interactiva agregada a una imagen de banner debe contener suficiente información para identificar el producto de forma inequívoca en el sistema back-end existente.

Existen diferentes maneras de identificar un conjunto de variables que se utilizarán para los datos de puntos interactivos.

A veces, puede ser suficiente consultar a los especialistas en TI responsables de la implementación de Quickview existente, ya que es probable que sepan cuál es el conjunto mínimo de datos necesario para identificar Quickview en el sistema. Sin embargo, en la mayoría de los casos también es posible simplemente analizar el comportamiento existente del código front-end.

La mayoría de las implementaciones de Quickview utilizan el siguiente paradigma:

* El usuario activa un elemento de interfaz de usuario en el sitio web. Por ejemplo, al hacer clic en un **[!UICONTROL Vista rápida]** botón.
* El sitio web envía una solicitud de Ajax al servidor para cargar los datos o el contenido de la vista rápida, si es necesario.
* Los datos de vista rápida se traducen al contenido como preparación para su renderización en la página web.
* Por último, el código front-end procesa visualmente dicho contenido en la pantalla.

El método entonces es visitar diferentes áreas del sitio web existente donde se implementa la función de vista rápida, almacenar en déclencheur la vista rápida y capturar la URL de Ajax enviada por la página web para cargar los datos o el contenido de vista rápida.

Normalmente no es necesario que utilice ninguna herramienta de depuración especializada. Los navegadores web modernos cuentan con inspectores web que realizan un trabajo adecuado. A continuación se indican algunos ejemplos de exploradores web que incluyen inspectores web:

* Para ver todas las solicitudes HTTP salientes en Google Chrome, pulse F12 para abrir el **[!UICONTROL Herramientas para desarrolladores]** y, a continuación, haga clic en el **[!UICONTROL Red]** pestaña .

   En un Mac, presione **[!UICONTROL Comando + Opción + I]** para abrir el **[!UICONTROL Herramientas para desarrolladores]** y, a continuación, haga clic en la ficha Red.

* En Firefox, puede activar el complemento Firebug pulsando F12 y utilizando su pestaña Net, o puede utilizar el complemento integrado **[!UICONTROL Inspector]** herramienta y su **[!UICONTROL Red]** pestaña .

   En un Mac, presione **[!UICONTROL Comando + Opción + I]** para abrir el **[!UICONTROL Herramientas para desarrolladores]** y, a continuación, haga clic en el **[!UICONTROL Inspector]** pestaña .

Cuando la supervisión de red está activada en el explorador, ponga en déclencheur la vista rápida en la página.

Ahora, busque la URL de Ajax de vista rápida en el registro de red y copie la URL grabada para su análisis futuro. En la mayoría de los casos, cuando se déclencheur la vista rápida, hay numerosas solicitudes que se envían al servidor. Normalmente, la URL de Ajax de vista rápida es una de las primeras de la lista. Tiene una ruta o porción de cadena de consulta compleja y su tipo MIME de respuesta es `text/html`, `text/xml`o `text/javascript`.

Durante este proceso, es importante visitar diferentes áreas del sitio web, con diferentes tipos y categorías de productos. El motivo es que las URL de vista rápida pueden tener partes que son comunes para una categoría de sitio web determinada, pero cambian solo si visita un área diferente del sitio web.

En el caso más simple, la única parte de la variable en la URL de vista rápida es el SKU del producto. En este caso, el valor SKU es la única pieza de datos que necesita para agregar zonas interactivas a la imagen del banner.

Sin embargo, en casos complejos, la URL de vista rápida tiene diferentes elementos además del SKU, como ID de categoría, código de color, código de tamaño, etc. En estos casos, cada elemento es una variable independiente en la definición de datos de puntos interactivos de la función de imagen interactiva de ventas en AEM Assets.

Veamos los siguientes ejemplos de direcciones URL de vista rápida y las variables de puntos interactivos resultantes:

<table> 
     <tbody> 
      <tr> 
       <td><p>SKU único, que se encuentra en la cadena de consulta.</p> </td> 
       <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
        <ul> 
         <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
        </ul> <p>La única parte de variable en la dirección URL es el valor del parámetro de cadena de consulta productId= y es claramente un valor SKU. Por lo tanto, nuestras zonas interactivas solo necesitan campos SKU rellenados con valores como <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>SKU único, que se encuentra en la ruta de URL.</p> </td> 
       <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
        <ul> 
         <li><p><code>https://server/product/6422350843</code></p> </li> 
         <li><p><code>https://server/product/1607745002</code></p> </li> 
         <li><p><code>https://server/product/0086724882</code></p> </li> 
        </ul> <p>La parte variable se encuentra en la última parte de la ruta y se convierte en el valor SKU de las zonas interactivas: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>SKU e ID de categoría en la cadena de consulta.</p> </td> 
       <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
        <ul> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
        </ul> <p>En este caso, hay dos partes diferentes en la dirección URL. El SKU se almacena en la variable <code>prodId</code> y el ID de categoría</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**Ejemplo**

Puede aplicar el mismo enfoque utilizado en los tres ejemplos anteriores a la página web de demostración:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

La página web de demostración tiene varias miniaturas de producto, cada una con un botón de vista rápida etiquetado **[!UICONTROL Más información]**. Con la herramienta de depuración del explorador web aún activada, haga clic en cada botón y anote las URL de vista rápida registradas. Después de activar las cuatro vistas rápidas del producto disponibles en la página, tiene la siguiente lista de solicitudes de vista rápida realizadas en el servidor:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Al examinar estas llamadas al servidor, verá que la información específica del producto solo está presente en la ruta de solicitud. También observa que la cadena de consulta no se utiliza en absoluto y que hay dos tipos distintos de fragmentos de datos involucrados:

* El primer tipo es Hombres o Mujeres. Puede llamar a esta &quot;categoría de producto&quot;.
* El segundo tipo es el nombre del producto, como CamoPullover. Puede suponer que este es el SKU del producto.

Dada esta información, toda la URL de vista rápida tiene el siguiente patrón:

`/datafeed/$categoryId$-$SKU$.json`

En función de dicho análisis, utilizaría `categoryId` y `SKU` para zonas interactivas.

Ya está listo para cargar un titular de imagen y agregarle zonas interactivas mediante la función de imagen interactiva de ventas de AEM Assets.

## (Opcional) Creación de un ajuste preestablecido de visualizador de imagen interactivo {#optional-creating-an-interactive-image-viewer-preset}

Puede elegir utilizar el ajuste preestablecido predeterminado preestablecido de visualizador de imagen interactiva incorporado, denominado **[!UICONTROL Shoppable_Banner]** que viene con AEM Assets. O puede crear su propio ajuste preestablecido de visualizador personalizado para utilizarlo con imágenes interactivas.

Al crear un ajuste preestablecido personalizado del visualizador de imagen interactiva, puede determinar el aspecto de las zonas interactivas en el banner de imagen. Como parte de la creación del ajuste preestablecido de visualizador, puede elegir utilizar un gráfico de zona interactiva de una galería de imágenes predefinidas.

Después de guardar el ajuste preestablecido de visualizador, se activa automáticamente (se activa) en el **[!UICONTROL Ajuste preestablecido de visor]** en AEM Assets. Esta funcionalidad significa que está visible en el componente de Medios interactivos y siempre que se vea un recurso. Sin embargo, para *deliver* un banner interactivo con este ajuste preestablecido de visualizador, debe *publicar* también su ajuste preestablecido de visor (esto es cierto para ajustes preestablecidos de visor personalizados o integrados).

**Para crear un ajuste preestablecido de visualizador de imagen interactivo**:

1. En el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Ajustes preestablecidos de visor]**.
1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Crear]**.
1. En el **[!UICONTROL Nuevo ajuste preestablecido de visualizador]** , escriba un nombre para describir el ajuste preestablecido del visualizador de banners interactivo.

   Este es el título que aparecerá en el **[!UICONTROL Ajuste preestablecido de visor]** después de guardar.
1. En el **[!UICONTROL Tipo de medio enriquecido]** menú desplegable, seleccione **[!UICONTROL Imagen interactiva]**.
1. Pulse **Crear**.
1. En el **[!UICONTROL Editar ajuste preestablecido de visualizador]** de la página, pulse **[!UICONTROL Aspecto]** pestaña .
1. Realice una de las siguientes acciones:

   * Para cargar su propia imagen de zona interactiva que desee usar en imágenes, pulse el botón **[!UICONTROL Selector de recursos]** icono. En el **[!UICONTROL Seleccionar contenido]** página, vaya a la imagen de zona interactiva que desee usar, selecciónela y, a continuación, pulse el botón **[!UICONTROL Marca de verificación]** en la esquina superior derecha.
   * Para seleccionar una imagen de zona interactiva predefinida, pulse el botón **[!UICONTROL Galería de puntos interactivos]** icono. En la paleta galería de zonas interactivas, pulse la imagen de zona interactiva que desee utilizar.

1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**.

   Asegúrese de publicar el nuevo ajuste preestablecido de visor.

   Consulte [Ajustes Preestablecidos Del Visor De Publicaciones Que Ha Agregado](managing-viewer-presets.md#publishing-viewer-presets).

   Ya está listo para cargar un titular de imagen.

## Carga de un banner de imagen {#uploading-an-image-banner}

Si ya ha cargado las imágenes que desea utilizar, avance al siguiente paso, [Adición de zonas interactivas a un titular de imagen](#adding-hotspots-to-an-image-banner).

**Para cargar un titular de imagen**:

1. Cargue banners de imagen que desee hacer interactivos.

   Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

   Ya está listo para agregar zonas interactivas al titular de la imagen; consulte la siguiente tarea a continuación.

## Adición de zonas interactivas a un titular de imagen {#adding-hotspots-to-an-image-banner}

Puede agregar zonas interactivas a un banner de imagen mediante el editor del **[!UICONTROL Administración de puntos interactivos]** página.

Cuando agregue zonas interactivas, puede definirlas como una visualización emergente de vista rápida, como un hipervínculo o un fragmento de experiencia.

Consulte [Fragmentos de experiencias](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Tenga en cuenta que las herramientas de uso compartido de medios sociales en Imagen interactiva no son compatibles cuando incruste el visor en un fragmento de experiencia. Para solucionar este problema, puede utilizar o crear ajustes preestablecidos de visualizador que no tengan herramientas de uso compartido en redes sociales. Estos ajustes preestablecidos de visor permiten incrustarlos correctamente en fragmentos de experiencias.

**[!UICONTROL Deshacer]** y **[!UICONTROL Rehacer]** , cerca de la esquina superior derecha de la página, son compatibles durante la sesión de creación/edición actual.

Cuando termine de crear la imagen interactiva, puede utilizar **[!UICONTROL Vista previa]** para ver una representación de cómo aparecerá la imagen interactiva para los clientes.

Consulte [(Opcional) Vista previa de imágenes interactivas](#optional-previewing-interactive-images).

>[!NOTE]
>
>Cuando se añaden zonas interactivas a una imagen en una imagen interactiva o un titular de carrusel, la información del punto interactivo se almacena en la misma ubicación de metadatos (en relación con la ubicación de la imagen), independientemente de si es una imagen interactiva o un titular de carrusel. Esta funcionalidad significa que puede reutilizar fácilmente la misma imagen (junto con sus datos de puntos interactivos definidos) en cualquier visor.
>
>No obstante, tenga en cuenta que los carrusel Banners admiten mapas de imágenes en imágenes que también pueden contener zonas interactivas; una imagen interactiva no. Tenga esto en cuenta si desea crear una imagen interactiva o un titular de carrusel que utilice la misma imagen. Es posible que desee crear imágenes interactivas y titulares de carrusel utilizando copias independientes de la misma imagen.
>
>Consulte también [Banner de carrusel](carousel-banners.md).

>[!NOTE]
>
>Si edita imágenes interactivas con zonas interactivas y recorta la imagen, se eliminarán las zonas interactivas.

**Para agregar zonas interactivas a un titular de imagen**:

1. En la vista Recursos, desplácese hasta el banner de imagen que desee convertir en interactivo.
1. Realice una de las siguientes acciones:

   * Pase el ratón sobre la imagen y, a continuación, toque **[!UICONTROL Select]** (icono de marca de verificación). En la barra de herramientas, pulse **[!UICONTROL Editar]**.
   * Pase el ratón sobre la imagen y, a continuación, toque **[!UICONTROL Más acciones]** (icono de tres puntos) > **[!UICONTROL Editar]**.
   * Toque la imagen para abrirla en la **[!UICONTROL Vista de detalles]** página. En la barra de herramientas, pulse **[!UICONTROL Editar]**.

1. Cerca de la esquina superior izquierda de la página, pulse **[!UICONTROL Agregar zona interactiva]** (icono con el dedo) para abrir el **[!UICONTROL Administración de puntos interactivos]** página.
1. Cerca de la esquina superior izquierda de la página, pulse **[!UICONTROL Zona interactiva]**.
1. a. Cerca de la esquina superior izquierda del **Administración de puntos interactivos** página, toque **[!UICONTROL Zona interactiva]**.
b. En la imagen, pulse una ubicación en la que desee que aparezca el punto interactivo. Si es necesario, arrastre la zona interactiva para ajustar su ubicación.
c. Agregue más zonas interactivas según sea necesario repitiendo los pasos a y b. d. (Opcional) Para eliminar una zona interactiva, selecciónela en la imagen y pulse **[!UICONTROL Eliminar]** (icono de la papelera) en la sección **[!UICONTROL Puntos interactivos]** encabezado.

1. En el **[!UICONTROL Nombre]** campo de texto, escriba el nombre de la zona interactiva. Este nombre también aparece en la sección **[!UICONTROL Zona interactiva seleccionada]** lista desplegable.
1. Realice una de las siguientes acciones:

   * Toque **[!UICONTROL Vista rápida]**.

      * Si es cliente de AEM Sites o de comercio electrónico, pulse el botón **[!UICONTROL Selector de productos]** (lupa) para abrir **[!UICONTROL Seleccionar producto]** página. Pulse el producto que desee utilizar y, a continuación, pulse **[!UICONTROL Select]** en la esquina superior derecha de la página para volver a la **[!UICONTROL Administración de puntos interactivos]** página.
      * Si *not* un cliente de AEM Sites o de comercio electrónico

         * Consulte [Identificación de variables de zona interactiva](#optional-identifying-hotspot-variables); deberá definir estas variables.
         * A continuación, introduzca manualmente el valor de SKU. En el **[!UICONTROL Valor de SKU]** campo de texto, escriba el SKU del producto (unidad de mantenimiento de stock), que es un identificador único para cada producto o servicio distinto que ofrezca. El valor de SKU introducido rellena automáticamente la parte variable de la plantilla de vista rápida, de modo que el sistema sepa que debe asociar la zona interactiva tocada con la vista rápida de un SKU en particular.
         * (Opcional) Si hay otras variables dentro de la vista rápida que debe utilizar para identificar un producto, pulse **[!UICONTROL Agregar variable genérica]**. En el campo de texto, especifique una variable adicional. Por ejemplo, `category=Mens` es una variable añadida.
   * Toque **Hipervínculo**.

      * Si es cliente de AEM Sites, toque la **[!UICONTROL Selector de sitio]** para desplazarse a una dirección URL. Tenga en cuenta que el método de vinculación basado en URL no es posible si el contenido interactivo tiene vínculos con direcciones URL relativas, especialmente vínculos a páginas de AEM Sites.
      * Si es un cliente independiente, en la variable **[!UICONTROL HREF]** , especifique la ruta de URL completa a una página web vinculada.

      Asegúrese de especificar si desea abrir el vínculo en una nueva pestaña del explorador (opción predeterminada recomendada) o en la misma pestaña.

      Consulte [Uso de selectores](working-with-selectors.md) para obtener más información.

   * Toque **Fragmento de experiencia**.

      * Si es cliente de AEM Sites, toque la **[!UICONTROL Buscar]** (lupa) para abrir **[!UICONTROL Fragmento de experiencia]** página. Pulse el fragmento de experiencia que desee utilizar y, a continuación, pulse **[!UICONTROL Select]** en la esquina superior derecha de la página para volver a la página de administración de puntos interactivos.

         Consulte [Fragmentos de experiencias](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >Tenga en cuenta que las herramientas de uso compartido de medios sociales en Imagen interactiva no son compatibles cuando incruste el visor en un fragmento de experiencia. Para solucionar este problema, puede utilizar o crear ajustes preestablecidos de visualizador que no tengan herramientas de uso compartido en redes sociales. Estos ajustes preestablecidos de visor permiten incrustarlos correctamente en fragmentos de experiencias.

      * Especifique la anchura y la altura del fragmento de experiencia tal como aparecerán en el banner.



1. Toque **[!UICONTROL Guardar]** para guardar el trabajo y volver a la **[!UICONTROL Examinar]** página.
1. Publique la imagen interactiva. La publicación permite entregar el banner a través de la nube y también genera código incrustado si necesita integrarse con un sitio web de terceros.

   Consulte [Publicación de recursos](managing-assets-touch-ui.md#publishing-assets).

   Después de agregar zonas interactivas y publicar la imagen interactiva, ya está listo para agregarla al sitio web existente.

   Consulte [Integración de una imagen interactiva con el sitio web](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Si edita imágenes interactivas con zonas interactivas y recorta la imagen, se eliminarán las zonas interactivas.

### (Opcional) Vista previa de imágenes interactivas {#optional-previewing-interactive-images}

Puede utilizar Vista previa para ver una representación del aspecto que tendrá la imagen interactiva para los clientes y para probar las zonas interactivas de la imagen para asegurarse de que se comportan del modo esperado.

Cuando esté satisfecho con la imagen interactiva, puede publicarla.\
Consulte [Incrustación del visualizador de imágenes o vídeos en una página web](embed-code.md).\
Consulte [Vinculación de URL a la aplicación web](linking-urls-to-yourwebapplication.md). Tenga en cuenta que el método de vinculación basado en URL no es posible si el contenido interactivo tiene vínculos con direcciones URL relativas, especialmente vínculos a páginas de AEM Sites.\
Consulte [Adición de recursos de Dynamic Media a las páginas.](adding-dynamic-media-assets-to-pages.md)

**Para previsualizar imágenes interactivas**:

1. En la vista Recursos, desplácese a la imagen interactiva existente que haya creado y pulse para abrirla en Vista previa.
1. Cerca de la esquina superior izquierda de la página Vista previa, en la **[!UICONTROL Contenido]** lista desplegable, toque **[!UICONTROL Visualizadores]**.
1. En el **[!UICONTROL Visualizadores]** lista, pulsar **[!UICONTROL Shoppable_Banner]** o el nombre del ajuste preestablecido de visualizador de imágenes interactivo que ha creado.
1. Pulse las zonas interactivas de la imagen para probar las acciones asociadas.

## Publicación de recursos de imagen interactivos {#publishing-interactive-image-assets}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md) para obtener más información sobre cómo publicar recursos de imagen interactivos.

## Integración de una imagen interactiva con el sitio web {#integrating-an-interactive-image-with-your-website}

Después de cargar una imagen de banner, agregar zonas interactivas a la imagen y publicar la imagen interactiva, ya está listo para agregarla a la página del sitio web.

Si es cliente de AEM Sites, puede agregar la imagen interactiva arrastrando el componente de Medios interactivos a su página. Consulte [Adición de recursos de Dynamic Media a las páginas.](adding-dynamic-media-assets-to-pages.md)

Si es cliente independiente de AEM Assets, puede agregar manualmente la imagen interactiva a su sitio web como se describe en esta sección.

1. Copie el código incrustado de la imagen interactiva publicada.

   Consulte [Incrustación del visualizador de imágenes o vídeos en una página web](embed-code.md).

1. Agregue el código incrustado copiado en la ubicación deseada dentro de la página web.

   El código incrustado copiado está configurado para un entorno interactivo, por lo que debe ajustarse automáticamente al área asignada.

**Ejemplo**

Ejemplo de uso del sitio web de demostración:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

Observe que la imagen de los tres hombres es estática `IMG` etiqueta:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

La integración es tan sencilla como eliminar `IMG` y sustituirlo por el código incrustado copiado de AEM Assets. Puede ver el resultado en la siguiente URL que muestra la imagen interactiva de ventas en la página con tres puntos interactivos de círculo:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>En este punto, las zonas interactivas de la imagen interactiva de la tienda del sitio web de la demostración solo tienen fines de visualización; aún no están integrados con las vistas rápidas existentes.

Para aplicar un recorte a una imagen interactiva de ventas para un entorno interactivo, puede incluir el atributo de configuración de imagen interactiva `ZoomView.iscommand` a la ruta, donde `ZoomView` es el componente al que llamar y `iscommand` es el comando de servidor de imágenes de recorte que se aplica.

Consulte [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) atributo de configuración.

Consulte [recortar](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) servidor de imágenes.

Ya está listo para integrar la imagen interactiva con una vista rápida existente en su sitio web.

## Integración de una imagen interactiva con una vista rápida existente {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Esta tarea solo se aplica si es cliente independiente de AEM Assets.

El último paso de este proceso es integrar la imagen interactiva con una implementación de vista rápida existente en el sitio web. No existe una solución para la integración que funcione en todos los casos. Cada implementación de QuickView es única y se necesita un enfoque específico que muy probablemente involucre la asistencia de una persona de TI de front-end.

La implementación de vista rápida existente representa normalmente una cadena de acciones interrelacionadas que se producen en la página web en el siguiente orden:

1. Un usuario déclencheur un elemento en la interfaz de usuario del sitio web.
1. El código del front-end obtiene una URL de vista rápida basada en el elemento de la interfaz de usuario que se activó en el paso 1.
1. El código front-end envía una solicitud de Ajax utilizando la URL obtenida en el paso 2.
1. La lógica back-end devuelve los datos o el contenido de vista rápida correspondientes al código front-end.
1. El código front-end carga los datos o el contenido de Quickview.
1. De forma opcional, el código front-end convierte los datos de Quickview cargados en una representación de HTML.
1. El código front-end muestra un cuadro de diálogo modal o panel y representa el contenido del HTML en la pantalla para el usuario final.

Es posible que estas llamadas no representen llamadas de API públicas independientes a las que la lógica de página web puede llamar desde un paso arbitrario. En su lugar, se trata de una llamada encadenada en la que cada paso siguiente se oculta en la última fase (llamada de retorno) del paso anterior.

Al mismo tiempo que la imagen interactiva de ventas sustituye al paso 1 y al paso 2 parcialmente, cuando un usuario hace clic en un punto interactivo dentro de la imagen de ventas, el visor gestiona dicha interacción del usuario. El visor devuelve un evento a la página web que contiene todos los datos de zona interactiva añadidos anteriormente a AEM Assets.

En un controlador de eventos de este tipo, el código front-end hace lo siguiente:

* Escucha un evento emitido por la imagen interactiva de ventas.
* Crea una URL de vista rápida basada en los datos de zona interactiva.
* Déclencheur el proceso de carga de la vista rápida desde el servidor y de renderización en la pantalla para su visualización.

El código incrustado devuelto por AEM Assets ya tiene un controlador de eventos listo para usar en su lugar que se comenta, como se ve en el siguiente fragmento de código resaltado:

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : { 
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({ 
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 }, 
             });
        */
        s7interactiveimageviewer.init();
```

Por lo tanto, solo es necesario descomentar el código y reemplazar el cuerpo del controlador ficticio con el código específico de la página web en particular.

El proceso de construcción de la URL de vista rápida es básicamente opuesto al proceso utilizado para identificar las variables de zona interactiva incluidas anteriormente.

Consulte [Identificación de variables de zona interactiva](#optional-identifying-hotspot-variables).

Con nuestros ejemplos anteriores de URL de vista rápida, puede ver, en los ejemplos siguientes, cómo se construye la URL de vista rápida en cada caso:

<table> 
 <tbody> 
  <tr> 
   <td><p>SKU único, que se encuentra en la cadena de consulta</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>SKU único, que se encuentra en la ruta de URL</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>SKU e ID de categoría en la cadena de consulta</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td> 
  </tr> 
 </tbody> 
</table>

El último paso para almacenar en déclencheur la URL de vista rápida y activar el panel de vista rápida requiere, muy probablemente, la asistencia de una persona de TI de front-end de su departamento de TI. Tienen conocimientos para saber mejor cómo realizar un déclencheur exacto de la implementación de QuickView desde el paso adecuado, teniendo una URL de Quickview lista para usar.

Puede ver cómo se aplican estos pasos al sitio web de demostración para integrar completamente una imagen interactiva de ventas con el código de vista rápida. Anteriormente, la estructura de la URL de vista rápida se identificaba como la siguiente:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Para reconstruir esta URL dentro de la `quickViewActivate` , puede utilizar el `categoryId` y `SKU` los campos disponibles en la variable `inData` objeto que el código del visor pasa al controlador:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

El sitio web de demostración activa el cuadro de diálogo Vista rápida utilizando un `loadQuickView()` llamada de función. Esta función toma solo un argumento, que es la URL de datos de vista rápida. Como tal, el último paso necesario para integrar la imagen interactiva de ventas es añadir la siguiente línea de código al `quickViewActivate` controlador:

```xml
loadQuickView(quickViewUrl);
```

El siguiente es el código fuente completo:

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : { 
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({ 
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    }, 
   });
 s7interactiveimageviewer.init();
```

El sitio web de demostración final con la imagen interactiva completamente integrada tiene el siguiente aspecto:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html)

## Uso de las vistas rápidas para crear ventanas emergentes personalizadas {#using-quickviews-to-create-custom-pop-ups}

Consulte [Crear ventanas emergentes personalizadas con vistas rápidas](custom-pop-ups.md).
