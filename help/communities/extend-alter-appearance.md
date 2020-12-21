---
title: Modificar el aspecto (HBS)
seo-title: Modificar el aspecto
description: Modificación de los scripts HBS
seo-description: Modificación de los scripts HBS
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Modificar el aspecto (HBS) {#alter-the-appearance-hbs}

Ahora que los componentes del sistema de comentarios personalizados del directorio de aplicaciones (/apps) están implementados, con un resourceSuperType que hace referencia al sistema de comentarios predeterminado y el modelo/Vista personalizado registrado, es posible modificar la implementación.

Para una demostración sencilla, se elimina una característica visual, el avatar que se muestra del usuario que ha iniciado sesión y que publica un comentario.

>[!NOTE]
>
>Para utilizar la extensión, la instancia del sistema de comentarios de un sitio web que se verá afectado (/content) debe establecer resourceType como el sistema de comentarios personalizado.

## Modificar los scripts de HBS {#modify-the-hbs-scripts}

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Abrir [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Comente la etiqueta que incluye el avatar de un anuncio de comentario (~ línea 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Abrir [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Comente la etiqueta que incluye el avatar de la siguiente entrada de comentario (~ línea 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Seleccione **Guardar todo**

## Replicar aplicación personalizada {#replicate-custom-app}

Una vez modificada la aplicación, es necesario volver a replicar el componente personalizado.

Una manera de hacerlo es

* Desde el menú principal

   * Seleccione **[!UICONTROL Herramientas > Operaciones > Replicación]**
   * Seleccione `Activate Tree`
   * Set `Start Path`: a `/apps/custom`
   * Desmarcar `Only Modified`
   * Botón Seleccionar `Activate`

## Comentario modificado de vista en la página de muestra publicada {#view-modified-comment-on-published-sample-page}

[Si continúa la ](extend-sample-page.md#publish-sample-page) experiencia en la instancia de publicación, que aún ha iniciado sesión como el mismo usuario, ahora es posible actualizar la página en el entorno de publicación para realizar la vista de la modificación para eliminar el avatar:

![chlimage_1-81](assets/chlimage_1-81.png)

## Paquete de extensión de comentarios de muestra {#sample-comment-extension-package}

Se adjunta un paquete de la aplicación de comentarios personalizados creada en este tutorial.

[Obtener archivo](assets/sample-comment-extension-6-1-fp3.zip)