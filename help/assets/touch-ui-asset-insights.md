---
title: Utilice la función de perspectivas de recursos para realizar un seguimiento del uso de las imágenes
description: La función de perspectivas de recursos le permite realizar un seguimiento de las clasificaciones de usuarios y las estadísticas de uso de las imágenes que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobes.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 8%

---


# Información sobre Assets {#asset-insights}

Descubra cómo la función de perspectivas de recursos le permite realizar un seguimiento de las clasificaciones de usuarios y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobe.

La función de perspectivas de recursos le permite rastrear las clasificaciones de usuarios y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobes para obtener perspectivas sobre su rendimiento y popularidad.

Assets Insights captura los detalles de la actividad del usuario, como el número de veces que se califica, hace clic y las impresiones de un recurso (el número de veces que se carga el recurso en el sitio web). Asigna puntuaciones a los recursos en función de estas estadísticas. Puede utilizar las estadísticas de rendimiento y puntuaciones para seleccionar los recursos populares para su inclusión en catálogos, campañas de marketing, etc. Puede incluso formular políticas de archivado y renovación de licencias para los recursos en función de estas estadísticas.

Para que Assets Insights capture estadísticas de uso de recursos de un sitio web, debe incluir el código incrustado del recurso en el código del sitio web.

Para que Asset Insights pueda mostrar las estadísticas de uso de los recursos, primero configure la función de la que desea obtener datos de sistema de informes de [!DNL Adobe Analytics]. Para obtener más información, consulte [Configuración de perspectivas](touch-ui-configuring-asset-insights.md)de recursos.

>[!NOTE]
>
>Las perspectivas solo se admiten para imágenes.

## Estadísticas de Vista de un recurso {#viewing-statistics-for-an-asset}

Puede realizar la vista de las puntuaciones de perspectivas de recursos desde la página de metadatos.

1. En la interfaz de usuario de Recursos, seleccione el recurso y, a continuación, toque o haga clic en el icono **[!UICONTROL Propiedades]** de la barra de herramientas.
1. En la página Propiedades, toque o haga clic en la ficha **[!UICONTROL Perspectivas]** .
1. Revise los detalles de uso del recurso en la ficha **[!UICONTROL Perspectivas]** . La sección **[!UICONTROL Puntuación]** describe el uso total de recursos y las recuperaciones de rendimiento de un recurso.

   La puntuación de uso describe la cantidad de veces que se utiliza el recurso en varias soluciones.

   La puntuación de **[!UICONTROL impresiones]** es el número de veces que el recurso se carga en el sitio web. El número que se muestra en **[!UICONTROL Clics]** es el número de veces que se hace clic en el recurso.

1. Revise la sección Estadísticas **[!UICONTROL de]** uso para saber de qué entidades formaba parte el recurso y qué soluciones creativas lo utilizaron recientemente. Cuanto mayor sea el uso, buenas serán las posibilidades de que el recurso sea popular entre los usuarios. Los datos de uso se muestran en los siguientes encabezados:

   * **[!UICONTROL Recurso]**: Número de veces que el recurso formaba parte de una colección o un recurso compuesto
   * **[!UICONTROL Web y móvil]**: El número de veces que el recurso formaba parte de sitios web y aplicaciones
   * **[!UICONTROL Social]**: El número de veces que se ha utilizado el recurso en soluciones como Adobe Social y Adobe Campaign
   * **[!UICONTROL Correo electrónico]**: El número de veces que el recurso se ha utilizado en campañas de correo electrónico

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Debido a que la función de perspectivas de recursos generalmente recopila los datos de soluciones de Adobe Analytics de forma periódica, es posible que la sección Soluciones no muestre los datos más recientes. El período de tiempo durante el cual se muestran los datos depende de la programación de la operación de recuperación que se ejecuta Asset Insights para recuperar datos de Analytics.

1. Para ver las estadísticas de rendimiento del recurso gráficamente durante un período de tiempo, seleccione el período en la sección **[!UICONTROL Estadísticas de rendimiento]**. Los detalles, incluidos los clics y las impresiones, se muestran como líneas de tendencia de un gráfico.

   ![climage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >A diferencia de los datos de la sección Soluciones, la sección Estadísticas de rendimiento muestra los datos más recientes.

1. Para obtener el código incrustado del recurso que incluye en los sitios web con el fin de obtener datos de rendimiento, toque o haga clic en **[!UICONTROL Obtener código]** incrustado debajo de la miniatura del recurso. Para obtener más información sobre cómo incluir el código incrustado en páginas web de terceros, consulte [Uso del rastreador de páginas y código incrustado en páginas](touch-ui-using-page-tracker.md)web.

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Estadísticas acumuladas de Vista de activos {#viewing-aggregate-statistics-for-assets}

Puede ver las puntuaciones de todos los recursos de una carpeta simultáneamente mediante la **[!UICONTROL Vista de la información]**.

1. En la interfaz de usuario de Recursos, desplácese a la carpeta que contenga los recursos para los que desee realizar la vista.
1. Toque o haga clic en el icono Diseño de la barra de herramientas y, a continuación, elija **[!UICONTROL Vista]** de perspectivas.
1. La página muestra las puntuaciones de uso de los recursos. Compare las clasificaciones de los distintos recursos y obtenga perspectivas.

## Programar trabajo en segundo plano {#scheduling-background-job}

Asset Insights obtiene de forma periódica los datos de uso de los recursos de los grupos de informes de Adobe Analytics. De forma predeterminada, Asset Insights ejecuta un trabajo en segundo plano cada 24 horas a las 2 de la madrugada para recuperar datos. Sin embargo, puede modificar tanto la frecuencia como la hora configurando el servicio Trabajo **[!UICONTROL de sincronización de informes de rendimiento de recursos DAM de]** Adobe CQ desde la consola web.

1. Pulse el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. Abra la configuración del servicio Trabajo **[!UICONTROL de sincronización de informes de rendimiento de recursos DAM de]** Adobe CQ.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique la frecuencia de Planificador deseada y la hora de inicio del trabajo en la expresión de Planificador de propiedades. Guarde los cambios.
