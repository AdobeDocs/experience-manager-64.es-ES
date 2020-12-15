---
title: Publicar carpetas en Brand Portal
description: Obtenga información sobre cómo publicar y cancelar la publicación de carpetas en Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 27%

---


# Publicar carpetas en Brand Portal {#publish-folders-to-brand-portal}

Como administrador de Adobe Experience Manager (AEM) Assets, puede publicar recursos y carpetas en la instancia de AEM Assets Brand Portal (o programar el flujo de trabajo de publicación para una fecha y hora posteriores) para su organización. Sin embargo, primero debe integrar AEM Assets con Brand Portal. Para obtener más información, consulte [Configurar AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Después de publicar un recurso o una carpeta, estará disponible para los usuarios de Brand Portal.

Si realiza las modificaciones posteriores en el recurso o la carpeta original en AEM Assets, los cambios no se reflejarán en Brand Portal hasta que vuelva a publicar el recurso o la carpeta. Esta función garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

## Publicar carpetas en Brand Portal {#publish-folders-to-brand-portal-1}

1. En la interfaz de AEM Assets, coloque el puntero sobre la carpeta deseada y seleccione la opción **[!UICONTROL Publicar]** en las acciones rápidas.

   Como alternativa, seleccione la carpeta que desee y siga los pasos posteriores.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar carpetas ahora**

   Para publicar las carpetas seleccionadas en Brand Portal, haga una de las acciones siguientes:

   * En la barra de herramientas, seleccione **[!UICONTROL Publicación rápida]**. A continuación, en el menú, seleccione **[!UICONTROL Publicar en Brand Portal]**.
   * En la barra de herramientas, seleccione **[!UICONTROL Administrar publicación]**.

3. A continuación, en la **[!UICONTROL Acción]** seleccione **[!UICONTROL Publicar en Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Ahora]**. Toque **[!UICONTROL Siguiente].**
4. En **[!UICONTROL Ámbito]**, confirme la selección y toque **[!UICONTROL Publicar en Brand Portal]**.

   Aparece un mensaje que indica que la carpeta se ha puesto en cola para su publicación en Brand Portal. Inicie sesión en la interfaz de Brand Portal para ver la carpeta publicada.

   **Publicar carpetas más tarde**

   Para programar el flujo de trabajo de publicación en Brand Portal de carpetas de recursos para una fecha u hora posterior:

   1. Una vez que haya seleccionado los recursos y las carpetas que desea publicar, seleccione **[!UICONTROL Administrar publicación]** en la barra de herramientas de la parte superior.
   2. En la página **[!UICONTROL Administrar publicación]**, seleccione **[!UICONTROL Publicar en portal de marca]** en **[!UICONTROL Acción]** y seleccione **[!UICONTROL Más adelante]** en **[!UICONTROL Programación]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque **[!UICONTROL Siguiente]**.
   4. Confirme la selección en **[!UICONTROL Ámbito]**. Toque **[!UICONTROL Siguiente]**.
   5. Especifique un título de flujo de trabajo en **[!UICONTROL Flujos de trabajo]**. Toque **[!UICONTROL Publicar posteriormente]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Cancelar publicación desde Brand Portal {#unpublish-folders-from-brand-portal}

Puede eliminar cualquier carpeta de recursos publicada en Brand Portal cancelándola de la publicación de la instancia de AEM Author. Después de cancelar la publicación de la carpeta original, su copia ya no estará disponible para los usuarios de Brand Portal.

Tiene la opción de cancelar la publicación de carpetas desde Brand Portal rápidamente o programarlas para una fecha y hora posteriores. Para cancelar la publicación de carpetas de recursos desde Brand Portal:

1. En la interfaz de AEM Assets de la instancia de AEM Author, seleccione la carpeta que desee cancelar la publicación.

   ![publish2bp-1](assets/publish2bp-1.png)

2. En la barra de herramientas, toque o haga clic en **[!UICONTROL Administrar publicación]**.

3. **Cancelar la publicación de Brand Portal ahora**

   Para cancelar rápidamente la publicación de la carpeta deseada desde Brand Portal:

   1. En la página **[!UICONTROL Administrar publicación]**, en **[!UICONTROL Acción]** seleccione **[!UICONTROL Cancelar publicación en Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Ahora]**.
   2. Toque o haga clic **[!UICONTROL Siguiente].**
   3. Dentro de **[!UICONTROL Ámbito]**, confirme la selección y toque **[!UICONTROL Cancelar la publicación desde Brand Portal]**.

   ![confirmar-cancelar publicación](assets/confirm-unpublish.png)

   **Cancelar la publicación de Brand Portal más tarde**

   Para programar la publicación de una carpeta desde Brand Portal a una fecha y hora posteriores:

   1. En la página **[!UICONTROL Administrar publicación]**, en **[!UICONTROL Acción]** seleccione **[!UICONTROL Cancelar publicación en Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Más adelante].**.
   2. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque **[!UICONTROL Siguiente]**.
   3. Dentro de **[!UICONTROL Ámbito]**, confirme la selección y toque **[!UICONTROL Siguiente]**.
   4. Especifique un **[!UICONTROL título de flujo de trabajo]** en **[!UICONTROL Flujos de trabajo]**. Toque **[!UICONTROL Cancelar la publicación posteriormente].**

      ![flujos de trabajo sin publicar](assets/unpublishworkflows.png)


>[!NOTE]
>
>El procedimiento para publicar o cancelar la publicación de un recurso en o desde Brand Portal es similar al procedimiento correspondiente para una carpeta.
