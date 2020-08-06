---
title: Función de foro de preguntas y respuestas
seo-title: Función de foro de preguntas y respuestas
description: Añadir la función de foro QnA en una página
seo-description: Añadir la función de foro QnA en una página
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Función de foro de preguntas y respuestas {#q-a-forum-feature}

## Introducción {#introduction}

La función de foro QnA (preguntas y respuestas) proporciona un área para que los miembros de la comunidad hagan y respondan preguntas:

* Crear nuevas preguntas
* Imágenes en línea (con compatibilidad para arrastrar y soltar)
* Vista y respuesta a preguntas
* Buscar una pregunta
* Ayudar a moderar el contenido de QnA
* Identifique las mejores respuestas
* Mover las preguntas de control de calidad de una página a otra

Esta sección de la documentación describe

* Añadir la función de foro QnA en un sitio AEM
* Configuración del `QnA`componente

## Añadir un foro de preguntas y respuestas a una página {#adding-a-q-a-forum-to-a-page}

Para agregar un `QnA` componente a una página en modo de autor, utilice el navegador de componentes para ubicarlo `Communities / QnA` y arrastrarlo hasta su lugar en una página en la que debería aparecer el foro de control de calidad.

Para obtener la información necesaria, visite [Communities Components Basics](basics.md)(Conceptos básicos de componentes de comunidades).

Cuando se incluyen las bibliotecas [del lado del cliente](qna-essentials.md#essentials-for-client-side) necesarias, así es como aparecerá el `QnA` componente:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuración de QnA {#configuring-qna}

Seleccione el componente colocado al que desea acceder y seleccione el `QnA` `Configure` icono que abre el cuadro de diálogo de edición.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]** , especifique la configuración de los temas (preguntas) y las respuestas (respuestas):

* **[!UICONTROL Temas por página]** Define el número de preguntas y publicaciones que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]** Si se selecciona, la publicación de temas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrado]** Si está marcado, el foro está cerrado a nuevas preguntas y comentarios. El valor predeterminado no está marcado.

* **[!UICONTROL Editor]** de texto enriquecido Si está marcado, los temas y comentarios se pueden introducir con marcado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir etiquetado]** Si está activado, permita que los miembros agreguen etiquetas a su anuncio (consulte la ficha Campo **** de etiqueta). El valor predeterminado no está marcado.

* **[!UICONTROL Permitir cargas]** de archivos Si está activada, permita que los archivos adjuntos se agreguen a la pregunta o comentario. El valor predeterminado no está marcado.

* **[!UICONTROL Tamaño]** máximo de archivo relevante solo si 
`Allow File Uploads` está marcado. Este campo limitará el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos]** de archivo permitidos relevantes solo si 
`Allow File Uploads` está marcado. lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL El tamaño]** máximo del archivo de imagen adjunto solo es relevante si se ha marcado Permitir cargas de archivos. Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir lo siguiente]** Si está marcado, incluya la siguiente función para las publicaciones del foro, que permite que se [notifique](notifications.md) a los miembros de las nuevas publicaciones. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir fijación]** Si se selecciona, los temas del foro pueden fijarse en la parte superior de la lista de temas. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir Suscripciones]** por correo electrónico Si está activada, permita que se notifique a los miembros de los anuncios nuevos por correo electrónico ([suscripción](subscriptions.md)). Requiere `Allow Following` que se marque y se configure [el](email.md)correo electrónico. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir respuestas]** Si está activada, permita respuestas a los comentarios publicados en la pregunta. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y temas]** Si se selecciona esta opción, permita que los miembros eliminen los comentarios y las preguntas que han publicado. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir voto]** Si está activada, incluya la función de voto con una pregunta. El valor predeterminado no está marcado.

* **[!UICONTROL Mover la respuesta seleccionada al principio]** Si está activada, la primera respuesta que se muestra es una respuesta seleccionada. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar distintivos]** Si está activada, muestre [distintivos](implementing-scoring.md) obtenidos y asignados con una entrada de blog de miembro. El valor predeterminado no está marcado.

* **[!UICONTROL Si se selecciona Permitir contenido]** destacado, la idea se puede identificar como contenido [](featured.md)destacado. El valor predeterminado no está marcado.

#### Ficha Moderación del usuario {#user-moderation-tab}

En la ficha Moderación **[!UICONTROL del]** usuario, especifique cómo se administran los temas publicados (preguntas) y las respuestas (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

* **[!UICONTROL Denegar respuestas]** Si se selecciona, los moderadores de miembros de confianza podrán denegar las respuestas publicadas y evitar que la respuesta aparezca en el foro público de preguntas y respuestas. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrar o volver a abrir temas]** Si se selecciona, los moderadores de miembros de confianza pueden cerrar una pregunta (tema) para ediciones y respuestas posteriores, y también pueden volver a abrir una pregunta. El valor predeterminado no está marcado.

* **[!UICONTROL Mover temas]** Si está activado, permita que los moderadores del lado de publicación muevan las preguntas. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar anuncios]** Si está activada, permita que los miembros marquen las preguntas o respuestas de otros como inapropiadas. El valor predeterminado no está marcado.

* **[!UICONTROL Marcar Lista]** de motivo Si está activada, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan una pregunta o respuesta como inadecuada. El valor predeterminado no está marcado.

* **[!UICONTROL Razón]** de marca personalizada Si está activada, permita que los miembros introduzcan su propio motivo para marcar una pregunta o respuesta como inadecuada. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral]** de moderaciónIntroduzca el número de veces que los miembros deben marcar una pregunta o respuesta antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite]** de marcado Escriba el número de veces que se debe marcar una pregunta o respuesta antes de que se oculte en la vista pública. Si se establece en -1, la pregunta o respuesta marcada nunca se oculta en la vista pública. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

#### Ficha Campo de etiqueta {#tag-field-tab}

En la ficha Campo **** de etiqueta, las etiquetas que se pueden aplicar, si se permiten en la ficha **[!UICONTROL Configuración]** , están limitadas según las Áreas de nombres elegidas.

* **[!UICONTROL Áreas de nombres]** Pertinentes Permitidas si 
`Allow Tagging` se marca en la ficha **Configuración** . Las etiquetas que se pueden aplicar están limitadas a las que se encuentran dentro de las categorías de Área de nombres seleccionadas. La lista de Áreas de nombres incluye &quot;Etiquetas estándar&quot; (la Área de nombres predeterminada) y &quot;Incluir todas las etiquetas&quot;. El valor predeterminado no está marcado, lo que significa que se permiten todas las Áreas de nombres.

* **[!UICONTROL Límite]** de sugerencias Introduzca el número de etiquetas que se mostrarán como una sugerencia para el miembro que se publica en el foro. Un valor de 
`-1` significa que no hay límites. El valor predeterminado es 0.

#### Ficha Ordenar configuración {#sort-settings-tab}

En la ficha **[!UICONTROL Ordenar configuración]** , especifique cómo se ordenan los comentarios publicados cuando se muestran.

* **[!UICONTROL Ordenar por]** Marcar todas las selecciones de clasificación permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. El valor predeterminado es `Newest, Oldest, Last Updated`.

* **[!UICONTROL Configure la opción Desplegable predeterminada]** para seleccionar una de las opciones de ordenación seleccionadas para que aparezca como opción predeterminada. El valor predeterminado es 
`Newest`.

* **[!UICONTROL Seleccione Opciones de tiempo para la]** extracción de ordenación de Analytics para seleccionar una de las opciones de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. El valor predeterminado es `All`.

## Experiencia de Visitante del sitio {#site-visitor-experience}

### Identificación de respuestas {#identifying-answers}

Una respuesta se puede marcar como una respuesta correcta o útil mediante el `Select Answer` botón. Una vez que una pregunta se marca como respondida, no se puede seleccionar otra respuesta hasta que se anule la selección de la primera mediante el `Unmark Chosen Answer`botón.

Una vez seleccionada como respuesta viable, puede que no se seleccione con el `Unmark Chosen Answer` botón.

Una vez seleccionada una respuesta como respuesta viable, `Answered`se muestra una indicación de que la pregunta se ha mostrado junto al tema de la pregunta en la página principal de control de calidad.

### Moderadores y administradores {#moderators-and-administrators}

Cuando el usuario que ha iniciado sesión tiene privilegios de moderador o administrador, puede realizar las tareas de moderación permitidas por la configuración del componente, independientemente de quién haya creado la pregunta o la respuesta.

También tienen la capacidad de identificar respuestas.

### Miembros {#members}

Cuando se inicia sesión en el visitante del sitio, según la configuración, es posible que

* Publicar una nueva pregunta
* Editar o eliminar preguntas creadas por ellos
* También puede marcar las preguntas o respuestas de otros
* Puede identificar las respuestas a las preguntas creadas

### Anónimo {#anonymous}

Los visitantes del sitio que no hayan iniciado sesión sólo podrán leer las preguntas y respuestas publicadas, traducirlas si son compatibles, pero no podrán agregar preguntas ni respuestas, ni marcar las publicaciones de otros.

## Información adicional {#additional-information}

Puede encontrar más información en la página de [QnA Essentials](qna-essentials.md) para desarrolladores.

Para obtener información sobre la moderación de los temas y comentarios publicados, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

Para etiquetar temas y comentarios publicados, consulte [Etiquetado de contenido](tag-ugc.md)generado por el usuario.
