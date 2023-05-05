---
title: Modificar el aspecto
seo-title: Alter the Appearance
description: Modificación de la secuencia de comandos
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Modificar el aspecto {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Modificación del script {#modify-the-script}

La secuencia de comandos comment.hbs es responsable de crear el HTML general para cada comentario.

Para no mostrar el avatar junto a cada comentario publicado:

1. Copiar `comment.hbs`from `libs`a `apps`
   1. Seleccionar `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Select **[!UICONTROL Copiar]**
   1. Seleccionar `/apps/social/commons/components/hbs/comments/comment`
   1. Select **[!UICONTROL Pegar]**
1. Abra la superposición `comment.hbs`
   * Haga doble clic en el nodo  `comment.hbs`en `/apps/social/commons/components/hbs/comments/comment folder`
1. Busque las siguientes líneas y elimínelas o coméntelas:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Elimine las líneas o las rodee con &quot;&lt;!>—&#39; y &#39;—>&#39; para comentarlos. Además, los caracteres &#39;xxx&#39; se están agregando como indicador visual de dónde se habría encontrado el avatar.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Duplicación de la superposición {#replicate-the-overlay}

Inserte el componente de comentarios superpuestos en la instancia de publicación mediante la herramienta de replicación.

>[!NOTE]
>
>Una forma más sólida de replicación sería crear un paquete en el Administrador de paquetes y [activar](../../help/sites-administering/package-manager.md#replicating-packages) es así. Se puede exportar y archivar un paquete.

En la navegación global, seleccione **[!UICONTROL Herramientas > Implementación > Replicación]** y luego **[!UICONTROL Activar árbol]**.

Para la Ruta de inicio, introduzca `/apps/social/commons` y seleccione **[!UICONTROL Activar]**.

![imagen_1-42](assets/chlimage_1-42.png)

## Ver resultados {#view-results}

Si inicia sesión en la instancia de publicación como administrador, por ejemplo, http://localhost:4503/crx/de como administrador/administrador, puede verificar que los componentes superpuestos estén allí.

Si cierra la sesión y vuelve a iniciarla como `aaron.mcdonald@mailinator.com/password` y actualice la página, observará que el comentario publicado ya no se muestra con un avatar, sino con un simple &quot;xxx&quot;.

![imagen_1-43](assets/chlimage_1-43.png)
