---
title: Elementos esenciales del blog
seo-title: Elementos esenciales del blog
description: Información general del blog
seo-description: Información general del blog
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---


# Elementos esenciales del blog {#blog-essentials}

Desde AEM comunidades 6.1, un blog es una actividad comunitaria. Los artículos de blog ahora se publican desde el entorno de publicación, donde anteriormente, los artículos de blog solamente podían crearse en el entorno del autor y publicarse.

Los artículos de blog ahora pueden ser creados por cualquier miembro de la comunidad, a menos que estén restringidos a miembros privilegiados.

Esta página proporciona la información esencial para trabajar con la función de blog.

>[!NOTE]
>
>La infraestructura subyacente de la función de blog es la característica de historial.

## Esenciales para el cliente {#essentials-for-client-side}

La función de blog consta de dos componentes principales disponibles mediante la adición de la función [](functions.md#blog-function) Blog o la adición de los componentes a una página en modo de edición de autor.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/historial/componentes/hbs/historial</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.historial</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>consulte Función <a href="blog-feature.md">de blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra lateral de blog {#blog-sidebar}

| **resourceType** | social/historial/componentes/hbs/barra lateral |
|---|---|
| [**inclusible **](scf.md#add-or-include-a-communities-component) | No |
| [**clientllibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propiedades** | consulte Función [de blog](blog-feature.md) |

* [Personalizaciones del lado del cliente](client-customize.md)

## Esenciales para servidor {#essentials-for-server-side}

* [API de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Extremos de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Blog {#blog-function}

Una estructura de sitio de comunidad que incluye la función [](functions.md#blog-function) Bog tendrá componentes `Blog` y `Blog Sidebar` configurados. La función Blog permite identificar un grupo [de usuarios miembros](users.md#privileged-members-group)privilegiados.

### Acceso a entradas de blog (UGC) {#accessing-blog-entries-ugc}

La UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido](moderate-ugc.md)generado por el usuario.

A partir de AEM 6.1 Comunidades, el uso de un almacén [](working-with-srp.md) común para UGC incluye el acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Descripción general](srp.md) del proveedor de recursos de Almacenamiento: introducción y uso del repositorio
* [Elementos esenciales](srp-and-ugc.md) de SRP y UGC: métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) : directrices de codificación
* [Refactorización](socialutils.md) de SocialUtils: asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales

## Editor principal {#primary-publisher}

Cuando la implementación es un conjunto de servidores de publicación, es necesario identificar un editor principal que sondeará los artículos programados para publicarse.

Consulte Editor [principal](deploy-communities.md#primary-publisher) para obtener más información.

## Permitir medios enriquecidos {#allowing-rich-media}

La plataforma AEM bloquea los vínculos de otros sitios web para evitar los ataques XSS como se describe en

* [Protect contra scripts entre sitios (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partir de AEM 6.2, las modificaciones que anteriormente se requerían manualmente se incluyen en el archivo de configuración predeterminado AntiSamy.

Los medios enriquecidos se incorporan en un artículo de blog seleccionando el `Embed Media from External Sites` icono:  ![chlimage_1-471](assets/chlimage_1-471.png)

