---
title: Añadir las funciones de Dynamic Media Classic en la página
seo-title: Añadir las funciones de Dynamic Media Classic en la página
description: Adobe Dynamic Media Classic es una solución alojada para administrar, mejorar, publicar y distribuir recursos de medios enriquecidos en pantallas e impresiones web, móviles, de correo electrónico y conectadas a Internet.
seo-description: Adobe Dynamic Media Classic es una solución alojada para administrar, mejorar, publicar y distribuir recursos de medios enriquecidos en pantallas e impresiones web, móviles, de correo electrónico y conectadas a Internet.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '3428'
ht-degree: 31%

---


# Añadir las funciones de Dynamic Media Classic en la página{#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) es una solución alojada para administrar, mejorar, publicar y distribuir recursos de medios enriquecidos en pantallas e impresiones web, móviles, de correo electrónico y conectadas a Internet.

Puede realizar la vista de AEM recursos publicados en Dynamic Media Classic en varios visores:

* Zoom
* Flotante
* Vídeo
* Plantilla de imagen
* Imagen

Puede publicar recursos digitales directamente desde AEM a Dynamic Media Classic y puede publicarlos de Dynamic Media Classic a AEM.

En esta sección se describe cómo publicar recursos digitales de AEM a Dynamic Media Classic y viceversa. Los visores también se describen en detalle. Para obtener información sobre la configuración de AEM para Dynamic Media Classic, consulte [Integración de Dynamic Media Classic con AEM](/help/sites-administering/scene7.md).

Consulte también [Adición de mapas de imagen](/help/assets/image-maps.md).

Para obtener más información sobre el uso de componentes de vídeo con AEM, consulte lo siguiente:

* [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>If Dynamic Media Classic assets do not display properly, make sure that Dynamic media is [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) and then refresh the page.

## Publicación manual en Dynamic Media Classic desde Assets {#manually-publishing-to-scene-from-assets}

Puede publicar recursos digitales en Dynamic Media Classic desde la consola Recursos en la IU clásica o directamente desde el recurso.

>[!NOTE]
>
>AEM publica en Dynamic Media Classic de forma asíncrona. After you click **[!UICONTROL Publish]**, it may take several seconds for your asset to publish to Dynamic Media Classic.


### Publicación desde la consola Recursos {#publishing-from-the-assets-console}

Para publicar en Dynamic Media Classic desde la consola Recursos si los recursos están en una carpeta de destinatario de Dynamic Media Classic:

1. In the AEM classic UI, click **[!UICONTROL Digital Assets]** to access the digital asset manager.

1. Select the asset (or assets) or folder from within the target folder you want to publish to Dynamic Media Classic and right-click and select **[!UICONTROL Publish to Dynamic Media Classic]**. También puede seleccionar **[!UICONTROL Publicar en Dynamic Media Classic]** en el menú **[!UICONTROL Herramientas] .

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Vaya a Dynamic Media Classic y confirme que los recursos están disponibles.

   >[!NOTE]
   >
   >If the assets are not in a Dynamic Media Classic synchronized folder, **[!UICONTROL Publish to Dynamic Media Classic]** in both menus is visible but disabled.

### Publicación desde un recurso {#publishing-from-an-asset}

Puede publicar manualmente un recurso siempre que se encuentre dentro de la carpeta de Dynamic Media Classic sincronizada.

>[!NOTE]
>
>Si el recurso no se encuentra en la carpeta sincronizada de Dynamic Media Classic, el vínculo para **[!UICONTROL publicar en Dynamic Media Classic]** no estará disponible.

**Para publicar en Dynamic Media Classic directamente desde un recurso** digital:

1. En AEM, haga clic en **[!UICONTROL Recursos digitales]** para acceder al administrador de recursos digitales.

1. Haga doble clic en dicha opción para abrir un recurso.

1. En el panel de detalles del recurso, seleccione **[!UICONTROL Publicar en Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. El vínculo cambia a **[!UICONTROL Publicando...]** y, a continuación, a **[!UICONTROL Publicado]**. Vaya a Dynamic Media Classic y confirme que el recurso está disponible.

   >[!NOTE]
   >
   >If the asset does not publish properly to Dynamic Media Classic, the link changes to **[!UICONTROL Publishing Failed]**. Si el recurso ya se ha publicado en Dynamic Media Classic, el vínculo lee **[!UICONTROL Volver a publicar en Dynamic Media Classic]**. La republicación le permite realizar cambios en un recurso en AEM y volver a publicarlo.

### Publishing assets from outside the CQ target folder {#publishing-assets-from-outside-the-cq-target-folder}

Adobe recomienda publicar recursos en Dynamic Media Classic solo desde los recursos de la carpeta de destinatario de Dynamic Media Classic. However, if you need to upload assets from a folder outside of the target folder, you can still do that by uploading them to an *ad-hoc* folder on Dynamic Media Classic.

Para ello, configure la configuración de la nube para la página en la que aparecerá el recurso. A continuación, agregue un componente de Dynamic Media Classic a la página y arrastre y suelte un recurso en el componente. After the page properties are set for that page, a **[!UICONTROL Publish to Dynamic Media Classic]** link appears that when selected triggers uploading to Dynamic Media Classic.

>[!NOTE]
>
>Los recursos que se encuentran en la carpeta ad-hoc no aparecen en el navegador de contenido de Dynamic Media Classic.

**Para publicar los recursos que residen fuera de la carpeta de destino de CQ**:

1. In AEM in the classic UI, click **[!UICONTROL Websites]** and navigate to the web page that you want to add a digital asset to that is not yet published to Dynamic Media Classic. (Se aplican las reglas de herencia de página habituales).

1. In the sidekick, click the **[!UICONTROL Page]** icon, then click **[!UICONTROL Page Properties]**.

1. Haga clic en **[!UICONTROL Cloud Services]>[!UICONTROL Añadir servicios]>[!UICONTROL Dynamic Media Classic (Scene7)]**.
1. En la lista desplegable Adobe Dynamic Media Classic, seleccione la configuración que desee y haga clic en **[!UICONTROL Aceptar]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. En la página web, agregue un componente de Dynamic Media Classic (Scene7) a la ubicación deseada en la página.
1. En el buscador de contenido, arrastre un recurso digital hasta el componente. Puede ver un vínculo para **[!UICONTROL comprobar el estado]** de publicación de Dynamic Media Classic.

   >[!NOTE]
   >
   >If the digital asset is in the CQ target folder, then no link to **[!UICONTROL Check Dynamic Media Classic Publication Status]** appears. Los recursos simplemente se colocan en el componente.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Haga clic en **[!UICONTROL Comprobar el estado]** de publicación de Dynamic Media Classic. Si el recurso no está publicado, AEM publica el recurso en Dynamic Media Classic. Una vez cargado, el recurso se encuentra en la carpeta ad hoc. De forma predeterminada, la carpeta ad-hoc se encuentra en la `name_of_the_company/CQ5_adhoc`. Puede [configurarla, si es necesario](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Si el recurso no está en una carpeta sincronizada de Dynamic Media Classic y no hay ninguna configuración de nube de Dynamic Media Classic asociada a la página actual, la carga fallará.

## Componentes de Dynamic Media Classic (Scene7) {#scene-components}

Los siguientes componentes de Dynamic Media Classic están disponibles en AEM:

* Zoom
* Flotante (zoom)
* Plantilla de imagen
* Imagen
* Vídeo

>[!NOTE]
>
>These components are not available by default and need to be selected in **[!UICONTROL Design]** mode before using.

After they are made available in **[!UICONTROL Design]** mode, you can add the components to your page like any other AEM component. Los recursos que aún no se han publicado en Dynamic Media Classic se publican en Dynamic Media Classic si se encuentran en una carpeta sincronizada o en una página o con una configuración de nube de Dynamic Media Classic.

### Flash viewers end-of-life notice {#flash-viewers-end-of-life-notice}

A partir del 31 de enero de 2017, Adobe Dynamic Media Classic dejó de ofrecer asistencia técnica para la plataforma del visor de Flash.

For more information about this important change, see [Flash viewer end-of-life FAQs](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Adding a Dynamic Media Classic component to a page {#adding-a-scene-component-to-a-page}

Añadir un componente de Dynamic Media Classic en una página es lo mismo que agregar un componente a cualquier página. Los componentes de Dynamic Media Classic se describen en detalle en las siguientes secciones.

**Para agregar un componente o visor de Dynamic Media Classic a una página de la IU** clásica:

1. En AEM, abra la página en la que desea agregar el componente de Dynamic Media Classic.

1. If no Dynamic Media Classic components are available, click the ruler in the sidekick to enter **[!UICONTROL Design]** mode, click **[!UICONTROL Edit]** parsys, and select all the **[!UICONTROL Dynamic Media Classic]** components to make them available.

1. Return to **[!UICONTROL Edit]** mode by clicking the pencil in the sidekick.

1. Drag a component from the **[!UICONTROL Dynamic Media Classic]** group in the sidekick onto the page in the desired location.

1. Haga clic en **[!UICONTROL Editar]** para abrir el componente.

1. Edite el componente según sea necesario y haga clic en **[!UICONTROL Aceptar]** para guardar los cambios.

### Adición de experiencias de visualización interactiva a un sitio web con capacidad de respuesta {#adding-interactive-viewing-experiences-to-a-responsive-website}

El diseño interactivo para sus recursos implica que estos se ajustan según el lugar en que se muestren. Con el diseño interactivo, los mismos recursos se muestran de forma eficaz en varios dispositivos.

**Para añadir una experiencia de visualización interactiva a un sitio interactivo en la interfaz de usuario clásica**:

1. Log in to AEM, and ensure that you have [configured Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) and that Dynamic Media Classic components are available.

   >[!NOTE]
   >
   >Si los componentes WCM de Dynamic Media Classic no están disponibles, asegúrese de activarlos mediante el modo **[!UICONTROL Diseño] .

1. In a website with the Dynamic Media Classic components enabled, drag an **[!UICONTROL Image]** viewer to the page.
1. Edit the component and adjust the breakpoints in the **[!UICONTROL Dynamic Media Classic Settings]** tab.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Confirme que los visores cambian de tamaño de manera interactiva y que las interacciones están optimizadas para dispositivos de escritorio, tabletas y móviles.

### Configuración común a todos los componentes de Dynamic Media Classic {#settings-common-to-all-scene-components}

Aunque las opciones de configuración varían, las siguientes son comunes a todos los componentes de Dynamic Media Classic:

* **[!UICONTROL Referencia del archivo]**: navegue a un archivo al que quiera hacer referencia. La referencia de archivo muestra la URL del recurso y no necesariamente la URL completa de Dynamic Media Classic, incluidos los comandos y parámetros de URL. En este campo no se pueden agregar comandos ni parámetros de URL de Dynamic Media Classic. Deben añadirse mediante la funcionalidad correspondiente del componente.
* **[!UICONTROL Anchura]**: le permite definir la anchura.
* **[!UICONTROL Altura]**: le permite definir la altura.

You set these configuration options by double-clicking a Dynamic Media Classic component, for example, when you open a **[!UICONTROL Zoom]** component:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

El componente Zoom HTML5 muestra una imagen más grande al pulsar el botón +.

El recurso dispone de herramientas de zoom en la parte inferior. Haga clic en **[!UICONTROL +]** para ampliar. Haga clic en **[!UICONTROL -]** para reducir. Clicking **[!UICONTROL x]** or the reset zoom arrow brings the image back to the original size it was imported as. Haga clic en las flechas diagonales para pasar a pantalla completa. Haga clic en **[!UICONTROL Editar]** para configurar el componente. With this component, you can configure [settings common to all Dynamic Media Classic components](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flotante {#flyout}

En el componente Flotante HTML5, el recurso se muestra como una pantalla dividida: a la izquierda aparece con el tamaño especificado y a la derecha aparece la porción modificada con el zoom. Haga clic en **[!UICONTROL Editar]** para configurar el componente. With this component, you can configure [settings common to all Dynamic Media Classic components](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Si el componente Flotante utiliza un tamaño personalizado, se utiliza dicho tamaño y se desactiva la configuración interactiva del componente.
>
>If your Flyout component uses the default size, as set in the [!UICONTROL Design] view, then the default size is used and the component stretches to accomodate the page layout size with responsive setup of the component enabled. Sin embargo, tenga en cuenta que existe una limitación en la configuración interactiva del componente. Al utilizar el componente Flotante con la configuración interactiva, no debe usarlo con la ampliación de página completa. De lo contrario, el menú flotante puede extenderse más allá del borde derecho de la página.

![chlimage_1-81](assets/chlimage_1-81.png)

### Imagen {#image}

El componente de imagen de Dynamic Media Classic le permite añadir la funcionalidad de Dynamic Media Classic a sus imágenes, como los modificadores de Dynamic Media Classic, los ajustes preestablecidos de imagen o visor y el enfoque. El componente de imagen de Dynamic Media Classic es similar a otros componentes de imagen en AEM con la funcionalidad especial de Dynamic Media Classic. En este ejemplo, la imagen tiene el modificador de URL de Dynamic Media Classic, `&op_invert=1` aplicado.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Título, Texto]** alternativo: en la ficha [!UICONTROL Avanzado] , agregue un título a la imagen y texto alternativo para los usuarios que tienen gráficos desactivados.

**[!UICONTROL URL, Abrir en]** : puede definir un recurso desde para abrir un vínculo. Set the **[!UICONTROL URL]** and **[!UICONTROL Open in]** to indicate whether you want it to open in the same window or a new window.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Ajuste preestablecido]** de visor: seleccione un ajuste preestablecido de visor existente en el menú desplegable. Si el ajuste preestablecido de visor que busca no está visible, es posible que tenga que hacerlo visible. Consulte [Administración de ajustes preestablecidos de visor](/help/assets/managing-viewer-presets.md). No es posible seleccionar un ajuste preestablecido de visor si utiliza un ajuste preestablecido de imagen, y viceversa.

**[!UICONTROL Configuración]** de Dynamic Media Classic: seleccione la configuración de Dynamic Media Classic que desee utilizar para recuperar los ajustes preestablecidos de imagen activos de Scene7 Publishing System.

**[!UICONTROL Ajuste preestablecido]** de imagen: seleccione un ajuste preestablecido de imagen existente en el menú desplegable. Si el ajuste preestablecido de imagen que busca no está visible, es posible que tenga que hacerlo visible. Consulte [Administración de ajustes preestablecidos de imagen](/help/assets/managing-image-presets.md). No es posible seleccionar un ajuste preestablecido de visor si utiliza un ajuste preestablecido de imagen, y viceversa.

**[!UICONTROL Formato]** de salida: seleccione el formato de salida de la imagen, por ejemplo jpeg. En función del formato de salida que seleccione, puede tener opciones de configuración adicionales. Consulte [Administración de ajustes preestablecidos de imagen](/help/assets/managing-image-presets.md).

**[!UICONTROL Enfoque]** : seleccione cómo desea enfocar la imagen. El enfoque se explica en detalle en Calidad de imagen de Dynamic Media Classic de [*Adobe y en Optimizaciones*](/help/assets/assets/s7_sharpening_images.pdf) de enfoque.

**[!UICONTROL Modificadores]** de URL: puede cambiar los efectos de imagen proporcionando comandos de imagen adicionales de Dynamic Media Classic. These are described in [Managing Image Presets](/help/assets/managing-image-presets.md) and the [Command reference](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Puntos de interrupción]** : si el sitio web responde, desea ajustar los puntos de interrupción. Los puntos de interrupción deben separarse con comas `,`.

### Plantilla de imagen {#image-template}

[Las plantillas](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) de imagen de Dynamic Media Classic son contenido de Photoshop con capas que se importó a Dynamic Media Classic, donde el contenido y las propiedades se parametrizaron para la variabilidad. El componente **[!UICONTROL Plantilla de imagen]** le permite importar imágenes y cambiar el texto de forma dinámica en AEM. Además, puede configurar el componente **[!UICONTROL Plantilla de imágenes]** para utilizar valores de ClientContext, de modo que cada usuario experimenta la imagen de una forma personalizada.

Haga clic en **[!UICONTROL Editar]** para configurar el componente. You can configure [settings common to all Dynamic Media Classic components](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) as well as other settings described in this section.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Referencia de archivo, Ancho, Altura]** : consulte los ajustes comunes a todos los componentes de Dynamic Media Classic.

>[!NOTE]
>
>Los comandos y parámetros de URL de Dynamic Media Classic no se pueden agregar directamente a la URL de referencia de archivo. Solo se pueden definir en la interfaz de usuario del componente en el panel **[!UICONTROL Parámetro]**.

**[!UICONTROL Título, Texto]** alternativo En la ficha Plantilla  de imagen de Dynamic Media Classic, agregue un título a la imagen y texto alternativo para los usuarios que tengan gráficos desactivados.

**[!UICONTROL URL, Abrir en]** Puede definir un recurso desde para abrir un vínculo. Defina la **[!UICONTROL dirección URL]** y, en **[!UICONTROL Abrir en]**, indique si quiere que se abra en la misma ventana o en una nueva.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Panel]** de parámetros Al importar una imagen, los parámetros se rellenan previamente con información de la imagen. Si no existe contenido que se pueda cambiar de forma dinámica, esta ventana está vacía.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Cambio del texto de forma dinámica {#changing-text-dynamically}

Para cambiar el texto de forma dinámica, escriba el nuevo texto en los campos y haga clic en **[!UICONTROL Aceptar]**. En este ejemplo, el **[!UICONTROL Precio]** es ahora $50 y el envío cuesta 99 centavos.

![chlimage_1-86](assets/chlimage_1-86.png)

El texto de la imagen cambia. Para restablecer el texto al valor original, haga clic en **[!UICONTROL Restablecer]** junto al campo.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Cambio del texto para reflejar un valor de ClientContext {#changing-text-to-reflect-the-value-of-a-client-context-value}

To link a field to a client context value, click **[!UICONTROL Select]** to open the client-context menu, select the client context, and click **[!UICONTROL OK]**. En este ejemplo, el nombre cambia en función de la vinculación de valor de Nombre con el nombre con formato que consta en el perfil.

![chlimage_1-88](assets/chlimage_1-88.png)

El texto refleja el nombre del usuario de la sesión actual. Para restablecer el texto al valor original, haga clic en **[!UICONTROL Restablecer]** junto al campo.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Convertir la plantilla de imagen de Dynamic Media Classic en un vínculo {#making-the-scene-image-template-a-link}

**Para convertir la plantilla de imagen de Dynamic Media Classic en un vínculo**:

1. On the page with the Dynamic Media Classic image template component, click **[!UICONTROL Edit]**.
1. En el campo **[!UICONTROL URL]**, introduzca la dirección URL a la que los usuarios se dirigen al hacer clic en la imagen. In the **[!UICONTROL Open in]** field, select whether you want the target to open (a new window or same window).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Haga clic en **[!UICONTROL OK]**.

### Componente de vídeo {#video-component}

The Dynamic Media Classic **[!UICONTROL Video]** component (available from the Dynamic Media Classic section of the sidekick) uses device and bandwidth detection to serve the right video to each screen. Este componente es un reproductor de vídeo HTML5; se trata de un visor único que se puede utilizar en múltiples canales.

Se puede usar para conjuntos de vídeos adaptables, un solo vídeo MP4 o un solo vídeo F4V.

See [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) for more information on how videos work with Dynamic Media Classic integration. In addition, see how [the **Dynamic Media Classic video** component compares to the foundation **video** component](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-91](assets/chlimage_1-91.png)

### Limitaciones conocidas del componente de vídeo {#known-limitations-for-the-video-component}

Adobe DAM y WCM muestran si se ha cargado un vídeo maestro. No muestran estos recursos de proxy:

* Representaciones codificadas de Dynamic Media Classic
* Conjuntos de vídeos adaptables de Dynamic Media Classic

Al utilizar un conjunto de vídeos adaptables con el componente de vídeo de Dynamic Media Classic, debe cambiar el tamaño del componente para adaptarlo a las dimensiones del vídeo.

## Navegador de contenido de Dynamic Media Classic {#scene-content-browser}

El navegador de contenido de Dynamic Media Classic permite la vista de contenido desde Dynamic Media Classic directamente en AEM. To access the content browser, in the Content Finder, select **[!UICONTROL Dynamic Media Classic]** in the touch-optimized user interface or the **[!UICONTROL S7]** icon in the classic user interface. La funcionalidad es idéntica en ambas interfaces de usuario.

Si tiene varias configuraciones, AEM muestra de forma predeterminada la [configuración predeterminada](/help/sites-administering/scene7.md#configuring-a-default-configuration). Puede seleccionar diferentes configuraciones directamente en el navegador de contenido de Dynamic Media Classic en el menú desplegable.

>[!NOTE]
>
>* Los recursos ubicados en la carpeta ad-hoc no aparecen en el navegador de contenido de Dynamic Media Classic.
>* Cuando la Previsualización [segura está activada](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), los recursos publicados y no publicados en Dynamic Media Classic aparecen en el navegador de contenido de Dynamic Media Classic.
>* If you do not see **[!UICONTROL Dynamic Media Classic]** or the **[!UICONTROL S7]** icon as an option in the content browser, you need to [configure Dynamic Media Classic to work with AEM](/help/sites-administering/scene7.md).

   >
   >
* Para vídeo, el navegador de contenido de Dynamic Media Classic admite:
   >
   >
* Conjuntos de vídeos adaptables: contenedor de todas las representaciones de vídeo necesarias para la reproducción sin errores en varias pantallas.
>* Vídeo MP4 sencillo
>* Vídeo F4V sencillo


### Exploración del contenido en la interfaz de usuario clásica {#browsing-content-in-the-classic-ui}

Para examinar el contenido de Dynamic Media Classic, haga clic en la ficha **[!UICONTROL S7]** .

Puede cambiar la configuración a la que accede seleccionando la configuración. Las carpetas cambian según la configuración seleccionada.

![chlimage_1-92](assets/chlimage_1-92.png)

Al igual que ocurre con el buscador de contenido para los recursos, puede buscar recursos y filtrar los resultados. Sin embargo, a diferencia del buscador de recursos, al introducir una palabra clave en la pestaña **[!UICONTROL S7]**, el nombre del archivo *comienza por* la cadena introducida, en lugar de *contener* la palabra clave en el nombre de archivo.

De forma predeterminada, los recursos se muestran por el nombre de archivo. También puede filtrar los resultados por el tipo de recurso.

>[!NOTE]
>
>Para vídeo, el navegador de contenido de Dynamic Media Classic de WCM admite:
>
>* Conjuntos de vídeos adaptables: contenedor de todas las representaciones de vídeo necesarias para la reproducción sin errores en varias pantallas.
>* Vídeo MP4 sencillo
>* Vídeo F4V sencillo

>



### Búsqueda de recursos de Dynamic Media Classic con el navegador de contenido {#searching-for-scene-assets-with-the-content-browser}

La búsqueda de recursos de Dynamic Media Classic es similar a la búsqueda de recursos de AEM, excepto que cuando realiza una búsqueda, verá una vista remota de los recursos en el sistema de Dynamic Media Classic, en lugar de importarlos directamente a AEM.

Puede utilizar la interfaz de usuario clásica o la optimizada para el uso táctil para ver y buscar recursos. Según la interfaz, la búsqueda es ligeramente diferente.

Al buscar en cualquier interfaz de usuario, puede filtrar según los criterios siguientes (aquí se muestra la IU optimizada para el uso táctil):

**[!UICONTROL Escriba palabras clave]** : puede buscar recursos por nombre. Al buscar, las palabras clave que introduce es por lo que comienza el nombre de archivo. Por ejemplo, al escribir la palabra “natación”, el sistema buscaría cualquier nombre de archivo de recurso que comience por esas letras en ese orden. Asegúrese de hacer clic en Entrar después de escribir el término para buscar el recurso.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Carpeta/ruta]** : el nombre de la carpeta que aparece se basa en la configuración seleccionada. Para ver los niveles inferiores, haga clic en el icono de carpeta, seleccione una subcarpeta y, a continuación, haga clic en la marca de verificación para seleccionarla.

Si introduce una palabra clave y selecciona una carpeta, AEM realiza la búsqueda en esa carpeta y todas las subcarpetas. Sin embargo, si no introduce ninguna palabra clave cuando realice la búsqueda, al seleccionar la carpeta solo se mostrarán los recursos de esa carpeta y no se incluirá ninguna de las subcarpetas.

De forma predeterminada, AEM realiza la búsqueda en la carpeta seleccionada y todas las subcarpetas.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Tipo de recurso]** Seleccione Dynamic Media Classic para examinar el contenido de Dynamic Media Classic. Esta opción solo está disponible si ya ha configurado Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**[!UICONTROL Configuración]** Si tiene más de una configuración de Dynamic Media Classic definida en [!UICONTROL Cloud Services], puede seleccionarla aquí. Como resultado, la carpeta cambiará según la configuración que haya elegido.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Tipo]** de recurso En el navegador de Dynamic Media Classic, puede filtrar los resultados para incluir cualquiera de los siguientes elementos: imágenes, plantillas, vídeos y conjuntos de vídeos adaptables. Si no selecciona ningún tipo de recurso, AEM busca de manera predeterminada todos los tipos de recursos.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Al buscar vídeos, se busca una sola representación. Los resultados devuelven la representación original (solo &amp;ast;.mp4) y la representación codificada.
>* Al buscar un conjunto de vídeos adaptables, busca en la carpeta y en todas las subcarpetas, pero solo si ha agregado una palabra clave a la búsqueda. Si no ha añadido ninguna palabra clave, AEM no busca en las subcarpetas.

>



**[!UICONTROL Estado]** de publicación Puede filtrar los recursos en función del estado de publicación: [!UICONTROL Publicado] o [!UICONTROL sin publicar]. If you do not select any [!UICONTROL Publish status], AEM by default searches all publish statuses.

![chlimage_1-98](assets/chlimage_1-98.png)

