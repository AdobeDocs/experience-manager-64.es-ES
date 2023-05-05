---
title: Integración con Adobe Analytics
seo-title: Integrating with Adobe Analytics
description: Aprenda a integrar AEM con Adobe Analytics.
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 65%

---

# Integración con Adobe Analytics{#integrating-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La integración de Adobe Analytics y AEM permite rastrear la actividad de la página web:

* Una configuración de Adobe Analytics permite a AEM autenticarse con Adobe Analytics.
* Un marco de trabajo identifica los datos que se envían al grupo de informes de Adobe Analytics.

Los datos incluyen datos de página y usuario; por ejemplo:

* datos que recopilan los componentes de AEM
* clics en vínculos
* información de uso de vídeo
* número de visitas a la página desde Adobe Analytics

Las siguientes páginas le ayudan a configurar la integración:

* [Conectarse a Adobe Analytics y crear marcos](/help/sites-administering/adobeanalytics-connect.md)
* [Configuración de Seguimiento de vínculos para Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Asignación de datos de componente con propiedades de Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Configuración del seguimiento de vídeo para Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

También puede usar la variable [Asistente de inclusión](/help/sites-administering/opt-in.md) para realizar fácilmente la integración.

>[!NOTE]
>
>Consulte también el artículo explicativo: [Integración de AEM con Adobe Target y Adobe Analytics mediante DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Información adicional {#further-information}

Consulte:

* [Ampliación de la integración con Adobe Analytics](/help/sites-developing/extending-analytics.md) para obtener información acerca del desarrollo de componentes que recopilan datos de usuario y la personalización del marco de trabajo de Adobe Analytics.
* El artículo de la base de conocimiento, [Integración de Adobe Analytics: solución de problemas](https://helpx.adobe.com/es/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), para obtener información acerca de la solución de problemas de la integración de Adobe Analytics.

>[!NOTE]
>
>Si utiliza Adobe Analytics con una configuración proxy personalizada, debe [configurar dos paquetes](/help/sites-deploying/configuring-osgi.md) OSGi (por ejemplo, con la consola web) necesarios para las configuraciones proxy del cliente **HTTP de Apache**. Ambas son necesarias, ya que algunas funcionalidades de AEM utilizan las API 3.x, mientras que otras utilizan las API 4.x. Configuración de:
>
>* **Cliente HTTP 3.1 de Day Commons** para configurar la API 3.x;\
   >  por ejemplo, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Configuración proxy de componentes HTTP de Apache** para configurar la API 4.x;
>
>  por ejemplo, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
