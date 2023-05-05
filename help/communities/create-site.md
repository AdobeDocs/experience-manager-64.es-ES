---
title: Crear un nuevo sitio de comunidad
seo-title: Author a New Community Site
description: Cómo crear un nuevo sitio de AEM Communities
seo-description: How to author a new AEM Communities site
uuid: b8557416-cae4-489e-ab3b-e94d56686b7a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: bf182bb7-e305-45be-aadb-d71efd70f8cb
exl-id: 5d58f9c5-3210-48ef-94a3-805a1a57e3af
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 2%

---

# Crear un nuevo sitio de comunidad {#author-a-new-community-site}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Crear un nuevo sitio de comunidad {#create-a-new-community-site}

Utilice la instancia de autor para crear un nuevo sitio de comunidad

* Iniciar sesión con privilegios de administrador
* Desde la navegación global: **[!UICONTROL Navegación > Comunidades > Sitios]**

La consola Sitios de comunidades proporciona un asistente para guiar uno a través de los pasos de creación de un sitio de comunidad. Es posible pasar a la `Next`paso o `Back`hasta el paso anterior antes de comprometer el sitio en el paso final.

Para empezar a crear un nuevo sitio de comunidad:

* Seleccione el `Create` botón

![createcommunitysite](assets/createcommunitysite.png)

### Paso 1: Plantilla del sitio {#step-site-template}

![createsitetemplate63](assets/createsitetemplate63.png)

En el [Paso Plantilla del sitio](sites-console.md#step2013asitetemplate), introduzca un título, una descripción, el nombre de la dirección URL y seleccione una plantilla de sitio de la comunidad, por ejemplo:

* **[!UICONTROL Título del sitio de la comunidad]**: `Getting Started Tutorial`

* **[!UICONTROL Descripción del sitio de la comunidad]**: `A site for engaging with the community.`

* **[!UICONTROL Raíz del sitio de la comunidad]**: (deje en blanco para la raíz predeterminada `/content/sites`)

* **[!UICONTROL Configuraciones de nube]**: (deje en blanco si no se especifica ninguna configuración de nube) proporcione la ruta a las configuraciones de nube especificadas.
* **[!UICONTROL Idioma de base del sitio de la comunidad]**: (deje intacto para un solo idioma: Inglés) utilice el menú desplegable para elegir una *o más* idiomas básicos de los idiomas disponibles: alemán, italiano, francés, japonés, español, portugués (Brasil), chino (tradicional) y chino (simplificado). Se creará un sitio de comunidad para cada idioma agregado y existirá en la misma carpeta de sitio siguiendo las prácticas recomendadas descritas en [Traducción de contenido para sitios multilingües](../../help/sites-administering/translation.md). La página raíz de cada sitio contendrá una página secundaria denominada por el código de idioma de uno de los idiomas seleccionados, como &quot;en&quot; para inglés o &quot;fr&quot; para francés.

* **[!UICONTROL Nombre del sitio de la comunidad]**: participación

   * Vuelva a comprobar el nombre porque no es fácil cambiarlo después de crear el sitio
   * La dirección URL inicial se muestra debajo del nombre del sitio de la comunidad
   * Para una URL válida, añada un código de idioma base + &quot;.html&quot;
   * *Por ejemplo*, http://localhost:4502/content/sites/ `engage/en.html`

* **[!UICONTROL Plantilla]**: menú desplegable para elegir `Reference Site`

Seleccione **[!UICONTROL Siguiente]**

### Paso 2: Diseño {#step-design}

El paso Diseño se presenta en dos secciones para seleccionar el tema y el banner de marca:

#### TEMA DEL SITIO DE LA COMUNIDAD {#community-site-theme}

Seleccione el estilo que desee aplicar a la plantilla. Cuando se selecciona, el tema se superpone con una marca de verificación.

![sitetheme](assets/sitetheme.png)

#### MARCA DE SITIOS DE LA COMUNIDAD {#community-site-branding}

(Opcional) Cargue una imagen de banner para mostrarla en las páginas del sitio. El banner se fija en el borde izquierdo del explorador, entre el encabezado del sitio de la comunidad y el menú (vínculos de navegación). La altura del banner se recorta a 120 píxeles. No se puede cambiar el tamaño del banner para ajustarlo a la anchura del navegador y a la altura de 120 píxeles.

![chlimage_1-353](assets/chlimage_1-353.png) ![chlimage_1-354](assets/chlimage_1-354.png)

Seleccione **[!UICONTROL Siguiente]**.

### Paso 3: Configuración {#step-settings}

En el paso Configuración , antes de seleccionar `Next`, tenga en cuenta que hay siete secciones que proporcionan acceso a configuraciones que implican administración de usuarios, etiquetado, moderación, administración de grupos, análisis, traducción y habilitación.

Visite la [Introducción a AEM Communities para la activación](getting-started-enablement.md) tutorial para experimentar con el trabajo con las funciones de habilitación.

#### ADMINISTRACIÓN DE USUARIOS {#user-management}

Marque todas las casillas de verificación para [Administración de usuarios](sites-console.md#user-management)

* Para permitir que los visitantes del sitio se registren por su cuenta
* Para permitir que los visitantes del sitio vean el sitio sin iniciar sesión
* Para permitir que los miembros envíen y reciban mensajes de otros miembros de la comunidad
* Para permitir el inicio de sesión con Facebook en lugar de registrar y crear un perfil
* Para permitir el inicio de sesión con Twitter en lugar de registrar y crear un perfil

>[!NOTE]
>
>Para un entorno de producción, es necesario crear aplicaciones Facebook y Twitter personalizadas. Consulte [Inicio de sesión en Social con Facebook y Twitter](social-login.md).

![createsitesettings](assets/createsitesettings.png)

#### ETIQUETADO {#tagging}

Las etiquetas que se pueden aplicar al contenido de la comunidad se controlan seleccionando AEM áreas de nombres previamente definidas a través del [Consola de etiquetado](../../help/sites-administering/tags.md#tagging-console) (como el [Área de nombres del tutorial](setup.md#create-tutorial-tags)).

La búsqueda de áreas de nombres es sencilla mediante la búsqueda por tipo. Por ejemplo,

* Escriba &#39;tut&#39;
* Seleccionar `Tutorial`

![chlimage_1-355](assets/chlimage_1-355.png)

#### FUNCIONES {#roles}

[Funciones de miembro de la comunidad](users.md) se asignan mediante la configuración de la sección Funciones .

Para permitir que un miembro de la comunidad (o grupo de miembros) experimente el sitio como administrador de la comunidad, utilice la búsqueda por adelantado y seleccione el nombre del miembro o grupo en las opciones de la lista desplegable.

Por ejemplo,

* Escriba &quot;q&quot;
* Select [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Servicio de túnel](https://helpx.adobe.com/experience-manager/6-3/communities/using/deploy-communities.html#tunnel-service-on-author) permite seleccionar miembros y grupos que solo existen en el entorno de publicación.

![community_roles-1](assets/community_roles-1.png)

#### MODERACIÓN {#moderation}

Acepte la configuración global predeterminada para [moderación](sites-console.md#moderation) contenido generado por el usuario (UGC).

![chlimage_1-356](assets/chlimage_1-356.png)

#### ANALYTICS {#analytics}

Si Adobe Analytics tiene licencia y se ha configurado un marco y un servicio en la nube de Analytics, es posible habilitar Analytics y seleccionar el marco.

Consulte [Funciones de Configuración de Analytics para Communities](analytics.md).

![chlimage_1-357](assets/chlimage_1-357.png)

#### TRADUCCIÓN {#translation}

La variable [Configuración de traducción](sites-console.md#translation) especifique el idioma base para el sitio, así como si UGC puede traducirse o no y en qué idioma, si es así.

* Marque **[!UICONTROL Permitir traducción automática]**
* Deje seleccionados los idiomas predeterminados para la traducción por el servicio de traducción automática predeterminado
* Deje el proveedor de traducción predeterminado y la configuración
* No hay necesidad de una tienda global porque no hay copias de idioma
* Select **[!UICONTROL Traducir toda la página]**
* Opción Dejar persistencia predeterminada

![chlimage_1-358](assets/chlimage_1-358.png)

#### HABILITACIÓN {#enablement}

Deje vacío al crear una comunidad de participación.

Para un tutorial similar, cree rápidamente un [comunidad de habilitación](overview.md#enablement-community), consulte [Introducción a AEM Communities para la activación](getting-started-enablement.md).

Seleccione **[!UICONTROL Siguiente]**.

### Paso 4: Crear sitio de comunidades {#step-create-communities-site}

Seleccione **[!UICONTROL Crear]**.

![chlimage_1-359](assets/chlimage_1-359.png)

Cuando el proceso termina, la carpeta del nuevo sitio se muestra en la consola Comunidades - Sitios .

![communiessitesconsole](assets/communitiessitesconsole.png)

## Publicar el nuevo sitio de la comunidad {#publish-the-new-community-site}

El sitio creado debe administrarse desde la consola Comunidades - Sitios , la misma consola desde la que se pueden crear sitios nuevos.

Después de seleccionar la carpeta del sitio de la comunidad para abrirla, pase el ratón sobre el icono del sitio para que aparezcan cuatro iconos de acción:

![siteactionicon-1](assets/siteactionicons-1.png)

Al seleccionar el cuarto icono de elipses (Más acciones), aparecen las opciones Exportar sitio y Eliminar sitio .

![siteactionsnew-1](assets/siteactionsnew-1.png)

De izquierda a derecha se encuentran:

* **Abrir sitio**
Seleccione el icono de lápiz para abrir el sitio de la comunidad en modo de edición de autor, para añadir o configurar componentes de página

* **Editar sitio**
Seleccione el icono de propiedades para abrir el sitio de la comunidad para la modificación de propiedades, como el título o para cambiar el tema

* **Publicar sitio**
Seleccione el icono del mundo para publicar el sitio de la comunidad (por ejemplo, si el servidor de publicación se está ejecutando en el equipo local, entonces a localhost:4503 de forma predeterminada)

* **Exportar sitio**
Seleccione el icono de exportación para crear un paquete del sitio de la comunidad que esté almacenado en [gestor de paquetes](../../help/sites-administering/package-manager.md) y descargado.

   Tenga en cuenta que UGC no se incluye en el paquete del sitio.

* **Eliminar sitio**

   seleccione el icono eliminar para eliminar el sitio de la comunidad desde **[!UICONTROL Comunidades > Consola Sitios]**. Esta acción elimina todos los elementos asociados con el sitio, como UGC, grupos de usuarios, activos y registros de base de datos.

![siteactions-1](assets/siteactions-1.png)

>[!NOTE]
>
>Si no utiliza el puerto predeterminado 4503 para la instancia de publicación, edite el agente de replicación predeterminado para establecer el número de puerto en el valor correcto.
>
>En la instancia de autor, desde el menú principal
>
>1. Vaya a **[!UICONTROL Herramientas > Operaciones > Replicación]** menú
>1. Select **[!UICONTROL Agentes en autor]**
>1. Select **[!UICONTROL Agente predeterminado (publicar)]**
>1. Junto a **[!UICONTROL Configuración]** select **[!UICONTROL Editar]**
>1. En el cuadro de diálogo emergente de Configuración del agente, seleccione la pestaña Transporte
>1. En URI, cambie el número de puerto, 4503, al número de puerto deseado

>
>Por ejemplo, para utilizar el puerto 6103: `http://localhost:6103/bin/receive?sling:authRequestLogin=1`
>
>1. Select **[!UICONTROL OK]**
>1. (Opcional) Seleccione `Clear` o `Force Retry` para restablecer la cola de replicación


### Seleccionar publicación {#select-publish}

Después de asegurarse de que el servidor de publicación se está ejecutando, seleccione el icono del mundo para publicar el sitio de la comunidad.

![chlimage_1-360](assets/chlimage_1-360.png)

Cuando el sitio de la comunidad se ha publicado correctamente, aparece brevemente un mensaje:

![chlimage_1-361](assets/chlimage_1-361.png)

### Aviso sobre nuevos grupos de usuarios de la comunidad {#notice-new-community-user-groups}

Junto con el nuevo sitio de la comunidad, se crean nuevos grupos de usuarios que tienen los permisos adecuados establecidos para diversas funciones administrativas. Para obtener más información, visite [Grupos de usuarios para sitios de la comunidad](users.md#usergroupsforcommunitysites).

Para este nuevo sitio de comunidad, dado el nombre de sitio &quot;participar&quot; en el paso 1, los cuatro nuevos grupos de usuarios pueden verse desde la [Consola Grupos](members.md) (navegación global: Comunidades, Grupos):

* Administradores de comunidad
* Administradores de grupos de participación de la comunidad
* Miembros de participación de la comunidad
* Moderadores de participación de la comunidad
* Miembros privilegiados de participación de la comunidad
* Community Engage Sitecontentmanager

Observe que [Aaron McDonald](tutorials.md#demo-users) es miembro de

* Administradores de comunidad
* Moderadores de participación de la comunidad
* Miembros de participación de la comunidad (indirectamente como miembro del grupo Moderadores)

![chlimage_1-362](assets/chlimage_1-362.png)

#### http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-363](assets/chlimage_1-363.png)

## Configurar para error de autenticación {#configure-for-authentication-error}

Una vez configurado un sitio y presionado para publicarlo, [configurar asignación de inicio de sesión](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) en la instancia de publicación. La ventaja es que cuando las credenciales de inicio de sesión no se introducen correctamente, el error de autenticación vuelve a mostrar la página de inicio de sesión del sitio de la comunidad con un mensaje de error.

Agregue un `Login Page Mapping` como

* /content/sites/engagement/en/signin:/content/sites/actual/actual

## Pasos opcionales {#optional-steps}

### Cambiar la página principal predeterminada {#change-the-default-home-page}

Cuando se trabaja con el sitio de publicación con fines de demostración, puede ser útil cambiar la página principal predeterminada al nuevo sitio.

Para ello, es necesario utilizar [CRXDE](http://localhost:4503/crx/de) Lite para editar el [asignación de recursos](../../help/sites-deploying/resource-mapping.md) al publicar.

Para empezar:

1. En la publicación, inicie sesión con privilegios de administrador
1. Vaya a [http://localhost:4503/crx/de](http://localhost:4503/crx/de)
1. En el explorador del proyecto, expanda `/etc/map`
1. Seleccione el `http` node

   * Select **[!UICONTROL Crear nodo]**

      * **Nombre** localhost.4503

         (do *not* use `:`)

      * **Tipo** [sling:Asignación](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Con `localhost.4503` nodo seleccionado

   * Añadir propiedades

      * **Nombre** sling:match
      * **Tipo** Cadena
      * **Valor** localhost.4503/\$

         (debe terminar con &#39;$&#39; char)
   * Añadir propiedades

      * **Nombre** sling:internalRedirect
      * **Tipo** Cadena
      * **Valor** /content/sites/engage/en.html


1. Select **[!UICONTROL Guardar todo]**
1. (opcional) Eliminar el historial de navegación
1. Vaya a http://localhost:4503/

   * Llegue a http://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Para desactivarlo, simplemente anteponga el `sling:match` valor de propiedad con una &quot;x&quot; - `xlocalhost.4503/$` - y **[!UICONTROL Guardar todo]**.

![chlimage_1-364](assets/chlimage_1-364.png)

#### Solución de problemas: Error al guardar el mapa {#troubleshooting-error-saving-map}

Si no puede guardar los cambios, asegúrese de que el nombre del nodo sea `localhost.4503`, con un separador de &quot;puntos&quot;, y no `localhost:4503` con un separador de &quot;dos puntos&quot;, como `localhost`no es un prefijo de espacio de nombres válido.

![chlimage_1-365](assets/chlimage_1-365.png)

#### Solución de problemas: No se puede redirigir {#troubleshooting-fail-to-redirect}

El **$**&#39; al final de la expresión regular `sling:match`es crucial, por lo que solo `http://localhost:4503/` está asignado, de lo contrario el valor de redireccionamiento se antepone a cualquier ruta que pueda existir después de server:port en la dirección URL. Por lo tanto, cuando AEM intenta redirigir a la página de inicio de sesión, falla.

### Modificación del sitio {#modify-the-site}

Una vez creado el sitio por primera vez, los autores pueden usar la variable [Icono Abrir sitio](sites-console.md#authoring-site-content) para realizar actividades de creación de AEM estándar.

Además, los administradores pueden usar la variable [Icono Editar sitio](sites-console.md#modifying-site-properties) para modificar las propiedades del sitio, como el título.

Después de cualquier modificación, recuerde **guardar** y **volver a publicar** el sitio.

>[!NOTE]
>
>Si no está familiarizado con AEM, consulte la documentación de [tratamiento básico](../../help/sites-authoring/basic-handling.md) y [guía rápida para la creación de páginas](../../help/sites-authoring/qg-page-authoring.md).
