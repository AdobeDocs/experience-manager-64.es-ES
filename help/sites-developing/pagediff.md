---
title: Desarrollo y diferencia de página
seo-title: Desarrollo y diferencia de página
description: Desarrollo y diferencia de página
seo-description: nulo
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 8%

---


# Desarrollo y diferencia de página{#developing-and-page-diff}

## Descripción general de características {#feature-overview}

La creación de contenido es un proceso iterativo. La creación con eficiencia de contenido requiere poder ver qué ha cambiado de una iteración a otra. Visualizar una versión de la página y luego otra es un proceso poco eficaz y propenso a errores. Un autor quiere poder comparar la página actual con una versión anterior en paralelo con las diferencias resaltadas.

La diferencia de página permite al usuario comparar la página actual con los lanzamientos, versiones anteriores, etc. Para obtener más información sobre esta función de usuario, consulte [Diferencias de página](/help/sites-authoring/page-diff.md).

## Detalles de la operación {#operation-details}

Al comparar versiones de una página, la versión anterior que el usuario desea comparar se vuelve a crear AEM en segundo plano para facilitar la comparación de diferencias. Esto es necesario para poder procesar el contenido [para una comparación en paralelo](/help/sites-authoring/page-diff.md#presentation-of-differences).

Esta operación de recreación la realiza AEM internamente y es transparente para el usuario y no requiere ninguna intervención. Sin embargo, un administrador que viera el repositorio por ejemplo en CRX DE Lite vería estas versiones recreadas dentro de la estructura de contenido.

Dependiendo del nivel de parche de AEM, el comportamiento es diferente y puede requerir ciertos permisos para funcionar correctamente.

### Antes de AEM 6.4.3 {#prior-to-aem}

Cuando se compara el contenido, todo el árbol hasta la página para comparar se vuelve a crear en la siguiente ubicación:

`/content/versionhistory/<userId>/<site structure>`

Debido a que al usar el mecanismo de diferencia de página, AEM recrea la versión anterior de la página, para poder usar la función el usuario debe tener ciertos permisos de JCR.

>[!CAUTION]
>
>Para utilizar la función de diferencia de página, el usuario debe tener el permiso **Modificar/Crear/Eliminar** en el nodo `/content/versionhistory`.

### A partir del AEM 6.4.3 {#as-of-aem}

Cuando se compara el contenido, todo el árbol hasta la página para comparar se vuelve a crear en la siguiente ubicación:

`/tmp/versionhistory/`

Este contenido lo crea un usuario de servicio con permisos que limitan la visibilidad del usuario actual. Por este motivo, no se necesitan permisos especiales.

Una tarea de limpieza se ejecuta automáticamente para limpiar este contenido temporal.

## Limitaciones del desarrollador {#developer-limitations}

Anteriormente, en la interfaz de usuario clásica, había que tener especialmente en cuenta el desarrollo para facilitar AEM diferenciación (como el uso de la biblioteca de etiquetas `cq:text` o la integración personalizada del servicio `DiffService` OSGi en los componentes). Esto ya no es necesario para la nueva función de diferencia, ya que la diferencia se produce en el lado del cliente mediante la comparación DOM.

Sin embargo, hay varias limitaciones que el desarrollador debe tener en cuenta.

* Esta función utiliza clases CSS que no tienen espacios de nombres en el producto AEM. Si se incluyen en la página otras clases CSS personalizadas o clases CSS de terceros con los mismos nombres, la visualización de la diferencia puede verse afectada.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Dado que la comparación de diferencias es del lado del cliente y se ejecuta al cargar la página, cualquier ajuste al DOM después de que se haya ejecutado el servicio de comparación de diferencias del lado del cliente no se contabilizará. Esto puede afectar

   * Componentes que utilizan AJAX para incluir contenido
   * Aplicaciones de una sola página
   * Componentes basados en JavaScript que manipulan el DOM tras la interacción del usuario.

