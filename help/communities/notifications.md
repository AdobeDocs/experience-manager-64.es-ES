---
title: Notificaciones de comunidades
seo-title: Communities Notifications
description: AEM Communities tiene notificaciones que muestran eventos de interés para el miembro de la comunidad que ha iniciado sesión
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 2%

---

# Notificaciones de comunidades {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

AEM Communities proporciona una sección de notificaciones que muestra eventos de interés para el miembro de la comunidad que ha iniciado sesión.

Las notificaciones son similares a [actividades](essentials-activities.md) y [suscripciones](subscriptions.md) que pueden resultar de

* El miembro que publica contenido
* El miembro que decide seguir a otro miembro
* El miembro que elige seguir temas específicos, artículos y otros subprocesos de contenido

Lo que distingue las notificaciones de actividades y suscripciones es

* Un vínculo a la sección de notificaciones siempre está presente en el encabezado de un sitio de la comunidad
   * Las actividades requieren que [función de flujo de actividad](functions.md#activity-stream-function) para su inclusión en la estructura del sitio de la comunidad
   * Las suscripciones requieren [configuración del correo electrónico](email.md)
* La implementación de las notificaciones se realiza a través de canales ampliables y conectables
   * Las actividades solo están disponibles en la web
   * Las suscripciones solo están disponibles mediante correo electrónico

Como comunidades [FP1](deploy-communities.md#latestfeaturepack), los canales de notificación disponibles son

* El canal web, al que se accede mediante la variable `Notifications` vínculo
* El canal de correo electrónico, disponible cuando el correo electrónico está configurado correctamente

Los canales futuros son móviles y de escritorio.

### Requisitos  {#requirements}

**Configurar correo electrónico**

El correo electrónico debe configurarse para que el canal de correo electrónico de las notificaciones funcione.

Para obtener instrucciones sobre la configuración del correo electrónico, consulte [Configuración del correo electrónico](analytics.md).

**Habilitar seguir**

Los componentes deben configurarse para habilitar lo siguiente. Las funciones que permiten lo siguiente son: [blog](blog-feature.md), [foro](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filelibrary](file-library.md)y [comentarios](comments.md).

Tenga en cuenta que

* Componentes utilizados en la comunidad [plantillas de sitio](sites.md) y [plantillas de grupo](tools-groups.md) ya puede configurarse para permitir lo siguiente

* Los perfiles de miembros ya están configurados para permitir que otros miembros sigan

## Notificaciones de lo siguiente {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

La variable **Seguir** proporciona un medio para seguir entradas como actividades, suscripciones o notificaciones. Cada vez que se usa la variable **Seguir** está seleccionado, es posible activar o desactivar una selección. La variable `Email Subscriptions` La selección solo está presente cuando está configurada.

Si se selecciona cualquier método de seguimiento, el texto del botón cambia a **A continuación**. Para mayor comodidad, es posible seleccionar `Unfollow All` para desactivar todos los métodos.

La variable **Seguir** aparece el botón

* Al ver el perfil de otro miembro
* En una página de características principales, como foros, QnA y blogs
   * Sigue toda la actividad de esa función general
* Para una entrada específica, como un tema de foro, una pregunta de control de calidad o un artículo de blog
   * Sigue toda la actividad de esa entrada específica

## Administración de la configuración de notificaciones {#managing-notification-settings}

Al seleccionar el vínculo Configuración de notificación de la página Notificaciones , es posible que cada miembro administre cómo se reciben las notificaciones.

El canal web siempre está habilitado.

![chlimage_1-255](assets/chlimage_1-255.png)

El canal de correo electrónico, que se basa en las [configuración del correo electrónico](email.md), proporciona la misma configuración que para el canal web.

El canal de correo electrónico está desactivado de forma predeterminada.

![chlimage_1-256](assets/chlimage_1-256.png)

Un miembro puede activarlo, pero aun así depende del correo electrónico que se esté configurando.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualización de notificaciones  {#viewing-notifications}

### Notificaciones web {#web-notifications}

A [asistente creado sitio de comunidad](sites-console.md) ahora incluye un vínculo a la variable `Notifications` en la barra de encabezado del sitio, encima del banner. A diferencia de los mensajes, las notificaciones se crean para cada sitio de la comunidad, mientras que los mensajes deben habilitarse durante el proceso de creación del sitio.

Al visitar el sitio publicado, seleccione la opción `Notifications` el vínculo mostrará todas las notificaciones del miembro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notificaciones por correo electrónico {#email-notifications}

Cuando el canal de correo electrónico está habilitado, el miembro recibe un correo electrónico que contiene un vínculo al contenido de la web.

![chlimage_1-259](assets/chlimage_1-259.png)
