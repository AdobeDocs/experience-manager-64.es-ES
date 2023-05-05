---
title: Creación de grupos anidados
seo-title: Authoring Nested Groups
description: Crear grupos anidados
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 4%

---

# Creación de grupos anidados {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Creación de grupos en el autor {#creating-groups-on-author}

Al autor, desde la navegación global

* Select **[!UICONTROL Comunidades > Sitios]**
* Select **[!UICONTROL carpeta de participación]** para abrirlo
* Seleccione la tarjeta para el **[!UICONTROL Tutorial de introducción]**  Sitio en inglés
   * Seleccionar la imagen de la tarjeta
   * Do *not* seleccionar un icono

El resultado es alcanzar la variable [Consola Grupos](groups.md):

![imagen_1-53](assets/chlimage_1-53.png)

La función de grupos se muestra como una carpeta en la que se crean instancias de grupos. Seleccione la carpeta Grupos para abrirla. El grupo creado al publicar está visible.

![imagen_1-54](assets/chlimage_1-54.png)

## Crear grupo de artes principales {#create-main-arts-group}

Este grupo se puede crear porque la estructura del sitio para la participación incluye una función de grupo. La configuración de la función en el `Reference Template` de forma predeterminada, permite seleccionar cualquier plantilla de grupo habilitada. Por lo tanto, la plantilla elegida para este nuevo grupo será la `Reference Group`.

Estas consolas son muy similares a la consola Sitios de Communities .

* Select **[!UICONTROL Crear grupo]**
* `1 Community Group Template`:
   * Título del grupo de la comunidad: Artes
   * Descripción del grupo de la comunidad: Un grupo de padres para varios grupos de arte.
   * Raíz del grupo de la comunidad: *dejar como predeterminado*
   * Idiomas de grupo de comunidad disponibles adicionales: utilice el menú desplegable para seleccionar los idiomas de grupo de comunidad disponibles. El menú muestra todos los idiomas en los que se crea el sitio de la comunidad principal. Los usuarios pueden seleccionar entre estos idiomas para crear grupos en varias configuraciones regionales en este solo paso. El mismo grupo se crea en varios idiomas especificados en la consola Grupos de los respectivos sitios de la comunidad.
   * Nombre del grupo de la comunidad: arts
   * Plantilla: desplegable para seleccionar `Reference Group`
   * Seleccionar `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Continúe por los demás paneles con esta configuración:

* **2 Diseño**
   * Puede cambiar el diseño o permitir que el diseño predeterminado del sitio principal sea
   * Seleccione **[!UICONTROL Siguiente]**
* **3 Configuración**
   * **Moderación**
      * Dejar vacío (heredar del sitio principal)
   * **Suscripción**
      * use default `Optional Membership`
   * **Miniatura**
      * `optional`
   * Seleccionar `Next`
* Seleccione **[!UICONTROL Crear]**

### Grupos de anidación dentro del Grupo de Artes {#nesting-groups-within-arts-group}

La variable `groups` La carpeta debe contener dos grupos (puede que sea necesario actualizar la página).

![createcommunitygroup](assets/createcommunitygroup.png)

#### Publicar grupo  {#publish-group}

Antes de crear grupos anidados dentro de la variable `arts`, pase el ratón sobre el `arts` y seleccione el icono de publicación para publicarlo.

![imagen_1-55](assets/chlimage_1-55.png)

Espere a que se confirme que se publicó el grupo.

![imagen_1-56](assets/chlimage_1-56.png)

La variable `arts` El grupo también debe contener `groups` , pero una que esté vacía y en la que se puedan crear nuevos grupos. Vaya a la carpeta de grupos de artes y cree 3 grupos anidados, cada uno con una configuración de pertenencia diferente:

1. Visital
   * Título: `Visual Arts`
   * Nombre: `visual`
   * Plantilla: `Reference Group`
   * Membresía: select `Optional Membership`
Un grupo público abierto a todos los miembros
1. Auditorio
   * Título: `Auditory Arts`
   * Nombre: `auditory`
   * Plantilla: `Reference Group`
   * Membresía: select `Required Membership`
Un grupo abierto, disponible para que los miembros se unan

1. Historia

   * Título: `Art History`
   * Nombre: `history`
   * Plantilla: `Reference Group`
   * Membresía: select `Restricted Membership`
Un grupo secreto, visible únicamente para los miembros invitados como ejemplo, invita 
[usuario de demostración](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Actualice la página para ver los tres grupos anidados (subcomunidades).

Si es necesario, para desplazarse a los grupos anidados desde la consola Sitios de Communities:

* Select **[!UICONTROL carpeta de participación]**
* Select **[!UICONTROL Tutorial de introducción]** tarjeta
* Select **[!UICONTROL Carpeta Grupos]**
* Select **[!UICONTROL tarjeta de arte]**
* Select **[!UICONTROL Carpeta Grupos]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Grupos de publicaciones {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Después de publicar el sitio de la comunidad principal, es necesario

* Publicar cada grupo individualmente
   * Esperando confirmación de que el grupo se publicó
* Publicar grupo principal antes de publicar cualquier grupo anidado en
   * Todos los grupos deben publicarse de forma descendente.

![chlimage_1-59](assets/chlimage_1-59.png)

## Experiencia en la publicación {#experience-on-publish}

Es posible experimentar los diferentes grupos cuando se inicia sesión, por ejemplo, con la variable [usuarios de demostración](tutorials.md#demo-users) usado para

* Miembro del grupo Arte/Historia: emily.andrews@mailinator.com/password
   * El grupo restringido (secreto), arte/historia, será visible
   * Se pueden ver grupos opcionales (públicos)
   * Pueden unirse a grupos restringidos (abiertos)
* Administrador de grupos: aaron.mcdonald@mailinator.com/password
   * Se pueden ver grupos opcionales (públicos)
   * pueden unirse a grupos restringidos (abiertos)
   * No verá grupos restringidos (secretos)

Acceso a las comunidades [Consolas Miembros y Grupos](members.md) un autor para agregar otros usuarios a varios grupos de miembros que se correspondan con los grupos de la comunidad.
