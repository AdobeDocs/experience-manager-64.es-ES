---
title: Añadir una marca de agua en los recursos digitales
description: Aprenda a utilizar la función de marca de agua para añadir una marca de agua digital a los recursos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfd6d022ef7d21ab6fc4ed17483890eb5766af18
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 3%

---


# Marcar los recursos digitales {#watermarking}

[!DNL Adobe Experience Manager Assets] le permite agregar una marca de agua digital a los recursos para ayudar a los usuarios a verificar la autenticidad y propiedad de los derechos de autor de los recursos. [!DNL Experience Manager Assets] admite texto que se va a utilizar como marca de agua en archivos PNG y JPEG.

Recursos Adobe Experience Manager (AEM) permite agregar una marca de agua digital a las imágenes para ayudar a los usuarios a comprobar la autenticidad y propiedad de los recursos con copyright. AEM Assets admite texto que se va a utilizar como marca de agua en archivos PNG y JPEG.

Para poder aplicar marcas de agua a los recursos, agregue el paso de la marca de agua en el flujo de trabajo [!UICONTROL Recurso de actualización de DAM].

1. Acceda a la interfaz de usuario [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Flujo de trabajo]** > **[!UICONTROL Modelos]**.
1. En la página Modelos de flujo de trabajo, seleccione el flujo de trabajo **[!UICONTROL Recurso de actualización de DAM]** y haga clic en **[!UICONTROL Editar]**.

1. En el panel lateral, arrastre el paso **[!UICONTROL Añadir marca de agua]** y agréguela al flujo de trabajo [!UICONTROL Recurso de actualización de DAM].

   ![Arrastre el paso Agregar marca de agua en el flujo de trabajo de recursos de actualización de DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque el paso [!UICONTROL Añadir marca de agua] en cualquier lugar antes del paso [!UICONTROL Procesar miniatura].

1. Abra el paso **[!UICONTROL Añadir marca de agua]** para mostrar sus propiedades.
1. En la ficha **[!UICONTROL Argumentos]**, especifique valores válidos en los distintos campos, incluyendo texto, tipo de fuente, tamaño, color, posición, orientación, etc. Para confirmar los cambios, haga clic en **[!UICONTROL Listo]**.

   ![Proporcione los argumentos en el paso de adición de marca de agua en Recursos](assets/arguments_add_watermark_aem_assets.png)

1. Guarde el flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]** con el paso de marca de agua.
1. En la interfaz de usuario AEM, cargue un recurso de ejemplo. La marca de agua aparece con el tamaño de fuente, el color, etc., en la posición configurada en los pasos anteriores.

Para marcar documentos PDF mediante programación o con información dinámica, considere la posibilidad de utilizar la oferta de [servicios de Documento de AEM](/help/forms/using/overview-aem-document-services.md).

## Sugerencias y limitaciones {#tips-limitations}

* Solo se admiten marcas de agua basadas en texto. Las imágenes no se utilizan como marcas de agua, aunque puede cargar imágenes al crear el [!UICONTROL proceso de Añadir marca de agua].
* Solo se admiten archivos PNG y JPEG para marcar con agua. Otros formatos de recursos no están marcados con agua.
