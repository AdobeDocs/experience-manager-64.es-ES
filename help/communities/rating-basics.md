---
title: Clasificaciones esenciales
seo-title: Clasificaciones esenciales
description: Descripción general del componente Clasificación
seo-description: Descripción general del componente Clasificación
uuid: 48ef61ad-be7a-4a6b-a284-23e5bb4f1671
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7dc3ef57-05c3-45d4-ace3-bb3ba6ea768b
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 1%

---


# Elementos esenciales de clasificación {#rating-essentials}

El componente de clasificación, una subclase [tally](tally.md), permite a los miembros de la comunidad que inicien sesión clasificar una función en el sitio web.

Se permite colocar varias instancias de un componente de votación en la misma página; cada instancia debe configurarse con una propiedad `tally name` única.

No se admite la publicación anónima de una clasificación. Los visitantes del sitio deben registrarse e iniciar sesión para participar en una clasificación solo una vez. El visitante firmado (miembro) puede cambiar su calificación en cualquier momento.

## Esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td> social/tally/componentes/hbs/clasificación</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>Sí: las propiedades se pueden editar en el modo <i>de diseño </i></td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.rating</td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>propiedades</strong></td> 
   <td><p>Consulte <a href="rating.md">Uso de Clasificación</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Esenciales para servidor {#essentials-for-server-side}

* [API de Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Extremos de recuento](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Acceso a clasificaciones contabilizadas (UGC) {#accessing-posted-ratings-ugc}

La UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir de AEM comunidades 6.1, el uso de un [almacén común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Descripción general](srp.md)  del proveedor de recursos de almacenamiento: introducción y uso del repositorio
* [Elementos esenciales](srp-and-ugc.md)  de SRP y UGC: métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) : directrices de codificación
* [Refactorización](socialutils.md)  de SocialUtils: asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales

