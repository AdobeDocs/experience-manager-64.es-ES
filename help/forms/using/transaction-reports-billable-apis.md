---
title: API facturables de informes de transacciones
seo-title: Transaction Reports Billable APIs
description: Lista de todas las API que se contabilizan como transacciones
seo-description: List of all the APIs that are accounted as transactions
uuid: 8861e325-7393-4d2c-9ec1-17f391ca3909
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 82e72ffb-2faa-45fe-8bb2-f485d8fa043e
exl-id: 18b5c6e2-3b0c-4ec8-9e65-c4105b47be4e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1895'
ht-degree: 93%

---

# API facturables de informes de transacciones {#transaction-reports-billable-apis}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Lista de todas las API que se contabilizan como transacciones

AEM Forms ofrece varias API para enviar formularios, procesar documentos y representar documentos. Algunas API se contabilizan como transacciones y otras se pueden usar libremente. Este documento proporciona una lista de todas las API que se contabilizan como transacciones en un informe de transacciones. Estos son algunos escenarios comunes en los que se utiliza un API facturable:

* Enviar un formulario adaptable, un formulario HTML5 y un conjunto de formularios
* Representar una versión impresa o web de una comunicación interactiva
* Convertir un documento de un formato a otro
* Acoplar un documento PDF dinámico
* Generar un documento de registro
* Combinar un documento PDF interactivo con otro documento PDF
* Usar los pasos asignar tarea y servicios doc de flujos de trabajo de AEM
* Usar formularios adaptables en un formulario adaptable

Las API de facturación no tienen en cuenta el número de páginas, la longitud de un documento o formulario o el formato final del documento representado. Un informe de transacciones divide las transacciones en tres categorías: Documentos procesados, documentos procesados y Forms enviado.

* **Formularios enviados:** Cuando los datos se envían desde cualquier tipo de formulario creado con AEM Forms y los datos se envían a cualquier repositorio de almacenamiento de datos o base de datos, se considera envío de formulario. Por ejemplo, el envío de un formulario adaptable, un formulario HTML5, PDF Forms y un conjunto de formularios se contabilizan como formularios enviados. Cada formulario de un conjunto de formularios se considera un envío. Por ejemplo, si un conjunto de formularios tiene 5 formularios, cuando se envía el conjunto de formularios, el servicio de informes de transacciones lo contabiliza como 5 envíos.
* **Documentos representados:** Generar un documento mediante la combinación de una plantilla y datos, la firma o certificación digitalmente de un documento, el uso de las API de servicios de documentos facturables para servicios de documento o la conversión de un documento de un formato a otro se contabilizan como documentos representados.

>[!NOTE]
>
>La interfaz de usuario Informes de transacciones muestra tres categorías: formularios enviados, documentos representados y documentos procesados. Tanto los documentos representados como los documentos procesados se contabilizan como documentos representados.

## API de servicios de documentos facturables {#billable-document-services-apis}

### Generar un servicio PDF {#generate-pdf-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td> 
   <td>Crea un Adobe PDF a partir de tipos de archivo compatibles.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td> 
   <td>Crea un Adobe PDF a partir de tipos de archivo compatibles.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td> 
   <td>Convierte un Adobe PDF en tipos de archivo compatibles. </td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td> 
   <td>Convierte un Adobe PDF en tipos de archivo compatibles. </td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td> 
   <td>Convierte un Adobe PDF en tipos de archivo compatibles. </td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td> 
   <td><p>Crea un PDF a partir de páginas HTML.</p> </td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td> 
   <td>Crea un PDF a partir de direcciones URL que señalan una página HTML.</td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td> 
   <td>Crea un PDF a partir de direcciones URL que señalan una página HTML.</td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td> 
   <td>Optimiza al PDF para reducir el tamaño del archivo eliminando metadatos innecesarios sin afectar a la calidad.</td> 
   <td>Documentos procesados<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio Distiller {#distiller-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td> 
   <td>Crea un Adobe PDF a partir de tipos de archivo compatibles.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td> 
   <td>Crea un Adobe PDF a partir de tipos de archivo compatibles.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Documento de servicio de registro (Servicio DoR) {#document-of-record-service-dor-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td> 
   <td>Invoca el método de representación especificado para generar un documento de registro utilizando los parámetros proporcionados.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio de salida {#output-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td> 
   <td>Combina datos y plantillas para crear un documento de PDF.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PDFOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePDFOutputBatch</a></td> 
   <td>Combina datos y plantillas para crear un conjunto de documentos PDF.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td> 
   <td>Convierte los documentos XDP y PDF a los formatos de archivo PostScript (PS), Printer Command Language (PCL) y ZPL. </td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td> 
   <td>Convierte los documentos XDP y PDF a los formatos de archivo PostScript (PS), Printer Command Language (PCL) y ZPL. </td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PrintedOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePrintedOutputBatch</a></td> 
   <td>Convierte un conjunto de documentos XDP y PDF a un conjunto de formatos de archivo PostScript (PS), Printer Command Language (PCL) y ZPL. </td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio de Forms {#forms-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td> 
   <td>Representa el formulario PDF a partir de plantillas XDP. Las plantillas XP se crean en Forms Designer.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td> 
   <td>Extrae datos de un formulario PDF o de plantillas XDP</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio ConvertPDF {#convert-pdf-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td> 
   <td>Convierte un documento PDF en una lista de documentos de imagen. Los formatos de imagen compatibles son JPEG, JPEG2K, PNG y TIFF.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td> 
   <td>Convierte un archivo de PDF plano al formato PostScript mediante las opciones especificadas en la especificación de opciones.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio de Forms con códigos de barras {#barcoded-forms-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td> 
   <td>Descodifica todos los códigos de barras en un objeto de documento y devuelve un objeto de documento org.w3c.dom. que contiene datos recuperados del código de barras.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio Assembler {#assembler-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">invoke</a></td> 
   <td>Ejecuta el documento DDX especificado y devuelve un objeto <a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a> que contiene los documentos resultantes. </td> 
   <td>Documentos procesados</td> 
   <td>Las siguientes operaciones no se contabilizan como transacciones:
    <ul> 
     <li>Crear paquetes o portafolios</li> 
     <li>Configurar varios XDP </li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">invoke</a></td> 
   <td>Ejecuta el documento DDX especificado y devuelve un objeto <a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a> que contiene los documentos resultantes. </td> 
   <td>Documentos procesados</td> 
   <td>Todos los formatos de archivo de entrada compatibles con Generador de PDF, Formularios y Servicios de salida; el servicio Ensamblador admite todos esos formatos como formatos de archivo de salida. </td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-" target="_blank">toPDFA</a></td> 
   <td>Convertir un documento especificado en PDF/A utilizando las opciones especificadas.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* El API de invocación del servicio de ensamblador puede llamar internamente a un API facturable de otro servicio en función de la entrada. Por lo tanto, la API de invocación puede contabilizarse como ninguna, única o múltiples transacciones. El número de transacciones contabilizadas depende de la entrada y las API internas invocadas.
>* Un documento PDF único producido mediante el servicio de ensamblador puede contabilizarse como ninguna, única o múltiples transacciones. El número de transacciones contabilizadas depende del código DDX proporcionado.
>


### Servicio de utilidad de PDF  {#pdf-utility-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td> 
   <td>Convierte un documento PDF en un archivo XDP. Para que un documento PDF se convierta correctamente en un archivo XDP, el documento PDF debe contener un flujo XFA en el diccionario AcroForm.</td> 
   <td>Documentos procesados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Servicio Doc Assurance {#doc-assurance-service}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/docassurance/client/api/DocAssuranceService.html#secureDocument-com.adobe.aemfd.docmanager.Document-com.adobe.fd.docassurance.client.api.EncryptionOptions-com.adobe.fd.docassurance.client.api.SignatureOptions-com.adobe.fd.docassurance.client.api.ReaderExtensionOptions-com.adobe.fd.signatures.pdf.inputs.UnlockOptions-">secureDocument</a></td> 
   <td>La API permite proteger el documento. Puede utilizar la API para firmar, certificar, leer, ampliar o encriptar un documento PDF. </td> 
   <td>Documentos procesados</td> 
   <td>Firme y certifique únicamente el funcionamiento de la variable <a href="https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/docassurance/client/api/DocAssuranceService.html#secureDocument-com.adobe.aemfd.docmanager.Document-com.adobe.fd.docassurance.client.api.EncryptionOptions-com.adobe.fd.docassurance.client.api.SignatureOptions-com.adobe.fd.docassurance.client.api.ReaderExtensionOptions-com.adobe.fd.signatures.pdf.inputs.UnlockOptions-">secureDocument</a> se facturan.</td> 
  </tr>
 </tbody>
</table>

## API de captura de datos facturables {#billable-data-capture-apis}

Todos los eventos de envío de formularios adaptables, formularios HTML5 y conjuntos de formularios se contabilizan como transacciones. De forma predeterminada, el envío de un formulario PDF no se contabiliza como una transacción. Utilice el [API de informes de transacciones](record-transaction-custom-implementation.md) para registrar un envío de PDF forms como una transacción.

### Formularios adaptables {#adaptive-forms}

<table> 
 <tbody>
  <tr>
   <td><p>Caso práctico</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td>Enviar un formulario adaptable</td> 
   <td>Envía un formulario adaptable a la acción de envío configurada. </td> 
   <td>Formularios enviados</td> 
   <td>
    <ul> 
     <li>Cuenta de envíos correcta para una o dos transacciones. El número de transacciones contabilizadas depende del tipo de acción de envío utilizada para el envío. Por ejemplo, enviar al PDF mediante cuentas de acción de envío por correo electrónico para dos recuentos de transacciones. Una transacción para el envío de formularios y otra para el PDF generado mediante el servicio documento de registro (DOR). </li> 
     <li>El uso del formulario adaptable en un formulario adaptable (conjunto de formularios de formulario adaptable) contabiliza solo una transacción. Puede tener cualquier número de formularios adaptables dentro de un formulario adaptable.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Formularios HTML5 {#html-forms}

<table> 
 <tbody>
  <tr>
   <td><p>Caso práctico</p> </td> 
   <td>Descripción </td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td>Enviar un formulario HTML5</td> 
   <td>Envía un formulario HTML5 para enviar la dirección URL configurada en el formulario.</td> 
   <td>Formularios enviados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Conjunto de formularios {#form-set}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td>Enviar un conjunto de formularios</td> 
   <td>Envía el conjunto de formularios a la dirección URL de envío configurada en el conjunto de formularios.</td> 
   <td>Formularios enviados</td> 
   <td>
    <ul> 
     <li>El uso del formulario adaptable en un formulario adaptable (conjunto de formularios de formulario adaptable) contabiliza solo una transacción. Puede tener cualquier número de formularios adaptables dentro de un formulario adaptable.</li> 
     <li>Todos los formularios de un conjunto de formularios de Formularios HTML5 se contabilizan como una transacción independiente. </li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Flujos de trabajo de comunicación interactiva facturables y AEM centrados en formularios en las API de OSGi {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Asignar pasos de tareas y servicios de documentos de flujos de trabajo AEM centrados en formularios en OSGi y todas las representaciones de comunicación interactiva y se contabilizan como transacciones. La vista previa de una comunicación interactiva en la instancia de autor y la vista previa en la instancia de publicación mediante la interfaz de usuario del agente no se contabilizan como transacciones. Si un paso de flujo de trabajo cuenta una transacción y el flujo de trabajo no se completa, el recuento de transacciones no se invierte.

### Comunicación interactiva - Canal web {#interactive-communication-web-channel}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td>Representar un canal web</td> 
   <td>Abre la versión web de una comunicación interactiva.</td> 
   <td>Documentos representados</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
 </tbody>
</table>

### Comunicación interactiva - Canal de impresión {#interactive-communication-print-channel}

<table> 
 <tbody>
  <tr>
   <td><p>API</p> </td> 
   <td>Descripción</td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">representar</a> (convertir en PDF)</td> 
   <td>Genera la versión PDF de una comunicación interactiva.</td> 
   <td>Documentos representados</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
 </tbody>
</table>

### Flujos de trabajo AEM centrados en formularios en OSGi  {#form-centric-aem-workflows-on-osgi}

<table> 
 <tbody>
  <tr>
   <td><p>Caso de uso</p> </td> 
   <td>Categoría del informe de transacción</td> 
   <td>Información adicional</td> 
  </tr>
  <tr>
   <td>Enviar un paso Asignar tarea</td> 
   <td>Formularios enviados</td> 
   <td>
    <div> 
    </div> </td> 
  </tr>
  <tr>
   <td>Enviar un punto de inicio de aplicación de flujo de trabajo </td> 
   <td>Formularios enviados</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Enviar una comunicación interactiva (canal de impresión) desde la interfaz de usuario del agente a un flujo de trabajo</td> 
   <td>Documentos representados</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Registrar API facturables como transacciones para código personalizado {#recording-billable-apis-as-transactions-for-custom-code}

Las acciones como enviar un formulario PDF, utilizar la interfaz de usuario del agente para obtener una vista previa de una comunicación interactiva, usar el envío de formulario no estándar y las implementaciones personalizadas no se contabilizan como transacciones. AEM Forms proporciona un API para registrar esas acciones como transacciones. Puede llamar al API desde sus implementaciones personalizadas para [registrar una transacción](record-transaction-custom-implementation.md).

## Artículos relacionados {#related-articles}

* [Información general sobre los informes de transacciones](/help/forms/using/transaction-reports-overview.md)
* [Ver y comprender los informes de transacciones](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Registrar una transacción para implementaciones personalizadas](/help/forms/using/record-transaction-custom-implementation.md)
