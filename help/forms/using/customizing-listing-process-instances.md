---
title: Personalización de la lista de instancias de proceso
seo-title: Personalización de la lista de instancias de proceso
description: Cómo personalizar las propiedades que se muestran en la instancia de proceso en el espacio de trabajo de AEM Forms.
seo-description: Cómo personalizar las propiedades que se muestran en la instancia de proceso en el espacio de trabajo de AEM Forms.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---


# Personalización de la lista de instancias de proceso {#customizing-the-listing-of-process-instances}

La lista de la instancia de proceso se muestra en la ficha Seguimiento del espacio de trabajo de AEM Forms.

En la lista de instancias de proceso, para cada instancia de proceso, el espacio de trabajo de AEM Forms muestra algunas propiedades de esa instancia. Las siguientes propiedades están disponibles para cada instancia de proceso. Estas propiedades se almacenan como atributos en el modelo de componentes de instancia de proceso y están disponibles para su uso en su vista y plantilla.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propiedad</strong></td> 
   <td><strong>Comentarios</strong></td> 
  </tr> 
  <tr> 
   <td>Descripción</td> 
   <td>Descripción de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>iniciador</td> 
   <td>Nombre del iniciador de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>ID del iniciador de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>Marca de hora cuando se completó el proceso.</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>ID de la instancia de proceso.</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 = Iniciado<br /> 1 = Ejecutando<br /> 2 = Completado<br /> 3 = Finalizando<br /> 4 = Terminado<br /> 5 = Terminando<br /> 6 = Suspendido<br /> 7 = Suspendiendo<br /> 8 = Sin suspender</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>Nombre del proceso.</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>Marca de hora cuando se inició el proceso.</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>Matriz de objetos de variables de proceso. Cada objeto de variable de proceso contiene <strong>nombre</strong> (el nombre de la variable de proceso), <strong>valor</strong> (valor de la variable de proceso) y<strong> tipo</strong> (el tipo de variable de proceso).</td> 
  </tr> 
 </tbody> 
</table>

**Ejemplo:**

Para mostrar la propiedad `description` de la instancia de proceso en la tarjeta de instancia de proceso, lleve a cabo los siguientes pasos.

1. Siga los [pasos genéricos para la personalización del espacio de trabajo de AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Haga lo siguiente:

   1. Copie /libs/ws/js/runtime/templates/processinstance.html a/apps/ws/js/Runtime/templates/, si no existe. Haga clic en **Guardar todo**.
   1. Añada div de descripción del proceso con class = &#39;processDescription&#39; inprocessinstance.html.

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Haga lo siguiente:

   1. Abra /apps/ws/js/registry.js para editar.
   1. Busque y reemplace `text!/lc/libs/ws/js/runtime/templates/processinstance.html`por `text!/lc/`**aplicaciones**/ws/js/runtime/templates/processinstance.html.

1. Los cambios anteriores pueden requerir una actualización del archivo CSS mediante la adición de una entrada en la hoja de estilo /apps/ws/css/newStyle.css de la siguiente manera:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
