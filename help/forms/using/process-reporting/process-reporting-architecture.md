---
title: Funcionamiento de los informes de procesos
seo-title: How Process Reporting Works
description: Descripción de los servicios que conforman AEM Forms en JEE Process Reporting e introducción a la interfaz de usuario de Process Reporting.
seo-description: Description of the services that make up the AEM Forms on JEE Process Reporting and an introduction to the Process Reporting UI
uuid: 00a2dd6d-8a6f-4c7b-b03e-81cfd4bcf50d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: 4afc68fc-6b39-4c31-95fa-2ef3111c57da
exl-id: 05ef8b08-bb1d-441d-8b02-5f047efbabcb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 92%

---

# Funcionamiento de los informes de procesos {#how-process-reporting-works}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Process Reporting es el módulo de informes de AEM Forms en JEE.

Process Reporting permite ejecutar informes sobre procesos y tareas de AEM Forms.

Process Reporting utiliza el repositorio incrustado del módulo para publicar datos de Forms. A continuación, utiliza esos datos para ejecutar informes.

Process Reporting consta de los siguientes módulos:

* [Servicio ProcessDataPublisher](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [Servicio ProcessDataStorage](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [Servicio OSGi](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Servlet Query Data](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Interfaz de usuario de Process Reporting](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Arquitectura de Process Reporting {#process-reporting-architecture-br}

![plataforma_process_reporting](assets/processreportingarchitecture.png)

## Módulos de Process Reporting {#process-reporting-modules}

### Servicio ProcessDataPublisher {#processdatapublisher-service-br}

El servidor ProcessDataPublisher se ejecuta periódicamente en la base de datos de AEM Forms y extrae los datos que han cambiado desde la última ejecución del servicio. A continuación, publica los datos en el servicio Process Data Storage.

Para obtener más información sobre la configuración del servicio, consulte [Configuración del servicio ProcessDataPublisher](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### Servicio ProcessDataStorageProvider {#processdatastorageprovider-service-br}

El servicio ProcessDataStorageProvider recibe datos de proceso del servicio ProcessDataPublisher y los guarda en el repositorio de Process Reporting.

Para obtener más información sobre la configuración del servicio, consulte [Configuración del servicio ProcessDataStorageProvider](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### Servicio OSGi {#osgi-service-br}

QueryDataServlet utiliza este servicio para obtener los datos de informe del repositorio de Process Reporting.

### Servicio QueryDataServlet {#querydataservlet-service-br}

El servicio QueryDataServlet acepta consultas de la interfaz de usuario de Process Reporting.

A continuación, utiliza los servicios OSGi para obtener los datos de informe relevantes, procesa los datos y los devuelve a la interfaz de usuario.

### Interfaz de usuario de Process Reporting {#process-reporting-user-interface-br}

La interfaz de usuario de Process Reporting es una interfaz basada en explorador web. Esta interfaz se utiliza para ver la información de procesos y tareas publicada en la base de datos de AEM Forms.

### Servicio QueryDataServlet {#querydataservlet-service-br-1}

El servicio QueryDataServlet acepta consultas de la interfaz de usuario de Process Reporting.

A continuación, utiliza los servicios OSGi para obtener los datos de informe relevantes, procesa los datos y los devuelve a la interfaz de usuario.

### Informes personalizados {#custom-reports-br}

Puede crear sus propios informes personalizados y mostrarlos en la pestaña Informes personalizados de la interfaz de usuario de Process Reporting.

Para ver los pasos para crear un informe personalizado, consulte Creación de un informe personalizado en el artículo [Informes personalizados en Process Reporting](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
