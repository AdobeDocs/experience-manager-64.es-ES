---
title: Esenciales del catálogo
seo-title: Catalog Essentials
description: Información general del catálogo
seo-description: Catalog overview
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
exl-id: 1e0a7cab-39b9-4c90-810c-c93fb76c3869
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 6%

---

# Esenciales del catálogo {#catalog-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de catálogo de los sitios de la comunidad de habilitación.

La función de catálogo, cuando se incluye en un sitio de la comunidad, permite a los miembros de la comunidad examinar y seleccionar los recursos de habilitación enumerados en un catálogo.

La variable [ `enablement catalog` componente](catalog.md) permite a los miembros de la comunidad acceder a un catálogo de [recursos de habilitación](resources.md). El uso de etiquetas AEM es una parte importante de la gestión del aspecto de los recursos de habilitación en un catálogo.

Consulte [Etiquetado de recursos de habilitación](tag-resources.md).

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/activación/componentes/hbs/catálogo</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr> 
  <tr> 
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.catalog<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learn.path</td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/catalog.hbs<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/clientlibs/catalog.css</td> 
  </tr> 
  <tr> 
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="catalog.md">Función de catálogo</a></td> 
  </tr> 
 </tbody> 
</table>

## Elementos esenciales para el servidor {#essentials-for-server-side}

### Función Catálogo {#catalog-function}

Una estructura de sitio de la comunidad que incluye el [Función Catálogo](functions.md#catalog-function), incluye un `enablement catalog` componente.

### Prefiltros {#pre-filters}

Cuando se añade una función Catálogo a un sitio de comunidad, es posible restringir los recursos de habilitación y las rutas de aprendizaje que aparecen en el catálogo especificando un prefiltro. Esto se hace estableciendo propiedades en la instancia del recurso de catálogo para el sitio.

Con el ejemplo de [Tutorial de habilitación](getting-started-enablement.md):

* Sobre el autor
* Uso [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md)

   * Como [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* Vaya al recurso de catálogo en la página de catálogo

   * Por ejemplo, `/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`. 

* Añadir un nodo de filtros secundarios

   * Seleccione el `catalog`node
   * Select **[!UICONTROL Crear nodo]**

      * Nombre: `filters`
      * Tipo: `nt:unstructured`
   * Select **[!UICONTROL Guardar todo]**


* Agregar `se_resource-tags` a la `filters` node

   * Seleccione el `filters` node
   * Añadir una propiedad Multi

      * Nombre: `se_resource-tags`
      * Tipo: cadena
      * Valor: *&lt;enter a=&quot;&quot; span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />TagID](#pre-filter-tagids)>*[
      * Select **[!UICONTROL Multi]**
      * Select **[!UICONTROL Agregar]**

         * En el cuadro de diálogo emergente, seleccione `+` para agregar identificadores de etiquetas prefiltrados adicionales

* Volver a publicar el sitio de la comunidad

![chlimage_1-189](assets/chlimage_1-189.png)

#### TagID prefiltrados {#pre-filter-tagids}

El filtro previo [TagIDs](../../help/sites-developing/framework.md#tagid) debe coincidir exactamente con las etiquetas aplicadas a los recursos de habilitación. Se pueden ver en la sección `resources` carpeta del sitio como valores de la propiedad `se_resource-tags`.

![chlimage_1-190](assets/chlimage_1-190.png)

### API de referencia {#reference-apis}

* [API de habilitación](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API de informes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API de informes de Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/model/api/package-summary.html)
