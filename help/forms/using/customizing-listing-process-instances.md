---
title: Personalizar la lista de instancias de proceso
seo-title: Customizing the listing of process instances
description: Personalizar las propiedades mostradas en la instancia de proceso en AEM Forms Workspace.
seo-description: How-to customize the properties displayed in process instance in AEM Forms workspace.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
exl-id: e7b8206c-bac2-48a6-b353-d06bc73b29f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 91%

---

# Personalizar la lista de instancias de proceso {#customizing-the-listing-of-process-instances}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La lista de instancias de proceso se muestra en la pestaña Seguimiento de AEM Forms Workspace.

En la lista de instancias de proceso, para cada instancia de proceso, AEM Forms Workspace muestra algunas propiedades. Las siguientes propiedades están disponibles para cada instancia de proceso. Estas propiedades se almacenan como atributos en el modelo de componentes de instancias de proceso y están disponibles para usarlas en su vista y plantilla.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propiedad</strong></td> 
   <td><strong>Comentarios</strong></td> 
  </tr> 
  <tr> 
   <td>description</td> 
   <td>Descripción de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>initiator</td> 
   <td>Nombre del iniciador de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>ID del iniciador de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>Marca de hora de cuando se completó el proceso.</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>ID de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 = Iniciado<br /> 1 = En ejecución<br /> 2 = Completo<br /> 3 = Finalizado<br /> 4 = Terminado<br /> 5 = Finalización<br /> 6 = Suspendido<br /> 7 = Suspender<br /> 8 = Sin suspensión</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>Nombre del proceso.</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>Marca de tiempo de cuando se inició el proceso.</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>La matriz de objetos de variables de proceso. Cada objeto de variable de proceso contiene <strong>name</strong> (el nombre de la variable de proceso), <strong>value</strong> (valor de la variable de proceso) y<strong> type</strong> (el tipo de variable de proceso).</td> 
  </tr> 
 </tbody> 
</table>

**Ejemplo:**

Para mostrar la propiedad `description` de la instancia de proceso en la tarjeta Instancia de proceso, realice los siguientes pasos.

1. Siga los [Pasos genéricos para personalizar AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Haga lo siguiente:

   1. Copie /libs/ws/js/runtime/templates/processinstance.html a/apps/ws/js/runtime/templates/, si no existe. Haga clic en **Guardar todo**.
   1. Agregue un div de descripción del proceso con class = &#39;processDescription&#39; inprocessinstance.html.

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Haga lo siguiente:

   1. Abra /apps/ws/js/registry.js para editarlo.
   1. Busque y reemplace `text!/lc/libs/ws/js/runtime/templates/processinstance.html` con `text!/lc/`**apps**/ws/js/runtime/templates/processinstance.html.

1. Los cambios anteriores pueden requerir una actualización del archivo CSS al agregar una entrada en la hoja de estilo /apps/ws/css/newStyle.css de la siguiente manera:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
