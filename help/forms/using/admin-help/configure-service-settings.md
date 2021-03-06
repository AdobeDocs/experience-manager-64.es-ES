---
title: Configuración de los ajustes del servicio
seo-title: Configure service settings
description: Obtenga información sobre cómo configurar los ajustes del servicio.
seo-description: Learn how to configure service settings.
uuid: e95425a4-62f6-473e-b21b-d081c432e02d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2fab4b0c-e5db-47cd-b85a-4ff5ad6eb178
exl-id: be1f8c59-b5d8-4d87-af7b-1034d73e7e83
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '10683'
ht-degree: 0%

---

# Configuración de los ajustes del servicio {#configure-service-settings}

Puede utilizar la página Administración de servicios para configurar las opciones de cada uno de los servicios que forman parte de AEM formularios. La configuración disponible varía en función del servicio que se esté configurando.

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de servicios.
1. Detenga el servicio antes de cambiarlo. (Consulte [Inicio y parada de servicios](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services)).
1. Haga clic en el nombre del servicio que desea configurar.
1. Si el servicio tiene una pestaña Configuración , utilícela para cambiar la configuración del servicio. Consulte la lista de vínculos a continuación para obtener más información.

   >[!NOTE]
   >
   >No todos los servicios enumerados en la página Administración de servicios tienen una pestaña Configuración . Para los procesos que ha creado, la pestaña Configuración aparece únicamente si ha añadido un parámetro de configuración al proceso en Workbench. (Consulte &quot;Parámetros de configuración&quot; en * [Ayuda de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) ) *

1. Haga clic en la pestaña Security y establezca la configuración de seguridad del servicio. Consulte [Modificación de la configuración de seguridad de un servicio](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Si el servicio tiene una pestaña Endpoints , utilícela para cambiar la configuración del extremo. Consulte [Administración de puntos de conexión](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Haga clic en la ficha Agrupación y defina la configuración de agrupación. Consulte [Configuración del agrupamiento para un servicio](configure-service-settings.md#configuring-pooling-for-a-service).
1. Haga clic en Guardar para guardar los cambios o haga clic en Cancelar para descartarlos.
1. Seleccione la casilla de verificación situada junto al nombre del servicio y haga clic en Start para reiniciar el servicio.

## Configuración del servicio Flujo de trabajo de auditoría {#audit-workflow-service-settings}

Workbench proporciona la capacidad de registrar instancias de proceso tal y como se ejecutan durante la ejecución y, a continuación, reproducirlas para observar el comportamiento del proceso. (Consulte [Ayuda de Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)). Para conservar espacio en el sistema de archivos del servidor de formularios, puede limitar la cantidad de datos de registro de procesos almacenados. Puede configurar las siguientes propiedades del servicio Servicio de flujo de trabajo de auditoría ( `AuditWorkflowService`):

**maxNumberOfRecordingInstances:** el número máximo de grabaciones almacenadas. Cuando se almacena el número máximo, la grabación más antigua se elimina del sistema de archivos cuando se crea una nueva grabación. Esta propiedad es útil si tiende a crear muchas grabaciones y desea eliminar las grabaciones antiguas automáticamente. El valor predeterminado es 50.

**MaxNumberOfRecordingEntries:** el número máximo de entradas de datos que se pueden almacenar para cada grabación. Las entradas de datos son información sobre las operaciones en el proceso. Se almacenan varias entradas para cada ejecución de una operación, como si se inició la operación, si se completó la operación y si la ruta que lleva a la operación está completa. Esta propiedad es útil cuando los procesos pueden incluir muchas ejecuciones de operaciones, por ejemplo, cuando se encuentra un bucle sin fin. El valor predeterminado es 50.

## configuración del servicio de formularios con código de barras {#barcoded-forms-service-settings}

El servicio de códigos de barras `(BarcodedFormsService)` extrae datos de códigos de barras de imágenes digitalizadas. El servicio acepta un formulario con códigos de barras (TIFF o PDF) como entrada y extrae la representación automática de los datos codificados por el código de barras.

Los siguientes ajustes están disponibles para el servicio de formularios con códigos de barras.

**Leer a la izquierda:** cuando se selecciona, las imágenes de código de barras se analizan horizontalmente de derecha a izquierda.

**Leído a la derecha:** cuando se selecciona, las imágenes de código de barras se analizan horizontalmente de izquierda a derecha.

**Leer arriba:** cuando se selecciona, las imágenes de código de barras se analizan verticalmente de abajo a arriba.

**Leer hacia abajo:** cuando se selecciona, las imágenes de código de barras se analizan verticalmente de arriba a abajo.

>[!NOTE]
>
>De forma predeterminada, están seleccionadas todas las opciones. Anule la selección de una opción solo si está seguro de que no aparecen códigos de barras de ese modo en los formularios.

**Ruta del archivo base:** la ruta del archivo relativa a la cual se resuelven los parámetros del archivo de entrada y salida del lote para las operaciones Ejecutar trabajo de archivo XML y Ejecutar trabajo de archivo plano. En las configuraciones agrupadas, la ruta del archivo base debe ser una ubicación del sistema de archivos compartido a la que todos los nodos del clúster tengan acceso de lectura y escritura.

**Nombre de la fuente de datos:** el nombre de la fuente de datos que se utiliza para mantener la información de estado e historial sobre los trabajos de procesamiento por lotes. La fuente de datos especificada debe admitir transacciones globales (XA).

## Configuración del servicio Central Migration Bridge (obsoleto) {#central-migration-bridge-service-settings}

El servicio Puente de migración central ( `CentralMigrationBridge`) invoca un subconjunto de la funcionalidad Adobe Central Pro Output Server (Central), que incluye los comandos JFMERGE, JFTRANS y XMLIMPORT. Las operaciones del servicio Central Migration Bridge permiten reutilizar los siguientes activos de Central en AEM formularios:

* diseño de plantilla (&amp;ast;.ifd)
* plantillas de salida (&amp;ast;.mdf)
* archivos de datos (&amp;archivos ast;.dat)
* archivos de preámbulo (&amp;archivos ast;.pre)
* archivos de definición de datos (&amp;ast;.tdf)

La siguiente configuración está disponible para el servicio Central Migration Bridge.

**Directorio de instalación central:** directorio en el que está instalado Adobe Central 5.7.

## Content Repository Connector para la configuración de servicio de Documentum de EMC {#content-repository-connector-for-emc-documentum-service-settings}

El Content Repository Connector para el servicio Documentum de EMC ( `EMCDocumentumContentRepositoryConnector`) permite crear procesos que interactúan con contenido almacenado en un repositorio de Documentum.

La siguiente configuración está disponible para el conector de repositorio de contenido para el servicio Documentum de EMC.

**Ruta predeterminada del objeto Asset Link:** la parte predeterminada de la ruta en el repositorio de Documentum para almacenar el objeto Asset Link. La ruta real consiste en la ruta predeterminada y la ubicación de la plantilla de formulario en el repositorio de formularios AEM.

Por ejemplo, si la ruta de acceso predeterminada se establece en `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` y la plantilla de formulario se almacena en una carpeta `/Docbase/forms/`, el objeto Asset Link se almacena en la siguiente ubicación:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

El valor predeterminado de esta configuración es `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`.

## Content Repository Connector para la configuración de servicio de IBM FileNet {#content-repository-connector-for-ibm-filenet-service-settings}

Content Repository Connector para IBM FileNet permite crear procesos que interactúan con contenido almacenado en un repositorio de IBM FileNet.

La siguiente configuración está disponible para el conector del repositorio de contenido para el servicio IBM FileNet.

**Ruta predeterminada del objeto Asset Link:** la parte predeterminada de la ruta en el repositorio IBM FileNet para almacenar el objeto Asset Link. La ruta real consiste en la ruta predeterminada y la ubicación de la plantilla de formulario en el repositorio de formularios AEM.

Por ejemplo, si la ruta de acceso predeterminada se establece en `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` y la plantilla de formulario se almacena en una carpeta `/Docbase/forms/`, el objeto Asset Link se almacena en la siguiente ubicación:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

El valor predeterminado de esta configuración es `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`.

## Convertir configuración de servicio PDF {#convert-pdf-service-settings}

El servicio Convertir PDF ( `ConvertPdfService`) convierte los documentos PDF a PostScript y a varios formatos de imagen (JPEG, JPEG 2000, PNG y TIFF). La conversión de un documento PDF a PostScript es útil para la impresión desatendida basada en servidor en cualquier impresora PostScript. La conversión de un documento PDF en un archivo TIFF de varias páginas es práctica cuando se archivan documentos en sistemas de administración de contenido que no admiten documentos PDF.

Los siguientes ajustes están disponibles para el servicio Convertir PDF.

**Tipo de Transacción:** especifica cómo se debe propagar un contexto de transacción a una operación.

**Requerido:** admite un contexto de transacción si existe uno; de lo contrario, se crea un nuevo contexto de transacción. Este es el valor predeterminado.

**Requiere nuevo:** siempre crea un nuevo contexto de transacción. Si existe un contexto de transacción activo, se suspende.

**Tiempo de espera de transacción (en segundos):** El número de segundos que el proveedor de transacciones subyacente debe esperar antes de revertir una transacción que esté realizando esta operación. Este valor se ignorará si se propaga un contexto de transacción existente. El valor predeterminado es 180.

**Resolución de umbral para suavizado (en dpi):**  La resolución de imagen debajo de la cual se aplica suavizado (o suavizado) al texto, el arte lineal y las imágenes, si ha seleccionado las opciones &quot;Aplicar suavizado a&quot; para esos elementos.

**Aplicar suavizado al texto:** controla el suavizado del texto. Para desactivar el suavizado de texto y hacer que el texto sea más nítido y fácil de leer con un ampliador de pantalla, desactive esta casilla de verificación.

**Aplicar suavizado a LineArt:** aplica suavizado para eliminar ángulos abruptos en líneas.

**Aplicar suavizado a las imágenes:**  aplica suavizado para minimizar los cambios bruscos en las imágenes.

## Configuración del servicio de Distiller {#distiller-service-settings}

El servicio de Distiller ( `DistillerService`) convierte los archivos PostScript, Encapsulated PostScript (EPS) y PRN a archivos PDF a través de una red.

Los siguientes ajustes están disponibles para el servicio Distiller.

**Configuración de Adobe PDF:** se aplican los siguientes ajustes preconfigurados al PDF generado:

* Impresión de alta calidad
* Páginas de gran tamaño
* PDFA1b CMYK 2005
* PDFA1b RGB 2005
* PDFX1a 2001
* PDFX3 2002
* Calidad de prensa
* Tamaño de archivo más pequeño
* Estándar

Se pueden crear nuevas configuraciones a través de la interfaz de usuario de PDF Generator.

**Configuración de seguridad:** configuración de seguridad preconfigurada que se aplica a documentos PDF generados. El valor predeterminado es Sin seguridad. Debe crear la configuración de seguridad mediante el Generador de PDF y, a continuación, introducir la configuración aquí.

**Tamaño del grupo:** El tamaño inicial del grupo. Cuando se implementa el servicio Distiller, este número se utiliza para determinar el número de instancias de implementación de servicio que se crean y asignan al grupo gratuito que espera solicitudes de invocación. El contenedor de servicio puede responder inmediatamente a las solicitudes de invocación sin tener que inicializar primero una instancia de servicio.

## Configuración del servicio de Gestión de documentos {#document-management-service-settings}

>[!NOTE]
>
>Adobe® Content Services ES (obsoleto) es un sistema de administración de contenido instalado con LiveCycle. Permite a los usuarios diseñar, administrar, monitorear y optimizar procesos centrados en el ser humano. La compatibilidad con los servicios de contenido (obsoletos) finaliza el 31/12/2014. Consulte [documento del ciclo vital del producto de Adobe](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).

El servicio de Administración de documentos ( `DocumentManagementService`) permite que los procesos utilicen la funcionalidad de administración de contenido que proporcionan los servicios de contenido (obsoleto). Las operaciones de gestión de documentos proporcionan tareas básicas necesarias para mantener espacios y contenido en el sistema de administración de contenido. Algunos ejemplos de estas tareas son copiar, eliminar, mover, recuperar y almacenar contenido, crear espacios y asociaciones, y obtener y establecer atributos de contenido.

Los siguientes ajustes están disponibles para el servicio de gestión de documentos.

**Esquema de tienda:** el esquema del almacén en el que se encuentra el contenido. El valor predeterminado es workspace.

**Puerto HTTP:** puerto utilizado para acceder a los servicios de contenido (obsoleto). El valor predeterminado es 8080.

## Configuración del servicio de correo electrónico {#email-service-settings}

El correo electrónico se utiliza normalmente para distribuir contenido o proporcionar información de estado como parte de un proceso automatizado. El servicio de correo electrónico ( `EmailService`) permite que los procesos reciban mensajes de correo electrónico de un servidor POP3 o IMAP y que envíen mensajes de correo electrónico a un servidor SMTP.

Por ejemplo, un proceso utiliza el servicio de correo electrónico para enviar un mensaje de correo electrónico con un archivo adjunto de formulario PDF. El servicio de correo electrónico se conecta a un servidor SMTP para enviar el mensaje de correo electrónico con el archivo adjunto. El formulario PDF está diseñado para permitir que el destinatario haga clic en Enviar después de completar el formulario. La acción hace que el formulario se devuelva como archivo adjunto al servidor de correo electrónico designado. El servicio de correo electrónico recupera el mensaje de correo electrónico devuelto y almacena el formulario completado en una variable de formulario de datos de proceso.

Las siguientes configuraciones están disponibles para el servicio de correo electrónico.

**Host SMTP:** la dirección IP o URL del servidor SMTP que se va a utilizar para enviar correo electrónico.

**Número de puerto SMTP:** puerto utilizado para conectarse al servidor SMTP.

**Autenticar SMTP:** seleccione si se requiere autenticación de usuario para conectarse al servidor SMTP.

**Usuario SMTP:** el nombre de usuario de la cuenta de usuario que se utiliza para iniciar sesión en el servidor SMTP.

**Contraseña SMTP:** la contraseña asociada a la cuenta de usuario SMTP.

**Seguridad de transporte SMTP:** el protocolo de seguridad que se utiliza para conectar con el servidor SMTP:

* Seleccione Ninguno si no se utiliza ningún protocolo (los datos se envían en texto sin formato)
* Seleccione SSL si se utiliza el protocolo Secure Sockets Layer.
* Seleccione TLS si se utiliza la Seguridad de capa de transporte.

**Host POP3/IMAP:** la dirección IP o URL del servidor POP3 o IMAP que se utilizará para enviar correo electrónico.

**Nombre de usuario POP3/IMAP:** el nombre de usuario de la cuenta de usuario que se utilizará para iniciar sesión en el servidor POP3 o IMAP.

**Contraseña POP3/IMAP:** la contraseña asociada a la cuenta de usuario POP3 o IMAP.

**Número de puerto POP3/IMAP:** el puerto utilizado para conectarse al servidor POP3 o IMAP.

**POP3/IMAP:** el protocolo que se utiliza para enviar y recibir correos electrónicos.

**Recibir seguridad de transporte:**  el protocolo de seguridad que se utiliza para conectarse al servidor SMTP:

* Seleccione Ninguno si no se utiliza ningún protocolo (los datos se envían en texto sin formato).
* Seleccione SSL si se utiliza el protocolo Secure Sockets Layer.
* Seleccione TLS si se utiliza la Seguridad de capa de transporte.

## Configuración del servicio de cifrado {#encryption-service-settings}

El servicio Encryption ( `EncryptionService`) permite cifrar y descifrar documentos. Cuando se cifra un documento, su contenido se vuelve ilegible. Un usuario autorizado puede descifrar el documento para obtener acceso al contenido. Si un documento PDF está cifrado con una contraseña, el usuario debe especificar la contraseña de apertura antes de que el documento se pueda ver en Adobe Reader o Adobe Acrobat. Del mismo modo, si un documento PDF está cifrado con un certificado, el usuario debe descifrar el documento PDF con la clave pública correspondiente al certificado (clave privada) que se utilizó para codificar el documento PDF.

Las siguientes configuraciones están disponibles para el servicio de cifrado.

**Servidor LDAP predeterminado al que conectarse:** Nombre de host del servidor LDAP utilizado para recuperar certificados para el cifrado de documentos.

**Puerto LDAP predeterminado al que conectarse:** Número de puerto del servidor LDAP.

**Nombre de usuario LDAP predeterminado:** si el servidor LDAP requiere autenticación, especifique el nombre de usuario que se utilizará para conectar con el servidor LDAP.

**Contraseña LDAP predeterminada:** si el servidor LDAP requiere autenticación, especifique la contraseña que corresponde al nombre de usuario que se utilizará para conectar con el servidor LDAP.

>[!NOTE]
>
>Utilice la autenticación simple (nombre de usuario y contraseña) solo cuando la conexión esté protegida mediante SSL (mediante LDAPS).

**Modo de compatibilidad:**

## Configuración del servicio FTP {#ftp-service-settings}

El servicio FTP ( `FTP`) permite que los procesos interactúen con un servidor FTP. Las operaciones del servicio FTP pueden recuperar archivos del servidor FTP, colocarlos en el servidor FTP y eliminar archivos del servidor FTP. Por ejemplo, los documentos, como los informes generados a partir de un proceso, se pueden almacenar en un servidor FTP para su distribución. O un sistema externo puede generar algunos archivos basados en pasos anteriores de un proceso. En un paso posterior del proceso, los archivos pueden transferirse a una ubicación remota.

El servicio FTP cuenta con las siguientes opciones de configuración:

**Host predeterminado:** la dirección IP o la dirección URL del servidor FTP.

**Puerto predeterminado:** puerto utilizado para conectarse al servidor FTP. El valor predeterminado es 21.

**Nombre de usuario predeterminado:** el nombre de la cuenta de usuario que puede utilizar para acceder al servidor FTP. La cuenta de usuario debe tener suficientes privilegios para realizar las operaciones de FTP que requiere este servicio.

**Contraseña predeterminada:** la contraseña que se debe utilizar con el nombre de usuario especificado para la autenticación con el servidor FTP.

## Generar configuración del servicio PDF {#generate-pdf-service-settings}

El servicio Generate PDF ( `GeneratePDFService`) convierte los archivos en varios formatos nativos en documentos PDF y convierte los documentos PDF en una serie de formatos de archivo.

Los siguientes ajustes están disponibles para el servicio Generate PDF.

**Configuración de Adobe PDF:** el nombre de la configuración preconfigurada de Adobe PDF que se aplicará a un trabajo de conversión si esta configuración no se especifica como parte de los parámetros de invocación de API. La configuración de Adobe PDF se configura en la consola de administración haciendo clic en Servicios > Generador de PDF > Configuración de Adobe PDF. Estos ajustes solo se aplican a las conversiones basadas en PDFMaker.

**Configuración de seguridad:** el nombre de la configuración de seguridad preconfigurada que se aplicará a un trabajo de conversión si esta configuración no se especifica como parte de los parámetros de invocación de API. La configuración de seguridad se configura en la consola de administración haciendo clic en Servicios > Generador de PDF > Configuración de seguridad.

**Configuración del tipo de archivo:** el nombre de la configuración preconfigurada de tipo de archivo que se aplicará a un trabajo de conversión si esta configuración no se especifica como parte de los parámetros de invocación de API. La configuración del tipo de archivo se configura en la consola de administración haciendo clic en Servicios > Generador de PDF > Configuración del tipo de archivo.

**Usar Acrobat WebCapture (solo Windows):** cuando esta configuración es verdadera, el servicio Generate PDF utiliza Acrobat X Pro para todas las conversiones de HTML a PDF. Esto puede mejorar la calidad de los archivos PDF producidos a partir de HTML, aunque el rendimiento puede ser ligeramente inferior. El valor predeterminado es false.

**Utilizar la conversión de imágenes de Acrobat (solo Windows):** cuando esta configuración es verdadera, el servicio Generar PDF utiliza Acrobat X Pro para todas las conversiones de imagen a PDF. Esta configuración solo es útil si el mecanismo de conversión de Java puro predeterminado no puede convertir correctamente una proporción significativa de las imágenes de entrada. El valor predeterminado es false.

**Habilitar conversiones de AutoCAD basadas en Acrobat (solo Windows):**  Cuando esta configuración es verdadera, el servicio Generate PDF utiliza Acrobat X Pro para todas las conversiones de DWG a PDF. Esta configuración solo es útil si AutoCAD no está instalado en el servidor o si el mecanismo de conversión de AutoCAD no puede convertir archivos correctamente.

**Expresiones regulares para averiguar los caracteres especiales prohibidos en el nombre de usuario (solo Windows):** especifica los caracteres que interfieren con las operaciones del Export PDF y del Optimize PDF cuando los caracteres aparecen en el nombre de un usuario.

**ImageToPDF Pool Size:** el tamaño del grupo del conversor predeterminado (Java puro) de imagen a PDF en el servicio Generate PDF. Esta configuración controla el máximo de conversiones simultáneas de imagen a PDF que puede realizar el servicio Generate PDF. El valor predeterminado de esta configuración (recomendado para sistemas de un solo procesador) es 3, que puede aumentar en sistemas de varios procesadores.

**Tamaño del grupo de archivos HTML a PDF:** El tamaño del grupo del conversor de HTML a PDF en el servicio Generate PDF. Esta configuración controla el máximo de conversiones simultáneas de HTML a PDF que puede realizar el servicio Generate PDF. El valor predeterminado de esta configuración (recomendado para sistemas de un solo procesador) es 3, que puede aumentar en sistemas de varios procesadores.

**Tamaño de grupo OCR:** el tamaño de grupo del PaperCaptureService que PDF Generator utiliza para OCR. El valor predeterminado de esta configuración (recomendado para sistemas de un solo procesador) es 3, que puede aumentar en sistemas de varios procesadores. Esta configuración solo es válida en sistemas Windows.

**Familia de fuentes alternativa para conversiones HTML a PDF:**  el nombre de la familia de fuentes que se utilizará en documentos PDF cuando la fuente utilizada en el HTML original no esté disponible para el servidor de formularios AEM. Especifique una familia de fuentes si espera convertir páginas HTML que utilicen fuentes no disponibles. Por ejemplo, las páginas creadas en idiomas regionales podrían utilizar fuentes no disponibles.

**Lógica de reintento para** conversiones nativasGobierna los reintentos de generación de PDF si ha fallado el primer intento de conversión:

**No hay reintento**

No vuelva a intentar la conversión de PDF si ha fallado el primer intento de conversión

**Reintentar**

Vuelva a intentar la conversión de PDF independientemente de si se ha alcanzado el umbral de tiempo de espera. La duración de tiempo de espera predeterminada para el primer intento es de 270 segundos.

**Vuelva a intentar si el tiempo lo permite**

Vuelva a intentar la conversión de PDF si el tiempo consumido para el primer intento de conversión fue menor que la duración del tiempo de espera especificada. Por ejemplo, si la duración del tiempo de espera es de 270 y el primer intento consumía 200, PDF Generator volverá a probar la conversión. Si el primer intento consumía 270, la conversión no se volverá a intentar.

## Guías ES4 Ajustes del servicio de utilidades {#guides-es4-utilities-service-settings}

Al crear una guía, algunos recursos, como la definición de la guía, se incrustan en ella. Los recursos también pueden existir como referencias a recursos de aplicación almacenados localmente o en el servidor de AEM forms. La Guía no contiene datos y los valores de la ubicación de envío y las entradas no son adecuados para todos los entornos externos.

En la mayoría de los casos, los servicios de renderización de guías predeterminados son suficientes para preparar una guía para su uso en Workspace u otros entornos externos. (En la vista Servicios, en Workbench, el servicio predeterminado es Guías (sistema)/Procesos/Guía de procesamiento - 1.0). El servicio Guide Utilities ( `GuidesUtility`) le permite crear un proceso personalizado para procesar una guía, si es necesario.

Las operaciones de Guide Utilities permiten añadir las siguientes tareas de representación de la guía a un proceso:

* Determinar si hay datos disponibles para rellenar la guía con
* Incrustar los datos de la guía o convertirlos en un vínculo
* Conversión de contenido referenciado en direcciones URL a las que se puede acceder desde fuera
* Sustituir valores en un documento HTML u otro envoltorio, o convertirlos en direcciones URL a las que se pueda acceder externamente
* Definir la ubicación de envío
* Especificar valores de entrada
* Crear un parámetro para representar el contenido al que se hace referencia
* Si hay variaciones disponibles, establezca una variación

Los valores predeterminados del servicio Guide Utilities admiten la mayoría de los casos de uso. Sin embargo, si es necesario, puede cambiar los siguientes valores.

**publicPaths:** esta opción está en desuso. No utilice esta opción con AEM formularios.

**pathInfoExpiryInSeconds:** El intervalo después del cual caduca una solicitud de información de ruta de un cliente. El valor predeterminado es 1.

**colateralExpiryInSeconds:** intervalo tras el cual caduca una solicitud de colateral de un cliente. El valor predeterminado es 315576000.

**dismatchExpiryInSeconds:** El intervalo después del cual caduca una solicitud de material colateral de un cliente, cuando la etiqueta eTag (etiqueta de entidad) no coincide. (Una eTag es un encabezado de respuesta HTTP). El valor predeterminado es 1.

**guideContext:** la raíz de contexto de la aplicación web Guides. Coincide con el valor establecido mediante la aplicación web Guías. El valor predeterminado es /Guías/.

**secureRandomAlgorithm:** El algoritmo que se utilizará al generar claves e identificadores. Este valor se pasa al método getInstance de la clase Java SecureRandom. El valor predeterminado es SHA1PRNG.

**idBytes:** el número de bytes aleatorios que se utilizarán para un identificador de clave. El valor predeterminado es 6.

**macAlgorithm:** el algoritmo MAC (código de autenticación de mensajes) que se utilizará para la verificación de URL colateral. Este método se pasa al método getInstance de la clase Mac. El valor predeterminado es HmacSHA1.

**macRefreshIntervalInMinutes:** Cantidad de tiempo que una clave está activa. Cuando se ha activado una clave para este intervalo, se genera una nueva clave. La nueva clave se convierte en la clave activa. La clave activa anteriormente se conserva durante el 10% del intervalo de actualización. Este comportamiento permite que las direcciones URL que se generan utilizando la clave antigua sigan funcionando en el conmutador de claves. El valor predeterminado es 144000.

**macOverapIntervalInMinutes:** El tiempo que la clave anterior seguirá siendo válida después de que se genere una nueva. El valor predeterminado es 1440 minutos (1 día).

**macKeySeed:** un valor semilla para generar la dirección URL segura. Cuando esta es una opción, la clave nunca se actualiza. Si se configura la misma semilla en diferentes servidores, los servidores generarán direcciones URL seguras compatibles. Esto puede resultar útil si se utilizan varios servidores de formularios detrás de un equilibrador de carga. Introduzca una secuencia aleatoria de caracteres y números como semilla.

### Uso de guías en un clúster de servidores {#using-guides-in-a-server-cluster}

La renderización de una guía en un clúster de servidores que no utiliza sesiones adhesivas falla con una NullPointerException. Una solicitud de guías aprovecha las direcciones URL seguras que, de forma predeterminada, son únicas para el servidor en el que se generan. En un clúster que utiliza sesiones adhesivas, después de que una solicitud llegue a un nodo del clúster, todas las solicitudes posteriores para esa sesión o usuario se dirigen exclusivamente a ese servidor y todo está bien. En un clúster que no utiliza sesiones duraderas, las solicitudes posteriores pueden visitar cualquier servidor del clúster. Si el servidor al que llegan las solicitudes no es el servidor original, no resuelven la URL segura.

Si utiliza guías en un clúster de servidores que no utiliza sesiones adhesivas, establezca el valor macKeySeed para el servicio GuidesUtility y, a continuación, detenga e inicie el clúster.

El valor macKeySeed es la semilla del generador de números aleatorios que se utiliza para generar las direcciones URL seguras. Si establece este valor, cada nodo del clúster inicializará el generador de números aleatorios de la misma manera y tendrá acceso a las mismas direcciones URL seguras. Puede utilizar cualquier cadena aleatoria para este valor semilla.

Cambie el valor macKeySeed cuando necesite actualizar las direcciones URL seguras. La actualización de las direcciones URL seguras depende de la política de seguridad y es similar a la política de actualización para cambiar la contraseña raíz maestra del servidor. macSeedValue es análogo a la contraseña maestra para las direcciones URL seguras, ya que se utiliza para generar un nuevo número aleatorio único para su uso en la generación y recuperación de direcciones URL seguras.

Debe reiniciar el clúster porque macSeedValue es de solo lectura al iniciar el sistema. Todos los nodos deben reiniciarse para leer el valor, ya que lo utilizan de forma independiente para inicializar sus números aleatorios internos con el valor semilla.

## Configuración del servicio JDBC {#jdbc-service-settings}

El servicio JDBC ( `JdbcService`) permite que los procesos interactúen con las bases de datos.

La siguiente configuración está disponible para el servicio JDBC.

**datasourceName:**  valor de cadena que representa el nombre JNDI del origen de datos que se utilizará para conectar con el servidor de base de datos. El origen de datos debe definirse en el servidor de aplicaciones que aloja el servidor de formularios. El valor predeterminado es el nombre JNDI del origen de datos para la base de datos de AEM forms.

## Configuración del servicio JMS {#jms-service-settings}

El servicio JMS ( `JMS`) permite la interacción con los proveedores de sistemas de mensajería Java (JMS) que implementan tanto la mensajería punto a punto como la mensajería de publicación/suscripción.

Configure el servicio JMS con propiedades predeterminadas para que las operaciones de servicio puedan conectarse e interactuar con un proveedor JMS y un servicio JNDI asociado. Los valores de las propiedades del servicio se establecen en valores predeterminados basados en el servidor de aplicaciones JBoss. Cambie estos valores si utiliza un servidor de aplicaciones diferente para alojar AEM formularios.

Los siguientes ajustes están disponibles para el servicio JMS.

**URL del proveedor:** URL del proveedor de servicios JNDI. El valor predeterminado se basa en el servidor de aplicaciones JBoss. Las siguientes direcciones URL son valores predeterminados para los servidores de aplicaciones que admite AEM formularios:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**Nombre de usuario de JNDI:** el nombre de usuario de la cuenta que se utiliza para la autenticación con el proveedor de servicios de JNDI que se utiliza para buscar nombres de temas y de colas. El valor predeterminado es invitado.

**Contraseña JNDI:** la contraseña asociada al nombre de usuario especificado para el nombre de usuario JNDI. El valor predeterminado es invitado.

**Factoría de contexto inicial:** la clase Java que se utilizará como fábrica de contexto inicial. El servicio JMS utiliza esta clase para crear un contexto inicial, que es el punto de partida para resolver nombres de temas y colas. El valor predeterminado es la fábrica de contexto inicial para el servicio JMS en JBoss. Las siguientes clases son las fábricas de contexto iniciales para los servidores de aplicaciones que admite AEM formularios:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**WebLogic:** weblogic.jndi.WLInitialContextFactory

**WebSphere:** com.ibm.websphere.naming.WsnInitialContextFactory

**Nombre de usuario de conexión:**  la contraseña asociada al nombre de usuario especificado para Nombre de usuario de conexión. El valor predeterminado es invitado.

**Contraseña de conexión:** la contraseña asociada al nombre de usuario especificado para Nombre de usuario de conexión. El valor predeterminado es invitado.

**Otras propiedades:** Pares de nombre y valor de propiedad que puede pasar al proveedor de servicios JNDI. Estas propiedades dependen de la implementación y configuración del proveedor que esté utilizando.

Los pares de nombre y valor de la propiedad están separados por punto y coma **;**. Por ejemplo, el siguiente texto muestra el valor que se especificaría para dos propiedades denominadas name1 y name2, con valores value1 y value2, respectivamente:

`name1=value1;name2=value2`

## Configuración del servicio LDAP {#ldap-service-settings}

El servicio LDAP ( `LDAPService`) proporciona operaciones para consultar directorios LDAP. Los directorios LDAP generalmente se utilizan para almacenar información sobre las personas, los grupos y los servicios de una organización.

Los siguientes ajustes están disponibles para el servicio LDAP.

**Factoría de contexto inicial:**  la clase Java que se utilizará como fábrica de contexto. Esta clase se utiliza para crear una conexión con el servidor LDAP. El valor predeterminado es com.sun.jndi.ldap.LdapCtxFactory, que es apropiado para la mayoría de los servidores LDAP.

**URL del proveedor:** la URL que se utiliza para conectar con el servicio LDAP. El formato del valor es `ldap://server name:port`

*nombre del* servidor es el nombre del equipo que aloja el servidor LDAP

** representa el puerto de comunicaciones que utiliza el servicio LDAP. El valor predeterminado es 389, que es el puerto estándar utilizado para conexiones LDAP.

**Nombre de usuario:** el nombre de usuario de la cuenta de usuario que se utiliza para iniciar sesión en el servidor LDAP. La cuenta de usuario debe tener permiso para conectarse al servidor y leer la información en el directorio LDAP.

Según el servidor LDAP, el nombre de usuario podría ser un nombre de usuario sencillo como `myname` o un DN, como `cn=myname,cn=users,dc=myorg`.

**Contraseña:** la contraseña que corresponde al nombre de usuario proporcionado para la configuración Nombre de usuario.

**Otras propiedades:** un valor de cadena que representa otras propiedades y sus valores correspondientes que puede proporcionar al servidor LDAP. El valor tiene el formato siguiente:

`property=value;property=value;...`

## Configuración del servicio de configuración de Microsoft SharePoint {#microsoft-sharepoint-configuration-service-settings}

El servicio de configuración de Microsoft SharePoint `(MSSharePointConfigService)`permite especificar credenciales para el usuario de formularios AEM que tiene permisos de suplantación. Para obtener información sobre los permisos de suplantación, consulte [Configuración del conector para Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html).

Los siguientes ajustes están disponibles para el servicio de configuración de Microsoft SharePoint:

* Nombre de usuario de un usuario con permisos de suplantación
* Contraseña del usuario anterior

**Habilitar SSL (HTTPS):**

**Tiempo de vida:** tiempo, en segundos, que este perfil de aprovisionamiento es válido y almacenado en caché en el cliente. El valor predeterminado es 86400 (24 horas). Cuando una aplicación cliente se sincroniza con el servidor y ha transcurrido la cantidad de tiempo especificada, la aplicación cliente solicita un nuevo perfil de aprovisionamiento del servidor.

**Cifrado:** especifica si se cifrarán los datos almacenados en el dispositivo móvil.

**Aplicación Forms:** activa la función Forms en las aplicaciones cliente móviles. Cuando se selecciona esta opción, los usuarios pueden abrir formularios e iniciar procesos desde sus dispositivos móviles.

**Aplicación Tareas:** activa la función Tareas en las aplicaciones cliente móviles. Cuando se selecciona esta opción, los usuarios pueden acceder a sus listas de tareas y completar tareas desde sus dispositivos móviles.

**Aplicación de servicios de contenido:** activa la función Servicios de contenido en la aplicación cliente móvil. Esta función solo está disponible para iOS. Cuando se selecciona esta opción, los usuarios de iPhone y iPad pueden acceder a los archivos almacenados en el servidor WebDAV de su organización.

**Compatibilidad sin conexión:** permite a los usuarios continuar utilizando las aplicaciones cliente móviles incluso cuando no tienen conexión con el servidor (por ejemplo, cuando están fuera del rango de celdas o en modo avión). Los usuarios también deben habilitar la configuración Compatibilidad con sin conexión en sus dispositivos móviles. Esta función está disponible para dispositivos Android e iOS. De forma predeterminada, esta función está desactivada.

>[!NOTE]
>
>Si la compatibilidad con sin conexión se ha habilitado y, a continuación, la desactiva, los perfiles de aprovisionamiento de los usuarios se actualizan inmediatamente o en cuanto están en línea. Si un usuario ha estado trabajando sin conexión, todas las tareas pendientes se devuelven a su lista Tareas y todos los elementos de su cola, incluidos los formularios pendientes, las tareas y los formularios que contengan errores de validación, se eliminan de la cola.

**Android:** permite que los dispositivos Android se conecten al servidor.

**Apple iOS:** permite que los iPhone y los iPad se conecten al servidor.

**AIR:** permite que los dispositivos que ejecutan aplicaciones basadas en Adobe AIR® se conecten al servidor.

**BlackBerry:** permite que los dispositivos BlackBerry se conecten al servidor.

**Se requiere Android Microsoft Exchange ActiveSync:** especifica si el administrador de directivas (EA) de Microsoft Exchange ActiveSync debe estar instalado y activo en dispositivos Android. Cuando se selecciona esta opción, EA debe aplicarse en el dispositivo Android. Cuando esta opción no está seleccionada, no se realiza ninguna comprobación, aunque se siguen aplicando otros requisitos.

**Longitud mínima del PIN de Android:** los dispositivos Android deben tener una configuración global que obligue a que el PIN o la contraseña tengan al menos esta longitud. No basta con tener un PIN de la longitud especificada. El sistema debe aplicar la longitud del PIN para que los usuarios no puedan quitarlo ni acortarlo más tarde. El valor predeterminado es 4.

**Reintentos de contraseña máxima de Android antes del borrado:** los dispositivos Android tienen una configuración global que borra el sistema después de un número especificado de intentos de contraseña no válidos. Esta configuración global está habilitada y es igual o menor que el valor especificado aquí. El valor predeterminado es 5.

**Eliminación de borrado de Android:** especifica lo que sucede cuando se produce una infracción de directiva en un dispositivo Android. Cuando se selecciona esta opción, se elimina la cuenta. Cuando no se selecciona esta opción, se eliminan la contraseña de la cuenta almacenada y los datos almacenados en caché. No se realizan más intentos de sincronización hasta que el usuario corrija la infracción de directiva.

## Configuración del servicio de salida {#output-service-settings}

El servicio Output `(OutputService)`permite combinar los datos de formulario XML con un diseño de formulario creado en AEM Designer de formularios para crear una secuencia de salida de documento en uno de los siguientes formatos:

* Flujo de salida de documento PDF o PDF/A.
* Flujo de salida de Adobe PostScript.
* Flujo de salida de Printer Control Language (PCL).
* Flujo de salida de Zebra Programming Language (ZPL).

El flujo de salida se puede enviar a una impresora de red, una impresora local o un archivo de disco. Cuando se utiliza el servicio Output como parte de un proceso, también se puede enviar el flujo de salida a un destinatario de correo electrónico como archivo adjunto.

Los siguientes ajustes están disponibles para el servicio Output .

**Tipo de transacción:** especifica cómo se debe propagar un contexto de transacción a una operación:

**Requerido:** admite un contexto de transacción si ya existe uno; de lo contrario, se crea un nuevo contexto de transacción. Este es el valor predeterminado.

**Requiere nuevo:** siempre crea un nuevo contexto de transacción. Si existe un contexto de transacción activo, se suspende.

**Tiempo de espera de la transacción (en segundos):** El número de segundos que el proveedor de transacciones subyacente espera antes de revertir una transacción que ajusta esta operación. Este valor se ignora si se propaga un contexto de transacción existente.

Cuando se procesan archivos de datos de gran tamaño o funcionan en un servidor ocupado, puede ser necesario aumentar el tiempo de espera del servicio de salida. Para cambiar el valor de tiempo de espera, asegúrese de que los servidores de hardware tengan memoria adecuada y de que la memoria esté disponible en la pila de Java Application Server. El valor predeterminado es `180`.

## Configuración del servicio PDFG {#pdfg-config-service-settings}

Los siguientes ajustes están disponibles para el servicio de configuración PDFG ( `PDFGConfigService`).

**Directorio de opciones de trabajo del usuario:** la ruta de la carpeta del sistema de archivos donde el servicio c escribe los archivos de opciones de trabajo a los que puede acceder Acrobat Pro Extended. El valor predeterminado es [user.home]/Application Data/Adobe/Adobe PDF/Settings.

**Directorio de inicio de PS:**  la ruta de la carpeta del sistema de archivos donde se guardan los archivos de inicio requeridos por Adobe Acrobat Distiller. El valor predeterminado es [user.home]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**Archivo de inicio PS:** el nombre del archivo de inicio requerido por Adobe Acrobat Distiller. El valor predeterminado es example.ps.

**Tiempo de espera de conversión del servidor:** el tiempo de espera máximo de conversión del trabajo (en segundos) para el servicio Generate PDF y el servicio Distiller. Esta configuración limita el tiempo de espera máximo de conversión que se puede especificar en el archivo config.xml y en las páginas de la consola de administración para PDF Generator. El valor predeterminado es 270.

**Tiempo de espera global del servidor:** al realizar conversiones de PDF, un servidor de formularios tiene en cuenta el límite de tiempo de espera. Configure el valor de tiempo de espera para resolver el problema.

**Prefijo de opciones de trabajo:** Prefijo utilizado por el servicio Generar PDF para anteponer una cadena corta a los archivos de opciones de trabajo que crea temporalmente para que Acrobat Distiller los use. El valor predeterminado es pdfg.

**Aplicaciones no Unicode:** una lista de nombres de aplicaciones separados por comas que se sabe que no admiten Unicode. Esta lista está previamente rellenada con los nombres de varias aplicaciones, cuya compatibilidad está preconfigurada en PDF Generator. Si decide añadir compatibilidad con conversiones de PDF a través de otras aplicaciones de terceros que no sean compatibles con Unicode, debe agregarlas a esta lista. El valor predeterminado es Autocad,Excel,PowerPoint,Project,Publisher,Visio,Word,WordPerfect.

**Recuento de grupos de subprocesos del servidor:** controla el tamaño del grupo de subprocesos que utiliza el servicio Generar PDF internamente para atender las solicitudes de conversión de HTML a PDF que implican araña (conversión de páginas vinculadas accesibles desde la página principal). El valor predeterminado es 20.

**Segundos del análisis de limpieza PDFG:** consulte la sección Segundos de caducidad del trabajo para obtener más información.

**Segundos de caducidad del trabajo:** el servicio Generate PDF elimina los archivos de entrada en cuanto se convierten. Almacena los archivos de salida temporalmente durante un periodo determinado por los segundos del análisis de limpieza PDFG y los segundos de caducidad del trabajo.

La configuración Segundos de caducidad del trabajo especifica la antigüedad de un archivo o carpeta vacía antes de poder eliminarlo. La configuración de segundos de análisis de limpieza PDFG especifica la frecuencia con la que un subproceso de limpieza busca en las carpetas temporales archivos que se pueden eliminar.

Por ejemplo, si los segundos de caducidad del trabajo se establecen en 100 y los segundos del análisis de limpieza del PDFG se establecen en 200, el subproceso de limpieza se ejecuta cada 200 segundos y elimina los archivos que tengan 100 segundos o más.

El valor predeterminado de segundos del análisis de limpieza PDFG es `43200` (12 horas). El valor predeterminado de segundos de caducidad del trabajo es `86400` (24 horas).

**Configuración regional predeterminada:** se utiliza para anular la configuración regional predeterminada (país + idioma) del servidor en el que se implementa el servicio Generate PDF. Si no se especifica este parámetro, la configuración regional predeterminada se determina a partir del sistema operativo en el que se implementa el servicio. Este parámetro controla el idioma en el que se devuelven los mensajes de error a las API.

## flujo de trabajo de formularios Configuración del servicio de servicios de datos {#forms-workflow-data-services-service-settings}

Los siguientes servicios amplían los servicios de datos y exponen ensambladores que Workspace utiliza para hablar con el servidor. No cambie las opciones de configuración de estos servicios a menos que se le indique que lo haga por Adobe Support. Estos servicios no están destinados al acceso directo:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Configuración del servicio remoto {#remoting-service-settings}

La mayoría de los servicios están configurados de modo que pueda acceder a ellos a través de (obsoleto para AEM formularios) AEM Forms Remoting. Para obtener información sobre (obsoleto para formularios AEM) AEM Remoting de formularios, consulte [Programación con formularios AEM](https://adobe.com/go/learn_aemforms_programming_63).

Los siguientes ajustes están disponibles para el servicio Remoting.

**Método de autenticación del cliente de Flex:** determina el tipo de respuesta que el servidor envía al cliente cuando el servicio invocado está habilitado para la seguridad, la operación invocada no admite invocaciones anónimas y el cliente pasa credenciales no válidas o no válidas. Elija entre Personalizado o Básico. El valor predeterminado es Básico.

**Permitir serialización de clases no serializables:** la mayoría de los extremos de formularios AEM permiten utilizar solo clases serializables para la invocación. En versiones anteriores, el extremo Remoting permitía que se usaran clases no serializables para la invocación de clientes basados en Flex. Para evitar una vulnerabilidad de seguridad descrita en APS11-15, esto cambió. Si desea seguir utilizando clases no serializables con el extremo Remoting de Flex, active esta casilla de verificación.

## Configuración del servicio de repositorio {#repository-service-settings}

El servicio Repositorio ( `RepositoryService`) proporciona servicios de administración y almacenamiento de recursos para AEM formularios. Cuando los desarrolladores crean una aplicación, pueden implementar los recursos en el repositorio en lugar de en un sistema de archivos. Los recursos pueden incluir cualquier tipo de material colateral, incluidos formularios XML, PDF forms (incluidos los formularios Acrobat), fragmentos de formulario, imágenes, perfiles, políticas, archivos SWF, archivos DDX, esquemas XML, archivos WSDL y datos de prueba.

Puede utilizar el repositorio predeterminado incluido en AEM formularios o un repositorio de terceros (Content Server de Documentum de EMC, IBM FileNet Content Manager o IBM Content Manager).

El servicio Proveedor de repositorio es un delegado de servicio que actúa como interfaz de un servicio de proveedor. Esto le permite conectarse a una API común y no tiene que saber qué servicio de proveedor está implementando las capacidades de almacenamiento. El servicio de proveedor de repositorios proporciona almacenamiento de base de datos para los recursos del servicio Repositorio.

La siguiente configuración está disponible para el servicio Repositorio.

**Servicio de proveedor:** el nombre del servicio que se usa como proveedor de almacenamiento. El valor predeterminado es RepositoryProviderService.

## Configuración del servicio de firma {#signature-service-settings}

El servicio Signature ( `SignatureService`) permite a su organización proteger la seguridad y la privacidad de los documentos de Adobe PDF que distribuye y recibe. Este servicio utiliza firmas digitales y certificación para garantizar que los documentos no se modifiquen. Al alterar un documento, se rompe su firma. Dado que las características de seguridad se aplican al propio documento, éste sigue siendo seguro y controlado durante todo su ciclo de vida; más allá del cortafuegos, cuando se descarga sin conexión y cuando se envía de nuevo a su organización.

Los siguientes ajustes están disponibles para el servicio de firma.

**Nombre del servicio SPI HSM remoto:** esta opción se utiliza cuando el HSM está instalado en un equipo remoto. Especifique esta opción cuando AEM formularios esté instalado en una Windows de 64 bits y utilice dispositivos HSM para firmar.

**URL del servicio web HSM remoto:** especifique esta opción cuando AEM formularios estén instalados en Windows de 64 bits y esté utilizando dispositivos HSM para firmar.

**Certificación para incluir cambios en la carga del formulario:**  cuando se selecciona esta opción, el estado del formulario XFA se certifica, además de la plantilla XFA. Tenga en cuenta que habilitar esta opción puede tener un impacto negativo en el rendimiento. El valor predeterminado es true.

**Ejecutar secuencias de comandos JavaScript del documento:** especifica si se ejecutarán las secuencias de comandos JavaScript del documento durante las operaciones de firma. El valor predeterminado es false.

**Procesar documentos con compatibilidad con Acrobat 9:** especifica si se desea habilitar la compatibilidad con Acrobat 9. Por ejemplo, cuando se selecciona esta opción, la certificación visible en PDF dinámicos está activada. El valor predeterminado es false.

**Incrustar información de revocación al firmar:** especifica si la información de revocación está incrustada al firmar el documento PDF. El valor predeterminado es false.

**Incrustar información de revocación al certificar:** especifica si la información de revocación está incrustada al certificar el documento PDF. El valor predeterminado es false.

**Aplicar incrustación de información de revocación para todos los certificados durante la firma/certificación:**  especifica si una operación de firma o certificación falla si no está incrustada la información de revocación válida para todos los certificados. Tenga en cuenta que si un certificado no contiene ninguna CRL o información de OCSP, se considera válido aunque no se recupere ninguna información de revocación. El valor predeterminado es false.

**Orden de comprobación de revocación:** especifica el orden de comprobación de revocación cuando es posible realizar la comprobación mediante los mecanismos Lista de revocación de certificados (CRL) y Protocolo de estado de certificado en línea (OCSP). El valor predeterminado es OCSPFFirst.

**Tamaño máximo de la información de archivo de revocación:** el tamaño máximo de la información de archivo de revocación en kilobytes. AEM formularios intentan almacenar la mayor cantidad de información de revocación posible sin superar el límite. El valor predeterminado es 10 KB.

**Firmas de soporte creadas a partir de compilaciones previas al lanzamiento de productos de Adobe:**  cuando se selecciona esta opción, la firma creada con la versión previa al lanzamiento de los productos de Adobe se validará correctamente. El valor predeterminado es false.

**Opción de hora de verificación:** especifica la hora de verificación del certificado de un firmante. El valor predeterminado es Tiempo seguro distinto de la hora actual.

**Usar información de revocación archivada en firma durante la validación:** especifica si la información de revocación archivada con la firma se utiliza para la comprobación de revocación. El valor predeterminado es true.

**Usar información de validación almacenada en el documento para la validación de firmas:** cuando se selecciona esta opción, la información de validación (incluida la información de revocación y marca de tiempo) incrustada en el documento se utiliza para validar firmas. El valor predeterminado es true.

**Máximo de sesiones de verificación anidadas permitidas:** el número máximo de sesiones de verificación anidadas permitidas. AEM formularios utiliza este valor para evitar un bucle infinito al verificar los certificados de firmante de OCSP o CRL cuando el certificado OCSP o CRL no está configurado correctamente. El valor predeterminado es 10.

**Matiz de reloj máximo para verificación:** El tiempo máximo, en minutos, que la hora de firma puede ser posterior a la hora de validación. Si el sesgo del reloj es bueno que este valor, la firma no será válida. El valor predeterminado es de 65 minutos.

**Caché de duración del certificado:** la duración de un certificado, recuperado en línea o por otros medios, en la caché. El valor predeterminado es 1 día.

### Opciones de transporte {#transport-options}

**Host proxy:** la dirección URL del host proxy. Solo se usa si se proporciona algún valor válido. No hay ningún valor predeterminado.

**Puerto proxy:** el puerto proxy. Escriba cualquier número de puerto válido del 0 al 65535. El valor predeterminado es 80.

**Nombre de usuario de inicio de sesión del proxy:** el nombre de usuario de inicio de sesión del proxy. Solo se usa si se proporciona algún valor válido para el host proxy y el puerto proxy. No hay ningún valor predeterminado.

**Contraseña de inicio de sesión del proxy:** la contraseña de inicio de sesión del proxy. Solo se usa si se proporciona algún valor válido para el host proxy, el puerto proxy y el nombre de usuario de inicio de sesión proxy. No hay ningún valor predeterminado.

**Límite máximo de descarga:** la cantidad máxima de datos, en MB, que se pueden recibir por conexión. El valor mínimo es 1 MB y el valor máximo es 1024 MB. El valor predeterminado es 16 MB.

**Tiempo de espera de conexión:** el tiempo máximo de espera, en segundos, para establecer una conexión nueva. El valor mínimo es 1 y el valor máximo es 300. El valor predeterminado es 5.

**Tiempo de espera de socket:** el tiempo máximo de espera, en segundos, antes de que se produzca un tiempo de espera de socket (mientras espera la transferencia de datos). El valor mínimo es 1 y el valor máximo es 3600. El valor predeterminado es 30.

### Opciones de validación de ruta {#path-validation-options}

**Requerir directiva explícita:** especifica si la ruta debe ser válida para al menos una de las directivas de certificado que está asociada al anclaje de confianza del certificado del firmante. El valor predeterminado es false.

**Inhibir CUALQUIER directiva:** especifica si el identificador de objeto de directiva (OID) debe procesarse si está incluido en un certificado. El valor predeterminado es false.

**Inhibir asignación de directivas:** especifica si se permite la asignación de directivas en la ruta de certificación. El valor predeterminado es false.

**Comprobar todas las rutas:** especifica si todas las rutas deben validarse o si la validación debe detenerse después de encontrar la primera ruta válida. Seleccione true o false. El valor predeterminado es false.

**Servidor LDAP:** el servidor LDAP utilizado para buscar certificados para la validación de rutas. No hay ningún valor predeterminado.

**Siga los URI del certificado AIA:** especifica si los identificadores de recursos uniformes (URI) del certificado AIA se procesan durante la detección de rutas. El valor predeterminado es false.

**Extensión de restricciones básicas requerida en certificados de CA:** especifica si la extensión del certificado de restricciones básicas de entidad de certificación (CA) debe estar presente para certificados de CA. Algunos certificados raíz certificados (7 y anteriores) alemanes no son compatibles con RFC 3280 y no contienen la extensión de restricción básica. Si se sabe que el certificado EE de un usuario encadena hasta una raíz alemana de este tipo, anule la selección de esta casilla de verificación. El valor predeterminado es true.

**Requerir firma de certificado válida durante la creación de cadenas:** especifica si el generador de cadenas requiere firmas válidas en los certificados utilizados para crear cadenas. Cuando se selecciona esta casilla de verificación, el generador de cadenas no genera cadenas con firmas RSA no válidas en certificados. Considere la cadena CA > ICA > EE donde la firma de la CA en un ICA no es válida. Si este ajuste es cierto, la construcción de la cadena se detendrá en el ICA, y la CA no estará incluida en la cadena. Si esta configuración es falsa, se genera la cadena completa de 3 certificados. Esta configuración no afecta a las firmas DSA. El valor predeterminado es false.

### Opciones del proveedor de marcas de hora {#timestamp-provider-options}

**URL del servidor TSP:** la URL del proveedor de marca de tiempo predeterminado. Solo se usa si se proporciona algún valor válido. No hay ningún valor predeterminado.

**Nombre de usuario del servidor TSP:** el nombre de usuario si lo requiere el proveedor de marcas de tiempo. Solo se usa si se proporciona algún valor válido para la dirección URL. No hay ningún valor predeterminado.

**Contraseña del servidor TSP:** la contraseña del nombre de usuario anterior si la requiere el proveedor de marcas de tiempo. Solo se usa si se proporciona algún valor válido para la dirección URL y el nombre de usuario. No hay ningún valor predeterminado.

**Algoritmo de hash de solicitud:** especifica el algoritmo hash que se utilizará al crear la solicitud para el proveedor de marca de tiempo. El valor predeterminado es SHA1.

**Estilo de comprobación de revocación:** especifica el estilo de comprobación de revocación utilizado para determinar el estado de confianza del certificado del proveedor de marca de tiempo a partir de su estado de revocación observado. El valor predeterminado es BestEffort.

**Enviar cadena nonce:** especifica si se envía un nonce con la solicitud del proveedor de marca de tiempo. Una cadena nonce puede ser una marca de tiempo, un contador de visitas de una página web o un marcador especial destinado a limitar o impedir la reproducción o reproducción no autorizadas de un archivo. El valor predeterminado es true.

**Usar marcas de hora caducadas durante la validación:** cuando se selecciona esta opción, se pueden utilizar marcas de hora caducadas para recuperar los tiempos de validación de las firmas. El valor predeterminado es true.

**Tamaño de respuesta de TSP:** tamaño estimado, en bytes, de la respuesta de TSP. Este valor debe representar el tamaño máximo de la respuesta de marca de tiempo que podría devolver el proveedor de marca de tiempo configurado. No cambie esto a menos que esté absolutamente seguro. El valor mínimo es 60B y el valor máximo es 10240B. El valor predeterminado es 4096B.

**Ignore TimeStamp Server Extension**: Seleccione la opción  **Ignore TimeStamp Server** Extension para impedir que el servidor de AEM Forms contacte con el servidor de marca de hora especificado. La selección de la opción ayuda a evitar errores de proceso que se producen debido al tiempo de espera de conexión entre AEM Forms y los servidores de marca de hora.

### Opciones de lista de revocación de certificados {#certificate-revocation-list-options}

**Consultar primero URI local:** especifica si se debe dar preferencia a la ubicación CRL proporcionada en URI local o búsqueda CRL sobre cualquier ubicación especificada dentro de un certificado para comprobar la revocación. El valor predeterminado es false.

**URI local para la búsqueda de CRL:** URL del proveedor de CRL local. Este valor solo se consulta si la configuración Consultar URI local Primero está establecida en true. No hay ningún valor predeterminado.

**Estilo de comprobación de revocación:** especifica el estilo de comprobación de revocación utilizado para determinar el estado de confianza del certificado del proveedor de CRL a partir de su estado de revocación observado. El valor predeterminado es BestEffort.

**Servidor LDAP para búsqueda de CRL:** el servidor LDAP utilizado para obtener las CRL (como www.ldap.com). Todas las consultas basadas en DN para listas CRL se dirigirán a este servidor. No hay ningún valor predeterminado.

**Ir en línea:** especifica si desea conectarse para recuperar una CRL. Si es false, solo se consultan las CRL almacenadas en caché (en el disco local o las incrustadas con la firma). El valor predeterminado es true.

**Ignorar fechas de validez:** especifica si se ignorarán las horas thisUpdate y nextUpdate de la respuesta, lo que evita que estos tiempos tengan un efecto negativo en la validez de la respuesta. El valor predeterminado es false.

**Requerir extensión AKI en CRL:** especifica si la extensión del identificador de clave de autoridad debe incluirse en una CRL. El valor predeterminado es false.

### Opciones del protocolo de estado de certificado en línea {#online-certificate-status-protocol-options}

**URL del servidor OCSP:** URL del servidor OCSP predeterminado. El uso del servidor OCSP especificado mediante esta URL depende de la configuración de la opción de consulta de URL . No hay ningún valor predeterminado.

**Opción de consulta de URL:** controla la lista y el orden de los servidores OCSP que se utilizan para realizar la comprobación de estado. El valor predeterminado es UseAIAInCert.

**Estilo de comprobación de revocación:** especifica el estilo de comprobación de revocación que se utiliza al verificar el certificado del servidor OCSP. El valor predeterminado es CheckIfAvailable.

**Enviar cadena nonce:** especifica si se envía un nonce con la solicitud OCSP. Una cadena nonce puede ser una marca de tiempo, un contador de visitas de una página web o un marcador especial destinado a limitar o impedir la reproducción o reproducción no autorizadas de un archivo. El valor predeterminado es true.

**Tiempo de sesgo máximo del reloj:** el sesgo máximo permitido, en minutos, entre el tiempo de respuesta y la hora local. El valor mínimo es 0 y el valor máximo es 2147483647m. El valor predeterminado es 5m.

**Tiempo de frescura de la respuesta:** tiempo máximo, en minutos, para el que una respuesta OCSP preconstruida se considera válida. El valor mínimo es 1m y el valor máximo permitido es 2147483647. El valor predeterminado es 525600 (un año).

**Firmar solicitud OCSP:** especifica si se debe firmar la solicitud OCSP. El valor predeterminado es false.

**Alias de credencial del firmante de la solicitud:** especifica el alias de credencial que se utiliza para firmar la solicitud OCSP si la firma está habilitada. Solo se utiliza si la firma de la solicitud OCSP está habilitada. No hay ningún valor predeterminado.

**Ir en línea:** especifica si conectarse para realizar la comprobación de revocación. El valor predeterminado es true.

**Ignore los tiempos thisUpdate y nextUpdate de la respuesta:** especifica si se deben ignorar los tiempos thisUpdate y nextUpdate de la respuesta, lo que evita que estos tiempos tengan un efecto negativo en la validez de la respuesta. El valor predeterminado es false.

**Permitir extensión OCSPNoCheck:** especifica si la extensión OCSPNoCheck está permitida en el certificado de firma de respuesta. El valor predeterminado es true.

**Requerir extensión OCSP ISIS-MTT CertHash:** especifica si se debe incluir una extensión hash de clave pública de certificado en las respuestas OCSP. El valor predeterminado es false.

### Opciones de administración de errores para la depuración {#error-handling-options-for-debugging}

**Purgar caché de certificados en la siguiente llamada de API:** especifica si se purga la caché de certificados cuando se llama a la siguiente operación del servicio de firma. Después de llamar a la operación, esta opción se establece en false. El valor predeterminado es false.

**Purgar la caché de CRL en la siguiente llamada de API:** especifica si se purga la caché de CRL cuando se llama a la siguiente operación del servicio de firma. Después de llamar a la operación, esta opción se establece en false. El valor predeterminado es false.

**Purgar la caché de OCSP en la siguiente llamada de API:** especifica si se purga la caché de OCSP cuando se llama a la siguiente operación de servicio de firma. Después de llamar a la operación, esta opción se establece en false. El valor predeterminado es false.

## Configuración del servicio de carpetas vigiladas {#watched-folder-service-settings}

El servicio Carpeta vigilada ( `WatchedFolder`) configura los atributos que son comunes para todos los extremos de carpeta observados. También proporciona valores predeterminados para los extremos de carpeta observados. (Consulte [Configuración de puntos finales de carpeta observados](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints)). No se invoca por aplicaciones de cliente externas ni se utiliza en procesos creados en Workbench.

Las siguientes opciones de configuración están disponibles para el servicio Carpeta vigilada.

**Expresión Cron:** la expresión cron tal como la usa quartz para programar el sondeo del directorio de entrada.

**Recuento de repeticiones:** el número de veces que se sondea el directorio de entrada. El recuento de repetición predeterminado que se debe usar si este valor no se especifica en la configuración del extremo. Un valor de -1 indica la digitalización indefinida del directorio. El valor predeterminado es -1.

**Intervalo de repetición:** el número predeterminado si hay segundos entre cada encuesta. Este valor se utiliza como intervalo de repetición a menos que se especifique un valor diferente en la configuración del extremo de la carpeta observada. El valor predeterminado es 5. Consulte la descripción de la configuración Tamaño de lote para obtener más información.

**Asíncrono:** identifica el tipo de invocación como asíncrono o sincrónico. Los procesos transitorios y sincrónicos solo se pueden invocar sincrónicamente. El valor predeterminado es asíncrono.

**Tiempo de espera:** el valor predeterminado, en segundos, tras el cual se recuperan los archivos de las carpetas de entrada. Si el archivo o la carpeta son anteriores al tiempo especificado en el tiempo de espera, se selecciona para su procesamiento. El valor predeterminado es 0.

**Tamaño de lote:** el valor predeterminado del número de archivos o carpetas que se procesan por análisis. El valor predeterminado es 2.

La configuración Intervalo de repetición y Tamaño de lote determinan cuántos archivos ha visto la carpeta en cada análisis. Watched Folder utiliza un grupo de subprocesos de Quartz para analizar la carpeta de entrada. El grupo de subprocesos se comparte con otros servicios. Si el intervalo de análisis es pequeño, los subprocesos analizan la carpeta de entrada con frecuencia. Si los archivos se sueltan con frecuencia en la carpeta vigilada, mantenga el intervalo de análisis reducido. Si los archivos se pierden con poca frecuencia, utilice un intervalo de exploración mayor para que los demás servicios puedan utilizar los subprocesos.

Si hay un gran volumen de archivos que se están perdiendo, aumente el tamaño del lote. Por ejemplo, si el servicio invocado por el extremo de carpeta vigilada puede procesar 700 archivos por minuto y los usuarios colocan los archivos en la carpeta de entrada a la misma velocidad, al establecer el tamaño del lote en 350 y el intervalo de repetición en 30 segundos, se ayudará al rendimiento de la carpeta vigilada sin incurrir en el coste de digitalizar la carpeta vigilada con demasiada frecuencia.

Cuando se sueltan los archivos en la carpeta vigilada, se enumeran los archivos de entrada, lo que puede reducir el rendimiento si se realiza la digitalización cada segundo. El aumento del intervalo de análisis puede mejorar el rendimiento. Si el volumen de archivos que se van a perder es pequeño, ajuste el tamaño del lote y el intervalo de repetición en consecuencia. Por ejemplo, si se pierden 10 archivos cada segundo, intente establecer el intervalo de repetición en 1 segundo y el tamaño del lote en 10.

En una configuración de clúster, el tamaño del lote de un extremo de carpeta vigilada no se escala a varios nodos de clúster. Por ejemplo, si el tamaño del lote se establece en `2` para un clúster de dos nodos y la opción Aceleración está seleccionada, los nodos procesan los archivos colectivamente en lotes de dos en lugar de que cada nodo procese dos archivos a la vez.

**Sobrescribir nombres de archivo duplicados:**  una cadena booleana que especifica si la carpeta vista sobrescribe los nombres de archivo de resultados duplicados y si se deben sobrescribir los documentos conservados con el mismo nombre.

**Conservar carpeta:** el valor predeterminado de la carpeta de conservación. Esta carpeta se utiliza para copiar los archivos de origen en en caso de que la entrada se procese correctamente. Este valor puede ser una ruta vacía, relativa o absoluta con un patrón de archivo como se describe en la configuración de la carpeta de resultados.

**Carpeta de errores:** el nombre de la carpeta donde se copian los archivos de error. Este valor puede ser una ruta vacía, relativa o absoluta con un patrón de archivo como se describe en la configuración de la carpeta de resultados.

**Carpeta de resultados:** el nombre predeterminado de la carpeta de resultados. Esta carpeta se utiliza para copiar los archivos de resultados en . Este valor puede ser una ruta vacía, relativa o absoluta con el siguiente patrón de archivo.

* %F = prefijo de nombre de archivo
* %E = extensión de nombre de archivo
* %Y = año (completo)
* %y = año (dos últimos dígitos)
* %M = mes
* %D = día del mes
* %d = día del año
* %H = hora (reloj de 24 horas)
* %h = hora (reloj de 12 horas)
* %m = minuto
* %s = segundo
* %l = milisegundo
* %R = número aleatorio (de 0 a 9)
* %P = id. de proceso o trabajo

Por ejemplo, si es las 8 PM del 17 de julio de 2009 y especifica `C:/Test/WF0/failure/%Y/%M/%D/%H/`, la carpeta de resultados es `C:/Test/WF0/failure/2009/07/17/20`.

Si la ruta no es absoluta sino relativa, la carpeta se crea dentro de la carpeta vigilada. Para obtener más información sobre los patrones de archivo, consulte [Acerca de los patrones de archivo](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Cuanto menor sea el tamaño de las carpetas resultantes, mejor será el rendimiento de la carpeta vigilada. Por ejemplo, si la carga estimada de la carpeta vigilada es de 1000 archivos cada hora, pruebe un patrón como `result/%Y%M%D%H` para que se cree una nueva subcarpeta cada hora. Si la carga es menor (por ejemplo, 1000 archivos por día), puede utilizar un patrón como `result/%Y%M%D`.

**Carpeta de escenario:** el nombre predeterminado de la carpeta de escenario dentro de la carpeta vigilada.

**Carpeta de entrada:** el nombre predeterminado de la carpeta de entrada dentro de la carpeta vigilada.

**Conservar si hay un error:** si el valor es verdadero, los archivos originales se conservan en la carpeta de errores si se produce un error.

**Aceleración:** cuando se selecciona esta opción, limita el número de trabajos de carpeta observados que AEM los procesos de formularios en un momento determinado. El valor Tamaño de lote determina el número máximo de trabajos (consulte Acerca de la regulación).

## Configuración del servicio Web {#web-service-service-settings}

El servicio Servicio Web ( `WebService`) permite que los procesos invoquen operaciones de servicio Web.

El servicio Web Service permite que los procesos invoquen operaciones de servicio Web. Por ejemplo, una organización puede querer integrar un proceso para almacenar y recuperar información como los detalles de contacto y cuenta invocando los servicios web expuestos de un proveedor de servicios. El servicio Web invoca un servicio Web especificado y pasa los valores de cada uno de sus parámetros. A continuación, guarda los valores devueltos de la operación en una variable designada dentro de un proceso.

El servicio Web Service interactúa con los servicios Web enviando y recibiendo mensajes SOAP. El servicio también admite el envío de archivos adjuntos MIME, MTOM y SwaRef con mensajes SOAP mediante el protocolo WS-Attachment. Las interacciones del servicio Web son compatibles con los sistemas SAP y los servicios Web .NET.

Las siguientes configuraciones están disponibles para el servicio Web Service.

**Almacén de claves:** la ruta completa del archivo del almacén de claves que contiene la clave privada que se utilizará para la autenticación. El servidor de formularios debe poder acceder al archivo.

**Contraseña del almacén de claves:** la contraseña del archivo del almacén de claves.

**Tipo de almacén de claves:** el tipo de almacén de claves. No proporcione ningún valor para utilizar el tipo de almacén de claves predeterminado configurado para la JVM que ejecuta el servidor de formularios. De lo contrario, proporcione uno de los siguientes valores:

* jks
* pkcs12
* cms
* jceks

**Almacén de confianza:** la ruta completa del archivo del almacén de confianza que contiene la clave pública del servidor de servicios web.

**Contraseña del almacén de confianza:** la contraseña del archivo del almacén de confianza.

**Tipo de almacén de confianza:** el tipo de almacén de confianza. No proporcione ningún valor para utilizar el tipo de almacén de claves predeterminado configurado para la JVM que ejecuta el servidor de formularios. De lo contrario, proporcione uno de los siguientes valores:

* jks
* pkcs12
* cms
* jceks

## Configuración del servicio de transformación XSLT {#xslt-transformation-service-settings}

El servicio de transformación XSLT ( `XSLTService`) permite a los procesos aplicar transformaciones de lenguaje de hojas de estilo extensibles (XSLT) en documentos XML.

La siguiente configuración está disponible para el servicio de transformación XSLT.

**Nombre de fábrica:** el nombre completo de la clase Java que se utiliza para realizar transformaciones XSLT. Si no se especifica ningún valor, se utilizará la fábrica predeterminada configurada en la máquina virtual Java que ejecuta el servidor de formularios.

## Modificación de la configuración de seguridad de un servicio {#modifying-security-settings-for-a-service}

el servidor de formularios le permite configurar las opciones de seguridad de cada servicio, lo que le permite configurar el control de acceso detallado en un nivel servicio por servicio.

Se instalan perfiles de seguridad predeterminados, que se pueden configurar para satisfacer las necesidades del sistema. Cada perfil de seguridad tiene un dominio asociado y se crea a nivel de usuario o de grupo.

### Modificación de la configuración de seguridad de un servicio {#modify-security-settings-for-a-service}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de servicios.
1. En la página Administración de servicios , haga clic en el servicio para configurarlo.
1. Haga clic en la ficha Seguridad .
1. En la lista Requerir que los llamadores se autentiquen, seleccione Sí o No para especificar si el servicio se puede invocar con o sin credenciales.

   Si selecciona Sí, el llamador del servicio debe estar autenticado y el usuario principal de la llamada debe estar autorizado para invocar el servicio; de lo contrario, se rechazará el intento de invocación.

   Si selecciona No, el llamador del servicio puede o no estar autenticado. La invocación del servicio siempre se realizará correctamente porque no hay comprobación de autorización.

1. Para los servicios que contienen una o más operaciones marcadas para acceso anónimo, seleccione o anule la selección de Acceso anónimo permitido. Cuando el acceso anónimo está habilitado, cualquier usuario del sistema puede invocar operaciones en el servicio. Si el acceso anónimo está deshabilitado, se debe conceder a los usuarios permiso para llamar al servicio e invocar operaciones. A los usuarios se les conceden estos permisos directamente o como parte de un grupo que tenga dichos permisos.
1. En algunos servicios, la cuenta de usuario que ejecuta la operación afecta a los resultados. Por ejemplo, en los servicios de contenido (obsoleto), el usuario que almacena el contenido pasa a ser el propietario del contenido, lo que afecta a quién puede acceder más adelante al contenido. Si está utilizando un proceso para almacenar contenido, piense en qué usuario se utiliza para ejecutar el servicio de gestión de documentos, ya que ese usuario será el propietario del contenido almacenado.

   Para especificar la identidad en tiempo de ejecución utilizada por un servicio para ejecutar operaciones, seleccione Especificar ejecución como, seleccione una opción de la lista asociada y, a continuación, haga clic en Guardar. Elija entre las siguientes opciones:

   **Invocador:** utiliza la misma identidad que el usuario que invocó el servicio.

   **Sistema:** utiliza el usuario del sistema para ejecutar el servicio con privilegios completos.

   **Usuario con nombre:** permite ejecutar el servicio como un usuario específico. Cuando seleccione esta opción, haga clic en Seleccionar usuario para mostrar la página Seleccionar principal, donde puede buscar y seleccionar al usuario.

   Si no selecciona Especificar ejecución como, se usa el comportamiento predeterminado.

   >[!NOTE]
   >
   >Los servicios de procesamiento y envío que se utilizan con variables xfaForm, Document Form y Form siempre se ejecutan con la cuenta de usuario del sistema.

1. Haga clic en Agregar entidad de seguridad para especificar los permisos que los usuarios y grupos tienen para este servicio.
1. La pantalla Seleccionar principal muestra los usuarios y grupos configurados en Administración de usuarios. Si el usuario o grupo que desea no se muestra, utilice la función de búsqueda para encontrarlo. Haga clic en un nombre de usuario o grupo.
1. En la pantalla Agregar permisos , seleccione los permisos que desea asignar al usuario o grupo para este servicio:

   * **INVOKE_PERM:** Para invocar todas las operaciones en el servicio
   * **MODIFY_CONFIG_PERM:** Para modificar la configuración de un servicio
   * **SUPERVISOR_PERM:** Para ver los datos de instancias de proceso de un servicio creado a partir de un proceso
   * **START_STOP_PERM:** Para iniciar y detener un servicio
   * **ADD_REMOVE_ENDPOINTS_PERM:** Para agregar, quitar y modificar puntos finales de un servicio
   * **CREATE_VERSION_PERM:** Para crear una nueva versión del servicio
   * **DELETE_VERSION_PERM:** Para eliminar una versión del servicio
   * **MODIFY_VERSION_PERM:** Para modificar una versión del servicio
   * **READ_PERM:** Para ver el servicio
   * **PROCESS_OWNER_PERM:** para su uso en una versión futura de AEM formularios. No utilice este permiso.
   * **SERVICE_MANAGER_PERM:** para su uso en una versión futura de AEM formularios. No utilice este permiso.
   * **SERVICE_AGENT_PERM:** para su uso en una versión futura de AEM formularios. No utilice este permiso.

1. Haga clic en Agregar.

### Eliminación del principal de un perfil de seguridad {#remove-the-principal-from-a-security-profile}

1. En la página Administración de servicios , seleccione el servicio que desea configurar.
1. Haga clic en la pestaña **Security**, seleccione el perfil de seguridad que desea eliminar y haga clic en **Remove**.

## Configuración de la agrupación de un servicio {#configuring-pooling-for-a-service}

Cada servicio puede aprovechar las capacidades de agrupación para gestionar solicitudes de invocación entrantes. El uso de un grupo de servicios garantiza que las instancias de servicio se invoquen mediante un solo subproceso a la vez y se reutilicen en todas las solicitudes de invocación, lo que puede mejorar el rendimiento. También puede utilizar la agrupación para especificar la opción Maximum Async Service Instances (Máximo de instancias de servicio asincrónicas), que permite a los servicios limitar el número de solicitudes gestionadas en paralelo.

### Habilitar agrupación {#enable-pooling}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de servicios.
1. En la página Administración de servicios , haga clic en el servicio para configurarlo.
1. Haga clic en la ficha Agrupación .
1. En la lista Estrategia de procesamiento de solicitudes , seleccione Instancias agrupadas para todas las solicitudes.
1. En el cuadro Tamaño inicial del grupo de instancias de servicio, introduzca el tamaño inicial del grupo. Cuando se implementa el servicio, este número se utiliza para determinar el número de instancias de implementación de servicio que se crean y asignan al grupo gratuito, en espera de solicitudes de invocación. Esto permite que el contenedor de servicios responda inmediatamente a las solicitudes de invocación sin tener que inicializar primero una instancia de servicio.
1. En el cuadro Tamaño máximo del grupo de instancias de servicio, introduzca el número máximo de instancias en el grupo para un servicio determinado. Esta configuración controla el número de subprocesos que pueden ejecutar un servicio determinado en un momento determinado. El valor predeterminado es 0, lo que da como resultado un tamaño de grupo ilimitado.
1. En el cuadro Máximo de instancias de servicio asincrónicas , introduzca el número máximo de instancias del grupo que se pueden utilizar para atender solicitudes asincrónicas en un momento determinado. Esta configuración permite que el servicio limite el número de solicitudes que puede gestionar en paralelo.
1. En el cuadro Tiempo de espera de invocación, introduzca el número de milisegundos que hay que esperar para que un servicio esté disponible para una solicitud de invocación. Si no especifica ningún valor para esta configuración, el valor predeterminado es 0, lo que no provoca que se produzca un tiempo de espera.
1. Haga clic en Guardar.

### Eliminar agrupación {#remove-pooling}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de servicios.
1. En la página Administración de servicios , haga clic en el servicio para configurarlo.
1. Haga clic en la ficha Agrupación .
1. En la lista Estrategia de procesamiento de solicitudes , seleccione Nueva instancia para cada solicitud o Instancia única para todas las solicitudes.

   **Instancia única para todas las solicitudes:** se crea y almacena en caché una instancia de servicio cuando la primera solicitud entra en el contenedor. Cada solicitud posterior utiliza la misma instancia de servicio para gestionar la solicitud.

   **Nueva instancia para cada solicitud:** se crea una nueva instancia de servicio para cada invocación recibida.

1. Haga clic en Guardar.
