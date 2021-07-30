---
title: Administración de etiquetas
seo-title: Administración de etiquetas
description: Obtenga información sobre cómo administrar Etiquetas en AEM.
seo-description: Obtenga información sobre cómo administrar Etiquetas en AEM.
uuid: 77e1280a-feea-4edd-94b6-4fb825566c42
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 69253ee9-8c28-436b-9331-6fb875f64cba
exl-id: 5c78edf8-148f-41a3-8b11-c1dada34090e
source-git-commit: 2208d23985ebd913b6aa9dee3bf16ce7529a8fa6
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 5%

---

# Administración de etiquetas{#administering-tags}

Las etiquetas son un método rápido y fácil de clasificar contenido dentro de un sitio web. Se pueden considerar como palabras clave o etiquetas (metadatos) que permiten encontrar el contenido más rápidamente como resultado de una búsqueda.

En Adobe Experience Manager (AEM), una etiqueta puede ser una propiedad de

* un nodo de contenido para una página (consulte [Uso de etiquetas](/help/sites-authoring/tags.md))

* un nodo de metadatos para un recurso (consulte [Administración de metadatos para recursos digitales](/help/assets/metadata.md))

Además de las páginas y los recursos, las etiquetas se utilizan para las funciones de AEM Communities

* contenido generado por el usuario (consulte [Etiquetado UGC)](/help/communities/tag-ugc.md)

* Recursos de habilitación (consulte [Etiquetado de recursos de habilitación](/help/communities/functions.md#catalog-function))

## Características de las etiquetas {#tag-features}

Algunas de las características de las etiquetas de AEM incluyen:

* Las etiquetas se pueden agrupar en varios espacios de nombres. Tales jerarquías permiten la construcción de taxonomías. Estas taxonomías son globales a lo largo de AEM.
* La restricción principal para las etiquetas recién creadas es que deben ser únicas dentro de un espacio de nombres específico.
* El título de una etiqueta no debe incluir caracteres de separación de ruta de etiqueta (tampoco se mostrarán si están presentes)

   * dos puntos (:): delimita la etiqueta del espacio de nombres
   * barra diagonal (/): delimita las subetiquetas

* Los autores y los visitantes del sitio pueden aplicar etiquetas. Independientemente del creador, todas las formas de etiquetas están disponibles para selección, tanto durante la asignación a una página como durante la búsqueda.
* Los miembros del grupo &quot;administradores de etiquetas&quot; y los miembros que tengan derechos de modificación a `/content/cq:tags` pueden crear etiquetas y modificar su taxonomía.

   * Una etiqueta que contiene etiquetas secundarias se denomina etiqueta contenedora
   * Una etiqueta que no es una etiqueta contenedora se denomina etiqueta hoja
   * Un espacio de nombres de etiqueta es una etiqueta de hoja o una etiqueta de contenedor

* Las etiquetas las utiliza el [componente de búsqueda](https://helpx.adobe.com/experience-manager/core-components/using/quick-search.html) para facilitar la búsqueda de contenido.
* Las etiquetas las utiliza el [componente teaser](https://helpx.adobe.com/experience-manager/core-components/using/teaser.html), que supervisa la nube de etiquetas de un usuario para proporcionar contenido de destino.
* Si el etiquetado es un aspecto importante del contenido

   * asegúrese de empaquetar etiquetas con las páginas que las utilizan
   * asegúrese de [permisos de etiqueta](#setting-tag-permissions) habilitar acceso de lectura

## Consola de etiquetado {#tagging-console}

La consola Etiquetado se utiliza para crear y administrar etiquetas y sus taxonomías. Un objetivo es evitar tener muchas etiquetas similares relacionadas básicamente con lo mismo: por ejemplo, página y páginas o calzado y zapatos.

Las etiquetas se administran agrupando en áreas de nombres, revisando el uso de las etiquetas existentes antes de crear otras nuevas y reorganizando sin desconectar la etiqueta del contenido al que se hace referencia actualmente.

Para acceder a la consola Etiquetado :

* en author
* iniciar sesión con privilegios administrativos
* desde la navegación global

   * select **`Tools`**
   * seleccione **`General`**
   * seleccione **`Tagging`**

![managing_tags_usingthetagasministrationconsole](assets/managing_tags_usingthetagasministrationconsole.png)

### Creación de un área de nombres {#creating-a-namespace}

Para crear un nuevo espacio de nombres, seleccione el icono **`Create Namespace`**.

El área de nombres es en sí misma una etiqueta y no necesita contener ninguna subetiqueta. Sin embargo, para seguir creando una taxonomía, [cree subetiquetas](#creating-tags), que a su vez pueden ser etiquetas de hoja o de contenedor.

![chlimage_1-183](assets/chlimage_1-183.png) ![creating_tags_andnamespaces](assets/creating_tags_andnamespaces.png)

* **Título**
* (obligatorio) *Un título de visualización para el espacio de nombres.

* **Nombre**
* (opcional) *Un nombre para el área de nombres. Si no se especifica, se crea un nombre de nodo válido desde el Título. Consulte [TagID](/help/sites-developing/framework.md#tagid).

* **Descripción**
* (opcional) *Una descripción del área de nombres.

Una vez introducida la información requerida

* seleccione **Crear**

### Operaciones con etiquetas {#operations-on-tags}

Si se selecciona un área de nombres u otra etiqueta, está disponible la siguiente operación :

* [Ver propiedades](#viewing-tag-properties)
* [Referencias](#showing-tag-references)
* [Crear etiqueta](#creating-tags)
* [Editar](#editing-tags)
* [Mover](#moving-tags)
* [Combinar](#merging-tags)
* [Publicación](#publishing-tags)
* [Cancelar publicación](#unpublishing-tags)
* [Eliminar](#deleting-tags)

![chlimage_1-184](assets/chlimage_1-184.png)

Cuando la ventana del explorador no es lo suficientemente ancha como para mostrar todos los iconos, los iconos situados más a la derecha se agrupan en un icono **`... More`**, que mostrará una lista desplegable de los iconos de operación ocultos cuando se seleccionen.

![chlimage_1-185](assets/chlimage_1-185.png)

### Selección de una etiqueta de área de nombres {#selecting-a-namespace-tag}

Cuando se selecciona por primera vez, si el espacio de nombres no contiene etiquetas, las propiedades se muestran a la derecha; de lo contrario, se muestran las etiquetas secundarias. Cada etiqueta seleccionada mostrará las etiquetas que contiene o sus propiedades si no tiene etiquetas secundarias.

Para seleccionar la etiqueta para las operaciones y para seleccionar varias opciones, seleccione solo el icono al lado del título. Al seleccionar el título, solo se mostrarán las propiedades o se abrirá la etiqueta para mostrar su contenido.

![chlimage_1-186](assets/chlimage_1-186.png) ![chlimage_1-187](assets/chlimage_1-187.png)

### Visualización de las propiedades de la etiqueta {#viewing-tag-properties}

![chlimage_1-188](assets/chlimage_1-188.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, la selección del icono **`View Properties`** da como resultado la visualización de información sobre el `name`, la hora de la última edición y el número de referencias. Si se publica, se muestra la hora de la última publicación y el id del editor. Esta información aparecerá en una columna a la izquierda de las columnas de etiquetas.

![chlimage_1-189](assets/chlimage_1-189.png)

### Mostrar referencias de etiquetas {#showing-tag-references}

![chlimage_1-190](assets/chlimage_1-190.png)

Cuando se selecciona un área de nombres u otra etiqueta, al seleccionar el icono **`References`**se identificará el contenido al que se ha aplicado la etiqueta.

La visualización inicial es un recuento de etiquetas aplicadas.

![chlimage_1-191](assets/chlimage_1-191.png)

Al seleccionar la flecha a la derecha del recuento, se muestran los nombres de referencia.

La ruta a la referencia se muestra como información del objeto al pasar el ratón por encima de una referencia.

![chlimage_1-192](assets/chlimage_1-192.png)

### Creación de etiquetas {#creating-tags}

![chlimage_1-193](assets/chlimage_1-193.png)

Cuando se selecciona un espacio de nombres u otra etiqueta (seleccionando el icono junto al título), se puede crear una etiqueta secundaria para la etiqueta actual seleccionando el icono **`Create Tag`**.

![chlimage_1-194](assets/chlimage_1-194.png)

* **Título**
* (obligatorio) *Un título para mostrar para la etiqueta.

* **Nombre**
* (opcional) *Un nombre para la etiqueta. Si no se especifica, se crea un nombre de nodo válido desde el Título. Consulte [TagID](/help/sites-developing/framework.md#tagid).

* **Descripción**
* (opcional) *Una descripción de la etiqueta.

Una vez introducida la información requerida

* seleccione **Crear**

### Edición de tags {#editing-tags}

![chlimage_1-195](assets/chlimage_1-195.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, es posible modificar el Título, la Descripción y proporcionar las localizaciones del Título seleccionando el icono **`Edit`**.

Después de realizar las ediciones, seleccione **Guardar**.

Para obtener más información sobre cómo agregar traducciones de idioma, consulte la sección sobre [Administración de etiquetas en diferentes idiomas](#managing-tags-in-different-languages).

![chlimage_1-196](assets/chlimage_1-196.png)

### Movimiento de tags {#moving-tags}

![chlimage_1-197](assets/chlimage_1-197.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, la selección del icono **`Move`** permitirá a los administradores y desarrolladores de etiquetas limpiar la taxonomía moviendo la etiqueta a una nueva ubicación o cambiando su nombre. Cuando la etiqueta seleccionada es una etiqueta contenedora, al mover la etiqueta también se moverán todas las etiquetas secundarias.

>[!NOTE]
>
>Se recomienda que los autores solo puedan [editar](#editing-tags) la `title` etiqueta de la etiqueta, no mover ni cambiar el nombre de las etiquetas.

![chlimage_1-198](assets/chlimage_1-198.png)

* **Ruta**

   *(solo lectura)* La ruta actual a la etiqueta seleccionada.

* **Desplácese**
a la nueva ruta en la que se moverá la etiqueta .

* **Cambiar nombre**
aMuestra inicialmente el 
`name`de la etiqueta . Se puede introducir un nuevo `name`.

* seleccione **Guardar**

### Combinación de tags {#merging-tags}

![chlimage_1-199](assets/chlimage_1-199.png)

Se pueden combinar etiquetas cuando una taxonomía tiene duplicados. Cuando la etiqueta A se combina con la etiqueta B, todas las páginas etiquetadas con la etiqueta A se etiquetarán con la etiqueta B y la etiqueta A ya no estará disponible para los autores.

Cuando se selecciona un espacio de nombres u otra etiqueta, al seleccionar el icono **`Merge`**se abrirá un panel en el que se puede seleccionar la ruta de acceso en la que se va a combinar.

![chlimage_1-200](assets/chlimage_1-200.png)

* **Ruta**

   *(readonly)* La ruta de la etiqueta seleccionada para combinarse en otra etiqueta.

* **Combine**
enExaminar para seleccionar la ruta de la etiqueta en la que desea combinar.

>[!NOTE]
>
>Después de la combinación, la **ruta **seleccionada originalmente (virtualmente) ya no existe.
>
>Cuando se mueve o combina una etiqueta referenciada, la etiqueta no se elimina físicamente de modo que sea posible mantener referencias.

### Publicación de etiquetas {#publishing-tags}

![chlimage_1-201](assets/chlimage_1-201.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, se selecciona el icono **`Publish`**para activar la etiqueta en el entorno de publicación. De forma similar al contenido de la página, solo se publica la etiqueta seleccionada, independientemente de si es una etiqueta contenedora o no.

Para publicar una taxonomía (un área de nombres y subetiquetas), la práctica recomendada es crear un [paquete](/help/sites-administering/package-manager.md) del área de nombres (consulte [Nodo raíz de taxonomía](/help/sites-developing/framework.md#taxonomy-root-node)). Asegúrese de [aplicar permisos](#setting-tag-permissions) al espacio de nombres antes de crear el paquete.

### Cancelación de la publicación de etiquetas {#unpublishing-tags}

![chlimage_1-202](assets/chlimage_1-202.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, al seleccionar el icono **`Unpublish`**se desactiva la etiqueta en el entorno de creación y se elimina del entorno de publicación. De forma similar a la operación `Delete`, si la etiqueta seleccionada es una etiqueta contenedora, todas las etiquetas secundarias se desactivarán en el entorno de creación y se eliminarán del entorno de publicación.

### Eliminación de tags {#deleting-tags}

![chlimage_1-203](assets/chlimage_1-203.png)

Cuando se selecciona un espacio de nombres u otra etiqueta, al seleccionar el icono **`Delete`**se elimina permanentemente la etiqueta del entorno de creación. Si la etiqueta se publicó, también se elimina del entorno de publicación. Si la etiqueta seleccionada es una etiqueta contenedora, también se eliminarán todas sus etiquetas secundarias.

## Configuración de permisos de etiquetas {#setting-tag-permissions}

Los permisos de etiquetas son [&#39;secure (de forma predeterminada)&#39;](/help/sites-administering/production-ready.md); una práctica recomendada para el entorno de publicación que requiere permiso de lectura para permitir explícitamente etiquetas. Básicamente, esto se hace creando un paquete del espacio de nombres de la etiqueta después de que se hayan establecido los permisos en el autor e instalando el paquete en todas las instancias de publicación.

* en instancia de autor

   * iniciar sesión con privilegios administrativos
   * acceda a la [Consola de seguridad](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console),

      * por ejemplo, vaya a http://localhost:4502/useradmin
   * en el panel izquierdo, seleccione el grupo (o usuario) para el que se va a conceder [permiso de lectura](/help/sites-administering/security.md#permissions)
   * en el panel derecho, busque **Ruta **al área de nombres de la etiqueta

      * por ejemplo, `/content/cq:tags/mycommunity`
   * seleccione `checkbox`en la columna **Read**
   * seleccione **Guardar**



![chlimage_1-204](assets/chlimage_1-204.png)

* garantizar que todas las instancias de publicación tengan los mismos permisos

   * un método es [crear un paquete](/help/sites-administering/package-manager.md#package-manager) del espacio de nombres en author

      * en la pestaña `Advanced`, para `AC Handling` seleccione `Overwrite`
   * replicar el paquete

      * elija `Replicate` en el gestor de paquetes


## Administración de tags en distintos idiomas {#managing-tags-in-different-languages}

La propiedad `title`de una etiqueta puede traducirse a varios idiomas. Una vez traducida, la etiqueta apropiada `title`puede mostrarse según el idioma del usuario o el idioma de la página.

### Definición de títulos de tags en varios idiomas {#defining-tag-titles-in-multiple-languages}

A continuación se describe cómo traducir el `title`de la etiqueta **Animals** de inglés a alemán y francés.

Para empezar, seleccione la etiqueta en el espacio de nombres **Stock Photography** y seleccione el icono **`Edit`**(consulte la sección [Edición de etiquetas](#editing-tags)).

El panel Editar etiqueta presenta la capacidad de elegir los idiomas en los que se localizará el título de la etiqueta.

A medida que se selecciona cada idioma, aparece un cuadro de entrada de texto en el que se puede introducir el título traducido.

Una vez introducidas todas las traducciones, seleccione **Guardar **para salir del modo de edición.

![chlimage_1-205](assets/chlimage_1-205.png)

En general, el idioma elegido para la etiqueta se toma del idioma de la página, cuando está disponible. Cuando se utiliza la [ `tag` utilidad](/help/sites-developing/building.md#tagging-on-the-client-side) en otros casos (por ejemplo, en formularios o en cuadros de diálogo), el idioma de la etiqueta depende del contexto.

En lugar de utilizar la configuración de idioma de la página, la consola Etiquetado utiliza la configuración de idioma del usuario. En la consola Etiquetado, para la etiqueta &quot;Animals&quot;, se mostraba &quot;Animaux&quot; para un usuario que establecía el idioma en francés en sus propiedades de usuario.

Para agregar un nuevo idioma al cuadro de diálogo, consulte [Adición de un nuevo idioma al cuadro de diálogo Editar etiqueta](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog).

>[!NOTE]
>
>La nube de etiquetas y las palabras clave meta del componente de página estándar utilizan la etiqueta localizada `titles`en función del idioma de la página, si está disponible.

## Medios {#resources}

* [Etiquetado para desarrolladores](/help/sites-developing/tags.md)

   Información sobre el marco de etiquetado, así como la ampliación e inclusión de etiquetas en aplicaciones personalizadas.

* [Consola de etiquetado de la IU clásica](/help/sites-administering/classic-console.md)
