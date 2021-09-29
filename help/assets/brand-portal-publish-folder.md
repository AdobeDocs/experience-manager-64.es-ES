---
title: Publicar carpetas en Brand Portal
description: Obtenga información sobre cómo publicar y cancelar la publicación de carpetas en Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# Publicar carpetas en Brand Portal {#publish-folders-to-brand-portal}

Como administrador de Adobe Experience Manager Assets, puede publicar recursos y carpetas en la instancia [!DNL Experience Manager Assets Brand Portal] (o programar el flujo de trabajo de publicación para una fecha y hora posteriores) de su organización. Sin embargo, primero debe integrar [!DNL Experience Manager Assets] con [!DNL Brand Portal]. Para obtener más información, consulte [Configuración [!DNL Experience Manager Assets] con Brand Portal](configure-aem-assets-with-brand-portal.md).

Después de publicar un recurso o una carpeta, estará disponible para los usuarios de Brand Portal.

Si realiza las modificaciones posteriores al recurso o la carpeta originales en [!DNL Assets], los cambios no se reflejarán en Brand Portal hasta que vuelva a publicar el recurso o la carpeta. Esta función garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

## Publicar carpetas en Brand Portal {#publish-folders-to-brand-portal-1}

1. En la interfaz [!DNL Assets], pase el ratón sobre la carpeta deseada y seleccione la opción **[!UICONTROL Publicar]** en las acciones rápidas.

   Como alternativa, seleccione la carpeta deseada y siga los pasos adicionales.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar carpetas ahora**

   Para publicar las carpetas seleccionadas en Brand Portal, haga una de las acciones siguientes:

   * En la barra de herramientas, seleccione **[!UICONTROL Publicación rápida]**. A continuación, en el menú, seleccione **[!UICONTROL Publicar en Brand Portal]**.
   * En la barra de herramientas, seleccione **[!UICONTROL Administrar publicación]**.

3. A continuación, en **[!UICONTROL Action]** seleccione **[!UICONTROL Publicar en Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Ahora]**. Toque **[!UICONTROL Siguiente].**
4. Dentro de **[!UICONTROL Scope]**, confirme la selección y pulse **[!UICONTROL Publicar en Brand Portal]**.

   Aparece un mensaje que indica que la carpeta se ha puesto en cola para su publicación en Brand Portal. Inicie sesión en la interfaz de Brand Portal para ver la carpeta publicada.

   **Publicar carpetas más tarde**

   Para programar el flujo de trabajo de publicación en Brand Portal de las carpetas de recursos para una fecha u hora posterior:

   1. Una vez que haya seleccionado los recursos o carpetas que desea publicar, seleccione **[!UICONTROL Administrar publicación]** en la barra de herramientas de la parte superior.
   2. En la página **[!UICONTROL Administrar publicación]**, seleccione **[!UICONTROL Publicar en Brand Portal]** en **[!UICONTROL Acción]** y seleccione **[!UICONTROL Más adelante]** en **[!UICONTROL Programación]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque **[!UICONTROL Siguiente]**.
   4. Confirme la selección en **[!UICONTROL Ámbito]**. Toque **[!UICONTROL Siguiente]**.
   5. Especifique un título de flujo de trabajo en **[!UICONTROL Flujos de trabajo]**. Toque **[!UICONTROL Publicar posteriormente]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Cancelar publicación desde Brand Portal {#unpublish-folders-from-brand-portal}

Puede eliminar cualquier carpeta de recursos publicada en Brand Portal cancelando la publicación de la instancia de autor [!DNL Experience Manager]. Después de cancelar la publicación de la carpeta original, su copia ya no estará disponible para los usuarios de Brand Portal.

Tiene la opción de cancelar la publicación de carpetas de Brand Portal rápidamente o programarlas para una fecha y hora posteriores. Para cancelar la publicación de carpetas de recursos desde Brand Portal:

1. En la interfaz [!DNL Assets] de la instancia de autor [!DNL Experience Manager], seleccione la carpeta en la que desea cancelar la publicación.

   ![publish2bp-1](assets/publish2bp-1.png)

2. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Administrar publicación]**.

3. **Cancelar publicación desde Brand Portal ahora**

   Para cancelar la publicación de la carpeta deseada rápidamente desde Brand Portal:

   1. En la página **[!UICONTROL Administrar publicación]**, en **[!UICONTROL Acción]** seleccione **[!UICONTROL Cancelar publicación de Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Ahora]**.
   2. Toque o haga clic en **[!UICONTROL Siguiente].**
   3. Dentro de **[!UICONTROL Scope]**, confirme la selección y pulse **[!UICONTROL Cancelar publicación desde Brand Portal]**.

   ![confirmar-cancelar publicación](assets/confirm-unpublish.png)

   **Cancelar publicación desde Brand Portal más tarde**

   Para programar la publicación de una carpeta desde Brand Portal para una fecha y hora posteriores:

   1. En la página **[!UICONTROL Administrar publicación]**, en **[!UICONTROL Acción]** seleccione **[!UICONTROL Cancelar publicación de Brand Portal]** y, en **[!UICONTROL Programación]**, seleccione **[!UICONTROL Más tarde].**
   2. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque **[!UICONTROL Siguiente]**.
   3. Dentro de **[!UICONTROL Scope]**, confirme la selección y pulse **[!UICONTROL Next]**.
   4. Especifique un **[!UICONTROL Título del flujo de trabajo]** en **[!UICONTROL Flujos de trabajo]**. Toque **[!UICONTROL Cancelar publicación posteriormente].**

      ![flujos de trabajo sin publicar](assets/unpublishworkflows.png)


>[!NOTE]
>
>El procedimiento para publicar o cancelar la publicación de un recurso en Brand Portal es similar al procedimiento correspondiente para una carpeta.
