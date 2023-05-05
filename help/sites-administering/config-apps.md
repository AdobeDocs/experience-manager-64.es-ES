---
title: Configuración para aplicaciones AEM
seo-title: Configuring for AEM Apps
description: Obtenga información sobre cómo configurar AEM aplicaciones.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 4%

---

# Configuración para aplicaciones AEM{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Apps proporciona la capacidad de actualizar el contenido de su aplicación por aire (OTA). El contenido actualizado se almacena en la instancia de publicación. Para permitir que la aplicación del dispositivo se conecte a la instancia de publicación y compruebe si hay actualizaciones, la instancia de publicación debe configurarse para permitir un encabezado de referente vacío.

## Configuración del encabezado de referente vacío {#configuring-empty-referrer-header}

Para configurar el servicio de filtro de referente:

* Abra la consola Apache Felix (**Configuraciones**) en:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Inicie sesión como administrador.
* En el **Configuraciones** seleccione: *Filtro de referente de Apache Sling*
* Marque el campo Permitir vacío para permitir encabezados de referente vacíos o que faltan.
* Haga clic en **Guardar** para guardar los cambios.

![chlimage_1-58](assets/chlimage_1-58.png)

Consulte la [Configuración de OSGI](/help/sites-deploying/osgi-configuration-settings.md) y [Lista de comprobación de seguridad: problemas con la falsificación de solicitudes entre sitios](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) para obtener más información.
