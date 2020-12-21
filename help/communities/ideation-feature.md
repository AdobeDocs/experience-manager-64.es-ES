---
title: Función de la idea
seo-title: Función de la idea
description: Añadir y configurar la función Ideación
seo-description: Añadir y configurar la función Ideación
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# Característica de ideación {#ideation-feature}

## Introducción {#introduction}

La función de ideación proporciona un área para los visitantes del sitio con sesión iniciada (miembros de la comunidad) en el entorno de publicación para:

* Crear ideas para compartir con la comunidad
* Vista y comentarios sobre ideas
* Seguir una idea
* Votación de una idea

Esta sección de la documentación describe

* Añadir la función de ideación en un sitio AEM
* Configuración del componente Ideación

## Añadir una idea en una página {#adding-a-ideation-to-a-page}

Para agregar un componente `Ideation` a una página en modo de autor, utilice el navegador de componentes para ubicar `Communities / Ideation` y arrástrelo a su lugar en una página donde debería aparecer la idea.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se incluyen las [bibliotecas requeridas del lado del cliente](ideation.md#essentials-for-client-side), así es como aparecerá el componente `Ideation`:

![chlimage_1-21](assets/chlimage_1-29.png)

## Configuración de una idea {#configuring-an-ideation}

Seleccione el componente `Ideation` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]**, especifique la configuración de las ideas y los comentarios:

* **[!UICONTROL Título]**
de la ideaTítulo que se muestra para la idea. El valor predeterminado es 
`Ideation`.

* **[!UICONTROL Ideación]**
DescripciónDescripción que se muestra como un subtítulo de la idea. El valor predeterminado no es una descripción.

* **[!UICONTROL Temas por]**
páginaDefine el número de ideas/publicaciones que se muestran por página. El valor predeterminado es 10.

* ****
ModeradoSi se selecciona, la publicación de ideas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* ****
CerradoSi se selecciona, el foro de ideas está cerrado a nuevas ideas y comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Editor]**
de texto enriquecidoSi se selecciona, las ideas y los comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
etiquetadoSi está activado, permite que los miembros agreguen etiquetas a su anuncio (consulte  **[!UICONTROL Etiqueta]** campo ficha). El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi está activada, permita que los archivos adjuntos se agreguen a la idea o comentario. El valor predeterminado no está marcado.

* **[!UICONTROL Max File]**
SizeRelevant solo si 
`Allow File Uploads` está marcado. Este campo limitará el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de]**
archivo permitidosRelevante solo si 
`Allow File Uploads` está marcado. Lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Adjuntar máximo]**
tamaño de archivo de imagenRelevante solo si se ha marcado Permitir cargas de archivos. Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir]**
respuestasSi está activada, permite responder a los comentarios publicados en la idea. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y]**
temasSi se selecciona esta opción, permita que los miembros eliminen los comentarios e ideas que han publicado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
lo siguienteSi está activada, incluya la siguiente función para anuncios de ideas, que permite que se  [](notifications.md) notifique a los miembros de los anuncios nuevos. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
suscripciones por correo electrónicoSi está activada, permita que se notifique a los miembros de las nuevas publicaciones por correo electrónico ([suscripción](subscriptions.md)). Requiere que `Allow Following` se compruebe y [se configure el correo electrónico](email.md). El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
votoSi está marcado, permite votar los comentarios de una idea. El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar]**
distintivosSi está activada, muestre  [](implementing-scoring.md) distintivos obtenidos y asignados con la idea de un miembro. El valor predeterminado no está marcado.

* **[!UICONTROL Si se selecciona Permitir]**
contenido destacado, la idea se puede identificar como contenido [ ](featured.md)destacado. El valor predeterminado no está marcado.

### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha **[!UICONTROL Moderación del usuario]**, especifique cómo se administran las ideas y los comentarios publicados (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Denegar]**
anunciosSi se selecciona, se permitirá a los moderadores miembros de confianza denegar publicaciones e impedir que la publicación aparezca en el foro público. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar/volver a abrir]**
temasSi se selecciona, los moderadores de miembros de confianza pueden cerrar un tema para realizar más ediciones y comentarios, y también pueden volver a abrir un tema. El valor predeterminado no está marcado.

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
de nombres permitidosRelevante si 
`Allow Tagging` se verifica bajo la  **** ficha Settingstab. Las etiquetas que se pueden aplicar están limitadas a las que se encuentran dentro de las categorías de Área de nombres seleccionadas. La lista de Áreas de nombres incluye &quot;Etiquetas estándar&quot; (la Área de nombres predeterminada) y &quot;Incluir todas las etiquetas&quot;. El valor predeterminado no está marcado, lo que significa que se permiten todas las Áreas de nombres.

* **[!UICONTROL Límite de]**
sugerenciasIntroduzca el número de etiquetas que se mostrarán como una sugerencia para el miembro que se publica en el foro. Un valor de 
**-** 1 significa que no hay límite. El valor predeterminado es 0.

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

## Experiencia de Visitante del sitio {#site-visitor-experience}

### Creación de ideas {#creating-idea}

Al igual que con todas las características de las Comunidades, si no se ha iniciado sesión, un visitante del sitio solo puede leer ideas y vista otras opiniones (a través de comentarios y votaciones/preferencias).

Una vez que haya iniciado sesión, un miembro puede crear una nueva idea.

![chlimage_1-32](assets/chlimage_1-32.png)

Antes de enviar la idea, es posible que el miembro guarde un borrador.

Al seleccionar el botón `Save as Draft`, se guarda un borrador.

![chlimage_1-33](assets/chlimage_1-33.png)

Cuando visualice borradores guardados en la ficha `My Drafts`, seleccione `Read More` para volver a entrar en el modo de edición:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Proporcionar comentarios {#providing-feedback}

Una vez publicada la idea, otros miembros pueden iniciar sesión, abrir la idea ( `Read More`) y darle gusto, agregando así al recuento de votos, y hacer comentarios.

![chlimage_1-35](assets/chlimage_1-35.png)

### Información adicional {#additional-information}

Puede encontrar más información en la página [Ideation Essentials](ideation.md) para desarrolladores.

Para obtener información sobre la moderación de los temas y comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar temas y comentarios publicados, consulte [Etiquetado de contenido generado por el usuario](tag-ugc.md).
