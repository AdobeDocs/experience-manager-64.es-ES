---
title: Configuración de funciones de habilitación
seo-title: Configuring Enablement Features
description: Configurar las funciones de habilitación en Communities
seo-description: Configure enablement features in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 7%

---

# Configuración de funciones de habilitación {#configuring-enablement-features}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Las funciones de habilitación permiten crear [comunidades de habilitación](overview.md#enablement-community).

* Esta función requiere licencias adicionales para su uso en un entorno de producción.

El uso de las funciones de habilitación requiere lo siguiente:

Instalación de:

* **SCORM**
El Modelo de referencia de objetos de contenido compartible (SCORM) es una colección de estándares y especificaciones para el aprendizaje electrónico. SCORM también define cómo el contenido puede empaquetarse en un archivo ZIP transferible.

* **MySQL**
MySQL es una base de datos relacional que se utiliza principalmente para el seguimiento de SCORM y los datos de informes para la habilitación, así como tablas para el seguimiento del progreso del vídeo. El SCORM para el paquete de características de habilitación requiere el controlador JDBC de MySQL.

* **FFmpeg**
FFmpeg es una solución para convertir y transmitir audio y vídeo y, cuando se instala, se utiliza para una transcodificación adecuada de [Recursos de vídeo](../../help/sites-authoring/default-components-foundation.md#video). Para las comunidades de habilitación, se utiliza en el entorno de creación para obtener metadatos de los recursos cargados, así como para generar una miniatura que se mostrará al enumerar el recurso.

Configuración de:

* **Administradores de la comunidad**
Para las comunidades de habilitación, solo los miembros del 
`Community Enablement Managers` se puede asignar la función de `*Community Site* Enablement Manager`, cuyos permisos pueden incluir creación de contenido, asignaciones y administración de miembros en el entorno de publicación.

Configuración opcional de:

* **Adobe Analytics**
La integración con Adobe Analytics agrega funciones de informes completas y admite la adición de Video Heartbeat a Analytics.

* **Dispatcher**

## Pasos de configuración {#configuration-steps}

A continuación se indican los pasos necesarios para habilitar a las comunidades.

Cada paso vincula a la documentación que proporciona los detalles necesarios.

**En todas las instancias de autor/publicación:**

1. **[instalar el controlador JDBC para MySQL](deploy-communities.md#jdbc-driver-for-mysql)**
Utilizar la consola web (paquetes): Instalar *http://localhost:4502/system/console/bundles*
Instalar *before* instalación del paquete SCORM

1. **[instalar paquete SCORM](deploy-communities.md#scorm-package)**
Utilice el Administrador de paquetes: 
*http://localhost:4502/crx/packmgr/*

**En cualquier servidor:**

1. **[instalar MySQL, MySQL Workbench](mysql.md)**

1. **[instalar bases de datos MySQL](mysql.md#database-setup)**
Ejecución de scripts SQL descargados de la instancia de autor
\
   Usar MySQL Workbench

**En la misma instancia de autor de alojamiento de servidor:**

1. **[instalar FFmpeg](ffmpeg.md)**

**En todas las instancias de autor/publicación:**

1. **[configurar el grupo de conexiones JDBC](mysql.md#configure-jdbc-connections)**
Usar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar el servicio de motor SCORM](mysql.md#aem-communities-scormengine-service)**
Usar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar filtros CSRF](mysql.md#adobe-granite-csrf-filter)**
Usar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**En la instancia de autor:**

1. (*opcional*) **[configurar el servicio de Analytics](analytics.md)**
Utilice Herramientas, Implementación, consola Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurar FFmpeg](ffmpeg.md#configure-ffmpeg-transcoding-service)**
Uso de la consola Flujo de trabajo/Modelos

1. **[habilitar servicio de túnel](deploy-communities.md#tunnel-service-on-author)**
Usar la consola web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[crear administradores de la comunidad](users.md#creating-community-members)** Para el entorno de creación, utilice la consola de seguridad clásica-UI: *http://localhost:4502/useradmin*
crear usuarios con path = /home/users/community

   * Agregue miembros a los siguientes grupos:

      * Administradores de habilitación de la comunidad
      * Administradores de comunidades

## Dispatcher {#dispatcher}

Cuando la implementación incluye [AEM Dispatcher](https://helpx.adobe.com/es/experience-manager/dispatcher/using/dispatcher.html), para que las funciones de habilitación funcionen correctamente, la variable `clientheader`y `filter`es necesario modificar las secciones. Consulte [Configuración de Dispatcher para Communities](dispatcher.md#enablement).
