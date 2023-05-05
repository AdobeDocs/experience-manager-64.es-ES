---
title: Adición de una marca de agua a los recursos digitales
description: Aprenda a utilizar la función de marca de agua para agregar una marca de agua digital a los recursos.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# Marcar sus recursos digitales {#watermarking}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] le permite agregar una marca de agua digital a los recursos para ayudar a los usuarios a verificar la autenticidad y propiedad de los recursos protegida por derechos de autor. [!DNL Experience Manager Assets] admite texto que se utilizará como marca de agua en archivos PNG y JPEG.

Recursos Adobe Experience Manager permite agregar una marca de agua digital a las imágenes para ayudar a los usuarios a comprobar la autenticidad y la propiedad de los recursos protegida por derechos de autor. [!DNL Experience Manager] Assets admite texto que se utilizará como marca de agua en archivos PNG y JPEG.

Para poder aplicar una marca de agua a los recursos, agregue el paso de marca de agua en el [!UICONTROL Recurso de actualización DAM] flujo de trabajo.

1. Acceda a la [!DNL Experience Manager] interfaz de usuario y vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Flujo de trabajo]** > **[!UICONTROL Modelos]**.
1. En la página Modelos de flujo de trabajo , seleccione la opción **[!UICONTROL Recurso de actualización DAM]** flujo de trabajo y haga clic en **[!UICONTROL Editar]**.

1. En el panel lateral, arrastre el **[!UICONTROL Agregar marca de agua]** y agréguelo a la función [!UICONTROL Recurso de actualización DAM] flujo de trabajo.

   ![Arrastre el paso Agregar marca de agua al flujo de trabajo de recursos de actualización de DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque el [!UICONTROL Agregar marca de agua] pase a cualquier lugar antes de que [!UICONTROL Miniatura de proceso] paso a paso.

1. Abra el **[!UICONTROL Agregar marca de agua]** para mostrar sus propiedades.
1. En el **[!UICONTROL Argumentos]** , especifique valores válidos en los distintos campos, como texto, tipo de fuente, tamaño, color, posición, orientación, etc. Para confirmar los cambios, haga clic en **[!UICONTROL Listo]**.

   ![Proporcione los argumentos en el paso agregar marca de agua de Assets](assets/arguments_add_watermark_aem_assets.png)

1. Guarde el flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]** con el paso de marca de agua.
1. En el [!DNL Experience Manager] interfaz de usuario de , cargue un recurso de ejemplo. La marca de agua aparece con el tamaño de fuente, el color, etc., en la posición que configuró en los pasos anteriores.

Para marcar con agua documentos de PDF mediante programación o con información dinámica, considere la posibilidad de utilizar [[!DNL Experience Manager] Servicios de documentos](/help/forms/using/overview-aem-document-services.md) oferta.

## Sugerencias y limitaciones {#tips-limitations}

* Solo se admiten marcas de agua basadas en texto. Las imágenes no se utilizan como marcas de agua, aunque se pueden cargar imágenes al crear la variable [!UICONTROL Agregar proceso de marca de agua].
* Solo se admiten archivos PNG y JPEG para marcar con agua. Otros formatos de recursos no están marcados con agua.
