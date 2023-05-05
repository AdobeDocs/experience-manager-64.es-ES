---
title: DSRP - Proveedor de recursos de almacenamiento de bases de datos relacionales
seo-title: DSRP - Relational Database Storage Resource Provider
description: Configuración de AEM Communities para utilizar una base de datos relacional como su tienda común
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: f364e7da-ee54-4ab2-a630-7ec9239005ac
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d23acb18-6761-4290-9e7a-a434582791bd
role: Admin
exl-id: 3dd2bdc9-0c4d-43d9-a731-ca8c27503e1c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 4%

---

# DSRP - Proveedor de recursos de almacenamiento de bases de datos relacionales {#dsrp-relational-database-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de DSRP {#about-dsrp}

Cuando AEM Communities está configurado para utilizar una base de datos relacional como su almacén común, el contenido generado por el usuario (UGC) es accesible desde todas las instancias de autor y publicación sin necesidad de sincronización ni replicación.

Consulte también [Características de las opciones de SRP](working-with-srp.md#characteristics-of-srp-options) y [Topologías recomendadas](topologies.md).

## Requisitos  {#requirements}

* [MySQL](#mysql-configuration), una base de datos relacional
* [Apache Solr](#solr-configuration), una plataforma de búsqueda

>[!NOTE]
>
>La configuración de almacenamiento predeterminada ahora se almacena en la ruta conf(`/conf/global/settings/community/srpc/defaultconfiguration`) en lugar de ruta de etc (`/etc/socialconfig/srpc/defaultconfiguration`). Se recomienda que siga la [pasos de migración](#migration-steps-0dt) para que default srp funcione según lo esperado.

## Configuración de base de datos relacional {#relational-database-configuration}

### Configuración de MySQL {#mysql-configuration}

Una instalación de MySQL puede compartirse entre las características de habilitación y el almacén común (DSRP) dentro del mismo grupo de conexiones utilizando diferentes nombres de base de datos (esquema) y también diferentes conexiones (servidor:puerto).

Para obtener más información sobre la instalación y configuración, consulte [Configuración de MySQL para DSRP](dsrp-mysql.md).

### Configuración de Solr {#solr-configuration}

Una instalación de Solr se puede compartir entre el almacén de nodos (Oak) y el almacén común (SRP) utilizando diferentes colecciones.

Si las colecciones Oak y SRP se utilizan intensamente, puede instalarse un segundo Solr por motivos de rendimiento.

Para los entornos de producción, el modo SolrCloud proporciona un rendimiento mejorado con respecto al modo independiente (una única configuración local de Solr).

Para obtener más información sobre la instalación y configuración, consulte [Configuración de Solr para SRP](solr.md).

### Seleccionar DSRP {#select-dsrp}

La variable [Consola de configuración de almacenamiento](srp-config.md) permite seleccionar la configuración de almacenamiento predeterminada, que identifica qué implementación de SRP utilizar.

Al autor, para acceder a la consola de configuración de almacenamiento

* Iniciar sesión con privilegios de administrador
* En el **menú principal**

   * Select **[!UICONTROL Herramientas]** (del panel izquierdo)
   * Select **[!UICONTROL Comunidades]**
   * Select **[!UICONTROL Configuración de almacenamiento]**

      * Por ejemplo, la ubicación resultante es: [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp)
      >[!NOTE]
      >
      >La configuración de almacenamiento predeterminada ahora se almacena en la ruta conf(`/conf/global/settings/community/srpc/defaultconfiguration`) en lugar de ruta de etc (`/etc/socialconfig/srpc/defaultconfiguration`). Se recomienda que siga la [pasos de migración](#migration-steps-0dt) para que default srp funcione según lo esperado.

      ![chlimage_1-128](assets/chlimage_1-128.png)

* Select **[!UICONTROL Proveedor de recursos de almacenamiento de bases de datos (DSRP)]**
* **Configuración de la base de datos**

   * **[!UICONTROL Nombre de la fuente de datos JDBC]**

      El nombre proporcionado a la conexión MySQL debe ser el mismo que se introdujo en [Configuración de JDBC OSGi](dsrp-mysql.md#configurejdbcconnections)

      *default*: comunidades

   * **[!UICONTROL Nombre de la base de datos]**

      Nombre dado al esquema en [init_schema.sql](dsrp-mysql.md#obtain-the-sql-script) script

      *default*: comunidades

* **SolrConfiguration**

   * **[](https://cwiki.apache.org/confluence/display/solr/Using+ZooKeeper+to+Manage+Configuration+Files)Host de Zookeeper**

      Deje este valor en blanco si ejecuta Solr utilizando el ZooKeeper interno. De lo contrario, al ejecutar en [Modo SolrCloud](solr.md#solrcloud-mode) con un ZooKeeper externo, establezca este valor en el URI del ZooKeeper, como *my.server.com:80*

      *default*: *&lt;blank>*

   * **[!UICONTROL URL de Solr]**

      *default*: https://127.0.0.1:8983/solr/

      * **[!UICONTROL Colección Solr]**

         *default*: colección1

* Seleccione **[!UICONTROL Enviar]**

### Pasos de migración de tiempo de inactividad cero para defaultsrp {#migration-steps-0dt}

Siga estos pasos para asegurarse de que la página predeterminada de srp [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp) funciona según lo esperado:

1. Cambie el nombre de la ruta en `/etc/socialconfig` a `/etc/socialconfig_old`, de modo que la configuración del sistema vuelva a jsrp (predeterminado).
1. Ir a la página defaultsrp [http://localhost:4502/communities/admin/defaultsrp](http://localhost:4502/communities/admin/defaultsrp), donde jsrp está configurado. Haga clic en el **[!UICONTROL submit]** para que se cree un nuevo nodo de configuración predeterminado en `/conf/global/settings/community/srpc`.
1. Eliminar la configuración predeterminada creada `/conf/global/settings/community/srpc/defaultconfiguration`.
1. Copiar la configuración antigua `/etc/socialconfig_old/srpc/defaultconfiguration` en lugar del nodo eliminado (`/conf/global/settings/community/srpc/defaultconfiguration`) en el paso anterior.
1. Eliminar el nodo antiguo etc `/etc/socialconfig_old`.

## Publicación de la configuración {#publishing-the-configuration}

El DSRP debe identificarse como el almacén común en todas las instancias de autor y publicación.

Para que la configuración idéntica esté disponible en el entorno de publicación:

Sobre el autor:

* Vaya del menú principal a **[!UICONTROL Herramientas > Operaciones > Replicación]**
* Hacer doble clic **[!UICONTROL Activar árbol]**
* **Ruta de inicio:**

   * Vaya a `/conf/global/settings/community/srpc/`

* Asegúrese `Only Modified` no está seleccionado.
* Select **[!UICONTROL Activar]**

## Administración de datos de usuario {#managing-user-data}

Para obtener información sobre *usuarios*, *perfiles de usuario* y *grupos de usuarios*, introducidos a menudo en el entorno de publicación, visita

* [Sincronización de usuarios](sync.md)
* [Administración de usuarios y grupos de usuarios](users.md)

## Reindexación de Solr para DSRP {#reindexing-solr-for-dsrp}

Para reindexar DSRP Solr, siga la documentación de [reindexación de MSRP](msrp.md#msrp-reindex-tool), sin embargo, al reindexar para DSRP, utilice esta URL en su lugar: **/services/social/datastore/rdb/reindex**

Por ejemplo, un comando curl para reindexar DSRP tendría este aspecto:

```shell
curl -u admin:password -X POST -F path=/ https://host:port/services/social/datastore/rdb/reindex
```
