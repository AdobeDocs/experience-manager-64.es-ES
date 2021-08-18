---
title: Clientlibs para componentes de Communities
seo-title: Clientlibs para componentes de Communities
description: Bibliotecas de cliente para comunidades
seo-description: Bibliotecas de cliente para comunidades
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---

# Clientlibs para componentes de Communities {#clientlibs-for-communities-components}

## Introducción {#introduction}

En esta sección de la documentación se describe cómo agregar bibliotecas del lado del cliente (clientlibs) a una página para componentes de Communities.

Para obtener información básica, visite:

* [Uso de ](../../help/sites-developing/clientlibs.md) bibliotecas del lado del cliente, que proporcionan detalles de uso, así como herramientas de depuración
* [Clientlibs para ](client-customize.md#clientlibs) SCF, que proporciona información útil al personalizar componentes de SCF

## Por qué se requieren Clientlibs {#why-clientlibs-are-required}

Las bibliotecas de clientes son necesarias para el correcto funcionamiento (JavaScript) y el estilo (CSS) de un componente.

Cuando existe una [función de comunidad](functions.md) para una función, todos los componentes y configuraciones necesarios, incluidos los clientlibs necesarios, estarán presentes en el sitio de la comunidad. Solo si los componentes adicionales van a estar disponibles para los autores, se necesitarán añadir clientlibs adicionales.

Cuando faltan los clientlibs requeridos, [añadir un componente Communities a una página](author-communities.md) podría provocar errores de javascript y un aspecto inesperado.

### Ejemplo: Revistas colocadas sin Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Ejemplo: Revisiones colocadas con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificación de Clientlibs Requeridos {#identifying-required-clientlibs}

La información de funciones esenciales para los desarrolladores identifica los clientlibs necesarios.

Además, desde una instancia de AEM, al navegar por la [Community Components Guide](components-guide.md) se proporciona acceso a una lista de categorías clientlib necesarias para un componente.

Por ejemplo, en la parte superior de la [página Revisiones](http://localhost:4502/content/community-components/en/reviews.html), los clientlibs requeridos que aparecen listados son

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Adición de Clientlibs Necesarios {#adding-required-clientlibs}

Cuando se desee añadir un componente Comunidades a una página, será necesario agregar las clientlibs necesarias para el componente si no está presente.

Utilice [CRXDE|Lite](#using-crxde-lite) para modificar una lista de clientlibslist existente para una página del sitio de la comunidad.

Para agregar una clientlib para un sitio de la comunidad usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Vaya a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Busque el nodo `clientlibslist` de la página en la que desea agregar el componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con nodo `clientlibslist` seleccionado

   * Busque la propiedad String[] `scg:requiredClientLibs`
   * Seleccione su `Value` para acceder al cuadro de diálogo matriz de cadenas

      * Desplácese hacia abajo si es necesario
      * Seleccione `+` para introducir una nueva biblioteca de cliente

         * Repetir para agregar más bibliotecas de cliente
      * Seleccione **[!UICONTROL OK]**
   * Seleccione **[!UICONTROL Guardar todo]**



>[!NOTE]
>
>Si el sitio no es un sitio de la comunidad, es necesario descubrir la existencia o ubicación de las bibliotecas de cliente que se utilizan para el sitio.

Utilizando el ejemplo [Introducción a AEM Communities](getting-started.md), donde `site-name` es *comprometer*, así es como aparecería la lista clientliblist si agregara el componente de revisiones:

![chlimage_1-247](assets/chlimage_1-247.png)
