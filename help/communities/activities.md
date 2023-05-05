---
title: Función Flujos de actividad
seo-title: Activity Streams Feature
description: Actividades de un miembro de la comunidad que ha iniciado sesión
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Función Flujos de actividad {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Las actividades de un miembro de la comunidad que ha firmado, como la publicación en un foro o blog, se recopilan en un flujo que puede filtrarse y mostrarse de varias maneras a través de la configuración de la `Activity Streams` componente.

La capacidad de seguir agrega otra visión de las actividades cuando los miembros de la comunidad siguen publicaciones de interés o siguen las actividades de otros miembros de la comunidad.

Esta sección de la documentación describe

* Adición del componente Flujos de actividad a un sitio AEM
* Ajustes de configuración del componente Flujos de actividad

## Adición de flujos de actividad a una página {#adding-activity-streams-to-a-page}

Si desea agregar un `Activity Streams` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Activity Streams`

y arrástrela a su lugar en una página en la que deberían aparecer las emisiones de actividad.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](essentials-activities.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Activity Streams` aparecerá el componente:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuración de flujos de actividad {#configuring-activity-streams}

Seleccione la colocación `Activity Streams` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-196](assets/chlimage_1-196.png)

En el **[!UICONTROL Actividades del usuario]** , especifique qué actividades mostrar:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Número máximo de actividades]**
El número de actividades que se van a mostrar
* **[!UICONTROL Ruta de recurso de flujo]**
Déjelo en blanco para acceder de forma predeterminada al sitio de la comunidad o al grupo de la comunidad. La ruta del recurso de flujo identifica el origen de las actividades. El valor predeterminado es en blanco.
* **[!UICONTROL Mostrar vista de actividades del usuario]**
si se selecciona, la página actividades incluirá una pestaña que filtra las actividades en función de las generadas dentro de la comunidad por el miembro actual. El valor predeterminado está marcado.
* **[!UICONTROL Mostrar la vista de todas las actividades]**
Si se selecciona, la página actividades incluirá una pestaña que incluye todas las actividades generadas dentro de la comunidad a la que tiene acceso el miembro actual. El valor predeterminado está marcado.
* **[!UICONTROL Mostrar la siguiente vista]**
Si se selecciona, la página actividades incluirá una pestaña que filtra las actividades en función de las que sigue el miembro actual. El valor predeterminado está marcado.

## Vista siguiente {#following-view}

Los componentes deben configurarse para habilitar lo siguiente. Las funciones que permiten lo siguiente son: [blog](blog-feature.md), [foro](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filelibrary](file-library.md)y [comentarios](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

La variable **Seguir** proporciona un medio para seguir entradas como actividades, [notificaciones](notifications.md)y/o [suscripciones](subscriptions.md). Cada vez que se usa la variable **Seguir** está seleccionado, es posible activar o desactivar una selección. La variable `Email Subscriptions` La selección solo está presente cuando está configurada.

Si se selecciona cualquier método de seguimiento, el texto del botón cambia a **A continuación**. Para mayor comodidad, es posible seleccionar `Unfollow All` para desactivar todos los métodos.

La variable **Seguir** aparecerá:

* Al ver el perfil de otro miembro
* En una página de características principales, como foros, QnA y blogs
   * Sigue toda la actividad de esa función general

* Para una entrada específica, como un tema de foro, una pregunta de control de calidad o un artículo de blog
   * Sigue toda la actividad de esa entrada específica

## Información adicional {#additional-information}

Puede encontrar más información en la [Elementos esenciales de flujos de actividad](essentials-activities.md) para desarrolladores.
