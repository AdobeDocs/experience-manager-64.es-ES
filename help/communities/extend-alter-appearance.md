---
title: Modificar el aspecto (HBS)
seo-title: Alter the Appearance
description: Modificación de los scripts HBS
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 3%

---

# Modificar el aspecto (HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Ahora que los componentes del sistema de comentarios personalizados del directorio de aplicaciones (/apps) están implementados, con un resourceSuperType que hace referencia al sistema de comentarios predeterminado y el Model/View personalizado registrado, es posible modificar la implementación.

Para una demostración sencilla, se elimina una característica visual, el avatar mostrado por el usuario que ha iniciado sesión y que publica un comentario.

>[!NOTE]
>
>Para utilizar la extensión de , la instancia del sistema de comentarios de un sitio web que se vea afectado (/content) debe establecer su resourceType en el sistema de comentarios personalizado.

## Modificación de los scripts HBS {#modify-the-hbs-scripts}

Uso [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Apertura [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Comente la etiqueta que incluye el avatar para una publicación de comentario (~ línea 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Apertura [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Comente la etiqueta que incluye el avatar para la siguiente entrada de comentario (~ línea 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Select **Guardar todo**

## Replicar aplicación personalizada {#replicate-custom-app}

Una vez modificada la aplicación, es necesario volver a replicar el componente personalizado.

Una forma de hacerlo es

* Desde el menú principal

   * Select **[!UICONTROL Herramientas > Operaciones > Replicación]**
   * Seleccionar `Activate Tree`
   * Establezca `Start Path`: a `/apps/custom`
   * Desmarcar `Only Modified`
   * Select `Activate` botón

## Ver comentario modificado en la página de muestra publicada {#view-modified-comment-on-published-sample-page}

[Continuación de la experiencia](extend-sample-page.md#publish-sample-page) en la instancia de publicación, que aún ha iniciado sesión como el mismo usuario, ahora es posible actualizar la página en el entorno de publicación para ver la modificación para eliminar el avatar:

![chlimage_1-81](assets/chlimage_1-81.png)

## Paquete de extensión de comentario de ejemplo {#sample-comment-extension-package}

Se adjunta un paquete de la aplicación de comentarios personalizados creada en este tutorial.

[Obtener archivo](assets/sample-comment-extension-6-1-fp3.zip)
