---
title: AEM Forms en grupos y privilegios de OSGi
seo-title: AEM Forms on OSGi Groups and Privileges
description: Asignar usuarios a los grupos para administrar AEM Forms en OSGi
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 75%

---

# AEM Forms en grupos y privilegios de OSGi {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Asignar usuarios a los grupos para administrar AEM Forms en OSGi

Puede [crear grupos](/help/sites-administering/user-group-ac-admin.md#group-administration) y asignar políticas y [usuarios](/help/sites-administering/user-group-ac-admin.md#user-administration) a los grupos de AEM. Estas políticas controlan los permisos de los usuarios que forman parte del grupo.

Una vez realizada la instalación [Paquete de complementos de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md), los grupos mencionados en este artículo, como forms-user y forms-power-user, están disponibles automáticamente para su asignación. La siguiente tabla muestra una lista de las tareas que un usuario puede realizar para AEM Forms en OSGi en función de las asignaciones de grupo:

<table> 
 <tbody>
  <tr>
   <td>Grupo</td> 
   <td>Tareas</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Crear, previsualizar, publicar y enviar formularios adaptables</li> 
     <li>Crear, previsualizar y publicar comunicaciones interactivas y fragmentos de documentos</li> 
     <li>Cargar recursos en una instancia de AEM</li> 
     <li>Crear temáticas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>Crear, previsualizar, publicar y enviar formularios adaptables</li> 
     <li>Crear, previsualizar y publicar comunicaciones interactivas y fragmentos de documentos</li> 
     <li>Crear scripts para formularios adaptables mediante el editor de código</li> 
     <li>Cargar recursos, incluidos scripts</li> 
     <li>Crear temáticas</li> 
     <li>Importar paquetes que contengan XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Revisar envíos</li> 
     <li>Aprobar o rechazar envíos</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Crear y previsualizar formularios adaptables o plantillas de comunicaciones interactivas</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Crear y modificar un modelo de datos de formulario</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-user-agent</td> 
   <td>
    <ul> 
     <li>Acceder a cartas de Administración de correspondencia o Interactive Communications mediante la interfaz de usuario del agente</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Crear una aplicación de la bandeja de entrada</li> 
     <li>Crear un modelo del flujo de trabajo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Uso de aplicaciones AEM bandeja de entrada</li> 
     <li>Administrar instancias de flujo de trabajo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Configurar PDF Generator</li> 
     <li>Configurar carpetas inspeccionadas</li> 
     <li>Administrar aplicaciones de flujo de trabajo</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. El usuario con privilegios de grupo de usuarios de formularios no puede escribir secuencias de comandos para formularios adaptables.
1. El usuario con privilegios del grupo de autores de plantillas no puede escribir scripts para plantillas.
