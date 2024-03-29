---
title: Invalidar el contenido en caché de CDN
seo-title: Invalidating your CDN cached content
description: Al invalidar el contenido almacenado en caché de la CDN (red de distribución de contenido), puede actualizar rápidamente los recursos que entrega Dynamic Media, en lugar de esperar a que caduque la caché.
seo-description: Invalidating your CDN (Content Delivery Network) cached content lets you quickly update assets that are delivered by Dynamic Media, instead of waiting for the cache to expire.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Asset Management,CDN Cache
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 28%

---

# Invalidar el contenido en caché de CDN {#invalidating-your-cdn-cached-content}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La CDN almacena en caché los recursos de Dynamic Media para una entrega rápida. Sin embargo, cuando actualice un recurso, es posible que desee que esos cambios surtan efecto inmediatamente. Al invalidar el contenido almacenado en caché de la CDN (red de distribución de contenido), puede actualizar rápidamente los recursos que entrega Dynamic Media, en lugar de esperar a que caduque la caché.

Consulte también [Información general de caché en Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Para invalidar el contenido en caché de la CDN:**

1. Inicie sesión en la aplicación de escritorio de Dynamic Media Classic.

   [aplicación de escritorio de Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)

   Adobe proporcionó las credenciales y el inicio de sesión en el momento de la provisión. Si no dispone de esta información, póngase en contacto con el servicio de asistencia técnica.

1. Haga clic en **[!UICONTROL Ajustes > Ajustes de aplicación > Configuracióngeneral]**.
1. En la página Configuración general de la aplicación , en el encabezado de grupo Servidores , busque la **[!UICONTROL Plantilla de invalidación de CDN]** cuadro de texto.

1. Especifique la plantilla que se utiliza para invalidar la caché de la CDN (red de entrega de contenido).

   Por ejemplo, supongamos que introduce una URL de imagen (incluidos los ajustes preestablecidos de imagen o los modificadores) que hace referencia a `<ID>`, en lugar de un ID de imagen específico, como en el ejemplo siguiente:

   `https://server.com/is/image/Company/<ID>?$product$`

   Si la plantilla solo contiene `<ID>`y, a continuación, Dynamic Media rellena `https://<server>/is/image` donde `<server>` es el nombre del servidor de publicación que se define en Configuración general y &lt;id> es el activo o recursos seleccionados para invalidarse.

1. En la esquina inferior derecha de la página, haga clic en **[!UICONTROL Cerrar]**.
1. En la interfaz de usuario de la aplicación de escritorio de Dynamic Media Classic, seleccione uno o varios recursos y haga clic en **[!UICONTROL Archivo > Invalidar CDN]**. Verá una lista de una o más direcciones URL generadas a partir de la plantilla creada y los recursos seleccionados. Utiliza la URL del servidor que aparece en &quot;Nombre del servidor publicado&quot; en Configuración general de la aplicación.

   Por ejemplo, con la plantilla de invalidación de CDN establecida en el paso anterior, suponga que ha seleccionado una sola imagen de recurso de imagen denominada `Backpack_B`. Al hacer clic en **[!UICONTROL Archivo > Invalidar CDN]** resulta en la siguiente URL generada en la interfaz de usuario de Invalidación de CDN:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. En el cuadro de lista URL, haga clic en **[!UICONTROL Continuar]** para borrar la caché de cada URL específica. Tenga en cuenta que puede editar una dirección URL o agregar una dirección URL escribiéndola o pegándola en el cuadro de lista de direcciones URL; no es necesario configurar la plantilla de invalidación de CDN de antemano.

   Después de hacer clic en **[!UICONTROL Continuar]**, se muestra un indicador que proporciona una estimación del tiempo que tardará en borrarse la caché.

   Si seleccionó varios recursos y, a continuación, hizo clic en **[!UICONTROL Archivo > Invalidar CDN]**, se hace referencia a cada recurso en la **[!UICONTROL URL de plantilla guardada]**. Por lo tanto, puede definir una **[!UICONTROL plantilla de invalidación de CDN]** que haga referencia a cada ajuste preestablecido de imagen URL al que se hace referencia en el sitio web (como detalles del producto, resultados de búsqueda, etc.). A continuación, al seleccionar una o varias imágenes para la invalidación desde la caché, las direcciones URL rellenan automáticamente la interfaz.

   >[!NOTE]
   >
   >Al seleccionar recursos y, a continuación, hacer clic en **[!UICONTROL Archivo > Invalidar CDN]**, Dynamic Media utiliza una plantilla de CDN no válida para crear automáticamente direcciones URL que se van a invalidar desde la red de entrega de contenido (CDN). Si no hay nada en el cuadro de texto **[!UICONTROL Plantilla de invalidación de CDN]**, aparecerá una lista de URL en blanco. El almacenamiento en caché en la CDN no está basado en recursos; se basa en la URL. Por lo tanto, es necesario conocer las direcciones URL completas que se encuentran en el sitio web. Después de establecer dichas direcciones URL, puede agregarlas al cuadro de texto **[!UICONTROL Invalidar plantilla CDN]** en los pasos anteriores. A continuación, puede seleccionar esos recursos e invalidar las direcciones URL en un solo paso.
   >
   >Otra opción es agregar direcciones URL completas al **[!UICONTROL Invalidar CDN]** lista. Si sigue este método, no es necesario seleccionar recursos en Dynamic Media Classic antes de ir a la **[!UICONTROL Archivo > Invalidar CDN]** .
