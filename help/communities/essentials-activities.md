---
title: Aspectos básicos del flujo de actividad
seo-title: Activity Stream Essentials
description: Lista de actividades recientes realizadas por un miembro o lista de actividades recientes en un único subproceso de contenido
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# Aspectos básicos del flujo de actividad {#activity-stream-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las actividades de un miembro de la comunidad que ha firmado, como la publicación en un foro o blog, se recopilan en un flujo que puede filtrarse y mostrarse de varias formas a través de la configuración del componente de flujos de actividad.

La capacidad de seguir agrega otro conjunto de actividades cuando los miembros de la comunidad siguen publicaciones de interés u otros miembros de la comunidad.

Todo [sitios de la comunidad](overview.md#communitiessites) incluya una página de perfil de usuario para el miembro que ha iniciado sesión que mostrará las actividades de miembro de la misma manera.

## Conceptos  {#concepts}

Un *flujo de actividad* es la lista de actividades recientes realizadas por un miembro o una lista de actividades recientes en un único subproceso de contenido, como un tema de foro o un blog.

Un miembro puede seguir un flujo de actividad siguiendo a otro individuo o contenido.

A *fuente de noticias* es una combinación de los flujos de actividad seguida por un miembro en un único flujo.

A [gráfico social](essentials-socialgraph.md) captura las siguientes relaciones de un miembro a otro.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/flujos de actividad/componentes/hbs/flujos de actividad</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="activities.md">Función Flujos de actividad</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de flujos de actividad](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API de escucha de flujos de actividad](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Secuencia de actividades {#activity-stream-function}

Una estructura de sitio de la comunidad que incluye el [Función del flujo de actividad](functions.md#activity-stream-function), incluye un `activity streams` componente.
