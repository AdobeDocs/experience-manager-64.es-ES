---
title: Configurar extremos de carpetas vigiladas
seo-title: Configuring watched folder endpoints
description: Obtenga información sobre cómo configurar los extremos de las carpetas vigiladas.
seo-description: Learn how to configure watched folder endpoints.
uuid: 01fb5ff8-2071-44bd-9241-7d5d41a5b26e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 761e7909-43ba-4642-bcfc-8d76f139b9a3
exl-id: bce7eee6-17c6-4eaf-b679-b47e611bed87
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '7199'
ht-degree: 20%

---

# Configurar extremos de carpetas vigiladas {#configuring-watched-folder-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Un administrador puede configurar una carpeta de red, conocida como *carpeta vigilada*, de modo que cuando un usuario coloca un archivo (como un archivo PDF) en la carpeta vigilada, se invoque una operación de servicio configurada y manipule el archivo. Una vez que el servicio realiza la operación especificada, guarda el archivo modificado en una carpeta de salida especificada.

## Configuración del servicio Carpeta vigilada {#configuring-the-watched-folder-service}

Antes de configurar un extremo de carpeta vigilada, configure el servicio Carpeta vigilada. Los parámetros de configuración del servicio Carpeta vigilada tienen dos propósitos:

* Para configurar atributos que sean comunes para todos los extremos de carpeta observados
* Para proporcionar valores predeterminados para todos los extremos de carpeta vistos

Después de configurar el servicio Carpeta vigilada, agregue un extremo Carpeta vigilada para el servicio de destino. Al agregar el punto final, se establecen valores, como el nombre del servicio y el nombre de la operación que se invocarán cuando los archivos o carpetas se coloquen en la carpeta de entrada del servicio configurado Watched Folder. Para obtener más información sobre la configuración del servicio Carpeta vigilada, consulte [Configuración del servicio de carpetas vigiladas](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).

## Creación de una carpeta vigilada {#creating-a-watched-folder}

Puede crear una carpeta vista de las dos formas siguientes:

* Al configurar la configuración de un extremo de carpeta vigilada, escriba la ruta completa al directorio principal en el cuadro Ruta y añada el nombre de la carpeta vigilada que se creará, como se muestra en este ejemplo:
   `  C:\MyPDFs\MyWatchedFolder`Debido a que la carpeta MyWatchedFolder no existe, AEM formularios intentan crearla en esa ubicación.

* Cree una carpeta en el sistema de archivos antes de configurar un punto final de carpeta vigilada y después escriba la ruta completa en el cuadro Ruta.

En un entorno agrupado, la carpeta que se utilizará como carpeta vigilada debe ser accesible, grabable y compartida en el sistema de archivos o la red. En esta situación, cada instancia de servidor de aplicaciones del clúster debe tener acceso a la misma carpeta compartida.

En Windows, si el servidor de aplicaciones se está ejecutando como un servicio, debe iniciarse con el acceso adecuado a la carpeta compartida de una de las siguientes maneras:

* Configurar el servicio del servidor de aplicaciones Iniciar sesión como **parameter** para comenzar como un usuario específico con acceso adecuado a la carpeta vigilada compartida.
* Configure la opción del servicio del servidor de aplicaciones Iniciar como sistema local para permitir que el servicio interactúe con el escritorio. Esta opción requiere que la carpeta vigilada compartida sea accesible y grabable para todos.

## Agrupación de carpetas vigiladas {#chaining-together-watched-folders}

Las carpetas vigiladas se pueden encadenar juntas para que un documento resultante de una carpeta vigilada sea el documento de entrada de la siguiente carpeta vigilada. Cada carpeta vigilada puede invocar un servicio diferente. Al configurar las carpetas vigiladas de esta manera, se pueden invocar varios servicios. Por ejemplo, una carpeta vigilada podría convertir archivos PDF a Adobe PostScript® y una segunda carpeta vigilada podría convertir los archivos PostScript a formato PDF/A. Para ello, simplemente configure la variable *result* carpeta de la carpeta vigilada definida por el primer punto final para señalar al *input* carpeta de la carpeta vigilada definida por su segundo punto final.

El resultado de la primera conversión iría a \path\result. La entrada para la segunda conversión sería \path\result y el resultado de la segunda conversión iría a \path\result\result (o el directorio que defina en el cuadro Carpeta de resultados para la segunda conversión).

## Interacción de los usuarios con las carpetas vigiladas {#how-users-interact-with-watched-folders}

Para un punto final de carpeta vigilada, los usuarios pueden invocar copiando o arrastrando archivos de entrada o carpetas desde sus escritorios a una carpeta vigilada. Los archivos se procesarán en el orden en que lleguen.

En los extremos de carpeta vigilados, si el trabajo requiere un solo archivo de entrada, el usuario puede copiar ese archivo en la raíz de la carpeta vigilada.

Si el trabajo contiene más de un archivo de entrada, el usuario debe crear una carpeta fuera de la jerarquía de carpetas vigiladas que contenga todos los archivos necesarios. Esta nueva carpeta debe incluir los archivos de entrada (y opcionalmente un archivo DDX si el proceso lo requiere). Una vez construida la carpeta de trabajo, el usuario la copia en la carpeta de entrada de la carpeta vigilada.

>[!NOTE]
>
>Asegúrese de que el servidor de aplicaciones haya eliminado el acceso a los archivos de la carpeta vigilada. Si AEM formularios no pueden eliminar los archivos de la carpeta de entrada después de analizarlos, el proceso asociado se invocará indefinidamente.

## Salida de carpeta vigilada {#watched-folder-output}

Cuando la entrada es una carpeta y la salida consta de varios archivos, AEM formularios crea una carpeta de salida con el mismo nombre que la carpeta de entrada y copia los archivos de salida en esa carpeta. Cuando la salida consiste en un mapa del documento que contiene un par clave-valor, como el resultado de un proceso Salida, la clave se utilizará como nombre del archivo de salida.

Los nombres de archivo de salida que resulten de un proceso de extremo no pueden contener caracteres que no sean letras, números y un punto (.) antes de la extensión de archivo. AEM formularios convierte otros caracteres a sus valores hexadecimales.

Las aplicaciones cliente recogen los documentos resultantes de la carpeta de resultados de la carpeta vigilada. Los errores de proceso se registran en la carpeta de errores de la carpeta vigilada.

## Cómo funciona la carpeta vigilada {#how-watched-folder-works}

El módulo Carpeta vigilada contiene estos servicios:

* Servicio de carpetas vigiladas
* provider.file_scan_service
* provider.file_write_results_service

Además de los servicios enumerados anteriormente, Watched Folder también depende de otros servicios, incluido el servicio Scheduler para programar los trabajos y el servicio Job Manager para admitir la invocación asincrónica de los servicios de destino.

### Procesamiento de una solicitud de invocación en una carpeta vigilada {#how-watched-folder-processes-an-invocation-request}

El servicio Carpeta vigilada gestiona la creación, actualización y eliminación de los extremos. Una vez que el administrador crea los extremos, el servicio Scheduler los programa para activarlos en función del intervalo de repetición o la expresión cron especificados.

Este diagrama ilustra cómo la carpeta vigilada procesa una solicitud de invocación.

![en_watchedfolder](assets/en_watchedfolder.png)

El proceso de invocación de un servicio mediante carpetas vigiladas es el siguiente:

1. Una aplicación cliente coloca archivos o carpetas en la carpeta de entrada de la carpeta vigilada.
1. Cuando se produce el intervalo de análisis del trabajo, el servicio Scheduler invoca provider.file_scan_service para procesar los archivos o carpetas de la carpeta de entrada.
1. provider.file_scan_service realiza estas tareas:

   * Analiza la carpeta de entrada en busca de archivos o carpetas que coincidan con el patrón de inclusión de archivos y excluye los archivos o carpetas del patrón de exclusión de archivos especificado. Primero se recogen los archivos o carpetas más antiguos. También se recogen los archivos y carpetas anteriores al tiempo de espera. En un análisis, el número de archivos o carpetas que se procesan se basa en el tamaño del lote. Para obtener información sobre los patrones de archivo, consulte [Acerca de los patrones de archivo](configuring-watched-folder-endpoints.md#about-file-patterns). Para obtener información sobre cómo configurar el tamaño del lote, consulte [Configuración del servicio de carpetas vigiladas](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).
   * Recopila los archivos o carpetas para su procesamiento. Si los archivos o carpetas no se descargan completamente, se recogen en el siguiente análisis. Para asegurarse de que las carpetas están completamente descargadas, los administradores deben crear una carpeta con un nombre utilizando el patrón de exclusión de archivos. Una vez que la carpeta tiene todos los archivos, se debe cambiar el nombre al patrón especificado en el patrón de archivos de inclusión. Este paso garantiza que la carpeta tenga todos los archivos necesarios para invocar el servicio. Para obtener más información sobre cómo garantizar que las carpetas se descarguen completamente, consulte [Sugerencias y trucos para carpetas vigiladas](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).
   * Mueve los archivos o carpetas a la carpeta del escenario después de seleccionarlos para su procesamiento.
   * Convierte los archivos o carpetas de la carpeta de escenario a la entrada adecuada según las asignaciones de parámetros de entrada de extremo. Para ver ejemplos de asignaciones de parámetros de entrada, consulte [Sugerencias y trucos para carpetas vigiladas](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).

1. El servicio de destino configurado para el extremo se invoca sincrónica o asincrónicamente. El servicio de destino se invoca utilizando el nombre de usuario y la contraseña configurados para el extremo.

   * La invocación sincrónica llama al servicio de destino directamente y gestiona inmediatamente la respuesta.
   * Para la invocación asíncrona, se llama al servicio de destino a través del servicio Administrador de trabajos, que coloca la solicitud en una cola. A su vez, el servicio del administrador de trabajos llama al provider.file_write_results_service para controlar los resultados.

1. El provider.file_write_results_service gestiona la respuesta o el error de la invocación del servicio de destino. Cuando se realiza correctamente, la salida se guarda en la carpeta de resultados en función de la configuración del extremo. provider.file_write_results_service también conserva la fuente si el extremo está configurado para conservar los resultados una vez finalizados correctamente.

   Cuando la invocación del servicio de destino resulta en un error, provider.file_write_results_service registra el motivo del error en un archivo failure.log y coloca ese archivo en la carpeta de errores. La carpeta de errores se crea en función de los parámetros de configuración especificados para el extremo. Cuando el administrador establece la opción Conservar si hay error en la configuración del extremo, provider.file_write_results_service también copia los archivos de origen en la carpeta de errores. Para obtener información sobre cómo recuperar archivos de la carpeta de errores, consulte [Puntos de error y recuperación](configuring-watched-folder-endpoints.md#failure-points-and-recovery).

## Configuración de extremo de carpeta vigilada {#watched-folder-endpoint-settings}

Utilice los siguientes ajustes para configurar un punto final de carpeta vigilada.

**Nombre:** (Obligatorio) Identifica el extremo. No incluya un carácter &lt; porque truncará el nombre mostrado en Workspace. Si introduce una URL como nombre del extremo, asegúrese de que cumple las reglas de sintaxis especificadas en RFC1738.

**Descripción:** Descripción del extremo. No incluya un carácter &lt; porque truncará la descripción que se muestra en Workspace.

**Ruta:** (Obligatorio) Especifica la ubicación de la carpeta vigilada. En un entorno agrupado, esta configuración debe apuntar a una carpeta de red compartida a la que se pueda acceder desde todos los equipos del clúster.

**Asíncrono:** Identifica el tipo de invocación como asíncrono o sincrónico. El valor predeterminado es asíncrono. Se recomienda asincrónico para procesos de larga duración y sincrónico para procesos transitorios o de corta duración.

**Expresión Cron:** Introduzca una expresión cron si la carpeta vigilada debe programarse utilizando una expresión cron. Cuando se configura esta opción, se ignora el intervalo de repetición.

**Intervalo de repetición:** Intervalo en segundos para analizar la carpeta vigilada para obtener información. A menos que la configuración del acelerador esté habilitada, el intervalo de repetición debe ser mayor que el tiempo para procesar un trabajo promedio; de lo contrario, el sistema podría sobrecargarse. El valor predeterminado es 5. Consulte la descripción del tamaño del lote para obtener más información.

**Recuento de repetición:** Número de veces que la carpeta vigilada explora la carpeta o el directorio. Un valor de -1 indica escaneo indefinido. El valor predeterminado es -1.

**Acelerador:** Cuando se selecciona esta opción, limita el número de trabajos de carpeta observados que AEM los procesos de formularios en un momento determinado. El número máximo de trabajos viene determinado por el valor Tamaño del lote. (Consulte Acerca de la restricción.)

**Nombre de usuario:** (Obligatorio) El nombre de usuario que se utiliza al invocar un servicio de destino desde la carpeta de visualización. El valor predeterminado es SuperAdmin.

**Nombre de dominio:** (Obligatorio) Dominio del usuario. El valor predeterminado es DefaultDom.

**Tamaño del lote:** Número de archivos o carpetas que se van a recoger por análisis. Utilizar para evitar sobrecargas en el sistema; el análisis de demasiados archivos al mismo tiempo puede provocar un bloqueo. El valor predeterminado es 2.

La configuración Intervalo de repetición y Tamaño de lote determinan cuántos archivos ha visto la carpeta en cada análisis. La carpeta inspeccionada utiliza un grupo de hilos de Quartz para analizar la carpeta de entrada. El grupo de subprocesos se comparte con otros servicios. Si el intervalo de análisis es pequeño, los subprocesos analizarán la carpeta de entrada con frecuencia. Si los archivos se pierden con frecuencia en la carpeta vigilada, deberá reducir el intervalo de análisis. Si los archivos se pierden con poca frecuencia, utilice un intervalo de exploración mayor para que los demás servicios puedan utilizar los subprocesos.

Si se pierde un gran volumen de archivos, aumente el tamaño del lote. Por ejemplo, si el servicio invocado por el extremo de carpeta vigilada puede procesar 700 archivos por minuto y los usuarios colocan los archivos en la carpeta de entrada a la misma velocidad, al establecer el tamaño del lote en 350 y el intervalo de repetición en 30 segundos, se ayudará al rendimiento de la carpeta vigilada sin incurrir en el coste de digitalizar la carpeta vigilada con demasiada frecuencia.

Cuando se sueltan los archivos en la carpeta vigilada, se enumeran los archivos de entrada, lo que puede reducir el rendimiento si se realiza la digitalización cada segundo. El aumento del intervalo de análisis puede mejorar el rendimiento. Si el volumen de archivos que se van a perder es pequeño, ajuste el tamaño del lote y el intervalo de repetición en consecuencia. Por ejemplo, si se pierden 10 archivos cada segundo, intente establecer el intervalo de repetición en 1 segundo y el tamaño del lote en 10.

**Tiempo de espera:** Tiempo, en milisegundos, que debe esperarse antes de analizar una carpeta o archivo después de crearlo. Por ejemplo, si el tiempo de espera es de 3 600 000 milisegundos (una hora) y el archivo se creó hace un minuto, el archivo se recopilará después de que hayan transcurrido 59 minutos o más. El valor predeterminado es 0.

Esta configuración es útil para asegurarse de que un archivo o carpeta se copia completamente en la carpeta de entrada. Por ejemplo, si tiene un archivo grande para procesar y tarda diez minutos en descargarse, establezca el tiempo de espera en 10&amp;ast;60 &amp;ast;1000 milisegundos. Esto evita que la carpeta vigilada analice el archivo si no tiene diez minutos de antigüedad.

**Patrón de exclusión de archivo:** Punto y coma **;** lista delimitada de patrones que utiliza una carpeta vigilada para determinar qué archivos y carpetas se deben analizar y recoger. No se analizará ningún archivo o carpeta con este patrón para su procesamiento.

Esta configuración es útil cuando la entrada es una carpeta con varios archivos. El contenido de la carpeta se puede copiar en una carpeta con un nombre que recoge la carpeta vigilada. Esto evita que la carpeta vigilada recoja una carpeta para procesarla antes de que la carpeta se copie completamente en la carpeta de entrada.

Puede usar patrones de archivo para excluir:

* Archivos con extensiones de nombre de archivo específicas; por ejemplo, &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf.
* Archivos con nombres específicos; por ejemplo, data.&amp;ast; excluiría archivos y carpetas con nombre *data1*, *data2*, etc.
* Archivos con expresiones compuestas en el nombre y la extensión, como en estos ejemplos:

   * Data[0-9][0-9][0-9].[dD][aA][tT]
   * &amp;ast;.[dD][Aa][Tt]
   * &amp;ast;.[Xx][Mm][Ll]

Para obtener más información sobre los patrones de archivo, consulte [Información sobre los patrones de archivo](configuring-watched-folder-endpoints.md#about-file-patterns).

**Patrón de archivo de inclusión:** (Obligatorio) Punto y coma **;** lista delimitada de patrones que utiliza la carpeta vigilada para determinar qué carpetas y archivos analizar y recoger. Por ejemplo, si el Patrón de archivo de inclusión es input&amp;ast;, todos los archivos y carpetas que coincidan con input&amp;ast; se recogerán. Esto incluye archivos y carpetas llamados input1, input2, etc.

El valor predeterminado es &amp;ast; e indica todos los archivos y carpetas.

Puede utilizar patrones de archivo para incluir:

* Archivos con extensiones de nombre de archivo específicas; por ejemplo, &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf.
* Archivos con nombres específicos; por ejemplo, data.&amp;ast; incluiría archivos y carpetas con nombre *data1*, *data2*, etc.
* Archivos con expresiones compuestas en el nombre y la extensión, como en estos ejemplos:

   * Data[0-9][0-9][0-9].[dD][aA][tT]
   * &amp;ast;.[dD][Aa][Tt]
   * &amp;ast;.[Xx][Mm][Ll]

Para obtener más información sobre los patrones de archivo, consulte [Información sobre los patrones de archivo](configuring-watched-folder-endpoints.md#about-file-patterns).

**Carpeta de resultados:** La carpeta en la que se almacenan los resultados guardados. Si los resultados no aparecen en esta carpeta, compruebe la carpeta de errores. Los archivos de solo lectura no se procesan y se guardan en la carpeta de errores. Este valor puede ser una ruta absoluta o relativa con los siguientes patrones de archivo:

* %F = prefijo del nombre de archivo
* %E = extensión del nombre de archivo
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
* %R = número aleatorio (entre 0 y 9)
* %P = ID del proceso o trabajo

Por ejemplo, si es las 8 p. m. del 17 de julio de 2009 y especifica `C:/Test/WF0/failure/%Y/%M/%D/%H/`, la carpeta de resultados es `C:/Test/WF0/failure/2009/07/17/20`.

Si la ruta no es absoluta sino relativa, la carpeta se creará dentro de la carpeta vigilada. El valor predeterminado es result/%Y/%M/%D/, que es la carpeta de resultados dentro de la carpeta vigilada. Para obtener más información sobre los patrones de archivo, consulte [Información sobre los patrones de archivo](configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Cuanto menor sea el tamaño de las carpetas resultantes, mejor será el rendimiento de la carpeta vigilada. Por ejemplo, si la carga estimada de la carpeta vigilada es de 1000 archivos cada hora, pruebe un patrón como `result/%Y%M%D%H` para que se cree una nueva subcarpeta cada hora. Si la carga es menor (por ejemplo, 1000 archivos por día), puede utilizar un patrón como `result/%Y%M%D`.

**Conservar carpeta:** Ubicación en la que se almacenan los archivos después de escanearlos y recogerlos correctamente. La ruta puede ser absoluta, relativa o nula. Puede utilizar patrones de archivo, tal como se describe para la carpeta Resultados. El valor predeterminado es preserve/%Y/%M/%D/.

**Carpeta de errores:** Carpeta donde se guardan los archivos de error. Esta ubicación siempre es relativa a la carpeta vigilada. Puede utilizar patrones de archivo, tal como se describe para la carpeta Resultados.

Los archivos de solo lectura no se procesan y se guardan en la carpeta de errores.

El valor predeterminado es failure/%Y/%M/%D/.

**Conservar En Caso De Fallo:** Preservar archivos de entrada en caso de que no se ejecute la operación en un servicio. El valor predeterminado es True.

**Sobrescribir nombres de archivo duplicados:** Cuando se establece en True, los archivos de la carpeta de resultados y de la carpeta de preservación se sobrescriben. Cuando se establece en False, se utilizan archivos y carpetas con un sufijo de índice numérico para el nombre. El valor predeterminado es False.

**Duración de la purga:** (Obligatorio) Los archivos y carpetas de la carpeta de resultados se depuran cuando son anteriores a este valor. Este valor se mide en días. Esta configuración es útil para garantizar que la carpeta de resultados no se llene.

El valor de -1 días indica que nunca se eliminará la carpeta de resultados. El valor predeterminado es -1.

**Nombre de la operación:** (Obligatorio) Una lista de operaciones que se pueden asignar al extremo de la carpeta vigilada.

**Asignaciones de parámetros de entrada:** Se utiliza para configurar la entrada necesaria para procesar el servicio y la operación. La configuración disponible depende de qué servicio esté utilizando el extremo de carpeta vigilada. Estos son los dos tipos de entradas:

**Literal:** La carpeta de visualización utiliza el valor introducido en el campo tal como se muestra. Se admiten todos los tipos de Java básicos. Por ejemplo, si una API utiliza entradas como String, long, int y Boolean, la cadena se convierte al tipo adecuado y se invoca el servicio.

**Variable:** El valor introducido es un patrón de archivo que la carpeta vigilada utiliza para seleccionar la entrada. Por ejemplo, en el caso del servicio encrypt password, donde el documento de entrada debe ser un archivo PDF, el usuario puede utilizar &amp;ast;.pdf como patrón de archivo. La carpeta vigilada recogerá todos los archivos de la carpeta vigilada que coincidan con este patrón e invocará el servicio para cada archivo. Cuando se utiliza una variable, todos los archivos de entrada se convierten en documentos. Solo se admiten las API que utilizan Document como tipo de entrada.

**Asignaciones de parámetros de salida:** Se utiliza para configurar los resultados del servicio y la operación. La configuración disponible depende de qué servicio esté utilizando el extremo de carpeta vigilada.

El resultado Carpeta vigilada puede ser un solo documento, una lista de documentos o un mapa de documentos. Estos documentos de salida se guardan en la carpeta de resultados, utilizando el patrón especificado en la asignación de parámetros de salida.

>[!NOTE]
>
>Al especificar nombres que den como resultado nombres de archivo de salida únicos, mejora el rendimiento. Por ejemplo, considere el caso en el que el servicio devuelve un documento de salida y la asignación de parámetros de salida lo asigna a `%F.%E` (el nombre de archivo y la extensión del archivo de entrada). En este caso, si los usuarios sueltan archivos con el mismo nombre cada minuto y la carpeta de resultados está configurada en `result/%Y/%M/%D`y la opción Sobrescribir nombre de archivo duplicado está desactivada, la carpeta vigilada intentará resolver los nombres de archivo duplicados. El proceso de resolución de nombres de archivo duplicados puede afectar al rendimiento. En esta situación, cambiar la asignación de parámetros de salida a `%F_%h_%m_%s_%l` para agregar horas, minutos, segundos y milisegundos al nombre, o asegurarse de que los archivos perdidos tengan nombres únicos puede mejorar el rendimiento.

## Acerca de los patrones de archivo {#about-file-patterns}

Los administradores pueden especificar el tipo de archivo que puede invocar un servicio. Se pueden establecer varios patrones de archivo para cada carpeta vigilada. Un patrón de archivo puede ser una de las siguientes propiedades de archivo:

* Archivos con extensiones de nombre de archivo específicas; por ejemplo, &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf,;
* Archivos con nombres específicos; por ejemplo, data.&amp;ast;
* Archivos con expresiones compuestas en el nombre y la extensión, como en estos ejemplos:

   * Data[0-9][0-9][0-9].[dD][aA][tT]
   * &amp;ast;.[dD][Aa][Tt]
   * &amp;ast;.[Xx][Mm][Ll]

El administrador puede definir el patrón de archivo de la carpeta de salida en la que desea almacenar los resultados. Para las carpetas de salida (resultado, conservar y error), el administrador puede especificar cualquiera de estos patrones de archivo:

* %Y = año (completo)
* %y = año (dos últimos dígitos)
* %M = mes
* %D = día del mes
* %d = día del año
* %h = hora
* %m = minuto
* %s = segundo
* %R = número aleatorio entre 0 y 9
* %J = Nombre del trabajo

Por ejemplo, la ruta a la carpeta de resultados puede ser `C:\Adobe\Adobe_Experience_Manager_forms\BarcodedForms\%y\%m\%d`.

Las asignaciones de parámetros de salida también pueden especificar patrones adicionales, como los siguientes:

* %F = Nombre de archivo de origen
* %E = Extensión de nombre de archivo de origen

Si el patrón de asignación de parámetros de salida termina con &quot;File.separator&quot; (que es el separador de rutas), se crea una carpeta y el contenido se copia en esa carpeta. Si el patrón no termina con &quot;File.separator&quot;, el contenido (archivo de resultados o carpeta) se crea con ese nombre. Para obtener más información sobre las asignaciones de parámetros de salida, consulte [Sugerencias y trucos para carpetas vigiladas](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).

## Acerca de la restricción {#about-throttling}

Cuando la restricción está habilitada para un extremo de carpeta de inspección, limita el número de trabajos de carpeta observados que se pueden procesar en un momento dado. El número máximo de trabajos está determinado por el valor Tamaño del lote, también configurable en el punto final de la carpeta inspeccionada. Los documentos entrantes en el directorio de entrada de la carpeta vigilada no se sondearán cuando se alcance el límite de regulación. Los documentos también permanecerán en el directorio de entrada hasta que se hayan completado otros trabajos de carpeta observados y se realice otro intento de encuesta. En el caso del procesamiento sincrónico, todos los trabajos procesados en una sola encuesta se contabilizarán en el límite de regulación, aunque los trabajos se procesen consecutivamente en un solo subproceso.

>[!NOTE]
>
>La restricción no se escala con un grupo. Cuando la restricción está habilitada, el grupo en su conjunto no procesará más del número de trabajos especificado en Tamaño de lote en un momento dado. Este límite es para todo el grupo y no es específico de cada nodo del grupo. Por ejemplo, con un tamaño de lote de 2, se podía alcanzar el límite de restricción con un solo nodo procesando dos trabajos, y ningún otro nodo encuestaría el directorio de entrada hasta que se complete uno de los trabajos.

### Funcionamiento de la restricción {#how-throttling-works}

La carpeta vigilada explora la carpeta de entrada en cada intervalo de repetición, recoge el número de archivos especificados en el tamaño del lote e invoca el servicio de destino para cada uno de estos archivos. Por ejemplo, si el tamaño del lote es de cuatro, en cada análisis, la carpeta vigilada recogerá cuatro archivos, creará cuatro solicitudes de invocación e invocará el servicio de destino. Antes de que se completen estas solicitudes, si se invoca la carpeta vigilada, se reiniciarán cuatro trabajos, independientemente de si se han completado los cuatro trabajos anteriores.

La restricción impide que la carpeta inspeccionada invoque nuevos trabajos cuando los trabajos anteriores no se completan. La carpeta vigilada detectará los trabajos en curso y procesará los nuevos trabajos en función del tamaño del lote menos los trabajos en curso. Por ejemplo, en la segunda invocación, si el número de trabajos completados es solo tres y un trabajo sigue en curso, la carpeta inspeccionada invoca solo tres trabajos más.

* La carpeta inspeccionada depende del número de archivos presentes en la carpeta de fase para averiguar cuántos trabajos hay en curso. Si los archivos permanecen sin procesar en la carpeta de ensayo, la carpeta vigilada no invocará más trabajos. Por ejemplo, si el tamaño del lote es de cuatro y hay tres trabajos estancados, la carpeta vigilada solo invocará un trabajo en invocaciones posteriores. Existen varios escenarios que pueden hacer que los archivos permanezcan sin procesar en la carpeta de fase. Cuando los trabajos están estancados, el administrador puede finalizar el proceso en la página de administración del flujo de trabajo de formularios para que la carpeta vigilada mueva los archivos fuera de la carpeta del escenario.
* Si el servidor de formularios se desactiva antes de que la carpeta vigilada pueda invocar los trabajos, el administrador puede sacar los archivos de la carpeta del escenario. Para obtener más información, consulte [Puntos de error y recuperación](configuring-watched-folder-endpoints.md#failure-points-and-recovery).
* Si el servidor de formularios se está ejecutando pero la carpeta vigilada no se está ejecutando cuando el servicio Administrador de trabajos vuelve a llamarse, lo que ocurre cuando los servicios no se inician en la secuencia ordenada, el administrador puede sacar los archivos de la carpeta del escenario. Para obtener más información, consulte [Puntos de error y recuperación](configuring-watched-folder-endpoints.md#failure-points-and-recovery).

## Rendimiento y escalabilidad {#performance-and-scalability}

La carpeta vigilada puede servir 100 carpetas en total en un solo nodo. El rendimiento de la carpeta vigilada depende del rendimiento del servidor de formularios. Para la invocación asíncrona, el rendimiento depende más de la carga del sistema y de los trabajos que están en la cola del Administrador de trabajos.

El rendimiento de la carpeta vigilada se puede mejorar añadiendo nodos al clúster. Los trabajos de carpeta vigilados se distribuyen entre los nodos del clúster en virtud del planificador de Quartz y, en el caso de solicitudes asincrónicas, por el servicio Administrador de trabajos. Todos los trabajos se mantienen en la base de datos.

La carpeta vigilada depende del servicio Planificador para programar, anular la programación y volver a programar los trabajos. Hay otros servicios disponibles, como el servicio Gestión de eventos, el servicio Administrador de usuarios y el servicio Proveedor de correo electrónico, que comparten el grupo de subprocesos del servicio Planificador. Esto puede afectar al rendimiento de la carpeta vigilada. El ajuste del grupo de subprocesos del servicio Planificador será necesario cuando todos los servicios empiecen a utilizarlo.

## Carpetas vigiladas en un clúster {#watched-folders-in-a-cluster}

En un clúster, la carpeta vigilada depende del programador de Quartz y del servicio Administrador de trabajos para el equilibrio de carga y la conmutación por error. Para obtener más información sobre el comportamiento del clúster de Quartz, consulte [Documentación de Quartz](https://www.quartz-scheduler.org/documentation).

Carpeta vigilada realiza estas tres tareas principales en cada encuesta:

* Analizar la carpeta
* Invocar el servicio de destino
* Gestión de los resultados

El equilibrio de carga y el comportamiento de conmutación por error cambian dependiendo de si la carpeta vigilada está configurada para la invocación sincrónica o asincrónica.

### Carpeta vigilada sincrónica en un clúster {#synchronous-watched-folder-in-a-cluster}

Para invocaciones sincrónicas, el equilibrador de carga de Quartz decide qué nodo obtendrá el evento de sondeo. El nodo que obtiene el evento de sondeo realiza todas las tareas siguientes: escanee la carpeta, invoque el servicio de target y gestione los resultados.

![en_synchwatchedfoldercluster](assets/en_synchwatchedfoldercluster.png)

En el caso de invocaciones sincrónicas, cuando falla un nodo, el programador de Quartz envía nuevos eventos de sondeo a otros nodos. Se perderán las invocaciones iniciadas en el nodo fallido. Para obtener más información sobre cómo recuperar los archivos asociados con el trabajo fallido, consulte [Puntos de error y recuperación](configuring-watched-folder-endpoints.md#failure-points-and-recovery).

### Carpeta vigilada asincrónica en un clúster {#asynchronous-watched-folder-in-a-cluster}

Para invocaciones asíncronas, el equilibrador de carga de Quartz decide qué nodo obtendrá el evento de sondeo. El nodo que obtiene el evento de sondeo analizará la carpeta de entrada e invocará el servicio de destino colocando la solicitud en la cola de servicio del administrador de trabajos. El equilibrador de carga del servicio de administrador de trabajos, a su vez, es responsable de decidir qué nodo procesará la solicitud de invocación. Es posible que, aunque el nodo A haya creado la solicitud de invocación, el nodo B termine procesando la solicitud. O el nodo que inició la solicitud de invocación también puede terminar procesando la solicitud.

![en_asynchwatchedfoldercluster](assets/en_asynchwatchedfoldercluster.png)

En el caso de invocaciones asíncronas, cuando falla un nodo, el programador de Quartz envía nuevos eventos de sondeo a otros nodos. Las solicitudes de invocación que se crearon en el nodo fallido estarán en la cola de servicio de Job Manager y se enviarán a otros nodos para su procesamiento. Los archivos para los que no se crean solicitudes de invocación permanecerán en la carpeta de etapa. Para obtener más información sobre cómo recuperar los archivos asociados con el trabajo fallido, consulte [Puntos de error y recuperación](configuring-watched-folder-endpoints.md#failure-points-and-recovery).

## Puntos de error y recuperación {#failure-points-and-recovery}

En cada evento de encuesta, la carpeta inspeccionada bloquea la carpeta de entrada, mueve los archivos que coinciden con el patrón de archivo de inclusión a la carpeta de fase y, a continuación, desbloquea la carpeta de entrada. El bloqueo es necesario para que dos subprocesos no recojan el mismo conjunto de archivos y los procesen dos veces. Las posibilidades de que esto ocurra aumentan con un intervalo de repetición pequeño y un tamaño de lote grande. Tras mover los archivos a la carpeta de fase, la carpeta de entrada se desbloquea para que otros hilos puedan analizar la carpeta. Este paso ayuda a proporcionar un alto rendimiento, ya que otros hilos pueden analizar mientras uno procesa los archivos.

Una vez que los archivos se mueven a la carpeta de fase, las solicitudes de invocación se crean para cada archivo y se invoca el servicio de destino. Puede haber casos en los que la carpeta inspeccionada no pueda recuperar los archivos de la carpeta de fase:

* Si el servidor se apaga antes de que la carpeta inspeccionada pueda crear la solicitud de invocación, los archivos de la carpeta de fase permanecen en la carpeta de fase y no se recuperan.
* Si la carpeta inspeccionada ha creado correctamente la solicitud de invocación para cada uno de los archivos de la carpeta de fase y el servidor se bloquea, hay dos comportamientos basados en el tipo de invocación:

**Sincrónica:** Si la carpeta Watched está configurada para invocar el servicio sincrónicamente, todos los archivos de la carpeta stage permanecen sin procesar en la carpeta stage.

**Asíncrono:** En este caso, la carpeta vigilada depende del servicio Administrador de trabajos. Si el servicio Administrador de trabajos vuelve a llamar a la carpeta inspeccionada, los archivos de la carpeta de fase se mueven a la carpeta de conservación o de errores en función de los resultados de la invocación. Si el servicio Administrador de trabajos no vuelve a llamar a la carpeta inspeccionada, los archivos permanecerán sin procesar en la carpeta de fase. Esta situación ocurre cuando la carpeta inspeccionada no se está ejecutando cuando el administrador de trabajos vuelve a llamar.

### Recuperación de archivos de origen no procesados en la carpeta de escenario {#recovering-unprocessed-source-files-in-the-stage-folder}

Cuando la carpeta inspeccionada no puede procesar los archivos de origen en la carpeta de fase, puede recuperar los archivos sin procesar.

1. Reinicie el servidor de la aplicación o el nodo.
1. (Opcional) Impida que la carpeta vigilada procese nuevos archivos de entrada. Si omite este paso, será mucho más difícil determinar qué archivos no se procesan en la carpeta de fase. Para evitar que la carpeta inspeccionada procese nuevos archivos de entrada, realice una de las siguientes tareas:

   * En Aplicaciones y servicios, cambie el parámetro Incluir patrón de archivo para el extremo de la carpeta vigilada a algo que no coincida con ninguno de los nuevos archivos de entrada (por ejemplo, introduzca `NOMATCH`).
   * Suspenda el proceso que está creando nuevos archivos de entrada.
   Espere hasta que AEM formularios recupere y procese todos los archivos. La mayoría de los archivos deben recuperarse y los nuevos archivos de entrada deben procesarse correctamente. El tiempo que espera para que la carpeta inspeccionada se recupere y procese los archivos dependerá de la duración de la operación que se invoque y del número de archivos que se recuperarán.

1. Determine qué archivos no se pueden procesar. Si ha esperado una cantidad de tiempo adecuada y ha completado el paso anterior, y todavía quedan archivos sin procesar en la carpeta de fase, vaya al paso siguiente.

   >[!NOTE]
   >
   >Puede consultar la marca de fecha y hora de los archivos en el directorio de fase. Según el número de archivos y el tiempo de procesamiento normal, puede determinar qué archivos son lo suficientemente antiguos como para que se consideren atascados.

1. Copie los archivos sin procesar del directorio de fase al directorio de entrada.
1. Si ha impedido que la carpeta inspeccionada procese nuevos archivos de entrada en el paso 2, cambie el patrón de archivo de inclusión a su valor anterior o vuelva a habilitar el proceso que ha deshabilitado.

## Consideraciones de seguridad para carpetas vigiladas {#security-considerations-for-watched-folders}

Cada carpeta vigilada se configura con un nombre de usuario y una contraseña. Estas credenciales se utilizan al invocar los servicios. La carpeta vigilada se basa en el hecho de que la carpeta compartida está protegida con el sistema de archivos de seguridad subyacente, de modo que solo el propietario de la carpeta vigilada puede acceder a la carpeta compartida.

## Sugerencias y trucos para carpetas vigiladas {#tips-and-tricks-for-watched-folders}

A continuación se ofrecen algunos consejos y trucos al configurar el extremo de la carpeta vigilada:

* Si tiene una carpeta vigilada en Windows que esté procesando archivos de imagen, especifique los valores de la opción Incluir patrón de archivo o Excluir patrón de archivo para evitar que la carpeta vigilada sondee el archivo Thumbs.db generado automáticamente por Windows.
* Si se especifica una expresión cron, se ignora el intervalo de repetición. El uso de la expresión cron se basa en el sistema de programación de trabajos de código abierto de Quartz, versión 1.4.0.
* El tamaño del lote es el número de archivos o carpetas que se recogerán en cada análisis de la carpeta vigilada. Si el tamaño del lote se establece en dos y diez archivos o carpetas se sueltan en la carpeta de entrada de la carpeta vigilada, solo se recogerán dos en cada análisis. En el siguiente análisis, que se realizará después del tiempo especificado en el intervalo de repetición, se recogerán los dos archivos siguientes.
* En el caso de los patrones de archivo, los administradores pueden especificar expresiones regulares con compatibilidad añadida a los patrones comodín para especificar los patrones de archivo. La carpeta vigilada modifica la expresión regular para admitir patrones comodín como &amp;ast;.&amp;ast; o &amp;ast;.pdf. Estas expresiones regulares no admiten estos patrones comodín.
* La carpeta vigilada busca en la carpeta de entrada la entrada y no sabe si el archivo o carpeta de origen se copia completamente en la carpeta de entrada antes de comenzar a procesar el archivo o la carpeta. Para asegurarse de que el archivo o la carpeta de origen se copien completamente en la carpeta de entrada de la carpeta vigilada antes de que se recoja el archivo o la carpeta, realice las siguientes tareas:

   * Utilice Tiempo de espera, que es el tiempo en milisegundos que la carpeta observada espera desde la última hora de modificación. Utilice esta función si tiene archivos grandes para procesar. Por ejemplo, si un archivo tarda 10 minutos en descargarse, especifique el tiempo de espera como 10&amp;ast;60 &amp;ast;1000 milisegundos. Esto evitará que la carpeta vigilada recoja el archivo si no es tan antigua como 10 minutos.
   * Utilice el patrón de exclusión de archivos e incluya el patrón de archivo. Por ejemplo, si el patrón de archivo de exclusión es `ex*` y el patrón de archivo de inclusión es `in*`, la carpeta vigilada recogerá los archivos que empiezan por &quot;en&quot; y no recogerá los archivos que comienzan por &quot;ex&quot;. Para copiar archivos o carpetas grandes, cambie primero el nombre del archivo o carpeta para que el nombre comience por &quot;ex&quot;. Después de que el archivo o la carpeta denominada &quot;ex&quot; se copien completamente en la carpeta vigilada, renómbrala a &quot;in&amp;ast;&quot;.

* Utilice la duración de depuración para mantener la carpeta de resultados limpia. La carpeta vigilada limpia todos los archivos que sean anteriores a la duración mencionada en la duración de la depuración. La duración es de días.
* Al agregar un extremo de carpeta vigilada, después de seleccionar el nombre de la operación, se rellena la asignación de parámetros de entrada. Para cada entrada de la operación, se genera un campo de asignación de parámetro de entrada. Estos son ejemplos de asignaciones de parámetros de entrada:

   * Para `com.adobe.idp.Document` entrada: Si la operación de servicio tiene una entrada de tipo `Document`, el administrador puede especificar el tipo de asignación como `Variable`. La carpeta vigilada recogerá la entrada de la carpeta de entrada de la carpeta vigilada en función del patrón de archivo especificado para el parámetro de entrada. Si el administrador especifica `*.pdf` como parámetro, cada archivo que tenga una extensión .pdf se recogerá y se convertirá a `com.adobe.idp.Document`y el servicio invocado.
   * Para `java.util.Map` entrada: Si la operación de servicio tiene una entrada de tipo `Map`, el administrador puede especificar el tipo de asignación como `Variable` e introduzca un valor de asignación con un patrón como `*.pdf`. Por ejemplo, un servicio necesita un mapa de dos `com.adobe.idp.Document` objetos que representan dos archivos en la carpeta de entrada como 1.pdf y 2.pdf. Carpeta vigilada creará un mapa con la clave como nombre de archivo y el valor como `com.adobe.idp.Document`.
   * Para `java.util.List` entrada: Si la operación de servicio tiene una entrada de tipo List, el administrador puede especificar el tipo de asignación como `Variable` e introduzca un valor de asignación con un patrón como `*.pdf`. Cuando se sueltan archivos PDF en la carpeta de entrada, la carpeta vigilada creará una lista de `com.adobe.idp.Document` objetos que representan estos archivos e invocan el servicio de destino.
   * Para `java.lang.String`: El administrador tiene dos opciones. En primer lugar, el administrador puede especificar el tipo de asignación como `Literal` e introduzca un valor de asignación como una cadena, por ejemplo, `hello.` La carpeta vigilada invocará el servicio con la cadena `hello`. En segundo lugar, el administrador puede especificar el tipo de asignación como un `Variable` e introduzca un valor de asignación con un patrón como `*.txt`. En este último caso, los archivos con la extensión .txt se leerán como un documento forzado como una cadena para invocar el servicio.
   * Tipo primitivo de Java: El administrador puede especificar el tipo de asignación como `Literal` y proporcione el valor. La carpeta vigilada invocará el servicio con el valor especificado.

* Carpeta vigilada está diseñada para trabajar con documentos. Los productos admitidos son `com.adobe.idp.Document`, `org.w3c.Document`, `org.w3c.Node`, así como una lista y un mapa de estos tipos. Cualquier otro tipo dará como resultado un error en la carpeta de errores.
* Si los resultados no están en la carpeta de resultados, compruebe la carpeta de errores para ver si se ha producido un error.
* La carpeta vigilada funciona mejor si se utiliza en modo asincrónico. En este modo, la Carpeta vigilada coloca la solicitud de invocación en la cola y vuelve a llamar. A continuación, la cola se procesa asincrónicamente. Cuando la opción Asincrónico no está establecida, la carpeta vigilada invoca el servicio de destino sincrónicamente y el motor de proceso espera hasta que el servicio se realiza con la solicitud y se producen los resultados. Si el servicio de destino tarda mucho en procesar la solicitud, es posible que la carpeta vigilada obtenga errores de tiempo de espera.
* La creación de carpetas vigiladas para operaciones de importación y exportación no permite la abstracción de la extensión del nombre de archivo. Al invocar el servicio de integración de datos de formulario mediante carpetas vigiladas, es posible que el tipo de extensión del nombre del archivo de salida no coincida con el formato de salida deseado para el tipo de objeto de documento. Por ejemplo, si el archivo de entrada de una carpeta vigilada que invoca la operación de exportación es un formulario XFA que contiene datos, el resultado debe ser un archivo de datos XDP. Para obtener un archivo de salida con la extensión de nombre de archivo correcta, puede especificarlo en la asignación de parámetros de salida. En este ejemplo, puede usar %F.xdp para la asignación de parámetros de salida.
* La carpeta vigilada puede procesar archivos de entrada antes de que se copien completamente en la carpeta. El bloqueo de archivos no es obligatorio en UNIX, como en Windows. Por este motivo, cuando se copia un archivo en una carpeta vigilada, esta puede mover el archivo a la etapa de ensayo sin esperar a que se complete la copia del archivo. Este comportamiento hace que solo se procese una parte del archivo de entrada. Actualmente hay dos soluciones alternativas:

   * Solución 1

      1. Especifique un patrón para el patrón de archivo de exclusión, como temp&amp;ast;.ps.
      1. Copie los archivos que empiecen por temp (por ejemplo, temp1.ps) en la carpeta observada.
      1. Una vez que el archivo se haya copiado completamente en la carpeta vigilada, cambie el nombre del archivo para que se corresponda con el patrón especificado para Incluir patrón de archivo. Carpeta vigilada luego mueve el archivo completado a la etapa.
   * Solución 2

      Si sabe cuánto tiempo tardará en copiarse los archivos en una carpeta vigilada, especifique el tiempo en segundos para el tiempo de espera. Carpeta vigilada espera el tiempo especificado antes de mover el archivo a la etapa.

      Esto no supone un problema para los archivos de Windows porque Windows bloquea un archivo cuando se está escribiendo un subproceso. Sin embargo, este es un problema para las carpetas en Windows. Para las carpetas, debe seguir los pasos de Solución 1.


* Si el atributo de extremo Conservar nombre de carpeta para la carpeta vigilada está establecido en una ruta de directorio nula, el directorio de ensayo no se limpia como debería estar. El directorio aún contiene el archivo procesado y la carpeta temporal.

## Recomendaciones específicas del servicio para carpetas vigiladas {#service-specific-recommendations-for-watched-folders}

Para todos los servicios, debe ajustar el tamaño del lote y el intervalo de repetición de la carpeta vigilada, de modo que la velocidad a la que la carpeta vigilada recoge nuevos archivos y carpetas para su procesamiento no supere la velocidad de los trabajos que puede procesar el servidor de formularios AEM. Los parámetros reales que se van a utilizar pueden variar en función de cuántas carpetas vigiladas están configuradas, qué servicios están utilizando carpetas vigiladas y la intensidad de los trabajos en el procesador.

### Generar recomendaciones de servicio de PDF {#generate-pdf-service-recommendations}

* El servicio Generar PDF solo puede convertir un archivo a la vez para estos tipos de archivo: Microsoft Word, Microsoft Excel, Microsoft PowerPoint, Microsoft Project, AutoCAD, Adobe Photoshop®, Adobe FrameMaker® y Adobe PageMaker®. Se trata de trabajos de larga duración; por lo tanto, asegúrese de mantener el tamaño del lote en un valor bajo. Aumente también el intervalo de repetición si hay más nodos en el clúster.
* Para los tipos de archivo PostScript (PS), PostScript encapsulado (EPS) y de imagen, el servicio Generar PDF puede procesar varios archivos en paralelo. Debe ajustar cuidadosamente el tamaño del grupo de media de sesión (que rige el número de conversiones que se realizarán en paralelo) en función de la capacidad del servidor y el número de nodos en el clúster. A continuación, aumente el tamaño del lote a un número que sea igual al tamaño del grupo de media sesión para los tipos de archivo que está intentando convertir. La frecuencia de sondeo debe estar determinada por el número de nodos del clúster; sin embargo, como el servicio Generate PDF procesa estos tipos de trabajos con bastante rapidez, puede configurar el intervalo de repetición a un valor bajo como 5 o 10.
* Aunque el servicio Generate PDF puede convertir sólo un archivo de OpenOffice a la vez, la conversión es bastante rápida. La lógica anterior para las conversiones de PS, EPS e imagen también se aplica a las conversiones de OpenOffice.
* Para permitir una distribución uniforme de la carga en el clúster, mantenga bajo el tamaño del lote y aumente el intervalo de repetición.

### recomendaciones de servicio de formularios con códigos de barras {#barcoded-forms-service-recommendations}

* Para obtener el mejor rendimiento al procesar formularios con códigos de barras (archivos pequeños), introduzca `10` para el tamaño de lote y `2` para Intervalo de repetición.
* Cuando se colocan muchos archivos en la carpeta de entrada, los errores con archivos ocultos se denominan *thumbs.db* puede producirse. Por lo tanto, se recomienda configurar el patrón de archivo de inclusión para los archivos de inclusión con el mismo valor especificado para la variable de entrada (por ejemplo, `*.tiff`). Esto evita que la carpeta vigilada procese los archivos de base de datos.
* Un valor de tamaño de lote de `5` y el intervalo de repetición de `2` normalmente es suficiente, ya que el servicio Forms con códigos de barras suele tardar unos 0,5 segundos en procesar un código de barras.
* La carpeta vigilada no espera a que el motor de proceso finalice el trabajo antes de que recopile nuevos archivos o carpetas. Sigue analizando la carpeta observada e invocando el servicio de destino. Este comportamiento puede sobrecargar el motor, causando problemas de recursos y tiempos de espera. Asegúrese de utilizar el intervalo de repetición y el tamaño del lote para restringir la entrada de la carpeta vigilada. Puede aumentar el intervalo de repetición y reducir el tamaño del lote si existen más carpetas vigiladas o habilitar la limitación en el punto final. Para obtener información sobre la regulación, consulte [Acerca de la restricción](configuring-watched-folder-endpoints.md#about-throttling).
* Carpeta vigilada suplanta al usuario especificado en el nombre de usuario y el nombre de dominio. Carpeta vigilada invoca al servicio como este usuario si se invoca directamente o si el proceso es de corta duración. Para un proceso de larga duración, el proceso se invoca con el contexto del sistema. Los administradores pueden establecer directivas del sistema operativo para la carpeta vigilada a fin de determinar a qué usuario permitir o denegar el acceso.
* Utilice patrones de archivo para organizar resultados, errores y conservar carpetas. (Consulte [Acerca de los patrones de archivo](configuring-watched-folder-endpoints.md#about-file-patterns).)
* La carpeta vigilada depende del programador de Quartz para analizar las carpetas vigiladas. El programador de Quartz tiene un grupo de subprocesos para escanearlos. Si el intervalo de repetición para la carpeta observada es muy bajo (&lt; 5 segundos) y el tamaño del lote es alto (> 2), puede producirse una condición de carrera. Cuando se produce esta condición, dos subprocesos de Quartz recogen un archivo:

   * Uno de los subprocesos encuentra correctamente el archivo e invoca el servicio de destino con el archivo .
   * El segundo subproceso ve el archivo pero falla cuando intenta averiguar si el archivo es válido (archivo de lectura o escritura), lo que provoca errores falsos que indican que el archivo no se puede procesar porque es de solo lectura. Esto solo ocurre con un intervalo de repetición bajo y un tamaño de lote elevado.
