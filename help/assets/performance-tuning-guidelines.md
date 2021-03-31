---
title: Guía de ajuste del rendimiento de los activos
description: Áreas de enfoque clave en AEM configuración, cambios en hardware, software y componentes de red para eliminar cuellos de botella y optimizar el rendimiento de AEM Assets.
contentOwner: AG
feature: Administración de activos
role: Arquitecto,Administrador
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '3210'
ht-degree: 0%

---


# Guía de ajuste del rendimiento de los activos {#assets-performance-tuning-guide}

Una configuración de Adobe Experience Manager (AEM) Assets contiene varios componentes de hardware, software y red. Según el escenario de implementación, es posible que necesite cambios específicos en la configuración del hardware, software y componentes de red para eliminar los cuellos de botella en el rendimiento.

Además, la identificación y el cumplimiento de ciertas directrices de optimización de hardware y software ayudan a crear una base sólida que permite que la implementación de AEM Assets cumpla con las expectativas de rendimiento, escalabilidad y fiabilidad.

Un rendimiento deficiente en AEM Assets puede afectar a la experiencia del usuario en cuanto al rendimiento interactivo, el procesamiento de recursos, la velocidad de descarga y otras áreas.

De hecho, la optimización del rendimiento es una tarea fundamental que se realiza antes de establecer métricas de objetivo para cualquier proyecto.

Estas son algunas áreas clave en las que puede descubrir y solucionar problemas de rendimiento antes de que afecten a los usuarios.

## Plataforma {#platform}

Aunque AEM es compatible con varias plataformas, el Adobe ha encontrado el soporte bueno para herramientas nativas en Linux y Windows, lo que contribuye a un rendimiento óptimo y a la facilidad de implementación. Lo ideal es implementar un sistema operativo de 64 bits para satisfacer los altos requerimientos de memoria de una implementación de AEM Assets. Al igual que con cualquier implementación AEM, debe implementar TarMK siempre que sea posible. Aunque TarMK no puede escalar más allá de una única instancia de autor, se ha descubierto que funciona mejor que MongoMK. Puede añadir instancias de descarga de TarMK para aumentar el poder de procesamiento del flujo de trabajo de la implementación de AEM Assets.

### Carpeta temporal {#temp-folder}

Para mejorar los tiempos de carga de los recursos, utilice almacenamiento de alto rendimiento para el directorio temporal de Java. En Linux y Windows, se puede utilizar una unidad RAM o SSD. En entornos basados en la nube, se podría utilizar un tipo de almacenamiento de alta velocidad equivalente. Por ejemplo, en Amazon EC2, se puede utilizar una unidad [efemeral](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) para la carpeta temporal.

Si el servidor tiene suficiente memoria, configure una unidad RAM. En Linux, ejecute estos comandos para crear una unidad RAM de 8 GB:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

En el sistema operativo Windows, tendría que usar un controlador de terceros para crear una unidad RAM o simplemente usar almacenamiento de alto rendimiento como SSD.

Una vez que el volumen temporal de alto rendimiento esté listo, establezca el parámetro JVM -Djava.io.tmpdir. Por ejemplo, puede agregar el parámetro JVM a continuación a la variable CQ_JVM_OPTS en el script bin/start de AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Configuración de Java {#java-configuration}

### Versión de Java {#java-version}

Como Oracle dejó de publicar actualizaciones para Java 7 en abril de 2015, Adobe recomienda implementar AEM Assets en Java 8. En algunos casos, ha demostrado un mejor rendimiento.

### Parámetros de JVM {#jvm-parameters}

Debe configurar los siguientes parámetros de JVM:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=verdadero

## Almacenamiento de datos y configuración de memoria {#data-store-and-memory-configuration}

### Configuración del almacén de datos de archivo {#file-data-store-configuration}

Se recomienda separar el almacén de datos del almacén de segmentos para todos los usuarios de AEM Assets. Además, la configuración de los parámetros `maxCachedBinarySize` y `cacheSizeInMB` puede ayudar a maximizar el rendimiento. Establezca `maxCachedBinarySize` en el tamaño de archivo más pequeño que se pueda guardar en la caché. Especifique el tamaño de la caché en memoria que se utilizará para el almacén de datos en `cacheSizeInMB`. Adobe recomienda establecer este valor entre el 2 % y el 10 % del tamaño total de pila. Sin embargo, las pruebas de carga/rendimiento pueden ayudar a determinar la configuración ideal.

### Configure el tamaño máximo de la caché de imágenes almacenada en búfer {#configure-the-maximum-size-of-the-buffered-image-cache}

Al cargar grandes cantidades de recursos en Adobe Experience Manager, para permitir picos inesperados en el consumo de memoria y para evitar que JVM falle con OutOfMemoryErrors, reduzca el tamaño máximo configurado de la caché de imágenes almacenada en búfer. Tomemos un ejemplo de que tiene un sistema con una pila máxima (- `Xmx`param) de 5 GB, un Oak BlobCache establecido en 1 GB y una caché de documentos de 2 GB. En este caso, la caché almacenada en búfer tomaría un máximo de 1,25 GB y memoria, lo que dejaría solo 0,75 GB de memoria para picos inesperados.

Configure el tamaño de caché en búfer en la consola web OSGi. En `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, establezca la propiedad `cq.dam.image.cache.max.memory` en bytes. Por ejemplo, 1073741824 es 1 GB (1024 x 1024 x 1024 = 1 GB).

Desde AEM 6.1 SP1, si utiliza un nodo `sling:osgiConfig` para configurar esta propiedad, asegúrese de establecer el tipo de datos en Long. Para obtener más información, consulte [CQBufferedImageCache consume mucho durante las cargas de recursos](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Almacenes de datos compartidos {#shared-data-stores}

La implementación de un almacén de datos de archivos compartidos o S3 puede ayudar a ahorrar espacio en disco y aumentar el rendimiento de la red en implementaciones a gran escala. Para obtener más información sobre las ventajas y desventajas de utilizar un almacén de datos compartido, consulte [Guía de tamaño de recursos](assets-sizing-guide.md).

### Almacén de datos S3 {#s-data-store}

La siguiente configuración del almacén de datos S3 ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) ayudó a extraer en Adobe 12,8 TB de objetos grandes binarios (BLOB) de un almacén de datos de archivos existente en un almacén de datos S3 en un sitio del cliente:

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Optimización de red {#network-optimization}

Adobe recomienda habilitar HTTPS porque muchas empresas tienen cortafuegos que olfatean el tráfico HTTP, lo que afecta negativamente a las cargas y corrompe los archivos. Para cargas de archivos grandes, asegúrese de que los usuarios tengan conexiones cableadas a la red porque una red WiFi se satura rápidamente. Para obtener instrucciones sobre cómo identificar los cuellos de botella de la red, consulte [Guía de tamaño de los recursos](assets-sizing-guide.md). Para evaluar el rendimiento de la red analizando la topología de la red, consulte [Consideraciones de la red de recursos](assets-network-considerations.md).

Principalmente, la estrategia de optimización de la red depende de la cantidad de ancho de banda disponible y de la carga en la instancia de AEM. Las opciones de configuración comunes, incluidos los cortafuegos o los proxies, pueden ayudar a mejorar el rendimiento de la red. Estos son algunos puntos clave a tener en cuenta:

* Dependiendo del tipo de instancia (pequeño, moderado, grande), asegúrese de que tiene suficiente ancho de banda de red para su instancia de AEM. Una asignación adecuada del ancho de banda es especialmente importante si AEM está alojado en AWS.
* Si la instancia de AEM está alojada en AWS, puede beneficiarse de tener una política de escalado versátil. Actualice la instancia si los usuarios esperan una carga alta. Desactívelo para una carga moderada/baja.
* HTTPS: La mayoría de los usuarios tienen cortafuegos que olfatean el tráfico HTTP, lo que puede afectar negativamente a la carga de archivos o incluso a los archivos dañados durante la operación de carga.
* Cargas de archivos grandes: Asegúrese de que los usuarios tengan conexiones cableadas a la red (las conexiones WiFi se saturan rápidamente).

## Flujos de trabajo {#workflows}

### Flujos de trabajo transitorios {#transient-workflows}

Siempre que sea posible, establezca el flujo de trabajo de recursos de actualización de DAM en Transient. La configuración reduce significativamente los gastos generales necesarios para procesar flujos de trabajo porque, en este caso, los flujos de trabajo no necesitan pasar por los procesos normales de seguimiento y archivo.

>[!NOTE]
>
>De forma predeterminada, el flujo de trabajo de recursos de actualización de DAM está establecido en Transient en AEM 6.3. En este caso, puede omitir el siguiente procedimiento.

1. Abra `http://localhost:4502/miscadmin` en la instancia de AEM que desee configurar.

1. En el árbol de navegación, expanda **[!UICONTROL Herramientas]** > **[!UICONTROL Flujo de trabajo]** > **[!UICONTROL Modelos]** > **[!UICONTROL Dam]**.
1. Haga doble clic en **[!UICONTROL Recurso de actualización de DAM]**.
1. En el panel de herramientas flotante, cambie a la ficha **[!UICONTROL Página]** y haga clic en **[!UICONTROL Propiedades de página]**.
1. Seleccione **[!UICONTROL Flujo de trabajo transitorio]** Haga clic en **[!UICONTROL Aceptar]**.

   >[!NOTE]
   >
   >Algunas funciones no admiten flujos de trabajo transitorios. Si la implementación de AEM Assets requiere estas funciones, no configure flujos de trabajo transitorios.

   En los casos en los que no se puedan utilizar flujos de trabajo transitorios, ejecute el flujo de trabajo purgando regularmente para eliminar los flujos de trabajo archivados de recursos de actualización de DAM para garantizar que el rendimiento del sistema no se degrade.

   Normalmente, se deben ejecutar flujos de trabajo de depuración semanalmente. Sin embargo, en escenarios con gran densidad de recursos, como durante la ingesta de recursos a gran escala, puede ejecutarlo con mayor frecuencia.

   Para configurar la depuración del flujo de trabajo, añada una nueva configuración de Adobe Granite Workflow Purge a través de la consola OSGi. A continuación, configure y programe el flujo de trabajo como parte de la ventana de mantenimiento semanal.

   Si la depuración se ejecuta durante demasiado tiempo, se agota el tiempo de espera. Por lo tanto, debe asegurarse de que los trabajos de depuración se completen para evitar situaciones en las que los flujos de trabajo de depuración no se completen debido al alto número de flujos de trabajo.

   Por ejemplo, después de ejecutar numerosos flujos de trabajo no transitorios (que crean nodos de instancia de flujo de trabajo), puede ejecutar el [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) según sea necesario. Elimina inmediatamente las instancias de flujo de trabajo redundantes y completadas en lugar de esperar a que se ejecute el programador de purga de flujo de trabajo de Granite de Adobe.

### Máximo de trabajos paralelos {#maximum-parallel-jobs}

De forma predeterminada, AEM ejecuta un número máximo de trabajos paralelos igual al número de procesadores en el servidor. El problema con esta configuración es que durante períodos de carga pesada, todos los procesadores están ocupados por flujos de trabajo de recursos de actualización de DAM, lo que ralentiza la capacidad de respuesta de la interfaz de usuario e impide que los AEM ejecuten otros procesos que salvaguardan el rendimiento y la estabilidad del servidor. Como práctica recomendada, establezca este valor en la mitad de los procesadores disponibles en el servidor realizando los siguientes pasos:

1. En AEM Author, vaya a [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Haga clic en Editar en cada cola de flujo de trabajo que sea relevante para la implementación, por ejemplo, cola de flujo de trabajo transitorio de Granite.
1. Cambie el valor de Máximo de trabajos paralelos y haga clic en Guardar.

Establecer una cola para la mitad de los procesadores disponibles es una solución viable para empezar. Sin embargo, es posible que tenga que aumentar o reducir este número para lograr el máximo rendimiento y ajustarlo por entorno. Existen colas independientes para flujos de trabajo transitorios y no transitorios, así como otros procesos, como flujos de trabajo externos. Si varias colas configuradas en el 50% de los procesadores están activos simultáneamente, el sistema puede sobrecargarse rápidamente. Las colas que se utilizan con frecuencia varían considerablemente entre las implementaciones de los usuarios. Por lo tanto, es posible que tenga que configurarlos cuidadosamente para lograr la máxima eficiencia sin sacrificar la estabilidad del servidor.

### Descarga {#offloading}

Para flujos de trabajo de gran volumen o flujos de trabajo que requieren muchos recursos, como la transcodificación de vídeo, puede descargar los flujos de trabajo de recursos de actualización de DAM en una segunda instancia de creación. A menudo, el problema con la descarga es que cualquier carga que se guarde descargando el procesamiento del flujo de trabajo se compensa con el coste de replicar el contenido de un lado a otro entre instancias.

A partir de AEM 6.2 y con un paquete de funciones para AEM 6.1, puede realizar la descarga con replicación sin binarios. En este modelo, las instancias de autor comparten un almacén de datos común y solo envían los metadatos de una y otra vez mediante la replicación de reenvío. Aunque este método funciona bien con un almacén de datos de archivos compartidos, puede haber problemas con un almacén de datos S3. Debido a que los subprocesos de escritura en segundo plano pueden inducir latencia, es posible que un recurso no se haya escrito en el almacén de datos antes de que se inicie el trabajo de descarga.

### Configuración de recursos de actualización de DAM {#dam-update-asset-configuration}

El flujo de trabajo de recursos de actualización de DAM contiene un conjunto completo de pasos que se configuran para tareas como la generación de Dynamic Media Classic PTIFF y la integración de InDesigns Server. Sin embargo, es posible que la mayoría de los usuarios no necesiten varios de estos pasos. Adobe recomienda crear una copia personalizada del modelo de flujo de trabajo de DAM Update Asset y eliminar los pasos innecesarios. En este caso, actualice los lanzadores de DAM Update Asset para que apunten al nuevo modelo.

>[!NOTE]
>
>La ejecución intensiva del flujo de trabajo de recursos de actualización de DAM puede aumentar considerablemente el tamaño del almacén de datos del archivo. Los resultados de un experimento realizado por Adobe han demostrado que el tamaño del almacén de datos puede aumentar aproximadamente en 400 GB si se realizan alrededor de 5500 flujos de trabajo en un plazo de 8 horas.
>
>Es un aumento temporal y el almacén de datos se restaura a su tamaño original después de ejecutar la tarea de recolección de residuos del almacén de datos.
>
>Normalmente, la tarea de recolección de basura del almacén de datos se ejecuta semanalmente junto con otras tareas de mantenimiento programadas.
>
>Si tiene un espacio de disco limitado y ejecuta los flujos de trabajo de recursos de actualización de DAM intensamente, considere la posibilidad de programar la tarea de colección de residuos con más frecuencia.

#### Generación de representación en tiempo de ejecución {#runtime-rendition-generation}

Los clientes utilizan imágenes de diversos tamaños y formatos en su sitio web o para su distribución a socios comerciales. Dado que cada representación se añade a la huella del recurso en el repositorio, Adobe recomienda utilizar esta función con cautela. Para reducir la cantidad de recursos necesarios para procesar y almacenar imágenes, puede generar estas imágenes en tiempo de ejecución en lugar de como representaciones durante la ingesta.

Muchos clientes de Sites implementan un servlet de imagen que cambia el tamaño y recorta las imágenes en el momento en que se solicitan, lo que impone una carga adicional en la instancia de publicación. Sin embargo, mientras estas imágenes se puedan almacenar en caché, el desafío se puede mitigar.

Un enfoque alternativo es utilizar la tecnología Dynamic Media Classic para transferir por completo la manipulación de imágenes. Además, puede implementar Brand Portal que no solo asuma las responsabilidades de generación de representación de la infraestructura de AEM, sino también todo el nivel de publicación.

#### ImageMagick {#imagemagick}

Si personaliza el flujo de trabajo de recursos de actualización de DAM para generar representaciones mediante ImageMagick, Adobe recomienda modificar el archivo policy.xml en */etc/ImageMagick/*. De forma predeterminada, ImageMagick utiliza todo el espacio de disco disponible en el volumen del sistema operativo y la memoria disponible. Realice los siguientes cambios de configuración dentro de la sección `policymap` de policy.xml para limitar estos recursos.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Además, establezca la ruta de la carpeta temporal de ImageMagick en el archivo *configure.xml* (o estableciendo la variable de entorno `MAGIC_TEMPORARY_PATH`) en una partición de disco que tenga suficiente espacio y IOPS.

>[!CAUTION]
>
>Una mala configuración puede hacer que su servidor sea inestable si ImageMagick utiliza todo el espacio disponible en disco. Los cambios de política necesarios para procesar archivos de gran tamaño con ImageMagick pueden afectar al rendimiento del AEM. Para obtener más información, consulte [instalar y configurar ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>Los archivos ImageMagick `policy.xml` y `configure.xml` se pueden encontrar en `/usr/lib64/ImageMagick-*/config/` en lugar de en `/etc/ImageMagick/`. Consulte la [documentación de ImageMagick](https://www.imagemagick.org/script/resources.php) para obtener más información sobre las ubicaciones de los archivos de configuración.

Si utiliza AEM en Adobe Managed Services (AMS), póngase en contacto con el Servicio de atención al cliente de Adobe si tiene previsto procesar muchos archivos PSD o PSB de gran tamaño. Es posible que el Experience Manager no procese archivos PSB de alta resolución que superen los 30000 x 23000 píxeles.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP escritura {#xmp-writeback}

XMP reescritura actualiza el recurso original cada vez que se modifican los metadatos en AEM, lo que resulta en lo siguiente:

* El recurso en sí se modifica
* Se crea una versión del recurso
* Recurso de actualización DAM se ejecuta con el recurso

Los resultados enumerados consumen recursos considerables. Por lo tanto, Adobe recomienda [desactivar XMP escritura](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html) si no es necesaria.

La importación de una gran cantidad de metadatos puede resultar en una actividad de escritura de XMP intensiva en recursos si se marca el indicador de flujos de trabajo de ejecución. Planifique una importación de este tipo durante el uso del servidor liviano para que el rendimiento de otros usuarios no se vea afectado.

## Replicación {#replication}

Al replicar recursos en un gran número de instancias de publicación, por ejemplo en una implementación de Sites, Adobe recomienda utilizar la replicación en cadena. En este caso, la instancia de autor se duplica en una sola instancia de publicación que, a su vez, se duplica en las otras instancias de publicación, lo que libera la instancia de autor.

### Configurar la replicación en cadena {#configure-chain-replication}

1. Elija la instancia de publicación que desea utilizar para encadenar las réplicas a
1. En esa instancia de publicación agregue agentes de replicación que apunten a las otras instancias de publicación
1. En cada uno de esos agentes de replicación, habilite **[!UICONTROL On Receive]** en la pestaña **[!UICONTROL Déclencheur]**

>[!NOTE]
>
>Adobe no recomienda la activación automática de recursos. Sin embargo, si es necesario, Adobe recomienda hacer esto como el último paso de un flujo de trabajo, normalmente Recurso de actualización DAM.

## Índices de búsqueda {#search-indexes}

Asegúrese de implementar los service packs más recientes y las correcciones relacionadas con el rendimiento, ya que a menudo incluyen actualizaciones en los índices del sistema. Consulte [Consejos de ajuste del rendimiento | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) para algunas optimizaciones de índice que se pueden aplicar, según su versión de AEM.

Cree índices personalizados para consultas que ejecuta a menudo. Para obtener más información, consulte [metodología para analizar consultas lentas](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) y [creación de índices personalizados](/help/sites-deploying/queries-and-indexing.md). Para obtener más información sobre las prácticas recomendadas de consulta e índice, consulte [Prácticas recomendadas para consultas e indexación](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Configuraciones de índice de Lucene {#lucene-index-configurations}

Se pueden realizar algunas optimizaciones en las configuraciones de índice Oak que pueden ayudar a mejorar el rendimiento de AEM Assets:

Actualice la configuración de LuceneIndexProvider:

1. Vaya a /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Habilite **[!UICONTROL CopyOnRead , CopyOnWrite y Archivos de índice de recuperación previa]** en versiones anteriores a AEM 6.2. Estos valores están habilitados de forma predeterminada en AEM 6.2 y versiones posteriores.

Actualice las configuraciones de índice para mejorar el tiempo de reindexación:

1. Abra CRXDe /crx/de/index.jsp e inicie sesión como usuario administrativo
1. Vaya a /oak:index/lucene
1. Agregue una propiedad String[] denominada **[!UICONTROL excludedPaths]** con los valores &quot;/var&quot;, &quot;/etc/workflow/instances&quot; y &quot;/etc/replication&quot;
1. Vaya a /oak:index/damAssetLucene
1. Agregue una propiedad String[] denominada **[!UICONTROL includedPaths]** con un valor &quot;/content/dam&quot;
1. Guardar

(solo AEM6.1 y 6.2) Actualice el índice ntBaseLucene para mejorar el rendimiento de eliminación y movimiento de recursos:

1. Vaya a */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Agregue dos nodos nt:unstructured **[!UICONTROL slingResource]** y **[!UICONTROL damResolvedPath]** en */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Establezca las propiedades siguientes en los nodos (donde las propiedades ordered y propertyIndex son de tipo *Boolean*:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvePath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. En el nodo /oak:index/ntBaseLucene, establezca la propiedad `reindex=true`
1. Haga clic en **[!UICONTROL Guardar todo]**
1. Supervise el archivo error.log para ver cuándo se completa la indexación:

   Se completó la reindexación de los índices: [/oak:index/ntBaseLucene]

1. También puede ver que la indexación se completa actualizando el nodo /oak:index/ntBaseLucene en CRXDe, ya que la propiedad reindex volvería a ser false
1. Una vez finalizada la indexación, vuelva a CRXDe y establezca la propiedad **[!UICONTROL type]** como deshabilitada en estos dos índices

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Haga clic en **[!UICONTROL Guardar todo]**

Desactive la extracción de texto de Lucene:

Si los usuarios no necesitan poder buscar en el contenido de los recursos, por ejemplo, buscando el texto contenido en documentos PDF, puede mejorar el rendimiento del índice desactivando esta función.

1. Vaya al administrador de paquetes AEM /crx/packmgr/index.jsp
1. Cargue e instale el paquete siguiente

[Obtener archivo](assets/disable_indexingbinarytextextraction-10.zip)

### Total de hipótesis {#guess-total}

Al crear consultas que generen grandes conjuntos de resultados, utilice el parámetro `guessTotal` para evitar una gran utilización de la memoria al ejecutarlas.

## Problemas conocidos {#known-issues}

### Archivos grandes {#large-files}

Hay dos problemas conocidos principales relacionados con archivos grandes en AEM. Cuando los archivos alcanzan tamaños buenos de más de 2 GB, la sincronización en espera en frío puede encontrarse con una situación de falta de memoria. En algunos casos, evita que se ejecute la sincronización en espera. En otros casos, provoca que la instancia principal se bloquee. Este escenario se aplica a cualquier archivo de AEM que tenga más de 2 GB, incluidos los paquetes de contenido.

Del mismo modo, cuando los archivos alcanzan el tamaño de 2GB mientras se utiliza un almacén de datos S3 compartido, puede tardar algún tiempo en que el archivo se mantenga completamente desde la caché al sistema de archivos. Como resultado, cuando se utiliza la replicación sin binarios, es posible que los datos binarios no se hayan mantenido antes de que se complete la replicación. Esta situación puede dar lugar a problemas, especialmente si la disponibilidad de los datos es importante, por ejemplo en escenarios de descarga.

## Pruebas de rendimiento {#performance-testing}

Para cada implementación AEM, establezca un régimen de pruebas de rendimiento que pueda identificar y resolver cuellos de botella rápidamente. Aquí hay algunas áreas clave en las que centrarse.

### Pruebas de red {#network-testing}

Para todos los problemas de rendimiento de la red del cliente, realice las siguientes tareas:

* Probar el rendimiento de la red desde la red del cliente
* Pruebe el rendimiento de la red desde la red de Adobe. Para los clientes de AMS, trabaje con su CSE para realizar pruebas desde la red de Adobe.
* Probar el rendimiento de la red desde otro punto de acceso
* Utilizando una herramienta de referencia de red
* Realización de pruebas con Dispatcher

### Prueba de instancias de AEM {#aem-instance-testing}

Para minimizar la latencia y lograr un alto rendimiento mediante la utilización eficiente de la CPU y el uso compartido de la carga, supervise el rendimiento de su instancia de AEM regularmente. En particular:

* Ejecute pruebas de carga con la instancia de AEM
* Monitorización del rendimiento de carga y la capacidad de respuesta de la interfaz de usuario

## Lista de comprobación de rendimiento de AEM Assets {#aem-assets-performance-checklist}

* Habilite HTTPS para evitar cualquier husmeador de tráfico HTTP corporativo.
* Utilice una conexión por cable para la carga pesada de recursos.
* Establezca parámetros óptimos de JVM.
* Configure un almacén de datos de sistema de archivos o un almacén de datos S3.
* Deshabilite la generación de subrecursos. Si está activado, AEM flujo de trabajo crea un recurso independiente para cada página en un recurso de varias páginas. Cada una de estas páginas es un recurso individual que consume espacio en disco adicional, requiere control de versiones y procesamiento adicional del flujo de trabajo. Si no necesita páginas independientes, deshabilite la generación de subrecursos y las actividades de extracción de páginas.
* Habilitar flujos de trabajo transitorios.
* Ajuste las colas del flujo de trabajo de Granite para limitar los trabajos simultáneos.
* Configure ImageMagick para limitar el consumo de recursos.
* Elimine los pasos innecesarios del flujo de trabajo de recursos de actualización de DAM .
* Configure el flujo de trabajo y la depuración de versiones.
* Optimice la configuración del índice de Lucene.
* Optimice los índices con los service packs y las revisiones más recientes. Consulte con el Servicio de atención al cliente de Adobe si hay optimizaciones de índice adicionales que puedan estar disponibles.
* Utilice `guessTotal` para optimizar el rendimiento de las consultas.
* Si configura AEM para detectar tipos de archivo a partir del contenido de los archivos (configurando [!UICONTROL Day CQ DAM Mime Type Service] en [!UICONTROL AEM Web Console]), cargue muchos archivos de forma masiva durante las horas de menor afluencia, ya que la operación requiere muchos recursos.
