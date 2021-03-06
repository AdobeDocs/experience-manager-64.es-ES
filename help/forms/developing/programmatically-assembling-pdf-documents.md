---
title: Montaje programático de documentos PDF
seo-title: Montaje programático de documentos PDF
description: Utilice la API del servicio Assembler para ensamblar varios documentos PDF en un único documento PDF utilizando la API de Java y la API del servicio Web.
seo-description: Utilice la API del servicio Assembler para ensamblar varios documentos PDF en un único documento PDF utilizando la API de Java y la API del servicio Web.
uuid: aa3f8f39-1fbc-48d0-82ff-6caaadf125fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: ebe8136b-2a79-4035-b9d5-aa70a5bbd4af
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Ensamblaje programático de documentos PDF {#programmatically-assembling-pdf-documents}

Puede utilizar la API del servicio Assembler para ensamblar varios documentos PDF en un único documento PDF. La siguiente ilustración muestra tres documentos PDF que se están combinando en un solo documento PDF.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

Para ensamblar dos o más documentos PDF en un solo documento PDF, se necesita un documento DDX. Un documento DDX describe el documento PDF que produce el servicio Assembler. Es decir, el documento DDX indica al servicio Assembler qué acciones realizar.

A los efectos de esta discusión, supongamos que se utiliza el siguiente documento DDX.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
     <PDF result="out.pdf"> 
         <PDF source="map.pdf" /> 
         <PDF source="directions.pdf" /> 
     </PDF> 
 </DDX>
```

Este documento DDX combina dos documentos PDF llamados *map.pdf* y *addresses.pdf* en un solo documento PDF.

>[!NOTE]
>
>Para ver un documento DDX que desmonta un documento PDF, consulte [Desensamblaje programático de documentos PDF](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Para obtener más información sobre el servicio Assembler, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Para obtener más información sobre un documento DDX, consulte [Servicio de ensamblador y referencia DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Consideraciones al invocar el servicio Assembler mediante servicios Web {#considerations-when-invoking-assembler-service-using-web-services}

Cuando se añaden encabezados y pies de página durante el ensamblaje de documentos grandes, es posible que se produzca un error `OutOfMemory` y que los archivos no se ensamblen. Para reducir la probabilidad de que este problema ocurra, añada un elemento `DDXProcessorSetting` al documento DDX, como se muestra en el siguiente ejemplo.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

Puede agregar este elemento como secundario del elemento `DDX` o como secundario de un elemento `PDF result`. El valor predeterminado de esta configuración es 0 (cero), que desactiva la selección y el DDX se comporta como si el elemento `DDXProcessorSetting` no estuviera presente. Si ha encontrado un error `OutOfMemory`, es posible que tenga que establecer el valor en un número entero, normalmente entre 500 y 5000. Un valor pequeño de punto de comprobación resulta en comprobaciones más frecuentes.

## Resumen de los pasos {#summary-of-steps}

Para ensamblar un solo documento PDF de varios documentos PDF, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un cliente del ensamblador PDF.
1. Haga referencia a un documento DDX existente.
1. Haga referencia a documentos PDF de entrada.
1. Establezca las opciones de tiempo de ejecución.
1. Ensamble los documentos PDF de entrada.
1. Extraiga los resultados.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en JBoss)

si AEM Forms se implementa en un servidor de aplicaciones J2EE compatible que no sea JBoss, debe reemplazar los archivos adobe-Utilities.jar y jbossall-client.jar con archivos JAR específicos del servidor de aplicaciones J2EE en el que se implementa AEM Forms.

**Crear un cliente de ensamblador PDF**

Para poder realizar una operación Assembler mediante programación, debe crear un cliente Assembler.

**Referencia a un documento DDX existente**

Se debe hacer referencia a un documento DDX para ensamblar un documento PDF. Por ejemplo, considere el documento DDX que se introdujo en esta sección. Este documento DDX ordena al servicio Assembler que combine dos documentos PDF en un único documento PDF.

**Documentos PDF de entrada de referencia**

Haga referencia a los documentos PDF de entrada que desee pasar al servicio Assembler. Por ejemplo, si desea pasar dos documentos PDF de entrada llamados Mapa y Direcciones, debe pasar los archivos PDF correspondientes.

Tanto el archivo map.pdf como el archivo addresses.pdf deben colocarse en un objeto de colección. El nombre de la clave debe coincidir con el valor del atributo de origen PDF del documento DDX. No importa cuál sea el nombre del archivo PDF si coinciden la clave y el atributo de origen del documento DDX.

>[!NOTE]
>
>Se devuelve un objeto `*AssemblerResult*`, que contiene un objeto de colección, si invoca la operación `*invokeDDX*`. Esta operación se utiliza cuando se pasan dos o más documentos PDF de entrada al servicio Assembler. Sin embargo, si sólo pasa un PDF de entrada al servicio Assembler y espera un solo documento devuelto, invoque la operación `*invokeOneDocument*`. Al invocar esta operación, se devuelve un solo documento. Para obtener información sobre el uso de esta operación, consulte [Agrupación de documentos PDF cifrados](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Establecer opciones de tiempo de ejecución**

Puede establecer opciones en tiempo de ejecución que controlan el comportamiento del servicio Assembler mientras realiza un trabajo. Por ejemplo, puede definir una opción que indique al servicio Assembler que continúe procesando un trabajo si se encuentra un error. Para obtener información sobre las opciones de tiempo de ejecución que puede establecer, consulte la referencia de clase `AssemblerOptionSpec` en [Referencia de API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Montaje de los documentos PDF de entrada**

Después de crear el cliente de servicio, hacer referencia a un archivo DDX, crear un objeto de colección que almacene documentos PDF de entrada y establecer opciones de tiempo de ejecución, puede invocar la operación DDX. Cuando se utiliza el documento DDX especificado en esta sección, los archivos map.pdf y address.pdf se combinan en un documento PDF.

**Extraer los resultados**

El servicio Assembler devuelve un objeto `java.util.Map`, que se puede obtener del objeto `AssemblerResult` y que contiene resultados de operación. El objeto `java.util.Map` devuelto contiene los documentos resultantes y cualquier excepción.

En la tabla siguiente se resumen algunos de los valores clave y tipos de objeto que se pueden encontrar en el objeto `java.util.Map` devuelto.

<table> 
 <thead> 
  <tr> 
   <th><p>Valor clave</p></th> 
   <th><p>Tipo de objeto</p></th> 
   <th><p>Descripción</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>com.adobe.idp.Document</code></p></td> 
   <td><p>Contiene los documentos resultantes especificados en un elemento resultante DDX</p></td> 
  </tr> 
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>Exception</code></p></td> 
   <td><p>Contiene cualquier excepción para el documento</p></td> 
  </tr> 
  <tr> 
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td> 
   <td><p><code>com.adobe.idp.Documen</code></p></td> 
   <td><p>Contiene el registro de trabajos</p></td> 
  </tr> 
 </tbody> 
</table>

**Consulte también**

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Desensamblar documentos PDF mediante programación](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Montaje de documentos PDF utilizando la API de Java {#assemble-pdf-documents-using-the-java-api}

Ensamble un documento PDF utilizando la API del servicio Assembler (Java):

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-assembler-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un cliente del ensamblador PDF.

   * Cree un objeto `ServiceClientFactory` que contenga propiedades de conexión.
   * Cree un objeto `AssemblerServiceClient` utilizando su constructor y pasando el objeto `ServiceClientFactory`.

1. Haga referencia a un documento DDX existente.

   * Cree un objeto `java.io.FileInputStream` que represente el documento DDX utilizando su constructor y pasando un valor de cadena que especifique la ubicación del archivo DDX.
   * Cree un objeto `com.adobe.idp.Document` utilizando su constructor y pasando el objeto `java.io.FileInputStream`.

1. Haga referencia a documentos PDF de entrada.

   * Cree un objeto `java.util.Map` que se utilice para almacenar documentos PDF de entrada mediante un constructor `HashMap`.
   * Para cada documento PDF de entrada, cree un objeto `java.io.FileInputStream` utilizando su constructor y pasando la ubicación del documento PDF de entrada.
   * Para cada documento PDF de entrada, cree un objeto `com.adobe.idp.Document` y pase el objeto `java.io.FileInputStream` que contiene el documento PDF.
   * Para cada documento de entrada, agregue una entrada al objeto `java.util.Map` invocando su método `put` y pasando los siguientes argumentos:

      * Un valor de cadena que representa el nombre de la clave. Este valor debe coincidir con el valor del elemento de origen PDF especificado en el documento DDX.
      * Un objeto `com.adobe.idp.Document` (o `java.util.List` objeto que especifica varios documentos) que contiene el documento PDF de origen.

1. Establezca las opciones de tiempo de ejecución.

   * Cree un objeto `AssemblerOptionSpec` que almacene opciones en tiempo de ejecución empleando su constructor.
   * Defina las opciones en tiempo de ejecución para satisfacer los requisitos empresariales invocando un método que pertenece al objeto `AssemblerOptionSpec` . Por ejemplo, para solicitar al servicio Assembler que continúe procesando un trabajo cuando se produce un error, invoque el método `AssemblerOptionSpec` del objeto `setFailOnError` y pase `false`.

1. Ensamble los documentos PDF de entrada.

   Invoque el método `AssemblerServiceClient` del objeto `invokeDDX` y pase los siguientes valores obligatorios:

   * Un objeto `com.adobe.idp.Document` que representa el documento DDX que se va a utilizar
   * Un objeto `java.util.Map` que contiene los archivos PDF de entrada que se van a ensamblar
   * Un objeto `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` que especifica las opciones de tiempo de ejecución, incluidos el nivel predeterminado de fuente y registro de trabajo

   El método `invokeDDX` devuelve un objeto `com.adobe.livecycle.assembler.client.AssemblerResult` que contiene los resultados del trabajo y cualquier excepción que se haya producido.

1. Extraiga los resultados.

   Para obtener el documento PDF recién creado, realice las siguientes acciones:

   * Invoque el método `AssemblerResult` del objeto `getDocuments`. Esto devuelve un objeto `java.util.Map`.
   * Repita el objeto `java.util.Map` hasta que encuentre el objeto `com.adobe.idp.Document` resultante. (Puede utilizar el elemento de resultado PDF especificado en el documento DDX para obtener el documento).
   * Invoque el método `com.adobe.idp.Document` del objeto `copyToFile` para extraer el documento PDF.

   >[!NOTE]
   >
   >Si `*LOG_LEVEL*` se configuró para producir un registro, puede extraer el registro utilizando el método `*AssemblerResult*` del objeto `*getJobLog*`.

**Consulte también**

[Inicio rápido (modo SOAP): Montaje de un documento PDF mediante la API de Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Montaje de documentos PDF utilizando la API de servicio Web {#assemble-pdf-documents-using-the-web-service-api}

Ensamble documentos PDF utilizando la API del servicio Assembler (servicio web):

1. Incluir archivos de proyecto.

   Cree un proyecto de Microsoft .NET que utilice MTOM. Asegúrese de utilizar la siguiente definición WSDL: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sustituya `localhost` por la dirección IP del servidor que hospeda AEM Forms.

1. Cree un cliente del ensamblador PDF.

   * Cree un objeto `AssemblerServiceClient` utilizando su constructor predeterminado.
   * Cree un objeto `AssemblerServiceClient.Endpoint.Address` utilizando el constructor `System.ServiceModel.EndpointAddress`. Pase un valor de cadena que especifique el WSDL al servicio de AEM Forms (por ejemplo, `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). No es necesario utilizar el atributo `lc_version`. Este atributo se utiliza al crear una referencia de servicio.
   * Cree un objeto `System.ServiceModel.BasicHttpBinding` obteniendo el valor del campo `AssemblerServiceClient.Endpoint.Binding`. Establezca el valor devuelto en `BasicHttpBinding`.
   * Establezca el campo `System.ServiceModel.BasicHttpBinding` del objeto `MessageEncoding` en `WSMessageEncoding.Mtom`. Este valor garantiza que se utilice MTOM.
   * Habilite la autenticación HTTP básica realizando las siguientes tareas:

      * Asigne el nombre de usuario de los formularios AEM al campo `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Asigne el valor de contraseña correspondiente al campo `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Asigne el valor constante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Asigne el valor constante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Haga referencia a un documento DDX existente.

   * Cree un objeto `BLOB` utilizando su constructor. El objeto `BLOB` se utiliza para almacenar el documento DDX.
   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo del documento DDX y el modo en que se abre el archivo.
   * Cree una matriz de bytes que almacene el contenido del objeto `System.IO.FileStream`. Puede determinar el tamaño de la matriz de bytes obteniendo la propiedad `System.IO.FileStream` del objeto `Length`.
   * Rellene la matriz de bytes con datos de flujo invocando el método `System.IO.FileStream` del objeto `Read` y pasando la matriz de bytes, la posición de inicio y la longitud de flujo para leer.
   * Rellene el objeto `BLOB` asignando su propiedad `MTOM` con el contenido de la matriz de bytes.

1. Haga referencia a documentos PDF de entrada.

   * Para cada documento PDF de entrada, cree un objeto `BLOB` utilizando su constructor. El objeto `BLOB` se utiliza para almacenar el documento PDF de entrada.
   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo del documento PDF de entrada y el modo en que se abre el archivo.
   * Cree una matriz de bytes que almacene el contenido del objeto `System.IO.FileStream`. Puede determinar el tamaño de la matriz de bytes obteniendo la propiedad `System.IO.FileStream` del objeto `Length`.
   * Rellene la matriz de bytes con datos de flujo invocando el método `System.IO.FileStream` del objeto `Read`. Pase la matriz de bytes, la posición de inicio y la longitud del flujo para leerlos.
   * Rellene el objeto `BLOB` asignando su campo `MTOM` con el contenido de la matriz de bytes.
   * Cree un objeto `MyMapOf_xsd_string_To_xsd_anyType`. Este objeto de colección se utiliza para almacenar documentos PDF de entrada.
   * Para cada documento PDF de entrada, cree un objeto `MyMapOf_xsd_string_To_xsd_anyType_Item`. Por ejemplo, si se utilizan dos documentos PDF de entrada, cree dos objetos `MyMapOf_xsd_string_To_xsd_anyType_Item`.
   * Asigne un valor de cadena que represente el nombre clave al campo `MyMapOf_xsd_string_To_xsd_anyType_Item` del objeto `key`. Este valor debe coincidir con el valor del elemento de origen PDF especificado en el documento DDX. (Realice esta tarea para cada documento PDF de entrada).
   * Asigne el objeto `BLOB` que almacena el documento PDF al campo `MyMapOf_xsd_string_To_xsd_anyType_Item` del objeto `value`. (Realice esta tarea para cada documento PDF de entrada).
   * Agregue el objeto `MyMapOf_xsd_string_To_xsd_anyType_Item` al objeto `MyMapOf_xsd_string_To_xsd_anyType`. Invoque el método `MyMapOf_xsd_string_To_xsd_anyType` del objeto `Add` y pase el objeto `MyMapOf_xsd_string_To_xsd_anyType`. (Realice esta tarea para cada documento PDF de entrada).

1. Establezca las opciones de tiempo de ejecución.

   * Cree un objeto `AssemblerOptionSpec` que almacene opciones en tiempo de ejecución empleando su constructor.
   * Defina las opciones en tiempo de ejecución para satisfacer los requisitos empresariales asignando un valor a un miembro de datos que pertenece al objeto `AssemblerOptionSpec`. Por ejemplo, para solicitar al servicio Assembler que continúe procesando un trabajo cuando se produzca un error, asigne `false` al miembro de datos `AssemblerOptionSpec` del objeto `failOnError`.

1. Ensamble los documentos PDF de entrada.

   Invoque el método `AssemblerServiceClient` del objeto `invoke` y pase los siguientes valores:

   * Un objeto `BLOB` que representa el documento DDX.
   * La matriz `mapItem` que contiene los documentos PDF de entrada. Sus claves deben coincidir con los nombres de los archivos de origen PDF y sus valores deben ser los objetos `BLOB` que correspondan a esos archivos.
   * Un objeto `AssemblerOptionSpec` que especifica opciones en tiempo de ejecución.

   El método `invoke` devuelve un objeto `AssemblerResult` que contiene los resultados del trabajo y cualquier excepción que pueda haberse producido.

1. Extraiga los resultados.

   Para obtener el documento PDF recién creado, realice las siguientes acciones:

   * Acceda al campo `AssemblerResult` del objeto `documents`, que es un objeto `Map` que contiene los documentos PDF resultantes.
   * Repita el objeto `Map` hasta que encuentre la clave que coincida con el nombre del documento resultante. A continuación, convierta el `value` del miembro de la matriz en un `BLOB`.
   * Extraiga los datos binarios que representan el documento PDF accediendo a la propiedad `BLOB` del objeto `MTOM`. Esto devuelve una matriz de bytes que puede escribir en un archivo PDF.

   >[!NOTE]
   >
   >Si `LOG_LEVEL` se configuró para producir un registro, puede extraer el registro obteniendo el valor del miembro de datos `jobLog` del objeto `AssemblerResult`.

**Consulte también**

[Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
