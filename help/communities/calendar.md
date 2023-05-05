---
title: Función de calendario
seo-title: Calendar Feature
description: Proporciona información de eventos de la comunidad en formato de calendario
seo-description: Provides community event information in a calendar format
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
exl-id: f95d1471-82a1-4c37-ac5b-0eb861c823a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 7%

---

# Función de calendario {#calendar-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La función de calendario permite proporcionar información de eventos de la comunidad en formato de calendario a todos los visitantes del sitio o solo a los visitantes del sitio (miembros de la comunidad), mientras que solo los miembros autorizados pueden agregar eventos.

Esta sección de la documentación describe:

* Adición de la función de calendario a un sitio AEM
* Ajustes de configuración para `Calendar`componentes

## Adición de un calendario a una página {#adding-a-calendar-to-a-page}

Para agregar un `Calendar` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Calendar`

y arrástrela a su lugar en una página, por ejemplo, una posición relativa a la función para que los usuarios la revisen.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](calendar-basics-for-developers.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Calendar` aparecerá el componente.

![chlimage_1-112](assets/chlimage_1-112.png)

### Configuración del calendario {#configuring-calendar}

Seleccione la colocación `Calendar`para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### Ficha Configuración {#settings-tab}

En el **[!UICONTROL Configuración]** , especifique si desea permitir o no que las etiquetas se apliquen a las entradas del calendario.

* **[!UICONTROL Eventos por página]**

   Define el número de eventos que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Moderado]**

   Si se selecciona, la publicación de eventos de calendario y comentarios debe aprobarse antes de que aparezcan en un sitio de publicación. El valor predeterminado no está seleccionado.

* **[!UICONTROL Cerrado]**

   Si se selecciona, el calendario se cierra a nuevas entradas de eventos y comentarios. El valor predeterminado no está seleccionado.

* **[!UICONTROL Editor de texto enriquecido]**

   Si se selecciona, los eventos de calendario y los comentarios se pueden introducir con marcado. El valor predeterminado está marcado.

* **[!UICONTROL Permitir etiquetado]**

   Si está activada, permita que los miembros agreguen etiquetas a los eventos que anuncien (consulte **Campo de etiqueta** ). El valor predeterminado está marcado.

* **[!UICONTROL Permitir cargas de archivos]**

   Si está activada, permita que los archivos adjuntos se agreguen a un evento o comentario de calendario. El valor predeterminado está marcado.

* **[!UICONTROL Permitir seguimiento]**

   Si está activada, permita que los miembros sigan los eventos anunciados en el calendario. El valor predeterminado está marcado.

* **[!UICONTROL Tamaño máximo de archivo]**

   Solo relevante si `Allow File Uploads` está activada. Este campo limita el tamaño (en bytes) de un archivo cargado. El valor predeterminado es 104857600 (10 Mb).

* **[!UICONTROL Tipos de archivo permitidos]**

   Solo relevante si `Allow File Uploads` está activada. Lista de extensiones de archivo separados por coma con el separador &quot;punto&quot;. Por ejemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Si se especifica algún tipo de archivo, no se permitirá cargar aquellos que no se especifiquen. El valor predeterminado no se especifica de forma que se permitan todos los tipos de archivo.

* **[!UICONTROL Tamaño máximo de archivo de imagen adjunto]**

   Solo es relevante si está marcada la opción Permitir cargas de archivos . Número máximo de bytes que puede tener un archivo de imagen cargado. El valor predeterminado es 2097152 (2 Mb).

* **[!UICONTROL Tipos de imagen de portada permitidos]**

   Lista separada por comas de las extensiones de archivo de imagen con el separador &quot;punto&quot;. El valor predeterminado es `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL Permitir respuestas de debate]**

   Si está marcada esta opción, permita que se respondan a los comentarios anunciados en el evento de calendario. El valor predeterminado está marcado.

* **[!UICONTROL Permitir que los usuarios eliminen comentarios y eventos]**

   Si está activada, permita que los miembros eliminen los comentarios y los eventos de calendario que hayan publicado. El valor predeterminado está marcado.

* **[!UICONTROL Habilitar la votación]**

   Si está marcada esta opción, incluya la función Votación con un evento de calendario. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar rutas]**

   Mostrar rutas en la página de eventos. El valor predeterminado está marcado.

* **[!UICONTROL Filtro de intervalo de fechas]**

   Define el número de días agregados a la fecha actual para calcular el valor &quot;Para&quot; del filtro de página de lista de eventos de calendario. El número predeterminado es 30.

* **[!UICONTROL Permitir contenido destacado]**

   Si se selecciona, la idea puede identificarse como [contenido destacado](featured.md). El valor predeterminado no está seleccionado.

En el **[!UICONTROL Moderación del usuario]** especifique cómo se administran los temas publicados y las respuestas (contenido generado por el usuario). Para obtener más información, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

#### Pestaña Moderación del usuario {#user-moderation-tab}

* **[!UICONTROL Denegar entradas]**

   Si se selecciona, se permitirá a los moderadores miembros de confianza denegar publicaciones e impedir que la publicación aparezca en el foro público. El valor predeterminado está marcado.

* **[!UICONTROL Cerrar/abrir de nuevo los eventos]**

   Si se selecciona, los moderadores miembros de confianza pueden cerrar un evento para realizar más ediciones y comentarios, y también pueden volver a abrir un evento. El valor predeterminado está marcado.

* **[!UICONTROL Marcar entradas]**

   Si está activada, permita que los miembros marquen los eventos o comentarios de otros como inapropiados. El valor predeterminado está marcado.

* **[!UICONTROL Lista de motivos de indicación]**

   Si está marcada esta opción, permita que los miembros elijan, desde una lista desplegable, el motivo por el que marcan un evento o comentario como inapropiado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Motivo de indicación personalizado]**

   Si está marcada esta opción, permita que los miembros especifiquen su propio motivo para marcar un evento o comentario como inapropiado. El valor predeterminado no está seleccionado.

* **[!UICONTROL Umbral de moderación]**

   Introduzca el número de veces que los miembros deben marcar un evento o comentario antes de notificar a los moderadores. El valor predeterminado es 1 ( una vez).

* **[!UICONTROL Límite de indicación]**

   Introduzca el número de veces que se debe marcar un evento o comentario antes de ocultarlo de la vista pública. Si se establece en -1, el tema o comentario marcado nunca se oculta a la vista del público. De lo contrario, este número debe ser bueno o igual al umbral de moderación. El valor predeterminado es 5.

#### Ficha Campo de etiqueta {#tag-field-tab}

En el **[!UICONTROL Campo de etiqueta]** , las etiquetas que se pueden aplicar, si se permiten en la sección **[!UICONTROL Configuración]** , se limitan según los espacios de nombres seleccionados.

* **[!UICONTROL Espacios de nombres permitidos]**

   Pertinente si `Allow Tagging` se marca en la sección **[!UICONTROL Configuración]** pestaña . Las etiquetas que se pueden aplicar se limitan a las que están dentro de las categorías de espacio de nombres seleccionadas. La lista de áreas de nombres incluye &quot;Etiquetas estándar&quot; (el espacio de nombres predeterminado) así como &quot;Incluir todas las etiquetas&quot;. El valor predeterminado es ninguno activado, lo que significa que se permiten todas las áreas de nombres.

* **[!UICONTROL Límite de sugerencias]**

   Introduzca el número de etiquetas que se mostrarán como una sugerencia para el usuario que publica en el foro. El valor predeterminado es `-1` (sin límites).

>[!NOTE]
>
>Visita [Administración de etiquetas](../../help/sites-administering/tags.md) para aprender a añadir un nuevo espacio de nombres de etiqueta (taxonomía).

#### Ficha Traducción {#translation-tab}

En el **[!UICONTROL Traducción]** , si la traducción está habilitada para el sitio de la comunidad, la traducción se puede configurar para que traduzca todo el subproceso (evento y comentarios) en lugar de anuncios específicos.

* **[!UICONTROL Traducir todos]**

   Si se selecciona, el evento y los comentarios se traducen al idioma preferido del usuario. El valor predeterminado está marcado.

## Experiencia del visitante del sitio {#site-visitor-experience}

En el entorno de publicación, la función de calendario mostrará un campo de búsqueda con un intervalo de fechas predeterminado y cualquier evento de calendario que se encuentre dentro de ese intervalo.

Cuando se selecciona un evento de calendario, se muestran los detalles, la descripción y los comentarios del evento de calendario.

Otras capacidades dependen de si el visitante del sitio es moderador, administrador, miembro de la comunidad, miembro privilegiado o anónimo.

### Moderadores y administradores {#moderators-and-administrators}

Cuando el usuario que ha iniciado sesión tiene privilegios de moderador o administrador, puede realizar [tareas de moderación](moderate-ugc.md) (según lo permita la configuración del componente) en todos los eventos de calendario y comentarios anunciados en un evento.

![chlimage_1-115](assets/chlimage_1-115.png)

### Miembros {#members}

Cuando el usuario que ha iniciado sesión es un miembro de la comunidad o [miembro privilegiado](users.md#privileged-members-group) (según la configuración), pueden seleccionar `New Event` para crear y anunciar un nuevo evento de calendario.

Concretamente, pueden

* Crear un nuevo evento de calendario
* Publicar un comentario en un evento de calendario
* Editar su propio evento de calendario o comentario
* Eliminar su propio evento de calendario o comentario
* Marcar eventos de calendario o comentarios de otros

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### Anónimo {#anonymous}

Los visitantes del sitio que no hayan iniciado sesión solo podrán leer los eventos de calendario anunciados, traducirlos si son compatibles, pero no pueden agregar un evento o comentario ni marcar los eventos o comentarios de otros.

![chlimage_1-118](assets/chlimage_1-118.png)

## Información adicional {#additional-information}

Puede encontrar más información en la [Elementos básicos del calendario](calendar-basics-for-developers.md) para desarrolladores.

Para moderar eventos de calendario y comentarios, consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

Para etiquetar eventos de calendario y comentarios, consulte [Etiquetado del contenido generado por el usuario](tag-ugc.md).

Para ver la traducción de los eventos y comentarios del calendario, consulte [Traducción del contenido generado por el usuario](translate-ugc.md).
