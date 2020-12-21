---
title: Funciones de comunidad
seo-title: Funciones de comunidad
description: Obtenga información sobre cómo acceder a la consola Funciones de comunidad
seo-description: Obtenga información sobre cómo acceder a la consola Funciones de comunidad
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 2%

---


# Funciones de comunidad {#community-functions}

El tipo de características que se esperan de una experiencia de comunidad son bien conocidas. Las funciones de la comunidad están disponibles como funciones de la comunidad. Fundamentalmente, son una o más páginas preprogramadas para implementar una función de comunidad que requiere más que simplemente agregar un componente a una página en modo de autor. Son los componentes básicos utilizados para definir la estructura de una [plantilla de sitio de comunidad](sites.md) desde la cual se [crean los sitios de comunidad](sites-console.md).

Una vez creado un sitio de comunidad, se puede agregar contenido a las páginas resultantes mediante el modo de creación estándar [AEM](../../help/sites-authoring/editing-content.md).

Hay varias funciones de comunidad disponibles de inmediato, como se ve en la consola de funciones de comunidad. En futuras versiones se ofrecerán más funciones de la comunidad y también se podrán crear funciones personalizadas.

>[!NOTE]
>
>Las consolas para la creación de [sitios de comunidad](sites-console.md), [plantillas de sitio de comunidad](sites.md), [plantillas de grupo de comunidad](tools-groups.md) y [funciones de comunidad](functions.md) sólo se pueden usar en el entorno de creación.

## Consola de funciones de comunidad {#community-functions-console}

En el entorno de creación, para llegar a la consola de funciones de comunidad

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Funciones de la comunidad]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Funciones precompiladas {#pre-built-functions}

A continuación se ofrece una breve descripción de las funciones que se ofrecen con AEM Communities. Cada función está compuesta de una o más páginas AEM que contienen componentes de Communities conectados en una función que se incorpora fácilmente a una [plantilla de sitio de comunidad](sites.md).

Una plantilla de sitio de comunidad proporciona la estructura de un sitio de comunidad, incluyendo inicio de sesión, perfiles de usuario, notificaciones, mensajes, menú del sitio, búsqueda, tema y características de marca.

### Configuración de título y dirección URL {#title-and-url-settings}

**** Título y  **** URLson propiedades comunes a todas las funciones de la comunidad.

Cuando se agrega una función de comunidad a una plantilla de sitio de comunidad o cuando [modifica](sites-console.md#modifying-site-properties) la estructura de un sitio de comunidad, se abre el cuadro de diálogo de la función para que se puedan configurar el Título y la dirección URL.

#### Detalles de la función de configuración {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Título]**
(
*requerido*) Texto que aparece en el menú de características del sitio

* **[!UICONTROL URL]**
 (*requerido*) El nombre utilizado para generar el URI. El nombre debe cumplir las [convenciones de nombres](../../help/sites-developing/naming-conventions.md) impuestas por AEM y JCR.

Por ejemplo, si utiliza el sitio creado a partir del tutorial [Introducción](getting-started.md), si

* Título = Página Web
* URL = página

A continuación, la dirección URL de la página es http://local_host:4503/content/sites/engage/en/page.html y el vínculo de menú de la página aparece como:

![chlimage_1-381](assets/chlimage_1-381.png)

### Función Secuencia de actividades {#activity-stream-function}

La función de flujo de actividad es una página con un [componente Flujos de Actividad](activities.md) con todas las vistas seleccionadas (todas las actividades, actividades de usuario y siguientes). Consulte también [Actividad Stream Essentials](essentials-activities.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo:

#### Detalles de la función de configuración {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Mostrar la]**
vista &quot;Mis Actividades&quot; Si está activada, la página Actividades incluirá una ficha que filtros actividades basadas en las generadas dentro de la comunidad por el miembro actual. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar la]**
vista &quot;Todas las Actividades&quot; Si está activada, la página Actividades incluirá una ficha que incluye todas las actividades generadas dentro de la comunidad a la que tiene acceso el miembro actual. El valor predeterminado está marcado.

* **[!UICONTROL Mostrar la]**
vista &quot;Fuente de noticias&quot; Si está activada, la página Actividades incluirá una ficha que filtros actividades basadas en las que sigue el miembro actual. El valor predeterminado está marcado.

### Función Asignaciones {#assignments-function}

La función de asignaciones es la función básica que define un [sitio de comunidad para la habilitación](overview.md#enablement-community). Permite asignar recursos de habilitación a los miembros de la comunidad. Consulte también [Assignments Essentials](essentials-assignments.md) para desarrolladores.

Esta función está disponible como una función del complemento [de habilitación](enablement.md). El complemento de habilitación requiere licencias adicionales para su uso en un entorno de producción.

Cuando se agrega a una plantilla, la única configuración es para [Configuración de título y URL](#title-and-url-settings).

### Función Blog {#blog-function}

La función de blog es una página con un [componente de blog](blog-feature.md) configurado para el etiquetado, la carga de archivos, el seguimiento y los miembros para la autoedición, la votación y la moderación. Consulte también [Blog Essentials](blog-developer-basics.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo:

![chlimage_1-383](assets/chlimage_1-383.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el blog solo permitirá que los miembros privilegiados creen artículos permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden crear. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se activa, el blog incluirá la capacidad de los miembros para cargar archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por subprocesosSi no se selecciona, el blog permitirá respuestas (comentarios) a un artículo, pero no se permiten las respuestas a los comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea se puede identificar como contenido [ de ](featured.md)funciones. El valor predeterminado está marcado.

### Función Calendario {#calendar-function}

La función de calendario es una página con un [componente de calendario](calendar.md) configurado para permitir el etiquetado. Consulte también [Calendar Essentials](calendar-basics-for-developers.md) para desarrolladores.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo:

![chlimage_1-384](assets/chlimage_1-384.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
fijaciónSi se selecciona, el foro permitirá que las respuestas al tema se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el blog solo permitirá que los miembros privilegiados creen artículos permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden crear. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se activa, el blog incluirá la capacidad de los miembros para cargar archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por subprocesosSi no se selecciona, el blog permitirá respuestas (comentarios) a un artículo, pero no se permiten las respuestas a los comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea se puede identificar como contenido [ de ](featured.md)funciones. El valor predeterminado está marcado.

### Función Catálogo {#catalog-function}

La función de catálogo permite que los miembros de [comunidad de habilitación](overview.md#enablement-community) exploren los recursos de habilitación que no están asignados a ellos. Consulte [Etiquetado de recursos de habilitación](tag-resources.md) y [Catalog Essentials](catalog-developer-essentials.md) para desarrolladores.

Todos los recursos de habilitación y las rutas de aprendizaje del sitio de la comunidad se mostrarán en todos los catálogos si su propiedad, ` [Show in Catalog](resources.md)`, se establece en true. Para incluir explícitamente recursos y rutas de aprendizaje, es necesario aplicar un [prefiltro](catalog-developer-essentials.md#pre-filters) al catálogo.

Cuando se agrega a una plantilla, la configuración permite especificar las Áreas de nombres de etiquetas utilizadas para configurar el filtro de etiquetas presentado en los visitantes del sitio:

![catalogfunc](assets/catalogfunc.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Seleccionar todos los espacios de nombres]**

   * Las Áreas de nombres de etiquetas seleccionadas definen las etiquetas que pueden seleccionar los visitantes para filtrar la lista de los recursos de activación enumerados en el catálogo.
   * Si se selecciona, están disponibles todas las Áreas de nombres de etiquetas permitidas para el sitio de la comunidad.
   * Si no se selecciona, es posible seleccionar una o varias Áreas de nombres permitidas para el sitio de la comunidad.
   * El valor predeterminado está marcado.

### Función de contenido destacado {#featured-content-function}

La función de contenido destacado es una página con un [componente de contenido destacado](featured.md) configurado para permitir que se agreguen y eliminen comentarios.

Se puede permitir o no admitir la capacidad de presentar contenido por componente (consulte [Función de blog](#blog-function), [Función de calendario](#calendar-function), [Función de foro](#forum-function), [Función de ideación](#ideation-function) y [Función de QnA](#qna-function)).

Cuando se agrega a una plantilla, la única configuración es para [Configuración de título y URL](#title-and-url-settings).

### Función Biblioteca del archivo {#file-library-function}

La función de biblioteca de archivos es una página con un [componente de biblioteca de archivos](file-library.md) configurado para permitir que se agreguen y eliminen comentarios.

Cuando se agrega a una plantilla, la única configuración es para [Configuración de título y URL](#title-and-url-settings).

### Función Foro {#forum-function}

La función de foro es una página con un [componente de foro](forum.md) configurado para el etiquetado, la carga de archivos, el seguimiento de miembros para la autoedición, la votación y la moderación.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo:

#### Detalles de la función de configuración {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
fijaciónSi se selecciona, el foro permitirá que las respuestas al tema se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas al permitir la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se activa, el foro incluirá la capacidad de los miembros para cargar archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por subprocesosSi no se selecciona, el foro permitirá comentarios sobre un tema, pero no se permiten las respuestas a esos comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea se puede identificar como contenido [ de ](featured.md)funciones. El valor predeterminado está marcado.

### Función Grupos {#groups-function}

>[!CAUTION]
>
>La función de grupos debe *no* ser la *primera ni la única* función en la estructura de un sitio o en una plantilla de sitio de comunidad.
>
>Cualquier otra función, como la [función de página](#page-function), debe incluirse y enumerarse primero.

La función de grupos permite a los miembros de la comunidad crear subcomunidades dentro del sitio de la comunidad en el entorno de publicación.

Según la [configuración](sites-console.md#groupmanagement) cuando la función Grupos se incluya en una [plantilla de sitio de comunidad](sites.md), los grupos pueden ser públicos o privados y se pueden configurar una o más plantillas de grupo de comunidad para proporcionar una selección de plantillas cuando se cree realmente el grupo de comunidad (por ejemplo, desde el entorno de publicación). Una [plantilla de grupo de comunidad](tools-groups.md) especifica qué características de comunidades se crean para las páginas de grupo, como los foros y los calendarios.

Cuando se crea un grupo de comunidad, se crea dinámicamente un grupo de miembros para el nuevo grupo, al que se pueden asignar o unir miembros. Para obtener más información, consulte [Administración de usuarios y grupos de usuarios](users.md).

A partir del paquete de funciones 1](deploy-communities.md#latestfeaturepack) de Communities [, los grupos de comunidades se crean en el entorno de creación mediante la consola [Grupos de sitios de comunidades](groups.md) y se pueden crear en el entorno de publicación cuando está habilitada.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo:

![chlimage_1-386](assets/chlimage_1-386.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Seleccionar]**
plantillas de grupoMenú desplegable que permite seleccionar una o varias plantillas de grupo habilitadas, de las que puede elegir el futuro creador de un nuevo grupo de comunidad (en el entorno de publicación).

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas al permitir la selección de un grupo [ de seguridad de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
creación de publicaciónSi está activada, los miembros autorizados de la comunidad pueden crear un grupo en el entorno de publicación. Si no se selecciona, los nuevos grupos (subcomunidades) solo se pueden crear en el entorno de creación desde la consola Grupos de sitios de comunidades.

   El valor predeterminado es `checked`.

### Función ideación {#ideation-function}

La función de ideación es una página con un [componente de ideación](ideation-feature.md).

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo, que especifica los nombres predeterminados de Título y URL, así como la configuración de visualización predeterminada de la plantilla:

![chlimage_1-387](assets/chlimage_1-387.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro solo permitirá que los miembros privilegiados publiquen temas al permitir la selección de un grupo [ de seguridad de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi está activada, la idea incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas mediante subprocesosSi no se selecciona, la idea permitirá respuestas (comentarios) a un tema, pero no se permiten respuestas a comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea se puede identificar como contenido [ de ](featured.md)funciones. El valor predeterminado está marcado.

### Función de la tabla de clasificación {#leaderboard-function}

La función de tabla de clasificación es una página con un [componente de tabla de clasificación](enabling-leaderboard.md).

**NOTA**: el componente Mesa de liderazgo necesitará una configuración adicional  ** después de crear el sitio de la comunidad a partir de una plantilla de comunidad que incluya la función Mesa de liderazgo. Será necesario especificar las [reglas](enabling-leaderboard.md#rules-tab) del componente Leaderboard, que dependen de la configuración de [puntuación y distintivos](implementing-scoring.md) para el sitio de la comunidad.

Cuando se agrega a una plantilla, se abre el siguiente cuadro de diálogo, que especifica los nombres predeterminados de Título y URL, así como la configuración de visualización predeterminada de la plantilla:

![chlimage_1-388](assets/chlimage_1-388.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Mostrar]**
distintivoSi se selecciona, se incluye una columna para los iconos de distintivo en la tabla de clasificación.

   El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar]**
nombre del distintivoSi se selecciona, se incluye una columna para el nombre del distintivo en la tabla de clasificación.

   El valor predeterminado no está marcado.

* **[!UICONTROL Mostrar]**
avatarSi se selecciona, la imagen de avatar del miembro se incluye en el panel de control, junto al vínculo de nombre del perfil del miembro.

   El valor predeterminado no está marcado.

### Función Página {#page-function}

La función de página agrega una página en blanco al sitio de la comunidad que está conectada a las características del sitio de la comunidad: inicio de sesión, menú, notificaciones, mensajes, temas y marca. Se puede agregar contenido a la página mediante el [modo de creación de AEM estándar](../../help/sites-authoring/editing-content.md).

Cuando se agrega a una plantilla, la única configuración es para [Configuración de título y URL](#title-and-url-settings).

### Función Preguntas y respuestas {#qna-function}

La función QnA es una página con un [componente QnA](working-with-qna.md) configurado para el etiquetado, la carga de archivos, el seguimiento y los miembros para la autoedición, la votación y la moderación.

Cuando se agrega a una plantilla, la configuración permite la restricción a los miembros privilegiados:

![chlimage_1-389](assets/chlimage_1-389.png)

* Consulte [Configuración de título y dirección URL](#title-and-url-settings)
* **[!UICONTROL Permitir]**
fijaciónSi se selecciona, el foro permitirá que las respuestas al tema se fijen al principio de la lista de comentarios. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
miembros privilegiadosSi se selecciona, el foro QnA solo permitirá que los miembros privilegiados publiquen preguntas, permitiendo la selección de un grupo [ de miembros ](users.md#privileged-members-group)privilegiados. Si no se selecciona, todos los miembros de la comunidad pueden publicar. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir]**
cargas de archivosSi se activa, el foro de control de calidad incluirá la posibilidad de que los miembros carguen archivos. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
respuestas por hiloSi no se selecciona, el foro QnA permitirá comentarios (respuestas) a una pregunta publicada, pero no se permiten respuestas a las respuestas. El valor predeterminado está marcado.

* **[!UICONTROL Permitir]**
contenido destacadoSi se selecciona, la idea se puede identificar como contenido [ de ](featured.md)funciones. El valor predeterminado está marcado.

## Crear función de la comunidad {#create-community-function}

La capacidad de crear una función de comunidad se alcanza seleccionando el icono `Create Community Function` situado en la parte superior de la consola de funciones de comunidad. Se pueden crear varias funciones basadas en el mismo modelo de AEM y, a continuación, personalizarlas de forma única abriéndolas en el modo de edición de autor.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nombre de función de la comunidad {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

En el panel Nombre de función de comunidad, se configuran un nombre, una descripción y si la función está habilitada o deshabilitada:

* **[!UICONTROL Nombre de la función de la comunidad]**
Nombre de la función que se utiliza para la visualización y el almacenamiento

* **[!UICONTROL Función de la comunidad]**
DescripciónDescripción de la función para visualización

* **[!UICONTROL Deshabilitado/]**
HabilitadoUn conmutador que controla si se puede hacer referencia a la función

### Modelo AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

En el panel `AEM Blueprint`, es posible seleccionar el modelo que es la implementación subyacente de la función de comunidad.

La función de comunidad es un minisitio compuesto de una o más páginas, precableado para su inclusión en un sitio de la comunidad, incluyendo inicio de sesión, perfiles de usuario, notificaciones, mensajes, menú del sitio, búsqueda, tema y características de marca. Una vez creada la función, es posible [abrir la función](#open-community-function) en el modo de edición del autor y personalizar la configuración de la página o del componente.

Dado que la función de comunidad se implementa como [Live Copy](../../help/sites-administering/msm.md#live-copies) de un [modelo](../../help/sites-administering/msm-livecopy.md#creatingablueprint), es posible implementar los cambios realizados en una función que afecta a todas las páginas del sitio de comunidad creadas a partir de la [plantilla del sitio de comunidad](sites.md) o [plantilla de grupo de comunidad](tools-groups.md) que incluye la función. También es posible desasociar una página de su modelo principal para realizar modificaciones a nivel de página.

Consulte también [Administrador de múltiples sitios](../../help/sites-administering/msm.md).

### Miniatura    {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

En el panel Miniatura, se puede cargar una imagen para mostrarla en la [consola de funciones de comunidad](#community-functions-console).

## Abrir función de la comunidad {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Seleccione el icono `Open Community Function` para acceder al modo de edición del autor y crear el contenido de la página y modificar la configuración de los componentes de la función.

### Configurar componentes {#configuring-components}

Una función de comunidad se implementa como Live Copy de un modelo de AEM, cuyos detalles se documentan en [Multi Site Manager](../../help/sites-administering/msm.md).

Es posible no sólo crear contenido de página, sino también configurar componentes.

Si configura un componente en una página de un sitio de comunidad creado, puede que sea necesario cancelar [herencia](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) para configurar el componente. La herencia debe restablecerse cuando se complete la configuración.

Para obtener más información sobre la configuración, visite [Communities Components](author-communities.md) para autores.

## Editar función de la comunidad {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Seleccione el icono `Edit Community Function` para editar las propiedades de la función utilizando los mismos paneles que [para crear una función de comunidad](#create-community-function), incluyendo habilitar o deshabilitar la función.
