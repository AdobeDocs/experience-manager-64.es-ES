---
cloud: experience-cloud
product: adobe experience manager
audience: end-user
user-guide-title: Guía de implementación de AEM 6.4
user-guide-description: Learn more about installing, deploying, and the architecture of Adobe Experience Manager 6.4, including our Adobe Managed Services cloud deployment.
translation-type: tm+mt
source-git-commit: 27db148008709e28bab42f25e79f530fe37affb4
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 11%

---


# Guía del usuario de implementación de AEM 6.4 {#deploying}

+ [Guía del usuario de implementación](home.md)
+ Introducción a la Plataforma AEM {#introduction}
   + [Introducción a la Plataforma AEM](platform.md)
   + [Requisitos técnicos](technical-requirements.md)
   + [Elementos de Almacenamiento en AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM con MongoDB](aem-with-mongodb.md)
+ Implementación de AEM {#deploying}
   + [Implementación y mantenimiento](deploy.md)
   + [Implementaciones recomendadas](recommended-deploys.md)
   + [Instalación del servidor de aplicaciones](application-server-install.md)
   + [Instalación independiente personalizada](custom-standalone-install.md)
   + [Línea de comandos: start y stop](command-line-start-and-stop.md)
   + [Configuración de almacenes de nodos y almacenes de datos en AEM 6](data-store-config.md)
   + [Limpieza de revisión](revision-cleanup.md)
   + [Cómo ejecutar AEM con TarMK Cold Standby](tarmk-cold-standby.md)
   + [Compatibilidad con RDBMS en AEM 6.4](rdbms-support-in-aem.md)
   + [Consultas de roble e indexación](queries-and-indexing.md)
   + [Indexación a través del Jar de Oak-run](indexing-via-the-oak-run-jar.md)
   + [Casos de uso de indización de Oak-run.jar](oak-run-indexing-usecases.md)
   + [Resolución de problemas con los índices Oak](troubleshooting-oak-indexes.md)
   + [Opción En La Recopilación De Estadísticas De Uso Agregado](opt-in-aggregated-usage-statistics.md)
   + [Actualizar definiciones del vehículo de lanzamiento](update-release-vehicle-definitions.md)
   + [Solución de problemas](troubleshooting.md)
+ Configuración de AEM {#configuring}
   + [Conceptos básicos de configuración](configuring.md)
   + [Registro](configure-logging.md)
   + [Configuración de OSGi](configuring-osgi.md)
   + [Configuración de OSGi](osgi-configuration-settings.md)
   + [Ejecutar modos](configure-runmodes.md)
   + [Consola web](web-console.md)
   + [Replicación](replication.md)
   + [Replicar usando SSL mutuo](mssl-replication.md)
   + [Resolución de problemas de replicación](troubleshoot-rep.md)
   + [Caducidad de objetos estáticos](expiration-static-objects.md)
   + [Depuración de versiones](version-purging.md)
   + [Monitoreo y mantenimiento de la instancia de AEM](monitoring-and-maintaining.md)
   + [Descarga de trabajos](offloading.md)
   + [Inicio de sesión único](single-sign-on.md)
   + [Asignación de recursos](resource-mapping.md)
   + [Habilitación de HTTP sobre SSL](/help/sites-administering/ssl-by-default.md)
   + [Comprobaciones de coherencia y de recorrido](consistency-check.md)
   + [Directrices de rendimiento](performance-guidelines.md)
   + [Optimización del rendimiento](configuring-performance.md)
   + [Guía de rendimiento de recursos](assets-performance-sizing.md)
   + [Artículos de procedimientos de configuración](ht-deploy.md)
   + [Eliminación de sitios de Geometrixx](removing-the-geometrixx-sites.md)
   + [Configuración de la consola web](configuring-web-console.md)
+ Actualización a AEM 6.4 {#upgrading}
   + [Actualización a AEM 6.4](upgrade.md)
   + [Planificación de la actualización](upgrade-planning.md)
   + [Evaluación de la complejidad de la actualización con el detector de patrones](pattern-detector.md)
   + [Compatibilidad con versiones anteriores en AEM 6.4](backward-compatibility.md)
   + [Procedimiento de actualización](upgrade-procedure.md)
   + [Realización de una actualización in situ](in-place-upgrade.md)
   + [Migración de contenido diferido](lazy-content-migration.md)
   + [Uso de la herramienta de migración CRX2Oak](using-crx2oak.md)
   + [Tareas de mantenimiento previas a la actualización](pre-upgrade-maintenance-tasks.md)
   + [Comprobaciones posteriores a la actualización y resolución de problemas](post-upgrade-checks-and-troubleshooting.md)
   + [Actualización de Forms de búsqueda personalizada](upgrading-custom-search-forms.md)
   + [Upgrades sostenibles](sustainable-upgrades.md)
   + [Actualización del código y las personalizaciones](upgrading-code-and-customizations.md)
   + [Pasos de actualización para las instalaciones de Application Server](app-server-upgrade.md)
   + [Lista de paquetes obsoletos desinstalados tras la actualización](obsolete-bundles.md)
+ Reestructuración del repositorio {#restructuring}
   + [Reestructuración del repositorio en AEM 6.4](repository-restructuring.md)
   + [Reestructuración común de repositorios en AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de sitios en AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de activos en AEM 6.4](assets-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de Dynamic Media en AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de Forms en AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio de comercio electrónico en AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Reestructuración del repositorio para AEM Communities en 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ eCommerce {#ecommerce}
   + [Información general sobre comercio electrónico](ecommerce.md)
   + [Commerce Cloud SAP](sap-commerce-cloud.md)
   + [Commerce Cloud de Salesforce](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Prácticas recomendadas   {#practices}
   + [Implementación de optimizaciones](best-practices.md)
   + [Árbol de rendimiento](performance-tree.md)
   + [Prácticas recomendadas para pruebas de rendimiento](best-practices-for-performance-testing.md)
   + [Prácticas recomendadas para Consultas e indexación](best-practices-for-queries-and-indexing.md)
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
