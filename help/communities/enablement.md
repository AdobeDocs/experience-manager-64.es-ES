---
title: Configuración de funciones de habilitación
seo-title: Configuración de funciones de habilitación
description: Configurar las funciones de habilitación en Communities
seo-description: Configurar las funciones de habilitación en Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Configuración de funciones de habilitación {#configuring-enablement-features}

## Información general {#overview}

Las funciones de habilitación permiten crear [comunidades de habilitación](overview.md#enablement-community).

* Esta función requiere licencias adicionales para su uso en un entorno de producción.

El uso de las funciones de habilitación requiere lo siguiente:

Instalación de:

* ****
SCORMSharable Content Object Reference Model (SCORM) es una colección de estándares y especificaciones para aprendizaje electrónico. SCORM también define cómo el contenido puede empaquetarse en un archivo ZIP transferible.

* ****
MySQLMySQL es una base de datos relacional que se utiliza principalmente para el seguimiento de SCORM y los datos de informes para la habilitación, así como tablas para el seguimiento del progreso del vídeo. El SCORM para el paquete de características de habilitación requiere el controlador JDBC de MySQL.

* ****
FFmpegFFmpeg es una solución para convertir y transmitir audio y vídeo y, cuando se instala, se utiliza para la transcodificación adecuada de los recursos de  [vídeo](../../help/sites-authoring/default-components-foundation.md#video). Para las comunidades de habilitación, se utiliza en el entorno de creación para obtener metadatos de los recursos cargados, así como para generar una miniatura que se mostrará al enumerar el recurso.

Configuración de:

* **Gestores**
de la comunidadPara comunidades de habilitación, solo miembros del 
`Community Enablement Managers` se puede asignar la función de  `*Community Site* Enablement Manager` al grupo de usuarios, cuyos permisos pueden incluir la creación de contenido, asignaciones y administración de miembros en el entorno de publicación.

Configuración opcional de:

* **Adobe**
AnalyticsIntegration with Adobe Analytics añade funciones de informes completas y admite la adición de Video Heartbeat a Analytics.

* **Dispatcher**

## Pasos de configuración {#configuration-steps}

A continuación se indican los pasos necesarios para habilitar a las comunidades.

Cada paso vincula a la documentación que proporciona los detalles necesarios.

**En todas las instancias de autor/publicación:**

1. **[instale el controlador JDBC para la consola web](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse (paquetes): Instale  *http://localhost:4502/system/console/*
paquetesInstale  ** antes de instalar el paquete SCORM

1. **[instalar el](deploy-communities.md#scorm-package)**
paquete SCORMutilizar el administrador de paquetes: 
*http://localhost:4502/crx/packmgr/*

**En cualquier servidor:**

1. **[instalar MySQL, MySQL Workbench](mysql.md)**

1. **[instalar](mysql.md#database-setup)**
bases de datos MySQLEjecutar secuencias de comandos SQL descargadas de la instancia de autor
\
   Usar MySQL Workbench

**En la misma instancia de autor de alojamiento de servidor:**

1. **[instalar FFmpeg](ffmpeg.md)**

**En todas las instancias de autor/publicación:**

1. **[configurar el](mysql.md#configure-jdbc-connections)**
pool de conexiones JDBCusar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar el](mysql.md#aem-communities-scormengine-service)**
servicio del motor SCORMusar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar](mysql.md#adobe-granite-csrf-filter)**
filtros CSRFusar consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**En la instancia de autor:**

1. (*opcional*) **[configurar el servicio de Analytics](analytics.md)**
Utilice Herramientas, Implementación, consola Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurar la consola](ffmpeg.md#configure-ffmpeg-transcoding-service)**
Flujo de trabajo/Modelos FFmpegUse

1. **[habilitar el](deploy-communities.md#tunnel-service-on-author)**
servicio de túnelUtilizar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[crear](users.md#creating-community-members)** administradores de la comunidadPara el entorno de creación, utilice la consola de seguridad de la IU clásica:  *http://localhost:4502/*
useradmincreate user(s) with path = /home/users/community

   * Agregue miembros a los siguientes grupos:

      * Administradores de habilitación de la comunidad
      * Administradores de comunidades

## Dispatcher {#dispatcher}

Cuando la implementación incluye [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), para que las funciones de habilitación funcionen correctamente, es necesario modificar las secciones `clientheader`y `filter`. Consulte [Configuración de Dispatcher para Communities](dispatcher.md#enablement).
