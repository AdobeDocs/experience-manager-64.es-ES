---
title: Tendencias de actividad
seo-title: Activity Trends
description: Adición de un componente de Lista de actividades de la comunidad a una página
seo-description: Adding a Community Activity List component to a page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 6%

---

# Tendencias de actividad {#activity-trends}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La variable `Community Activity List` proporciona la capacidad de agregar información de tendencias con respecto a anuncios y vistas por miembros, así como anuncios y vistas de contenido.

Esta sección de la documentación describe

* Adición de la variable `Community Activity List` componente a un [sitio de la comunidad](overview.md#community-sites)

* Ajustes de configuración para `Community Activity List` componente

## Requisito {#requirement}

Los datos del `Community Activity List` solo está disponible cuando Adobe Analytics tiene licencia y está configurado para el sitio de la comunidad.

Consulte [Funciones de Configuración de Analytics para Communities](analytics.md).

## Adición de una lista de actividades de la comunidad a una página {#adding-a-community-activity-list-to-a-page}

Para agregar un `Community Activity List` a una página en modo de autor, busque el componente `Communities / Community Activity List` y arrástrela a su lugar en una página.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando se coloca por primera vez en una página de un sitio de comunidad, así es como aparece el componente:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuración de la lista de actividades de la comunidad  {#configuring-community-activity-list}

Seleccione la colocación `Community Activity List` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-228](assets/chlimage_1-228.png)

En el **[!UICONTROL Comentarios]** especifique si aparecen los comentarios de los archivos cargados y cómo aparecerán:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Especifique si desea mostrar datos sobre los miembros de la comunidad o el contenido generado por el usuario (UGC).

   Seleccionar de
   * `Members`
   * `Content`

   El valor predeterminado es `Members`.

* **[!UICONTROL Título que se mostrará]**

   Un título descriptivo que se mostrará encima de los datos, como `Trending Content`.

   El valor predeterminado no es título.

* **[!UICONTROL Número de de visualizaciones]**

   El número de elementos que desea enumerar.

   El valor predeterminado es 10.

* **[!UICONTROL Tipo de actividad]**

   Seleccione uno de
   * `Views`(visitas a la página)
   * `Posts`(creación de UGC)
   * `Follows`
   * `Likes`

   El valor predeterminado es Vistas.

* **[!UICONTROL Período de tiempo]**

   Seleccione uno de
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   El valor predeterminado es `Total`.

* **[!UICONTROL Ruta de contexto]**

   Proporciona la capacidad de ampliar el ámbito de la actividad a un subconjunto del sitio, como un Blog específico.

   El valor predeterminado es todo el sitio de la comunidad.

* **[!UICONTROL Suma de recuento de miembros]**

   Cuando está desactivada, solo se cuentan los anuncios de nivel superior. Por ejemplo, si el contexto es la página raíz (el valor predeterminado), se muestra una `Activity Type`de `Posts`nunca mostrará ninguna actividad, ya que no se puede publicar contenido en la página raíz. Cuando se selecciona, se incluyen los recuentos de todas las páginas descendientes.

   El valor predeterminado está marcado.

## Página de ejemplo con 4 componentes {#example-page-with-components}

**Visitantes principales** config: Tipo = Miembros, Tipo de actividad = Vistas

**Colaboradores principales** config: Tipo = Miembros, Tipo de actividad = Anuncios

**Contenido principal** config: Tipo = Contenido, Tipo de actividad = Vistas,

**Tendencias de contenido** config: Tipo = Contenido, Tipo de actividad = Anuncios

![chlimage_1-230](assets/chlimage_1-230.png)
