---
title: AEM Forms en grupos y privilegios OSGi
seo-title: AEM Forms en grupos y privilegios OSGi
description: Asignación de usuarios a los grupos para administrar los formularios AEM en OSGi
seo-description: Asignación de usuarios a los grupos para administrar los formularios AEM en OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
translation-type: tm+mt
source-git-commit: 17f5041c16996ec3f230650451a816c08170837c
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---


# AEM Forms en grupos y privilegios OSGi {#aem-forms-on-osgi-groups-and-privileges}

Asignación de usuarios a los grupos para administrar los formularios AEM en OSGi

Puede [crear grupos](/help/sites-administering/user-group-ac-admin.md#group-administration) y asignar políticas y [usuarios](/help/sites-administering/user-group-ac-admin.md#user-administration) a los grupos en AEM. Estas directivas controlan los privilegios de los usuarios que forman parte del grupo.

Una vez que instale el paquete [de complementos de formularios](/help/forms/using/installing-configuring-aem-forms-osgi.md)AEM, los grupos mencionados en este artículo, como el usuario de formularios y el usuario que puede utilizar formularios, estarán disponibles automáticamente para su asignación. La tabla siguiente lista las tareas que un usuario puede realizar para AEM Forms en OSGi en función de las asignaciones de grupo:

<table> 
 <tbody>
  <tr>
   <td>Agrupar</td> 
   <td>Tareas</td> 
  </tr>
  <tr>
   <td>form-user <sup><a href="#main-pars-text">[1]</a></sup></td> 
   <td>
    <ul> 
     <li>Creación, previsualización, publicación y envío de formularios adaptables</li> 
     <li>Creación, previsualización y publicación de comunicaciones interactivas y fragmentos de documento</li> 
     <li>Carga de recursos en una instancia de AEM</li> 
     <li>Crear temáticas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-user</td> 
   <td>
    <ul> 
     <li>Creación, previsualización, publicación y envío de formularios adaptables</li> 
     <li>Creación, previsualización y publicación de comunicaciones interactivas y fragmentos de documento</li> 
     <li>Creación de secuencias de comandos para formularios adaptables mediante el editor de código</li> 
     <li>Carga de recursos, incluidas secuencias de comandos</li> 
     <li>Crear temáticas</li> 
     <li>Importar paquetes que contengan XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submit-reviewers</td> 
   <td>
    <ul> 
     <li>Revisar envíos</li> 
     <li>Aprobar o rechazar envíos</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>templates-author <sup><a href="#main-pars-text">[2]</a></sup></td> 
   <td>
    <ul> 
     <li>Creación y previsualización de formularios adaptables o plantillas de comunicaciones interactivas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-author</p> </td> 
   <td>
    <ul> 
     <li>Crear y modificar un modelo de datos de formulario</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>Acceso a cartas de Correspondencia o comunicaciones interactivas mediante la interfaz de usuario del agente</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Creación de una aplicación de bandeja de entrada</li> 
     <li>Creación de un modelo de flujo de trabajo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Uso de aplicaciones de bandeja de entrada de AEM</li> 
     <li>Administrar instancias de flujo de trabajo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administradores</td> 
   <td>
    <ul> 
     <li>Configurar generador de PDF</li> 
     <li>Configurar carpeta vigilada</li> 
     <li>Administrar aplicaciones de flujo de trabajo</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. El usuario con privilegios de grupo de usuarios de formularios no puede escribir secuencias de comandos para formularios adaptables.
1. El usuario con privilegios de grupo de autores de plantillas no puede escribir secuencias de comandos para plantillas.

