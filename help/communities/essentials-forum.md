---
title: Forum Essentials
seo-title: Forum Essentials
description: Información general del foro
seo-description: Forum overview
uuid: 68849582-8742-40be-9e7e-0b574ae38815
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 059c5bbe-07eb-4873-8157-2196df887b27
exl-id: 6562a440-887e-4a48-a14e-64dc36c70793
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 4%

---

# Forum Essentials {#forum-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de foro.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceTypes</strong></td> 
   <td>social/forum/components/hbs/forum<br /> social/forum/components/hbs/topic<br /> social/forum/components/hbs/post</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.forum</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/forum/components/hbs/forum/forum.hbs<br /> /libs/social/forum/components/hbs/post/post.hbs<br /> /libs/social/forum/components/hbs/topic/topic.hbs<br /> /libs/social/forum/components/hbs/topic/list-item.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/forum/components/hbs/forum/clientlibs/forum.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="forum.md">Función de foro</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de foro](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/forum/client/api/package-summary.html)

* [Puntos finales de foro](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/forum/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Foro {#forum-function}

Una estructura de sitio de la comunidad que incluye el [Función de foro](functions.md#forum-function), incluye un `forum` , así como la configuración que afecta a la moderación, el etiquetado y la traducción.

### Acceso a anuncios de foro (UGC) {#accessing-forum-posts-ugc}

UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir del AEM 6.1 Comunidades, se utilizará un [tienda común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
