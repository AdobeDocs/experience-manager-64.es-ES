---
title: Pasos de actualización para las instalaciones de Application Server
seo-title: Pasos de actualización para las instalaciones de Application Server
description: Obtenga información sobre cómo actualizar las instancias de AEM implementadas a través de los servidores de aplicaciones.
seo-description: Obtenga información sobre cómo actualizar las instancias de AEM implementadas a través de los servidores de aplicaciones.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
translation-type: tm+mt
source-git-commit: 510b6765e11a5b3238407322d847745f09183d63
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Pasos de actualización para las instalaciones de Application Server{#upgrade-steps-for-application-server-installations}

En esta sección se describe el procedimiento que debe seguirse para actualizar AEM para las instalaciones de Application Server.

Todos los ejemplos de este procedimiento utilizan JBoss como servidor de aplicaciones e implican que ya tiene implementada una versión de trabajo de AEM. El procedimiento tiene por objeto el documento de las actualizaciones realizadas desde **AEM versión 5.6 a 6.3**.

1. Primero, inicio JBoss. En la mayoría de los casos, puede hacerlo ejecutando la secuencia de comandos de `standalone.sh` inicio, ejecutando este comando desde el terminal:

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Si AEM 5.6 ya está implementado, compruebe que los paquetes funcionan correctamente al ejecutar:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. A continuación, anule la implementación de AEM 5.6:

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
   >En este ejemplo, oak-repository es el directorio temporal donde residirá el repositorio recientemente convertido. Antes de realizar este paso, asegúrese de tener la última versión de crx2oak.jar.

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

1. Quite los archivos y las carpetas que ya no sean necesarios. Los elementos que debe eliminar específicamente son:

   * La carpeta **** launchpad/startup. Puede eliminarlo ejecutando el siguiente comando en el terminal: `rm -rf crx-quickstart/launchpad/startup`
   * El archivo **base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * El **archivo** BootstrapCommandFile_timestamp.txt: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Copie el almacén de segmentos recién migrado a su ubicación correcta:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Copie también el almacén de datos:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. A continuación, debe crear la carpeta que contendrá las configuraciones de OSGi que se utilizarán con la nueva instancia actualizada. Más concretamente, una carpeta denominada install debe crearse en **crx-quickstart**.

1. Ahora, cree el almacén de nodos y el almacén de datos que se utilizarán con AEM 6.3. Para ello, cree dos archivos con los nombres siguientes en **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Estos dos archivos configurarán AEM para utilizar un almacén de nodos TarMK y un almacén de datos File.

1. Edite los archivos de configuración para que estén listos para su uso. Más específicamente:

   * Añada la siguiente línea a **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * A continuación, agregue las siguientes líneas a **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Quite el modo de ejecución crx2 ejecutando:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Ahora debe cambiar los modos de ejecución en el archivo de guerra AEM 6.3. Para hacerlo, primero cree una carpeta temporal que albergue la guerra de AEM 6.3. El nombre de la carpeta en este ejemplo será **temp**. Una vez copiado el archivo de guerra, extraiga su contenido ejecutándose desde la carpeta temp:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Una vez extraído el contenido, vaya a la carpeta **WEB-INF** y edite el `web.xml` archivo para cambiar los modos de ejecución. Para buscar la ubicación en la que se han establecido en XML, busque la `sling.run.modes` cadena. Una vez que lo encuentre, cambie los modos de ejecución en la siguiente línea de código, que de forma predeterminada se establece en author:

   ```shell
   <param-value >author</param-value>
   ```

1. Cambie el valor de autor anterior y defina los modos de ejecución en: author,crx3,crx3tar El bloque final de código debería tener este aspecto:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Volver a crear el frasco con el contenido modificado:

   ```shell
   jar cvf aem62.war
   ```

1. Finalmente, despliegue el nuevo archivo de guerra:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```

