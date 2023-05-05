---
title: Adición de funciones de Dynamic Media Classic a la página
seo-title: Adding Dynamic Media Classic features to your page
description: Adobe Dynamic Media Classic es una solución alojada para administrar, mejorar, publicar y distribuir recursos de medios enriquecidos en la Web, dispositivos móviles, correo electrónico y pantallas e impresiones conectadas a Internet.
seo-description: Adobe Dynamic Media Classic is a hosted solution for managing, enhancing, publishing, and delivering rich media assets to Web, mobile, email, and Internet-connected displays and print.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
exl-id: 93921d23-a2bf-43b6-b002-58a7482b22b0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3383'
ht-degree: 0%

---

# Adición de funciones de Dynamic Media Classic a la página{#adding-scene-features-to-your-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Dynamic Media Classic es una solución alojada para administrar, mejorar, publicar y distribuir recursos de medios enriquecidos en la Web, dispositivos móviles, correo electrónico y pantallas e impresiones conectadas a Internet.

Puede ver AEM recursos publicados en Dynamic Media Classic en varios visores:

* Acercar o alejar
* Flotante
* Vídeo
* Plantilla de imagen
* Imagen

Puede publicar recursos digitales directamente de AEM a Dynamic Media Classic y hacerlo desde Dynamic Media Classic a AEM.

En esta sección se describe cómo publicar recursos digitales de AEM a Dynamic Media Classic y viceversa. Los visualizadores también se describen en detalle. Para obtener información sobre la configuración de AEM para Dynamic Media Classic, consulte [Integración de Dynamic Media Classic con AEM](/help/sites-administering/scene7.md).

Consulte también [Adición de mapas de imagen](/help/assets/image-maps.md).

Para obtener más información sobre el uso de componentes de vídeo con AEM, consulte lo siguiente:

* [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Si los recursos de Dynamic Media Classic no se muestran correctamente, asegúrese de que Dynamic Media esté [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) y, a continuación, actualice la página.

## Publicación manual en Dynamic Media Classic desde Assets {#manually-publishing-to-scene-from-assets}

Puede publicar recursos digitales en Dynamic Media Classic desde la consola Recursos en la IU clásica o directamente desde el recurso.

>[!NOTE]
>
>AEM publica en Dynamic Media Classic de forma asíncrona. Después de hacer clic en **[!UICONTROL Publicación]**, puede tardar varios segundos en que el recurso se publique en Dynamic Media Classic.

### Publicación desde la consola Recursos {#publishing-from-the-assets-console}

Para publicar en Dynamic Media Classic desde la consola Recursos si los recursos están en una carpeta de destino de Dynamic Media Classic:

1. En la IU clásica AEM, haga clic en **[!UICONTROL Recursos digitales]** para acceder al administrador de recursos digitales.

1. Seleccione el recurso (o recursos) o la carpeta de la carpeta de destino que desea publicar en Dynamic Media Classic, haga clic con el botón derecho y seleccione **[!UICONTROL Publicar en Dynamic Media Classic]**. También puede seleccionar **[!UICONTROL Publicar en Dynamic Media Classic]** de la variable **[!UICONTROL Herramientas]** para abrir el Navegador.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Vaya a Dynamic Media Classic y confirme que los recursos están disponibles.

   >[!NOTE]
   >
   >Si los recursos no están en una carpeta sincronizada de Dynamic Media Classic, **[!UICONTROL Publicar en Dynamic Media Classic]** en ambos menús está visible pero desactivada.

### Publicación desde un recurso {#publishing-from-an-asset}

Puede publicar manualmente un recurso siempre que este se encuentre dentro de la carpeta sincronizada de Dynamic Media Classic.

>[!NOTE]
>
>Si el recurso no está ubicado en la carpeta sincronizada de Dynamic Media Classic, el vínculo a **[!UICONTROL Publicar en Dynamic Media Classic]** no está disponible.

**Para publicar en Dynamic Media Classic directamente desde un recurso digital**:

1. En AEM, haga clic en **[!UICONTROL Recursos digitales]** para acceder al administrador de recursos digitales.

1. Haga doble clic para abrir un recurso.

1. En el panel de detalles del recurso, seleccione **[!UICONTROL Publicar en Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. El vínculo cambia a **[!UICONTROL Publicando...]** y luego **[!UICONTROL Publicado]**. Vaya a Dynamic Media Classic y confirme que el recurso está disponible.

   >[!NOTE]
   >
   >Si el recurso no se publica correctamente en Dynamic Media Classic, el vínculo cambia a **[!UICONTROL Error de publicación]**. Si el recurso ya se ha publicado en Dynamic Media Classic, el vínculo es **[!UICONTROL Volver a publicar en Dynamic Media Classic]**. La republicación permite realizar cambios en un recurso en AEM y volver a publicarlo.

### Publicación de recursos desde fuera de la carpeta de destino de CQ {#publishing-assets-from-outside-the-cq-target-folder}

Adobe recomienda publicar recursos en Dynamic Media Classic solo desde recursos de la carpeta de destino de Dynamic Media Classic. Sin embargo, si necesita cargar recursos de una carpeta que esté fuera de la carpeta de destino, puede hacerlo cargándolos en una *ad-hoc* en Dynamic Media Classic.

Para ello, configure la configuración de Cloud para la página en la que aparecerá el recurso. A continuación, agregue un componente Dynamic Media Classic a la página y arrastre y suelte un recurso en el componente. Una vez que se hayan establecido las propiedades de página para esa página, se enviará una **[!UICONTROL Publicar en Dynamic Media Classic]** aparece que, cuando se selecciona, los déclencheur se cargan en Dynamic Media Classic.

>[!NOTE]
>
>Los recursos que se encuentran en la carpeta ad hoc no aparecen en el navegador de contenido de Dynamic Media Classic.

**Para publicar recursos que residen fuera de la carpeta de destino de CQ**:

1. En AEM en la IU clásica, haga clic en **[!UICONTROL Sitios web]** y vaya a la página web a la que desee agregar un recurso digital que aún no se haya publicado en Dynamic Media Classic. (Se aplican las reglas de herencia de página normales).

1. En la barra de tareas, haga clic en la **[!UICONTROL Página]** y, a continuación, haga clic en **[!UICONTROL Propiedades de página]**.

1. Haga clic en **[!UICONTROL Cloud Services] > [!UICONTROL Añadir servicios] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. En la lista desplegable Adobe Dynamic Media Classic , seleccione la configuración que desee y haga clic en **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. En la página web, agregue un componente Dynamic Media Classic (Scene7) a la ubicación deseada en la página.
1. En el buscador de contenido, arrastre un recurso digital al componente. Verá un vínculo a **[!UICONTROL Comprobar el estado de publicación de Dynamic Media Classic]**.

   >[!NOTE]
   >
   >Si el recurso digital está en la carpeta de destino de CQ, no hay vínculo a **[!UICONTROL Comprobar el estado de publicación de Dynamic Media Classic]** aparece. Los recursos simplemente se colocan en el componente.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Haga clic en **[!UICONTROL Comprobar el estado de publicación de Dynamic Media Classic]**. Si el recurso no está publicado, AEM publica el recurso en Dynamic Media Classic. Una vez cargado, el recurso se encuentra en la carpeta ad hoc. De forma predeterminada, la carpeta ad hoc se encuentra en la `name_of_the_company/CQ5_adhoc`. Puede [configure esto, si es necesario](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Si el recurso no está en una carpeta sincronizada de Dynamic Media Classic y no hay ninguna configuración de nube de Dynamic Media Classic asociada a la página actual, la carga fallará.

## Componentes de Dynamic Media Classic (Scene7) {#scene-components}

Los siguientes componentes de Dynamic Media Classic están disponibles en AEM:

* Acercar o alejar
* Flotante (zoom)
* Plantilla de imagen
* Imagen
* Vídeo

>[!NOTE]
>
>Estos componentes no están disponibles de forma predeterminada y deben seleccionarse en **[!UICONTROL Diseño]** antes de utilizar.

Una vez que estén disponibles en **[!UICONTROL Diseño]** , puede añadir los componentes a la página como cualquier otro componente de AEM. Los recursos que aún no se han publicado en Dynamic Media Classic se publican en Dynamic Media Classic si se encuentran en una carpeta sincronizada o en una página o con una configuración de nube de Dynamic Media Classic.

### Aviso de fin de vida útil de los visores de Flash {#flash-viewers-end-of-life-notice}

A partir del 31 de enero de 2017, Adobe Dynamic Media Classic dejó oficialmente de ofrecer asistencia para la plataforma del visor de Flash.

### Adición de un componente de Dynamic Media Classic a una página {#adding-a-scene-component-to-a-page}

Añadir un componente Dynamic Media Classic a una página es lo mismo que añadir un componente a cualquier página. Los componentes de Dynamic Media Classic se describen en detalle en las secciones siguientes.

**Para añadir un componente/visor de Dynamic Media Classic a una página en la IU clásica**:

1. En AEM, abra la página a la que desee añadir el componente Dynamic Media Classic.

1. Si no hay componentes de Dynamic Media Classic disponibles, haga clic en la regla de la barra de tareas para entrar **[!UICONTROL Diseño]** modo, haga clic en **[!UICONTROL Editar]** parsys y seleccione todas las **[!UICONTROL Dynamic Media Classic]** componentes para que estén disponibles.

1. Volver a **[!UICONTROL Editar]** haciendo clic en el lápiz de la barra de tareas.

1. Arrastre un componente desde la **[!UICONTROL Dynamic Media Classic]** en la barra de tareas hasta la página en la ubicación deseada.

1. Haga clic en **[!UICONTROL Editar]** para abrir el componente.

1. Edite el componente según sea necesario y haga clic en **[!UICONTROL OK]** para guardar los cambios.

### Adición de experiencias de visualización interactivas a un sitio web interactivo {#adding-interactive-viewing-experiences-to-a-responsive-website}

El diseño interactivo de los recursos significa que estos se adaptan según el lugar en que se muestren. Con el diseño interactivo, los mismos recursos se muestran de forma eficaz en varios dispositivos.

**Para añadir una experiencia de visualización interactiva a un sitio interactivo en la IU clásica**:

1. Inicie sesión en AEM y asegúrese de que ha [Cloud Services configurados de Adobe Dynamic Media Classic](/help/sites-administering/scene7.md#configuring-scene-integration) y que los componentes de Dynamic Media Classic están disponibles.

   >[!NOTE]
   >
   >Si los componentes WCM de Dynamic Media Classic no están disponibles, asegúrese de habilitarlos mediante **[!UICONTROL Diseño] en el menú contextual.

1. En un sitio web con los componentes de Dynamic Media Classic activados, arrastre y **[!UICONTROL Imagen]** del visor a la página.
1. Edite el componente y ajuste los puntos de interrupción en el **[!UICONTROL Configuración de Dynamic Media Classic]** pestaña .

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Confirme que los visualizadores cambian de tamaño de forma interactiva y que todas las interacciones están optimizadas para escritorio, tableta y móvil.

### Configuración común a todos los componentes de Dynamic Media Classic {#settings-common-to-all-scene-components}

Aunque las opciones de configuración varían, las siguientes son comunes a todos los componentes de Dynamic Media Classic:

* **[!UICONTROL Referencia de archivo]** - Busque el archivo al que desee hacer referencia. La referencia de archivo muestra la URL del recurso y no necesariamente la URL completa de Dynamic Media Classic, incluidos los comandos y parámetros de URL. No se pueden agregar comandos y parámetros de URL de Dynamic Media Classic en este campo. Deben añadirse a través de la funcionalidad correspondiente del componente.
* **[!UICONTROL Anchura]** - Permite definir la anchura.
* **[!UICONTROL Altura]** - Permite establecer la altura.

Para establecer estas opciones de configuración, haga doble clic en un componente de Dynamic Media Classic, por ejemplo, al abrir un **[!UICONTROL Zoom]** componente:

![chlimage_1-80](assets/chlimage_1-80.png)

### Acercar o alejar {#zoom}

El componente Zoom HTML5 muestra una imagen más grande al pulsar el botón +.

El recurso tiene herramientas de zoom en la parte inferior. Haga clic en **[!UICONTROL +]** para ampliar. Haga clic en **[!UICONTROL -]** para reducir. Hacer clic **[!UICONTROL x]** o la flecha para restablecer el zoom devuelve la imagen al tamaño original que se importó como. Haga clic en las flechas diagonales para convertirlas en pantalla completa. Haga clic en **[!UICONTROL Editar]** para configurar el componente. Con este componente, puede configurar [configuración común a todos los componentes de Dynamic Media Classic](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flotante {#flyout}

En el componente Flotante de HTML5, el recurso se muestra como pantalla dividida; dejó el recurso en el tamaño especificado; a la derecha se muestra la porción de zoom. Haga clic en **[!UICONTROL Editar]** para configurar el componente. Con este componente, puede configurar [configuración común a todos los componentes de Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Si el componente Flotante utiliza un tamaño personalizado, se utiliza ese tamaño personalizado y se desactiva la configuración interactiva del componente.
>
>Si el componente Flotante utiliza el tamaño predeterminado, tal como se establece en la variable [!UICONTROL Diseño] , se utiliza el tamaño predeterminado y el componente se expande para adaptarse al tamaño del diseño de página con la configuración interactiva del componente activada. Sin embargo, tenga en cuenta que hay una limitación en la configuración interactiva del componente. Cuando se utiliza el componente Flotante con configuración interactiva, no se debe utilizar con la ampliación de página completa. De lo contrario, el menú flotante podría extenderse más allá del borde derecho de la página.

![chlimage_1-81](assets/chlimage_1-81.png)

### Imagen {#image}

El componente Imagen de Dynamic Media Classic le permite añadir funciones de Dynamic Media Classic a sus imágenes, como modificadores de Dynamic Media Classic, ajustes preestablecidos de imágenes o visores y nitidez. El componente de imagen de Dynamic Media Classic es similar a otros componentes de imagen en AEM con funcionalidad especial de Dynamic Media Classic. En este ejemplo, la imagen tiene el modificador Dynamic Media Classic URL, `&op_invert=1` aplicado.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Título, Texto alternativo]** - En el [!UICONTROL Avanzadas] , añada un título a la imagen y texto alternativo para los usuarios que tengan los gráficos desactivados.

**[!UICONTROL URL, Abrir en]** - Puede configurar un recurso de para abrir un vínculo. Configure las variables **[!UICONTROL URL]** y **[!UICONTROL Abrir en]** para indicar si desea que se abra en la misma ventana o en una ventana nueva.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Ajuste preestablecido del visor]** - Seleccione un ajuste preestablecido de visualizador existente en el menú desplegable. Si el ajuste preestablecido de visualizador que está buscando no está visible, es posible que tenga que hacerlo visible. Consulte [Administración de ajustes preestablecidos de visor](/help/assets/managing-viewer-presets.md). No puede seleccionar un ajuste preestablecido de visualizador si utiliza un ajuste preestablecido de imagen y viceversa.

**[!UICONTROL Configuración de Dynamic Media Classic]** - Seleccione la configuración de Dynamic Media Classic que desea utilizar para recuperar los ajustes preestablecidos de imagen activos de Scene7 Publishing System.

**[!UICONTROL Ajuste preestablecido de imagen]** - Seleccione un ajuste preestablecido de imagen existente en el menú desplegable. Si el ajuste preestablecido de imagen que está buscando no está visible, es posible que tenga que hacerlo visible. Consulte [Administración de ajustes preestablecidos de imagen](/help/assets/managing-image-presets.md). No puede seleccionar un ajuste preestablecido de visualizador si utiliza un ajuste preestablecido de imagen y viceversa.

**[!UICONTROL Formato de salida]** - Seleccione el formato de salida de la imagen, por ejemplo jpeg. Según el formato de salida que seleccione, puede tener opciones de configuración adicionales. Consulte [Administración de ajustes preestablecidos de imagen](/help/assets/managing-image-presets.md).

**[!UICONTROL Enfoque]** - Seleccione cómo desea enfocar la imagen. El enfoque se explica en detalle en [*Mejores prácticas de calidad de imagen y perfeccionamiento de Adobe Dynamic Media Classic*](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL Modificadores de URL]** - Puede cambiar los efectos de imagen suministrando comandos de imagen Dynamic Media Classic adicionales. Estos se describen en [Administración de ajustes preestablecidos de imagen](/help/assets/managing-image-presets.md) y [Referencia de comandos](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Puntos de interrupción]** - Si su sitio web es interactivo, desea ajustar los puntos de interrupción. Los puntos de interrupción deben separarse con comas `,`.

### Plantilla de imagen {#image-template}

[Plantillas de imagen de Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) son contenido de Photoshop en capas que se importó a Dynamic Media Classic, donde el contenido y las propiedades se parametrizaron para la variabilidad. La variable **[!UICONTROL Plantilla de imagen]** componente permite importar imágenes y cambiar el texto dinámicamente en AEM. Además, puede configurar la variable **[!UICONTROL Plantilla de imagen]** para utilizar valores de ClientContext, de modo que cada usuario experimente la imagen de forma personalizada.

Haga clic en **[!UICONTROL Editar]** para configurar el componente. Puede configurar [configuración común a todos los componentes de Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) , así como otras configuraciones descritas en esta sección.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Referencia del archivo, Anchura y Altura]** - Consulte la configuración común a todos los componentes de Dynamic Media Classic.

>[!NOTE]
>
>Los comandos y parámetros de URL de Dynamic Media Classic no se pueden agregar directamente a la URL de referencia de archivo. Solo se pueden definir en la interfaz de usuario del componente en la **[!UICONTROL Parámetro]** panel.

**[!UICONTROL Título, Texto alternativo]** En el [!UICONTROL Plantilla de imagen de Dynamic Media Classic] , añada un título a la imagen y texto alternativo para los usuarios que tengan los gráficos desactivados.

**[!UICONTROL URL, Abrir en]** Puede configurar un recurso de para abrir un vínculo. Configure las variables **[!UICONTROL URL]** y **[!UICONTROL Abrir en]** indique si desea que se abra en la misma ventana o en una ventana nueva.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Panel de parámetros]** Al importar una imagen, los parámetros se rellenan previamente con información de la imagen. Si no hay contenido que se pueda cambiar dinámicamente, esta ventana está vacía.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Cambio dinámico del texto {#changing-text-dynamically}

Para cambiar el texto de forma dinámica, introduzca nuevo texto en los campos y haga clic en **[!UICONTROL OK]**. En este ejemplo, la variable **[!UICONTROL Precio]** ahora es $50 y el envío cuesta 99 centavos.

![chlimage_1-86](assets/chlimage_1-86.png)

El texto de la imagen cambia. Para restablecer el texto al valor original, haga clic en **[!UICONTROL Restablecer]** junto al campo .

![chlimage_1-87](assets/chlimage_1-87.png)

#### Cambio de texto para reflejar el valor de un valor de ClientContext {#changing-text-to-reflect-the-value-of-a-client-context-value}

Para vincular un campo a un valor de ClientContext, haga clic en **[!UICONTROL Select]** para abrir el menú client-context, seleccione client context y haga clic en **[!UICONTROL OK]**. En este ejemplo, el nombre cambia en función de la vinculación del nombre con el nombre con formato en el perfil.

![chlimage_1-88](assets/chlimage_1-88.png)

El texto refleja el nombre del usuario que ha iniciado sesión en ese momento. Para restablecer el texto al valor original, haga clic en **[!UICONTROL Restablecer]** junto al campo .

![chlimage_1-89](assets/chlimage_1-89.png)

#### Conversión de la plantilla de imagen de Dynamic Media Classic en un vínculo {#making-the-scene-image-template-a-link}

**Conversión de la plantilla de imagen de Dynamic Media Classic en un vínculo**:

1. En la página con el componente de plantilla de imagen de Dynamic Media Classic , haga clic en **[!UICONTROL Editar]**.
1. En el **[!UICONTROL URL]** , introduzca la dirección URL a la que se dirigen los usuarios cuando se hace clic en la imagen. En el **[!UICONTROL Abrir en]** , seleccione si desea que se abra el destino (una nueva ventana o la misma ventana).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Haga clic en **[!UICONTROL Aceptar]**.

### Componente de vídeo {#video-component}

Dynamic Media Classic **[!UICONTROL Vídeo]** (disponible en la sección Dynamic Media Classic de la barra de tareas) utiliza la detección de dispositivos y ancho de banda para ofrecer el vídeo correcto a cada pantalla. Este componente es un reproductor de vídeo HTML5; es un visor único que se puede utilizar en varios canales.

Se puede utilizar para conjuntos de vídeos adaptables, un solo vídeo MP4 o un solo vídeo F4V.

Consulte [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) para obtener más información sobre cómo funcionan los vídeos con la integración de Dynamic Media Classic. Además, consulte cómo [el **Vídeo de Dynamic Media Classic** el componente se compara con la base **video** componente](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![imagen_1-91](assets/chlimage_1-91.png)

### Limitaciones conocidas del componente de vídeo {#known-limitations-for-the-video-component}

Adobe DAM y WCM muestran si se ha cargado un vídeo maestro. No muestran estos recursos de proxy:

* Representaciones codificadas de Dynamic Media Classic
* Conjuntos de vídeos adaptables de Dynamic Media Classic

Al utilizar un conjunto de vídeos adaptables con el componente de vídeo de Dynamic Media Classic, debe cambiar el tamaño del componente para que se ajuste a las dimensiones del vídeo.

## Navegador de contenido de Dynamic Media Classic {#scene-content-browser}

El navegador de contenido de Dynamic Media Classic le permite ver el contenido de Dynamic Media Classic directamente en AEM. Para acceder al navegador de contenido, en el Buscador de contenido, seleccione **[!UICONTROL Dynamic Media Classic]** en la interfaz de usuario táctil o en la **[!UICONTROL S7]** en la interfaz de usuario clásica. La funcionalidad es idéntica entre ambas interfaces de usuario.

Si tiene varias configuraciones, AEM de forma predeterminada muestra la variable [configuración predeterminada](/help/sites-administering/scene7.md#configuring-a-default-configuration). Puede seleccionar diferentes configuraciones directamente en el navegador de contenido de Dynamic Media Classic en el menú desplegable.

>[!NOTE]
>
>* Los recursos ubicados en la carpeta ad hoc no aparecen en el explorador de contenido de Dynamic Media Classic.
>* When [La vista previa segura está activada](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), tanto los recursos publicados como los no publicados en Dynamic Media Classic aparecen en el navegador de contenido de Dynamic Media Classic.
>* Si no ve **[!UICONTROL Dynamic Media Classic]** o **[!UICONTROL S7]** como opción en el navegador de contenido, debe [configurar Dynamic Media Classic para que funcione con AEM](/help/sites-administering/scene7.md).
>
>* Para vídeo, el navegador de contenido de Dynamic Media Classic admite:
>
>* Conjuntos de vídeos adaptables: contenedor de todas las representaciones de vídeo necesarias para una reproducción perfecta en varias pantallas
>* Un solo vídeo MP4
>* Vídeo F4V único


### Exploración del contenido en la IU clásica {#browsing-content-in-the-classic-ui}

Examine el contenido en Dynamic Media Classic haciendo clic en el botón **[!UICONTROL S7]** pestaña .

Puede cambiar la configuración a la que accede seleccionando la configuración . Las carpetas cambian según la configuración que seleccione.

![chlimage_1-92](assets/chlimage_1-92.png)

Al igual que con el buscador de contenido para Assets, puede buscar recursos y filtrar los resultados. Sin embargo, a diferencia del buscador de recursos, al introducir una palabra clave en la variable **[!UICONTROL S7]** ficha, nombre del archivo *comienza con* la cadena que ha introducido, en lugar de *contain* la palabra clave en el nombre del archivo.

De forma predeterminada, los recursos se muestran por nombre de archivo. También puede filtrar los resultados por tipo de recurso.

>[!NOTE]
>
>Para vídeo, el navegador de contenido Dynamic Media Classic de WCM admite:
>
>* Conjuntos de vídeos adaptables: contenedor de todas las representaciones de vídeo necesarias para una reproducción perfecta en varias pantallas
>* Un solo vídeo MP4
>* Vídeo F4V único
>


### Búsqueda de recursos de Dynamic Media Classic con el navegador de contenido {#searching-for-scene-assets-with-the-content-browser}

La búsqueda de recursos de Dynamic Media Classic es similar a la búsqueda de recursos de AEM, excepto que, al realizar la búsqueda, se ve una vista remota de los recursos en el sistema de Dynamic Media Classic, en lugar de importarlos directamente a AEM.

Puede utilizar la IU clásica o la IU táctil para ver y buscar recursos. En función de la interfaz, la búsqueda es ligeramente diferente.

Al buscar en cualquiera de las IU, puede filtrar por los siguientes criterios (que se muestran aquí en la IU táctil):

**[!UICONTROL Escribir palabras clave]** - Puede buscar recursos por nombre. Al buscar las palabras clave introducidas, comienza con el nombre del archivo. Por ejemplo, si escribe la palabra &quot;natación&quot;, buscará cualquier nombre de archivo de recurso que comience con esas letras en ese orden. Asegúrese de hacer clic en Intro después de escribir el término para buscar el recurso.

![imagen_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Carpeta/ruta]** - El nombre de la carpeta que aparece se basa en la configuración seleccionada. Para explorar en profundidad los niveles inferiores, haga clic en el icono de la carpeta, seleccione una subcarpeta y, a continuación, haga clic en la marca de verificación para seleccionarla.

Si introduce una palabra clave y selecciona una carpeta, AEM busca esa carpeta y las subcarpetas. Sin embargo, si no introduce ninguna palabra clave al buscar, seleccionar la carpeta solo mostrará los recursos de esa carpeta y no incluirá ninguna subcarpeta.

De forma predeterminada, AEM busca la carpeta seleccionada y todas las subcarpetas.

![imagen_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Tipo de recurso]** Seleccione Dynamic Media Classic para examinar el contenido de Dynamic Media Classic. Esta opción solo está disponible si ya ha configurado Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**[!UICONTROL Configuración]** Si tiene más de una configuración de Dynamic Media Classic definida en [!UICONTROL Cloud Services], puede seleccionarlo aquí. Como resultado, la carpeta cambiará según la configuración que haya elegido.

![imagen_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Tipo de recurso]** En el explorador de Dynamic Media Classic, puede filtrar los resultados para incluir cualquiera de los siguientes elementos: imágenes, plantillas, vídeos y conjuntos de vídeos adaptables. Si no selecciona ningún tipo de recurso, AEM de forma predeterminada busca todos los tipos de recurso.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Al buscar vídeo, está buscando una sola representación. Los resultados devuelven la representación original (solo &amp;ast;.mp4) y la representación codificada.
>* Al buscar un conjunto de vídeos adaptables, está buscando en la carpeta y en todas las subcarpetas, pero solo si ha añadido una palabra clave a la búsqueda. Si no ha añadido ninguna palabra clave, AEM no busca en las subcarpetas.
>


**[!UICONTROL Estado de publicación]** Puede filtrar los recursos en función del estado de publicación: [!UICONTROL Publicado] o [!UICONTROL Sin publicar]. Si no selecciona ninguna [!UICONTROL Estado de publicación], AEM de forma predeterminada busca todos los estados de publicación.

![imagen_1-98](assets/chlimage_1-98.png)
