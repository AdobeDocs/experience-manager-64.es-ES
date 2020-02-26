---
title: Configurar el etiquetado basado en AI mediante el servicio de contenido inteligente
description: Obtenga información sobre cómo configurar el etiquetado inteligente y el etiquetado inteligente mejorado en AEM mediante el servicio de contenido inteligente.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# Configuración del etiquetado de recursos mediante el servicio de contenido inteligente {#configure-asset-tagging-using-the-smart-content-service}

Obtenga información sobre cómo configurar el etiquetado inteligente y el etiquetado inteligente mejorado en AEM mediante el servicio de contenido inteligente.

Puede integrar Adobe Experience Manager (AEM) con Smart Content Service. Utilice esta configuración para acceder al servicio de contenido inteligente desde AEM y etiquetar automáticamente las imágenes.

En el artículo se detallan las siguientes tareas clave necesarias para configurar el servicio de contenido inteligente. En el back-end, el servidor AEM autentica las credenciales de servicio con la puerta de enlace de E/S de Adobe antes de reenviar la solicitud al servicio de contenido inteligente.

1. Cree una configuración de Smart Content Service en AEM para generar una clave pública. Obtenga un certificado público para la integración de OAuth.
1. Cree una integración en Adobe I/O y cargue la clave pública generada.
1. Configure la instancia de AEM utilizando la clave de API y otras credenciales de Adobe I/O.
1. De forma opcional, habilite el etiquetado automático en la carga de recursos.

## Requisitos previos {#prerequisites}

Antes de utilizar el servicio de contenido inteligente, asegúrese de lo siguiente para crear una integración en Adobe I/O:

* Una cuenta de Adobe ID que tiene privilegios de administrador para la organización.
* El servicio de Smart Content Service está habilitado para su organización.

Para habilitar Etiquetas inteligentes mejoradas, además de las anteriores, instale también el último Service Pack [de](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)AEM.

## Obtener certificado público {#obtain-public-certificate}

Un certificado público le permite autenticar su perfil en Adobe I/O.

1. From the AEM user interface, tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. En la página Cloud Services, pulse o haga clic en **[!UICONTROL Configurar ahora]** en **[!UICONTROL Etiquetas inteligentes de recursos]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]** , especifique un título y un nombre para la configuración de etiquetas inteligentes. Toque o haga clic en **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL AEM Smart Content Service]** , utilice los valores siguientes:

   **[!UICONTROL URL de servicio]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Servidor de autorización]**: `https://ims-na1.adobelogin.com`

   Deje el resto de campos en blanco por ahora (se proporcionará más tarde). Tap/click **[!UICONTROL OK]**.

   ![Cuadro de diálogo de AEM Smart Content Service para proporcionar la URL del servicio de contenido](assets/aem_scs.png)

   >[!NOTE]
   >
   >La dirección URL proporcionada como URL [!UICONTROL de servicio] no es accesible a través del explorador y genera un error 404. La configuración funciona correctamente con el mismo valor del parámetro de URL [!UICONTROL de] servicio. Para consultar el estado general del servicio de Adobe I/O y la programación de mantenimiento, consulte [https://status.adobe.com](https://status.adobe.com).

1. Toque o haga clic en **[!UICONTROL Descargar certificado público para la integración]** de OAuth y descargue el archivo de certificado público `AEM-SmartTags.crt`.

   ![Una representación de la configuración creada para el servicio de etiquetado inteligente](assets/download_link.png)

## Creación de la integración de Adobe I/O {#create-adobe-i-o-integration}

Para utilizar las API de Smart Content Service, cree una integración en Adobe I/O para generar clave de API, ID de cuenta técnica, ID de organización y Secreto de cliente.

1. Acceda a [https://console.adobe.io](https://console.adobe.io/).
1. En la página **[!UICONTROL Integraciones]** , seleccione su organización.
1. Toque o haga clic en **[!UICONTROL Nueva integración]**.
1. En la página **[!UICONTROL Crear una nueva integración]** , seleccione **[!UICONTROL Acceder a una API]**. Pulse o haga clic en **[!UICONTROL Continuar]**.
1. En **[!UICONTROL Experience Cloud]**, seleccione Contenido **[!UICONTROL inteligente]**. Pulse o haga clic en **[!UICONTROL Continuar]**.

   ![Al crear una nueva integración, seleccione Contenido inteligente en Experience Cloud, en las opciones disponibles](assets/smart_content.png)

1. En la página siguiente, seleccione **[!UICONTROL Nueva integración]**. Pulse o haga clic en **[!UICONTROL Continuar]**.
1. En la página Detalles **[!UICONTROL de la]** integración, especifique un nombre para la puerta de enlace de integración y agregue una descripción.
1. En los certificados **[!UICONTROL de claves]** públicas, cargue el `AEM-SmartTags.crt` archivo que descargó anteriormente.
1. Tap/click **[!UICONTROL Create Integration]**.
1. Para ver la información de la integración, toque o haga clic en **[!UICONTROL Continuar a los detalles]** de la integración.

   ![En la ficha Información general, puede revisar la información proporcionada para la integración.](assets/integration_details.png)

## Configurar el servicio de contenido inteligente {#configure-smart-content-service}

Para configurar la integración, utilice los valores de los campos de ID de cuenta técnica, ID de organización, Secreto de cliente, Servidor de autorización y clave de API de la integración de Adobe I/O. La creación de una configuración de nube de etiquetas inteligentes permite la autenticación de solicitudes de API desde la instancia de AEM.

1. En la interfaz de usuario de AEM, toque o haga clic en el logotipo de AEM. Vaya a **[!UICONTROL Herramientas > Servicio de nube > Servicios]** de nube heredados para abrir la consola de Cloud Services.
1. En Etiquetas **[!UICONTROL inteligentes de]** recursos, abra la configuración creada anteriormente. En la página de configuración del servicio, haga clic en **[!UICONTROL Editar]**.
1. En el cuadro de diálogo **[!UICONTROL AEM Smart Content Service]**, utilice los valores predefinidos para los campos **[!UICONTROL URL de servicio]** y **[!UICONTROL Servidor de autorización]**.
1. Para los campos Clave de API, Id de cuenta técnica, Id de organización y Secreto de cliente, utilice los valores generados anteriormente.

## Validar la configuración {#validate-the-configuration}

Después de completar la configuración, puede utilizar un MBean de JMX para validar la configuración. Para validar, siga estos pasos.

1. En AEM, para abrir la consola OSGi, haga clic en **[!UICONTROL Herramientas > Operaciones > Consola]** web. Haga clic en **[!UICONTROL Principal > JMX]**.
1. Haga clic en **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Abre **[!UICONTROL SimilitudBuscar varias tareas.]**
1. Haga clic en **[!UICONTROL validateConfigs()]**. En el cuadro de diálogo **[!UICONTROL Validar configuraciones]** , haga clic en **[!UICONTROL Invocar]**.

   El resultado de validación se muestra en el mismo cuadro de diálogo.

## Habilitar el etiquetado inteligente en el flujo de trabajo de recursos de actualización de DAM (opcional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. En la interfaz de usuario de AEM, toque o haga clic en el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. En la página **[!UICONTROL Modelos de flujo de trabajo]**, seleccione el modelo de flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]**.
1. Toque o haga clic en **[!UICONTROL Editar]** desde la barra de herramientas.
1. Expanda el panel lateral para mostrar los pasos. Arrastre el paso **[!UICONTROL Recurso de etiqueta inteligente]** que está disponible en la sección Flujo de trabajo de DAM y colóquelo después del paso **[!UICONTROL Miniaturas del proceso]**.

   ![Agregue el paso del recurso de etiquetas inteligentes después del paso de la miniatura del proceso en el flujo de trabajo de recursos de actualización de DAM](assets/chlimage_1-105.png)

1. Abra el paso en modo de edición. En **[!UICONTROL Configuración avanzada]**, compruebe que la opción **[!UICONTROL Avance del controlador]** está seleccionada.

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. En la pestaña **[!UICONTROL Argumentos]**, seleccione **[!UICONTROL Omitir errores]** si desea que el flujo de trabajo se complete aunque falle el paso de etiquetado automático.

   ![chlimage_1-107](assets/chlimage_1-107.png)

   Para etiquetar recursos al cargarlos, independientemente de si el etiquetado inteligente está activado en las carpetas, seleccione **[!UICONTROL Omitir marca]** de etiqueta inteligente.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Toque o haga clic en **[!UICONTROL Aceptar]** para cerrar el paso del proceso y, a continuación, guarde el flujo de trabajo.

>[!MORELIKETHIS]
>
>* [Comprender las etiquetas inteligentes en Recursos AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [Uso de etiquetas inteligentes con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [Uso de etiquetas inteligentes mejoradas con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [Configuración de etiquetas inteligentes mejoradas en AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)

