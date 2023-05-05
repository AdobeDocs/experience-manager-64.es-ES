---
title: Compatibilidad con RDBMS en AEM 6.4
seo-title: RDBMS Support in AEM 6.4
description: Obtenga información sobre la compatibilidad con la persistencia de la base de datos relacional en AEM 6.4 y las opciones de configuración disponibles.
seo-description: Learn about the relational database persistence support in AEM 6.4 and the available configuration options.
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuring
exl-id: 89523bb4-e4c4-469c-802b-6fe27c816a2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 1%

---

# Compatibilidad con RDBMS en AEM 6.4{#rdbms-support-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

La compatibilidad con la persistencia de la base de datos relacional en AEM se implementa mediante Document Microkernel. Document Microkernel es la base que también se usa para implementar la persistencia de MongoDB.

Consiste en una API de Java basada en la API de Java de Mongo. También se proporciona una implementación de la API de BlobStore. De forma predeterminada, los blobs se almacenan en la base de datos.

Para obtener más información sobre los detalles de implementación, consulte la [RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html) y [RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html) documentación.

>[!NOTE]
>
>Compatibilidad con **PostgreSQL 9.4** también se proporciona, pero solo con fines de demostración. No estará disponible para entornos de producción.

## Bases de datos compatibles {#supported-databases}

Para obtener más información sobre el nivel de soporte de bases de datos relacionales en AEM, consulte la [Página Requisitos técnicos](/help/sites-deploying/technical-requirements.md).

## Pasos de configuración {#configuration-steps}

El repositorio se crea configurando el `DocumentNodeStoreService` Servicio OSGi. Se ha ampliado para admitir la persistencia de bases de datos relacionales además de MongoDB.

Para que funcione, es necesario configurar una fuente de datos con AEM. Esto se realiza mediante la variable `org.apache.sling.datasource.DataSourceFactory.config` archivo. Los controladores JDBC para la base de datos respectiva deben proporcionarse por separado como paquetes OSGi dentro de la configuración local.

Para ver los pasos sobre la creación de paquetes OSGi para controladores JDBC, consulte esta [documentación](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle) en el sitio web de Apache Sling.

>[!NOTE]
>
>Algunos de los controladores SQL ya están empaquetados como paquetes OSGi.
>
>Si este es el caso, copie el archivo jar a install-path/crx-quickstart/install/9.

Una vez configurados los paquetes, siga los siguientes pasos para configurar la AEM con persistencia de RDB:

1. Asegúrese de que el daemon de base de datos está iniciado y de que dispone de una base de datos activa para su uso con AEM.
1. Copie el jar AEM 6.3 en el directorio de instalación.
1. Cree una carpeta llamada `crx-quickstart\install` en el directorio de instalación.
1. Configure el almacén de nodos del documento creando un archivo de configuración con el siguiente nombre en el `crx-quickstart\install` directorio:

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Configure la fuente de datos y los parámetros JDBC creando otro archivo de configuración con el siguiente nombre en el `crx-quickstart\install` carpeta:

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >Para obtener información detallada sobre la configuración de la fuente de datos para cada base de datos admitida, consulte [Opciones de configuración de fuentes de datos](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options).

1. A continuación, prepare los paquetes OSGi de JDBC que se van a utilizar con AEM:

   1. Descargue el archivo ZIP de https://dev.mysql.com/downloads/connector/j/
      * la versión debe ser >= 5.1.38
   1. Extraiga el `mysql-connector-java-version-bin.jar` (paquete) del archivo
   1. Utilice la consola web para instalar e iniciar el paquete :
      * Vaya a *http://serveraddress:serverport/system/console/bundles*
      * Select **Instalar/actualizar**
      * Vaya a seleccionar el paquete extraído del archivo ZIP descargado
      * Compruebe que **Controlador JDBC de oracle Corporation para MySQLcom.mysql.jdbc** está activa y la inicia.

1. Finalmente, comience AEM con el `crx3` y `crx3rdb` modos de ejecución:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## Opciones de configuración de fuentes de datos {#data-source-configuration-options}

La variable `org.apache.sling.datasource.DataSourceFactory-oak.config` La configuración OSGi se utiliza para configurar los parámetros necesarios para la comunicación entre AEM y la capa de persistencia de la base de datos.

Estas son las opciones de configuración disponibles:

* `datasource.name:` El nombre de la fuente de datos. El valor predeterminado es `oak`.

* `url:` La cadena URL de la base de datos que debe utilizarse con JDBC. Cada tipo de base de datos tiene su propio formato de cadena URL. Para obtener más información, consulte [Formatos de cadena de URL](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats) más abajo.

* `driverClassName:` El nombre de clase de controlador JDBC. Esto variará según la base de datos que desee utilizar y, posteriormente, el controlador que se necesite para conectarse a ella. A continuación se muestran los nombres de clase de todas las bases de datos admitidas por AEM:

   * `org.postgresql.Driver` para PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` para DB2;
   * `oracle.jdbc.OracleDriver` para el Oracle;
   * `com.mysql.jdbc.Driver` para MySQL y MariaDB (experimental);
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` para Microsoft SQL Server (experimental).

* `username:` El nombre de usuario con el que se ejecuta la base de datos.

* `password:` La contraseña de la base de datos.

### Formatos de cadena de URL {#url-string-formats}

Se utiliza un formato de cadena de URL diferente en la configuración de la fuente de datos según el tipo de base de datos que se deba utilizar. A continuación se muestra una lista de formatos para las bases de datos que AEM admite actualmente:

* `jdbc:postgresql:databasename` para PostgreSQL;

* `jdbc:db2://localhost:port/databasename` para DB2;
* `jdbc:oracle:thin:localhost:port:SID` para el Oracle;
* `jdbc:mysql://localhost:3306/databasename` para MySQL y MariaDB (experimental);

* `jdbc:sqlserver://localhost:1453;databaseName=name` para Microsoft SQL Server (experimental).

## Limitaciones conocidas {#known-limitations}

Aunque la persistencia de RDBMS admite el uso simultáneo de varias instancias de AEM con una sola base de datos, las instalaciones simultáneas no lo son.

Para solucionar este problema, asegúrese de ejecutar primero la instalación con un solo miembro y añada los demás después de que el primero haya finalizado la instalación.
