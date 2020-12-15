---
title: Configuración de perspectivas de recursos
description: Obtenga información sobre cómo configurar las perspectivas de recursos en AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 10%

---


# Configuración de perspectivas de recursos {#configuring-asset-insights}

Adobe Experience Manager (AEM) Assets obtiene de Adobe Analytics datos de uso de AEM recursos utilizados por sitios web de terceros. Para habilitar Asset Insights para recuperar estos datos y generar perspectivas, primero configure la función para integrarla con Adobe Analytics.

>[!NOTE]
>
>Las perspectivas solo son compatibles y se proporcionan para imágenes.

1. En AEM, haga clic en **[!UICONTROL Herramientas > Assets]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Haga clic en la tarjeta **[!UICONTROL Configuración de información]**.
1. En el asistente, seleccione un centro de datos y proporcione sus credenciales, incluido el nombre de su organización, el nombre de usuario y la contraseña.

   ![chlimage_1-211](assets/insights_config2.png)

1. Pulse o haga clic en **[!UICONTROL Autenticar]**.
1. Después de AEM autenticar las credenciales, en la lista **[!UICONTROL Grupo de informes]**, elija un grupo de informes de Adobe Analytics desde el que desee que Asset Insights recopile datos. Haga clic en **[!UICONTROL Agregar]**.
1. Después de AEM configure el grupo de informes, toque o haga clic **[!UICONTROL Listo]**.

## Rastreador de páginas {#page-tracker}

Después de configurar la cuenta de Analytics, se genera el código de rastreador de páginas. Para permitir que Assets Insights rastree AEM recursos utilizados en sitios web de terceros, incluya el código del rastreador de páginas en el código del sitio web. Utilice la utilidad Rastreador de páginas de AEM Assets para generar el código del rastreador de páginas. Para obtener más información sobre cómo incluir el código del rastreador de páginas en páginas web de terceros, consulte [Uso del rastreador de páginas y el código incrustado en páginas web](touch-ui-using-page-tracker.md).

1. En AEM, haga clic en **[!UICONTROL Herramientas > Recursos]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. En la página **[!UICONTROL Navegación]**, haga clic en la tarjeta **[!UICONTROL Rastreador de páginas de perspectivas]**.
1. Haga clic en el icono **[!UICONTROL Descargar]** para descargar el código del rastreador de páginas.