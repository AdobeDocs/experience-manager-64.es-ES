---
title: Imágenes panorámicas
seo-title: Imágenes panorámicas
description: Aprenda a trabajar con imágenes panorámicas en Dynamic Media.
seo-description: Aprenda a trabajar con imágenes panorámicas en Dynamic Media.
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 4%

---


# Imágenes panorámicas {#panoramic-images}

En esta sección se describe cómo trabajar con el visor de imágenes panorámicas para procesar imágenes panorámicas esféricas y así disfrutar de una experiencia de visualización inmersiva de 360° de una habitación, propiedad, ubicación o paisaje.

See also [Managing Viewer Presets](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Carga de recursos para su uso con el visor de imágenes panorámicas {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Para que un recurso cargado se considere una imagen panorámica esférica que se va a utilizar con el visor de imágenes panorámicas, el recurso debe tener una o ambas de las opciones siguientes:

* Proporción de aspecto de 2.

   Puede anular la configuración de proporción de aspecto predeterminada de 2 en **[!UICONTROL CRXDE Lite]** de la siguiente manera:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Etiquetado con las palabras clave `equirectangular`, o `spherical`y `panorama`, o `spherical` y `panoramic`. Consulte [Uso de etiquetas](/help/sites-authoring/tags.md).

Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente de **[!UICONTROL medios panorámicas]**.

Para cargar recursos para utilizarlos con el visor de imágenes panorámicas, consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

## Configuración de Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Para que el visor de imágenes panorámicas funcione correctamente en AEM, debe sincronizar los ajustes preestablecidos de visor de imágenes panorámicas con los metadatos específicos de Dynamic Media Classic y Dynamic Media Classic para que los ajustes preestablecidos de visor se actualicen en el JCR. Para ello, configure Dynamic Media Classic de la siguiente manera:

1. [Inicie sesión en la instancia de Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) para cada cuenta de compañía.

1. Cerca de la esquina superior derecha de la página, haga clic en **[!UICONTROL Ajustes > Ajustes de aplicación > Ajustes de publicación > Servidor]** de imágenes.
1. En la página Publicación **[!UICONTROL del servidor de]** imágenes, en el menú desplegable Contexto **[!UICONTROL de]** publicación situado cerca de la parte superior, seleccione Servicio **[!UICONTROL de imágenes]**.

1. En la misma página **[!UICONTROL de publicación]** del servidor de imágenes, busque el encabezado Atributos **[!UICONTROL de]** solicitud.
1. En el encabezado Atributos **[!UICONTROL de]** solicitud, busque Límite **[!UICONTROL de tamaño de imagen de]** respuesta. A continuación, en los campos **[!UICONTROL Anchura]** y **[!UICONTROL Altura]** asociados, aumente el tamaño máximo permitido para imágenes panorámicas.

   Dynamic Media Classic tiene un límite de 25.000.000 píxeles. El tamaño máximo permitido para imágenes con una proporción de aspecto de 2:1 es de 7000 x 3500. Sin embargo, para las pantallas de escritorio típicas, 4096 x 2048 píxeles es suficiente.

   >[!NOTE]
   >
   >Solo se admiten las imágenes que alcanzan el tamaño máximo permitido de imagen. Las solicitudes de imágenes que superen el límite de tamaño darán como resultado una respuesta de 403.

1. En el encabezado Atributos de **solicitud]** , haga lo siguiente:

   * Establezca **[!UICONTROL el modo]** de confusión de solicitudes en **[!UICONTROL Deshabilitado]**.
   * Establezca **[!UICONTROL el modo]** de bloqueo de solicitudes en **[!UICONTROL Deshabilitado]**.

   Estos ajustes son necesarios para utilizar el componente de medios **[!UICONTROL panorámicas]** en AEM.

1. En la parte inferior de la página Servidor de **[!UICONTROL imágenes Publicar]** , en la parte izquierda, toque **[!UICONTROL Guardar]**.

1. En la esquina inferior derecha, toque **[!UICONTROL Cerrar]**.

### Resolución de problemas del componente de medios panorámicos {#troubleshooting-the-panoramic-media-wcm-component}

Si ha colocado una imagen en el componente **[!UICONTROL Panoramic Media]** de WCM y el marcador de posición del componente se ha contraído, es posible que desee solucionar los problemas siguientes:

* Si se produce un error 403 Prohibido, es posible que el tamaño de la imagen solicitada sea demasiado grande. Revise la configuración de Límite *de tamaño de imagen de* respuesta en [Configuración de Dynamic Media Classic (Scene7)](#configuring-dynamic-media-classic-scene).

* Para un bloqueo ** no válido en el recurso o error *de* análisis mostrado en la página, marque Modo **[!UICONTROL de confusión]** de solicitudes y Modo **[!UICONTROL de bloqueo de]** solicitudes para asegurarse de que están desactivadas.
* Si se produce un error de lienzo contaminado, configure una ruta de archivo de definición de conjunto de **[!UICONTROL reglas e Invalide CTN]** para las solicitudes anteriores del recurso de imagen.
* Si la calidad de la imagen es muy baja después de una solicitud de imagen con un tamaño superior al límite admitido, compruebe que el ajuste Atributos de codificación **[!UICONTROL JPEG > Calidad]** no esté vacío. Una configuración típica del campo **[!UICONTROL Calidad]** es `95`. Puede encontrar la configuración en la página **[!UICONTROL Servidor de imágenes Publicar]** . Para acceder a la página, consulte [Configuración de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Vista previa de imágenes panorámicas {#previewing-panoramic-images}

Consulte [Vista previa de recursos](previewing-assets.md).

## Publicación de imágenes panorámicas {#publishing-panoramic-images}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md).
