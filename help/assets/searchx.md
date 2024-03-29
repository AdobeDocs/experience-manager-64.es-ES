---
title: Ampliación de la búsqueda de recursos
description: Amplíe las capacidades de búsqueda de [!DNL Experience Manager] Recursos más allá de las búsquedas predeterminadas, busca recursos por cadenas.
contentOwner: AG
feature: Search
role: Developer
exl-id: d68c735f-2699-4923-a7e7-4d1356eae335
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 13%

---

# Ampliación de la búsqueda de recursos {#extending-assets-search}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede ampliar las funciones de búsqueda de Adobe Experience Manager Assets. Fuera de la caja, [!DNL Experience Manager] Los recursos buscan recursos por cadenas.

La búsqueda se realiza a través de la interfaz de QueryBuilder para que la búsqueda se pueda personalizar con varios predicados. Puede superponer el conjunto predeterminado de predicados en el siguiente directorio: `/apps/dam/content/search/searchpanel/facets`.

También puede agregar fichas adicionales al [!DNL Experience Manager] Panel de administración de recursos.

>[!CAUTION]
>
>A partir de [!DNL Experience Manager] 6.4, la IU clásica está en desuso. Para ver el anuncio, consulte [Funciones obsoletas y eliminadas](../release-notes/deprecated-removed-features.md). Se le recomienda utilizar la IU táctil. Para las personalizaciones, consulte [Facetas de búsqueda](search-facets.md).

## Superposición {#overlaying}

Para superponer los predicados preconfigurados, copie el `facets` nodo de `/libs/dam/content/search/searchpanel` a `/apps/dam/content/search/searchpanel/` o especificar otro `facetURL` en la configuración del panel de búsqueda (el valor predeterminado es `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>De forma predeterminada, la estructura de directorios en / `apps` no existe y debe crearse. Asegúrese de que los tipos de nodo coinciden con los de / `libs`.

## Adición de pestañas {#adding-tabs}

Puede agregar fichas de búsqueda adicionales configurándolas en la sección [!DNL Experience Manager] Administrador de recursos. Para crear pestañas adicionales:

1. Crear la estructura de carpetas `/apps/wcm/core/content/damadmin/tabs,`si aún no existe, y copie la `tabs` nodo de `/libs/wcm/core/content/damadmin` y péguelo.
1. Cree y configure la segunda pestaña como desee.

   >[!NOTE]
   >
   >Cuando cree un segundo panel siteadminsearchpanel, asegúrese de establecer un `id` para evitar conflictos de formularios.

## Creación de predicados personalizados {#creating-custom-predicates}

[!DNL Experience Manager] Assets viene con un conjunto de predicados predefinidos que pueden utilizarse para personalizar una página de uso compartido de recursos. La personalización de un recurso compartido de esta forma se explica en [Creación y configuración de una página de uso compartido de recursos](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Además de usar predicados preexistentes, [!DNL Experience Manager] los desarrolladores también pueden crear sus propios predicados utilizando [API del generador de consultas](/help/sites-developing/querybuilder-api.md).

La creación de predicados personalizados requiere conocimientos básicos sobre [Marco de utilidades](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

La práctica recomendada es copiar un predicado existente y ajustarlo. Los predicados de ejemplo se encuentran en `/libs/cq/search/components/predicates`.

### Ejemplo: Crear un predicado de propiedad simple {#example-build-a-simple-property-predicate}

Para crear un predicado de propiedad:

1. Cree una carpeta de componentes en el directorio de proyectos, por ejemplo `/apps/geometrixx/components/titlepredicate`.
1. Añadir `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Añadir `titlepredicate.jsp`.

   ```xml
   <%--
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
   
       });
   
   </script>
   ```

1. Para que el componente esté disponible, hace falta poder editarlo. Para hacer que un componente sea editable, en CRXDE, agregue un nodo `cq:editConfig` de tipo principal `cq:EditConfig`. Para poder eliminar párrafos, agregue una propiedad de varios valores `cq:actions` con un único valor de **ELIMINAR**.
1. Vaya al explorador y a la página de muestra (por ejemplo, `press.html`) cambiar al modo de diseño y activar el nuevo componente para el sistema de párrafos predicado (por ejemplo, **left**).

1. En **Editar** , el nuevo componente ya está disponible en la barra de tareas (que se encuentra en la **Buscar** grupo). Inserte el componente en el **Predicados** y escriba una palabra de búsqueda, por ejemplo, **Diamante** y haga clic en la lupa para iniciar la búsqueda.

   >[!NOTE]
   >
   >Al buscar, asegúrese de escribir el término exactamente, incluidas las mayúsculas y minúsculas correctas.

### Ejemplo: Crear un predicado de grupo simple {#example-build-a-simple-group-predicate}

Para crear un predicado de grupo:

1. Cree una carpeta de componentes en el directorio de proyectos, por ejemplo `/apps/geometrixx/components/picspredicate`.
1. Añadir `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Añadir `titlepredicate.jsp`:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
   
       });
   ```

1. Para que el componente esté disponible, hace falta poder editarlo. Para hacer que un componente sea editable, en CRXDE, agregue un nodo `cq:editConfig` de tipo principal `cq:EditConfig`. Para poder eliminar párrafos, agregue una propiedad de varios valores `cq:actions` con un solo valor de `DELETE`.
1. Vaya al explorador y a la página de muestra (por ejemplo, `press.html`) cambiar al modo de diseño y activar el nuevo componente para el sistema de párrafos predicado (por ejemplo, **left**).
1. En **Editar** , el nuevo componente ya está disponible en la barra de tareas (que se encuentra en la **Buscar** grupo). Inserte el componente en el **Predicados** para abrir el Navegador.

### Widgets de predicados instalados {#installed-predicate-widgets}

Los siguientes predicados están disponibles como widgets preconfigurados de ExtJS.

### Predicado de texto completo {#fulltextpredicate}

| Propiedad | Tipo | Descripción |
|---|---|---|
| predicateName | Cadena | Nombre del predicado. El valor predeterminado es `fulltext` |
| searchCallback | Función | Llamada de retorno para activar la búsqueda en un evento `keyup`. El valor predeterminado es `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Propiedad | Tipo | Descripción |
|---|---|---|
| predicateName | Cadena | Nombre del predicado. El valor predeterminado es `property` |
| propertyName | Cadena | Nombre de la propiedad JCR. El valor predeterminado es `jcr:title` |
| defaultValue | Cadena | Valor predeterminado rellenado previamente. |

### PathPredicate {#pathpredicate}

| Propiedad | Tipo | Descripción |
|---|---|---|
| predicateName | Cadena | Nombre del predicado. El valor predeterminado es `path` |
| rootPath | Cadena | Ruta raíz del predicado. El valor predeterminado es `/content/dam` |
| pathFieldPredicateName | Cadena | El valor predeterminado es `folder` |
| showFlatOption | Booleano | Indicador que muestra la casilla de verificación `search in subfolders`. El valor predeterminado es true. |

### DatePredicate {#datepredicate}

| Propiedad | Tipo | Descripción |
|---|---|---|
| predicateName | Cadena | Nombre del predicado. El valor predeterminado es `daterange` |
| propertyname | Cadena | Nombre de la propiedad JCR. El valor predeterminado es `jcr:content/jcr:lastModified` |
| defaultValue | Cadena | Valor predeterminado predefinido |

### OptionsPredicate {#optionspredicate}

| Propiedad | Tipo | Descripción |
|---|---|---|
| título | Cadena | Añade un título superior adicional |
| predicateName | Cadena | Nombre del predicado. El valor predeterminado es `daterange` |
| propertyname | Cadena | Nombre de la propiedad JCR. El valor predeterminado es `jcr:content/metadata/cq:tags` |
| contraer | Cadena | Contraer nivel. El valor predeterminado es `level1` |
| triggerSearch | Booleano | Indicador para activar la búsqueda al marcar. El valor predeterminado es false |
| searchCallback | Función | Llamada de retorno para activar la búsqueda. El valor predeterminado es `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Número | Tiempo de espera antes de que se active searchCallback. El valor predeterminado es 800 ms |

## Personalización de resultados de búsqueda {#customizing-search-results}

La presentación de los resultados de búsqueda en una página Uso compartido de recursos se rige por la lente seleccionada. [!DNL Experience Manager] Assets viene con un conjunto de objetivos predefinidos que se pueden utilizar para personalizar una página de uso compartido de recursos. La personalización de un recurso compartido de esta forma se explica en [Creación y configuración de una página de uso compartido de recursos](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Además de usar lentes preexistentes, [!DNL Experience Manager] los desarrolladores también pueden crear sus propias lentes.
