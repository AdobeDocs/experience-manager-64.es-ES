---
title: Tendencias de actividad
seo-title: Tendencias de actividad
description: Añadir un componente de Lista de Actividad comunitaria en una página
seo-description: Añadir un componente de Lista de Actividad comunitaria en una página
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 4%

---


# Tendencias de actividad {#activity-trends}

## Introducción {#introduction}

El componente `Community Activity List` permite agregar información de tendencias con respecto a publicaciones y vistas de miembros, así como anuncios y vistas de contenido.

Esta sección de la documentación describe

* Añadir el componente `Community Activity List` en un [sitio de comunidad](overview.md#community-sites)

* Configuración del componente `Community Activity List`

## Requisito {#requirement}

Los datos para `Community Activity List` sólo están disponibles cuando Adobe Analytics tiene licencia y está configurado para el sitio de la comunidad.

Consulte [Configuración de Analytics para funciones de comunidades](analytics.md).

## Añadir una Lista de Actividad de comunidad en una página {#adding-a-community-activity-list-to-a-page}

Para agregar un componente `Community Activity List` a una página en modo de autor, localice el componente `Communities / Community Activity List` y arrástrelo a su lugar en una página.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se coloca por primera vez en una página de un sitio de comunidad, así es como aparece el componente:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuración de la Lista de Actividad de comunidad {#configuring-community-activity-list}

Seleccione el componente `Community Activity List` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-228](assets/chlimage_1-228.png)

En la ficha **[!UICONTROL Comentarios]**, especifique si aparecen los comentarios de los archivos cargados y cómo aparecen:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Especifique si desea mostrar datos sobre miembros de la comunidad o contenido generado por el usuario (UGC).

   Seleccionar de
   * `Members`
   * `Content`

   El valor predeterminado es `Members`.

* **[!UICONTROL Título que se mostrará]**

   Un título descriptivo que se muestra encima de los datos, como `Trending Content`.

   El valor predeterminado no es un título.

* **[!UICONTROL Número de de visualizaciones]**

   Número de elementos que se van a lista.

   El valor predeterminado es 10.

* **[!UICONTROL Tipo de actividad]**

   Seleccione uno de los
   * `Views`(visitas a la página)
   * `Posts`(creación de UGC)
   * `Follows`
   * `Likes`

   El valor predeterminado es Vistas.

* **[!UICONTROL Período de tiempo]**

   Seleccione uno de los
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   El valor predeterminado es `Total`.

* **[!UICONTROL Ruta de contexto]**

   Proporciona la capacidad de ampliar el ámbito de la actividad a un subconjunto del sitio, como un blog específico.

   El valor predeterminado es todo el sitio de la comunidad.

* **[!UICONTROL Suma de recuento de miembros]**

   Cuando no está marcada (desactivada), solo se cuentan las publicaciones de nivel superior. Por ejemplo, si el contexto es la página raíz (el valor predeterminado), un `Activity Type`de `Posts`nunca mostrará ninguna actividad, ya que no se puede publicar contenido en la página raíz. Cuando se selecciona, se incluyen los recuentos de todas las páginas descendientes.

   El valor predeterminado está marcado.

## Ejemplo de página con 4 componentes {#example-page-with-components}

**Principales** visitantesConfiguración: Tipo = Miembros, tipo de Actividad = Vistas

**Contributorsconfig** principal: Tipo = Miembros, tipo de Actividad = Anuncios

**Configuración de** contenido superior: Tipo = Contenido, tipo de Actividad = Vistas,

**Tendencia de** Contentconfig: Tipo = Contenido, tipo de Actividad = Anuncios

![chlimage_1-230](assets/chlimage_1-230.png)
