---
title: Crear nodos
seo-title: Create Nodes
description: Superponer el sistema de comentarios
seo-description: Overlay the comments system
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
exl-id: fc044a4e-0037-405f-8c26-b388c6a98733
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 12%

---

# Crear nodos {#create-nodes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Superponga el sistema de comentarios con una versión personalizada copiando el número mínimo de archivos necesarios de /libs en /apps y modificándolos en /apps.

>[!CAUTION]
>
>El contenido de la carpeta /libs nunca se edita porque cualquier reinstalación o actualización puede eliminar o reemplazar la carpeta /libs mientras el contenido de la carpeta /apps se deja intacto.

Uso [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) en una instancia de autor, comience por crear una ruta en la carpeta /apps que sea idéntica a la ruta a los componentes superpuestos en la carpeta /libs.

La ruta duplicada es

* `/libs/social/commons/components/hbs/comments/comment`

Algunos nodos de la ruta son carpetas y otros son componentes.

1. Vaya a [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Crear `/apps/social` (si aún no existe)
   * Select `/apps` node
   * **[!UICONTROL Crear > Carpeta ...]**
      * Introduzca el nombre: `social`
1. Select `social` node
   * **[!UICONTROL Crear > Carpeta...]**
      * Introduzca el nombre: `commons`
1. Select `commons` node
   * **[!UICONTROL Crear > Carpeta...]**
      * Introduzca el nombre: `components`
1. Select `components` node
   * **[!UICONTROL Crear > Carpeta...]**.
      * Introduzca el nombre: `hbs`
1. Select `hbs` node
   * **[!UICONTROL Crear > Crear componente...]**
      * Introducir etiqueta: `comments`
      * Escriba el título: `Comments`
      * Escriba la descripción: `List of comments without showing avatars`
      * Super Type: `social/commons/components/comments`
      * Introducir grupo: `Communities`
      * Haga clic en **[!UICONTROL Siguiente]** hasta **[!UICONTROL OK]**
1. Select `comments` node

   * **[!UICONTROL Crear > Crear componente...]**

      * Introducir etiqueta: `comment`
      * Escriba el título: `Comment`
      * Escriba la descripción: `A comment instance without avatars`
      * Super Type: `social/commons/components/comments/comment`
      * Introducir grupo: `.hidden`
      * Haga clic en **[!UICONTROL Siguiente]** hasta **[!UICONTROL OK]**
   * Select **[!UICONTROL Guardar todo]**
1. Eliminar el valor predeterminado `comments.jsp`
   * Seleccionar nodo `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Seleccione **[!UICONTROL Eliminar]**
1. Eliminar el comentario predeterminado.jsp
   * seleccionar nodo `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Seleccione **[!UICONTROL Eliminar]**
   * Select **[!UICONTROL Guardar todo]**

>[!NOTE]
>
>Para preservar la cadena de herencia, la variable `Super Type` (propiedad) `sling:resourceSuperType`) de los componentes de superposición se establecen con el mismo valor que la variable `Super Type` de los componentes que se van a superponer, en este caso
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`
>


El propio overlay `Type`(propiedad) `sling:resourceType`) debe ser una referencia automática relativa para que cualquier contenido que no se encuentre en /apps se busque en /libs.
* Nombre: `sling:resourceType`
* Tipo: `String`
* Valor: `social/commons/components/hbs/comments`

1. Seleccione el verde `[+] Add`
   * Nombre: `sling:resourceType`
   * Tipo: `String`
   * Valor: `social/commons/components/hbs/comments/comment`
1. Seleccione el verde `[+] Add`
   * Select **[!UICONTROL Guardar todo]**

![Chlimage_1-4](assets/chlimage_1-4.png)
