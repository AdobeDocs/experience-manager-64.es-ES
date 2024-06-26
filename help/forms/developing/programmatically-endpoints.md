---
title: Administración programática de puntos de conexión
seo-title: Programmatically Managing Endpoints
description: Utilice el servicio de registro de puntos finales para añadir puntos finales de EJB, añadir puntos finales de SOAP, añadir puntos finales de carpeta vigilados, añadir puntos finales de correo electrónico, añadir puntos finales de Remoting, añadir puntos finales de Administrador de tareas, modificar puntos finales, eliminar puntos finales y recuperar información del conector de punto final.
seo-description: Use the Endpoint Registry service to add EJB endpoints, add SOAP endpoint, add Watched Folder endpoints, add Email endpoints, add  Remoting endpoints, add Task Manager endpoints, modify endpoints, remove endpoints, and retrieve endpoint connector information.
uuid: 5dc50946-3323-4c5d-a43b-31c1c980bd04
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 076889a7-9c9f-4b6f-a45b-67a9b3923c36
role: Developer
exl-id: 1dc43962-dffe-4062-838f-737b3100ad28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '10827'
ht-degree: 2%

---

# Administración programática de puntos de conexión {#programmatically-managing-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

**Acerca del servicio de registro de extremo**

El servicio Endpoint Registry permite administrar los extremos mediante programación. Por ejemplo, puede añadir los siguientes tipos de extremos a un servicio:

* EJB
* SOAP
* Carpeta vigilada
* Correo electrónico
* (obsoleto para formularios AEM) Remoting
* Administrador de tareas

   >[!NOTE]
   >
   >SOAP, EJB y (obsoleto para AEM formularios en JEE) Los extremos de reasignación se crean automáticamente para cada servicio activado. Los extremos SOAP y EJB permiten SOAP y EJB para todas las operaciones de servicio.

   Un extremo Remoting permite a los clientes de Flex invocar operaciones en el servicio AEM Forms al que se agrega el extremo. Se crea un destino de Flex con el mismo nombre que el extremo y los clientes de Flex pueden crear RemoteObjects que apunten a este destino para invocar operaciones en el servicio correspondiente.

   Los extremos Correo electrónico, Administrador de tareas y Carpeta vigilada exponen solo una operación específica del servicio. La adición de estos extremos requiere un segundo paso de configuración para seleccionar un método para invocar, establecer parámetros de configuración y especificar asignaciones de parámetros de entrada y salida.

   Puede organizar los extremos de TaskManager en grupos llamados *categories*. A continuación, estas categorías se exponen a Workspace mediante TaskManager, donde los usuarios finales ven los extremos de TaskManager a medida que se clasifican. Dentro de Workspace, los usuarios finales ven estas categorías en el panel de navegación. Los extremos de cada categoría se muestran como tarjetas de proceso en la página Iniciar procesos de Workspace.

   Puede realizar estas tareas mediante el servicio Endpoint Registry:

* Añada puntos finales de EJB. (Consulte [Adición de puntos de conexión EJB](programmatically-endpoints.md#adding-ejb-endpoints).)
* Añada extremos SOAP. (Consulte [Adición de puntos de conexión SOAP](programmatically-endpoints.md#adding-soap-endpoints).)
* Agregar extremos de carpeta vigilada (consulte [Añadir puntos finales de carpeta vigilada](programmatically-endpoints.md#adding-watched-folder-endpoints).)
* Añada puntos finales de correo electrónico. (Consulte [Añadir puntos de conexión de correo electrónico](programmatically-endpoints.md#adding-email-endpoints).)
* Añada los extremos de Remoting. (Consulte [Adición de puntos de conexión remotos](programmatically-endpoints.md#adding-remoting-endpoints).)
* Agregar extremos de TaskManager (consulte [Adición de puntos de conexión de TaskManager](programmatically-endpoints.md#adding-taskmanager-endpoints).)
* Modificación de puntos de conexión (consulte [Modificación de puntos finales](programmatically-endpoints.md#modifying-endpoints).)
* Eliminación de extremos (consulte [Eliminación de extremos](programmatically-endpoints.md#removing-endpoints).)
* Recuperar información del conector del extremo (Consulte [Recuperación de información del conector de extremo](programmatically-endpoints.md#retrieving-endpoint-connector-information).)

## Adición de puntos de conexión EJB {#adding-ejb-endpoints}

Puede añadir mediante programación un extremo EJB a un servicio mediante la API Java de AEM Forms. Al agregar un extremo EJB a un servicio, está permitiendo que una aplicación cliente invoque el servicio mediante el modo EJB. Es decir, al configurar las propiedades de conexión necesarias para invocar AEM Forms, puede seleccionar el modo EJB. (Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>No se puede agregar un punto final de EJB utilizando servicios web.

>[!NOTE]
>
>Normalmente, un punto final de EJB se agrega a un servicio de forma predeterminada. Sin embargo, se puede agregar un punto final de EJB a un proceso que se implementa mediante programación o cuando se eliminó un punto final de EJB y se debe agregar de nuevo.

### Resumen de los pasos {#summary-of-steps}

Para añadir un punto final de EJB a un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistry Client` objeto.
1. Establezca los atributos de extremo de EJB.
1. Cree un punto final de EJB.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Antes de añadir mediante programación un extremo de EJB, debe crear un `EndpointRegistryClient` objeto.

**Establecer atributos de extremo de EJB**

Para crear un punto final de EJB para un servicio, especifique los siguientes valores:

* **Identificador de conector**: Especifica el tipo de extremo que se va a crear. Para crear un extremo de EJB, especifique `EJB`.
* **Descripción**: Especifica la descripción del extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Identificador de servicio**: Especifica el servicio al que pertenece el extremo.
* **Nombre de la operación**: Especifica el nombre de la operación que se invoca mediante el extremo. Al crear un extremo de EJB, especifique un carácter comodín ( `*`). Sin embargo, si desea especificar una operación específica en lugar de invocar todas las operaciones de servicio, especifique el nombre de la operación en lugar de usar el carácter comodín ( `*`).

**Crear un extremo de EJB**

Después de establecer los atributos de extremo de EJB, puede crear un extremo de EJB para un servicio.

**Habilitar el punto final**

Después de crear un nuevo extremo, debe habilitarlo. Después de habilitar el extremo, se puede utilizar para invocar el servicio. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Añadir un extremo EJB mediante la API de Java](programmatically-endpoints.md#adding-an-ejb-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo EJB mediante la API de Java {#adding-an-ejb-endpoint-using-the-java-api}

Añada un punto final de EJB mediante la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java. (

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Establezca los atributos de extremo de EJB.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `EJB`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la operación que se invoca invocando la variable `CreateEndpointInfo` del objeto `setOperationName` y pase un valor de cadena que especifique el nombre de la operación. Para los extremos SOAP y EJB, especifique un carácter comodín ( `*`), lo que implica todas las operaciones.

1. Cree un punto final de EJB.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el nuevo punto final de EJB.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` método enable del objeto y pasar el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Añadir un extremo EJB mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Adición de puntos de conexión SOAP {#adding-soap-endpoints}

Puede añadir mediante programación un extremo SOAP a un servicio mediante la API Java de AEM Forms. Al agregar un extremo SOAP, se habilita una aplicación cliente para que invoque el servicio mediante el modo SOAP. Es decir, al configurar las propiedades de conexión necesarias para invocar AEM Forms, puede seleccionar el modo SOAP.

>[!NOTE]
>
>No se puede agregar un extremo SOAP utilizando servicios web.

>[!NOTE]
>
>Normalmente, un extremo SOAP se agrega a un servicio de forma predeterminada. Sin embargo, se puede agregar un extremo SOAP a un proceso que se implementa mediante programación o cuando se elimina un extremo SOAP y se tiene que agregar de nuevo.

### Resumen de los pasos {#summary_of_steps-1}

Para agregar un extremo SOAP a un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Establezca los atributos de extremo SOAP.
1. Cree un extremo SOAP.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Estos archivos JAR son necesarios para crear un extremo SOAP. Sin embargo, se requieren archivos JAR adicionales si se utiliza el extremo SOAP para invocar el servicio. Para obtener información sobre los archivos JAR de AEM Forms, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para agregar mediante programación un extremo SOAP a un servicio, debe crear un `EndpointRegistryClient` objeto.

**Establecer atributos de extremo SOAP**

Para agregar un extremo SOAP a un servicio, especifique los siguientes valores:

* **Valor del identificador del conector**: Especifica el tipo de extremo que se va a crear. Para crear un extremo SOAP, especifique `SOAP`.
* **Descripción**: Especifica la descripción del extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Valor del identificador de servicio**: Especifica el servicio al que pertenece el extremo.
* **Nombre de la operación**: Especifica el nombre de la operación que se invoca mediante el extremo. Al crear un extremo SOAP, especifique un carácter comodín ( `*`). Sin embargo, si desea especificar una operación específica en lugar de invocar todas las operaciones de servicio, especifique el nombre de la operación en lugar de usar el carácter comodín ( `*`).

**Crear un extremo SOAP**

Después de establecer los atributos de extremo SOAP, puede crear un extremo SOAP.

**Habilitar el punto final**

Después de crear un nuevo extremo, debe habilitarlo. Cuando el extremo está habilitado, se puede utilizar para invocar el servicio. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Añadir un extremo SOAP mediante la API de Java](programmatically-endpoints.md#add-a-soap-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo SOAP mediante la API de Java {#add-a-soap-endpoint-using-the-java-api}

Agregue un extremo SOAP a un servicio mediante la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Establezca los atributos de extremo SOAP.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `SOAP`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la operación que se invoca invocando la variable `CreateEndpointInfo` del objeto `setOperationName` y pasando un valor de cadena que especifica el nombre de la operación. Para los extremos SOAP y EJB, especifique un carácter comodín ( `*`), lo que implica todas las operaciones.

1. Cree un extremo SOAP.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el nuevo extremo SOAP.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` método enable del objeto y pase el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Añadir un extremo SOAP mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Añadir puntos finales de carpeta vigilada {#adding-watched-folder-endpoints}

Puede agregar mediante programación un extremo de carpeta vigilada a un servicio mediante la API Java de AEM Forms. Al agregar un extremo de carpeta vigilada, se permite a los usuarios colocar un archivo (como un archivo PDF) en una carpeta. Cuando el archivo se coloca en la carpeta , se invoca el servicio configurado y se manipula el archivo. Una vez que el servicio realiza la operación especificada, guarda el archivo modificado en una carpeta de salida especificada. Una carpeta vista está configurada para analizarse con un intervalo de velocidad fijo o con un programa cron, como todos los lunes, miércoles y viernes al mediodía.

Para añadir mediante programación un extremo de carpeta vigilada a un servicio, tenga en cuenta el siguiente proceso de corta duración denominado *EncryptDocument*. (Consulte [Explicación de los procesos de AEM Forms](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).)

![aw_aw_encryptdocumentprocess](assets/aw_aw_encryptdocumentprocess.png)

Este proceso acepta un documento de PDF no protegido como valor de entrada y, a continuación, pasa el documento de PDF no protegido al `EncryptPDFUsingPassword` operación. El documento del PDF está cifrado con una contraseña y el documento del PDF cifrado con contraseña es el valor de salida de este proceso. El nombre del valor de entrada (el documento PDF no protegido) es `InDoc` y el tipo de datos es `com.adobe.idp.Document`. El nombre del valor de salida (el documento de PDF cifrado con contraseña) es `SecuredDoc` y el tipo de datos es `com.adobe.idp.Document`.

>[!NOTE]
>
>No se puede agregar un extremo de carpeta vigilada mediante servicios web.

### Resumen de los pasos {#summary_of_steps-2}

Para agregar un extremo de carpeta vigilada a un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Establezca los atributos de extremo de la carpeta vigilada.
1. Especifique los valores de configuración.
1. Defina los valores de parámetro de entrada.
1. Defina un valor de parámetro de salida.
1. Cree un extremo de carpeta vigilada.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para agregar mediante programación un extremo de carpeta vigilada, debe crear un `EndpointRegistryClient` objeto.

**Establecer atributos de extremo de carpeta vigilada**

Para crear un extremo de carpeta vigilada para un servicio, especifique los siguientes valores:

* **Identificador de conector**: Especifica el tipo de extremo que se crea. Para crear un extremo de carpeta vigilada, especifique `WatchedFolder`.
* **Descripción**: Especifica la descripción del extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Identificador de servicio**: Especifica el servicio al que pertenece el extremo. Por ejemplo, para agregar un extremo de carpeta vigilada al proceso que se introduce en esta sección (un proceso se convierte en un servicio cuando se activa mediante Workbench), especifique `EncryptDocument`.
* **Nombre de la operación**: Especifica el nombre de la operación que se invoca mediante el extremo. Normalmente, al crear un extremo de carpeta vigilada para un servicio originado en un proceso creado en Workbench, el nombre de la operación es `invoke`.

**Especificar valores de configuración**

Debe especificar valores de configuración para un extremo de carpeta vigilada al agregar mediante programación un extremo de carpeta vigilada a un servicio. Un administrador especifica estos valores de configuración si se agrega un extremo de carpeta vigilada mediante la consola de administración.

La siguiente lista especifica los valores de configuración que se establecen al agregar mediante programación un extremo de carpeta vigilada a un servicio:

* **url**: Especifica la ubicación de la carpeta vigilada. En un entorno agrupado, este valor debe apuntar a una carpeta de red compartida a la que se pueda acceder desde todos los equipos del clúster.
* **asincrónico**: Identifica el tipo de invocación como asíncrono o sincrónico. Los procesos transitorios y sincrónicos solo se pueden invocar sincrónicamente. El valor predeterminado es True. Se recomienda asíncrono.
* **cronExpression**: Utilizado por quartz para programar el sondeo del directorio de entrada.
* **purgeDuration**: Es un atributo obligatorio. Los archivos y carpetas de la carpeta de resultados se depuran cuando son anteriores a este valor. Este valor se mide en días. Este atributo es útil para garantizar que la carpeta de resultados no esté llena. El valor de -1 días indica que nunca se eliminará la carpeta de resultados. El valor predeterminado es -1.
* **repeatInterval**: Intervalo, en segundos, para analizar la carpeta vigilada para obtener información. A menos que la restricción esté habilitada, este valor debe ser mayor que el tiempo para procesar un trabajo promedio; de lo contrario, el sistema podría sobrecargarse. El valor predeterminado es 5.
* **RepeatCount**: Número de veces que una carpeta vigilada explora la carpeta o el directorio. Un valor de -1 indica escaneo indefinido. El valor predeterminado es -1.
* **throttleOn**: Limita el número de trabajos de carpeta vigilada que se pueden procesar en un momento determinado. El número máximo de trabajos viene determinado por el valor batchSize.
* **userName**: El nombre de usuario que se utiliza al invocar un servicio de destino desde la carpeta vigilada. Este valor es obligatorio. El valor predeterminado es SuperAdmin.
* **domainName**: El dominio del usuario. Este valor es obligatorio. El valor predeterminado es DefaultDom.
* **batchSize**: Número de archivos o carpetas que se van a recoger por análisis. Utilice este valor para evitar una sobrecarga en el sistema; el análisis de demasiados archivos al mismo tiempo puede provocar un bloqueo. El valor predeterminado es 2.
* **waitTime**: Tiempo, en milisegundos, que se debe esperar antes de analizar una carpeta o archivo después de la creación. Por ejemplo, si el tiempo de espera es de 36 000 000 milisegundos (una hora) y el archivo se creó hace un minuto, este archivo se selecciona después de que hayan transcurrido 59 minutos o más. Este atributo es útil para garantizar que un archivo o carpeta se copie completamente en la carpeta de entrada. Por ejemplo, si tiene un archivo grande para procesar y tarda diez minutos en descargarse, establezca el tiempo de espera en 10&amp;ast;60 &amp;ast;1000 milisegundos. Esta configuración evita que la carpeta vigilada analice el archivo si no ha estado esperando durante diez minutos. El valor predeterminado es 0.
* **excludeFilePattern**: Patrón que utiliza una carpeta vigilada para determinar qué archivos y carpetas analizar y recoger. Los archivos o carpetas que tengan este patrón no se analizarán para su procesamiento. Esta configuración es útil cuando la entrada es una carpeta que contiene varios archivos. El contenido de la carpeta se puede copiar en una carpeta que tenga un nombre que la carpeta vigilada vaya a recoger. Este paso evita que la carpeta vigilada recoja una carpeta para procesarla antes de que la carpeta se copie completamente en la carpeta de entrada. Por ejemplo, si el valor excludeFilePattern es `data*`, todos los archivos y carpetas que coinciden con `data*` no se recogen. Esto incluye archivos y carpetas con nombre `data1`, `data2`, etc. Además, el patrón se puede complementar con patrones comodín para especificar patrones de archivo. La carpeta vigilada modifica la expresión regular para admitir patrones comodín como `*.*` y `*.pdf`. Estas expresiones regulares no admiten estos patrones comodín.
* **includeFilePattern**: Patrón que utiliza la carpeta vigilada para determinar qué carpetas y archivos analizar y recoger. Por ejemplo, si este valor es `*`, todos los archivos y carpetas que coinciden con `input*` son recogidos. Esto incluye archivos y carpetas con nombre `input1`, `input2`, etc. El valor predeterminado es `*`. Este valor indica todos los archivos y carpetas. Además, el patrón se puede complementar con patrones comodín para especificar patrones de archivo. La carpeta vigilada modifica la expresión regular para admitir patrones comodín como `*.*` y `*.pdf`. Estas expresiones regulares no admiten estos patrones comodín. Este valor es obligatorio.
* **resultFolderName**: La carpeta en la que se almacenan los resultados guardados. Esta ubicación puede ser una ruta de directorio absoluta o relativa. Si los resultados no aparecen en esta carpeta, compruebe la carpeta de errores. Los archivos de solo lectura no se procesan y se guardan en la carpeta de errores. El valor predeterminado es `result/%Y/%M/%D/`. Esta es la carpeta de resultados dentro de la carpeta vigilada.
* **preserveFolderName**: Ubicación en la que se almacenan los archivos después de realizar el análisis y la recogida con éxito. Esta ubicación puede ser absoluta, relativa o nula. El valor predeterminado es `preserve/%Y/%M/%D/`.
* **failureFolderName**: Carpeta donde se guardan los archivos de error. Esta ubicación siempre es relativa a la carpeta vigilada. Los archivos de solo lectura no se procesan y se guardan en la carpeta de errores. El valor predeterminado es `failure/%Y/%M/%D/`.
* **preserveOnFailure**: Preservar archivos de entrada en caso de que no se ejecute la operación en un servicio. El valor predeterminado es True.
* **overwriteDuplicateFilename**: Cuando se establece en true, los archivos de la carpeta de resultados y de la carpeta de preservación se sobrescriben. Cuando se establece en false, los archivos y carpetas que tienen un sufijo de índice numérico se utilizan para el nombre. El valor predeterminado es False.

**Definir valores de parámetros de entrada**

Al crear un extremo de carpeta vigilada, debe definir los valores de parámetro de entrada. Es decir, debe describir los valores de entrada que se pasan a la operación que invoca la carpeta vigilada. Por ejemplo, considere el proceso introducido en este tema. Tiene un valor de entrada denominado `InDoc` y su tipo de datos es `com.adobe.idp.Document`. Al crear un extremo de carpeta vigilada para este proceso (después de activar un proceso, se convierte en un servicio), debe definir el valor del parámetro de entrada.

Para definir los valores de parámetro de entrada necesarios para un extremo de carpeta vigilada, especifique los siguientes valores:

**Nombre del parámetro de entrada**: Nombre del parámetro de entrada. El nombre de un valor de entrada se especifica en Workbench para un proceso. Si el valor de entrada pertenece a una operación de servicio (un servicio que no es un proceso creado en Workbench), el nombre de entrada se especifica en el archivo component.xml. Por ejemplo, el nombre del parámetro de entrada para el proceso introducido en esta sección es `InDoc`.

**Tipo de asignación**: Se utiliza para configurar los valores de entrada necesarios para invocar la operación de servicio. Existen dos tipos de asignación:

* `Literal`: El extremo Carpeta vigilada utiliza el valor introducido en el campo tal como se muestra. Se admiten todos los tipos de Java básicos. Por ejemplo, si una API utiliza entradas como String, long, int y Boolean, la cadena se convierte al tipo adecuado y se invoca el servicio.
* `Variable`: El valor introducido es un patrón de archivo que la carpeta vigilada utiliza para seleccionar la entrada. Por ejemplo, si selecciona Variable para el tipo de asignación y el documento de entrada debe ser un archivo PDF, puede especificar `*.pdf`como valor de asignación.

**Valor de asignación**: Especifica el valor del tipo de asignación. Por ejemplo, si selecciona un `Variable` tipo de asignación, puede especificar `*.pdf` como patrón de archivo.

**Tipo de datos**: Especifica el tipo de datos de los valores de entrada. Por ejemplo, el tipo de datos del valor de entrada del proceso introducido en esta sección es `com.adobe.idp.Document`.

**Definición de un valor de parámetro de salida**

Al crear un extremo de carpeta vigilada, debe definir un valor de parámetro de salida. Es decir, debe describir el valor de salida que devuelve el servicio que invoca el extremo de la carpeta vigilada. Por ejemplo, considere el proceso introducido en este tema. Tiene un valor de salida denominado `SecuredDoc` y su tipo de datos es `com.adobe.idp.Document`. Al crear un extremo de carpeta vigilada para este proceso (después de activar un proceso, se convierte en un servicio), debe definir el valor del parámetro de salida.

Para definir un valor de parámetro de salida requerido para un extremo de carpeta vigilada, especifique los siguientes valores:

**Nombre del parámetro de salida**: Nombre del parámetro de salida. El nombre de un valor de salida de proceso se especifica en Workbench. Si el valor de salida pertenece a una operación de servicio (un servicio que no es un proceso creado en Workbench), el nombre de salida se especifica en el archivo component.xml. Por ejemplo, el nombre del parámetro de salida para el proceso introducido en esta sección es `SecuredDoc`.

**Tipo de asignación**: Se utiliza para configurar la salida del servicio y la operación. Las opciones disponibles son las siguientes:

* Si el servicio devuelve un único objeto (un solo documento), el patrón es `%F.pdf` y el destino de origen es sourcefilename.pdf. Por ejemplo, el proceso introducido en esta sección devuelve un solo documento. Como resultado, el tipo de asignación se puede definir como `%F.pdf` ( `%F` significa utilizar el nombre de archivo dado). El patrón `%E` especifica la extensión del documento de entrada.
* Si el servicio devuelve una lista, el patrón es `Result\%F\`y el destino de origen es Result\sourcefilename\source1 (output 1) y Result\sourcefilename\source2 (output 2).
* Si el servicio devuelve un mapa, el patrón es `Result\%F\`y el destino de origen es Result\sourcefilename\file1 y Result\sourcefilename\file2. Si el mapa tiene más de un objeto, el patrón es `Result\%F.pdf` y el destino de origen es Result\sourcefilename1.pdf (output 1), Result\sourcefilenam2.pdf (output 2), etc.

**Tipo de datos**: Especifica el tipo de datos del valor devuelto. Por ejemplo, el tipo de datos del valor devuelto del proceso introducido en esta sección es `com.adobe.idp.Document`.

**Crear un extremo de carpeta vigilada**

Después de establecer los atributos del extremo, los valores de configuración y definir los valores de los parámetros de entrada y salida, debe crear el extremo de la carpeta vigilada.

**Habilitar el punto final**

Después de crear un extremo de carpeta vigilada, debe habilitarlo. Cuando el extremo está habilitado, se puede utilizar para invocar el servicio. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Añadir un extremo de carpeta vigilada mediante la API de Java](programmatically-endpoints.md#add-a-watched-folder-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo de carpeta vigilada mediante la API de Java {#add-a-watched-folder-endpoint-using-the-java-api}

Agregue un extremo de carpeta vigilada mediante la API Java de AEM Forms:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Establezca los atributos de extremo de la carpeta vigilada.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `WatchedFolder`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la operación que se invoca invocando la variable `CreateEndpointInfo` del objeto `setOperationName` y pasando un valor de cadena que especifica el nombre de la operación. Normalmente, al crear un extremo de carpeta vigilada para un servicio originado en un proceso creado en Workbench, se invoca el nombre de la operación.

1. Especifique los valores de configuración.

   Para que cada valor de configuración se establezca para el extremo de la carpeta vigilada, debe invocar la variable `CreateEndpointInfo` del objeto `setConfigParameterAsText` método. Por ejemplo, para configurar la variable `url` valor de configuración, invoque la variable `CreateEndpointInfo` del objeto `setConfigParameterAsText` y pase los siguientes valores de cadena:

   * Un valor de cadena que especifica el nombre del valor de configuración. Al configurar la variable `url` valor de configuración, especifique `url`.
   * Un valor de cadena que especifica el valor del valor de configuración. Al configurar la variable `url` , especifique la ubicación de la carpeta vigilada.

   >[!NOTE]
   >
   >Para ver todos los valores de configuración establecidos para el servicio EncryptDocument, consulte el ejemplo de código Java ubicado en [Inicio rápido: Añadir un extremo de carpeta vigilada mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api).

1. Defina los valores de parámetro de entrada.

   Defina un valor de parámetro de entrada invocando la variable `CreateEndpointInfo` del objeto `setInputParameterMapping` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del parámetro de entrada. Por ejemplo, el nombre del parámetro de entrada para el servicio EncryptDocument es `InDoc`.
   * Un valor de cadena que especifica el tipo de datos del parámetro de entrada. Por ejemplo, el tipo de datos de la variable `InDoc` el parámetro de entrada es `com.adobe.idp.Document`.
   * Un valor de cadena que especifica el tipo de asignación. Por ejemplo, puede especificar `variable`.
   * Un valor de cadena que especifica el valor del tipo de asignación. Por ejemplo, puede especificar &amp;ast;.pdf como patrón de archivo.

   >[!NOTE]
   >
   >Invocar el `setInputParameterMapping` para cada valor de parámetro de entrada que se va a definir. Dado que el proceso EncryptDocument solo tiene un parámetro de entrada, debe invocar este método una vez.

1. Defina un valor de parámetro de salida.

   Defina un valor de parámetro de salida invocando la variable `CreateEndpointInfo` del objeto `setOutputParameterMapping` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del parámetro de salida. Por ejemplo, el nombre del parámetro de salida para el servicio EncryptDocument es `SecuredDoc`.
   * Un valor de cadena que especifica el tipo de datos del parámetro de salida. Por ejemplo, el tipo de datos de la variable `SecuredDoc` el parámetro de salida es `com.adobe.idp.Document`.
   * Un valor de cadena que especifica el tipo de asignación. Por ejemplo, puede especificar `%F.pdf`.

1. Cree un extremo de carpeta vigilada.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el extremo de la carpeta vigilada.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` del objeto `enable` y pasando el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Añadir un extremo de carpeta vigilada mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Archivos constantes de valores de configuración de carpetas vigiladas {#watched-folder-configuration-values-constant-file}

La variable [Inicio rápido: Añadir un extremo de carpeta vigilada mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api) utiliza un archivo constante que debe formar parte del proyecto Java para compilar el inicio rápido. Este archivo constante representa los valores de configuración que deben establecerse al agregar un extremo de carpeta vigilada. El siguiente código Java representa el archivo constante.

```as3
 /** 
     * This class contains constants that can be used when setting Watched Folder  
     * configuration values 
     */ 
  
 public final class WatchedFolderEndpointConfigConstants { 
          
         public static final String PROPERTY_FILEPROVIDER_URL = "url"; 
         public static final String PROPERTY_PROPERTY_ASYNCHRONOUS = "asynchronous"; 
         public static final String PROPERTY_CRON_EXPRESSION = "cronExpression"; 
         public static final String PROPERTY_PURGE_DURATION = "purgeDuration"; 
         public static final String PROPERTY_REPEAT_INTERVAL = "repeatInterval"; 
         public static final String PROPERTY_REPEAT_COUNT = "repeatCount"; 
         public static final String PROPERTY_THROTTLE = "throttleOn"; 
         public static final String PROPERTY_USERNAMER = "userName"; 
         public static final String PROPERTY_DOMAINNAME = "domainName"; 
         public static final String PROPERTY_FILEPROVIDER_BATCH_SIZE = "batchSize"; 
         public static final String PROPERTY_FILEPROVIDER_WAIT_TIME = "waitTime"; 
         public static final String PROPERTY_EXCLUDE_FILE_PATTERN = "excludeFilePattern"; 
         public static final String PROPERTY_INCLUDE_FILE_PATTERN = "excludeFilePattern"; 
         public static final String PROPERTY_FILEPROVIDER_RESULT_FOLDER_NAME =  "resultFolderName"; 
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_FOLDER_NAME = "preserveFolderName"; 
         public static final String PROPERTY_FILEPROVIDER_FAILURE_FOLDER_NAME = "failureFolderName"; 
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_ON_FAILURE = "preserveOnFailure"; 
         public static final String PROPERTY_FILEPROVIDER_OVERWRITE_DUPLICATE_FILENAME = "overwriteDuplicateFilename";      
        }
```

## Añadir puntos de conexión de correo electrónico {#adding-email-endpoints}

Puede añadir mediante programación un extremo de correo electrónico a un servicio mediante la API Java de AEM Forms. Al añadir un extremo de correo electrónico, se permite a los usuarios enviar un mensaje de correo electrónico con uno o más archivos adjuntos a una cuenta de correo electrónico especificada. A continuación, se invoca la operación configurar servicio y manipula los archivos. Una vez que el servicio realiza la operación especificada, envía un mensaje de correo electrónico al remitente con los archivos modificados como archivos adjuntos.

Para añadir mediante programación un extremo de correo electrónico a un servicio, tenga en cuenta el siguiente proceso breve denominado *MyApplication\EncryptDocument*. Para obtener información sobre los procesos de corta duración, consulte [Explicación de los procesos de AEM Forms](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).

![ae_ae_encryptdocumentprocess](assets/ae_ae_encryptdocumentprocess.png)

Este proceso acepta un documento de PDF no protegido como valor de entrada y, a continuación, pasa el documento de PDF no protegido al `EncryptPDFUsingPassword` operación. Este proceso cifra el documento del PDF con una contraseña y devuelve el documento del PDF cifrado con contraseña como valor de salida. El nombre del valor de entrada (el documento PDF no protegido) es `InDoc` y el tipo de datos es `com.adobe.idp.Document`. El nombre del valor de salida (el documento de PDF cifrado con contraseña) es `SecuredDoc` y el tipo de datos es `com.adobe.idp.Document`.

>[!NOTE]
>
>No puede agregar un extremo de correo electrónico mediante servicios web.

### Resumen de los pasos {#summary_of_steps-3}

Para añadir un extremo de correo electrónico a un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Establezca los atributos de extremo del correo electrónico.
1. Especifique los valores de configuración.
1. Defina los valores de parámetro de entrada.
1. Defina un valor de parámetro de salida.
1. Cree el extremo de correo electrónico.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para poder agregar mediante programación un extremo de correo electrónico, debe crear un `EndpointRegistryClient` objeto.

**Establecer atributos de extremo de correo electrónico**

Para crear un extremo de correo electrónico para un servicio, especifique los siguientes valores:

* **Valor del identificador del conector**: Especifica el tipo de extremo que se crea. Para crear un extremo de correo electrónico, especifique `Email`.
* **Descripción**: Especifica una descripción para el extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Valor del identificador de servicio**: Especifica el servicio al que pertenece el extremo. Por ejemplo, para añadir un extremo de correo electrónico al proceso que se introduce en esta sección (un proceso se convierte en un servicio cuando se activa mediante Workbench), especifique `EncryptDocument`.
* **Nombre de la operación**: Especifica el nombre de la operación que se invoca mediante el extremo. Normalmente, al crear un extremo de correo electrónico para un servicio originado en un proceso creado en Workbench, el nombre de la operación es `invoke`.

**Especificar valores de configuración**

Debe especificar valores de configuración para un extremo de correo electrónico al agregar mediante programación un extremo de correo electrónico a un servicio. Un administrador especifica estos valores de configuración si se agrega un extremo de correo electrónico mediante la consola de administración.

>[!NOTE]
>
>La cuenta de correo electrónico que se supervisa es una cuenta especial que se utiliza solo para el extremo de correo electrónico . Esta cuenta no es una cuenta de correo electrónico de un usuario normal. La cuenta de correo electrónico de un usuario normal no debe configurarse como la cuenta que utiliza el proveedor de correo electrónico porque este elimina los mensajes de correo electrónico de la bandeja de entrada una vez que han finalizado con los mensajes.

Los siguientes valores de configuración se establecen al agregar mediante programación un extremo de correo electrónico a un servicio:

* **cronExpression**: Expresión cron si el correo electrónico debe programarse usando una expresión cron.
* **RepeatCount**: Número de veces que el extremo del correo electrónico analiza la carpeta o el directorio. Un valor de -1 indica escaneo indefinido. El valor predeterminado es -1.
* **repeatInterval**: La velocidad de digitalización en segundos que utiliza el receptor para comprobar el correo entrante. El valor predeterminado es 10.
* **startDelay**: Tiempo de espera para analizar después de que se inicie el planificador. La hora predeterminada es 0.
* **batchSize**: Número de mensajes de correo electrónico que procesa el receptor por escaneo para obtener un rendimiento óptimo. El valor -1 indica todos los correos electrónicos. El valor predeterminado es 2.
* **userName**: El nombre de usuario que se utiliza al invocar un servicio de Target desde el correo electrónico. El valor predeterminado es `SuperAdmin`.
* **domainName**: Un valor de configuración obligatorio. El valor predeterminado es `DefaultDom`.
* **domainPattern**: Especifica los patrones de dominio del correo electrónico entrante que acepta el proveedor. Por ejemplo, si `adobe.com` se utiliza, solo se procesa el correo electrónico de adobe.com y se ignora el correo electrónico de otros dominios.
* **filePattern**: Especifica los patrones de archivo adjunto entrantes que acepta el proveedor. Esto incluye archivos que tienen extensiones de nombre de archivo específicas (&amp;ast;.dat, &amp;ast;.xml), archivos que tienen nombres específicos (datos) y archivos que tienen expresiones compuestas en el nombre y la extensión (&amp;ast;).[dD][aA][Tt]). El valor predeterminado es `*`.
* **recipientSucfulJob**: Una dirección de correo electrónico a la que se envían mensajes para indicar los trabajos realizados correctamente. De forma predeterminada, siempre se envía un mensaje de trabajo correcto al remitente. Si escribe `sender`, los resultados de correo electrónico se envían al remitente. Se admiten hasta 100 destinatarios. Especifique destinatarios adicionales con direcciones de correo electrónico, cada uno separado por una coma. Para desactivar esta opción, deje este valor en blanco. En algunos casos, es posible que desee almacenar en déclencheur un proceso y no desee que se le notifique por correo electrónico el resultado. El valor predeterminado es `sender`.
* **recipientFailedJob**: Una dirección de correo electrónico a la que se envían mensajes para indicar los trabajos fallidos. De forma predeterminada, siempre se envía un mensaje de trabajo fallido al remitente. Si escribe `sender`, los resultados de correo electrónico se envían al remitente. Se admiten hasta 100 destinatarios. Especifique destinatarios adicionales con direcciones de correo electrónico, cada uno separado por una coma. Para desactivar esta opción, deje este valor en blanco. El valor predeterminado es `sender`.
* **inboxHost**: El nombre de host de la bandeja de entrada o la dirección IP que debe analizar el proveedor de correo electrónico.
* **inboxPort**: Puerto que utiliza el servidor de correo electrónico. El valor predeterminado para POP3 es 110 y el valor predeterminado para IMAP es 143. Si SSL está habilitado, el valor predeterminado para POP3 es 995 y el valor predeterminado para IMAP es 993.
* **inboxProtocol**: El protocolo de correo electrónico para el extremo de correo electrónico que se utiliza para analizar la bandeja de entrada. Las opciones son `IMAP` o `POP3`. El servidor de correo de host de la bandeja de entrada debe admitir estos protocolos.
* **inboxTimeOut**: Tiempo de espera en segundos para que el proveedor de correo electrónico espere a recibir respuestas de la bandeja de entrada. El valor predeterminado es 60.
* **inboxUser**: El nombre de usuario necesario para iniciar sesión en la cuenta de correo electrónico. Según el servidor de correo electrónico y la configuración, esto solo puede ser la parte del nombre de usuario del correo electrónico o puede ser la dirección de correo electrónico completa.
* **inboxPassword**: La contraseña del usuario de la bandeja de entrada.
* **inboxSSLEnabled**: Establezca este valor para forzar al proveedor de correo electrónico a utilizar SSL al enviar mensajes de notificación de resultados o errores. Asegúrese de que el host IMAP o POP3 sea compatible con SSL.
* **smtpHost**: El nombre de host del servidor de correo al que envía los resultados y mensajes de error el proveedor de correo electrónico.
* **smtpPort**: El valor predeterminado del puerto SMTP es 25.
* **smtpUser**: La cuenta de usuario del proveedor de correo electrónico que se utiliza cuando envía notificaciones por correo electrónico de resultados y errores.
* **smtpPassword**: La contraseña de la cuenta SMTP. Algunos servidores de correo no requieren una contraseña SMTP.
* **charSet**: El conjunto de caracteres utilizado por el proveedor de correo electrónico. El valor predeterminado es `UTF-8`.
* **smtpSSLEnabled**: Establezca este valor para forzar al proveedor de correo electrónico a utilizar SSL al enviar mensajes de notificación de resultados o errores. Asegúrese de que el host SMTP sea compatible con SSL.
* **failedJobFolder**: Especifica un directorio en el que almacenar los resultados cuando el servidor de correo SMTP no está operativo.
* **asincrónico**: Cuando se establece en sincrónico, se procesan todos los documentos de entrada y se devuelve una sola respuesta. Cuando se establece en asincrónico, se envía una respuesta para cada documento de entrada que se procesa. Por ejemplo, se crea un extremo de correo electrónico para el proceso introducido en este tema y se envía un mensaje de correo electrónico a la bandeja de entrada del extremo que contiene varios documentos de PDF no protegidos. Cuando todos los documentos del PDF se cifran con una contraseña y si el extremo está configurado como sincrónico, se envía un mensaje de correo electrónico de respuesta única con todos los documentos del PDF protegidos adjuntos. Si el extremo está configurado como asincrónico, se envía un mensaje de correo electrónico de respuesta independiente para cada documento de PDF protegido. Cada mensaje de correo electrónico contiene un solo documento de PDF como archivo adjunto. El valor predeterminado es asíncrono.

**Definir valores de parámetros de entrada**

Al crear un extremo de correo electrónico, debe definir los valores de parámetro de entrada. Es decir, debe describir los valores de entrada que se pasan a la operación que invoca el extremo de correo electrónico. Por ejemplo, considere el proceso introducido en este tema. Tiene un valor de entrada denominado `InDoc` y su tipo de datos es `com.adobe.idp.Document`. Al crear un extremo de correo electrónico para este proceso (después de activar un proceso, se convierte en un servicio), debe definir el valor del parámetro de entrada.

Para definir los valores de parámetro de entrada necesarios para un extremo de correo electrónico, especifique los siguientes valores:

**Nombre del parámetro de entrada**: Nombre del parámetro de entrada. El nombre de un valor de entrada se especifica en Workbench para un proceso. Si el valor de entrada pertenece a una operación de servicio (un servicio de Forms que no es un proceso creado en Workbench), el nombre de entrada se especifica en el archivo component.xml. Por ejemplo, el nombre del parámetro de entrada para el proceso introducido en esta sección es `InDoc`.

**Tipo de asignación**: Se utiliza para configurar los valores de entrada necesarios para invocar la operación de servicio. Dos tipos de asignación son los siguientes:

* `Literal`: El extremo Email utiliza el valor introducido en el campo como se muestra. Se admiten todos los tipos de Java básicos. Por ejemplo, si una API utiliza entradas como String, long, int y Boolean, la cadena se convierte al tipo adecuado y se invoca el servicio.
* `Variable`: El valor introducido es un patrón de archivo que el extremo Email utiliza para elegir la entrada. Por ejemplo, si selecciona Variable para el tipo de asignación y el documento de entrada debe ser un archivo PDF, puede especificar `*.pdf` como valor de asignación.

**Valor de asignación**: Especifica el valor del tipo de asignación. Por ejemplo, si selecciona un tipo de asignación Variable , puede especificar `*.pdf` como patrón de archivo.

**Tipo de datos**: Especifica el tipo de datos de los valores de entrada. Por ejemplo, el tipo de datos del valor de entrada del proceso introducido en esta sección es com.adobe.idp.Document.

**Definición de un valor de parámetro de salida**

Al crear un extremo de correo electrónico, debe definir un valor de parámetro de salida. Es decir, debe describir el valor de salida que devuelve el servicio que invoca el extremo de correo electrónico. Por ejemplo, considere el proceso introducido en este tema. Tiene un valor de salida denominado `SecuredDoc` y su tipo de datos es `com.adobe.idp.Document`. Al crear un extremo de correo electrónico para este proceso (después de activar un proceso, se convierte en un servicio), debe definir el valor del parámetro de salida.

Para definir un valor de parámetro de salida requerido para un extremo de correo electrónico, especifique los siguientes valores:

**Nombre del parámetro de salida**: Nombre del parámetro de salida. El nombre de un valor de salida de proceso se especifica en Workbench. Si el valor de salida pertenece a una operación de servicio (un servicio que no es un proceso creado en Workbench), el nombre de salida se especifica en el archivo component.xml. Por ejemplo, el nombre del parámetro de salida para el proceso introducido en esta sección es `SecuredDoc`.

**Tipo de asignación**: Se utiliza para configurar la salida del servicio y la operación. Las opciones disponibles son las siguientes:

* Si el servicio devuelve un único objeto (un solo documento), el patrón es `%F.pdf` y el destino de origen es sourcefilename.pdf. Por ejemplo, el proceso introducido en esta sección devuelve un solo documento. Como resultado, el tipo de asignación se puede definir como `%F.pdf` ( `%F` significa utilizar el nombre de archivo dado). El patrón `%E` especifica la extensión del documento de entrada.
* Si el servicio devuelve una lista, el patrón es `Result\%F\`y el destino de origen es Result\sourcefilename\source1 (output 1) y Result\sourcefilename\source2 (output 2).
* Si el servicio devuelve un mapa, el patrón es `Result\%F\`y el destino de origen es Result\sourcefilename\file1 y Result\sourcefilename\file2. Si el mapa tiene más de un objeto, el patrón es `Result\%F.pdf` y el destino de origen es Result\sourcefilename1.pdf (output 1), Result\sourcefilenam2.pdf (output 2), etc.

**Tipo de datos**: Especifica el tipo de datos del valor devuelto. Por ejemplo, el tipo de datos del valor devuelto del proceso introducido en esta sección es `com.adobe.idp.Document`.

**Crear el extremo de correo electrónico**

Después de establecer los atributos de extremo de correo electrónico y los valores de configuración, y definir los valores de parámetro de entrada y salida, debe crear el extremo de correo electrónico.

**Habilitar el punto final**

Después de crear un extremo de correo electrónico, debe habilitarlo. Cuando el extremo está habilitado, se puede utilizar para invocar el servicio. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Añadir un extremo de correo electrónico mediante la API de Java](programmatically-endpoints.md#add-an-email-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo de correo electrónico mediante la API de Java {#add-an-email-endpoint-using-the-java-api}

Añada un extremo de correo electrónico mediante la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Establezca los atributos de extremo del correo electrónico.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `Email`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la operación que se invoca invocando la variable `CreateEndpointInfo` del objeto `setOperationName` y pasando un valor de cadena que especifica el nombre de la operación. Normalmente, al crear un extremo de correo electrónico para un servicio originado en un proceso creado en Workbench, se invoca el nombre de la operación.

1. Especifique los valores de configuración.

   Para cada valor de configuración que se establezca para el extremo de correo electrónico, debe invocar la variable `CreateEndpointInfo` del objeto `setConfigParameterAsText` método. Por ejemplo, para configurar la variable `smtpHost` valor de configuración, invoque la variable `CreateEndpointInfo` del objeto `setConfigParameterAsText` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del valor de configuración. Al configurar la variable `smtpHost` valor de configuración, especifique `smtpHost`.
   * Un valor de cadena que especifica el valor del valor de configuración. Al configurar la variable `smtpHost` , especifique un valor de cadena que especifique el nombre del servidor SMTP.

   >[!NOTE]
   >
   >Para ver todos los valores de configuración establecidos para el servicio EncryptDocument introducidos en esta sección, consulte el ejemplo de código Java ubicado en [Inicio rápido: Añadir un extremo de correo electrónico mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api).

1. Defina los valores de parámetro de entrada.

   Defina un valor de parámetro de entrada invocando la variable `CreateEndpointInfo` del objeto `setInputParameterMapping` y pase los siguientes valores:

   * Un valor de cadena que especifica el nombre del parámetro de entrada. Por ejemplo, el nombre del parámetro de entrada para el servicio EncryptDocument es `InDoc`.
   * Un valor de cadena que especifica el tipo de datos del parámetro de entrada. Por ejemplo, el tipo de datos de la variable `InDoc` el parámetro de entrada es `com.adobe.idp.Document`.
   * Un valor de cadena que especifica el tipo de asignación. Por ejemplo, puede especificar `variable`.
   * Un valor de cadena que especifica el valor del tipo de asignación. Por ejemplo, puede especificar &amp;ast;.pdf como patrón de archivo.

   >[!NOTE]
   >
   >Invocar el `setInputParameterMapping` para cada valor de parámetro de entrada que se va a definir. Dado que el proceso EncryptDocument solo tiene un parámetro de entrada, debe invocar este método una vez.

1. Defina un valor de parámetro de salida.

   Defina un valor de parámetro de salida invocando la variable `CreateEndpointInfo` del objeto `setOutputParameterMapping` y pasando los siguientes valores:

   * Un valor de cadena que especifica el nombre del parámetro de salida. Por ejemplo, el nombre del parámetro de salida para el servicio EncryptDocument es `SecuredDoc`.
   * Un valor de cadena que especifica el tipo de datos del parámetro de salida. Por ejemplo, el tipo de datos de la variable `SecuredDoc` el parámetro de salida es `com.adobe.idp.Document`.
   * Un valor de cadena que especifica el tipo de asignación. Por ejemplo, puede especificar `%F.pdf`.

1. Cree el extremo de correo electrónico.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el extremo de correo electrónico.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` del objeto `enable` y pasando el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Añadir un extremo de carpeta vigilada mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Archivo constante de valores de configuración de correo electrónico {#email-configuration-values-constant-file}

La variable [Inicio rápido: Añadir un extremo de correo electrónico mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api) utiliza un archivo constante que debe formar parte del proyecto Java para compilar el inicio rápido. Este archivo constante representa los valores de configuración que deben establecerse al agregar un extremo de correo electrónico. El siguiente código Java representa el archivo constante.

```as3
 /** 
     * This class contains constants that can be used when setting email endpoint  
     * configuration values 
     */ 
 public class EmailEndpointConfigConstants { 
      
     public static final String PROPERTY_EMAILPROVIDER_CRON_EXPRESSION = "cronExpression"; 
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_COUNT = "repeatCount"; 
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_INTERVAL = "repeatInterval"; 
     public static final String PROPERTY_EMAILPROVIDER_START_DELAY = "startDelay"; 
     public static final String PROPERTY_EMAILPROVIDER_BATCH_SIZE = "batchSize"; 
     public static final String PROPERTY_EMAILPROVIDER_USERNAME = "userName"; 
     public static final String PROPERTY_EMAILPROVIDER_DOMAINNAME = "domainName"; 
     public static final String PROPERTY_EMAILPROVIDER_DOMAINPATTERN = "domainPattern"; 
     public static final String PROPERTY_EMAILPROVIDER_FILEPATTERN = "filePattern"; 
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_SUCCESSFUL_JOB = "recipientSuccessfulJob"; 
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_FAILED_JOB = "recipientFailedJob"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_HOST = "inboxHost"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PORT = "inboxPort"; 
     public static final String PROPERTY_EMAILPROVIDER_PROTOCOL = "inboxProtocol"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_TIMEOUT = "inboxTimeOut"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_USER = "inboxUser"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PASSWORD = "inboxPassword"; 
     public static final String PROPERTY_EMAILPROVIDER_INBOX_SSL = "inboxSSLEnabled"; 
     public static final String PROPERTY_EMAILPROVIDER_SMTP_HOST = "smtpHost"; 
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PORT = "smtpPort"; 
     public static final String PROPERTY_EMAILPROVIDER_SMTP_USER = "smtpUser"; 
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PASSWORD = "smtpPassword"; 
     public static final String PROPERTY_EMAILPROVIDER_CHARSET = "charSet"; 
     public static final String PROPERTY_EMAILPROVIDER_SMTP_SSL = "smtpSSLEnabled"; 
     public static final String PROPERTY_EMAILPROVIDER_FAILED_FOLDER = "failedJobFolder"; 
     public static final String PROPERTY_EMAILPROVIDER_ASYNCHRONOUS = "asynchronous"; 
 }
```

## Adición de puntos de conexión remotos {#adding-remoting-endpoints}

>[!NOTE]
>
>API de LiveCycle Remoting obsoletas para AEM formularios en JEE.

Puede agregar mediante programación un extremo Remoting a un servicio mediante la API Java de AEM Forms. Al agregar un extremo Remoting, está permitiendo que una aplicación de Flex invoque el servicio mediante remoting. (Consulte [Invocación de AEM Forms mediante AEM Forms Remoting (obsoleto para formularios AEM)](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Para añadir mediante programación un extremo Remoting a un servicio, tenga en cuenta el siguiente proceso de corta duración denominado *EncryptDocument*.

![ar_ar_encryptdocumentprocess](assets/ar_ar_encryptdocumentprocess.png)

Este proceso acepta un documento de PDF no protegido como valor de entrada y, a continuación, pasa el documento de PDF no protegido al `EncryptPDFUsingPassword` operación. El documento del PDF está cifrado con una contraseña y el documento del PDF cifrado con contraseña es el valor de salida de este proceso. El nombre del valor de entrada (el documento PDF no protegido) es `InDoc` y el tipo de datos es `com.adobe.idp.Document`. El nombre del valor de salida (el documento de PDF cifrado con contraseña) es `SecuredDoc` y el tipo de datos es `com.adobe.idp.Document`.

Para demostrar cómo agregar un extremo Remoting a un servicio, esta sección agrega un extremo Remoting a un servicio llamado EncryptDocument.

>[!NOTE]
>
>No se puede agregar un extremo Remoting mediante servicios web.

### Resumen de los pasos {#summary_of_steps-4}

Para eliminar un punto final de un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Establezca los atributos de extremo de Remoting.
1. Cree un extremo Remoting.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para agregar mediante programación un extremo Remoting, debe crear un `EndpointRegistryClient` objeto.

**Establecer atributos de extremo de Remoting**

Para crear un extremo Remoting para un servicio, especifique los siguientes valores:

* **Valor del identificador del conector**: Especifica el tipo de extremo que se crea. Para crear un extremo Remoting, especifique `Remoting`.
* **Descripción**: Especifica la descripción del extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Valor del identificador de servicio**: Especifica el servicio al que pertenece el extremo. Por ejemplo, para agregar un extremo Remoting al proceso que se introduce en esta sección (un proceso se convierte en un servicio cuando se activa dentro de Workbench), especifique `EncryptDocument`.
* **Nombre de la operación**: Especifica el nombre de la operación que se invoca mediante el extremo. Al crear un extremo Remoting, especifique un carácter comodín (&amp;ast;).

**Crear un extremo remoto**

Después de establecer los atributos de extremo Remoting, puede crear un extremo Remoting para un servicio.

**Habilitar el punto final**

Después de crear un nuevo extremo, debe habilitarlo. Cuando un extremo Remoting está habilitado, permite que un cliente de Flex invoque el servicio.

**Consulte también**

[Añadir un extremo de Remoting mediante la API de Java](programmatically-endpoints.md#add-a-remoting-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo de Remoting mediante la API de Java {#add-a-remoting-endpoint-using-the-java-api}

Añada un punto final de Remoting utilizando la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Establezca los atributos de extremo de Remoting.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `Remoting`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la operación que invoca el `CreateEndpointInfo` del objeto `setOperationName` y pasando un valor de cadena que especifica el nombre de la operación. Para un extremo Remoting, especifique un carácter comodín (&amp;ast;).

1. Cree un extremo Remoting.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el nuevo extremo Remoting.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` del objeto `enable` y pasando el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Adición de un extremo de Remoting mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Adición de puntos de conexión de TaskManager {#adding-taskmanager-endpoints}

Puede agregar mediante programación un extremo de TaskManager a un servicio mediante la API Java de AEM Forms. Al agregar un extremo de TaskManager a un servicio, se habilita un usuario de Workspace para que invoque el servicio. Es decir, un usuario que trabaja en Workspace puede invocar un proceso que tiene un extremo TaskManager correspondiente.

>[!NOTE]
>
>No se puede agregar un extremo de TaskManager mediante servicios web.

### Resumen de los pasos {#summary_of_steps-5}

Para agregar un extremo de TaskManager a un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Cree una categoría para el extremo.
1. Establezca los atributos de extremo de TaskManager.
1. Cree un extremo de TaskManager.
1. Habilite el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para poder agregar mediante programación un extremo de TaskManager, debe crear un `EndpointRegistryClient` objeto.

**Crear una categoría para el extremo**

Las categorías se utilizan para organizar servicios dentro de Workspace. Es decir, un usuario de Workspace puede invocar un servicio que tiene un extremo de TaskManager seleccionando una categoría dentro de Workspace. Al crear un extremo de TaskManager, puede hacer referencia a una categoría existente o crear mediante programación una nueva categoría.

>[!NOTE]
>
>Esta sección crea una nueva categoría como parte de la adición de un extremo de TaskManager a un servicio.

**Establecer atributos de extremo de TaskManager**

Para crear un extremo de TaskManager para un servicio, especifique los siguientes valores:

* **Identificador de conector**: Especifica el tipo de extremo que se crea. Para crear un extremo de TaskManager, especifique `TaskManagerConnector`.
* **Descripción**: Especifica la descripción del extremo.
* **Nombre**: Especifica el nombre del extremo.
* **Identificador de servicio**: Especifica el servicio al que pertenece el extremo.
* **Categoría**: Especifica un valor de identificador de categoría asociado al extremo TaskManager.
* **Nombre de la operación**: Normalmente, al crear un extremo de TaskManager para un servicio que se origina en un proceso creado en Workbench, el nombre de la operación es `invoke`.

**Crear un extremo de TaskManager**

Después de establecer los atributos de extremo de TaskManager, puede crear un extremo de TaskManager para un servicio.

**Habilitar el punto final**

Después de crear un nuevo extremo, debe habilitarlo. Cuando el punto final está habilitado, se puede utilizar para invocar el servicio desde Workspace. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Añadir un extremo de TaskManager mediante la API de Java](programmatically-endpoints.md#add-a-taskmanager-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Añadir un extremo de TaskManager mediante la API de Java {#add-a-taskmanager-endpoint-using-the-java-api}

Agregue un extremo de TaskManager usando la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Cree una categoría para el extremo.

   * Cree un `CreateEndpointCategoryInfo` usando su constructor y pasando los siguientes valores:

      * Un valor de cadena que especifica el valor de identificador de la categoría
      * Un valor de cadena que especifica la descripción de la categoría
   * Cree la categoría invocando la variable `EndpointRegistryClient` del objeto `createEndpointCategory` y pasando el `CreateEndpointCategoryInfo` objeto. Este método devuelve un `EndpointCategory` objeto que representa la nueva categoría.


1. Establezca los atributos de extremo de TaskManager.

   * Cree un `CreateEndpointInfo` usando su constructor.
   * Especifique el valor del identificador del conector invocando la variable `CreateEndpointInfo` del objeto `setConnectorId` método y pasar el valor de cadena `TaskManagerConnector`.
   * Especifique la descripción del extremo invocando el `CreateEndpointInfo` del objeto `setDescription` y pasando un valor de cadena que describe el punto final.
   * Especifique el nombre del extremo invocando la variable `CreateEndpointInfo` del objeto `setName` y pasando un valor de cadena que especifica el nombre.
   * Especifique el servicio al que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setServiceId` y pasando un valor de cadena que especifica el nombre del servicio.
   * Especifique la categoría a la que pertenece el extremo invocando la variable `CreateEndpointInfo` del objeto `setCategoryId` y pasando un valor de cadena que especifica el valor del identificador de categoría. Puede invocar la variable `EndpointCategory` del objeto `getId` para obtener el valor de identificador de esta categoría.
   * Especifique la operación que se invoca invocando la variable `CreateEndpointInfo` del objeto `setOperationName` y pasando un valor de cadena que especifica el nombre de la operación. Normalmente, al crear un `TaskManager` para un servicio que se originó en un proceso creado en Workbench, el nombre de la operación es `invoke`.

1. Cree un extremo de TaskManager.

   Cree el punto final invocando la variable `EndpointRegistryClient` del objeto `createEndpoint` y pasando el `CreateEndpointInfo` objeto. Este método devuelve un `Endpoint` que representa el nuevo extremo de TaskManager.

1. Habilite el punto final.

   Habilitar el extremo invocando el `EndpointRegistryClient` del objeto `enable` y pasando el `Endpoint` objeto devuelto por el `createEndpoint` método.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Añadir un extremo de TaskManager mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Modificación de puntos finales {#modifying-endpoints}

Puede modificar mediante programación un extremo existente mediante la API Java de AEM Forms. Si modifica un punto final, puede cambiar el comportamiento del punto final. Considere, por ejemplo, un punto final de Carpeta vigilada que especifica una carpeta que se utiliza como carpeta vigilada. Puede modificar mediante programación los valores de configuración que pertenecen al extremo de la carpeta vigilada, lo que hace que otra carpeta funcione como la carpeta vigilada. Para obtener información sobre los valores de configuración que pertenecen a un extremo de carpeta vigilada, consulte [Añadir puntos finales de carpeta vigilada](programmatically-endpoints.md#adding-watched-folder-endpoints).

Para demostrar cómo modificar un punto final, esta sección modifica un punto final de Carpeta vigilada al cambiar la carpeta que se comporta como la carpeta vigilada.

>[!NOTE]
>
>No se puede modificar un punto final mediante servicios web.

### Resumen de los pasos {#summary_of_steps-6}

Para modificar un punto final, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Recupere el punto final.
1. Especifique nuevos valores de configuración.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para modificar un extremo mediante programación, debe crear un `EndpointRegistryClient` objeto.

**Recupere el punto final para modificar**

Para poder modificar un punto final, debe recuperarlo. Para recuperar un punto final, debe conectarse como usuario que puede acceder a un punto final. Se recomienda conectarse como administrador. (Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Puede recuperar un punto final recuperando una lista de puntos finales. A continuación, puede iterar a través de la lista, buscando el punto final específico que desea eliminar. Por ejemplo, puede localizar un punto final determinando el servicio que corresponde al punto final y el tipo de punto final. Cuando localice el punto final, puede modificarlo.

**Especificar nuevos valores de configuración**

Al modificar un extremo, especifique nuevos valores de configuración. Por ejemplo, para modificar un extremo de carpeta vigilada, restablezca todos los valores de configuración de extremo de carpeta vigilada, no solo los que desea modificar. Para obtener información sobre los valores de configuración que pertenecen a un extremo de carpeta vigilada, consulte [Añadir puntos finales de carpeta vigilada](programmatically-endpoints.md#adding-watched-folder-endpoints).

>[!NOTE]
>
>Para obtener información sobre los valores de configuración que pertenecen a un extremo de correo electrónico, consulte [Añadir puntos de conexión de correo electrónico](programmatically-endpoints.md#adding-email-endpoints).

>[!NOTE]
>
>No puede modificar el servicio que invoca el extremo. Si intenta modificar el servicio, se produce una excepción. Para modificar el servicio asociado a un punto final determinado, elimine el punto final y cree uno nuevo. (Consulte [Eliminación de extremos](programmatically-endpoints.md#removing-endpoints).)

**Consulte también**

[Modificación de un extremo mediante la API de Java](programmatically-endpoints.md#modifying-an-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Modificación de un extremo mediante la API de Java {#modifying-an-endpoint-using-the-java-api}

Modifique un punto final utilizando la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Recupere el punto final para modificar.

   * Recupere una lista de todos los extremos a los que el usuario actual (especificado en las propiedades de conexión) puede acceder invocando la variable `EndpointRegistryClient` del objeto `getEndpoints` método y pasar una `PagingFilter` objeto que actúa como filtro. Puede pasar un `(PagingFilter)null` para devolver todos los extremos. Este método devuelve un `java.util.List` objeto donde cada elemento es un `Endpoint` objeto. Para obtener información sobre un `PagingFilter` objeto, consulte [Referencia de la API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Iterar a través de la variable `java.util.List` para determinar si tiene extremos. Si existen extremos, cada elemento es un `EndPoint` instancia.
   * Determine el servicio que corresponde a un punto final invocando la variable `EndPoint` del objeto `getServiceId` método. Este método devuelve un valor de cadena que especifica el nombre del servicio.
   * Determine el tipo de extremo invocando el `EndPoint` del objeto `getConnectorId` método. Este método devuelve un valor de cadena que especifica el tipo de extremo. Por ejemplo, si el extremo es un extremo de carpeta vigilada, este método devuelve `WatchedFolder`.

1. Especifique nuevos valores de configuración.

   * Cree un `ModifyEndpointInfo` invocando su constructor.
   * Para cada valor de configuración que se va a establecer, invoque la variable `ModifyEndpointInfo` del objeto `setConfigParameterAsText` método. Por ejemplo, para establecer el valor de configuración de la url, invoque la función `ModifyEndpointInfo` del objeto `setConfigParameterAsText` y pase los siguientes valores:

      * Un valor de cadena que especifica el nombre del valor de configuración. Por ejemplo, para configurar la variable `url` valor de configuración, especifique `url`.
      * Un valor de cadena que especifica el valor del valor de configuración. Para definir un valor para la variable `url` , especifique la ubicación de la carpeta vigilada.
   * Invocar el `EndpointRegistryClient` del objeto `modifyEndpoint` y pase el `ModifyEndpointInfo` objeto.


**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Modificación de un extremo mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eliminación de extremos {#removing-endpoints}

Puede eliminar mediante programación un extremo de un servicio mediante la API Java de AEM Forms. Después de quitar un extremo, no se puede invocar el servicio utilizando el método de invocación que habilitó el extremo. Por ejemplo, si elimina un extremo SOAP de un servicio, no puede invocar el servicio mediante el modo SOAP.

Para demostrar cómo quitar un punto final de un servicio, esta sección elimina un punto final de EJB de un servicio denominado *EncryptDocument*.

>[!NOTE]
>
>No se puede quitar un punto final mediante servicios web.

### Resumen de los pasos {#summary_of_steps-7}

Para eliminar un punto final de un servicio, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `EndpointRegistryClient` objeto.
1. Recupere el punto final.
1. Elimine el punto final.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Para obtener información sobre la ubicación de estos archivos JAR, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Crear un objeto de cliente de EndpointRegistry**

Para eliminar un extremo mediante programación, debe crear un `EndpointRegistryClient` objeto.

**Recupere el punto final que desea eliminar**

Para poder eliminar un punto final, debe recuperarlo. Para recuperar un punto final, debe conectarse como usuario que puede acceder a un punto final. Se recomienda conectarse como administrador. (Consulte [Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

Puede recuperar un punto final recuperando una lista de puntos finales. A continuación, puede iterar a través de la lista, buscando el punto final específico que desea eliminar. Por ejemplo, puede localizar un punto final determinando el servicio que corresponde al punto final y el tipo de punto final. Cuando localice el punto final, puede eliminarlo.

**Eliminar el punto final**

Después de crear un nuevo extremo, debe habilitarlo. Cuando el extremo está habilitado, se puede utilizar para invocar el servicio. Después de habilitar el punto final, puede verlo en la consola de administración.

**Consulte también**

[Eliminación de un extremo mediante la API de Java](programmatically-endpoints.md#removing-an-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eliminación de un extremo mediante la API de Java {#removing-an-endpoint-using-the-java-api}

Elimine un punto final utilizando la API de Java:

1. Incluir archivos de proyecto.

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto de cliente EndpointRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `EndpointRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Recupere el punto final que desea eliminar.

   * Recupere una lista de todos los extremos a los que tiene acceso el usuario actual (especificado en las propiedades de conexión) invocando la variable `EndpointRegistryClient` del objeto `getEndpoints` método y pasar una `PagingFilter` objeto que actúa como filtro. Puede pasar `(PagingFilter)null` para devolver todos los extremos. Este método devuelve un `java.util.List` objeto donde cada elemento es un `Endpoint` objeto.
   * Iterar a través de la variable `java.util.List` para determinar si tiene extremos. Si existen extremos, cada elemento es un `EndPoint` instancia.
   * Determine el servicio que corresponde a un punto final invocando la variable `EndPoint` del objeto `getServiceId` método. Este método devuelve un valor de cadena que especifica el nombre del servicio.
   * Determine el tipo de extremo invocando el `EndPoint` del objeto `getConnectorId` método. Este método devuelve un valor de cadena que especifica el tipo de extremo. Por ejemplo, si el punto final es un punto final de EJB, este método devuelve `EJB`.

1. Elimine el punto final.

   Elimine el punto final invocando la variable `EndpointRegistryClient` del objeto `remove` y pasando el `EndPoint` que representa el punto final que se va a quitar.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Eliminación de un extremo mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Recuperación de información del conector de extremo {#retrieving-endpoint-connector-information}

Puede recuperar mediante programación información sobre conectores de extremo mediante la API de AEM Forms. Un conector permite que un extremo invoque un servicio mediante varios métodos de invocación. Por ejemplo, un conector de carpeta vigilada permite que un extremo invoque un servicio mediante carpetas vigiladas. Mediante la recuperación mediante programación de información sobre los conectores de extremo, puede recuperar los valores de configuración asociados a un conector, como los valores de configuración necesarios y los opcionales.

Para demostrar cómo recuperar información sobre los conectores de extremo, esta sección recupera información sobre un conector de carpeta vigilada. (Consulte [Añadir puntos finales de carpeta vigilada](programmatically-endpoints.md#adding-watched-folder-endpoints).)

>[!NOTE]
>
>No se puede recuperar información sobre extremos mediante servicios web.

>[!NOTE]
>
>Este tema utiliza la variable `ConnectorRegistryClient` API para recuperar información sobre conectores de extremo. (Consulte [Referencia de la API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

### Resumen de los pasos {#summary_of_steps-8}

Para recuperar la información del conector de extremo, realice las siguientes tareas:

1. Incluir archivos de proyecto.
1. Cree un `ConnectorRegistryClient` objeto.
1. Especifique el tipo de conector.
1. Recupere valores de configuración.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

Los siguientes archivos JAR deben agregarse a la ruta de clase del proyecto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-Utilities.jar (obligatorio si AEM Forms está implementado en el servidor de aplicaciones JBoss)
* jbossall-client.jar (requerido si AEM Forms está implementado en el servidor de aplicaciones JBoss)

Si AEM Forms se implementa en un servidor de aplicaciones J2EE compatible que no sea JBoss, sustituya adobe-Utilities.jar y jbossall-client.jar por archivos JAR específicos del servidor de aplicaciones J2EE en el que se implementa AEM Forms. Para obtener información sobre la ubicación de todos los archivos JAR de AEM Forms, consulte [Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Creación de un objeto cliente ConnectorRegistry**

Para recuperar mediante programación la información del conector del extremo, cree un `ConnectorRegistryClient` objeto.

**Especifique el tipo de conector**

Especifique el tipo de conector desde el que desea recuperar información. Existen los siguientes tipos de conectores:

* **EJB**: Permite que una aplicación cliente invoque un servicio mediante el modo EJB.
* **SOAP**: Permite que una aplicación cliente invoque un servicio mediante el modo SOAP.
* **Carpeta vigilada**: Permite que las carpetas vigiladas invoquen un servicio.
* **Correo electrónico**: Permite que los mensajes de correo electrónico invoquen un servicio.
* **Remoto**: Permite que una aplicación cliente de Flex invoque un servicio.
* **TaskManagerConnector**: Permite a un usuario de Workspace invocar un servicio desde Workspace.

**Recuperar valores de configuración**

Después de especificar el tipo de conector, puede recuperar información sobre el conector, como el valor de configuración admitido. Por ejemplo, para cualquier conector, puede determinar qué valores de configuración son obligatorios y cuáles son opcionales.

**Consulte también**

[Recuperar información del conector de extremo mediante la API de Java](programmatically-endpoints.md#retrieve-endpoint-connector-information-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Recuperar información del conector de extremo mediante la API de Java {#retrieve-endpoint-connector-information-using-the-java-api}

Recupere la información del conector de extremo mediante la API de Java:

1. Incluir archivos de proyecto. .

   Incluya archivos JAR del cliente, como adobe-livecycle-client.jar, en la ruta de clase de su proyecto Java.

1. Cree un objeto cliente ConnectorRegistry.

   * Cree un `ServiceClientFactory` objeto que contiene propiedades de conexión.
   * Cree un `ConnectorRegistryClient` usando su constructor y pasando el `ServiceClientFactory` objeto.

1. Especifique el tipo de conector.

   Especifique el tipo de conector invocando la variable `ConnectorRegistryClient` del objeto `getEndpointDefinition` y pasando un valor de cadena que especifica el tipo de conector. Por ejemplo, para especificar el tipo de conector Carpeta vigilada, pase el valor de cadena `WatchedFolder`. Este método devuelve un `Endpoint` objeto que corresponde al tipo de conector.

1. Recupere valores de configuración.

   * Recupere los valores de configuración asociados dentro de este extremo invocando la variable `Endpoint` del objeto `getConfigParameters` método. Este método devuelve una matriz de `ConfigParameter` objetos.
   * Recupere información sobre cada valor de configuración recuperando cada elemento dentro de la matriz. Cada elemento es un `ConfigParameter` objeto. Por ejemplo, puede determinar si el valor de configuración es obligatorio u opcional invocando la variable `ConfigParameter` del objeto `isRequired` método. Si el valor de configuración es obligatorio, este método devuelve `true`.

**Consulte también**

[Resumen de los pasos](programmatically-endpoints.md#summary-of-steps)

[Inicio rápido: Recuperación de información del conector de extremo mediante la API de Java](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
