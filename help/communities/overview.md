---
title: Información general de AEM Communities
seo-title: Información general de AEM Communities
description: Información general sobre las funciones y la configuración de AEM Communities
seo-description: Información general sobre las funciones y la configuración de AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 4%

---


# Información general de AEM Communities {#aem-communities-overview}

Las comunidades de Adobe Experience Manager (AEM) ofrecen la posibilidad de crear rápidamente un sitio de comunidad local que tenga un rendimiento y una gestión mejorados, y que anime a los visitantes a convertirse en miembros valiosos de la comunidad.

Póngase en contacto con el representante de cuentas para obtener información sobre la licencia de AEM Communities, así como sobre las licencias adicionales para funciones de habilitación y Adobe Analytics.

## Funciones de comunidades {#communities-features}

AEM Communities permite el desarrollo de una relación con los visitantes del sitio que informan a través de blogs, preguntas y respuestas y calendarios de eventos, a la vez que obtiene perspectivas a través de foros, comentarios y otro contenido de la comunidad, a menudo denominado contenido generado por el usuario (UGC, por sus siglas en inglés).

Además, AEM Communities permite la moderación por parte de miembros de confianza en el entorno de publicación, el inicio de sesión social con Twitter y Facebook, la traducción en línea del contenido de la comunidad, la creación de grupos de la comunidad desde el sitio de la comunidad publicada, la puntuación para otorgar distintivos, el uso compartido de archivos, las notificaciones y los flujos de actividad.

Las características de las comunidades pueden demostrarse con la [AEM Máquina](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) de demostración disponible públicamente en GitHub.com o con la nueva implementación de referencia de We.Retail.

## Sitios de la comunidad {#community-sites}

Un sitio de comunidad es un sitio AEM creado con un simple asistente que resulta en un sitio web con muchas características comunes preprogramadas en el sitio.

Asistente para la creación [del sitio](sites-console.md):

* Ensamble las características del sitio, en función de la plantilla [del sitio de la](sites.md) comunidad seleccionada, que es
   * Creado a partir de funciones [comunitarias](#community-functions)
   * Función opcional de grupos [de](#communitygroups) comunidad
* Utiliza la configuración para configurar:
   * Moderación
   * Inicio de sesión
   * Traducción
* Proporciona funciones esenciales:
   * Diseño adaptable: Utiliza temáticas [de Bootstrap de Twitter](https://getbootstrap.com)
   * Inicio de sesión: Registro propio, inicio de sesión [](social-login.md)social, perfiles de usuario
   * Notificaciones: Los Miembros consideran que los eventos son pertinentes para ellos
   * Mensajería: Los miembros pueden enviar o recibir mensajes dentro del sitio de la comunidad
   * Buscar: Capacidad para realizar búsquedas dentro del sitio de la comunidad
   * Cambio de idioma: Posibilidad de seleccionar un idioma para un sitio [multilingüe](../../help/sites-administering/translation.md)
   * Administración: Acceso para miembros autorizados para moderar y administrar usuarios dentro del sitio de la comunidad
* Elimina muchos pasos de creación a nivel de página:
   * Marca: Carga opcional de una imagen de pancarta para mostrarla en todas las páginas del sitio de la comunidad
   * Menú de navegación: Se proporcionan vínculos de navegación para las funciones incluidas en la plantilla del sitio de la comunidad

Para disfrutar de la facilidad de crear rápidamente un nuevo sitio de comunidad, visite [Introducción a AEM Communities](getting-started.md).

## Persistencia del contenido de la comunidad {#community-content-persistence}

Para mejorar el rendimiento y la sincronización del contenido de la comunidad, AEM Communities requiere un almacén común específico para el contenido generado por el usuario (UGC) compartido entre todas las instancias de AEM (autor y publicación).

Se puede acceder fácilmente al contenido de la comunidad a través del proveedor de recursos de almacenamiento (SRP), que proporciona una capa para separar el acceso de la topología subyacente y admite un almacén común para UGC.

Para obtener más información sobre la persistencia del contenido de la comunidad y las implementaciones recomendadas, visite:

* [Almacenamiento](working-with-srp.md)de contenido de la comunidad: analiza las opciones de almacenamiento de SRP disponibles para UGC
* [Topologías](topologies.md)recomendadas: analiza las topologías en función del caso de uso y la opción de SRP
* [Actualización a AEM comunidades](upgrade.md)6.3: proporciona información útil sobre UGC cuando se mueve a AEM 6.3.

## Consolas de comunidades {#communities-consoles}

En el entorno de creación, la consola de navegación global proporciona acceso a la consola [](consoles.md)Comunidades, que contiene:

* consola [Sitios](sites-console.md)

   * Creación de sitios
   * Edición del sitio
   * Administración de sitios
   * [Consola de grupos](groups.md) de comunidad

* [Consola de moderación](moderation.md)

   * IU común de moderación masiva para entornos de creación y publicación
   * Nuevos criterios de filtrado

* [Consolas de administración de miembros y grupos](members.md)

   * Proporciona la capacidad de crear y administrar usuarios de publicación (miembros) desde el entorno de creación
   * Permite prohibir miembros
   * Proporciona la capacidad de crear y administrar grupos de usuarios del lado de la publicación (grupos de miembros) desde el entorno de creación

* [Consola de informes](reports.md)

   * Proporciona la capacidad de generar informes sobre asignaciones, anuncios y vistas

* [Consola de recursos](resources.md)

   * Proporciona la capacidad de crear recursos de habilitación y rutas de aprendizaje
   * Proporciona acceso a informes sobre recursos de habilitación y rutas de aprendizaje

La consola de herramientas globales proporciona acceso a las siguientes herramientas de Comunidades:

* [Consola Plantillas](tools.md#sitetemplatesconsole) de sitio

   * Crear y administrar plantillas de sitio de comunidad

* [Consola Plantillas](tools.md#grouptemplatesconsole) de grupo

   * Crear y administrar plantillas de grupos de comunidad

* [Consola de funciones](tools.md#communityfunctionsconsole) de comunidad

   * Crear y administrar funciones de comunidad

* [Consola de configuración](tools.md#storageconfiguratonconsole) de Almacenamiento

   * Seleccionar y configurar el almacén [](working-with-srp.md) común para el sitio

* [Guía de componentes](components-guide.md)

   * Un sitio de muestra, [Community Components](http://localhost:4502/editor.html/content/community-components/en.html), que proporciona una muestra de todos los componentes de Communities con su configuración predeterminada y la capacidad de experimentar con ellos

## Plantillas de sitio de la comunidad {#community-site-templates}

La creación del sitio de la comunidad se basa en la selección de una plantilla del sitio de la comunidad para configurar rápidamente un sitio de la comunidad que sea independiente de cualquier sitio de muestra.

Una plantilla de sitio de comunidad, compuesta de funciones de comunidad y plantillas de grupo de comunidad, proporciona la estructura de un sitio de comunidad, incluyendo inicio de sesión, perfiles de usuario, mensajes, menú del sitio, búsqueda, tema y características de marca.

Consulte la consola [Plantillas](sites.md)del sitio.

## Funciones de comunidad {#community-functions}

Las características que se esperan de una experiencia comunitaria son bien conocidas. Con AEM Communities, estas funciones están disponibles como componentes básicos, conocidas como funciones de la comunidad.

Las funciones de la comunidad son páginas AEM normales compuestas por componentes conectados en una función que se incorpora fácilmente a una plantilla de sitio de comunidad.

Consulte la consola [Funciones de](functions.md)comunidad.

## Grupos de la comunidad y plantillas de grupo {#community-groups-and-group-templates}

La función de grupos de comunidad es la capacidad para que una subcomunidad sea creada dinámicamente dentro de un sitio de comunidad por usuarios autorizados y miembros de la comunidad desde los entornos de creación y publicación.

Desde el entorno de creación, se pueden crear grupos de comunidad (subcomunidades) dentro de un sitio de comunidad existente o anidados dentro de un grupo existente, cuando la estructura de la plantilla contenga la función [](functions.md#groups-function)Grupos.

La creación de un grupo de comunidad requiere la selección de una plantilla de grupo de comunidad que proporcione el diseño de las páginas de grupo de la comunidad. Cuando se agrega una función Grupos a una estructura de plantilla, se configura para especificar una plantilla de grupo o para proporcionar una selección de plantillas en el momento en que se crea un nuevo grupo de comunidad.

Consulte también:

* [Consola](groups.md) Grupos del sitio: creación de subcomunidades en el entorno de creación
* [Consola](tools-groups.md) Plantillas de grupo: creación de una estructura de sitio para grupos
* [Introducción a AEM Communities](getting-started.md) : tutorial para crear rápidamente un sitio de comunidad que incluya grupos anidados

## Componentes de comunidad {#community-components}

Los componentes [de](author-communities.md) comunidad a partir de los cuales se crea un sitio de comunidad pueden utilizarse para agregar funciones de comunidades a cualquier sitio AEM.

La guía [de componentes de](components-guide.md) comunidad está disponible para la exploración interactiva de los componentes.

## Tipos de comunidades {#types-of-communities}

### Comunidad de participación {#engagement-community}

Una comunidad de participación es un sitio de la comunidad dedicado a atraer clientes para que informen, soliciten comentarios y permitan a los clientes interactuar como miembros de la comunidad.

Las características de una comunidad de participación pueden incluir:

* Inicio de sesión
* Mensajes
* Foros
* Comentarios
* Críticas
* Clasificaciones
* Votación
* Blogs
* Grupos
* Calendarios
* Traducción
* Moderación
* Notificaciones
* Puntuación y distintivos
* sistema de informes de Analytics

Para experimentar la facilidad de crear rápidamente una nueva comunidad de participación, visite [Introducción a AEM Communities](getting-started.md).

### Comunidad de habilitación {#enablement-community}

Una comunidad de habilitación es un sitio de la comunidad que incluye funciones para el aprendizaje en línea.

Las características de una comunidad de habilitación pueden incluir:

* Todas las características de una comunidad de [participación](#engagement-community)
* Capacidad para asignar contenido y recursos de aprendizaje a miembros y grupos de miembros
* Admite contenido SCORM, como cuestionarios y pruebas
* Seguimiento de la finalización de las asignaciones
* Acceso a sistemas de informes y análisis
* La capacidad de tener una conversación sobre un recurso de aprendizaje a través de foros, mensajes, comentarios y valoraciones

Se puede crear una comunidad de habilitación cuando se configura [el complemento](enablement.md)Habilitación, que requiere licencias adicionales para su uso en un entorno de producción. Un sitio de comunidad de habilitación incluirá la función [](#community-functions)asignaciones.

Para disfrutar de la facilidad de crear una nueva comunidad de habilitación, visite [Introducción a AEM Communities para la habilitación](getting-started-enablement.md).

## AEM Demo Machine {#aem-demo-machine}

La [AEM Máquina](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) de demostración administra y ejecuta demostraciones para AEM [sitios](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [recursos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [comunidades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [aplicaciones](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)yForms, que a menudo requieren más configuración que simplemente lanzar una instancia de QuickStart. AEM Demo Machine configurará [infraestructura](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) adicional como MongoDB, Solr, MySQL, FFmpeg y servidores de correo electrónico.

La AEM Demo Machine consta de

* Una interfaz de usuario [gráfica](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Secuencias de comandos Apache ANT con [propiedades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) y [destinatarios configurables](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Paquetes para instalarAEM Demo Machine se probó correctamente con CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 y AEM 6.3 en Windows, MacOS y Linux.

La AEM Demo Machine requiere una licencia de AEM válida.

>[!NOTE]
>
>Vista de una introducción [](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) en vídeo a la AEM Demo Machine (13:26).

## Documentación de AEM Communities {#aem-communities-documentation}

* Visite [Implementar comunidades](deploy-communities.md) para conocer las implementaciones recomendadas.

* Visite [Administración de sitios](administer-landing.md) de comunidades para obtener información sobre cómo crear un sitio de comunidad, agregar grupos de la comunidad, configurar plantillas de sitio de la comunidad, moderar contenido de la comunidad, administrar miembros, etiquetado, notificaciones, puntuación y distintivos.

* Visite [Desarrollar comunidades](communities.md) para conocer el marco de componentes sociales (SCF) y personalizar componentes y características de Comunidades.

* Visite [Creación de componentes](author-communities.md) de comunidades para obtener información sobre cómo crear y configurar componentes de comunidades.

