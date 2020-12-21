---
title: Introducción al Sistema de informes de procesos
seo-title: Introducción al Sistema de informes de procesos
description: Introducción y funciones clave de AEM Forms en el Sistema de informes de procesos JEE
seo-description: Introducción y funciones clave de AEM Forms en el Sistema de informes de procesos JEE
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Introducción al Sistema de informes de procesos {#introduction-to-process-reporting}

![proceso-sistema de informes](assets/process-reporting.png)

Process Sistema de informes es una herramienta basada en explorador que se utiliza para crear y vista de informes en procesos y tareas de AEM Forms.

El Sistema de informes de procesos proporciona un conjunto de informes listos para usar que le permiten filtrar, vista de información sobre procesos de larga duración, duración del proceso y volumen del flujo de trabajo.

Además, Process Sistema de informes proporciona una interfaz para ejecutar consultas ad hoc e integrar vistas de informes personalizadas en la interfaz de usuario de Process Sistema de informes.

Para obtener la lista de los exploradores admitidos, consulte [Plataformas admitidas por AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

El Sistema de informes de procesos se basa en módulos que:

* Leer datos de proceso de la base de datos de AEM Forms
* Publicación de datos de proceso en un repositorio de Process Sistema de informes incrustado
* Proporciona una interfaz de usuario basada en explorador para los informes de vista

## Capacidades clave {#key-capabilities}

### Sistema de informes siempre activado {#always-on-reporting}

![administración del sitio](assets/site-management.png)

Vista la lista de procesos de larga ejecución, procese gráficos de duración y ejecute consultas personalizadas con filtros.

El Sistema de informes de procesos también ofrece la opción de exportar los datos de informes y consultas en formato CSV.

### Informes específicos {#adhoc-reports}

![print-&amp;-color](assets/print-&-colour.png)

Use filtros para obtener una vista específica de sus datos.

Puede buscar procesos o tareas por ID, duración, fechas de inicio y finalización, iniciador de procesos, etc.

Puede combinar varios filtros para crear informes específicos.

Luego puede guardar los filtros del informe para que se ejecuten en una fecha u hora posterior.

### Historial de procesos/Tareas {#process-task-history}

![administración de archivos](assets/file-management.png)

Los servidores de AEM Forms ejecutan numerosos procesos en paralelo. Estos procesos continúan en la transición de un estado a otro. Al publicar datos de Forms en el repositorio de Process Sistema de informes a intervalos regulares, Process Sistema de informes conserva la información de transición sobre los procesos que se ejecutan en AEM Forms.

### Control de acceso {#access-control-br}

![sin título](assets/untitled.png)

Los informes de procesos proporcionan acceso basado en permisos a la interfaz de usuario.

Esto significa que solo los usuarios con permisos de sistema de informes tienen acceso a la interfaz de usuario de Process Sistema de informes.


