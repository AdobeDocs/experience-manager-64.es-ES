---
title: Inicio rápido (SOAP) de la API de Java del servicio Utilidades XMP
seo-title: XMP Utilities Service Java APIQuick Start(SOAP)
description: Utilice el servicio XMP Utilidades para exportar e importar XMP metadatos.
seo-description: Use the XMP Utilities service to export and import XMP metadata.
uuid: 5db4c623-75db-4a34-9ad2-3c917619e296
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 1b229ddf-9350-40b6-8056-dcbe0c5afd5b
role: Developer
exl-id: fdbf9942-7e4d-4b76-971f-d26d89c4c4cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 5%

---

# Inicio rápido de la API de Java del servicio de utilidades de XMP (SOAP) {#xmp-utilities-service-java-apiquick-start-soap}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los siguientes Inicio rápido están disponibles para el servicio XMP Utilidades.

[Inicio rápido (modo SOAP): Exportación de metadatos de XMP mediante la API de Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api)

[Inicio rápido (modo SOAP): Importación de metadatos de XMP mediante la API de Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api)

Las operaciones de AEM Forms se pueden realizar mediante la API con establecimiento inflexible de tipos de AEM Forms y el modo de conexión se debe establecer en SOAP.

>[!NOTE]
>
>Los inicios rápidos ubicados en Programación con formularios AEM se basan en el servidor de Forms si está utilizando otro sistema operativo, como UNIX, reemplace las rutas específicas de Windows con rutas compatibles con el sistema operativo aplicable. Del mismo modo, si utiliza otro servidor de aplicaciones J2EE, asegúrese de especificar propiedades de conexión válidas. Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Inicio rápido (modo SOAP): Exportación de metadatos de XMP mediante la API de Java {#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api}

El siguiente ejemplo de código recupera, inspecciona y guarda XMP metadatos. (Consulte [Exportación de metadatos desde documentos de PDF](/help/forms/developing/xmp-utilities.md#exporting-metadata-from-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-pdfutility-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import com.adobe.livecycle.xmputility.*; 
 import com.adobe.livecycle.xmputility.client.*; 
 import java.util.*; 
 import java.io.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class ExportMetadata 
 { 
     public static void main(String[] args) 
     { 
         try 
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             //Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a XMP Utility client 
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory); 
  
             // Specify a PDF document whose metadata is to be exported 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf"); 
             Document inDoc = new Document(fileInputStream); 
  
             // Export the XMP metadata object 
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(inDoc); 
  
             // Inspect the XMP metadata object (retrieve the document?s author in this case) 
             String name = myXmp.getAuthor(); 
             System.out.println("The document?s author is " + name); 
  
             // Export the XMP metadata to an XML file 
             Document outDoc = xmpUt.exportXMP(inDoc); 
             File xmpFile = new File("c:\\LoanMetaData.xml"); 
             outDoc.copyToFile(xmpFile); 
         } 
         catch (Exception e) 
         { 
             System.out.println("Error occurred: " + e.getMessage()); 
         } 
     } 
 } 
 
```

## Inicio rápido (modo SOAP): Importación de metadatos de XMP mediante la API de Java {#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api}

El siguiente ejemplo de código importa XMP metadatos y guarda el nuevo archivo de PDF en el disco. El documento del PDF se basa en un archivo del PDF llamado Loan.pdf. El documento XML que contiene los metadatos que se van a importar en el documento PDF se basa en un archivo XML denominado *LoanMetaData.xml*. Para obtener información sobre este archivo XML, consulte [Importación de metadatos en documentos de PDF](/help/forms/developing/xmp-utilities.md#importing-metadata-into-pdf-documents).

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-pdfutility-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import com.adobe.livecycle.xmputility.*; 
 import com.adobe.livecycle.xmputility.client.*; 
 import java.util.*; 
 import java.io.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class ImportMetadata 
 { 
     public static void main(String[] args) 
     { 
         try 
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             //Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a XMP Utility client 
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory); 
  
             //Specify a PDF document into which XMP metadata is imported 
             FileInputStream filePDF = new FileInputStream("C:\\Adobe\Loan.pdf"); 
             Document inDoc = new Document(filePDF); 
  
             //Specify an XML file containing XMP metadata to import 
             FileInputStream fileXML = new FileInputStream("C:\\Adobe\LoanMetaData.xml"); 
             Document xmpDoc = new Document(fileXML ); 
  
             //Import the XMP metadata 
             Document outDoc = xmpUt.importXMP(inDoc, xmpDoc); 
  
             //Inspect the XMP metadata object (retrieve the document?s author in this case) 
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(outDoc); 
             String name = myXmp.getAuthor(); 
             System.out.println("The document?s author is " + name); 
  
             //Save the PDF document containing the new metadata 
             File pdfFile = new File("c:\\Adobe\LoanWithMetadata.pdf"); 
             outDoc.copyToFile(pdfFile); 
         } 
         catch (Exception e) 
         { 
             System.out.println("Error occurred: " + e.getMessage()); 
         } 
     } 
 }
```
