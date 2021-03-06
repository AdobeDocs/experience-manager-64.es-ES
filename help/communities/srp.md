---
title: Información general del proveedor de recursos de almacenamiento
seo-title: Información general del proveedor de recursos de almacenamiento
description: Almacenamiento Común para las Comunidades
seo-description: Almacenamiento Común para las Comunidades
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---


# Información general del proveedor de recursos de almacenamiento {#storage-resource-provider-overview}

## Introducción {#introduction}

A partir de AEM Communities 6.1, el contenido de la comunidad, conocido comúnmente como contenido generado por el usuario (UGC), se almacena en un único almacén común proporcionado por un [proveedor de recursos de almacenamiento](working-with-srp.md) (SRP).

Existen varias opciones de SRP, todas las cuales acceden a UGC a través de una nueva interfaz de AEM Communities, la [API de SocialResourceProvider](srp-and-ugc.md) (API de SRP), que incluye todas las operaciones de creación, lectura, actualización y eliminación (CRUD).

Todos los componentes de SCF se implementan mediante la API de SRP, lo que permite que el código se desarrolle sin tener conocimiento de la [topología subyacente](topologies.md) ni de la ubicación de UGC.

***La API de SocialResourceProvider solo está disponible para clientes con licencia de AEM Communities.***

>[!NOTE]
>
>**Componentes** personalizados: Para los clientes con licencia de AEM Communities, la API de SRP está disponible para los desarrolladores de componentes personalizados con el fin de acceder a UGC independientemente de la topología subyacente. Consulte [SRP y UGC Essentials](srp-and-ugc.md).

Consulte también:

* [Elementos esenciales](srp-and-ugc.md)  de SRP y UGC: métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización](socialutils.md)  de SocialUtils: asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales

## Acerca del repositorio {#about-the-repository}

Para comprender el SRP, es útil comprender el rol del repositorio de AEM (OAK) en un sitio de comunidad AEM.

**Repositorio de contenido Java (JCR)**
Este estándar define un modelo de datos y una interfaz de programación de aplicaciones (API[ ](https://jackrabbit.apache.org/jcr/jcr-api.html)JCR) para repositorios de contenido. Combina características de file systems convencionales con las de bases de datos relacionales y agrega una serie de funciones adicionales que las aplicaciones de contenido necesitan con frecuencia.

Una implementación de JCR es el repositorio de AEM, OAK.

**Apache Jackrabbit Oak (OAK)**
[](../../help/sites-deploying/platform.md) OAK es una implementación de JCR 2.0 que es un sistema de almacenamiento de datos diseñado específicamente para aplicaciones centradas en el contenido. Es un tipo de base de datos jerárquica diseñada para datos no estructurados y semiestructurados. El repositorio almacena no sólo el contenido orientado al usuario, sino también todo el código, las plantillas y los datos internos que utiliza la aplicación. La interfaz de usuario para acceder al contenido es [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Tanto JCR como OAK suelen utilizarse para hacer referencia al repositorio de AEM.

Después de desarrollar el contenido del sitio en el entorno de creación privado, debe copiarse en el entorno de publicación pública. Esto generalmente se realiza mediante una operación denominada *[replicación](deploy-communities.md#replication-agents-on-author)*. Esto sucede bajo el control del autor/desarrollador/administrador.

Para UGC, el contenido lo introducen visitantes registrados del sitio (miembros de la comunidad) en el entorno de publicación pública. Esto sucede al azar.

A los efectos de la gestión y el sistema de informes, es útil tener acceso a UGC desde el entorno privado de creación. Con SRP, el acceso a UGC desde el autor es más coherente y eficaz, ya que no es necesario realizar la replicación inversa desde la publicación hasta el autor.

## Acerca de SRP {#about-srp}

Cuando UGC se guarda en almacenamiento compartido, hay una sola instancia de contenido de miembro a la que se puede acceder, en la mayoría de las implementaciones, desde los entornos de creación y publicación. Independientemente de la elección de SRP (MSRP, ASRP, JSRP), se debe acceder a todos mediante programación con la API de SRP.

>[!NOTE]
>
>Consulte [SRP y UGC Essentials](srp-and-ugc.md) para obtener el código de muestra y detalles adicionales.
>
>Consulte [Acceso a UGC con SRP](accessing-ugc-with-srp.md) para conocer las prácticas recomendadas al codificar.

### ASRP {#asrp}

En el caso de ASRP, UGC no se almacena en JCR, sino en un servicio en la nube alojado y administrado por Adobe. El UGC almacenado en ASRP no se puede ver con el CRXDE Lite ni se puede acceder a él mediante la API de JCR.

Consulte [ASRP - Proveedor de recursos de Almacenamiento de Adobe](asrp.md).

No es posible que los desarrolladores accedan directamente al UGC.

ASRP utiliza la nube de Adobe para consultas.

### MSRP {#msrp}

En el caso del MSRP, UGC no se almacena en JCR, sino en MongoDB. El UGC almacenado en MSRP no puede visualizarse con CRXDE Lite ni accederse a él mediante la API de JCR.

Consulte [MSRP - Proveedor de recursos de Almacenamiento MongoDB](msrp.md).

Aunque el MSRP es comparable al ASRP, dado que todas las instancias de servidor AEM están accediendo al mismo UGC, es posible utilizar herramientas comunes para acceder directamente al UGC almacenado en MongoDB.

MSRP utiliza Solr para consultas.

### JSRP {#jsrp}

JSRP es el proveedor predeterminado para acceder a todos los UGC en una sola instancia de AEM. Proporciona la capacidad de experimentar rápidamente AEM Communities 6.1 sin necesidad de configurar MSRP o ASRP.

Consulte [JSRP - Proveedor de recursos de Almacenamiento JCR](jsrp.md).

En el caso de JSRP, mientras que UGC se almacena en JCR y se puede acceder a él a través de la API de CRXDE Lite y JCR, se recomienda encarecidamente que nunca se use la API de JCR para hacerlo; de lo contrario, los cambios futuros podrían afectar al código personalizado.

Además, no se comparte el repositorio para los entornos de creación y publicación. Aunque un clúster de instancias de publicación resulta en un repositorio de publicación compartido, el contenido generado por usuarios especificado en la publicación no estará visible para el autor, por lo tanto no podrá administrar el contenido generado por usuarios del autor. UGC solo se mantiene en el repositorio de AEM (JCR) de la instancia en la que se introdujo.

JSRP utiliza los índices Oak para consultas.

## Acerca de los nodos de sombra en JCR {#about-shadow-nodes-in-jcr}

Los nodos de sombra, que imitan la ruta a UGC, existen en el repositorio local para cumplir dos propósitos:

1. [control de acceso (ACL](#for-access-control-acls))
1. [Recursos no existentes (NER)](#for-non-existing-resources-ners)

Independientemente de la implementación de SRP, el UGC real *no estará visible en la misma ubicación que el nodo de sombra.

### Para Control de acceso (ACL) {#for-access-control-acls}

Algunas implementaciones de SRP, como ASRP y MSRP, almacenan contenido comunitario en bases de datos que no proporcionan verificación de ACL. Los nodos de sombra proporcionan una ubicación en el repositorio local a la que se pueden aplicar las ACL.

Mediante la API de SRP, todas las opciones de SRP realizan la misma comprobación de la ubicación de sombra antes de todas las operaciones de CRUD.

La comprobación de ACL utiliza un método de utilidad que devuelve una ruta adecuada para comprobar los permisos aplicados al UGC del recurso.

Consulte [SRP y UGC Essentials](srp-and-ugc.md) para obtener el código de muestra.

### Para recursos no existentes (NER) {#for-non-existing-resources-ners}

Algunos componentes de Communities pueden incluirse en una secuencia de comandos y, por tanto, requieren un nodo direccionable Sling para admitir funciones de Communities. [Los ](scf.md#add-or-include-a-communities-component) componentes incluidos se denominan recursos no existentes.

Los nodos de sombra proporcionan una ubicación direccionable Sling en el repositorio.

>[!CAUTION]
>
>Dado que el nodo de sombra tiene varios usos, la presencia de un nodo de sombra *no* implica que el componente es NER.

### Ubicación del almacenamiento {#storage-location}

A continuación se muestra un ejemplo de un nodo de sombra que utiliza el componente [Comentarios](http://localhost:4502/content/community-components/en/comments.html) en la [Guía de componentes de comunidad](components-guide.md):

* El componente existe en el repositorio local en:

   /content/community-components/es/comments/jcr:content/content/inclusible/comments

* El nodo de sombra correspondiente existe en el repositorio local en:

   /content/usergenerate/content/community-components/es/comments/jcr:content/content/inclusible/comments

No se encuentra ningún UGC en el nodo de sombra.

El comportamiento predeterminado es configurar nodos de sombra en una instancia de publicación siempre que se haga referencia al subárbol correspondiente para una lectura o una escritura.

Como ejemplo, supongamos que la implementación es [MSRP](msrp.md) con un conjunto de servidores de publicación TarMK.

Cuando un [miembro](users.md) publica UGC en pub1 (almacenado en MongoDB), los nodos de sombra se crean en JCR en pub1.

La primera vez que se lee UGC en pub2, si no hay nada configurado, el comportamiento predeterminado es crear los nodos de sombra.

Si no se desea el comportamiento predeterminado, debe configurarse en la instancia de creación y resumirse en todas las instancias de publicación, que suele ser un proceso manual.
