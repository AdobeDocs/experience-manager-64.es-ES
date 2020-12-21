---
title: Modificar el aspecto
seo-title: Modificar el aspecto
description: Modificación de la secuencia de comandos
seo-description: Modificación de la secuencia de comandos
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 1ae2d7f99286e0b958d343778159e2d35095510e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Modificar el aspecto {#alter-the-appearance}

## Modificar la secuencia de comandos {#modify-the-script}

La secuencia de comandos comment.hbs es responsable de crear el HTML general para cada comentario.

Para no mostrar el avatar al lado de cada comentario publicado:

1. Copiar `comment.hbs`de `libs`a `apps`
   1. Seleccione `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Seleccione **[!UICONTROL Copiar]**
   1. Seleccione `/apps/social/commons/components/hbs/comments/comment`
   1. Seleccione **[!UICONTROL Pegar]**
1. Abra el `comment.hbs` superpuesto
   * Haga clic en doble en el nodo `comment.hbs`en `/apps/social/commons/components/hbs/comments/comment folder`
1. Busque las líneas siguientes y elimínelas o coméntelas:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Elimine las líneas o rodearlas con &#39;&lt;!—&#39; y &#39;—>&#39; para comentarlos. Además, los caracteres &#39;xxx&#39; se están agregando como un indicador visual de dónde se habría encontrado el avatar.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Replicar la superposición {#replicate-the-overlay}

Inserte el componente de comentarios superpuestos en la instancia de publicación mediante la herramienta de replicación.

>[!NOTE]
>
>Una forma más sólida de replicación sería crear un paquete en el Administrador de paquetes y [activarlo](../../help/sites-administering/package-manager.md#replicating-packages). Se puede exportar y archivar un paquete.

En la navegación global, seleccione **[!UICONTROL Herramientas > Implementación > Replicación]** y luego **[!UICONTROL Activar árbol]**.

Para la ruta de Inicio, introduzca `/apps/social/commons` y seleccione **[!UICONTROL Activar]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Resultados de vista {#view-results}

Si inicia sesión en la instancia de publicación como administrador, por ejemplo: http://localhost:4503/crx/de como administrador/administrador, puede comprobar que los componentes superpuestos están allí.

Si cierra sesión y vuelve a iniciarla como `aaron.mcdonald@mailinator.com/password` y actualiza la página, observará que el comentario publicado ya no se muestra con un avatar, sino que se muestra un simple &#39;xxx&#39;.

![chlimage_1-43](assets/chlimage_1-43.png)

