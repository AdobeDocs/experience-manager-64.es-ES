---
title: Etiquetado del contenido generado por el usuario
seo-title: Tagging User Generated Content
description: El etiquetado del contenido generado por el usuario (UGC) es la forma en que los miembros de la comunidad pueden ayudar a otros miembros a buscar contenido
seo-description: Tagging of user generated content (UGC) is how community members can help other members search for content
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
role: Admin
exl-id: 834df392-df38-498c-9e2a-489484e20e0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 6%

---

# Etiquetado del contenido generado por el usuario {#tagging-user-generated-content}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

El etiquetado del contenido generado por el usuario (UGC) es el modo en que los miembros de la comunidad pueden ayudar a otros miembros a buscar contenido.

Normalmente, los autores y administradores aplican las etiquetas en el entorno de creación. Etiquetar UGC es único en el sentido de que los miembros de la comunidad aplican las etiquetas UGC en el entorno de publicación.

Los espacios de nombres y las taxonomías de etiquetas son los mismos para ambas aplicaciones.

## Funciones de Communities {#communities-features}

Las funciones de AEM Communities que se pueden configurar para permitir el etiquetado son

* [Blog](blog-feature.md)
* [Calendario](calendar.md)
* [Biblioteca de archivos](file-library.md)
* [Foro](forum.md#configuretheaddedforum)
* [Preguntas y respuestas](working-with-qna.md)

## Administración de etiquetas {#administering-tags}

Consulte [Administración de etiquetas](../../help/sites-administering/tags.md#tagging-console) para crear y administrar áreas de nombres y taxonomías de etiquetas.

Consulte [Aspectos básicos de las etiquetas](tag.md) para obtener información del desarrollador.

Consulte [Uso de la nube de etiquetas social](tagcloud.md) para agregar un componente de Social Tag Cloud a una página para facilitar la búsqueda de UGC publicado con las etiquetas aplicadas.

### Permisos de etiquetas {#tag-permissions}

Los permisos predeterminados se establecen para que todos los usuarios del entorno de publicación no puedan leer los espacios de nombres de etiquetas.

Dado que las etiquetas se aplican a UGC en el entorno de publicación, el permiso de lectura debe estar habilitado para los miembros de la comunidad para que puedan seleccionar las etiquetas que desee aplicar.

Consulte [Configuración de permisos de etiquetas](../../help/sites-administering/tags.md#setting-tag-permissions).

A continuación se muestra cómo aparece en CRXDE cuando un administrador aplica permisos de lectura a `/etc/tag/discussions` para el grupo `*Community Engage Members*`.

![chlimage_1-74](assets/chlimage_1-74.png)
