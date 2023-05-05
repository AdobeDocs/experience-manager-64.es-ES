---
title: Consolas de comunidades
seo-title: Communities Consoles
description: Consolas de comunidad explicadas
seo-description: Community Consoles explained
uuid: 1c5b2600-9059-4b44-9741-f1b627423d3c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5fa9ee8b-5893-4ae9-a986-bfdbb00f355f
role: Admin
exl-id: f31072dc-ad2d-4f2d-b222-05d7fb19e471
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 3%

---

# Consolas de comunidades {#communities-consoles}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las consolas de AEM Communities, disponibles en el entorno de creación desde el panel de navegación global, proporcionan acceso a tareas administrativas como

* [Creación de un sitio de comunidad](sites-console.md)
* Adición [grupos](groups.md) anidado dentro del sitio
* Administración [plantillas de sitio de la comunidad](sites.md)
* Administración [miembros de la comunidad](members.md)
* [Moderación](moderate-ugc.md) contenido generado por el usuario (UGC)
* Crear [distintivos personalizados](badges.md)
* Configuración de la variable [almacenamiento predeterminado para UGC](srp-config.md)

When [Almacenamiento de UGC](working-with-srp.md) está configurado para ser un almacén común compartido por los entornos de autor y publicación, la variable [consola de moderación](moderation.md), disponible tanto en entornos de autor como de publicación, funciona en una instancia solitaria de UGC.

En el entorno de creación, después de iniciar sesión con privilegios de administrador, la variable `Communities` las consolas están disponibles en las consolas de herramientas y navegación.

>[!NOTE]
>
>En el entorno de publicación, una [sitio de la comunidad](sites-console.md) mostrará un `Administration`elemento de menú cuando el miembro que ha iniciado sesión tiene los privilegios adecuados.

## Panel de navegación global {#global-navigation-panel}

![imagen_1-91](assets/chlimage_1-91.png)

Seleccione el `Adobe Experience Manager` en la esquina superior izquierda para abrir el panel de navegación global y acceder a dos iconos:

* [Consola de navegación](#navigation-console)
* [Consola Herramientas](tools.md)

## Consola de navegación {#navigation-console}

Para acceder a las distintas consolas de Communities, en la navegación global, seleccione **navegación, Comunidades**.

![chlimage_1-92](assets/chlimage_1-92.png)

* [Sites](sites-console.md)

   La consola Sitios es accesible en el entorno de creación con el fin de crear y administrar los sitios de la comunidad y su [grupos](groups.md).

* [Moderación](moderation.md)

   La consola Moderación es para la moderación masiva de UGC y en el entorno de creación. En el entorno de publicación, se puede acceder a una consola de moderación masiva similar a los miembros de la comunidad a los que se haya asignado la función de [moderador de la comunidad](users.md#publishenvironmentusersandgroups) para uno o más sitios de comunidad.

* [Miembros, grupos](members.md)

   Las consolas Miembros y Grupos sirven para administrar los miembros de la comunidad y los grupos de miembros que existen en el entorno de publicación desde el entorno de creación.

* [Informes](reports.md)

   La consola Informes es donde se pueden generar informes sobre asignaciones, vistas de página y contenido publicado (UGC) cuando un sitio de la comunidad tiene [habilitado para Adobe Analytics](sites-console.md#analytics). La consola solo está disponible en el entorno de creación.

* [Recursos](resources.md)

   La consola Recursos es donde [administradores de habilitación](enablement.md#communitymanagers) crear, administrar y asignar recursos a miembros de un [sitio de la comunidad de habilitación](overview.md#enablement-community). La consola solo está disponible en el entorno de creación.

## Consola Herramientas {#tools-console}

Para acceder a [Herramientas de comunidades](tools.md) (anteriormente, consola de administración), desde la navegación global: **[!UICONTROL Herramientas > Comunidades]**
