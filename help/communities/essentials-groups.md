---
title: Elementos esenciales del grupo de la comunidad
seo-title: Elementos esenciales del grupo de la comunidad
description: Creación dinámica de sitios de comunidad
seo-description: Creación dinámica de sitios de comunidad
uuid: 168e7aeb-6e9a-468d-8ac4-274007cea252
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4f85cd3c-5158-4f23-abe2-7e375fd0c8d4
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---


# Community Group Essentials {#community-group-essentials}

La función de grupos de comunidad es la capacidad para que una subcomunidad sea creada dinámicamente dentro de un sitio de comunidad por usuarios autorizados desde los entornos de publicación y creación.

A partir del paquete de funciones 1](deploy-communities.md#latestfeaturepack) de Communities [es posible que los grupos se aniden dentro de otros grupos

## Esenciales para el cliente {#essentials-for-client-side}

### Lista de miembros de grupos de la comunidad {#community-groups-member-list}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/group/components/hbs/communitygroupmemberlist</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.communitygroups</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/communitygroupmemberlist.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/memberList.css</td> 
  </tr>
  <tr>
   <td><strong>propiedades</strong></td> 
   <td>Consulte <a href="creating-groups.md">Grupo de la comunidad</a></td> 
  </tr>
 </tbody>
</table>

### Grupos de la comunidad {#community-groups}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/group/components/hbs/communitygroups</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.communitygroups</td> 
  </tr>
  <tr>
   <td> <strong>plantillas</strong></td> 
   <td> /libs/social/group/components/hbs/communitygroups/communitygroups.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/communitygroups.css</td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Esenciales para servidor {#essentials-for-server-side}

* [API de grupo de comunidad](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Extremos de grupo de la comunidad](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Grupos {#groups-function}

Una estructura de sitio de comunidad que incluye una [función de grupos](functions.md#groups-function) admitirá la creación de nuevos `community groups` desde los entornos de publicación y creación. El grupo de comunidad creado incluirá un componente `community groups member list` que lista a los miembros del grupo.

Una o más [plantillas de grupo de comunidad](tools-groups.md), que proporcionan el diseño de las páginas de grupo de comunidad, pueden configurarse para la función Grupos cuando la función se agrega a una [plantilla de sitio de comunidad](sites.md) o se anida dentro de una plantilla de grupo de comunidad.

La inclusión de varias plantillas de grupo de comunidad da como resultado que se presente una opción de diseño al usuario autorizado en el momento en que se crea un nuevo grupo de comunidad para el sitio de comunidad, como se muestra en la sección sobre [grupos de comunidad](creating-groups.md) para autores.

### Grupos anidados {#nested-groups}

En el caso de Communities [FP1](deploy-communities.md#latestfeaturepack), es posible incluir una función Groups en una plantilla de grupo, permitiendo así que los grupos anidados (subcomunidades).

Cuando una plantilla de grupo o sitio de comunidad incluye la función Grupos, es posible

* Crear una subcomunidad en el entorno de creación
* Cree un grupo en el entorno de publicación, cuando esté configurado para permitirlo

Al crear un grupo en el entorno de creación, primero es necesario publicar el sitio de comunidad y, a continuación, publicar el grupo. Al publicar el sitio de la comunidad se publicarán las páginas del grupo sin crear los grupos de miembros de la subcomunidad en los que se configuran las ACL. Por lo tanto, un grupo restringido (secreto) puede ser visible hasta que se publique explícitamente el grupo.

## Vínculos e información relacionada {#links-and-related-information}

* [Administración de usuarios y grupos de usuarios](users.md)
* [Consola Grupos de comunidades](groups.md)
* [Función Grupos](functions.md#groups-function)
* [Plantillas de grupos](tools-groups.md)

