---
title: Utilice la función de Assets Insights para realizar un seguimiento del uso de las imágenes
description: La función de Assets Insights permite realizar un seguimiento de las clasificaciones de los usuarios y las estadísticas de uso de las imágenes que se usan en sitios web de terceros, campañas de marketing y soluciones creativas de los Adobes.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 7%

---

# Información sobre Assets {#asset-insights}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Descubra cómo la función Assets Insights permite rastrear las clasificaciones de usuario y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de Adobe.

La función Información de recursos permite realizar un seguimiento de las clasificaciones de usuario y las estadísticas de uso de los recursos que se utilizan en sitios web de terceros, campañas de marketing y soluciones creativas de los Adobes para obtener perspectivas sobre su rendimiento y popularidad.

Assets Insights captura los detalles de la actividad del usuario, como el número de veces que se clasifica, se hace clic en un recurso y las impresiones (el número de veces que se carga el recurso en el sitio web). Asigna puntuaciones a los recursos en función de estas estadísticas. Puede utilizar las puntuaciones y las estadísticas de rendimiento para seleccionar recursos populares para su inclusión en catálogos, campañas de marketing, etc. Incluso puede formular políticas de archivado y renovación de licencias para recursos en función de estas estadísticas.

Para que Assets Insights capture las estadísticas de uso de los recursos de un sitio web, debe incluir el código incrustado del recurso en el código del sitio web.

Para que Assets Insights muestre las estadísticas de uso de los recursos, configure primero la función para recuperar los datos de informes de [!DNL Adobe Analytics]. Para obtener más información, consulte [Configuración de Assets Insights](touch-ui-configuring-asset-insights.md). Para utilizar esta función en una instalación local, compre [!DNL Adobe Analytics] licencia por separado. Clientes con [!DNL Managed Services] receive [!DNL Analytics] licencia incluida con [!DNL Experience Manager]. Consulte [Descripción del producto de Managed Services](https://helpx.adobe.com/es/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Las perspectivas son compatibles y solo se proporcionan para imágenes.

## Ver estadísticas de un recurso {#viewing-statistics-for-an-asset}

Puede ver las puntuaciones de Assets Insights desde la página de metadatos.

1. En la interfaz de usuario (IU) de Assets, seleccione el recurso y, a continuación, toque o haga clic en el **[!UICONTROL Propiedades]** de la barra de herramientas.
1. En la página Propiedades , toque o haga clic en el botón **[!UICONTROL Perspectivas]** pestaña .
1. Revise los detalles de uso del recurso en la **[!UICONTROL Perspectivas]** pestaña . La variable **[!UICONTROL Puntuación]** describe el uso total de los recursos y el rendimiento total de un recurso .

   La puntuación de uso describe la cantidad de veces que se utiliza el recurso en varias soluciones.

   La variable **[!UICONTROL Impresiones]** score es el número de veces que el recurso se carga en el sitio web. El número mostrado debajo de **[!UICONTROL Clics]** es el número de veces que se hace clic en el recurso.

1. Consulte la **[!UICONTROL Estadísticas de uso]** para saber de qué entidades formaba parte el recurso y qué soluciones creativas lo utilizaron recientemente. Cuanto mayor sea el uso, buenas serán las posibilidades de que el recurso sea popular entre los usuarios. Los datos de uso se muestran en los siguientes encabezados:

   * **[!UICONTROL Activo]**: El número de veces que el recurso formaba parte de una colección o un recurso compuesto
   * **[!UICONTROL Web y dispositivos móviles]**: El número de veces que el recurso formaba parte de sitios web y aplicaciones
   * **[!UICONTROL Social]**: El número de veces que se usó el recurso en soluciones como Adobe Social y Adobe Campaign
   * **[!UICONTROL Correo electrónico]**: El número de veces que se utilizó el recurso en campañas de correo electrónico

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >La función de Assets Insights obtiene los datos de las soluciones de [!DNL Adobe Analytics] de forma periódica, es posible que la sección de soluciones no muestre los datos más recientes. El período de tiempo durante el cual se muestran los datos depende de la programación de la operación de recuperación que ejecuta Assets Insights para recuperar [!DNL Analytics] datos.

1. Para ver las estadísticas de rendimiento del recurso gráficamente durante un período de tiempo, seleccione el período en la sección **[!UICONTROL Estadísticas de rendimiento]**. Los detalles, incluidos los clics y las impresiones, se muestran como líneas de tendencia de un gráfico.

   ![Chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >A diferencia de los datos de la sección de soluciones, la sección de estadísticas de rendimiento muestra los datos más recientes.

1. Para obtener el código incrustado del recurso que incluye en los sitios web para obtener datos de rendimiento, haga clic en **[!UICONTROL Obtener código incrustado]** debajo de la miniatura del recurso. Para obtener más información sobre cómo incluir el código incrustado en páginas web de terceros, consulte [Uso del rastreador de páginas e Incrustar código en páginas web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Ver estadísticas acumuladas de recursos {#viewing-aggregate-statistics-for-assets}

Puede ver las puntuaciones de todos los recursos de una carpeta simultáneamente mediante la **[!UICONTROL Vista de la información]**.

1. En la interfaz de usuario de Assets, vaya a la carpeta que contiene los recursos para los que desea ver información.
1. Pulse o haga clic en el icono Diseño de la barra de herramientas y, a continuación, elija **[!UICONTROL Vista de perspectivas]**.
1. La página muestra las puntuaciones de uso de los recursos. Compare las clasificaciones de los distintos recursos y extraiga perspectivas.

## Programar trabajo en segundo plano {#scheduling-background-job}

Assets Insights recupera de forma periódica los datos de uso de los recursos de los grupos de informes de Adobe Analytics. De forma predeterminada, Assets Insights ejecuta un trabajo en segundo plano cada 24 horas a las 2 de la madrugada para recuperar datos. Sin embargo, puede modificar la frecuencia y la hora configurando la variable **[!UICONTROL Trabajo de sincronización de informes de rendimiento de recursos DAM de Adobe CQ]** desde la consola web.

1. Toque . [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. Abra el **[!UICONTROL Trabajo de sincronización de informes de rendimiento de recursos DAM de Adobe CQ]** configuración del servicio.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique la frecuencia del planificador que desee y la hora de inicio del trabajo en la expresión del programador de propiedades. Guarde los cambios.
