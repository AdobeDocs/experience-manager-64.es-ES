---
title: Información general de AEM Communities
seo-title: AEM Communities Overview
description: Información general sobre las funciones y la configuración de AEM Communities
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---

# Información general de AEM Communities {#aem-communities-overview}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las comunidades de Adobe Experience Manager (AEM) ofrecen la capacidad de crear rápidamente un sitio de comunidad local que tenga un rendimiento mejorado, una administración del sitio mejorada y que fomente la conversión de los visitantes del sitio a miembros valiosos de la comunidad.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Funciones de Communities {#communities-features}

AEM Communities permite el desarrollo de una relación con los visitantes del sitio que informan a través de blogs, preguntas y respuestas y calendarios de eventos, a la vez que obtiene perspectivas a través de foros, comentarios y otro contenido de la comunidad, a menudo denominado contenido generado por el usuario (UGC).

Además, AEM Communities permite la moderación por parte de miembros de confianza en el entorno de publicación, el inicio de sesión social con Twitter y Facebook, la traducción en línea del contenido de la comunidad, la creación de grupos de la comunidad desde el sitio de la comunidad publicado, la puntuación para asignar distintivos, el uso compartido de archivos, las notificaciones y los flujos de actividades.

Las características de las comunidades se pueden mostrar utilizando la variable [AEM de demostración](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible públicamente en GitHub.com o con la nueva implementación de referencia de We.Retail.

## Sitios de la comunidad {#community-sites}

Un sitio de comunidad es un sitio AEM creado con un simple asistente que resulta en un sitio web con muchas funciones comunes preprogramadas en el sitio.

La variable [asistente de creación de sitios](sites-console.md):

* Ensamble las características del sitio, según la selección [plantilla del sitio de la comunidad](sites.md) que es
   * Integrado desde [funciones de la comunidad](#community-functions)
   * Opcional [grupos de la comunidad](#communitygroups) función
* Utiliza la configuración para configurar:
   * Moderación
   * Inicio de sesión
   * Traducción
* Proporciona características esenciales:
   * Diseño interactivo: Usos [Temas del Bootstrap de twitter](https://getbootstrap.com)
   * Inicio de sesión: Autoregistro, [inicio de sesión social](social-login.md), perfiles de usuario
   * Notificaciones: Los miembros ven acontecimientos importantes para ellos
   * Mensajería: Los miembros podrán enviar o recibir mensajes dentro del sitio de la comunidad
   * Buscar: Capacidad de buscar dentro del sitio de la comunidad
   * Cambio de idioma: Posibilidad de seleccionar un idioma para un [sitio multilingüe](../../help/sites-administering/translation.md)
   * Administración: Acceso para miembros autorizados para moderar y administrar usuarios dentro del sitio de la comunidad
* Elimina muchos pasos de creación a nivel de página:
   * Marcas: Carga opcional de una imagen de banner para mostrarla en todas las páginas del sitio de la comunidad
   * Menú de navegación: Se proporcionan vínculos de navegación para las funciones incluidas en la plantilla del sitio de la comunidad

Para experimentar la facilidad de crear rápidamente un nuevo sitio de comunidad, visite [Introducción a AEM Communities](getting-started.md).

## Persistencia de contenido de la comunidad {#community-content-persistence}

Para mejorar el rendimiento y la sincronización del contenido de la comunidad, AEM Communities requiere un almacén común específico para el contenido generado por el usuario (UGC) compartido entre todas las instancias de AEM (autor y publicación).

Se puede acceder fácilmente al contenido de la comunidad a través del proveedor de recursos de almacenamiento (SRP), que proporciona una capa para separar el acceso de la topología subyacente y soporta un almacén común para UGC.

Para obtener más información sobre la persistencia del contenido de la comunidad y las implementaciones recomendadas, visite:

* [Almacenamiento de contenido de la comunidad](working-with-srp.md): analiza las opciones de almacenamiento SRP disponibles para UGC
* [Topologías recomendadas](topologies.md): discute topologías basadas en casos de uso y elección de SRP
* [Actualización a AEM 6.3 Communities](upgrade.md): proporciona información útil sobre UGC al pasar a AEM 6.3.

## Consolas de comunidades {#communities-consoles}

En el entorno de creación, la consola de navegación global proporciona acceso al [Consola Comunidades](consoles.md), que contiene:

* consola [Sitios](sites-console.md)

   * Creación de sitios
   * Edición del sitio
   * Administración del sitio
   * [Grupos de la comunidad](groups.md) consola

* [Moderación](moderation.md) consola

   * Interfaz de usuario de moderación masiva común para entornos de creación y publicación
   * Nuevos criterios de filtrado

* [Miembros y grupos](members.md) consolas de administración

   * Proporciona la capacidad de crear y administrar usuarios del lado de publicación (miembros) desde el entorno de creación
   * Permite prohibir miembros
   * Proporciona la capacidad de crear y administrar grupos de usuarios del lado de publicación (grupos de miembros) desde el entorno de creación

* [Informes](reports.md) consola

   * Permite generar informes sobre asignaciones, publicaciones y vistas

* [Recursos](resources.md) consola

   * Proporciona la capacidad de crear recursos de habilitación y rutas de aprendizaje
   * Proporciona acceso a informes sobre recursos de habilitación y rutas de aprendizaje

La consola de herramientas globales proporciona acceso a las siguientes herramientas de Communities:

* [Plantillas de sitio](tools.md#sitetemplatesconsole) consola

   * Crear y administrar plantillas de sitio de la comunidad

* [Plantillas de grupo](tools.md#grouptemplatesconsole) consola

   * Crear y administrar plantillas de grupos de la comunidad

* [Funciones de la comunidad](tools.md#communityfunctionsconsole) consola

   * Crear y administrar funciones de la comunidad

* [Configuración de almacenamiento](tools.md#storageconfiguratonconsole) consola

   * Seleccione y configure el [tienda común](working-with-srp.md) para el sitio

* [Guía de componentes](components-guide.md)

   * Un sitio de muestra, [Componentes de comunidad](http://localhost:4502/editor.html/content/community-components/en.html), que proporciona un ejemplo de todos los componentes de Communities con su configuración predeterminada y la capacidad de experimentar con ellos

## Plantillas de sitio de la comunidad {#community-site-templates}

La creación del sitio de la comunidad se basa en la selección de una plantilla del sitio de la comunidad para configurar rápidamente un sitio de la comunidad que sea independiente de cualquier sitio de muestra.

Una plantilla de sitio de la comunidad, compuesta de funciones de la comunidad y plantillas de grupos de la comunidad, proporciona la estructura de un sitio de la comunidad, que incluye: inicio de sesión, perfiles de usuario, mensajería, menú del sitio, búsqueda, tema y funciones de marca.

Consulte la [Consola Plantillas de sitio](sites.md).

## Funciones de la comunidad {#community-functions}

Las características que se esperan de una experiencia comunitaria son bien conocidas. Con AEM Communities, estas funciones están disponibles como componentes básicos, conocidos como funciones de la comunidad.

Las funciones de comunidad son páginas AEM normales compuestas por componentes conectados en una función que se incorpora fácilmente en una plantilla de sitio de somity.

Consulte la [Consola de funciones de comunidad](functions.md).

## Grupos de la comunidad y plantillas de grupo {#community-groups-and-group-templates}

La función de grupos de comunidad es la capacidad de los usuarios autorizados y los miembros de la comunidad de crear dinámicamente una subcomunidad dentro de un sitio de comunidad desde los entornos de autor y publicación .

Desde el entorno de creación, se pueden crear grupos de comunidad (subcomunidades) dentro de un sitio de comunidad existente o anidados dentro de un grupo existente, cuando la estructura de la plantilla contiene la variable [Función de grupos](functions.md#groups-function).

La creación de un grupo de comunidad requiere la selección de una plantilla de grupo de comunidad que proporcione el diseño de las páginas de grupo de la comunidad. Cuando se agrega una función Grupos a una estructura de plantilla, se configura para especificar una plantilla de grupo o para proporcionar una selección de plantillas al crear un nuevo grupo de comunidad.

Consulte también lo siguiente:

* [Consola Grupos de sitios](groups.md) - crear subcomunidades en el entorno de creación
* [Consola Plantillas de grupo](tools-groups.md) - crear estructura de sitio para grupos
* [Introducción a AEM Communities](getting-started.md) : tutorial para crear rápidamente un sitio de comunidad que incluya grupos anidados

## Componentes de comunidad {#community-components}

La variable [componentes de la comunidad](author-communities.md) desde el cual se crea un sitio de comunidad puede utilizarse para agregar características de Communities a cualquier sitio AEM.

La variable [guía de componentes de comunidad](components-guide.md) está disponible para la exploración interactiva de los componentes.

## Tipos de comunidades {#types-of-communities}

### Comunidad de participación {#engagement-community}

Una comunidad de participación es un sitio de la comunidad que se centra en atraer clientes para que informen, soliciten comentarios y permitan a los clientes interactuar como miembros de la comunidad.

Las características de una comunidad de participación pueden incluir:

* Inicio de sesión
* Mensajes
* Foros
* Comentarios
* Repasos
* Clasificaciones
* Votación
* Blogs
* Grupos
* Calendarios
* Traducción
* Moderación
* Notificaciones
* Puntuación y distintivos
* Informes de Analytics

Para experimentar la facilidad de crear rápidamente una nueva comunidad de participación, visite [Introducción a AEM Communities](getting-started.md).

### Comunidad de habilitación {#enablement-community}

Una comunidad de habilitación es un sitio de la comunidad que incluye características para el aprendizaje en línea.

Las características de una comunidad de habilitación pueden incluir:

* Todas las características de un [comunidad de participación](#engagement-community)
* Capacidad para asignar contenido y recursos de aprendizaje a miembros y grupos de miembros
* Admite contenido SCORM, como cuestionarios y pruebas
* Seguimiento de la finalización de asignaciones
* Acceso a informes y análisis
* La capacidad de tener una conversación sobre un recurso de aprendizaje a través de foros, mensajes, comentarios y clasificaciones

Se puede crear una comunidad de habilitación cuando el [El complemento de habilitación está configurado](enablement.md), que requiere licencias adicionales para su uso en un entorno de producción. Un sitio de la comunidad de habilitación incluirá el [asignar, función](#community-functions).

Para experimentar la facilidad de crear una nueva comunidad de habilitación, visite [Introducción a AEM Communities para la activación](getting-started-enablement.md).

## AEM de demostración {#aem-demo-machine}

La variable [AEM de demostración](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) administra y ejecuta demostraciones para AEM [Sitios](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Recursos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Comunidades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Aplicaciones](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) y [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), que a menudo requieren más configuración que simplemente iniciar una instancia de QuickStart. El equipo de demostración de AEM configurará más [infraestructura](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) como MongoDB, Solr, MySQL, FFmpeg y servidores de correo electrónico.

La AEM de demostración está formada por

* A [interfaz gráfica de usuario](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Secuencias de comandos de Apache ANT con configuración [propiedades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) y [targets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Paquetes para instalar AEM Demo Machine se probó correctamente con CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 y AEM 6.3 en Windows, MacOS y Linux.

AEM Demo Machine requiere una licencia de AEM válida.

>[!NOTE]
>
>Ver un [introducción de vídeo](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) a la máquina de demostración de AEM (13:26).

## Documentación de AEM Communities {#aem-communities-documentation}

* Visita [Implementación de comunidades](deploy-communities.md) para obtener más información sobre las implementaciones recomendadas.

* Visita [Administración de sitios de comunidades](administer-landing.md) para obtener información sobre la creación de un sitio de comunidad, la adición de grupos de comunidad, la configuración de plantillas de sitio de comunidad, la moderación del contenido de la comunidad, la administración de miembros, el etiquetado, las notificaciones, la puntuación y los distintivos.

* Visita [Desarrollo de comunidades](communities.md) para obtener información sobre el marco de componentes sociales (SCF) y la personalización de componentes y funciones de Communities.

* Visita [Creación de componentes de Communities](author-communities.md) para aprender a crear con y configurar componentes de Communities.
