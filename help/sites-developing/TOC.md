---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guía del usuario sobre desarrollo en AEM 6.4
breadcrumb-title: Guía de desarrollo
user-guide-description: Esta guía explica cómo crear una instancia de AEM.
feature: Developing
role: Developer
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 26%

---


# Guía del usuario sobre desarrollo en AEM 6.4 {#developing}

+ [Información general sobre el desarrollo de la guía del usuario](home.md)
+ Introducción para desarrolladores{#introduction}
   + [Introducción al desarrollo de AEM Sites: Tutorial de WKND](getting-started.md)
   + [AEM Conceptos principales](the-basics.md)
   + [Estructura de la interfaz de usuario táctil AEM](touch-ui-structure.md)
   + [Conceptos de la IU táctil AEM](touch-ui-concepts.md)
   + [Desarrollo de AEM: directrices y prácticas recomendadas](dev-guidelines-bestpractices.md)
   + [Uso de bibliotecas del lado del cliente](clientlibs.md)
   + [Desarrollo y diferencia de página](pagediff.md)
   + [Limitaciones del editor](editor-limitations.md)
   + [Marco de protección del CSRF](csrf-protection.md)
   + [Modelado de datos - Modelo de David Nuescheler](model-data.md)
   + [Contribución a AEM](contributing-to-cq.md)
   + [Seguridad](security.md)
   + [Materiales de referencia](reference-materials.md)
   + [Creación de un sitio web con todas las funciones (IU clásica)](website.md)
   + [Diseños y Designer (IU clásica)](designer.md)
+ Plataforma{#platform}
   + [Hoja de referencia de Sling](sling-cheatsheet.md)
   + [Uso de los adaptadores de Sling](sling-adapters.md)
   + [Bibliotecas de etiquetas](taglib.md)
   + Plantillas{#templates}
      + [Plantillas](templates.md)
      + [Plantillas de página: editables ](page-templates-editable.md)
      + [Plantillas de página: estáticas](page-templates-static.md)
      + [Plantillas de fragmento de contenido](content-fragment-templates.md)
      + [Representación de plantilla adaptable](templates-adaptive-rendering.md)
   + [Uso de la fusión de recursos de Sling en AEM](sling-resource-merger.md)
   + [Superposiciones](overlays.md)
   + [Convenciones de nomenclatura](naming-conventions.md)
   + [Creación de un nuevo componente de campo de interfaz de usuario de Granite](granite-ui-component.md)
   + Query Builder{#query-builder}
      + [Implementación de un evaluador de predicados personalizado para el generador de consultas](implementing-custom-predicate-evaluator.md)
      + [Referencia de predicados del generador de consultas](querybuilder-predicate-reference.md)
      + [API del Generador de consultas](querybuilder-api.md)
   + Etiquetado{#tagging}
      + [Etiquetado](tags.md)
      + [Marco de trabajo de etiquetado de AEM](framework.md)
      + [Creación del etiquetado en una aplicación AEM](building.md)
   + [Personalización de páginas que muestra el Controlador de errores](customizing-errorhandler-pages.md)
   + [Tipos de nodos personalizados](custom-nodetypes.md)
   + [Adición de fuentes para la renderización gráfica](adding-fonts.md)
   + [Conexión a bases de datos SQL](jdbc.md)
   + [Externalización de direcciones URL](externalizer.md)
   + [Creación y consumo de trabajos para descarga](dev-offloading.md)
   + [Configuración del uso de cookies](cookie-optout.md)
   + [Cómo acceder mediante programación al JCR de AEM](access-jcr.md)
   + [Integración de servicios con la consola JMX](jmx-integration.md)
   + [Desarrollo del Editor por lotes](dev-bulk-editor.md)
   + [Desarrollo de informes](dev-reports.md)
   + eCommerce{#ecommerce}
      + [eCommerce](ecommerce.md)
      + [Desarrollo (genérico)](generic.md)
      + [Desarrollo con Commerce Cloud SAP](sap-commerce-cloud.md)
+ Componentes{#components}
   + [Componentes principales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=es)
   + [Sistema de estilos](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html)
   + [Información general sobre componentes](components.md)
   + [Componentes AEM: conceptos básicos](components-basics.md)
   + [Desarrollo de componentes AEM](developing-components.md)
   + [Desarrollo de componentes de AEM: ejemplos de código](developing-components-samples.md)
   + [Exportador JSON para servicios de contenido](json-exporter.md)
   + [Activación de la exportación de JSON para un componente](json-exporter-components.md)
   + [Editor de imágenes](image-editor.md)
   + [Etiqueta decorativa](decoration-tag.md)
   + [Uso de Ocultar condiciones](hide-conditions.md)
   + [Configuración de varios editores in situ](multiple-inplace-editors.md)
   + [Modo de desarrollador](developer-mode.md)
   + [Prueba de la interfaz de usuario](hobbes.md)
   + [Componentes para fragmentos de contenido](components-content-fragments.md)
   + [Obtención de información de página en formato JSON](pageinfo.md)
   + Internacionalización{#internationalization}
      + [Internacionalización de componentes](i18n.md)
      + [Internacionalización de cadenas de IU](i18n-dev.md)
      + [Uso del traductor para administrar diccionarios](i18n-translator.md)
      + [Extracción de cadenas para traducir](i18n-extract.md)
   + Componentes de la IU clásica{#classic-ui-components}
      + [Desarrollo de componentes AEM (IU clásica)](developing-components-classic.md)
      + [Uso y ampliación de utilidades (IU clásica)](widgets.md)
      + [Uso de xtype (IU clásica)](xtypes.md)
      + [Desarrollo de Forms (IU clásica)](developing-forms.md)
+ Administración de experiencias sin objetivos{#headless}
   + [Sin cabezal e híbrido con AEM](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [Activación de la exportación de JSON para un componente](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html)
   + Aplicaciones de una sola página{#spas}
      + [Introducción y tutorial de SPA](spa-walkthrough.md)
      + [Tutorial de SPA WKND](spa-wknd.md)
      + [Introducción a SPA en AEM: React](spa-getting-started-react.md)
      + [Introducción a SPA en AEM: Angular](spa-getting-started-angular.md)
      + [Implementación de un componente de React para SPA](spa-implementing-react-component.md)
      + [Profundización en SPA](spa-deep-dives.md)
      + [Información general del editor de SPA](spa-overview.md)
      + [Desarrollo de SPA para AEM](spa-architecture.md)
      + [Modelo SPA](spa-blueprint.md)
      + [Componente de página SPA](spa-page-component.md)
      + [Asignación de modelos dinámicos a componentes para SPA](spa-dynamic-model-to-component-mapping.md)
      + [Enrutamiento de modelo SPA](spa-routing.md)
      + [Integración de SPA y Adobe Experience Platform Launch](spa-launch.md)
      + [SPA y procesamiento en el servidor](spa-ssr.md)
      + [SPA Materiales de referencia](spa-reference-materials.md)
   + [API HTTP](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html)
   + [Fragmentos de contenido](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [Fragmentos de experiencias](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
+ Herramientas de desarrollo{#devtools}
   + [Herramientas de desarrollo](dev-tools.md)
   + [Herramientas de modernización de AEM](modernization-tools.md)
   + [Editor de cuadro de diálogo](dialog-editor.md)
   + [Herramienta Conversión de cuadro de diálogo](dialog-conversion.md)
   + [Desarrollo con CRXDE Lite](developing-with-crxde-lite.md)
   + [Administración de paquetes con Maven](vlt-mavenplugin.md)
   + [Desarrollo de AEM proyectos con Eclipse](howto-projects-eclipse.md)
   + [Cómo crear AEM proyectos con Apache Maven](ht-projects-maven.md)
   + [Desarrollo de AEM proyectos con IntelliJ IDEA](ht-intellij.md)
   + [Cómo utilizar la herramienta VLT](ht-vlttool.md)
   + [Cómo utilizar la herramienta Proxy Server](ht-proxy-server.md)
   + [Extensión de AEM Brackets](aem-brackets.md)
   + [Herramientas para desarrolladores de AEM para Eclipse](aem-eclipse.md)
   + [AEM Repo Tool](aem-repo-tool.md)
+ Personalización{#personlization}
   + [ContextHub](contexthub.md)
   + [Referencia de la API de JavaScript de ContextHub](contexthub-api.md)
   + [Ampliación de ContextHub](ch-extend.md)
   + [Agregar ContextHub a páginas y acceder a tiendas](ch-adding.md)
   + [Ejemplos de candidatos a la tienda de ContextHub](ch-samplestores.md)
   + [Tipos de módulos de interfaz de usuario de ContextHub de muestra](ch-samplemodules.md)
   + [Diagnóstico de ContextHub](ch-diagnostics.md)
   + [Desarrollo para contenido de destino](target.md)
   + Client Context{#client-context}
      + [Client Context en detalle](client-context.md)
      + [API de JavaScript de Client Context](ccjsapi.md)
+ Ampliación de AEM{#extending-aem}
   + [Personalización de la creación de páginas](customizing-page-authoring-touch.md)
   + [Personalización de las consolas](customizing-consoles-touch.md)
   + [Personalización de vistas de propiedades de página](page-properties-views.md)
   + [Configuración de la página para la edición masiva de las propiedades de página](bulk-editing.md)
   + [Personalizar y ampliar fragmentos de contenido](customizing-content-fragments.md)
   + Extensión de flujos de trabajo{#extending-workflows}
      + [Desarrollo y ampliación de flujos de trabajo](workflows.md)
      + [Creación de modelos de flujo de trabajo](workflows-models.md)
      + [Ampliación de la funcionalidad del flujo de trabajo](workflows-customizing-extending.md)
      + [Interactuar con flujos de trabajo mediante programación](workflows-program-interaction.md)
      + [Referencia de pasos de flujo de trabajo](workflows-step-ref.md)
      + [Prácticas recomendadas del flujo de trabajo](workflows-best-practices.md)
      + [Referencia del proceso de flujo de trabajo](workflows-process-ref.md)
   + [Ampliación del administrador de varios sitios](extending-msm.md)
   + Seguimiento y análisis{#extending-analytics}
      + [Ampliación del seguimiento de eventos](extending-analytics.md)
      + [Añadir el seguimiento de Adobe Analytics a los componentes](extending-analytics-components.md)
      + [Personalización del marco de trabajo de Adobe Analytics](extending-analytics-framework.md)
      + [Implementación de la nomenclatura de páginas del lado del servidor para Analytics](extending-analytics-pa-naming.md)
   + Cloud Services{#extending-cloud-services}
      + [Configuraciones de Cloud Service](extending-cloud-config.md)
      + [Creación de un Cloud Service personalizado](extending-cloud-config-custom-cloud.md)
   + [Creación de extensiones personalizadas](extending-campaign-extensions.md)
   + Forms{#extending-forms}
      + [Creación de asignaciones de formularios personalizados](extending-campaign-form-mapping.md)
      + [Creación de plantillas de página AEM personalizadas con componentes de formulario de Adobe Campaign](extending-campaign-custom-template.md)
      + [Secuencia de comandos de análisis de solicitud](analyze-request.md)
   + [Integración de servicios con la consola JMX](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html)
   + [Desarrollo del Editor por lotes](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html)
   + Ampliación de la IU clásica{#extending-classic-ui}
      + [Personalización de la consola Sitios web (IU clásica)](customizing-siteadmin.md)
      + [Personalización de la consola de bienvenida (IU clásica)](customizing-the-welcome-console.md)
      + [Desarrollo de informes](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html)
+ Pruebas{#testing}
   + [Planificación](planning.md)
   + [¿Qué entornos de prueba se necesitarán?](test-environments.md)
   + [Definición de los casos de prueba](test-cases.md)
   + [Pruebas: ¿cuándo y con quién?](when-who.md)
   + [Compilar el plan de prueba](test-plan.md)
   + [Seguimiento de resultados y envío de comentarios](results-and-feedback.md)
   + [Herramientas de prueba y seguimiento](tools.md)
   + [Aceptación y desactivación](acceptance-signoff.md)
   + [La próxima versión...](the-next-release.md)
   + [Listas de comprobación](checklists.md)
   + [Día duro](tough-day.md)
   + [Prueba de la interfaz de usuario](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html)
+ Prácticas recomendadas{#bestpractices}
   + [Información general sobre prácticas recomendadas](best-practices.md)
   + [Directrices de desarrollo de AEM y prácticas recomendadas](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html?lang=es)
   + [Prácticas recomendadas de desarrollo](development-practices.md)
   + [Arquitectura de contenido](content-architecture.md)
   + [Arquitectura de software](software-architecture.md)
   + Implementación de referencia de We.Retail{#we-retail}
      + [Implementación de referencia de We.Retail](we-retail.md)
      + [Probar fragmentos de contenido en We.Retail](we-retail-content-fragments.md)
      + [Prueba de componentes principales en We.Retail](we-retail-core-components.md)
      + [Probar plantillas editables en We.Retail](we-retail-editable-templates.md)
      + [Probar un diseño interactivo en We.Retail](we-retail-responsive-layout.md)
      + [Cómo probar la estructura de sitios globalizados en We.Retail](we-retail-globalized-site-structure.md)
      + [Cómo probar fragmentos de experiencias en We.Retail](we-retail-experience-fragments.md)
   + [Consejos de codificación](coding-tips.md)
   + [Precauciones del código](code-pitfalls.md)
   + [Paquetes OSGI](osgi-bundles.md)
   + [Integración de JCR](jcr-integration.md)
   + [Ejemplos de código](code-samples.md)
   + [Solución de problemas de consultas lentas](troubleshooting-slow-queries.md)
+ Web móvil{#mobileweb}
   + [Web móvil](mobile-web.md)
   + [Creación de filtros de grupo de dispositivos](groupfilters.md)
   + [Diseño interactivo para páginas web](responsive.md)
   + [Creación de sitios para dispositivos móviles](mobile.md)
   + [Emuladores](emulators.md)

<!--
Deleted link to broken helpx video:
    + [Understanding Content Fragments and Content Services in AEM](https://helpx.adobe.com/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
-->
