---
title: Preguntas más frecuentes AEM
seo-title: AEM 6.4 preguntas más frecuentes
description: Utilice estas preguntas más frecuentes para comprender, configurar y solucionar problemas o flujos de trabajo comunes en AEM.
seo-description: Utilice estas preguntas más frecuentes para comprender, configurar y solucionar problemas o flujos de trabajo comunes en AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---


# Preguntas más frecuentes AEM{#aem-faqs}

Siga esta página para obtener respuestas a algunos problemas AEM de resolución de problemas y configuración.

## Sites {#sites}

### ¿Cómo configuro la distribución sin binarios? {#how-do-i-configure-binary-less-distribution}

La distribución sin binarios es compatible con implementaciones en un almacén de datos compartido e incluye agentes que aprovechan el exportador de paquetes de distribución basado en Vault (PID de fábrica: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`).

Con el modo sin binarios habilitado, los paquetes de contenido distribuidos contienen referencias a binarios en lugar de a los binarios reales.

### ¿Cómo habilito la distribución sin binarios? {#how-do-i-enable-binary-less-distribution}

Para habilitar la distribución sin binarios, implemente con un almacén de blob compartido.\
Compruebe la `useBinaryReferences` propiedad en la configuración OSGI con el PID de fábrica ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*que está utilizando el agente.

### ¿Cómo puedo personalizar los mensajes de error al navegar por la jerarquía de páginas en AEM consola Sitios? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Compruebe el panel Red (del navegador Chrome) donde haya una configuración personal (JS no se ha minimizado).

Vista la `Initiator` columna para determinar el iniciador de una solicitud. Proporciona los archivos y los números de línea desde donde se realizan las llamadas de AJAX. Posteriormente, puede rastrear la función de gestión de errores y cambiar el mensaje de error según sus necesidades.

### ¿Cómo habilitar permisos al crear una copia de idioma para autores de contenido en AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Para crear la función de copia de idioma, los autores de contenido necesitan permisos en la `/content/projects` ubicación.

Si se requiere que los autores también gestionen proyectos, la solución consiste en agregar al autor al `project-administrators` grupo.

### ¿Cómo cambiar el formato al crear una copia de idioma para un proyecto? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Cree una raíz de idioma y una copia de idioma dentro de la raíz, antes de crear un proyecto de traducción.

Por ejemplo,\
Cree una raíz de idioma en `/content/geometrixx` con el nombre como `fr_LU` (y el título como francés (Luxemburgo)). Posteriormente, cree una copia de idioma de la página desde el panel de referencias y vaya a `Create structure only` la opción de `Create & Translate`. Finalmente, cree un proyecto de traducción y luego agregue la copia de idioma al trabajo de traducción.

Para obtener más información, consulte los recursos adicionales siguientes:

* [Preparación del contenido para la traducción](/help/sites-administering/tc-prep.md)
* [Administración de proyectos de traducción](/help/sites-administering/tc-manage.md)

### ¿Cómo auditar las capacidades de AEM como, por ejemplo, los intentos de inicio de sesión y los cambios de ACL o permisos? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM ha introducido la capacidad de registrar cambios administrativos para mejorar la resolución de problemas y la auditoría. De forma predeterminada, la información se registra en el `error.log` archivo. Para facilitar la supervisión, se recomienda que se redirijan a un archivo de registro independiente.\
Para redirigir el resultado a un archivo de registro independiente, consulte [Cómo auditar las operaciones de administración de usuarios en AEM](/help/sites-administering/audit-user-management-operations.md).

### ¿Cómo habilitar SSL de forma predeterminada? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 se suministra con el asistente SSL y oferta una interfaz de usuario para configurar la compatibilidad con SSL de Jetty y Granite Jetty.

Para habilitar SSL de forma predeterminada, consulte [SSL de forma predeterminada](/help/sites-administering/ssl-by-default.md).

### ¿Cuál es la arquitectura recomendada al utilizar los servicios de contenido de AEM desde una aplicación móvil, idealmente Reaccionar nativo? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Los servicios de contenido se basan en los modelos de Sling y los desarrolladores de AEM deben proporcionar un pojo de modelo de Sling para cada componente exportado.

Para comprender cómo utilizar AEM servicios de contenido desde una aplicación React, consulte el tutorial [Introducción a los servicios](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) de contenido de AEM.

Además, si los desarrolladores desean exportar un árbol de componentes, también pueden implementar las interfaces `ComponentExporter` y `ContainerExporter` , así como utilizar el `ModelFactory` para iterar sobre los componentes secundarios y devolver su representación de modelo. Consulte los recursos siguientes:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] Apache [Sling :: Modelos Sling](https://sling.apache.org/documentation/bundles/models.html)

### ¿Cómo desactivar AEM ventana emergente de encuesta 6.4? {#how-to-disable-aem-survey-pop-up}

Puede optar por la recopilación de estadísticas de uso mediante la IU táctil o la consola web. Para obtener instrucciones detalladas, consulte [Opción de recopilación](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)de estadísticas de uso agregadas.

### ¿Existe un buen recurso que destaca las características clave para la actualización a AEM 6.4? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Consulte [Explicación de las razones para actualizar AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) que describe el desglose de alto nivel de las funciones clave para los clientes que están considerando actualizar a la versión más reciente de Adobe Experience Manager.

### ¿Cómo configurar una instancia de AEM para utilizar el filtro PorterStem? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

El filtro PorterStem aplica el algoritmo de temporización Porter para inglés. Los resultados son similares al uso del atleta de bola de nieve con el argumento *language=&quot;English&quot;* . Pero este stemmer está codificado directamente en Java y no está basado en Snowball. No acepta una lista de palabras protegidas y sólo es apropiado para texto en inglés.

Oak expone un conjunto de elementos de configuración del analizador de lucene que se utilizan en AEM. Para aprender a utilizar filtros, consulte **Apache Oak Analyzers** en la guía [de implementación de búsquedas](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)simples.

### ¿Cómo realizar una reindexación completa? {#how-to-perform-a-full-re-indexing}

La reindexación debe abordarse siempre teniendo debidamente en cuenta su impacto en AEM rendimiento general y durante períodos de baja actividad o ventanas de mantenimiento.

Consulte las [Prácticas recomendadas para Consultas e indexación](/help/sites-deploying/best-practices-for-queries-and-indexing.md) para comprender las razones para volver a indexar.

### ¿Es compatible con las bibliotecas JS minimizadas en el Importador de diseños? {#do-we-support-minified-js-libs-in-design-importer}

Debe cambiar la propiedad de configuración predeterminada del procesador JS del Administrador de biblioteca HTML de Adobe Granite a ***min:gcc***. Para importar el paquete de diseño correctamente, se recomienda incluir bibliotecas de terceros preminimizadas en nuestras bibliotecas de cliente.

## Assets {#assets}

### ¿Por qué se repite el flujo de trabajo de Recursos al cargar archivos MP4 (por ejemplo, mediante el método de arrastrar y soltar)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Si el usuario no dispone de permisos de eliminación en el nodo de recursos para cargar los archivos de película, los nodos de fragmentos de eliminación fallan y se reinicia la carga.

### ¿Cuál es el número máximo de recursos digitales que se pueden utilizar con AEM 6.4 a la vez? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager (AEM) 6.4 permite cargar hasta 2 GB de recursos a la vez.

Para obtener información adicional sobre el número máximo de recursos que se pueden utilizar con AEM 6.4, consulte Guía [de tamaño de](/help/assets/assets-sizing-guide.md)recursos.

### ¿Cuál es la configuración predeterminada para las configuraciones de OOTB al crear una copia de idioma? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Al crear copias de idioma mediante la IU clásica, los recursos no se mueven bajo la nueva jerarquía de idioma, sino que se utilizan desde el maestro de idioma.

Mientras que, al crear una copia de idioma mediante la IU táctil (**Referencias** -> **Actualizar copia** de idioma), se crea una nueva carpeta DAM en el nuevo idioma y se hace referencia a los recursos desde allí.

Esta es la configuración predeterminada para las configuraciones de OOTB. Puede definir **Traducir recursos** de página = **No traducir** en configuraciones de traducción.\
Para AEM 6.4, **Herramientas** > **Cloud Services** > Servicios **de** Translation Cloud.

### ¿Cómo deshabilitar un componente AEM que causa crecimiento exponencial para el AEM SegmentStore (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Puede desactivar el activador de componentes OSGi. Para utilizar este servicio, consulte [Activador](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)de componentes OSGi.

Como solución alternativa, también puede deshabilitar manualmente el componente mediante la interfaz de usuario o mediante un `curl` comando (ejemplo más abajo), después de cada reinicio AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### ¿Cómo configurar las perspectivas de recursos con AEM instancia 6.4? {#how-to-configure-asset-insights-with-aem-instance}

Para configurar y configurar las perspectivas de recursos para Experience Manager implementados mediante la Activación de Adobe (DTM), consulte [Configurar perspectivas de recursos con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### ¿Cómo personalizar las consolas de administración? {#how-to-customize-admin-consoles}

AEM proporciona varios mecanismos que le permiten personalizar las consolas y la funcionalidad de creación de páginas de la instancia de creación.
Para obtener información sobre cómo crear una consola personalizada y personalizar una vista predeterminada para una consola, consulte [Personalización de las consolas](/help/sites-developing/customizing-consoles-touch.md).

### ¿Cuál es la diferencia entre los componentes basados en CoralUI 2 y CoralUI 3? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Se ha creado un nuevo conjunto de componentes Sling de Granite UI Foundation para Coral3 y se encuentra en [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Hay un conjunto para los componentes basados en CoralUI 2 y otro para los componentes basados en CoralUI 3. El nuevo conjunto no será sólo una copia y pegado del conjunto anterior, sino que se limpiará (por ejemplo, racionalizando, eliminando funciones obsoletas). Por lo tanto, se recomienda que una página utilice únicamente conjuntos basados en CoralUI 3 o en CoralUI 2.

Para obtener más información detallada, consulte Guía [de migración a CoralUI 3 basada](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### ¿Cómo personalizar el componente de búsqueda en AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

Para obtener más información sobre la mejora/clasificación de la búsqueda y la implementación adicional, consulte la guía de implementación de búsqueda [simple.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

La implementación de la búsqueda simple son los materiales del laboratorio de la Cumbre 2017 AEM Search Demystified.

### Si un cliente compra únicamente la licencia de Sitios en AEM, ¿aún tiene acceso a Recursos? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

No, el cliente no puede acceder a Recursos (ni a ningún otro elemento que no sea Sitios). Aunque todos los componentes de Adobe Experience Manager (AEM) locales están incluidos en el JAR, el cliente sólo tiene acceso autorizado a los componentes del JAR para los que tiene licencia en su contrato. Si desean explorar otros componentes, pueden utilizar el programa de prueba de AEM durante un máximo de 45 días o pueden firmar un pedido de venta de $0 que les autorice a evaluar (sin uso de producción) los componentes con nombre, como Recursos.

Consulte los siguientes recursos para obtener más información sobre AEM software local y los servicios gestionados de Adobe:

* [Software local Adobe Experience Manager](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### ¿Cómo puede un cliente ampliar las propiedades predeterminadas de una página o un recurso? {#how-to-extend-default-properties-page-or-asset}

Para obtener más información sobre la ampliación de las propiedades predeterminadas de una página o un recurso, consulte los recursos siguientes:

* [Esquemas de metadatos en recursos](/help/assets/metadata-schemas.md)
* [Personalización de Vistas de propiedades de página](/help/sites-developing/page-properties-views.md)
