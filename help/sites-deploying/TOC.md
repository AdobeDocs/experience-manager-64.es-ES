---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guía de implementación de AEM 6.4
breadcrumb-title: Guía de implementación
user-guide-description: Obtenga más información sobre la instalación, la implementación y la arquitectura de Adobe Experience Manager 6.4, incluida nuestra implementación en la nube de Adobe Managed Services.
feature: Deploying
role: Architect
source-git-commit: 35aea0e087334a1c1e6a708f2182bd9dee799dc0
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 22%

---


# Guía del usuario de implementación de AEM 6.4 {#deploying}

+ [Guía del usuario de implementación](home.md)
+ Introducción a la plataforma AEM {#introduction}
   + [Introducción a la plataforma AEM](platform.md)
   + [Requisitos técnicos](technical-requirements.md)
   + [Elementos de almacenamiento en AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM con MongoDB](aem-with-mongodb.md)
+ Implementación de AEM {#deploying}
   + [Implementación y mantenimiento](deploy.md)
   + [Implementaciones recomendadas](recommended-deploys.md)
   + [Instalación del servidor de aplicaciones](application-server-install.md)
   + [Instalación independiente personalizada](custom-standalone-install.md)
   + [Línea de comandos: start y stop](command-line-start-and-stop.md)
   + [Configuración de almacenes de nodos y almacenes de datos en AEM 6](data-store-config.md)
   + [Limpieza de revisión](revision-cleanup.md)
   + [Ejecución de AEM con el modo de espera pasiva TarMK](tarmk-cold-standby.md)
   + [Compatibilidad con RDBMS en AEM 6.4](rdbms-support-in-aem.md)
   + [Consultas e indexación de Oak](queries-and-indexing.md)
   + [Indexación a través de Oak-run Jar](indexing-via-the-oak-run-jar.md)
   + [Casos de uso de indexación de Oak-run.jar](oak-run-indexing-usecases.md)
   + [Resolución de problemas de índices Oak](troubleshooting-oak-indexes.md)
   + [Inclusión En La Recopilación De Estadísticas De Uso Agregado](opt-in-aggregated-usage-statistics.md)
   + [Solución de problemas](troubleshooting.md)
+ Configurar AEM {#configuring}
   + [Conceptos básicos de configuración](configuring.md)
   + [Registro](configure-logging.md)
   + [Configuración de OSGi](configuring-osgi.md)
   + [Ajustes de configuración de OSGi](osgi-configuration-settings.md)
   + [Ejecutar modos](configure-runmodes.md)
   + [Consola web](web-console.md)
   + [Replicación](replication.md)
   + [Replicar usando SSL mutuo](mssl-replication.md)
   + [Solución de problemas de replicación](troubleshoot-rep.md)
   + [Caducidad de objetos estáticos](expiration-static-objects.md)
   + [Depuración de versiones](version-purging.md)
   + [Supervisión y mantenimiento de la instancia de AEM](monitoring-and-maintaining.md)
   + [Descarga de trabajos](offloading.md)
   + [Inicio de sesión único](single-sign-on.md)
   + [Asignación de recursos](resource-mapping.md)
   + [Habilitación de HTTP en SSL](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/ssl-by-default.html)
   + [Comprobaciones de coherencia y travesía](consistency-check.md)
   + [Directrices de rendimiento](performance-guidelines.md)
   + [Optimización del rendimiento](configuring-performance.md)
   + [Guía de rendimiento de recursos](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html)
   + [Artículos de procedimientos de configuración](ht-deploy.md)
   + [Eliminación de sitios de Geometrixx](removing-the-geometrixx-sites.md)
   + [Configuración de la consola web](configuring-web-console.md)
+ Actualización a AEM 6.4 {#upgrading}
   + [Actualización a AEM 6.4](upgrade.md)
   + [Planificación de la actualización](upgrade-planning.md)
   + [Evaluación de la complejidad de la actualización con Pattern Detector](pattern-detector.md)
   + [Compatibilidad con versiones anteriores en AEM 6.4](backward-compatibility.md)
   + [Procedimiento de actualización](upgrade-procedure.md)
   + [Uso de la reindexación sin conexión para reducir el tiempo de inactividad durante una actualización](upgrade-offline-reindexing.md)
   + [Realización de una actualización in situ](in-place-upgrade.md)
   + [Migración de contenido diferido](lazy-content-migration.md)
   + [Uso de la herramienta de migración CRX2Oak](using-crx2oak.md)
   + [Tareas de mantenimiento previas a la actualización](pre-upgrade-maintenance-tasks.md)
   + [Comprobación y solución de problemas posteriores a la actualización](post-upgrade-checks-and-troubleshooting.md)
   + [Actualización de Forms de búsqueda personalizada](upgrading-custom-search-forms.md)
   + [Actualizaciones sostenibles](sustainable-upgrades.md)
   + [Actualización de código y personalizaciones](upgrading-code-and-customizations.md)
   + [Pasos de actualización para las instalaciones del servidor de aplicaciones](app-server-upgrade.md)
   + [Lista de paquetes obsoletos desinstalados después de la actualización](obsolete-bundles.md)
+ Reestructuración de repositorios {#restructuring}
   + [Reestructuración de repositorios en AEM 6.4](repository-restructuring.md)
   + [Reestructuración común de repositorios en AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de sitios en AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de activos en AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=es)
   + [Reestructuración del repositorio de Dynamic Media en AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de Forms en AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración de repositorios de comercio electrónico en AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración de repositorios para AEM Communities en la versión 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ eCommerce {#ecommerce}
   + [Información general sobre comercio electrónico](ecommerce.md)
   + [Commerce Cloud SAP](sap-commerce-cloud.md)
   + [Commerce Cloud de Salesforce](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Prácticas recomendadas   {#practices}
   + [Prácticas Recomendadas De Implementación](best-practices.md)
   + [Árbol de rendimiento](performance-tree.md)
   + [Prácticas recomendadas para pruebas de rendimiento](best-practices-for-performance-testing.md)
   + [Prácticas recomendadas para consultas e indexación](best-practices-for-queries-and-indexing.md)
   + [Interfaz de usuario de Recommendations para clientes](ui-recommendations.md)
   + [Rendimiento y escalabilidad](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->
