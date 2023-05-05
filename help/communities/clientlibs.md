---
title: Clientlibs para componentes de Communities
seo-title: Clientlibs for Communities Components
description: Bibliotecas de cliente para comunidades
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 3%

---

# Clientlibs para componentes de Communities {#clientlibs-for-communities-components}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

En esta sección de la documentación se describe cómo agregar bibliotecas del lado del cliente (clientlibs) a una página para componentes de Communities.

Para obtener información básica, visite:

* [Uso de bibliotecas del lado del cliente](../../help/sites-developing/clientlibs.md) que proporciona detalles de uso, así como herramientas de depuración
* [Clientlibs para SCF](client-customize.md#clientlibs) que proporciona información útil al personalizar componentes de SCF

## Por qué se requieren Clientlibs {#why-clientlibs-are-required}

Las bibliotecas de clientes son necesarias para el correcto funcionamiento (JavaScript) y el estilo (CSS) de un componente.

Cuando existe un [función de comunidad](functions.md) para una función, todos los componentes y configuraciones necesarios, incluido el clientlibs requerido, estarán presentes en el sitio de la comunidad. Solo si los componentes adicionales van a estar disponibles para los autores, se necesitarán añadir clientlibs adicionales.

Cuando faltan las clientlibs requeridas, [adición de un componente Comunidades a una página](author-communities.md) podría provocar errores de javascript y un aspecto inesperado.

### Ejemplo: Revistas colocadas sin Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Ejemplo: Revisiones colocadas con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificación de Clientlibs Requeridos {#identifying-required-clientlibs}

La información de funciones esenciales para los desarrolladores identifica los clientlibs necesarios.

Además, desde una instancia de AEM, vaya a la [Guía de componentes de comunidad](components-guide.md) proporciona acceso a una lista de categorías clientlib requeridas para un componente.

Por ejemplo, en la parte superior del [Página de revisiones](http://localhost:4502/content/community-components/en/reviews.html) los clientlibs requeridos enumerados son

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Adición de Clientlibs Necesarios {#adding-required-clientlibs}

Cuando se desee añadir un componente Comunidades a una página, será necesario agregar las clientlibs necesarias para el componente si no está presente.

Uso [CRXDE|Lite](#using-crxde-lite) para modificar una lista de clientlibslist existente para una página de sitio de la comunidad.

Para agregar una clientlib para un sitio de la comunidad usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Vaya a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Busque la variable `clientlibslist` nodo de la página en la que desea añadir el componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* con `clientlibslist` nodo seleccionado

   * Localizar la cadena[] property `scg:requiredClientLibs`
   * Seleccione su `Value` para acceder al cuadro de diálogo matriz de cadenas

      * Desplácese hacia abajo si es necesario
      * Select `+` para introducir una nueva biblioteca de cliente

         * Repetir para agregar más bibliotecas de cliente
      * Select **[!UICONTROL OK]**
   * Select **[!UICONTROL Guardar todo]**



>[!NOTE]
>
>Si el sitio no es un sitio de la comunidad, es necesario descubrir la existencia o ubicación de las bibliotecas de cliente que se utilizan para el sitio.

Al usar la variable [Introducción a AEM Communities](getting-started.md) ejemplo, donde `site-name` es *participación*, así es como aparecerá clientliblist si agrega el componente de revisiones:

![chlimage_1-247](assets/chlimage_1-247.png)
