---
title: NO PUBLICAR, PERO NO DELETE Personalizar tipos de datos para modelos de fragmentos de contenido
seo-title: Customizing Data Types for Content Fragment Models
description: Los tipos de datos utilizados en los modelos de fragmento de contenido se pueden personalizar.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 2%

---


# NO PUBLICAR, PERO NO DELETE Personalizar tipos de datos para modelos de fragmentos de contenido{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[Fragmentos de contenido](/help/assets/content-fragments.md) se basan en [modelos de fragmento de contenido](/help/assets/content-fragments-models.md). Estos modelos se crean a partir de [elementos](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de diferentes tipos de datos.

Hay varios tipos de datos disponibles, incluidos texto de una sola línea, texto enriquecido multilínea, campos numéricos, selectores booleanos, opciones de menú desplegable, fecha y hora, etc. AEM usuarios pueden seleccionar tipos de datos en función de la intención editorial de los fragmentos correspondientes. Esto le permite adaptar los modelos de texto simples a modelos complejos con distintos tipos de contenido y la experiencia de creación de fragmentos asociada.

Los tipos de datos se definen mediante una [combinación de propiedades de nodo](#properties) retenido en [ubicaciones específicas en el repositorio](#locations-in-the-repository). También puede crear su propio [tipos de datos](#creating-your-data-type) y [fieldProperties](#creating-your-own-fieldproperties-property).

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
>No debe cambiar nada en la variable `/libs` ruta.
>
>Todo lo que haya puede cambiar en la próxima actualización, o la instalación de un servicio o paquete de correcciones.

## Propiedades {#properties}

Las propiedades de nodo se utilizan para definir los tipos de datos:

* [Propiedades de tipos de datos](#data-type-properties)
* y dentro de [fieldProperties](#fieldproperties)

### Propiedades de tipo de datos {#data-type-properties}

Todos los tipos de datos se representan en una estructura de nodos como en:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Cada nodo de `/items` tiene propiedades que definen cómo se debe representar ese tipo de datos dentro del editor de modelos.

Para que el tipo de datos esté presente en el editor de modelos, deben estar presentes todas las propiedades siguientes:

* `fieldIcon`

   [Icono de CoralUI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) para representar el tipo de datos en la interfaz de usuario del editor de modelos.

* ` [fieldProperties](#fieldproperties)`

   Matriz que representa las propiedades de configuración de cada tipo de datos.

* `fieldResourceType`

   El tipo de recurso Sling utilizado para procesar el tipo de datos en un fragmento de contenido. Para los tipos de datos que se pueden procesar de diferentes maneras (por ejemplo, como entrada de texto simple o entrada de texto multilínea), esta propiedad debe crearse como una matriz que contenga todos los tipos de recursos. La variable `renderasfield` se agregará automáticamente a `fieldProperties` para permitir al usuario elegir el tipo de recurso que debe añadir al modelo,

* `fieldPropResourceType`

   El tipo de recurso Sling utilizado para procesar la propiedad predeterminada para el tipo de datos.

   Por ejemplo, para el tipo de datos:

   * Texto de una sola línea, la variable `fieldPropResourceType` sería un `textfield` componente
   * Booleano, la variable `fieldPropResourceType` sería un `checkbox` componente

* `fieldViewResourceType`

   El tipo de recurso Sling utilizado para procesar el tipo de datos en la vista previa, al construir el modelo. Cuando el usuario arrastra el tipo de datos a la izquierda del editor de modelos, la variable `fieldViewResourceType` representa el componente que se representa allí. Se utiliza para casos en los que no desea procesar el componente completo, pero solo desea procesar un sustituto que minimice la sobrecarga del editor de modelos.

* `fieldTitle`

   Propiedad que define el título de este tipo de datos. Por ejemplo, **Texto de una sola línea** para un `textfield` componente, **Texto de varias líneas** para un componente multicampo.

* `valueType`

   Este es el tipo de valor que devuelve el tipo de datos cuando se almacena internamente. Consulte [Asignaciones](#mappings).

* `renderType`

   Es una representación interna del tipo de datos. Conecta el `valueType` a un componente de interfaz de usuario. Consulte [Asignaciones](#mappings).

* `listOrder`

   Cada tipo de datos necesita un valor que represente su orden en la lista. Se utiliza para garantizar el orden correcto de los distintos campos (añadidos o movidos arrastrando y soltando) al guardar el editor de modelos. Este valor debe ser un número entero y se recomienda asignarlo de forma ascendente y ordenada. Al crear un nuevo tipo de datos, es mejor asignar el valor en función del último tipo de datos de la lista (el valor más alto de `listOrder` presente en los tipos de datos).

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
   <td>cadena</td> 
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
   <td>booleano</td> 
   <td>booleano</td> 
  </tr> 
  <tr> 
   <td>Fecha y hora</td> 
   <td>calendario</td> 
   <td>hora</td> 
  </tr> 
  <tr> 
   <td>Lista desglosada</td> 
   <td>string/long</td> 
   <td>enumeración</td> 
  </tr> 
  <tr> 
   <td>Etiquetas</td> 
   <td>cadena</td> 
   <td>etiquetas</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Algunos tipos (por ejemplo, `string`, `long`, entre otros) pueden tener varios valores. En este caso, el componente utilizado para la renderización y edición suele envolverse en un componente de varios campos ( `granite/ui/components/coral/foundation/form/multifield`). La excepción son las etiquetas, en las que el componente de edición es responsable de procesarlo correctamente.

### fieldProperties {#fieldproperties}

Las propiedades de configuración de cada tipo de datos. Valores para `fieldProperties`:

* `base`

   Esta es la base de todos `fieldProperties` componentes. La definición está situada en `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Contiene la variable `fieldRoot`, que `fieldProperties` puede utilizarse al crear entradas para recuperar la ruta correcta.

   Ejemplo: para obtener la ruta correcta para un **Etiqueta de campo** necesitará la clave para identificar el componente al que pertenece, la entrada para este campo debe ser `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Este componente añade la casilla de verificación predeterminada para la variable `Boolean` tipo de datos, así como los parámetros de Sling `checked@Delete` y `checked@TypeHint`.

* `datepickerfields`

   Componente que añade las entradas ocultas necesarias para que funcione el componente selector de fechas. Incluye la creación de las propiedades `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` y `maxDate`.

* `datetimepickerfields`

   Esto añade un campo de selección para `Date&Time` tipo de datos para distinguir entre `Date` y `Date&Time` opciones.

* `datevaluefield`

   Esto agrega un selector de fecha a las propiedades, de modo que un usuario pueda seleccionar un valor predeterminado para la variable `Date&Time` tipo de datos.

* `descriptionfield`

   Este componente añade un campo de texto multilínea que representa la descripción del componente seleccionado actualmente en el editor multilínea. El procesador del Editor de modelos lo agrega automáticamente al final de cada propiedad de tipo de datos.

* `labelfield`

   Componente que agrega un `textfield` entrada que agrega la etiqueta de campo para un tipo de datos que puede tener etiquetas de campo.

* `maptopropertyfield`

   Este componente añade la variable `Name` en las propiedades, dando un identificador al componente seleccionado de un tipo de datos. Debe estar presente en todos los tipos de datos.

* `maxlengthfield`

   Se utiliza para añadir la variable `maxLength` para su uso con tipos de datos que acepten esta propiedad. Por ejemplo, con **Texto de una sola línea**, **Número**, etc.

* `multieditorfield`

   Esto agrega todo el campo oculto necesario para que funcione el editor de varias líneas, que está representado por la variable **Texto de varias líneas** tipo de datos.

* `mvfields`

   Componente que añade todos los campos ocultos necesarios para que funcione un componente multicampo. Por ejemplo, para la segunda opción de un **Texto de una sola línea** tipo de datos. Esto debe añadirse para cualquier componente que se represente como un campo múltiple.

* `numbertypefield`

   Seleccione la opción para **Número** tipo de datos que selecciona entre **Número entero** o **Fracción** para el **Número** tipo de datos.

* `numbervaluefield`

   A `numberfield` selector de valor predeterminado para la variable **Número** `type.options` Esto agrega las opciones de entrada para la variable **Enumeración** tipo de datos, que se utiliza para determinar los valores del componente de cuadro de selección.

* `placeholderfield`

   Se trata de un campo de texto que actúa como entrada para la variable `emptyText` propiedad de un componente. Esto debe ser utilizado por todos los tipos de datos que acepten un marcador de posición (lo que no es muy complicado; p. ej. **Texto de una sola línea**, **Número**, etc.).

* `renderasfield`

   Este es el componente que se procesa automáticamente cuando varios `fieldResourceTypes` están presentes en la propiedad del nodo de tipo de datos .

* `requiredfield`

   Esta es una casilla de verificación que representa la variable `required` para un componente. Debido a que la mayoría de los componentes aceptan la variable `required` , este campo se puede utilizar para la mayoría de los tipos de datos.

* `tagsfields`

   Componentes que agregan las entradas necesarias para un `tagfield` componente que se va a procesar, utilizado por el **Etiquetas** tipo de datos.

* `tagsroot`

   Un selector de rutas que usa el **Etiquetas** tipo de datos para establecer la ruta raíz de `tagsfield` componente.

* `textfield`

   Utilizado por la variable `Boolean` tipo de datos para establecer la etiqueta de campo de la casilla de verificación definida por este tipo de datos.

* `textvaluefield`

   La propiedad value predeterminada de **Texto de una sola línea** tipo de datos.

## Creación del tipo de datos {#creating-your-data-type}

Para crear su propio tipo de datos, debe:

* [Crear la estructura de nodos](#creating-the-node-structure)
* [Definir las propiedades del tipo de datos](#defining-the-properties-for-your-data-type)

Entonces puede [use su tipo de datos](#using-your-data-type).

También puede [cree su propio `fieldProperties`](#creating-your-own-fieldproperties-property).

### Creación de la estructura de nodos {#creating-the-node-structure}

La estructura de nodos debe crearse en `/apps` para superponer los tipos de datos. Si aún no existe, debe crear:

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

1. En `/items` puede agregar nuevos nodos para representar sus nuevos tipos de datos:

   * Tipo de nodo: `nt:unstructured`
   * &quot;Propiedades: see [Definición de las propiedades para el tipo de datos](#defining-the-properties-for-your-data-type)

### Definición de las propiedades para el tipo de datos {#defining-the-properties-for-your-data-type}

1. Determinar los valores para lo siguiente [propiedades de tipo de datos](#data-type-properties) que son necesarios para su tipo de datos:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Definen cómo se procesarán los componentes del tipo de datos. Pueden ser cualquier componente; incluir sus propios componentes personalizados (necesita un conjunto coincidente de ` [fieldProperties](#fieldproperties)`).

   Defina estas propiedades, con los valores adecuados, en el nodo del tipo de datos.

1. Determine el ` [fieldProperties](#fieldproperties)` para usar. Esto depende de los atributos o propiedades que `fieldResourceType` necesidades.

   Por ejemplo, una `granite/ui/components/coral/foundation/form/textfield`debe tener un **Nombre de la etiqueta**, **Longitud máxima**, **Texto del marcador de posición** y **Valor predeterminado** propiedad.

   Puede elegir entre la opción predeterminada [fieldProperties](#fieldproperties)o [crear sus propias propiedades](#creating-your-own-fieldproperties-property).

   Defina estas propiedades, con los valores adecuados, en el nodo del tipo de datos.

1. Determinar los valores para lo siguiente [propiedades de tipo de datos](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Defina estas propiedades, con los valores adecuados, en el nodo del tipo de datos.

### Uso del tipo de datos {#using-your-data-type}

Después de guardar esta estructura de nodos, con todas las propiedades aplicadas, puede abrir cualquier modelo con el editor de modelos y ver y utilizar el nuevo tipo de datos.

## Creación de su propia propiedad fieldProperties {#creating-your-own-fieldproperties-property}

Puede elegir entre la opción predeterminada [fieldProperties](#fieldproperties)o cree el suyo propio:

1. Cree un componente en:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Si la ruta no existe, puede crearla con `nt:folder` nodos.

   1. Para tener acceso a las variables, este componente debe ampliar:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. El componente debe poder incluirse mediante:

      `sling:include`

   1. Este componente debe representar un campo (si un usuario necesita introducir datos) o una entrada oculta con las propiedades necesarias para el tipo de datos. Por ejemplo, un componente multicampo requiere un nodo secundario con el tipo de campo que debe duplicar, por lo que debe haber una entrada que pueda crear (a través de la mecánica del POST de sling) un nodo secundario de un tipo específico.

1. El nombre base de este componente debe agregarse a `fieldProperties`.
1. Repita el proceso para todas las propiedades que necesite.

