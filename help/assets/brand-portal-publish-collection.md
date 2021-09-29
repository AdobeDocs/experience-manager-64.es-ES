---
title: Publicar colecciones en Brand Portal
description: Obtenga información sobre cómo publicar y cancelar la publicación de colecciones en Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 22%

---

# Publicar colecciones en Brand Portal {#publish-collections-to-brand-portal}

Como administrador de Adobe Experience Manager Assets, puede publicar colecciones en la instancia [!DNL Experience Manager Assets Brand Portal] de su organización. Sin embargo, primero debe integrar Recursos con Brand Portal. Para obtener más información, consulte [Configurar Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Si realiza las modificaciones posteriores a la colección original en Assets, los cambios no se reflejarán en Brand Portal hasta que vuelva a publicar la colección. Esta característica garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

>[!NOTE]
>
>Los fragmentos de contenido no se pueden publicar en Brand Portal. Por lo tanto, si selecciona fragmentos de contenido en [!DNL Experience Manager] Autor, la acción **[Publicar en Brand Portal]** no estará disponible.
>
>Si las colecciones que contienen fragmentos de contenido se publican de [!DNL Experience Manager] Autor a Brand Portal, todo el contenido de la carpeta, excepto los fragmentos de contenido, se replican en la interfaz de Brand Portal.

## Publicación de una colección en Brand Portal {#publish-a-collection-to-brand-portal}

1. En la interfaz de usuario de Assets, pulse o haga clic en el logotipo [!DNL Experience Manager]. A continuación, vaya a **[!UICONTROL Assets > Colecciones]** desde la página **[!UICONTROL Navegación]**.
2. En la consola Colecciones , seleccione la colección que desee publicar en Brand Portal.

   ![select_collection](assets/select_collection.png)

3. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Publicar en Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. En el cuadro de diálogo de confirmación, pulse o haga clic en **[!UICONTROL Publicar]**.
5. Cierre el mensaje de confirmación.
6. Inicie sesión en Brand Portal como administrador. La colección publicada está disponible en la consola Colecciones.

   ![published_collection](assets/published_collection.png)

## Cancelar la publicación de colecciones {#unpublish-collections}

Puede cancelar la publicación de colecciones que publica desde Assets en Brand Portal. Después de cancelar la publicación de la colección original, la copia ya no estará disponible para los usuarios de Brand Portal.

1. En la consola Colecciones de su instancia [!DNL Assets] y seleccione la colección que desea cancelar la publicación.

   ![select_collection-1](assets/select_collection-1.png)

2. En la barra de herramientas, pulse o haga clic en el icono **[!UICONTROL Quitar de Brand Portal]**.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. En el cuadro de diálogo, pulse o haga clic en **[!UICONTROL Cancelar publicación]**.
4. Cierre el mensaje de confirmación. La colección se quita de la interfaz de Brand Portal.
