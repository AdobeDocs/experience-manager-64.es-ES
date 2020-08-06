---
title: Creación de grupos anidados
seo-title: Creación de grupos anidados
description: Crear grupos anidados
seo-description: Crear grupos anidados
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 3%

---


# Creación de grupos anidados {#authoring-nested-groups}

## Creación de grupos en el autor {#creating-groups-on-author}

En el autor, desde la navegación global

* Seleccionar **[!UICONTROL comunidades > Sitios]**
* Seleccione **[!UICONTROL la carpeta]** de participación para abrirla
* Seleccione la tarjeta para el sitio **[!UICONTROL Tutorial]** de introducción en inglés
   * Seleccionar la imagen de la tarjeta
   * No *seleccione* un icono

El resultado es llegar a la consola [](groups.md)Grupos:

![chlimage_1-53](assets/chlimage_1-53.png)

La función de grupos se mostrará como una carpeta en la que se crearán las instancias de grupos. Seleccione la carpeta Grupos para abrirla. El grupo creado al publicar está visible.

![chlimage_1-54](assets/chlimage_1-54.png)

## Crear grupo de artes principales {#create-main-arts-group}

Este grupo se puede crear porque la estructura del sitio para la participación incluye una función de grupo. La configuración de la función en el sitio `Reference Template` de forma predeterminada permite la selección de cualquier plantilla de grupo habilitada. Por lo tanto, la plantilla elegida para este nuevo grupo será la `Reference Group`.

Estas consolas son muy similares a la consola Sitios de comunidades.

* Seleccionar **[!UICONTROL crear grupo]**
* `1 Community Group Template`:
   * Título del grupo de la comunidad: Artes
   * Descripción del grupo de la comunidad: Un grupo de padres para varios grupos de artes.
   * Raíz del grupo de la comunidad: *dejar como predeterminado*
   * Idioma(s) adicional(s) disponible(s) del grupo de la comunidad:utilice el menú desplegable para seleccionar los idiomas disponibles del grupo de la comunidad. El menú muestra todos los idiomas en los que se crea el sitio de comunidad principal. Los usuarios pueden seleccionar entre estos idiomas para crear grupos en varias configuraciones regionales en este solo paso. El mismo grupo se crea en varios idiomas especificados en la consola Grupos de los respectivos sitios de la comunidad.
   * Nombre del grupo de la comunidad: artes
   * Plantilla: desplegable para seleccionar `Reference Group`
   * Seleccione `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Continúe por los demás paneles con esta configuración:

* **2 Diseño**
   * Puede cambiar el diseño o permitir que el diseño del sitio principal sea el predeterminado
   * Seleccione **[!UICONTROL Siguiente]**
* **3 Configuración**
   * **Moderación**
      * Dejar vacío (heredar del sitio principal)
   * **Suscripción**
      * use default `Optional Membership`
   * **Miniatura**
      * `optional`
   * Seleccione `Next`
* Seleccione **[!UICONTROL Crear]**

### Grupos de anidación dentro del grupo de artes {#nesting-groups-within-arts-group}

La `groups` carpeta ahora debe contener dos grupos (puede que sea necesario actualizar la página).

![createcommunitygroup](assets/createcommunitygroup.png)

#### Publicar grupo {#publish-group}

Antes de crear grupos anidados dentro del `arts``arts` grupo, coloque el puntero sobre la tarjeta y seleccione el icono de publicación para publicarla.

![chlimage_1-55](assets/chlimage_1-55.png)

Espere a que se confirme que se publicó el grupo.

![chlimage_1-56](assets/chlimage_1-56.png)

El `arts` grupo también debe contener una `groups` carpeta, pero una que esté vacía y en la que se puedan crear nuevos grupos. Vaya a la carpeta del grupo de artes y cree 3 grupos anidados, cada uno con una configuración de pertenencia diferente:

1. Visitante
   * Título: `Visual Arts`
   * Nombre: `visual`
   * Plantilla: `Reference Group`
   * Membresía: seleccionar `Optional Membership`un grupo público, abierto a todos los miembros
1. Auditorio
   * Título: `Auditory Arts`
   * Nombre: `auditory`
   * Plantilla: `Reference Group`
   * Membresía: seleccionar `Required Membership`un grupo abierto, disponible para que los miembros se unan

1. Historia

   * Título: `Art History`
   * Nombre: `history`
   * Plantilla: `Reference Group`
   * Membresía: seleccionar `Restricted Membership`Un grupo secreto, visible sólo para los miembros invitados como ejemplo, invitar 
[usuario de demostración](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Actualice la página para ver los tres grupos anidados (subcomunidades).

Si es necesario, para desplazarse a los grupos anidados desde la consola Sitios de comunidades:

* Seleccionar carpeta **[!UICONTROL de participación]**
* Seleccione la tarjeta **[!UICONTROL Tutorial]** de introducción
* Seleccionar carpeta **[!UICONTROL de grupos]**
* Seleccionar tarjeta **[!UICONTROL de artes]**
* Seleccionar carpeta **[!UICONTROL de grupos]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Grupos de publicaciones {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Después de publicar el sitio de la comunidad principal, es necesario

* Publicar cada grupo individualmente
   * Esperando confirmación de que se publicó el grupo
* Publicar grupo principal antes de publicar cualquier grupo anidado en
   * Todos los grupos deben publicarse de manera vertical.

![chlimage_1-59](assets/chlimage_1-59.png)

## Experiencia en la publicación {#experience-on-publish}

Es posible experimentar los diferentes grupos al iniciar sesión, por ejemplo con los usuarios [de](tutorials.md#demo-users) demostración utilizados para

* Miembro del grupo Arte/Historia: emily.andrews@mailinator.com/password
   * El grupo restringido (secreto), arte/historia, será visible
   * Puede ver grupos opcionales (públicos)
   * Pueden unirse a grupos restringidos (abiertos)
* Administrador de grupos: aaron.mcdonald@mailinator.com/password
   * Puede ver grupos opcionales (públicos)
   * puede unirse a grupos restringidos (abiertos)
   * No se verán grupos restringidos (secretos)

Acceda a las consolas [Miembros y Grupos de comunidades](members.md) del autor para agregar otros usuarios a varios grupos de miembros que se correspondan con los grupos de la comunidad.
