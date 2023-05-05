---
title: Precauciones del código
seo-title: Code pitfalls
description: Problemas comunes de codificación que se evitan al desarrollar para AEM
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 6%

---

# Precauciones del código{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Evitar enlaces de Sling en código Java {#avoid-sling-bindings-in-java-code}

Los enlaces de Sling son una manera inapropiada de obtener acceso a un servicio en el 90% de los casos. En su lugar, debe usar *@Reference* o *@Inject* anotaciones.

## Evitar Thread.interrupt en el código Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* es peligroso porque puede cerrar archivos, incluidos archivos Lucene y archivos de caché persistentes, cuando se los llama en el momento incorrecto.

## Evite mezclar la sincronización de Java con ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Esto puede llevar a una condición de carrera en la que el código eventualmente se bloqueará.
