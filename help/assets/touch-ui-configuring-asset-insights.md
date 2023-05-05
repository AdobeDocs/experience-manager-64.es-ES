---
title: Configuración de Assets Insights
description: Obtenga información sobre cómo configurar Assets Insights en [!DNL Experience Manager] Recursos.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 11%

---

# Configuración de Assets Insights {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets obtiene datos de uso alrededor de [!DNL Experience Manager] recursos utilizados por sitios web de terceros de Adobe Analytics. Para permitir que Assets Insights recupere estos datos y genere perspectivas, configure primero la función para integrarla con Adobe Analytics.

>[!NOTE]
>
>Las perspectivas solo se admiten y se proporcionan para imágenes.

1. En AEM, haga clic en **[!UICONTROL Herramientas > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Haga clic en la tarjeta **[!UICONTROL Configuración de información]**.
1. En el asistente, seleccione un centro de datos y proporcione sus credenciales, incluidos el nombre de su organización, el nombre de usuario y la contraseña.

   ![chlimage_1-211](assets/insights_config2.png)

1. Pulse o haga clic en **[!UICONTROL Autenticar]**.
1. Después [!DNL Experience Manager] autentica las credenciales, desde el **[!UICONTROL Grupo de informes]** elija un grupo de informes de Adobe Analytics desde el que quiera que Assets Insights recupere datos. Haga clic en **[!UICONTROL Agregar]**.
1. Después [!DNL Experience Manager] configura su grupo de informes, toque o haga clic en **[!UICONTROL Listo]**.

## Rastreador de páginas {#page-tracker}

Después de configurar la cuenta de Analytics, se genera el código Rastreador de páginas . Para habilitar el seguimiento de Assets Insights [!DNL Experience Manager] recursos utilizados en sitios web de terceros, incluya el código de seguimiento de página en el código del sitio web. Utilice la utilidad Rastreador de páginas en [!DNL Experience Manager] Recursos para generar el código del rastreador de páginas. Para obtener más información sobre cómo incluir el código del rastreador de páginas en páginas web de terceros, consulte [Uso del rastreador de páginas e Incrustar código en páginas web](touch-ui-using-page-tracker.md).

1. En AEM, haga clic en el botón **[!UICONTROL Herramientas > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. En la página **[!UICONTROL Navegación]**, haga clic en la tarjeta **[!UICONTROL Rastreador de páginas de perspectivas]**.
1. Haga clic en el **[!UICONTROL Descargar]** para descargar el código del rastreador de páginas.
