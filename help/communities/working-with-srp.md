---
title: 'SRP: Almacenamiento de contenido de la comunidad'
seo-title: 'SRP: Almacenamiento de contenido de la comunidad'
description: A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en una única tienda común proporcionada por un proveedor de recursos de almacenamiento (SRP)
seo-description: A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en una única tienda común proporcionada por un proveedor de recursos de almacenamiento (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP: Almacenamiento de contenido de la comunidad {#srp-community-content-storage}

## Introducción {#introduction}

A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en un único almacén común proporcionado por un proveedor de recursos de almacenamiento (SRP). Existen varias opciones de SRP entre las que elegir, como ASRP, MSRP y JSRP.

A diferencia de las versiones anteriores, no existe una replicación inversa/avanzada de UGC en AEM instancias. En su lugar, el SRP hace que UGC sea directamente accesible para crear, leer, actualizar y eliminar operaciones (CRUD) desde todas las instancias de creación y publicación, con una excepción para JSRP.

A continuación se detallan las [características de cada opción](#characteristics-of-srp-options)de SRP, que es una información crucial para el proceso de decisión al elegir el SRP apropiado y la implementación [](topologies.md)subyacente.

Para obtener más información sobre el uso de SRP para UGC, consulte Información general sobre el proveedor de recursos de [Almacenamiento](srp.md).

>[!NOTE]
>
>SRP se aplica solamente al contenido de la comunidad. No afecta al lugar donde se almacena el contenido del sitio (almacén[de](../../help/sites-deploying/data-store-config.md)nodos) y no afecta a la gestión segura del registro de usuarios, perfiles de usuarios y grupos de usuarios entre instancias de AEM (consulte también [Administración de datos](#managing-user-data)de usuario).

>[!CAUTION]
>
>A partir de AEM 6.1, [UGC nunca se replica](#ugc-never-replicated).
>
>Cuando la implementación no incluye un almacén común, como la topología [JSRP](topologies.md#jsrp) predeterminada, UGC solo estará visible en la instancia de publicación o autor AEM en la que se introdujo. Solo si la topología incluye un clúster de publicación, el UGC estará visible en cualquier instancia de publicación.

## Características de las opciones de SRP {#characteristics-of-srp-options}

[ASRP - Proveedor de recursos de Almacenamiento de Adobe](asrp.md)\
Con esta opción, el UGC se mantiene de forma remota en un servicio en la nube alojado y administrado por Adobe. Requiere una licencia adicional y trabajar con un representante de cuentas para proporcionar la cuenta para esa licencia específica.

* Requiere un servicio de nube asociado proporcionado y apoyado por Adobe para almacenar contenido de la comunidad
* Requiere la elección de un centro de datos en una zona geográfica específica (EE. UU., EMEA, APAC)
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Adecuado para la granja de publicación TarMK
* Adecuado cuando no hay intención de invertir en almacenamientos locales

>[!NOTE]
>
>Hay un límite para cargar archivos adjuntos a publicaciones (o comentarios) en ASRP, que es de 50 MB.

[MSRP - Proveedor de recursos de Almacenamiento MongoDB](msrp.md)\
Con esta opción, el UGC se mantiene directamente en una instancia local de MongoDB.

* Requiere una instalación local con licencia de MongoDB para almacenar contenido comunitario
* Requiere una instalación local de Apache Solr
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Adecuado para un conjunto de servidores de publicación TarMK existente
* Adecuado para un clúster MongoMK o RdbMK
* Adecuado para esperar grandes volúmenes de contenido de comunidad

[DSRP - Proveedor de recursos de Almacenamiento de base de datos relacional](dsrp.md)\
Con esta opción, el UGC se mantiene directamente en una instancia de base de datos MySQL local.

* Requiere una instalación local de MySQL para almacenar contenido comunitario
* Requiere una instalación local de Apache Solr
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Adecuado para un conjunto de servidores de publicación TarMK existente
* Adecuado para un clúster MongoMK o RdbMK
* Adecuado para esperar grandes volúmenes de contenido de comunidad

[JSRP - Proveedor de recursos de Almacenamiento JCR](jsrp.md)\
Con la opción predeterminada, no hay ninguna tienda común. El UGC solo se conserva en el mismo repositorio JCR que la instancia de AEM en la que se introdujo.

* Almacena el contenido de la comunidad en el repositorio JCR de la instancia de publicación o autor AEM en la que se publicó
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Requiere un clúster de publicación si se implementa más de una instancia de publicación (no hay ningún mecanismo de replicación entre instancias de publicación en un conjunto de servidores TarMK)
* La moderación solo se realiza en el entorno de publicación (no existe un mecanismo de replicación inversa/reenvío entre el autor y la publicación)
* Generalmente mejor para desarrollo, demostraciones y capacitación

## Configuración de SRP {#configuring-srp}

La especificación de la opción de almacenamiento predeterminada, basada en la implementación subyacente, se realiza a través de la consola [Configuración de](srp-config.md)Almacenamiento.

Para obtener detalles de configuración de cada opción, consulte:

* [ASRP - Proveedor de recursos de Almacenamiento de Adobe](asrp.md)
* [MSRP - Proveedor de recursos de Almacenamiento MongoDB](msrp.md)
* [DSRP - Proveedor de recursos de Almacenamiento de base de datos relacional](dsrp.md)
* [JSRP - Proveedor de recursos de Almacenamiento JCR](jsrp.md)

Si no hay ninguna opción de almacenamiento seleccionada, JSRP está activado de forma predeterminada.

## Información adicional {#additional-information}

### UGC nunca replicado {#ugc-never-replicated}

En el entorno de creación, un autor crea contenido de página y lo replica en el entorno de publicación. Cuando una página incluye una función de AEM Communities interactiva, como comentarios, revisiones, foros, blogs o QnA, la interacción de los miembros (firmada en visitantes del sitio) en una instancia de publicación da como resultado que el usuario haya introducido contenido generado (UGC) en el entorno de publicación.

Anteriormente, este contenido de comunidad se replicaba de forma inversa en instancias de autor y de autor replicado en instancias de publicación. Era problemático mantener la coherencia entre AEM instancias con replicación inversa y posterior.

A partir de AEM Communities 6.1, se ha eliminado la necesidad de replicar UGC mediante el uso de almacenamientos compartidos para UGC, como se ha descrito anteriormente.

Mientras que el contenido del sitio se replica, el UGC nunca se replica.

### Administración de datos de usuario {#managing-user-data}

También son de interés para los [*usuarios *, los grupos* de *usuarios y los perfiles* de *](users.md)usuarios. Estos datos relacionados con el usuario, cuando se crean y actualizan en el entorno de publicación, deben estar disponibles para otras instancias de publicación cuando la topología es un conjunto de[publicaciones](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

A partir de AEM Communities 6.1, los datos relacionados con el usuario se sincronizan mediante la distribución Sling en lugar de la replicación. Para obtener más información, visite Sincronización [de usuarios](sync.md).

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

Al actualizar a AEM Communities 6.3, si es necesario conservar UGC preexistente, se deben tomar medidas en función de si la comunidad de AEM 5.6.1 o AEM 6.0 ha utilizado almacenamientos de Adobe a petición o almacenamiento local de UGC.

Para obtener más información, visite [Actualización a AEM Communities 6.3](upgrade.md).
