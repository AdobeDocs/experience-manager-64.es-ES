---
title: Pasos de actualización para las instalaciones del servidor de aplicaciones
seo-title: Pasos de actualización para las instalaciones del servidor de aplicaciones
description: Obtenga información sobre cómo actualizar instancias de AEM que se implementan mediante servidores de aplicaciones.
seo-description: Obtenga información sobre cómo actualizar instancias de AEM que se implementan mediante servidores de aplicaciones.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Actualización
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Pasos de actualización para instalaciones del servidor de aplicaciones{#upgrade-steps-for-application-server-installations}

En esta sección se describe el procedimiento que debe seguirse para actualizar el AEM de las instalaciones del servidor de aplicaciones.

Todos los ejemplos de este procedimiento utilizan JBoss como servidor de aplicaciones e implican que tiene una versión de trabajo de AEM ya implementado. El procedimiento está pensado para documentar las actualizaciones realizadas de **AEM versión 5.6 a 6.3**.

1. Primero, inicie JBoss. En la mayoría de los casos, puede hacerlo ejecutando el script de inicio `standalone.sh`, ejecutando este comando desde el terminal:

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Si AEM 5.6 ya está implementado, compruebe que los paquetes funcionan correctamente ejecutando:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. A continuación, quite la implementación de AEM 5.6:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Detenga JBoss.

1. Ahora, migre el repositorio utilizando la herramienta de migración crx2oak:

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >En este ejemplo, oak-repository es el directorio temporal donde residirá el repositorio recién convertido. Antes de realizar este paso, asegúrese de tener la última versión de crx2oak.jar.

1. Elimine las propiedades necesarias del archivo sling.properties haciendo lo siguiente:

   1. Abra el archivo ubicado en `crx-quickstart/launchpad/sling.properties`
   1. Texto del paso Elimine las siguientes propiedades y guarde el archivo:

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. Elimine los archivos y carpetas que ya no sean necesarios. Los elementos que debe eliminar específicamente son:

   * **launchpad/startup folder**. Puede eliminarlo ejecutando el siguiente comando en el terminal: `rm -rf crx-quickstart/launchpad/startup`
   * El **archivo base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * El archivo **BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Copie el almacén de segmentos recién migrado a su ubicación correcta:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Copie también el almacén de datos:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. A continuación, debe crear la carpeta que contendrá las configuraciones de OSGi que se utilizarán con la nueva instancia actualizada. Más específicamente, una carpeta denominada install debe crearse en **crx-quickstart**.

1. Ahora, cree el almacén de nodos y el almacén de datos que se utilizarán con AEM 6.3. Para ello, cree dos archivos con los nombres siguientes en **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Estos dos archivos configurarán AEM para utilizar un almacén de nodos TarMK y un almacén de datos de archivo.

1. Edite los archivos de configuración para que estén listos para su uso. Más específicamente:

   * Agregue la línea siguiente a **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * A continuación, agregue las siguientes líneas a **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Elimine el modo de ejecución crx2 ejecutando:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Ahora necesita cambiar los modos de ejecución en el archivo war AEM 6.3. Para ello, primero cree una carpeta temporal que aloje la guerra de AEM 6.3. El nombre de la carpeta en este ejemplo será **temp**. Una vez copiado el archivo war, extraiga su contenido ejecutándolo desde la carpeta temporal:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Una vez extraído el contenido, vaya a la carpeta **WEB-INF** y edite el archivo `web.xml` para cambiar los modos de ejecución. Para encontrar la ubicación donde se establecen en el XML, busque la cadena `sling.run.modes`. Una vez que lo encuentre, cambie los modos de ejecución en la siguiente línea de código, que de forma predeterminada está configurada como autor:

   ```shell
   <param-value >author</param-value>
   ```

1. Cambie el valor de autor anterior y establezca los modos de ejecución en: author,crx3,crx3tar El bloque final de código debería tener este aspecto:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Vuelva a crear el frasco con el contenido modificado:

   ```shell
   jar cvf aem62.war
   ```

1. Finalmente, despliegue el nuevo archivo war:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```

