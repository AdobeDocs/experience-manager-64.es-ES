---
title: Configuración del filtro de referente para permitir que esté vacío
seo-title: Setting Your Referrer Filter to Allow Empty
description: Siga esta página para obtener más información sobre el filtro de referente. Para permitir que el visualizador de aplicaciones de AEM Mobile vea aplicaciones en la instancia de autor, deberá establecer el filtro de referente de HTML en "permitir vacío".
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

---

# Configuración del filtro de referente para permitir que esté vacío{#setting-your-referrer-filter-to-allow-empty}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe recomienda utilizar el Editor de SPA para proyectos que requieren una representación del lado del cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

Para permitir que el visualizador de aplicaciones de AEM Mobile vea aplicaciones en la instancia de autor, deberá establecer el filtro de referente de HTML en &quot;permitir vacío&quot;.

Si no tiene intención de usar el Visor de aplicaciones para revisar aplicaciones dentro de los estados de desarrollo y ensayo, no necesita cambiar la configuración predeterminada del filtro de remitente del reenvío.

Dentro de la instancia de autor de AEM en ejecución, vaya a: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) y busque &quot;Filtro de referente de Apache Sling&quot;. Haga clic en para editar el filtro del referente y marque la casilla &quot;Permitir vacío&quot; (consulte la imagen siguiente). A continuación, pulse el botón Guardar y cierre la página del explorador.

![Configuración del filtro de referente](assets/chlimage_1-106.png)
