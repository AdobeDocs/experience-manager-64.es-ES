---
title: Elementos esenciales del panel de control
seo-title: Leaderboard Essentials
description: Información general sobre las características del panel de vanguardia
seo-description: Leaderboard feature overview
uuid: 815a6928-b147-496d-9751-13159ad1304d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7449f99e-77d7-4c0f-96d5-b67d5e1f124a
exl-id: 20c16e96-2ba8-4f2d-8cfa-8cd804e3441f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 10%

---

# Elementos esenciales del panel de control {#leaderboard-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de panel de control.

Antes de incluir el componente de panel de encabezado en una página, es necesario configurar [Puntuación y distintivos de comunidades](implementing-scoring.md). Consulte también [Aspectos básicos de la puntuación y los distintivos](configure-scoring.md).

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/gamificación/componentes/hbs/panel de control</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.gamification.hbs.leaderboard</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="enabling-leaderboard.md">Función de portapapeles</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

### Función Biblioteca del archivo {#file-library-function}

Una estructura de sitio de la comunidad que incluye el [Función del panel de instrumentos](functions.md#leaderboard-function), incluye un `leaderboard` componente.
