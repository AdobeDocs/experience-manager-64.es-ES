---
title: Aspectos básicos de las revisiones
seo-title: Reviews Essentials
description: Revisiones y revisión de componentes de resumen
seo-description: Reviews and Review Summary components
uuid: 540c106e-ee3b-4261-82b2-a909d254dbf7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 62669a9d-2107-4644-a4bf-143d0ac148b3
exl-id: ddd2bd98-b375-4d1e-b9d1-5efc3dbca398
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 4%

---

# Aspectos básicos de las revisiones {#reviews-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta función consta de dos componentes que funcionan juntos: revisiones y resumen de revisión.

Las revisiones son un componente compuesto basado en un [sistema de comentarios](essentials-comments.md) que contiene uno o más [clasificación](rating-basics.md) (recuento).

No se admite la publicación anónima de una revisión. Los visitantes del sitio deben registrarse e iniciar sesión para agregar una revisión. El visitante (miembro) que haya iniciado sesión puede actualizar su revisión en cualquier momento.

## Elementos esenciales para el cliente {#essentials-for-client-side}

### Repasos {#reviews}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/reseñas/componentes/hbs/reseñas</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>Sí: las propiedades se pueden editar en <i>diseño </i>mode</td> 
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.reviews</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td> 
  </tr>
  <tr>
   <td><strong>propiedades</strong></td> 
   <td>Consulte <a href="reviews.md">Uso de revisiones</a></td> 
  </tr>
 </tbody>
</table>

### Resumen de críticas {#review-summary}

| **resourceType** | social/reseñas/componentes/hbs/resumen |
|---|---|
| [**inclusible**](scf.md#add-or-include-a-communities-component) | Sí: las propiedades se pueden editar en *diseño *modo |
| [**clientllibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **templates** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **propiedades** | Consulte [Uso de revisiones](reviews.md) |

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [Revisar API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Revisar extremos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Acceso a revisiones publicadas (UGC) {#accessing-posted-reviews-ugc}

UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir del AEM 6.1 Comunidades, se utilizará un [tienda común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
