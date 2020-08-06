---
title: Acceso a UGC con SRP
seo-title: Acceso a UGC con SRP
description: Cuando un sitio está configurado para utilizar ASRP o MSRP, el UGC real no se almacena en AEM almacén de nodos (JCR)
seo-description: Cuando un sitio está configurado para utilizar ASRP o MSRP, el UGC real no se almacena en AEM almacén de nodos (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# Acceso a UGC con SRP {#accessing-ugc-with-srp}

## Acerca de SRP {#about-srp}

Todos los componentes y funciones de AEM Communities se crean en el marco de componentes [sociales (SCF)](scf.md), que invoca la API de SocialResourceProvider para acceder a todo el contenido generado por el usuario (UGC).

Antes de crear un sitio de comunidad, el proveedor de recursos de [almacenamiento (SRP)](working-with-srp.md) debe configurarse para seleccionar una implementación coherente con la [topología](topologies.md)subyacente. Las implementaciones de SRP se basan en tres opciones de almacenamiento:

1. [ASRP](asrp.md) : almacenamiento a pedido de Adobe
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Acerca del Almacenamiento UGC {#about-ugc-storage}

Lo que es importante saber sobre el almacenamiento de UGC es que, cuando un sitio está configurado para utilizar ASRP o MSRP, el UGC real no se almacena en AEM almacén [de](../../help/sites-deploying/data-store-config.md) nodos (JCR).

Aunque puede haber nodos en JCR que ocultan el UGC para proporcionar metadatos útiles, estos nodos no deben confundirse con el UGC real.

Consulte Información general del proveedor de recursos de [Almacenamiento.](srp.md)

## Práctica recomendada {#best-practice}

Al desarrollar componentes personalizados, los desarrolladores deben tener cuidado de codificar independientemente de la topología elegida actualmente, conservando así la flexibilidad para pasar a una nueva topología en el futuro.

### Supongamos que JCR no está disponible {#assume-jcr-not-available}

Deben evitarse los métodos específicos de JCR.

Métodos para utilizar:

* Sling API (recurso de Sling)
   * No asumir que hay nodos JCR

* Eventos OSGi
   * No supongamos que hay eventos JCR

* [Utilidades de recursos sociales](socialutils.md#socialresourceutilities-package)
* [SCF Utilities](socialutils.md#scfutilities-package)

Métodos para evitar:

* API de nodo
* eventos JCR
* Iniciadores de flujo de trabajo (que utilizan eventos JCR)

### Usar colecciones de búsqueda {#use-search-collections}

Los diferentes SRP pueden tener diferentes idiomas de consulta nativos. Se recomienda utilizar métodos del paquete [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) para invocar el idioma de consulta adecuado.

Para obtener más información, consulte [Search Essentials](search-implementation.md).

## Medios {#resources}

* [Almacenamiento](working-with-srp.md) de contenido de la comunidad: analiza las opciones de SRP disponibles para una tienda común UGC
* [Descripción general](srp.md) del proveedor de recursos de Almacenamiento: introducción y uso del repositorio
* [Elementos esenciales](srp-and-ugc.md) de SRP y UGC: métodos y ejemplos de utilidad SRP
* [Esenciales](search-implementation.md) de búsqueda: información esencial para buscar UGC
* [Refactorización](socialutils.md) de SocialUtils: asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
