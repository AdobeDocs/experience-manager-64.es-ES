---
title: Función de ideación
seo-title: Ideation Feature
description: Adición y configuración de la función Ideación
seo-description: Adding and configuring the Ideation feature
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 1%

---

# Función de ideación {#ideation-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La función de ideación proporciona un área para los visitantes del sitio que han iniciado sesión (miembros de la comunidad) en el entorno de publicación para:

* Cree ideas para compartirlas con la comunidad
* Ver y comentar ideas
* Seguir una idea
* Votación sobre una idea

Esta sección de la documentación describe

* Adición de la función de ideación a un sitio AEM
* Ajustes de configuración del componente Ideación

## Adición de una idea a una página {#adding-a-ideation-to-a-page}

Para agregar un `Ideation` a una página en modo de autor, utilice el navegador de componentes para localizar `Communities / Ideation` y arrástrela a su lugar en una página en la que debería aparecer la idea.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](ideation.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Ideation`aparecerá el componente:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuración de una idea {#configuring-an-ideation}

Seleccione la colocación `Ideation` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Ficha Configuración {#settings-tab}

En el **[!UICONTROL Configuración]** especifique la configuración de las ideas y los comentarios:

* **[!UICONTROL Título de la idea]**
Título para mostrar la idea. El valor predeterminado es 
`Ideation`.

* **[!UICONTROL Descripción de la idea]**
Descripción que se mostrará como un subtítulo para la idea. El valor predeterminado no es una descripción.

* **[!UICONTROL Temas por página]**
Define el número de ideas/anuncios que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]**
Si se selecciona, la publicación de ideas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrado]**
Si se selecciona, el foro de ideación está cerrado a nuevas ideas y comentarios. El valor predeterminado no está seleccionado.

* **[!UICONTROL Editor de texto enriquecido]**
Si se selecciona, las ideas y los comentarios pueden introducirse con marcado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir etiquetado]**
Si está activada, permita que los miembros agreguen etiquetas a su publicación (consulte **[!UICONTROL Campo de etiqueta]** ). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir cargas de archivos]**
Si está activada, permita que los archivos adjuntos se agreguen a la idea o comentario. El valor predeterminado no está seleccionado.

* **[!UICONTROL Tamaño máximo del archivo]**
Solo relevante si 
`Allow File Uploads` está activada. Este campo limita el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de archivo permitidos]**
Solo relevante si 
`Allow File Uploads` está activada. Lista de extensiones de archivo separados por coma con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar aquellos que no se especifiquen. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Adjuntar tamaño máximo de archivo de imagen]**
Solo es relevante si está marcada la opción Permitir cargas de archivos . Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir respuestas]**
Si está marcada esta opción, permita que se respondan a los comentarios publicados en la idea. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y temas]**
Si se selecciona, permita que los miembros eliminen los comentarios e ideas que publicaron. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir lo siguiente]**
Si está marcada esta opción, incluya la siguiente función para anuncios de ideas, que permite que los miembros se [notificadas](notifications.md) de nuevos puestos. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir suscripciones de correo electrónico]**
Si está activada, permita que se notifique a los miembros de los anuncios nuevos por correo electrónico ([suscripción](subscriptions.md)). Requiere `Allow Following` que se comprobarán y [correo electrónico configurado](email.md). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir votación]**
Si está comprobado, permita votar los comentarios de una idea. El valor predeterminado no está seleccionado.

* **[!UICONTROL Mostrar distintivos]**
Si está activada, muestre ganado y asignado [distintivos](implementing-scoring.md) con la idea de un miembro. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir contenido destacado]**
si se selecciona, la idea puede identificarse como [contenido destacado](featured.md). El valor predeterminado no está seleccionado.

### Pestaña Moderación del usuario {#user-moderation-tab}

En el **[!UICONTROL Moderación del usuario]** especifique cómo se administran las ideas y comentarios publicados (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Denegar publicaciones]**
Si se selecciona, se permitirá a los moderadores miembros de confianza denegar publicaciones e impedir que la publicación aparezca en el foro público. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrar/volver a abrir temas]**
Si se selecciona, los moderadores miembros de confianza pueden cerrar un tema para realizar más ediciones y comentarios, y también pueden volver a abrir un tema. El valor predeterminado no está seleccionado.

* **[!UICONTROL Marcar anuncios]**
Si se selecciona, permita a los miembros marcar como inapropiados los temas o comentarios de otros. El valor predeterminado no está seleccionado.

* **[!UICONTROL Lista de motivos del indicador]**
Si está marcada esta opción, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan un tema o comentario como inapropiado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Razón de marca personalizada]**
Si está activada, permita que los miembros especifiquen su propio motivo para marcar un tema o comentario como inapropiado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Umbral de moderación]**
Introduzca el número de veces que los miembros deben marcar un tema o comentario antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite de marcado]**
Introduzca el número de veces que se debe marcar un tema o comentario antes de ocultarlo de la vista pública. Si se establece en -1, el tema o comentario marcado nunca se oculta a la vista del público. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

### Ficha Campo de etiqueta {#tag-field-tab}

En el **[!UICONTROL Campo de etiqueta]** , las etiquetas que se pueden aplicar, si se permiten en la sección **[!UICONTROL Configuración]** , se limitan según los espacios de nombres seleccionados.

* **[!UICONTROL Espacios de nombres permitidos]**
Pertinente si 
`Allow Tagging` se marca en la sección **Configuración** pestaña . Las etiquetas que se pueden aplicar se limitan a las que están dentro de las categorías de espacio de nombres seleccionadas. La lista de áreas de nombres incluye &quot;Etiquetas estándar&quot; (el espacio de nombres predeterminado) así como &quot;Incluir todas las etiquetas&quot;. El valor predeterminado es ninguno activado, lo que significa que se permiten todas las áreas de nombres.

* **[!UICONTROL Límite de sugerencias]**
Introduzca el número de etiquetas que se mostrarán como una sugerencia para el usuario que publica en el foro. Un valor de 
**-** 1 significa que no hay límite. El valor predeterminado es 0.

### Ficha Ordenar configuración {#sort-settings-tab}

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

### Creación de una idea {#creating-idea}

Al igual que con todas las características de Communities, si no se ha iniciado sesión, el visitante del sitio solo puede leer ideas y ver otras opiniones (a través de comentarios y votos/&quot;Me gusta&quot;).

Una vez que haya iniciado sesión, un miembro puede crear una nueva idea.

![chlimage_1-32](assets/chlimage_1-32.png)

Antes de presentar la idea, es posible que el miembro guarde un borrador.

Seleccione la `Save as Draft` , se guarda un borrador.

![chlimage_1-33](assets/chlimage_1-33.png)

Al ver borradores guardados en el `My Drafts` , seleccione `Read More` para volver a entrar en el modo de edición:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Proporcionar comentarios {#providing-feedback}

Una vez publicada la idea, otros miembros pueden iniciar sesión, abrir la idea ( `Read More`) y me gusta la idea, añadiendo así al recuento de votos, y hacer comentarios.

![chlimage_1-35](assets/chlimage_1-35.png)

### Información adicional {#additional-information}

Puede encontrar más información en la [Aspectos básicos de la idea](ideation.md) para desarrolladores.

Para moderar los temas y comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar temas y comentarios publicados, consulte [Etiquetado del contenido generado por el usuario](tag-ugc.md).
