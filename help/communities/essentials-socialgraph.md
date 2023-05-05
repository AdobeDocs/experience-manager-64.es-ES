---
title: Social Graph Essentials
seo-title: Social Graph Essentials
description: información general sobre el componente siguiente
seo-description: follow component and following component overview
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 5%

---

# Social Graph Essentials {#social-graph-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La capacidad de un miembro de la Comunidad de seguir [actividades](essentials-activities.md) además de ser seguido, se establece mediante dos componentes:

La variable `follow`debe asociarse con otro recurso y esta asociación ya está establecida para los miembros de Communities y las funciones de una [sitio de la comunidad](overview.md#communitiessites).

La variable `following`en el componente se enumeran los miembros que siguen al miembro actual o al miembro actual. Este gráfico social de las relaciones entre los miembros se incluye en el perfil de usuario establecido para un sitio de comunidad.

## Elementos esenciales para el cliente {#essentials-for-client-side}

### Siguiente {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>gráfico social/social/componentes/hbs/relaciones</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="socialgraph.md">Uso del gráfico social</a></td> 
  </tr>
  <tr>
   <td><strong> opcional<br /> property</strong></td> 
   <td>
    <ul> 
     <li>Nombre: <strong><code>outgoing</code></strong></li> 
     <li>Tipo: Booleano</li> 
     <li>Valor:<br /> 
      <ul> 
       <li><i>true </i>- el <code>following</code> presentará una lista de los miembros que son el miembro que ha iniciado sesión en ese momento <code>follows</code></li> 
       <li><i>false </i>- el <code>following</code> enumerará los miembros que <code>follow </code>el miembro con sesión iniciada actualmente</li> 
      </ul> </li> 
    </ul> <p>El valor predeterminado es <i>true</i> si falta la propiedad. Actualmente, no es posible establecer esta propiedad mediante el cuadro de diálogo de edición en modo de autor. La propiedad debe agregarse a una instancia de la variable <code>following </code>nodo que utiliza <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### Seguir {#follow}

| **resourceType** | social/socialgraph/components/hbs/following |
|---|---|
| [**inclusible**](scf.md#add-or-include-a-communities-component) | No |
| **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de gráfico social](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Puntos finales de gráfico social](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Personalizaciones del lado del servidor](server-customize.md)
