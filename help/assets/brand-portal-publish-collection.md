---
title: Publicar colecciones en Brand Portal
description: Descubra cómo publicar y cancelar la publicación de colecciones en Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Publish collections to Brand Portal {#publish-collections-to-brand-portal}

Como administrador de Recursos Adobe Experience Manager (AEM), puede publicar colecciones en la instancia de AEM Assets Brand Portal para su organización. Sin embargo, primero debe integrar Recursos AEM con Brand Portal. Para obtener más información, consulte [Configuración de la integración de AEM Assets con Brand Portal](brand-portal-configuring-integration.md).

Si realiza las modificaciones posteriores a la colección original en Recursos AEM, los cambios no se reflejan en Brand Portal hasta que vuelva a publicar la colección. Esta característica garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

>[!NOTE]
>
>Los fragmentos de contenido no se pueden publicar en Brand Portal. Por lo tanto, si selecciona fragmentos de contenido en AEM Author, la acción **[Publicar en Brand Portal]** no estará disponible.
>
>Si las colecciones que contienen fragmentos de contenido se publican desde AEM Author hasta Brand Portal, todos los contenidos de la carpeta, excepto los fragmentos de contenido, se replican en la interfaz de Brand Portal.

## Publicación de una colección en Brand Portal {#publish-a-collection-to-brand-portal}

1. En la interfaz de usuario de Recursos AEM, toque o haga clic en el logotipo de AEM. A continuación, vaya a **[!UICONTROL Recursos > Colecciones]** desde la página **[!UICONTROL de navegación]** .
2. En la consola Colecciones, seleccione la colección que desee publicar en Brand Portal.

   ![select_collection](assets/select_collection.png)

3. En la barra de herramientas, toque o haga clic en **[!UICONTROL Publicar en Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. En el cuadro de diálogo de confirmación, toque o haga clic en **[!UICONTROL Publicar]**.
5. Cierre el mensaje de confirmación.
6. Inicie sesión en Brand Portal como administrador. La colección publicada está disponible en la consola Colecciones.

   ![publish_collection](assets/published_collection.png)

## Cancelar la publicación de colecciones {#unpublish-collections}

Puede cancelar la publicación de las colecciones que publica desde Recursos AEM en Brand Portal. Una vez que haya cancelado la publicación de la colección original, su copia ya no estará disponible para los usuarios de Brand Portal.

1. Desde la consola Colecciones de la instancia de Recursos AEM y seleccione la colección que desee cancelar la publicación.

   ![select_collection-1](assets/select_collection-1.png)

2. En la barra de herramientas, toque o haga clic en el icono **[!UICONTROL Eliminar de Brand Portal]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. En el cuadro de diálogo, toque o haga clic en **[!UICONTROL Cancelar publicación]**.
4. Cierre el mensaje de confirmación. La colección se elimina de la interfaz de Brand Portal.
