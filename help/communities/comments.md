---
title: Uso de comentarios
seo-title: Uso de comentarios
description: La función Comentarios permite a los visitantes del sitio que inician sesión compartir sus opiniones y conocimientos
seo-description: La función Comentarios permite a los visitantes del sitio que inician sesión compartir sus opiniones y conocimientos
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 6%

---


# Uso de comentarios {#using-comments}

## Introducción {#introduction}

La función de comentarios se utiliza para permitir que los visitantes del sitio (miembros) que inicien sesión compartan sus opiniones y conocimientos sobre el contenido del sitio. Esta función suele estar presente en otras funciones, pero puede agregarse a cualquier sitio web.

Esta sección de la documentación describe

* Añadir `Comments`en una página
* Configuración del componente `Comments`

>[!NOTE]
>
>No se admite la publicación anónima de un comentario. Los visitantes del sitio deben registrarse (convertirse en miembros) e iniciar sesión para participar.

## Añadir comentarios a una página {#adding-comments-to-a-page}

Para agregar un componente `Comments`a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Comments`

y arrástrelo a su lugar en una página, como una posición relativa a la función en la que los usuarios pueden comentar o simplemente en la parte inferior de la página.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se incluyen las [bibliotecas requeridas del lado del cliente](essentials-comments.md#essentials-for-client-side), así es como aparecerá el componente `Comments`.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Sólo puede existir un componente `Comments`en una página. Tenga en cuenta que varias funciones de Comunidades ya incluyen comentarios, como un blog, calendario, foro, control de calidad y reseñas.

## Configuración de comentarios {#configuring-comments}

Seleccione el componente `Comments` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![](assets/configure.png) ![configurecommentssettings](assets/commentssettings.png)

### Ficha Comentarios {#comments-tab}

En la ficha **[!UICONTROL Comentarios]**, especifique cómo los visitantes introducen los comentarios.

* **[!UICONTROL Permitir respuestas]**

   Si se selecciona, permite que los miembros respondan a los comentarios existentes. El valor predeterminado no está marcado.

* **[!UICONTROL Comentarios por página]**

   Limita el número de comentarios mostrados por página, así como el número de respuestas mostradas. El valor predeterminado es 10.

* **[!UICONTROL Permitir cargas de archivos]**

   Si se selecciona, la opción para cargar un archivo se mostrará con el cuadro de entrada de texto. El valor predeterminado no está marcado.

* **[!UICONTROL Tamaño máximo de archivo]**

   Solo es relevante si está activada la opción Permitir cargas de archivos. Este valor limitará el tamaño del archivo cargado. El límite predeterminado es 10 MB.

* **[!UICONTROL Longitud máxima del mensaje]**

   Número máximo de caracteres que se pueden introducir en el cuadro de texto. El valor predeterminado es de 4096 caracteres.

* **[!UICONTROL Tipos de archivo permitidos]**

   Solo es relevante si está activada la opción Permitir cargas de archivos. Lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirán los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Editor de texto enriquecido]**

   Si se selecciona, los comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Habilitar la votación]**

   Si se selecciona, la opción de votar hacia arriba o hacia abajo se mostrará con el cuadro de entrada de texto. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir seguimiento]**

   Si está activada, permita que los miembros sigan los comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar insignias]**

   Si se selecciona, permita que se muestren las insignias ganadas y concedidas. El valor predeterminado no está marcado.

### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha **[!UICONTROL Moderación del usuario]**, especifique cómo se administran los comentarios publicados. Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Moderación previa]**

   Si se selecciona, los comentarios deben aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* **[!UICONTROL Eliminar comentarios]**

   Si se selecciona, se proporciona al miembro que publicó el comentario la capacidad de eliminarlo. El valor predeterminado no está marcado.

* **[!UICONTROL Denegar comentarios]**

   Si se selecciona, permita que los moderadores rechacen los comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar/abrir de nuevo los comentarios]**

   Si se selecciona, permita que los moderadores cierren y vuelvan a abrir los comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar comentarios]**

   Si se selecciona, permita que los miembros marquen los comentarios como inapropiados. El valor predeterminado no está marcado.

* **[!UICONTROL Lista de motivos de indicación]**

   Si se selecciona, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan un comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Motivo de indicación personalizado]**

   Si se selecciona, permita que los miembros especifiquen su propio motivo para marcar un comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral de moderación]**

   Escriba el número de veces que los miembros deben marcar un comentario antes de que se notifique a los moderadores. El valor predeterminado es una vez (1).

* **[!UICONTROL Límite de indicación]**

   Escriba el número de veces que se debe marcar un comentario antes de que se oculte de la vista pública. Este número debe ser bueno o igual al **[!UICONTROL Umbral de moderación]**. El valor predeterminado es 5.

### Ficha Ordenar configuración {#sort-settings-tab}

En la ficha **[!UICONTROL Ordenar configuración]**, especifique cómo se ordenan los comentarios publicados cuando se muestran.

* **[!UICONTROL Campo de ordenación]**

   Despliegue para seleccionar uno de `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed` o `Most Liked`.

* **[!UICONTROL Orden]**

   Despliegue para seleccionar uno de `Ascending` o `Descending`.

### Cambiar a un tipo de comentario personalizado {#changing-to-a-custom-comment-type}

Al cambiar el tipo de recurso de comentarios, el sistema de comentarios ya no generará una instancia de un comentario usando el valor predeterminado, sino una instancia personalizada (ampliada) por los desarrolladores.

Una vez conocidos los tipos de recursos personalizados, introduzca [Modo de diseño](../../help/sites-authoring/default-components-designmode.md) y haga clic en el doble del componente `Comments` colocado para abrir un cuadro de diálogo con una ficha adicional.

En la ficha **[!UICONTROL Tipos de recursos]**, especifique el resourceType personalizado para nuevas instancias de los componentes `Comments or Voting`:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Tipo de medio de comentario]**

   Vaya al resourceType de un componente `comment`extendido (comentario único) en /apps. Por ejemplo, `/apps/social/commons/components/hbs/comments/comment`

   Este recurso identificará el resourceType del UGC creado cuando un visitante publica un comentario.

* **[!UICONTROL Tipo de medio de votación]**

   Vaya al resourceType de un componente `voting`extendido en /apps. Por ejemplo, `/apps/social/components/hbs/voting`

   Este recurso identificará el tipo de recurso del UGC creado cuando un visitante publique una votación.

* **[!UICONTROL Tipo de recurso del sistema de comentarios]**

   Vaya al resourceType de un componente `comments`extendido (sistema de comentarios) en /apps. Deje en blanco a menos que la plantilla de página [incluya dinámicamente](scf.md#add-or-include-a-communities-component) el sistema de comentarios en la secuencia de comandos subyacente en lugar de agregarla a la página como un recurso (nodo de comentarios). Obtenga más información leyendo sobre el asistente [{{include}}](handlebars-helpers.md#include).

## Experiencia de Visitante del sitio {#site-visitor-experience}

### Moderadores y administradores {#moderators-and-administrators}

Cuando el usuario que ha iniciado sesión tiene privilegios de moderador o administrador, puede realizar las tareas de moderación permitidas por la configuración del componente, independientemente de quién haya creado el comentario.

### Miembros {#members}

Cuando se inicia sesión en el visitante del sitio, según la configuración, es posible que

* Publicar un nuevo comentario
* Editar su propio comentario
* Eliminar sus propios comentarios
* Marcar comentarios de otros

### Anónimo {#anonymous}

Los visitantes del sitio que no hayan iniciado sesión solo podrán leer los comentarios publicados, traducirlos si son compatibles, pero no podrán agregar comentarios ni marcar los comentarios de otros.

## Información adicional {#additional-information}

Puede encontrar más información en la página [Comments Essentials](essentials-comments.md) para desarrolladores.

Para obtener información sobre la moderación de los comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para ver la traducción de los comentarios publicados, consulte [Traducción de contenido generado por el usuario](translate-ugc.md).
