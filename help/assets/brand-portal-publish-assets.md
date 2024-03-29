---
title: Publicar carpetas en Brand Portal
description: Obtenga información sobre cómo publicar y cancelar la publicación de recursos en Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 30%

---

# Publicar recursos en Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Como administrador de Adobe Experience Manager Assets, puede publicar recursos en [!DNL Experience Manager Assets Brand Portal] (o programe el flujo de trabajo de publicación para una fecha y hora posteriores) para su organización. Sin embargo, primero debe configurar [!DNL Assets] con [!DNL Brand Portal]. Para obtener más información, consulte [Configurar [!DNL Assets] con [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

Después de publicar un recurso, este está disponible para los usuarios de Brand Portal.

Si realiza las modificaciones posteriores al recurso original en [!DNL Assets], los cambios no se reflejarán en Brand Portal hasta que vuelva a publicar el recurso. Esta función garantiza que los cambios en curso no estén disponibles en Brand Portal. Solo los cambios aprobados publicados por un administrador están disponibles en Brand Portal.

Una vez que la replicación se haya realizado correctamente, puede publicar recursos, carpetas y colecciones en [!DNL Brand Portal]. Para publicar recursos en Brand Portal, siga estos pasos:

>[!NOTE]
>
>Adobe recomienda la publicación escalonada, preferiblemente durante las horas no pico, para que la variable [!DNL Experience Manager] el autor no ocupa recursos excesivos.

1. En la consola Recursos , pase el ratón sobre los recursos que quiera y seleccione **[!UICONTROL Publicación]** de las acciones rápidas.

   También puede seleccionar los recursos que desea publicar en Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Para publicar los recursos en Brand Portal, hay dos opciones disponibles:
   * [Publicar recursos inmediatamente](#publish-now)
   * [Publicar recursos más tarde](#publish-later)

## Publicar recursos ahora {#publish-now}

Para publicar los recursos seleccionados en Brand Portal, haga una de las acciones siguientes:

* En la barra de herramientas, seleccione **[!UICONTROL Publicación rápida]**. A continuación, en el menú , seleccione **[!UICONTROL Publicar en Brand Portal]**.

* En la barra de herramientas, seleccione **[!UICONTROL Administrar publicación]**.

   1. A continuación, desde el **[!UICONTROL Acción]** select **[!UICONTROL Publicar en Brand Portal]** y de **[!UICONTROL Programación]** select **[!UICONTROL Ahora]**. Toque o haga clic **[!UICONTROL Siguiente].**

   2. Within **[!UICONTROL Ámbito]**, confirme la selección y pulse o haga clic en **[!UICONTROL Publicar en Brand Portal]**.

Aparece un mensaje que indica que los recursos se han puesto en cola para su publicación en Brand Portal. Inicie sesión en la interfaz de Brand Portal para ver los recursos publicados.

## Publicar recursos más tarde {#publish-later}

Para programar la publicación de recursos en Brand Portal para una fecha u hora posterior:

1. Una vez que haya seleccionado los recursos o carpetas que desea publicar, seleccione **[!UICONTROL Administrar publicación]** en la barra de herramientas de la parte superior.
2. Activado **[!UICONTROL Administrar publicación]** página, seleccione **[!UICONTROL Publicar en Brand Portal]** from **[!UICONTROL Acción]** y seleccione **[!UICONTROL Más tarde]** from **[!UICONTROL Programación]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque o haga clic **[!UICONTROL Siguiente]**.
4. Seleccione una **[!UICONTROL Fecha de activación]** y especifique la hora. Toque o haga clic **[!UICONTROL Siguiente]**.
5. Especifique un título de flujo de trabajo en **[!UICONTROL Flujos de trabajo]**. Toque o haga clic **[!UICONTROL Publicar más tarde]**.

   ![publishworkflow](assets/publishworkflow.png)

Ahora, inicie sesión en Brand Portal para ver si los recursos publicados están disponibles en la interfaz de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
