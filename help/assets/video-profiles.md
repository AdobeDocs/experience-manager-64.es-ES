---
title: Perfiles de vídeo de Dynamic Media
description: Dynamic Media incluye un perfil de codificación de vídeo adaptable predefinido. Los ajustes de este perfil listos para usar están optimizados para ofrecer a sus clientes la mejor experiencia de visualización de vídeo posible.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
exl-id: 3602e1b9-624d-408f-a7f6-1598b62dbd22
feature: Video Profiles,Video
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3104'
ht-degree: 18%

---

# Perfiles de vídeo de Dynamic Media {#video-profiles}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Dynamic Media ya viene con un perfil de codificación de vídeo adaptable predefinido. Los ajustes de este perfil listos para usar están optimizados para ofrecer a sus clientes la mejor experiencia de visualización posible. Al codificar los vídeos maestros mediante el perfil de codificación de vídeo adaptable, durante la reproducción el reproductor de vídeo ajusta automáticamente la calidad del flujo de vídeo en función de la velocidad de conexión a Internet de sus clientes. Esto se conoce como flujo adaptable.

A continuación se indican otros factores que determinan la calidad de los vídeos:

* **Resolución del vídeo maestro cargado**

   Si el vídeo MP4 se grabó a una resolución inferior, como 240p o 360p, no se puede transmitir en alta definición.

* **Tamaño del reproductor de vídeo**

   De forma predeterminada, la variable **[!UICONTROL Anchura]** en el perfil de codificación de vídeo adaptable está establecido en **[!UICONTROL Automático]**. De nuevo, durante la reproducción, se utiliza la mejor calidad en función del tamaño del reproductor.

Consulte también [Prácticas recomendadas para la codificación de vídeo](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>Para generar los metadatos de un vídeo y las miniaturas de imágenes de vídeo asociadas, el propio vídeo debe pasar por el proceso de codificación en Dynamic Media. En AEM, el flujo de trabajo de **[!UICONTROL codificación de vídeo de Dynamic Media]** codifica el vídeo si ha activado Dynamic Media y ha configurado los servicios de nube de vídeo. Este flujo de trabajo captura el historial de procesos de flujo de trabajo y la información de errores.
>
>Consulte [Supervisión de la codificación de vídeo y progreso de publicación en YouTube](video.md#monitoring-video-encoding-and-youtube-publishing-progress). Si ha habilitado Dynamic Media y ha configurado los servicios de nube de vídeo, la variable **[!UICONTROL Codificar vídeo de Dynamic Media]** El flujo de trabajo de se aplica automáticamente al cargar un vídeo. (Si no utiliza medios dinámicos, el flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]** tiene efecto).
>
>Los metadatos son útiles cuando se buscan recursos. Las miniaturas son imágenes de vídeo estáticas que se generan durante la codificación. El sistema AEM los necesita y se utilizan en la interfaz de usuario para ayudarle a identificar visualmente los vídeos en la **[!UICONTROL Vista de tarjetas]**, **[!UICONTROL Resultados de la búsqueda]** y **[!UICONTROL Lista de recursos]** vista. Puede ver las miniaturas generadas al pulsar el botón **[!UICONTROL Representaciones]** icono (paleta de un pintor) de un vídeo codificado.

Cuando haya terminado de crear el perfil de vídeo, debe aplicarlo a una carpeta o varias carpetas. Consulte [Aplicación de un perfil de vídeo a carpetas.](#applying-a-video-profile-to-folders)

Para definir parámetros de procesamiento avanzados para otros tipos de recursos, consulte [Configuración del procesamiento de recursos](config-dms7.md#configuring-asset-processing).

## Ajustes preestablecidos de codificación de vídeo adaptable {#adaptive-video-encoding-presets}

En la tabla siguiente se identifican los perfiles de codificación de prácticas recomendadas para la transmisión de vídeo adaptable a dispositivos móviles, tabletas y equipos de escritorio. Puede utilizar estos ajustes preestablecidos para cualquier vídeo de relación de aspecto.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Códec de formato de vídeo</strong></td> 
   <td><strong>Tamaño de vídeo: ancho (px)</strong></td> 
   <td><strong>Tamaño del vídeo: altura (px)</strong></td> 
   <td><strong>Mantener proporción de aspecto?</strong></td> 
   <td><strong>Velocidad de bits de vídeo (Kbps)</strong></td> 
   <td><strong>Velocidad De Fotogramas De Vídeo (Fps)</strong></td> 
   <td><strong>Códec de audio</strong></td> 
   <td><strong>Velocidad de bits de audio (Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>Sí</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>Sí</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>720<br /> </td> 
   <td>Sí</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## Creación de un perfil de codificación de vídeo de Dynamic Media para flujo adaptable {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media ya viene con un perfil predefinido de codificación de vídeo adaptable (un grupo de ajustes de carga de vídeo para MP4 H.264) optimizado para la mejor experiencia de visualización. Puede utilizar este perfil al cargar los vídeos.

Sin embargo, si este perfil predefinido no satisface sus necesidades, puede elegir crear su propio perfil de codificación de vídeo adaptable. Al utilizar la configuración **[!UICONTROL Codificar para flujo adaptable]**-*una práctica recomendada*: todos los ajustes preestablecidos de codificación que agregue al perfil se validan para garantizar que todos los vídeos tengan la misma proporción de aspecto. Además, los vídeos codificados se tratan como un conjunto de varias velocidades de bits para la transmisión.

Al crear el perfil de codificación de vídeo, verá que la mayoría de las opciones de codificación se rellenan previamente con ajustes predeterminados recomendados para ayudarle. Sin embargo, si selecciona un valor que no sea el predeterminado recomendado, tenga en cuenta que puede provocar una mala calidad de vídeo durante la reproducción y otros problemas de rendimiento.

Por lo tanto, para todos los ajustes preestablecidos de codificación de vídeo MP4 H.264 del perfil, se validan los siguientes valores para garantizar que sean los mismos en todos los ajustes preestablecidos de codificación individuales del perfil, lo que permite la transmisión adaptativa:

* Códec de formato de vídeo: MP4 H.264 (.mp4)
* Códec de audio
* Velocidad de bits de audio
* Mantener proporción de aspecto
* Codificación de dos pasos
* Velocidad de bits constante
* Perfil H264
* Velocidad de muestreo de audio

Si los valores no son los mismos, puede seguir creando el perfil tal cual. Sin embargo, tenga en cuenta que la transmisión adaptativa no será posible. En su lugar, los usuarios verán la transmisión de una sola velocidad de bits. Se recomienda editar la configuración de codificación para utilizar los mismos valores en ajustes preestablecidos de codificación individuales en el perfil. (Tenga en cuenta que el editor de perfiles/ajustes preestablecidos de vídeo debe aplicar la paridad de los ajustes de codificación de vídeo adaptable si **[!UICONTROL Codificar para flujo adaptable]** está activada).

Consulte también [Creación de un perfil de codificación de vídeo para flujo progresivo](#creating-a-video-encoding-profile-for-progressive-streaming).

Consulte también [Prácticas recomendadas para la codificación de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parámetros de procesamiento avanzados para otros tipos de recursos, consulte [Configuración del procesamiento de recursos](config-dms7.md#configuring-asset-processing).

Cuando haya terminado de crear el perfil de vídeo, debe aplicarlo a una o varias carpetas.

**Para crear un perfil de codificación de vídeo de Dynamic Media para flujo adaptable**:

1. Toque o haga clic en el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. Toque **[!UICONTROL Crear]** para agregar un nuevo perfil de vídeo.

1. Introduzca un nombre y una descripción para el perfil.
1. Asegúrese de que **[!UICONTROL Codificar para flujo adaptable]** está activada (predeterminada).
1. Toque **[!UICONTROL Agregar ajuste preestablecido de codificación de vídeo]**.
1. En el **[!UICONTROL Básico]** , defina las opciones de vídeo y audio.

   Pulse el icono de información situado junto a cada opción para obtener descripciones adicionales o ajustes recomendados basados en el códec de formato de vídeo seleccionado.

1. En el encabezado Tamaño del vídeo, asegúrese de que **[!UICONTROL Mantener relación de aspecto]** está activada.
1. Establezca la resolución del tamaño del fotograma de vídeo en píxeles. Utilice la variable **[!UICONTROL Automático]** para escalar automáticamente para que coincida con la proporción de aspecto del origen (relación ancho-alto). Por ejemplo, Automático x 480 o 640 x Automático.

   Realice una de las siguientes acciones:

   * En el **[!UICONTROL Anchura]** , introduzca **[!UICONTROL auto]**. En el **[!UICONTROL Altura]** , introduzca un valor en píxeles.
   * Para ayudarle a visualizar el tamaño del vídeo, toque la variable **[!UICONTROL Información]** a la derecha de **[!UICONTROL Altura]** para abrir el **[!UICONTROL Calculadora de tamaño]** página. Uso **[!UICONTROL Calculadora de tamaño]** para definir las dimensiones de vídeo (representadas por el cuadro azul) que desee. Toque **[!UICONTROL X]** en la esquina superior derecha cuando haya terminado.

1. (Opcional) Toque la **[!UICONTROL Avanzadas]** y asegúrese de que **[!UICONTROL Usar valores predeterminados]** está activada (recomendado). También puede modificar la configuración avanzada de vídeo y audio.
1. En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]** para guardar el ajuste preestablecido.
1. Realice una de las siguientes acciones:

   * Repita los pasos del 5 al 10 para crear ajustes preestablecidos de codificación adicionales. (El flujo de vídeo adaptable requiere más de un ajuste preestablecido de vídeo).
   * En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]** para guardar el perfil.

## Monitorización del progreso de un trabajo de codificación {#monitoring-the-progress-of-an-encoding-job}

Se muestra un indicador de procesamiento (o barra de progreso) para que pueda supervisar visualmente el progreso de un trabajo de codificación de vídeo.

También puede ver el `error.log` para controlar el progreso de un trabajo de codificación, para ver si la codificación ha finalizado o si se ha producido algún error en el trabajo. La variable `error.log` se encuentra en la variable `logs` carpeta donde está instalada la instancia de AEM.

## Creación de un perfil de codificación de vídeo de Dynamic Media para flujo progresivo {#creating-a-video-encoding-profile-for-progressive-streaming}

Si decide no utilizar la opción **[!UICONTROL Codificar para flujo adaptable]**, tenga en cuenta que todos los ajustes preestablecidos de codificación que agregue al perfil se tratan como representaciones de vídeo individuales para flujo de una sola velocidad de bits o entrega de vídeo progresivo. Además, no hay ninguna validación para garantizar que todas las representaciones de vídeo tengan la misma proporción de aspecto.

Dependiendo del modo que esté ejecutando, los códecs de formato de vídeo compatibles son los siguientes:

* Modo Dynamic Media-Scene7: H.264 (.mp4)
* Modo híbrido de Dynamic Media: H.264 (.mp4), WebM

Consulte también [Creación de un perfil de codificación de vídeo para flujo adaptable](#creating-a-video-encoding-profile-for-adaptive-streaming).

Consulte también [Prácticas recomendadas para la codificación de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parámetros de procesamiento avanzados para otros tipos de recursos, consulte [Configuración del procesamiento de recursos](config-dms7.md#configuring-asset-processing).

Cuando haya terminado de crear el perfil de vídeo, debe aplicarlo a una o varias carpetas.

**Para crear un perfil de codificación de vídeo de Dynamic Media para flujo progresivo:**

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. Toque **[!UICONTROL Crear]** para agregar un nuevo perfil de vídeo.
1. Introduzca un nombre y una descripción para el perfil.
1. Borre la variable **[!UICONTROL Codificar para flujo adaptable]** en el Navegador.
1. Toque **[!UICONTROL Agregar ajuste preestablecido de codificación de vídeo]**.
1. En el **[!UICONTROL Básico]** , defina las opciones de vídeo y audio.

   Toque . **[!UICONTROL Información]** junto a cada opción para obtener descripciones adicionales o ajustes recomendados basados en el códec de formato de vídeo seleccionado.

1. (Opcional) En el **Tamaño del vídeo** encabezado, desmarcar **[!UICONTROL Mantener relación de aspecto]**.
1. En el **[!UICONTROL Anchura]** , introduzca **[!UICONTROL auto]**; a la derecha del **[!UICONTROL Altura]** , toque el **[!UICONTROL Información]** icono. Utilice la variable **[!UICONTROL Calculadora de tamaño]** para definir la dimensión de vídeo (cuadro azul) como desee. Toque **[!UICONTROL X]** cuando haya terminado.
1. (Opcional) Realice una de las siguientes acciones:

   * Toque . **[!UICONTROL Avanzadas]** y asegúrese de que **[!UICONTROL Usar valores predeterminados]** está activada (recomendado).
   * Borre la variable **[!UICONTROL Usar valores predeterminados]** y especifique la configuración de vídeo y audio que desea.

      Toque . **[!UICONTROL Información]** junto a cada opción para obtener descripciones adicionales o ajustes recomendados basados en el códec de formato de vídeo seleccionado.

1. En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]** para guardar el ajuste preestablecido.
1. Realice una de las siguientes acciones:

   * Repita los pasos del 5 al 10 para crear ajustes preestablecidos de codificación adicionales.
   * En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]** para almacenar el perfil.

## Uso de parámetros de codificación de vídeo personalizados {#using-custom-added-video-encoding-parameters}

Puede editar un perfil de codificación de vídeo existente para aprovechar los parámetros avanzados de codificación de vídeo que no se encuentran en la interfaz de usuario al crear o editar un perfil de vídeo en AEM. Personalizó la adición de uno o más parámetros avanzados, como **[!UICONTROL minBitrate]** y **[!UICONTROL maxBitrate]**: al perfil existente.

**Para utilizar parámetros de codificación de vídeo personalizados**:

1. Pulse el logotipo de AEM y, a continuación, vaya a **[!UICONTROL Herramientas > General > CRXDE Lite]**.
1. En el **[!UICONTROL CRXDE Lite]** en la **[!UICONTROL Explorer]** a la izquierda, vaya a:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. En el panel situado en la parte inferior derecha de la página, desde la **[!UICONTROL Propiedades]** especifique la **[!UICONTROL Nombre]**, **[!UICONTROL Tipo]** y **[!UICONTROL Valor]** del parámetro que desea utilizar.

   Los siguientes parámetros avanzados están disponibles para su uso:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Nombre</strong></td> 
    <td><strong>Descripción</strong><br /> </td> 
    <td><strong>Tipo</strong><br /> </td> 
    <td><strong>Valor</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>Nivel H.264 que se utilizará para la codificación. Normalmente, esto se determina automáticamente según la configuración de codificación que utilice.</td> 
    <td><code>String</code></td> 
    <td><p>10 * nivel h264</p> <p>Por ejemplo, 3,0 = 30, 1,3 = 13)</p> <p>No hay ningún valor predeterminado.</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>El número de fotogramas de destino entre fotogramas clave. Calcule este valor para generar un fotograma clave cada 2-10 segundos. Por ejemplo, a 30 fotogramas por segundo, el intervalo de fotogramas clave debe ser de 60 a 300.<br /> <br /> Los intervalos más bajos de los fotogramas clave mejoran la búsqueda de flujo y el comportamiento de conmutación de flujo para las codificaciones de vídeo adaptables, y también pueden mejorar la calidad de los vídeos que tienen mucho movimiento. Sin embargo, debido a que los fotogramas clave aumentan el tamaño de un archivo, un intervalo de fotogramas clave inferior generalmente da como resultado una menor calidad de vídeo general a una velocidad de bits determinada.</td> 
    <td><code>String</code></td> 
    <td><p>Número positivo.</p> <p>El valor predeterminado es 300.</p> <p>El valor recomendado para HLS (HTTP Live Streaming) es 60-90.</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>Velocidad de bits mínima para permitir codificaciones de velocidad de bits variables, en Kbps (kilobits por segundo).</p> <p>Este parámetro solo se aplica cuando<strong> Utilizar velocidad de bits constante</strong> se anula la selección de la ficha Avanzado cuando se crea o edita un perfil de codificación de vídeo.</p> <p>Consulte también <a href="/help/assets/video.md#bitrate">Velocidad de bits</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Número positivo, en Kbps.</p> <p>No hay ningún valor predeterminado.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Velocidad de bits máxima para permitir codificaciones de velocidad de bits variables, en Kbps.</p> <p>Este parámetro solo se aplica cuando<strong> Utilizar velocidad de bits constante</strong> se anula la selección de la ficha Avanzado cuando se crea o edita un perfil de codificación de vídeo.</p> <p>Consulte también <a href="/help/assets/video.md#bitrate">Velocidad de bits</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Número positivo, en Kbps.</p> <p>No hay ningún valor predeterminado. Sin embargo, el valor recomendado es hasta dos veces superior a la velocidad de bits de la codificación.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Definir valor como <code>true</code> para forzar una velocidad de bits constante para el flujo de audio, si es compatible con el códec de audio.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>El valor predeterminado es <code>false</code>.</p> <p>El valor recomendado para HLS (HTTP Live Streaming) es <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Cerca de la esquina inferior derecha de la página, pulse **[!UICONTROL Agregar]**.
1. Realice una de las siguientes acciones:

   * Repita los pasos 3 y 4 para agregar otro parámetro al perfil de codificación de vídeo.
   * Cerca de la esquina superior izquierda de la página, pulse **[!UICONTROL Guardar todo]**.

1. En la esquina superior izquierda de la variable **[!UICONTROL CRXDE Lite]** de la página, pulse **[!UICONTROL Página de inicio]** para volver a AEM.

### Edición de un perfil de codificación de vídeo de Dynamic Media {#editing-a-video-encoding-profile}

Puede editar cualquier perfil de codificación de vídeo que haya creado para agregar, editar o eliminar ajustes preestablecidos de vídeo dentro de ese perfil.

De forma predeterminada, no puede editar los **[!UICONTROL Codificación de vídeo adaptable]** perfil incluido con Dynamic Media. En su lugar, puede copiar fácilmente el perfil y guardarlo con un nuevo nombre. A continuación, puede editar los ajustes preestablecidos que desee en el perfil copiado.

Consulte también [Prácticas recomendadas para la codificación de vídeo](video.md#best-practices-for-encoding-videos).

Para definir parámetros de procesamiento avanzados para otros tipos de recursos, consulte [Configuración del procesamiento de recursos](config-dms7.md#configuring-asset-processing).

**Para editar un perfil de codificación de vídeo de Dynamic Media**:

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. En el **[!UICONTROL Perfiles de vídeo]** , marque un nombre de perfil de vídeo.
1. En la barra de herramientas, pulse **[!UICONTROL Editar]**.
1. En el **[!UICONTROL Perfil de codificación de vídeo]** , edite el nombre y la descripción como desee.
1. Como práctica recomendada, compruebe que la casilla de verificación **[!UICONTROL Codificar para flujo adaptable]** está activada.

   Pulse el icono de información para ver una descripción del flujo adaptable. (Si está editando un perfil de vídeo progresivo, no active esta casilla de verificación).

1. En el **[!UICONTROL Ajustes preestablecidos de codificación de vídeo]** encabezado, agregar, editar o eliminar ajustes preestablecidos de codificación de vídeo que conforman el perfil.

   Toque . **[!UICONTROL Información]** junto a cada opción de **[!UICONTROL Básico]** y **[!UICONTROL Avanzadas]** para obtener descripciones adicionales o ajustes recomendados basados en el códec de formato de vídeo seleccionado.

1. En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**.

### Copia de un perfil de codificación de vídeo de Dynamic Media {#copying-a-video-encoding-profile}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. En el **[!UICONTROL Perfiles de vídeo]** , marque un nombre de perfil de vídeo.
1. En la barra de herramientas, pulse **[!UICONTROL Copiar]**.
1. En el **[!UICONTROL Perfil de codificación de vídeo]** , introduzca un nuevo nombre para el perfil.
1. Como práctica recomendada, compruebe que la casilla de verificación **[!UICONTROL Codificar para flujo adaptable]** está activada. Pulse el icono de información para ver una descripción del flujo adaptable. (Si está copiando un perfil de vídeo progresivo, no active la casilla de verificación).

   En Dynamic Media: modo híbrido, si un ajuste preestablecido de vídeo WebM forma parte del perfil de vídeo, **[!UICONTROL Codificar para flujo adaptable]** no es posible porque todos los ajustes preestablecidos deben ser MP4.
1. En el **[!UICONTROL Ajustes preestablecidos de codificación de vídeo]** encabezado, agregar, editar o eliminar ajustes preestablecidos de codificación de vídeo que conforman el perfil.

   Toque . **[!UICONTROL Información]** junto a cada opción de **[!UICONTROL Básico]** y **[!UICONTROL Avanzadas]** para ver la configuración y las descripciones recomendadas.

1. En la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**.

### Eliminación de un perfil de codificación de vídeo de Dynamic Media {#deleting-a-video-encoding-profile}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. En el **[!UICONTROL Perfiles de vídeo]** , marque uno o varios nombres de perfil de vídeo.
1. En la barra de herramientas, pulse **[!UICONTROL Eliminar]**.
1. Pulse **[!UICONTROL Aceptar]**.

## Aplicación de un perfil de vídeo de Dynamic Media a carpetas {#applying-a-video-profile-to-folders}

Al asignar un perfil de vídeo a una carpeta, las subcarpetas heredan automáticamente el perfil de su carpeta principal. Esto significa que solo puede asignar un perfil de vídeo a una carpeta. Como tal, considere detenidamente la estructura de carpetas en la que carga, almacena, utiliza y archiva recursos.

Si ha asignado un perfil de vídeo diferente a una carpeta, el nuevo perfil anula el perfil anterior. Los recursos de carpeta existentes no cambian. El nuevo perfil se aplica a los recursos que se agregan a la carpeta más adelante.

Las carpetas que tienen un perfil asignado se indican en la interfaz de usuario por el nombre del perfil que aparece en el nombre de la tarjeta.

![chlimage_1-517](assets/chlimage_1-517.png)

Puede aplicar perfiles de vídeo a carpetas específicas o globalmente a todos los recursos.

### Aplicación de perfiles de vídeo a carpetas específicas {#applying-video-profiles-to-specific-folders}

Puede aplicar un perfil de vídeo a una carpeta desde el menú **[!UICONTROL Herramientas]** o, si se encuentra en la carpeta, desde **[!UICONTROL Propiedades]**. En esta sección se describe cómo aplicar perfiles de vídeo a las carpetas de ambos modos.

Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

#### Aplicación de perfiles de vídeo de Dynamic Media a carpetas desde la interfaz de usuario Perfiles {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. Seleccione el perfil de vídeo que desea aplicar a una o varias carpetas.
1. Pulse **[!UICONTROL Aplicar perfil a las carpetas]** y seleccione las carpetas que desee utilizar para recibir los recursos cargados recientemente. A continuación, pulse **[!UICONTROL Aplicar]**. Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

#### Aplicación de perfiles de vídeo de Dynamic Media a carpetas desde Propiedades {#applying-video-profiles-to-folders-from-properties}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Recursos]** y, a continuación, a la carpeta a la que desee aplicar un perfil de vídeo.
1. En la carpeta, pulse la marca de verificación para seleccionarla y, a continuación, pulse **[!UICONTROL Propiedades]**.
1. Seleccione el **[!UICONTROL Perfiles de vídeo]** , seleccione el perfil en el menú desplegable y pulse **[!UICONTROL Guardar y cerrar]**. Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Aplicación de un perfil de vídeo de Dynamic Media globalmente {#applying-a-video-profile-globally}

Además de aplicar un perfil a una carpeta, también puede aplicarlo de forma global para que cualquier contenido cargado en AEM recursos de cualquier carpeta tenga aplicado el perfil seleccionado.

**Aplicación de un perfil de vídeo de Dynamic Media globalmente**:

1. Vaya al CRXDE Lite al nodo siguiente: `/content/dam/jcr:content`.
1. Añadir la propiedad **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Toque **[!UICONTROL Guardar todo]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Eliminación de un perfil de vídeo de Dynamic Media de las carpetas {#removing-a-video-profile-from-folders}

Al quitar un perfil de vídeo de una carpeta, las subcarpetas heredan automáticamente la eliminación del perfil de su carpeta principal. Sin embargo, cualquier procesamiento de archivos que se haya producido dentro de las carpetas permanece intacto.

Puede quitar un perfil de vídeo de una carpeta desde el menú **[!UICONTROL Herramientas]** o, si se encuentra en la carpeta, desde **[!UICONTROL Configuración de carpeta]**. En esta sección se describe cómo quitar perfiles de vídeo de las carpetas de ambos modos.

### Eliminación de perfiles de vídeo de Dynamic Media de las carpetas mediante la interfaz de usuario de Perfiles {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de vídeo]**.
1. Seleccione el perfil de vídeo que desea eliminar de una carpeta o varias carpetas.
1. Toque **[!UICONTROL Eliminar perfil de las carpetas]** y seleccione la carpeta o carpetas múltiples de las que desee utilizar para quitar el perfil y pulse **[!UICONTROL Eliminar]**.

   Puede confirmar que el perfil de vídeo ya no se aplica a una carpeta porque el nombre ya no aparece debajo del nombre de la carpeta.

### Eliminación de perfiles de vídeo de Dynamic Media de las carpetas mediante Propiedades {#removing-video-profiles-from-folders-via-properties}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Recursos]** y, a continuación, a la carpeta desde la que desea eliminar un perfil de vídeo.
1. En la carpeta, pulse la marca de verificación para seleccionarla y, a continuación, pulse **[!UICONTROL Propiedades]**.
1. Seleccione el **[!UICONTROL Perfiles de vídeo]** y seleccione **[!UICONTROL Ninguna]** en el menú desplegable y pulse **[!UICONTROL Guardar y cerrar]**. Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.
