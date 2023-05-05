---
title: Acceso a UGC con SRP
seo-title: Accessing UGC with SRP
description: Cuando un sitio está configurado para utilizar ASRP o MSRP, el UGC real no se almacena en AEM almacén de nodos (JCR)
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---

# Acceso a UGC con SRP {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de SRP {#about-srp}

Todos los componentes y funciones de AEM Communities se basan en la variable [marco de componentes sociales (SCF)](scf.md), que invoca la API de SocialResourceProvider para acceder a todo el contenido generado por el usuario (UGC).

Antes de crear un sitio de comunidad, la variable [proveedor de recursos de almacenamiento (SRP)](working-with-srp.md) debe configurarse para seleccionar una implementación coherente con el subyacente [topología](topologies.md). Las implementaciones de SRP se basan en tres opciones de almacenamiento:

1. [ASRP](asrp.md) - Adobe de almacenamiento bajo demanda
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Acerca del almacenamiento UGC {#about-ugc-storage}

Lo que es importante saber sobre el almacenamiento de UGC es que, cuando un sitio está configurado para utilizar ASRP o MSRP, el UGC real no se almacena en AEM [almacén de nodos](../../help/sites-deploying/data-store-config.md) (JCR).

Aunque puede haber nodos en JCR que ensombrecen el UGC para proporcionar metadatos útiles, estos nodos no deben confundirse con el UGC real.

Consulte [Información general del proveedor de recursos de almacenamiento.](srp.md)

## Práctica recomendada {#best-practice}

Al desarrollar componentes personalizados, los desarrolladores deben tener cuidado de codificar independientemente de la topología elegida actualmente, conservando así la flexibilidad para pasar a una nueva topología en el futuro.

### Supongamos que JCR no está disponible {#assume-jcr-not-available}

Se deben evitar los métodos específicos de JCR.

Métodos para utilizar:

* API de Sling (recurso de Sling)
   * No asumir que hay nodos JCR

* Eventos de OSGi
   * No asuma que hay eventos JCR

* [Utilidades de recursos sociales](socialutils.md#socialresourceutilities-package)
* [Utilidades de SCF](socialutils.md#scfutilities-package)

Métodos para evitar:

* API de nodo
* Eventos de JCR
* Iniciadores de flujo de trabajo (que utilizan eventos JCR)

### Usar colecciones de búsqueda {#use-search-collections}

Los diferentes SRP pueden tener diferentes idiomas de consulta nativos. Se recomienda utilizar métodos del [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) para invocar el idioma de consulta adecuado.

Para obtener más información, consulte [Elementos básicos de búsqueda](search-implementation.md).

## Recursos {#resources}

* [Almacenamiento de contenido de la comunidad](working-with-srp.md) - analiza las opciones de SRP disponibles para una tienda común UGC
* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Elementos básicos de búsqueda](search-implementation.md) - información esencial para la búsqueda de UGC
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
