---
title: Iniciar y detener del servidor de aplicaciones WebSphere
seo-title: Starting and stopping WebSphere Application Server
description: Varios procedimientos requieren que detenga o inicie la instancia de WebSphere donde desee implementar productos de formularios AEM. En este documento se describe cómo iniciar y detener el servidor de aplicaciones WebSphere.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 8%

---

# Iniciar y detener del servidor de aplicaciones WebSphere {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Varios procedimientos requieren que detenga o inicie la instancia de WebSphere donde desee implementar productos de formularios AEM. Si no está seguro de si el servidor de aplicaciones se ha iniciado, primero puede ver el estado de WebSphere Application Server.

## Ver el estado del servidor de aplicaciones WebSphere {#view-the-status-of-websphere-application-server}

1. Desde un símbolo del sistema, vaya a la *[raíz de appserver]* directorio /bin.
1. Introduzca el siguiente comando, sustituyendo *server_name* con el nombre de su servidor de aplicaciones WebSphere:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## Iniciar servidor de aplicaciones WebSphere {#start-websphere-application-server}

1. Desde un símbolo del sistema, vaya a la *[raíz de appserver]* directorio /bin.
1. Introduzca el siguiente comando, sustituyendo *server_name* con el nombre de su servidor de aplicaciones WebSphere:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## Detener el servidor de aplicaciones WebSphere {#stop-websphere-application-server}

1. Desde un símbolo del sistema, vaya a la *[raíz de appserver]* directorio /bin.
1. Introduzca el siguiente comando, sustituyendo *server_name* con el nombre de su servidor de aplicaciones WebSphere:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
