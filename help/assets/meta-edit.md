---
title: Edición o adición de metadatos
description: Obtenga información sobre los metadatos de recursos en [!DNL Experience Manager] Recursos y varias formas de editar los metadatos de los recursos.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 9%

---

# Edición o adición de metadatos {#how-to-edit-or-add-metadata}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los metadatos son información adicional sobre el recurso que se puede buscar. Se extrae automáticamente al cargar una imagen. Puede editar los metadatos existentes o agregar nuevas propiedades de metadatos a los campos existentes (por ejemplo, cuando un campo de metadatos está en blanco).

Debido a que las empresas necesitan vocabularios de metadatos controlados y confiables, [!DNL Experience Manager] Los recursos no permiten la adición ad hoc de nuevas propiedades de metadatos. Aunque los autores no pueden agregar nuevos campos de metadatos para los recursos, los desarrolladores sí pueden. Consulte [Creación de una nueva propiedad de metadatos para recursos](meta-edit.md#editing-metadata-schema).

## Edición de metadatos de un recurso {#editing-metadata-for-an-asset}

Para editar metadatos:

1. Realice una de las siguientes acciones:

   * En la interfaz de usuario de Assets, seleccione el recurso y toque o haga clic en el **[!UICONTROL Ver propiedades]** de la barra de herramientas.
   * En la miniatura del recurso, seleccione el **[!UICONTROL Ver propiedades]** acción rápida.
   * En la página de recursos, toque o haga clic en el **[!UICONTROL Ver propiedades]** icono ![icono de información](assets/do-not-localize/info_icon.png) en la barra de herramientas.

   La página de recursos muestra todos los metadatos del recurso. Estos metadatos se extraían automáticamente cuando se cargaban (incorporaban) en [!DNL Experience Manager] Recursos.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Edite los metadatos de las distintas pestañas, según sea necesario, y cuando termine, pulse o haga clic en **[!UICONTROL Guardar]** en la barra de herramientas para guardar los cambios. Pulse o haga clic en **[!UICONTROL Cerrar]** para volver a la interfaz web de Assets.

   >[!NOTE]
   >
   >Si un campo de texto está vacío, no hay ningún conjunto de metadatos existente. Puede introducir un valor en el campo y guardarlo para añadir esa propiedad de metadatos.

Cualquier cambio en los metadatos de un recurso se vuelve a escribir en el binario original como parte de sus datos XMP. Esto se realiza mediante AEM flujo de trabajo de reescritura de metadatos. Cambios realizados en las propiedades existentes (como `dc:title`) se sobrescriben y se crean recientemente (incluidas propiedades personalizadas como `cq:tags`) se añaden al esquema .

XMP reescritura es compatible y está habilitada para las plataformas y los formatos de archivo descritos en [Requisitos técnicos.](/help/sites-deploying/technical-requirements.md)

## Edición del esquema de metadatos {#editing-metadata-schema}

Para obtener más información sobre cómo editar el esquema de metadatos, consulte [Edición de formularios de esquema de metadatos](metadata-schemas.md#editing-metadata-schema-forms).

## Registro de un espacio de nombres personalizado en [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

Puede agregar sus propias áreas de nombres dentro de AEM. Del mismo modo que hay áreas de nombres predefinidas como cq, jcr y sling, puede tener un espacio de nombres para los metadatos del repositorio y el procesamiento xml.

1. Vaya a la página de administración del tipo de nodo `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Toque o haga clic en **[!UICONTROL Espacios de nombres]** en la parte superior de la página. La página de administración del área de nombres se muestra en una ventana.

1. Para agregar un área de nombres, toque o haga clic en **[!UICONTROL Nuevo]** en la parte inferior.
1. Especifique un área de nombres personalizada en la convención de área de nombres XML (especifique el id en forma de URI y un prefijo asociado para el id) y pulse o haga clic en **[!UICONTROL Guardar]**.

## Sugerencias y limitaciones {#best-practices-limitations}

* Las actualizaciones de metadatos mediante la interfaz de usuario táctil cambian las propiedades de los metadatos en la variable `dc` espacio de nombres. Cualquier actualización realizada mediante la API HTTP cambia las propiedades de los metadatos en la variable `jcr` espacio de nombres. Consulte [actualización de metadatos mediante la API HTTP](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [Acerca de los metadatos y sus necesidades en Assets](metadata.md)

