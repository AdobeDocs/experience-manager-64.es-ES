---
title: 'SRP: Almacenamiento de contenido de la comunidad'
seo-title: 'SRP: Almacenamiento de contenido de la comunidad'
description: A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en un único almacén común proporcionado por un proveedor de recursos de almacenamiento (SRP)
seo-description: A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en un único almacén común proporcionado por un proveedor de recursos de almacenamiento (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---

# SRP: Almacenamiento de contenido de la comunidad {#srp-community-content-storage}

## Introducción {#introduction}

A partir de AEM Communities 6.1, el contenido generado por el usuario (UGC) se almacena en un único almacén común proporcionado por un proveedor de recursos de almacenamiento (SRP). Existen varias opciones de SRP entre las que elegir, como ASRP, MSRP y JSRP.

A diferencia de las versiones anteriores, no hay una replicación inversa/avanzada de UGC en AEM instancias. En su lugar, el SRP hace que UGC sea directamente accesible para crear, leer, actualizar y eliminar operaciones (CRUD) desde todas las instancias de autor y publicación, con una excepción para JSRP.

A continuación se muestran las [características de cada opción de SRP](#characteristics-of-srp-options), que es información crucial para el proceso de decisión al elegir el SRP apropiado y la [implementación subyacente](topologies.md).

Para obtener más información sobre el uso de SRP para UGC, consulte [Información general del proveedor de recursos de almacenamiento](srp.md).

>[!NOTE]
>
>La SRP se aplica solo al contenido de la comunidad. No afecta al lugar en el que se almacena el contenido del sitio ([almacén de nodos](../../help/sites-deploying/data-store-config.md)) y no afecta a la gestión segura del registro de usuarios, los perfiles de usuario y los grupos de usuarios entre AEM instancias (consulte también [Administración de datos de usuario](#managing-user-data)).

>[!CAUTION]
>
>A partir de AEM 6.1, [UGC nunca se replica](#ugc-never-replicated).
>
>Cuando la implementación no incluye un almacén común, como la topología predeterminada [JSRP](topologies.md#jsrp), UGC solo será visible en la instancia de autor o publicación de AEM en la que se introdujo. Solo si la topología incluye un clúster de publicación, el UGC estará visible en cualquier instancia de publicación.

## Características de las opciones de SRP {#characteristics-of-srp-options}

[ASRP: proveedor de recursos de almacenamiento de Adobe](asrp.md)\
Con esta opción, el UGC se mantiene de forma remota en un servicio en la nube alojado y administrado por Adobe. Se requiere una licencia adicional y trabajar con un representante de cuentas para suministrar la cuenta para esa licencia específica.

* Requiere un servicio de nube asociado, proporcionado y apoyado por Adobe, para almacenar contenido de la comunidad
* Requiere la elección de un centro de datos en una geografía específica (EE. UU., EMEA, APAC)
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Compatible con la granja de publicación TarMK
* Adecuado cuando no hay intención de invertir en almacenamiento local

>[!NOTE]
>
>La carga de archivos adjuntos a anuncios (o comentarios) en ASRP tiene un límite de 50 MB.

[MSRP - Proveedor de recursos de almacenamiento MongoDB](msrp.md)\
Con esta opción, el UGC se mantiene directamente en una instancia local de MongoDB.

* Requiere una instalación local con licencia de MongoDB para almacenar contenido de la comunidad
* Requiere una instalación local de Apache Solr
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Adecuado para una granja de publicación TarMK existente
* Adecuado para un clúster MongoMK o RdbMK
* Adecuado para esperar grandes volúmenes de contenido de la comunidad

[DSRP - Proveedor de recursos de almacenamiento de bases de datos relacionales](dsrp.md)\
Con esta opción, el UGC se mantiene directamente en una instancia local de base de datos MySQL.

* Requiere una instalación local de MySQL para almacenar contenido de la comunidad
* Requiere una instalación local de Apache Solr
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Adecuado para una granja de publicación TarMK existente
* Adecuado para un clúster MongoMK o RdbMK
* Adecuado para esperar grandes volúmenes de contenido de la comunidad

[JSRP: proveedor de recursos de almacenamiento JCR](jsrp.md)\
Con la opción predeterminada, no hay ningún almacén común. El UGC solo se mantiene en el mismo repositorio JCR que la instancia de AEM en la que se introdujo.

* Almacena contenido de la comunidad en el repositorio JCR de la instancia de autor o publicación AEM en la que se publicó.
* Requiere que todo acceso programático a UGC se realice a través de la API de SRP
* Requiere un clúster de publicación si se implementa más de una instancia de publicación (no hay ningún mecanismo de replicación entre instancias de publicación en una granja TarMK)
* La moderación solo se realiza en el entorno de publicación (no hay ningún mecanismo de replicación inversa/de reenvío entre el autor y la publicación)
* Generalmente mejor para desarrollo, demostraciones y capacitación

## Configuración de SRP {#configuring-srp}

La especificación de la opción de almacenamiento predeterminada, basada en la implementación subyacente, se realiza a través de la [Consola de configuración de almacenamiento](srp-config.md).

Para obtener detalles de configuración de cada opción, consulte:

* [ASRP: proveedor de recursos de almacenamiento de Adobe](asrp.md)
* [MSRP - Proveedor de recursos de almacenamiento MongoDB](msrp.md)
* [DSRP - Proveedor de recursos de almacenamiento de bases de datos relacionales](dsrp.md)
* [JSRP: proveedor de recursos de almacenamiento JCR](jsrp.md)

Si no hay ninguna opción de almacenamiento seleccionada activamente, JSRP está habilitado de forma predeterminada.

## Información adicional {#additional-information}

### UGC nunca se replicó {#ugc-never-replicated}

En el entorno de creación, un autor crea contenido de página y lo replica en el entorno de publicación. Cuando una página incluye una función interactiva de AEM Communities, como comentarios, revisiones, foros, blogs o control de calidad, la interacción de los miembros (visitantes registrados en el sitio) en una instancia de publicación provoca que el contenido generado por el usuario (UGC) se introduzca en el entorno de publicación.

Anteriormente, el contenido de esta comunidad se replicaba de forma inversa en instancias de autor y de autor replicado en instancias de publicación. Era problemático mantener la coherencia entre AEM instancias con replicación inversa y avanzada.

A partir de AEM Communities 6.1, la necesidad de replicación de UGC se ha eliminado mediante el uso del almacenamiento compartido para UGC, como se describe anteriormente.

Mientras el contenido del sitio se replica, UGC nunca se replica.

### Administración de datos de usuario {#managing-user-data}

También son de interés para las comunidades [*usuarios*, *grupos de usuarios* y *perfiles de usuario*](users.md). Estos datos relacionados con el usuario, cuando se crean y actualizan en el entorno de publicación, deben estar disponibles para otras instancias de publicación cuando la topología es un [conjunto de servidores de publicación](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

A partir de AEM Communities 6.1, los datos relacionados con el usuario se sincronizan mediante la distribución Sling en lugar de la replicación. Para obtener más información, visite [Sincronización de usuarios](sync.md).

### Actualización a AEM Communities 6.2 {#upgrading-to-aem-communities}

Al actualizar a AEM Communities 6.3, si es necesario conservar UGC preexistente, se deben tomar medidas en función de si la comunidad AEM 5.6.1 o AEM 6.0 utiliza almacenamiento de Adobe bajo demanda o almacenamiento local de UGC.

Para obtener más información, visite [Actualización a AEM Communities 6.3](upgrade.md).
