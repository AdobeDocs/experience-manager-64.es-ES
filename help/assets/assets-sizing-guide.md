---
title: Guía de tamaño de recursos
description: 'Prácticas recomendadas para determinar métricas eficientes para estimar la infraestructura y los recursos necesarios para implementar AEM Assets. '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
translation-type: tm+mt
source-git-commit: 6aec5927c00f70ce2c044ffd56cabbf68a81071a
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 0%

---


# Guía de tamaño de recursos {#assets-sizing-guide}

Al ajustar el tamaño del entorno para una implementación de Adobe Experience Manager (AEM) Assets, es importante asegurarse de que hay suficientes recursos disponibles en cuanto a rendimiento de disco, CPU, memoria, E/S y red. Cambiar el tamaño de muchos de estos recursos requiere comprender cuántos recursos se cargan en el sistema. Si no hay una métrica mejor disponible, puede dividir el tamaño de la biblioteca existente por la página de la biblioteca para buscar la velocidad a la que se crean los recursos.

## Disco {#disk}

### Almacén de datos {#datastore}

Un error común que se produce al ajustar el tamaño del espacio de disco necesario para una implementación de Recursos es basar los cálculos en el tamaño de las imágenes sin procesar que se van a ingerir en el sistema. De forma predeterminada, AEM crea tres representaciones además de la imagen original para utilizarlas en la representación de los elementos de la interfaz de usuario AEM. En implementaciones anteriores, se ha observado que estas representaciones suponen el doble del tamaño de los recursos que se ingieren.

La mayoría de los usuarios definen las representaciones personalizadas además de las representaciones predeterminadas. Además de las representaciones, AEM Assets permite extraer subrecursos de tipos de archivo comunes, como InDesign y Illustrator.

Por último, las funciones de control de versiones de AEM almacenan duplicados de los recursos en el historial de versiones. Puede configurar las versiones que se purgarán con frecuencia. Sin embargo, muchos usuarios eligen conservar versiones en el sistema durante mucho tiempo, lo que consume espacio adicional en el almacenamiento.

Teniendo en cuenta estos factores, se requiere una metodología para calcular un espacio de almacenamiento aceptablemente preciso para almacenar los recursos del usuario.

1. Determine el tamaño y el número de recursos que se cargarán en el sistema.
1. Obtenga una muestra representativa de los recursos que se van a cargar en AEM. Por ejemplo, si planea cargar archivos PSD, JPG, AI y PDF en el sistema, necesitará varias imágenes de muestra de cada formato de archivo. Además, estas muestras deben ser representativas de los diferentes tamaños de archivo y de la complejidad de las imágenes.
1. Defina las representaciones que se utilizarán.
1. Cree las representaciones en AEM mediante las aplicaciones de Creative Cloud de ImageMagick o Adobe. Además de las representaciones que especifican los usuarios, cree representaciones listas para usar. Para los usuarios que implementan Scene7, puede utilizar el binario IC para generar las representaciones PTIFF que se almacenarán en AEM.
1. Si planea utilizar subrecursos, genérelos para los tipos de archivo correspondientes. Consulte la documentación en línea sobre cómo generar páginas de subrecursos a partir de archivos de InDesign o archivos PNG/PDF a partir de capas de Illustrator.
1. Compare el tamaño de las imágenes de salida, las representaciones y los subrecursos con las imágenes originales. Permite generar un factor de crecimiento esperado cuando se carga el sistema. Por ejemplo, si genera representaciones y subrecursos con un tamaño combinado de 3 GB después de procesar 1 GB de recursos, el factor de crecimiento de la representación es 3.
1. Determine el tiempo máximo durante el cual se mantendrán las versiones de los recursos en el sistema.
1. Determinar la frecuencia con la que se modifican los recursos existentes en el sistema. Si AEM se utiliza como centro de colaboración en flujos de trabajo creativos, la cantidad de cambios es alta. Si solo se cargan en el sistema los recursos acabados, este número es mucho menor.
1. Determine cuántos recursos se cargan en el sistema cada mes. Si no está seguro, compruebe el número de recursos disponibles actualmente y divida el número por la edad del recurso más antiguo para calcular un número aproximado.

La realización de los pasos 1 a 9 ayuda a determinar lo siguiente:

* Tamaño sin procesar de los recursos que se van a cargar
* Número de recursos que se van a cargar
* Factor de crecimiento de representación
* Número de modificaciones de activos realizadas por mes
* Número de meses para mantener versiones de recursos
* Número de nuevos recursos cargados cada mes
* Años de crecimiento para asignar espacio

Puede especificar estos números en la hoja de cálculo Tamaño de red para determinar el espacio total necesario para el almacén de datos. También es una herramienta útil para determinar el impacto de mantener versiones de recursos o modificar los recursos en el crecimiento de AEM en disco.

Los datos de ejemplo completados en la herramienta muestran la importancia de realizar los pasos mencionados. Si cambia el tamaño del almacén de datos basándose únicamente en las imágenes sin procesar que se están cargando (1 TB), puede que haya subestimado el tamaño del repositorio en un factor de 15.

[Obtener archivo](assets/disk_sizing_tool.xlsx)

### Almacenes de datos compartidos {#shared-datastores}

Para grandes almacenes de datos, puede implementar un almacén de datos compartido a través de un almacén de datos de archivos compartidos en una unidad conectada a la red o a través de un almacén de datos S3. En este caso, las instancias individuales no necesitan mantener una copia de los binarios. Además, un almacén de datos compartido facilita la replicación sin binarios y ayuda a reducir el ancho de banda utilizado para replicar recursos para publicar entornos o descargar instancias.

#### Use Cases {#use-cases}

El almacén de datos se puede compartir entre una instancia de autor principal y en espera para minimizar el tiempo que se tarda en actualizar la instancia en espera con los cambios realizados en la instancia principal. Adobe recomienda compartir el almacén de datos entre una instancia de autor principal y instancias de autor de descarga para reducir los gastos generales en la descarga del flujo de trabajo. También puede compartir el almacén de datos entre el autor y las instancias de publicación para minimizar el tráfico durante la replicación.

#### Desventajas {#drawbacks}

Debido a algunos escollos, no se recomienda compartir un almacén de datos en todos los casos.

#### Punto único de falla {#single-point-of-failure}

Tener un almacén de datos compartido introduce un solo punto de falla en una infraestructura. Imagine un escenario en el que el sistema tiene un autor y dos instancias de publicación, cada una con su propio almacén de datos. Si alguno de ellos se bloquea, los otros dos pueden seguir ejecutándose. Sin embargo, si se comparte el almacén de datos, una única falla de disco puede eliminar toda la infraestructura. Por lo tanto, asegúrese de mantener una copia de seguridad del almacén de datos compartido desde donde puede restaurar el almacén de datos rápidamente.

Es preferible implementar el servicio AWS S3 para los almacenes de datos compartidos porque reduce significativamente la probabilidad de fallo en comparación con las arquitecturas de disco normales.

#### Mayor complejidad {#increased-complexity}

Los almacenes de datos compartidos también aumentan la complejidad de las operaciones, como la recolección de elementos no utilizados. Normalmente, la recolección de elementos no utilizados para un almacén de datos independiente se puede iniciar con un solo clic. Sin embargo, los almacenes de datos compartidos requieren operaciones de barrido de marcas en cada miembro que utilice el almacén de datos, además de ejecutar la colección real en un solo nodo.

Para las operaciones de AWS, la implementación de una única ubicación central (mediante S3), en lugar de crear una matriz RAID de volúmenes EBS, puede compensar significativamente la complejidad y los riesgos operativos del sistema.

#### Problemas de rendimiento {#performance-concerns}

Un almacén de datos compartido requiere que los binarios se almacenen en una unidad montada en red que se comparte entre todas las instancias. Dado que se accede a estos binarios a través de una red, el rendimiento del sistema se ve afectado negativamente. Puede mitigar parcialmente el impacto mediante una conexión de red rápida a un arreglo rápido de discos. Sin embargo, esta es una propuesta cara. En el caso de las operaciones de AWS, todos los discos son remotos y requieren conectividad de red. Los volúmenes efímeros pierden datos cuando la instancia se detiene o inicio.

#### Latencia {#latency}

La latencia en implementaciones S3 se introduce mediante los subprocesos de escritura en segundo plano. Los procedimientos de copia de seguridad deben tener en cuenta esta latencia y los procedimientos de descarga. Es posible que el recurso S3 no esté presente en S3 cuando inicio un trabajo de descarga. Además, los índices de Lucene pueden estar incompletos al realizar una copia de seguridad. Se aplica a cualquier archivo con distinción de tiempo escrito en el almacén de datos S3 y al que se acceda desde otra instancia.

### Tienda de nodos/almacén de Documentos {#node-store-document-store}

Es difícil obtener cifras precisas de tamaño para un NodeStore o DocumentStore debido a los recursos que consumen los siguientes:

* Metadatos del recurso
* Versiones de recursos
* Registros de auditoría
* flujos de trabajo archivados y activos

Dado que los binarios se almacenan en el almacén de datos, cada binario ocupa algún espacio. La mayoría de los repositorios tienen un tamaño inferior a 100 GB. Sin embargo, es posible que haya repositorios más grandes de hasta 1 TB de tamaño. Además, para realizar una compactación sin conexión, se necesita suficiente espacio libre en el volumen para reescribir el repositorio compactado junto con la versión compactada previamente. Una buena regla general es ajustar el tamaño del disco a 1,5 veces el tamaño esperado para el repositorio.

Para el repositorio, utilice discos SSD o discos con un nivel de IOPS bueno a 3000. Para eliminar las posibilidades de que IOPS introduzca cuellos de botella en el rendimiento, supervise los niveles de espera de E/S de CPU para detectar los primeros signos de problemas.

[Obtener archivo](assets/aem_environment_sizingtool.xlsx)

## Red {#network}

AEM Assets tiene una serie de casos de uso que hacen que el rendimiento de la red sea más importante que en muchos de nuestros proyectos AEM. Un cliente puede tener un servidor rápido, pero si la conexión de red no es lo suficientemente grande como para admitir la carga de los usuarios que cargan y descargan recursos del sistema, entonces seguirá siendo lenta. Existe una buena metodología para determinar el punto de interrupción en la conexión de red de un usuario a AEM en [AEM consideraciones de recursos para la experiencia del usuario, tamaño de instancia, evaluación del flujo de trabajo y topología](assets-network-considerations.md)de red.

## WebDAV {#webdav}

Si agrega la aplicación de escritorio AEM a la combinación, los problemas de red se agravan debido a las ineficiencias del protocolo WebDAV.

Para ilustrar estas ineficiencias, Adobe probó el rendimiento del sistema mediante WebDAV en OS X. Se ha abierto, editado y guardado un archivo InDesign de 3,5 MB. Se formularon las siguientes observaciones:

* Se generaron alrededor de 100 solicitudes HTTP para completar la operación
* El archivo se cargó cuatro veces a través de HTTP
* El archivo se descargó una vez a través de HTTP
* La operación completa tardó 42 segundos en completarse
* Se movió un total de 18 MB de datos

Al analizar el tiempo de ahorro promedio para los archivos a través de WebDAV, se descubrió que el rendimiento aumenta considerablemente a medida que el ancho de banda aumenta hasta el nivel de 5 a 10 Mbps. Por lo tanto, Adobe recomienda que cada usuario que acceda al sistema simultáneamente tenga al menos 10 Mbps de velocidad de carga y un ancho de banda de 5 a 10 Mbps.

Para obtener más información, consulte [Resolución de problemas de AEM aplicación](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)de escritorio.

## Restricciones     {#limitations}

Al ajustar el tamaño de una implementación, es importante tener en cuenta las limitaciones del sistema. Si la implementación propuesta supera estas limitaciones, utilice estrategias creativas, como la partición de los recursos en varias implementaciones de Recursos.

El tamaño del archivo no es el único factor que contribuye a problemas de memoria insuficiente (OOM). También depende de las dimensiones de la imagen. Puede evitar problemas con OOM proporcionando un tamaño de pila más alto cuando inicio AEM.

Además, puede editar la propiedad de tamaño de umbral del `com.day.cq.dam.commons.handler.StandardImageHandler` componente en Configuration Manager para utilizar un archivo temporal intermedio bueno a cero.

## Número máximo de recursos {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

El límite en el número de archivos que pueden existir en un almacén de datos puede ser de 2.1 billones debido a las limitaciones del sistema de archivos. Es probable que el repositorio encuentre problemas debido a un gran número de nodos mucho antes de alcanzar el límite del almacén de datos.

Si las representaciones no se generan correctamente, utilice la biblioteca Camera Raw. Sin embargo, en este caso, el lado más largo de la imagen no debe ser bueno de 65000 píxeles. Además, la imagen no debe contener más de 512 MP (512 &amp;ast;) 1024 &amp;ast; 1024 píxeles)&#39;. *El tamaño del recurso es insignificante*.

Es difícil estimar con precisión el tamaño del archivo TIFF admitido de forma predeterminada (OOTB) con un montón específico para AEM, ya que factores adicionales, como el procesamiento de la influencia del tamaño de los píxeles. Es posible que AEM procesar un archivo de tamaño de 255 MB OOTB, pero no puede procesar un tamaño de archivo de 18 MB porque este último consta de un número inusualmente mayor de píxeles en comparación con el primero.

## Tamaño de los recursos {#size-of-assets}

De forma predeterminada, AEM permite cargar recursos de tamaños de archivo de hasta 2 GB. Para cargar recursos muy grandes en AEM, consulte [Configuración para cargar recursos](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)muy grandes.
