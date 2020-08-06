---
title: Publicar colecciones en Brand Portal
description: Descubra cómo publicar y cancelar la publicación de colecciones en Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 21%

---


# Publicar colecciones en Brand Portal {#publish-collections-to-brand-portal}

Como administrador de Adobe Experience Manager (AEM) Assets, puede publicar colecciones en la instancia de AEM Assets Brand Portal para su organización. Sin embargo, primero debe integrar AEM Assets con Brand Portal. Para obtener más información, consulte [Configurar AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Si realiza las modificaciones posteriores a la colección original en AEM Assets, los cambios no se reflejan en Brand Portal hasta que vuelva a publicar la colección. Esta característica garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

>[!NOTE]
>
>Los fragmentos de contenido no se pueden publicar en Brand Portal. Therefore, if you select content fragment(s) on AEM Author, then **[Publish to Brand Portal]** action is not available.
>
>Si las colecciones que contienen fragmentos de contenido se publican desde AEM Author hasta Brand Portal, todos los contenidos de la carpeta, excepto los fragmentos de contenido, se replican en la interfaz de Brand Portal.

## Publicación de una colección en Brand Portal {#publish-a-collection-to-brand-portal}

1. En la interfaz de usuario de AEM Assets, toque o haga clic en el logotipo de AEM. A continuación, vaya a **[!UICONTROL Recursos > Colecciones]** desde la página **[!UICONTROL de navegación]** .
2. En la consola Colecciones, seleccione la colección que desee publicar en Brand Portal.

   ![select_collection](assets/select_collection.png)

3. From the toolbar, tap/click **[!UICONTROL Publish to Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. In the confirmation dialog, tap/click **[!UICONTROL Publish]**.
5. Cierre el mensaje de confirmación.
6. Inicie sesión en Brand Portal como administrador. La colección publicada está disponible en la consola Colecciones.

   ![publish_collection](assets/published_collection.png)

## Cancelar la publicación de colecciones {#unpublish-collections}

Puede cancelar la publicación de las colecciones que publique desde AEM Assets en Brand Portal. Una vez que haya cancelado la publicación de la colección original, su copia ya no estará disponible para los usuarios de Brand Portal.

1. En la consola Colecciones de la instancia de AEM Assets, seleccione la colección que desee cancelar la publicación.

   ![select_collection-1](assets/select_collection-1.png)

2. From the toolbar, tap/click the **[!UICONTROL Remove from Brand Portal]** icon.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. In the dialog, tap/click **[!UICONTROL Unpublish]**.
4. Cierre el mensaje de confirmación. La colección se quita de la interfaz de Brand Portal.
