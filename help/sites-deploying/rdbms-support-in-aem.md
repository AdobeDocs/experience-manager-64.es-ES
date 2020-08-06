---
title: Compatibilidad con RDBMS en AEM 6.4
seo-title: Compatibilidad con RDBMS en AEM 6.4
description: Obtenga información sobre la compatibilidad con la persistencia de bases de datos relacionales en AEM 6.4 y las opciones de configuración disponibles.
seo-description: Obtenga información sobre la compatibilidad con la persistencia de bases de datos relacionales en AEM 6.4 y las opciones de configuración disponibles.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
translation-type: tm+mt
source-git-commit: 5513b24953438cc6c1b3f0027ff5535b4a1874d8
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---


# Compatibilidad con RDBMS en AEM 6.4{#rdbms-support-in-aem}

## Información general {#overview}

La compatibilidad con la persistencia de la base de datos relacional en AEM se implementa usando Documento Microkernel. El Documento Microkernel es la base que también se utiliza para implementar la persistencia de MongoDB.

Consiste en una API de Java basada en la API de Java de Mongo. También se proporciona una implementación de la API de BlobStore. De forma predeterminada, los blobs se almacenan en la base de datos.

Para obtener más información sobre los detalles de implementación, consulte la documentación de [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) y [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) .

>[!NOTE]
>
>También se proporciona compatibilidad con **PostgreSQL 9.4** , pero solo con fines de demostración. No estará disponible para entornos de producción.

## Bases de datos admitidas {#supported-databases}

Para obtener más información sobre el nivel de soporte de la Base de Datos Relacional en AEM, consulte la página [Requisitos](/help/sites-deploying/technical-requirements.md)Técnicos.

## Pasos de configuración {#configuration-steps}

El repositorio se crea configurando el servicio `DocumentNodeStoreService` OSGi. Se ha ampliado para admitir la persistencia de bases de datos relacionales además de MongoDB.

Para que funcione, una fuente de datos debe configurarse con AEM. Esto se realiza a través del `org.apache.sling.datasource.DataSourceFactory.config` archivo. Los controladores JDBC para la base de datos respectiva deben proporcionarse por separado como paquetes OSGi dentro de la configuración local.

Para ver los pasos para crear paquetes OSGi para controladores JDBC, consulte esta [documentación](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) en el sitio web Apache Sling.

>[!NOTE]
>
>Algunos de los controladores SQL ya están empaquetados como paquetes OSGi.
>
>Si este es el caso, simplemente copie el archivo jar a install-path/crx-quickstart/install/9.

Una vez configurados los paquetes, siga los pasos siguientes para configurar AEM con persistencia de RDB:

1. Asegúrese de que se ha iniciado el daemon de base de datos y de que dispone de una base de datos activa para su uso con AEM.
1. Copie el tarro AEM 6.3 en el directorio de instalación.
1. Cree una carpeta llamada `crx-quickstart\install` en el directorio de instalación.
1. Configure el almacén de nodos de documento creando un archivo de configuración con el siguiente nombre en el `crx-quickstart\install` directorio:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Configure el origen de datos y los parámetros JDBC creando otro archivo de configuración con el siguiente nombre en la `crx-quickstart\install` carpeta:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >Para obtener información detallada sobre la configuración del origen de datos para cada base de datos admitida, consulte Opciones [de configuración de fuentes](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options)de datos.

1. A continuación, prepare los paquetes OSGi de JDBC para utilizar con AEM:

   1. Descargue el archivo ZIP de https://dev.mysql.com/downloads/connector/j/
      * la versión debe ser >= 5.1.38
   1. Extraer el `mysql-connector-java-version-bin.jar` (paquete) del archivo
   1. Utilice la consola web para instalar y inicio del paquete:
      * Vaya a *http://serveraddress:serverport/system/console/bundles*
      * Seleccione **Instalar/Actualizar**
      * Busque el paquete seleccionado extraído del archivo ZIP descargado
      * Compruebe que el controlador JDBC de **Oracle Corporation para MySQLcom.mysql.jdbc** está activo y inicio.

1. Por último, el inicio AEM con los modos `crx3` y `crx3rdb` de ejecución:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Opciones de configuración de fuentes de datos {#data-source-configuration-options}

La configuración `org.apache.sling.datasource.DataSourceFactory-oak.config` OSGi se utiliza para configurar los parámetros necesarios para la comunicación entre AEM y la capa de persistencia de la base de datos.

Están disponibles las siguientes opciones de configuración:

* `datasource.name:` El nombre del origen de datos. El valor predeterminado es `oak`.

* `url:` La cadena URL de la base de datos que debe usarse con JDBC. Cada tipo de base de datos tiene su propio formato de cadena URL. Para obtener más información, consulte Formatos [de cadena de](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) URL a continuación.

* `driverClassName:` El nombre de la clase de controlador JDBC. Esto variará en función de la base de datos que desee utilizar y, posteriormente, del controlador necesario para conectarse a ella. A continuación se muestran los nombres de clase de todas las bases de datos admitidas por AEM:

   * `org.postgresql.Driver` para PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` DB2;
   * `oracle.jdbc.OracleDriver` para Oracle;
   * `com.mysql.jdbc.Driver` MySQL y MariaDB (experimental);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` para Microsoft SQL Server (experimental).

* `username:` Nombre de usuario con el que se ejecuta la base de datos.

* `password:` La contraseña de la base de datos.

### Formatos de cadena URL {#url-string-formats}

Se utiliza un formato de cadena URL diferente en la configuración del origen de datos según el tipo de base de datos que se deba utilizar. A continuación se muestra una lista de formatos para las bases de datos que AEM admiten actualmente:

* `jdbc:postgresql:databasename` para PostgreSQL;

* `jdbc:db2://localhost:port/databasename` DB2;
* `jdbc:oracle:thin:localhost:port:SID` para Oracle;
* `jdbc:mysql://localhost:3306/databasename` MySQL y MariaDB (experimental);

* `jdbc:sqlserver://localhost:1453;databaseName=name` para Microsoft SQL Server (experimental).

## Limitaciones conocidas {#known-limitations}

Aunque la persistencia de RDBMS admite el uso simultáneo de varias instancias de AEM con una sola base de datos, las instalaciones simultáneas no.

Para solucionar esto, asegúrese de ejecutar primero la instalación con un solo miembro y agregar los demás después de que el primero haya terminado de realizar la instalación.

