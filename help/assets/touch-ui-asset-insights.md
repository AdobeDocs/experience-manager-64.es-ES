---
title: Utilice la función Asset Insights para realizar un seguimiento del uso de las imágenes
description: La función Asset Insights permite rastrear las clasificaciones de usuarios y las estadísticas de uso de las imágenes que se usan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobe.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 8%

---


# Información sobre Assets {#asset-insights}

Descubra cómo la función Asset Insights permite rastrear las clasificaciones de usuario y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobe.

La función Asset Insights permite realizar un seguimiento de las clasificaciones de usuarios y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas del Adobe para obtener perspectivas sobre su rendimiento y popularidad.

Assets Insights captura los detalles de la actividad del usuario, como el número de veces que se clasifica, se hace clic en un recurso y las impresiones (el número de veces que se carga el recurso en el sitio web). Asigna puntuaciones a los recursos en función de estas estadísticas. Puede utilizar las puntuaciones y las estadísticas de rendimiento para seleccionar recursos populares para su inclusión en catálogos, campañas de marketing, etc. Incluso puede formular políticas de archivado y renovación de licencias para recursos en función de estas estadísticas.

Para que Assets Insights capture las estadísticas de uso de los recursos de un sitio web, debe incluir el código incrustado del recurso en el código del sitio web.

Para que Asset Insights pueda mostrar las estadísticas de uso de los recursos, configure primero la función para recuperar los datos de informes de [!DNL Adobe Analytics]. Para obtener más información, consulte [Configuración de Asset Insights](touch-ui-configuring-asset-insights.md).

>[!NOTE]
>
>Las perspectivas son compatibles y solo se proporcionan para imágenes.

## Ver estadísticas de un recurso {#viewing-statistics-for-an-asset}

Puede ver las puntuaciones de Asset Insights desde la página de metadatos.

1. En la interfaz de usuario (IU) de Assets, seleccione el recurso y, a continuación, pulse o haga clic en el icono **[!UICONTROL Propiedades]** de la barra de herramientas.
1. En la página Propiedades , pulse o haga clic en la pestaña **[!UICONTROL Perspectivas]**.
1. Revise los detalles de uso del recurso en la pestaña **[!UICONTROL Insights]**. La sección **[!UICONTROL Puntuación]** describe el uso total de los recursos y las puntuaciones de rendimiento de un recurso.

   La puntuación de uso describe la cantidad de veces que se utiliza el recurso en varias soluciones.

   La puntuación **[!UICONTROL Impresiones]** es el número de veces que el recurso se carga en el sitio web. El número mostrado en **[!UICONTROL Clicks]** es el número de veces que se hace clic en el recurso.

1. Revise la sección **[!UICONTROL Estadísticas de uso]** para saber de qué entidades formaba parte el recurso y qué soluciones creativas lo utilizaron recientemente. Cuanto mayor sea el uso, buenas serán las posibilidades de que el recurso sea popular entre los usuarios. Los datos de uso se muestran en los siguientes encabezados:

   * **[!UICONTROL Recurso]**: El número de veces que el recurso formaba parte de una colección o un recurso compuesto
   * **[!UICONTROL Web y dispositivos móviles]**: El número de veces que el recurso formaba parte de sitios web y aplicaciones
   * **[!UICONTROL Social]**: El número de veces que se usó el recurso en soluciones como Adobe Social y Adobe Campaign
   * **[!UICONTROL Correo electrónico]**: El número de veces que se utilizó el recurso en campañas de correo electrónico

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Debido a que la función Asset Insights generalmente recupera los datos de Soluciones de Adobe Analytics de forma periódica, es posible que la sección Soluciones no muestre los datos más recientes. El período de tiempo durante el cual se muestran los datos depende de la programación de la operación de recuperación que Asset Insights ejecuta para recuperar datos de Analytics.

1. Para ver las estadísticas de rendimiento del recurso gráficamente durante un período de tiempo, seleccione el período en la sección **[!UICONTROL Estadísticas de rendimiento]**. Los detalles, incluidos los clics y las impresiones, se muestran como líneas de tendencia de un gráfico.

   ![Chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >A diferencia de los datos de la sección Soluciones , la sección Estadísticas de rendimiento muestra los datos más recientes.

1. Para obtener el código incrustado del recurso que incluye en los sitios web para obtener datos de rendimiento, pulse o haga clic en **[!UICONTROL Obtener código incrustado]** debajo de la miniatura del recurso. Para obtener más información sobre cómo incluir el código incrustado en páginas web de terceros, consulte [Uso del rastreador de páginas y código incrustado en páginas web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Ver estadísticas agregadas de los recursos {#viewing-aggregate-statistics-for-assets}

Puede ver las puntuaciones de todos los recursos de una carpeta simultáneamente mediante la **[!UICONTROL Vista de la información]**.

1. En la interfaz de usuario de Assets, vaya a la carpeta que contiene los recursos para los que desea ver información.
1. Pulse o haga clic en el icono Diseño de la barra de herramientas y, a continuación, elija **[!UICONTROL Vista de perspectivas]**.
1. La página muestra las puntuaciones de uso de los recursos. Compare las clasificaciones de los distintos recursos y extraiga perspectivas.

## Programar trabajo en segundo plano {#scheduling-background-job}

Asset Insights obtiene de forma periódica datos de uso de los recursos de los grupos de informes de Adobe Analytics. De forma predeterminada, Asset Insights ejecuta un trabajo en segundo plano cada 24 horas a las 2 de la madrugada para recuperar datos. Sin embargo, puede modificar la frecuencia y la hora configurando el servicio **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** desde la consola web.

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. Abra la configuración del servicio **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique la frecuencia del planificador que desee y la hora de inicio del trabajo en la expresión del programador de propiedades. Guarde los cambios.
