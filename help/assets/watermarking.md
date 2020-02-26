---
title: Marcar sus imágenes como agua
description: Utilice la función de marca de agua para añadir una marca de agua digital a las imágenes PNG Y JPEG.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# Marcar los recursos como agua {#watermarking}

Recursos Adobe Experience Manager (AEM) le permite agregar una marca de agua digital a las imágenes para ayudar a los usuarios a comprobar la autenticidad y propiedad de los recursos con copyright. AEM Assets admite texto que se va a utilizar como marca de agua en archivos PNG y JPEG.

Para poder aplicar marcas de agua a los recursos, agregue el paso [!UICONTROL Marca de agua] en el flujo de trabajo de recursos [!UICONTROL de actualización de] DAM.

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. En la página Modelos de flujo de trabajo, seleccione el flujo de trabajo de recursos **[!UICONTROL de actualización de]** DAM y haga clic en **[!UICONTROL Editar]**.

1. En el panel lateral, arrastre el paso **[!UICONTROL Agregar marca de agua]** y agréguelo al flujo de trabajo de actualización de recursos [!UICONTROL de] DAM.

   ![Darg add watermark step in the DAM update asset workflow (Darg add watermark step paso de adición de marca de agua en el flujo de trabajo del recurso de actualización de DAM)](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque el paso [!UICONTROL Agregar marca de agua] en cualquier lugar antes del paso [!UICONTROL Procesar miniatura] .

1. Abra el paso **[!UICONTROL Agregar marca de agua]** para mostrar sus propiedades.
1. En la ficha **[!UICONTROL Argumentos]** , especifique valores válidos en los distintos campos, como texto, tipo de fuente, tamaño, color, posición, orientación, etc. Para confirmar los cambios, toque o haga clic en el icono Listo.

   ![Proporcione los argumentos en el paso de adición de marca de agua en Recursos](assets/arguments_add_watermark_aem_assets.png)

1. Guarde el flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]** con el paso de marca de agua.
1. En la interfaz de usuario de AEM, cargue un recurso de ejemplo. La marca de agua aparece con el tamaño de fuente, el color, etc., en la posición configurada en los pasos anteriores.
