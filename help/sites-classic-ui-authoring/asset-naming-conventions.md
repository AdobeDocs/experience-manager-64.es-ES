---
title: Convenciones de nomenclatura para la prueba de recursos
seo-title: Naming conventions for assets
description: Los nodos del repositorio están sujetos a las convenciones de nomenclatura del repositorio de contenido Java. Sin embargo, Adobe Experience Manager impone otras convenciones para el nombre de los nodos de recursos.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 6%

---

# Convenciones de nomenclatura para la prueba de recursos{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los nodos del repositorio están sujetos a las convenciones de nomenclatura de la [Repositorio de contenido Java](/help/sites-developing/the-basics.md#java-content-repository). Sin embargo, Adobe Experience Manager impone otras convenciones para el nombre de los nodos de recursos.

## IU clásica {#classic-ui}

La IU clásica impone restricciones más estrictas:

* Valida el nombre del recurso cuando hay un nombre de nodo explícito cuando:

   * se proporciona un título de recurso para su conversión en el nombre de nodo
   * se proporciona un nombre de nodo explícito

* Caracteres válidos (solo estos caracteres son realmente válidos cuando se crea un recurso desde la IU clásica):

   * &quot;a&quot; a &quot;z&quot;
   * De la &quot;A&quot; a la &quot;Z&quot;
   * De &quot;0&quot; a &quot;9&quot;
   * _ (guion bajo)
   * `-` (guion/signo menos)
