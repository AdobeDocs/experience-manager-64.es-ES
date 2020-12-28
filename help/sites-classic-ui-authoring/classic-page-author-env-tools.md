---
title: 'Creación: Entorno y herramientas'
seo-title: 'Creación: entorno y herramientas'
description: La consola Sitios web permite desplazarse por el sitio web y administrarlo. La estructura del sitio web, dividida en dos paneles, se puede ampliar para realizar acciones en los elementos necesarios.
seo-description: La consola Sitios web permite desplazarse por el sitio web y administrarlo. La estructura del sitio web, dividida en dos paneles, se puede ampliar para realizar acciones en los elementos necesarios.
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 87%

---


# Creación: Entorno y herramientas{#authoring-the-environment-and-tools}

El entorno de creación AEM ofrece varios mecanismos para organizar y editar el contenido. Se puede acceder a las herramientas desde varios editores de páginas y distintas consolas.

## Administración de sitios {#site-administration}

La consola **Sitios web** permite desplazarse por el sitio web y administrarlo. La estructura del sitio web, dividida en dos paneles, se puede ampliar para realizar acciones en los elementos necesarios:

![chlimage_1-153](assets/chlimage_1-153.png)

## Edición del contenido de la página {#editing-your-page-content}

Hay un editor de páginas independiente en la IU clásica; utiliza el buscador de contenido y la barra de tareas:

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## Acceso a la Ayuda {#accessing-help}

Se puede acceder a varios medios de **Ayuda** directamente desde AEM:

Además de poder acceder a la [ayuda desde las barras de herramientas de la consola](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help), también se puede acceder a ella desde la barra de tareas (utilizando el icono ?) al editar una página:

![](do-not-localize/sidekick-collapsed-2.png)

O con el botón **Ayuda** del cuadro de diálogo de edición de componentes específicos; esto mostrará la ayuda contextual.

## Barra de tareas {#sidekick}

La ficha **Componentes** de la barra de tareas le permite explorar los componentes que se pueden añadir a la página actual. El grupo requerido puede ampliarse y, a continuación, un componente puede arrastrarse a la ubicación deseada de la página.

![chlimage_1-155](assets/chlimage_1-155.png)

## Buscador de contenido {#the-content-finder}

El buscador de contenido es una forma rápida y fácil de encontrar activos y contenido dentro del repositorio mientras se edita una página.

Puede utilizar el buscador de contenido para ubicar toda una serie de medios. Cuando convenga, puede arrastrar un elemento y colocarlo en un párrafo de la página:

* [Imágenes](#finding-images)
* [Documentos](#finding-documents)
* [Películas](#finding-movies)
* [Navegador de medios de Scene 7](/help/sites-administering/scene7.md#scene7contentbrowser)
* [Páginas](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [Párrafos](#referencing-paragraphs-from-other-pages)
* [Productos](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* O bien para [examinar el sitio web según la estructura del repositorio](#the-content-finder)

Puede [buscar elementos específicos](#the-content-finder) con todas las opciones.

### Búsqueda de imágenes {#finding-images}

En esta ficha aparece una lista con las imágenes del repositorio.

Después de crear un párrafo de imagen en la página, puede arrastrar un elemento y colocarlo adentro del párrafo.

![chlimage_1-156](assets/chlimage_1-156.png)

### Búsqueda de documentos {#finding-documents}

En esta ficha, se muestra una lista con los documentos del repositorio.

Después de crear un párrafo Download en la página, puede arrastrar un elemento y colocarlo adentro del párrafo.

![chlimage_1-157](assets/chlimage_1-157.png)

### Búsqueda de películas {#finding-movies}

Esta ficha enumera las películas (por ejemplo, elementos de Flash) del repositorio.

Después de crear un párrafo apropiado (por ejemplo, Flash) en la página, puede arrastrar un elemento y colocarlo dentro del párrafo.

![chlimage_1-158](assets/chlimage_1-158.png)

### Productos {#products}

Esta ficha enumera los productos. Después de crear un párrafo apropiado (por ejemplo, Producto) en la página, puede arrastrar un elemento y colocarlo dentro del párrafo.

![chlimage_1-159](assets/chlimage_1-159.png)

### Búsqueda de páginas {#finding-pages}

Esta ficha muestra todas las páginas. Haga clic con el doble en cualquier página para abrirla y editarla.

![chlimage_1-160](assets/chlimage_1-160.png)

### Referencia a párrafos de otras páginas {#referencing-paragraphs-from-other-pages}

Esta ficha permite buscar otra página. Se mostrará una lista con todos los párrafos de esa página. Luego puede arrastrar un párrafo a su página actual para crear una referencia al párrafo original.

![chlimage_1-161](assets/chlimage_1-161.png)

### Uso de la vista de repositorio completo {#using-the-full-repository-view}

En esta ficha, se muestran todos los medios del repositorio.

![chlimage_1-162](assets/chlimage_1-162.png)

### Utilización de la búsqueda con el navegador de contenido {#using-search-with-the-content-browser}

Puede buscar elementos específicos en todas las opciones. Cualquier etiqueta y medio que coincida con el patrón de búsqueda aparece en una lista:

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

También puede utilizar caracteres comodín en las búsquedas. Se admiten los caracteres comodín siguientes:

* `*` - Hace coincidir una secuencia de cero o más caracteres.

* `?` - Hace coincidir un solo carácter.

>[!NOTE]
>
>Hay una seudopropiedad &quot;name&quot; que debe utilizarse para realizar búsquedas de comodín.

Por ejemplo, si hay disponible una imagen con el nombre:

`ad-nmvtis.jpg`

Los siguientes patrones de búsqueda la encontrarán (así como cualquier otra imagen que coincida con el patrón):

* `name:*nmv*`
* `name:AD*` - la coincidencia de caracteres *no* distingue entre mayúsculas y minúsculas.
* `name:ad?nm??is.*` - en una consulta, puede utilizar tantos caracteres comodín como desee.

>[!NOTE]
>
>También puede utilizar la búsqueda [SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html).

## Mostrar referencias {#showing-references}

AEM permite ver qué páginas están vinculadas a la página con la que está trabajando.

Para mostrar referencias de páginas directas:

1. En la barra de tareas, seleccione el icono de ficha **Página**.

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. Seleccione **Mostrar referencias...** AEM abre la ventana Referencias y muestra qué páginas hacen referencia a la página seleccionada, incluidas sus rutas.

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

En determinadas situaciones, hay disponibles acciones adicionales en la barra de tareas, como:

* [Lanzamientos](/help/sites-classic-ui-authoring/classic-launches.md)
* [Live Copies](/help/sites-administering/msm.md)

* [Modelo](/help/sites-administering/msm-best-practices.md)

Se pueden ver otras [relaciones entre páginas en la consola Sitios web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console).

## Registro de auditorías {#audit-log}

Se puede acceder al **registro de auditoría** desde la ficha **Información** de la barra de tareas. Enumera las acciones recientes realizadas en la página actual; por ejemplo:

![chlimage_1-163](assets/chlimage_1-163.png)

## Información de la página {#page-information}

La consola Sitio web también [proporciona información sobre el estado actual de la página](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) como publicación, modificación, bloqueo, Live Copy, etc.

## Modos de página    {#page-modes}

Al editar una página con la IU clásica hay varios modos a los que se puede acceder mediante los iconos en la parte inferior de la barra de tareas:

![](do-not-localize/chlimage_1-15.png)

La fila de iconos en la parte inferior de la barra de tareas se usa para cambiar de modo al trabajar con las páginas:

* [Editar](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   Este es el modo predeterminado y le permite editar la página, al agregar o eliminar componentes y hacer otros cambios.

* [Vista previa](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   Este modo permite obtener una vista previa de la página como si apareciera en el sitio web con formato final.

* [Diseño](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   En este modo, puede editar el diseño de la página configurando los componentes accesibles.

>[!NOTE]
>
>Hay otras opciones disponibles:
>
>* [Andamiaje](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [ClientContext](/help/sites-administering/client-context.md)
>* Sitios web: abrirá la consola Sitios web
>* Volver a cargar: actualizará la página.


## Métodos abreviados del teclado {#keyboard-shortcuts}

Hay varios [métodos abreviados del teclado](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) disponibles.
