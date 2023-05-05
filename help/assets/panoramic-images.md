---
title: Imágenes panorámicas
description: Aprenda a trabajar con imágenes panorámicas en Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# Imágenes panorámicas {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta sección se describe cómo trabajar con el visor de imágenes panorámicas para representar imágenes panorámicas esféricas y así obtener una experiencia de visualización de 360° inmersiva de una habitación, propiedad, ubicación o paisaje.

Consulte también [Administración de ajustes preestablecidos de visor](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Carga de recursos para su uso con el visor de imágenes panorámicas {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Para que un recurso cargado pueda considerarse una imagen panorámica esférica que pretenda usar con el visor de imágenes panorámicas, el recurso debe tener una o ambas de las siguientes opciones:

* Una relación de aspecto de 2.

   Puede anular la configuración predeterminada de relación de aspecto de 2 en **[!UICONTROL CRXDE Lite]** a continuación:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Etiquetado con las palabras clave `equirectangular`o `spherical`y `panorama`o `spherical` y `panoramic`. Consulte [Uso de etiquetas](/help/sites-authoring/tags.md).

Tanto la proporción de aspecto como los criterios de palabra clave se aplican a los recursos panorámicos para la página de detalles de recursos y el componente de **[!UICONTROL medios panorámicas]**.

Para cargar recursos para usarlos con el visor de imágenes panorámicas, consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

## Configuración de Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Para que el visor de imágenes panorámicas funcione correctamente en AEM, debe sincronizar los ajustes preestablecidos del visor de imágenes panorámicas con los metadatos específicos de Dynamic Media Classic y Dynamic Media Classic para que los ajustes preestablecidos del visor se actualicen en el JCR. Para lograr esto, configure Dynamic Media Classic de la siguiente manera:

1. [Inicie sesión en la aplicación de escritorio de Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) para cada cuenta de empresa.

1. Cerca de la esquina superior derecha de la página, haga clic en **[!UICONTROL Configuración > Configuración de la aplicación > Configuración de publicación > Servidor de imágenes]**.
1. En el **[!UICONTROL Publicación en el servidor de imágenes]** desde la página **[!UICONTROL Publicar contexto]** menú desplegable cerca de la parte superior, seleccione **[!UICONTROL Servicio de imágenes]**.

1. En el mismo **[!UICONTROL Publicación en el servidor de imágenes]** , busque el encabezado **[!UICONTROL Atributos de solicitud]**.
1. En el **[!UICONTROL Atributos de solicitud]** encabezado, localizar **[!UICONTROL Límite de tamaño de imagen de respuesta]**. A continuación, en el **[!UICONTROL Anchura]** y **[!UICONTROL Altura]** , aumente el tamaño máximo permitido de imagen para imágenes panorámicas.

   Dynamic Media Classic tiene un límite de 25 000 000 píxeles. El tamaño máximo permitido para imágenes con una proporción de aspecto de 2:1 es de 7000 x 3500. Sin embargo, para las pantallas de escritorio típicas, 4096 x 2048 píxeles es suficiente.

   >[!NOTE]
   >
   >Solo se admiten las imágenes que se encuentran dentro del tamaño máximo permitido de imagen. Las solicitudes de imágenes que superen el límite de tamaño darán como resultado una respuesta 403.

1. En el **[Atributos de solicitud]** , haga lo siguiente:

   * Establezca **[!UICONTROL Modo de ofuscación de solicitud]** a **[!UICONTROL Desactivado]**.
   * Establezca **[!UICONTROL Modo de bloqueo de solicitud]** a **[!UICONTROL Desactivado]**.

   Esta configuración es necesaria para usar la variable **[!UICONTROL Medios panorámicos]** en AEM.

1. En la parte inferior del **[!UICONTROL Publicación en el servidor de imágenes]** página, en el lado izquierdo, pulse **[!UICONTROL Guardar]**.

1. En la esquina inferior derecha, pulse **[!UICONTROL Cerrar]**.

### Solución de problemas del componente de medios panorámicos {#troubleshooting-the-panoramic-media-wcm-component}

Si ha colocado una imagen en la variable **[!UICONTROL Medios panorámicos]** en su WCM y el marcador de posición del componente contraído, es posible que desee solucionar los siguientes problemas:

* Si se produce un error de 403 prohibido, es posible que el tamaño de la imagen solicitada sea demasiado grande. Consulte la *Límite de tamaño de imagen de respuesta* configuración de [Configuración de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Para un *Bloqueo no válido* en el recurso o *Error de análisis* mostrado en la página, marque **[!UICONTROL Modo de ofuscación de solicitud]** y **[!UICONTROL Modo de bloqueo de solicitud]** para asegurarse de que están desactivados.
* Para un error de lienzo teñido, configure un **[!UICONTROL Ruta del archivo de definición de conjunto de reglas e invalidar CTN]** para las solicitudes anteriores del recurso de imagen.
* Si la calidad de la imagen se vuelve muy baja después de una solicitud de imagen con un tamaño superior al límite admitido, compruebe que la variable **[!UICONTROL Atributos de codificación del JPEG > Calidad]** no está vacío. Una configuración típica para la variable **[!UICONTROL Calidad]** el campo es `95`. Puede encontrar la configuración en la **[!UICONTROL Publicación en el servidor de imágenes]** página. Para acceder a la página, consulte [Configuración de Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Vista previa de imágenes panorámicas {#previewing-panoramic-images}

Consulte [Vista previa de recursos](previewing-assets.md).

## Publicar imágenes panorámicas {#publishing-panoramic-images}

Consulte [Publicación de recursos](publishing-dynamicmedia-assets.md).
