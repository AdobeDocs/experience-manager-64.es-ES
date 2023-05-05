---
title: Agregar comentario a una página de muestra
seo-title: Add Comment to Sample Page
description: Agregar comentarios personalizados a una página
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# Agregar comentario a una página de muestra {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Ahora que los componentes del sistema de comentarios personalizados están en su lugar en el directorio de aplicaciones (/apps), es posible utilizar el componente ampliado. La instancia del sistema de comentarios de un sitio web afectado debe establecer su resourceType como sistema de comentarios personalizado e incluir todas las bibliotecas de cliente necesarias.

## Identificar Clientlibs Necesarios {#identify-required-clientlibs}

Las bibliotecas de cliente necesarias para el estilo y funcionamiento de los Comentarios predeterminados también son necesarias para los Comentarios extendidos.

La variable [Guía de componentes de comunidad](components-guide.md) identifica las bibliotecas de cliente necesarias. Vaya a la Guía del componente y vea el componente Comentarios, por ejemplo:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Tenga en cuenta las tres bibliotecas de cliente necesarias para que Comentarios se procese y funcione correctamente. Tendrán que incluirse cuando se haga referencia a los Comentarios ampliados, así como al [biblioteca de cliente de comentarios extendidos](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Agregar comentarios personalizados a una página {#add-custom-comments-to-a-page}

Como solo puede haber un sistema de comentarios por página, es más sencillo crear una página de muestra como se describe en la breve [Crear una página de muestra](create-sample-page.md) tutorial.

Una vez creado, introduzca el modo Diseño y ponga a disposición el grupo de componentes Personalizado para permitir que el `Alt Comments` componente que se agregará a la página.

Para que el comentario aparezca y funcione correctamente, las bibliotecas de cliente para Comentarios deben agregarse a la lista clientlibslist de la página (consulte [Clientlibs para componentes de Communities](clientlibs.md)).

### Comentarios de Clientlibs en la página de muestra {#comments-clientlibs-on-sample-page}

![Comentarios de Clientlibs en la página de muestra](assets/chlimage_1-48.png)

### Autor: Comentario alternativo en la página de muestra {#author-alt-comment-on-sample-page}

![Comentario alternativo en la página de muestra](assets/chlimage_1-49.png)

### Autor: Nodo de comentarios de página de muestra {#author-sample-page-comments-node}

Puede verificar el resourceType en CRXDE viendo las propiedades del nodo de comentarios de la página de muestra en `/content/sites/sample/en/jcr:content/content/primary/comments`.

![imagen_1-50](assets/chlimage_1-50.png)

### Publicar página de muestra {#publish-sample-page}

Una vez agregado el componente personalizado a la página, también es necesario (re) [publicar la página](sites-console.md#publishing-the-site).

### Publicar: Comentario alternativo en la página de muestra {#publish-alt-comment-on-sample-page}

Después de publicar la aplicación personalizada y la página de muestra, debería ser posible introducir un comentario. Cuando haya iniciado sesión, ya sea con un [usuario de demostración](tutorials.md#demo-users) o administrador, debería ser posible publicar un comentario.

Aquí está aaron.mcdonald@mailinator.com publicando un comentario:

![imagen_1-51](assets/chlimage_1-51.png) ![imagen_1-52](assets/chlimage_1-52.png)

Ahora que parece que el componente extendido funciona correctamente con el aspecto predeterminado, es hora de modificar el aspecto.
