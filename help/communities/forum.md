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
* Configuración del componente `Forum`

## Añadir un foro a una página {#adding-a-forum-to-a-page}

Para agregar un componente `Forum` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Forum`

Y arrástrelo a su lugar en una página donde debería aparecer el foro.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se incluyen las [bibliotecas requeridas del lado del cliente](essentials-forum.md#essentials-for-client-side), así es como aparecerá el componente `Forum`:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuración de un foro {#configuring-a-forum}

Seleccione el componente `Forum` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]**, especifique la configuración de los temas y las respuestas:

* **[!UICONTROL Temas por]**
páginaDefine el número de temas/publicaciones que se muestran por página. El valor predeterminado es 10.

* ****
ModeradoSi se selecciona, la publicación de temas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* ****
CerradoSi se selecciona, el foro está cerrado a nuevos temas y comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Editor]**
de texto enriquecidoSi se selecciona, los temas y comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
etiquetadoSi está activado, permite que los miembros agreguen etiquetas a su anuncio (consulte  **[!UICONTROL Etiqueta]** campo ficha). El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi está activada, permita que los archivos adjuntos se agreguen al tema o comentario. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
lo siguienteSi está marcado, incluya la siguiente función para las publicaciones del foro, que permite que se  [](notifications.md) notifique a los miembros de las nuevas publicaciones. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
fijaciónSi se selecciona, los temas del foro pueden fijarse en la parte superior de la lista de temas. El valor predeterminado no está marcado.

* **[!UICONTROL Si se selecciona Permitir]**
contenido destacado, la idea se puede identificar como contenido [ ](featured.md)destacado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
suscripciones por correo electrónicoSi está activada, permita que se notifique a los miembros de las nuevas publicaciones por correo electrónico ([suscripción](subscriptions.md)). Requiere que `Allow Following` se compruebe y [se configure el correo electrónico](email.md). El valor predeterminado no está marcado.

* **[!UICONTROL Max File]**
SizeRelevant solo si 
`Allow File Uploads` está marcado. Este campo limitará el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de]**
archivo permitidosRelevante solo si 
`Allow File Uploads` está marcado. Lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Adjuntar máximo]**
tamaño de archivo de imagenRelevante solo si se ha marcado Permitir cargas de archivos. Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir]**
respuestas mediante subprocesosSi está activada, permita respuestas a los comentarios publicados en el tema. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y]**
temasSi se selecciona esta opción, permita que los miembros eliminen los comentarios y temas que han publicado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
votoSi está activada, incluya la función Votación con un tema. El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar rutas de]**
exploraciónSi está activada, muestre las rutas de navegación en las páginas de temas. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar]**
distintivosSi está activada, muestre  [](implementing-scoring.md) distintivos obtenidos y asignados con una entrada de blog de miembro. El valor predeterminado no está marcado.

>[!NOTE]
>
>Puede que sea necesario comprobar `AllowThreaded Replies` y `Allow users to Delete Comments and Topics` para habilitar los comentarios sobre un tema.

### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha **[!UICONTROL Moderación del usuario]**, especifique cómo se administran los temas publicados y las respuestas (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Denegar]**
anunciosSi se selecciona, se permitirá a los moderadores miembros de confianza denegar publicaciones e impedir que la publicación aparezca en el foro público. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar/volver a abrir]**
temasSi se selecciona, los moderadores de miembros de confianza pueden cerrar un tema para realizar más ediciones y comentarios, y también pueden volver a abrir un tema. El valor predeterminado no está marcado.

* **[!UICONTROL Mover]**
temasSi está activada, permita que los moderadores del lado de publicación muevan los temas. El valor predeterminado está marcado.

* **[!UICONTROL Marcar]**
anunciosSi está activada, permite a los miembros marcar los temas o comentarios de otros como inapropiados. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar]**
lista de motivosSi está activada, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan un tema o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Razón del]**
indicador personalizadoSi está activada, permita que los miembros introduzcan su propio motivo para marcar un tema o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral]**
de moderaciónIntroduzca el número de veces que los miembros deben marcar un tema o comentario antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Marcar]**
límiteEspecifique el número de veces que se debe marcar un tema o comentario antes de que se oculte en la vista pública. Si se establece en -1, el tema o comentario marcado nunca se oculta en la vista pública. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

### Ficha Campo de etiqueta {#tag-field-tab}

En la ficha **[!UICONTROL Campo de etiqueta]**, las etiquetas que se pueden aplicar, si se permiten en la ficha **[!UICONTROL Configuración]**, están limitadas según las Áreas de nombres elegidas.

* **[!UICONTROL Espacios]**
de nombres permitidosRelevante si  `Allow Tagging` se marca en la  **** ficha Configuración. Las etiquetas que se pueden aplicar están limitadas a las que se encuentran dentro de las categorías de Área de nombres seleccionadas. La lista de Áreas de nombres incluye &quot;Etiquetas estándar&quot; (la Área de nombres predeterminada) y &quot;Incluir todas las etiquetas&quot;. El valor predeterminado no está marcado, lo que significa que se permiten todas las Áreas de nombres.

* **[!UICONTROL Límite de]**
sugerenciasIntroduzca el número de etiquetas que se mostrarán como una sugerencia para el miembro que se publica en el foro. El valor predeterminado es 
**-** 1 (sin límites).

### Ficha Traducción {#translation-tab}

En la ficha **[!UICONTROL Traducción]**, si la traducción está habilitada para el sitio de la comunidad, la traducción puede configurarse para traducir el tema completo o los anuncios seleccionados.

* **[!UICONTROL Traducir]**
todoSi está marcado, el hilo del foro se traduce al idioma preferido del usuario. El valor predeterminado no está marcado.

### Ficha Ordenar configuración {#sort-settings-tab}

En la ficha **[!UICONTROL Ordenar configuración]**, especifique cómo se ordenan los comentarios publicados cuando se muestran.

* **[!UICONTROL Ordenar]**
porVerificar todas las selecciones de clasificación permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. El valor predeterminado es `Newest, Oldest, Last Updated`.

* **[!UICONTROL Configure]**
DefaultPull para seleccionar una de las opciones de ordenación seleccionadas para que aparezca como opción predeterminada. El valor predeterminado es 
`Newest`.

* **[!UICONTROL Seleccione Opciones de tiempo para la]**
clasificación de AnalyticsDesplegable para seleccionar uno de los 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. El valor predeterminado es `All`.

## Información adicional {#additional-information}

Puede encontrar más información en la página [Forum Essentials](essentials-forum.md) para desarrolladores.

Para obtener información sobre la moderación de los temas y comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar temas y comentarios publicados, consulte [Etiquetado de contenido generado por el usuario](tag-ugc.md).

Para obtener la traducción de los temas y comentarios publicados, consulte [Traducción de contenido generado por el usuario](translate-ugc.md).
