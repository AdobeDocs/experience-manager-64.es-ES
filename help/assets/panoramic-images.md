---
title: Imágenes panorámicas
Description: Learn how to work with panoramic images in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Imágenes panorámicas
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 4%

---

# Imágenes panorámicas {#panoramic-images}

En esta sección se describe cómo trabajar con el visor de imágenes panorámicas para representar imágenes panorámicas esféricas y así obtener una experiencia de visualización de 360° inmersiva de una habitación, propiedad, ubicación o paisaje.

Consulte también [Administración de ajustes preestablecidos de visualizador](managing-viewer-presets.md).

![imagen panorámica2](assets/panoramic-image2.png)

## Carga de recursos para su uso con el visor de imágenes panorámicas {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Para que un recurso cargado pueda considerarse una imagen panorámica esférica que pretenda usar con el visor de imágenes panorámicas, el recurso debe tener una o ambas de las siguientes opciones:

* Una relación de aspecto de 2.

   Puede anular la configuración predeterminada de relación de aspecto de 2 en **[!UICONTROL CRXDE Lite]** de la siguiente manera:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Etiquetado con las palabras clave `equirectangular`, o `spherical`y `panorama`, o `spherical` y `panoramic`. Consulte [Uso de etiquetas](/help/sites-authoring/tags.md).

Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente de **[!UICONTROL medios panorámicas]**.

Para cargar recursos para usarlos con el visor de imágenes panorámicas, consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

## Configuración de Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Para que el visor de imágenes panorámicas funcione correctamente en AEM, debe sincronizar los ajustes preestablecidos del visor de imágenes panorámicas con los metadatos específicos de Dynamic Media Classic y Dynamic Media Classic para que los ajustes preestablecidos de visor se actualicen en el JCR. Para ello, configure Dynamic Media Classic de la siguiente manera:

1. [Inicie sesión en la ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) aplicación de escritorio de Dynamic Media Classic para cada cuenta de empresa.

1. Cerca de la esquina superior derecha de la página, haga clic en **[!UICONTROL Configuración > Configuración de la aplicación > Configuración de la publicación > Servidor de imágenes]**.
1. En la página **[!UICONTROL Publicación del servidor de imágenes]**, en el menú desplegable **[!UICONTROL Publicar contexto]** cerca de la parte superior, seleccione **[!UICONTROL Servicio de imágenes]**.

1. En la misma página **[!UICONTROL Publicación del servidor de imágenes]**, busque el encabezado **[!UICONTROL Atributos de solicitud]**.
1. En el encabezado **[!UICONTROL Solicitar atributos]**, busque **[!UICONTROL Responder límite de tamaño de imagen]**. A continuación, en los campos **[!UICONTROL Width]** y **[!UICONTROL Height]** asociados, aumente el tamaño máximo permitido de imagen para imágenes panorámicas.

   Dynamic Media Classic tiene un límite de 25 000 000 píxeles. El tamaño máximo permitido para imágenes con una proporción de aspecto de 2:1 es de 7000 x 3500. Sin embargo, para las pantallas de escritorio típicas, 4096 x 2048 píxeles es suficiente.

   >[!NOTE]
   >
   >Solo se admiten las imágenes que se encuentran dentro del tamaño máximo permitido de imagen. Las solicitudes de imágenes que superen el límite de tamaño darán como resultado una respuesta 403.

1. En el encabezado **[Solicitar atributos]**, haga lo siguiente:

   * Establezca **[!UICONTROL Modo de ofuscación de solicitudes]** en **[!UICONTROL Deshabilitado]**.
   * Establezca **[!UICONTROL Modo de bloqueo de solicitudes]** en **[!UICONTROL Deshabilitado]**.

   Estos ajustes son necesarios para utilizar el componente **[!UICONTROL Medios panorámicos]** en AEM.

1. En la parte inferior de la página **[!UICONTROL Image Server Publish]**, en el lado izquierdo, pulse **[!UICONTROL Guardar]**.

1. En la esquina inferior derecha, pulse **[!UICONTROL Cerrar]**.

### Solución de problemas del componente de medios panorámicos {#troubleshooting-the-panoramic-media-wcm-component}

Si ha colocado una imagen en el componente **[!UICONTROL Medios panorámicos]** de su WCM y el marcador de posición del componente se ha contraído, es posible que desee solucionar los siguientes problemas:

* Si se produce un error de 403 prohibido, es posible que el tamaño de la imagen solicitada sea demasiado grande. Revise la configuración de *Reply Image Size Limit* en [Configuración de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Para un *Bloqueo no válido* en el recurso o *Error de análisis* mostrado en la página, marque **[!UICONTROL Modo de ofuscación de solicitudes]** y **[!UICONTROL Modo de bloqueo de solicitudes]** para asegurarse de que están desactivados.
* Para un error de lienzo teñido, configure una **[!UICONTROL Ruta de archivo de definición de conjunto de reglas e invalide CTN]** para las solicitudes anteriores del recurso de imagen.
* Si la calidad de la imagen es muy baja después de una solicitud de imagen con un tamaño superior al límite admitido, compruebe que la configuración **[!UICONTROL JPEG Encoding Attributes > Quality]** no esté vacía. Una configuración típica para el campo **[!UICONTROL Quality]** es `95`. Puede encontrar la configuración en la página **[!UICONTROL Publicación del servidor de imágenes]**. Para acceder a la página, consulte [Configuración de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Vista previa de imágenes panorámicas {#previewing-panoramic-images}

Consulte [Vista previa de recursos](previewing-assets.md).

## Publicar imágenes panorámicas {#publishing-panoramic-images}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md).
