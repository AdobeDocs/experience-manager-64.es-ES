---
title: Notas de versión específicas de Adobe Experience Manager 6.4
seo-title: Notas de la versión
description: 'Adobe Experience Manager 6.4 señala la información de la versión, las novedades, cómo instalar y las listas de cambio detalladas. '
seo-description: 'Adobe Experience Manager 6.4 señala la información de la versión, las novedades, cómo instalar y las listas de cambio detalladas. '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
translation-type: tm+mt
source-git-commit: 6be9e5049600420c86120d0b6c84c1c321d7dc63
workflow-type: tm+mt
source-wordcount: '2746'
ht-degree: 25%

---


# Notas de versión específicas de Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

## Información de la versión {#release-information}

<table> 
 <tbody>
  <tr>
   <th>Producto</th> 
   <td>Adobe Experience Manager<br /> </td> 
  </tr>
  <tr>
   <th>Versión</th> 
   <td>6.4</td> 
  </tr>
  <tr>
   <th>Tipo</th> 
   <td>Versión principal</td> 
  </tr>
  <tr>
   <th>Fecha de disponibilidad general</th> 
   <td>April 4, 2018<br /> </td> 
  </tr>
  <tr>
   <th>Actualizaciones recomendadas</th> 
   <td>See <a href="https://helpx.adobe.com/es/experience-manager/aem-releases-updates.html">AEM releases and updates</a></td> 
  </tr>
 </tbody>
</table>

### Trivia {#trivia}

El ciclo de publicación de esta versión de Adobe Experience Manager comenzó el 27 de abril de 2017, pasó por 22 iteraciones de garantía de calidad y corrección de errores, y finalizó el 22 de marzo de 2018. La cantidad total de problemas relacionados con los clientes, incluidas las mejoras y nuevas características corregidas en esta versión, es de 704. 

Adobe Experience Manager 6.4 está disponible desde el 4 de abril de 2018.

>[!NOTE]
>
>Adobe recomienda instalar el Service Pack más reciente, ya que todos los paquetes de funciones nuevos solo se entregan a través de [Service Pack](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html).

## Novedades {#what-s-new}

Adobe Experience Manager 6.4 es una actualización de la base de código de Adobe Experience Manager 6.3. Proporciona funciones nuevas y mejoradas, correcciones importantes para los clientes, mejoras de alta prioridad y correcciones generales de errores orientadas a la estabilidad del producto. También incluye la mayoría de todos los paquetes de funciones de Adobe Experience Manager 6.3, correcciones urgentes y versiones de Service Pack.

La lista siguiente proporciona información general, mientras que las páginas subsiguientes lista los detalles completos.

### Experience Manager Foundation {#experience-manager-foundation}

Lista completa de cambios en [AEM Foundation](wcm-platform.md).

La plataforma de Adobe Experience Manager 6.4 se basa en versiones actualizadas de la arquitectura basada en OSGi (Apache Sling y Apache Felix) y el repositorio de contenido Java: Apache Jackrabbit Oak 1.8.2.

Quickstart utiliza Eclipse Jetty 9.3.22 como motor de servlet.

#### Interfaz de usuario {#user-interface}

Se han realizado varias mejoras en la interfaz de usuario para que sea más productiva y fácil de usar.

* [Nuevo carril](/help/sites-authoring/basic-handling.md#content-tree) del árbol de contenido para navegar rápidamente por una jerarquía. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica.
* Se ha mejorado la experiencia de desplazamiento en la vista de tarjetas y listas de carpetas grandes.
* [Se mejoró la interacción con los resultados](/help/sites-authoring/search.md) de búsqueda: el botón Atrás restaura el resultado de búsqueda anterior.
* [Métodos abreviados](/help/sites-authoring/keyboard-shortcuts.md)de teclado adicionales, para las acciones más comunes, como abrir un carril concreto, editar, mover y eliminar elementos o abrir propiedades.
* [Posibilidad de desactivar los métodos abreviados](/help/sites-authoring/user-properties.md) de teclado (activar/desactivar en Preferencias).
* [Dejar de mostrar marcas de hora en toda la interfaz de usuario](/help/sites-authoring/user-properties.md) en relación después de 7 días (opción predeterminada en Preferencias).

Consulte la documentación [de](/help/sites-authoring/home.md) creación para obtener más información sobre estas funciones.

>[!CAUTION]
>
>Adobe no tiene previsto realizar más mejoras en la interfaz de usuario clásica. AEM 6.4 tiene la interfaz de usuario clásica incluida y los clientes que actualicen desde versiones anteriores pueden seguir utilizándola. Tenga en cuenta que la interfaz de usuario clásica será totalmente compatible mientras esté en desuso. [Obtener más información](/help/sites-deploying/ui-recommendations.md).

#### Repositorio de contenido {#content-repository}

* Compactación más rápida y eficiente de Online Revision Cleanup. Las pruebas internas muestran que la nueva compactación de cola es hasta 10 veces más rápida y puede recuperar más espacio en disco con menos IOPS en comparación con AEM 6.3. Esto produce un menor impacto en el rendimiento mientras se ejecuta la limpieza de revisión en línea. Para obtener más información, consulte [la página](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)de documentación.

* Limpieza continua de revisión para MongoMK reemplaza el mantenimiento de limpieza programado
* Mejora de la eficacia de la limpieza de revisión en las novelas de Documento

#### Búsqueda e indexación {#search-indexing}

* Soporte mejorado para operaciones de indexación mediante la ejecución en roble (CLI):

   * Comprobación de la coherencia del índice
   * Estadísticas de indexación
   * Configuración de índice Im/Export
   * Reindexación

* Reducción del crecimiento del repositorio relacionado con Lucene para mejorar el rendimiento general del sistema

Para obtener más información, visite [esta página](/help/sites-deploying/indexing-via-the-oak-run-jar.md)de documentación.

#### Monitoreo {#monitoring}

* Una nueva descripción general [del sistema](/help/sites-administering/operations-dashboard.md#system-overview) proporciona una vista instantánea de todos los estados y actividades del sistema relacionados con el rendimiento
* Un nuevo conjunto de [comprobaciones](/help/sites-administering/operations-dashboard.md#health-checks) de estado en torno a la indexación, Consultas y mantenimiento

#### Proyectos y flujos de trabajo {#projects-and-workflows}

* Editor [de flujo de trabajo completamente nuevo para crear y editar modelos](/help/sites-developing/workflows-models.md)de flujo de trabajo.

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Actualizar desde la versión anterior {#upgrade-from-earlier-version}

* [Compatibilidad](/help/sites-deploying/backward-compatibility.md)con versiones anteriores: Las funciones compatibles con versiones anteriores de 6.4 ayudan a que el código personalizado siga siendo compatible en la mayoría de los casos y reducen el esfuerzo de actualización.
* [Evaluación](/help/sites-deploying/pattern-detector.md)de la complejidad de la actualización: Nueva herramienta de detección de patrones para evaluar la complejidad de las actualizaciones antes de realizar la actualización.
* [Reestructuración](/help/sites-deploying/repository-restructuring.md)del repositorio: reestructuración significativa (principalmente /etc.) para facilitar las actualizaciones y promover las mejores prácticas de implementación
* Para obtener información más general sobre las actualizaciones, consulte la [página](/help/sites-deploying/upgrade.md) para obtener más información.

### Experience Manager Sites {#experience-manager-sites}

Full list of changes in [AEM Sites and Add-ons](sites.md).

#### Experiencias fluidas {#fluid-experiences}

La introducción de Experiencias fluidas en el inicio de 2017, respaldada por Fragmentos de contenido, Fragmentos de experiencia y Servicios de contenido, fue el inicio de evolucionar hacia un gestor de contenido de varios canales. AEM 6.4 extiende cada una de las áreas de forma significativa:

**[Fragmentos de contenido](/help/assets/content-fragments.md)**

Las novedades de 6.4 son un editor de modelos [de](/help/assets/content-fragments-models.md) contenido visual y un nuevo componente [](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) configurable que proporciona una salida HTML flexible y JSON que se incluirá en Content Services.

**Fragmentos de experiencias**

La creación de variaciones en un fragmento con el mismo contenido, pero con un diseño diferente, ahora es más eficaz gracias a la función Bloques de creación. Además de enviar fragmentos de experiencias a Facebook y Pinterest, ahora es posible enviarlos a Adobe Target como oferta.

**Content Services**

Se incluyen varias mejoras en Sling Model Exporter y los componentes principales para proporcionar una salida JSON sólida para incrustar contenido en aplicaciones móviles y experiencias generadas con aplicaciones de una sola página.

#### Obtener sitios creados más rápido {#gettings-sites-built-quicker}

AEM 6.4 completa la transformación del modelo de componentes de la próxima generación. El concepto de componentes principales introducido en AEM 6.3, que ahora se une al sistema de estilos, proporciona una forma eficaz de crear nuevos sitios y ampliarlos.

Tutorial recomendado para aprender cómo aprovechar mejor el nuevo modelo de componentes: [Introducción a los AEM Sites: Tutorial de WKND](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)

#### Complemento de pantallas {#screens-add-on}

El envío de un mensaje coherente en todos los canales de marketing, incluidas las redes de señalización digital y kioscos, es lo que los AEM Screens representan. AEM 6.4 añade compatibilidad para ejecutar el reproductor de señales en el hardware de sistemas operativos Microsoft Windows y Google Chrome. Además, hay disponibles mejoras en la administración y programación de dispositivos remotos (grupos de canales).

Para obtener más información sobre las actualizaciones de Pantallas, consulte la Guía [del usuario de](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)AEM Screens.

### Experience Manager Communities {#experience-manager-communities}

AEM 6.4 incorpora muchas funciones y mejoras nuevas a Comunidades. La lista completa de los cambios está disponible en [AEM Communities](communities-release-notes.md). Los aspectos destacados de esta versión son:

#### Mejoras en la moderación {#enhancements-to-moderation}

**Detección automática de spam**

Se ha proporcionado un nuevo motor de detección de spam para filtrar el contenido generado por usuarios no deseados en los sitios y grupos de la comunidad. Una vez activado desde system/console/configMgr, marca un fragmento de contenido generado por el usuario como contenido no deseado basado en un conjunto predefinido de palabras no deseadas. Para obtener más información sobre el motor de detección de spam, consulte [automoderación de contenido](/help/communities/moderate-ugc.md#spam-detection)generado por usuarios de la comunidad.

![spamdetection](assets/spamdetection.png)

**Nuevos filtros para la garantía de calidad**

Se han añadido nuevos filtros, denominados Respondido y No Respondido, a la consola de moderación masiva para filtrar las preguntas de control de calidad. Para saber cómo funcionan los filtros de estado Respondido y No Respondido, consulte [Moderación masiva del contenido](/help/communities/moderation.md#main-pars-note-521961797)generado por el usuario.

**filtros de moderación de marcadores**

Se ha proporcionado la capacidad de marcar los filtros de moderación predefinidos en la consola de moderación. Estos filtros se anexan al final de la cadena URL, por lo que se pueden compartir, reutilizar y volver a examinar más adelante. Obtenga información sobre cómo marcar filtros en la consola [de moderación](/help/communities/moderation.md#main-pars-note-429176623)masiva.

#### Eliminar UGC y perfiles de usuario {#delete-ugc-and-user-profiles}

AEM 6.4 Communities expone las API [](/help/communities/user-ugc-management-service.md) integradas y el [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) de muestra para permitir que los usuarios finales controlen sus datos. Estas API también permiten a las organizaciones de procesamiento de datos y de control de datos atender las solicitudes de cumplimiento del RGPD de la UE.

#### Mejoras en la administración del sitio y del grupo {#enhancements-to-site-and-group-management}

**Crear grupos de varias configuraciones regionales en un solo paso**

Se ha proporcionado la capacidad de crear grupos multilingües en una sola operación. Para crear estos grupos, los usuarios pueden navegar hasta la colección de grupos del sitio de comunidades deseado desde la consola Sitios. Cree un grupo y especifique los idiomas deseados en la página Plantilla de grupo de comunidad. Para obtener más información sobre esta funcionalidad, consulte la consola [de grupos](/help/communities/groups.md)de comunidad.

![grupo multilingüe](assets/multilingualgroup.png)

**[Eliminar sitios y grupos de la comunidad con un clic](/help/communities/groups.md)**

El icono Eliminar ya está disponible en los sitios y grupos respectivos, mientras navega desde la navegación global. Con este icono se eliminan todos los elementos y el contenido asociados con el sitio o grupo y se eliminan todas las asociaciones de usuarios. Para obtener más información sobre esta funcionalidad, consulte [administración de sitios](/help/communities/create-site.md#main-pars-text-fe17) de la comunidad y [administración de grupos](/help/communities/groups.md#main-pars-text-5e8c)de la comunidad.

#### Enhancements to Enablement {#enhancements-to-enablement}

Las funciones Asignación y Catálogo ahora están disponibles dentro de los grupos. Esto permite crear, administrar y publicar contenido de aprendizaje para un conjunto específico de miembros de la comunidad objetivo. Para obtener más información sobre cómo habilitar grupos de la comunidad, consulte [Administración de recursos](/help/communities/resource.md)de habilitación.

![catálogo de asignaciones](assets/assignmentcatalog.png)

### Recursos de Experience Manager {#experience-manager-assets}

AEM 6.4 incorpora varias funciones y mejoras nuevas en Assets, incluida la integración de Creative Cloud mejorada, innovaciones clave de Inteligencia artificial, administración de metadatos mejorada, mejoras en el sistema de informes y mejoras generales en la experiencia del usuario. lista completa de los cambios disponibles en [AEM Assets](assets.md). Los aspectos más destacados de la versión son:

**Adobe Asset Link**

Adobe Asset Link en Creative Cloud para empresas optimiza la colaboración entre creativos y especialistas en marketing en el proceso de creación de contenido. Es una nueva función nativa en Creative Cloud para empresas que conecta Photoshop CC, Illustrator CC e InDesign CC con AEM: sin que los creativos tengan que dejar sus herramientas de elección.

Para obtener más información sobre esta capacidad, los requisitos previos y cómo acceder a ella, consulte [Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html).

![adobe_asset_link](assets/adobe_asset_link.png)

**Aplicación de escritorio de AEM**

La aplicación de escritorio de AEM se ha actualizado a la versión 1.8, que es compatible con AEM 6.4. La lista completa de los cambios para la aplicación de escritorio de AEM se proporciona en un documento de notas [de la versión de la aplicación de escritorio de](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html) AEM dedicado.

Las mejoras introducidas desde la versión AEM 6.3 incluyen la capacidad de cargar carpetas jerárquicas en segundo plano, una nueva interfaz de usuario para supervisar las operaciones en segundo plano de recursos, almacenamiento en caché mejorado, redes e inicio de sesión, así como mejoras generales de estabilidad. La documentación también incluye una guía [de](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)prácticas recomendadas.

**Adobe Sensei Services**

Las nuevas funciones incluyen etiquetas inteligentes mejoradas, con la capacidad de aprender taxonomía empresarial del cliente, etiquetar automáticamente recursos digitales con etiquetas específicas del cliente y Búsqueda de traducción inteligente, lo que mejora la capacidad de detección en varios idiomas al traducir los términos de búsqueda sobre la marcha. Para obtener más información sobre esta función, consulte Etiquetas inteligentes [mejoradas](/help/assets/enhanced-smart-tags.md).

![Enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**Metadatos**

Entre las diversas mejoras se incluye la capacidad de importar y exportar metadatos simultáneamente para una gran cantidad de recursos y construcciones de metadatos avanzadas, como los metadatos en [cascada](/help/assets/cascading-metadata.md).

**Informes**

El sistema de informes de recursos ha sido objeto de una gran revisión en AEM 6.4 con la nueva estructura de sistema de informes, la experiencia del usuario y más informes de OOTB para casos de uso del cliente. Para obtener información sobre cómo generar varios informes, consulte Informes [](/help/assets/asset-reports.md)de recursos.

**Experiencia del usuario**

Se han realizado varias mejoras para mejorar la navegación, la búsqueda y la experiencia de administración de los usuarios de Recursos, como la experiencia de desplazamiento, el botón de retroceso de la búsqueda, los filtros de búsqueda mejorados y muchas más. lista completa disponible en [AEM Assets](assets.md).

**Brand Portal**

Varias mejoras en áreas de metadatos, sistema de informes, derechos digitales, experiencia de inicio de sesión y rendimiento de publicación para la distribución de recursos. Para obtener información sobre las nuevas mejoras y funciones, consulte [Novedades del portal](https://helpx.adobe.com/experience-manager/brand-portal/using/whats-new.html)de marcas de AEM Assets.

#### Dynamic Media Add-on {#dynamic-media-add-on}

AEM 6.4 incluye muchas funciones y mejoras nuevas en Dynamic Media. La lista completa está disponible en [AEM Assets](assets.md). Entre los aspectos destacados se incluyen los siguientes:

**Recorte inteligente**

Smart Crop, con tecnología Adobe Sensei, proporciona automáticamente recorte no destructivo de imágenes, preservando el punto de interés para un diseño interactivo. Si es necesario, puede previsualización las sugerencias de imagen recortada y ajustarlas manualmente. Esta función también permite la generación automatizada de muestras para imágenes de productos.

Consulte la documentación [de Perfiles](/help/assets/image-profiles.md) de imagen para obtener más información sobre el uso de Recorte inteligente.

Consulte [Añadir recursos de Dynamic Media a páginas](/help/assets/adding-dynamic-media-assets-to-pages.md) para obtener más información sobre cómo trabajar con recorte inteligente en el componente de Dynamic Media.

**Imágenes inteligentes**

Las imágenes inteligentes aprovechan las características de visualización únicas de cada usuario para ofrecer automáticamente imágenes optimizadas para su experiencia, lo que resulta en un mayor rendimiento y compromiso.

Consulte la documentación de imágenes [inteligentes](/help/assets/imaging-faq.md) para obtener más información.

![smart_cut](assets/smart_crop.png)

**Nuevas mejoras en los medios y visores**

Los nuevos visores, incluidos Panorámico y VR, le permiten ofrecer experiencias más envolventes.

Consulte la documentación [de imágenes](/help/assets/panoramic-images.md) panorámicas para obtener más información.

**Recursos 3D**

Nueva integración con [Adobe Dimension CC](https://www.adobe.com/products/dimension.html), una aplicación de Creative Cloud para la creación de experiencias 3D.

Consulte [Uso de la documentación de recursos](/help/assets/assets-3d.md) 3D para obtener más información.

![no localizar/3d](assets/do-not-localize/3d.png)

### Experience Manager Forms {#experience-manager-forms}

AEM 6.4 Forms incorpora varias funciones y mejoras nuevas. Los aspectos más destacados incluyen:

* Comunicaciones interactivas de varios canales
* Precompletar comunicaciones interactivas desde aplicaciones empresariales
* Modernización del flujo de trabajo y compatibilidad con trabajadores móviles
* Carga diferida de fragmentos
* Actualización de un solo salto de LiveCycle a Experience Manager Forms 6.4

Más detalles en la página de notas de la versión de [AEM Forms](forms.md) . Also, see the [Summary of new features and enhancements in AEM 6.4 Forms](/help/forms/using/whats-new.md) for information about new and improved features and documentation resources.

### Experience Manager Livefyre {#experience-manager-livefyre}

Puede integrar Livefyre con su instancia de AEM 6.4. En esta página encontrará más información sobre cómo integrar Livefyre con AEM:

* [Integración de Livefyre](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html)

### Aprovechar el desarrollo centrado en el cliente {#leverage-customer-focused-development}

Adobe utiliza un modelo de desarrollo centrado en el cliente que le permite contribuir en todas las etapas del proceso de desarrollo, la especificación, el desarrollo y las pruebas. Agradecemos a todos los clientes y socios que hayan contribuido en este proceso.

Adobe cuenta con los procedimientos y procesos necesarios para permitir la recopilación, priorización y seguimiento de la resolución de errores centrada en el cliente y el desarrollo de solicitudes de mejora. The [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) is integrated with the Adobe Enhancement &amp; Defect Tracking System. Las preguntas de los clientes se identifican y resuelven con el Servicio de atención al cliente siempre que es posible. Cuando estas preguntas se envían al departamento de I+D, se recopila toda la información de los clientes y se utiliza para establecer prioridades y elaborar informes. Asimismo, se otorga prioridad en cuanto al desarrollo de los problemas de compatibilidad y garantías pagadas y a las mejoras pagadas de los clientes.

Este proceso de establecimiento de prioridades creó más de 500 cambios orientados al cliente que se solucionaron en AEM 6.4.

## Lista de archivos que forman parte de la versión {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Quickstart independiente: cq-quickstart-6.4.0.jar
* Inicio rápido del servidor de aplicaciones: cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 or newer for various web servers and platforms ([download link](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html))
* Plugin para Eclipse IDE ([más información y descarga](/help/sites-developing/aem-eclipse.md))

* Extensión para el editor de texto Brackets ([más información y descarga](/help/sites-developing/aem-brackets.md))
* Dependencias de Maven/Gradle (vínculo[de](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)descarga)

**Sites**

* Componentes principales (proyecto[](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)GitHub)
* Implementación de referencia We.Retail ([más información](/help/sites-developing/we-retail.md))
* Arquetipo de modelo de proyecto (proyecto[GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* AEM Screens Players for various target platforms ([download](https://download.macromedia.com/screens/))
* Modelos de idioma de contenido inteligente. El idioma inglés está preinstalado, pero se pueden descargar más idiomas

   * [Alemán](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Español](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiano](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Francés](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [Herramienta](/help/sites-developing/dialog-conversion.md) de conversión de cuadro de diálogo para migrar componentes de la IU clásica a Coral 3

**Assets**

* Aplicación de escritorio de Adobe Experience Manager ([leer más](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html) y [descargar](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html))

* Package to add enhanced PDF Rasterizer ([read more](/help/assets/aem-pdf-rasterizer.md) and [download](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/assets/aem-assets-pdf-rasterizer-pkg))

* Paquete para agregar compatibilidad ampliada con imágenes RAW ([más información](/help/assets/camera-raw.md))

**Forms**

* Paquetes para las funciones de AEM Forms:

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

## Idiomas {#languages}

La interfaz de usuario está disponible en los idiomas siguientes:

* Inglés
* Alemán
* Francés
* Español
* Italiano
* Portugués de Brasil
* Japonés
* Chino simplificado
* Chino tradicional (compatibilidad limitada)
* Coreano

Experience Manager 6.4 se ha certificado para GB18030-2005 CITS para que pueda utilizar el estándar de codificación de caracteres chinos.

## Instalar y actualizar {#install-update}

Consulte las [instrucciones de instalación](/help/sites-deploying/custom-standalone-install.md) para ver los requisitos de configuración.

Consulte la [documentación de actualización](/help/sites-deploying/upgrade.md) para obtener instrucciones detalladas.

## Plataformas compatibles {#supported-platforms}

Encontrará la matriz completa de plataformas admitidas, incluido el nivel de compatibilidad en los [requisitos técnicos de AEM 6.4](/help/sites-deploying/technical-requirements.md)

>[!NOTE]
>
>Oracle ha adoptado un modelo de soporte a largo plazo (LTS) para los productos Oracle Java SE. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe solo proporcionará soporte a las versiones LTS de Java para ejecutar AEM en producción. Por lo tanto, Java 8 es la versión que se recomienda para AEM 6.4.

## Funciones en desuso y eliminadas {#deprecated-and-removed-features}

Adobe evalúa constantemente las capacidades del producto y, con el tiempo, planea sustituir las capacidades con versiones más potentes o decide volver a implementar los elementos seleccionados y así poder estar mejor preparado para futuras expectativas o extensiones.

En cuanto a Adobe Experience Manager 6.4, [consulte la lista de funciones en desuso y eliminadas](deprecated-removed-features.md). La página también contiene un anuncio previo de los cambios en 2019 y un aviso importante para los clientes que se actualizan a partir de versiones anteriores.

## Listas de cambios detallados {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[Formularios AEM](forms.md)

[AEM Foundation](wcm-platform.md)

## Problemas conocidos {#known-issues}

[Lista de problemas conocidos](known-issues.md)

### Descarga de productos y asistencia (sitios restringidos) {#product-download-and-support-restricted-sites}

Estos sitios solo están disponibles para los clientes. Si es un cliente y requiere acceso, póngase en contacto con su administrador de cuentas de Adobe.

* [](https://daycare.day.com) [Descarga de productos en Licensing.adobe.com](https://licensing.adobe.com/)

* [Asistencia al cliente en daycare.day.com](https://daycare.day.com)

