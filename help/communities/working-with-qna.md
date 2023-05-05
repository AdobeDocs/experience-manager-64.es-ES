---
title: Función de foro de preguntas y respuestas
seo-title: Q&A Forum Feature
description: Adición de la función de foro QnA a una página
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 1%

---

# Función de foro de preguntas y respuestas {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La función de foro QnA (preguntas y respuestas) proporciona un área para que los miembros de la comunidad hagan y respondan preguntas:

* Crear nuevas preguntas
* Imágenes en línea (con compatibilidad para arrastrar y soltar)
* Ver y responder preguntas
* Buscar una pregunta
* Ayudar a moderar el contenido de control de calidad
* Identificar las mejores respuestas
* Mover preguntas de control de calidad de una página a otra

Esta sección de la documentación describe

* Adición de la función de foro QnA a un sitio AEM
* Ajustes de configuración para `QnA`componente

## Adición de un foro de preguntas y respuestas a una página {#adding-a-q-a-forum-to-a-page}

Para agregar un `QnA` a una página en modo de autor, utilice el navegador de componentes para localizar `Communities / QnA` y arrástrela a su lugar en una página donde debería aparecer el foro QnA.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](qna-essentials.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `QnA` aparecerá el componente:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuración de QnA {#configuring-qna}

Seleccione la colocación `QnA` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Ficha Configuración {#settings-tab}

En el **[!UICONTROL Configuración]** , especifique la configuración para los temas (preguntas) y las respuestas (respuestas):

* **[!UICONTROL Temas por página]**
Define el número de preguntas/anuncios que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]**
Si se selecciona, la publicación de temas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrado]**
Si se selecciona, el foro se cierra a nuevas preguntas y comentarios. El valor predeterminado no está seleccionado.

* **[!UICONTROL Editor de texto enriquecido]**
Si se selecciona, los temas y comentarios se pueden introducir con marcado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir etiquetado]**
Si está activada, permita que los miembros agreguen etiquetas a su publicación (consulte **[!UICONTROL Campo de etiqueta]** ). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir cargas de archivos]**
Si está activada, permita que los archivos adjuntos se agreguen a la pregunta o comentario. El valor predeterminado no está seleccionado.

* **[!UICONTROL Tamaño máximo del archivo]**
Solo relevante si 
`Allow File Uploads` está activada. Este campo limita el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de archivo permitidos]**
Solo relevante si 
`Allow File Uploads` está activada. Lista de extensiones de archivo separados por coma con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar aquellos que no se especifiquen. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Adjuntar tamaño máximo de archivo de imagen]**
Solo es relevante si está marcada la opción Permitir cargas de archivos . Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir lo siguiente]**
Si está marcada esta opción, incluya la siguiente función para las publicaciones en el foro, que permite que los miembros se [notificadas](notifications.md) de nuevos puestos. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir anclaje]**
Si se selecciona, los temas del foro pueden colocarse en la parte superior de la lista de temas. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir suscripciones de correo electrónico]**
Si está activada, permita que se notifique a los miembros de los anuncios nuevos por correo electrónico ([suscripción](subscriptions.md)). Requiere `Allow Following` que se comprobarán y [correo electrónico configurado](email.md). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir respuestas]**
Si está activada, permita que se respondan a los comentarios publicados en la pregunta. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y temas]**
Si está activada, permita que los miembros eliminen los comentarios y preguntas que hayan publicado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir votación]**
Si está marcada esta opción, incluya la función Votación con una pregunta. El valor predeterminado no está seleccionado.

* **[!UICONTROL Mover La Respuesta Seleccionada A La Parte Superior]**
Si se selecciona, la primera respuesta que se muestra es una respuesta seleccionada. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar distintivos]**
Si está activada, muestre ganado y asignado [distintivos](implementing-scoring.md) con la entrada de blog de un miembro. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir contenido destacado]**
si se selecciona, la idea puede identificarse como [contenido destacado](featured.md). El valor predeterminado no está seleccionado.

#### Pestaña Moderación del usuario {#user-moderation-tab}

En el **[!UICONTROL Moderación del usuario]** especifique cómo se administran los temas publicados (preguntas) y las respuestas (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Denegar respuestas]**
Si se selecciona, los moderadores miembros de confianza podrán denegar las respuestas publicadas e impedir que la respuesta aparezca en el foro público de preguntas y respuestas. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrar/volver a abrir temas]**
Si se selecciona, los moderadores miembros de confianza pueden cerrar una pregunta (tema) para ediciones y respuestas adicionales, y también pueden volver a abrir una pregunta. El valor predeterminado no está seleccionado.

* **[!UICONTROL Mover temas]**
Si está marcada esta opción, permita que los moderadores del lado de publicación movieran las preguntas. El valor predeterminado no está seleccionado.

* **[!UICONTROL Marcar anuncios]**
Si se selecciona, permita a los miembros marcar las preguntas o respuestas de otros como inapropiadas. El valor predeterminado no está seleccionado.

* **[!UICONTROL Lista de motivos del indicador]**
Si está activada, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan una pregunta o respuesta como inadecuada. El valor predeterminado no está seleccionado.

* **[!UICONTROL Razón de marca personalizada]**
Si se selecciona, permita a los miembros introducir sus propios motivos para marcar una pregunta o respuesta como inapropiada. El valor predeterminado no está seleccionado.

* **[!UICONTROL Umbral de moderación]**
Introduzca el número de veces que los miembros deben marcar una pregunta o respuesta antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite de marcado]**
Introduzca el número de veces que se debe marcar una pregunta o respuesta antes de ocultarla de la vista pública. Si se establece en -1, la pregunta o respuesta marcada nunca se oculta a la vista del público. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

#### Ficha Campo de etiqueta {#tag-field-tab}

En el **[!UICONTROL Campo de etiqueta]** , las etiquetas que se pueden aplicar, si se permiten en la sección **[!UICONTROL Configuración]** , se limitan según los espacios de nombres seleccionados.

* **[!UICONTROL Espacios de nombres permitidos]**
Pertinente si 
`Allow Tagging` se marca en la sección **Configuración** pestaña . Las etiquetas que se pueden aplicar se limitan a las que están dentro de las categorías de espacio de nombres seleccionadas. La lista de áreas de nombres incluye &quot;Etiquetas estándar&quot; (el espacio de nombres predeterminado) así como &quot;Incluir todas las etiquetas&quot;. El valor predeterminado es ninguno activado, lo que significa que se permiten todas las áreas de nombres.

* **[!UICONTROL Límite de sugerencias]**
Introduzca el número de etiquetas que se mostrarán como una sugerencia para el usuario que publica en el foro. Un valor de 
`-1` significa que no hay límites. El valor predeterminado es 0.

#### Ficha Ordenar configuración {#sort-settings-tab}

En el **[!UICONTROL Configuración de ordenación]** , especifique cómo se ordenan los comentarios publicados cuando se muestran.

* **[!UICONTROL Ordenar por]**
Compruebe todas las selecciones de ordenación permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. El valor predeterminado es `Newest, Oldest, Last Updated`.

* **[!UICONTROL Establecer como predeterminado]**
Despliegue para seleccionar una de las opciones de ordenación seleccionadas que aparecerán como predeterminadas. El valor predeterminado es 
`Newest`.

* **[!UICONTROL Seleccionar opciones de tiempo para la clasificación de Analytics]**
Desplegable para seleccionar uno de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. El valor predeterminado es `All`.

## Experiencia del visitante del sitio {#site-visitor-experience}

### Identificación de respuestas {#identifying-answers}

Una respuesta puede marcarse como una respuesta correcta o útil utilizando la variable `Select Answer` botón. Una vez que una pregunta está marcada como Respondida, no se puede seleccionar otra respuesta hasta que no se haya seleccionado la primera mediante la función `Unmark Chosen Answer`botón.

Una vez seleccionada como respuesta viable, puede que no esté seleccionada con la función `Unmark Chosen Answer` botón.

Una vez seleccionada la respuesta como respuesta viable, una indicación de que la pregunta se ha `Answered`se muestra junto al tema de la pregunta en la página de control de calidad principal.

### Moderadores y administradores {#moderators-and-administrators}

Cuando el usuario que ha iniciado sesión tiene privilegios de moderador o administrador, puede realizar las tareas de moderación permitidas por la configuración del componente, independientemente de quién haya creado la pregunta o la respuesta.

También tienen la capacidad de identificar respuestas.

### Miembros {#members}

Cuando el visitante del sitio ha iniciado sesión, según la configuración, es posible que

* Publicar una nueva pregunta
* Editar o eliminar preguntas creadas por ellos
* También puede marcar las preguntas o respuestas de otros
* Puede identificar respuestas para preguntas creadas por ellos

### Anónimo {#anonymous}

Los visitantes del sitio que no hayan iniciado sesión solo podrán leer las preguntas y respuestas publicadas, traducirlas si son compatibles, pero no podrán agregar preguntas ni respuestas, ni marcar las publicaciones de otros.

## Información adicional {#additional-information}

Puede encontrar más información en la [Aspectos básicos de la garantía de calidad](qna-essentials.md) para desarrolladores.

Para moderar los temas y comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar temas y comentarios publicados, consulte [Etiquetado del contenido generado por el usuario](tag-ugc.md).
