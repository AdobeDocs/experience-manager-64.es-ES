---
title: Visualización de datos de análisis de la página
seo-title: Seeing Page Analytics Data
description: Utilice los datos de análisis de la página para medir la eficacia del contenido de la página
seo-description: Use page analytics data to gauge the effectiveness of their page content
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 6509c0ce-fc3a-4248-8dc7-db10602c30d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 14%

---

# Visualización de datos de análisis de la página{#seeing-page-analytics-data}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Utilice los datos de análisis de la página para medir la eficacia del contenido de la página.

## Analytics visible desde la consola {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Los datos de análisis de página se muestran en [Vista de lista](/help/sites-authoring/basic-handling.md#list-view) de la consola Sitios . Cuando las páginas se muestran en formato de lista, las siguientes columnas están disponibles de forma predeterminada:

* Vistas de la página
* Visitantes únicos
* Tiempo empleado en la página

Cada columna muestra un valor para el período de informe actual y también indica si el valor ha aumentado o disminuido desde el período de informe anterior. Los datos que ve se actualizan cada 12 horas.

>[!NOTE]
>
>Para cambiar el periodo de actualización, [configuración del intervalo de importación](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Abra el **Sitios** consola; por ejemplo [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. En el extremo derecho de la barra de herramientas (esquina superior derecha), toque o haga clic en el icono para seleccionar **Vista de lista** (el icono mostrado dependerá de la variable [vista actual](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. De nuevo, en el extremo derecho de la barra de herramientas (esquina superior derecha), toque o haga clic en el icono y seleccione **Configuración de vista**. La variable **Configurar columnas** se abrirá. Realice los cambios necesarios y confirme con **Actualizar**.

   ![aa-04](assets/aa-04.png)

### Selección del período de informe {#selecting-the-reporting-period}

Seleccione el período de informe para el que los datos de Analytics aparecen en la consola Sitios :

* Datos de los últimos 30 días
* Datos de los últimos 90 días
* Datos de este año

El período de informe actual aparece en la barra de herramientas de la consola Sitios (a la derecha de la barra de herramientas superior). Utilice la lista desplegable para seleccionar el período de informe requerido.\
![aa-05](assets/aa-05.png)

### Configuración de las columnas de datos disponibles {#configuring-available-data-columns}

Los miembros del grupo de usuarios administradores de análisis pueden configurar la consola Sitios para permitir que los autores vean columnas de Analytics adicionales.

>[!NOTE]
>
>Cuando un árbol de páginas contiene elementos secundarios asociados a distintas configuraciones de nube de Adobe Analytics, no se pueden configurar las columnas de datos disponibles para las páginas.

1. En la vista de lista, utilice los selectores de vista (derecha de la barra de herramientas) y seleccione **Configuración de vista** y luego A **Agregar datos de análisis personalizados**.

   ![aa-15](assets/aa-15.png)

1. Seleccione las métricas que desee exponer a los autores en la consola Sitios y, a continuación, haga clic en **Agregar**.

   Las columnas que aparecen se recuperan de Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Apertura de perspectivas de contenido desde sitios {#opening-content-insights-from-sites}

Apertura [Perspectiva de contenido](/help/sites-authoring/content-insights.md) desde la consola Sitios para investigar más a fondo la eficacia de la página.

1. En la consola Sitios , seleccione la página para la que desea ver Perspectivas de contenido.
1. En la barra de herramientas, haga clic en el icono Analytics y Recommendations .

   ![](do-not-localize/chlimage_1-16.png)

## Analytics visible desde el Editor de páginas (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Debido a los cambios de seguridad de la API de Adobe Analytics, ya no es posible utilizar la versión de Activity Map incluida en AEM.
>
>La variable [Complemento Activity Map proporcionado por Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=es) debe usarse ahora.
