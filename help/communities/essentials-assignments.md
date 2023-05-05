---
title: Ascripciones esenciales
seo-title: Assignments Essentials
description: Información general sobre la función Asignaciones para comunidades de habilitación
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 14%

---

# Ascripciones esenciales {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de asignaciones de [comunidad de habilitación](overview.md#enablement-community) sitios web.

La función de asignaciones es la capacidad de asignar recursos de habilitación y rutas de aprendizaje a miembros de comunidades de habilitación.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/habilitación/componentes/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learn.path</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="assignments.md">Función de asignaciones</a></td> 
  </tr>
 </tbody>
</table>

### Estado de finalización y éxito {#completion-and-success-status}

El estado de Finalización y Éxito se utiliza en los informes, así como en los banners de estado en Asignaciones.

Estado de finalización:

* Sin asignar
* No iniciado (nuevo)
* En curso
* Completar

Estado de éxito:

* Desconocido
* Pase
* Error

Las únicas combinaciones posibles de Estado de finalización y éxito son:

| **Finalización** | **Correcto** |
|---|---|
| Sin iniciar | Desconocido |
| En curso | Desconocido |
| Completar | Pase |
| Completar | Error |

## Elementos esenciales para el servidor {#essentials-for-server-side}

### Función Asignaciones {#assignments-function}

Una estructura de sitio de la comunidad que incluye el [Función Asignaciones](functions.md#assignments-function), incluye un ` [assignments](assignments.md)` componente.

### API de referencia {#reference-apis}

* [API de habilitación](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API de informes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API de informes de Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
