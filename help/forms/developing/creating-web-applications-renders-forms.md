---
title: Creación de aplicaciones web que procesen Forms
seo-title: Creación de aplicaciones web que procesen Forms
description: Cree una aplicación basada en web que utilice servlets de Java para invocar el servicio Forms y procesar formularios. El servlet de Java sirve como vínculo entre el servicio de Forms que devuelve un formulario y un explorador web cliente.
seo-description: Cree una aplicación basada en web que utilice servlets de Java para invocar el servicio Forms y procesar formularios. El servlet de Java sirve como vínculo entre el servicio de Forms que devuelve un formulario y un explorador web cliente.
uuid: 00de10c5-79bd-4d8a-ae18-32f1fd2623bf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f29b089e-8902-4744-81c5-15ee41ba8069
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1913'
ht-degree: 0%

---


# Creación de aplicaciones web que procesen Forms {#creating-web-applications-thatrenders-forms}

## Creación de aplicaciones web que procesen Forms {#creating-web-applications-that-renders-forms}

Puede crear una aplicación basada en web que utilice servlets de Java para invocar el servicio de Forms y procesar formularios. La ventaja de utilizar un servlet Java™ es que puede escribir el valor devuelto del proceso en un navegador web cliente. Es decir, un servlet Java se puede utilizar como vínculo entre el servicio Forms que devuelve un formulario y un explorador web cliente.

>[!NOTE]
>
>En esta sección se describe cómo crear una aplicación basada en web que utilice un servlet Java que invoque el servicio Forms y procese formularios basados en fragmentos. (Consulte [Procesamiento de Forms basado en fragmentos](/help/forms/developing/rendering-forms-based-fragments.md)).

Con un servlet Java, puede escribir un formulario en un explorador web del cliente para que este pueda ver e introducir datos en el formulario. Después de rellenar el formulario con datos, el usuario web hace clic en un botón de envío ubicado en el formulario para enviar información al servlet Java, donde se pueden recuperar y procesar los datos. Por ejemplo, los datos se pueden enviar a otro proceso.

En esta sección se explica cómo crear una aplicación basada en web que permita al usuario seleccionar datos de formulario basados en Estados Unidos o datos de formulario basados en Canadá, como se muestra en la siguiente ilustración.

![cw_cw_fragmentwebclient](assets/cw_cw_fragmentwebclient.png)

El formulario procesado es un formulario basado en fragmentos. Es decir, si el usuario selecciona datos estadounidenses, el formulario devuelto utiliza fragmentos basados en datos estadounidenses. Por ejemplo, el pie de página del formulario contiene una dirección americana, como se muestra en la siguiente ilustración.

![cw_cw_fragementformfooter](assets/cw_cw_fragementformfooter.png)

Del mismo modo, si el usuario selecciona datos canadienses, el formulario devuelto contiene una dirección canadiense, como se muestra en la siguiente ilustración.

![cw_cw_fragementformfootercnd](assets/cw_cw_fragementformfootercnd.png)

>[!NOTE]
>
>Para obtener información sobre la creación de diseños de formulario basados en fragmentos, consulte [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

**Archivos de muestra**

Esta sección utiliza archivos de ejemplo que se pueden encontrar en la siguiente ubicación:

&lt;>Directorio *de instalación de Forms Designer >/Samples/Forms/Purchase Order/Form Fragments*

donde &lt;*directorio de instalación*> es la ruta de instalación. Para los fines de la aplicación cliente, el archivo Purchase Order Dynamic.xdp se copió de esta ubicación de instalación y se implementó en una aplicación de Forms denominada *Applications/FormsApplication*. El archivo Purchase Order Dynamic.xdp se coloca en una carpeta denominada FormsFolder. Del mismo modo, los fragmentos se colocan en la carpeta denominada Fragmentos, como se muestra en la siguiente ilustración.

![cw_cw_fragmentsrepository](assets/cw_cw_fragmentsrepository.png)

Para acceder al diseño de formulario Purchase Order Dynamic.xdp, especifique `Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp` como nombre del formulario (el primer parámetro pasado al método `renderPDFForm`) y `repository:///` como valor de URI raíz del contenido.

Los archivos de datos XML utilizados por la aplicación web se movieron de la carpeta Data a `C:\Adobe` (el sistema de archivos que pertenece al servidor de aplicaciones J2EE que aloja AEM Forms). Los nombres de archivo son Orden de compra *Canada.xml* y Orden de compra *US.xml*.

>[!NOTE]
>
>Para obtener información sobre la creación de una aplicación de Forms mediante Workbench, consulte [Ayuda de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

### Resumen de los pasos {#summary-of-steps}

Para crear aplicaciones basadas en Web que procesen formularios basados en fragmentos, realice los siguientes pasos:

1. Cree un nuevo proyecto web.
1. Cree una lógica de aplicación Java que represente el servlet Java.
1. Cree la página web para la aplicación web.
1. Empaquete la aplicación web a un archivo WAR.
1. Implemente el archivo WAR en el servidor de aplicaciones J2EE.
1. Pruebe la aplicación web.

>[!NOTE]
>
>Algunos de estos pasos dependen de la aplicación J2EE en la que se implementa AEM Forms. Por ejemplo, el método que utilice para implementar un archivo WAR depende del servidor de aplicaciones J2EE que esté utilizando. En esta sección se supone que AEM Forms está implementado en JBoss®.

### Creación de un proyecto web {#creating-a-web-project}

El primer paso para crear una aplicación web que contenga un servlet Java que pueda invocar el servicio Forms es crear un nuevo proyecto web. El IDE de Java en el que se basa este documento es Eclipse 3.3. Mediante el IDE de Eclipse, cree un proyecto web y agregue los archivos JAR necesarios al proyecto. Finalmente, añada una página HTML denominada *index.html* y un servlet Java al proyecto.

La siguiente lista especifica los archivos JAR que debe añadir al proyecto web:

* adobe-forms-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar

Para ver la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Para crear un proyecto web:**

1. Inicie Eclipse y haga clic en **Archivo** > **Nuevo proyecto**.
1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **Web** > **Proyecto Web dinámico**.
1. Escriba `FragmentsWebApplication` para el nombre del proyecto y haga clic en **Finalizar**.

**Para agregar los archivos JAR necesarios al proyecto:**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el proyecto `FragmentsWebApplication` y seleccione **Propiedades**.
1. Haga clic en **Ruta de compilación de Java** y, a continuación, haga clic en la pestaña **Bibliotecas**.
1. Haga clic en el botón **Add External JARs** y busque los archivos JAR que desea incluir.

**Para agregar un servlet Java al proyecto:**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el proyecto `FragmentsWebApplication` y seleccione **Nuevo** > **Otro**.
1. Expanda la carpeta **Web**, seleccione **Servlet** y, a continuación, haga clic en **Siguiente**.
1. En el cuadro de diálogo Crear servlet, escriba `RenderFormFragment` para el nombre del servlet y haga clic en **Finalizar**.

**Para añadir una página HTML al proyecto:**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el proyecto `FragmentsWebApplication` y seleccione **Nuevo** > **Otro**.
1. Expanda la carpeta **Web**, seleccione **HTML** y haga clic en **Siguiente**.
1. En el cuadro de diálogo Nuevo HTML, escriba `index.html` para el nombre del archivo y haga clic en **Finalizar**.

>[!NOTE]
>
>Para obtener información sobre la creación de la página HTML que invoca el servlet Java `RenderFormFragment`, consulte [Creación de la página web](/help/forms/developing/rendering-forms.md#creating-the-web-page).

### Creación de la lógica de aplicación Java para el servlet {#creating-java-application-logic-for-the-servlet}

Puede crear una lógica de aplicación Java que invoque el servicio Forms desde el servlet Java. El siguiente código muestra la sintaxis del servlet Java `RenderFormFragment`:

```as3
     public class RenderFormFragment extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
         doPost(req,resp); 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
             //Add code here to invoke the Forms service 
             }
```

Normalmente, no colocaría código de cliente dentro del método `doGet` o `doPost` de un servlet Java. Una práctica recomendada de programación es colocar este código dentro de una clase independiente, crear una instancia de la clase desde el método `doPost` (o el método `doGet`) e llamar a los métodos adecuados. Sin embargo, para la brevedad del código, los ejemplos de código de esta sección se reducen al mínimo y los ejemplos de código se colocan en el método `doPost` .

Para procesar un formulario basado en fragmentos mediante la API de servicio de Forms, realice las siguientes tareas:

1. Incluya archivos JAR del cliente, como adobe-forms-client.jar, en la ruta de clase de su proyecto Java. Para obtener información sobre la ubicación de estos archivos, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Recupere el valor del botón de opción que se envía desde el formulario HTML y especifica si se deben utilizar datos estadounidenses o canadienses. Si se envía American, cree un `com.adobe.idp.Document` que almacene datos ubicados en el *Purchase Order US.xml*. Del mismo modo, si es canadiense, cree un `com.adobe.idp.Document` que almacene datos ubicados en el archivo *Purchase Order Canada.xml*.
1. Cree un objeto `ServiceClientFactory` que contenga propiedades de conexión. (Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).
1. Cree un objeto `FormsServiceClient` utilizando su constructor y pasando el objeto `ServiceClientFactory`.
1. Cree un objeto `URLSpec` que almacene valores de URI usando su constructor.
1. Invoque el método `URLSpec` del objeto `setApplicationWebRoot` y pase un valor de cadena que represente la raíz web de la aplicación.
1. Invoque el método `URLSpec` del objeto `setContentRootURI` y pase un valor de cadena que especifique el valor de URI raíz del contenido. Asegúrese de que el diseño de formulario y los fragmentos se encuentran en el URI raíz del contenido. Si no es así, el servicio de Forms genera una excepción. Para hacer referencia al repositorio de AEM Forms, especifique `repository://`.
1. Invoque el método `URLSpec` del objeto `setTargetURL` y pase un valor de cadena que especifique el valor de la dirección URL de destino donde se registran los datos del formulario. Si define la dirección URL de destino en el diseño de formulario, puede pasar una cadena vacía. También puede especificar la dirección URL a la que se envía un formulario para realizar cálculos.
1. Invoque el método `FormsServiceClient` del objeto `renderPDFForm` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del diseño de formulario, incluida la extensión del nombre de archivo.
   * Un objeto `com.adobe.idp.Document` que contiene datos para combinar con el formulario (creado en el paso 2).
   * Un objeto `PDFFormRenderSpec` que almacena opciones en tiempo de ejecución. Para obtener más información, consulte [Referencia de API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Un objeto `URLSpec` que contiene valores de URI necesarios para el servicio Forms para procesar un formulario basado en fragmentos.
   * Un objeto `java.util.HashMap` que almacena archivos adjuntos. Se trata de un parámetro opcional y puede especificar `null` si no desea adjuntar archivos al formulario.

   El método `renderPDFForm` devuelve un objeto `FormsResult` que contiene un flujo de datos de formulario que debe escribirse en el explorador web del cliente.

1. Cree un objeto `com.adobe.idp.Document` invocando el método `FormsResult` del objeto ‘s `getOutputContent`.
1. Obtenga el tipo de contenido del objeto `com.adobe.idp.Document` invocando su método `getContentType`.
1. Establezca el tipo de contenido del objeto `javax.servlet.http.HttpServletResponse` invocando su método `setContentType` y pasando el tipo de contenido del objeto `com.adobe.idp.Document`.
1. Cree un objeto `javax.servlet.ServletOutputStream` que se utilice para escribir el flujo de datos del formulario en el explorador web del cliente invocando el método `javax.servlet.http.HttpServletResponse` del objeto `getOutputStream`.
1. Cree un objeto `java.io.InputStream` invocando el método `com.adobe.idp.Document` del objeto `getInputStream`.
1. Cree una matriz de bytes rellénela con la secuencia de datos del formulario invocando el método `InputStream` del objeto `read`y pasando la matriz de bytes como argumento.
1. Invoque el método `javax.servlet.ServletOutputStream` del objeto `write` para enviar la secuencia de datos del formulario al explorador web del cliente. Pase la matriz de bytes al método `write`.

El siguiente ejemplo de código representa el servlet Java que invoca el servicio Forms y procesa un formulario basado en fragmentos.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.io.IOException; 
 import java.io.PrintWriter; 
  
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import java.net.URL; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormFragment extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
  
     } 
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
     throws ServletException, IOException { 
          
          
              
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Get the value of selected radio button 
             String radioValue = req.getParameter("radio"); 
              
             //Create an Document object to store form data 
             Document oInputData = null;  
              
             //The value of the radio button determines the form data to use 
             //which determines which fragments used in the form 
             if (radioValue.compareTo("AMERICAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml"); 
                 oInputData = new Document(myData);  
             } 
             else if (radioValue.compareTo("CANADIAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml"); 
                 oInputData = new Document(myData);  
             } 
                      
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Set the parameter values for the renderPDFForm method 
             String formName = "Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp";   
                                      
             //Cache the PDF form 
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
          
             //Specify URI values that are required to render a form 
             //design based on fragments 
             URLSpec uriValues = new URLSpec();  
             uriValues.setApplicationWebRoot("https://[server]:[port]/RenderFormFragment"); 
             uriValues.setContentRootURI("repository:///"); 
             uriValues.setTargetURL("https://[server]:[port]/FormsServiceClientApp/HandleData"); 
                      
             //Invoke the renderPDFForm method and write the  
             //results to a client web browser 
             FormsResult formOut = formsClient.renderPDFForm( 
                         formName,               //formQuery 
                         oInputData,             //inDataDoc 
                         pdfFormRenderSpec,      //PDFFormRenderSpec 
                         uriValues,                //urlSpec 
                         null                    //attachments 
                         ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse object’s content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
      
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
 }
```

### Creación de la página web {#creating-the-web-page}

La página web index.html proporciona un punto de entrada al servlet Java e invoca el servicio Forms. Esta página web es un formulario HTML básico que contiene dos botones de opción y un botón de envío. El nombre de los botones de radio es radio. Cuando el usuario hace clic en el botón de envío, los datos del formulario se publican en el servlet Java `RenderFormFragment`.

El servlet Java captura los datos que se publican desde la página HTML mediante el siguiente código Java:

```as3
             Document oInputData = null;  
              
             //Get the value of selected radio button 
             String radioValue = req.getParameter("radio"); 
                          
             //The value of the radio button determines the form data to use 
             //which determines which fragments used in the form 
             if (radioValue.compareTo("AMERICAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml"); 
                 oInputData = new Document(myData);  
             } 
             else if (radioValue.compareTo("CANADIAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml"); 
                 oInputData = new Document(myData);  
             }
```

El siguiente código HTML se encuentra en el archivo index.html que se creó durante la configuración del entorno de desarrollo. (Consulte [Creación de un proyecto web](/help/forms/developing/rendering-forms.md#creating-a-web-project)).

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
 <html xmlns="https://www.w3.org/1999/xhtml"> 
 <head> 
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
 <title>Untitled Document</title> 
 </head> 
  
 <body> 
 <form name="myform" action="https://[server]:[port]/FragmentsWebApplication/RenderFormFragment" method="post"> 
      <table> 
      <tr> 
        <th>Forms Fragment Web Client</th> 
      </tr> 
      <tr> 
        <td> 
          <label> 
          <input type="radio" name="radio" id="radio_Data" value="CANADIAN" /> 
          Canadian data<br /> 
          </label> 
          <p> 
            <label> 
            <input type="radio" name="radio" id="radio_Data" value="AMERICAN" checked/> 
            American data</label> 
          </p> 
        </td> 
      </tr> 
      <tr> 
      <td> 
        <label> 
          <input type="submit" name="button_Submit" id="button_Submit" value="Submit" /> 
            </label> 
            </td> 
         </tr> 
        </table> 
      </form>     
 </body> 
 </html>
```

### Empaquetado de la aplicación web {#packaging-the-web-application}

Para implementar el servlet Java que invoca el servicio Forms, empaquete la aplicación web a un archivo WAR. Asegúrese de que los archivos JAR externos de los que depende la lógica empresarial del componente, como adobe-livecycle-client.jar y adobe-forms-client.jar, también estén incluidos en el archivo WAR.

**Para empaquetar una aplicación web en un archivo WAR:**

1. En la ventana **Project Explorer**, haga clic con el botón derecho en el proyecto `FragmentsWebApplication` y seleccione **Export** > **WAR file**.
1. En el cuadro de texto **Web module**, escriba `FragmentsWebApplication` para el nombre del proyecto Java.
1. En el cuadro de texto **Destination**, escriba `FragmentsWebApplication.war`**para el nombre del archivo** especifique la ubicación del archivo WAR y, a continuación, haga clic en Finish.

### Implementación del archivo WAR en el servidor de aplicaciones J2EE {#deploying-the-war-file-to-the-j2ee-application-server}

Puede implementar el archivo WAR en el servidor de aplicaciones J2EE en el que se implementa AEM Forms. Una vez implementado el archivo WAR, puede acceder a la página web HTML mediante un navegador web.

**Para implementar el archivo WAR en el servidor de aplicaciones J2EE:**

* Copie el archivo WAR de la ruta de exportación a *[Instalación de Forms]*\Adobe\Adobe Experience Manager Forms\jboss\server\all\deploy.

### Prueba de la aplicación web {#testing-your-web-application}

Después de implementar la aplicación web, puede probarla con un explorador web. Suponiendo que esté utilizando el mismo equipo que aloja AEM Forms, puede especificar la siguiente URL:

* http://localhost:8080/FragmentsWebApplication/index.html

   Seleccione un botón de opción y haga clic en el botón Enviar. Un formulario basado en fragmentos aparecerá en el explorador web. Si se producen problemas, consulte el archivo de registro del servidor de aplicaciones J2EE.

