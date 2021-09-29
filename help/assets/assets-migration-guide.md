---
title: Migrar recursos a Adobe Experience Manager Assets de forma masiva
description: Cómo introducir recursos en AEM, aplicar metadatos, generar representaciones y activarlos para publicar instancias.
contentOwner: AG
feature: Migration,Renditions,Asset Management
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '1772'
ht-degree: 8%

---

# Guía de migración de recursos {#assets-migration-guide}

A la hora de migrar recursos a AEM, hay que tener en cuenta varios pasos. La extracción de recursos y metadatos de su página principal actual está fuera del ámbito de este documento, ya que varía ampliamente entre implementaciones. En su lugar, este documento describe cómo incorporar estos recursos a AEM, aplicar sus metadatos, generar representaciones y activar o publicar los recursos.

## Requisitos previos {#prerequisites}

Antes de realizar cualquiera de los pasos descritos a continuación, revise e implemente las directrices en [Consejos de ajuste del rendimiento de los recursos](performance-tuning-guidelines.md). Muchos pasos, como configurar el máximo de trabajos simultáneos, mejoran la estabilidad y el rendimiento del servidor bajo carga. Otros pasos, como la configuración del almacén de datos de archivos, son difíciles de realizar una vez que el sistema se ha cargado con recursos.

>[!NOTE]
>
>Las siguientes herramientas de migración de recursos no forman parte de Adobe Experience Manager. El Servicio de atención al cliente de Adobe no admite estas herramientas.
>
>* ACS [!DNL Experience Manager] Herramientas Tag Maker
>* Importador de recursos CSV de herramientas de ACS [!DNL Experience Manager]
>* Administrador de flujo de trabajo masivo de ACS Commons
>* Administrador de acción rápida de ACS Commons
>* Flujo de trabajo sintético

>
>Este software es de código abierto y está cubierto por la [Licencia de ](https://adobe-consulting-services.github.io/pages/license.html)Apache v2. Para hacer una pregunta o informar de un problema, visite los respectivos [ [!DNL Experience Manager] problemas de GitHub para ACS Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) y [ [!DNL Experience Manager] ACS Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrar a [!DNL Experience Manager] {#migrate-to-aem}

La migración de recursos a [!DNL Experience Manager] requiere varios pasos y debe verse como un proceso por fases. Las fases de la migración son las siguientes:

1. Desactivar flujos de trabajo.
1. Cargar etiquetas.
1. Ingesta de recursos.
1. Procese representaciones.
1. Activar recursos.
1. Habilitar flujos de trabajo.

![chlimage_1-223](assets/chlimage_1-223.png)

### Desactivación de flujos de trabajo {#disable-workflows}

Antes de iniciar una migración, deshabilite los iniciadores para el flujo de trabajo `DAM Update Asset` . Es mejor ingerir todos los recursos en el sistema y luego ejecutar los flujos de trabajo por lotes. Si ya está activo mientras se realiza la migración, puede programar que estas actividades se ejecuten durante las horas de inactividad.

### Cargar etiquetas {#load-tags}

Es posible que ya tenga una taxonomía de etiquetas en su lugar de aplicación a las imágenes. Las herramientas como el Importador de recursos CSV y la funcionalidad de perfiles de metadatos pueden ayudar a automatizar la aplicación de etiquetas a los recursos. Antes de esto, añada las etiquetas en el Experience Manager . La función [ACS [!DNL Experience Manager] Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) permite rellenar las etiquetas utilizando una hoja de cálculo de Microsoft Excel que se carga en el sistema.

### Ingesta de recursos {#ingest-assets}

El rendimiento y la estabilidad son preocupaciones importantes al ingerir activos en el sistema. Cuando cargue muchos datos en el Experience Manager, asegúrese de que el sistema funciona bien. Esto minimizó el tiempo necesario para añadir los datos y ayuda a evitar sobrecargar el sistema. Esto ayuda a evitar el bloqueo del sistema, especialmente en sistemas que ya están en producción.

Existen dos métodos para cargar los recursos en el sistema: un método basado en push que utilice HTTP o un método basado en pull-based que use las API de JCR.

#### Insertar a través de HTTP {#push-through-http}

El equipo de Managed Services de Adobe utiliza una herramienta denominada Botón para cargar datos en entornos de clientes. Glutton es una pequeña aplicación Java que carga todos los recursos de un directorio en otro directorio en una instancia [!DNL Experience Manager]. En lugar de Glutton, también puede utilizar herramientas como scripts Perl para publicar los recursos en el repositorio.

Hay dos desventajas principales en el uso del enfoque de pasar por https:

1. Transmita los recursos a través de HTTP al servidor. Esto requiere un poco de sobrecarga y requiere tiempo, lo que hace que se alargue el tiempo que se tarda en realizar la migración.
1. Si tiene etiquetas y metadatos personalizados que se deben aplicar a los recursos, este método requiere un segundo proceso personalizado que debe ejecutarse para aplicar estos metadatos a los recursos una vez importados.

El otro método para la ingesta de recursos es extraer recursos del sistema de archivos local. Sin embargo, si no puede obtener una unidad externa o un recurso compartido de red montados en el servidor para realizar un método basado en extracción, la mejor opción es publicar los recursos a través de HTTP.

#### Extracción del sistema de archivos local {#pull-from-the-local-file-system}

El [ACS [!DNL Experience Manager] Importador de recursos CSV de herramientas](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) extrae recursos del sistema de archivos y metadatos de recursos de un archivo CSV para la importación de recursos. La API del [!DNL Experience Manager] Administrador de recursos se utiliza para importar los recursos en el sistema y aplicar las propiedades de metadatos configuradas. Lo ideal es que los recursos se monten en el servidor mediante un montaje de archivo de red o a través de una unidad externa.

Cuando los recursos no se transmiten a través de una red, el rendimiento general mejora mucho. Este método suele ser el método más eficaz para cargar recursos en el repositorio. Además, puede importar todos los recursos y metadatos en un solo paso, ya que la herramienta admite la ingesta de metadatos. No se requiere ningún otro paso para aplicar los metadatos, por ejemplo, utilizando una herramienta independiente.

### Procesar representaciones {#process-renditions}

Después de cargar los recursos en el sistema, debe procesarlos a través del flujo de trabajo de recursos de actualización de DAM para extraer metadatos y generar representaciones. Antes de realizar este paso, debe duplicar y modificar el flujo de trabajo de recursos de actualización de DAM para adaptarlo a sus necesidades. Es posible que no sea necesario realizar algunos pasos en el flujo de trabajo predeterminado, como la generación de Dynamic Media Classic PTIFF o la integración del servidor de InDesign.

Después de configurar el flujo de trabajo según sus necesidades, tiene dos opciones para ejecutarlo:

1. El enfoque más sencillo es [ACS Commons’ Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Esta herramienta le permite ejecutar una consulta y procesar los resultados de la consulta a través de un flujo de trabajo. También hay opciones para configurar los tamaños de lote.
1. Puede utilizar [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) junto con [Synth Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html). Aunque este enfoque es mucho más implicado, le permite eliminar la sobrecarga del motor de flujo de trabajo [!DNL Experience Manager] al optimizar el uso de los recursos del servidor. Además, Fast Action Manager aumenta todavía más el rendimiento mediante la supervisión dinámica de los recursos del servidor y la limitación de la carga localizada en el sistema. Se han proporcionado ejemplos de secuencias de comandos en la página de características de ACS Commons.

### Activar recursos {#activate-assets}

Para implementaciones que tienen un nivel de publicación, debe activar los recursos en el conjunto de servidores de publicación. Aunque Adobe recomienda ejecutar más de una instancia de publicación única, lo más eficaz es replicar todos los recursos en una instancia de publicación única y luego clonar esa instancia. Al activar un gran número de recursos, después de activar una activación de árbol, es posible que tenga que intervenir. He aquí por qué: Al activar activaciones, los elementos se añaden a la cola de trabajos/eventos de Sling. Una vez que el tamaño de esta cola empieza a superar los aproximadamente 40.000 elementos, el procesamiento se ralentiza drásticamente. Una vez que el tamaño de esta cola supera los 100.000 elementos, la estabilidad del sistema empieza a verse afectada.

Para solucionar este problema, puede utilizar el [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) para administrar la replicación de recursos. Esto funciona sin utilizar las colas de Sling, reduciendo la sobrecarga y limitando la carga de trabajo para evitar que el servidor se sobrecargue. En la página de documentación de la función se muestra un ejemplo de uso de FAM para administrar la replicación.

Otras opciones para obtener recursos en el conjunto de servidores de publicación incluyen el uso de [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) o [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), que se proporcionan como herramientas como parte de Jackrabbit. Otra opción es usar una herramienta de código abierto para su infraestructura [!DNL Experience Manager] llamada [Grabbit](https://github.com/TWCable/grabbit), que afirma tener un rendimiento más rápido que el de vlt.

Para cualquiera de estos enfoques, la advertencia es que los recursos de la instancia de autor no se muestran como activados. Para gestionar el marcado de estos recursos con el estado de activación correcto, también debe ejecutar una secuencia de comandos para marcar los recursos como activados.

>[!NOTE]
>
>Adobe no mantiene o no admite Grabbit.

### Clonar publicación {#clone-publish}

Una vez activados los recursos, puede clonar la instancia de publicación para crear tantas copias como sea necesario para la implementación. La clonación de un servidor es bastante sencilla, pero hay que recordar algunos pasos importantes. Para clonar la publicación:

1. Haga una copia de seguridad de la instancia de origen y del almacén de datos.
1. Restaure la copia de seguridad de la instancia y del almacén de datos a la ubicación de destino. Los siguientes pasos hacen referencia a esta nueva instancia.
1. Realice una búsqueda del sistema de archivos en `crx-quickstart/launchpad/felix` para `sling.id`. Elimine este archivo.
1. En la ruta raíz del almacén de datos, busque y elimine cualquier archivo `repository-XXX`.
1. Edite `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` y `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` para señalar la ubicación del almacén de datos en el nuevo entorno.
1. Inicie el entorno.
1. Actualice la configuración de cualquier agente de replicación en los autores para que apunten a las instancias de publicación correctas o a los agentes de vaciado de Dispatcher en la nueva instancia para que apunten a los distribuidores correctos para el nuevo entorno.

### Habilitar flujos de trabajo {#enable-workflows}

Una vez que hayamos completado la migración, los iniciadores de los flujos de trabajo de recursos de actualización de DAM deben volver a habilitarse para admitir la generación de representaciones y la extracción de metadatos para el uso diario del sistema.

## Migración de recursos entre implementaciones de [!DNL Experience Manager] {#migrate-between-aem-instances}

Aunque no es tan común, a veces es necesario migrar grandes cantidades de datos de una instancia [!DNL Experience Manager] a otra; por ejemplo, cuando realice una actualización [!DNL Experience Manager], actualice el hardware o migre a un nuevo centro de datos, como con una migración de AMS.

En este caso, los recursos ya se rellenan con metadatos y las representaciones ya se han generado. Simplemente puede centrarse en mover recursos de una instancia a otra. Al migrar entre instancias [!DNL Experience Manager], se realizan los siguientes pasos:

1. Desactivar flujos de trabajo: Como está migrando representaciones junto con nuestros recursos, desea deshabilitar los iniciadores de flujo de trabajo para DAM Update Asset.

1. Migrar etiquetas: Dado que ya tiene etiquetas cargadas en la instancia [!DNL Experience Manager] de origen, puede crearlas en un paquete de contenido e instalarlas en la instancia de destino.

1. Migrar recursos: Existen dos herramientas recomendadas para mover recursos de una instancia [!DNL Experience Manager] a otra:

   * **Vault Remote Copy**, o  `vlt rcp`, le permite utilizar vlt en una red. Puede especificar un directorio de origen y destino y vlt descarga todos los datos del repositorio desde una instancia y los carga en la otra. Vlt rcp está documentado en [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **** Grabbitis es una herramienta de sincronización de contenido de código abierto desarrollada por Time Warner Cable para su  [!DNL Experience Manager] implementación. Como utiliza flujos de datos continuos, en comparación con vlt rcp, tiene una latencia menor y reclama una mejora de velocidad de dos a diez veces más rápida que vlt rcp. Grabbit también admite la sincronización de contenido delta únicamente, lo que le permite sincronizar los cambios una vez completada la migración inicial.

1. Activar recursos: Siga las instrucciones para [activar recursos](#activate-assets) documentadas para la migración inicial a AEM.

1. Clonar publicación: Al igual que con una nueva migración, cargar una única instancia de publicación y clonarla es más eficaz que activar el contenido en ambos nodos. Consulte [Clonación de publicación.](#clone-publish)

1. Habilitación de flujos de trabajo: Una vez completada la migración, vuelva a habilitar los iniciadores para los flujos de trabajo de recursos de actualización de DAM para admitir la generación de representaciones y la extracción de metadatos para el uso diario del sistema.
