---
title: Elementos esenciales del blog
seo-title: Blog Essentials
description: Información general del blog
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 4%

---

# Elementos esenciales del blog {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Desde AEM 6.1 Communities, un blog es una actividad comunitaria. Los artículos de blog ahora se publican desde el entorno de publicación, donde anteriormente, los artículos de blog solo podían crearse en el entorno de creación y publicarse .

Los artículos de blog pueden ser creados por cualquier miembro de la comunidad, a menos que estén restringidos a miembros privilegiados.

Esta página proporciona la información esencial para trabajar con la función de blog.

>[!NOTE]
>
>La infraestructura subyacente de la función de blog es la función de diario.

## Elementos esenciales para el cliente {#essentials-for-client-side}

La función de blog consta de dos componentes principales que están disponibles añadiendo la variable [Función del blog](functions.md#blog-function) o añadiendo los componentes a una página en modo de edición de autor.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.journal</td> 
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
   <td>see <a href="blog-feature.md">Función del blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra lateral de blog {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**inclusible**](scf.md#add-or-include-a-communities-component) | No |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propiedades** | see [Función del blog](blog-feature.md) |

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Puntos finales de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Blog {#blog-function}

Una estructura de sitio de la comunidad que incluye el [Bog, función](functions.md#blog-function) se habrá configurado `Blog` y `Blog Sidebar` componentes. La función Blog admite la identificación de un [grupo de usuarios miembro privilegiado](users.md#privileged-members-group).

### Acceso a entradas de blog (UGC) {#accessing-blog-entries-ugc}

UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir del AEM 6.1 Comunidades, se utilizará un [tienda común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales

## Editor principal {#primary-publisher}

Cuando la implementación es un conjunto de servidores de publicación, es necesario identificar un editor principal que sondeará los artículos programados para publicarse.

Consulte [Editor principal](deploy-communities.md#primary-publisher) para obtener más información.

## Permitir medios enriquecidos {#allowing-rich-media}

La plataforma AEM bloquea los vínculos de otros sitios web para evitar los ataques XSS tal como se describe en

* [Protect contra scripts en sitios múltiples (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partir de AEM 6.2, las modificaciones que anteriormente se requerían realizar manualmente se incluyen en el archivo de configuración predeterminado AntiSamy.

El contenido multimedia enriquecido se incrusta en un artículo de blog seleccionando la variable `Embed Media from External Sites` icono:  ![chlimage_1-471](assets/chlimage_1-471.png)
