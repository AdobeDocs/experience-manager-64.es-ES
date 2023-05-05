---
title: Crear los componentes
seo-title: Create the Components
description: Crear el componente Comentarios
seo-description: Create the Comments component
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
exl-id: 48809969-5d14-41bb-bc6d-5857e679ceba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 6%

---

# Crear los componentes {#create-the-components}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El ejemplo de ampliación de componentes utiliza el sistema de comentarios, que en realidad está compuesto por dos componentes

* Comentarios : el sistema de comentarios que incluye el componente colocado en una página.
* Comentario : El componente que captura una instancia de un comentario publicado.

Se deben implementar ambos componentes, especialmente si se personaliza el aspecto de un comentario publicado.

>[!NOTE]
>
>Solo se permite un sistema de comentarios por página de sitio.
>
>Muchas funciones de Communities ya incluyen un sistema de comentarios cuyo resourceType se puede modificar para hacer referencia al sistema de comentarios ampliado.

## Crear el componente Comentarios {#create-the-comments-component}

Estas direcciones especifican un **Grupo** valor distinto de `.hidden` por lo tanto, el componente puede estar disponible desde el navegador de componentes (barra de tareas).

La eliminación del archivo JSP creado automáticamente se debe a que se utilizará el archivo HBS predeterminado en su lugar.

1. Vaya a **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Cree una ubicación para aplicaciones personalizadas:

   * Seleccione el `/apps` node

      * **Crear carpeta** named **[!UICONTROL custom]**
   * Seleccione el `/apps/custom` node

      * **Crear carpeta** named **[!UICONTROL componentes]**


1. Seleccione el `/apps/custom/components` node

   * **[!UICONTROL Crear > Componente...]**

      * **Etiqueta**: *comentarios*
      * **Título**: *Comentarios Alt*
      * **Descripción**: *Estilo de comentarios alternativo*
      * **Super Tipo**: *social/commons/components/hbs/comments*
      * **Grupo**: *Personalizado*
   * Seleccione **[!UICONTROL Siguiente]**
   * Seleccione **[!UICONTROL Siguiente]**
   * Seleccione **[!UICONTROL Siguiente]**
   * Select **[!UICONTROL OK]**


1. Expanda el nodo recién creado: `/apps/custom/components/comments`
1. Select **[!UICONTROL Guardar todo]**
1. Clic con el botón derecho `comments.jsp`
1. Seleccione **[!UICONTROL Eliminar]**
1. Select **[!UICONTROL Guardar todo]**

![chlimage_1-70](assets/chlimage_1-70.png)

### Crear el componente de comentario secundario {#create-the-child-comment-component}

Estas direcciones están configuradas **Grupo** a `.hidden` ya que solo el componente principal debe incluirse en una página.

La eliminación del archivo JSP creado automáticamente se debe a que se utilizará el archivo HBS predeterminado en su lugar.

1. Vaya a la `/apps/custom/components/comments` node
1. Haga clic con el botón derecho en el nodo

   * Select **[!UICONTROL Crear > Componente...]**

      * **Etiqueta**: *comment*
      * **Título**: *Comentario alternativo*
      * **Descripción**: *Estilo de comentario alternativo*
      * **Super Tipo**: *social/commons/components/hbs/comments/comment*
      * **Grupo**: `*.hidden*`
   * Seleccione **[!UICONTROL Siguiente]**
   * Seleccione **[!UICONTROL Siguiente]**
   * Seleccione **[!UICONTROL Siguiente]**
   * Select **[!UICONTROL OK]**


1. Expanda el nodo recién creado: `/apps/custom/components/comments/comment`
1. Select **[!UICONTROL Guardar todo]**
1. Clic con el botón derecho `comment.jsp`
1. Seleccione **[!UICONTROL Eliminar]**
1. Select **[!UICONTROL Guardar todo]**

![chlimage_1-71](assets/chlimage_1-71.png) ![chlimage_1-72](assets/chlimage_1-72.png)

### Copiar y modificar los scripts HBS predeterminados {#copy-and-modify-the-default-hbs-scripts}

Uso [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Copie `comments.hbs`

   * De [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * Hasta [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Editar `comments.hbs` a:

   * Cambiar el valor de la variable `data-scf-component` (~line 20):

      * De `social/commons/components/hbs/comments`
      * A `/apps/custom/components/comments`
   * Modifique para incluir el componente de comentario personalizado (~line 75):

      * Replace `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * con `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Copie `comment.hbs`

   * De [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * Hasta [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Editar `comment.hbs` a:

   * Cambiar el valor del atributo data-scf-component (~ línea 19)

      * De `social/commons/components/hbs/comments/comment`
      * A `/apps/custom/components/comments/comment`

* Select `/apps/custom` node
* Select **[!UICONTROL Guardar todo]**

## Crear una carpeta de biblioteca de cliente {#create-a-client-library-folder}

Para evitar tener que incluir explícitamente esta biblioteca de cliente, se podría usar el valor de categorías para la clientlib del sistema de comentarios predeterminado ( `cq.social.author.hbs.comments`), pero entonces esta clientlib se incluiría también para todas las instancias del componente predeterminado.

Uso [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Select `/apps/custom/components/comments` node
* Select **[!UICONTROL Crear nodo]**

   * **Nombre**: `clientlibs`
   * **Tipo**: `cq:ClientLibraryFolder`
   * Agregar a **[!UICONTROL Propiedades]** pestaña:

      * **Nombre** `categories` **Tipo** `String` **Valor** `cq.social.author.hbs.comments` `Multi`
      * **Nombre** `dependencies` **Tipo** `String` **Valor** `cq.social.scf` `Multi`

* Select **[!UICONTROL Guardar todo]**
* con `/apps/custom/components/comments/clientlib`como nodo seleccionado, cree 3 archivos:

   * **Nombre**: `css.txt`
   * **Nombre**: `js.txt`
   * **Nombre**: customcomentsystem.js

* Introduzca &#39;customcomentsystem.js&#39; como contenido de `js.txt`
* Select **[!UICONTROL Guardar todo]**

![chlimage_1-73](assets/chlimage_1-73.png)

## Registrar el modelo y la vista de SCF {#register-the-scf-model-view}

Al ampliar (anular) un componente SCF, resourceType es diferente (al superponer se utiliza el mecanismo de búsqueda relativo que busca `/apps` before `/libs` para que resourceType siga siendo el mismo). Por este motivo es necesario escribir JavaScript (en la biblioteca de cliente) para registrar el modelo JS de SCF y ver el resourceType personalizado.

Introduzca el siguiente texto como contenido de `customcommentsystem.js`:

### customcommentsystem.js {#customcommentsystem-js}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";
 
    var CustomComment = SCF.Components["social/commons/components/hbs/comments/comment"].Model;
    var CustomCommentView = SCF.Components["social/commons/components/hbs/comments/comment"].View;

    var CustomCommentSystem = SCF.Components["social/commons/components/hbs/comments"].Model;
    var CustomCommentSystemView = SCF.Components["social/commons/components/hbs/comments"].View;
 
    SCF.registerComponent('/apps/custom/components/comments/comment', CustomComment, CustomCommentView);
    SCF.registerComponent('/apps/custom/components/comments', CustomCommentSystem, CustomCommentSystemView);

})($CQ, _, Backbone, SCF);
```

* Select **[!UICONTROL Guardar todo]**

## Publicar la aplicación {#publish-the-app}

Para experimentar el componente ampliado en el entorno de publicación, es necesario duplicar el componente personalizado.

Una forma de hacerlo es

* Desde la navegación global

   * Select **[!UICONTROL Herramientas > Implementación > Replicación]**
   * Seleccionar `Activate Tree`
   * Establezca `Start Path`: a `/apps/custom`
   * Desmarcar `Only Modified`
   * Select `Activate`botón
