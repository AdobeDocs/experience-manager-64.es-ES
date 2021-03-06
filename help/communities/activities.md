---
title: Función de flujo de actividad
seo-title: Función de flujo de actividad
description: Actividades de un miembro de la comunidad que ha iniciado sesión
seo-description: Actividades de un miembro de la comunidad que ha iniciado sesión
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Función de flujo de actividad {#activity-streams-feature}

## Introducción {#introduction}

Las actividades de un miembro de la comunidad firmado, como publicar en un foro o blog, se recopilan en un flujo que puede filtrarse y mostrarse de diversas maneras a través de la configuración del componente `Activity Streams`.

La capacidad de seguir agrega otra vista de actividades cuando los miembros de la comunidad siguen publicaciones de interés o siguen las actividades de otros miembros de la comunidad.

Esta sección de la documentación describe

* Añadir el componente Flujos de Actividad en un sitio AEM
* Configuración del componente Flujos de Actividad

## Añadir flujos de Actividad a una página {#adding-activity-streams-to-a-page}

Si desea agregar un componente `Activity Streams` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Activity Streams`

y arrástrelo a su lugar en una página donde deberían aparecer los flujos de actividad.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se incluyen las [bibliotecas requeridas del lado del cliente](essentials-activities.md#essentials-for-client-side), así es como aparecerá el componente `Activity Streams`:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuración de flujos de Actividad {#configuring-activity-streams}

Seleccione el componente `Activity Streams` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-196](assets/chlimage_1-196.png)

En la ficha **[!UICONTROL Actividades de usuario]**, especifique qué actividades mostrar:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Número máximo de]**
actividadesEl número de actividades que se mostrarán
* **[!UICONTROL Ruta del]**
recurso del flujoDeje en blanco para establecer de forma predeterminada el sitio de la comunidad o el grupo de la comunidad. La ruta del recurso de flujo identifica el origen de las actividades. El valor predeterminado está en blanco.
* **[!UICONTROL Mostrar vista de Actividades de usuario]**
activada, la página de actividades incluirá una ficha que filtros actividades basadas en las generadas dentro de la comunidad por el miembro actual. El valor predeterminado está marcado.
* **[!UICONTROL Mostrar todas las Actividades]**
VerSi está activada, la página actividades incluirá una ficha que incluye todas las actividades generadas dentro de la comunidad a la que tiene acceso el miembro actual. El valor predeterminado está marcado.
* **[!UICONTROL Mostrar]**
vista siguienteSi está activada, la página actividades incluirá una ficha que filtros actividades en función de las que sigue el miembro actual. El valor predeterminado está marcado.

## Vista siguiente {#following-view}

Los componentes deben configurarse para habilitar lo siguiente. Las funciones que permiten lo siguiente son [blog](blog-feature.md), [foro](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [biblioteca de archivos](file-library.md) y [comentarios](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

El botón **Seguir** proporciona un medio para seguir las entradas como actividades, [notificaciones](notifications.md) y/o [suscripciones](subscriptions.md). Cada vez que se selecciona el botón **Seguir**, es posible activar o desactivar una selección. La selección `Email Subscriptions` sólo está presente cuando está configurada.

Si se selecciona cualquier método de seguimiento, el texto del botón cambia a **Siguiente**. Para mayor comodidad, es posible seleccionar `Unfollow All` para desactivar todos los métodos.

Aparecerá el botón **Seguir**:

* Al ver el perfil de otro miembro
* En una página de características principal, como foros, QnA y blogs
   * Sigue toda la actividad de esa función general

* Para una entrada específica, como un tema del foro, una pregunta de preguntas y respuestas o un artículo del blog
   * Sigue toda la actividad de esa entrada específica

## Información adicional {#additional-information}

Puede encontrar más información en la página [Actividad Streams Essentials](essentials-activities.md) para desarrolladores.
