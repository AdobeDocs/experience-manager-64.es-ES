---
title: Función de calendario
seo-title: Función de calendario
description: Proporciona información de eventos de comunidad en formato de calendario
seo-description: Proporciona información de eventos de comunidad en formato de calendario
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Función de calendario {#calendar-feature}

## Introducción {#introduction}

La función de calendario permite proporcionar información de eventos de comunidad en formato de calendario a todos los visitantes del sitio o solamente a los visitantes del sitio (miembros de la comunidad), mientras que sólo los miembros autorizados pueden agregar eventos.

Esta sección de la documentación describe:

* Adición de la función de calendario a un sitio de AEM
* Configuración de `Calendar`componentes

## Adding a Calendar to a Page {#adding-a-calendar-to-a-page}

Para agregar un `Calendar` componente a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Calendar`

y arrástrelo a su lugar en una página, como una posición relativa a la función que los usuarios deben revisar.

Para obtener la información necesaria, visite [Communities Components Basics](basics.md)(Conceptos básicos de componentes de comunidades).

Cuando se incluyen las bibliotecas [](calendar-basics-for-developers.md#essentials-for-client-side) requeridas del lado del cliente, así es como aparecerá el `Calendar` componente.

![chlimage_1-112](assets/chlimage_1-112.png)

### Configuración del calendario {#configuring-calendar}

Seleccione el `Calendar`componente colocado al que desea acceder y seleccione el `Configure` icono que abre el cuadro de diálogo de edición.

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]** , especifique si desea permitir o no que las etiquetas se apliquen a las entradas de calendario.

* **[!UICONTROL Eventos por página]**

   Define el número de eventos que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]**

   Si se selecciona, la publicación de eventos de calendario y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está marcado.

* **[!UICONTROL Cerrado]**

   Si se selecciona, el calendario se cierra a nuevas entradas y comentarios de eventos. El valor predeterminado no está marcado.

* **[!UICONTROL Editor de texto enriquecido]**

   Si se selecciona, los eventos de calendario y los comentarios se pueden introducir con marcado. El valor predeterminado está marcado.

* **[!UICONTROL Permitir etiquetado]**

   Si está activada, permita que los miembros agreguen etiquetas a los eventos que publiquen (consulte la ficha Campo **** Etiqueta). El valor predeterminado está marcado.

* **[!UICONTROL Permitir cargas de archivos]**

   Si está activada, permita que los archivos adjuntos se agreguen a un evento de calendario o comentario. El valor predeterminado está marcado.

* **[!UICONTROL Permitir seguimiento]**

   Si está activada, permita que los miembros sigan los eventos anunciados en el calendario. El valor predeterminado está marcado.

* **[!UICONTROL Tamaño máximo de archivo]**

   Solo es pertinente si `Allow File Uploads` está marcado. Este campo limitará el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de archivo permitidos]**

   Solo es pertinente si `Allow File Uploads` está marcado. Una lista separada por comas de extensiones de archivo con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar los no especificados. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Tamaño máximo de archivo de imagen adjunto]**

   Solo es relevante si está activada la opción Permitir cargas de archivos. Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Tipos de imagen de portada permitidos]**

   Lista separada por comas de extensiones de archivo de imagen con el separador &quot;punto&quot;. El valor predeterminado es `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL Permitir respuestas de debate]**

   Si está activada, permita respuestas a los comentarios publicados en el evento de calendario. El valor predeterminado está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y eventos]**

   Si está activada, permita que los miembros eliminen los comentarios y los eventos de calendario que anunciaron. El valor predeterminado está marcado.

* **[!UICONTROL Habilitar la votación]**

   Si está activada, incluya la función Votación con un evento de calendario. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar rutas]**

   Mostrar rutas en la página de eventos. El valor predeterminado está marcado.

* **[!UICONTROL Filtro de intervalo de fechas]**

   Define el número de días agregados a la fecha actual para calcular el valor &quot;A&quot; del filtro de página de lista de eventos de calendario. El número predeterminado es 30.

* **[!UICONTROL Permitir contenido destacado]**

   Si se selecciona, la idea se puede identificar como contenido [](featured.md)destacado. El valor predeterminado no está marcado.

En la ficha Moderación **[!UICONTROL del]** usuario, especifique cómo se administran los temas y las respuestas publicados (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

#### Ficha Moderación del usuario {#user-moderation-tab}

* **[!UICONTROL Denegar entradas]**

   Si se selecciona, los moderadores miembros de confianza podrán denegar las publicaciones e impedir que aparezcan en el foro público. El valor predeterminado está marcado.

* **[!UICONTROL Cerrar/abrir de nuevo los eventos]**

   Si se selecciona, los moderadores de miembros de confianza pueden cerrar un evento para realizar más ediciones y comentarios, y también pueden volver a abrir un evento. El valor predeterminado está marcado.

* **[!UICONTROL Marcar entradas]**

   Si se selecciona, permita que los miembros marquen los eventos o comentarios de otros como inapropiados. El valor predeterminado está marcado.

* **[!UICONTROL Lista de motivos de indicación]**

   Si se selecciona, permita que los miembros elijan, en una lista desplegable, el motivo por el que marcan un evento o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Motivo de indicación personalizado]**

   Si está activada, permita que los miembros especifiquen su propio motivo para marcar un evento o comentario como inapropiado. El valor predeterminado no está marcado.

* **[!UICONTROL Umbral de moderación]**

   Introduzca el número de veces que los miembros deben marcar un evento o comentario antes de que se notifique a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite de indicación]**

   Introduzca el número de veces que se debe marcar un evento o comentario antes de ocultarlo en la vista pública. Si se establece en -1, el tema o comentario marcado nunca se oculta en la vista pública. De lo contrario, este número debe ser mayor o igual que el umbral de moderación. El valor predeterminado es 5.

#### Ficha Campo de etiqueta {#tag-field-tab}

En la ficha Campo **** Etiqueta, las etiquetas que se pueden aplicar, si se permiten en la ficha **[!UICONTROL Configuración]** , se limitan según los espacios de nombres elegidos.

* **[!UICONTROL Espacios de nombres permitidos]**

   Relevante si `Allow Tagging` se marca en la ficha **[!UICONTROL Configuración]** . Las etiquetas que se pueden aplicar están limitadas a las que se encuentran dentro de las categorías de espacio de nombres seleccionadas. La lista de espacios de nombres incluye &quot;Etiquetas estándar&quot; (el espacio de nombres predeterminado) y &quot;Incluir todas las etiquetas&quot;. El valor predeterminado no está marcado, lo que significa que se permiten todos los espacios de nombres.

* **[!UICONTROL Límite de sugerencias]**

   Escriba el número de etiquetas que se mostrarán como una sugerencia para el miembro que se publica en el foro. El valor predeterminado es `-1` (sin límites).

>[!NOTE]
>
>Visite [Administración de etiquetas](../../help/sites-administering/tags.md) para obtener información sobre cómo agregar un nuevo espacio de nombres de etiquetas (taxonomía).

#### Ficha Traducción {#translation-tab}

En la ficha **[!UICONTROL Traducción]** , si la traducción está habilitada para el sitio de la comunidad, la traducción puede configurarse para traducir el subproceso completo (evento y comentarios) en lugar de publicaciones específicas.

* **[!UICONTROL Traducir todos]**

   Si se selecciona, el evento y los comentarios se traducen al idioma preferido del usuario. El valor predeterminado está marcado.

## Experiencia del visitante del sitio {#site-visitor-experience}

En el entorno de publicación, la función de calendario mostrará un campo de búsqueda con un intervalo de fechas predeterminado y cualquier evento de calendario que se encuentre dentro de ese intervalo.

Cuando se selecciona un evento de calendario, se muestran los detalles, la descripción y los comentarios del evento de calendario.

Otras capacidades dependen de si el visitante del sitio es un moderador, administrador, miembro de la comunidad, miembro privilegiado o anónimo.

### Moderadores y administradores {#moderators-and-administrators}

Cuando el usuario que ha iniciado sesión tiene privilegios de moderador o administrador, puede realizar tareas [de](moderate-ugc.md) moderación (según lo permitido por la configuración del componente) en todos los eventos de calendario y comentarios publicados en un evento.

![chlimage_1-115](assets/chlimage_1-115.png)

### Miembros {#members}

Cuando el usuario que ha iniciado sesión es miembro de la comunidad o miembro [](users.md#privileged-members-group) privilegiado (según la configuración), puede seleccionar `New Event` crear y anunciar un nuevo evento de calendario.

Concretamente, pueden

* Crear un nuevo evento de calendario
* Anunciar un comentario en un evento de calendario
* Editar su propio evento de calendario o comentario
* Eliminar su propio evento de calendario o comentario
* Marcar los eventos de calendario o comentarios de otros

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### Anónimo {#anonymous}

Los visitantes del sitio que no hayan iniciado sesión sólo podrán leer los eventos de calendario publicados, traducirlos si son compatibles, pero no podrán agregar un evento o comentario ni marcar los eventos o comentarios de otros.

![chlimage_1-118](assets/chlimage_1-118.png)

## Información adicional {#additional-information}

Puede encontrar más información en la página [Calendar Essentials](calendar-basics-for-developers.md) para desarrolladores.

Para obtener información sobre la moderación de eventos de calendario y comentarios, consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

Para etiquetar eventos de calendario y comentarios, consulte [Etiquetado de contenido](tag-ugc.md)generado por el usuario.

Para ver la traducción de eventos de calendario y comentarios, consulte [Traducción de contenido](translate-ugc.md)generado por el usuario.
