---
title: Configuración de Assets Insights
description: Obtenga información sobre cómo configurar Assets Insights en  [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 10%

---

# Configuración de Assets Insights {#configuring-asset-insights}

Adobe Experience Manager Assets recupera los datos de uso de los [!DNL Experience Manager] recursos utilizados por sitios web de terceros desde Adobe Analytics. Para permitir que Assets Insights recupere estos datos y genere perspectivas, configure primero la función para integrarla con Adobe Analytics.

>[!NOTE]
>
>Las perspectivas solo se admiten y se proporcionan para imágenes.

1. En AEM, haga clic en **[!UICONTROL Herramientas > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Haga clic en la tarjeta **[!UICONTROL Configuración de información]**.
1. En el asistente, seleccione un centro de datos y proporcione sus credenciales, incluidos el nombre de su organización, el nombre de usuario y la contraseña.

   ![chlimage_1-211](assets/insights_config2.png)

1. Pulse o haga clic en **[!UICONTROL Autenticar]**.
1. Después de que [!DNL Experience Manager] autentique sus credenciales, en la lista **[!UICONTROL Grupo de informes]**, elija un grupo de informes de Adobe Analytics desde el que desea que Assets Insights recupere datos. Haga clic en **[!UICONTROL Agregar]**.
1. Una vez [!DNL Experience Manager] configurado el grupo de informes, pulse o haga clic en **[!UICONTROL Listo]**.

## Rastreador de páginas {#page-tracker}

Después de configurar la cuenta de Analytics, se genera el código Rastreador de páginas . Para permitir que Assets Insights rastree los [!DNL Experience Manager] recursos utilizados en sitios web de terceros, incluya el código del rastreador de páginas en el código del sitio web. Utilice la utilidad Rastreador de páginas en [!DNL Experience Manager] Assets para generar el código de seguimiento de páginas. Para obtener más información sobre cómo incluir el código del rastreador de páginas en páginas web de terceros, consulte [Uso del rastreador de páginas e Incrustar código en páginas web](touch-ui-using-page-tracker.md).

1. En AEM, haga clic en **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. En la página **[!UICONTROL Navegación]**, haga clic en la tarjeta **[!UICONTROL Rastreador de páginas de perspectivas]**.
1. Haga clic en el icono **[!UICONTROL Download]** para descargar el código del rastreador de páginas.
