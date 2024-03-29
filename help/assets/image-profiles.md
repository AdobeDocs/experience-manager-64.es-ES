---
title: Perfiles de imagen de Dynamic Media
seo-title: Dynamic Media Image Profiles
description: Cree perfiles de imagen que contengan ajustes para máscara de enfoque, recorte inteligente o muestra inteligente, o ambos, y aplique el perfil a una carpeta de recursos de imagen.
seo-description: Create Image Profiles that contain settings for unsharp mask, and smart crop or smart swatch, or both, then apply the profile to a folder of image assets.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
exl-id: 895103c8-df58-40f0-85d6-e29637edce53
feature: Image Profiles
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2960'
ht-degree: 8%

---

# Perfiles de imagen de Dynamic Media {#image-profiles}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Al cargar imágenes, puede recortar automáticamente la imagen al cargarla aplicando un perfil de imagen a la carpeta.

>[!NOTE]
>
>El recorte inteligente solo está disponible en el modo Dynamic Media - Scene7.

>[!IMPORTANT]
>
>Los perfiles de imagen no se aplican a archivos PDF, GIF animado o INDD (Adobe InDesign).


## Opciones de recorte {#crop-options}

Al implementar Recorte inteligente en imágenes, Adobe recomienda las siguientes prácticas recomendadas y aplica el siguiente límite:

| Tipo de límite | Práctica recomendada | Límite impuesto |
| --- | --- | --- |
| Número de recortes inteligentes por imagen | 5 | 100 |

Consulte también [Limitaciones de Dynamic Media](/help/assets/limitations.md).

<!-- CQDOC-16069 for paragraph directly below -->

Las coordenadas de recorte inteligentes dependen de la relación de aspecto. Es decir, para cada ajuste de recorte inteligente de un perfil de imagen, si la proporción de aspecto es la misma para las dimensiones agregadas en el perfil de imagen, se envía la misma proporción de aspecto a Dynamic Media. Como resultado, Adobe recomienda utilizar el mismo área de recorte. De este modo, se garantiza que no haya ningún impacto en las diferentes dimensiones utilizadas en el perfil de imagen.

Cada generación de recorte inteligente que cree requiere un procesamiento adicional. Por ejemplo, si se agregan más de cinco relaciones de aspecto de recorte inteligente, la tasa de consumo de los recursos puede ser lenta. También puede causar un aumento de la carga en los sistemas. Como puede aplicar Recorte inteligente en el nivel de carpeta, Adobe recomienda utilizarlo en las carpetas *only* donde sea necesario.

**Pautas para definir el Recorte inteligente en un perfil de imagen**
Para mantener bajo control el uso de Smart Crop y optimizar el tiempo de procesamiento y almacenamiento de los cultivos, Adobe recomienda las siguientes directrices y sugerencias:

* Evite crear perfiles de recorte inteligente duplicados que tengan los mismos valores de anchura y altura.
* Asigne un nombre a los cultivos inteligentes en función de las dimensiones de recorte, no del uso final. Esto ayuda a optimizar para duplicados donde se utiliza una sola dimensión en varias páginas.
* Cree perfiles de imagen en el tipo página/recurso para carpetas y subcarpetas específicas en lugar de un perfil de recorte inteligente común que se aplique a todas las carpetas o a todos los recursos.
* Un perfil de imagen que aplique a las subcarpetas anula un perfil de imagen que se aplica a la carpeta.
* Cree perfiles de imagen en el tipo página/recurso para carpetas y subcarpetas específicas en lugar de un perfil de recorte inteligente común que se aplique a todas las carpetas o a todos los recursos.
* Un perfil de imagen que aplique a las subcarpetas anula un perfil de imagen que se aplique a la carpeta.
* Lo ideal es tener entre 10 y 15 cultivos inteligentes por imagen para optimizar los índices de pantalla y el tiempo de procesamiento.

<!--
* Image assets that are going to have a smart crop applied to them must be a minimum of 50 x 50 pixels or larger. CQDOC-20087
* An Image Profile that contains duplicate smart crop dimensions is not permitted. CQDOC-20087
* Duplicate named Image Profiles that have smart crop options set are not permitted. CQDOC-20087
* Create page-wise/asset type-wise Image Profiles for specific folders and subfolders instead of a common smart crop profile that is applied to all folders or all assets.
* An Image Profile that you apply to subfolders overrides an Image Profile that is applied to the folder.
* Ideally, have 10-15 smart crops per image to optimize for screen ratios and processing time. -->
<!-- * Avoid creating duplicate smart crop profiles that have the same width and height values. 
* Name smart crops based on crop dimensions, not on end usage. Doing so helps to optimize for duplicates where a single dimension is used on multiple pages. -->

Tiene dos opciones de recorte de imagen para elegir. También puede automatizar la creación de muestras de color e imagen o conservar el contenido de recorte en las resoluciones de destino.

>[!IMPORTANT]
>
>・ Adobe recomienda revisar los cultivos y muestras generados para asegurarse de que sean adecuados y relevantes para su marca y sus valores.
・ El formato de imagen CMYK no es compatible con el recorte inteligente.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opción</strong></td> 
   <td><strong>Cuándo se usa</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>Recorte de píxeles</td> 
   <td>Recorte masivo de imágenes basado únicamente en dimensiones.</td> 
   <td><p>Para utilizar esta opción, seleccione <strong>Recorte de píxeles</strong> en la lista desplegable Opciones de recorte .</p> <p>Para recortar desde los lados de una imagen, introduzca el número de píxeles que se recortarán desde cualquier lado o lado de la imagen. La cantidad de imagen recortada depende de la configuración de ppi (píxeles por pulgada) en el archivo de imagen.</p> <p>Un recorte de píxeles del perfil de imagen se representa de la siguiente manera:<br /> </p> 
    <ul> 
     <li>Los valores son Superior, Inferior, Izquierda y Derecha.</li> 
     <li>La parte superior izquierda se considera 0,0 y el recorte de píxeles se calcula a partir de ahí.</li> 
     <li>Punto inicial de recorte: La izquierda es X y la superior es Y</li> 
     <li>Cálculo horizontal: dimensión de píxeles horizontal de la imagen original menos Izquierda y luego menos Derecha.</li> 
     <li>Cálculo vertical: altura vertical de píxeles menos Superior y, a continuación, menos Inferior.</li> 
    </ul> <p>Por ejemplo, supongamos que tiene una imagen de 4000 x 3000 píxeles. Se utilizan valores: Superior=250, Inferior=500, Izquierda=300, Derecha=700.</p> <p>Desde la parte superior izquierda (300.250), recorte utilizando el espacio de relleno (4000-300-700, 3000-250-500 o 3000.2250).</p> </td> 
  </tr> 
  <tr> 
   <td>Recorte inteligente</td> 
   <td>Imágenes de recorte masivo basadas en su punto focal visual.</td> 
   <td><p>Smart Crop utiliza el poder de la inteligencia artificial en Adobe Sensei para automatizar rápidamente el recorte de imágenes en masa. El recorte inteligente detecta y recorta automáticamente al punto focal de cualquier imagen para capturar el punto de interés deseado, independientemente del tamaño de la pantalla.</p> <p>Para utilizar el Recorte inteligente, seleccione <strong>Recorte inteligente</strong> en la lista desplegable Opciones de recorte y, a continuación, a la derecha de Recorte de imagen adaptable, habilite (active) la función.</p> <p>Los tamaños predeterminados de los puntos de interrupción Grande, Medio y Pequeño generalmente abarcan toda la gama de tamaños que la mayoría de las imágenes se utilizan en dispositivos móviles y tabletas, equipos de escritorio y titulares. Si lo desea, puede editar los nombres predeterminados de Grande, Medio y Pequeño.</p> <p>Para agregar más puntos de interrupción, haga clic en <strong>Agregar recorte</strong>; para eliminar un recorte, haga clic en el icono de la papelera.</p> </td> 
  </tr> 
  <tr> 
   <td>Muestra de color e imagen</td> 
   <td>Genera de forma masiva una muestra de imagen para cada imagen.</td> 
   <td><p><strong>Nota</strong>: La muestra inteligente no es compatible con Dynamic Media Classic.</p> <p>Localice y genere automáticamente muestras de alta calidad a partir de imágenes de productos que muestren color o textura.</p> <p>Para utilizar la muestra de color e imagen, seleccione <strong>Recorte inteligente</strong> en la lista desplegable Opciones de recorte y, a continuación, a la derecha de Color y Muestra de imagen, habilite (active) la función. Introduzca un valor de píxel en los cuadros de texto Ancho y Alto.</p> <p>Aunque todos los cultivos de imagen están disponibles en el carril Representaciones , las muestras solo se utilizan mediante la función Copiar URL . Es necesario que utilice su propio componente de visualización para representar la muestra en el sitio. (La excepción a esta regla son los banners de carrusel. Dynamic Media proporciona el componente de visualización para la muestra utilizada en los banners de carrusel).</p> <p><strong>Uso de muestras de imagen</strong></p> <p>La dirección URL para muestras de imagen es sencilla:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>donde <code>:Swatch</code> se anexa a la solicitud de recurso.</p> <p><strong>Uso de muestras de color</strong></p> <p>Para utilizar muestras de color, debe realizar una <code>req=userdata</code> con lo siguiente:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Por ejemplo, el siguiente es un recurso de muestra en Dynamic Media Classic:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>y aquí está el correspondiente del recurso de muestra <code>req=userdata</code> URL:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>La variable <code>req=userdata</code> la respuesta es la siguiente:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>También puede solicitar un <code>req=userdata</code> en formato XML o JSON, como en los siguientes ejemplos de URL respectivos:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Máscara de enfoque {#unsharp-mask}

Utilice **Máscara de enfoque** para ajustar un efecto de filtro de enfoque en la imagen final con disminución de resolución. Puede controlar la intensidad del efecto, el radio del efecto (medido en píxeles) y un umbral de contraste que se ignora. Este efecto utiliza las mismas opciones que el filtro &quot;Máscara de enfoque&quot; de Adobe Photoshop.

>[!NOTE]
La máscara de enfoque solo se aplica a las representaciones a escala reducida dentro del PTIFF (tiff piramidal) que se reducen a más del 50%. Esto significa que las representaciones de mayor tamaño dentro del PTIFF no se ven afectadas por la máscara de enfoque, mientras que las representaciones de menor tamaño, como las miniaturas, se modifican (y muestran la máscara de enfoque).

En **Máscara de enfoque**, tiene las siguientes opciones de filtrado:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opción</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>Cantidad</td> 
   <td>Controla la cantidad de contraste aplicada a los píxeles de borde. El valor predeterminado es 1,75. Para imágenes de alta resolución, puede aumentarlo hasta 5. Piense en Amount como una medida de la intensidad del filtro. El rango es 0-5.</td> 
  </tr> 
  <tr> 
   <td>Radio</td> 
   <td>Determina el número de píxeles adyacentes a los píxeles de borde que afectarán al enfoque. En las imágenes de alta resolución, especifique un valor entre 1 y 2. Un valor bajo solo aplica enfoque a los píxeles de borde; un valor alto enfoca una banda más ancha de píxeles. El valor adecuado depende del tamaño de la imagen. El valor predeterminado es 0,2. El rango es 0-250.</td> 
  </tr> 
  <tr> 
   <td>Umbral</td> 
   <td><p>Determina el intervalo de contraste que se debe ignorar cuando se aplica el filtro de máscara de enfoque. En otras palabras, esta opción determina la diferencia entre los píxeles enfocados y el área circundante antes de que se consideren píxeles de borde y se agranden. Para evitar la introducción del ruido, experimente con valores entre 0 y 255.</p> </td> 
  </tr> 
 </tbody> 
</table>

El enfoque se describe en [Enfoque de imágenes](/help/assets/assets/sharpening_images.pdf).

## Creación de perfiles de imagen de Dynamic Media {#creating-image-profiles}

Para definir parámetros de procesamiento avanzados para otros tipos de recursos, consulte [Configuración del procesamiento de recursos](config-dms7.md#configuring-asset-processing).

**Para crear perfiles de imagen de Dynamic Media**:

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de imagen]**.
1. Toque **[!UICONTROL Crear]** para agregar un perfil de imagen.
1. Introduzca un nombre de perfil y valores para máscara de enfoque, recorte o muestra, o ambos.

   Puede que le resulte útil utilizar un nombre de perfil que sea específico para el propósito deseado. Por ejemplo, si desea crear un perfil que genere muestras solamente (donde Recorte inteligente está desactivado y Color y Muestra de imagen está activada), puede utilizar el nombre de perfil &quot;Muestras inteligentes&quot;.

   Consulte también [Opciones de recorte y muestra inteligente](#crop-options) y [Máscara de enfoque](#unsharp-mask).

   ![recortar](assets/crop.png)

1. Pulse **[!UICONTROL Guardar]**. El perfil recién creado aparece en la lista de perfiles disponibles.

## Edición o eliminación de perfiles de imagen de Dynamic Media {#editing-or-deleting-image-profiles}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de imagen]**.
1. Seleccione el perfil de imagen que desee editar o eliminar. Para editarlo, seleccione **[!UICONTROL Editar perfil de procesamiento de imágenes]**. Para quitarlo, seleccione **[!UICONTROL Eliminar perfil de procesamiento de imágenes]**.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Si está editando, guarde los cambios. Si elimina, confirme que desea eliminar el perfil.

## Aplicación de un perfil de imagen de Dynamic Media a carpetas {#applying-an-image-profile-to-folders}

Al asignar un perfil de imagen a una carpeta, las subcarpetas heredan automáticamente el perfil de su carpeta principal. Este flujo de trabajo significa que solo puede asignar un perfil de imagen a una carpeta. Como tal, considere detenidamente la estructura de carpetas en la que carga, almacena, utiliza y archiva recursos.

Si asignó un perfil de imagen diferente a una carpeta, el nuevo perfil sobrescribirá el perfil anterior. Los recursos de carpeta existentes no cambian. El nuevo perfil se aplica a los recursos que se agregan a la carpeta más adelante.

Las carpetas que tienen un perfil asignado se indican en la interfaz de usuario por el nombre del perfil que aparece en la tarjeta.

Al agregar un recorte inteligente a un perfil de imagen existente, debe recuperar la variable [Flujo de trabajo de recursos de actualización de DAM](assets-workflow.md) si desea generar cultivos para recursos existentes en el repositorio de recursos.

Puede aplicar Perfiles de imagen a carpetas específicas o globalmente a todos los recursos.

### Aplicación de perfiles de imagen de Dynamic Media a carpetas específicas {#applying-image-profiles-to-specific-folders}

Puede aplicar un perfil de imagen a una carpeta desde el **[!UICONTROL Herramientas]** o si está en la carpeta, desde **[!UICONTROL Propiedades]**. En esta sección se describe cómo aplicar Perfiles de imagen a las carpetas de ambos modos.

Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

#### Aplicación de perfiles de imagen de Dynamic Media a carpetas desde la interfaz de usuario de Perfiles {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de imagen]**.
1. Seleccione el perfil de imagen que desea aplicar a una o varias carpetas.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Toque **[!UICONTROL Aplicar perfil de procesamiento a las carpetas]** y seleccione la carpeta o carpetas múltiples que desee utilizar para recibir los recursos cargados recientemente y toque o haga clic en **[!UICONTROL Aplicar]**. Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

#### Aplicación de perfiles de imagen de Dynamic Media a carpetas desde Propiedades {#applying-image-profiles-to-folders-from-properties}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Recursos]**. A continuación, vaya a la carpeta principal de la carpeta a la que desea aplicar un perfil de imagen.
1. En la carpeta, pulse la marca de verificación para seleccionarla y, a continuación, pulse **[!UICONTROL Propiedades]**.
1. Pulse la pestaña **[!UICONTROL Perfiles de imagen]**. En la lista desplegable **[!UICONTROL Nombre del perfil]**, seleccione el perfil y, a continuación, pulse **[!UICONTROL Guardar y cerrar]**. Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Aplicación global de un perfil de imagen de Dynamic Media {#applying-an-image-profile-globally}

Además de aplicar un perfil a una carpeta, también puede aplicarlo de forma global para que cualquier contenido cargado en AEM Assets en cualquier carpeta tenga aplicado el perfil seleccionado.

**Para aplicar un perfil de imagen de Dynamic Media globalmente**:

1. Realice una de las siguientes acciones:

   * Vaya a **https://&lt;aem server=&quot;&quot;>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam** y aplique el perfil adecuado y pulse **Guardar**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Vaya al CRXDE Lite al nodo siguiente: `/content/dam/jcr:content`.

      Añadir la propiedad `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` y toque **[!UICONTROL Guardar todo]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Edición del recorte inteligente o de la muestra inteligente de una sola imagen {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!NOTE]
El recorte inteligente solo está disponible en el modo Dynamic Media - Scene7.

Puede realinear manualmente o cambiar el tamaño de la ventana de recorte inteligente de una imagen para refinar aún más su punto focal.

Después de editar un recorte inteligente y guardarlo, el cambio se propaga en todas partes donde utilice el recorte para imágenes específicas.

Si es necesario, puede volver a ejecutar el recorte inteligente para volver a generar los cultivos adicionales.

Consulte también [Edición del recorte inteligente o de la muestra inteligente de varias imágenes](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Edición del recorte inteligente o de la muestra inteligente de una sola imagen**:

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Recursos]** y, a continuación, a la carpeta a la que se le haya aplicado un recorte inteligente o un perfil de imagen de muestra inteligente.
1. Abra el contenido tocando la carpeta .
1. Pulse la imagen con el recorte inteligente o la muestra inteligente que desee ajustar.
1. En la barra de herramientas, pulse **[!UICONTROL Recorte inteligente]**.

1. Realice una de las siguientes acciones:

   * Cerca de la esquina superior derecha de la página, arrastre la barra deslizante a la izquierda o a la derecha para aumentar o reducir la visualización de la imagen, respectivamente.
   * En la imagen, arrastre un controlador de esquina para ajustar el tamaño del área visible del recorte o muestra.
   * En la imagen, arrastre el cuadro/muestra a una nueva ubicación. Solo se pueden editar muestras de imágenes; las muestras de color son estáticas.
   * Sobre la imagen, pulse  **[!UICONTROL Revertir]** para deshacer todas las ediciones y restaurar el recorte o muestra original.

1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]** y, a continuación, toque **[!UICONTROL Cerrar]** para volver a la carpeta de recursos.

## Edición del recorte inteligente o de la muestra inteligente de varias imágenes {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Después de aplicar un perfil de imagen (que contiene Recorte inteligente) a una carpeta, todas las imágenes de esa carpeta tienen un recorte aplicado a ellas. Si lo desea, puede *manualmente* vuelva a alinear o cambie el tamaño de la ventana de recorte inteligente en varias imágenes para restringir aún más su punto focal.

Después de editar un recorte inteligente y guardarlo, el cambio se propaga en todas partes donde utilice el recorte para imágenes específicas.

Si es necesario, puede volver a ejecutar el recorte inteligente para volver a generar los cultivos adicionales.

**Editar el recorte inteligente o la muestra inteligente de varias imágenes**:

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Recursos]** y, a continuación, a una carpeta que tenga aplicado un recorte inteligente o un perfil de imagen de muestra inteligente.
1. En la carpeta , pulse el botón **[!UICONTROL Más acciones]** (...) y, a continuación, pulse **[!UICONTROL Recorte inteligente]**.

1. En el **[!UICONTROL Editar recortes inteligentes]** , realice una de las acciones siguientes:

   * Ajuste el tamaño de visualización de las imágenes en la página.

      A la derecha de la lista desplegable de nombre del punto de interrupción, arrastre la barra deslizante hacia la izquierda o la derecha para cambiar el tamaño de la visualización de la imagen visible.

      ![edit_smart_farms-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtre la lista de imágenes visibles en función de los nombres de puntos de interrupción. En el ejemplo siguiente, las imágenes se filtran en el nombre del punto de interrupción &quot;Medio&quot;.

      Cerca de la esquina superior derecha de la página, en la lista desplegable, seleccione un nombre de punto de interrupción para filtrar las imágenes que ve. (Consulte la imagen anterior).

      ![edit_smart_farms-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Cambie el tamaño del cuadro de recorte inteligente. Realice una de las siguientes acciones:

      * Si la imagen tiene un recorte inteligente o solo una muestra inteligente, arrastre en la imagen el controlador de esquina del cuadro de recorte para ajustar el tamaño del área visible del recorte.
      * Si la imagen tiene un recorte inteligente y una muestra inteligente, arrastre el controlador de esquina del cuadro de recorte para ajustar el tamaño del área visible del recorte. O bien, toque o haga clic en la muestra inteligente situada debajo de la imagen (las muestras de color son estáticas) y, a continuación, arrastre el controlador de esquina del cuadro de recorte para ajustar el tamaño del área visible de la muestra.

      ![Cambiar el tamaño del recorte inteligente de una imagen.](assets/edit_smart_crops-resize.png)

   * Mueva el cuadro de recorte inteligente. Realice una de las siguientes acciones:

      * Si la imagen tiene un recorte inteligente o solo una muestra inteligente, arrastre el cuadro de recorte a una nueva ubicación.
      * Si la imagen tiene un recorte inteligente y una muestra inteligente, arrastre el cuadro de recorte inteligente a una nueva ubicación. O bien, toque la muestra inteligente debajo de la imagen (las muestras de color son estáticas) y, a continuación, arrastre el cuadro de recorte de muestras inteligentes a una nueva ubicación.

      ![edit_smart_farms-move](assets/edit_smart_crops-move.png)

   * Deshacer todas las ediciones y restaurar el recorte inteligente o la muestra inteligente original (se aplica solo a la sesión de edición actual).

      Toque **[!UICONTROL Revertir]** encima de la imagen.

      ![edit_smart_farms-revert](assets/edit_smart_crops-revert.png)



1. Cerca de la esquina superior derecha de la página, pulse **[!UICONTROL Guardar]**. a continuación, toque **[!UICONTROL Cerrar]** para volver a la carpeta de recursos.

## Eliminación de un perfil de imagen de las carpetas {#removing-an-image-profile-from-folders}

Al quitar un perfil de imagen de una carpeta, las subcarpetas heredan automáticamente la eliminación del perfil de su carpeta principal. Sin embargo, cualquier procesamiento de archivos que se haya producido dentro de las carpetas permanece intacto.

Puede quitar un perfil de imagen de una carpeta desde la **[!UICONTROL Herramientas]** o si está en la carpeta, desde **[!UICONTROL Propiedades]**. En esta sección se describe cómo quitar perfiles de imagen de las carpetas de ambos modos.

### Eliminación de perfiles de imagen de Dynamic Media de las carpetas mediante la interfaz de usuario Perfiles {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Assets > Perfiles de imagen]**.
1. Seleccione el perfil de imagen que desea eliminar de una carpeta o varias carpetas.
1. Pulse **[!UICONTROL Eliminar perfil de procesamiento de las carpetas]** y seleccione la carpeta o carpetas que desee utilizar para quitar el perfil. A continuación, pulse **[!UICONTROL Eliminar]**.

   Puede confirmar que el perfil de imagen ya no se aplica a una carpeta porque el nombre ya no aparece debajo del nombre de la carpeta.

### Eliminación de perfiles de imagen de Dynamic Media de las carpetas mediante Propiedades {#removing-image-profiles-from-folders-via-properties}

1. Pulse el logotipo de AEM y navegue **[!UICONTROL Recursos]** y, a continuación, a la carpeta desde la que desea eliminar un perfil de imagen.
1. En la carpeta, pulse la marca de verificación para seleccionarla y, a continuación, pulse **[!UICONTROL Propiedades]**.
1. Seleccione el **[!UICONTROL Perfiles de imagen]** pestaña .
1. En el **[!UICONTROL Nombre del perfil]** lista desplegable, seleccione **[!UICONTROL Ninguna]** y, a continuación, toque **[!UICONTROL Guardar y cerrar]**.

   Las carpetas que ya tienen un perfil asignado se indican mediante la visualización del nombre del perfil directamente debajo del nombre de la carpeta.
