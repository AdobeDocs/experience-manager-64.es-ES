---
title: Trabajar con el repositorio de AEM Forms
seo-title: Working with AEM Forms Repository
description: Administre el repositorio de AEM Forms para crear carpetas, escribir, enumerar, leer, actualizar recursos y buscar recursos mediante la API de Java y la API de servicio web. Además, aprenda a crear relaciones de recursos, bloquear y eliminar recursos.
seo-description: Manage AEM Forms repository to create folders, write, list, read, update resources, and search resources using the Java API and Web Service API. In addition, learn how to create resource relationships, lock and delete resources.
uuid: 6ead49f9-ca0d-4ee4-86a6-0a9ced6ec4f8
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d2c95881-6c02-4e34-85af-84607df54287
role: Developer
exl-id: e006c32b-edff-40f2-8c0a-228008dcf03a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '9146'
ht-degree: 1%

---

# Trabajar con el repositorio de AEM Forms {#working-with-aem-forms-repository}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

**Acerca del Servicio de Repositorio**

El servicio Repositorio proporciona servicios de administración y almacenamiento de recursos a AEM Forms. Cuando los desarrolladores crean un *AEM Forms* , pueden implementar los recursos en el repositorio en lugar del sistema de archivos. Los recursos pueden incluir cualquier tipo de material colateral, incluidos formularios XML, PDF forms (incluidos los formularios Acrobat), fragmentos de formulario, imágenes, perfiles, políticas, archivos de SWF, archivos DDX, esquemas XML, archivos WSDL y datos de prueba.

Por ejemplo, considere la siguiente aplicación de Forms llamada *Aplicaciones/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Observe que hay un archivo llamado Loan.xdp ubicado en FormsFolder. Para acceder a este diseño de formulario, debe especificar la ruta completa (incluida la versión): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Para obtener información sobre la creación de una aplicación de Forms mediante Workbench, consulte [Ayuda de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

La ruta a un recurso ubicado en el repositorio de AEM Forms es:

`Applications/Application-name/Application-version/Folder.../Filename`

Los siguientes valores muestran algunos ejemplos de valores de URI:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>Puede examinar el repositorio de AEM Forms utilizando un explorador web. Para explorar el repositorio, introduzca la siguiente URL en un explorador web https://[nombre del servidor]:[puerto del servidor]/repository. Puede verificar los resultados de inicio rápido asociados a la sección Trabajo con el repositorio de AEM Forms mediante un explorador web. Por ejemplo, si agrega contenido al repositorio de AEM Forms, puede ver el contenido en un explorador web. (Consulte [Inicio rápido (modo SOAP): Escritura de un recurso mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

La API del repositorio proporciona una serie de operaciones que puede utilizar para almacenar y recuperar información del repositorio. Por ejemplo, puede obtener una lista de recursos o recuperar recursos específicos almacenados en el repositorio cuando se necesita un recurso como parte del procesamiento de una aplicación.

>[!NOTE]
>
>La API del repositorio no se puede usar para interactuar con los servicios de contenido (obsoleto). Para interactuar con los servicios de contenido (obsoletos), utilice la API de gestión de documentos.

Mediante la API de servicio del repositorio, puede realizar las siguientes tareas:

* Crear carpetas. Consulte [Creación de carpetas](aem-forms-repository.md#creating-folders).
* Escribir recursos y sus propiedades. Consulte [Escribir recursos](aem-forms-repository.md#writing-resources).
* Enumerar recursos en una colección determinada o relacionados con otros recursos. Consulte [Listing Resources](aem-forms-repository.md#listing-resources).
* Lea los recursos y sus propiedades. Consulte [Leer recursos](aem-forms-repository.md#reading-resources).
* Actualice los recursos y sus propiedades. Consulte [Actualización de recursos](aem-forms-repository.md#updating-resources).
* Busque recursos, incluido su historial, recursos relacionados y propiedades. Consulte [Búsqueda de recursos](aem-forms-repository.md#searching-for-resources).
* Especifique las relaciones entre los recursos. Consulte [Creación de Relaciones de Recursos](aem-forms-repository.md#creating-resource-relationships).
* Administre el control de acceso a los recursos, incluido el bloqueo y desbloqueo de recursos, y lea y escriba listas de control de acceso (ACL). Consulte [Bloqueo de recursos](aem-forms-repository.md#locking-resources).
* Elimine los recursos y sus propiedades. Consulte [Eliminación de recursos](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Con la API del repositorio, no puede administrar el control de acceso a recursos, buscar recursos ni especificar relaciones de recursos mediante un repositorio ECM.

>[!NOTE]
>
>Cuando se escribe un PDF cifrado en el repositorio, no se puede utilizar la función de extracción de relaciones automatizada. De lo contrario, se puede almacenar un PDF cifrado en el repositorio y recuperarlo posteriormente. El recuperador puede elegir descifrar el PDF después de recuperarlo del repositorio.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Creación de carpetas {#creating-folders}

Las carpetas (colecciones de recursos) se utilizan para almacenar objetos (archivos o recursos) en agrupaciones organizadas. Las carpetas pueden contener recursos y otras carpetas, también conocidas como subcarpetas. Los recursos solo se pueden almacenar en una carpeta a la vez.

Los archivos heredan las listas de control de acceso (ACL) de las carpetas y las subcarpetas heredan las ACL de sus carpetas principales. Por lo tanto, las carpetas principales deben existir para poder crear carpetas secundarias. El IDE permite interactuar solamente carpeta por carpeta, no archivo por archivo. No es posible crear versiones de carpetas y no es necesario hacerlo; una carpeta no contiene datos en sí. En su lugar, solo es un contenedor de recursos que contienen datos. El ACL predeterminado es un permiso de nivel de sistema, lo que significa que los usuarios deben tener permisos de nivel de sistema (leer, escribir, atravesar, administrar ACL) hasta que alguien les conceda permisos para una carpeta en particular. Las ACL solo funcionan en el IDE.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary-of-steps}

Para crear una carpeta, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree el cliente de servicio.
1. Cree la carpeta .
1. Escriba la carpeta en el repositorio.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder crear una colección de recursos mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Crear la carpeta**

Invoque el método del servicio Repositorio para crear la recopilación de recursos y rellenarla con información de identificación, incluido su UUID, nombre de carpeta y descripción.

**Escriba la carpeta en el repositorio**

Invoque el método del servicio Repositorio para escribir la recopilación de recursos, especificando el URI de la carpeta de destino.

**Consulte también**

[Creación de carpetas mediante la API de Java](aem-forms-repository.md#create-folders-using-the-java-api)

[Creación de carpetas mediante la API de servicio web](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Creación de carpetas mediante la API de Java {#create-folders-using-the-java-api}

Cree una carpeta utilizando la API de servicio del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos de proyecto en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Crear la carpeta

   Para crear una colección de recursos, primero debe crear una `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` objeto.

   Invocar el `repositoryInfomodelFactoryBean` del objeto `newResourceCollection` y pase los siguientes parámetros:

   * A `com.adobe.repository.infomodel.Id` Identificador UUID que se asignará al recurso.
   * A `com.adobe.repository.infomodel.Lid` Identificador UUID que se asignará al recurso.
   * A `java.lang.String` que contiene el nombre de la colección de recursos. Por ejemplo, `FormsFolder`.

   El método devuelve un valor `com.adobe.repository.infomodel.bean.ResourceCollection` que representa la nueva carpeta.

   Defina la descripción de la carpeta utilizando la variable `setDescription` y pase el siguiente parámetro:

   * A `String` que describe la colección de recursos. En este ejemplo, `"test Folder"` se utiliza `.`


1. Escriba la carpeta en el repositorio

   Invocar el `ResourceRepositoryClient` del objeto `writeResource` y pase el URI de la carpeta y el `ResourceCollection` objeto. Por ejemplo, el URI de la carpeta puede ser el siguiente valor `/Applications/FormsApplication/1.0/`.

   El método devuelve una instancia de la `com.adobe.repository.infomodel.bean.Resource` objeto. Por ejemplo, puede recuperar el valor de identificador del nuevo recurso invocando la variable `com.adobe.repository.infomodel.bean.Resource` del objeto `getId` método.

**Consulte también**

[Creación de carpetas](aem-forms-repository.md#creating-folders)

[Inicio rápido (modo SOAP): Creación de una carpeta mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Creación de carpetas mediante la API de servicio web {#create-folders-using-the-web-service-api}

Cree una carpeta utilizando la API de servicio del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL de repositorio utilizando base64.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` objeto que contiene el nombre de usuario y la contraseña.

1. Crear la carpeta

   Cree la carpeta utilizando el constructor predeterminado para `ResourceCollection` y pase los siguientes parámetros:

   * Un `Id` objeto, que se crea invocando el constructor predeterminado para la variable `Id` y asignado a la `Resource` del objeto `id` campo .
   * Un `Lid` objeto, que se crea invocando el constructor predeterminado para la variable `Lid` y asignado a la `Resource` del objeto `lid` campo .
   * Una cadena que contiene el nombre de la colección de recursos, que se asigna a la variable `Resource` del objeto `name` campo . El nombre utilizado en este ejemplo es `"testfolder"`.
   * Una cadena que contiene la descripción de la colección de recursos, que se asigna a la variable `Resource` del objeto `description` campo . La descripción utilizada en este ejemplo es `"test folder"`.

1. Escriba la carpeta en el repositorio

   Invocar el `RepositoryServiceService` del objeto `writeResource` y pase los siguientes parámetros:

   * Ruta donde se creará la carpeta.
   * La variable `ResourceCollection` que representa la carpeta.
   * Pass `null` para los otros dos parámetros.

**Consulte también**

[Creación de carpetas](aem-forms-repository.md#creating-folders)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Escribir recursos {#writing-resources}

Puede crear recursos en una ubicación determinada del repositorio. El tamaño natural del archivo está sujeto a las limitaciones de la base de datos y al tiempo de espera de la sesión. Para la configuración predeterminada, los archivos están limitados a 25 MB. Para aumentar o reducir el tamaño máximo del archivo, debe cambiar la configuración de la base de datos.

La escritura de recursos equivale a almacenar datos en el repositorio. Una vez que escriba un recurso en el repositorio, este será accesible para todos los clientes del ecosistema del repositorio. Al escribir recursos en el repositorio, como esquemas XML, archivos XDP y archivos XSD, el contenido se analiza en función del tipo MIME. Si se admite el tipo MIME, el analizador determina si existe una relación implícita con otro contenido. Por ejemplo, si una hoja de estilos en cascada (CSS) tiene una URL relativa que hace referencia a una CSS común, se espera que también envíe la CSS común al repositorio. La relación entre los dos recursos se almacena como una relación pendiente durante un período no ajustable de 30 días. Cuando envía la CSS común al repositorio dentro del periodo de 30 días, se forma la relación.

Cuando crea un recurso, la lista de control de acceso (ACL) se hereda de la carpeta principal. La carpeta raíz tiene permisos de nivel de sistema hasta que se crea un recurso o carpeta inicial, momento en el que el recurso o la carpeta reciben permisos ACL predeterminados.

Puede escribir recursos mediante programación mediante la API Java del servicio Repositorio o la API del servicio Web.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-1}

Para escribir un recurso, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique el URI del recurso que se va a leer.
1. Lea el recurso .

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique el URI de la carpeta de destino del recurso**

Cree una cadena que contenga el URI del recurso que se va a leer. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*carpeta*&quot;.

**Crear el recurso**

Invoque el método del servicio Repositorio para crear el recurso y rellénelo con información de identificación, incluyendo su UUID, nombre de recurso y descripción.

**Especificar el contenido del recurso**

Invoque el método del servicio Repositorio para crear contenido de recursos y almacenar ese contenido en el recurso.

**Escribir el recurso en la carpeta de destino**

Invoque el método del servicio Repositorio para escribir el recurso, especificando el URI de la carpeta de destino.

**Consulte también**

[Escribir recursos mediante la API de Java](aem-forms-repository.md#write-resources-using-the-java-api)

[Escribir recursos mediante la API de servicio web](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Escribir recursos mediante la API de Java {#write-resources-using-the-java-api}

Escriba un recurso utilizando la API de servicio del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique el URI de la carpeta de destino del recurso

   Especifique el URI de la carpeta de destino del recurso. En este caso, porque el recurso tiene el nombre `testResource` se almacenará en la carpeta denominada `testFolder`, el URI de la carpeta es `"/testFolder"`. El URI se almacena como un `java.lang.String` objeto.

1. Crear el recurso

   Para crear un recurso, primero debe crear un `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` objeto.

   Invocar el `RepositoryInfomodelFactoryBean` del objeto `newResource` que crea un `com.adobe.repository.infomodel.bean.Resource` objeto. En este ejemplo, se proporcionan los siguientes parámetros:

   * A `com.adobe.repository.infomodel.Id` objeto, que se crea invocando el constructor predeterminado para la variable `Id` Clase .
   * A `com.adobe.repository.infomodel.Lid` objeto, que se crea invocando el constructor predeterminado para la variable `Lid` Clase .
   * A `java.lang.String` que contiene el nombre de archivo del recurso.

   Para especificar la descripción del recurso, invoque la variable `Resource` del objeto `setDescription` y pase una cadena que contenga la descripción. En este ejemplo, la descripción es `"test resource"`.

1. Especificar el contenido del recurso

   Para crear contenido para el recurso, invoque la variable `RepositoryInfomodelFactoryBean` del objeto `newResourceContent` que devuelve un valor `com.adobe.repository.infomodel.bean.ResourceContent` objeto. Añada contenido a `ResourceContent` objeto. En este ejemplo, esto se logra realizando las siguientes tareas:

   * Invocación del `ResourceContent` del objeto `setDataDocument` método y pasar un `com.adobe.idp.Document` object
   * Invocación del `ResourceContent` del objeto `setSize` y pasando el tamaño en bytes del `Document` object

   Añada el contenido al recurso invocando la variable `Resource` del objeto `setContent` y pasando el `ResourceContent` objeto. Para obtener más información, consulte [Referencia de la API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Escribir el recurso en la carpeta de destino

   Invocar el `ResourceRepositoryClient` del objeto `writeResource` y pase el URI de la carpeta, así como el `Resource` objeto.

**Consulte también**

[Escribir recursos](aem-forms-repository.md#writing-resources)

[Inicio rápido (modo SOAP): Escritura de un recurso mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Escribir recursos mediante la API de servicio web {#write-resources-using-the-web-service-api}

Escriba un recurso utilizando la API de servicio del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL de repositorio utilizando base64.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especifique el URI de la carpeta de destino del recurso

   Especifique el URI de la carpeta de destino del recurso. En este caso, porque el recurso tiene el nombre `testResource` se almacenará en la carpeta denominada `testFolder`, el URI de la carpeta es `"/testFolder"`. Cuando utilice un idioma compatible con Microsoft .NET Framework (por ejemplo, C#), almacene el URI en un `System.String` objeto.

1. Crear el recurso

   Para crear un recurso, invoque el constructor predeterminado para `Resource` Clase . En este ejemplo, la siguiente información se almacena en la variable `Resource` objeto:

   * A `com.adobe.repository.infomodel.Id` objeto, que se crea invocando el constructor predeterminado para la variable `Id` y asignado a la `Resource` del objeto `id` campo .
   * A `com.adobe.repository.infomodel.Lid` objeto, que se crea invocando el constructor predeterminado para la variable `Lid` y asignado a la `Resource` del objeto `lid` campo .
   * Una cadena que contiene el nombre de archivo del recurso, que se asigna a la variable `Resource` del objeto `name` campo . El nombre utilizado en este ejemplo es `"testResource"`.
   * Una cadena que contiene la descripción del recurso, que se asigna a la variable `Resource` del objeto `description` campo . La descripción utilizada en este ejemplo es `"test resource"`.

1. Especificar el contenido del recurso

   Para crear contenido para el recurso, invoque el constructor predeterminado para la variable `ResourceContent` Clase . A continuación, añada contenido al `ResourceContent` objeto. En este ejemplo, esto se logra realizando las siguientes tareas:

   * Asignación de un `BLOB` objeto que contiene un documento de `ResourceContent` del objeto `dataDocument` campo .
   * Asignación del tamaño en bytes de la variable `BLOB` al `ResourceContent` del objeto `size` campo .

   Añada el contenido al recurso asignando la variable `ResourceContent` al `Resource` del objeto `content` campo .

1. Escribir el recurso en la carpeta de destino

   Invocar el `RepositoryServiceService` del objeto `writeResource` y pase el URI de la carpeta, así como el `Resource` objeto. Pass `null` para los otros dos parámetros.

**Consulte también**

[Escribir recursos](aem-forms-repository.md#writing-resources)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Listing Resources {#listing-resources}

Puede descubrir recursos enumerando recursos. Se realiza una consulta en el repositorio para encontrar todos los recursos relacionados con una colección de recursos determinada.

Una vez que haya organizado los recursos, puede inspeccionar la estructura que ha creado al ver una rama concreta de la estructura, como lo haría en un sistema operativo.

La lista de recursos funciona según la relación: los recursos son miembros de carpetas. La afiliación está representada por una relación de tipo &quot;miembro de&quot;. Cuando enumera los recursos en una carpeta determinada, consulta los recursos relacionados con una carpeta determinada mediante la relación &quot;miembro de&quot;. Las relaciones son direccionales: un miembro de una relación tiene un origen que es miembro del objetivo. La fuente es el recurso; el destino es la carpeta principal.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-2}

Para enumerar los recursos, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree el cliente de servicio.
1. Especifique la ruta de la carpeta.
1. Recupere la lista de recursos.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder crear una colección de recursos mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especificar la ruta de la carpeta**

Cree una cadena que contenga la ruta de la carpeta que contiene los recursos. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*carpeta*&quot;.

**Recupere la lista de recursos**

Invoque el método Repository service para recuperar la lista de recursos, especificando la ruta de la carpeta de destino.

**Consulte también**

[Enumerar recursos mediante la API de Java](aem-forms-repository.md#list-resources-using-the-java-api)

[Enumerar recursos mediante la API de servicio web](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Enumerar recursos mediante la API de Java {#list-resources-using-the-java-api}

Enumerar recursos utilizando la API de servicio de Repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especificar la ruta de la carpeta

   Especifique el URI de la colección de recursos que desea consultar. En este caso, su URI es `"/testFolder"`. El URI se almacena como un `java.lang.String` objeto.

1. Recupere la lista de recursos

   Invocar el `ResourceRepositoryClient` del objeto `listMembers` y pase el URI de la carpeta.

   El método devuelve un valor `java.util.List` de `com.adobe.repository.infomodel.bean.Resource` objetos que son el origen de un `com.adobe.repository.infomodel.bean.Relation` de tipo `Relation.TYPE_MEMBER_OF` y tengan el URI de recopilación de recursos como destino. Puede iterar a través de esta `List` para recuperar cada uno de los recursos. En este ejemplo, se muestra el nombre y la descripción de cada recurso.

**Consulte también**

[Listing Resources](aem-forms-repository.md#listing-resources).

[Inicio rápido (modo SOAP): Listado de recursos mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Enumerar recursos mediante la API de servicio web {#list-resources-using-the-web-service-api}

Enumerar recursos utilizando la API de servicio del Repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL del repositorio.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especificar la ruta de la carpeta

   Especifique una cadena que contenga el URI de la carpeta que se va a consultar. En este caso, su URI es `"/testFolder"`. Cuando utilice un idioma compatible con Microsoft .NET Framework (por ejemplo, C#), almacene el URI en un `System.String` objeto.

1. Recupere la lista de recursos

   Invocar el `RepositoryServiceService` del objeto `listMembers` y pase el URI de la carpeta como el primer parámetro. Pass `null` para los otros dos parámetros.

   El método devuelve una matriz de objetos que se pueden convertir en `Resource` objetos. Puede iterar a través de la matriz de objetos para recuperar cada uno de los recursos relacionados. En este ejemplo, se muestra el nombre y la descripción de cada recurso.

**Consulte también**

[Listing Resources](aem-forms-repository.md#listing-resources).

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Leer recursos {#reading-resources}

Puede recuperar recursos de una ubicación determinada en el repositorio para leer su contenido y metadatos. El flujo de trabajo es front-end mediante un formulario de inicialización. El proceso tiene todos los permisos necesarios para leer el formulario. El sistema recupera el formulario de datos y lee el contenido del repositorio. El repositorio concede acceso al contenido y a los metadatos (la capacidad de saber si el recurso existe).

El repositorio tiene los cuatro tipos de permisos siguientes:

* **traverse**: permite enumerar recursos; es decir, para leer metadatos de recursos, pero no contenido de recursos
* **read**: le permite leer contenido de recursos
* **write**: permite escribir contenido de recursos
* **administración de listas de control de acceso (ACL)**: le permite manipular las ACL en los recursos

Los usuarios solo pueden ejecutar procesos cuando tienen permiso para ejecutar el proceso. Los usuarios de IDE necesitan permisos de lectura y travesía para sincronizarse con el repositorio. Las ACL se aplican solo en el momento del diseño porque el tiempo de ejecución se produce dentro del contexto del sistema.

Puede leer recursos mediante programación mediante la API Java del servicio Repositorio o la API del servicio Web.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-3}

Para leer un recurso, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique el URI del recurso que se va a leer.
1. Lea el recurso .

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique el URI del recurso que se va a leer**

Cree una cadena que contenga el URI del recurso que se va a leer. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*recurso*&quot;.

**Leer el recurso**

Invoque el método del servicio Repositorio para leer el recurso, especificando el URI.

**Consulte también**

[Leer recursos mediante la API de Java](aem-forms-repository.md#read-resources-using-the-java-api)

[Lectura de recursos mediante la API de servicio web](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Leer recursos mediante la API de Java {#read-resources-using-the-java-api}

Lea un recurso utilizando la API de servicio del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique el URI del recurso que se va a leer

   Especifique un valor de cadena que represente el URI del recurso que se va a recuperar. Por ejemplo, suponiendo que el recurso tenga el nombre *testResource* que se encuentra en una carpeta denominada *testFolder*, especifique `/testFolder/testResource`.

1. Leer el recurso

   Invocar el `ResourceRepositoryClient` del objeto `readResource` y pase el URI del recurso como parámetro. Este método devuelve un `Resource` que representa el recurso.

**Consulte también**

[Leer recursos](aem-forms-repository.md#reading-resources)

[Inicio rápido (modo SOAP): Leer un recurso mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Lectura de recursos mediante la API de servicio web {#reading-resources-using-the-web-service-api}

Lea un recurso utilizando la API de servicio del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL del repositorio. (Consulte [Creación de un ensamblado de cliente .NET que utilice la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)
   * Haga referencia al ensamblado del cliente Microsoft .NET. (Consulte [Creación de un ensamblado de cliente .NET que utilice la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especifique el URI del recurso que se va a leer

   Especifique una cadena que contenga el URI del recurso que se va a recuperar. En este caso, porque el recurso tiene el nombre `testResource` está en la carpeta denominada `testFolder`, su URI es `"/testFolder/testResource"`. Cuando utilice un idioma compatible con Microsoft .NET Framework (por ejemplo, C#), almacene el URI en un `System.String` objeto.

1. Leer el recurso

   Invocar el `RepositoryServiceService` del objeto `readResource` y pase el URI del recurso como el primer parámetro. Pass `null` para los otros dos parámetros.

**Consulte también**

[Leer recursos](aem-forms-repository.md#reading-resources)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Actualización de recursos {#updating-resources}

Puede recuperar y actualizar el contenido de los recursos en el repositorio. Al actualizar los recursos, el control de acceso a esos recursos permanece sin cambios entre las versiones. Al realizar una actualización, tiene la opción de incrementar la versión principal. Si no decide incrementar la versión principal, la versión secundaria se actualiza automáticamente.

Al actualizar un recurso, la nueva versión se crea en función de los atributos de recurso especificados. Al actualizar un recurso, se especifican dos parámetros importantes: el URI de destino y una instancia de recurso que contiene todos los metadatos actualizados. Es importante tener en cuenta que si no cambia un atributo determinado (por ejemplo, el nombre), el atributo sigue siendo necesario en la instancia que pasa. Las relaciones que se crean al analizar el contenido se añaden a la versión específica y no se presentan a menos que se especifique lo contrario.

Por ejemplo, si actualiza un archivo XDP y contiene referencias a otros recursos, esas referencias adicionales también se registrarán. Supongamos que la versión 1.0 de form.xdp tiene dos referencias externas: un logotipo y una hoja de estilo, y posteriormente se actualiza form.xdp para que ahora tenga tres referencias: un logotipo, una hoja de estilo y un archivo de esquema. Durante la actualización, el repositorio agregará la tercera relación (al archivo de esquema) a su tabla de relación pendiente. Una vez que el archivo de esquema está presente en el repositorio, la relación se formará automáticamente. Sin embargo, si la versión 2.0 de form.xdp ya no utiliza el logotipo, la versión 2.0 de form.xdp no tendrá relación con el logotipo.

Todas las operaciones de actualización son atómicas y transaccionales. Por ejemplo, si dos usuarios leen el mismo recurso y ambos deciden actualizar la versión 1.0 a la versión 2.0, uno de ellos tendrá éxito y uno de ellos fallará, la integridad del repositorio se mantendrá y ambos recibirán un mensaje que confirme el éxito o el error. Si la transacción no se confirma, se redirigirá en caso de error de la base de datos y se agotará el tiempo de espera o se volverá a utilizar en función del servidor de aplicaciones.

Puede actualizar los recursos mediante programación mediante la API de Java del servicio Repositorio o la API de servicio Web.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-4}

Para actualizar un recurso, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Recupere el recurso que desea actualizar.
1. Actualice el recurso.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Recupere el recurso que desea actualizar**

Lea el recurso . Para obtener más información, consulte [Leer recursos](aem-forms-repository.md#reading-resources).

**Actualizar el recurso**

Defina la nueva información en el recurso e invoque el método del servicio Repositorio para actualizar el recurso, especificando el URI, el recurso actualizado y cómo se debe actualizar la información de la versión.

**Consulte también**

[Actualización de recursos mediante la API de Java](aem-forms-repository.md#update-resources-using-the-java-api)

[Actualización de recursos mediante la API de servicio web](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Actualización de recursos mediante la API de Java {#update-resources-using-the-java-api}

Actualice un recurso utilizando la API de servicio del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Recupere el recurso que desea actualizar

   Especifique el URI del recurso para recuperar y leer el recurso. En este ejemplo, el URI del recurso es `"/testFolder/testResource"`.

1. Actualizar el recurso

   Actualice el `Resource` información del objeto. En este ejemplo, para actualizar la descripción, invoque la función `Resource` del objeto `setDescription` y pase la nueva cadena de descripción como parámetro.

   A continuación, invoque el `ServiceClientFactory` del objeto `updateResource` y pase los siguientes parámetros:

   * A `java.lang.String` que contiene el URI del recurso.
   * La variable `Resource` que contiene la información actualizada del recurso.
   * A `boolean` que indica si se debe actualizar la versión principal o secundaria. En este ejemplo, un valor de `true` se transfiere para indicar que la versión principal se va a incrementar.

**Consulte también**

[Actualización de recursos](aem-forms-repository.md#updating-resources)

[Inicio rápido (modo SOAP): Actualización de un recurso mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Actualización de recursos mediante la API de servicio web {#update-resources-using-the-web-service-api}

Actualice un recurso mediante la API del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL del repositorio.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Recupere el recurso que desea actualizar

   Especifique el URI del recurso que se va a recuperar y lea el recurso. En este ejemplo, el URI del recurso es `"/testFolder/testResource"`. Para obtener más información, consulte [Leer recursos](aem-forms-repository.md#reading-resources).

1. Actualizar el recurso

   Actualice el `Resource` información del objeto. En este ejemplo, para actualizar la descripción, asigne un nuevo valor a la variable `Resource` del objeto `description` campo .

1. Invocar el `RepositoryServiceService` del objeto `updateResource` y pase los siguientes parámetros:

   * A `System.String` que contiene el URI del recurso.
   * La variable `Resource` que contiene la información actualizada del recurso.
   * A `boolean` que indica si se debe actualizar la versión principal o secundaria. En este ejemplo, un valor de `true` se transfiere para indicar que la versión principal se va a incrementar.
   * Pass `null` para los dos parámetros restantes.

**Consulte también**

[Actualización de recursos](aem-forms-repository.md#updating-resources)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Búsqueda de recursos {#searching-for-resources}

Puede construir consultas utilizadas para buscar recursos en el repositorio, incluido el historial, los recursos relacionados y las propiedades.

Puede recuperar recursos relacionados para determinar las dependencias entre un formulario y sus fragmentos. Por ejemplo, si tiene un formulario, puede determinar qué fragmentos o recursos externos utiliza. Si tiene una imagen, también puede averiguar qué formularios utilizan la imagen. También puede buscar recursos relacionados mediante el filtrado basado en propiedades. Por ejemplo, puede buscar todos los formularios que utilicen una imagen con un nombre especificado o cualquier imagen utilizada por un formulario con un nombre especificado. También puede buscar mediante las propiedades de los recursos. Por ejemplo, puede realizar una consulta para encontrar todos los formularios o recursos cuyo nombre comience con una cadena determinada que pueda incluir los caracteres comodín de ’%’ y ’_’. Recuerde que las búsquedas basadas en propiedades no se basan en relaciones; estas búsquedas se basan en el supuesto de que tiene conocimientos específicos sobre un recurso determinado.

**Instrucciones de consulta**

A *query* contiene una o más afirmaciones que se unen lógicamente con condiciones. A *statement* consta de un operando izquierdo, un operador y un operando derecho. Además, puede especificar el orden que se utilizará para los resultados de búsqueda. La variable *orden* contiene información equivalente a un SQL `ORDER BY` y consta de elementos que contienen los atributos en los que se basó la búsqueda, así como un valor que indica si se va a utilizar el orden ascendente o descendente.

Puede buscar recursos mediante programación mediante la API Java del servicio Repositorio. En este momento, no es posible utilizar la API de servicio web para buscar recursos.

**Comportamiento de la ordenación**

El orden no se respeta al invocar el `ResourceRepositoryClient` del objeto `searchProperties` y especificar un criterio de ordenación. Por ejemplo, supongamos que crea un recurso con tres propiedades personalizadas, donde los nombres de atributos son `name`, `secondName`y `asecondName`. A continuación, cree un elemento de orden en el nombre del atributo y establezca la variable `ascending` valor `true`.

A continuación, invoque la variable `ResourceRepositoryClient` del objeto `searchProperties` y pase en el orden. La búsqueda devuelve el recurso correcto, con las tres propiedades . Sin embargo, las propiedades no se ordenan por nombre de atributo. Se devuelven en el orden en que se añadieron: `name`, `secondName`y `asecondName`.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-5}

Para buscar recursos, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique la carpeta de destino para la búsqueda.
1. Especifique los atributos utilizados en la búsqueda.
1. Cree la consulta utilizada en la búsqueda.
1. Cree el orden de los resultados de la búsqueda.
1. Busque los recursos .
1. Recupere los recursos del resultado de la búsqueda.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique la carpeta de destino para la búsqueda**

Cree una cadena que contenga la ruta base desde la que realizar la búsqueda. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*carpeta*&quot;.

**Especifique los atributos utilizados en la búsqueda**

Puede basar la búsqueda en los atributos contenidos dentro de los recursos. Especifique los valores de los atributos en los que desea realizar la búsqueda.

**Crear la consulta utilizada en la búsqueda**

Construya una consulta utilizando instrucciones y condiciones. Cada instrucción especificará el atributo en el que se basará la búsqueda, la condición que se utilizará y el valor de atributo que se utilizará en la búsqueda.

**Crear el criterio de ordenación para los resultados de búsqueda**

El criterio de ordenación consta de elementos, cada uno de los cuales contiene uno de los atributos utilizados en la búsqueda y un valor que indica si se va a utilizar el orden ascendente o descendente.

**Buscar los recursos**

Busque los recursos utilizando la carpeta , la consulta y el orden de clasificación. Además, indique la profundidad de la búsqueda y un límite superior en el número de resultados que desea devolver.

**Recupere los recursos del resultado de la búsqueda**

Repita la lista de recursos devueltos y extraiga la información para un procesamiento posterior.

**Consulte también**

[Buscar recursos mediante la API de Java](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Buscar recursos mediante la API de Java {#search-for-resources-using-the-java-api}

Busque un recurso utilizando la API de servicio del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique la carpeta de destino para la búsqueda

   Especifique el URI de la ruta base desde la que se ejecutará la búsqueda. En este ejemplo, el URI del recurso es `/testFolder`.

1. Especifique los atributos utilizados en la búsqueda

   Especifique los valores de los atributos en los que desea realizar la búsqueda. Los atributos existen dentro de un `com.adobe.repository.infomodel.bean.Resource` objeto. En este ejemplo, la búsqueda se realizará en el atributo name; por lo tanto, `java.lang.String` que contiene el `Resource` se utiliza el nombre del objeto, que es `testResource` en este caso.

1. Crear la consulta utilizada en la búsqueda

   Para crear una consulta, cree una `com.adobe.repository.query.Query` invocando el constructor predeterminado para la variable `Query` y añadir instrucciones a la consulta.

   Para crear una instrucción, invoque el constructor para `com.adobe.repository.query.Query.Statement` y pase los siguientes parámetros:

   * Un operando izquierdo que contiene la constante de atributo de recurso. En este ejemplo, como el nombre del recurso se utiliza como base para la búsqueda, el valor estático `Resource.ATTRIBUTE_NAME` se utiliza.
   * Un operador que contiene la condición utilizada en la búsqueda del atributo. El operador debe ser una de las constantes estáticas de la variable `Query.Statement` Clase . En este ejemplo, el valor estático `Query.Statement.OPERATOR_BEGINS_WITH` se utiliza.
   * Operando derecho que contiene el valor de atributo en el que se debe realizar la búsqueda. En este ejemplo, el atributo name, una `String` que contiene el valor `"testResource"`, se utiliza.

   Especifique el área de nombres del operando izquierdo invocando la variable `Query.Statement` del objeto `setNamespace` y pasando uno de los valores estáticos contenidos en la variable `com.adobe.repository.infomodel.bean.ResourceProperty` Clase . En este ejemplo, se utiliza `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY`.

   Agregue cada instrucción a la consulta invocando la variable `Query` del objeto `addStatement` y pasando el `Query.Statement` objeto.

1. Crear el criterio de ordenación para los resultados de búsqueda

   Para especificar el criterio de ordenación utilizado en los resultados de búsqueda, cree un `com.adobe.repository.query.sort.SortOrder` invocando el constructor predeterminado para la variable `SortOrder` y añadir elementos al orden.

   Para crear un elemento para el criterio de ordenación, invoque uno de los constructores para `com.adobe.repository.query.sort.SortOrder.Element` Clase . En este ejemplo, como el nombre del recurso se utiliza como base para la búsqueda, el valor estático `Resource.ATTRIBUTE_NAME` se utiliza como primer parámetro y en orden ascendente (un `boolean` valor de `true`) se especifica como el segundo parámetro.

   Agregue cada elemento al orden invocando la variable `SortOrder` del objeto `addSortElement` y pasando el `SortOrder.Element` objeto.

1. Buscar los recursos

   Para buscar `resources` en función de las propiedades de atributo, invoque la variable `ResourceRepositoryClient` del objeto `searchProperties` y pase los siguientes parámetros:

   * A `String` que contiene la ruta base desde la que se ejecutará la búsqueda. En este caso, `"/testFolder"` se utiliza.
   * La consulta utilizada en la búsqueda.
   * La profundidad de la búsqueda. En este caso, `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` se utiliza para indicar que se van a utilizar la ruta base y todas sus carpetas.
   * Un `int` que indica la primera fila desde la que se selecciona el conjunto de resultados sin paginar. En este ejemplo, `0` se ha especificado.
   * Un `int` que indica el número máximo de resultados que se van a devolver. En este ejemplo, `10` se ha especificado.
   * El orden utilizado en la búsqueda.

   El método devuelve un valor `java.util.List` de `Resource` objetos en el orden especificado.

1. Recupere los recursos del resultado de la búsqueda

   Para recuperar los recursos contenidos en el resultado de la búsqueda, repita el `List` y convertir cada objeto en un `Resource` para extraer su información. En este ejemplo, se muestra el nombre de cada recurso.

**Consulte también**

[Búsqueda de recursos](aem-forms-repository.md#searching-for-resources)

[Inicio rápido (modo SOAP): Búsqueda de recursos mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Creación de Relaciones de Recursos {#creating-resource-relationships}

Puede especificar relaciones entre los recursos del repositorio. Hay tres tipos de relaciones:

* **Dependencia**: una relación en la que un recurso depende de otros recursos, lo que significa que todos los recursos relacionados se necesitan en el repositorio.
* **Pertenencia (sistema de archivos)**: una relación en la que un recurso se encuentra dentro de una carpeta determinada.
* **Personalizado**: una relación que especifique entre los recursos. Por ejemplo, si un recurso se ha desaprobado y otro se ha introducido en el repositorio, puede especificar su propia relación de reemplazo.

Puede crear sus propias relaciones personalizadas. Por ejemplo, si almacena un archivo HTML en el repositorio y utiliza una imagen, puede especificar una relación personalizada para relacionar el archivo HTML con la imagen (ya que normalmente solo los archivos XML se asocian a imágenes utilizando una relación de dependencia definida por el repositorio). Otro ejemplo de relación personalizada sería si desea crear una vista diferente del repositorio con una estructura de gráfico cíclica en lugar de una estructura de árbol. Puede definir un gráfico circular junto con un visualizador para recorrer esas relaciones. Por último, podría indicar que un recurso reemplaza a otro recurso aunque los dos recursos sean completamente diferentes. En ese caso, puede definir un tipo de relación fuera del rango reservado y crear una relación entre esos dos recursos. Su aplicación sería el único cliente que podría detectar y procesar la relación, y podría utilizarse para realizar búsquedas en esa relación.

Puede especificar mediante programación relaciones entre los recursos mediante el uso de la API de Java del servicio Repositorio o la API de servicio Web.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-6}

Para especificar una relación entre dos recursos, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique los URI de los recursos que desea relacionar.
1. Cree la relación.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique los URI de los recursos que desea relacionar**

Cree cadenas que contengan los URI del recurso que desea relacionar. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*recurso*&quot;.

**Crear la relación**

Invoque el método del servicio Repositorio para crear y especificar el tipo de relación.

**Consulte también**

[Creación de recursos de relación mediante la API de Java](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Creación de recursos de relación mediante la API de servicio web](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Creación de recursos de relación mediante la API de Java {#create-relationship-resources-using-the-java-api}

Cree recursos de relación utilizando la API Java del servicio Repositorio, realice las siguientes tareas:

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique los URI de los recursos que desea relacionar

   Especifique los URI de los recursos que desea relacionar. En este caso, porque los recursos tienen el nombre `testResource1` y `testResource2` y se encuentran en la carpeta denominada `testFolder`, sus URI son `"/testFolder/testResource1"` y `"/testFolder/testResource2"`. Los URI se almacenan como un `java.lang.String` objetos. En este ejemplo, los recursos se escriben primero en el repositorio y se recuperan sus URI. Para obtener más información sobre cómo escribir un recurso, consulte [Escribir recursos](aem-forms-repository.md#writing-resources).

1. Crear la relación

   Invocar el `ResourceRepositoryClient` del objeto `createRelationship` y pase los siguientes parámetros:

   * URI del recurso de origen.
   * El URI del recurso de destino.
   * El tipo de relación, que es una de las constantes estáticas de la variable `com.adobe.repository.infomodel.bean.Relation` Clase . En este ejemplo, se establece una relación de dependencia especificando el valor `Relation.TYPE_DEPENDANT_OF`.
   * A `boolean` valor que indica si el recurso de destino se actualiza automáticamente al `com.adobe.repository.infomodel.Id`Identificador basado en el nuevo recurso de encabezado. En este ejemplo, debido a la relación de dependencia, el valor `true` se ha especificado.

   También puede recuperar una lista de recursos relacionados para un recurso determinado invocando la variable `ResourceRepositoryClient` del objeto `getRelated` y pasar los siguientes parámetros:

   * El URI del recurso para el que se recuperan los recursos relacionados. En este ejemplo, el recurso de origen ( `"/testFolder/testResource1"`).
   * A `boolean` que indica si el recurso especificado es el recurso de origen de la relación. En este ejemplo, el valor `true` se especifica porque es el caso.
   * El tipo de relación, que es una de las constantes estáticas de la variable `Relation` Clase . En este ejemplo, se especifica una relación de dependencia utilizando el mismo valor utilizado anteriormente: `Relation.TYPE_DEPENDANT_OF`.

   La variable `getRelated` el método devuelve un `java.util.List` de `Resource` objetos a través de los cuales se puede iterar para recuperar cada uno de los recursos relacionados, moldeando los objetos contenidos en la variable `List` a `Resource` como usted lo hace. En este ejemplo, `testResource2` se espera que esté en la lista de recursos devueltos.

**Consulte también**

[Creación de Relaciones de Recursos](aem-forms-repository.md#creating-resource-relationships)

[Inicio rápido (modo SOAP): Creación de relaciones entre recursos mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Creación de recursos de relación mediante la API de servicio web {#create-relationship-resources-using-the-web-service-api}

Cree recursos de relación utilizando la API del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL del repositorio.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especifique los URI de los recursos que desea relacionar

   Especifique los URI de los recursos que desea relacionar. En este caso, porque los recursos tienen el nombre `testResource1` y `testResource2` y se encuentran en la carpeta denominada `testFolder`, sus URI son `"/testFolder/testResource1"` y `"/testFolder/testResource2"`. Cuando se utiliza un idioma compatible con Microsoft .NET Framework (por ejemplo, C#), los URI se almacenan como un `System.String` objetos. En este ejemplo, los recursos se escriben primero en el repositorio y se recuperan sus URI. Para obtener más información sobre cómo escribir un recurso, consulte [Escribir recursos](aem-forms-repository.md#writing-resources).

1. Crear la relación

   Invocar el `RepositoryServiceService` del objeto `createRelationship` y pase los siguientes parámetros:

   * URI del recurso de origen.
   * El URI del recurso de destino.
   * Tipo de relación. En este ejemplo, se establece una relación de dependencia especificando el valor `3`.
   * A `boolean` que indica si se especificó el tipo de relación. En este ejemplo, el valor `true` se ha especificado.
   * A `boolean` valor que indica si el recurso de destino se actualiza automáticamente al `Id`Identificador basado en el nuevo recurso de encabezado. En este ejemplo, debido a la relación de dependencia, el valor `true` se ha especificado.
   * A `boolean` que indica si se especificó el encabezado de destino. En este ejemplo, el valor `true` se ha especificado.
   * Pass `null` para el último parámetro.

   También puede recuperar una lista de recursos relacionados para un recurso determinado invocando la variable `RepositoryServiceService` del objeto `getRelated` y pasar los siguientes parámetros:

   * El URI del recurso para el que se recuperan los recursos relacionados. En este ejemplo, el recurso de origen ( `"/testFolder/testResource1"`).
   * A `boolean` que indica si el recurso especificado es el recurso de origen de la relación. En este ejemplo, el valor `true` se especifica porque es el caso.
   * A `boolean` que indica si se especificó el recurso de origen. En este ejemplo, el valor `true` se proporciona.
   * Matriz de enteros que contiene los tipos de relación. En este ejemplo, una relación de dependencia se especifica utilizando el mismo valor en la matriz que se usó anteriormente: `3`.
   * Pass `null` para los dos parámetros restantes.

   La variable `getRelated` devuelve una matriz de objetos que se pueden convertir en `Resource` objetos a través de los cuales puede iterar para recuperar cada uno de los recursos relacionados. En este ejemplo, `testResource2` se espera que esté en la lista de recursos devueltos.

**Consulte también**

[Creación de Relaciones de Recursos](aem-forms-repository.md#creating-resource-relationships)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bloqueo de recursos {#locking-resources}

Puede bloquear un recurso o conjunto de recursos para su uso exclusivo por un usuario en particular o para uso compartido entre más de un usuario. Un bloqueo compartido indica que algo va a pasar con el recurso, pero no impide que nadie más tome medidas con ese recurso. Un bloqueo compartido debe considerarse un mecanismo de señalización. Un bloqueo exclusivo significa que el usuario que ha bloqueado el recurso va a cambiar el recurso y el bloqueo garantiza que nadie más pueda hacerlo hasta que el usuario ya no necesite acceder al recurso y haya liberado el bloqueo. Si un administrador de repositorios desbloquea un recurso, todos los bloqueos exclusivos y compartidos de ese recurso se eliminarán automáticamente. Este tipo de acción está diseñado para situaciones en las que un usuario ya no está disponible y no ha desbloqueado el recurso.

Cuando un recurso está bloqueado, aparece un icono de bloqueo cuando se ve la ficha Recursos ubicada en Workbench, como se muestra en la siguiente ilustración.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

Puede controlar mediante programación el acceso a los recursos mediante la API de Java del servicio Repositorio o la API de servicio Web.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-7}

Para bloquear y desbloquear recursos, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique el URI del recurso que se va a bloquear.
1. Bloquee el recurso.
1. Recupere los bloqueos del recurso.
1. Desbloquear el recurso

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique el URI del recurso que se va a bloquear**

Cree una cadena que contenga el URI del recurso que se va a bloquear. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*recurso*&quot;.

**Bloqueo del recurso**

Invoque el método del servicio Repositorio para bloquear el recurso, especificando el URI, el tipo de bloqueo y la profundidad de bloqueo.

**Recuperar los bloqueos del recurso**

Invoque el método del servicio Repositorio para recuperar los bloqueos del recurso, especificando el URI.

**Desbloquear el recurso**

Invoque el método del servicio Repositorio para desbloquear el recurso, especificando el URI.

**Consulte también**

[Bloqueo de recursos mediante la API de Java](aem-forms-repository.md#lock-resources-using-the-java-api)

[Bloqueo de recursos mediante la API de servicio web](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bloqueo de recursos mediante la API de Java {#lock-resources-using-the-java-api}

Bloqueo de recursos mediante la API de servicio del Repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique el URI del recurso que se va a bloquear

   Especifique el URI del recurso que se va a bloquear. En este caso, porque el recurso tiene el nombre `testResource` está en la carpeta denominada `testFolder`, su URI es `"/testFolder/testResource"`. El URI se almacena como un `java.lang.String` objeto.

1. Bloqueo del recurso

   Invocar el `ResourceRepositoryClient` del objeto `lockResource` y pase los siguientes parámetros:

   * URI del recurso.
   * El ámbito de bloqueo. En este ejemplo, dado que el recurso se bloqueará para uso exclusivo, el ámbito de bloqueo se especifica como `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE`.
   * La profundidad del bloqueo. En este ejemplo, dado que el bloqueo se aplicará solo al recurso en cuestión y a ninguno de sus miembros o elementos secundarios, la profundidad de bloqueo se especifica como `Lock.DEPTH_ZERO`.

   >[!NOTE]
   >
   >La versión sobrecargada de `lockResource` que requiere cuatro parámetros genera una excepción. Asegúrese de utilizar la variable `lockResource` que requiere tres parámetros, como se muestra en este tutorial.

1. Recuperar los bloqueos del recurso

   Invocar el `ResourceRepositoryClient` del objeto `getLocks` y pase el URI del recurso como parámetro. El método devuelve una lista de objetos Lock a través de la cual puede iterar. En este ejemplo, el propietario del bloqueo, la profundidad y el ámbito se imprimen para cada objeto invocando el objeto Lock `getOwnerUserId`, `getDepth`y `getType` métodos, respectivamente.

1. Desbloquear el recurso

   Invocar el `ResourceRepositoryClient` del objeto `unlockResource` y pase el URI del recurso como parámetro. Para obtener más información, consulte la [Referencia de la API de AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Consulte también**

[Bloqueo de recursos](aem-forms-repository.md#locking-resources)

[Inicio rápido (modo SOAP): Bloqueo de un recurso mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bloqueo de recursos mediante la API de servicio web {#lock-resources-using-the-web-service-api}

Bloqueo de recursos mediante la API de servicio del Repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL de repositorio con Base64.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especifique el URI del recurso que se va a bloquear

   Especifique una cadena que contenga el URI del recurso que se va a bloquear. En este caso, porque el recurso tiene el nombre `testResource` está en la carpeta `testFolder`, su URI es `"/testFolder/testResource"`. Cuando utilice un idioma compatible con Microsoft .NET Framework (por ejemplo, C#), almacene el URI en un `System.String` objeto.

1. Bloqueo del recurso

   Invocar el `RepositoryServiceService` del objeto `lockResource` y pase los siguientes parámetros:

   * URI del recurso.
   * El ámbito de bloqueo. En este ejemplo, dado que el recurso se bloqueará para uso exclusivo, el ámbito de bloqueo se especifica como `11`.
   * La profundidad del bloqueo. En este ejemplo, dado que el bloqueo se aplicará solo al recurso en cuestión y a ninguno de sus miembros o elementos secundarios, la profundidad de bloqueo se especifica como `2`.
   * Un `int` que indica el número de segundos hasta que caduca el bloqueo. En este ejemplo, el valor de `1000` se utiliza.
   * Pass `null` para el último parámetro.

1. Recuperar los bloqueos del recurso

   Invocar el `RepositoryServiceService` del objeto `getLocks` y pase el URI del recurso como el primer parámetro y `null` para el segundo parámetro. El método devuelve un valor `object` matriz que contiene `Lock` objetos a través de los cuales se puede iterar. En este ejemplo, el propietario del bloqueo, la profundidad y el ámbito se imprimen para cada objeto accediendo a cada uno de ellos `Lock` del objeto `ownerUserId`, `depth`y `type` , respectivamente.

1. Desbloquear el recurso

   Invocar el `RepositoryServiceService` del objeto `unlockResource` y pase el URI del recurso como el primer parámetro y `null` para el segundo parámetro.

**Consulte también**

[Bloqueo de recursos](aem-forms-repository.md#locking-resources)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Eliminación de recursos {#deleting-resources}

Puede eliminar recursos mediante programación desde una ubicación determinada del repositorio utilizando la API Java (SOAP) del servicio Repositorio.

Cuando elimina un recurso, la eliminación es normalmente permanente, aunque en algunos casos los repositorios ECM pueden almacenar las versiones del recurso según sus mecanismos de historial. Por lo tanto, al eliminar un recurso, es importante estar seguro de que no necesitará ese recurso de nuevo. Los motivos comunes para eliminar un recurso incluyen la necesidad de aumentar el espacio disponible en la base de datos. Puede eliminar una versión de un recurso, pero si lo hace, debe especificar el identificador del recurso y no su identificador lógico (LID) o ruta. Si elimina una carpeta, todo lo que haya en ella, incluidas las subcarpetas y los recursos, se eliminará automáticamente.

Los recursos relacionados no se eliminan. Por ejemplo, si tiene un formulario que utiliza el archivo logo.gif y elimina logo.gif, se almacenará una relación en la tabla de relación pendiente. Como alternativa, para la desaprobación de versiones, establezca el estado del objeto de la última versión en obsoleto.

Una operación de eliminación no es segura para las transacciones en sistemas ECM. Por ejemplo, si intenta eliminar 100 recursos y la operación falla en el recurso número 50, las primeras 49 instancias se eliminarán, pero el resto no. De lo contrario, el comportamiento predeterminado es rollback (sin compromiso).

>[!NOTE]
>
>Al usar la variable `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` con el repositorio ECM (Content Server de Documentum de EMC y IBM FileNet P8 Content Manager), la transacción no se revertirá si la eliminación falla en uno de los recursos especificados, lo que significa que los archivos que se han eliminado no se pueden eliminar.

>[!NOTE]
>
>Para obtener más información sobre el servicio Repositorio, consulte [Referencia de servicios para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumen de los pasos {#summary_of_steps-8}

Para eliminar un recurso, siga estos pasos:

1. Incluir archivos de proyecto.
1. Cree un cliente de servicio de Repositorio.
1. Especifique el URI del recurso que se va a eliminar.
1. Elimine el recurso.

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente mediante Java, incluya los archivos JAR necesarios. Si utiliza servicios web, incluya los archivos proxy.

**Crear el cliente de servicio**

Para poder leer un recurso mediante programación, debe establecer una conexión y proporcionar credenciales. Esto se logra creando un cliente de servicio.

**Especifique el URI del recurso que se va a eliminar**

Cree una cadena que contenga el URI del recurso que se va a eliminar. La sintaxis incluye barras diagonales, como en este ejemplo: &quot;/*ruta*/*recurso*&quot;. Si el recurso que se va a eliminar es una carpeta, la eliminación será recursiva.

**Eliminar el recurso**

Invoque el método del servicio Repositorio para eliminar el recurso, especificando el URI.

**Consulte también**

[Eliminación de recursos mediante la API de Java](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Eliminación de recursos mediante la API de servicio web](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Inicio rápido de la API del servicio de repositorio](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Eliminación de recursos mediante la API de Java (SOAP) {#delete-resources-using-the-java-api-soap}

Elimine un recurso mediante la API del repositorio (Java):

1. Incluir archivos de proyecto

   Incluya archivos JAR de cliente en la ruta de clase de su proyecto Java.

1. Crear el cliente de servicio

   Cree un `ResourceRepositoryClient` usando su constructor y pasando un `ServiceClientFactory` objeto que contiene propiedades de conexión.

1. Especifique el URI del recurso que se va a eliminar

   Especifique el URI del recurso que se va a recuperar. En este caso, como el recurso llamado testResourceToBeDeleted está en la carpeta testFolder, su URI es `/testFolder/testResourceToBeDeleted`. El URI se almacena como un `java.lang.String` objeto. En este ejemplo, el recurso se escribe primero en el repositorio y se recupera su URI. Para obtener más información sobre cómo escribir un recurso, consulte [Escribir recursos](aem-forms-repository.md#writing-resources).

1. Eliminar el recurso

   Invocar el `ResourceRepositoryClient` del objeto `deleteResource` y pase el URI del recurso como parámetro.

**Consulte también**

[Eliminación de recursos](aem-forms-repository.md#deleting-resources)

[Inicio rápido (modo SOAP): Búsqueda de recursos mediante la API de Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusión de archivos de biblioteca Java de AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuración de las propiedades de conexión](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eliminación de recursos mediante la API de servicio web {#delete-resources-using-the-web-service-api}

Elimine un recurso mediante la API del repositorio (servicio web):

1. Incluir archivos de proyecto

   * Cree un ensamblado de cliente Microsoft .NET que consuma el WSDL de repositorio con Base64.
   * Haga referencia al ensamblado del cliente Microsoft .NET.

1. Crear el cliente de servicio

   Con el ensamblado del cliente Microsoft .NET, cree un `RepositoryServiceService` invocando su constructor predeterminado. Establezca su `Credentials` propiedad usando una `System.Net.NetworkCredential` que contiene el nombre de usuario y la contraseña.

1. Especifique el URI del recurso que se va a eliminar

   Especifique el URI del recurso que se va a recuperar. En este caso, porque el recurso tiene el nombre `testResourceToBeDeleted` está en la carpeta denominada `testFolder`, su URI es `"/testFolder/testResourceToBeDeleted"`. En este ejemplo, el recurso se escribe primero en el repositorio y se recupera su URI. Para obtener más información sobre cómo escribir un recurso, consulte [Escribir recursos](aem-forms-repository.md#writing-resources).

1. Eliminar el recurso

   Invocar el `RepositoryServiceService` del objeto `deleteResources` método y pasar una `System.String` matriz que contiene el URI del recurso como el primer parámetro. Pass `null` para el segundo parámetro.

**Consulte también**

[Eliminación de recursos](aem-forms-repository.md#deleting-resources)

[Invocación de AEM Forms mediante la codificación Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
