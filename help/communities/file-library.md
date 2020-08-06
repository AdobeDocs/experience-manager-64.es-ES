---
title: Función de la biblioteca de archivos
seo-title: Función de la biblioteca de archivos
description: La función Biblioteca de archivos permite que los visitantes del sitio iniciados en sesión carguen, gestionen y descarguen archivos
seo-description: La función Biblioteca de archivos permite que los visitantes del sitio iniciados en sesión carguen, gestionen y descarguen archivos
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---


# Función de la biblioteca de archivos {#file-library-feature}

## Introducción {#introduction}

La función de biblioteca de archivos proporciona un lugar para que los visitantes del sitio que han iniciado sesión (miembros de la comunidad) carguen, gestionen y descarguen archivos dentro del sitio de la comunidad.

Esta sección de la documentación describe

* Añadir la función de biblioteca de archivos en un sitio AEM
* Configuración del `File Library` componente

## Añadir una biblioteca de archivos en una página {#adding-a-file-library-to-a-page}

Para agregar un `File Library` componente a una página en modo de autor, ubique el componente

* `Communities / File Library`

y arrástrelo a su lugar en una página.

Para obtener la información necesaria, visite [Communities Components Basics](basics.md)(Conceptos básicos de componentes de comunidades).

Cuando se incluyen las bibliotecas [del lado del cliente](essentials-file-library.md#essentials-for-client-side) necesarias, así es como aparecerá el `File Library` componente:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configuración de la biblioteca de archivos {#configuring-file-library}

Seleccione el componente colocado al que desea acceder y seleccione el `File Library` `Configure` icono que abre el cuadro de diálogo de edición.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Ficha Comentarios {#comments-tab}

En la ficha **[!UICONTROL Comentarios]** , especifique si se mostrarán los comentarios de los archivos cargados y cómo se mostrarán:

* **[!UICONTROL Permitir comentarios en archivos]** Si está activada, permita comentarios en los archivos cargados. El valor predeterminado no está marcado.

* **[!UICONTROL Comentarios por página]** Limita el número de comentarios que se muestran por página, así como el número de respuestas que se muestran. El valor predeterminado es 
**10**.

* **[!UICONTROL Tamaño]** máximo del archivoEste valor limitará el tamaño del archivo cargado. El límite predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Longitud]** máxima del mensaje Número máximo de caracteres que se pueden introducir en el cuadro de texto. El valor predeterminado es de 4096 caracteres.

* **[!UICONTROL Tipos]** de archivo permitidos lista de extensiones de archivo separadas por coma con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirán los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Editor]** de texto enriquecido Si está marcado, los comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Eliminar comentarios]** Si se selecciona, los usuarios pueden eliminar sus propios comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir etiquetado]** Si se selecciona, se habilitará la capacidad de agregar una etiqueta al archivo. El valor predeterminado no está marcado.

* **[!UICONTROL Áreas de nombres]** permitidas Si se selecciona Permitir etiquetado, las etiquetas disponibles se limitarán a las Áreas de nombres seleccionadas. Si no se marca ninguna, se permite todo. El valor predeterminado es todas las Áreas de nombres.

* **[!UICONTROL Límite]** de sugerencias Si se selecciona Permitir etiquetado, esta configuración limita el número de etiquetas sugeridas para mostrar. Si se establece en -1, no hay límite. El valor predeterminado es -1.

* **[!UICONTROL Permitir voto]** Si se selecciona, se habilitará la capacidad de votar para un archivo. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir lo siguiente]** Si está activado, incluya la siguiente función para los artículos de blog, que permite que se [notifique](notifications.md) a los miembros de los nuevos anuncios. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir respuestas por subprocesos]** Si está activada, permita respuestas a los comentarios publicados. El valor predeterminado no está marcado.

### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha Moderación **** del usuario, configure la moderación de los comentarios si se permiten:

* **[!UICONTROL Premoderación]** Si está activada, los comentarios deben aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* **[!UICONTROL Eliminar comentarios]** Si se selecciona, el visitante que publicó el comentario puede eliminarlo. El valor predeterminado está marcado.

* **[!UICONTROL Denegar comentarios]** Si se selecciona, permita que los moderadores de miembros de confianza rechacen los comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar/volver a abrir Comentarios]** Si está activado, permita que los moderadores de miembros de confianza cierren y vuelvan a abrir los comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar comentarios]** Si está activada, permita que los visitantes marquen comentarios como inapropiados. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar Lista]** de motivo Si está activada, permita que los visitantes elijan, desde una lista desplegable, el motivo por el que marcan un comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Razón]** de marca personalizada Si está activada, permita que los visitantes introduzcan su propio motivo para marcar un comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral]** de moderaciónIntroduzca el número de veces que los visitantes deben marcar un comentario antes de que se notifique a los moderadores. El valor predeterminado es una vez (
**1**).

* **[!UICONTROL Límite]** de marcado Escriba el número de veces que se debe marcar un comentario antes de que se oculte en la vista pública. Este número debe ser bueno o igual que la variable 
**Umbral de moderación**. El valor predeterminado es 5.

## Información adicional {#additional-information}

Puede encontrar más información en la página [File Library Essentials](essentials-file-library.md) para desarrolladores.

Para obtener información sobre la moderación de los temas y comentarios publicados, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

Para etiquetar temas y comentarios publicados, consulte [Etiquetado de contenido](tag-ugc.md)generado por el usuario.
