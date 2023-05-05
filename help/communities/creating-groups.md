---
title: Grupos de la comunidad
seo-title: Community Groups
description: Creación de grupos de comunidades
seo-description: Creating community groups
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 2%

---

# Grupos de la comunidad {#community-groups}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La función de grupos de comunidad es la capacidad de los usuarios autorizados (miembros de la comunidad y autores) desde los entornos de publicación y creación para crear dinámicamente una subcomunidad dentro de un sitio de comunidad.

Esta capacidad está presente cuando la variable [Función de grupos](functions.md#groups-function) está presente en la variable [sitio de la comunidad](sites-console.md) estructura.

A [plantilla de grupo de la comunidad](tools-groups.md) proporciona el diseño de la página de grupo de comunidad cuando se crea un grupo de comunidad de forma dinámica.

Se seleccionan una o más plantillas de grupo para la función de grupos cuando la función se agrega a la estructura de un sitio de la comunidad o a una plantilla de sitio de la comunidad. Esta lista de plantillas de grupo se presenta al miembro o autor que crea dinámicamente un nuevo grupo desde el sitio de la comunidad.

## Creación de un nuevo grupo {#creating-a-new-group}

La capacidad de crear un nuevo grupo de comunidad depende de la existencia de un sitio de comunidad que incluya la función de grupos, como uno creado a partir de la variable ` [Reference Site Template](sites.md)`.

Los ejemplos siguientes utilizan el sitio de comunidad creado a partir de la variable `Reference Site Template` tal como se describe en la sección [Introducción a AEM Communities](getting-started.md) tutorial.

Esta es la página que se carga al publicar cuando la variable **[!UICONTROL Grupos]** elemento de menú seleccionado:

![chlimage_1-236](assets/chlimage_1-236.png)

Al seleccionar la variable **[!UICONTROL Nuevo grupo]** , se abre un cuadro de diálogo de edición.

En el **[!UICONTROL Configuración]** , proporcione las funciones básicas del grupo:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nombre del grupo]**
Título del grupo que se mostrará en el sitio de la comunidad.

* **[!UICONTROL Descripción]**
Descripción del grupo que se mostrará en el sitio de la comunidad.

* **[!UICONTROL Invitar]**
Una lista de miembros a los que invitar para unirse al grupo. La búsqueda de tipo por adelantado proporcionará sugerencias de los miembros de la comunidad a los que invitar.

* **[!UICONTROL Nombre de la dirección URL del grupo]**
Nombre de la página de grupo que forma parte de la dirección URL.

* **[!UICONTROL Abrir grupo]**
Selección 
`Open Group` indica que cualquier visitante anónimo del sitio puede ver el contenido y deseleccionará `Member Only Group`.

* **[!UICONTROL Grupo solo de miembros]**
Selección 
`Member Only Group` indica que solo los miembros del grupo pueden ver el contenido y anularán la selección `Open Group`.

En el **[!UICONTROL Plantilla]** es la capacidad de seleccionar de la lista de plantillas de grupo de la comunidad que se especificaron cuando la función de grupos se incluyó en la estructura del sitio de la comunidad o en una plantilla de sitio de la comunidad.

![chlimage_1-238](assets/chlimage_1-238.png)

En el **[!UICONTROL Imagen]** es la capacidad de cargar una imagen para mostrarla en el grupo en la página Grupos del sitio de la comunidad. La hoja de estilo predeterminada cambiará el tamaño de la imagen a 170 x 90 píxeles.

![chlimage_1-239](assets/chlimage_1-239.png)

Seleccione la **[!UICONTROL Crear grupo]** , las páginas del grupo se crean en función de la plantilla elegida, y se crea un grupo de usuarios para la pertenencia, y la página Grupos se actualiza para mostrar la nueva subcomunidad.

Por ejemplo, la página Grupos con una nueva subcomunidad titulada &quot;Grupo de enfoque&quot;, para la que se cargó una imagen en miniatura, aparecerá de la siguiente manera (aún con sesión iniciada como administrador de grupo de la comunidad):

![chlimage_1-240](assets/chlimage_1-240.png)

Al seleccionar la variable `Focus Group` el vínculo abrirá la página Grupo de enfoque en el explorador, que tiene una apariencia inicial basada en la plantilla elegida, e incluye un submenú debajo del menú del sitio de la comunidad principal:

![chlimage_1-241](assets/chlimage_1-241.png)

## Componente de lista de miembros del grupo de la comunidad {#community-group-member-list-component}

La variable `Community Group Member List` está diseñado para ser utilizado por desarrolladores de plantillas de grupo.

## Información adicional {#additional-information}

Puede encontrar más información en la [Community Group Essentials](essentials-groups.md) para desarrolladores.

Para obtener más información relacionada con los grupos de la comunidad, visite [Administración de usuarios y grupos de usuarios](users.md).
