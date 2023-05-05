---
title: Función de foro
seo-title: Forum Feature
description: Cómo añadir y configurar la función de foro
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 1%

---

# Función de foro {#forum-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La función de foro proporciona un área para los visitantes del sitio que han iniciado sesión (miembros de la comunidad) en el entorno de publicación para:

* Crear nuevos temas
* Ver y responder temas
* Seguir un tema
* Buscar en un foro
* Ayudar a moderar el contenido del foro
* Mover temas de foro de una página a otra

Esta sección de la documentación describe

* Adición de la función de foro a un sitio AEM
* Ajustes de configuración para `Forum`componente

## Adición de un foro a una página {#adding-a-forum-to-a-page}

Para agregar un `Forum` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Forum`

Y arrástrela a su lugar en una página donde debería aparecer el foro.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](essentials-forum.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Forum`aparecerá el componente:

![imagen_1-60](assets/chlimage_1-60.png)

## Configuración de un foro {#configuring-a-forum}

Seleccione la colocación `Forum` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![climage_1-61](assets/chlimage_1-61.png) ![imagen_1-62](assets/chlimage_1-62.png)

### Ficha Configuración {#settings-tab}

En el **[!UICONTROL Configuración]** especifique la configuración de los temas y las respuestas:

* **[!UICONTROL Temas por página]**
Define el número de temas/anuncios que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]**
Si se selecciona, la publicación de temas y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrado]**
Si se selecciona, el foro se cierra a nuevos temas y comentarios. El valor predeterminado no está seleccionado.

* **[!UICONTROL Editor de texto enriquecido]**
Si se selecciona, los temas y comentarios se pueden introducir con marcado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir etiquetado]**
Si está activada, permita que los miembros agreguen etiquetas a su publicación (consulte **[!UICONTROL Campo de etiqueta]** ). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir cargas de archivos]**
Si está activada, permita que los archivos adjuntos se agreguen al tema o comentario. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir lo siguiente]**
Si está marcada esta opción, incluya la siguiente función para las publicaciones en el foro, que permite que los miembros se [notificadas](notifications.md) de nuevos puestos. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir anclaje]**
Si se selecciona, los temas del foro pueden colocarse en la parte superior de la lista de temas. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir contenido destacado]**
si se selecciona, la idea puede identificarse como [contenido destacado](featured.md). El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir suscripciones de correo electrónico]**
Si está activada, permita que se notifique a los miembros de los anuncios nuevos por correo electrónico ([suscripción](subscriptions.md)). Requiere `Allow Following` que se comprobarán y [correo electrónico configurado](email.md). El valor predeterminado no está seleccionado.

* **[!UICONTROL Tamaño máximo del archivo]**
Solo relevante si 
`Allow File Uploads` está activada. Este campo limita el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de archivo permitidos]**
Solo relevante si 
`Allow File Uploads` está activada. Lista de extensiones de archivo separados por coma con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar aquellos que no se especifiquen. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Adjuntar tamaño máximo de archivo de imagen]**
Solo es relevante si está marcada la opción Permitir cargas de archivos . Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Permitir respuestas con subprocesos]**
Si está marcada esta opción, permita que se respondan a los comentarios publicados en el tema. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y temas]**
Si está marcada esta opción, permita que los miembros eliminen los comentarios y temas que publicaron. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir votación]**
Si está marcada esta opción, incluya la función Votación con un tema. El valor predeterminado no está seleccionado.

* **[!UICONTROL Mostrar rutas de exploración]**
Si está activada, muestre las rutas de navegación en las páginas de temas. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar distintivos]**
Si está activada, muestre ganado y asignado [distintivos](implementing-scoring.md) con la entrada de blog de un miembro. El valor predeterminado no está seleccionado.

>[!NOTE]
>
>Puede ser necesario comprobar ambas `AllowThreaded Replies` y `Allow users to Delete Comments and Topics` para activar los comentarios sobre un tema.

### Pestaña Moderación del usuario {#user-moderation-tab}

En el **[!UICONTROL Moderación del usuario]** especifique cómo se administran los temas publicados y las respuestas (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

* **[!UICONTROL Denegar publicaciones]**
Si se selecciona, se permitirá a los moderadores miembros de confianza denegar publicaciones e impedir que la publicación aparezca en el foro público. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrar/volver a abrir temas]**
Si se selecciona, los moderadores miembros de confianza pueden cerrar un tema para realizar más ediciones y comentarios, y también pueden volver a abrir un tema. El valor predeterminado no está seleccionado.

* **[!UICONTROL Mover temas]**
Si está marcada esta opción, permita que los moderadores del lado de publicación movieran los temas. El valor predeterminado está marcado.

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
Pertinente si `Allow Tagging` se marca en la sección **[!UICONTROL Configuración]** pestaña . Las etiquetas que se pueden aplicar se limitan a las que están dentro de las categorías de espacio de nombres seleccionadas. La lista de áreas de nombres incluye &quot;Etiquetas estándar&quot; (el espacio de nombres predeterminado) así como &quot;Incluir todas las etiquetas&quot;. El valor predeterminado es ninguno activado, lo que significa que se permiten todas las áreas de nombres.

* **[!UICONTROL Límite de sugerencias]**
Introduzca el número de etiquetas que se mostrarán como una sugerencia para el usuario que publica en el foro. El valor predeterminado es 
**-** 1 (sin límites).

### Ficha Traducción {#translation-tab}

En el **[!UICONTROL Traducción]** , si la traducción está habilitada para el sitio de la comunidad, la traducción se puede configurar para traducir el tema completo o los anuncios seleccionados.

* **[!UICONTROL Traducir todo]**
Si se selecciona, el hilo del foro se traduce al idioma preferido del usuario. El valor predeterminado no está seleccionado.

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

## Información adicional {#additional-information}

Puede encontrar más información en la [Forum Essentials](essentials-forum.md) para desarrolladores.

Para moderar los temas y comentarios publicados, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar temas y comentarios publicados, consulte [Etiquetado del contenido generado por el usuario](tag-ugc.md).

Para ver la traducción de los temas y comentarios publicados, consulte [Traducción del contenido generado por el usuario](translate-ugc.md).
