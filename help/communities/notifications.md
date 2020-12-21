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
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Notificaciones de comunidades {#communities-notifications}

## Información general {#overview}

AEM Communities proporciona una sección de notificaciones que muestra eventos de interés para el miembro de la comunidad que ha firmado.

Las notificaciones son similares a [actividades](essentials-activities.md) y [suscripciones](subscriptions.md) como pueden resultar de

* El miembro que publica contenido
* El miembro que decide seguir a otro miembro
* El miembro decide seguir temas específicos, artículos y otros hilos de contenido

Lo que distingue las notificaciones de las actividades y suscripciones es

* Siempre hay un vínculo a la sección de notificaciones en el encabezado de un sitio de comunidad
   * Las actividades requieren que la [función de flujo de actividad](functions.md#activity-stream-function) se incluya en la estructura del sitio de la comunidad
   * Las suscripciones requieren [configuración de correo electrónico](email.md)
* La implementación de las notificaciones se realiza mediante canales escalables y conectables
   * Las actividades solo están disponibles en la web
   * Las suscripciones solo están disponibles mediante correo electrónico

A partir de Communities [FP1](deploy-communities.md#latestfeaturepack), los canales de notificación disponibles son

* El canal web, al que se accede mediante el vínculo `Notifications`
* El canal de correo electrónico, disponible cuando el correo electrónico está configurado correctamente

Los canales futuros son móviles y de escritorio.

### Requisitos {#requirements}

**Configurar correo electrónico**

El correo electrónico debe configurarse para que el canal de correo electrónico de las notificaciones funcione.

Para obtener instrucciones sobre cómo configurar el correo electrónico, consulte [Configuración del correo electrónico](analytics.md).

**Habilitar Seguir**

Los componentes deben configurarse para habilitar lo siguiente. Las funciones que permiten lo siguiente son [blog](blog-feature.md), [foro](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [biblioteca de archivos](file-library.md) y [comentarios](comments.md).

Tenga en cuenta que:

* Los componentes utilizados dentro de las plantillas de [sitio](sites.md) y [plantillas de grupo](tools-groups.md) de la comunidad ya pueden configurarse para permitir lo siguiente

* Los perfiles de miembros ya están configurados para permitir que otros miembros sigan

## Notificaciones de: {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

El botón **Seguir** proporciona un medio para seguir las entradas como actividades, suscripciones y/o notificaciones. Cada vez que se selecciona el botón **Seguir**, es posible activar o desactivar una selección. La selección `Email Subscriptions` sólo está presente cuando está configurada.

Si se selecciona cualquier método de seguimiento, el texto del botón cambia a **Siguiente**. Para mayor comodidad, es posible seleccionar `Unfollow All` para desactivar todos los métodos.

Aparecerá el botón **Seguir**

* Al ver el perfil de otro miembro
* En una página de características principal, como foros, QnA y blogs
   * Sigue toda la actividad de esa función general
* Para una entrada específica, como un tema del foro, una pregunta de preguntas y respuestas o un artículo del blog
   * Sigue toda la actividad de esa entrada específica

## Administración de la configuración de notificación {#managing-notification-settings}

Al seleccionar el vínculo Configuración de notificación en la página Notificaciones, cada miembro puede administrar cómo se reciben las notificaciones.

El canal web siempre está habilitado.

![chlimage_1-255](assets/chlimage_1-255.png)

El canal de correo electrónico, que depende de la configuración [correcta del correo electrónico](email.md), proporciona la misma configuración que para el canal Web.

El canal de correo electrónico está desactivado de forma predeterminada.

![chlimage_1-256](assets/chlimage_1-256.png)

Un miembro puede activarlo, pero aún depende de la configuración del correo electrónico.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualización de notificaciones{#viewing-notifications} 

### Notificaciones Web {#web-notifications}

Un [asistente creó un sitio de comunidad](sites-console.md) ahora incluye un vínculo a la función `Notifications` en la barra de encabezado del sitio sobre el letrero. A diferencia de los mensajes, las notificaciones se crean para cada sitio de la comunidad, mientras que los mensajes se deben habilitar durante el proceso de creación del sitio.

Al visitar el sitio publicado, al seleccionar el vínculo `Notifications` se mostrarán todas las notificaciones del miembro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notificaciones de correo electrónico {#email-notifications}

Cuando el canal de correo electrónico está activado, el miembro recibe un correo electrónico que contiene un vínculo al contenido de la web.

![chlimage_1-259](assets/chlimage_1-259.png)

