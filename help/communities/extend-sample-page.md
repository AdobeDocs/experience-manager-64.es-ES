---
title: Añadir comentario a página de muestra
seo-title: Añadir comentario a página de muestra
description: Añadir comentarios personalizados a una página
seo-description: Añadir comentarios personalizados a una página
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
translation-type: tm+mt
source-git-commit: 44c56ec5de6e9a832aaa52ab4a6c4978af7a9865
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Añadir comentario en página de muestra {#add-comment-to-sample-page}

Ahora que los componentes del sistema de comentarios personalizados están en su lugar en el directorio de aplicaciones (/apps), es posible utilizar el componente extendido. La instancia del sistema de comentarios de un sitio web que se verá afectado debe establecer resourceType como el sistema de comentarios personalizado e incluir todas las bibliotecas de cliente necesarias.

## Identifique los clientes {#identify-required-clientlibs} requeridos

Las bibliotecas de cliente necesarias para el estilo y funcionamiento de los comentarios predeterminados también son necesarias para los comentarios extendidos.

La [Guía de componentes de comunidad](components-guide.md) identifica las bibliotecas de cliente requeridas. Vaya a la Guía del componente y vista del componente Comentarios, por ejemplo:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Tenga en cuenta las tres bibliotecas de cliente necesarias para que Comentarios se procese y funcione correctamente. Será necesario incluirlos donde se haga referencia a los Comentarios extendidos, así como a la biblioteca cliente [Comentarios extendidos&#39;](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Añadir comentarios personalizados a una página {#add-custom-comments-to-a-page}

Como sólo puede haber un sistema de comentarios por página, es más sencillo crear una página de muestra como se describe en el breve tutorial [Crear una página de muestra](create-sample-page.md).

Una vez creado, ingrese al modo Diseño y ponga a disposición el grupo de componentes Personalizado para permitir que el componente `Alt Comments` se agregue a la página.

Para que el comentario aparezca y funcione correctamente, las bibliotecas de cliente para Comentarios deben agregarse a la lista clientlibsde la página (consulte [Clientlibs para componentes de comunidades](clientlibs.md)).

### Comentarios de Clientlibs en la página de muestra {#comments-clientlibs-on-sample-page}

![Comentarios de clientes en la página de muestra](assets/chlimage_1-48.png)

### Autor: Comentario alternativo en la página de muestra {#author-alt-comment-on-sample-page}

![Comentario alternativo en la página de muestra](assets/chlimage_1-49.png)

### Autor: Nodo de comentarios de página de muestra {#author-sample-page-comments-node}

Puede comprobar resourceType en CRXDE viendo las propiedades del nodo de comentarios de la página de muestra en `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Publicar página de muestra {#publish-sample-page}

Una vez agregado el componente personalizado a la página, también es necesario (re) [publicar la página](sites-console.md#publishing-the-site).

### Publicar: Comentario alternativo en la página de muestra {#publish-alt-comment-on-sample-page}

Después de publicar tanto la aplicación personalizada como la página de muestra, debería ser posible introducir un comentario. Al iniciar sesión, ya sea con un [usuario de demostración](tutorials.md#demo-users) o administrador, debería ser posible publicar un comentario.

Aquí está aaron.mcdonald@mailinator.com un comentario:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Ahora que parece que el componente extendido funciona correctamente con la apariencia predeterminada, es hora de modificar la apariencia.

