---
title: Componentes, funciones y características esenciales
seo-title: Component, Function and Feature Essentials
description: Función de los sitios, plantillas y grupos de la comunidad
seo-description: How community sites, templates, and groups function
uuid: 6edfca2d-fe5b-4261-b033-51dc2f9dbfd7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 2d308756-79d1-4d69-b51c-d4b6e692a137
exl-id: bde29d3a-8bc8-4c30-b764-a2fa1ac34069
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 18%

---

# Componentes, funciones y características esenciales {#component-function-and-feature-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las funciones de AEM Communities requieren que los visitantes del sitio se conviertan en miembros e inicien sesión en el [sitio de la comunidad](overview.md#communitiessites) antes de poder publicar contenido. Así, [plantillas de sitio de la comunidad](sites.md), desde el cual se encuentra un sitio de comunidad [created](sites-console.md), están diseñados para incluir una función de inicio de sesión, así como perfiles de usuario, mensajes, búsquedas, moderación y traducción.

Un sitio de la comunidad ayudará a los miembros a crear grupos de la comunidad cuando [función de grupos de comunidades](functions.md#groups-function) se incluye en la plantilla de sitio de la comunidad seleccionada.

A continuación se muestran vínculos a información esencial para componentes, funciones y características de Communities.

## Componentes básicos {#base-components}

* [Comentarios](essentials-comments.md)
* [Repasos](reviews-basics.md)
* [Tally](tally.md)

   * [Me está gustando](essentials-liking.md)
   * [Clasificación](rating-basics.md)
   * [Votación](essentials-voting.md)
   * *Encuesta (ya no está disponible)*

## Componentes con funciones {#components-with-functions}

* [Flujos de actividad](essentials-activities.md)
* [Asignaciones](essentials-assignments.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Calendario](calendar-basics-for-developers.md)
* [Catálogo](catalog-developer-essentials.md)
* [Contenido destacado](essentials-featured.md)
* [Biblioteca de archivos](essentials-file-library.md)
* [Foro](essentials-forum.md)
* [Grupos](essentials-groups.md)
* [Ideación](ideation.md)
* [Tabla de clasificación](leaderboard.md)
* [Preguntas y respuestas](qna-essentials.md) `(QnA)`

## Características {#features}

* [Bibliotecas de cliente](clientlibs.md)
* [Sitios de la comunidad](sites-for-developers.md)
* [Eventos OSGi de componentes](events.md)
* [Carga de componentes](sideloading.md)
* [Mensajes](essentials-messaging.md)
* [Editor de texto enriquecido](rte.md)
* [Puntuación y distintivos](configure-scoring.md)
* [Búsqueda](search-implementation.md)
* [Gráfico social](essentials-socialgraph.md)
* [Proveedor de recursos de almacenamiento](srp-and-ugc.md) `(SRP)`

* [Etiquetado](tag.md)

## Javadocs {#javadocs}

La variable [javadocs en línea](../../help/sites-developing/reference-materials.md) reflejan las API disponibles en la versión AEM 6.3.\
Las API de Communities están en `com.adobe.cq.social.*` paquetes.

Para cada [paquete de características](deploy-communities.md#latestfeaturepack), hay disponible un jar javadoc. Para obtener más información, visite [Uso de Maven para comunidades](maven.md#javadocs).

## Información adicional {#additional-information}

* [Marco de componentes sociales (SCF)](scf.md)

   * [Personalizaciones del lado del cliente](client-customize.md)
   * [Personalizaciones del lado del servidor](server-customize.md)
   * [Información general del proveedor de recursos de almacenamiento](srp.md)

* [Directrices de codificación](code-guide.md)
* [Tutoriales](tutorials.md)
* [Solución de problemas](troubleshooting.md)
