---
title: '"Me gusta" de Essentials'
seo-title: Liking Essentials
description: Descripción general del componente "Me gusta"
seo-description: Liking component overview
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
exl-id: 509d1fb4-a88d-4438-a618-ba063adb6fb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 3%

---

# &quot;Me gusta&quot; de Essentials {#liking-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El componente &quot;Me gusta&quot;, un [tally](tally.md) subclase, es una herramienta útil que permite a los miembros expresar una opinión positiva sobre un contenido en particular simplemente seleccionando el icono del corazón.

Se permite colocar varias instancias de un componente de &quot;Me gusta&quot; en la misma página; cada instancia debe configurarse con un `tally name` propiedad.

No se admite la publicación anónima de un Me gusta. Los visitantes del sitio deben registrarse e iniciar sesión para participar en el &quot;Me gusta&quot;. El visitante (miembro) que ha iniciado sesión puede activarse y desactivarse en cualquier momento.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/componentes/hbs/Me gusta</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>Sí: las propiedades se pueden editar en <i>diseño </i>mode</td> 
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

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Puntos finales totales](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Acceso al voto publicado (UGC) {#accessing-posted-voting-ugc}

UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir del AEM 6.1 Comunidades, se utilizará un [tienda común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
