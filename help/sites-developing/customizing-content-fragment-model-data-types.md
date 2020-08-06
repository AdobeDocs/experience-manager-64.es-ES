---
title: NO PUBLIQUE, PERO NO DELETE Personalización de tipos de datos para modelos de fragmentos de contenido
seo-title: Personalización de tipos de datos para modelos de fragmentos de contenido
description: Los tipos de datos utilizados en los modelos de fragmentos de contenido se pueden personalizar.
seo-description: Los tipos de datos utilizados en los modelos de fragmentos de contenido se pueden personalizar.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# NO PUBLIQUE, PERO NO DELETE Personalización de tipos de datos para modelos de fragmentos de contenido{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Los fragmentos](/help/assets/content-fragments.md) de contenido se basan en modelos [de fragmentos de](/help/assets/content-fragments-models.md)contenido. Estos modelos se crean a partir de [elementos](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de diferentes tipos de datos.

Hay disponibles varios tipos de datos predeterminados, como texto de una sola línea, texto enriquecido multilínea, campos numéricos, selectores booleanos, opciones de menú desplegable, fecha y hora, etc. AEM usuarios pueden seleccionar tipos de datos en función de la intención editorial de los fragmentos correspondientes. Esto le permite adaptarse a modelos de texto sencillos a través de modelos complejos con diferentes tipos de contenido y la experiencia de creación de fragmentos asociada.

Los tipos de datos se definen mediante una [combinación de propiedades](#properties) de nodo que se mantienen en ubicaciones [específicas del repositorio](#locations-in-the-repository). También puede crear sus propios tipos [de](#creating-your-data-type) datos y [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Ubicaciones en el repositorio {#locations-in-the-repository}

Todos los tipos de datos predeterminados se declaran en:

`/libs/settings`

Puede agregar nuevos tipos de datos superponiendo la estructura de nodos como se indica a continuación en `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>No debe cambiar nada en la `/libs` ruta.
>
>Todo lo que haya puede cambiar en la próxima actualización o instalación de un servicio o paquete de correcciones.

## Propiedades {#properties}

Las propiedades de nodo se utilizan para definir los tipos de datos:

* [Propiedades de tipos de datos](#data-type-properties)
* y dentro de esos [fieldProperties](#fieldproperties)

### Propiedades del tipo de datos {#data-type-properties}

Todos los tipos de datos están representados en una estructura de nodos como en:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Cada nodo debajo `/items` tiene propiedades que definen cómo se debe representar ese tipo de datos dentro del editor de modelos.

Deben estar presentes las siguientes propiedades para que el tipo de datos esté presente en el editor de modelos:

* `fieldIcon`

   [Icono](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) CoralUI para representar el tipo de datos en la interfaz de usuario del editor de modelos.

* ` [fieldProperties](#fieldproperties)`

   Matriz que representa las propiedades de configuración de cada tipo de datos.

* `fieldResourceType`

   Tipo de recurso Sling utilizado para representar el tipo de datos en un fragmento de contenido. Para los tipos de datos que se pueden procesar de diferentes maneras (por ejemplo, como entrada de texto simple o entrada de texto multilínea), esta propiedad debe crearse como una matriz que contenga todos los tipos de recursos. La `renderasfield` propiedad se agregará automáticamente a `fieldProperties` para permitir que el usuario elija el tipo de recurso que necesita agregar al modelo.

* `fieldPropResourceType`

   Tipo de recurso Sling utilizado para representar la propiedad predeterminada para el tipo de datos.

   Por ejemplo, para el tipo de datos:

   * Texto de una sola línea, `fieldPropResourceType` sería un `textfield` componente
   * Booleano, el `fieldPropResourceType` componente sería un `checkbox` componente

* `fieldViewResourceType`

   Tipo de recurso Sling utilizado para representar el tipo de datos en la previsualización, al construir el modelo. Cuando el usuario arrastra el tipo de datos a la izquierda del editor de modelos, la `fieldViewResourceType` propiedad representa el componente que se procesa allí. Se utiliza para los casos en los que no se desea procesar el componente completo, pero solo se desea procesar un sustituto que minimice la sobrecarga en el editor de modelos.

* `fieldTitle`

   Propiedad que define el título de este tipo de datos. Por ejemplo, texto **de** una sola línea para un `textfield` componente, texto **de** varias líneas para un componente de varios campos.

* `valueType`

   Es el tipo de valor que devuelve el tipo de datos cuando se almacena internamente. Consulte [Asignaciones](#mappings).

* `renderType`

   Es una representación interna del tipo de datos. Conecta el `valueType` a un componente de interfaz de usuario. Consulte [Asignaciones](#mappings).

* `listOrder`

   Cada tipo de datos necesita un valor que represente su orden en la lista. Se utiliza para garantizar el orden correcto de los distintos campos (agregados/movidos mediante arrastrar y soltar) al guardar el editor de modelos. Este valor debe ser un número entero y se recomienda asignarlo de forma ascendente y ordenada. Al crear un nuevo tipo de datos, es mejor asignar el valor en función del último tipo de datos de la lista (el valor más alto del `listOrder` valor presente en los tipos de datos).

#### Asignaciones {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>Tipo de datos<br /> </td> 
   <td>Tipo de valor<br /> </td> 
   <td>Tipo de procesamiento</td> 
  </tr> 
  <tr> 
   <td>Texto de línea única</td> 
   <td>Cadena</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Texto multilínea</td> 
   <td>cadena, con tipo de contenido<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Número (entero/largo)<br /> </td> 
   <td>long</td> 
   <td>número</td> 
  </tr> 
  <tr> 
   <td>Número (doble/flotante)</td> 
   <td>double</td> 
   <td>número</td> 
  </tr> 
  <tr> 
   <td>Booleano</td> 
   <td>boolean</td> 
   <td>boolean</td> 
  </tr> 
  <tr> 
   <td>Fecha y hora</td> 
   <td>calendario</td> 
   <td>time</td> 
  </tr> 
  <tr> 
   <td>Enumeración</td> 
   <td>string/long</td> 
   <td>lista desglosada</td> 
  </tr> 
  <tr> 
   <td>Etiquetas</td> 
   <td>Cadena</td> 
   <td>etiquetas</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Algunos tipos (por ejemplo, `string`, `long`entre otros) pueden tener varios valores. En este caso, el componente utilizado para la representación y edición suele estar ajustado por un componente de varios campos ( `granite/ui/components/coral/foundation/form/multifield`). La excepción son las etiquetas, en las que el componente de edición es responsable de procesarlo correctamente.

### fieldProperties {#fieldproperties}

Las propiedades de configuración de cada tipo de datos. Valores para `fieldProperties`:

* `base`

   Esta es la base de todos los `fieldProperties` componentes. La definición se encuentra en `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Contiene la variable `fieldRoot`, que posteriormente `fieldProperties` puede utilizarse al crear entradas para recuperar la ruta correcta.

   Ejemplo: para obtener la ruta correcta para una etiqueta **de** campo, necesitará la clave para identificar el componente al que pertenece, la entrada para este campo debe ser `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Este componente agrega la casilla de verificación predeterminada para el tipo de `Boolean` datos, así como los parámetros `checked@Delete` y `checked@TypeHint`Sling.

* `datepickerfields`

   Componente que agrega las entradas ocultas necesarias para que el componente del selector de fechas funcione. Incluye la creación de las propiedades `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat``minDate` y `maxDate`.

* `datetimepickerfields`

   Esto agrega un campo de selección para el tipo de `Date&Time` datos para distinguir entre `Date` y `Date&Time` las opciones.

* `datevaluefield`

   Esto agrega un marcador de datos a las propiedades, de modo que un usuario puede seleccionar un valor predeterminado para el tipo de datos `Date&Time` .

* `descriptionfield`

   Este componente agrega un campo de texto de varias líneas que representa la descripción del componente seleccionado actualmente en el editor de varias líneas. El procesador del Editor de modelos lo agrega automáticamente al final de cada propiedad de tipo de datos.

* `labelfield`

   Componente que agrega una `textfield` entrada que agrega la etiqueta de campo para un tipo de datos que puede tener etiquetas de campo.

* `maptopropertyfield`

   Este componente agrega el `Name` campo en las propiedades, lo que proporciona un identificador al componente seleccionado de un tipo de datos. Debe estar presente en todos los tipos de datos.

* `maxlengthfield`

   Se utiliza para agregar la `maxLength` propiedad para utilizarla con tipos de datos que aceptan esta propiedad. Por ejemplo, con texto **de una** sola línea, **número**, etc.

* `multieditorfield`

   Esto agrega todo el campo oculto necesario para que funcione el editor de varias líneas, representado por el tipo de datos Texto **** multilínea.

* `mvfields`

   Componente que agrega todos los campos ocultos necesarios para que funcione un componente de varios campos. Por ejemplo, para la segunda opción de un tipo de datos Texto **de una** sola línea. Debe agregarse para cualquier componente que se procese como un campo múltiple.

* `numbertypefield`

   Seleccione la opción para el tipo de datos **Número** que selecciona entre **Entero** o **Fracción** para el tipo de datos **Número** .

* `numbervaluefield`

   Un selector de valores `numberfield` predeterminado para el **número** `type.options` Agrega la entrada de opciones para el tipo de datos de **Lista desglosada** , que se utiliza para determinar los valores del componente de cuadro de selección.

* `placeholderfield`

   Es un campo de texto que actúa como entrada para la `emptyText` propiedad de un componente. Debe ser utilizado por todos los tipos de datos que aceptan un marcador de posición (esto no es muy complicado; Por ejemplo: texto **de** una sola línea, **número**, etc.).

* `renderasfield`

   Es el componente que se procesa automáticamente cuando hay varios `fieldResourceTypes` presentes en la propiedad del nodo de tipo de datos.

* `requiredfield`

   Se trata de una casilla de verificación que representa la `required` propiedad de un componente. Dado que la mayoría de los componentes aceptan el `required` campo, este campo se puede utilizar para la mayoría de los tipos de datos.

* `tagsfields`

   Componentes que agregan las entradas necesarias para que se procese un `tagfield` componente, utilizadas por el tipo de datos **Etiquetas** .

* `tagsroot`

   Selector de ruta utilizado por el tipo de datos **Etiquetas** para establecer la ruta raíz del `tagsfield` componente.

* `textfield`

   El tipo de datos lo utiliza para establecer la etiqueta de campo de la casilla de verificación definida por este tipo de datos. `Boolean`

* `textvaluefield`

   La propiedad value predeterminada para el tipo de datos Texto **** de una sola línea.

## Creación de un tipo de datos {#creating-your-data-type}

Para crear su propio tipo de datos debe:

* [Crear la estructura de nodos](#creating-the-node-structure)
* [Definir las propiedades del tipo de datos](#defining-the-properties-for-your-data-type)

A continuación, puede [utilizar el tipo](#using-your-data-type)de datos.

También puede [crear su propio `fieldProperties`](#creating-your-own-fieldproperties-property).

### Creación de la estructura de nodos {#creating-the-node-structure}

La estructura de nodos debe crearse en `/apps` para poder superponer los tipos de datos. Si aún no existe, debe crear:

1. Si aún no existe, debe crear:

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` ya debe existir.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` puede que sea necesario crear con los tipos de nodos especificados.

1. En `/items` puede agregar nuevos nodos para representar los nuevos tipos de datos:

   * Tipo de nodo: `nt:unstructured`
   * &quot;Propiedades: consulte [Definición de propiedades para el tipo de datos](#defining-the-properties-for-your-data-type)

### Definición de las propiedades para el tipo de datos {#defining-the-properties-for-your-data-type}

1. Determine los valores de las siguientes propiedades [de tipo de](#data-type-properties) datos que son necesarias para el tipo de datos:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Definen cómo se procesarán los componentes del tipo de datos. Pueden ser cualquier componente; incluyendo sus propios componentes personalizados (necesita un conjunto de ` [fieldProperties](#fieldproperties)`).

   Defina estas propiedades, con los valores correspondientes, en el nodo del tipo de datos.

1. Determinar el ` [fieldProperties](#fieldproperties)` uso. Depende de los atributos o propiedades que `fieldResourceType` necesite.

   Por ejemplo, un `granite/ui/components/coral/foundation/form/textfield`usuario debe tener un Nombre **de** etiqueta, una Longitud **** máxima, un Texto **de** marcador de posición y una propiedad Valor **** predeterminado.

   Puede elegir entre [fieldProperties](#fieldproperties)lista para usar o [crear sus propias propiedades](#creating-your-own-fieldproperties-property).

   Defina estas propiedades, con los valores correspondientes, en el nodo del tipo de datos.

1. Determinar valores para las siguientes propiedades [de tipo de](#data-type-properties)datos:

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Defina estas propiedades, con los valores correspondientes, en el nodo del tipo de datos.

### Uso del tipo de datos {#using-your-data-type}

Después de guardar esta estructura de nodos, con todas las propiedades aplicadas, puede abrir cualquier modelo con el editor de modelos y ver y utilizar el nuevo tipo de datos.

## Creación de su propia propiedad fieldProperties {#creating-your-own-fieldproperties-property}

Puede elegir entre [fieldProperties](#fieldproperties)predefinidas o crear las suyas:

1. Cree un componente en:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Si la ruta no existe, puede crearla con `nt:folder` nodos.

   1. Para tener acceso a las variables, este componente debe ampliar:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. El componente debería poder incluirse mediante:

      `sling:include`

   1. Este componente debe representar un campo (si un usuario necesita introducir datos) o una entrada oculta con las propiedades necesarias para el tipo de datos. Por ejemplo, un componente multicampo requiere un nodo secundario con el tipo de campo que debe duplicado, por lo que debe haber una entrada que pueda crear (mediante mecánica de POST sling) un nodo secundario de un tipo específico.

1. Se debe agregar el nombre base de este componente a `fieldProperties`.
1. Repita el procedimiento para todas las propiedades que necesite.

