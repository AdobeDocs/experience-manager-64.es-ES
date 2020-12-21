---
title: Experimente el sitio publicado
seo-title: Experimente el sitio publicado
description: Explorar un sitio publicado
seo-description: Explorar un sitio publicado
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---


# Experimente el sitio publicado {#experience-the-published-site}

## Buscar nuevo sitio en la publicación {#browse-to-new-site-on-publish}

Ahora que se ha publicado el sitio de comunidades recién creado, busque la dirección URL que se muestra al crear el sitio, pero en el servidor de publicación, por ejemplo:

* URL del autor = http://localhost:4502/content/sites/engage/en.html
* URL de publicación = http://localhost:4503/content/sites/engage/en.html

Para minimizar la confusión sobre qué miembro ha iniciado sesión en la creación y publicación, se recomienda utilizar distintos navegadores para cada instancia.

Al llegar por primera vez al sitio publicado, el visitante del sitio no suele haber iniciado sesión y sería anónimo.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-310](assets/chlimage_1-311.png)

## Visitante del sitio anónimo {#anonymous-site-visitor}

Un visitante de sitio anónimo ve lo siguiente en la interfaz de usuario:

* Título del sitio. Tutorial de introducción
* Sin vínculo de perfil
* Ningún vínculo de mensajes
* Ningún vínculo de notificaciones
* Campo de búsqueda
* Iniciar sesión en el vínculo
* La pancarta de la marca
* Vínculos de menú para los componentes incluidos en la plantilla de sitio de referencia

Si selecciona varios vínculos, encontrará que están en modo de solo lectura.

## Impedir el acceso anónimo a JCR {#prevent-anonymous-access-on-jcr}

Una limitación conocida expone el contenido del sitio de la comunidad a visitantes anónimos a través del contenido jcr y json, aunque **permitir acceso anónimo** está deshabilitado para el contenido del sitio. Sin embargo, este comportamiento se puede controlar mediante restricciones de Sling como solución alternativa.

Para proteger el contenido del sitio de la comunidad del acceso de usuarios anónimos a través del contenido jcr y json, siga estos pasos:

1. En la instancia de AEM Author, vaya a https://&lt;host>:&lt;puerto>/editor.html/content/site/&lt;nombre del sitio>.html.

   >[!NOTE]
   >
   >No vaya al sitio localizado.

1. Vaya a **[!UICONTROL Propiedades de la página]**.

   ![site-authentication](assets/site-authentication.png)

1. Vaya a la ficha **[!UICONTROL Avanzado]**.

   ![page-properties](assets/page-properties.png)

1. Habilite **[!UICONTROL Requisito de autenticación]**.
1. Añada la ruta de la página de inicio de sesión. Por ejemplo, `/content/......./GetStarted`.
1. Publique la página.

## Miembro de la comunidad de confianza {#trusted-community-member}

Esta experiencia supone que a [Aaron McDonald](tutorials.md#demo-users) se le asignaron las funciones de [administrador de la comunidad y moderador](create-site.md#roles). Si no es así, vuelva al entorno de creación para [modificar la configuración del sitio](sites-console.md#modifying-site-properties) y seleccione Aaron McDonald como administrador de la comunidad y moderador.

En la esquina superior derecha, seleccione `Log in` y firme con el nombre de usuario &quot;aaron.mcdonald@mailinator.com&quot; y la contraseña &quot;password&quot;. Tenga en cuenta la capacidad de iniciar sesión con credenciales de Twitter o Facebook.

![chlimage_1-312](assets/chlimage_1-312.png)

Una vez iniciada la sesión, observe que hay un nuevo elemento de menú, `Administration`, que aparece porque al miembro se le dio la función de moderador. Ahora seleccionar varios vínculos es más interesante.

![chlimage_1-313](assets/chlimage_1-313.png)

Observe que la página Calendario es la página de inicio porque la plantilla de sitio de referencia elegida incluía primero la función Calendario, seguida de la función Flujo de Actividad, la función Foro, etc. Esta estructura está visible desde la consola [Plantilla del sitio](sites.md#edit-site-template) o al modificar las propiedades del sitio en el entorno de creación:

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Para obtener más información sobre los componentes y funciones de Communities, visite
>
>* [Componentes](author-communities.md)  de comunidades (para autores)
>* [Componentes, funciones y características esenciales](essentials.md)  (para desarrolladores)

>



## Vínculo de foro {#forum-link}

Para vista de la función básica de foro, seleccione el vínculo Foro.

Los miembros pueden publicar un tema nuevo o seguir un tema.

Los visitantes del sitio pueden realizar vistas de anuncios y ordenarlos de diversas maneras.

![chlimage_1-315](assets/chlimage_1-315.png)

## Vínculo de grupos {#groups-link}

Como Aaron es administrador de grupos, si selecciona el vínculo Grupos, Aaron podrá crear un nuevo grupo de la comunidad seleccionando una plantilla de grupo, una imagen, si el grupo es abierto o secreto, e invitando a los miembros.

Este es un ejemplo en el que se crea un grupo en el entorno de publicación.

Los grupos también se pueden crear en el entorno del autor y administrar dentro del sitio de la comunidad en el entorno del autor (la [consola de grupos de la comunidad](groups.md)). La experiencia de [creación de grupos en el autor](nested-groups.md) es la siguiente en este tutorial.

![chlimage_1-316](assets/chlimage_1-316.png)

Crear un grupo de referencia:

1. Seleccionar **[!UICONTROL Nuevo grupo]**
1. **[!UICONTROL Ficha Configuración]**
   * Nombre del grupo: `Sports`
   * Descripción: `A parent group for various sporting groups`
   * Nombre de URL del grupo: `sports`
   * seleccionar `Open Group` (permitir que cualquier miembro de la comunidad participe al unirse)
1. **[!UICONTROL Ficha Plantilla]**
   * Seleccionar `Reference Group` (contiene una función de grupo en su estructura para permitir grupos anidados)
1. Seleccione **[!UICONTROL Crear grupo]**

![chlimage_1-317](assets/chlimage_1-317.png)

Una vez creado el nuevo grupo, **seleccione el nuevo grupo de deportes** para crear dos grupos (anidados) dentro de él. Como una estructura de sitio no puede comenzar con la función de grupos, después de abrir el grupo Deportes, es necesario seleccionar el vínculo Grupos:

![chlimage_1-318](assets/chlimage_1-318.png)

El segundo conjunto de vínculos, comenzando por `Blog`, pertenece al grupo seleccionado actualmente, el grupo `Sports`. Al seleccionar el vínculo &quot;Deportes&quot; `Groups`, es posible anidar dos grupos dentro del grupo Deportes.

Como ejemplo, agregue dos n `ew groups.`

* Uno con el nombre `Baseball`
   * Déjelo configurado como `Open Group` (pertenencia requerida)
   * En la ficha Plantillas, seleccione `Conversational Group`
* Uno con el nombre `Gymnastics`
   * Cambiar su configuración a `Member Only Group` (pertenencia restringida)
   * En la ficha Plantillas, seleccione `Conversational Group`

**Aviso**:

* Es posible que sea necesario actualizar la página antes de que se muestren ambos grupos
* Esta plantilla *no incluye la función de grupos, por lo que no será posible anidar más grupos
* Al crear, la [consola de grupos](groups.md) proporciona una tercera opción: `Public Group` (abono opcional)

Una vez creados ambos grupos, seleccione el grupo de béisbol, un grupo abierto y observe sus vínculos: `Discussions` `What's New` `Members`
Los vínculos del grupo se muestran debajo de los vínculos del sitio principal y se muestran de la siguiente manera:

![chlimage_1-319](assets/chlimage_1-319.png)

En el caso del autor: con privilegios administrativos, vaya a la consola [Grupos de comunidades](members.md) y agregue Weston McCall al grupo `Community Engage Gymnastics <uid> Members`.

Continuando con la publicación, cierre la sesión como Aaron McDonald y vista los grupos en el grupo de deportes como un visitante anónimo en el sitio:

* Desde página de inicio
* Seleccionar `Groups`vínculo
* Seleccionar `Sports`vínculo
* Seleccione el vínculo &quot;Deportes&quot; `Groups`

Sólo el grupo de béisbol será visible.

Inicie sesión como Weston McCall (weston.mccall@dodgit.com / contraseña) y navegue a la misma ubicación. Observe que Weston puede `Join` abrir el grupo `Baseball` y `enter or Leave` el grupo privado `Gymnastics`.

![chlimage_1-320](assets/chlimage_1-320.png)

## Vínculo de página Web {#web-page-link}

Vista la página Web básica incluida en el sitio seleccionando el vínculo Página Web. Las herramientas AEM de creación estándar pueden utilizarse para agregar contenido a esta página en el entorno de creación.

Por ejemplo, vaya a la instancia **author**, abra la carpeta `engage` en la consola [Communities Sites](sites-console.md), seleccione el icono **Open Site** para entrar en el modo de edición del autor. A continuación, seleccione el modo de previsualización para seleccionar el vínculo `Web Page`y, a continuación, seleccione el modo de edición para añadir los componentes Título y Texto. Por último, vuelva a publicar solo la página o todo el sitio.

![chlimage_1-321](assets/chlimage_1-321.png)

## Vínculo de administración {#administration-link}

Cuando el miembro de la comunidad tiene privilegios de moderación, el vínculo Administración estará visible y, al seleccionarlo, se mostrará el contenido de la comunidad publicado y se permitirá que esté [moderado](moderate-ugc.md) de manera similar a la [consola de moderación](moderation.md) en el entorno de creación.

Utilice el botón Atrás del explorador para volver al sitio publicado. La mayoría de las consolas no son accesibles desde la navegación global en el entorno de publicación.

![chlimage_1-322](assets/chlimage_1-322.png)

## Autorregistro {#self-registration}

Después de cerrar sesión, es posible crear un nuevo registro de usuario.

* Seleccione `Log In`
* Seleccione `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

De forma predeterminada, la dirección de correo electrónico es la identificación de inicio de sesión. Si no se selecciona, el visitante puede introducir su propia identificación de inicio de sesión (nombre de usuario). El nombre de usuario debe ser único en el entorno de publicación.

Después de especificar el nombre, el correo electrónico y la contraseña del usuario, al seleccionar `Sign Up`se creará el usuario y se le permitirá firmarlo.

Una vez iniciada la sesión, la primera página presentada es su `Profile`página, que pueden personalizar.

![chlimage_1-325](assets/chlimage_1-325.png)

Si el miembro olvida su identificación de inicio de sesión, es posible recuperarla utilizando su dirección de correo electrónico.

![chlimage_1-326](assets/chlimage_1-326.png)
