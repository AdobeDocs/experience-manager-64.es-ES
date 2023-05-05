---
title: Preguntas más frecuentes sobre AEM
seo-title: AEM 6.4 frequently asked questions
description: Utilice estas preguntas frecuentes para comprender, configurar y solucionar problemas o flujos de trabajo comunes en AEM.
seo-description: Use these FAQs to understand, configure, and troubleshoot common workflows or issues in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# Preguntas más frecuentes sobre AEM{#aem-faqs}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Siga esta página para obtener respuestas a algunos problemas AEM de solución de problemas y configuración.

## Sites {#sites}

### ¿Cómo configuro la distribución sin binarios? {#how-do-i-configure-binary-less-distribution}

La distribución sin binario es compatible con implementaciones en un almacén de datos compartido e implica agentes que aprovechan el exportador de paquetes de distribución basado en Vault (PID de fábrica: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) creador de paquetes.

Con el modo sin binario habilitado, los paquetes de contenido distribuidos contienen referencias a binarios en lugar de a los binarios reales.

### ¿Cómo habilito la distribución sin binarios? {#how-do-i-enable-binary-less-distribution}

Para habilitar la distribución sin binarios, implemente con una tienda de blob compartida.\
Marque la `useBinaryReferences` en la configuración OSGI con el PID de fábrica ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* que su agente está usando.

### ¿Cómo puedo personalizar los mensajes de error al navegar por la jerarquía de páginas en AEM consola Sitios? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Compruebe el panel Red (del navegador Chrome) donde haya una configuración personal (JS no se ha minificado).

Consulte la `Initiator` para determinar el iniciador de una solicitud. Proporciona los archivos y los números de línea desde donde se realizan las llamadas de AJAX. Posteriormente, puede rastrear la función de gestión de errores y cambiar el mensaje de error según sus necesidades.

### ¿Cómo habilitar permisos al crear copia de idioma para autores de contenido en AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Para crear la función de copia de idioma, los autores de contenido necesitan permisos en `/content/projects` ubicación.

Si se requiere que los autores administren también los proyectos, la solución es agregar el autor a `project-administrators` grupo.

### ¿Cómo cambiar el formato al crear una copia de idioma para un proyecto? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Cree una raíz de idioma y una copia de idioma dentro de la raíz, antes de crear un proyecto de traducción.

Por ejemplo,\
Cree una raíz de idioma en `/content/geometrixx` con nombre como `fr_LU` (y el título como francés (Luxemburgo)). Posteriormente, cree una copia de idioma de la página desde el panel de referencias y vaya a `Create structure only` en `Create & Translate`. Finalmente, cree un proyecto de traducción y, a continuación, añada la copia de idioma al trabajo de traducción.

Para obtener más información, consulte los recursos adicionales a continuación:

* [Preparación del contenido para su traducción](/help/sites-administering/tc-prep.md)
* [Administración de proyectos de traducción](/help/sites-administering/tc-manage.md)

### ¿Cómo auditar las capacidades de AEM como, por ejemplo, los intentos de inicio de sesión y los cambios de ACL o permisos? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM ha introducido la capacidad de registrar cambios administrativos para mejorar la resolución de problemas y la auditoría. De forma predeterminada, la información se registra en la `error.log` archivo. Para facilitar la monitorización, se recomienda que se redirijan a un archivo de registro independiente.\
Para redirigir la salida a un archivo de registro independiente, consulte [Cómo auditar las operaciones de administración de usuarios en AEM](/help/sites-administering/audit-user-management-operations.md).

### ¿Cómo se habilita SSL de forma predeterminada? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 se envía con el asistente SSL y ofrece una interfaz de usuario para configurar la compatibilidad con Jetty y Granite Jetty SSL.

Para habilitar SSL de forma predeterminada, consulte [SSL de forma predeterminada](/help/sites-administering/ssl-by-default.md).

### ¿Cuál es la arquitectura recomendada al utilizar los servicios de contenido de AEM desde una aplicación móvil, idealmente React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Los servicios de contenido se basan en los modelos de Sling y los desarrolladores de AEM deben proporcionar un pojo de modelo de Sling para cada componente que se exporte.

Para comprender cómo utilizar AEM servicios de contenido desde una aplicación React, consulte [Introducción a los servicios de contenido AEM](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) tutorial.

Además, si los desarrolladores desean exportar un árbol de componentes, también pueden implementar la variable `ComponentExporter` y `ContainerExporter` interfaces, así como usar la variable `ModelFactory` para iterar los componentes secundarios y devolver su representación de modelo. Consulte los siguientes recursos:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling : Modelos de Sling](https://sling.apache.org/documentation/bundles/models.html)

### ¿Cómo deshabilitar AEM ventana emergente de encuesta 6.4? {#how-to-disable-aem-survey-pop-up}

Puede optar por la recopilación de estadísticas de uso mediante la IU táctil o la consola web. Para obtener instrucciones detalladas, consulte [Inclusión en la recopilación de estadísticas de uso agregadas](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### ¿Hay un buen recurso que destaque las características clave para actualizar a AEM 6.4? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Consulte [Explicación de las razones para actualizar AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) que describe el desglose de alto nivel de las funciones clave para los clientes que se plantean actualizar a la última versión de Adobe Experience Manager.

### ¿Cómo configurar una instancia de AEM para utilizar el filtro PorterStem? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

El filtro PorterStem aplica el Algoritmo de posicionamiento de Porter para inglés. Los resultados son similares al uso del temporizador de portero de bola de nieve con la variable *language=&quot;English&quot;* argumento. Pero este stemmer está codificado directamente en Java y no está basado en Snowball. No acepta una lista de palabras protegidas y solo es apropiado para texto en inglés.

Oak expone un conjunto de elementos de configuración del analizador de lucene que se utilizan en AEM. Para aprender a utilizar filtros, consulte **Analizadores de Apache Oak** en [Guía de implementación de búsqueda simple](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### ¿Cómo realizar una reindexación completa? {#how-to-perform-a-full-re-indexing}

La reindexación siempre debe abordarse teniendo debidamente en cuenta su impacto en AEM rendimiento general y realizarse durante períodos de baja actividad o períodos de mantenimiento.

Consulte la [Prácticas recomendadas para consultas e indexación](/help/sites-deploying/best-practices-for-queries-and-indexing.md) para comprender las razones para la reindexación.

### ¿Somos compatibles con las bibliotecas JS minimizadas en el Importador de diseños? {#do-we-support-minified-js-libs-in-design-importer}

Debe cambiar la propiedad de configuración predeterminada del procesador JS del Administrador de bibliotecas del HTML Granite de Adobe a ***min:gcc***. Para importar el paquete de diseño correctamente, se recomienda incluir las bibliotecas de terceros preminimizadas en nuestras bibliotecas del lado del cliente.

## Assets {#assets}

### ¿Por qué el flujo de trabajo de Assets se repite al cargar archivos MP4 (por ejemplo, mediante el método de arrastrar y soltar)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Si el usuario no tiene permisos de eliminación en el nodo de recursos al cargar los archivos de película, los nodos eliminar fragmento fallan y la carga se reinicia.

### ¿Cuál es el número máximo de activos digitales que se pueden utilizar con AEM 6.4 a la vez? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Actualmente, Adobe Experience Manager (AEM) 6.4 permite cargar hasta 2 GB de recursos a la vez.

Para obtener información adicional sobre el número máximo de activos que se pueden utilizar con AEM 6.4, consulte [Guía de tamaño de recursos](/help/assets/assets-sizing-guide.md).

### ¿Cuál es la configuración predeterminada para las configuraciones de OOTB al crear una copia de idioma? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Al crear copias de idioma mediante la IU clásica, los recursos no se mueven dentro de la nueva jerarquía de idiomas, sino que se utilizan desde el maestro de idiomas.

Por el contrario, al crear una copia de idioma mediante la IU táctil (**Referencias** -> **Actualizar copia de idioma**), se crea una nueva carpeta DAM en el nuevo idioma y se hace referencia a los recursos desde allí.

Esta es la configuración predeterminada para las configuraciones de OOTB. Puede establecer **Traducir recursos de página** = **No traducir** en Configuraciones de traducción.\
Para AEM 6.4, **Herramientas** > **Cloud Services** > **Servicios de nube de traducción**.

### ¿Cómo deshabilitar un componente AEM que causa crecimiento exponencial para el SegmentStore de AEM (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Puede desactivar el activador de componentes OSGi. Para utilizar este servicio, consulte [Activador de componentes OSGi](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Como solución alternativa, también puede deshabilitar manualmente el componente a través de la interfaz de usuario o mediante una `curl` (ejemplo abajo), después de cada reinicio AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### ¿Configurar Assets Insights con AEM instancia 6.4? {#how-to-configure-asset-insights-with-aem-instance}

Para configurar Assets Insights para el Experience Manager implementado mediante la activación de Adobe (DTM), consulte [Configuración de Assets Insights con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### ¿Cómo personalizar las consolas de administración? {#how-to-customize-admin-consoles}

AEM proporciona varios mecanismos para permitirle personalizar las consolas y la funcionalidad de creación de páginas de la instancia de creación.
Para aprender a crear una consola personalizada y personalizar una vista predeterminada para una consola, consulte [Personalización de las consolas](/help/sites-developing/customizing-consoles-touch.md).

### ¿Cuál es la diferencia entre los componentes basados en CoralUI 2 y CoralUI 3? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Se crea un nuevo conjunto de componentes de Sling de Granite UI Foundation para Coral3 y se encuentra en [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Hay un conjunto para los componentes basados en CoralUI 2 y otro para los componentes basados en CoralUI 3. El nuevo conjunto no será solo una copia y pegado del conjunto antiguo, sino que se limpiará (por ejemplo, racionalizando, eliminando funciones obsoletas). Por lo tanto, se recomienda que una página solo utilice conjuntos basados en CoralUI 3 o en CoralUI 2.

Para obtener más información detallada, consulte [Guía de migración a CoralUI 3](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### ¿Cómo personalizar el componente de búsqueda en AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

Para obtener más información sobre la mejora/clasificación de búsquedas y la implementación adicional, consulte [Guía de implementación de búsqueda simple.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

La implementación de búsqueda simple son los materiales del laboratorio de la Cumbre 2017 AEM Search Demystified.

### Si un cliente compra solo la licencia de Sites en AEM, ¿sigue teniendo acceso a Assets? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

No, el cliente no puede acceder a Recursos (ni a nada que no sea Sitios). Aunque todos los Adobe Experience Manager (AEM) On-Premise incluyen en el JAR, el cliente solo tiene acceso autorizado a los componentes del JAR para los que tiene licencia en su contrato. Si desean explorar otros componentes, pueden utilizar el programa de prueba de AEM durante un máximo de 45 días o pueden firmar un pedido de venta de 0 $ que les autorice a evaluar (sin uso de producción) componentes asignados, como Recursos.

Consulte los siguientes recursos para obtener más información sobre AEM software On-Premise y Adobe Managed Services:

* [Software On-Premise de Adobe Experience Manager](https://helpx.adobe.com/es/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/es/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### ¿Cómo puede un cliente ampliar las propiedades predeterminadas de una página o un recurso? {#how-to-extend-default-properties-page-or-asset}

Para obtener más información sobre la ampliación de las propiedades predeterminadas de una página o un recurso, consulte los siguientes recursos:

* [Esquemas de metadatos en Assets](/help/assets/metadata-schemas.md)
* [Personalización de vistas de propiedades de página](/help/sites-developing/page-properties-views.md)
