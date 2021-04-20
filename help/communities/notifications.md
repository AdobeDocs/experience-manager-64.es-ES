---
title: Notificaciones de comunidades
seo-title: Notificaciones de comunidades
description: AEM Communities tiene notificaciones que muestran eventos de interés para el miembro de la comunidad que ha iniciado sesión
seo-description: AEM Communities tiene notificaciones que muestran eventos de interés para el miembro de la comunidad que ha iniciado sesión
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Notificaciones de comunidades {#communities-notifications}

## Información general {#overview}

AEM Communities proporciona una sección de notificaciones que muestra eventos de interés para el miembro de la comunidad que ha iniciado sesión.

Las notificaciones son similares a las [actividades](essentials-activities.md) y [suscripciones](subscriptions.md) que pueden resultar de

* El miembro que publica contenido
* El miembro que decide seguir a otro miembro
* El miembro que elige seguir temas específicos, artículos y otros subprocesos de contenido

Lo que distingue las notificaciones de actividades y suscripciones es

* Un vínculo a la sección de notificaciones siempre está presente en el encabezado de un sitio de la comunidad
   * Las actividades requieren que la [función del flujo de actividad](functions.md#activity-stream-function) se incluya en la estructura del sitio de la comunidad
   * Las suscripciones requieren [configuración del correo electrónico](email.md)
* La implementación de las notificaciones se realiza a través de canales ampliables y conectables
   * Las actividades solo están disponibles en la web
   * Las suscripciones solo están disponibles mediante correo electrónico

A partir de Communities [FP1](deploy-communities.md#latestfeaturepack), los canales de notificación disponibles son

* El canal web, al que se accede mediante el enlace `Notifications`
* El canal de correo electrónico, disponible cuando el correo electrónico está configurado correctamente

Los canales futuros son móviles y de escritorio.

### Requisitos {#requirements}

**Configurar correo electrónico**

El correo electrónico debe configurarse para que el canal de correo electrónico de las notificaciones funcione.

Para obtener instrucciones sobre la configuración del correo electrónico, consulte [Configuración del correo electrónico](analytics.md).

**Habilitar seguir**

Los componentes deben configurarse para habilitar lo siguiente. Las funciones que permiten lo siguiente son [blog](blog-feature.md), [foro](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [biblioteca de archivos](file-library.md) y [comentarios](comments.md).

Tenga en cuenta que

* Los componentes utilizados dentro de las plantillas de [sitio](sites.md) y [plantillas de grupo](tools-groups.md) de la comunidad ya pueden estar configurados para permitir lo siguiente

* Los perfiles de miembros ya están configurados para permitir que otros miembros sigan

## Notificaciones de la siguiente {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

El botón **Follow** proporciona un medio para seguir entradas como actividades, suscripciones y/o notificaciones. Cada vez que se selecciona el botón **Follow**, es posible activar o desactivar una selección. La selección `Email Subscriptions` solo está presente cuando está configurada.

Si se selecciona algún método de seguimiento, el texto del botón cambia a **Siguiendo**. Para su comodidad, es posible seleccionar `Unfollow All` para desactivar todos los métodos.

Aparecerá el botón **Follow**

* Al ver el perfil de otro miembro
* En una página de características principales, como foros, QnA y blogs
   * Sigue toda la actividad de esa función general
* Para una entrada específica, como un tema de foro, una pregunta de control de calidad o un artículo de blog
   * Sigue toda la actividad de esa entrada específica

## Administración de la configuración de notificación {#managing-notification-settings}

Al seleccionar el vínculo Configuración de notificación de la página Notificaciones , es posible que cada miembro administre cómo se reciben las notificaciones.

El canal web siempre está habilitado.

![chlimage_1-255](assets/chlimage_1-255.png)

El canal de correo electrónico, que se basa en una [configuración adecuada del correo electrónico](email.md), proporciona la misma configuración que para el canal web.

El canal de correo electrónico está desactivado de forma predeterminada.

![chlimage_1-256](assets/chlimage_1-256.png)

Un miembro puede activarlo, pero aun así depende del correo electrónico que se esté configurando.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualización de notificaciones{#viewing-notifications} 

### Notificaciones web {#web-notifications}

Un [asistente creado en el sitio de la comunidad](sites-console.md) ahora incluye un vínculo a la función `Notifications` en la barra de encabezado del sitio que se encuentra encima del banner. A diferencia de los mensajes, las notificaciones se crean para cada sitio de la comunidad, mientras que los mensajes deben habilitarse durante el proceso de creación del sitio.

Al visitar el sitio publicado, seleccionar el enlace `Notifications` mostrará todas las notificaciones del miembro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notificaciones de correo electrónico {#email-notifications}

Cuando el canal de correo electrónico está habilitado, el miembro recibe un correo electrónico que contiene un vínculo al contenido de la web.

![chlimage_1-259](assets/chlimage_1-259.png)

