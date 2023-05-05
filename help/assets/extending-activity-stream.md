---
title: Integración de recursos con el flujo de actividad
description: Describe las capacidades de grabación de [!DNL Experience Manager] y cómo configurar [!DNL Experience Manager] para registrar eventos específicos.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

---

# Integración de recursos con el flujo de actividad {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los usuarios de Adobe Experience Manager Assets realizan muchas acciones, como crear, cargar y eliminar recursos. Estas acciones se pueden registrar para que pueda proporcionar un historial de lo que ha hecho un usuario. En esta sección se describen las capacidades de grabación de [!DNL Experience Manager] y cómo configurar [!DNL Experience Manager] para registrar eventos específicos.

## Consideraciones de rendimiento y comportamiento predeterminado {#performance-considerations-and-default-behavior}

Esta integración podría requerir CPU y espacio en disco, por ejemplo, al realizar importaciones masivas. Por estas razones, la variable [!DNL Experience Manager] La integración de recursos con el flujo de actividad está desactivada de forma predeterminada.

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

## Configuración [!DNL Assets] Grabación de eventos {#configuring-aem-assets-events-recording}

La variable [Consola web](/help/sites-deploying/configuring-osgi.md) proporciona acceso al [!DNL Assets] Ajuste del grabador de eventos. Para configurar la variable [!DNL Assets] Grabador de eventos, siga este procedimiento:

1. Vaya a la **[!UICONTROL Consola web]**

1. Haga clic en **[!UICONTROL Configuración]**.

1. Haga doble clic **[!UICONTROL Grabador de eventos de CQ DAM de día]**.

1. Marque **[!UICONTROL Habilita este servicio]**.

1. Comprobar qué **[!UICONTROL Tipos de eventos]** desea que se registre en el flujo de actividad del usuario.

1. Haga clic en **[!UICONTROL Guardar]**.

## Leer eventos grabados {#reading-recorded-events}

Los eventos registrados se almacenan como actividades. Puede leerlos mediante programación utilizando la variable [API de ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
