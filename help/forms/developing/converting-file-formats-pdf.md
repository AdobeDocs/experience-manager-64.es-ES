---
title: Conversión entre formatos de archivo y PDF
seo-title: Converting Between File Formatsand PDF
description: Utilice el servicio Generate PDF para convertir formatos de archivo nativos a PDF. Generate PDF service también convierte PDF a otros formatos de archivo y optimiza el tamaño de los documentos PDF.
seo-description: Use the Generate PDF service to convert native file formats to PDF. Generate PDF service also converts PDF to other file formats and optimizes the size of PDF documents.
uuid: f72ad603-c996-4d48-9bfc-bed7bf776af6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 180cac3f-6378-42bc-9a47-60f9f08a7103
role: Developer
exl-id: 79091a75-2669-453f-9560-e58bfffa3487
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '7872'
ht-degree: 0%

---

# Conversión entre formatos de archivo y PDF {#converting-between-file-formatsand-pdf}

**Acerca del servicio Generate PDF**

El servicio Generate PDF convierte los formatos de archivo nativos a PDF. También convierte PDF a otros formatos de archivo y optimiza el tamaño de los documentos PDF.

El servicio Generate PDF utiliza aplicaciones nativas para convertir los siguientes formatos de archivo a PDF. A menos que se indique lo contrario, solo se admiten las versiones en alemán, francés, inglés y japonés de estas aplicaciones. *Windows* solo indica compatibilidad con Windows Server® 2003 y Windows Server 2008.

* Microsoft Office 2003 y 2007 para convertir DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS y PUB (solo Windows)

   >[!NOTE]
   >
   >Se requiere Acrobat® 9.2 o posterior para convertir el formato de Microsoft XPS a PDF.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 y 2009 para convertir DWF, DWG y DXW (solo en inglés)
* Corel WordPerfect 12 y X4 para convertir WPD, QPW, SHW (solo en inglés)
* OpenOffice 2.0, 2.4, 3.0.1 y 3.1 para convertir ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXC, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX y PUB

   >[!NOTE]
   >
   >El servicio Generate PDF no admite las versiones de 64 bits de OpenOffice.

* Adobe Photoshop® CS2 para convertir PSD (solo Windows)

   >[!NOTE]
   >
   >Photoshop CS3 y CS4 no son compatibles porque no admiten Windows Server 2003 o Windows Server 2008.

* Adobe FrameMaker® 7.2 y 8 para convertir FM (solo Windows)
* PageMaker Adobe® 7.0 para convertir PMD, PM6, P65 y PM (solo Windows)
* Formatos nativos admitidos por aplicaciones de terceros (requiere el desarrollo de archivos de configuración específicos para la aplicación) (solo Windows)

El servicio Generate PDF convierte los siguientes formatos de archivo basados en estándares a PDF.

* Formatos de vídeo: SWF, FLV (solo Windows)
* Formatos de imagen: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ y Linux®)

El servicio Generate PDF convierte PDF a los siguientes formatos de archivo (solo Windows):

* Encapsulated PostScript (EPS)
* HTML3.2
* HTML 4.01 con CSS 1.0
* DOC (formato Microsoft Word)
* RTF
* Texto (tanto accesible como sin formato)
* XML
* PDF/A-1a que utiliza solamente el espacio de color DeviceRGB
* PDF/A-1b que utiliza solamente el espacio de color DeviceRGB

El servicio Generate PDF requiere que realice estas tareas administrativas:

* Instalar las aplicaciones nativas necesarias en el equipo que aloja AEM Forms
* Instale Adobe Acrobat Professional o Acrobat Pro Extended 9.2 en el equipo que aloje AEM Forms
* Realizar tareas de configuración posteriores a la instalación

Estas tareas se describen en Instalación e implementación de formularios AEM usando JBoss Turnkey.

Puede realizar estas tareas mediante el servicio Generate PDF:

* Convierta de formatos de archivo nativos a PDF.
* Convierta documentos HTML en documentos PDF.
* Convierta documentos PDF a formatos de archivo.

>[!NOTE]
>
>Para obtener más información sobre el servicio Generate PDF, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversión de documentos de Word a documentos PDF {#converting-word-documents-to-pdf-documents}

En esta sección se describe cómo puede utilizar la API Generate PDF para convertir mediante programación un documento de Microsoft Word a un documento PDF.

>[!NOTE]
>
>Para obtener más información sobre los formatos de archivo adicionales, consulte [Adición de soporte para formatos de archivo nativos adicionales](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats).

>[!NOTE]
>
>Para obtener más información sobre el servicio Generate PDF, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary-of-steps}

Para convertir un documento de Microsoft Word en un documento PDF, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un cliente Generate PDF.
1. Recupere el archivo para convertir en un documento PDF.
1. Convierta el archivo en un documento PDF.
1. Recupere los resultados.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

**Crear un cliente de Generate PDF**

Para poder realizar mediante programación una operación Generate PDF, cree un cliente de servicio Generate PDF. Si utiliza la API de Java, cree un objeto `GeneratePdfServiceClient`. Si utiliza la API de servicio web, cree un objeto `GeneratePDFServiceService`.

**Recuperar el archivo para convertir en un documento PDF**

Recupere el documento de Microsoft Word para convertirlo en un documento PDF.

**Convertir el archivo en un documento PDF**

Después de crear el cliente de servicio Generate PDF, puede invocar el método `createPDF2`. Este método necesita información sobre el documento que se va a convertir, incluida la extensión de archivo.

**Recuperar los resultados**

Una vez convertido el archivo en un documento PDF, puede recuperar los resultados. Por ejemplo, después de convertir un archivo de Word en un documento PDF, puede recuperar y guardar el documento PDF.

**Consulte también**

[Convertir documentos de Word en documentos PDF mediante la API de Java](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Convertir documentos de Word en documentos PDF mediante la API de servicio Web](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generación de inicios rápidos de la API del servicio PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Convertir documentos de Word en documentos PDF mediante la API de Java {#convert-word-documents-to-pdf-documents-using-the-java-api}

Convertir un documento de Microsoft Word en un documento PDF mediante la API Generate PDF (Java):

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-generatepdf-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un cliente Generate PDF.

   * Cree un objeto `ServiceClientFactory` que contenga propiedades de conexión.
   * Cree un objeto `GeneratePdfServiceClient` utilizando su constructor y pasando el objeto `ServiceClientFactory`.

1. Recupere el archivo para convertir en un documento PDF.

   * Cree un objeto `java.io.FileInputStream` que represente el archivo de Word que desea convertir con su constructor. Pase un valor de cadena que especifique la ubicación del archivo.
   * Cree un objeto `com.adobe.idp.Document` utilizando su constructor y pasando el objeto `java.io.FileInputStream`.

1. Convierta el archivo en un documento PDF.

   Convierta el archivo en un documento PDF invocando el método `GeneratePdfServiceClient` del objeto `createPDF2` y pasando los siguientes valores:

   * Un objeto `com.adobe.idp.Document` que representa el archivo que se va a convertir.
   * Un objeto `java.lang.String` que contiene la extensión de archivo.
   * Un objeto `java.lang.String` que contiene la configuración del tipo de archivo que se utilizará en la conversión. La configuración del tipo de archivo proporciona configuración de conversión para diferentes tipos de archivo, como .doc o .xls.
   * Un objeto `java.lang.String` que contiene el nombre de la configuración de PDF que se va a utilizar. Por ejemplo, puede especificar `Standard`.
   * Un objeto `java.lang.String` que contiene el nombre de la configuración de seguridad que se va a utilizar.
   * Un objeto `com.adobe.idp.Document` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF.
   * Un objeto `com.adobe.idp.Document` opcional que contiene información de metadatos que se debe aplicar al documento PDF.

   El método `createPDF2` devuelve un objeto `CreatePDFResult` que contiene el nuevo documento PDF y una información de registro. El archivo de registro suele contener mensajes de error o de advertencia generados por la solicitud de conversión.

1. Recupere los resultados.

   Para obtener el documento PDF, realice las siguientes acciones:

   * Invoque el método `CreatePDFResult` del objeto `getCreatedDocument`, que devuelve un objeto `com.adobe.idp.Document`.
   * Invoque el método `com.adobe.idp.Document` del objeto `copyToFile` para extraer el documento PDF del objeto creado en el paso anterior.

   Si ha utilizado el método `createPDF2` para obtener el documento de registro (no aplicable a las conversiones HTML), realice las siguientes acciones:

   * Invoque el método `CreatePDFResult` del objeto `getLogDocument`. Esto devuelve un objeto `com.adobe.idp.Document`.
   * Invoque el método `com.adobe.idp.Document` del objeto `copyToFile` para extraer el documento de registro.


**Consulte también**

[Resumen de los pasos](converting-file-formats-pdf.md#summary-of-steps)

[Inicio rápido (modo SOAP): Conversión de un documento de Microsoft Word en un documento PDF mediante la API de Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir documentos de Word en documentos PDF mediante la API de servicio Web {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

Convertir un documento de Microsoft Word en un documento PDF mediante la API Generate PDF (servicio Web):

1. Incluir archivos de proyecto.

   Cree un proyecto de Microsoft .NET que utilice MTOM. Asegúrese de utilizar la siguiente definición WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sustituya `localhost` por la dirección IP del servidor que hospeda AEM Forms.

1. Cree un cliente Generate PDF.

   * Cree un objeto `GeneratePDFServiceClient` utilizando su constructor predeterminado.
   * Cree un objeto `GeneratePDFServiceClient.Endpoint.Address` utilizando el constructor `System.ServiceModel.EndpointAddress`. Pase un valor de cadena que especifique el WSDL al servicio de AEM Forms (por ejemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). No es necesario utilizar el atributo `lc_version`. Sin embargo, especifique `?blob=mtom`.
   * Cree un objeto `System.ServiceModel.BasicHttpBinding` obteniendo el valor del campo `GeneratePDFServiceClient.Endpoint.Binding`. Establezca el valor devuelto en `BasicHttpBinding`.
   * Establezca el campo `System.ServiceModel.BasicHttpBinding` del objeto `MessageEncoding` en `WSMessageEncoding.Mtom`. Este valor garantiza que se utilice MTOM.
   * Habilite la autenticación HTTP básica realizando las siguientes tareas:

      * Asigne el nombre de usuario de los formularios AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Asigne el valor de contraseña correspondiente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Asigne el valor constante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Asigne el valor constante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere el archivo para convertir en un documento PDF.

   * Cree un objeto `BLOB` utilizando su constructor. El objeto `BLOB` se utiliza para almacenar el archivo que desea convertir en un documento PDF.
   * Cree un objeto `System.IO.FileStream` invocando su constructor. Pase un valor de cadena que represente la ubicación del archivo que desea convertir y el modo en que desea abrir el archivo.
   * Cree una matriz de bytes que almacene el contenido del objeto `System.IO.FileStream`. Puede determinar el tamaño de la matriz de bytes obteniendo la propiedad `System.IO.FileStream` del objeto `Length`.
   * Rellene la matriz de bytes con datos de flujo invocando el método `System.IO.FileStream` del objeto `Read` y pasando la matriz de bytes, la posición de inicio y la longitud de flujo para leer.
   * Rellene el objeto `BLOB` asignando a su propiedad `MTOM` el contenido de la matriz de bytes.

1. Convierta el archivo en un documento PDF.

   Convierta el archivo en un documento PDF invocando el método `GeneratePDFServiceService` del objeto `CreatePDF2` y pasando los siguientes valores:

   * Un objeto `BLOB` que representa el archivo que se va a convertir.
   * Cadena que contiene la extensión del archivo.
   * Un objeto `java.lang.String` que contiene la configuración del tipo de archivo que se utilizará en la conversión. La configuración del tipo de archivo proporciona configuración de conversión para diferentes tipos de archivo, como .doc o .xls.
   * Un objeto de cadena que contiene la configuración de PDF que se va a utilizar. Puede especificar `Standard`.
   * Un objeto de cadena que contiene la configuración de seguridad que se va a utilizar. Puede especificar `No Security`.
   * Un objeto `BLOB` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF.
   * Un objeto `BLOB` opcional que contiene información de metadatos que se debe aplicar al documento PDF.
   * Un parámetro de salida de tipo `BLOB` que se rellena con el método `CreatePDF2`. El método `CreatePDF2` rellena este objeto con el documento convertido. (Este valor de parámetro solo es necesario para la invocación de servicio web).
   * Un parámetro de salida de tipo `BLOB` que se rellena con el método `CreatePDF2`. El método `CreatePDF2` rellena este objeto con el documento de registro. (Este valor de parámetro solo es necesario para la invocación de servicio web).

1. Recupere los resultados.

   * Recupere el documento PDF convertido asignando el campo `BLOB` del objeto `MTOM` a una matriz de bytes. La matriz de bytes representa el documento PDF convertido. Asegúrese de utilizar el objeto `BLOB` que se utiliza como parámetro de salida para el método `createPDF2`.
   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo del documento PDF convertido.
   * Cree un objeto `System.IO.BinaryWriter` invocando su constructor y pasando el objeto `System.IO.FileStream`.
   * Escriba el contenido de la matriz de bytes en un archivo PDF invocando el método `System.IO.BinaryWriter` del objeto `Write` y pasando la matriz de bytes.

**Consulte también**

[Resumen de los pasos](converting-file-formats-pdf.md#summary-of-steps)

[Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Invocación de AEM Forms mediante SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversión de documentos HTML a documentos PDF {#converting-html-documents-to-pdf-documents}

En esta sección se describe cómo puede utilizar la API Generate PDF para convertir documentos HTML en documentos PDF mediante programación.

>[!NOTE]
>
>Para obtener más información sobre el servicio Generate PDF, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-1}

Para convertir un documento HTML en un documento PDF, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un cliente Generate PDF.
1. Recupere el contenido HTML para convertir en un documento PDF.
1. Convierta el contenido HTML en un documento PDF.
1. Recupere los resultados.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

**Crear un cliente de Generate PDF**

Para poder realizar mediante programación una operación Generate PDF, debe crear un cliente de servicio Generate PDF. Si utiliza la API de Java, cree un objeto `GeneratePdfServiceClient`. Si utiliza la API de servicio web, cree un `GeneratePDFServiceService`.

**Recupere el contenido HTML para convertirlo en un documento PDF**

Haga referencia al contenido HTML que desea convertir en un documento PDF. Puede hacer referencia a contenido HTML, como un archivo HTML o contenido HTML al que se puede acceder mediante una URL.

**Convertir el contenido HTML en un documento PDF**

Después de crear el cliente de servicio, puede invocar la operación de creación de PDF adecuada. Esta operación necesita información sobre el documento que se va a convertir, incluida la ruta al documento de destino.

**Recuperar los resultados**

Una vez que el contenido HTML se convierte en un documento PDF, puede recuperar los resultados y guardar el documento PDF.

**Consulte también**

[Conversión de contenido HTML en un documento PDF mediante la API de Java](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[Convertir contenido HTML en un documento PDF mediante la API de servicio Web](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generación de inicios rápidos de la API del servicio PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Conversión de contenido HTML en un documento PDF mediante la API de Java {#convert-html-content-to-a-pdf-document-using-the-java-api}

Convertir un documento HTML en un documento PDF mediante la API Generate PDF (Java):

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-generatepdf-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un cliente Generate PDF.

   Cree un objeto `GeneratePdfServiceClient` utilizando su constructor y pasando un objeto `ServiceClientFactory` que contenga propiedades de conexión.

1. Recupere el contenido HTML para convertir en un documento PDF.

   Recupere contenido HTML creando una variable de cadena y asignando una URL que apunte al contenido HTML.

1. Convierta el contenido HTML en un documento PDF.

   Invoque el método `GeneratePdfServiceClient` del objeto `htmlToPDF2` y pase los siguientes valores:

   * Un objeto `java.lang.String` que contiene la dirección URL del archivo HTML que se va a convertir.
   * Un objeto `java.lang.String` que contiene la configuración del tipo de archivo que se utilizará en la conversión. La configuración del tipo de archivo puede incluir niveles de araña.
   * Un objeto `java.lang.String` que contiene el nombre de la configuración de seguridad que se va a utilizar.
   * Un objeto `com.adobe.idp.Document` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF. Si no se proporciona esta información, la configuración se elige automáticamente en función de los tres parámetros anteriores.
   * Un objeto `com.adobe.idp.Document` opcional que contiene información de metadatos que se debe aplicar al documento PDF.

1. Recupere los resultados.

   El método `htmlToPDF2` devuelve un objeto `HtmlToPdfResult` que contiene el nuevo documento PDF generado. Para obtener el documento PDF recién creado, realice las siguientes acciones:

   * Invoque el método `HtmlToPdfResult` del objeto `getCreatedDocument`. Esto devuelve un objeto `com.adobe.idp.Document`.
   * Invoque el método `com.adobe.idp.Document` del objeto `copyToFile` para extraer el documento PDF del objeto creado en el paso anterior.

**Consulte también**

[Conversión de documentos HTML a documentos PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Inicio rápido (modo SOAP): Conversión de contenido HTML en un documento PDF mediante la API de Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inicio rápido (modo SOAP): Conversión de contenido HTML en un documento PDF mediante la API de Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertir contenido HTML en un documento PDF mediante la API de servicio Web {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

Convertir contenido HTML en un documento PDF mediante la API Generate PDF (servicio web):

1. Incluir archivos de proyecto.

   Cree un proyecto de Microsoft .NET que utilice MTOM. Asegúrese de utilizar la siguiente definición WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sustituya `localhost` por la dirección IP del servidor que hospeda AEM Forms.

1. Cree un cliente Generate PDF.

   * Cree un objeto `GeneratePDFServiceClient` utilizando su constructor predeterminado.
   * Cree un objeto `GeneratePDFServiceClient.Endpoint.Address` utilizando el constructor `System.ServiceModel.EndpointAddress`. Pase un valor de cadena que especifique el WSDL al servicio de AEM Forms (por ejemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). No es necesario utilizar el atributo `lc_version`. Sin embargo, especifique `?blob=mtom`.
   * Cree un objeto `System.ServiceModel.BasicHttpBinding` obteniendo el valor del campo `GeneratePDFServiceClient.Endpoint.Binding`. Establezca el valor devuelto en `BasicHttpBinding`.
   * Establezca el campo `System.ServiceModel.BasicHttpBinding` del objeto `MessageEncoding` en `WSMessageEncoding.Mtom`. Este valor garantiza que se utilice MTOM.
   * Habilite la autenticación HTTP básica realizando las siguientes tareas:

      * Asigne el nombre de usuario de los formularios AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Asigne el valor de contraseña correspondiente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Asigne el valor constante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Asigne el valor constante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere el contenido HTML para convertir en un documento PDF.

   Recupere contenido HTML creando una variable de cadena y asignando una URL que apunte al contenido HTML.

1. Convierta el contenido HTML en un documento PDF.

   Convierta el contenido HTML en un documento PDF invocando el método `GeneratePDFServiceService` del objeto `HtmlToPDF2` y pasando los siguientes valores:

   * Cadena que contiene el contenido HTML que se va a convertir.
   * Un objeto `java.lang.String` que contiene la configuración del tipo de archivo que se utilizará en la conversión.
   * Un objeto de cadena que contiene la configuración de seguridad que se va a utilizar.
   * Un objeto `BLOB` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF.
   * Un objeto `BLOB` opcional que contiene información de metadatos que se debe aplicar al documento PDF.
   * Un parámetro de salida de tipo `BLOB` que se rellena con el método `CreatePDF2`. El método `CreatePDF2` rellena este objeto con el documento convertido. (Este valor de parámetro solo es necesario para la invocación de servicio web).

1. Recupere los resultados.

   * Recupere el documento PDF convertido asignando el campo `BLOB` del objeto `MTOM` a una matriz de bytes. La matriz de bytes representa el documento PDF convertido. Asegúrese de utilizar el objeto `BLOB` que se utiliza como parámetro de salida para el método `HtmlToPDF2`.
   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo del documento PDF convertido.
   * Cree un objeto `System.IO.BinaryWriter` invocando su constructor y pasando el objeto `System.IO.FileStream`.
   * Escriba el contenido de la matriz de bytes en un archivo PDF invocando el método `System.IO.BinaryWriter` del objeto `Write` y pasando la matriz de bytes.

**Consulte también**

[Conversión de documentos HTML a documentos PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Invocación de AEM Forms mediante SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversión de documentos PDF a formatos que no sean de imagen {#converting-pdf-documents-to-non-image-formats}

En esta sección se describe cómo puede utilizar la API de Generación de PDF Java y la API de servicio web para convertir mediante programación un documento PDF en un archivo RTF, que es un ejemplo de formato que no es de imagen. Otros formatos que no son imágenes incluyen HTML, texto, DOC y EPS. Al convertir un documento PDF a RTF, asegúrese de que el documento PDF no contenga elementos de formulario, como un botón de envío. Los elementos de formulario no se convierten.

>[!NOTE]
>
>Para obtener más información sobre el servicio Generate PDF, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-2}

Para convertir un documento PDF en cualquiera de los tipos admitidos, realice los siguientes pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente Generate PDF.
1. Recupere el documento PDF que desea convertir.
1. Convierta el documento PDF.
1. Guarde el archivo convertido.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

**Crear un cliente de Generate PDF**

Para poder realizar mediante programación una operación Generate PDF, debe crear un cliente de servicio Generate PDF. Si utiliza la API de Java, cree un objeto `GeneratePdfServiceClient`. Si utiliza la API de servicio web, cree un objeto `GeneratePDFServiceService`.

**Recupere el documento PDF que desea convertir**

Recupere el documento PDF para convertirlo a un formato que no sea de imagen.

**Convertir el documento PDF**

Después de crear el cliente de servicio, puede invocar la operación de exportación de PDF. Esta operación necesita información sobre el documento que se va a convertir, incluida la ruta al documento de destino.

**Guardar el archivo convertido**

Guarde el archivo convertido. Por ejemplo, si convierte un documento PDF en un archivo RTF, guarde el documento convertido en un archivo RTF.

**Consulte también**

[Conversión de un documento PDF en un archivo RTF mediante la API de Java](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Conversión de un documento PDF en un archivo RTF mediante la API de servicio Web](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generación de inicios rápidos de la API del servicio PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Conversión de un documento PDF en un archivo RTF mediante la API de Java {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

Convertir un documento PDF en un archivo RTF usando la API Generate PDF (Java):

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-generatepdf-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un cliente Generate PDF.

   Cree un objeto `GeneratePdfServiceClient` utilizando su constructor y pasando un objeto `ServiceClientFactory` que contenga propiedades de conexión.

1. Recupere el documento PDF que desea convertir.

   * Cree un objeto `java.io.FileInputStream` que represente el documento PDF que desea convertir utilizando su constructor. Pase un valor de cadena que especifique la ubicación del documento PDF.
   * Cree un objeto `com.adobe.idp.Document` utilizando su constructor y pasando el objeto `java.io.FileInputStream`.

1. Convierta el documento PDF.

   Invoque el método `GeneratePdfServiceClient` del objeto `exportPDF2` y pase los siguientes valores:

   * Un objeto `com.adobe.idp.Document` que representa el archivo PDF que se va a convertir.
   * Un objeto `java.lang.String` que contiene el nombre del archivo que se va a convertir.
   * Un objeto `java.lang.String` que contiene el nombre de la configuración de Adobe PDF.
   * Un objeto `ConvertPDFFormatType` que especifica el tipo de archivo de destino para la conversión.
   * Un objeto `com.adobe.idp.Document` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF.

   El método `exportPDF2` devuelve un objeto `ExportPDFResult` que contiene el archivo convertido.

1. Convierta el documento PDF.

   Para obtener el archivo recién creado, realice las siguientes acciones:

   * Invoque el método `ExportPDFResult` del objeto `getConvertedDocument`. Esto devuelve un objeto `com.adobe.idp.Document`.
   * Invoque el método `com.adobe.idp.Document` del objeto `copyToFile` para extraer el nuevo documento.

**Consulte también**

[Resumen de los pasos](converting-file-formats-pdf.md#summary-of-steps)

[Inicio rápido (modo SOAP): Conversión de contenido HTML en un documento PDF mediante la API de Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Conversión de un documento PDF en un archivo RTF mediante la API de servicio Web {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Convertir un documento PDF en un archivo RTF usando la API Generate PDF (servicio web):

1. Incluir archivos de proyecto.

   Cree un proyecto de Microsoft .NET que utilice MTOM. Asegúrese de utilizar la siguiente definición WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sustituya `localhost` por la dirección IP del servidor que hospeda AEM Forms.

1. Cree un cliente Generate PDf.

   * Cree un objeto `GeneratePDFServiceClient` utilizando su constructor predeterminado.
   * Cree un objeto `GeneratePDFServiceClient.Endpoint.Address` utilizando el constructor `System.ServiceModel.EndpointAddress`. Pase un valor de cadena que especifique el WSDL al servicio de AEM Forms (por ejemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). No es necesario utilizar el atributo `lc_version`. Sin embargo, especifique `?blob=mtom`.
   * Cree un objeto `System.ServiceModel.BasicHttpBinding` obteniendo el valor del campo `GeneratePDFServiceClient.Endpoint.Binding`. Establezca el valor devuelto en `BasicHttpBinding`.
   * Establezca el campo `System.ServiceModel.BasicHttpBinding` del objeto `MessageEncoding` en `WSMessageEncoding.Mtom`. Este valor garantiza que se utilice MTOM.
   * Habilite la autenticación HTTP básica realizando las siguientes tareas:

      * Asigne el nombre de usuario de los formularios AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Asigne el valor de contraseña correspondiente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Asigne el valor constante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Asigne el valor constante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere el documento PDF que desea convertir.

   * Cree un objeto `BLOB` utilizando su constructor. El objeto `BLOB` se utiliza para almacenar un documento PDF convertido.
   * Cree un objeto `System.IO.FileStream` invocando su constructor y pasando un valor de cadena que represente la ubicación del archivo del documento PDF y el modo en que se abre el archivo.
   * Cree una matriz de bytes que almacene el contenido del objeto `System.IO.FileStream`. Puede determinar el tamaño de la matriz de bytes obteniendo la propiedad `System.IO.FileStream` del objeto `Length`.
   * Rellene la matriz de bytes con datos de flujo invocando el método `System.IO.FileStream` del objeto `Read` y pasando la matriz de bytes, la posición de inicio y la longitud de flujo para leer.
   * Rellene el objeto `BLOB` asignando a su propiedad `MTOM` el contenido de la matriz de bytes.

1. Convierta el documento PDF.

   Invoque el método `GeneratePDFServiceServiceWse` del objeto `ExportPDF2` y pase los siguientes valores:

   * Un objeto `BLOB` que representa el archivo PDF que se va a convertir.
   * Cadena que contiene el nombre de la ruta del archivo que se va a convertir.
   * Un objeto `java.lang.String` que especifica la ubicación del archivo.
   * Un objeto de cadena que especifica el tipo de archivo de destino para la conversión. Especifique `RTF`.
   * Un objeto `BLOB` opcional que contiene la configuración que se debe aplicar durante la generación del documento PDF.
   * Un parámetro de salida de tipo `BLOB` que se rellena con el método `ExportPDF2`. El método `ExportPDF2` rellena este objeto con el documento convertido. (Este valor de parámetro solo es necesario para la invocación de servicio web).

1. Guarde el archivo convertido.

   * Recupere el documento RTF convertido asignando el campo `BLOB` del objeto `MTOM` a una matriz de bytes. La matriz de bytes representa el documento RTF convertido. Asegúrese de utilizar el objeto `BLOB` que se utiliza como parámetro de salida para el método `ExportPDF2`.
   * Cree un objeto `System.IO.FileStream` invocando su constructor. Pase un valor de cadena que represente la ubicación del archivo RTF.
   * Cree un objeto `System.IO.BinaryWriter` invocando su constructor y pasando el objeto `System.IO.FileStream`.
   * Escriba el contenido de la matriz de bytes en un archivo RTF invocando el método `System.IO.BinaryWriter` del objeto `Write` y pasando la matriz de bytes.

**Consulte también**

[Resumen de los pasos](converting-file-formats-pdf.md#summary-of-steps)

[Invocación de AEM Forms mediante MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Invocación de AEM Forms mediante SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Añadir compatibilidad con formatos de archivo nativos adicionales {#adding-support-for-additional-native-file-formats}

En esta sección se explica cómo agregar compatibilidad con formatos de archivo nativos adicionales. Proporciona una visión general de las interacciones entre el servicio Generate PDF y las aplicaciones nativas que este servicio utiliza para convertir formatos de archivo nativos a PDF.

Esta sección también explica lo siguiente:

* Cómo modificar la respuesta que el servicio Generate PDF proporciona a las aplicaciones nativas que este producto ya utiliza para convertir formatos de archivo nativos a PDF
* Las interacciones entre el servicio Generate PDF, el componente Generate PDF service Application Monitor (AppMon) y las aplicaciones nativas, como Microsoft Word
* Funciones que los gramaticales XML juegan en esas interacciones

### Interacciones de componentes {#component-interactions}

El servicio Generate PDF convierte los formatos de archivo nativos invocando la aplicación asociada al formato de archivo y luego interactuando con la aplicación para imprimir el documento utilizando la impresora predeterminada. La impresora predeterminada debe configurarse como Adobe PDF.

Esta ilustración muestra los componentes y controladores involucrados con la compatibilidad con aplicaciones nativas. También menciona los gramáticas XML que influyen en las interacciones.

Interacciones de componentes para la conversión de archivos nativos

Este documento utiliza el término *aplicación nativa* para indicar la aplicación utilizada para producir un formato de archivo nativo, como Microsoft Word.

** AppMonis es un componente empresarial que interactúa con una aplicación nativa del mismo modo en que un usuario navegaría por los cuadros de diálogo presentados por esa aplicación. Los gramáticas XML que utiliza AppMon para indicar a una aplicación, como Microsoft Word, que abra e imprima un archivo que incluya estas tareas secuenciales:

1. Abrir el archivo seleccionando Archivo > Abrir
1. Asegurarse de que aparezca el cuadro de diálogo Abrir; si no, gestión del error
1. Proporcione el nombre de archivo en el campo Nombre de archivo y haga clic en el botón Abrir
1. Garantizar que el archivo se abra
1. Abrir el cuadro de diálogo Imprimir seleccionando Archivo > Imprimir
1. Aseguramiento de que aparezca el cuadro de diálogo Imprimir

AppMon utiliza API Win32 estándar para interactuar con aplicaciones de terceros con el fin de transferir eventos de interfaz de usuario como pulsaciones de teclas y clics con el ratón, lo que resulta útil para controlar estas aplicaciones y producir archivos PDF a partir de ellas.

Debido a una limitación con estas API Win32, AppMon no puede distribuir estos eventos de interfaz de usuario a algunos tipos específicos de ventanas, como barras de menús flotantes (que se encuentran en algunas aplicaciones como TextPad) y ciertos tipos de cuadros de diálogo cuyo contenido no se puede recuperar mediante las API Win32.

Es fácil identificar visualmente una barra de menús flotante; sin embargo, tal vez no sea posible identificar los tipos especiales de diálogos sólo mediante una inspección visual. Necesitaría una aplicación de terceros, como Microsoft Spy++ (parte del entorno de desarrollo de Microsoft Visual C+++) o su WinID equivalente (que se puede descargar gratuitamente desde [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)), para examinar un cuadro de diálogo y determinar si AppMon podría interactuar con él mediante las API Win32 estándar.

Si WinID es capaz de extraer el contenido del cuadro de diálogo, como el texto, las ventanas secundarias, el ID de la clase de ventana, etc., AppMon también podría hacer lo mismo.

En esta tabla se muestra el tipo de información que se utiliza en la impresión de formatos de archivo nativos.

<table> 
 <thead> 
  <tr> 
   <th><p>Tipo de información</p></th> 
   <th><p>Descripción</p></th> 
   <th><p>Modificación/creación de entradas relacionadas con archivos nativos </p></th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td><p>Configuración administrativa </p></td> 
   <td><p>Incluye configuración de PDF, configuración de seguridad y configuración de tipo de archivo. </p><p>La configuración de tipo de archivo asocia las extensiones de nombre de archivo con las aplicaciones nativas correspondientes. La configuración del tipo de archivo también especifica la configuración nativa de la aplicación utilizada para imprimir archivos nativos. </p></td> 
   <td><p>Para cambiar la configuración de una aplicación nativa ya admitida, el administrador del sistema establece la Configuración de tipo de archivo en la consola de administración. </p><p>Para agregar compatibilidad con un nuevo formato de archivo nativo, debe editar manualmente el archivo. (Consulte <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">Adición o modificación de la compatibilidad con un formato de archivo nativo</a>). </p></td> 
  </tr> 
  <tr> 
   <td><p>Script </p></td> 
   <td><p>Especifica interacciones entre el servicio Generate PDF y una aplicación nativa. Estas interacciones normalmente dirigen la aplicación a imprimir un archivo en el controlador de Adobe PDF. </p><p>La secuencia de comandos contiene instrucciones que dirigen a la aplicación nativa a abrir cuadros de diálogo específicos y que proporcionan respuestas específicas a los campos y botones de esos cuadros de diálogo. </p></td> 
   <td><p>El servicio Generate PDF incluye archivos de script para todas las aplicaciones nativas admitidas. Puede modificar estos archivos utilizando una aplicación de edición XML.</p><p>Para agregar compatibilidad con una nueva aplicación nativa, debe crear un nuevo archivo de secuencia de comandos. (Consulte <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Creación o modificación de un archivo XML de diálogo adicional para una aplicación nativa</a>). </p></td> 
  </tr> 
  <tr> 
   <td><p>Instrucciones genéricas del cuadro de diálogo </p></td> 
   <td><p>Especifica cómo responder a cuadros de diálogo que son comunes a varias aplicaciones. Estos cuadros de diálogo los generan los sistemas operativos, las aplicaciones de ayuda (como PDFMaker) y los controladores. </p><p>El archivo que contiene esta información es appmon.global.en_US.xml.</p></td> 
   <td><p>No modifique este archivo. </p></td> 
  </tr> 
  <tr> 
   <td><p>Instrucciones del cuadro de diálogo específico de la aplicación</p></td> 
   <td><p>Especifica cómo responder a cuadros de diálogo específicos de la aplicación. </p><p>El archivo que contiene esta información es appmon.<i>[appname]</i>.dialog.<i>[locale]</i>.xml (por ejemplo, appmon.word.en_US.xml).</p></td> 
   <td><p>No modifique este archivo. </p><p>Para agregar instrucciones de cuadro de diálogo para una nueva aplicación nativa, consulte <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Creación o modificación de un archivo XML de cuadro de diálogo adicional para una aplicación nativa</a>.</p></td> 
  </tr> 
  <tr> 
   <td><p>Instrucciones adicionales del cuadro de diálogo específicas de la aplicación </p></td> 
   <td><p>Especifica anulaciones y adiciones a las instrucciones del cuadro de diálogo específicas de la aplicación. La sección presenta un ejemplo de dicha información. </p><p>El archivo que contiene esta información es appmon.<i>[appname]</i>.<i>[configuración regional]</i>.xml. Un ejemplo es appmon.add.en_US.xml.</p></td> 
   <td><p>Los archivos de este tipo se pueden crear y modificar utilizando una aplicación de edición XML. (Consulte <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Creación o modificación de un archivo XML de diálogo adicional para una aplicación nativa</a>). </p><p><strong>Importante</strong>: Debe crear instrucciones adicionales del cuadro de diálogo específicas de la aplicación para cada aplicación nativa que admita su servidor. </p></td> 
  </tr> 
 </tbody> 
</table>

### Acerca de los archivos XML de script y cuadro de diálogo {#about-the-script-and-dialog-xml-files}

Los archivos XML de secuencias de comandos dirigen el servicio Generar PDF para navegar por los cuadros de diálogo de la aplicación del mismo modo que un usuario navegaría por los cuadros de diálogo de la aplicación. Los archivos XML de secuencias de comandos también dirigen al servicio Generar PDF para que responda a los cuadros de diálogo; para ello, realiza acciones como pulsar botones, seleccionar o anular la selección de casillas de verificación o seleccionar elementos de menú.

Por el contrario, los archivos XML de cuadro de diálogo simplemente responden a cuadros de diálogo con los mismos tipos de acciones utilizadas en los archivos XML de secuencia de comandos.

#### Terminología del cuadro de diálogo y el elemento de ventana {#dialog-box-and-window-element-terminology}

Esta sección y la siguiente sección utilizan una terminología diferente para los cuadros de diálogo y los componentes que contienen, según la perspectiva que se describa. Los componentes del cuadro de diálogo son elementos como botones, campos y cuadros combinados.

Cuando esta sección y la siguiente sección describen cuadros de diálogo y sus componentes desde la perspectiva de un usuario, se utilizan términos como *cuadro de diálogo*, *botón*, *campo* y *cuadro combinado*.

Cuando esta sección y la siguiente sección describen cuadros de diálogo y sus componentes desde la perspectiva de su representación interna, se utiliza el término *elemento de ventana*. La representación interna de los elementos de ventana es una jerarquía, donde cada instancia de elemento de ventana se identifica mediante etiquetas. La instancia del elemento window también describe sus características físicas y su comportamiento.

Desde la perspectiva del usuario, los cuadros de diálogo y sus componentes muestran comportamientos diferentes, donde algunos elementos de los cuadros de diálogo se ocultan hasta que se activan. Desde la perspectiva de la representación interna, no existe tal cuestión de comportamiento. Por ejemplo, la representación interna de un cuadro de diálogo es similar a la de los componentes que contiene, con la excepción de que los componentes están anidados en el cuadro de diálogo.

En esta sección se describen los elementos XML que proporcionan instrucciones a AppMon. Estos elementos tienen nombres como el elemento `dialog` y el elemento `window`. Este documento utiliza una fuente monoespaciada para distinguir los elementos XML. El elemento `*dialog*` identifica un cuadro de diálogo que un archivo de secuencia de comandos XML puede causar que se muestre, ya sea de forma intencionada o no. El elemento `*window*` identifica un elemento de ventana (cuadro de diálogo o los componentes de un cuadro de diálogo).

#### Jerarquía {#hierarchy}

Este diagrama muestra la jerarquía de la secuencia de comandos y el cuadro de diálogo XML. Un archivo XML de secuencia de comandos se ajusta al esquema script.xsd , que incluye (en el sentido XML) el esquema window.xsd . Del mismo modo, un archivo XML de cuadro de diálogo se ajusta al esquema dialogs.xsd , que también incluye el esquema window.xsd .

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

Jerarquía de XML de secuencias de comandos y cuadros de diálogo

#### Archivos XML de script {#script-xml-files}

Un *archivo XML de secuencia de comandos* especifica una serie de pasos que dirigen a la aplicación nativa a desplazarse a ciertos elementos de ventana y luego proporcionar respuestas a esos elementos. La mayoría de las respuestas son texto o pulsaciones de teclas que corresponden a la entrada que un usuario daría a un campo, cuadro combinado o botón del cuadro de diálogo correspondiente.

La intención de la compatibilidad del servicio Generate PDF para archivos XML de secuencias de comandos es dirigir una aplicación nativa para imprimir un archivo nativo. Sin embargo, los archivos XML de secuencias de comandos se pueden utilizar para realizar cualquier tarea que un usuario pueda realizar al interactuar con los cuadros de diálogo de la aplicación nativa.

Los pasos de un archivo XML de secuencia de comandos se ejecutan en orden, sin posibilidad de ramificación. La única prueba condicional admitida es para el tiempo de espera/reintento, lo que hace que una secuencia de comandos termine si un paso no se completa correctamente dentro de un período de tiempo específico y después de un número específico de reintentos.

Además de los pasos secuenciales, las instrucciones dentro de un paso también se ejecutan en orden. Debe asegurarse de que los pasos y las instrucciones reflejen el orden en que un usuario realizaría esos mismos pasos.

Cada paso de un archivo XML de secuencia de comandos identifica el elemento de ventana que se espera que aparezca si las instrucciones del paso se realizan correctamente. Si aparece un cuadro de diálogo inesperado al ejecutar un paso de secuencia de comandos, el servicio Generate PDF busca los archivos XML de cuadro de diálogo tal como se describe en la siguiente sección.

#### Archivos XML de cuadro de diálogo {#dialog-xml-files}

La ejecución de aplicaciones nativas muestra diferentes cuadros de diálogo, que aparecen independientemente de si las aplicaciones nativas están en modo visible o invisible. Los cuadros de diálogo pueden generarlos el sistema operativo o la propia aplicación. Cuando las aplicaciones nativas se ejecutan bajo el control del servicio Generate PDF, los cuadros de diálogo del sistema y de la aplicación nativa se muestran en una ventana invisible.

Un *archivo XML de diálogo* especifica cómo responde el servicio Generate PDF a los cuadros de diálogo del sistema o de la aplicación nativa. Los archivos XML del cuadro de diálogo permiten que el servicio Generate PDF responda a los cuadros de diálogo no solicitados de forma que facilite el proceso de conversión.

Cuando el sistema o la aplicación nativa muestra un cuadro de diálogo que no está gestionado por el archivo XML de script que se está ejecutando actualmente, el servicio Generate PDF busca los archivos XML de cuadro de diálogo en este orden, deteniéndose cuando encuentra una coincidencia:

* appmon.*[appname]*.additional.*[locale]*.xml
* appmon.*[appname].[locale]*.xml (no modifique este archivo).
* appmon.global.*[locale]*.xml (no modifique este archivo).

Si el servicio Generar PDF encuentra una coincidencia para el cuadro de diálogo, la descarta enviándole la pulsación de tecla u otra acción especificada para el cuadro de diálogo. Si las instrucciones del cuadro de diálogo especifican un mensaje de anulación, el servicio Generate PDF finaliza el trabajo que se está ejecutando y genera un mensaje de error. Este mensaje de anulación se especificaría en el elemento `abortMessage` de la gramática XML del script.

Si el servicio Generar PDF encuentra un cuadro de diálogo que no se describe en ninguno de los archivos enumerados anteriormente, el servicio Generar PDF incorpora el rótulo del cuadro de diálogo en la entrada del archivo de registro. El trabajo que se está ejecutando finaliza el tiempo de espera. A continuación, puede utilizar la información del archivo de registro para componer nuevas instrucciones en el archivo XML de cuadro de diálogo adicional para la aplicación nativa.

### Adición o modificación de la compatibilidad con un formato de archivo nativo {#adding-or-modifying-support-for-a-native-file-format}

En esta sección se describen las tareas que debe realizar para admitir otros formatos de archivo nativos o para modificar la compatibilidad con un formato de archivo nativo ya compatible.

Antes de añadir o modificar la compatibilidad, debe completar las tareas siguientes.

#### Selección de una herramienta para identificar los elementos de ventana {#choosing-a-tool-for-identifying-window-elements}

Los archivos XML de cuadro de diálogo y secuencia de comandos requieren que identifique el elemento de ventana (cuadro de diálogo, campo u otro componente de diálogo) al que responde el elemento de cuadro de diálogo o de secuencia de comandos. Por ejemplo, después de que una secuencia de comandos invoque un menú para una aplicación nativa, la secuencia de comandos debe identificar el elemento de ventana de ese menú al que se deben aplicar pulsaciones de teclas o una acción.

Puede identificar fácilmente un cuadro de diálogo mediante el rótulo que muestra en su barra de título. Sin embargo, debe utilizar una herramienta como Microsoft Spy++ para identificar elementos de ventana de nivel inferior. Los elementos de ventana de nivel inferior se pueden identificar mediante una variedad de atributos, que no son obvios. Además, cada aplicación nativa puede identificar su elemento de ventana de forma diferente. Como resultado, existen varias formas de identificar un elemento de ventana. Este es el orden sugerido para considerar la identificación del elemento de ventana:

1. Pie de ilustración si es único
1. ID de control, que puede o no ser único para un cuadro de diálogo determinado
1. Nombre de la clase que puede o no ser único

Se puede utilizar cualquiera de estos tres atributos o una combinación de ellos para identificar una ventana.

Si los atributos no identifican un rótulo, puede identificar un elemento de ventana utilizando su índice con respecto a su elemento principal. Un *índice* especifica la posición del elemento de ventana en relación con sus elementos de ventana del mismo nivel. Con frecuencia, los índices son la única manera de identificar los cuadros combinados.

Tenga en cuenta estos problemas:

* Microsoft Spy++ muestra los subtítulos utilizando un signo &amp; para identificar la clave activa del subtítulo. Por ejemplo, Spy++ muestra el rótulo de un cuadro de diálogo de impresión como `Pri&nt`, lo que indica que la tecla de acceso directo es *n*. Los títulos de los rótulos en archivos XML de secuencias de comandos y cuadros de diálogo deben omitir los símbolos ampersands.
* Algunos rótulos incluyen saltos de línea. el servicio Generate PDF no puede identificar saltos de línea. Si un rótulo incluye un salto de línea, incluya un número suficiente del rótulo para diferenciarlo de los demás elementos de menú y, a continuación, utilice expresiones regulares para la pieza omitida. Un ejemplo es ( `^Long caption title$`). (Consulte [Uso de expresiones regulares en atributos de rótulo](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes)).
* Utilice entidades de caracteres (también denominadas secuencias de escape) para caracteres XML reservados. Por ejemplo, utilice `&` para los ampersands, `<` y `>` para los símbolos menor que y bueno que, `&apos;` para los apóstrofos y `&quot;` para las comillas.

Si planea trabajar en archivos XML de cuadros de diálogo o secuencias de comandos, debe instalar la aplicación Microsoft Spy++.

#### Desempaquetado de los archivos de diálogo y de secuencia de comandos {#unpackaging-the-dialog-and-script-files}

Los archivos de cuadro de diálogo y script residen en el archivo appmondata.jar . Para poder modificar cualquiera de estos archivos o agregar nuevos archivos de script o diálogo, debe desempaquetar este archivo JAR. Por ejemplo, supongamos que desea agregar compatibilidad con la aplicación EditPlus. Puede crear dos archivos XML, llamados appmon.editplus.script.en_US.xml y appmon.editplus.script.add.en_US.xml. Estas secuencias de comandos XML deben agregarse al archivo adobe-appmondata.jar en dos ubicaciones, tal como se especifica a continuación:

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. El archivo adobe-livecycle-native-jboss-x86_win32.ear se encuentra en la carpeta de exportación en el directorio de instalación de formularios *[AEM]\*configurationManager. (si AEM Forms está implementado en otro servidor de aplicaciones J2EE, reemplace el archivo adobe-livecycle-native-jboss-x86_win32.ear por el archivo EAR que corresponde a su servidor de aplicaciones J2EE).
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (el archivo adobe-appmondata.jar se encuentra en el archivo adobe-generatepdf-dsc.jar). El archivo adobe-generatepdf-dsc.jar se encuentra en la carpeta *[AEM directorio de instalación de formularios]*\deploy.

Después de agregar estos archivos XML al archivo adobe-appmondata.jar, debe volver a implementar el componente GeneratePDF. Para añadir archivos XML de script y diálogo al archivo adobe-appmondata.jar , realice estas tareas:

1. Con una herramienta como WinZip o WinRAR, abra adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > archivo adobe-appmondata.jar.
1. Agregue los archivos XML de script y diálogo al archivo appmondata.jar o modifique los archivos XML existentes en este archivo. (Consulte [Creación o modificación de un archivo XML de secuencia de comandos para una aplicación nativa](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)y [Creación o modificación de un archivo XML de diálogo adicional para una aplicación nativa](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application)).
1. Con una herramienta como WinZip o WinRAR, abra adobe-generatepdf-dsc.jar > adobe-appmondata.jar.
1. Agregue los archivos XML de script y diálogo al archivo appmondata.jar o modifique los archivos XML existentes en este archivo. (Consulte [Creación o modificación de un archivo XML de secuencia de comandos para una aplicación nativa](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)y [Creación o modificación de un archivo XML de diálogo adicional para una aplicación nativa](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application)). Después de agregar los archivos XML al archivo adobe-appmondata.jar , coloque el nuevo archivo adobe-appmondata.jar en el archivo adobe-generatepdf-dsc.jar .
1. Si agregó compatibilidad con un formato de archivo nativo adicional, cree una variable de entorno del sistema que proporcione la ruta de la aplicación (Consulte [Creación de una variable de entorno para localizar la aplicación nativa](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application)).

**Para volver a implementar el componente GeneratePDF**

1. Inicie sesión en Workbench.
1. Seleccione **Ventana** > **Mostrar vistas** > **Componentes**. Esta acción agrega la vista Componentes a Workbench.
1. Haga clic con el botón derecho en el componente GeneratePDF y, a continuación, seleccione **Stop Component**.
1. Cuando se haya detenido el componente, haga clic con el botón derecho y seleccione Desinstalar componente para quitarlo.
1. Haga clic con el botón derecho en el icono **Components** y seleccione **Install Component**.
1. Busque y seleccione el archivo adobe-generatepdf-dsc.jar modificado y, a continuación, haga clic en Abrir. Observe que aparece un cuadrado rojo junto al componente GeneratePDF.
1. Expanda el componente GeneratePDF, seleccione Descriptores de servicio y, a continuación, haga clic con el botón derecho en GeneratePDFService y seleccione Activar servicio.
1. En el cuadro de diálogo de configuración que aparece, introduzca los valores de configuración aplicables. Si deja estos valores en blanco, se utilizan los valores de configuración predeterminados.
1. Haga clic con el botón derecho en GeneratePDF y seleccione Start Component (Iniciar componente).
1. Expanda Servicios activos. Si se está ejecutando, aparece una flecha verde junto al nombre del servicio. De lo contrario, el servicio está en estado detenido.
1. Si el servicio está en estado detenido, haga clic con el botón derecho en el nombre del servicio y seleccione Iniciar servicio.

### Creación o modificación de un archivo XML de secuencia de comandos para una aplicación nativa {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Si desea dirigir archivos a una nueva aplicación nativa, debe crear un archivo XML de secuencia de comandos para dicha aplicación. Si desea modificar la forma en que el servicio Generate PDF interactúa con una aplicación nativa que ya se admite, debe modificar la secuencia de comandos para esa aplicación.

La secuencia de comandos contiene instrucciones que navegan por los elementos de ventana de la aplicación nativa y que proporcionan respuestas específicas a esos elementos. El archivo que contiene esta información es appmon.*[appname]*.script.*[locale]*.xml. Un ejemplo es appmon.notepad.script.en_US.xml.

#### Identificación de los pasos que debe ejecutar la secuencia de comandos {#identifying-steps-the-script-must-execute}

Con la aplicación nativa, determine los elementos de ventana que debe navegar y cada respuesta que debe realizar para imprimir el documento. Observe los cuadros de diálogo que resultan de cualquier respuesta. Los pasos serán similares a estos pasos:

1. Seleccione Archivo > Abrir.
1. Especifique la ruta y, a continuación, haga clic en Abrir.
1. Seleccione Archivo > Imprimir en la barra de menús.
1. Especifique las propiedades necesarias para la impresora.
1. Seleccione Imprimir y espere a que aparezca el cuadro de diálogo Guardar como. El cuadro de diálogo Guardar como es necesario para que el servicio Generar PDF especifique el destino del archivo PDF.

#### Identificación de los cuadros de diálogo especificados en los atributos de rótulo {#identifying-the-dialogs-specified-in-caption-attributes}

Utilice Microsoft Spy++ para obtener las identidades de las propiedades de elementos de ventana en la aplicación nativa. Debe tener estas identidades para escribir secuencias de comandos.

#### Uso de expresiones regulares en atributos de rótulo {#using-regular-expressions-in-caption-attributes}

Puede utilizar expresiones regulares en las especificaciones de rótulos. El servicio Generate PDF utiliza la clase `java.util.regex.Matcher` para admitir expresiones regulares. Esa utilidad admite las expresiones regulares descritas en `java.util.regex.Pattern`.

**Expresión regular que acomoda el nombre de archivo antepuesto al Bloc de notas en el banner Bloc de notas**

```as3
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. --> 
 <step> 
     <expectedWindow> 
         <window caption=".*Notepad"/> 
     </expectedWindow> 
 </step>
```

**Expresión regular que diferencia Imprimir de Configuración de impresión**

```as3
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. --> 
 <windowList> 
     <window controlID="0x01" caption="^Print$" action="press"/> 
 </windowList>
```

#### Ordenación de los elementos window y windowList {#ordering-the-window-and-windowlist-elements}

Debe ordenar los elementos `window` y `windowList` de la siguiente manera:

* Cuando varios elementos `window` aparecen como elementos secundarios en un elemento `windowList` o `dialog`, ordene esos elementos `window` en orden descendente, con las longitudes de los nombres `caption` indicando la posición en el orden.
* Cuando aparecen varios elementos `windowList` en un elemento `window`, ordene esos elementos `windowList` en orden descendente, con las longitudes de los atributos `caption` del primer elemento `indexes/`indicando la posición en el orden.

**Ordenación de elementos de ventana en un archivo de diálogo**

```as3
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <window caption="Unexpected Failure in DebugActiveProcess"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Adobe Acrobat - License Agreement"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Microsoft Visual.*Runtime Library"> 
     <…> 
 </window> 
  
 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. --> 
 <window caption="Adobe Acrobat - Registration"> 
     <…> 
 </window>
```

**Ordenación de elementos de ventana dentro de un elemento windowList**

```as3
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <windowList> 
     <window caption="Can&apos;t exit design mode because.* cannot be created"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="Do you want to continue loading the project?"/> 
     <window className="Button" caption="No" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="The macros in this project are disabled"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList>
```

### Creación o modificación de un archivo XML de diálogo adicional para una aplicación nativa {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Si crea una secuencia de comandos para una aplicación nativa que no se admitía anteriormente, también debe crear un archivo XML de cuadro de diálogo adicional para dicha aplicación. Cada aplicación nativa que utiliza AppMon debe tener solo un archivo XML de diálogo adicional. El archivo XML de cuadro de diálogo adicional es necesario incluso si no se esperan cuadros de diálogo no solicitados. El cuadro de diálogo adicional debe tener al menos un elemento `window`, aunque ese elemento `window` sea simplemente un marcador de posición.

>[!NOTE]
>
>En este contexto, el término adicional significa el contenido del appmon.[applicationname].add.[locale].xml . Este archivo especifica anulaciones y adiciones al archivo XML de diálogo.

También puede modificar el archivo XML de cuadro de diálogo adicional para una aplicación nativa con estos fines:

* Anulación del archivo XML del cuadro de diálogo para una aplicación con una respuesta diferente
* Adición de una respuesta a un cuadro de diálogo que no está abordado en el archivo XML de cuadro de diálogo para esa aplicación

El nombre de archivo que identifica un archivo XML de diálogo adicional es appmon.*[appname]*.add.*[locale]*.xml. Un ejemplo es appmon.excel.add.en_US.xml.

El nombre del archivo XML del cuadro de diálogo adicional debe utilizar el formato appmon.*[applicationname]*.add.*[locale]*.xml, donde  ** application-name debe coincidir exactamente con el nombre de la aplicación utilizado en el archivo de configuración XML y en la secuencia de comandos.

>[!NOTE]
>
>Ninguna de las aplicaciones genéricas especificadas en el archivo de configuración native2pdfconfig.xml tiene un archivo XML de diálogo principal. En la sección [Añadir o modificar compatibilidad con un formato de archivo nativo](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) se describen estas especificaciones.

Debe ordenar los `windowList` elementos que aparecen como secundarios en un elemento `window`. (Consulte [Ordenación de los elementos window y windowList](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements)).

### Modificación del archivo XML del cuadro de diálogo general {#modifying-the-general-dialog-xml-file}

Puede modificar el archivo XML del cuadro de diálogo general para responder a los cuadros de diálogo que genera el sistema o para responder a los cuadros de diálogo que son comunes a varias aplicaciones.

#### Adición de una entrada de tipo de archivo en el archivo de configuración XML {#adding-a-filetype-entry-in-the-xml-configuration-file}

Este procedimiento explica cómo actualizar el archivo de configuración del servicio Generate PDF para asociar tipos de archivo con aplicaciones nativas. Para actualizar este archivo de configuración, debe utilizar la consola de administración para exportar los datos de configuración a un archivo. El nombre de archivo predeterminado para los datos de configuración es native2pdfconfig.xml.

**Actualizar el archivo de configuración del servicio Generate PDF**

1. Seleccione **Inicio** > **Servicios** > **Generador de Adobe PDF** > **Archivos de configuración** y, a continuación, seleccione **Configuración de exportación**.
1. Modifique el elemento `filetype-settings` en el archivo native2pdfconfig.xml según sea necesario.
1. Seleccione **Inicio** > **Servicios** > **Generador de Adobe PDF** >**Archivos de configuración** y, a continuación, seleccione **Importar configuración**. Los datos de configuración se importan en el servicio Generate PDF (Generar PDF), sustituyendo a los ajustes anteriores.

>[!NOTE]
>
>El nombre de la aplicación se especifica como el valor del atributo `GenericApp` del elemento `name`. Este valor debe coincidir exactamente con el nombre correspondiente especificado en la secuencia de comandos que desarrolle para esa aplicación. Del mismo modo, el atributo `GenericApp` del elemento `displayName` debe coincidir exactamente con el rótulo de ventana `expectedWindow` de la secuencia de comandos correspondiente. Esta equivalencia se evalúa después de resolver cualquier expresión regular que aparezca en los atributos `displayName` o `caption`.

En este ejemplo, los datos de configuración predeterminados suministrados con el servicio Generate PDF se modificaron para especificar que el Bloc de notas (no Microsoft Word) se debe utilizar para procesar archivos con la extensión de nombre de archivo .txt. Antes de esta modificación, Microsoft Word se especificó como la aplicación nativa que debería procesar dichos archivos.

**Modificaciones para dirigir archivos de texto al Bloc de notas (native2pdfconfig.xml)**

```as3
 <filetype-settings> 
  
 <!-- Some native app file types were omitted for brevity. --> 
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. --> 
             <GenericApp 
                 extensions="txt" 
                 name="Notepad" displayName=".*Notepad"/> 
             <GenericApp  
                 extensions="wpd"  
                 name="WordPerfect" displayName="Corel WordPerfect"/> 
             <GenericApp extensions="pmd,pm6,p65,pm"  
                 name="PageMaker" displayName="Adobe PageMaker"/> 
             <GenericApp extensions="fm"  
                 name="FrameMaker" displayName="Adobe FrameMaker"/> 
             <GenericApp extensions="psd"  
                 name="Photoshop" displayName="Adobe Photoshop"/> 
         </settings> 
     </filetype-settings>
```

#### Creación de una variable de entorno para localizar la aplicación nativa {#creating-an-environment-variable-to-locate-the-native-application}

Cree una variable de entorno que especifique la ubicación del ejecutable de la aplicación nativa. La variable debe utilizar el formato *[application name]*_PATH, donde *application name* debe coincidir exactamente con el nombre de la aplicación utilizado en el archivo de configuración XML y en la secuencia de comandos, y donde la ruta contiene la ruta al ejecutable entre comillas dobles. Un ejemplo de una variable de entorno de este tipo es `Photoshop_PATH`.

Después de crear la nueva variable de entorno, debe reiniciar el servidor en el que se implementa el servicio Generate PDF.

**Crear una variable del sistema en el entorno de Windows XP**

1. Seleccione **Panel de control de Campaign > Sistema**.
1. En el cuadro de diálogo Propiedades del sistema, haga clic en la ficha **Avanzado** y, a continuación, haga clic en **Variables de entorno**.
1. En Variables del sistema en el cuadro de diálogo Variables de entorno, haga clic en **Nuevo**.
1. En el cuadro de diálogo Nueva variable del sistema, en el cuadro **Variable name**, escriba un nombre que utilice el formato *[application name]*_PATH.
1. En el cuadro **Variable value**, escriba la ruta completa y el nombre de archivo del archivo ejecutable de la aplicación y, a continuación, haga clic en **OK**. Por ejemplo, escriba: `c:\windows\Notepad.exe`
1. En el cuadro de diálogo Variables de entorno, haga clic en **Aceptar**.

**Crear una variable del sistema desde la línea de comandos**

1. En una ventana de línea de comandos, escriba la definición de la variable con este formato:

   ```as3
            [applicationname]_PATH=[Full path name]
   ```

   Por ejemplo, escriba: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Inicie una nueva línea de comandos para que la variable del sistema surta efecto.

#### Archivos XML {#xml-files}

AEM Forms incluye archivos XML de ejemplo que hacen que el servicio Generate PDF utilice el Bloc de notas para procesar cualquier archivo con la extensión de nombre de archivo .txt. Este código se incluye en esta sección. Además, debe realizar las demás modificaciones descritas en esta sección.

#### Archivo XML de cuadro de diálogo adicional {#additional-dialog-xml-file}

Este ejemplo contiene los cuadros de diálogo adicionales para la aplicación Notepad. Estos cuadros de diálogo pueden ser adicionales a los especificados por el servicio Generate PDF.

**Cuadro de diálogo del bloc de notas (appmon.notepad.add.en_US.xml)**

```as3
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd"> 
     <window caption="Caption Title"> 
         <windowList> 
             <window className="Button" caption="OK" action="press"/> 
         </windowList> 
     </window> 
 </dialogs>
```

#### Archivo XML de script {#script-xml-file}

Este ejemplo especifica cómo el servicio Generate PDF debe interactuar con el Bloc de notas para imprimir archivos utilizando la impresora Adobe PDF.

**Archivo XML de script del bloc de notas (appmon.notepad.script.en_US.xml)**

```as3
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<!-- 
* 
* ADOBE CONFIDENTIAL 
* ___________________ 
* Copyright 2004 - 2005 Adobe Systems Incorporated 
* All Rights Reserved. 
* 
* NOTICE:  All information contained herein is, and remains 
* the property of Adobe Systems Incorporated and its suppliers, 
* if any.  The intellectual and technical concepts contained 
* herein are proprietary to Adobe Systems Incorporated and its 
* suppliers and may be covered by U.S. and Foreign Patents, 
* patents in process, and are protected by trade secret or copyright law. 
* Dissemination of this information or reproduction of this material 
* is strictly forbidden unless prior written permission is obtained 
* from Adobe Systems Incorporated. 
*--> 
 
<!-- This file automates printing of text files via notepad to Adobe PDF printer. In order to see the complete hierarchy we recommend using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps--> 
 
<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd"> 
 
    <!-- In this step we wait for the application window to appear --> 
    <step> 
        <expectedWindow> 
            <window caption=".*Notepad"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->         
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Open...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear --> 
    <step> 
        <acquiredWindow> 
            <window caption="Open"> 
                <windowList> 
                    <window className="ComboBoxEx32"> 
                        <windowList> 
                            <window className="ComboBox"> 
                                <windowList> 
                                <window className="Edit" action="inputSourcePath"/> 
                                </windowList> 
                            </window> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Open" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open" action="disappear"/> 
        </expectedWindow> 
        <pause value="30"/> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog--> 
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Print...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print"> 
        </window> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Print dialog and click on the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"> 
                        <windowList> 
                            <window className="Button" caption="Preferences" action="press"/> 
                        </windowList> 
                    </window> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which  has the caption '"View Adobe PDF results' and we click on the button OK. The expectation is that 'Printing Preferences' dialog disappears. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Printing Preferences"> 
                <windowList> 
                    <window caption="Adobe PDF Settings"> 
                        <windowList> 
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/> 
                        </windowList> 
                        <windowList> 
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="OK" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the 'Print' dialog and click on the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"/> 
                    <window className="Button" caption="^Print$" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print" action="disappear"/> 
        </expectedWindow> 
    </step> 
    <step> 
        <expectedWindow> 
            <window caption="Save PDF File As"/> 
        </expectedWindow> 
    </step> 
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click on the Save button. The expectation is that the dialog disappears--> 
    <step> 
        <acquiredWindow> 
            <window caption="Save PDF File As"> 
                <windowList> 
                    <window className="Edit" action="inputDestinationPath"/> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Save" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Save PDF File As" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. --> 
    <abortMessage msg="15078"/> 
</application>
```
