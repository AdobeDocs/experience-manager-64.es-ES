---
title: Usar metadatos en una notificación por correo electrónico
seo-title: Use metadata in an email notification
description: Usar metadatos para rellenar información en una notificación de correo electrónico del flujo de trabajo de formularios
seo-description: Use metadata to populate information in a forms workflow email notification
uuid: 17e018c9-6bf8-4042-bba9-4ebe449304ac
topic-tags: publish
discoiquuid: bdf13893-630a-43cd-aaeb-c7c16bf4f8a6
exl-id: 248c5adf-23e9-463f-9f29-869ae2426c22
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 18%

---

# Usar metadatos en una notificación por correo electrónico  {#use-metadata-in-an-email-notification}

Usar metadatos para rellenar información en una notificación de correo electrónico del flujo de trabajo de formularios

Puede utilizar el paso Asignar tarea para crear y asignar tareas a un usuario o grupo. Cuando se asigna una tarea a un usuario o grupo, se envía una notificación por correo electrónico al usuario definido o a cada miembro del grupo definido. Una [notificación por correo electrónico](/help/forms/using/use-custom-email-template-assign-task-step.md) contiene el vínculo de la tarea asignada y la información relacionada con la tarea.

Puede utilizar metadatos en una plantilla de correo electrónico para rellenar dinámicamente la información en una notificación por correo electrónico. Por ejemplo, el valor del título, la descripción, la fecha de vencimiento, la prioridad, el flujo de trabajo y la última fecha de la siguiente notificación de correo electrónico se seleccionan de forma dinámica en el tiempo de ejecución (cuando se genera una notificación por correo electrónico).

![default-email-template](assets/default-email-template.png)

Los metadatos se almacenan en pares clave-valor. Puede especificar la clave en la plantilla de correo electrónico y la clave se sustituye por un valor en tiempo de ejecución (cuando se genera una notificación por correo electrónico). Por ejemplo, en el siguiente ejemplo de código, &quot;$ {workitem_title}&quot; es una clave. Se reemplaza con el valor &quot;Loan-Request&quot; en tiempo de ejecución.

```xml
subject=Task Assigned - ${workitem_title}

message=<html><body>\n\
 <table>\n\
  <tbody>\n\
   <tr>\n\
    <td>\n\
      Sample Company\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <pre style="font-size: 13px; font-family: Helvetica, Arial, sans-serif;  font-weight: normal; color: #323232;"> Hello ${workitem_assignee},\n\
 The following task has been assigned to you:</pre>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <table>\n\
      <tbody>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> TITLE</td>\n\
        <td>\n\
         <p>${workitem_title}</p>\n\
        </td>\n\
       </tr>\n\
                            <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DESCRIPTION</td>\n\
        <td>\n\
         <p>${workitem_description}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DUE DATE</td>\n\
        <td>\n\
         <p>${workitem_due_date}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> PRIORITY</td>\n\
        <td>\n\
         <p>${workitem_priority}</p>\n\
        </td>\n\
       </tr>\n\
       <tr>\n\
        <td> WORKFLOW</td>\n\
        <td>\n\
         <p>${workitem_workflow}</p>\n\
        </td>\n\
       </tr>\n\
      </tbody>\n\
     </table>\n\
    </td>\n\
   </tr>\n\
   <tr style = "text-align: center; vertical-align: middle;">\n\
    <td> \n\
     <a href="${workitem_url}" target="_blank" style="background-color: #1EBBBB; font-size: 18px; line-height: 25px; font-weight: bold; color: #FFFFFF; text-decoration: none; padding: 15px 15px 15px 15px;">Open Task</a>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <p><span style="font-size: 12px; font-weight: normal; font-style: italic; color: #919191;">This is an automatically generated email. Please do not reply to this email.</span></p>\n\
    </td>\n\
   </tr>\n\
  </tbody>\n\
 </table>\n\
</body>\n\
</html>\n\
```

## Uso de metadatos generados por el sistema en una notificación por correo electrónico {#using-system-generated-metadata-in-an-email-notification}

Una aplicación de AEM Forms proporciona varias variables de metadatos (pares clave-valor) listas para usar. Puede utilizar estas variables en una plantilla de correo electrónico. El valor de la variable se basa en la aplicación de formularios asociada. La siguiente tabla enumera todas las variables de metadatos disponibles de forma predeterminada:

<table> 
 <tbody> 
  <tr> 
   <td>Clave</td> 
   <td>Descripción</td> 
  </tr> 
  <tr> 
   <td>elemento de trabajo_título</td> 
   <td>Título de la aplicación de formularios asociada.</td> 
  </tr> 
  <tr> 
   <td>workitem_url</td> 
   <td>URL para acceder a la aplicación de formularios asociada.</td> 
  </tr> 
  <tr> 
   <td>workitem_description</td> 
   <td>Descripción de la aplicación de formularios asociada.</td> 
  </tr> 
  <tr> 
   <td>workitem_priority</td> 
   <td>Prioridad especificada para la aplicación de formularios asociada.</td> 
  </tr> 
  <tr> 
   <td>workitem_due_date</td> 
   <td>Última fecha para actuar en la aplicación de formularios asociada.</td> 
  </tr> 
  <tr> 
   <td>workitem_workflow</td> 
   <td>Nombre del flujo de trabajo asociado a la aplicación de formularios.</td> 
  </tr> 
  <tr> 
   <td>workitem_assign_timestamp</td> 
   <td>Fecha y hora en que se asignó el elemento de flujo de trabajo al usuario asignado actual.</td> 
  </tr> 
  <tr> 
   <td>workitem_assignee</td> 
   <td>Nombre del cesionario actual.</td> 
  </tr> 
  <tr> 
   <td>host_prefix</td> 
   <td>URL del servidor de creación. Por ejemplo, https://10.41.42.66:4502<br /> </td> 
  </tr> 
  <tr> 
   <td>publish_prefix</td> 
   <td>URL del servidor de publicación. Por ejemplo, https://10.41.42.66:4503</td> 
  </tr> 
 </tbody> 
</table>

## Uso de metadatos personalizados en una notificación por correo electrónico {#using-custom-metadata-in-an-email-notification}

También puede utilizar metadatos personalizados en una notificación por correo electrónico. Los metadatos personalizados contienen información además de los metadatos generados por el sistema. Por ejemplo, los detalles de directivas recuperados de una base de datos. Puede utilizar un paquete ECMAScript o OSGi para agregar metadatos personalizados en el repositorio crx:

### Usar ECMAScript para agregar metadatos personalizados  {#use-ecmascript-to-add-custom-metadata}

[ECMAScript es un lenguaje de script. ](https://en.wikipedia.org/wiki/ECMAScript) Se utiliza para scripts del lado del cliente y aplicaciones de servidor. Realice los siguientes pasos para utilizar ECMAScript para agregar metadatos personalizados a una plantilla de correo electrónico:

1. Inicie sesión en CRX DE con una cuenta administrativa. La URL es `https://[server]:[port]/crx/de/index.jsp`. 

1. Vaya a /apps/fd/dashboard/scripts/metadataScripts. Cree un archivo con la extensión .ecma. Por ejemplo, usermetadata.ecma

   Si la ruta mencionada anteriormente no existe, créela.

1. Agregue código al archivo .ecma que tenga la lógica de generar metadatos personalizados en pares clave-valor. Por ejemplo, el siguiente código ECMAScript genera metadatos personalizados para una póliza de seguro:

   ```
   function getUserMetaData()  {
       //Commented lines below provide an overview on how to set user metadata in map and return it.
       var HashMap = Packages.java.util.HashMap;
       var valuesMap = new HashMap();
       valuesMap.put("policyNumber", "2017568972695");
       valuesMap.put("policyHolder", "Adobe Systems");
   
       return valuesMap;
   }
   ```

1. Haga clic en Guardar todo. Ahora, la secuencia de comandos está disponible para su selección en AEM modelo de flujo de trabajo.

   ![assigntask-metadata](assets/assigntask-metadata.png)

1. (Opcional) Especifique el título de la secuencia de comandos:

   Si no especifica el título, el campo Metadatos personalizados muestra la ruta completa del archivo ECMAScript. Siga estos pasos para especificar un título significativo para la secuencia de comandos:

   1. Expanda el nodo del script, haga clic con el botón derecho en el nodo **[!UICONTROL jcr:content]** y haga clic en **[!UICONTROL Mixins]**.
   1. Mezcla de tipos:título en el cuadro de diálogo Editar mezclas y haga clic en **+**.
   1. Agregue una propiedad con los siguientes valores.

      | Nombre | jcr:title |
      |---|---|
      | Tipo | Cadena |
      | Valor | Especifique el título de la secuencia de comandos. Por ejemplo, metadatos personalizados para el titular de la directiva. El valor especificado se muestra en el paso asignar tarea. |

### Usar un paquete OSGi y la interfaz Java para agregar metadatos personalizados {#use-an-osgi-bundle-and-java-interface-to-add-custom-metadata}

Puede utilizar la interfaz Java WorkitemUserMetadataService para agregar metadatos personalizados para plantillas de correo electrónico. Puede crear un paquete OSGi que utilice la interfaz Java WorkitemUserMetadataService e implementarla en el servidor de AEM Forms. Hace que los metadatos estén disponibles para su selección en el paso Asignar tarea .

Para crear un paquete OSGi con la interfaz Java, agregue [SDK de cliente de AEM Forms](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) jar y [tarro de granito](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.workflow.api/1.0.2/) archivos como dependencias externas al proyecto de paquete OSGi. Puede utilizar cualquier IDE de Java para crear un paquete OSGi. El siguiente procedimiento proporciona los pasos para utilizar Eclipse para crear un paquete OSGi:

1. Abra Eclipse IDE. Vaya a Archivo > Nuevo proyecto.

1. En la pantalla Seleccionar un asistente, seleccione Proyecto Maven y haga clic en Siguiente.

1. En este nuevo proyecto llamado Maven, mantenga los valores predeterminados y haga clic en Siguiente. Seleccione un arquetipo y haga clic en Siguiente; por ejemplo, maven-archetype-quickstart. Especifique el ID de grupo, el ID de artefacto, la versión y el paquete del proyecto y haga clic en Finalizar. El proyecto se ha creado.

1. Abra el archivo pom.xml para editarlo y reemplace todo el contenido del archivo por lo siguiente:

   ```
   
   ```

1. Agregue código fuente que utilice la interfaz Java WorkitemUserMetadataService para agregar metadatos personalizados para plantillas de correo electrónico. A continuación se muestra un ejemplo de código:

   ```java
   package com.aem.impl;
   
   import com.adobe.fd.workspace.service.external.WorkitemUserMetadataService;
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Properties;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.osgi.framework.Constants;
   
   import java.util.HashMap;
   import java.util.Map;
   
   @Component
   @Service
   @Properties({
           @Property(name = Constants.SERVICE_DESCRIPTION, value = "A sample implementation of a user metadata service."),
           @Property(name = WorkitemUserMetadataService.SERVICE_PROPERTY_LABEL, value = "Default User Metadata Service")})
   
   public class WorkitemUserMetadataServiceImpl
     implements WorkitemUserMetadataService
   {
     public WorkitemUserMetadataServiceImpl() {}
   
     public Map<String, String> getUserMetadataMap()
     {
       HashMap<String, String> metadataMap = null;
       metadataMap = new HashMap();
       metadataMap.put("test_metadata", "tested-interface implementation");
       return metadataMap;
     }
   }
   ```

1. Abra un símbolo del sistema y vaya al directorio que contiene el proyecto del paquete OSGi. Utilice el siguiente comando para crear el paquete OSGi:

   `mvn clean install`

1. Cargue el paquete en un servidor de AEM Forms. Puede utilizar AEM Administrador de paquetes para importar el paquete en el servidor de AEM Forms.

Una vez importado el paquete, puede seleccionar los metadatos en el paso Asignar tarea y utilizarlos en una plantilla de correo electrónico.
