---
title: Aspectos básicos de la idea
seo-title: Ideation Essentials
description: Información general sobre la función de ideación
seo-description: Ideation feature overview
uuid: abaf03ee-8bf4-4241-96c3-474c95a30a88
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9e4f2f0-d1ff-40c0-abcf-645e40586a84
exl-id: 7fb68293-c6e3-4793-b433-205bcfc23e20
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 9%

---

# Aspectos básicos de la idea {#ideation-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de ideación, que es similar a un foro, pero con la capacidad de guardar como borrador y con una sensación más colaborativa.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ideation/components/hbs/ideation</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.vote<br /> cq.social.hbs.like<br /> cq.social.hbs.ideation</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/ideation.hbs<br /> /libs/social/ideation/components/hbs/ideation/ideationlists.hbs<br /> /libs/social/ideation/components/hbs/ideation/composer.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/clientlibs/ideation.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="ideation-feature.md">Función de ideación</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

### Función ideación {#ideation-function}

Una estructura de sitio de la comunidad que incluye el [Función de ideación](functions.md#ideation-function), incluye un `ideation` componente.
