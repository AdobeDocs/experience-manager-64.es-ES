---
title: Aspectos básicos de "Me gusta"
seo-title: Aspectos básicos de "Me gusta"
description: Descripción general del componente "Me gusta"
seo-description: Descripción general del componente "Me gusta"
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---


# Aspectos esenciales de &quot;Me gusta&quot; {#liking-essentials}

El componente &quot;Me gusta&quot;, una subclase [tally](tally.md), es una herramienta útil que permite a los miembros expresar una opinión positiva sobre un contenido determinado simplemente seleccionando el icono del corazón.

Se permite colocar varias instancias de un componente de &quot;Me gusta&quot; en la misma página; cada instancia debe configurarse con una propiedad `tally name` única.

No se admite la publicación anónima de un &quot;Me gusta&quot;. Los visitantes del sitio deben registrarse e iniciar sesión para participar en el &quot;Me gusta&quot;. El visitante firmado (miembro) puede activarse y desactivarse en cualquier momento.

## Esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/componentes/hbs/Me gusta</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>Sí: las propiedades se pueden editar en el modo <i>de diseño </i></td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.liking</td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>propiedades</strong></td> 
   <td><p>Consulte <a href="liking.md">Uso de "Me gusta"</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Esenciales para servidor {#essentials-for-server-side}

* [API de Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Extremos de recuento](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Acceso a Votación posteada (UGC) {#accessing-posted-voting-ugc}

La UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir de AEM comunidades 6.1, el uso de un [almacén común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Descripción general](srp.md)  del proveedor de recursos de almacenamiento: introducción y uso del repositorio
* [Elementos esenciales](srp-and-ugc.md)  de SRP y UGC: métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) : directrices de codificación
* [Refactorización](socialutils.md)  de SocialUtils: asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales

