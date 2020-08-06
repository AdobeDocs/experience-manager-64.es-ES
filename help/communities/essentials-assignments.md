---
title: Ascripciones esenciales
seo-title: Ascripciones esenciales
description: Descripción general de la función Asignaciones para comunidades de habilitación
seo-description: Descripción general de la función Asignaciones para comunidades de habilitación
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 13%

---


# Ascripciones esenciales {#assignments-essentials}

Esta página proporciona la información esencial para trabajar con la función de asignaciones de [habilitar los sitios de comunidad](overview.md#enablement-community) .

La función de asignaciones es la capacidad de asignar recursos de habilitación y rutas de aprendizaje a miembros de comunidades de habilitación.

## Esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/habilitación/componentes/hbs/miasignados</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.mysigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningPath</td> 
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
   <td>Consulte Función <a href="assignments.md">Asignaciones</a></td> 
  </tr>
 </tbody>
</table>

### Estado de finalización y éxito {#completion-and-success-status}

El estado de Finalización y Éxito se utiliza en los informes, así como en las pancartas de estado de las asignaciones.

Estado de finalización:

* Sin asignar
* No iniciado (nuevo)
* En curso
* Completar

Estado de éxito:

* Desconocido
* Pase
* Error

Las únicas combinaciones posibles de estado de finalización y éxito son:

| **Finalización** | **Correcto** |
|---|---|
| Sin iniciar | Desconocido |
| En curso | Desconocido |
| Completar | Pase |
| Completar | Error |

## Esenciales para servidor {#essentials-for-server-side}

### Función Asignaciones {#assignments-function}

Una estructura de sitio de comunidad que incluye la función [](functions.md#assignments-function)Asignaciones incluye un ` [assignments](assignments.md)` componente configurado.

### API de referencia {#reference-apis}

* [API de habilitación](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API de Sistema de informes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API de Sistema de informes Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)