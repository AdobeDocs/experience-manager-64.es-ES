---
title: Introducción a la creación de informes de procesos
seo-title: Introduction to Process Reporting
description: Introducción y funciones clave de AEM Forms en la creación de informes de procesos JEE
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
exl-id: 279b2f89-5b91-4b8f-ab0f-8ade9b9f3932
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Introducción a la creación de informes de procesos {#introduction-to-process-reporting}

![informes de procesos](assets/process-reporting.png)

Process Reporting es una herramienta basada en explorador que se utiliza para crear y ver informes sobre procesos y tareas de AEM Forms.

Process Reporting proporciona un conjunto de informes integrados que le permiten filtrar y ver información sobre procesos de larga duración, duración del proceso y volumen del flujo de trabajo.

Además, los informes de procesos proporcionan una interfaz para ejecutar consultas ad hoc e integrar vistas de informes personalizadas en la interfaz de usuario de Process Reporting.

Para obtener la lista de exploradores admitidos, consulte [Plataformas compatibles con AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

Process Reporting se basa en módulos que:

* Leer datos de proceso de la base de datos de AEM Forms
* Publicar datos de proceso en un repositorio incrustado de Process Reporting
* Proporciona una interfaz de usuario basada en navegador para ver informes

## Funcionalidades Clave {#key-capabilities}

### Informes siempre activos {#always-on-reporting}

![administración del sitio](assets/site-management.png)

Vea la lista de procesos de larga duración, procese gráficos de duración y ejecute consultas personalizadas con filtros.

Process Reporting también proporciona la opción de exportar los datos de informes y consultas en formato CSV.

### Informes específicos {#adhoc-reports}

![print-&amp;-color](assets/print-&-colour.png)

Utilice filtros para obtener una vista específica de los datos.

Puede buscar procesos o tareas por ID, duración, fechas de inicio y finalización, iniciador de procesos, etc.

Puede combinar varios filtros para crear informes específicos.

A continuación, puede guardar los filtros de informe para que se ejecuten en una fecha u hora posteriores.

### Historial de procesos/tareas {#process-task-history}

![administración de archivos](assets/file-management.png)

Los servidores de AEM Forms ejecutan numerosos procesos en paralelo. Estos procesos siguen en transición de un estado a otro. Al publicar datos de Forms en el repositorio de Process Reporting a intervalos regulares, Process Reporting conserva la información de transición sobre los procesos que se ejecutan en AEM Forms.

### Control de acceso {#access-control-br}

![sin título](assets/untitled.png)

Los informes de procesos proporcionan acceso basado en permisos a la interfaz de usuario.

Esto significa que solo los usuarios con permisos de informes tienen acceso a la interfaz de usuario de Process Reporting.
