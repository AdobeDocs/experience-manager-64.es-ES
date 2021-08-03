---
title: Vídeo en Dynamic Media
description: Aprenda a trabajar con vídeo en Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
exl-id: acb95a2b-0171-449e-97fa-f9a533f990de
feature: Vídeo
role: User
source-git-commit: d5b4f559b20c8671bd648d240b54cb65f73fd222
workflow-type: tm+mt
source-wordcount: '10377'
ht-degree: 4%

---

# Vídeo {#video}

En esta sección se describe cómo trabajar con vídeo en Dynamic Media.

## Inicio rápido: Vídeos {#quick-start-videos}

La siguiente descripción paso a paso del flujo de trabajo está diseñada para ayudarle a poner en marcha rápidamente los conjuntos de vídeos adaptables en Dynamic Media. Después de cada paso hay referencias cruzadas a encabezados de tema donde puede encontrar más información.

>[!NOTE]
>
>Antes de trabajar con vídeo en Dynamic Media, asegúrese de que su administrador de AEM ya haya habilitado y configurado los Cloud Services de Dynamic Media.
>
>* Consulte [Configuración de Cloud Services de Dynamic Media en Configuración de Dynamic Media - Modo híbrido.](/help/assets/config-dynamic.md)
>* Consulte [Configuración de Dynamic Media - Modo Scene7](config-dms7.md) y [Solución de problemas de Dynamic Media - Modo Scene7](troubleshoot-dms7.md)

>



1. **Cargue los** vídeos de Dynamic Media haciendo lo siguiente:

   * Cree su propio perfil de codificación de vídeo. O bien, simplemente puede utilizar el perfil predefinido &quot;Codificación de vídeo adaptable&quot; que viene con Dynamic Media.

      * [Creación de un perfil de codificación de vídeo](video-profiles.md).
      * Obtenga más información sobre [Prácticas recomendadas para la codificación de vídeo](#best-practices-for-encoding-videos).
   * Asocie el perfil de procesamiento de vídeo a una o varias carpetas donde vaya a cargar los vídeos maestros.

      * [Aplicación de un perfil de vídeo a carpetas](video-profiles.md#applying-a-video-profile-to-folders).
      * Obtenga más información sobre [Prácticas recomendadas para organizar los recursos digitales con el fin de utilizar perfiles de procesamiento](organize-assets.md#organize-using-folders).
      * Obtenga más información sobre [Organización de recursos digitales](organize-assets.md).
   * Cargue los vídeos de origen principales en las carpetas. Al agregar vídeos a la carpeta, estos se codifican según el perfil de procesamiento de vídeo que asignó a la carpeta.

      * Dynamic Media admite principalmente vídeos de formato corto con una duración máxima de 30 minutos.
      * Puede cargar archivos de vídeo de hasta 15 GB cada uno.
      * [Cargue sus vídeos](managing-video-assets.md#uploading-and-previewing-video-assets).
      * Obtenga más información sobre [Formatos de archivo de entrada compatibles](assets-formats.md#supported-multimedia-formats).
   * Monitorice cómo progresa la [codificación de vídeo](#monitoring-video-encoding-and-youtube-publishing-progress) desde la vista de recursos o flujos de trabajo.




1. **Administre sus** vídeos de Dynamic Media realizando una de las siguientes acciones:

   * Organizar, examinar y buscar recursos de vídeo

      * [Organización de recursos digitales](organize-assets.md)

         Obtenga más información sobre [Prácticas recomendadas para organizar los recursos digitales con el fin de utilizar perfiles de procesamiento](organize-assets.md#organize-using-folders)

      * [Búsqueda de ](search-video-assets.md) recursos de vídeo o  [Búsqueda de recursos](managing-assets-touch-ui.md#searching-assets)
   * Vista previa y publicación de recursos de vídeo

      * Vea el vídeo de origen y las representaciones codificadas del vídeo junto con sus miniaturas asociadas:

         [Vista previa de ](managing-video-assets.md#uploading-and-previewing-video-assets) vídeos o  [Vista previa de recursos](previewing-assets.md)

         [Visualización de representaciones de vídeo](video-renditions.md)

         [Administración de representaciones de vídeo](managing-assets-touch-ui.md#managing-renditions)

      * [Administrar ajustes preestablecidos de visor](managing-viewer-presets.md)
      * [Publicación de recursos](publishing-dynamicmedia-assets.md)
   * Trabajo con metadatos de vídeo

      * Vea las propiedades de una representación de vídeo codificada, como la velocidad de fotogramas, la velocidad de bits de audio y vídeo y el códec:

         [Visualización de las propiedades de representación de vídeo](video-renditions.md)

      * Edite las propiedades del vídeo, como el título, la descripción y las etiquetas, campos de metadatos personalizados:

         [Edición de propiedades de vídeo](managing-assets-touch-ui.md#editing-properties)

      * [Administración de metadatos de recursos digitales](metadata.md)
      * [Esquemas de metadatos](metadata-schemas.md)
   * Revisar, aprobar y anotar vídeos

      * [Anotación de ](managing-video-assets.md#annotating-video-assets) vídeo o  [anotación de recursos](managing-assets-touch-ui.md#annotating)
      * [Aplicación de flujos de trabajo a ](assets-workflow.md) recursos o  [Inicio de un flujo de trabajo en un recurso](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [Revisar recursos de carpetas](bulk-approval.md)
      * [Proyectos](/help/sites-authoring/projects.md)




1. **Publique los** vídeos de Dynamic Media realizando una de las siguientes acciones:

   * Si usa Adobe Experience Manager como sistema de administración de contenido web, puede agregar vídeos directamente a las páginas web.

      * [Adición de vídeos a las páginas web](adding-dynamic-media-assets-to-pages.md).
   * Si utiliza un sistema de administración de contenido web de terceros, puede vincular o incrustar vídeos a sus páginas web.

      * Integrar vídeo con URL:

         [Vincular URL en la aplicación web](linking-urls-to-yourwebapplication.md).
      * Integración de vídeo mediante el código incrustado en la página web:

         [Incrustación del visor de vídeo en una página](embed-code.md) web.
   * [Publicación de vídeos en YouTube](#publishing-videos-to-youtube).
   * [Generación de informes de vídeo](#viewing-video-reports).
   * [Adición de subtítulos al vídeo](#adding-captions-to-video).



## Trabajo con vídeo en Dynamic Media {#working-with-video-in-dynamic-media}

Vídeo en Dynamic Media es una solución integral que facilita la publicación de vídeos adaptables de alta calidad para su transmisión en varias pantallas, incluidos equipos de escritorio, iOS, Android, Blackberry y dispositivos móviles Windows. Un conjunto de vídeos adaptables agrupa versiones del mismo vídeo codificadas a diferentes velocidades de bits y formatos, como 400 kbps, 800 kbps y 1000 kbps. El equipo de escritorio o dispositivo móvil detecta el ancho de banda disponible.

Por ejemplo, en un dispositivo móvil iOS, detecta un ancho de banda como 3G, 4G o Wi-Fi. A continuación, selecciona automáticamente el vídeo codificado correcto entre las distintas tasas de bits de vídeo del conjunto de vídeos adaptables. El vídeo se transmite a escritorios, dispositivos móviles o tabletas.

Además, la calidad del vídeo se cambia automáticamente si las condiciones de red cambian en el escritorio o en el dispositivo móvil. Además, si un cliente entra en el modo de pantalla completa en un escritorio, el conjunto de vídeos adaptables responde mediante una mejor resolución, lo que mejora la experiencia de visualización del cliente. El uso de conjuntos de vídeos adaptables le ofrece la mejor reproducción posible para los clientes que reproduzcan vídeo de Dynamic Media en varias pantallas y dispositivos.

La lógica que utiliza un reproductor de vídeo para determinar qué vídeo codificado reproducir o seleccionar durante la reproducción se basa en el siguiente algoritmo:

1. El reproductor de vídeo carga el fragmento de vídeo inicial en función de la velocidad de bits más cercana al valor establecido para la &quot;velocidad de bits inicial&quot; en el propio reproductor.
1. El reproductor de vídeo cambia en función de los cambios en la velocidad de ancho de banda mediante los siguientes criterios:

   1. El reproductor elige el flujo de ancho de banda más alto por debajo o igual al ancho de banda estimado.
   1. El reproductor considera sólo el 80% del ancho de banda disponible. Sin embargo, si está subiendo, es más conservador, con solo el 70%, evitar sobreestimar y volver a empezar de inmediato.

Para obtener información técnica detallada sobre el algoritmo, consulte [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Para administrar conjuntos de vídeos adaptables y de vídeo único, se admite lo siguiente:

* Carga de vídeo desde numerosos formatos de vídeo y formatos de audio compatibles y codificación de vídeo al formato MP4 H.264 para su reproducción en varias pantallas. Puede utilizar ajustes preestablecidos de vídeo adaptable predefinidos, ajustes preestablecidos de codificación de vídeo único o personalizar su propia codificación para controlar la calidad y el tamaño del vídeo.

   * Cuando se genera un conjunto de vídeos adaptables, incluye vídeos MP4.
   * **Nota**: Los vídeos principales/de origen no se agregan a un conjunto de vídeos adaptables.

* Subtítulos de vídeo en todos los visores de vídeo HTML5.
* Organice, examine y busque vídeos con compatibilidad para metadatos completa para una administración eficiente de los recursos de vídeo.
* Envíe conjuntos de vídeos adaptables a la web, así como a escritorios y dispositivos móviles, incluidos iPhone, iPad, Android, Blackberry y Windows Phone.

El flujo de vídeo adaptable es compatible con diversas plataformas iOS. Consulte la [Guía de referencia de visores de Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Dynamic Media admite la reproducción de vídeo móvil para vídeo MP4 H.264. Puede encontrar los dispositivos Blackberry compatibles con este formato de vídeo en el siguiente enlace: [Formatos de vídeo compatibles con Blackberry](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

Puede encontrar los dispositivos de Windows compatibles con este formato de vídeo en el siguiente enlace: [Formatos de vídeo compatibles con Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* Reproduzca el vídeo con los ajustes preestablecidos del visualizador de vídeo de Dynamic Media, que incluyen lo siguiente:

   * Visores de vídeo únicos.
   * Visores de medios mixtos que combinan contenido de vídeo y de imagen.

* Configure reproductores de vídeo para satisfacer sus necesidades de promoción de la marca.
* Integre vídeo en su sitio web, sitio móvil o aplicación móvil con una URL simple o un código incrustado.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480). -->

Consulte también [Acerca de los visores HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=en#viewers-for-aem-assets-only) en la Guía de referencia de visores de Dynamic Media de Adobe.

## Práctica recomendada: Uso del visor de vídeo HTML5 {#best-practice-using-the-html-video-viewer}

Los ajustes preestablecidos del visor de vídeo HTML5 de Dynamic Media son reproductores de vídeo sólidos. Puede utilizarlos para evitar muchos problemas comunes asociados con la reproducción de vídeo HTML5 y problemas asociados con dispositivos móviles, como la falta de entrega de flujo adaptable y el limitado alcance del navegador de escritorio.

En el lado de diseño del reproductor, puede diseñar toda la funcionalidad del reproductor de vídeo mediante herramientas de desarrollo web estándar. Por ejemplo, puede diseñar los botones, los controles y el fondo personalizado de la imagen de póster utilizando HTML5 y CSS para ayudarle a llegar a sus clientes con un aspecto personalizado.

En el lado de reproducción del visor, detecta automáticamente la capacidad de vídeo del explorador. A continuación, sirve el vídeo utilizando la transmisión de vídeo HLS (flujo de vídeo adaptable). O, si esos métodos de envío no están presentes, se utiliza HTML5 progresiva en su lugar.

Al combinar en un solo reproductor la capacidad de diseñar los componentes de reproducción mediante HTML5 y CSS, tener reproducción incrustada y utilizar flujo adaptable y progresivo según la capacidad del explorador, se amplía el alcance del contenido de medios enriquecidos a los usuarios de escritorio y móviles y se garantiza una experiencia de vídeo optimizada.

Consulte también [Acerca de los visores HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html) en la Guía de referencia de visores de Adobe.

### Reproducción de vídeo en equipos de escritorio y dispositivos móviles mediante el visor de vídeo HTML5 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Para el streaming de vídeo adaptable móvil y de escritorio, los vídeos utilizados para el cambio de velocidad de bits se basan en todos los vídeos MP4 del conjunto de vídeos adaptables.

La reproducción de vídeo se produce mediante el flujo continuo de vídeo HLS (HTTP Live Streaming) o la descarga progresiva de vídeo. En versiones anteriores de AEM, como 6.0, 6.1 y 6.2, los vídeos se transmitían por HTTP.

Sin embargo, en AEM 6.3 y en adelante, los vídeos ahora se transmiten a través de HTTPS (es decir, flujo de vídeo HLS) porque la URL del servicio de puerta de enlace DM también utiliza HTTPS. Tenga en cuenta que este comportamiento predeterminado no afecta al cliente. Es decir, el flujo de vídeo siempre se producirá a través de HTTPS a menos que el explorador no lo admita. (véase la tabla siguiente). Por tanto,

* Si tiene un sitio web HTTPS con flujo de vídeo HTTPS, la transmisión está bien.
* Si tiene un sitio web HTTP con flujo de vídeo HTTPS, la transmisión está bien y no hay problemas de contenido mixto en el navegador web.

HLS (HTTP Live Streaming) es un estándar de Apple para el flujo de vídeo adaptable que ajusta automáticamente la reproducción en función de la capacidad de ancho de banda de la red. También permite al cliente &quot;buscar&quot; a cualquier punto del vídeo sin necesidad de esperar a que se descargue el resto del vídeo (consulte también Transmisión en directo HTTP).

El vídeo progresivo se entrega descargando y almacenando el vídeo localmente en la pantalla de escritorio o el dispositivo móvil del usuario.

En la tabla siguiente se describe el dispositivo, el navegador y el método de reproducción de los vídeos en equipos de escritorio y dispositivos móviles que utilizan el visor de vídeo de Dynamic Media.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Dispositivo</strong></td>
   <td><strong>Explorador</strong></td>
   <td><strong>Modo de reproducción de vídeo</strong></td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Internar Explorer 9 y 10</td>
   <td>Descarga progresiva.</td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Internar Explorer 11+</td>
   <td>En Windows 8 y Windows 10: forzar el uso de HTTPS siempre que se solicite HLS. Limitación conocida: HTTP en HLS no funciona en esta combinación de navegador/sistema operativo<br /> <br /> En Windows 7 - Descarga progresiva. Utiliza lógica estándar para seleccionar protocolo HTTP o HTTPS.</td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Firefox 23-44</td>
   <td>Descarga progresiva.</td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Firefox 45 o posterior</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Chrome</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Escritorio</td>
   <td>Safari (Mac)</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>Chrome (Android 6 o anterior)</td>
   <td>Descarga progresiva.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>Chrome (Android 7 o posterior)</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>Android (navegador predeterminado)</td>
   <td>Descarga progresiva.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>Safari (iOS)</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>Chrome (iOS)</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvil</td>
   <td>BlackBerry</td>
   <td>Flujo continuo de vídeo HLS.</td>
  </tr>
 </tbody>
</table>

## Arquitectura de la solución de vídeo de Dynamic Media {#architecture-of-dynamic-media-video-solution}

El siguiente gráfico muestra el flujo de trabajo general de creación de vídeos que se cargan y codifican mediante DMGgateway y que están disponibles para el consumo público.

![chlimage_1-427](assets/chlimage_1-427.png)

## Arquitectura de publicación híbrida para vídeos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Prácticas recomendadas para la codificación de vídeos {#best-practices-for-encoding-videos}

El flujo de trabajo de **[!UICONTROL codificación de vídeo de Dynamic Media]** codifica el vídeo si ha activado Dynamic Media y ha configurado los servicios de nube de vídeo. Este flujo de trabajo captura el historial de procesos de flujo de trabajo y la información de errores. Consulte [Supervisión de la codificación de vídeo y progreso de publicación en YouTube](#monitoring-video-encoding-and-youtube-publishing-progress). Si ha habilitado Dynamic Media y ha configurado los servicios de Video Cloud, el flujo de trabajo **[!UICONTROL Dynamic Media Encode Video]** surte efecto automáticamente al cargar un vídeo. (Si no utiliza Dynamic Media, el flujo de trabajo **[!UICONTROL DAM Update Asset]** tiene efecto).

<!-- DEAD ARTICLE AND VIDEO LINK The following are best-practice tips for encoding source video files.

For advice about video encoding, see the following:

* Article: *Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution:* [www.adobe.com/go/learn_s7_streaming101_en](https://www.adobe.com/go/learn_s7_streaming101_en).
* Video: *Video Encoding Basics:* [www.adobe.com/go/learn_s7_encoding_en](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Archivos de vídeo de origen principales {#source-video-files}

Cuando codifique un archivo de vídeo, utilice un archivo de vídeo de origen de la máxima calidad posible. Evite utilizar archivos de vídeo codificados anteriormente porque estos archivos ya están comprimidos y una codificación adicional crea un vídeo de calidad inferior.

* Dynamic Media admite principalmente vídeos de formato corto con una duración máxima de 30 minutos.
* Puede cargar archivos de vídeo de origen primarios de hasta 15 GB cada uno.

En la tabla siguiente se describe el tamaño recomendado, la proporción de aspecto y la velocidad de bits mínima que deben tener los archivos de vídeo de origen antes de codificarlos:

| Tamaño | Proporción de aspecto | Tasa de bits mínima |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 4500 kbps para la mayoría de los vídeos. |
| 1280 X 720 | 16:9 | 3000 - 6000 kbps, dependiendo de la cantidad de movimiento en el vídeo. |
| 1920 X 1080 | 16:9 | 6000 - 8000 kbps, dependiendo de la cantidad de movimiento en el vídeo. |

### Obtener los metadatos de un archivo {#obtaining-a-file-s-metadata}

Puede obtener los metadatos de un archivo consultando sus metadatos con una herramienta de edición de vídeo o utilizando una aplicación diseñada para obtener metadatos. A continuación se indican las instrucciones para utilizar MediaInfo, una aplicación de terceros, para obtener los metadatos de un archivo de vídeo:

1. Vaya a esta página web: [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo).
1. Seleccione y descargue el instalador para la versión GUI que está utilizando, y siga las instrucciones de instalación.
1. Después de la instalación, haga clic con el botón derecho en el archivo de vídeo (solo Windows) y seleccione **[!UICONTROL MediaInfo]**, o abra **[!UICONTROL MediaInfo]** y arrastre el archivo de vídeo a la aplicación. Verá todos los metadatos asociados con el archivo de vídeo, incluida su anchura, altura y fps.

### Proporción de aspecto {#aspect-ratio}

Cuando elija o cree un ajuste preestablecido de codificación de vídeo para el archivo de vídeo maestro, asegúrese de que el ajuste preestablecido tenga la misma relación de aspecto que el archivo de vídeo maestro. La relación de aspecto es la relación entre la anchura y la altura del vídeo.

Para determinar la relación de aspecto de un archivo de vídeo, obtenga los metadatos del archivo y tenga en cuenta la anchura y la altura del archivo (consulte Obtener los metadatos de un archivo más arriba). A continuación, utilice esta fórmula para determinar la relación de aspecto:

*anchura/altura = relación de aspecto*

En la tabla siguiente se describe cómo los resultados de la fórmula se traducen en opciones de relación de aspecto comunes:

| Resultado de la fórmula | Proporción de aspecto |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0,56 | 9:16 |

Por ejemplo, un vídeo con una anchura de 1440 x una altura de 1080 tiene una relación de aspecto de 1440/1080 o 1,33. En este caso, se elige un ajuste preestablecido de codificación de vídeo con una relación de aspecto de 4:3 para codificar el archivo de vídeo.

### Velocidad de bits {#bitrate}

La velocidad de bits es la cantidad de datos que se codifican para formar un solo segundo de reproducción de vídeo. La velocidad de bits se mide en kilobits por segundo (Kbps).

Dado que todos los códecs utilizan compresión con pérdida, la velocidad de bits es el factor más importante en la calidad del vídeo. Con la compresión con pérdidas, cuanto más comprima un archivo de vídeo, más degradará la calidad. Por este motivo, si todas las demás características son iguales (resolución, velocidad de fotogramas y códec), menor es la velocidad de bits, menor es la calidad del archivo comprimido.

Al seleccionar una codificación de velocidad de bits, hay dos tipos que puede elegir:

* **Codificación de velocidad de bits constante**  (CBR): durante la codificación CBR, la velocidad de bits o el número de bits por segundo se mantiene igual durante todo el proceso de codificación. La codificación CBR mantiene la velocidad de datos definida en su configuración en todo el vídeo. Además, la codificación CBR no optimiza los archivos multimedia para garantizar la calidad, pero sí ahorra espacio de almacenamiento.

   Utilice CBR si el vídeo contiene un nivel de movimiento similar en todo el vídeo. CBR se utiliza generalmente para transmitir contenido de vídeo. Consulte también [Uso de parámetros de codificación de vídeo personalizados](video-profiles.md#using-custom-added-video-encoding-parameters).

* **Codificación de velocidad de bits variable**  (VBR): la codificación VBR ajusta la velocidad de datos hacia abajo y hasta el límite superior establecido, según los datos requeridos por el compresor. Esto significa que durante un proceso de codificación VBR, la velocidad de bits del archivo multimedia aumenta o disminuye dinámicamente según las necesidades de velocidad de bits de los archivos multimedia.

   El VBR tarda más en codificarse, pero produce los resultados más favorables; la calidad del archivo multimedia es superior. VBR se utiliza generalmente para el envío progresivo http de contenido de vídeo.

**¿Cuándo debe usar VBR en comparación con CRB?**
Cuando se trata de seleccionar VBR en comparación con CBR, casi siempre se recomienda usar VBR para los archivos multimedia. VBR proporciona archivos de mayor calidad a velocidades de bits competitivas. Cuando utilice VBR, asegúrese de utilizar con codificación de dos pasos y establezca que la velocidad de bits máxima sea 1,5 veces la velocidad de bits de vídeo de destino.

Cuando elija un ajuste preestablecido de codificación de vídeo, tenga en cuenta la velocidad de conexión del usuario final de destino. Elija un ajuste preestablecido con una velocidad de datos del 80 % de esa velocidad. Por ejemplo, si la velocidad de conexión del usuario final objetivo es de 1000 Kbps, el mejor ajuste preestablecido es uno con una velocidad de datos de vídeo de 800 Kbps.

En esta tabla se describe la velocidad de datos de las velocidades de conexión típicas.

| Velocidad (Kbps) | Tipo de conexión |
|--- |--- |
| 256 | Conexión de acceso telefónico. |
| 800 | Conexión móvil típica. Para esta conexión, establezca como objetivo una velocidad de datos del rango de 400 a un máximo de 800 para las experiencias 3G. |
| 2000 | Conexión de escritorio de banda ancha típica. Para esta conexión, establezca como objetivo una velocidad de datos en el rango de 800 a 2000 Kbps, con la mayoría de objetivos que promedien entre 1200 y 1500 Kbps. |
| 5000 | Conexión de banda ancha típica. No se recomienda codificar en este rango superior porque la entrega de vídeo a esta velocidad no está disponible para la mayoría de los consumidores. |

### Resolución {#resolution}

**** La resolución describe la altura y la anchura de un archivo de vídeo en píxeles. La mayoría de los vídeos de origen se almacenan a alta resolución (por ejemplo, 1920 x 1080). Para fines de flujo continuo, el vídeo de origen se comprime a una resolución más pequeña (640 x 480 o más pequeña).

La resolución y la velocidad de datos son dos factores integrados que determinan la calidad del vídeo. Para mantener la misma calidad de vídeo, cuanto mayor sea el número de píxeles en un archivo de vídeo (mayor es la resolución), mayor será la velocidad de datos. Por ejemplo, considere el número de píxeles por fotograma en una resolución de 320 x 240 y un archivo de vídeo de resolución de 640 x 480:

| Resolución | Píxeles por fotograma |
|--- |--- |
| 320 x 240 | 76.800 |
| 640 x 480 | 307.200 |

El archivo de 640 x 480 tiene cuatro veces más píxeles por fotograma. Para lograr la misma velocidad de datos para estas dos resoluciones de ejemplo, se aplica cuatro veces la compresión al archivo de 640 x 480, lo que puede reducir la calidad del vídeo. Por lo tanto, una velocidad de datos de vídeo de 250 Kbps produce una visualización de alta calidad a una resolución de 320 x 240, pero no a una resolución de 640 x 480.

En general, cuanto mayor sea la velocidad de datos que utilice, mejor será el aspecto del vídeo y mayor será la resolución que utilice, mayor será la velocidad de datos necesaria para mantener la calidad de visualización (en comparación con resoluciones más bajas).

Como la resolución y la velocidad de datos están vinculadas, existen dos opciones al codificar vídeo:

* Elija una velocidad de datos y, a continuación, codifique con la resolución más alta que se muestre bien a la velocidad de datos elegida.
* Elija una resolución y, a continuación, codifique a la velocidad de datos necesaria para lograr vídeo de alta calidad en la resolución que elija.

Cuando elija (o cree) un ajuste preestablecido de codificación de vídeo para el archivo de vídeo maestro, utilice esta tabla para dirigirse a la resolución correcta:

| Resolución | Altura (píxeles) | Tamaño de la pantalla |
|--- |--- |--- |
| 240p | 240 | Pantalla pequeña |
| 300p | 300 | Pantalla pequeña normalmente para dispositivos móviles |
| 360p | 360 | Pantalla pequeña |
| 480p | 480 | Pantalla media |
| 720p | 720 | Pantalla grande |
| 1080p | 1080 | Pantalla grande de alta definición |

### Fps (fotogramas por segundo) {#fps-frames-per-second}

En los Estados Unidos y Japón, la mayoría de los vídeos se graban a 29,97 fotogramas por segundo (fps); en Europa, la mayor parte del vídeo se toma a 25 fps. La película es filmada a 24 fps.

Elija un ajuste preestablecido de codificación de vídeo que coincida con la velocidad de fps del archivo de vídeo maestro. Por ejemplo, si el vídeo maestro es de 25 fps, elija un ajuste preestablecido de codificación con 25 fps. De forma predeterminada, toda la codificación personalizada utiliza el fps del archivo de vídeo maestro. Por este motivo, no es necesario especificar explícitamente la configuración de fps al crear un ajuste preestablecido de codificación de vídeo.

### Dimensiones de codificación de vídeo {#video-encoding-dimensions}

Para obtener resultados óptimos, seleccione dimensiones de codificación de modo que el vídeo de origen sea un múltiplo completo de todos los vídeos codificados.

Para calcular esta proporción, se divide el ancho de origen por el ancho codificado para obtener la relación de ancho. A continuación, se divide la altura de origen por la altura codificada para obtener la relación de altura.

Si la proporción resultante es un número entero, significa que el vídeo se escala de forma óptima. Si la proporción resultante no es un número entero, afecta a la calidad del vídeo dejando artefactos de píxeles sobrantes en la pantalla. Este efecto es más visible cuando el vídeo tiene texto.

Por ejemplo, suponga que el vídeo de origen es de 1920 x 1080. En la tabla siguiente, los tres vídeos codificados proporcionan la configuración de codificación óptima para su uso.

<table> 
 <tbody> 
  <tr> 
   <th><p>Tipo de vídeo</p> </th> 
   <th><p>Anchura x Altura</p> </th> 
   <th><p>Proporción de anchura</p> </th> 
   <th><p>Proporción de altura</p> </th> 
  </tr>
  <tr> 
   <td><p>Origen</p> </td> 
   <td><p>1920x1080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### Formato de archivo de vídeo codificado {#encoded-video-file-format}

Dynamic Media recomienda utilizar ajustes preestablecidos de codificación de vídeo MP4 H.264. Dado que los archivos MP4 utilizan el códec de vídeo H.264, proporcionan vídeo de alta calidad pero en un tamaño de archivo comprimido.

## Publicación de vídeos en YouTube {#publishing-videos-to-youtube}

Puede publicar recursos de vídeo locales AEM directamente en un canal de YouTube que haya creado anteriormente.

Para publicar recursos de vídeo en YouTube, configure AEM Assets con etiquetas. Estas etiquetas se asocian a un canal de YouTube. Si la etiqueta de un recurso de vídeo coincide con la etiqueta de un canal de YouTube, el vídeo se publica en YouTube. Si el recurso de vídeo no tiene una etiqueta, no se publica en YouTube.

La publicación en YouTube evita el sistema de perfiles de procesamiento en AEM y, por lo tanto, también en el perfil de codificación de vídeo. Esto se produce porque YouTube tiene su propia codificación, por lo que no es necesario un perfil de procesamiento de vídeo. Sin embargo, en la mayoría de los casos, se espera que sus recursos de vídeo ya hayan pasado por un perfil de procesamiento de vídeo. Al omitir el perfil de procesamiento de vídeo y publicar directamente en YouTube, solo significa que el recurso de vídeo en AEM recurso no obtiene una miniatura visible. También significa que si se ejecuta en modo de ejecución dinámica de medios, los vídeos que no están codificados no funcionarán con ninguno de los tipos de recursos de Dynamic Media.

La publicación de recursos de vídeo en servidores de YouTube implica completar las siguientes tareas para garantizar una autenticación segura de servidor a servidor con YouTube:

1. [Configuración de Google Cloud](#configuring-google-cloud-settings)
1. [Creación de un canal de YouTube](#creating-a-youtube-channel)
1. [Agregar etiquetas para su publicación](#adding-tags-for-publishing)
1. [Habilitar el agente de replicación de YouTube Publish](#enabling-the-youtube-publish-replication-agent)
1. [Configuración de YouTube en AEM](#setting-up-youtube-in-aem)
1. [(Opcional) Automatice la configuración de las propiedades predeterminadas de YouTube para los vídeos cargados](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publicación de vídeos en el canal de YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Opcional) Verifique el vídeo publicado en YouTube](video.md#optional-verifying-the-published-video-on-youtube)
1. [Vincule las URL de YouTube a su aplicación web](#linking-youtube-urls-to-your-web-application)

También puede [cancelar la publicación de vídeos para eliminarlos de YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Configurar las opciones de Google Cloud {#configuring-google-cloud-settings}

Para publicar en YouTube, necesita una cuenta de Google. Si tiene una cuenta de GMAIL, ya tiene una cuenta de Google. Si no tiene una cuenta de Google, puede crearla fácilmente. Necesita la cuenta porque necesita credenciales para publicar recursos de vídeo en YouTube. Si ya ha creado una cuenta, omita esta tarea y continúe con [Creación de un canal de YouTube](#creating-a-youtube-channel).

>[!NOTE]
>
>Los siguientes pasos eran precisos en el momento de escribir este artículo. Sin embargo, Google actualiza periódicamente sus sitios web sin previo aviso. Como tal, estos pasos pueden ser ligeramente diferentes.

**Para configurar la configuración de Google Cloud:**

1. Cree una nueva cuenta de Google.

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Si ya tiene una cuenta de Google, vaya al paso siguiente.

1. Vaya a [https://cloud.google.com/](https://cloud.google.com/).
1. En la página Plataforma de Google Cloud, cerca de la parte superior, pulse **[!UICONTROL Consola]**. Puede que necesite **Iniciar sesión** con sus credenciales de cuenta de Google.
1. En la página **[!UICONTROL Tablero]**, pulse **[!UICONTROL Crear proyecto]**.
1. En el cuadro de diálogo **[!UICONTROL Nuevo proyecto]**, introduzca un nombre de proyecto.

   Tenga en cuenta que el ID del proyecto se basa en el nombre del proyecto. Como tal, elija cuidadosamente el nombre del proyecto; no se puede cambiar una vez creada. Además, tendrá que volver a introducir el mismo ID de proyecto cuando configure YouTube en Adobe Experience Manager más adelante. Puede que desee escribir el ID del proyecto.
1. Toque **[!UICONTROL Crear]**.

1. En el **[!UICONTROL Panel]** del proyecto, en la tarjeta **[!UICONTROL Introducción]**, pulse **[!UICONTROL Habilitar API y obtenga credenciales como claves]**.
1. Cerca de la parte superior de la página **[!UICONTROL Tablero]**, pulse **[!UICONTROL Habilitar API]**.
1. En la página **[!UICONTROL Biblioteca]**, en API de YouTube, pulse **[!UICONTROL API de datos de YouTube]**.
1. Cerca de la parte superior de la página **[!UICONTROL YouTube Data API v3]**, pulse **[!UICONTROL Habilitar]** para activarla.
1. Para utilizar la API, es posible que necesite credenciales. Si es necesario, pulse **[!UICONTROL Crear credenciales]**.
1. Desde **[!UICONTROL Desde dónde va a llamar a la API?]** lista desplegable, seleccione Servidor  **[!UICONTROL web (por ejemplo, node.js, Tomcat)]**.
1. En **[!UICONTROL A qué datos accederá?]** seleccione  **[!UICONTROL Datos de usuario]**.
1. Toque **[!UICONTROL Qué credenciales necesito?]**.
1. En el encabezado **[!UICONTROL Create an OAuth 2.0 client ID]** , introduzca un nombre único.
1. En el campo de texto bajo el encabezado **[!UICONTROL Autorized Javascript origins]** , introduzca la siguiente ruta, sustituyendo su propio dominio y número de puerto en la ruta y, a continuación, pulse **[!UICONTROL Enter]** para añadir la ruta a la lista:

   `https://<servername.domain>:<port_number>`

   Por ejemplo, `https://1a2b3c.mycompany.com:4321`

   **Nota**: El ejemplo de ruta anterior está diseñado únicamente con fines ilustrativos.

1. En el campo de texto bajo el encabezado **[!UICONTROL URI de redirección autorizada]** , introduzca lo siguiente, sustituyendo su propio dominio y número de puerto en la ruta, a continuación, pulse Intro para añadir la ruta a la lista:

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Por ejemplo, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Nota**: El ejemplo de ruta anterior está diseñado únicamente con fines ilustrativos.

1. Pulse **[!UICONTROL Crear ID de cliente]**.
1. En la página Credenciales , en el encabezado **[!UICONTROL Configurar la pantalla de consentimiento de OAuth 2.0]** , seleccione la dirección de Gmail que está utilizando actualmente.
1. En el campo de texto bajo el encabezado **[!UICONTROL Product name displayed to users]** , introduzca lo que desee mostrar en la pantalla de consentimiento.

   La pantalla de consentimiento se muestra al administrador de AEM cuando se autentican en YouTube; AEM se pondrá en contacto con YouTube para obtener permiso.

1. Toque **[!UICONTROL Continuar]**.
1. En el encabezado **[!UICONTROL Descargar credenciales]**, pulse **[!UICONTROL Descargar]**.
1. Guarde el archivo `client_id.json`.

   Necesitará este archivo json descargado cuando configure YouTube en Adobe Experience Manager más adelante.

1. Puntee **[!UICONTROL Listo]**.

   Ahora creará un canal de YouTube.

### Creación de un canal de YouTube {#creating-a-youtube-channel}

La publicación de vídeos en YouTube requiere que tenga uno o más canales. Si ya ha creado un canal de YouTube, puede omitir esta tarea y ir a **Añadir etiquetas para publicar**.

>[!CAUTION]
>
>Asegúrese de que ya ha configurado uno o varios canales en YouTube &amp;ast;before&amp;ast; los canales se agregan en Configuración de YouTube en AEM (consulte [Configuración de YouTube en AEM](#setting-up-youtube-in-aem) más adelante). Si no lo hace, no se le avisará de que no hay canales existentes. Sin embargo, la autenticación de Google se sigue produciendo cuando se agrega un canal, pero no hay opción de elegir el canal al que se envía el vídeo.

**Para crear un canal de YouTube:**

1. Vaya a [https://www.youtube.com](https://www.youtube.com/) e inicie sesión con sus credenciales de cuenta de Google.
1. En la esquina superior derecha de la página de YouTube, pulse la imagen de perfil (también puede aparecer como una letra dentro de un círculo de color sólido) y, a continuación, pulse **[!UICONTROL Configuración de YouTube]** (icono de engranaje redondo).
1. En la página **[!UICONTROL Información general]**, en el encabezado **[!UICONTROL Funciones adicionales]**, pulse **[!UICONTROL Ver todos mis canales o cree un nuevo canal]**.
1. En la página **[!UICONTROL Canales]**, pulse **[!UICONTROL Crear un nuevo canal]**.
1. En la página **[!UICONTROL Cuenta de marca]**, en el campo **[!UICONTROL Nombre de cuenta de marca]**, introduzca un nombre comercial o cualquier otro nombre de canal que elija donde desea publicar los recursos de vídeo y, a continuación, pulse **[!UICONTROL Crear]**.

   Recuerde el nombre que introduce aquí porque tendrá que introducirlo de nuevo cuando configure YouTube en AEM.

1. (Opcional) Si es necesario, agregue más canales.

   Ahora agregará etiquetas para su publicación.

### Agregar etiquetas para su publicación {#adding-tags-for-publishing}

Para publicar en YouTube sus vídeos, AEM asocia etiquetas a uno o varios canales de YouTube. Para agregar etiquetas para la publicación, consulte [Administración de etiquetas](/help/sites-administering/tags.md).

O bien, si desea utilizar las etiquetas predeterminadas en AEM, puede omitir esta tarea y ir a [Activación del agente de replicación de YouTube Publish](#enabling-the-youtube-publish-replication-agent).

### Habilitar el agente de replicación de YouTube Publish {#enabling-the-youtube-publish-replication-agent}

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Implementación > Replicación > Agentes en Author]**.
1. En la página **[!UICONTROL Agentes del autor]**, pulse **[!UICONTROL YouTube Publish (youtube)]**.
1. En la barra de herramientas, a la derecha de Configuración, pulse **[!UICONTROL Editar]**.
1. Seleccione la casilla **[!UICONTROL Enabled]** para activar el agente de replicación.
1. pulse **[!UICONTROL Aceptar]**.

   Ahora configurará YouTube en AEM.

### Configuración de YouTube en AEM {#setting-up-youtube-in-aem}

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Implementación > Cloud Services]**.
1. En el encabezado **[!UICONTROL Servicios de terceros]**, en YouTube, pulse **[!UICONTROL Configurar ahora]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]**, introduzca un título (obligatorio) y un nombre (opcional) en los campos correspondientes.
1. Toque **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Configuración de cuenta de YouTube]**, en el campo **[!UICONTROL Nombre de aplicación]**, introduzca el ID del proyecto de Google.

   Ha especificado el ID del proyecto al configurar Google Cloud por primera vez.

   Deje abierto el cuadro de diálogo **[!UICONTROL Configuración de cuenta de YouTube]**; regresarás a él en un momento.

1. Con un editor de texto sin formato, abra el archivo JSON que descargó y guardó anteriormente en la tarea Configuración de Google Cloud .
1. Seleccione y copie todo el texto JSON.
1. Vuelva al cuadro de diálogo **[!UICONTROL Configuración de cuenta de YouTube]**. En el campo **[!UICONTROL Configuración JSON]**, pegue el texto JSON.
1. Pulse **[!UICONTROL Aceptar]**.

   Ahora configurará los canales de YouTube en AEM.

1. A la derecha de **[!UICONTROL Canales disponibles]**, pulse **[!UICONTROL +]** (icono del signo “más”).
1. En el cuadro de diálogo **[!UICONTROL Configuración de canal de YouTube]**, en el campo **[!UICONTROL Título]**, introduzca el nombre del canal que creó en la tarea **C[!UICONTROL Creación de un canal de YouTube]** anterior.

   Si lo desea, puede agregar una descripción.

1. Pulse **[!UICONTROL Aceptar]**.
1. Se muestra la autenticación de YouTube/Google. Si aún no ha iniciado sesión en la cuenta de Google Cloud, omita este paso.

   * Introduzca el nombre de usuario y la contraseña de Google asociados al ID del proyecto de Google y el texto JSON anterior.
   * Dependiendo de cuántos canales haya visto su cuenta, verá dos o más artículos. Seleccione un canal. No seleccione la dirección de correo electrónico.
   * En la página siguiente, pulse **[!UICONTROL Accept]** para permitir el acceso a este canal.

1. Toque **[!UICONTROL Permitir]**.

   Ahora configurará las etiquetas para su publicación.

1. **Configuración de etiquetas para publicación** : en la página  **[!UICONTROL Cloud Services >]** YouTube, pulse el icono  **** icono para editar la lista de etiquetas que desea utilizar.
1. Pulse el icono de lista desplegable (acento circunflejo invertido) para mostrar la lista de etiquetas disponibles en AEM.
1. Toque una o más etiquetas para agregarlas.

   Para eliminar una etiqueta que haya agregado, seleccione la etiqueta y pulse **[!UICONTROL X]**.

1. Cuando haya terminado de agregar las etiquetas que desee, pulse **[!UICONTROL Aceptar]**.

   Ahora publica vídeos en su canal de YouTube.

### (Opcional) Automatice la configuración de las propiedades predeterminadas de YouTube para los vídeos cargados {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Puede automatizar la configuración de las propiedades de YouTube al cargar los vídeos. Esto se logra creando un perfil de procesamiento de metadatos en AEM.

Para crear el perfil de procesamiento de metadatos, en primer lugar copiará valores de los campos **[!UICONTROL Etiqueta de campo]**, **[!UICONTROL Asignar a propiedad]** y **[!UICONTROL Opciones]**, todos se encuentran en Esquemas de metadatos para vídeo. A continuación, creará su perfil de procesamiento de metadatos de vídeo de YouTube agregándole esos valores.

**Para automatizar opcionalmente la configuración de las propiedades predeterminadas de YouTube para los vídeos cargados:**

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Esquemas de metadatos]**.
1. Toque **[!UICONTROL default]**. (No agregue una marca de verificación al cuadro de selección a la izquierda de &quot;predeterminado&quot;).
1. En la página **[!UICONTROL default]**, marque la casilla a la izquierda de **[!UICONTROL video]** y, a continuación, pulse **[!UICONTROL Editar]**.
1. En la página **[!UICONTROL Editor de esquemas de metadatos]**, pulse la pestaña **[!UICONTROL Avanzado]**.
1. Bajo el encabezado Publicación de YouTube, pulse **[!UICONTROL Categoría de YouTube]**. (No pulse la lista desplegable Categoría de YouTube ).
1. A la derecha de la página, en la pestaña **[!UICONTROL Settings]**, haga lo siguiente:

   * En el campo de texto **[!UICONTROL Field Label]** , seleccione y copie el valor.

      Pegue el valor copiado en un editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

   * En el campo de texto **[!UICONTROL Map to property]** , seleccione y copie el valor.

      Pegue el valor copiado en el editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

   * En **[!UICONTROL Opciones]**, seleccione y copie el valor predeterminado que desee usar (como Personas y blogs o Ciencia y tecnología).

      Pegue el valor copiado en el editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

1. En el encabezado Publicación de YouTube , pulse **[!UICONTROL Privacidad de YouTube]**. (No pulse la lista desplegable Privacidad de YouTube ).
1. A la derecha de la página, en la pestaña **[!UICONTROL Settings]**, haga lo siguiente:

   * En el campo de texto **[!UICONTROL Field Label]** , seleccione y copie el valor.

      Pegue el valor copiado en un editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

   * En el campo de texto **[!UICONTROL Map to property]** , seleccione y copie el valor.

      Pegue el valor copiado en el editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

   * En **[!UICONTROL Opciones]**, seleccione y copie el valor predeterminado que desee utilizar. Tenga en cuenta que las opciones se agrupan en pares de dos. El campo inferior del par es el valor predeterminado que desea copiar, como público, no enumerado o privado.

      Pegue el valor copiado en el editor de texto abierto. Necesitará este valor más adelante cuando cree su perfil de procesamiento de metadatos. Deje abierto el editor de texto.

1. Cerca de la esquina superior derecha de la página **[!UICONTROL Editor de esquemas de metadatos]**, pulse **[!UICONTROL Cancelar]**.
1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas > Assets > Perfiles de metadatos]**.

1. En la página **[!UICONTROL Perfiles de metadatos]**, cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Crear]**. En el cuadro de diálogo **[!UICONTROL Agregar perfil de metadatos]**, en el campo de texto **[!UICONTROL Título del perfil]**, introduzca el nombre `YouTube Video`.
1. En la página **[!UICONTROL Editor de perfiles de metadatos]**, pulse la pestaña **[!UICONTROL Avanzar]**.
1. Agregue al perfil los valores de publicación de YouTube copiados haciendo lo siguiente:

   * En el lado derecho de la página, pulse la pestaña **[!UICONTROL Generar formulario]**.
   * Arrastre el componente etiquetado **[!UICONTROL Encabezado de sección]** a la izquierda y suéltelo en el área del formulario.
   * Toque **[!UICONTROL Etiqueta de campo]** para seleccionar el componente.
   * A la derecha de la página, en la pestaña **[!UICONTROL Settings]**, en el campo de texto **[!UICONTROL Field Label]**, introduzca `YouTube Publishing`.
   * Pulse la pestaña **[!UICONTROL Generar formulario]**, arrastre el componente etiquetado **[!UICONTROL Texto de una sola línea]** y suéltelo en el encabezado **[!UICONTROL Publicación de YouTube]** que acaba de crear.
   * Toque **[!UICONTROL Etiqueta de campo]** para seleccionar el componente.
   * En el lado derecho de la página, en la pestaña **[!UICONTROL Settings]**, pegue los valores **[!UICONTROL YouTube Publishing]** (**[!UICONTROL Field Label]** y **[!UICONTROL Map to property]** valor) que ha copiado anteriormente en sus respectivos campos del formulario. Pegue el valor **[!UICONTROL Choices]** en el campo **[!UICONTROL Valor predeterminado]**.

1. Agregue al perfil los valores de privacidad de YouTube copiados haciendo lo siguiente:

   * En el lado derecho de la página, pulse la pestaña **[!UICONTROL Generar formulario]**.
   * Arrastre el componente etiquetado **[!UICONTROL Encabezado de sección]** a la izquierda y suéltelo en el área del formulario.
   * Toque **[!UICONTROL Etiqueta de campo]** para seleccionar el componente.
   * A la derecha de la página, en la ficha Configuración , en el campo de texto Etiqueta de campo , introduzca `YouTube Privacy`.
   * Pulse la pestaña **[!UICONTROL Generar formulario]**, arrastre el componente etiquetado **[!UICONTROL Texto de una sola línea]** y suéltelo en el encabezado **[!UICONTROL Privacidad de YouTube]** que acaba de crear.
   * Toque **[!UICONTROL Etiqueta de campo]** para seleccionar el componente.
   * En el lado derecho de la página, en la pestaña **[!UICONTROL Settings]**, pegue los valores **[!UICONTROL YouTube Publishing]** (**[!UICONTROL Field Label]** y **[!UICONTROL Map to property]** valor) que ha copiado anteriormente en sus respectivos campos del formulario. Pegue el valor **[!UICONTROL Choices]** en el campo **[!UICONTROL Valor predeterminado]**.

1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**.
1. Aplique el perfil de metadatos de publicación de YouTube a las carpetas donde vaya a cargar los vídeos. Deberá tener configurados tanto el perfil de metadatos como el perfil de vídeo.

   Consulte [Perfiles de metadatos](metadata-profiles.md) y [Perfiles de vídeo](video-profiles.md).

### Publicación de vídeos en el canal de YouTube {#publishing-videos-to-your-youtube-channel}

Ahora asocia las etiquetas que agregó anteriormente a los recursos de vídeo. Este proceso permite AEM qué recursos publicar en el canal de YouTube.

Para publicar contenido de YouTube, AEM utiliza el flujo de trabajo **[!UICONTROL Publicar en YouTube]** , que permite supervisar el progreso y ver la información de los errores.
Consulte [Supervisión de la codificación de vídeo y progreso de publicación en YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Para publicar vídeos en el canal de YouTube:**

1. En AEM, vaya a un recurso de vídeo que desee publicar en el canal de YouTube.
1. Seleccione el recurso de vídeo.

   Independientemente del recurso de vídeo que seleccione (como el vídeo de origen original o una representación codificada de él), el vídeo de origen original siempre se carga.

1. En la barra de herramientas, pulse **[!UICONTROL Propiedades]**.
1. En la pestaña **[!UICONTROL Básico]**, en el encabezado Metadatos, pulse **[!UICONTROL Examinar]** a la derecha del campo **[!UICONTROL Etiquetas]**.
1. En la página **[!UICONTROL Seleccionar etiquetas]**, vaya a las etiquetas que desee utilizar y, a continuación, seleccione una o varias etiquetas.
1. En la esquina superior derecha de la página, pulse el icono **[!UICONTROL Confirm]**.
1. En la esquina superior derecha de la página de propiedades del vídeo, pulse **[!UICONTROL Guardar]**.
1. En la barra de herramientas, pulse **[!UICONTROL Publicar > Publicar]**.

   Si lo desea, puede verificar el vídeo publicado en su canal de YouTube.

### (Opcional) Verifique el vídeo publicado en YouTube {#optional-verifying-the-published-video-on-youtube}

Puede supervisar el progreso de la publicación de YouTube (o cancelar la publicación).

Consulte [Supervisión de la codificación de vídeo y progreso de publicación en YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Los tiempos de publicación pueden variar en gran medida en función de numerosos factores que incluyen el formato del vídeo maestro, el tamaño del archivo y el tráfico de carga. El proceso de publicación puede tardar entre unos minutos y varias horas. Además, tenga en cuenta que los formatos de mayor resolución se procesan mucho más lentamente. Por ejemplo, 720p y 1080p tardan mucho más en aparecer que 480p.

Después de ocho horas si todavía ve un mensaje de estado que dice **[!UICONTROL Cargado (procesado, espere)]**, intente eliminar el vídeo de nuestro sitio y cargarlo de nuevo.

### Vincule las URL de YouTube a su aplicación web {#linking-youtube-urls-to-your-web-application}

Puede obtener una cadena URL de YouTube que Dynamic Media genera después de publicar el vídeo. Cuando copia la URL de YouTube, esta se coloca en el Portapapeles para que pueda pegarla según sea necesario en las páginas de su sitio web o aplicación.

La URL de YouTube no está disponible para copiarse hasta que no haya publicado el recurso de vídeo en YouTube.

**Para vincular URL de YouTube a su aplicación web:**

1. Vaya al recurso de vídeo *publicado* de YouTube cuya URL desea copiar y, a continuación, selecciónelo.

   Recuerde que las direcciones URL de YouTube solo están disponibles para copiar *después* primero ha publicado *los recursos de vídeo* en YouTube.

1. En la barra de herramientas, pulse **[!UICONTROL Propiedades]**.
1. Pulse la pestaña **[!UICONTROL Advanced]**.
1. En el encabezado **[!UICONTROL Publicación de YouTube]**, en la lista **[!UICONTROL URL de YouTube]**, seleccione y copie el texto de la URL en el explorador web para obtener una vista previa del recurso o agregarlo a la página de contenido web.

### Cancelar la publicación de vídeos para eliminarlos de YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Cuando se cancela la publicación de un recurso de vídeo en AEM, el vídeo se elimina de YouTube.

>[!CAUTION]
>
>Si elimina un vídeo directamente desde YouTube, AEM desconoce y continúa comportándose como si el vídeo aún se hubiera publicado en YouTube. Cancele siempre la publicación de un recurso de vídeo de YouTube mediante AEM.

Para eliminar contenido de YouTube, AEM utiliza el flujo de trabajo **[!UICONTROL Cancelar publicación de YouTube]** , que permite supervisar el progreso y ver la información de los errores.
Consulte [Supervisión de la codificación de vídeo y progreso de publicación en YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Para cancelar la publicación de vídeos para eliminarlos de YouTube:**

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas]** > **[!UICONTROL Recursos]**.
1. Vaya a los recursos de vídeo que desea cancelar la publicación desde el canal de YouTube.
1. En un modo de selección de recursos, seleccione uno o varios recursos de vídeo publicados.
1. En la barra de herramientas, pulse **[!UICONTROL Cancelar publicación]** > **[!UICONTROL Cancelar publicación]**.

## Monitorización de la codificación de vídeo y del progreso de publicación de YouTube {#monitoring-video-encoding-and-youtube-publishing-progress}

Cuando se carga un nuevo vídeo en una carpeta que tiene codificación de vídeo aplicada o se publica el vídeo en YouTube, se puede supervisar el progreso (o fracaso) de la publicación de YouTube o codificación de vídeo de varias formas. El progreso real de publicación de YouTube solo está disponible a través de los registros, pero si falla o tiene éxito se enumera de maneras adicionales descritas en el siguiente procedimiento. Además, puede recibir notificaciones por correo electrónico cuando un flujo de trabajo de publicación de YouTube o una codificación de vídeo se completen o se interrumpa.

### Monitorización del progreso {#monitoring-progress}

Para monitorizar el progreso (incluida la codificación/publicación fallida de YouTube):

1. Vea el progreso de la codificación de vídeo en la carpeta de recursos:

   * En **[!UICONTROL Vista de tarjeta]**, el progreso de la codificación de vídeo se muestra en el recurso por porcentaje. Si hay un error, esta información también se muestra en el recurso.

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * En **[!UICONTROL Vista de lista]**, el progreso de codificación de vídeo se muestra en la columna **[!UICONTROL Estado de procesamiento]**. Si hay un error, este mensaje se muestra en la misma columna.

      ![chlimage_1-430](assets/chlimage_1-430.png)

      Esta columna no se muestra de forma predeterminada. Para habilitar la columna, seleccione **[!UICONTROL Ver configuración]** en el menú desplegable **[!UICONTROL Vistas]**, añada la columna **[!UICONTROL Estado de procesamiento]** y pulse **[!UICONTROL Actualizar]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. Vea el progreso en los detalles del recurso. Cuando toque un recurso, abra el menú desplegable y seleccione **[!UICONTROL Línea de tiempo]**. Para reducirlo a actividades de flujo de trabajo como codificación o publicación en YouTube, seleccione **[!UICONTROL Flujos de trabajo]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Cualquier información de flujo de trabajo, como la codificación, se muestra en la cronología. Para la publicación en YouTube, la línea de tiempo **[!UICONTROL Workflow]** también incluye el nombre del canal de YouTube y la URL de vídeo de YouTube. Además, puede ver cualquier notificación de error en la cronología **[!UICONTROL Workflow]**.

   >[!NOTE]
   >
   >Podría llevar mucho tiempo que los mensajes de error/error finalmente se registren debido a varias configuraciones de flujo de trabajo en **[!UICONTROL reintentos]**, **[!UICONTROL retraso de reintentos]** y **[!UICONTROL tiempo de espera]** de [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), por ejemplo:
   >
   >* Configuración de cola de trabajos Apache Sling
   >* Controlador de trabajos de proceso externo de flujo de trabajo de Granite de Adobe
   >* Cola de tiempo de espera de flujo de trabajo de Granite

   > 
   >Puede ajustar las propiedades de **[!UICONTROL reintentos]**, **[!UICONTROL reintentos de demora]** y **[!UICONTROL tiempo de espera]** en estas configuraciones.

1. Para los flujos de trabajo en curso, consulte **Instancias de flujo de trabajo** disponibles en **[!UICONTROL Herramientas > Flujo de trabajo > Instancias]**.

   >[!NOTE]
   >
   >Es posible que necesite derechos administrativos para acceder al menú **[!UICONTROL Tools]**.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Seleccione la instancia y pulse **[!UICONTROL Abrir historial]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   Desde el área **[!UICONTROL Workflow Instances]** también puede suspender, finalizar o cambiar el nombre de los flujos de trabajo. Consulte [Administración de flujos de trabajo](/help/sites-administering/workflows-administering.md) para obtener más información.

1. Para los trabajos con errores, consulte **Errores de flujo de trabajo** disponibles en **[!UICONTROL Herramientas > Flujo de trabajo > Errores]**. El **[!UICONTROL error de flujo de trabajo]** muestra todas las actividades de flujo de trabajo con errores.

   >[!NOTE]
   >
   >Es posible que necesite derechos administrativos para acceder al menú **[!UICONTROL Tools]**.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Podría llevar mucho tiempo que el mensaje de error finalmente se registre debido a varias configuraciones de flujo de trabajo en **[!UICONTROL reintentos]**, **[!UICONTROL reintentos de demora]** y **[!UICONTROL tiempo de espera]** de [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), por ejemplo:
   >
   >* Configuración de cola de trabajos Apache Sling
   >* Controlador de trabajos de proceso externo de flujo de trabajo de Granite de Adobe
   >* Cola de tiempo de espera de flujo de trabajo de Granite

   >
   >Puede ajustar las propiedades de **[!UICONTROL reintentos]**, **[!UICONTROL reintentos de demora]** y **[!UICONTROL tiempo de espera]** en estas configuraciones.

1. Para los flujos de trabajo completados, consulte **[!UICONTROL Archivo de flujo de trabajo]** disponible en **[!UICONTROL Herramientas > Flujo de trabajo > Archivar]**. El **[!UICONTROL archivo de flujo de trabajo]** enumera todas las actividades de flujo de trabajo completadas.

   Es posible que necesite derechos administrativos para acceder al menú **[!UICONTROL Tools]**.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. Puede recibir notificaciones por correo electrónico sobre los trabajos de flujo de trabajo anulados o fallidos. Un administrador puede configurar estas notificaciones por correo electrónico.
Consulte [Configuración de notificaciones por correo electrónico](#configuring-e-mail-notifications).

#### Configuración de notificaciones por correo electrónico {#configuring-e-mail-notifications}

Es posible que necesite derechos administrativos para acceder al menú **[!UICONTROL Tools]**.

La configuración de la notificación depende de si desea que se envíen notificaciones para trabajos de codificación o trabajos de publicación de YouTube:

* Para los trabajos de codificación, puede acceder a la página de configuración de todas las notificaciones de correo electrónico AEM flujo de trabajo en **[!UICONTROL Tools > Operations > Web Console]** y buscando **[!UICONTROL Day CQ Workflow Email Notification Service]**. Consulte [Configuración de la notificación de correo electrónico en AEM](/help/sites-administering/notification.md). Puede seleccionar o desmarcar las casillas de verificación de **[!UICONTROL Notificar al anular]** o **[!UICONTROL Notificar al completar]** según corresponda.

* Para los trabajos de publicación de YouTube, haga lo siguiente:

1. En AEM, seleccione **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Seleccione el flujo de trabajo **[!UICONTROL Publicar en YouTube]** y, a continuación, pulse **[!UICONTROL Editar]**.
1. Haga clic con el botón derecho en el paso del flujo de trabajo **[!UICONTROL YouTube Upload]** y, a continuación, pulse **[!UICONTROL Editar]**.
1. Pulse la pestaña **[!UICONTROL Argumento]s**.
1. Puede seleccionar o desmarcar las siguientes casillas de verificación:

   * **[!UICONTROL Inicio de publicación]**
   * **[!UICONTROL Error durante la publicación]**
   * **[!UICONTROL Finalización de la publicación]**, que incluye información sobre canales y direcciones URL

   Si desactiva una casilla de verificación, no recibirá la notificación de correo electrónico especificada del flujo de trabajo de YouTube Publish.

   >[!NOTE]
   >
   >Estos correos electrónicos son específicos de YouTube y se suman a las notificaciones de correo electrónico genéricas del flujo de trabajo. Como resultado, puede recibir dos conjuntos de notificaciones por correo electrónico: la notificación genérica disponible en el **Day CQ Workflow Email Notification Service** y una específica de YouTube según la configuración.

## Ver informes de vídeo {#viewing-video-reports}

Los informes de vídeo están disponibles cuando ejecuta Dynamic Media - Modo híbrido; los informes no están disponibles cuando se ejecuta el modo Dynamic Media - Scene7 .

Los informes de vídeo muestran varias métricas agregadas durante un período de tiempo específico para ayudarle a supervisar que *los vídeos individuales y agregados publicados están teniendo el rendimiento esperado. Los siguientes datos de métricas principales se agregan para todos los vídeos publicados en todo el sitio web:

* Inicios de vídeo
* Tasa de finalización
* Promedio de tiempo en vídeo
* Tiempo total en vídeo
* Vídeos por visita

También se muestra una tabla de todos los vídeos *publicados* para que pueda rastrear los vídeos más vistos del sitio web en función del número total de inicios de vídeo.

Al tocar un nombre de vídeo en la lista, se muestra el informe de retención de audiencia (desplegable) del vídeo en forma de gráfico de líneas. El gráfico muestra el número de vistas durante un momento determinado de la reproducción del vídeo. Cuando reproduce el vídeo, la barra vertical realiza el seguimiento en sincronización con el indicador de tiempo del reproductor. Las pérdidas en los datos del gráfico de líneas indican de dónde sale la audiencia del desinterés.

Si el vídeo se ha codificado fuera de Adobe Experience Manager Dynamic Media, el gráfico de retención de audiencia (desplegable) y los datos de Porcentaje de reproducción de la tabla no están disponibles.

Consulte también [Configuración de Cloud Services de Dynamic Media](/help/assets/config-dynamic.md).

>[!NOTE]
>
>El seguimiento y los informes de datos se basan exclusivamente en el uso del propio reproductor de vídeo de Dynamic Media y el ajuste preestablecido de reproductor de vídeo asociado. Como tal, no puede rastrear vídeos que se reproducen mediante otros reproductores de vídeo ni crear informes de ellos.

De forma predeterminada, la primera vez que se introduce Informes de vídeo, el informe muestra datos de vídeo a partir del primer mes del mes actual y termina con la fecha del mes actual. Sin embargo, puede anular el intervalo de fechas predeterminado especificando su propio intervalo de fechas. La próxima vez que introduzca Informes de vídeo, se utilizará el intervalo de fechas especificado.

Para que los informes de vídeo funcionen correctamente, se crea automáticamente un ID de grupo de informes cuando se configuran los Cloud Services de Dynamic Media. Al mismo tiempo, la ID del grupo de informes se envía al servidor de publicación, de modo que esté disponible para la función Copiar URL cuando se previsualizan los recursos. Sin embargo, esto requiere que el servidor de publicación ya esté configurado. Si el servidor de publicación no está configurado, aún puede publicar para ver el informe de vídeo; sin embargo, deberá volver a la configuración de Dynamic Media Cloud y pulsar **Aceptar**.

**Para ver informes de vídeo:**

1. En la esquina superior izquierda de AEM, pulse el logotipo de AEM y, a continuación, en el carril izquierdo, pulse **[!UICONTROL Herramientas]** > **[!UICONTROL Recursos]** > **[!UICONTROL Informes de vídeo]**.
1. En la página Informes de vídeo , realice una de las acciones siguientes:

   * Cerca de la esquina superior derecha, pulse el icono **[!UICONTROL Actualizar informe de vídeo]**.

      Solo es necesario utilizar Actualizar si la fecha de finalización del informe es el día actual. Esto le garantiza ver el seguimiento de vídeo que se ha producido desde la última vez que ejecutó el informe.

   * Cerca de la esquina superior derecha, pulse el icono **[!UICONTROL Selector de fecha]**.

      Especifique el intervalo de fechas de inicio y finalización para el que desee usar datos de vídeo y, a continuación, pulse **[!UICONTROL Ejecutar informe]**.
   El cuadro de grupo **[!UICONTROL Métricas principales]** identifica varias medidas agregadas para todos los vídeos *publicados* de su sitio.

1. En la tabla que enumera los vídeos más publicados, pulse un nombre de vídeo para reproducir el vídeo y también consulte el informe de retención de audiencia (desplegable) del vídeo.

### Ver informes de vídeo basados en un visor de vídeo creado con el SDK del visor HTML5 de Dynamic Media {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Si utiliza un visualizador de vídeo incorporado proporcionado por Dynamic Media o si ha creado un ajuste preestablecido de visualizador personalizado basado en un visualizador de vídeo incorporado, no se requiere ningún paso adicional para ver los informes de vídeo. Sin embargo, si ha creado su propio visor de vídeo basado en la API del SDK del visor HTML5, siga los siguientes pasos para asegurarse de que el visor de vídeo envía eventos de seguimiento a los informes de vídeo de Dynamic Media.

Utilice la [Guía de referencia de visores de Dynamic Media de Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html) y la [API del SDK de visor HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) para crear sus propios visores de vídeo.

Para ver informes de vídeo basados en un visor de vídeo creado con la API del SDK del visor HTML5:

1. Vaya a cualquier recurso de vídeo publicado.
1. Junto a la esquina superior izquierda de la página del recurso, en la lista desplegable, seleccione **[!UICONTROL Visualizadores]**.
1. Seleccione cualquier ajuste preestablecido de visualizador de vídeo y copie el código incrustado.
1. En el código incrustado, busque la línea con lo siguiente:

   `videoViewer.setParam("config2", "<value>");`

   El parámetro `config2` habilita el seguimiento en los visores HTML5. También es un ajuste preestablecido específico de la empresa que contiene la información de configuración para los informes de vídeo y para las configuraciones de Adobe Analytics específicas del cliente.

   El valor correcto del parámetro config2 se encuentra tanto en el **[!UICONTROL código incrustado]** como en la función de copia de **[!UICONTROL URL]**. En la URL del comando copiar **[!UICONTROL URL]**, el parámetro que se busca es `&config2=<value>`. El valor es casi siempre `companypreset`, pero en algunos casos también puede ser `companypreset-1`, `companypreset-2`, etc.

1. En el código personalizado del visor de vídeo, agregue AppMeasurementBridge .jsp a la página del visor haciendo lo siguiente:

   * En primer lugar, determine si necesita el parámetro `&preset`.

      Si el parámetro `config2` es `companypreset`, necesita *no* `&preset=parameter`.

      Si `config2` es cualquier otra cosa, establezca el parámetro preestablecido igual que el parámetro `config2`. Por ejemplo, si `config2=companypreset-2`, agregue `&param2=companypreset-2` a la URL de AppMeasurementBridge.jsp.

   * A continuación, agregue el script AppMeasurementBridge.jsp:

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Cree el componente TrackingManager haciendo lo siguiente:

   * Después de llamar a `s7sdk.Util.init();` cree una instancia de TrackingManager para rastrear eventos agregando lo siguiente:

      `var trackingManager = new s7sdk.TrackingManager();`

   * Conecte componentes a TrackingManager haciendo lo siguiente:

      En el controlador de eventos `s7sdk.Event.SDK_READY`, adjunte el componente que desee rastrear al TrackingManager.

      Por ejemplo, si el componente es `videoPlayer`, agregue

      `trackingManager.attach(videoPlayer);`

      para adjuntar el componente al trackingManager. Para rastrear varios visualizadores en una página, utilice varios componentes del administrador de seguimiento.

   * Cree el objeto AppMeasurementBridge agregando lo siguiente:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * Añada la función de seguimiento agregando lo siguiente:

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   El objeto appMeasurementBridge tiene una función de seguimiento integrada. Sin embargo, puede proporcionar su propia compatibilidad con varios sistemas de seguimiento u otra funcionalidad.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

## Agregar subtítulos a vídeo {#adding-captions-to-video}

Puede ampliar el alcance de sus vídeos a mercados globales añadiendo subtítulos a vídeos individuales o a conjuntos de vídeos adaptables. Al agregar subtítulos, evitará la necesidad de doblar el audio, o la necesidad de usar hablantes nativos para volver a grabar el audio para cada idioma diferente. El vídeo se reproduce en el idioma en que se grabó. Aparecen subtítulos en idiomas extranjeros para que personas de diferentes idiomas puedan entender la parte de audio.

Los subtítulos también permiten una buena accesibilidad al usar subtítulos optativos para personas sordas o con dificultades auditivas.

>[!NOTE]
>
>El reproductor de vídeo que utilice debe admitir la visualización de subtítulos.

Dynamic Media tiene la capacidad de convertir archivos de rótulos al formato JSON (JavaScript Object Notation). Esta conversión significa que puede incrustar el texto JSON en una página web como una transcripción oculta pero completa del vídeo. Los motores de búsqueda pueden rastrear e indexar el contenido para que los vídeos se puedan descubrir más fácilmente y proporcionar a los clientes detalles adicionales sobre el contenido del vídeo.

Consulte [Servicio de contenido estático (no de imagen)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) en la *Ayuda de Dynamic Media Image Serving and Rendering API Help* para obtener más información sobre el uso de la función JSON en una URL.

**Para agregar subtítulos o subtítulos a un vídeo:**

1. Utilice una aplicación o servicio de terceros para crear el archivo de subtítulos o subtítulos de vídeo.

   Asegúrese de que el archivo que crea sigue el estándar WebVTT (Web Video Text Tracks). La extensión del nombre de archivo del rótulo es .vtt. Puede obtener más información sobre el estándar de subtítulos WebVTT.

   Consulte [WebVTT: El formato de seguimiento de texto de vídeo web](https://dev.w3.org/html5/webvtt/).

   Existen herramientas y servicios gratuitos y premium que puede utilizar para crear archivos de subtítulos o subtítulos fuera de Dynamic Media. Por ejemplo, para crear un archivo de subtítulos de vídeo sencillo sin estilo, puede utilizar la siguiente herramienta gratuita de edición y creación de subtítulos en línea:

   [Creador de subtítulos WebVTT](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Para obtener los mejores resultados, utilice la herramienta en Internet Explorer 9 o posterior, Google Chrome o Safari.

   En la herramienta, en el campo **[!UICONTROL Enter URL of video file]** , pegue la URL copiada del archivo de vídeo y, a continuación, pulse **[!UICONTROL Load]**. Consulte [Obtención de una URL para un recurso](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) para obtener la URL del propio archivo de vídeo, que puede pegar en el campo **[!UICONTROL Introducir URL del archivo de vídeo]**. Internet Explorer, Chrome o Safari pueden reproducir el vídeo de forma predeterminada.

   Ahora siga las instrucciones en pantalla del sitio para crear y guardar el archivo WebVTT. Cuando haya terminado, copie el contenido del archivo de rótulo y péguelo en un editor de texto sin formato y guárdelo con la extensión .vtt filename .

   >[!NOTE]
   >
   >Para la compatibilidad global con subtítulos de vídeo en varios idiomas, tenga en cuenta que el estándar WebVTT requiere que cree archivos .vtt y llamadas independientes para cada idioma que desee admitir.

   Normalmente, le interesa asignar al archivo VTT de rótulo el mismo nombre que el archivo de vídeo y añadirlo a la configuración regional del idioma, como -EN, -FR o -DE, entre otros. Al hacerlo, puede ayudarle a automatizar la generación de las URL de vídeo con su sistema de administración de contenido web existente.

1. En AEM, cargue el archivo de subtítulos WebVTT en DAM.
1. Vaya al recurso de vídeo *publicado* que desea asociar al archivo de rótulo que ha cargado.

   Recuerde que las direcciones URL solo están disponibles para copiarse *después* de *publicar* los recursos por primera vez.

   Consulte [Publicación de recursos.](publishing-dynamicmedia-assets.md)

1. Realice una de las acciones siguientes:

   * Para obtener una experiencia del visor de vídeo emergente, pulse **[!UICONTROL URL]**. En el cuadro de diálogo URL, seleccione y copie la dirección URL en el portapapeles y, a continuación, pase la dirección URL a un editor de texto sencillo. Añada la URL copiada del vídeo con la siguiente sintaxis:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Observe el `,1` al final de la ruta del rótulo. Inmediatamente después de la extensión de nombre de archivo .vtt en la ruta, tiene la opción de habilitar (activar) o desactivar (desactivar) el botón de subtítulos en la barra del reproductor de vídeo configurando en `,1` o `,0`, respectivamente.

   * Para una experiencia con el visor de vídeo incrustado, pulse **[!UICONTROL Código incrustado]**. En el cuadro de diálogo Código incrustado , seleccione y copie el código incrustado en el portapapeles y, a continuación, pegue el código en un editor de texto sencillo. Añada el código incrustado copiado con la siguiente sintaxis:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Observe el `,1` al final de la ruta del rótulo. Inmediatamente después de la extensión de nombre de archivo .vtt en la ruta, tiene la opción de habilitar (activar) o desactivar (desactivar) el botón de subtítulos en la barra del reproductor de vídeo configurando en `,1` o `,0`, respectivamente.

## Agregar marcadores de capítulo a vídeo {#adding-chapter-markers-to-video}

Puede hacer que los vídeos de formulario largos sean más fáciles de ver y navegar añadiendo marcadores de capítulo a vídeos individuales o a conjuntos de vídeos adaptables. Cuando un usuario reproduce el vídeo, puede pulsar los marcadores de capítulo en la cronología del vídeo (también conocida como el depurador de vídeo) para desplazarse fácilmente a su punto de interés o para acceder inmediatamente a nuevos contenidos, demostraciones, tutoriales, etc.

>[!NOTE]
>
>El reproductor de vídeo que se utilice debe admitir el uso de marcadores de capítulo. Los reproductores de vídeo de Dynamic Media sí admiten marcadores de capítulo, pero es posible que no utilicen reproductores de vídeo de terceros.

Si lo desea, puede crear y personalizar su propio visor de vídeo con capítulos en lugar de usar un ajuste preestablecido de visualizador de vídeo. Para obtener instrucciones sobre la creación de su propio visor HTML5 con navegación por capítulos, en la API del SDK del visor HTML5 de Adobe, haga referencia al encabezado &quot;Personalización del comportamiento con modificadores&quot; en las clases `s7sdk.video.VideoPlayer` y `s7sdk.video.VideoScrubber`. Consulte la documentación [HTML5 Viewer SDK API]((https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) .

Puede crear una lista de capítulos para el vídeo de la misma manera que crea subtítulos. Es decir, se crea un archivo WebVTT. No obstante, tenga en cuenta que este archivo debe estar separado de cualquier archivo de subtítulos WebVTT que también esté utilizando; no se pueden combinar subtítulos y capítulos en un archivo WebVTT.

Puede utilizar el siguiente ejemplo como ejemplo del formato que utiliza para crear un archivo WebVTT con navegación por capítulos:

### Archivo WebVTT con navegación por capítulos de vídeo {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

En el ejemplo anterior, `Chapter 1` es el identificador de referencia y es opcional. La hora de referencia de `00:00:000 --> 01:04:364` especifica la hora de inicio y la hora de finalización del capítulo, en formato `00:00:000`. Los tres últimos dígitos son milisegundos y se pueden dejar como `000`, si se prefiere. El título del capítulo de `The bicycle store behind it all` es la descripción real del contenido del capítulo. El identificador de referencia, el tiempo de referencia de inicio y el título del capítulo aparecen en una ventana emergente del reproductor de vídeo cuando un usuario pasa el puntero del ratón sobre un punto de referencia visual en la cronología del vídeo.

Como está utilizando un visor de vídeo HTML5, asegúrese de que el archivo de capítulo que cree sigue el estándar WebVTT (Web Video Text Tracks). La extensión del nombre del archivo del capítulo es .vtt. Puede obtener más información sobre el estándar de subtítulos WebVTT.

Consulte [WebVTT: El formato de seguimiento de texto de vídeo web](https://dev.w3.org/html5/webvtt/)

**Para agregar marcadores de capítulo al vídeo:**

1. Con un editor de texto fuera de AEM, cree el archivo de capítulo de vídeo.

   Para la compatibilidad global con capítulos de vídeo en idiomas distintos del inglés, tenga en cuenta que el estándar WebVTT requiere que cree archivos .vtt y llamadas independientes para cada idioma que desee admitir.

1. Guarde el archivo `.vtt` en la codificación UTF8 para evitar problemas con la representación de caracteres en el texto del título del capítulo.

   Normalmente, le interesa asignar al archivo VTT de capítulo el mismo nombre que el archivo de vídeo y anexarlo con capítulos. Al hacerlo, puede ayudarle a automatizar la generación de las URL de vídeo con su sistema de administración de contenido web existente.
1. En AEM, cargue el archivo de capítulo WebVTT.

   Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

1. Realice una de las acciones siguientes:

   <table> 
     <tbody> 
      <tr> 
       <td>Para una experiencia de visor de vídeo emergente</td> 
       <td> 
       <ol> 
       <li>Vaya al recurso de vídeo <i>publicado </i>que desea asociar al archivo de capítulo que ha cargado. Recuerde que las direcciones URL solo están disponibles para copiarse <i>después</i> de <i>publicar</i> los recursos por primera vez. Consulte <a href="/help/assets/publishing-dynamicmedia-assets.md">Publicación de recursos.</a></li> 
       <li>En el menú desplegable, pulse <strong>Visualizadores</strong>.</li> 
       <li>En el carril izquierdo, pulse el nombre del ajuste preestablecido del visualizador de vídeo. Se abre una vista previa del vídeo en una página independiente.</li> 
       <li>En el carril izquierdo, en la parte inferior, pulse <strong>URL</strong>.</li> 
       <li>En el cuadro de diálogo URL, seleccione y copie la dirección URL en el portapapeles y, a continuación, pase la dirección URL a un editor de texto sencillo.</li> 
       <li>Anexe la URL copiada del vídeo con la siguiente sintaxis para asociarla con la URL copiada al archivo de capítulo:<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>Para una experiencia de visor de vídeo incrustada<br /> </td> 
       <td> 
       <ol> 
       <li>Vaya al recurso de vídeo <i>publicado </i>que desea asociar al archivo de capítulo que ha cargado. Recuerde que las direcciones URL solo están disponibles para copiarse <i>después</i> de <i>publicar</i> los recursos por primera vez. Consulte <a href="/help/assets/publishing-dynamicmedia-assets.md">Publicación de recursos.</a></li> 
       <li>En el menú desplegable, pulse <strong>Visualizadores</strong>.</li> 
       <li>En el carril izquierdo, pulse el nombre del ajuste preestablecido del visualizador de vídeo. Se abre una vista previa del vídeo en una página independiente.</li> 
       <li>En el carril izquierdo, en la parte inferior, pulse <strong>Incrustar</strong>.</li> 
       <li>En el cuadro de diálogo Código incrustado, seleccione y copie todo el código en el Portapapeles y, a continuación, péguelo en un editor de texto sencillo.</li> 
       <li>Añada el código incrustado del vídeo con la siguiente sintaxis para asociarlo a la URL copiada al archivo de capítulo:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## Acerca de las miniaturas de vídeo {#about-video-thumbnails}

Puede elegir entre una de las diez imágenes en miniatura generadas automáticamente por Dynamic Media para añadirlas al vídeo. El reproductor de vídeo muestra la miniatura seleccionada cuando se utiliza un recurso de vídeo con el componente Dynamic Media en el entorno de creación de AEM Sites, AEM Mobile o AEM Screens. La miniatura sirve como imagen estática que representa mejor el contenido de todo el vídeo y anima a los usuarios a pulsar el botón Reproducir .

En función del tiempo total que dure el vídeo, Dynamic Media captura diez imágenes en miniatura (predeterminadas) con el 1 %, 11 %, 21 %, 31 %, 41 %, 51 %, 61 %, 71 %, 81 % y 91 % en el vídeo. Las diez miniaturas persisten, lo que significa que si decide elegir una miniatura diferente más adelante, no es necesario volver a generar la serie. Obtenga una vista previa de las diez imágenes en miniatura y, a continuación, seleccione la que desee utilizar con el vídeo. Si desea cambiar a predeterminado, puede utilizar CRXDE Lite para configurar el intervalo de tiempo en el que se generan las imágenes en miniatura. Por ejemplo, si solo desea generar una serie de cuatro imágenes en miniatura con espaciado uniforme a partir del vídeo, puede configurar el tiempo de intervalo en 24 %, 49 %, 74 % y 99 %.

Lo ideal es agregar una miniatura de vídeo en cualquier momento después de cargar el vídeo, pero antes de publicar el vídeo en su sitio web.

Si lo prefiere, puede elegir cargar una miniatura personalizada para representar el vídeo en lugar de usar una miniatura generada por Dynamic Media. Por ejemplo, puede crear una imagen en miniatura personalizada que tenga el título del vídeo, una imagen de apertura llamativa o una imagen muy específica capturada del vídeo. La imagen en miniatura del vídeo personalizado que cargue debe tener una resolución máxima de 1280 x 720 píxeles (anchura mínima de 640 píxeles) y no debe superar los 2 MB.

>[!NOTE]
>
>Las miniaturas de vídeo personalizadas solo están disponibles cuando se ejecuta Dynamic Media en modo híbrido.

### Adición de una miniatura de vídeo {#adding-a-video-thumbnail}

1. Vaya a un recurso de vídeo cargado que quiera agregar una miniatura de vídeo.
1. En el modo de selección de recursos, ya sea en la **[!UICONTROL Vista de lista]** o en la **[!UICONTROL Vista de tarjeta]**, pulse el recurso de vídeo.
1. En la barra de herramientas, pulse el icono **[!UICONTROL Ver propiedades]** (un círculo con una &quot;i&quot;).
1. En la página **[!UICONTROL Propiedades]** del vídeo, pulse **[!UICONTROL Cambiar miniatura]**.
1. En la página **[!UICONTROL Cambiar miniatura]**, en la barra de herramientas, pulse **[!UICONTROL Seleccionar marco]**.

   Dynamic Media genera una serie de imágenes en miniatura a partir del vídeo, en función del intervalo de tiempo o intervalo de tiempo predeterminado que haya personalizado.

1. Previsualice las imágenes en miniatura generadas y, a continuación, seleccione la que desee agregar al vídeo.
1. Toque **[!UICONTROL Guardar cambio]**.

   La imagen en miniatura del vídeo se actualiza para usar la miniatura seleccionada. Si posteriormente decide cambiar la imagen en miniatura, puede volver a la página **[!UICONTROL Cambiar miniatura]** y seleccionar una nueva.

   Si ha configurado nuevos intervalos de tiempo predeterminados o ha cargado un nuevo vídeo para reemplazar el vídeo existente, deberá volver a generar las miniaturas en Dynamic Media.

   Consulte [Configuración del intervalo de tiempo predeterminado en el que se generan las miniaturas de vídeo](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configure el intervalo de tiempo predeterminado en el que se generan las miniaturas de vídeo {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Cuando configura y guarda el nuevo intervalo de tiempo predeterminado, el cambio se aplica automáticamente solo a los vídeos que cargue en el futuro. No aplica automáticamente el nuevo valor predeterminado a los vídeos que ha cargado anteriormente. Para los vídeos existentes, debe volver a generar las miniaturas.

Consulte [Adición de una miniatura de vídeo](#adding-a-video-thumbnail).

Para configurar el intervalo de tiempo predeterminado en el que se generan las miniaturas de vídeo,

1. En AEM, pulse **[!UICONTROL Herramientas]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. En la página CRXDE Lite, en el panel de directorio de la izquierda, vaya a `o etc/dam/imageserver/configuration/jcr:content/settings.`

   si el panel de directorio no está visible, es posible que tenga que tocar el icono >> a la izquierda de la pestaña Inicio .

1. En el panel inferior derecho, en la pestaña **[!UICONTROL Properties]**, pulse dos veces `thumbnailtime`.
1. En el cuadro de diálogo Editar tiempo de miniaturas, utilice los campos de texto para introducir valores de intervalo como porcentajes.

   * Pulse el icono de signo más (+) para añadir uno o varios campos de valor de intervalo. Es posible que deba desplazarse hasta la parte inferior del cuadro de diálogo para ver el icono.
   * Pulse el icono de signo menos (-) a la derecha de un campo de valor de intervalo para eliminarlo de la lista.
   * Pulse el icono de flecha arriba y el icono de flecha abajo para reordenar los valores de intervalo.

1. Pulse **[!UICONTROL Aceptar]** para volver a la pestaña **[!UICONTROL Propiedades]**.
1. Cerca de la esquina superior izquierda de la página CRXDE Lite, pulse **[!UICONTROL Guardar todo]** y, a continuación, pulse el icono **[!UICONTROL Página de inicio posterior]** en la esquina superior izquierda para volver a AEM.

   Consulte [Adición de una miniatura de vídeo.](#adding-a-video-thumbnail)

### Añadir una miniatura de vídeo personalizada {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>Esta función solo está disponible cuando se ejecuta Dynamic Media - Modo híbrido.

1. Vaya a un recurso de vídeo cargado que quiera agregar una miniatura de vídeo.
1. En el modo de selección de recursos, ya sea en la **[!UICONTROL Vista de lista]** o en la **[!UICONTROL Vista de tarjeta]**, pulse el recurso de vídeo.
1. En la barra de herramientas, pulse el icono **[!UICONTROL Ver propiedades]** (un círculo con una &quot;i&quot;).
1. En la página **[!UICONTROL Propiedades]** del vídeo, pulse **[!UICONTROL Cambiar miniatura]**.
1. En la página **[!UICONTROL Cambiar miniatura]**, en la barra de herramientas, pulse **[!UICONTROL Cargar nueva miniatura]**.
1. Vaya a la imagen en miniatura que desee usar, selecciónela y, a continuación, pulse **[!UICONTROL Abrir]** para comenzar a cargar la imagen en AEM
1. Una vez cargada la imagen correctamente, en la página **[!UICONTROL Cambiar miniatura]**, pulse **[!UICONTROL Guardar cambios]**.

   La miniatura personalizada se añade al vídeo.
