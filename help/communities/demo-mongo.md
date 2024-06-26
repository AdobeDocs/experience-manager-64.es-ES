---
title: Configuración de MongoDB para demostración
seo-title: How to Setup MongoDB for Demo
description: Configuración del MSRP para una instancia de autor y una instancia de publicación
seo-description: How to setup MSRP for one author instance and one publish instance
uuid: d2035a9e-f05c-4f90-949d-7cdae9646750
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0b126218-b142-4d33-a28c-a91ab4fe99ac
role: Admin
exl-id: e32fc619-6226-48c6-bbd7-1910963d1036
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 1%

---

# Configuración de MongoDB para demostración {#how-to-setup-mongodb-for-demo}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Este tutorial describe cómo configurar [MSRP](msrp.md) para *un autor* instancia y *una publicación* instancia.

Con esta configuración, se puede acceder al contenido de la comunidad desde los entornos de autor y publicación sin necesidad de reenviar o revertir la réplica del contenido generado por el usuario (UGC).

Esta configuración es adecuada para *sin producción* entornos como para desarrollo o demostración.

**A *producción* entorno:**

* Ejecute MongoDB con un conjunto de réplicas
* Utilizar SolrCloud
* Contener varias instancias del editor

## MongoDB {#mongodb}

### Instalar MongoDB {#install-mongodb}

* Descargar MongoDB desde [https://www.mongodb.org/](https://www.mongodb.org/)

   * Opción del sistema operativo:

      * Linux
      * Mac 10.8
      * Windows 7
   * Elección de la versión:

      * Como mínimo, utilice la versión 2.6


* Configuración básica

   * Siga las instrucciones de instalación de MongoDB
   * Configurar para mondios

      * No es necesario configurar los mongos o el uso compartido
   * La carpeta MongoDB instalada se denominará &lt;mongo-install>
   * La ruta de acceso del directorio de datos definido se denominará &lt;mongo-dbpath>


* MongoDB puede ejecutarse en el mismo host que AEM o de forma remota

### Iniciar MongoDB {#start-mongodb}

* &lt;mongo-install>/bin/mongod —dbpath &lt;mongo-dbpath>

Esto iniciará un servidor MongoDB utilizando el puerto predeterminado 27017.

* Para Mac, aumente el límite con el argumento de inicio &quot;ulimit -n 2048&quot;

>[!NOTE]
>
>Si MongoDB se inicia *after* AEM, **restart** all **AEM** para que se conecten correctamente a MongoDB.

### Opción de producción de muestra: Configurar conjunto de réplicas de MongoDB {#demo-production-option-setup-mongodb-replica-set}

Los siguientes comandos son un ejemplo de configuración de un conjunto de réplicas con 3 nodos en localhost:

* bin/mongod —port 27017 —dbpath data —replSet rs0&amp;
* bin/mongo

   * cfg = {&quot;_id&quot;: &quot;rs0&quot;,&quot;version&quot;: 1, &quot;miembros&quot;: [{&quot;_id&quot;: 0, &quot;host&quot;: &quot;127.0.0.1:27017&quot;}]}
   * rs.initiate(cfg)

* bin/mongod —port 27018 —dbpath data1 —replSet rs0&amp;
* bin/mongod —port 27019 —dbpath data2 —replSet rs0&amp;
* bin/mongo

   * rs.add(&quot;127.0.0.1:27018&quot;)
   * rs.add(&quot;127.0.0.1:27019&quot;)
   * rs.status()

## Solr {#solr}

### Instalar Solr {#install-solr}

* Descargar Solr desde [Apache Lucene](https://archive.apache.org/dist/lucene/solr/):

   * Compatible con cualquier sistema operativo
   * Utilice la versión 4.10 o la versión 5
   * Solr requiere Java 1.7 o bueno

* Configuración básica

   * Siga la configuración de Solr de &quot;ejemplo&quot;
   * No se necesita ningún servicio
   * La carpeta Solr instalada se denominará &lt;solr-install>

### Configuración de Solr para AEM Communities {#configure-solr-for-aem-communities}

Para configurar una colección Solr para MSRP para demostración, hay dos decisiones que se deben tomar (seleccione los enlaces a la documentación principal para obtener más información):

1. Ejecutar Solr de forma independiente o [Modo SolrCloud](msrp.md#solrcloudmode)
1. Instalar [standard](msrp.md#installingstandardmls) o [avanzado](msrp.md#installingadvancedmls) búsqueda multilingüe (MLS)

### Solar independiente {#standalone-solr}

El método para ejecutar Solr puede variar según la versión y la forma de instalación. La variable [Guía de referencia de Solr](https://archive.apache.org/dist/lucene/solr/ref-guide/) es la documentación autorizada.

Para simplificar, usando la versión 4.10 como ejemplo, inicie Solr en modo independiente:

* cd to &lt;solrinstall>/example
* java -jar start.jar

Esto iniciará un servidor HTTP Solr utilizando el puerto predeterminado 8983. Puede navegar hasta la consola Solr para obtener una consola Solr para realizar pruebas.

* consola Solr predeterminada: [http://localhost:8983/solr/](http://localhost:8983/solr/)

>[!NOTE]
>
>Si la consola Solr no está disponible, marque los registros en &lt;solrinstall>/example/logs. Compruebe si SOLR está intentando enlazarse a un nombre de host específico que no se puede resolver (p. ej. &quot;user-macbook-pro&quot;).
Si es así, actualice el archivo etc/hosts con una nueva entrada para este nombre de host (por ejemplo, 127.0.0.1 user-macbook-pro) y Solr se iniciará correctamente.

### SolrCloud {#solrcloud}

Para ejecutar una configuración de solrCloud muy básica (no de producción), comience con:

* java -Dbootstrap_confdir=./solr/collection1/conf -Dbootstrap_conf=true -DzkRun -jar start.jar

## Identificar MongoDB como almacén común {#identify-mongodb-as-common-store}

Inicie el autor y publique AEM instancias, si es necesario.

Si AEM se estaba ejecutando antes de que se iniciara MongoDB, entonces las instancias de AEM deberán reiniciarse.

Siga las instrucciones de la página de documentación principal: [MSRP - Tienda común MongoDB](msrp.md)

## Probar {#test}

Para probar y verificar el almacén común de MongoDB, publique un comentario en la instancia de publicación y visualícelo en la instancia de autor, así como vea el UGC en MongoDB y Solr:

1. En la instancia de publicación, vaya a la [Guía de componentes de comunidad](http://localhost:4503/content/community-components/en/comments.html) y seleccione el componente Comentarios.
1. Inicie sesión para publicar un comentario:
1. Introduzca el texto en el cuadro de entrada de texto del comentario y haga clic en **[!UICONTROL Publicación]**

   ![chlimage_1-191](assets/chlimage_1-191.png)

1. Simplemente vea el comentario en la [instancia de autor](http://localhost:4502/content/community-components/en/comments.html) (probablemente aún haya iniciado sesión como administrador/administrador).

   ![chlimage_1-192](assets/chlimage_1-192.png)

   Nota: mientras que hay nodos JCR en el *asipath* por lo que respecta al autor, se trata del marco SCF. El UGC real no está en JCR, está en MongoDB.

1. Ver el UGC en mongodb **[!UICONTROL Comunidades > Colecciones > Contenido]**

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Ver el UGC en Solr:

   * Vaya al tablero Solr: [http://localhost:8983/solr/](http://localhost:8983/solr/)
   * Usuario `core selector` para seleccionar `collection1`
   * Seleccionar `Query`
   * Seleccionar `Execute Query`

   ![chlimage_1-194](assets/chlimage_1-194.png)

## Solución de problemas {#troubleshooting}

### No aparece ningún UGC {#no-ugc-appears}

1. Asegúrese de que MongoDB esté instalado y funcionando correctamente.

1. Asegúrese de que MSRP esté configurado para ser el proveedor predeterminado:

   * En todas las instancias de creación y publicación de AEM, vuelva a la sección [Consola de configuración de almacenamiento](srp-config.md)

   o compruebe el repositorio AEM:

   * En JCR, si [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

      * No contiene un [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa que el proveedor de almacenamiento es JSRP
      * Si el nodo srpc existe y contiene el nodo [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), las propiedades de configuración predeterminada deben definir MSRP para que sea el proveedor predeterminado


1. Asegúrese de que AEM se reinició después de seleccionar el MSRP.
