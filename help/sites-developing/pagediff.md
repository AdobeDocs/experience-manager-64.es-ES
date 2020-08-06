---
title: Desarrollo y diferencia de página
seo-title: Desarrollo y diferencia de página
description: nulo
seo-description: nulo
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 7%

---


# Desarrollo y diferencia de página{#developing-and-page-diff}

## Información general de características {#feature-overview}

La creación de contenido es un proceso iterativo. La creación con eficiencia de contenido requiere poder ver qué ha cambiado de una iteración a otra. Visualizar una versión de la página y luego otra es un proceso poco eficaz y propenso a errores. Un autor desea poder comparar la página actual con una versión anterior en paralelo con las diferencias resaltadas.

La diferencia de página permite al usuario comparar la página actual con los inicios, las versiones anteriores, etc. Para obtener más información sobre esta función de usuario, consulte Diferencia [de página](/help/sites-authoring/page-diff.md).

## Detalles de la operación {#operation-details}

Al comparar versiones de una página, la versión anterior que el usuario desea comparar se vuelve a crear con AEM en segundo plano para facilitar la diferencia. Esto es necesario para poder representar el contenido [para una comparación](/help/sites-authoring/page-diff.md#presentation-of-differences)paralela.

Esta operación de recreación la realiza AEM internamente y es transparente para el usuario y no requiere ninguna intervención. Sin embargo, un administrador que visualiza el repositorio, por ejemplo, en CRX DE Lite, vería estas versiones recreadas dentro de la estructura de contenido.

Según el nivel de parche de AEM, el comportamiento es diferente y puede requerir ciertos permisos para funcionar correctamente.

### Antes del AEM 6.4.3 {#prior-to-aem}

Cuando se compara el contenido, todo el árbol hasta la página que comparar se vuelve a crear en la siguiente ubicación:

`/content/versionhistory/<userId>/<site structure>`

Porque al utilizar el mecanismo de diferencia de página, AEM recrea la versión anterior de la página, para poder utilizar la función el usuario debe tener determinados permisos de JCR.

>[!CAUTION]
>
>Para utilizar la función de diferencia de página, el usuario debe tener el permiso **Modificar/Crear/Eliminar** en el nodo `/content/versionhistory`.

### A partir del AEM 6.4.3 {#as-of-aem}

Cuando se compara el contenido, todo el árbol hasta la página que comparar se vuelve a crear en la siguiente ubicación:

`/tmp/versionhistory/`

Este contenido lo crea un usuario de servicio con permisos que limitan la visibilidad del usuario actual. Por este motivo, no se requieren permisos especiales.

Una tarea de limpieza se ejecuta automáticamente para limpiar este contenido temporal.

## Limitaciones del desarrollador {#developer-limitations}

Anteriormente, en la IU clásica, había que tener especialmente en cuenta el desarrollo para facilitar la difusión de AEM (como usar la biblioteca de `cq:text` etiquetas o personalizar la integración del servicio `DiffService` OSGi en los componentes). Esto ya no es necesario para la nueva función de diferencia, ya que la diferencia se produce en el cliente mediante la comparación DOM.

Sin embargo, hay una serie de limitaciones que el desarrollador debe tener en cuenta.

* Esta función utiliza clases CSS que no tienen nombres espaciados en el producto AEM. Si en la página se incluyen otras clases CSS personalizadas o clases CSS de terceros con los mismos nombres, la visualización de la diferencia puede verse afectada.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Debido a que la diferencia es del lado del cliente y se ejecuta al cargar la página, no se contabilizarán los ajustes en el DOM después de ejecutar el servicio de diferencias del lado del cliente. Esto puede afectar

   * Componentes que utilizan AJAX para incluir contenido
   * Aplicaciones de una sola página
   * Componentes basados en JavaScript que manipulan el DOM tras la interacción del usuario.

