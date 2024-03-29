---
title: Procesar formularios basados en fragmentos
seo-title: Rendering Forms Based on Fragments
description: Utilice el servicio Forms para procesar formularios basados en fragmentos creados con Designer.
seo-description: Use the Forms service to render forms that are based on fragments created using Designer.
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
role: Developer
exl-id: 49c4af9a-5797-468c-b3ad-f3140d445ff2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2231'
ht-degree: 4%

---

# Procesar formularios basados en fragmentos {#rendering-forms-based-on-fragments}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Procesar formularios basados en fragmentos {#rendering-forms-based-on-fragments-inner}

El servicio Forms puede procesar formularios basados en fragmentos creados con Designer. A *fragmento* es una parte reutilizable de un formulario y se guarda como un archivo XDP independiente que se puede insertar en varios diseños de formulario. Por ejemplo, un fragmento puede incluir un bloque de direcciones o texto legal.

El uso de fragmentos simplifica y acelera la creación y el mantenimiento de un gran número de formularios. Al crear un nuevo formulario, inserte una referencia al fragmento requerido y éste aparecerá en el formulario. La referencia de fragmento contiene un subformulario que señala al archivo XDP físico. Para obtener información sobre la creación de diseños de formulario basados en fragmentos, consulte [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Un fragmento puede incluir varios subformularios que se ajustan en un conjunto de subformularios de opciones. Los conjuntos de subformularios de opciones controlan la visualización de subformularios en función del flujo de datos de una conexión de datos. Se utilizan afirmaciones condicionales para determinar qué subformulario del conjunto aparece en el formulario enviado. Por ejemplo, cada subformulario de un conjunto puede incluir información de una ubicación geográfica concreta, y el subformulario que se muestra se puede determinar en función de la ubicación del usuario.

A *fragmento de secuencia de comandos* contiene funciones o valores de JavaScript reutilizables que se almacenan por separado de cualquier objeto en particular, como un analizador de fechas o una invocación de servicio Web. Estos fragmentos incluyen un único objeto de secuencia de comandos que aparece como un elemento secundario de variables en la paleta Jerarquía. Los fragmentos no se pueden crear a partir de secuencias de comandos que sean propiedades de otros objetos, como secuencias de comandos de sucesos validate, calculate o initialize.

Estas son las ventajas de utilizar fragmentos:

* **Reutilización de contenido**: Puede utilizar fragmentos para reutilizar contenido en varios diseños de formulario. Cuando necesita utilizar parte del mismo contenido en varios formularios, es más rápido y sencillo utilizar un fragmento que copiar o volver a crear el contenido. El uso de fragmentos también garantiza que el contenido y el aspecto de las partes de un diseño de formulario que se utilizan con frecuencia sean coherentes en todos los formularios de referencia.
* **Actualizaciones globales**: Puede utilizar fragmentos para realizar cambios globales en varios formularios solo una vez, en un archivo. Puede cambiar el contenido, los objetos de secuencia de comandos, los enlaces de datos, la presentación o los estilos de un fragmento, y todos los formularios XDP que hagan referencia al fragmento reflejarán los cambios.
* Por ejemplo, un elemento común en muchos formularios podría ser un bloque de direcciones que incluya un objeto de lista desplegable para el país. Si necesita actualizar los valores del objeto de lista desplegable, debe abrir muchos formularios para realizar los cambios. Si incluye el bloque de direcciones en un fragmento, solo necesita abrir un archivo de fragmento para realizar los cambios.
* Para actualizar un fragmento en un formulario de PDF, debe volver a guardar el formulario en Designer.
* **Creación de formularios compartidos**: Puede utilizar fragmentos para compartir la creación de formularios entre varios recursos. Los desarrolladores de formularios con experiencia en secuencias de comandos u otras funciones avanzadas de Designer pueden desarrollar y compartir fragmentos que aprovechan las secuencias de comandos y las propiedades dinámicas. Los diseñadores de formularios pueden utilizar esos fragmentos para presentar diseños de formulario y garantizar que todas las partes de un formulario tengan un aspecto y una funcionalidad coherentes en los distintos formularios diseñados por varias personas.

### Montaje de un diseño de formulario ensamblado mediante fragmentos {#assembling-a-form-design-assembled-using-fragments}

Puede ensamblar un diseño de formulario para pasarlo al servicio Forms basado en varios fragmentos. Para ensamblar varios fragmentos, utilice el servicio Assembler. Para ver un ejemplo del uso del servicio Ensamblar para crear un diseño de formulario que utilice otro servicio de Forms (el servicio Output ), consulte [Creación de documentos del PDF mediante fragmentos](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). En lugar de utilizar el servicio Output , puede realizar el mismo flujo de trabajo mediante el servicio Forms.

Al utilizar el servicio Assembler, se pasa un diseño de formulario que se ensambló con fragmentos. El diseño de formulario creado no hace referencia a otros fragmentos. Por el contrario, en este tema se trata el paso de un diseño de formulario que haga referencia a otros fragmentos al servicio Forms. Sin embargo, Assembler no montó el diseño de formulario. Se creó en Designer.

>[!NOTE]
>
>Para obtener más información sobre el servicio Forms, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Para obtener información sobre la creación de una aplicación basada en Web que procese formularios basados en fragmentos, consulte [Creación de aplicaciones web que procesen Forms](/help/forms/developing/creating-web-applications-renders-forms.md).

### Resumen de los pasos {#summary-of-steps}

Para procesar un formulario basado en fragmentos, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un objeto de API de cliente de Forms.
1. Especifique valores de URI.
1. Procese el formulario.
1. Escriba el flujo de datos del formulario en el explorador web del cliente.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

**Creación de un objeto de API de cliente de Forms**

Para poder realizar mediante programación una operación de API de cliente de servicio de Forms, debe crear un cliente de servicio de Forms.

**Especificar valores de URI**

Para procesar correctamente un formulario basado en fragmentos, debe asegurarse de que el servicio Forms puede localizar tanto el formulario como los fragmentos (archivos XDP) a los que hace referencia el diseño de formulario. Por ejemplo, supongamos que el formulario se denomina PO.xdp y que este formulario utiliza dos fragmentos llamados FooterUS.xdp y FooterCanada.xdp. En este caso, el servicio de Forms debe poder localizar los tres archivos XDP.

Puede organizar un formulario y sus fragmentos colocando el formulario en una ubicación y los fragmentos en otra, o bien puede colocar todos los archivos XDP en la misma ubicación. A los efectos de esta sección, supongamos que todos los archivos XDP se encuentran en el repositorio de AEM Forms. Para obtener información sobre cómo colocar archivos XDP en el repositorio de AEM Forms, consulte [Escribir recursos](/help/forms/developing/aem-forms-repository.md#writing-resources).

Al procesar un formulario basado en fragmentos, debe hacer referencia únicamente al formulario en sí y no a los fragmentos. Por ejemplo, debe hacer referencia a PO.xdp y no a FooterUS.xdp o FooterCanada.xdp. Asegúrese de colocar los fragmentos en una ubicación en la que el servicio de Forms pueda localizarlos.

**Procesamiento del formulario**

Un formulario basado en fragmentos se puede procesar de la misma manera que los formularios no fragmentados. Es decir, puede procesar el formulario como PDF, HTML o guías de formulario (obsoleto). El ejemplo de esta sección procesa un formulario basado en fragmentos como un formulario PDF interactivo. (Consulte [Renderización de PDF forms interactivos](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**Escribir el flujo de datos del formulario en el explorador web del cliente**

Cuando el servicio Forms procesa un formulario, devuelve un flujo de datos de formulario que debe escribir en el explorador web del cliente. Cuando se escribe en el explorador web del cliente, el formulario es visible para el usuario.

**Consulte también**

[Representar formularios en función de fragmentos mediante la API de Java](#render-forms-based-on-fragments-using-the-java-api)

[Representar formularios en función de fragmentos mediante la API de servicio web](#render-forms-based-on-fragments-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de Forms](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Procesar formularios PDF interactivos](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Creación de aplicaciones web que procesen Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Representar formularios en función de fragmentos mediante la API de Java {#render-forms-based-on-fragments-using-the-java-api}

Representar un formulario basado en fragmentos utilizando la API de Forms (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR del cliente, como adobe-forms-client.jar, en la ruta de clase de su proyecto Java.

1. Creación de un objeto de API de cliente de Forms

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `FormsServiceClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Especificar valores de URI

   * Cree un `URLSpec` objeto que almacena valores de URI utilizando su constructor.
   * Invocar el `URLSpec` del objeto `setApplicationWebRoot` y pase un valor de cadena que represente la raíz web de la aplicación.
   * Invocar el `URLSpec` del objeto `setContentRootURI` y pase un valor de cadena que especifique el valor de URI raíz del contenido. Asegúrese de que el diseño de formulario y los fragmentos se encuentran en el URI raíz del contenido. Si no es así, el servicio de Forms genera una excepción. Para hacer referencia al repositorio, especifique `repository://`.
   * Invocar el `URLSpec` del objeto `setTargetURL` y pase un valor de cadena que especifique el valor de la dirección URL de destino donde se publican los datos del formulario. Si define la dirección URL de destino en el diseño de formulario, puede pasar una cadena vacía. También puede especificar la dirección URL a la que se envía un formulario para realizar cálculos.

1. Procesamiento del formulario

   Invocar el `FormsServiceClient` del objeto `renderPDFForm` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del diseño de formulario, incluida la extensión del nombre de archivo. Si hace referencia a un diseño de formulario que forma parte de una aplicación de Forms, asegúrese de especificar la ruta completa, como `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` objeto que contiene datos para combinar con el formulario. Si no desea combinar datos, pase un vacío `com.adobe.idp.Document` objeto.
   * A `PDFFormRenderSpec` que almacena opciones en tiempo de ejecución.
   * A `URLSpec` objeto que contiene valores de URI necesarios para el servicio Forms para procesar un formulario basado en fragmentos.
   * A `java.util.HashMap` que almacena archivos adjuntos. Este es un parámetro opcional y puede especificar `null` si no desea adjuntar archivos al formulario.

   La variable `renderPDFForm` el método devuelve un `FormsResult` objeto que contiene un flujo de datos de formulario que debe escribirse en el explorador web del cliente.

1. Escribir el flujo de datos del formulario en el explorador web del cliente

   * Cree un `com.adobe.idp.Document` invocando el objeto `FormsResult` objeto ‘s `getOutputContent` método.
   * Obtenga el tipo de contenido de la variable `com.adobe.idp.Document` invocando su `getContentType` método.
   * Configure las variables `javax.servlet.http.HttpServletResponse` tipo de contenido del objeto invocando su `setContentType` y pasar el tipo de contenido de la variable `com.adobe.idp.Document` objeto.
   * Cree un `javax.servlet.ServletOutputStream` objeto utilizado para escribir el flujo de datos del formulario en el explorador web del cliente invocando la variable `javax.servlet.http.HttpServletResponse` del objeto `getOutputStream` método.
   * Cree un `java.io.InputStream` invocando el objeto `com.adobe.idp.Document` del objeto `getInputStream` método.
   * Crear una matriz de bytes rellenarla con la secuencia de datos del formulario invocando la variable `InputStream` del objeto `read`y pasando la matriz de bytes como argumento.
   * Invocar el `javax.servlet.ServletOutputStream` del objeto `write` método para enviar la secuencia de datos del formulario al explorador web del cliente. Pase la matriz de bytes a la `write` método.

**Consulte también**

[Procesar formularios basados en fragmentos](#rendering-forms-based-on-fragments)

[Inicio rápido (modo SOAP): Representación de un formulario basado en fragmentos mediante la API de Java](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Representar formularios en función de fragmentos mediante la API de servicio web {#render-forms-based-on-fragments-using-the-web-service-api}

Representar un formulario basado en fragmentos mediante la API de Forms (servicio web):

1. Incluir archivos de proyecto

   * Cree clases de proxy Java que consuman el WSDL del servicio Forms.
   * Incluya las clases proxy de Java en la ruta de clase.

1. Creación de un objeto de API de cliente de Forms

   Cree un `FormsService` y establezca los valores de autenticación.

1. Especificar valores de URI

   * Cree un `URLSpec` que almacenan valores de URI usando su constructor.
   * Invocar el `URLSpec` del objeto `setApplicationWebRoot` y pase un valor de cadena que represente la raíz web de la aplicación.
   * Invocar el `URLSpec` del objeto `setContentRootURI` y pase un valor de cadena que especifique el valor de URI raíz del contenido. Asegúrese de que el diseño de formulario se encuentra en el URI raíz del contenido. Si no es así, el servicio de Forms genera una excepción. Para hacer referencia al repositorio, especifique `repository://`.
   * Invocar el `URLSpec` del objeto `setTargetURL` y pase un valor de cadena que especifique el valor de la dirección URL de destino donde se publican los datos del formulario. Si define la dirección URL de destino en el diseño de formulario, puede pasar una cadena vacía. También puede especificar la dirección URL a la que se envía un formulario para realizar cálculos.

1. Procesamiento del formulario

   Invocar el `FormsService` del objeto `renderPDFForm` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del diseño de formulario, incluida la extensión del nombre de archivo. Si hace referencia a un diseño de formulario que forma parte de una aplicación de Forms, asegúrese de especificar la ruta completa, como `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` objeto que contiene datos para combinar con el formulario. Si no desea combinar datos, pase `null`.
   * A `PDFFormRenderSpec` que almacena opciones en tiempo de ejecución. Tenga en cuenta que la opción de PDF etiquetado no se puede establecer si el documento de entrada es un documento de PDF. Si el archivo de entrada es un archivo XDP, se puede configurar la opción de PDF etiquetado.
   * A `URLSpec` que contiene valores de URI requeridos por el servicio de Forms.
   * A `java.util.HashMap` que almacena archivos adjuntos. Este es un parámetro opcional y puede especificar `null` si no desea adjuntar archivos al formulario.
   * Un vacío `com.adobe.idp.services.holders.BLOBHolder` objeto que rellena el método . Este parámetro se utiliza para almacenar el formulario procesado.
   * Un vacío `javax.xml.rpc.holders.LongHolder` objeto que rellena el método . Este argumento almacenará el número de páginas del formulario.
   * Un vacío `javax.xml.rpc.holders.StringHolder` objeto que rellena el método . Este argumento almacenará el valor de configuración regional.
   * Un vacío `com.adobe.idp.services.holders.FormsResultHolder` que contendrá los resultados de esta operación.

   La variable `renderPDFForm` rellena el `com.adobe.idp.services.holders.FormsResultHolder` objeto que se pasa como el último valor de argumento con un flujo de datos de formulario que debe escribirse en el explorador web del cliente.

1. Escribir el flujo de datos del formulario en el explorador web del cliente

   * Cree un `FormResult` obteniendo el valor de `com.adobe.idp.services.holders.FormsResultHolder` del objeto `value` miembro de datos.
   * Cree un `BLOB` objeto que contiene datos de formulario invocando la variable `FormsResult` del objeto `getOutputContent` método.
   * Obtenga el tipo de contenido de la variable `BLOB` invocando su `getContentType` método.
   * Configure las variables `javax.servlet.http.HttpServletResponse` tipo de contenido del objeto invocando su `setContentType` y pasar el tipo de contenido de la variable `BLOB` objeto.
   * Cree un `javax.servlet.ServletOutputStream` objeto utilizado para escribir el flujo de datos del formulario en el explorador web del cliente invocando la variable `javax.servlet.http.HttpServletResponse` del objeto `getOutputStream` método.
   * Cree una matriz de bytes y rellénela invocando la variable `BLOB` del objeto `getBinaryData` método. Esta tarea asigna el contenido de la variable `FormsResult` a la matriz de bytes.
   * Invocar el `javax.servlet.http.HttpServletResponse` del objeto `write` método para enviar la secuencia de datos del formulario al explorador web del cliente. Pase la matriz de bytes a la `write` método.

**Consulte también**

[Procesar formularios basados en fragmentos](#rendering-forms-based-on-fragments)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
