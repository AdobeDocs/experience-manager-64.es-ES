---
title: Funciones de comunidad
seo-title: Funciones de comunidad
description: Obtenga información sobre cómo acceder a la consola Funciones de la comunidad
seo-description: Obtenga información sobre cómo acceder a la consola Funciones de la comunidad
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2543'
ht-degree: 2%

---


# Funciones de comunidad {#community-functions}

El tipo de funciones que se esperan de una experiencia de comunidad son bien conocidas. Las funciones de comunidad están disponibles como funciones de la comunidad. Fundamentalmente, son una o más páginas precableadas para implementar una función de comunidad que requiere algo más que simplemente añadir un componente a una página en modo de autor. Son los componentes básicos que se utilizan para definir la estructura de una [plantilla de sitio de la comunidad](sites.md) desde la que [se crean los sitios de la comunidad](sites-console.md).

Una vez creado un sitio de comunidad, se puede añadir contenido a las páginas resultantes mediante el [AEM modo de creación estándar](../../help/sites-authoring/editing-content.md).

Hay varias funciones de la comunidad disponibles inmediatamente, como se ve en la consola de funciones de la comunidad. En futuras versiones se presentarán más funciones de la comunidad, y también se podrán crear funciones personalizadas.

>[!NOTE]
>
>Las consolas para la creación de [sitios de la comunidad](sites-console.md), [plantillas de sitios de la comunidad](sites.md), [plantillas de grupos de la comunidad](tools-groups.md) y [funciones de la comunidad](functions.md) solo se deben usar en el entorno de creación.

## Consola de funciones de la comunidad {#community-functions-console}

En el entorno de creación, para llegar a la consola de funciones de la comunidad

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Funciones de la comunidad]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Funciones creadas previamente {#pre-built-functions}

A continuación se ofrece una breve descripción de las funciones entregadas con AEM Communities. Cada función consta de una o más páginas AEM que contienen componentes de Communities conectados en una función que se incorpora fácilmente en una [plantilla de sitio de la comunidad](sites.md).

Una plantilla de sitio de la comunidad proporciona la estructura para un sitio de la comunidad, que incluye: inicio de sesión, perfiles de usuario, notificaciones, mensajes, menú del sitio, búsqueda, tema y funciones de marca.

### Configuración de título y dirección URL {#title-and-url-settings}

**** Título y  **** URLson propiedades comunes a todas las funciones de la comunidad.

Cuando se agrega una función de comunidad a una plantilla de sitio de comunidad o se agrega al [modificar](sites-console.md#modifying-site-properties) la estructura de un sitio de comunidad, se abre el cuadro de diálogo de la función para que se puedan configurar el Título y la URL.

#### Detalles de la función de configuración {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Título]**
(
**) Texto que aparece en el menú de características del sitio

* **[!UICONTROL URL]**
 (*obligatorio*) El nombre utilizado para generar el URI. El nombre debe cumplir las [convenciones de nomenclatura](../../help/sites-developing/naming-conventions.md) impuestas por AEM y JCR.

Por ejemplo, si utiliza el sitio creado a partir del tutorial [Introducción](getting-started.md)

* Título = Página Web
* URL = página

A continuación, la dirección URL a la página es http://local_host:4503/content/sites/engage/en/page.html y el vínculo de menú de la página aparece como:

![chlimage_1-381](assets/chlimage_1-381.png)

### Función Secuencia de actividades {#activity-stream-function}

La función de flujo de actividad es una página con un [componente Flujos de actividad](activities.md) con todas las vistas seleccionadas (todas las actividades, actividades del usuario y las siguientes). Consulte también [Elementos esenciales del flujo de actividad](essentials-activities.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente:

#### Detalles de la función de configuración {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Mostrar la]**
vista &quot;Mis actividades&quot;Si está marcada, la página Actividades incluirá una pestaña que filtra las actividades en función de las generadas dentro de la comunidad por el miembro actual. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar la]**
vista &quot;Todas las actividades&quot;Si está marcada, la página Actividades incluirá una pestaña que incluye todas las actividades generadas dentro de la comunidad a la que tiene acceso el miembro actual. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar la]**
vista &quot;Fuente de noticias&quot; Si está marcada, la página Actividades incluirá una pestaña que filtra las actividades en función de las que sigue el miembro actual. El valor predeterminado está marcado.

### Función Asignaciones {#assignments-function}

La función de asignaciones es la función básica que define un [sitio de la comunidad para la habilitación](overview.md#enablement-community). Permite asignar recursos de habilitación a los miembros de la comunidad. Consulte también [Assigned Essentials](essentials-assignments.md) para desarrolladores.

Esta función está disponible como función del complemento [de habilitación](enablement.md). El complemento de habilitación requiere licencias adicionales para su uso en un entorno de producción.

Cuando se agrega a una plantilla, la única configuración es para [Configuración del título y la dirección URL](#title-and-url-settings).

### Función Blog {#blog-function}

La función de blog es una página con un [componente de blog](blog-feature.md) configurado para etiquetado, cargas de archivos, seguimiento, miembros para autoedición, votación y moderación. Consulte también [Blog Essentials](blog-developer-basics.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente:

![chlimage_1-383](assets/chlimage_1-383.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el blog solo permitirá a los miembros privilegiados crear artículos permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden crear. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se selecciona, el blog incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por subprocesosSi no se marca, el blog permitirá respuestas (comentarios) a un artículo, pero no se permiten respuestas a comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea puede identificarse como contenido [ ](featured.md)destacado. El valor predeterminado está marcado.

### Función Calendario {#calendar-function}

La función de calendario es una página con un [componente de calendario](calendar.md) configurado para permitir el etiquetado. Consulte también [Calendar Essentials](calendar-basics-for-developers.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente:

![chlimage_1-384](assets/chlimage_1-384.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
FijarSi está activado, el foro permite que las respuestas de los temas se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el blog solo permitirá a los miembros privilegiados crear artículos permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden crear. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se selecciona, el blog incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por subprocesosSi no se marca, el blog permitirá respuestas (comentarios) a un artículo, pero no se permiten respuestas a comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea puede identificarse como contenido [ ](featured.md)destacado. El valor predeterminado está marcado.

### Función Catálogo {#catalog-function}

La función de catálogo permite a los miembros de [comunidad de habilitación](overview.md#enablement-community) examinar los recursos de habilitación que no se les han asignado. Consulte [Tagging Enablement Resources](tag-resources.md) y [Catalog Essentials](catalog-developer-essentials.md) para desarrolladores.

Todos los recursos de habilitación y las rutas de aprendizaje del sitio de la comunidad se mostrarán en todos los catálogos si su propiedad, ` [Show in Catalog](resources.md)`, está establecida en true. Para incluir explícitamente recursos y rutas de aprendizaje, es necesario aplicar un [pre-filter](catalog-developer-essentials.md#pre-filters) al catálogo.

Cuando se agrega a una plantilla, la configuración permite especificar el área de nombres de la etiqueta utilizada para configurar el filtro de etiquetas presentado a los visitantes del sitio:

![catalogfunc](assets/catalogfunc.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Seleccionar todos los espacios de nombres]**

   * Los espacios de nombres de etiquetas seleccionados definen qué etiquetas pueden seleccionar los visitantes para filtrar la lista de recursos de habilitación que aparece en el catálogo.
   * Si se selecciona, están disponibles todos los espacios de nombres de etiquetas permitidos para el sitio de la comunidad.
   * Si está desactivada, es posible seleccionar una o más áreas de nombres permitidas para el sitio de la comunidad.
   * El valor predeterminado está marcado.

### Función de contenido destacado {#featured-content-function}

La función de contenido destacado es una página con un [componente de contenido destacado](featured.md) configurado para permitir que se agreguen y eliminen comentarios.

La capacidad de presentar contenido puede estar permitida o no permitida por componente (consulte [Función de blog](#blog-function), [Función de calendario](#calendar-function), [Función de foro](#forum-function), [Función de ideación](#ideation-function) y [Función de QnA](#qna-function)).

Cuando se agrega a una plantilla, la única configuración es para [Configuración del título y la dirección URL](#title-and-url-settings).

### Función Biblioteca del archivo {#file-library-function}

La función de biblioteca de archivos es una página con un [componente Biblioteca de archivos](file-library.md) configurado para permitir que se agreguen y eliminen comentarios.

Cuando se agrega a una plantilla, la única configuración es para [Configuración del título y la dirección URL](#title-and-url-settings).

### Función Foro {#forum-function}

La función de foro es una página con un [componente de foro](forum.md) configurado para el etiquetado, la carga de archivos, el seguimiento y los miembros que se pueden editar por sí mismos, votar y moderar.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente:

#### Detalles de la función de configuración {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
FijarSi está activado, el foro permite que las respuestas de los temas se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se selecciona, el foro incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas mediante subprocesosSi no se marca, el foro permitirá comentarios sobre un tema, pero no se permiten las respuestas a esos comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea puede identificarse como contenido [ ](featured.md)destacado. El valor predeterminado está marcado.

### Función Grupos {#groups-function}

>[!CAUTION]
>
>La función de grupos debe *no* ser la *primera ni la única* de la estructura de un sitio o de una plantilla de sitio de la comunidad.
>
>Cualquier otra función, como la [función de página](#page-function), debe incluirse y enumerarse primero.

La función de grupos permite a los miembros de la comunidad crear subcomunidades dentro del sitio de la comunidad en el entorno de publicación.

Dependiendo de la [configuración](sites-console.md#groupmanagement) cuando la función Grupos está incluida en una [plantilla de sitio de la comunidad](sites.md), los grupos pueden ser públicos o privados y se puede configurar una o más plantillas de grupo de la comunidad para proporcionar una selección de plantillas cuando el grupo de la comunidad se crea realmente (como desde el entorno de publicación). Una [plantilla de grupo de comunidad](tools-groups.md) especifica qué características de Communities se crean para las páginas de grupo, como foros y calendarios.

Cuando se crea un grupo de comunidad, se crea dinámicamente un grupo de miembros para el nuevo grupo, al que se pueden asignar o unir miembros. Para obtener más información, consulte [Administración de usuarios y grupos de usuarios](users.md).

A partir de Communities [feature pack 1](deploy-communities.md#latestfeaturepack), los grupos de comunidades se crean en el entorno de creación mediante la consola [Communities Sites&#39; Groups](groups.md) y se pueden crear en el entorno de publicación cuando está habilitada.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente:

![chlimage_1-386](assets/chlimage_1-386.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Seleccionar]**
plantillas de grupoMenú desplegable que permite seleccionar una o más plantillas de grupo habilitadas a partir de las cuales el futuro creador de un nuevo grupo de comunidad (en el entorno de publicación) puede elegir.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas permitiendo la selección de un grupo [ de seguridad de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
creación de publicaciónSi está activada, es posible que los miembros autorizados de la comunidad creen un grupo en el entorno de publicación. Si no se selecciona, los grupos nuevos (subcomunidades) solo se pueden crear en el entorno de creación desde la consola Grupos de sitios de Communities.

   El valor predeterminado es `checked`.

### Función ideación {#ideation-function}

La función de ideación es una página con un [componente de ideación](ideation-feature.md).

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente, que especifica los nombres predeterminados Título y URL, así como la configuración de visualización predeterminada para la plantilla:

![chlimage_1-387](assets/chlimage_1-387.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas permitiendo la selección de un grupo [ de seguridad de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
cargas de archivosSi está activada, la idea incluirá la capacidad de los miembros para cargar archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas mediante subprocesosSi no está activada, la idea permite respuestas (comentarios) a un tema, pero no se permiten respuestas a comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea puede identificarse como contenido [ ](featured.md)destacado. El valor predeterminado está marcado.

### Función de la tabla de clasificación {#leaderboard-function}

La función del panel de control es una página con un [componente del panel de control](enabling-leaderboard.md).

**NOTA**: el componente Leaderboard necesitará más configuración  ** después de crear el sitio de comunidad a partir de una plantilla de comunidad que incluya la función Leaderboard . Será necesario especificar las [reglas](enabling-leaderboard.md#rules-tab) del componente del panel de vanguardia, que dependen de la configuración de [puntuación e insignias](implementing-scoring.md) para el sitio de la comunidad.

Cuando se agrega a una plantilla, se abre el cuadro de diálogo siguiente, que especifica los nombres predeterminados Título y URL, así como la configuración de visualización predeterminada para la plantilla:

![chlimage_1-388](assets/chlimage_1-388.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Mostrar]**
distintivoSi se selecciona, se incluye una columna para los iconos de distintivo en el panel de encabezado.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Mostrar]**
nombre del distintivoSi se selecciona, se incluye una columna para el nombre del distintivo en el panel de encabezado.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Mostrar]**
avatarSi está activado, la imagen de avatar del miembro se incluye en el panel de control, junto al vínculo de nombre de su perfil de miembro.

   El valor predeterminado no está seleccionado.

### Función Página {#page-function}

La función de página agrega una página en blanco al sitio de la comunidad que está conectada a las características del sitio de la comunidad: inicio de sesión, menú, notificaciones, mensajería, tema y promoción de la marca. El contenido se puede añadir a la página mediante el [modo de creación de AEM estándar](../../help/sites-authoring/editing-content.md).

Cuando se agrega a una plantilla, la única configuración es para [Configuración del título y la dirección URL](#title-and-url-settings).

### Función Preguntas y respuestas {#qna-function}

La función QnA es una página con un [componente QnA](working-with-qna.md) configurado para etiquetado, cargas de archivos, seguimiento, miembros para autoedición, votación y moderación.

Cuando se agrega a una plantilla, la configuración permite restricciones a miembros con privilegios:

![chlimage_1-389](assets/chlimage_1-389.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
FijarSi está activado, el foro permite que las respuestas de los temas se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro QnA solo permitirá que los miembros privilegiados publiquen preguntas permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está seleccionado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se selecciona, el foro QnA incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas mediante subprocesosSi no se marca, el foro QnA permitirá comentarios (respuestas) a una pregunta publicada, pero no se permiten respuestas a las respuestas. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea puede identificarse como contenido [ ](featured.md)destacado. El valor predeterminado está marcado.

## Crear función de la comunidad {#create-community-function}

Para crear una función de comunidad, seleccione el icono `Create Community Function` situado en la parte superior de la consola Funciones de comunidad . Se pueden crear varias funciones basadas en el mismo modelo de AEM y luego personalizarlas de forma exclusiva abriendo en modo de edición de autor.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nombre de función de la comunidad {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

En el panel Nombre de función de la comunidad, se configuran un nombre, una descripción y si la función está habilitada o deshabilitada:

* **[!UICONTROL Nombre de función de la comunidad]**
El nombre de función que se utiliza para la visualización y el almacenamiento

* **[!UICONTROL Descripción de la función de la comunidad]**
Descripción de la función de visualización

* **[!UICONTROL Interruptor de alternancia deshabilitado/]**
habilitado que controla si se puede hacer referencia a la función

### Modelo AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

En el panel `AEM Blueprint`, es posible seleccionar el modelo que es la implementación subyacente de la función de la comunidad.

La función de comunidad es un minisitio compuesto por una o más páginas, precableado para su inclusión en un sitio de la comunidad, que incluye: inicio de sesión, perfiles de usuario, notificaciones, mensajes, menú del sitio, búsqueda, tema y funciones de marca. Una vez creada la función, es posible [abrir la función](#open-community-function) en modo de edición de autor y personalizar la configuración de la página o del componente.

Dado que la función de comunidad se implementa como una [Live Copy](../../help/sites-administering/msm.md#live-copies) de un [modelo](../../help/sites-administering/msm-livecopy.md#creatingablueprint), es posible implementar los cambios realizados en una función que afecta a todas las páginas de sitio de la comunidad creadas a partir de la [plantilla de sitio de la comunidad](sites.md) o la [plantilla de grupo de la comunidad](tools-groups.md) que incluye la función. También es posible desasociar una página de su modelo principal para realizar modificaciones en el nivel de página.

Consulte también [Multi Site Manager](../../help/sites-administering/msm.md).

### Miniatura    {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

En el panel Miniatura, se puede cargar una imagen para mostrarla en la [consola Funciones de la comunidad](#community-functions-console).

## Abrir función de la comunidad {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Seleccione el icono `Open Community Function` para entrar al modo de edición de autor para crear el contenido de la página y modificar la configuración de los componentes de la función.

### Configurar componentes {#configuring-components}

Una función de comunidad se implementa como Live Copy de un modelo de AEM, cuyos detalles se documentan en [Multi Site Manager](../../help/sites-administering/msm.md).

Es posible no solo crear contenido de página, sino también configurar componentes.

Si configura un componente en una página de un sitio de comunidad creado, puede ser necesario cancelar [herencia](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) para configurar el componente. La herencia debe restablecerse cuando se complete la configuración.

Para obtener más información sobre la configuración, visite [Communities Components](author-communities.md) para autores.

## Editar función de la comunidad {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Seleccione el icono `Edit Community Function` para editar las propiedades de la función utilizando los mismos paneles que [crear una función de comunidad](#create-community-function), incluida la activación o desactivación de la función.
