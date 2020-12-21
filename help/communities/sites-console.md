---
title: Consola Sitios de comunidades
seo-title: Consola Sitios de comunidades
description: Cómo acceder a la consola Sitios de comunidades
seo-description: Cómo acceder a la consola Sitios de comunidades
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
translation-type: tm+mt
source-git-commit: f4cdd3d5020b917676fe8715d4e21e98f3a096b4
workflow-type: tm+mt
source-wordcount: '3241'
ht-degree: 3%

---


# Consola Sitios de comunidades {#communities-sites-console}

La consola Sitios de comunidades proporciona acceso a:

* Creación de sitios
* Edición del sitio
* Administración de sitios
* [Creación y edición de grupos](groups.md)  anidados (subcomunidades)

Consulte [Introducción a AEM Communities](getting-started.md) para conocer la rapidez con que se puede crear un sitio de comunidad en el entorno de creación, así como cómo crear grupos de comunidad a partir de los entornos de creación y publicación.

>[!NOTE]
>
>Los menús principales de Comunidades para la creación de [sitios de comunidad](sites-console.md), [plantillas de sitio de comunidad](sites.md), [plantillas de grupo de comunidad](tools-groups.md) y [funciones de comunidad](functions.md) sólo se pueden utilizar en el entorno de creación.

## Requisitos previos {#prerequisites}

Antes de crear un sitio de comunidad, es *necesario* para:

* Asegúrese de que se estén ejecutando una o varias instancias de publicación
* Habilite el [servicio de túnel](deploy-communities.md#tunnel-service-on-author) para administrar miembros y grupos de miembros
* Identifique el [publicador principal](deploy-communities.md#primary-publisher)
* [Configure ](deploy-communities.md#replication-agents-on-author) la replicación cuando el puerto de publicador principal no sea el predeterminado (4503)

La práctica recomendada para garantizar que el sitio esté preparado para admitir muchas funciones es realizar los siguientes pasos:

* Instale el [paquete de funciones más reciente](deploy-communities.md#latestfeaturepack)
* Habilitar [Adobe Analytics](analytics.md) para AEM Communities
* Configurar [correo electrónico](email.md)
* Identifique [Administradores de la comunidad](users.md#creating-community-members)
* [Habilitar el ](social-login.md#adobe-granite-oauth-authentication-handler) controlador OAuth para el inicio de sesión social

## Acceso a la consola Sitios de comunidades {#accessing-communities-sites-console}

En el entorno de creación, para acceder a la consola Sitios de comunidades:

* Desde la navegación global: **[!UICONTROL Comunidades > Sitios]**

La consola Sitios de comunidades muestra todos los sitios de comunidad existentes. Desde esta consola, los sitios de comunidad pueden crearse, editarse, administrarse y eliminarse.

Para crear un nuevo sitio de comunidad, seleccione el icono **Crear**.

Para acceder a un sitio de comunidad existente, con el fin de crear, modificar, publicar, exportar o agregar un grupo anidado, seleccione el icono de carpeta del sitio.

Por ejemplo, la siguiente imagen muestra la consola principal Sitios de comunidades, que muestra las carpetas de dos sitios de comunidad: [habilitar](getting-started-enablement.md) y [comprometer](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## Creación del sitio {#site-creation}

La consola de creación del sitio proporciona un enfoque paso a paso para ensamblar las características del sitio en base a una [plantilla del sitio de comunidad](sites.md) y a la configuración seleccionadas.

Cada sitio creado incluye una función de inicio de sesión, ya que los visitantes del sitio deben iniciar sesión antes de poder publicar contenido, enviar mensajes o participar en un grupo. Otras funciones incluidas son los perfiles de usuario, los mensajes, las notificaciones, el menú del sitio, la búsqueda, la temática y la marca.

El proceso se inicia seleccionando el botón `Create` ubicado en la parte superior de la consola Sitios de comunidades.

El proceso de creación consiste en una serie de pasos presentados como paneles que contienen un conjunto de características que se deben configurar (presentados como subpaneles). Es posible avanzar al paso **Siguiente** o **Atrás** al paso anterior antes de comprometer el sitio en el paso final.

### Paso 1: Plantilla de sitio {#step-site-template}

![newsitetemplate](assets/newsitetemplate.png)

En el panel Plantilla del sitio, se especifican el título, la descripción, la raíz del sitio, el idioma base, el nombre y la plantilla del sitio:

* **[!UICONTROL Título]** del sitio de la comunidad: Título que se muestra para el sitio.

   El título aparece en el sitio publicado, así como en la interfaz de usuario del administrador del sitio.

* **[!UICONTROL Descripción]** del sitio de la comunidad: Descripción del sitio.

   La descripción no aparece en el sitio publicado.

* **[!UICONTROL Raíz]** del sitio de la comunidad: La ruta raíz del sitio.

   La raíz predeterminada es `/content/sites`, pero la raíz puede moverse a cualquier ubicación dentro del sitio Web.

* **[!UICONTROL Idioma]** base del sitio de la comunidad: (dejar intacto para un solo idioma: Inglés) utilice el menú desplegable para elegir uno  *o* varios idiomas disponibles: alemán, italiano, francés, japonés, español, portugués (Brasil), chino (tradicional) y chino (simplificado). Se creará un sitio de comunidad para cada idioma agregado y existirá dentro de la misma carpeta de sitio siguiendo las optimizaciones descritas en [Traducir contenido para sitios multilingües](../../help/sites-administering/translation.md). La página raíz de cada sitio contendrá una página secundaria con el nombre del código de idioma de uno de los idiomas seleccionados, como &quot;en&quot; para inglés o &quot;fr&quot; para francés.

* **[!UICONTROL Nombre]** del sitio de la comunidad: El nombre de la página raíz del sitio que aparece en la dirección URL

   * Compruebe el doble del nombre, ya que no es fácil cambiarlo después de crear el sitio
   * La dirección URL base ( `https://*server:port/site root/site name*)` se mostrará debajo de `Community Site Name`
   * Para una dirección URL válida, anexe un código de idioma base + &quot;.html&quot;

      *Por ejemplo*, `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL Community Site]** Templatemenu: Utilice el menú desplegable para elegir una plantilla [ de sitio de ](tools.md)comunidad disponible.

Seleccione **[!UICONTROL Siguiente]**

### Paso 2: Diseño {#step-design}

El panel Diseño contiene dos subpaneles para seleccionar el tema y la pancarta de marca:

#### TEMA DEL SITIO COMUNITARIO {#community-site-theme}

![sitetopic-1](assets/sitetheme-1.png)

El módulo utiliza [Bootstrap de Twitter](https://twitterbootstrap.org/) para proporcionar un diseño flexible y adaptable al sitio. Se puede seleccionar una de las muchas temáticas de Bootstrap precargadas para aplicar estilo a la plantilla de sitio de comunidad seleccionada o se puede cargar un tema de Bootstrap.

Cuando se selecciona, el tema se superpone con una marca de verificación azul opaca.

Después de publicar el sitio de comunidad, es posible [editar las propiedades](#modifying-site-properties) y seleccionar un tema diferente.

#### MARCA DEL SITIO COMUNITARIO {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

La marca del sitio de la comunidad es una imagen que se muestra como encabezado en la parte superior de cada página.

El tamaño de la imagen debe ser tan grande como la visualización esperada de la página en el navegador y 120 píxeles de altura.

Al crear o seleccionar una imagen, tenga en cuenta:

* La altura de la imagen se recortará a 120 píxeles medidos desde el borde superior de la imagen
* La imagen se fija en el borde izquierdo de la ventana del navegador
* No hay cambio de tamaño de la imagen, de modo que cuando la anchura de la imagen es...

   * Menor que el ancho del navegador, la imagen se repetirá horizontalmente
   * Buena al ancho del explorador, la imagen parece que se recorta

Seleccione **[!UICONTROL Siguiente]**.

### Paso 3: Configuración {#step-settings}

El panel Configuración contiene varios subpaneles que presentan las funciones que se deben configurar antes de pasar al último paso para crear el sitio.

* [ADMINISTRACIÓN DE USUARIOS](#user-management)
* [ETIQUETADO](#tagging)
* [FUNCIONES](#roles)
* [MODERACIÓN](#moderation)
* [ANALYTICS](#analytics)
* [TRADUCCIÓN](#translation)
* [HABILITACIÓN](#enablement)

>[!NOTE]
>
>**Habilitar servicio de túnel**
>
>Varios subpaneles de Configuración permiten que la asignación de un miembro de confianza modere UGC, administre grupos o se convierta en contactos para habilitar recursos en el entorno de publicación.
>
>La convención es que los [usuarios y grupos de usuarios](users.md) (miembros y grupos de miembros) del lado de publicación no se dupliquen en el entorno de creación.
>
>Por lo tanto, al crear el sitio de comunidad en el entorno de creación y asignar miembros de confianza a varias funciones, es necesario recuperar datos de miembros del entorno de publicación.
>
>Esto se logra habilitando el ` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`para el entorno de creación.

#### ADMINISTRACIÓN DE USUARIOS {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>Se recomienda que [habilite los sitios de la comunidad](overview.md#enablement-community) sean privados (comuníquese con el representante de cuentas para obtener más información).
>
>Un sitio de la comunidad es privado cuando se deniega el acceso a los visitantes anónimos del sitio, es posible que no se registre por sí mismo y que no utilice el inicio de sesión en redes sociales.

* **[!UICONTROL Permitir el registro de usuarios]**

   Si se selecciona, los visitantes del sitio pueden convertirse en miembros de la comunidad mediante el registro propio.

   Si no se selecciona, el sitio de la comunidad está *restringido* y los visitantes del sitio deben asignarse al grupo de miembros del sitio de la comunidad, realizar una solicitud o recibir una invitación por correo electrónico. Si no se selecciona, no se debe permitir el acceso anónimo.

   Desmarque la casilla de un *sitio de comunidad privado*. El valor predeterminado está marcado.

* **[!UICONTROL Permitir acceso anónimo]**

   Si se selecciona, el sitio de la comunidad está *abierto* y cualquier visitante del sitio puede acceder al sitio.

   Si no está activada, solo los miembros con sesión iniciada pueden acceder al sitio.

   Desmarque la casilla de un *sitio de comunidad privado*. El valor predeterminado está marcado.

* **[!UICONTROL Permitir mensajes]**

   Si se selecciona, los miembros pueden enviarse mensajes entre sí y al grupo dentro del sitio de la comunidad.

   Si no se selecciona, los mensajes no se configuran para la comunidad.

   El valor predeterminado no está marcado.

* **[!UICONTROL Permitir inicios de sesión de redes sociales: Facebook]**

   Si se selecciona, permita que los visitantes del sitio inicien sesión con las credenciales de su cuenta de Facebook. La [configuración de nube de Facebook](social-login.md#create-a-facebook-connect-cloud-service) seleccionada debe configurarse para agregar usuarios al grupo de miembros del sitio de la comunidad una vez que se haya creado el sitio de la comunidad.

   Si no se selecciona, no se muestra ningún inicio de sesión en Facebook.

   No se ha seleccionado un *sitio de comunidad privado*. El valor predeterminado no está marcado.

* **[!UICONTROL Permitir inicios de sesión de redes sociales: Twitter]**

   Si está activada, permita que los visitantes del sitio inicien sesión con las credenciales de su cuenta de Twitter. La [configuración de nube de Twitter](social-login.md#create-a-twitter-connect-cloud-service) seleccionada debe configurarse para agregar usuarios al grupo de miembros del sitio de la comunidad una vez que se haya creado el sitio de la comunidad.

   Si no se selecciona, no se muestra ningún inicio de sesión en Twitter.

   No se ha seleccionado un *sitio de comunidad privado*. El valor predeterminado no está marcado.

>[!NOTE]
>
>**[!UICONTROL Permitir inicios de sesión sociales]**
>
>Aunque las configuraciones de Facebook y Twitter de muestra pueden existir y ser seleccionables, para un [entorno de producción](../../help/sites-administering/production-ready.md), es necesario crear aplicaciones personalizadas de Facebook y Twitter. Consulte [Inicio de sesión social con Facebook y Twitter](social-login.md).

#### ETIQUETADO {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

Las etiquetas que se pueden aplicar al contenido de la comunidad se controlan seleccionando Áreas de nombres de etiquetas previamente definidas mediante la [Consola de etiquetado](../../help/sites-administering/tags.md#tagging-console).

Además, la selección de Áreas de nombres de etiquetas para el sitio de la comunidad limita la selección presentada al definir catálogos y recursos. Consulte [Etiquetado de recursos de habilitación](tag-resources.md) para obtener información importante.

* Cuadro de búsqueda de texto: Escritura de inicios para identificar las etiquetas permitidas para su uso en el sitio

#### ROLES {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

Las [funciones de los miembros de la comunidad](users.md) se asignan con esta configuración.

Encontrar miembros de la comunidad es fácil mediante la búsqueda por tipo.

* **[!UICONTROL Administradores de la comunidad]**

   Escritura de inicios para seleccionar uno o más miembros de la comunidad o grupos miembros que pueden administrar miembros de la comunidad y grupos miembros.

* **[!UICONTROL Moderadores de la comunidad]**

   Escritura de inicios para seleccionar uno o varios miembros de la comunidad o grupos de miembros en los que se debe confiar como moderadores del contenido generado por el usuario.

* **[!UICONTROL Miembros privilegiados de la comunidad]**

   Escritura de inicios para seleccionar uno o más miembros de la comunidad o grupos de miembros a los que se dará la posibilidad de crear contenido nuevo cuando `Allow Privileged Member` se haya seleccionado para una [función de comunidad](functions.md).

#### MODERACIÓN {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

Esta configuración controla la configuración global para moderar el contenido generado por el usuario (UGC). Los componentes individuales tienen una configuración adicional para controlar la moderación.

* **[!UICONTROL Contenido con moderación previa]**

   Si se selecciona, el contenido de la comunidad publicado no aparecerá hasta que lo apruebe un moderador. El valor predeterminado no está marcado. Para obtener más información, consulte [Moderación del contenido de la comunidad](moderate-ugc.md#premoderation).

* **[!UICONTROL Umbral de indicación antes de ocultar el contenido]**

   Si es bueno que no sea 0, el número de veces que se debe marcar un tema o publicación antes de ocultarlo en la vista pública. Si se establece en -1, el tema o anuncio marcado nunca se oculta en la vista pública. El valor predeterminado es 5.

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL Activar Analytics]**

   Solo está disponible cuando Adobe Analytics se [configuró](analytics.md) para las funciones de Communities.

   El valor predeterminado no está marcado. Cuando se selecciona, aparece un menú de selección adicional:

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL Referencia de la estructura de configuración de la nube]**

   En el menú desplegable, seleccione el marco de servicios en la nube de Analytics configurado para este sitio de comunidad.

   `Communities`es el ejemplo de marco de  [Analytics Configuration for Communities ](analytics.md#aem-analytics-framework-configuration) Featuresdocumentation.

#### TRADUCCIÓN {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL Permitir]**
traducción automáticaCuando está activada (la opción predeterminada está desactivada), la traducción automática está activada para UGC dentro del sitio. Esto no afecta a ningún otro contenido, como el contenido de la página, aunque el sitio esté configurado como un sitio multilingüe. Consulte [Traducción de contenido generado por el usuario](translate-ugc.md) para obtener información sobre cómo configurar un servicio de traducción con licencia para AEM Communities. Consulte [Traducción de contenido para sitios multilingües](../../help/sites-administering/translation.md) para obtener una descripción general completa.

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL Activar la traducción automática para los idiomas seleccionados]**

   Los idiomas habilitados para la traducción automática se establecen de forma predeterminada en la configuración del sistema especificada por la configuración de la integración de traducción [](translate-ugc.md#translation-integration-configuration). Esta configuración predeterminada se puede anular para este sitio eliminando los valores predeterminados o seleccionando otros idiomas en el menú desplegable.

* **[!UICONTROL Seleccione un proveedor de traducciones]**

   De forma predeterminada, el proveedor de servicio es un servicio de prueba que utiliza `microsoft`solo para demostración. Si no hay ningún proveedor de servicio de traducción con licencia, **Permitir traducción automática** debe estar desactivada.

* **[!UICONTROL Elegir almacén compartido global]**

   Para un sitio web con varias copias de idiomas, una tienda compartida global proporciona un único subproceso de conversación, visible desde cada copia de idioma. Esto se logra seleccionando uno de los idiomas incluidos como copia del idioma. El valor predeterminado es *No hay almacenamiento compartido global*.

* **[!UICONTROL Elija la configuración del proveedor de traducciones]**

   Elija un [marco de integración de traducción](../../help/sites-administering/tc-tic.md) creado para el proveedor de traducción con licencia.

* **Seleccione las opciones de traducción del sitio de la comunidad**

   * **[!UICONTROL Traducir toda la página]**

      Si se selecciona, todo el contenido generado por usuarios de una página se traduce al idioma base de la página.

      El valor predeterminado es *no seleccionado*.

   * **[!UICONTROL Traducir solo la selección]**

      Si se selecciona, aparece una opción de traducción junto a cada anuncio que permite traducir anuncios individuales al idioma base de la página.

      El valor predeterminado es *seleccionado*.

* **Seleccione las opciones de persistencia**

   * **[!UICONTROL Traducir las contribuciones a petición del usuario y continuar en el futuro]**

      Si se selecciona, el contenido no se traduce hasta que se realiza una solicitud. Una vez traducida, la traducción se almacena en el repositorio.

      El valor predeterminado es *no seleccionado*.

   * **[!UICONTROL No continuar traduciendo]**

      Si se selecciona, las traducciones no se almacenan en el repositorio.

      Si no se selecciona, las traducciones se conservan.

      El valor predeterminado es *no seleccionado*.

* **[!UICONTROL Smart]**
RenderSeleccione uno de los

   * `Always show contributions in the original language` (predeterminada)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### HABILITACIÓN {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

La configuración `ENABLEMENT`se aplica cuando la plantilla de sitio de comunidad elegida incluye la función [asignaciones](functions.md#assignments-function), que está disponible cuando las características de habilitación tienen licencia y [están configuradas](enablement.md). La plantilla de sitio de referencia que incluye la función de asignaciones es `Reference Structured Learning Site Template.`

* **[!UICONTROL Administradores de habilitación]**

   (requerido) Solo los miembros del grupo `Community Enablementmanagers` están disponibles para ser seleccionados para administrar esta comunidad de habilitación. Los administradores de habilitación son responsables de asignar miembros a los recursos. Consulte también [Administración de usuarios y grupos de usuarios](users.md).

* **[!UICONTROL ID de organización de Marketing Cloud]**

   (opcional) El ID de una licencia de [Video Heartbeat Analytics](analytics.md#video-heartbeat-analytics).

Seleccione **[!UICONTROL Siguiente]**.

### Paso 4: Crear sitio de comunidades {#step-create-communities-site}

Si se necesita algún ajuste, utilice el botón **Atrás** para realizarlo.

Una vez que **Create** se selecciona y se inicia, el proceso de creación del sitio no se puede interrumpir.

Una vez creado el sitio:

* No se admite el cambio de la dirección URL (nombre de nodo)
* Los cambios futuros en la plantilla del sitio de la comunidad no afectarán al sitio de la comunidad creado
* La desactivación de la plantilla del sitio de comunidad no afectará al sitio de comunidad creado
* Es posible editar la [ESTRUCTURA](#modify-structure) de un sitio de comunidad modificando sus propiedades

![chlimage_1-458](assets/chlimage_1-458.png)

Cuando se completa el proceso, la carpeta del nuevo sitio se muestra en la consola Sitios de comunidades, desde donde los autores pueden agregar contenido de página o los administradores pueden modificar las propiedades del sitio.

![chlimage_1-459](assets/chlimage_1-459.png)

Para modificar un sitio de comunidad, seleccione su carpeta de proyecto para abrirlo:

![siteactions-2](assets/siteactions-2.png)

Al pasar el ratón por encima de un sitio o tocar una tarjeta del sitio, aparecen iconos que permiten [editar el sitio en modo de autor](#authoring-site-content), [abrir las propiedades del sitio para modificarlo](#modifying-site-properties), [publicar el sitio](#publishing-the-site), [exportar el sitio](#exporting-the-site) y [eliminar el sitio](#deleting-the-site).

## Creación de contenido del sitio {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

El contenido de un sitio puede crearse con las mismas herramientas que cualquier otro sitio web AEM. Para abrir el sitio para la creación, seleccione el icono `Open Site` que aparece al pasar el ratón por el sitio. El sitio se abrirá en una nueva ficha para que la consola Sitios de comunidades permanezca accesible.

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
>
>Si no está familiarizado con AEM, vista la documentación sobre [administración básica](../../help/sites-authoring/basic-handling.md) y una [guía rápida para crear páginas](../../help/sites-authoring/qg-page-authoring.md).

## Modificación de las propiedades del sitio {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

Las propiedades de un sitio existente, especificadas durante el proceso de creación del sitio, se pueden modificar seleccionando el icono `Edit Site`que aparece al pasar el ratón por el sitio.

`Details of the following properties match the descriptions provided in the` [Creación ](#site-creation) del sitio.

![chlimage_1-463](assets/chlimage_1-463.png)

### Modificar básico {#modify-basic}

El panel BASIC permite modificar

* Título del sitio de la comunidad
* Descripción del sitio de la comunidad

No se puede modificar el nombre del sitio de la comunidad.

La elección de una plantilla de sitio de comunidad diferente no afectaría a un sitio de comunidad existente, ya que no queda ninguna conexión entre plantillas y sitios.

En su lugar, se puede modificar la [ESTRUCTURA](#modify-structure) del sitio de la comunidad.

### Modificar estructura {#modify-structure}

El panel ESTRUCTURA permite modificar la estructura creada inicialmente a partir de la plantilla de sitio de comunidad seleccionada. Desde el panel, es posible

* Arrastre y suelte [funciones de comunidad](functions.md) adicionales en la estructura del sitio
* En una instancia de una función de comunidad en la estructura del sitio:

   * **`gear icon`**

      editar la configuración, incluido el título para mostrar y el nombre de URL; último;

      así como [grupos de miembros privilegiados](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      quitar (eliminar) funciones de la estructura del sitio

   * **`grid icon`**

      modifique el orden de las funciones como se muestra en la barra de navegación de nivel superior del sitio

>[!NOTE]
>
>Puede cambiar el orden de todas las funciones en la estructura del sitio, excepto la función en la parte superior. Por lo tanto, no se puede cambiar la página de inicio del sitio de las comunidades.

>[!CAUTION]
>
>Aunque el título de visualización se puede cambiar sin efectos secundarios, no se recomienda editar el nombre de la dirección URL de una función de comunidad que pertenece a un sitio de comunidad.
>
>Por ejemplo, si se cambia el nombre de la URL, no se moverá el UGC existente, lo que tendrá el efecto de &#39;perder&#39; UGC.

>[!CAUTION]
>
>La función de grupos debe *no* ser la *primera ni la única* función de la estructura del sitio.
>
>Cualquier otra función, como la [función de página](functions.md#page-function), debe incluirse y enumerarse primero.

#### Ejemplo: Añadir una función de catálogo en una estructura de sitio de comunidad {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### Modificar diseño {#modify-design}

El panel DISEÑO permite aplicar un nuevo tema:

* [Tema del sitio de la comunidad](#community-site-theme)
* [Marca del sitio de la comunidad](#community-site-branding)
   * Desplácese hasta la parte inferior del panel para cambiar la imagen de marca

### Modificar configuración {#modify-settings}

El panel CONFIGURACIÓN permite acceder a la mayoría de los ajustes de los subpaneles de para el paso 3 de la creación del sitio de la comunidad:

* [Administración de usuarios](#user-management)
* [Etiquetas](#tagging)
* [Moderación](#moderation)
* [Funciones de miembro](#roles)
* [Análisis](#analytics)
* [Traducción](#translation)

### Modificar miniatura {#modify-thumbnail}

El panel MINIATURA permite cargar una imagen para representar el sitio en la consola Sitios de comunidades.

### Modificar habilitación {#modify-enablement}

El panel ACTIVACIÓN permite acceder a la configuración proporcionada durante la creación del sitio de la comunidad.

Consulte la descripción de [ENABLEMENT](#enablement).

## Publicación del sitio {#publishing-the-site}

Una vez creado o modificado un sitio de comunidad, es posible publicar (activar) el sitio seleccionando el icono `Publish Site`, que aparece al pasar el ratón por encima del sitio.

![chlimage_1-465](assets/chlimage_1-465.png)

Habrá una indicación después de que el sitio se haya publicado correctamente.

![chlimage_1-466](assets/chlimage_1-466.png)

### Publicación con grupos anidados {#publishing-with-nested-groups}

Después de publicar un sitio de comunidad, es necesario publicar individualmente cada subcomunidad (grupo anidado) creada mediante la [consola de grupos](groups.md).

## Exportación del sitio {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

Seleccione el icono de exportación, al pasar el ratón por encima del sitio, para crear un paquete del sitio de la comunidad que esté almacenado en [administrador de paquetes](../../help/sites-administering/package-manager.md) y descargado.\
Tenga en cuenta que UGC no se incluye en el paquete del sitio.

## Eliminación del sitio {#deleting-the-site}

![delete-icon-1](assets/deleteicon-1.png)

Para eliminar el sitio de comunidad, seleccione el icono Eliminar sitio que aparece al pasar el ratón sobre el sitio en la Consola de sitio de comunidades. Esta acción elimina todos los elementos asociados con el sitio, como UGC, grupos de usuarios, recursos y registros de bases de datos.

## Grupos de usuarios de la comunidad creados {#created-community-user-groups}

Una vez publicado el nuevo sitio de comunidad, se crean nuevos grupos de miembros (los grupos de usuarios se crean en el entorno de publicación) que tienen los permisos adecuados establecidos para diversas funciones administrativas y de miembros.

El nombre creado para los grupos de miembros incluye el *nombre del sitio* dado al sitio en [Paso 1](#step13asitetemplate) (el nombre que aparece en la dirección URL), así como un identificador único para evitar conflictos con los sitios de la comunidad y los grupos que tienen el mismo nombre del sitio para diferentes raíces del sitio de la comunidad.

Por ejemplo, si el nombre fuera &quot;engagement&quot; para un sitio llamado &quot;Tutorial de introducción&quot;, entonces el grupo de usuarios para moderadores sería:

* Título: Moderadores de participación de la comunidad
* Nombre: community-*engagement-uid*-moderadores

Tenga en cuenta que los miembros asignados a funciones como moderadores o administradores de grupos durante la creación del sitio se asignarán al grupo correspondiente y al grupo de miembros. Estos grupos y asignaciones de miembros se crean al publicar el nuevo sitio.

Para obtener más información, consulte [Administración de usuarios y grupos de usuarios](users.md).

>[!NOTE]
>
>Si [permite el inicio de sesión en Social: Facebook](#user-management) está habilitado, una vez que el grupo de usuarios
>
>* community-*&lt;site-name>*-*&lt;uid>*-members

se crea, el [servicio de nube de Facebook](social-login.md#createafacebookcloudservice) aplicado debe configurarse para agregar usuarios a este grupo.

## Error de configuración para autenticación {#configure-for-authentication-error}

De forma predeterminada, un sitio de comunidad redireccionará a una página de inicio de sesión de muestra cuando el usuario introduzca las credenciales incorrectas y no pueda iniciar sesión. Este inicio de sesión de muestra no estará presente en un [servidor de producción](../../help/sites-administering/production-ready.md).

Para redireccionar correctamente, una vez que un sitio se haya configurado y se haya insertado para publicar, complete estos pasos para obtener un error de autenticación al redirigir al sitio de la comunidad:

* En cada instancia de publicación AEM
* Iniciar sesión por primera vez con privilegios de administrador
* Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md)
   * Por ejemplo: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localizar `Adobe Granite Login Selector Authentication Handler`
* Seleccione el icono `pencil`para abrir la configuración y editarla
* Escriba las **[!UICONTROL Asignaciones de página de inicio de sesión]** de la siguiente manera:

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   por ejemplo:

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Seleccione **[!UICONTROL Guardar]**

![chlimage_1-468](assets/chlimage_1-468.png)

### Redirección de autenticación de prueba {#test-authentication-redirection}

En el mismo AEM, la instancia de publicación se configura con una asignación de página de inicio de sesión para el sitio de comunidad:

* Vaya a la página de inicio del sitio de la comunidad
   * Por ejemplo: [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* Seleccionar Cerrar sesión
* Seleccionar inicio de sesión
* Escriba credenciales obviamente incorrectas, como el nombre de usuario &quot;x&quot; y la contraseña &quot;x&quot;
* La página de inicio de sesión debe mostrarse con un error de &quot;inicio de sesión no válido&quot;

![chlimage_1-469](assets/chlimage_1-469.png)

## Acceso a sitios de la comunidad desde la consola Sitios principales {#accessing-community-sites-from-main-sites-console}

Desde la consola Sitios de navegación global, los sitios de comunidad se encuentran en la carpeta `Community Sites`.

Aunque es posible acceder a un sitio de la comunidad de esta manera, para tareas administrativas, el sitio de la comunidad debe ser accedido desde la consola Sitios de comunidades.

![chlimage_1-470](assets/chlimage_1-470.png)

