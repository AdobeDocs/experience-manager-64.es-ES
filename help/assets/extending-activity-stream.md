---
title: Integración de recursos con el flujo de actividad
description: Describe las capacidades de grabación de [!DNL Experience Manager] and how to configure [!DNL Experience Manager] para registrar eventos específicos.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Integración de recursos con el flujo de actividad {#integrating-assets-with-activity-stream}

Los usuarios de Adobe Experience Manager Assets realizan muchas acciones, como crear, cargar y eliminar recursos. Estas acciones se pueden registrar para que pueda proporcionar un historial de lo que ha hecho un usuario. En esta sección se describen las capacidades de registro de [!DNL Experience Manager] y cómo configurar [!DNL Experience Manager] para registrar eventos específicos.

## Consideraciones de rendimiento y comportamiento predeterminado {#performance-considerations-and-default-behavior}

Esta integración podría requerir CPU y espacio en disco, por ejemplo, al realizar importaciones masivas. Por estos motivos, la integración de [!DNL Experience Manager] Assets con el flujo de actividad está deshabilitada de forma predeterminada.

## Eventos de acción admitidos {#supported-action-events}

Se pueden configurar los siguientes eventos para que se registren:

* Licencia aceptada (ACEPTADA)
* Recurso creado (ASSET_CREATED)
* Recurso movido (ASSET_MOVED)
* Recurso quitado (ASSET_REMOVED)
* Licencia rechazada (RECHAZADA)
* Recurso descargado (DESCARGADO)
* Recurso con versión (VERSIONADO)
* Versión del recurso restaurada (RESTAURADA)
* Actualización de metadatos de recursos (METADATA_UPDATED)
* Recurso publicado en un sistema externo (PUBLISHED_EXTERNAL)
* Actualización original del recurso (ORIGINAL_UPDATED)
* Actualización de la representación de recursos (RENDITION_UPDATED)
* Representación de recursos eliminada (RENDITION_REMOVED)
* Subrecurso actualizado (SUBASSET_UPDATED)
* Subrecurso eliminado (SUBASSET_REMOVED)

## Configuración del registro de eventos [!DNL Assets] {#configuring-aem-assets-events-recording}

La [consola web](/help/sites-deploying/configuring-osgi.md) proporciona acceso al ajuste del grabador de eventos [!DNL Assets]. Para configurar el grabador de eventos [!DNL Assets], siga este procedimiento:

1. Vaya a la **[!UICONTROL consola web]**

1. Haga clic en **[!UICONTROL Configuration]**.

1. Haga doble clic **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Comprobar **[!UICONTROL Habilita este servicio]**.

1. Compruebe qué **[!UICONTROL Tipos de eventos]** desea registrar en el flujo de actividad del usuario.

1. Haga clic en **[!UICONTROL Guardar]**.

## Leer eventos grabados {#reading-recorded-events}

Los eventos registrados se almacenan como actividades. Puede leerlos mediante programación utilizando la [API de Activity Manager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
