---
title: Función de búsqueda
seo-title: Search Feature
description: Adición y configuración de la búsqueda en un sitio de Communities
seo-description: Adding and configuring Search to a Communities site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 2%

---

# Función de búsqueda {#search-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La función de búsqueda funciona con otras funciones, como los foros, para proporcionar la capacidad de buscar contenido.

Al añadir la capacidad de buscar anuncios introducidos por miembros de la comunidad, denominados contenido generado por el usuario (UGC), hay dos componentes: [ `Search`](#search-features) y [ `Search Results`](#search-results).

La página que incluye el `Search Results` admite tanto la búsqueda como la visualización de resultados.

La página que incluye el `Search`proporciona un lugar para iniciar una búsqueda con resultados que aparecen en el `Search Results` página.

La función de búsqueda se puede utilizar con cualquier otra función que permita a los visitantes del sitio y a los miembros ver el contenido.

## Búsqueda {#search-features}

### Agregar una búsqueda a una página {#add-search-to-a-page}

Para agregar un `Search` a una página en modo de autor, utilice el navegador de componentes para localizar `Communities / Search` y arrástrela a su lugar en una página. Uso de `Search` requiere una segunda página para `Search Results.`

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la biblioteca del cliente necesaria, `cq.social.hbs.search`, se incluye, así es como se muestra la variable `Search` aparecerá el componente.

![chlimage_1-373](assets/chlimage_1-373.png)

### Configurar la búsqueda agregada {#configure-the-added-search}

Seleccione la colocación `Search` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-374](assets/chlimage_1-374.png)

En el **[!UICONTROL Configuración de búsqueda]** , especifique cómo se buscan las rutas cuando un visitante introduce una consulta.

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL Rutas de búsqueda]**
Al agregar rutas de búsqueda mediante el botón Agregar elemento, la búsqueda de contenido es limitada. Por ejemplo, para limitar la búsqueda a un foro específico, seleccione un componente de foro ubicado en una página:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Página de resultados]**
Los resultados aparecerán en una página independiente especificada utilizando el explorador para seleccionar una página que contenga la variable 
`Search Results` componente.

## Resultados de la búsqueda {#search-results}

### Agregar resultados de búsqueda a una página {#add-search-results-to-a-page}

Para agregar un `Search Results` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Search Results`

y arrástrela a su lugar en una página. A diferencia del componente Búsqueda, no se necesita una segunda página, ya que los resultados se mostrarán en la misma página.

Si utiliza Buscar en otra parte dentro del sitio web, esta es una página con `Search Results` puede configurarse para que sea el `Result Page` para cualquiera o todas las instancias de `Search`.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la biblioteca del cliente necesaria, `cq.social.hbs.search`, se incluye, así es como se muestra la variable `Search Result` aparecerá el componente:

![chlimage_1-376](assets/chlimage_1-376.png)

### Configurar el resultado de la búsqueda agregada {#configure-the-added-search-result}

Seleccione la colocación `Search Results` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-377](assets/chlimage_1-377.png)

En el **[!UICONTROL Configuración de resultados de búsqueda]** , se puede especificar qué rutas se incluyen en la búsqueda cuando un visitante introduce una consulta.

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL Resultados de búsqueda por página]**
Defina el número de temas/anuncios que se muestran por página. El valor predeterminado es 10.

* **[!UICONTROL Rutas de búsqueda]**
Al agregar rutas de búsqueda mediante el botón Agregar elemento, la búsqueda de contenido es limitada.

## Información adicional {#additional-information}

Puede encontrar más información en la [Elementos básicos de búsqueda](search-implementation.md) para desarrolladores.
