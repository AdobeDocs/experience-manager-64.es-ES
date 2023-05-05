---
title: Crear una acción personalizada de la barra de herramientas
seo-title: Creating a custom toolbar action
description: Los desarrolladores de formularios pueden crear acciones personalizadas de la barra de herramientas para formularios adaptables en AEM Forms. Usar acciones personalizadas por parte de los autores de formularios puede proporcionar más flujos de trabajo y opciones a los usuarios finales.
seo-description: Form developers can create custom toolbar actions for adaptive forms in AEM Forms. Using custom actions form authors can provide more workflows and options to their end users.
uuid: 6761f389-1baa-4a59-a6e0-0f86f70fc692
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: b80a2bfe-6f57-4229-a9ee-1ec87f3c3306
exl-id: bb0abe28-843a-4195-afd5-5ee7f0a279be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 92%

---

# Crear una acción personalizada de la barra de herramientas {#creating-a-custom-toolbar-action}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Requisitos previos {#prerequisite}

Antes de crear una acción personalizada de la barra de herramientas, familiarícese con el [Usar bibliotecas del cliente](/help/sites-developing/clientlibs.md) y el [Desarrollar con CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Qué es una acción {#what-is-an-action-br}

Un formulario adaptable proporciona una barra de herramientas que permite al autor del formulario configurar un conjunto de opciones. Estas opciones se definen como acciones para el formulario adaptable. Haga clic en el botón Editar de la barra de herramientas del panel para definir las acciones admitidas por los formularios adaptables.

![Acciones predeterminadas de la barra de herramientas](assets/default_toolbar_actions.png)

Además del conjunto de acciones proporcionadas de forma predeterminada, puede crear acciones personalizadas en la barra de herramientas. Por ejemplo, puede agregar una acción para permitir al usuario revisar todos los campos de formulario adaptables antes de enviar un formulario.

## Pasos para crear una acción personalizada en un formulario adaptable {#steps}

Para ilustrar la creación de una acción personalizada de la barra de herramientas, los siguientes pasos le guiarán para crear un botón que permita a los usuarios finales revisar todos los campos del formulario adaptable antes de enviar un formulario rellenado.

1. Todas las acciones predeterminadas admitidas por los formularios adaptables están presentes en la carpeta `/libs/fd/af/components/actions`. En CRXDE, copie el nodo `fileattachmentlisting` de `/libs/fd/af/components/actions/fileattachmentlisting` a `/apps/customaction`.

1. Después de copiar el nodo en la carpeta `apps/customaction`, cambie el nombre del nodo a `reviewbeforesubmit`. Además, cambie las propiedades `jcr:title` y `jcr:description` del nodo.

   La propiedad `jcr:title` contiene el nombre de la acción que se muestra en el cuadro de diálogo de la barra de herramientas. La propiedad `jcr:description` contiene más información que se muestra cuando un usuario pasa el puntero sobre la acción.

   ![Jerarquía de nodos para la personalización de la barra de herramientas](assets/action3.png)

1. Seleccione `cq:template` nodo en el nodo `reviewbeforesubmit`. Asegúrese de que el valor de la propiedad `guideNodeClass` sea `guideButton` y cámbiela `jcr:title` en consecuencia.
1. Cambie la propiedad type en el nodo `cq:Template`. Para el ejemplo actual, cambie la propiedad de type a button.

   El valor de type se agrega como clase CSS en el HTML generado para el componente. Los usuarios pueden usar esa clase CSS para aplicar estilo a sus acciones. El estilo predeterminado para los dispositivos móviles y de escritorio se proporciona para los valores de button, submit, reset, y save type.

1. Seleccione la acción personalizada en el cuadro de diálogo de la barra de herramientas de edición de formularios adaptables. Se muestra el botón Revisar en la barra de herramientas del panel.

   ![La acción personalizada está disponible en la barra de herramientas](assets/custom_action_available_in_toolbar.png) ![Visualizar la acción personalizada de la barra de herramientas](assets/action7.png)

1. Para proporcionar funcionalidad al botón Revisar, agregue código JavaScript y CSS y código del lado del servidor en el archivo init.jsp, presentes dentro del nodo `reviewbeforesubmit`.

   Agregue el siguiente código en `init.jsp`.

   ```
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <guide:initializeBean name="guideField" className="com.adobe.aemds.guide.common.GuideButton"/>
   
   <c:if test="${not isEditMode}">
           <cq:includeClientLib categories="reviewsubmitclientlibruntime" />
   </c:if>
   
   <%--- BootStrap Modal Dialog  --------------%>
   <div class="modal fade" id="reviewSubmit" tabindex="-1">
       <div class="modal-dialog">
           <div class="modal-content">
               <div class="modal-header">
                   <h3>Review the Form Fields</h3>
               </div>
               <div class="modal-body">
                   <div class="modal-list">
                       <table>
                           <tr>
                               <td>
                                   <label>Your Name is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Pan Number is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Date Of Birth is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Total 80C Declaration Amount is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Total HRA Amount is: </label>
                               </td>
                           </tr>
                       </table>
                   </div>
               </div><!-- /.modal-body -->
               <div class="modal-footer">
                   <div class="fileAttachmentListingCloseButton col-md-2 col-xs-2 col-sm-2">
                       <button data-dismiss="modal">Close</button>
                   </div>
               </div>
           </div><!-- /.modal-content -->
       </div><!-- /.modal-dialog -->
   </div><!-- /.modal -->
   ```

   Agregue el siguiente código al archivo `ReviewBeforeSubmit.js`.

   ```
   /*anonymous function to handle show of review before submit view */
   $(function () {
       if($("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").length > 0) {
           $("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").click(function(){
               // Create the options object to be passed to the getElementProperty API
               var options = {},
                   result = [];
               options.somExpressions = [];
               options.propertyName = "value";
               guideBridge.visit(function(model){
                   if(model.name === "name" || model.name === "pan" || model.name === "dateofbirth" || model.name === "total" || model.name === "totalmonthlyrent"){
                           options.somExpressions.push(model.somExpression);
                   }
               }, this);
               result = guideBridge.getElementProperty(options);
   
               $('#reviewSubmit .reviewlabel').each(function(index, item){
                   var data = ((result.data[index] == null) ? "No Data Filled" : result.data[index]);
                   if($(this).next().hasClass("reviewlabelvalue")){
                       $(this).next().html(data);
                   } else {
                       $(this).after($("<td></td>").addClass("reviewlabelvalue col-md-6 active").html(data));
                   }
               });
               // added because in mobile devices it was causing problem of backdrop
               $("#reviewSubmit").appendTo('body');
               $("#reviewSubmit").modal("show");
           });
       }
   });
   ```

   Agregue el siguiente código al archivo `ReviewBeforeSubmit.css`.

   ```css
   .modal-list .reviewlabel {
       white-space: normal;
       text-align: right;
       padding:2px;
   }
   
   .modal-list .reviewlabelvalue {
       border: #cde0ec 1px solid;
       padding:2px;
   }
   
   /* Adding icon for this action in mobile devices */
   /* This is the glyphicon provided by bootstrap eye-open */
   /* .<type> .iconButton-icon */
   .reviewbeforesubmit .iconButton-icon {
       position: relative;
       top: -8px;
       font-family: 'Glyphicons Halflings';
       font-style: normal;
   }
   
   .reviewbeforesubmit .iconButton-icon:before {
       content: "\e105"
   }
   ```

1. Para comprobar la funcionalidad de la acción personalizada, abra el formulario adaptable en el modo de Vista previa y haga clic en Revisar en la barra de herramientas.

   >[!NOTE]
   >
   >La biblioteca `GuideBridge` no se carga en el modo de creación. Por lo tanto, esta acción personalizada no funciona en el modo de creación.

   ![Demostración de la acción personalizada del botón Revisar ](assets/action9.png)

## Ejemplos {#samples}

El siguiente archivo contiene un paquete de contenido. El paquete incluye un formulario adaptable relacionado con la demostración anterior de la acción personalizada de la barra de herramientas.

[Obtener archivo](assets/customtoolbaractiondemo.zip)
