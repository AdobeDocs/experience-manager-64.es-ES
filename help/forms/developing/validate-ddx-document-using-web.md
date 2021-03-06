---
title: Validación de un documento DDX mediante la API de servicio web
seo-title: Validación de un documento DDX mediante la API de servicio web
description: Utilice la API de servicio del ensamblador para validar un documento DDX.
seo-description: Utilice la API de servicio del ensamblador para validar un documento DDX.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---


# Validar un documento DDX utilizando la API de servicio web {#validate-a-ddx-document-using-theweb-service-api}

Valide un documento DDX utilizando la API del servicio Assembler (servicio web):

1. Incluir archivos de proyecto.

   Cree un proyecto de Microsoft .NET que utilice MTOM. Asegúrese de utilizar la siguiente definición WSDL: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Reemplace localhost por la dirección IP del servidor de formularios.

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

1. Defina las opciones en tiempo de ejecución para validar el documento DDX.

   * Cree un objeto `AssemblerOptionSpec` que almacene opciones en tiempo de ejecución empleando su constructor.
   * Establezca la opción en tiempo de ejecución que indica al servicio Assembler que valide el documento DDX asignando el valor true al miembro de datos `AssemblerOptionSpec` del objeto `validateOnly`.
   * Establezca la cantidad de información que el servicio Assembler escribe en el archivo de registro asignando un valor de cadena al miembro de datos `AssemblerOptionSpec` del objeto `logLevel`. método Al validar un documento DDX, desea que se escriba más información en el archivo de registro que ayudará en el proceso de validación. Como resultado, puede especificar el valor `FINE` o `FINER`. Para obtener información sobre las opciones de tiempo de ejecución que puede establecer, consulte la referencia de clase `AssemblerOptionSpec` en [Referencia de API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Realice la validación.

   Invoque el método `AssemblerServiceClient` del objeto `invokeDDX` y pase los siguientes valores:

   * Un objeto `BLOB` que representa el documento DDX.
   * El valor `null` del objeto `Map` que generalmente almacena documentos PDF.
   * Un objeto `AssemblerOptionSpec` que especifica opciones en tiempo de ejecución.

   El método `invokeDDX` devuelve un objeto `AssemblerResult` que contiene información que especifica si el documento DDX es válido.

1. Guarde los resultados de validación en un archivo de registro.

   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo de registro y el modo en que se abre el archivo. Asegúrese de que la extensión del nombre de archivo es .xml.
   * Cree un objeto `BLOB` que almacene información de registro obteniendo el valor del miembro de datos `AssemblerResult` del objeto `jobLog`.
   * Cree una matriz de bytes que almacene el contenido del objeto `BLOB`. Rellene la matriz de bytes obteniendo el valor del campo `BLOB` del objeto `MTOM`.
   * Cree un objeto `System.IO.BinaryWriter` invocando su constructor y pasando el objeto `System.IO.FileStream`.
   * Escriba el contenido de la matriz de bytes en un archivo PDF invocando el método `System.IO.BinaryWriter` del objeto `Write` y pasando la matriz de bytes.

   >[!NOTE]
   >
   >Si el documento DDX no es válido, se genera un `OperationException`. Dentro de la sentencia catch, puede obtener el valor del miembro `OperationException` del objeto `jobLog`.

**Consulte también**

[Validación de documentos DDX](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
