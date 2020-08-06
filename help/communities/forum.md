---
title: Función de foro
seo-title: Función de foro
description: Cómo agregar y configurar la función de foro
seo-description: Cómo agregar y configurar la función de foro
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# Función de foro {#forum-feature}

## Introducción {#introduction}

La función de foro proporciona un área para los visitantes del sitio con sesión iniciada (miembros de la comunidad) en el entorno de publicación para:

* Crear nuevos temas
* Vista y respuesta a los temas
* Seguir un tema
* Buscar en un foro
* Ayudar a moderar el contenido del foro
* Mover temas de foro de una página a otra

Esta sección de la documentación describe

* Añadir la función de foro en un sitio AEM
* Configuración del `Forum`componente

## Adding a Forum to a Page {#adding-a-forum-to-a-page}

Para agregar un `Forum` componente a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Forum`

Y arrástrelo a su lugar en una página donde debería aparecer el foro.

Para obtener la información necesaria, visite [Communities Components Basics](basics.md)(Conceptos básicos de componentes de comunidades).

Cuando se incluyen las bibliotecas [del lado del cliente](essentials-forum.md#essentials-for-client-side) necesarias, así es como aparecerá el `Forum`componente:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuración de un foro {#configuring-a-forum}

Seleccione el componente colocado al que desea acceder y seleccione el `Forum` `Configure` icono que abre el cuadro de diálogo de edición.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]** , especifique la configuración de los temas y las respuestas:

* **[!UICONTROL Temas por página]** Define el número de temas/publicaciones que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]** Si se selecciona, la publicación de temas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrado]** Si está marcado, el foro está cerrado a nuevos temas y comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Editor]** de texto enriquecido Si está marcado, los temas y comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir etiquetado]** Si está activado, permita que los miembros agreguen etiquetas a su anuncio (consulte la ficha Campo **** de etiqueta). El valor predeterminado no está marcado.

* **[!UICONTROL Permitir cargas]** de archivos Si está activada, permita que los archivos adjuntos se agreguen al tema o comentario. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir lo siguiente]** Si está marcado, incluya la siguiente función para las publicaciones del foro, que permite que se [notifique](notifications.md) a los miembros de las nuevas publicaciones. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir fijación]** Si se selecciona, los temas del foro pueden fijarse en la parte superior de la lista de temas. El valor predeterminado no está marcado.

* **[!UICONTROL Si se selecciona Permitir contenido]** destacado, la idea se puede identificar como contenido [](featured.md)destacado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir Suscripciones]** por correo electrónico Si está activada, permita que se notifique a los miembros de los anuncios nuevos por correo electrónico ([suscripción](subscriptions.md)). Requiere `Allow Following` que se marque y se configure [el](email.md)correo electrónico. El valor predeterminado no está marcado.

* **[!UICONTROL Tamaño]** máximo de archivo relevante solo si 
`Allow File Uploads` está marcado. Este campo limitará el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos]** de archivo permitidos relevantes solo si 
`Allow File Uploads` está marcado. lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL El tamaño]** máximo del archivo de imagen adjunto solo es relevante si se ha marcado Permitir cargas de archivos. Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir respuestas]** por hilos Si está activada, permita respuestas a comentarios publicados en el tema. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y temas]** Si se selecciona esta opción, permita que los miembros eliminen los comentarios y temas que han publicado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir voto]** Si está activada, incluya la función de voto con un tema. El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar rutas de exploración]** Si está activada, muestre las rutas de navegación en las páginas de temas. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar distintivos]** Si está activada, muestre [distintivos](implementing-scoring.md) obtenidos y asignados con una entrada de blog de miembro. El valor predeterminado no está marcado.

>[!NOTE]
>
>Puede que sea necesario comprobar `AllowThreaded Replies` y `Allow users to Delete Comments and Topics` activar los comentarios sobre un tema.

### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha Moderación **[!UICONTROL del]** usuario, especifique cómo se administran los temas y las respuestas publicados (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

* **[!UICONTROL Denegar publicaciones]** Si se selecciona, los moderadores miembros de confianza podrán denegar las publicaciones e impedir que aparezcan en el foro público. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar o volver a abrir temas]** Si se selecciona, los moderadores de miembros de confianza pueden cerrar un tema para realizar más ediciones y comentarios, y también pueden volver a abrir un tema. El valor predeterminado no está marcado.

* **[!UICONTROL Mover temas]** Si está activado, permita que los moderadores del lado de publicación muevan los temas. El valor predeterminado está marcado.

* **[!UICONTROL Marcar anuncios]** Si está activada, permite a los miembros marcar los temas o comentarios de otros como inapropiados. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar Lista]** de motivo Si está activada, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan un tema o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Razón]** de marca personalizada Si está activada, permita que los miembros introduzcan su propio motivo para marcar un tema o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral]** de moderaciónIntroduzca el número de veces que los miembros deben marcar un tema o comentario antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite]** de marcado Escriba el número de veces que se debe marcar un tema o comentario antes de que se oculte en la vista pública. Si se establece en -1, el tema o comentario marcado nunca se oculta en la vista pública. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

### Ficha Campo de etiqueta {#tag-field-tab}

En la ficha Campo **** de etiqueta, las etiquetas que se pueden aplicar, si se permiten en la ficha **[!UICONTROL Configuración]** , están limitadas según las Áreas de nombres elegidas.

* **[!UICONTROL Áreas de nombres]** permitidas relevantes si `Allow Tagging` se marca en la ficha **[!UICONTROL Configuración]** . Las etiquetas que se pueden aplicar están limitadas a las que se encuentran dentro de las categorías de Área de nombres seleccionadas. La lista de Áreas de nombres incluye &quot;Etiquetas estándar&quot; (la Área de nombres predeterminada) y &quot;Incluir todas las etiquetas&quot;. El valor predeterminado no está marcado, lo que significa que se permiten todas las Áreas de nombres.

* **[!UICONTROL Límite]** de sugerencias Introduzca el número de etiquetas que se mostrarán como una sugerencia para el miembro que se publica en el foro. El valor predeterminado es 
**-** 1 (sin límites).

### Ficha Traducción {#translation-tab}

En la ficha **[!UICONTROL Traducción]** , si la traducción está habilitada para el sitio de la comunidad, la traducción se puede configurar para traducir el tema completo o los anuncios seleccionados.

* **[!UICONTROL Traducir todo]** si está marcado, el hilo del foro se traduce al idioma preferido del usuario. El valor predeterminado no está marcado.

### Ficha Ordenar configuración {#sort-settings-tab}

En la ficha **[!UICONTROL Ordenar configuración]** , especifique cómo se ordenan los comentarios publicados cuando se muestran.

* **[!UICONTROL Ordenar por]** Marcar todas las selecciones de clasificación permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. El valor predeterminado es `Newest, Oldest, Last Updated`.

* **[!UICONTROL Configure la opción Desplegable predeterminada]** para seleccionar una de las opciones de ordenación seleccionadas para que aparezca como opción predeterminada. El valor predeterminado es 
`Newest`.

* **[!UICONTROL Seleccione Opciones de tiempo para la]** extracción de ordenación de Analytics para seleccionar una de las opciones de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. El valor predeterminado es `All`.

## Información adicional {#additional-information}

Puede encontrar más información en la página [Forum Essentials](essentials-forum.md) para desarrolladores.

Para obtener información sobre la moderación de los temas y comentarios publicados, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

Para etiquetar temas y comentarios publicados, consulte [Etiquetado de contenido](tag-ugc.md)generado por el usuario.

Para ver la traducción de los temas y comentarios publicados, consulte [Traducción de contenido](translate-ugc.md)generado por el usuario.
