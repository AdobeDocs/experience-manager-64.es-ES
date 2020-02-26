---
title: Adición de funciones de Search&amp;Promocionar a la página
seo-title: Adición de funciones de Search&amp;Promocionar a la página
description: Integrando las capacidades de Search&amp;Promote en su sitio Web, puede utilizar los componentes Search&amp;Promote para agregar características a sus páginas, tales como búsqueda de palabras clave, perfeccionamiento de búsqueda de página de resultados de búsqueda y titulares.
seo-description: Integrando las capacidades de Search&amp;Promote en su sitio Web, puede utilizar los componentes Search&amp;Promote para agregar características a sus páginas, tales como búsqueda de palabras clave, perfeccionamiento de búsqueda de página de resultados de búsqueda y titulares.
uuid: 8831aa56-9d7f-44ca-9d32-5901bf762154
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 277d7e67-5778-48cb-89bb-29bcc734a485
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Adding Search&amp;Promote features to your page {#adding-search-promote-features-to-your-page}

To integrate Search&amp;Promote capabilities in your web site, use the [!UICONTROL Search&amp;Promote] components to add the following features to your pages:

* Búsqueda de palabras clave
* Página de resultados de búsqueda
* Perfeccionamiento de la búsqueda
* Banners

Tenga en cuenta que puede utilizar las capacidades de Search&amp;Promote solo si el administrador de AEM las ha activado. Consulte [Integración con Adobe Search&amp;Promote](/help/sites-administering/search-and-promote.md).

Las facetas se configuran en el servidor de Search&amp;Promote, al igual que la información que cada componente proporciona. En la siguiente tabla se incluye una descripción breve de cada componente. En las secciones posteriores se proporciona información detallada acerca de su aplicación.

<table> 
 <tbody> 
  <tr> 
   <th>Componente Search&amp;Promote</th> 
   <th>Descripción</th> 
  </tr> 
  <tr> 
   <td>Banners</td> 
   <td>Muestra anuncios de letreros. Banners are selected based on data gathered through Search&amp;Promote.<br /> </td> 
  </tr> 
  <tr> 
   <td>Rutas de exploración</td> 
   <td>Muestra la palabra clave de búsqueda y la secuencia de filtros que el usuario ha aplicado a los resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Casilla de verificación: faceta</td> 
   <td>Una lista de casillas de verificación para seleccionar facetas para filtrar resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Faceta desplegable</td> 
   <td>Lista desplegable de facetas para filtrar los resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Faceta de lista de vínculo</td> 
   <td>Lista de vínculos de facetas para filtrar los resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Paginación</td> 
   <td>Controles para navegar por las páginas de resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Resultados</td> 
   <td>Muestra los resultados de una búsqueda de palabras clave.</td> 
  </tr> 
  <tr> 
   <td>Búsqueda </td> 
   <td>Agrega un campo de búsqueda a la página.</td> 
  </tr> 
 </tbody> 
</table>

## Creación de la página de resultados de búsqueda {#creating-the-search-results-page}

Utilice la consola WCM Websites para crear una página en la que se mostrarán los resultados de la búsqueda. Los resultados de una búsqueda de cualquier componente de búsqueda pueden aparecer en esta página si utiliza el mismo servicio de Search&amp;Promote. 

Los componentes que permiten a los usuarios revisar resultados de la búsqueda son Resultados y Paginación. El componente **[!UICONTROL Resultados]** no tiene propiedades configurables en modo Edición o Diseño.  El componente Resultados simplemente enumera los resultados de la búsqueda, en los que se ofrecen vínculos a otras páginas, y muestra la cantidad de resultados para la palabra clave de búsqueda. 

![srchresultscomp](assets/srchresultscomp.png)

El componente **[!UICONTROL Paginación]** permite a los usuarios navegar por varias páginas de resultados de la búsqueda. El usuario puede ver el número de páginas, desplazarse a la página siguiente o anterior, seleccionar una página para abrirla o consolidar los resultados en una página. 

![srchpaginación](assets/srchpagination.png)

You can configure the following component properties in [!UICONTROL Edit] mode to control runtime behavior:

* **[!UICONTROL Ocultar una sola página]** de resultados: seleccione esta opción para ocultar los controles de navegación de la página cuando la búsqueda devuelve una sola página de resultados.
* **[!UICONTROL Ocultar primero/último]** : seleccione esta opción para evitar que los usuarios salten a la primera o a la última página de resultados.
* **[!UICONTROL Ocultar anterior/siguiente]** : determina si los usuarios pueden navegar por las páginas de resultados en relación con la página actual.
* **[!UICONTROL Ocultar ver todo]** : determina si el usuario puede consolidar todos los resultados de búsqueda en una sola página. Normalmente, el uso de datos en páginas permite un uso más eficaz de los recursos del servidor. Seleccione esta opción para impedir la transferencia de conjuntos de datos de gran tamaño en un mensaje de respuesta.

## Activación del filtro de resultados por facetas {#enabling-the-filtering-of-results-by-facets}

Puede permitir a los usuarios filtrar resultados de búsqueda por facetas. The **[!UICONTROL Checkbox List Facet]**, **[!UICONTROL Dropdown Facet]**, and **[!UICONTROL Link List Facet]** components enable users to select one or more facets for filtering. Si se utilizan estos componentes, debe incluir el componente **[!UICONTROL Rutas de exploración]**. Las rutas de exploración indican los filtros actuales que se utilizan.

The **[!UICONTROL Checkbox List Facet**, **[!UICONTROL Dropdown Facet]**, and **[!UICONTROL Link List Facet]** components each have the following properties that you configure in **[!UICONTROL Edit]** mode:

* **[!UICONTROL Nombre]** de faceta: el nombre de la faceta que se utiliza para los filtros.

El componente **[!UICONTROL Faceta de lista de casilla de verificación]** muestra una lista de facetas con una casilla de verificación correspondiente. Utilice **[!UICONTROL Faceta de lista de casilla de verificación]** de modo que los usuarios puedan ver un subconjunto de resultados que incluyen elementos de varias facetas. Por ejemplo, la faceta Marca es adecuada porque varias marcas proporcionan el mismo tipo de producto.

Aparece una casilla de verificación para cada faceta asociada a un resultado de búsqueda. Cuando un usuario selecciona una casilla de verificación, la página se vuelve a cargar con un conjunto de resultados actualizado. Todas las casillas permanecen en la página para que los clientes puedan añadir o quitar facetas al filtro en cualquier momento:

![sandpcheckboxcomp](assets/sandpcheckboxcomp.png)

El componente **[!UICONTROL Faceta desplegable]** permite a los clientes seleccionar un elemento de faceta de una lista desplegable. Este componente es de utilidad cuando quiere que los clientes se centren en un solo elemento de faceta a la vez. Por ejemplo, la faceta Departamento es adecuada para permitir a los clientes refinar las búsquedas de producto por sexo. Juan busca *tejanos* y luego filtra con el departamento Hombres. 

La lista desplegable se rellena con las facetas asociadas a todos los resultados de la búsqueda. Al seleccionar un elemento de la lista desplegable, la página se vuelve a cargar con un conjunto de resultados actualizado. Los elementos de la lista desplegable no cambian para que los clientes puedan cambiar de una faceta a otra en cualquier momento. 

![sandpdropdownDepartment](assets/sandpdropdowndepartment.png)

El componente **[!UICONTROL Faceta de lista de vínculo]** permite a los clientes restringir progresivamente la selección de elementos categorizados bajo varios miembros de faceta o facetas.

Los miembros de faceta aparecen como una lista de vínculos. El texto de cada vínculo es el nombre de un miembro de faceta asociado a los resultados de búsqueda actuales. Cuando un cliente hace clic en un vínculo de faceta, la página se vuelve a cargar y se muestra un subconjunto de resultados. La lista de vínculos se actualiza en consecuencia para permitir una selección aún más delimitada.

![sandplinklistcomp](assets/sandplinklistcomp.png)

The links in the list also changes when a filter is applied from a different type of [!UICONTROL Search&amp;Promote] component. El uso de componentes de filtro de varios tipos puede proporcionar combinaciones eficaces de filtro.

El componente **[!UICONTROL Rutas de exploración]** permite al cliente ver los filtros que se aplican a los resultados de la búsqueda, en el orden en el que se aplicaron. Los clientes pueden hacer clic en los elementos de la ruta de exploración para volver a dicha combinación de filtros.

![sandpbreadcrumbcomp](assets/sandpbreadcrumbcomp.png)

Puede configurar las siguientes propiedades para las rutas de exploración en modo Edición y personalizar el aspecto del componente:

* **[!UICONTROL Delimitador]** : defina el carácter o la cadena de caracteres para que actúe como delimitador entre cada ruta de exploración. El campo Delimitador acepta cualquier cadena de caracteres como entrada. El valor predeterminado es: &quot;>&quot; (sin las comillas)
* **[!UICONTROL Delimitador]** final: defina un carácter o una cadena de caracteres que se mostrarán al final de las rutas de exploración. El campo Delimitador final acepta cualquier cadena de caracteres como entrada. La configuración predeterminada para esto es &quot;blank&quot; (es decir, no se muestra nada al final de la línea de ruta de exploración)

## Adición de cuadros de búsqueda {#adding-search-boxes}

The **[!UICONTROL Search]** component enables customers to perform keyword searches. Añada componentes de búsqueda a cada página en la que se desee proporcionar acceso a búsquedas. 

Configure the following properties in **[!UICONTROL Edit]** mode to control runtime behavior:

* **[!UICONTROL Ruta]** de página de resultados: la ruta a la página que muestra los resultados de la búsqueda.
* **[!UICONTROL Habilitar Completar]** automáticamente: seleccione esta opción para que aparezcan las palabras clave de búsqueda sugeridas cuando el cliente empiece a escribir en el cuadro de búsqueda.

![sandpsearchcomp](assets/sandpsearchcomp.png)

## Adición de titulares {#adding-banners}

The **[!UICONTROL Banners]** component displays banner advertisements according to the customer&#39;s Search&amp;Promote searches. La lógica en el servidor de Search&amp;Replace determina qué titular se muestra. Por ejemplo, una búsqueda de tejanos puede hacer que aparezca un titular relacionado con la moda. Filtrar por el departamento Hombres podría ajustar aún más la opción de titular.

The **[!UICONTROL Banners]** component provides one configurable property named **[!UICONTROL Banner Area]**. In **[!UICONTROL Edit]** mode, select one of the property values to specify how the banner appears. El servicio de Search&amp;Promote determina la lista de valores entre los que puede seleccionar.

## Ejemplo de página de búsqueda de Search&amp;Promote {#example-search-promote-search-page}

En este diagrama se muestran los componentes que se añaden a una página para crear la página de resultados de Search&amp;Promote a continuación.

![1328213789109](assets/1328213789109.png) ![sandpageexample](assets/sandppageexample.png)

