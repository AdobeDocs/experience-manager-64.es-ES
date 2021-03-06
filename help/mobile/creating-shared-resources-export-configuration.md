---
title: Creación de la configuración de exportación de recursos compartidos
seo-title: Creación de la configuración de exportación de recursos compartidos
description: Siga esta página para obtener información sobre la exportación de recursos compartidos desde Adobe Experience Manager (AEM) para cargarlos en AEM Mobile.
seo-description: Siga esta página para obtener información sobre la exportación de recursos compartidos desde Adobe Experience Manager (AEM) para cargarlos en AEM Mobile.
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
translation-type: tm+mt
source-git-commit: 95499f59b2ce7d5d864d948d596f3efaae0b0d27
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Creación de la configuración de exportación de recursos compartidos{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>Adobe recomienda el uso del Editor de SPA para proyectos que requieren una representación de cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Requisitos previos**:
>
>Antes de aprender a crear y modificar recursos compartidos, consulte [Sincronización de contenido](/help/mobile/mobile-ondemand-contentsync.md) para comprender los conceptos básicos.

Los usuarios de AEM Mobile utilizan la sincronización de contenido para exportar contenido en directo a contenido estático y utilizarlo en aplicaciones móviles. Esta exportación se produce cuando el contenido se carga en Mobile On-Demand Services desde AEM Mobile.

La propiedad ***dps-exportTemplate*** mencionada en la tabla anterior define la ruta a las configuraciones de exportación de la aplicación. Establezca esta propiedad para crear y modificar recursos compartidos.

Los siguientes recursos describen la exportación de recursos compartidos desde Adobe Experience Manager (AEM) para cargarlos en AEM Mobile.

Recursos HTML compartidos permite que los artículos compartan recursos HTML que, de lo contrario, deberían duplicarse para todos los artículos y pueden incluir iconos, fuentes, javascript y css.

La configuración de la sincronización de contenido que se encuentra en **&lt;dps-exportTemplate>/dps-HTMLResources>** debe configurarse para exportar todo el contenido que un artículo requiere para la representación estática de propiedades en el dispositivo.

>[!CAUTION]
>
>Puede realizar los pasos siguientes para vista de recursos compartidos de muestra, solo si tiene:
>
>* se instaló el contenido de muestra
>* ejecución de AEM instancia
>* no hay contexto personalizado configurado o un puerto diferente

>



Para vista de recursos compartidos de muestra, consulte los pasos siguientes:

1. Abra el CRXDE Lite en el servidor AEM.
1. Vaya a esta ruta *[/etc/contentsync/templates/dps-we-ilimitado-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)* para vista de los recursos compartidos de muestra.

   Puede realizar la vista de todas las propiedades necesarias para crear los recursos compartidos, como se muestra en la figura siguiente:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>Los recursos compartidos deben cargarse o exportarse a AEM Mobile On-demand Services cuando cambie alguno de los recursos compartidos.

