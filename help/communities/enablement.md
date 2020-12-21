---
title: Configuración de las funciones de habilitación
seo-title: Configuración de las funciones de habilitación
description: Configurar funciones de habilitación en Comunidades
seo-description: Configurar funciones de habilitación en Comunidades
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Configuración de las características de habilitación {#configuring-enablement-features}

## Información general {#overview}

Las funciones de habilitación permiten crear [comunidades de habilitación](overview.md#enablement-community).

* Esta función requiere licencias adicionales para su uso en un entorno de producción.

El uso de las funciones de habilitación requiere lo siguiente:

Instalación de:

* ****
SCORMSharable Content Object Reference Model (SCORM) es una colección de normas y especificaciones para el aprendizaje electrónico. SCORM también define cómo se puede empaquetar el contenido en un archivo ZIP transferible.

* ****
MySQLMySQL es una base de datos relacional que se utiliza principalmente para el seguimiento SCORM y los datos de sistema de informes para Habilitación, así como tablas para el seguimiento del progreso del video. El paquete de funciones SCORM para habilitación requiere el controlador JDBC MySQL.

* ****
FFmpegFFmpeg es una solución para convertir y transmitir audio y vídeo y, cuando se instala, se utiliza para una transcodificación adecuada de los recursos [ de ](../../help/sites-authoring/default-components-foundation.md#video)vídeo. Para las comunidades de habilitación, se utiliza en el entorno del autor para obtener metadatos de los recursos cargados y generar una miniatura para mostrarla al enumerar el recurso.

Configuración de:

* **Administradores**
de la comunidadPara las comunidades de habilitación, solo los miembros del 
`Community Enablement Managers` el grupo de usuarios puede tener asignada la función de  `*Community Site* Enablement Manager`, cuyos permisos pueden incluir la creación de contenido, las asignaciones y la administración de miembros en el entorno de publicación.

Configuración opcional de:

* **Adobe**
AnalyticsLa integración con Adobe Analytics agrega funciones de sistema de informes completas y admite la adición de Video Heartbeat a Analytics.

* **Dispatcher**

## Pasos de configuración {#configuration-steps}

A continuación se indican los pasos necesarios para habilitar a las comunidades.

Cada paso enlaza a la documentación que proporciona los detalles necesarios.

**En todas las instancias de autor/publicación:**

1. **[instalar el controlador JDBC para la consola web](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse (paquetes): Instalar  *http://localhost:4502/system/console/*
paquetesInstalar  ** antes de instalar el paquete SCORM

1. **[instalar](deploy-communities.md#scorm-package)**
paquete SCORMusar administrador de paquetes: 
*http://localhost:4502/crx/packmgr/*

**En cualquier servidor:**

1. **[instalar MySQL, MySQL Workbench](mysql.md)**

1. **[instalar](mysql.md#database-setup)**
bases de datos MySQL Ejecutar secuencias de comandos SQL descargadas de la instancia de creación
\
   Usar MySQL Workbench

**En la misma instancia de autor de alojamiento de servidor:**

1. **[instalar FFmpeg](ffmpeg.md)**

**En todas las instancias de autor/publicación:**

1. **[configurar el](mysql.md#configure-jdbc-connections)**
grupo de conexiones JDBConusar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar](mysql.md#aem-communities-scormengine-service)**
servicio de motor SCORMUsar consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar](mysql.md#adobe-granite-csrf-filter)**
filtros CSRFusar consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**En la instancia de autor:**

1. (*opcional*) **[configurar el servicio de Analytics](analytics.md)**
Utilice la consola Herramientas, Implementación y Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurar consola](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUsar flujo de trabajo/modelos

1. **[habilitar](deploy-communities.md#tunnel-service-on-author)**
servicio de túnelUsar consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[crear](users.md#creating-community-members)** administradores de comunidadPara el entorno de creación, utilice la consola de seguridad clásica-UI:  *http://localhost:4502/*
useradmincrear usuarios con path = /home/users/community

   * Añadir miembros a los siguientes grupos:

      * Administradores de habilitación de la comunidad
      * Administradores de comunidades

## Dispatcher {#dispatcher}

Cuando la implementación incluye [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), para que las características de habilitación funcionen correctamente, es necesario modificar las secciones `clientheader`y `filter`. Consulte [Configuración de Dispatcher para Comunidades](dispatcher.md#enablement).
