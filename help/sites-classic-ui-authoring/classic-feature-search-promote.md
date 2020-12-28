---
title: Añadir las funciones de Search&amp;Promocionar a su página
seo-title: Añadir las funciones de Search&amp;Promocionar a su página
description: Integrando las capacidades de Search&amp;Promote en su sitio Web, puede utilizar los componentes Search&amp;Promote para agregar características a sus páginas, tales como búsqueda de palabras clave, perfeccionamiento de búsqueda de página de resultados de búsqueda y titulares.
seo-description: Integrando las capacidades de Search&amp;Promote en su sitio Web, puede utilizar los componentes Search&amp;Promote para agregar características a sus páginas, tales como búsqueda de palabras clave, perfeccionamiento de búsqueda de página de resultados de búsqueda y titulares.
uuid: 8831aa56-9d7f-44ca-9d32-5901bf762154
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 277d7e67-5778-48cb-89bb-29bcc734a485
translation-type: tm+mt
source-git-commit: 263a1e514fa48f7aa7b696c801718ceff1e43ed7
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 57%

---


# Añadir características de Search&amp;Promote en la página {#adding-search-promote-features-to-your-page}

Para integrar las capacidades de Search&amp;Promote en su sitio Web, utilice los componentes [!UICONTROL Search&amp;Promote] para agregar las siguientes características a sus páginas:

* Búsqueda de palabras clave
* Página de resultados de búsqueda
* Perfeccionamiento de la búsqueda
* Banners

Tenga en cuenta que puede utilizar las capacidades de Search&amp;Promote solo si el administrador de AEM las ha activado. Consulte [Integración con Adobe Search&amp;Promote](/help/sites-administering/search-and-promote.md).

Las facetas se configuran en el servidor de Search&amp;Promote, al igual que la información que cada componente proporciona. En la siguiente tabla se incluye una descripción breve de cada componente. En las secciones posteriores se proporciona información detallada acerca de su aplicación.

<table> 
 <tbody> 
  <tr> 
   <th>Search&amp;Promote, componente</th> 
   <th>Descripción</th> 
  </tr> 
  <tr> 
   <td>Pancartas</td> 
   <td>Muestra anuncios de letreros. Los letreros se seleccionan en función de los datos recopilados mediante Search&amp;Promote.<br /> </td> 
  </tr> 
  <tr> 
   <td>Rutas de exploración</td> 
   <td>Muestra la palabra clave de búsqueda y la secuencia de filtros que el usuario ha aplicado a los resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Lista de casilla de verificación-Faceta</td> 
   <td>Lista de casillas de verificación para seleccionar facetas para filtrar los resultados de búsqueda.</td> 
  </tr> 
  <tr> 
   <td>Faceta desplegable</td> 
   <td>Una lista desplegable de facetas para filtrar los resultados de búsqueda.</td> 
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
   <td>Búsqueda  </td> 
   <td>Añade un campo de búsqueda en la página.</td> 
  </tr> 
 </tbody> 
</table>

## Creación de la página de resultados de búsqueda {#creating-the-search-results-page}

Utilice la consola WCM Websites para crear una página en la que se mostrarán los resultados de la búsqueda. Los resultados de una búsqueda de cualquier componente de búsqueda pueden aparecer en esta página si utiliza el mismo servicio de Search&amp;Promote. 

Los componentes que permiten a los usuarios revisar resultados de la búsqueda son Resultados y Paginación. El componente **[!UICONTROL Resultados]** no tiene propiedades configurables en modo Edición o Diseño.  El componente Resultados simplemente enumera los resultados de la búsqueda, en los que se ofrecen vínculos a otras páginas, y muestra la cantidad de resultados para la palabra clave de búsqueda. 

![srchresultscomp](assets/srchresultscomp.png)

El componente **[!UICONTROL Paginación]** permite a los usuarios navegar por varias páginas de resultados de la búsqueda. El usuario puede ver el número de páginas, desplazarse a la página siguiente o anterior, seleccionar una página para abrirla o consolidar los resultados en una página. 

![srchpaginación](assets/srchpagination.png)

Puede configurar las siguientes propiedades de componente en el modo [!UICONTROL Editar] para controlar el comportamiento del motor de ejecución:

* **[!UICONTROL Ocultar una sola página]**  de resultados: seleccione esta opción para ocultar los controles de navegación de la página cuando la búsqueda devuelve una sola página de resultados.
* **[!UICONTROL Ocultar primero/último]** : seleccione esta opción para evitar que los usuarios salten a la primera o a la última página de resultados.
* **[!UICONTROL Ocultar anterior/siguiente]** : determina si los usuarios pueden navegar por las páginas de resultados en relación con la página actual.
* **[!UICONTROL Ocultar vista todo]** : determina si el usuario puede consolidar todos los resultados de búsqueda en una sola página. Normalmente, el uso de datos en páginas permite un uso más eficaz de los recursos del servidor. Seleccione esta opción para impedir la transferencia de conjuntos de datos de gran tamaño en un mensaje de respuesta.

## Activación del filtro de resultados por facetas {#enabling-the-filtering-of-results-by-facets}

Puede permitir a los usuarios filtrar resultados de búsqueda por facetas. Los componentes **[!UICONTROL Faceta de Lista de casilla de verificación]**, **[!UICONTROL Faceta desplegable]** y **[!UICONTROL Faceta de Lista de vínculo]** permiten a los usuarios seleccionar una o varias facetas para filtrar. Si se utilizan estos componentes, debe incluir el componente **[!UICONTROL Rutas de exploración]**. Las rutas de exploración indican los filtros actuales que se utilizan.

Los componentes **[!UICONTROL Faceta de Lista de casilla de verificación]**, **[!UICONTROL Faceta desplegable]** y **[!UICONTROL Faceta de Lista de vínculo]** tienen las siguientes propiedades que se configuran en el modo **[!UICONTROL Editar]**:

* **[!UICONTROL Nombre]**  de faceta: el nombre de la faceta que se utiliza para filtros.

El componente **[!UICONTROL Faceta de lista de casilla de verificación]** muestra una lista de facetas con una casilla de verificación correspondiente. Utilice **[!UICONTROL Faceta de lista de casilla de verificación]** de modo que los usuarios puedan ver un subconjunto de resultados que incluyen elementos de varias facetas. Por ejemplo, la faceta Marca es adecuada porque varias marcas proporcionan el mismo tipo de producto.

Aparece una casilla de verificación para cada faceta asociada a un resultado de búsqueda. Cuando un usuario selecciona una casilla de verificación, la página se vuelve a cargar con un conjunto de resultados actualizado. Todas las casillas permanecen en la página para que los clientes puedan añadir o quitar facetas al filtro en cualquier momento:

![sandpcheckboxcomp](assets/sandpcheckboxcomp.png)

El componente **[!UICONTROL Faceta desplegable]** permite a los clientes seleccionar un elemento de faceta de una lista desplegable. Este componente es de utilidad cuando quiere que los clientes se centren en un solo elemento de faceta a la vez. Por ejemplo, la faceta Departamento es adecuada para permitir a los clientes refinar las búsquedas de producto por sexo. Juan busca *tejanos* y luego filtra con el departamento Hombres. 

La lista desplegable se rellena con las facetas asociadas a todos los resultados de la búsqueda. Al seleccionar un elemento de la lista desplegable, la página se vuelve a cargar con un conjunto de resultados actualizado. Los elementos de la lista desplegable no cambian para que los clientes puedan cambiar de una faceta a otra en cualquier momento. 

![sandpdropdownDepartment](assets/sandpdropdowndepartment.png)

El componente **[!UICONTROL Faceta de lista de vínculo]** permite a los clientes restringir progresivamente la selección de elementos categorizados bajo varios miembros de faceta o facetas.

Los miembros de faceta aparecen como una lista de vínculos. El texto de cada vínculo es el nombre de un miembro de faceta asociado a los resultados de búsqueda actuales. Cuando un cliente hace clic en un vínculo de faceta, la página se vuelve a cargar y se muestra un subconjunto de resultados. La lista de vínculos se actualiza en consecuencia para permitir una selección aún más delimitada.

![sandplinklistcomp](assets/sandplinklistcomp.png)

Los vínculos de la lista también cambian cuando se aplica un filtro desde un tipo diferente de componente [!UICONTROL Search&amp;Promote]. El uso de componentes de filtro de varios tipos puede proporcionar combinaciones eficaces de filtro.

El componente **[!UICONTROL Rutas de exploración]** permite al cliente ver los filtros que se aplican a los resultados de la búsqueda, en el orden en el que se aplicaron. Los clientes pueden hacer clic en los elementos de la ruta de exploración para volver a dicha combinación de filtros.

![sandpbreadcrumbcomp](assets/sandpbreadcrumbcomp.png)

Puede configurar las siguientes propiedades para las rutas de exploración en modo Edición y personalizar el aspecto del componente:

* **[!UICONTROL Delimitador]** : defina el carácter o la cadena de caracteres para que actúe como delimitador entre cada ruta de exploración. El campo Delimitador acepta cualquier cadena de caracteres como entrada. El valor predeterminado es: &quot;>&quot; (sin las comillas)
* **[!UICONTROL Delimitador]**  final: defina un carácter o una cadena de caracteres que se mostrará al final de las rutas de exploración. El campo Delimitador final acepta cualquier cadena de caracteres como entrada. La configuración predeterminada para esto es &quot;blank&quot; (es decir, no se muestra nada al final de la línea de ruta de exploración)

## Adición de cuadros de búsqueda {#adding-search-boxes}

El componente **[!UICONTROL Búsqueda]** permite a los clientes realizar búsquedas de palabras clave. Añada componentes de búsqueda a cada página en la que se desee proporcionar acceso a búsquedas. 

Configure las siguientes propiedades en el modo **[!UICONTROL Editar]** para controlar el comportamiento en tiempo de ejecución:

* **[!UICONTROL Ruta]**  de página de resultados: la ruta a la página que muestra los resultados de la búsqueda.
* **[!UICONTROL Habilitar Completar]**  automáticamente: seleccione esta opción para que aparezcan las palabras clave de búsqueda sugeridas cuando el cliente empiece a escribir en el cuadro de búsqueda.

![sandpsearchcomp](assets/sandpsearchcomp.png)

## Adición de titulares {#adding-banners}

El componente **[!UICONTROL Pancartas]** muestra publicidades de titular según las búsquedas de Search&amp;Promote del cliente. La lógica en el servidor de Search&amp;Replace determina qué titular se muestra. Por ejemplo, una búsqueda de tejanos puede hacer que aparezca un titular relacionado con la moda. Filtrar por el departamento Hombres podría ajustar aún más la opción de titular.

El componente **[!UICONTROL Pancartas]** proporciona una propiedad configurable denominada **[!UICONTROL Área de pancarta]**. En el modo **[!UICONTROL Editar]**, seleccione uno de los valores de propiedad para especificar cómo aparecerá el letrero. El servicio de Search&amp;Promote determina la lista de valores entre los que puede seleccionar.

## Ejemplo de página de búsqueda de Search&amp;Promote {#example-search-promote-search-page}

En este diagrama se muestran los componentes que se añaden a una página para crear la página de resultados de Search&amp;Promote a continuación.

![1328213789109](assets/1328213789109.png) ![sandpageexample](assets/sandppageexample.png)

