---
title: Convenciones de nomenclatura
seo-title: Naming Conventions
description: Los nodos del repositorio están sujetos a las convenciones de nomenclatura del repositorio de contenido Java
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 9%

---

# Convenciones de nomenclatura{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los nodos del repositorio están sujetos a las convenciones de nomenclatura de la [Repositorio de contenido Java](/help/sites-developing/the-basics.md#java-content-repository). Sin embargo, AEM impone otras convenciones para el nombre de los nodos de página.

## Convenciones de nomenclatura de páginas {#naming-conventions-for-pages}

Estas convenciones de nomenclatura se implementan en varios niveles:

* JcrUtil: la AEM aplicación de la [utilidades JCR](#jcr-utilities).
* PageManager: el [Administrador de páginas](#page-manager) proporciona métodos para operaciones a nivel de página.
* Según la IU utilizada:

   * [IU estándar con capacidad táctil](#standard-ui)
   * [IU clásica](#classic-ui)

### Utilidades de JCR {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) es la implementación AEM de las utilidades JCR. De particular interés para validar nombres son las asignaciones de caracteres que controla y las siguientes validaciones:

* `isValidName`

   * Comprueba si el nombre no está vacío y contiene solo caracteres válidos.
   * Se puede utilizar para comprobar si un nombre propuesto es válido.

* `createValidName`

   * Esto crea una etiqueta válida a partir de una cadena arbitraria.
   * Se puede utilizar para crear un nombre a partir de un título.

### Administrador de páginas {#page-manager}

[PageManager](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) proporciona métodos para las operaciones de nivel de página, basados en [JCRUtil](#jcr-utilities).

### IU estándar {#standard-ui}

La IU estándar con capacidad táctil:

* Valida el nombre según las restricciones impuestas por PageManager cuando:

   * se proporciona un título de página para su conversión en el nombre del nodo
   * se proporciona un nombre de nodo explícito

### IU clásica {#classic-ui}

La IU clásica impone restricciones más estrictas:

* Valida el nombre cuando hay un nombre de nodo explícito cuando:

   * se proporciona un título de página para su conversión en el nombre del nodo
   * se proporciona un nombre de nodo explícito

* Caracteres válidos (solo estos caracteres son realmente válidos cuando se crea una página desde la IU clásica, aunque `PageManagerImpl` permitiría caracteres adicionales):

   * &quot;a&quot; a &quot;z&quot;
   * De la &quot;A&quot; a la &quot;Z&quot;
   * De &quot;0&quot; a &quot;9&quot;
   * _ (guion bajo)
   * `-` (guion/signo menos)
