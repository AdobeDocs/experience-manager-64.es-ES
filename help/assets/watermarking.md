---
title: Adición de una marca de agua a los recursos digitales
description: Aprenda a utilizar la función de marca de agua para agregar una marca de agua digital a los recursos.
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 3%

---


# Marcar los recursos digitales {#watermarking}

[!DNL Adobe Experience Manager Assets] le permite agregar una marca de agua digital a los recursos para ayudar a los usuarios a verificar la autenticidad y propiedad de los recursos protegida por derechos de autor. [!DNL Experience Manager Assets] admite texto que se utilizará como marca de agua en archivos PNG y JPEG.

Recursos Adobe Experience Manager (AEM) permite agregar una marca de agua digital a las imágenes para ayudar a los usuarios a comprobar la autenticidad y la propiedad de los recursos protegida por derechos de autor. AEM Assets admite texto que se utilizará como marca de agua en archivos PNG y JPEG.

Para poder aplicar una marca de agua en los recursos, agregue el paso de marca de agua en el flujo de trabajo [!UICONTROL DAM Update Asset] .

1. Acceda a la interfaz de usuario [!DNL Experience Manager] y vaya a **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. En la página Modelos de flujo de trabajo , seleccione el flujo de trabajo **[!UICONTROL Activo de actualización de DAM]** y haga clic en **[!UICONTROL Editar]**.

1. En el panel lateral, arrastre el paso **[!UICONTROL Add Watermark]** y agréguelo al flujo de trabajo [!UICONTROL DAM Update Asset].

   ![Arrastre el paso Agregar marca de agua al flujo de trabajo de recursos de actualización de DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque el paso [!UICONTROL Add Watermark] en cualquier lugar antes del paso [!UICONTROL Process Thumbnail].

1. Abra el paso **[!UICONTROL Agregar marca de agua]** para mostrar sus propiedades.
1. En la pestaña **[!UICONTROL Argumentos]**, especifique valores válidos en los distintos campos, como texto, tipo de fuente, tamaño, color, posición, orientación, etc. Para confirmar los cambios, haga clic en **[!UICONTROL Listo]**.

   ![Proporcione los argumentos en el paso agregar marca de agua de Assets](assets/arguments_add_watermark_aem_assets.png)

1. Guarde el flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]** con el paso de marca de agua.
1. Desde la interfaz de usuario de AEM, cargue un recurso de ejemplo. La marca de agua aparece con el tamaño de fuente, el color, etc., en la posición que configuró en los pasos anteriores.

Para marcar documentos PDF mediante programación o con información dinámica, considere la posibilidad de utilizar la oferta [AEM Document Services](/help/forms/using/overview-aem-document-services.md).

## Sugerencias y limitaciones {#tips-limitations}

* Solo se admiten marcas de agua basadas en texto. Las imágenes no se utilizan como marcas de agua, aunque se pueden cargar imágenes al crear el [!UICONTROL Proceso de adición de marca de agua].
* Solo se admiten archivos PNG y JPEG con marca de agua. Otros formatos de recursos no están marcados con agua.
