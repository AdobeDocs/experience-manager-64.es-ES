---
title: Componentes Clientlibs for Communities
seo-title: Componentes Clientlibs for Communities
description: Bibliotecas de cliente para comunidades
seo-description: Bibliotecas de cliente para comunidades
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Componentes Clientlibs for Communities {#clientlibs-for-communities-components}

## Introducción {#introduction}

Esta sección de la documentación describe cómo agregar bibliotecas de cliente (clientlibs) a una página para componentes de Comunidades.

Para obtener información básica, visite:

* [Uso de las bibliotecas](../../help/sites-developing/clientlibs.md) del lado del cliente que proporcionan detalles de uso, así como herramientas de depuración
* [Clientlibs para SCF](client-customize.md#clientlibs) que proporciona información útil al personalizar componentes de SCF
* [Blog: Bibliotecas de clientes de AEM explicadas por ejemplo](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Por qué se requieren los clientes {#why-clientlibs-are-required}

Los clientes son necesarios para el correcto funcionamiento (JavaScript) y el estilo (CSS) de un componente.

Cuando exista una función [de](functions.md) comunidad para una función, todos los componentes y configuraciones necesarios, incluidos los clientes requeridos, estarán presentes en el sitio de la comunidad. Solo si los autores disponen de componentes adicionales, se necesitarían agregar clientes adicionales.

Cuando faltan los clientes requeridos, [agregar un componente Comunidades a una página](author-communities.md) podría provocar errores de javascript y un aspecto inesperado.

### Ejemplo: Revistas colocadas sin clientes {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Ejemplo: Revistas colocadas con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificación de los clientes requeridos {#identifying-required-clientlibs}

La información esencial de las funciones para los desarrolladores identifica a los clientes requeridos.

Además, desde una instancia de AEM, la navegación a la Guía [de componentes de](components-guide.md) comunidad proporciona acceso a una lista de categorías clientlib necesarias para un componente.

Por ejemplo: en la parte superior de la página [](http://localhost:4502/content/community-components/en/reviews.html) Reseñas, los clientes requeridos que aparecen son

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Añadir Clientlibs requeridos {#adding-required-clientlibs}

Cuando se desee agregar un componente Comunidades a una página, será necesario agregar los clientes necesarios para el componente si no están presentes.

Utilice [CRXDE|Lite](#using-crxde-lite) para modificar una lista de clientes existente para una página de sitio de comunidad.

Para agregar una clientlib para un sitio de comunidad mediante [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Vaya a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Busque el nodo de la `clientlibslist` página en la que desea agregar el componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con `clientlibslist` nodo seleccionado

   * Localizar la propiedad String[] `scg:requiredClientLibs`
   * Seleccione su `Value` para acceder al cuadro de diálogo de la matriz String

      * Desplácese hacia abajo si es necesario
      * Seleccione `+` para introducir una nueva biblioteca de cliente

         * Repetir para agregar más bibliotecas de cliente
      * Seleccione **[!UICONTROL Aceptar]**
   * Seleccione **[!UICONTROL Guardar todo]**



>[!NOTE]
>
>Si el sitio no es un sitio de la comunidad, es necesario descubrir la existencia o ubicación de las bibliotecas cliente que se utilizan para el sitio.

Con el ejemplo de [Introducción a AEM Communities](getting-started.md) , donde `site-name` se *involucra*, así es como aparecerá clientliblist si se agrega el componente de revisiones:

![chlimage_1-247](assets/chlimage_1-247.png)

