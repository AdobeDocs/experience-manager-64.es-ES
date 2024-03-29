---
title: Banner de carrusel
seo-title: Carousel Banners
description: Aprenda a trabajar con banners de carrusel en Dynamic Media
seo-description: Learn how to work with carousel banners in dynamic media
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
exl-id: d2fdad3f-513b-4147-a7c6-a3c1b64dd6e3
feature: Carousel Banners
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4771'
ht-degree: 4%

---

# Banner de carrusel {#carousel-banners}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los banners de carrusel permiten a los especialistas en marketing impulsar la conversión creando fácilmente contenido promocional giratorio interactivo y entregándolo a cualquier pantalla.

La creación y modificación del contenido de los titulares promocionales puede llevar mucho tiempo, lo que limita su capacidad de publicar rápidamente contenido nuevo o de dirigirlo mejor. Los banners de carrusel le permiten crear o modificar rápidamente banners giratorios, añadir interactividad, como zonas interactivas vinculadas a los detalles del producto o recursos relacionados, y enviarlos a cualquier pantalla, lo que le permite llevar el nuevo contenido promocional al mercado más rápido.

Los titulares de carrusel se designan mediante un banner con la palabra **CAROUSELSET**:

![chlimage_1-438](assets/chlimage_1-438.png)

En su sitio web, un banner de carrusel puede tener el siguiente aspecto:

![chlimage_1-439](assets/chlimage_1-439.png)

Aquí puede navegar por las imágenes (haciendo clic en los números). Además, las diapositivas giran automáticamente en función de un intervalo de tiempo que se pueda personalizar. Las imágenes agregadas en el banner de carrusel admiten zonas interactivas y mapas de imágenes, donde los usuarios pueden tocar o ir a un hipervínculo o acceder a una ventana de vista rápida.

En este ejemplo, un usuario ha tocado o hecho clic en un mapa de imagen y ha accedido a la ventana Vista rápida para obtener guantes:

![chlimage_1-440](assets/chlimage_1-440.png)

## Ver cómo se crean los titulares de carrusel {#watch-how-carousel-banners-are-created}

Mire un recorrido de 10 minutos y 33 segundos en [cómo se crean los titulares de carrusel](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). También aprenderá a previsualizar, editar y enviar banners de carrusel.

>[!NOTE]
>
>Los usuarios no administrativos deben agregarse al **dam-users** para poder crear o editar banners de carrusel. Si tiene problemas para crear o editar, póngase en contacto con el administrador del sistema, que puede agregarle al **dam-users** grupo.

## Inicio rápido: Banner de carrusel {#quick-start-carousel-banners}

Para ponerle en marcha rápidamente:

1. [Identificar las variables de zona interactiva y mapa de imagen](#identifying-hotspot-and-image-map-variables) (solo para clientes que utilizan AEM Assets + Dynamic Media)

   Comience identificando las variables dinámicas que utiliza la implementación de vista rápida existente de modo que pueda introducir los puntos interactivos y los datos de mapa de imagen correctamente durante el proceso de creación de banners de carrusel en AEM Assets.

   >[!NOTE]
   >
   >Si es cliente de AEM Sites o comercio electrónico, puede utilizar la función integrada para navegar a las páginas de producto y buscar los SKU existentes en el catálogo de productos. No es necesario introducir manualmente variables de zona interactiva o mapa de imagen. Consulte la información sobre [configuración de eCommerce](/help/sites-administering/generic.md).
   >
   >Si es cliente de AEM Assets y Dynamic Media, debe introducir manualmente los datos de las zonas interactivas y los mapas de imágenes y, a continuación, integrar la URL publicada o el código incrustado con el sistema de administración de contenido de terceros.

1. Opcional: [Cree un ajuste preestablecido de visualizador de conjuntos de carrusel](managing-viewer-presets.md), según sea necesario.

   Si es administrador, puede personalizar el comportamiento y el aspecto del carrusel creando su propio ajuste preestablecido de visualizador de carrusel. La principal ventaja es que puede volver a utilizar este ajuste preestablecido de visualizador personalizado para varios carruseles. Sin embargo, los usuarios también tienen la opción de personalizar el comportamiento y el aspecto del carrusel directamente durante la creación del carrusel. Este es el enfoque preferido cuando desea un diseño muy específico para un carrusel determinado.

1. [Cargar un titular de imagen](#uploading-image-banners).

   Cargue banners de imagen que desee hacer interactivos.

1. [Crear un conjunto de carrusel](#creating-carousel-sets).

   En Conjuntos de carruseles, los usuarios navegan por las imágenes de banner y tocan zonas interactivas o mapas de imágenes para acceder al contenido relevante.

   Para crear un conjunto de carrusel en Assets, pulse **[!UICONTROL Crear]** y, a continuación, seleccione **[!UICONTROL Conjuntos de carrusel]**. Agregue recursos a las diapositivas y pulse **[!UICONTROL Guardar]**. También puede editar el aspecto y el comportamiento del carrusel directamente en el editor.

1. [Agregue zonas interactivas o mapas de imágenes a un banner de imagen.](#adding-hotspots-or-image-maps-to-an-image-banner)

   Agregue una o más zonas interactivas o mapas de imagen a un banner de imagen y asocie cada una de ellas a una acción como un vínculo, una vista rápida o un fragmento de experiencia. Después de agregar zonas interactivas o mapas de imágenes, para finalizar esta tarea, publique el conjunto de carrusel. La publicación crea el código incrustado que puede utilizar para copiar y aplicar a la página de aterrizaje del sitio web.

   Consulte [(Opcional) Vista previa de banners de carrusel](#optional-previewing-carousel-banners) - Opcional. Si lo desea, puede ver una representación del conjunto de carrusel y probar su interactividad.

1. [Publicar letreros de carrusel.](#publishing-carousel-banners)

   Puede publicar un conjunto de carrusel como lo haría con cualquier recurso. En Assets, vaya al conjunto de carrusel, selecciónelo y toque o **[!UICONTROL Publicación]**. Al publicar un conjunto de carrusel, se activa la dirección URL y la cadena Incrustar.

1. Realice una de las siguientes acciones:

   * [Agregue un banner de carrusel a la página de su sitio web](#adding-a-carousel-banner-to-your-website-page) Puede añadir la URL del banner de carrusel o incrustar el código que ha copiado en la página del sitio web.

      * [Integración del banner de carrusel con una vista rápida existente](#integrating-the-carousel-banner-with-an-existing-quickview). Si utiliza un sistema de administración de contenido web de terceros, deberá integrar el nuevo titular de carrusel con la implementación de vista rápida existente en el sitio web.
   * [Agregue un banner de carrusel a su sitio web en AEM](adding-dynamic-media-assets-to-pages.md) Si es cliente de AEM Sites, puede añadir el conjunto de carrusel directamente a la página en AEM, utilizando el componente Medios interactivos .


Si necesita editar los conjuntos de carrusel, consulte [edición de conjuntos de carrusel](#editing-carousel-sets). Además, puede ver y editar [Propiedades del conjunto de carrusel](/help/assets/managing-assets-touch-ui.md#editing-properties).

## Identificación de variables de zona interactiva y mapa de imagen {#identifying-hotspot-and-image-map-variables}

Comience identificando las variables dinámicas que utiliza la implementación de vista rápida existente de modo que pueda introducir puntos interactivos o datos de mapa de imagen correctamente durante el proceso de creación de conjuntos de carrusel en AEM Assets.

Al agregar zonas interactivas o mapas de imágenes a una imagen de banner en AEM Assets, debe asignar un SKU y variables adicionales opcionales a cada zona interactiva o mapa de imagen. Estas variables se utilizan más adelante para hacer coincidir puntos interactivos o mapas de imágenes con contenido de vista rápida.

>[!NOTE]
>
>Si es cliente de AEM Sites o AEM comercio electrónico, omita este paso. No es necesario identificar manualmente las variables de zona interactiva o mapa de imagen; puede utilizar la integración con comercio electrónico para la integración del producto. Consulte la información sobre [configuración de eCommerce](/help/sites-administering/generic.md). Además, puede utilizar el componente interactivo y añadirlo a su página web.
>
>Si es cliente de AEM Assets o Media, publica la URL o el código incrustado y, a continuación, integre el sistema de administración de contenido de terceros e identifique los puntos interactivos y los mapas de imágenes manualmente.

Es importante identificar correctamente el número y el tipo de variables que se asociarán con los datos de zona interactiva o mapa de imagen. Cada zona interactiva o mapa de imagen que se añada a una imagen de banner debe contener suficiente información para identificar sin ambigüedades el producto en el sistema back-end existente. Al mismo tiempo, cada zona interactiva o mapa de imagen no debe incluir más datos de los necesarios. El motivo es que esto haría que el proceso de entrada de datos sea demasiado complejo y en curso, o la administración de mapas de imágenes sea más propensa a errores.

Existen diferentes maneras de identificar un conjunto de variables que se utilizarán para los datos de zona interactiva o mapa de imagen.

A veces, puede ser suficiente consultar a los especialistas en TI responsables de la implementación de Quickview existente, ya que es probable que sepan cuál es el conjunto mínimo de datos necesario para identificar Quickview en el sistema. Sin embargo, en la mayoría de los casos también es posible simplemente analizar el comportamiento existente del código front-end.

La mayoría de las implementaciones de Quickview utilizan el siguiente paradigma:

* El usuario activa un elemento de interfaz de usuario en el sitio web. Por ejemplo, al hacer clic en un **[!UICONTROL Vista rápida]** botón.
* El sitio web envía una solicitud de Ajax al servidor para cargar los datos o el contenido de la vista rápida, si es necesario.
* Los datos de vista rápida se traducen al contenido como preparación para su renderización en la página web.
* Por último, el código front-end procesa visualmente dicho contenido en la pantalla.

El método entonces es visitar diferentes áreas del sitio web existente donde se implementa la función de vista rápida, almacenar en déclencheur la vista rápida y capturar la URL de Ajax enviada por la página web para cargar los datos o el contenido de vista rápida.

Normalmente no es necesario que utilice ninguna herramienta de depuración especializada. Los navegadores web modernos cuentan con inspectores web que realizan un trabajo adecuado. A continuación se indican algunos ejemplos de exploradores web que incluyen inspectores web:

* Para ver todas las solicitudes HTTP salientes en Google Chrome, pulse F12 (Windows) o Comando-Opción-I (Mac) para abrir el panel Herramientas para desarrolladores y, a continuación, pulse el botón **[!UICONTROL Red]** pestaña .
* En Firefox, puede activar el complemento Firebug pulsando F12 (Windows) o Comando-Opción-I (Mac) y utilizar su ficha Red, o bien puede utilizar la herramienta Inspector integrada y su pestaña Red.

Cuando la supervisión de red está activada en el explorador, ponga en déclencheur la vista rápida en la página.

Ahora, busque la URL de Ajax de vista rápida en el registro de red y copie la URL grabada para su análisis futuro. En la mayoría de los casos, cuando se déclencheur la vista rápida, hay numerosas solicitudes que se envían al servidor. Normalmente, la URL de Ajax de vista rápida es una de las primeras de la lista. Tiene una ruta o porción de cadena de consulta compleja y su tipo MIME de respuesta es `text/html`, `text/xml`o `text/javascript`.

Durante este proceso, es importante visitar diferentes áreas del sitio web, con diferentes tipos y categorías de productos. El motivo es que las URL de vista rápida pueden tener partes que son comunes para una categoría de sitio web determinada, pero cambian solo si visita un área diferente del sitio web.

En el caso más simple, la única parte de la variable en la URL de vista rápida es el SKU del producto. En este caso, el valor SKU es la única pieza de datos que necesita para agregar zonas interactivas o mapas de imagen a la imagen del banner.

Sin embargo, en casos complejos, la URL de vista rápida tiene diferentes elementos además del SKU, como ID de categoría, código de color, código de tamaño, etc. En estos casos, cada elemento es una variable independiente en la definición de datos de zona interactiva o mapa de imagen en la función de titular de carrusel.

Veamos los siguientes ejemplos de direcciones URL de vista rápida y las variables de zona interactiva o mapa de imagen que se obtienen:

<table> 
 <tbody> 
  <tr> 
   <td>SKU único, que se encuentra en la cadena de consulta.</td> 
   <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>La única parte variable de la dirección URL es el valor de la variable <code>productId=</code> parámetro de cadena de consulta, y es claramente un valor de SKU. Por lo tanto, nuestras zonas interactivas o mapas de imágenes solo necesitan campos SKU rellenados con valores como <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU único, que se encuentra en la ruta de URL.</td> 
   <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>La parte variable se encuentra en la última parte de la ruta y se convierte en el valor SKU de las zonas interactivas o los mapas de imágenes:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU e ID de categoría en la cadena de consulta.</td> 
   <td><p>Las direcciones URL de vista rápida registradas incluyen lo siguiente:</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>En este caso, hay dos partes diferentes en la dirección URL. El SKU se almacena en la variable <code>prodId</code> y el ID de categoría se almacena en la variable <code>category=</code>parámetro.</p> <p>Como tal, las definiciones de zona interactiva/mapa de imagen son pares. Es decir, un valor de SKU y una variable adicional llamada <code>categoryId</code>. Los pares resultantes son los siguientes:</p> 
    <ul> 
     <li><p>SKU <strong><code>305466</code></strong> y <code>categoryId</code> es <code>1100004</code>.</p> </li> 
     <li><p>SKU <strong><code>310181</code></strong> y <code>categoryId</code> es <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>SKU <strong><code>308706</code></strong> y <code>categoryId</code> es <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Carga de banners de imagen {#uploading-image-banners}

Si ya ha cargado las imágenes que desea utilizar, avance al siguiente paso, [Creación de conjuntos de carrusel](#creating-carousel-sets). Tenga en cuenta que las imágenes utilizadas en el carrusel deben cargarse después de habilitar Dynamic Media.

Para cargar titulares de imagen, consulte [Carga de recursos](managing-assets-touch-ui.md).

## Creación de conjuntos de carrusel {#creating-carousel-sets}

>[!NOTE]
>
>Los usuarios no administrativos deben agregarse al **[!UICONTROL dam-users]** para poder crear o editar banners de carrusel. Si tiene problemas para crear o editar, póngase en contacto con el administrador del sistema, que puede agregarle al **dam-users** grupo.

**Para crear un conjunto de carrusel**:

1. En Assets, vaya a la carpeta en la que desee crear el conjunto de carrusel y pulse **[!UICONTROL Crear > Conjunto de carrusel]**.
1. En el **[!UICONTROL Editor de titular de carrusel]** página, toque **[!UICONTROL Toque para abrir el Selector de recursos]** para seleccionar la imagen de la primera diapositiva.

   En el **[!UICONTROL Editor de titular de carrusel]** realice una de las acciones siguientes:

   * Cerca de la esquina superior izquierda de la página, pulse **[!UICONTROL Agregar diapositiva]** icono.
   * Cerca del centro de la página, pulse **[!UICONTROL Toque para abrir el Selector de recursos]**.

   Pulse para seleccionar los recursos que desea incluir en el conjunto de carrusel. Los recursos seleccionados tienen un icono de marca de verificación sobre ellos. Cuando haya terminado, pulse en , cerca de la esquina superior derecha de la página **[!UICONTROL Select]**.

   Con el Selector de recursos, puede buscar recursos escribiendo una palabra clave y pulsando **[!UICONTROL Retorno]**. También puede aplicar filtros para restringir los resultados de búsqueda. Puede filtrar por ruta, colección, tipo de archivo y etiqueta. Seleccione el filtro y, a continuación, pulse el icono **[!UICONTROL Filtro]** en la barra de herramientas. Para cambiar la vista, pulse el botón **[!UICONTROL Ver]** icono y seleccionar **[!UICONTROL Vista de columna]**, **[!UICONTROL Vista de tarjeta]** o **[!UICONTROL Vista de lista]**.

   Consulte [Uso de selectores](working-with-selectors.md) para obtener más información.

1. Siga agregando diapositivas hasta que haya añadido todas las imágenes que desee rotar en el conjunto de carrusel.
1. (Opcional) Realice cualquiera de las siguientes acciones:

   * Si es necesario, arrastre las diapositivas para reordenar las imágenes en la lista de conjunto.
   * Para eliminar una imagen, selecciónela y, a continuación, pulse **[!UICONTROL Eliminar diapositiva]** en la barra de herramientas.
   * Para aplicar un ajuste preestablecido, cerca de la esquina superior derecha de la página, pulse la lista desplegable de ajustes preestablecidos y, a continuación, seleccione un ajuste preestablecido para aplicarlo al conjunto a la vez.

   Para eliminar una diapositiva, pulse la diapositiva y pulse **[!UICONTROL Eliminar diapositiva]** en la barra de herramientas. Para mover una diapositiva, pulse el icono del redirector y mantenga presionada la posición que desee y desplácese hasta la ubicación deseada.

1. Después de agregar las imágenes en las diapositivas, puede agregar un punto interactivo, un mapa de imágenes o ambos a la imagen. Consulte [adición de zonas interactivas o mapas de imágenes](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Puede cambiar el diseño visual y el comportamiento de los conjuntos de carrusel tocando o haciendo clic en las pestañas Comportamiento y Aspecto y realizando ajustes en el aspecto del banner de carrusel o en el comportamiento de componentes específicos. Consulte [administración de ajustes preestablecidos de visor](viewer-presets.md) para obtener más información sobre cómo utilizar el editor de visores.

   >[!NOTE]
   >
   >Para los banners de carrusel, lo siguiente puede ser lo que desee ajustar:
   >* Duración que muestra una imagen. De forma predeterminada, cada imagen se muestra durante 9 segundos.
   >* Animación. De forma predeterminada, cada transición de diapositiva es un fundido. Puede cambiarlo a una transición de diapositiva.
   >* Estilo de los botones. Los usuarios pueden rotar por los banners tocando cada punto o número. Puede cambiar dónde aparecen los botones del indicador de conjunto (y si son numéricos o de un estilo punteado) y su tamaño.
   >* Cambie el estilo de resaltado de un mapa de imagen o el icono utilizado para las zonas interactivas.
   >* Antes de editar un ajuste preestablecido de visualizador, elija el estilo en el que desea basar el ajuste preestablecido. Si no lo hace, cuando empiece a editar el ajuste preestablecido de visualizador, perderá todos los cambios si decide cambiar a otro ajuste preestablecido.


   También puede obtener una vista previa del aspecto que tendrá el titular del carrusel. Consulte [(Opcional) Vista previa de banners de carrusel](#optional-previewing-carousel-banners).

1. Toque **[!UICONTROL Guardar]** cuando termine.

## Adición de zonas interactivas o mapas de imágenes a un titular de imagen {#adding-hotspots-or-image-maps-to-an-image-banner}

Puede agregar zonas interactivas o mapas de imágenes a un banner mediante el editor de conjuntos de carrusel.

Al agregar zonas interactivas o mapas de imágenes, puede definirlas como una visualización emergente de vista rápida, como un hipervínculo o un fragmento de experiencia.

Consulte [Fragmentos de experiencias](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Tenga en cuenta que las herramientas de uso compartido de medios sociales en Carousel Banner no son compatibles cuando incrusta el visor en un fragmento de experiencia. Para solucionar este problema, puede utilizar o crear ajustes preestablecidos de visualizador que no tengan herramientas de uso compartido en redes sociales. Estos ajustes preestablecidos de visor permiten incrustarlos correctamente en fragmentos de experiencias.

Cuando agregue zonas interactivas o mapas de imágenes a una imagen, recuerde guardar su trabajo. **[!UICONTROL Deshacer]** y **[!UICONTROL Rehacer]** , cerca de la esquina superior derecha de la página, son compatibles durante la sesión de creación/edición actual.

Cuando termine de crear el banner de carrusel, puede utilizar **[!UICONTROL Vista previa]** para ver una representación de cómo aparecerá su titular de carrusel para los clientes.

Consulte [(Opcional) Vista previa de banners de carrusel](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Cuando se añaden zonas interactivas a una imagen en una [Imagen interactiva](interactive-images.md) Para un titular de carrusel, la información del punto interactivo se almacena en la misma ubicación de metadatos (en relación con la ubicación de la imagen), independientemente de si es una imagen interactiva o un titular de carrusel. Esta funcionalidad significa que puede reutilizar fácilmente la misma imagen (junto con sus datos de puntos interactivos definidos) en cualquier visor.
>
>No obstante, tenga en cuenta que los carrusel Banners admiten mapas de imágenes en imágenes que también pueden contener zonas interactivas; una imagen interactiva no. Tenga esto en cuenta si desea crear una imagen interactiva o un titular de carrusel que utilice la misma imagen. Es posible que desee crear imágenes interactivas y titulares de carrusel utilizando copias independientes de la misma imagen.

>[!NOTE]
>
>Si edita imágenes interactivas con zonas interactivas y recorta la imagen, se eliminarán las zonas interactivas.

**Para agregar zonas interactivas a un titular de imagen**:

1. En Assets, desplácese hasta el conjunto de carrusel que desee interactuar.
1. Seleccione el conjunto de carrusel y pulse **[!UICONTROL Editar]**.
1. En el Editor del visualizador de carrusel, seleccione la diapositiva que desee convertir en interactiva.
1. Cerca de la esquina superior izquierda de la página, pulse **[!UICONTROL Zona interactiva]** o **[!UICONTROL Mapa de imagen]**.
1. Realice una de las siguientes acciones:

   * Para zonas interactivas: En la imagen, pulse una ubicación en la que desee que aparezca el punto interactivo.
   * Para mapas de imágenes: En la imagen, pulse y arrastre desde la parte superior izquierda a la parte inferior derecha para crear el área del mapa de imagen. Para ajustar el tamaño del mapa de imagen, arrastre las esquinas.

   Si es necesario, arrastre el punto interactivo o el mapa de imagen a una nueva ubicación. Agregue zonas interactivas o mapas de imágenes adicionales según sea necesario.

   Para eliminar una zona interactiva o un mapa de imagen, pulse la pestaña **[!UICONTROL Acciones]**. En el encabezado **[!UICONTROL Mapas y zonas interactivas]**, del menú desplegable **[!UICONTROL Tipo seleccionado]**, seleccione el nombre del punto interactivo o del mapa de imagen que desea eliminar. Pulse el icono **[!UICONTROL Papelera]** situado junto al menú y, a continuación, pulse **[!UICONTROL Eliminar]**.

1. En el campo de texto Nombre , escriba el nombre del punto interactivo o del mapa de imagen. Este nombre también aparece en la sección **[!UICONTROL Mapas y puntos interactivos]** lista desplegable. Proporcionar un nombre facilita la identificación del punto interactivo o del mapa de imagen si decide realizar cambios en él en el futuro.
1. Realice una de las siguientes acciones en la sección **[!UICONTROL Acciones]** pestaña:

   * Toque **[!UICONTROL Vista rápida]**.

      * Si es cliente de AEM Sites y de comercio electrónico, pulse el botón **[!UICONTROL Selector de productos]** (lupa) para abrir **[!UICONTROL Seleccionar producto]** página. Pulse el producto que desee utilizar y, a continuación, pulse la marca de verificación en la esquina superior derecha de la página para volver a la **[!UICONTROL Editor de titular de carrusel]**.
      * Si no es cliente de AEM Sites o comercio electrónico

         * Consulte [Identificación de variables de zona interactiva](#identifying-hotspot-and-image-map-variables) como puede que desee definir estas variables.
         * A continuación, introduzca manualmente el valor de SKU. En el **[!UICONTROL Valor de SKU]** campo de texto, escriba el SKU del producto (unidad de mantenimiento de stock), que es un identificador único para cada producto o servicio distinto que ofrezca. El valor de SKU introducido rellena automáticamente la parte variable de la plantilla de vista rápida, de modo que el sistema sepa que debe asociar la zona interactiva tocada con la vista rápida de un SKU en particular.
         * (Opcional) Si hay otras variables dentro de la vista rápida que debe utilizar para identificar un producto, pulse **[!UICONTROL Agregar variable genérica]**. En el campo de texto, especifique una variable adicional. Por ejemplo, `category=Mens` es una variable añadida.
         * Consulte [Uso de selectores](working-with-selectors.md) para obtener más información.
   * Toque **[!UICONTROL Hipervínculo]**.

      * Si es cliente de AEM Sites, toque la **[!UICONTROL Selector de sitio]** para desplazarse a una dirección URL.

         >[!NOTE]
         >El método de vinculación basado en URL no es posible si el contenido interactivo tiene vínculos con direcciones URL relativas, especialmente vínculos a páginas de AEM Sites.

      * Si es un cliente independiente, en la variable **[!UICONTROL HREF]** , especifique la ruta de URL completa a una página web vinculada.

         Asegúrese de especificar si desea abrir el vínculo en una nueva pestaña del explorador (opción predeterminada recomendada) o en la misma pestaña.

         Consulte [Uso de selectores](working-with-selectors.md) para obtener más información.
   * Toque **[!UICONTROL Fragmento de experiencia]**.

      * Si es cliente de AEM Sites, toque la **[!UICONTROL Buscar]** (lupa) para abrir la página Fragmento de experiencia. Pulse el fragmento de experiencia que desee utilizar y, a continuación, pulse **[!UICONTROL Select]** en la esquina superior derecha de la página para volver a la página de administración de puntos interactivos.

         Consulte [Fragmentos de experiencias](/help/sites-authoring/experience-fragments.md).

         **Nota**: Tenga en cuenta que las herramientas de uso compartido de medios sociales en Carousel Banner no son compatibles cuando incrusta el visor en un fragmento de experiencia. Para solucionar este problema, puede utilizar o crear ajustes preestablecidos de visualizador que no tengan herramientas de uso compartido en redes sociales. Estos ajustes preestablecidos de visor permiten incrustarlos correctamente en fragmentos de experiencias.

      * Especifique la anchura y la altura del fragmento de experiencia tal como aparecerán en el banner.

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   También puede obtener una vista previa del aspecto que tendrá el titular del carrusel. Consulte [(Opcional) Vista previa de banners de carrusel](#optional-previewing-carousel-banners).

1. Pulse **[!UICONTROL Guardar]**.
1. Publique el conjunto de carrusel. La publicación crea el código incrustado o la URL que puede usar en la página del sitio web. Si es cliente de AEM Sites, puede agregar el conjunto de carrusel directamente a su página web.

   Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md).

   Consulte [Adición de un conjunto de carrusel a la página de aterrizaje del sitio web](#adding-a-carousel-banner-to-your-website-page)

## Edición de conjuntos de carrusel {#editing-carousel-sets}

>[!NOTE]
>
>Los usuarios no administrativos deben agregarse al **[!UICONTROL dam-users]** para poder crear o editar banners de carrusel. Si tiene problemas para crear o editar, póngase en contacto con el administrador del sistema, que puede agregarle al **[!UICONTROL dam-users]** grupo.

Puede realizar diversas tareas de edición en los conjuntos de carrusel, como las siguientes:

* Agregue diapositivas a un conjunto de carrusel. Consulte también [Uso de selectores](working-with-selectors.md).
* Vuelva a ordenar las diapositivas en el conjunto de carrusel.
* Eliminar recursos del conjunto de carrusel.
* Aplique un ajuste preestablecido de visualizador.
* Eliminar el conjunto de carrusel.
* Agregue o edite zonas interactivas y mapas de imágenes. Consulte también [Uso de selectores](working-with-selectors.md).

Tenga en cuenta que si está editando imágenes interactivas con zonas interactivas y recorta la imagen, se eliminarán las zonas interactivas.

**Edición de un conjunto de carrusel**:

1. Realice una de las siguientes acciones:

   * Pase el ratón sobre un recurso de conjunto de carrusel y, a continuación, pulse **[!UICONTROL Editar]** (icono de lápiz).
   * Pase el ratón sobre un recurso de conjunto de carrusel y pulse **[!UICONTROL Select]** (icono de marca de verificación) y, a continuación, pulse **[!UICONTROL Editar]** en la barra de herramientas.
   * Pulse en un recurso de conjunto de carrusel y, a continuación, en la esquina superior izquierda de la página pulse **[!UICONTROL Editar]** (icono de lápiz).

1. Para editar el conjunto de carrusel, realice una de las acciones siguientes:

   * Para añadir una diapositiva, pulse el botón **[!UICONTROL Agregar diapositiva]** a continuación, vaya al recurso que desee agregar a esa diapositiva y pulse la marca de verificación.
   * Para reordenar las diapositivas, arrastre una diapositiva a una nueva ubicación (seleccione el icono de reordenar para mover elementos).
   * Para añadir una zona interactiva o un mapa de imagen, pulse los iconos de zona interactiva o del mapa de imagen y consulte [adición de zonas interactivas y mapas de imágenes](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Para editar el aspecto o el comportamiento del conjunto de carrusel, pulse el botón **[!UICONTROL Aspecto]** o **[!UICONTROL Comportamiento]** y, a continuación, defina las opciones que desee.
   * Para editar puntos interactivos o mapas de imágenes, en la diapositiva adecuada, seleccione un punto interactivo o mapa de imágenes y realice los cambios que sean necesarios en la **[!UICONTROL Acciones]** pestaña .
   * Para eliminar una diapositiva, selecciónela y pulse **[!UICONTROL Eliminar diapositiva]** en la barra de herramientas.
   * Para aplicar un ajuste preestablecido, cerca de la esquina superior derecha de la página, pulse la lista desplegable de ajustes preestablecidos y, a continuación, seleccione un ajuste preestablecido de visualizador.
   * Para eliminar un conjunto de carrusel completo, vaya al conjunto de carrusel, selecciónelo y, a continuación, pulse **[!UICONTROL Eliminar]**.

## (Opcional) Vista previa de banners de carrusel {#optional-previewing-carousel-banners}

Puede usar **[!UICONTROL Vista previa]** para ver el aspecto que tendrá el banner de carrusel para los clientes y para probar los puntos interactivos y los mapas de imágenes de los banners de carrusel para asegurarse de que se comportan del modo esperado.

Cuando esté satisfecho con el banner de carrusel, puede publicarlo.

* Consulte [Incrustación del visualizador de imágenes o vídeos en una página web](embed-code.md).
* Consulte [Vinculación de URL a la aplicación web](linking-urls-to-yourwebapplication.md). Tenga en cuenta que el método de vinculación basado en URL no es posible si el contenido interactivo tiene vínculos con direcciones URL relativas, especialmente vínculos a páginas de AEM Sites.
* Consulte [Adición de recursos de Dynamic Media a las páginas.](adding-dynamic-media-assets-to-pages.md)

Puede obtener una vista previa de los banners de carrusel desde el Editor de carrusel (método preferido) o desde el **[!UICONTROL Visualizadores]** lista.

**Para obtener una vista previa de los titulares de carrusel**:

1. En **[!UICONTROL Recursos]**, vaya a un banner de carrusel existente que haya creado y pulse para abrirlo.
1. Pulse **[!UICONTROL Editar]**.
1. En la lista de ajustes preestablecidos de visualizador situada en la esquina derecha de la barra de herramientas, seleccione un visualizador para previsualizar el banner de carrusel.

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Toque **[!UICONTROL Vista previa]**.
1. Pulse las zonas interactivas o los mapas de imágenes de la imagen para probar las acciones asociadas.

**Para obtener una vista previa de los banners de carrusel desde la lista Visualizadores**:

1. En **[!UICONTROL Recursos]**, vaya a un banner de carrusel existente que haya creado y pulse para abrirlo.
1. Cerca de la esquina superior izquierda del **[!UICONTROL Vista previa]** de la página, pulse **[!UICONTROL Contenido]** icono.
1. En el **[!UICONTROL Visualizadores]** en el panel de la izquierda de la página, pulse el nombre del ajuste preestablecido del visor de banners de carrusel que desee utilizar.
1. Pulse las zonas interactivas o los mapas de imágenes de la imagen para probar las acciones asociadas.

## Publicación de letreros de carrusel {#publishing-carousel-banners}

Debe publicar el carrusel para utilizarlo. Al publicar un conjunto de carrusel, se activa la dirección URL y el código incrustado. También publica el carrusel en la nube de Dynamic Media, que está integrada con una CDN para una entrega escalable y con rendimiento.

Si utiliza una imagen interactiva existente con zonas interactivas para el banner de carrusel, debe publicar la imagen interactiva por separado después de publicar el banner de carrusel.

Además, si modifica una imagen interactiva publicada previamente que está utilizando en un banner de carrusel, debe publicar la imagen interactiva antes de que esos cambios se reflejen en el banner de carrusel.

Consulte [Publicación de recursos de Dynamic Media](publishing-dynamicmedia-assets.md) para obtener información sobre cómo publicar banners de carrusel.

## Adición de un titular de carrusel a la página web {#adding-a-carousel-banner-to-your-website-page}

Después de cargar imágenes de banner para crear un carrusel, agregar zonas interactivas o mapas de imagen al banner y publicar el conjunto de carrusel, ya está listo para agregarlo a la página de sitio web existente.

Si es cliente de AEM Sites, puede agregar el banner de carrusel directamente a la página arrastrando el componente Medios interactivos a la página. Consulte [Adición de recursos de Dynamic Media a las páginas.](adding-dynamic-media-assets-to-pages.md)

Sin embargo, si es cliente independiente de recursos de AEM, puede añadir manualmente el banner de carrusel a la página de aterrizaje de su sitio web, tal como se describe en esta sección.

1. Copie el código incrustado del conjunto de carrusel publicado.

   Consulte [Incrustación del visualizador de imágenes o vídeos en una página web](embed-code.md).

1. Agregue el código incrustado que copió de AEM Assets a su página web.

   El código incrustado copiado es interactivo, por lo que debe ajustarse automáticamente al área de incrustación de la página.

## Integración del titular de carrusel con una vista rápida existente {#integrating-the-carousel-banner-with-an-existing-quickview}

Esta tarea solo se aplica si es cliente independiente de AEM Assets.

El último paso de este proceso es la integración del titular de carrusel con una implementación de vista rápida existente en su sitio web. Cada implementación de QuickView es única y se necesita un enfoque específico que muy probablemente involucre la asistencia de una persona de TI de front-end.

La implementación de vista rápida existente representa normalmente una cadena de acciones interrelacionadas que se producen en la página web en el siguiente orden:

1. Un usuario déclencheur un elemento en la interfaz de usuario del sitio web.
1. El código del front-end obtiene una URL de vista rápida basada en el elemento de la interfaz de usuario que se activó en el paso 1.
1. El código front-end envía una solicitud de Ajax utilizando la URL obtenida en el paso 2.
1. La lógica back-end devuelve los datos o el contenido de vista rápida correspondientes al código front-end.
1. El código front-end carga los datos o el contenido de Quickview.
1. De forma opcional, el código front-end convierte los datos de Quickview cargados en una representación de HTML.
1. El código front-end muestra un cuadro de diálogo modal o panel y representa el contenido del HTML en la pantalla para el usuario final.

Es posible que estas llamadas no representen llamadas de API públicas independientes a las que la lógica de página web puede llamar desde un paso arbitrario. En su lugar, se trata de una llamada encadenada en la que cada paso siguiente se oculta en la última fase (llamada de retorno) del paso anterior.

Al mismo tiempo que el banner de carrusel sustituye al paso 1 y al paso 2 parcialmente, cuando un usuario hace clic en un punto interactivo o mapa de imagen dentro del banner de carrusel, el espectador gestiona esta interacción del usuario. El visor devuelve un evento a la página web que contiene todos los datos de zona interactiva o mapa de imagen agregados anteriormente.

En un controlador de eventos de este tipo, el código front-end hace lo siguiente:

* Escucha un evento emitido por el titular de carrusel.
* Crea una URL de vista rápida basada en los datos de zona interactiva o mapa de imagen.
* Déclencheur el proceso de carga de la vista rápida desde el servidor y de renderización en la pantalla para su visualización.

El código incrustado devuelto por AEM Assets ya tiene un controlador de eventos listo para usar en su lugar con comentarios.

Por lo tanto, solo es necesario descomentar el código y reemplazar el cuerpo del controlador ficticio con el código específico de la página web en particular.

El proceso de construcción de la URL de vista rápida es básicamente opuesto al proceso utilizado para identificar las variables de zona interactiva y mapa de imagen que se abarcaron anteriormente.

Consulte [Identificación de variables de zona interactiva y mapa de imagen](#identifying-hotspot-and-image-map-variables).

El último paso para almacenar en déclencheur la URL de vista rápida y activar el panel de vista rápida requiere, muy probablemente, la asistencia de una persona de TI de front-end de su departamento de TI. Tienen conocimientos para saber mejor cómo realizar un déclencheur exacto de la implementación de QuickView desde el paso adecuado, teniendo una URL de Quickview lista para usar.

## Uso de las vistas rápidas para crear ventanas emergentes personalizadas {#using-quickviews-to-create-custom-pop-ups}

Consulte [Uso de las vistas rápidas para crear ventanas emergentes personalizadas](custom-pop-ups.md).
