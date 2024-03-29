---
title: Invocación de procesos de larga vida centrados en el ser humano
seo-title: Invoking Human-Centric Long-Lived Processes
description: Invoque mediante programación procesos de larga duración centrados en el ser humano creados en Workbench usando una aplicación cliente basada en web Java que usa la API de invocación, una aplicación ASP.NET que usa servicios web y una aplicación cliente creada con Flex que usa Remoting.
seo-description: Programmatically invoke human-centric long-lived processes created in Workbench using a Java web-based client application that uses the Invocation API, an ASP.NET application that uses web services, and a client application built with Flex that uses Remoting.
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
role: Developer
exl-id: 4f581af8-9c1a-4e80-b459-a83a1dab3b01
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3748'
ht-degree: 0%

---

# Invocación de procesos de larga vida centrados en el ser humano {#invoking-human-centric-long-lived-processes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede invocar mediante programación procesos de larga duración centrados en el ser humano creados en Workbench utilizando estas aplicaciones cliente:

* Una aplicación de cliente basada en web de Java que utiliza la API de invocación. (Consulte [Invocación de AEM Forms mediante la API de Java](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).
* Una aplicación ASP.NET que utiliza servicios Web. (Consulte [Invocación de AEM Forms mediante servicios web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Una aplicación cliente creada con Flex que utiliza Remoting. (Consulte [Invocación de AEM Forms mediante AEM Forms Remoting (obsoleto para formularios AEM)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Se nombra el proceso que se invoca durante mucho tiempo. *FirstAppSolution/PreLoanProcess*. Puede crear este proceso siguiendo el tutorial especificado en [Creación de la primera aplicación de AEM Forms](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).

Un proceso centrado en el ser humano implica una tarea a la que un usuario puede responder mediante Workspace. Por ejemplo, con Workbench, puede crear un proceso que permita a un administrador bancario aprobar o denegar una solicitud de préstamo. La siguiente ilustración muestra el proceso *FirstAppSolution/PreLoanProcess*.

El proceso* FirstAppSolution/PreLoanProcess* acepta un parámetro de entrada denominado* formData* cuyo tipo de datos es XML. Los datos XML se combinan con un diseño de formulario denominado *PreLoanForm.xdp*. La siguiente ilustración muestra un formulario que representa una tarea asignada a un usuario para aprobar o denegar una solicitud de préstamo. El usuario aprueba o rechaza la aplicación utilizando Workspace. El usuario de Workspace puede aprobar la solicitud de préstamo haciendo clic en el botón Approve que se muestra en la siguiente ilustración. Del mismo modo, el usuario puede denegar la solicitud de préstamo haciendo clic en el botón denegar.

Un proceso de larga duración se invoca asincrónicamente y no se puede invocar sincrónicamente debido a los siguientes factores:

* Un proceso puede abarcar una cantidad de tiempo considerable.
* Un proceso puede abarcar límites organizativos.
* Un proceso necesita una entrada externa para que finalice. Por ejemplo, considere una situación en la que se envía un formulario a un administrador que está fuera de la oficina. En este caso, el proceso no se completa hasta que el administrador vuelva y rellene el formulario.

Cuando se invoca un proceso de larga duración, AEM Forms crea un valor de identificador de invocación como parte de la creación de un registro. El registro rastrea el estado del proceso de larga duración y se almacena en la base de datos de AEM Forms. Con el valor del identificador de invocación, se puede realizar un seguimiento del estado del proceso de larga duración. Además, puede utilizar el valor del identificador de invocación del proceso para realizar operaciones del Administrador de procesos, como terminar una instancia de proceso en ejecución.

>[!NOTE]
>
>AEM Forms no crea un valor de identificador de invocación ni un registro cuando se invoca un proceso de corta duración.

La variable `FirstAppSolution/PreLoanProcess` El proceso se invoca cuando un solicitante envía una solicitud, que se representa como datos XML. El nombre de la variable del proceso de entrada es `formData` y su tipo de datos es XML. A los efectos de esta discusión, supongamos que se utilizan los siguientes datos XML como entrada para la variable `FirstAppSolution/PreLoanProcess` proceso.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <LoanApp> 
 <Name>Sam White</Name> 
 <LoanAmount>250000</LoanAmount> 
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail> 
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
 </LoanApp>
```

Los datos XML que se pasan a un proceso deben coincidir con los campos ubicados en el formulario utilizado en el proceso. De lo contrario, los datos no se muestran dentro del formulario. Todas las aplicaciones que invocan la variable `FirstAppSolution/PreLoanProcess` proceso debe pasar este origen de datos XML. Las aplicaciones creadas en *Invocación de procesos de larga vida centrados en el ser humano* cree dinámicamente el origen de datos XML a partir de valores que un usuario haya introducido en un cliente web.

Con una aplicación cliente, puede enviar el proceso *FirstAppSolution/PreLoanProcess *procesar los datos XML necesarios. Un proceso de larga duración devuelve un valor de identificador de invocación como su valor devuelto. La siguiente ilustración muestra las aplicaciones cliente que invocan la función* FirstAppSolution/PreLoanProcess *proceso de larga duración. Las aplicaciones cliente envían datos XML y recuperan un valor de cadena que representa el valor del identificador de invocación.

**Consulte también**

[Creación de una aplicación web de Java que invoque un proceso prolongado centrado en el ser humano](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Creación de una aplicación web ASP.NET que invoque un proceso prolongado centrado en el ser humano](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Creación de una aplicación cliente creada con Flex que invoca un proceso prolongado centrado en el ser humano](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Creación de una aplicación web de Java que invoque un proceso prolongado centrado en el ser humano {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

Puede crear una aplicación basada en web que utilice un servlet Java para invocar el `FirstAppSolution/PreLoanProcess` proceso. Para invocar este proceso desde un servlet Java, utilice la API de invocación dentro del servlet Java. (Consulte [Invocación de AEM Forms mediante la API de Java](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

La siguiente ilustración muestra una aplicación cliente basada en web que publica valores de nombre, teléfono (o correo electrónico) y cantidad. Estos valores se envían al servlet Java cuando el usuario hace clic en el botón Enviar aplicación .

El servlet Java realiza las siguientes tareas:

* Recupera los valores anunciados desde la página HTML en el servlet Java.
* Crea dinámicamente un origen de datos XML para pasarlo al proceso* FirstAppSolution/PreLoanProcess *. Los valores de nombre, teléfono (o correo electrónico) y cantidad se especifican en el origen de datos XML.
* Invoca el *FirstAppSolution/PreLoanProcess* procesar mediante la API de invocación de AEM Forms.
* Devuelve el valor del identificador de invocación al explorador web del cliente.

### Resumen de los pasos {#summary-of-steps}

Para crear una aplicación Java basada en Web que invoque la variable `FirstAppSolution/PreLoanProcess` realice los siguientes pasos:

1. [Creación de un proyecto web](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Crear lógica de aplicación Java para el servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [Crear la página web para la aplicación web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Empaquete la aplicación web a un archivo WAR](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Implementar el archivo WAR en el servidor de aplicaciones J2EE que hospeda AEM Forms](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms).
1. [Probar la aplicación web](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Algunos de estos pasos dependen de la aplicación J2EE en la que se implementa AEM Forms. Por ejemplo, el método que utilice para implementar un archivo WAR depende del servidor de aplicaciones J2EE que esté utilizando. Se supone que AEM Forms está implementado en JBoss®.

### Creación de un proyecto web {#create-a-web-project}

El primer paso para crear una aplicación web es crear un proyecto web. El IDE de Java en el que se basa este documento es Eclipse 3.3. Mediante el IDE de Eclipse, cree un proyecto web y agregue los archivos JAR necesarios al proyecto. Añada una página de HTML denominada *index.html *y un servlet Java al proyecto.

La siguiente lista especifica los archivos JAR que se incluirán en el proyecto web:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Para ver la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>El archivo J2EE.jar define los tipos de datos que utiliza un servlet Java. Puede obtener este archivo JAR desde el servidor de aplicaciones J2EE en el que se implementa AEM Forms.

**Creación de un proyecto web**

1. Inicie Eclipse y haga clic en **Archivo** >  **Nuevo proyecto**.
1. En el **Nuevo proyecto** cuadro de diálogo, seleccione **Web** > **Proyecto web dinámico**.
1. Tipo `InvokePreLoanProcess` para obtener el nombre del proyecto y, a continuación, haga clic en **Finalizar**.

**Añadir los archivos JAR necesarios al proyecto**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el `InvokePreLoanProcess` proyecto y seleccione **Propiedades**.
1. Haga clic en **Ruta de compilación de Java** y, a continuación, haga clic en la **Bibliotecas** pestaña .
1. Haga clic en el **Añadir JAR externos** y busque los archivos JAR que desea incluir.

**Agregar un servlet Java al proyecto**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el `InvokePreLoanProcess` proyecto y seleccione **Nuevo** >  **Otro**.
1. Expanda el **Web** carpeta, seleccione **Servlet** y, a continuación, haga clic en **Siguiente**.
1. En el cuadro de diálogo Crear servlet, escriba `SubmitXML` para el nombre del servlet y, a continuación, haga clic en **Finalizar**.

**Agregar una página de HTML al proyecto**

1. En la ventana Explorador de proyectos, haga clic con el botón derecho en el `InvokePreLoanProcess` proyecto y seleccione **Nuevo** > **Otro**.
1. Expanda el **Web** carpeta, seleccione **HTML** y haga clic en **Siguiente**.
1. En el cuadro de diálogo Nuevo HTML, escriba `index.html` para el nombre de archivo y, a continuación, haga clic en **Finalizar**.

>[!NOTE]
>
>Para obtener información sobre la creación de contenido de HTML que invoque el servlet Java SubmitXML, consulte [Crear la página web para la aplicación web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application).

### Crear lógica de aplicación Java para el servlet {#create-java-application-logic-for-the-servlet}

Cree una lógica de aplicación Java que invoque la variable `FirstAppSolution/PreLoanProcess` procesar desde el servlet Java. El siguiente código muestra la sintaxis de la variable `SubmitXML` Servlet Java:

```as3
     public class SubmitXML extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
         doPost(req,resp); 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
             //Add code here to invoke the FirstAppSolution/PreLoanProcess process 
             }
```

Normalmente, no colocaría código de cliente dentro de un servlet Java `doGet` o `doPost` método. Una mejor práctica de programación es colocar este código dentro de una clase separada. A continuación, cree una instancia de la clase desde el `doPost` método (o `doGet` ) y llame a los métodos adecuados. Sin embargo, para la brevedad del código, los ejemplos de código se reducen al mínimo y se colocan en la variable `doPost` método.

Para invocar la variable `FirstAppSolution/PreLoanProcess` mediante la API de invocación, realice las siguientes tareas:

1. Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java. Para obtener información sobre la ubicación de estos archivos, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Recupere los valores de nombre, teléfono y cantidad enviados desde la página HTML. Utilice estos valores para crear dinámicamente un origen de datos XML que se envíe a la variable `FirstAppSolution/PreLoanProcess` proceso. Puede usar `org.w3c.dom` para crear el origen de datos XML (esta lógica de aplicación se muestra en el siguiente ejemplo de código).
1. Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión. (Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Cree un `ServiceClient` usando su constructor y pasando el `ServiceClientFactory` objeto. A `ServiceClient` permite invocar una operación de servicio. Gestiona tareas como la localización, el envío y las solicitudes de invocación de enrutamiento.
1. Cree un `java.util.HashMap` usando su constructor.
1. Invocar el `java.util.HashMap` del objeto `put` para que cada parámetro de entrada pase al proceso de larga duración. Asegúrese de especificar el nombre de los parámetros de entrada del proceso. Porque la variable `FirstAppSolution/PreLoanProcess` proceso requiere un parámetro de entrada de tipo `XML` (con nombre `formData`), solo tiene que invocar la variable `put` método una vez.

   ```as3
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process 
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                 
    //Create a Map object to store the parameter value 
    Map params = new HashMap(); 
    params.put("formData", inXML);
   ```

1. Cree un `InvocationRequest` invocando el objeto `ServiceClientFactory` del objeto `createInvocationRequest` y pasando los siguientes valores:

   * Un valor de cadena que especifica el nombre del proceso de larga duración que se va a invocar. Para invocar la variable `FirstAppSolution/PreLoanProcess` procesar, especificar `FirstAppSolution/PreLoanProcess`.
   * Valor de cadena que representa el nombre de la operación de proceso. El nombre de la operación de proceso de larga duración es `invoke`.
   * La variable `java.util.HashMap` que contiene los valores de parámetro que requiere la operación de servicio.
   * Un valor booleano que especifica `false`, que crea una solicitud asincrónica (este valor se aplica para invocar un proceso de larga duración).

   >[!NOTE]
   >
   >*Se puede invocar un proceso de corta duración pasando el valor true como el cuarto parámetro del método createInvocationRequest . Al pasar el valor true, se crea una solicitud sincrónica.*

1. Envíe la solicitud de invocación a AEM Forms invocando el `ServiceClient` del objeto `invoke` y pasando el `InvocationRequest` objeto. La variable `invoke` devuelve un valor `InvocationReponse` objeto.
1. Un proceso de larga duración devuelve un valor de cadena que representa un valor de identificación de invocación. Recupere este valor invocando la variable `InvocationReponse` del objeto `getInvocationId` método.

   ```as3
    //Send the invocation request to the long-lived process and  
    //get back an invocation response object 
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
    String invocationId = lcResponse.getInvocationId();
   ```

1. Escriba el valor de identificación de invocación en el explorador web del cliente. Puede usar un `java.io.PrintWriter` para escribir este valor en el navegador web del cliente.

### Inicio rápido: Invocación de un proceso de larga duración mediante la API de invocación {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

El siguiente ejemplo de código Java representa el servlet Java que invoca la variable `FirstAppSolution/PreLoanProcess` proceso.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 
     * (Because this  quick start is implemented as a Java servlet, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     * */ 
 import java.io.ByteArrayOutputStream; 
 import java.io.File; 
 import java.io.IOException; 
 import java.io.PrintWriter; 
  
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import javax.xml.parsers.DocumentBuilder; 
 import javax.xml.parsers.DocumentBuilderFactory; 
 import javax.xml.transform.Transformer; 
 import javax.xml.transform.TransformerFactory; 
 import javax.xml.transform.dom.DOMSource; 
 import javax.xml.transform.stream.StreamResult; 
  
 import com.adobe.idp.dsc.InvocationRequest; 
 import com.adobe.idp.dsc.InvocationResponse; 
 import com.adobe.idp.dsc.clientsdk.ServiceClient; 
 import org.w3c.dom.Element; 
  
     public class SubmitXML extends javax.servlet.http.HttpServlet implements javax.servlet.Servlet { 
       static final long serialVersionUID = 1L; 
      
        public SubmitXML() { 
         super(); 
     }        
      
      
     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
         // TODO Auto-generated method stub 
         doPost(request,response); 
     }       
      
     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
                  
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Create a ServiceClient object 
             ServiceClient myServiceClient = myFactory.getServiceClient(); 
              
             //Get the values that are passed from the Loan HTML page 
             String name = (String)request.getParameter("name"); 
             String phone = (String)request.getParameter("phone"); 
             String amount = (String)request.getParameter("amount"); 
                  
             //Create XML to pass to the FirstAppSolution/PreLoanProcess process 
             org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                                  
             //Create a Map object to store the XML input parameter value 
             Map params = new HashMap(); 
             params.put("formData", inXML);  
              
             //Create an InvocationRequest object 
             InvocationRequest lcRequest =  myFactory.createInvocationRequest( 
                 "FirstAppSolution/PreLoanProcess", //Specify the long-lived process name 
                     "invoke",           //Specify the operation name     
                     params,               //Specify input values 
                     false);               //Create an asynchronous request  
              
             //Send the invocation request to the long-lived process and  
             //get back an invocation response object 
             InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
             String invocationId = lcResponse.getInvocationId(); 
  
             //Create a PrintWriter instance 
             PrintWriter pp = response.getWriter();      
              
             //Write the invocation identifier value back to the client web browser 
             pp.println("The job status identifier value is: " +invocationId); 
              
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
      
      
      //Create XML data to pass to the long-lived process 
      private static org.w3c.dom.Document GetDataSource(String name, String phone, String amount) 
      { 
             org.w3c.dom.Document document = null; 
              
             try 
             { 
                 //Create DocumentBuilderFactory and DocumentBuilder objects 
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                 DocumentBuilder builder = factory.newDocumentBuilder(); 
  
                 //Create a new Document object 
                 document = builder.newDocument();  
  
                 //Create MortgageApp - the root element in the XML  
                 Element root = (Element)document.createElement("LoanApp"); 
                 document.appendChild(root); 
                                              
                 //Create an XML element for Name 
                 Element nameElement = (Element)document.createElement("Name"); 
                 nameElement.appendChild(document.createTextNode(name)); 
                 root.appendChild(nameElement); 
                  
                 //Create an XML element for Phone 
                 Element phoneElement = (Element)document.createElement("PhoneOrEmail"); 
                 phoneElement.appendChild(document.createTextNode(phone)); 
                 root.appendChild(phoneElement); 
                  
                 //Create an XML element for amount 
                 Element loanElement = (Element)document.createElement("LoanAmount"); 
                 loanElement.appendChild(document.createTextNode(amount)); 
                 root.appendChild(loanElement); 
  
                 //Create an XML element for ApprovalStatus 
                 Element approveElement = (Element)document.createElement("ApprovalStatus"); 
                 approveElement.appendChild(document.createTextNode("PENDING APPROVAL")); 
                 root.appendChild(approveElement); 
                                  
               } 
          catch (Exception e) { 
                   System.out.println("The following exception occurred: "+e.getMessage()); 
                } 
         return document; 
          } 
         }
```

### Crear la página web para la aplicación web {#create-the-web-page-for-the-web-application}

La página web * index.html * proporciona un punto de entrada al servlet Java que invoca la variable `FirstAppSolution/PreLoanProcess` proceso. Esta página web es un formulario HTML básico que contiene un formulario HTML y un botón de envío. Cuando el usuario hace clic en el botón de envío, los datos del formulario se publican en la `SubmitXML` servlet Java.

El servlet Java captura los datos que se publican desde la página HTML mediante el siguiente código Java:

```as3
 //Get the values that are passed from the Loan HTML page 
 String name = request.getParameter("name"); 
 String phone = request.getParameter("phone"); 
 String amount = request.getParameter("amount");
```

El siguiente código de HTML representa el archivo index.html que se creó durante la configuración del entorno de desarrollo. (Consulte [Creación de un proyecto web](invoking-human-centric-long-lived.md#create-a-web-project).)

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "https://www.w3.org/TR/html4/loose.dtd"> 
 <html> 
 <head> 
 <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1"> 
 <title>Insert title here</title> 
 </head> 
 <body> 
 <table> 
     <TBODY> 
         <TR> 
             <td><img src="financeCorpLogo.jpg" width="172" height="62"></TD> 
             <td><FONT size="+2"><strong>Java Loan Application Page</strong></FONT></TD> 
             <td> </TD> 
             <td> </TD> 
         </TR> 
          
     </TBODY> 
 </TABLE> 
     <FORM action="https://hiro-xp:8080/PreLoanProcess/SubmitXML" method="post"> 
        <table> 
          <TBODY> 
                <TR> 
                      <td><LABEL for="name">Name: </LABEL></TD> 
                  <td><INPUT type="text" name="name"></TD> 
                  <td><input type="submit" value="Submit Application"></TD> 
                  </TR> 
            <TR> 
                  <td> <LABEL for="phone">Phone/Email: </LABEL></TD> 
              <td><INPUT type="text" name="phone"></TD> 
                  <td></TD> 
              </TR> 
  
            <TR> 
                  <td><LABEL for="amount">Amount: </LABEL></TD> 
              <td><INPUT type="text" name="amount"></TD> 
                 <td></TD> 
             </TR> 
          </TBODY> 
 </TABLE> 
       </FORM> 
 </body> 
 </html>
```

### Empaquete la aplicación web a un archivo WAR {#package-the-web-application-to-a-war-file}

Para implementar el servlet Java que invoca la variable `FirstAppSolution/PreLoanProcess` procesar, empaquetar la aplicación web en un archivo WAR. Asegúrese de que los archivos JAR externos de los que depende la lógica empresarial del componente, como adobe-livecycle-client.jar y adobe-usermanager-client.jar, también estén incluidos en el archivo WAR.

La siguiente ilustración muestra el contenido del proyecto Eclipse, que se empaqueta en un archivo WAR.

>[!NOTE]
>
>En la ilustración anterior, el archivo de JPG se puede reemplazar por cualquier archivo de imagen de JPG.

**Empaquete una aplicación web a un archivo WAR:**

1. En el **Explorador de proyectos** haga clic con el botón derecho en la ventana `InvokePreLoanProcess` proyecto y seleccione **Exportar** > **Archivo WAR**.
1. En el **Módulo web** cuadro de texto, escriba `InvokePreLoanProcess` para el nombre del proyecto Java.
1. En el **Destino** cuadro de texto, escriba `PreLoanProcess.war`**para el** nombre de archivo, especifique la ubicación del archivo WAR y, a continuación, haga clic en Finalizar.

### Implementar el archivo WAR en el servidor de aplicaciones J2EE que hospeda AEM Forms {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Implemente el archivo WAR en el servidor de aplicaciones J2EE en el que se implementa AEM Forms. Para implementar el archivo WAR en el servidor de aplicaciones J2EE, copie el archivo WAR de la ruta de exportación a *[Instalación de AEM Forms]*\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy.

>[!NOTE]
>
>si AEM Forms no está implementado en JBoss, entonces debe implementar el archivo WAR de acuerdo con el servidor de aplicaciones J2EE que hospeda AEM Forms.

### Probar la aplicación web {#test-your-web-application}

Después de implementar la aplicación web, puede probarla con un explorador web. Suponiendo que esté utilizando el mismo equipo que aloja AEM Forms, puede especificar la siguiente URL:

* http://localhost:8080/PreLoanProcess/index.html

   Introduzca valores en los campos del formulario del HTML y haga clic en el botón Submit Application . Si se producen problemas, consulte el archivo de registro del servidor de aplicaciones J2EE.

   >[!NOTE]
   >
   >Para confirmar que la aplicación Java invocó el proceso, inicie Workspace y acepte el préstamo.

## Creación de una aplicación web ASP.NET que invoque un proceso prolongado centrado en el ser humano {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

Puede crear una aplicación ASP.NET que invoque la variable `FirstAppSolution/PreLoanProcess` proceso. Para invocar este proceso desde una aplicación ASP.NET, utilice los servicios Web. (Consulte [Invocación de AEM Forms mediante servicios web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

La siguiente ilustración muestra una aplicación cliente ASP.NET que obtiene datos de un usuario final. Los datos se colocan en un origen de datos XML y se envían a la variable `FirstAppSolution/PreLoanProcess` proceso cuando el usuario hace clic en el botón Enviar aplicación.

Una vez invocado el proceso, se muestra un valor de identificador de invocación. Se crea un valor de identificador de invocación como parte de un registro que rastrea el estado del proceso de larga duración.

La aplicación ASP.NET realiza las siguientes tareas:

* Recupera los valores introducidos por el usuario en la página web.
* Crea dinámicamente un origen de datos XML que se pasa al proceso* FirstAppSolution/PreLoanProcess *. Los tres valores se especifican en el origen de datos XML.
* Invoca el proceso* FirstAppSolution/PreLoanProcess *mediante los servicios web.
* Devuelve el valor del identificador de invocación y el estado de la operación de larga duración en el explorador web del cliente.

### Resumen de los pasos {#summary_of_steps-1}

Para crear una aplicación ASP.NET que pueda invocar el proceso FirstAppSolution/PreLoanProcess, realice los siguientes pasos:

1. [Crear una aplicación web ASP.NET](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Crear una página ASP que invoque FirstAppSolution/PreLoanProcess](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess).
1. [Ejecutar la aplicación ASP.NET](invoking-human-centric-long-lived.md#run-the-asp-net-application).

### Crear una aplicación web ASP.NET {#create-an-asp-net-web-application}

Cree una aplicación web ASP.NET .NET C# de Microsoft. La siguiente ilustración muestra el contenido del proyecto ASP.NET denominado *InvokePreLoanProcess*.

Aviso en Referencias de servicio, hay dos artículos. El primer elemento se llama* JobManager*. Esta referencia permite que la aplicación ASP.NET invoque el servicio Administrador de trabajos. Este servicio devuelve información sobre el estado de un proceso de larga duración. Por ejemplo, si el proceso se está ejecutando actualmente, este servicio devuelve un valor numérico que especifica que el proceso se está ejecutando. El nombre de la segunda referencia es *PreLoanProcess*. Esta referencia de servicio representa la referencia al proceso* FirstAppSolution/PreLoanProcess *. Después de crear una referencia de servicio, los tipos de datos asociados con el servicio AEM Forms están disponibles para su uso en el proyecto .NET.

**Crear un proyecto de ASP.NET:**

1. Inicie Microsoft Visual Studio 2008.
1. En el **Archivo** seleccione **Nuevo**, **Sitio web**.
1. En el **Plantillas** lista, seleccionar **Sitio Web ASP.NET**.
1. En el **Ubicación** seleccione una ubicación para el proyecto. Asigne un nombre al proyecto *InvokePreLoanProcess*.
1. En el **Idioma** , seleccione Visual C#
1. Haga clic en Aceptar.

**Añadir referencias de servicio:**

1. En el menú Proyecto, seleccione **Agregar referencia de servicio**.
1. En el **Dirección** , especifique el WSDL en el servicio Administrador de trabajos.

   ```as3
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. En el campo Área de nombres, escriba `JobManager`.
1. Haga clic en **Ir** y haga clic en **OK**.
1. En el **Proyecto** seleccione **Agregar referencia de servicio**.
1. En el **Dirección** , especifique el WSDL en el proceso FirstAppSolution/PreLoanProcess.

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. En el campo Área de nombres, escriba `PreLoanProcess`.
1. Haga clic en **Ir** y haga clic en **OK**.

>[!NOTE]
>
>Reemplazar `hiro-xp` con la dirección IP del servidor de aplicaciones J2EE que hospeda AEM Forms. La variable `lc_version` garantiza que la funcionalidad de AEM Forms, como MTOM, esté disponible. Sin especificar la variable `lc_version`no puede invocar AEM Forms mediante MTOM. (Consulte [Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

### Crear una página ASP que invoque FirstAppSolution/PreLoanProcess {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

Dentro del proyecto ASP.NET, agregue un formulario web (un archivo ASPX) que sea responsable de mostrar una página HTML al solicitante del préstamo. El formulario web se basa en una clase derivada de `System.Web.UI.Page`. La lógica de aplicación C# que invoca `FirstAppSolution/PreLoanProcess` se encuentra en el `Button1_Click` (este botón representa el botón Enviar aplicación).

La siguiente ilustración muestra la aplicación ASP.NET

En la tabla siguiente se enumeran los controles que forman parte de esta aplicación ASP.NET.

<table> 
 <thead> 
  <tr> 
   <th><p>Nombre de control</p></th> 
   <th><p>Descripción</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>TextBoxName</p></td> 
   <td><p>Especifica el nombre y los apellidos del cliente. </p></td> 
  </tr> 
  <tr> 
   <td><p>TextBoxPhone</p></td> 
   <td><p>Especifica el teléfono o la dirección de correo electrónico del cliente. </p></td> 
  </tr> 
  <tr> 
   <td><p>TextBoxAmount</p></td> 
   <td><p>Especifica el importe del préstamo.</p></td> 
  </tr> 
  <tr> 
   <td><p>Button1</p></td> 
   <td><p>Representa el botón Enviar aplicación.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelJobID</p></td> 
   <td><p>Un control Label que especifica el valor del valor del identificador de invocación.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelStatus</p></td> 
   <td><p>Un control Label que especifica el valor del estado del trabajo. Este valor se recupera invocando el servicio Administrador de trabajos. </p></td> 
  </tr> 
 </tbody> 
</table>

La lógica de aplicación que forma parte de la aplicación ASP.NET debe crear dinámicamente un origen de datos XML para pasarlo al `FirstAppSolution/PreLoanProcess` proceso. Los valores introducidos por el solicitante en la página HTML deben especificarse en el origen de datos XML. Estos valores de datos se combinan en el formulario cuando se visualiza en Workspace. Las clases ubicadas en la variable `System.Xml` namespace se utilizan para crear el origen de datos XML.

Al invocar un proceso que requiere datos XML de una aplicación ASP.NET, hay un tipo de datos XML disponible para su uso. Es decir, no puede pasar un `System.Xml.XmlDocument` al proceso. El nombre completo de esta instancia XML para pasar al proceso es `InvokePreLoanProcess.PreLoanProcess.XML`. Convertir el `System.Xml.XmlDocument` instancia a `InvokePreLoanProcess.PreLoanProcess.XML`. Puede realizar esta tarea utilizando el siguiente código.

```as3
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
 XmlDocument myXML = CreateXML(userName, phone, amount); 
      
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance 
 StringWriter sw = new StringWriter(); 
 XmlTextWriter xw = new XmlTextWriter(sw); 
 myXML.WriteTo(xw); 
  
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
 inXML.document = sw.ToString();
```

Para crear una página ASP que invoque la variable `FirstAppSolution/PreLoanProcess` realice las siguientes tareas en la `Button1_Click` método:

1. Cree un `FirstAppSolution_PreLoanProcessClient` usando su constructor predeterminado.
1. Cree un `FirstAppSolution_PreLoanProcessClient.Endpoint.Address` usando la variable `System.ServiceModel.EndpointAddress` constructor. Pase un valor de cadena que especifique el WSDL al servicio de AEM Forms y el tipo de codificación:

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   No es necesario que use la variable `lc_version` atributo. Este atributo se utiliza al crear una referencia de servicio. Sin embargo, asegúrese de especificar `?blob=mtom`.

   >[!NOTE]
   >
   >Reemplazar `hiro-xp`* con la dirección IP del servidor de aplicaciones J2EE que aloja AEM Forms. *

1. Cree un `System.ServiceModel.BasicHttpBinding` obteniendo el valor de `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` miembro de datos. Conversión del valor devuelto a `BasicHttpBinding`.
1. Configure las variables `System.ServiceModel.BasicHttpBinding` del objeto `MessageEncoding` miembro de datos a `WSMessageEncoding.Mtom`. Este valor garantiza que se utilice MTOM.
1. Habilite la autenticación HTTP básica realizando las siguientes tareas:

   * Asignar el nombre de usuario de los formularios AEM al miembro de datos `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName`.
   * Asignar el valor de contraseña correspondiente al miembro de datos `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password`.
   * Asignar el valor constante `HttpClientCredentialType.Basic` al miembro de datos `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Asignar el valor constante `BasicHttpSecurityMode.TransportCredentialOnly` al miembro de datos `BasicHttpBindingSecurity.Security.Mode`.

   El siguiente ejemplo de código muestra estas tareas.

   ```as3
    //Enable BASIC HTTP authentication 
    BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
    b.MessageEncoding = WSMessageEncoding.Mtom; 
    mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
    mortgageClient.ClientCredentials.UserName.Password = "password"; 
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
    b.MaxReceivedMessageSize = 2000000; 
    b.MaxBufferSize = 2000000; 
    b.ReaderQuotas.MaxArrayLength = 2000000;
   ```

1. Recupere los valores de nombre, teléfono y cantidad que el usuario introdujo en la página web. Utilice estos valores para crear dinámicamente un origen de datos XML que se envíe a la variable `FirstAppSolution/PreLoanProcess` proceso. Cree un `System.Xml.XmlDocument` que representa el origen de datos XML que se pasará al proceso (esta lógica de aplicación se muestra en el siguiente ejemplo de código).
1. Convertir el `System.Xml.XmlDocument` instancia a `InvokePreLoanProcess.PreLoanProcess.XML` (esta lógica de aplicación se muestra en el siguiente ejemplo de código).
1. Invocar el `FirstAppSolution/PreLoanProcess` proceso invocando la variable `FirstAppSolution_PreLoanProcessClient` del objeto `invoke_Async` método. Este método devuelve un valor de cadena que representa el valor del identificador de invocación del proceso de larga duración.
1. Cree un `JobManagerClient` usando un constructor. (Asegúrese de haber establecido una referencia de servicio al servicio Administrador de trabajos).
1. Repita los pasos del 1 al 5. Especifique la siguiente URL para el paso 2: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Cree un `JobId` usando su constructor.
1. Configure las variables `JobId` del objeto `id` miembro de datos con el valor devuelto de la variable `FirstAppSolution_PreLoanProcessClient` del objeto `invoke_Async` método.
1. Asigne la variable `value` true para la variable `JobId` del objeto `persistent` miembro de datos.
1. Cree un `JobStatus` invocando el objeto `JobManagerService` objeto `getStatus` y pasando el `JobId` objeto.
1. Obtenga el valor del estado recuperando el valor de la variable `JobStatus` del objeto `statusCode` miembro de datos.
1. Asigne el valor del identificador de invocación al `LabelJobID.Text` campo .
1. Asigne el valor de estado a la variable `LabelStatus.Text` campo .

### Inicio rápido: Invocación de un proceso de larga duración mediante la API de servicio web {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

El siguiente ejemplo de código C# invoca la variable `FirstAppSolution/PreLoanProcess`proceso.

```as3
 ???/** 
     * Ensure that you create a .NET project that uses  
     * MS Visual Studio 2008 and version 3.5 of the .NET 
     * framework. This is required to invoke a  
     * AEM Forms service using MTOM. 
      
  
 using System; 
 using System.Collections; 
 using System.Configuration; 
 using System.Data; 
 using System.Linq; 
 using System.Web; 
 using System.ServiceModel; 
 using System.Web.Security; 
 using System.Web.UI; 
 using System.Web.UI.HtmlControls; 
 using System.Web.UI.WebControls; 
 using System.Web.UI.WebControls.WebParts; 
 using System.Xml.Linq; 
 using System.Xml; 
 using System.IO; 
  
 //A reference to FirstAppSolution/PreLoanProcess 
 using InvokePreLoanProcess.PreLoanProcess; 
  
 //A reference to JobManager service 
 using InvokePreLoanProcess.JobManager; 
  
  
 namespace InvokePreLoanProcess 
 { 
        public partial class _Default : System.Web.UI.Page 
        { 
            //This method is called when the Submit Application button is  
            //Clicked 
            protected void Button1_Click(object sender, EventArgs e) 
            { 
                //Create a FirstAppSolution_PreLoanProcessClient object 
                FirstAppSolution_PreLoanProcessClient mortgageClient = new FirstAppSolution_PreLoanProcessClient(); 
                mortgageClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
                b.MessageEncoding = WSMessageEncoding.Mtom; 
                mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
                mortgageClient.ClientCredentials.UserName.Password = "password"; 
                b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b.MaxReceivedMessageSize = 2000000; 
                b.MaxBufferSize = 2000000; 
                b.ReaderQuotas.MaxArrayLength = 2000000; 
      
                //Retrieve values that user entered into the web page 
                String userName = TextBoxName.Text; 
                String phone = TextBoxPhone.Text; 
                String amount = TextBoxAmount.Text; 
  
                //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument myXML = CreateXML(userName, phone, amount); 
      
                StringWriter sw = new StringWriter(); 
                XmlTextWriter xw = new XmlTextWriter(sw); 
                myXML.WriteTo(xw); 
  
                InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
                inXML.document = sw.ToString();  
  
                //INvoke the FirstAppSolution/PreLoanProcess process 
                String invocationID =  mortgageClient.invoke_Async(inXML); 
  
                //Create a JobManagerClient object to obtain the status of the long-lived operation 
                JobManagerClient jobManager = new JobManagerClient(); 
                jobManager.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/JobManager?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b1 = (BasicHttpBinding)jobManager.Endpoint.Binding; 
                b1.MessageEncoding = WSMessageEncoding.Mtom; 
                jobManager.ClientCredentials.UserName.UserName = "administrator"; 
                jobManager.ClientCredentials.UserName.Password = "password"; 
                b1.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b1.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b1.MaxReceivedMessageSize = 2000000; 
                b1.MaxBufferSize = 2000000; 
                b1.ReaderQuotas.MaxArrayLength = 2000000; 
  
  
                //Create a JobID object that represents the status of the  
                //long-lived operation 
                JobId jobId = new JobId(); 
                jobId.id = invocationID; 
                jobId.persistent = true; 
                JobStatus jobStatus = jobManager.getStatus(jobId); 
                System.Int16 val2 = jobStatus.statusCode; 
                LabelJobID.Text = "The job status identifier value is " + invocationID;   
                LabelStatus.Text = "The status of the long-lived operation is " + getJobDescription(val2);  
      
            } 
  
            private static XmlDocument CreateXML(String name, String phone, String amount) 
            { 
                //This method dynamically creates a DDX document  
                //to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument xmlDoc = new XmlDocument(); 
  
                //Create the root element and append it to the XML DOM         
                System.Xml.XmlElement root = xmlDoc.CreateElement("LoanApp"); 
                xmlDoc.AppendChild(root); 
  
                //Create the Name element 
                XmlElement nameElement = xmlDoc.CreateElement("Name"); 
                nameElement.AppendChild(xmlDoc.CreateTextNode(name)); 
                root.AppendChild(nameElement); 
  
                //Create the LoanAmount element 
                XmlElement LoanAmount = xmlDoc.CreateElement("LoanAmount"); 
                LoanAmount.AppendChild(xmlDoc.CreateTextNode(amount)); 
                root.AppendChild(LoanAmount); 
  
                //Create the PhoneOrEmail element 
                XmlElement PhoneOrEmail = xmlDoc.CreateElement("PhoneOrEmail"); 
                PhoneOrEmail.AppendChild(xmlDoc.CreateTextNode(phone)); 
                root.AppendChild(PhoneOrEmail); 
  
                //Create the ApprovalStatus element 
                XmlElement ApprovalStatus = xmlDoc.CreateElement("ApprovalStatus"); 
                ApprovalStatus.AppendChild(xmlDoc.CreateTextNode("PENDING APPROVAL")); 
                root.AppendChild(ApprovalStatus); 
  
                //Return the XmlElement instance 
                return xmlDoc; 
            } 
  
  
            //Returns the String value of the Job Manager status code 
            private String getJobDescription(int val) 
            { 
                switch(val) 
                { 
                    case 0: 
                        return "JOB_STATUS_UNKNOWN"; 
      
                    case 1:  
                        return "JOB_STATUS_QUEUED"; 
  
                    case 2:  
                        return "JOB_STATUS_RUNNING"; 
  
                    case 3:  
                        return "JOB_STATUS_COMPLETED";   
      
                    case 4:  
                        return "JOB_STATUS_FAILED";  
  
                     case 5:  
                        return "JOB_STATUS_COMPLETED";  
      
                    case 6:  
                        return "JOB_STATUS_SUSPENDED"; 
      
                    case 7:  
                        return "JOB_STATUS_COMPLETE_REQUESTED"; 
      
                    case 8:  
                        return "JOB_STATUS_TERMINATE_REQUESTED"; 
  
                     case 9:  
                        return "JOB_STATUS_SUSPEND_REQUESTED"; 
  
                       case 10:  
                        return "JOB_STATUS_RESUME_REQUESTED"; 
                } 
  
                return ""; 
            } 
       } 
 } 
 
```

>[!NOTE]
>
>Los valores ubicados en el método definido por el usuario getJobDescription corresponden a los valores devueltos por el servicio Administrador de trabajos.

### Ejecutar la aplicación ASP.NET {#run-the-asp-net-application}

Después de compilar e implementar la aplicación ASP.NET, puede ejecutarla con un explorador Web. Asumiendo que el nombre del proyecto ASP.NET es *InvokePreLoanProcess*, especifique la siguiente URL en un explorador web:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

donde localhost es el nombre del servidor web que aloja el proyecto ASP.NET y 1629 es el número de puerto. Al compilar y crear la aplicación ASP.NET, Microsoft Visual Studio la implementa automáticamente.

>[!NOTE]
>
>Para confirmar que la aplicación ASP.NET invocó el proceso, inicie Workspace y acepte el préstamo.

## Creación de una aplicación cliente creada con Flex que invoca un proceso prolongado centrado en el ser humano {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

Puede crear una aplicación de cliente creada con Flex para invocar la variable *FirstAppSolution/PreLoanProcess* proceso. Esta aplicación utiliza Remoting para invocar la variable *FirstAppSolution/PreLoanProcess* proceso. (Consulte [Invocación de AEM Forms mediante AEM Forms Remoting (obsoleto para formularios AEM)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

La siguiente ilustración muestra una aplicación cliente creada con Flex que recopila datos de un usuario final. Los datos se colocan en un origen de datos XML y se envían al proceso.

Una vez invocado el proceso, se muestra un valor de identificador de invocación. Se crea un valor de identificador de invocación como parte de un registro que rastrea el estado del proceso de larga duración.

La aplicación cliente creada con Flex realiza las siguientes tareas:

* Recupera los valores introducidos por el usuario en la página web.
* Crea dinámicamente un origen de datos XML que se pasa al *FirstAppSolution/PreLoanProcess* proceso. Los tres valores se especifican en el origen de datos XML.
* Invoca el *FirstAppSolution/PreLoanProcess* procesar mediante Remoting.
* Devuelve el valor del identificador de invocación del proceso de larga duración.

### Resumen de los pasos {#summary_of_steps-2}

Para crear una aplicación cliente creada con Flex que pueda invocar el proceso FirstAppSolution/PreLoanProcess, realice los siguientes pasos:

1. Inicie un nuevo proyecto de Flex.
1. Incluya el archivo adobe-remoting-provider.swc en la ruta de clase de su proyecto. (Consulte [Inclusión del archivo de biblioteca Flex de AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Cree un `mx:RemoteObject` mediante ActionScript o MXML. (Consulte [Creación de una instancia mx:RemoteObject](/help/forms/developing/invoking-aem-forms-using-remoting.md))
1. Configure un `ChannelSet` para comunicarse con AEM Forms y asociarla con el `mx:RemoteObject` instancia. (Consulte [Creación de un canal en AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Llame al evento ChannelSet `login` para el método de `setCredentials` para especificar el valor del identificador de usuario y la contraseña. (Consulte [Uso del inicio de sesión único](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Cree el origen de datos XML para pasarlo a la variable `FirstAppSolution/PreLoanProcess` procesar creando una instancia XML. (Esta lógica de aplicación se muestra en el siguiente ejemplo de código).
1. Cree un objeto de tipo Object usando su constructor. Asigne el XML al objeto especificando el nombre del parámetro de entrada del proceso, como se muestra en el siguiente código:

   ```as3
    //Get the XML data to pass to the AEM Forms process 
    var xml:XML = createXML(); 
    var params:Object = new Object(); 
    params["formData"]=xml;
   ```

1. Invocar el `FirstAppSolution/PreLoanProcess` para ello, llame a la función `mx:RemoteObject` del `invoke_Async` método. Pase el `Object` que contiene el parámetro de entrada. (Consulte [Pasar valores de entrada](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Recupere el valor de identificación de invocación que se devuelve desde un proceso de larga duración, como se muestra en el siguiente código:

   ```as3
    // Handles async call that invokes the long-lived process 
    private function resultHandler(event:ResultEvent):void 
    { 
    ji = event.result as JobId; 
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
    }
   ```

### Invocación de un proceso de larga duración mediante Remoting {#invoking-a-long-lived-process-using-remoting}

El siguiente ejemplo de código Flex invoca la variable `FirstAppSolution/PreLoanProcess` proceso.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
  
 <mx:Application  xmlns="*" backgroundColor="#FFFFFF"  
      creationComplete="initializeChannelSet();"> 
  
 <mx:Script> 
          <![CDATA[ 
  
             import mx.controls.Alert; 
             import mx.rpc.events.FaultEvent; 
             import mx.rpc.events.ResultEvent; 
             import flash.net.navigateToURL; 
             import mx.messaging.ChannelSet; 
             import mx.messaging.channels.AMFChannel; 
             import mx.collections.ArrayCollection; 
             import mx.rpc.livecycle.JobId; 
             import mx.rpc.livecycle.JobStatus; 
             import mx.rpc.livecycle.DocumentReference; 
             import mx.formatters.NumberFormatter; 
      
             // Holds the job ID returned by LC.JobManager 
             private var ji:JobId;   
      
             private function initializeChannelSet():void  
              { 
              var cs:ChannelSet= new ChannelSet();  
         cs.addChannel(new AMFChannel("remoting-amf", "https://hiro-xp:8080/remoting/messagebroker/amf"));  
         LC_MortgageApp.setCredentials("tblue", "password"); 
         LC_MortgageApp.channelSet = cs; 
              } 
  
            private function submitApplication():void 
             { 
             //Get the XML data to pass to the AEM Forms process 
             var xml:XML = createXML(); 
             var params:Object = new Object(); 
             params["formData"]=xml; 
             LC_MortgageApp.invoke_Async(params); 
             } 
  
             // Handles async call that invokes the long-lived process 
             private function resultHandler(event:ResultEvent):void 
             { 
                ji = event.result as JobId; 
                jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
             } 
  
             private function createXML():XML 
             { 
                //Calculate the Mortgage value to place in the XML data 
                var propertyPrice:String = txtAmount.text ;  
                var name:String = txtName.text ; 
                var phone:String = txtPhone.text ;;  
      
                var model:XML =  
  
                  <LoanApp> 
                           <Name>{name}</Name> 
                           <LoanAmount>{propertyPrice}</LoanAmount> 
                           <PhoneOrEmail>{phone}</PhoneOrEmail>  
                           <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
                  </LoanApp> 
      
              return model; 
             } 
      
      
          ]]> 
       </mx:Script> 
      
       <!-- Declare the RemoteObject and set its destination to the mortgage-app remoting endpoint defined in AEM Forms. --> 
       <mx:RemoteObject id="LC_MortgageApp" destination="FirstAppSolution/PreLoanProcess" result="resultHandler(event);"> 
          <mx:method name="invoke_Async" result="resultHandler(event)"/> 
      </mx:RemoteObject> 
  
  
     <mx:Grid x="229" y="186"> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Image> 
                     <mx:source>file:///D|/LiveCycle_9/FirstApp/financeCorpLogo.jpg</mx:source> 
                 </mx:Image> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Flex Loan Application Page" fontSize="20"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Name:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtName"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Button label="Submit Application" click="submitApplication()"/> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Phone/Email:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtPhone"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Amount:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtAmount"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Label" id="jobStatusDisplay" enabled="true" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
     </mx:Grid> 
      
 </mx:Application> 
 
```
