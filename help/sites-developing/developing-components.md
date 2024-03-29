---
title: Desarrollo de componentes AEM
seo-title: Developing AEM Components
description: AEM componentes se utilizan para guardar, dar formato y procesar el contenido disponible en las páginas web.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages.
exl-id: d3c1559a-1a7a-46ed-a935-9ad226cdea33
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3511'
ht-degree: 3%

---

# Desarrollo de componentes AEM{#developing-aem-components}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM componentes se utilizan para guardar, dar formato y procesar el contenido disponible en las páginas web.

* When [creación de páginas](/help/sites-authoring/default-components.md), los componentes permiten a los autores editar y configurar el contenido.

   * Al crear un [Comercio](/help/sites-administering/ecommerce.md) sitio en el que los componentes pueden, por ejemplo, recopilar y procesar información del catálogo.

      Consulte [Desarrollo del comercio electrónico](/help/sites-developing/ecommerce.md) para obtener más información.

   * Al crear un [Comunidades](/help/communities/author-communities.md) sitio en el que los componentes pueden proporcionar información a sus visitantes y recopilarla.

      Consulte [Desarrollo de comunidades](/help/communities/communities.md) para obtener más información.

* En la instancia de publicación, los componentes representan el contenido, presentándolo como lo necesita a los visitantes del sitio web.

>[!NOTE]
>
>Esta página es una continuación del documento [Componentes AEM: conceptos básicos](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Componentes a continuación `/libs/cq/gui/components/authoring/dialog` están pensados para utilizarse únicamente en el Editor (cuadros de diálogo de componentes en la creación). Si se utilizan en otra parte (como en un cuadro de diálogo de asistente, por ejemplo), es posible que no se comporten del modo esperado.

## Ejemplos de código {#code-samples}

Esta página proporciona la documentación de referencia (o vínculos a la documentación de referencia) necesaria para desarrollar nuevos componentes para AEM. Consulte [Desarrollo de componentes de AEM: ejemplos de código](/help/sites-developing/developing-components-samples.md) para algunos ejemplos prácticos.

## Estructura {#structure}

La estructura básica de un componente se cubre en la página [Componentes AEM: conceptos básicos](/help/sites-developing/components-basics.md#structure). Ese documento cubre tanto las IU táctiles como las clásicas. Aunque no necesite utilizar la configuración clásica en el nuevo componente, puede ser útil que los tenga en cuenta al heredar de componentes existentes.

## Ampliación de los componentes y cuadros de diálogo existentes {#extending-existing-components-and-dialogs}

Según el componente que desee implementar, podría ser posible ampliar o personalizar una instancia existente en lugar de definir y desarrollar el conjunto [estructura](#structure) desde cero.

Al ampliar o personalizar un componente o cuadro de diálogo existente, puede copiar o replicar toda la estructura o la estructura necesaria para el cuadro de diálogo antes de realizar los cambios.

### Ampliación de un componente existente {#extending-an-existing-component}

Se puede ampliar un componente existente con [Jerarquía de tipo de recurso](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) y los mecanismos de herencia conexos.

>[!NOTE]
>
>Los componentes también se pueden redefinir con una superposición basada en la lógica de ruta de búsqueda. Sin embargo, en tal caso, la variable [Fusión de recursos de Sling](/help/sites-developing/sling-resource-merger.md) no se activará y `/apps` debe definir la superposición completa.

>[!NOTE]
>
>La variable [componente de fragmento de contenido](/help/sites-developing/customizing-content-fragments.md) también se puede personalizar y ampliar, aunque se deben tener en cuenta la estructura completa y las relaciones con Assets.

### Personalización de un cuadro de diálogo de componente existente {#customizing-a-existing-component-dialog}

También es posible anular un *cuadro de diálogo de componentes* usando la variable [Fusión de recursos de Sling](/help/sites-developing/sling-resource-merger.md) y definición de la propiedad `sling:resourceSuperType`.

Esto significa que solo necesita redefinir las diferencias necesarias, en lugar de redefinir todo el cuadro de diálogo (mediante `sling:resourceSuperType`). Este es ahora el método recomendado para ampliar un cuadro de diálogo de componentes

Consulte la [Fusión de recursos de Sling](/help/sites-developing/sling-resource-merger.md) para obtener más información.

## Definición del marcado {#defining-the-markup}

El componente se procesará con [HTML](https://www.w3schools.com/htmL/html_intro.asp). El componente debe definir el HTML necesario para tomar el contenido requerido y luego procesarlo según sea necesario, tanto en el entorno de autor como de publicación.

### Uso del lenguaje de plantilla del HTML {#using-the-html-template-language}

La variable [Lenguaje de plantilla del HTML (HTL)](https://helpx.adobe.com/experience-manager/htl/user-guide.html), introducido con AEM 6.0, sustituye a JSP (páginas de JavaServer) como sistema de plantillas preferido y recomendado del lado del servidor para HTML. Para los desarrolladores web que necesitan crear sitios web empresariales sólidos, HTL ayuda a lograr una mayor seguridad y eficacia en el desarrollo.

>[!NOTE]
>
>Aunque tanto HTL como JSP pueden utilizarse para desarrollar componentes, ilustraremos el desarrollo con HTL en esta página, ya que es el lenguaje de secuencias de comandos recomendado para AEM.

## Desarrollo de la lógica de contenido {#developing-the-content-logic}

Esta lógica opcional selecciona o calcula el contenido que se va a procesar. Se invoca desde expresiones HTL con el patrón de Use-API apropiado.

El mecanismo para separar la lógica de la apariencia ayuda a aclarar lo que se necesita para una vista determinada. También permite lógicas diferentes para vistas diferentes del mismo recurso.

### Uso de Java {#using-java}

[HTL Java Use-API permite que un archivo HTL acceda a los métodos de ayuda en una clase Java personalizada](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html). Esto le permite utilizar código Java para implementar la lógica de selección y configuración del contenido del componente.

### Uso de JavaScript {#using-javascript}

[La HTL JavaScript Use-API permite que un archivo HTL acceda al código de ayuda escrito en JavaScript](https://helpx.adobe.com/experience-manager/htl/using/use-api-javascript.html). Esto le permite utilizar código JavaScript para implementar la lógica de selección y configuración del contenido del componente.

### Uso de bibliotecas de HTML del lado del cliente {#using-client-side-html-libraries}

Los sitios web modernos dependen en gran medida del procesamiento del lado del cliente impulsado por código CSS y JavaScript complejo. Organizar y optimizar el servicio de este código puede ser un problema complicado.

Para ayudar a resolver este problema, AEM proporciona **Carpetas de biblioteca del lado del cliente**, que le permiten almacenar el código del lado del cliente en el repositorio, organizarlo en categorías y definir cuándo y cómo se debe servir cada categoría de código al cliente. A continuación, el sistema de biblioteca del lado del cliente se encarga de producir los vínculos correctos en la página web final para cargar el código correcto.

Lectura [Uso de bibliotecas de HTML del lado del cliente](/help/sites-developing/clientlibs.md) para obtener más información.

## Configuración del comportamiento de edición {#configuring-the-edit-behavior}

Puede configurar el comportamiento de edición de un componente, incluidos atributos como acciones disponibles para el componente, características del editor in situ y los oyentes relacionados con eventos en el componente. La configuración es común a la IU táctil y a la clásica, aunque con ciertas diferencias específicas.

La variable [el comportamiento de edición de un componente está configurado](/help/sites-developing/components-basics.md#edit-behavior) añadiendo un `cq:editConfig` nodo de tipo `cq:EditConfig` debajo del nodo del componente (de tipo `cq:Component`) y añadiendo propiedades específicas y nodos secundarios.

## Configuración del comportamiento de vista previa {#configuring-the-preview-behavior}

La variable [Modo WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) se establece al cambiar a **Vista previa** incluso cuando la página no se actualiza.

Para los componentes con una renderización que son sensibles al modo WCM, deben definirse para actualizarse específicamente y luego depender del valor de la cookie.

>[!NOTE]
>
>En la IU táctil solo se muestran los valores `EDIT` y `PREVIEW` se usan para la variable [Modo WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) cookie.

## Creación y configuración de un cuadro de diálogo {#creating-and-configuring-a-dialog}

Los cuadros de diálogo se utilizan para permitir que el autor interactúe con el componente. El uso de un cuadro de diálogo permite a los autores o administradores editar contenido, configurar el componente o definir parámetros de diseño (mediante un [Cuadro de diálogo Diseño](#creating-and-configuring-a-design-dialog))

### Interfaz de usuario de Coral y Granite {#coral-ui-and-granite-ui}

[Interfaz de usuario de Coral](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) y [Interfaz de usuario de Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) define el aspecto moderno de AEM.

[La interfaz de usuario de Granite proporciona una amplia gama de componentes básicos (widgets)](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) necesario para crear el cuadro de diálogo en el entorno de creación. Si es necesario, puede ampliar esta selección y crear su propio widget.

Para obtener más información, consulte:

* Interfaz de usuario de Coral

   * Proporciona una interfaz de usuario uniforme en todas las soluciones de la nube
   * [Conceptos de la IU AEM táctil: IU de Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Guía de Coral UI](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html)

* Interfaz de usuario de Granite

   * Proporciona un marcado de Coral UI dentro de componentes de Sling para crear consolas de interfaz de usuario y cuadros de diálogo
   * [Conceptos de la IU AEM táctil: Granite UI](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Documentación de Granite UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)

>[!NOTE]
>
>Debido a la naturaleza de los componentes de la interfaz de usuario de Granite (y a las diferencias con los widgets de ExtJS), hay algunas diferencias entre la forma en que los componentes interactúan con la IU táctil y la [IU clásica](/help/sites-developing/developing-components-classic.md).

### Creación de un nuevo cuadro de diálogo {#creating-a-new-dialog}

Cuadros de diálogo para la IU táctil:

* tienen nombre `cq:dialog`.
* se definen como `nt:unstructured` con el nodo `sling:resourceType` conjunto de propiedades.

* se encuentran debajo de sus `cq:Component` y junto a su definición de componente.
* se procesan en el lado del servidor (como componentes de Sling), según su estructura de contenido y el `sling:resourceType` propiedad.
* utilice el marco de la interfaz de usuario de Granite.
* contiene una estructura de nodos que describe los campos dentro del cuadro de diálogo.

   * estos nodos son `nt:unstructured` con el `sling:resourceType` propiedad.

Un ejemplo de estructura de nodos podría ser:

```xml
newComponent (cq:Component)
  cq:dialog (nt:unstructured)
    content 
      layout 
      items 
        column 
          items 
            file 
            description  
```

La personalización de un cuadro de diálogo es similar al desarrollo de un componente, ya que el cuadro de diálogo es en sí mismo un componente (es decir, el marcado procesado por un script de componente junto con el comportamiento/estilo proporcionado por una biblioteca de cliente).

Para ver ejemplos, consulte:

* `/libs/foundation/components/text/cq:dialog`
* `/libs/foundation/components/download/cq:dialog`

>[!NOTE]
>
>Si un componente no tiene ningún cuadro de diálogo definido para la IU táctil, el cuadro de diálogo de la IU clásica se utiliza como alternativa dentro de una capa de compatibilidad. Para personalizar este cuadro de diálogo, debe personalizar el cuadro de diálogo IU clásica. Consulte [Componentes AEM para la IU clásica](/help/sites-developing/developing-components-classic.md).

### Personalización de campos de cuadro de diálogo {#customizing-dialog-fields}

>[!NOTE]
>
>Consulte:
>
>* la sesión de AEM Gems sobre [Personalización de campos de cuadro de diálogo](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
>* el código de muestra relacionado cubierto en el [Ejemplo de código: Personalizar campos de cuadro de diálogo](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields).
>


#### Creación de un nuevo campo {#creating-a-new-field}

Las utilidades de la IU táctil se implementan como componentes de Granite UI.

Para crear un nuevo widget para utilizarlo en un cuadro de diálogo de componentes para la IU táctil, es necesario que [crear un nuevo componente de campo de interfaz de usuario de Granite](/help/sites-developing/granite-ui-component.md).

>[!NOTE]
>
>Para obtener más información sobre la interfaz de usuario de Granite, consulte la [Documentación de Granite UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

Si considera el cuadro de diálogo como un contenedor simple para un elemento de formulario, también puede ver el contenido principal del contenido del cuadro de diálogo como campos de formulario. La creación de un nuevo campo de formulario requiere la creación de un tipo de recurso; esto equivale a crear un componente nuevo. Para ayudarle en esa tarea, la interfaz de usuario de Granite ofrece un componente de campo genérico del que heredar (mediante `sling:resourceSuperType`):

`/libs/granite/ui/components/coral/foundation/form/field`

Más específicamente, la interfaz de usuario de Granite proporciona una serie de componentes de campo que son adecuados para su uso en diálogos (o, en términos más generales, en [formularios](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)).

>[!NOTE]
>
>Esto difiere de la IU clásica, donde los widgets se representan mediante `cq:Widgets` nodos, cada uno con un `xtype` para establecer la relación con su widget ExtJS correspondiente. Desde el punto de vista de la implementación, estas utilidades se representaron en el lado del cliente mediante el marco de trabajo de ExtJS.

Una vez creado el tipo de recurso, puede crear una instancia del campo añadiendo un nuevo nodo en el cuadro de diálogo, con la propiedad `sling:resourceType` haciendo referencia al tipo de recurso que acaba de introducir.

#### Creación de una biblioteca de cliente para estilos y comportamientos {#creating-a-client-library-for-style-and-behavior}

Si desea definir el estilo y el comportamiento del componente, puede crear una [biblioteca cliente](/help/sites-developing/clientlibs.md) que define su CSS/LESS y JS personalizados.

Para que la biblioteca de cliente se cargue únicamente para el cuadro de diálogo de componentes (es decir, no se cargará para otro componente), debe establecer la propiedad `extraClientlibs` del cuadro de diálogo con el nombre de categoría de la biblioteca de cliente que acaba de crear. Esto es aconsejable si la biblioteca de cliente es bastante grande o si el campo es específico de ese cuadro de diálogo y no lo necesitará en otros cuadros de diálogo.

Para que la biblioteca de cliente se cargue en todos los cuadros de diálogo, establezca la propiedad category de la biblioteca de cliente en `cq.authoring.dialog`. Este es el nombre de categoría de la biblioteca de cliente que se incluye de forma predeterminada al procesar todos los cuadros de diálogo. Desea hacerlo si la biblioteca de cliente es pequeña o si el campo es genérico y podría reutilizarse en otros cuadros de diálogo.

Para ver un ejemplo, consulte:

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * proporcionado por el [Ejemplo de código](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Ampliación (herencia) de un campo {#extending-inheriting-from-a-field}

Según sus necesidades, puede:

* Ampliación de un campo de interfaz de usuario de Granite determinado por herencia de componentes ( `sling:resourceSuperType`)
* Ampliar un widget determinado desde la biblioteca de widgets subyacente (en el caso de la interfaz de usuario de Granite, esta es Coral UI), siguiendo la API de biblioteca de utilidades (herencia de JS/CSS)

#### Acceso a campos de cuadro de diálogo {#access-to-dialog-fields}

También puede utilizar condiciones de renderización ( `rendercondition`) para controlar quién tiene acceso a pestañas/campos específicos del cuadro de diálogo; por ejemplo:

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Gestión de eventos de campo {#handling-field-events}

El método para gestionar eventos en campos de diálogo ahora se realiza con [oyentes en una biblioteca de cliente personalizada](#listeners-in-a-custom-client-library). Esto supone un cambio con respecto al método anterior de tener [oyentes en la estructura de contenido](#listeners-in-the-content-structure).

#### Oyentes en una biblioteca de cliente personalizada {#listeners-in-a-custom-client-library}

Para insertar lógica en el campo, debe:

1. Marque el campo con una clase CSS determinada (la variable *gancho*).
1. Defina, en la biblioteca de cliente, un oyente JS conectado a ese nombre de clase CSS (esto garantiza que la lógica personalizada tenga ámbitos únicamente en el campo y no afecte a otros campos del mismo tipo).

Para conseguirlo, debe conocer la biblioteca de widgets subyacente con la que desea interactuar. Consulte la [Documentación de Coral UI](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) para identificar a qué evento desea reaccionar. Esto es muy similar al proceso que tenía que realizar con ExtJS en el pasado: busque la página de documentación de un widget determinado y, a continuación, compruebe los detalles de su API de evento.

Para ver un ejemplo, consulte:

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * proporcionado por el [Ejemplo de código](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Oyentes en la estructura de contenido {#listeners-in-the-content-structure}

En la IU clásica con ExtJS, era habitual tener oyentes para un widget determinado en la estructura de contenido. Lograr lo mismo en la IU táctil es diferente cuando el código de oyente de JS (o cualquier código en absoluto) ya no está definido en el contenido.

La estructura de contenido describe la estructura semántica; no debe implicar la naturaleza del widget subyacente. Al no tener código JS en la estructura de contenido, puede cambiar los detalles de implementación sin tener que cambiar la estructura de contenido. En otras palabras, puede cambiar la biblioteca de utilidades sin necesidad de tocar la estructura de contenido.

#### Detección de la disponibilidad del cuadro de diálogo {#dialog-ready}

Si tiene un JavaScript personalizado que debe ejecutarse solo cuando el cuadro de diálogo esté disponible y listo, debe escuchar la `dialog-ready` evento.

Este evento se activa cada vez que se carga (o recarga) el cuadro de diálogo y está listo para utilizarse, lo que significa que siempre que haya un cambio (crear/actualizar) en el DOM del cuadro de diálogo.

`dialog-ready` se puede utilizar para conectar en código personalizado JavaScript que realiza personalizaciones en los campos dentro de un cuadro de diálogo o tareas similares.

### Validación de campos {#field-validation}

#### Campo obligatorio {#mandatory-field}

Para marcar un campo determinado como obligatorio, establezca la siguiente propiedad en el nodo de contenido del campo:

* Nombre: `required`
* Tipo: `Boolean`

Para ver un ejemplo, consulte:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title
```

#### Validación de campos (interfaz de usuario de Granite) {#field-validation-granite-ui}

La validación de campos en la interfaz de usuario de Granite y los componentes de Granite UI (equivalentes a las utilidades) se realiza mediante el uso de la variable `foundation-validation` API. [Consulte la `foundation-valdiation` Documentación de Granite para más detalles.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Para ver ejemplos, consulte:

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * proporcionado por el [Ejemplo de código](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Creación y configuración de un cuadro de diálogo de diseño {#creating-and-configuring-a-design-dialog}

El cuadro de diálogo Diseño se proporciona cuando un componente tiene detalles de diseño que se pueden editar en [Modo de diseño](/help/sites-authoring/default-components-designmode.md).

La definición es muy similar a la de un [cuadro de diálogo usado para editar contenido](#creating-a-new-dialog), con la diferencia de que se define como un nodo:

* Nombre del nodo: `cq:design_dialog`
* Tipo: `nt:unstructured`

## Creación y configuración de un editor in situ {#creating-and-configuring-an-inplace-editor}

Un editor in situ permite al usuario editar contenido directamente en el flujo de párrafos, sin necesidad de abrir un cuadro de diálogo. Por ejemplo, los componentes estándar Texto y Título tienen un editor in situ.

Un editor in situ no es necesario ni significativo para cada tipo de componente.

Consulte [Ampliación de la creación de páginas: agregar nuevo editor in situ](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) para obtener más información.

## Personalización de la barra de herramientas del componente {#customizing-the-component-toolbar}

La variable [Barra de herramientas de componentes](/help/sites-developing/touch-ui-structure.md#component-toolbar) proporciona al usuario acceso a una serie de acciones para el componente, como editar, configurar, copiar y eliminar.

Consulte [Ampliación de la creación de páginas: añadir nueva acción a una barra de herramientas de componentes](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) para obtener más información.

## Configuración de un componente para el carril de referencias (prestado/alquilado) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Si el nuevo componente hace referencia al contenido de otras páginas, puede considerar si desea que afecte a la variable **Contenido prestado** y **Contenido prestado** secciones de [**Referencias**](/help/sites-authoring/basic-handling.md#references) Carril.

La AEM predeterminada solo comprueba el componente de referencia. Para añadir su componente, debe configurar el paquete OSGi **Configuración de referencia de contenido de creación de WCM**.

Cree una nueva entrada en la definición, especificando el componente, junto con la propiedad que se va a comprobar. Por ejemplo:

`/apps/<your-Project>/components/reference@parentPath`

>[!NOTE]
>
>Al trabajar con AEM, existen varios métodos para administrar los parámetros de configuración de dichos servicios. Consulte [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

## Activación y adición del componente al sistema de párrafos {#enabling-and-adding-your-component-to-the-paragraph-system}

Una vez desarrollado el componente, debe habilitarse para su uso en un sistema de párrafos apropiado, de modo que se pueda utilizar en las páginas requeridas.

Esto se puede hacer mediante:

* using [Modo de diseño](/help/sites-authoring/default-components-designmode.md) al editar una página específica.
* definición de los componentes [en el sistema de párrafos de una plantilla](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system).

## Configurar un sistema de párrafos para que al arrastrar un recurso se cree una instancia de componente {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM ofrece la posibilidad de configurar un sistema de párrafos en la página para que [se crea automáticamente una instancia del nuevo componente cuando un usuario arrastra un recurso (adecuado) a una instancia de esa página](/help/sites-authoring/editing-content.md) (en lugar de arrastrar siempre un componente vacío a la página).

Se puede configurar este comportamiento y la relación entre activos y componentes necesaria:

1. En la definición de párrafo del diseño de la página. Por ejemplo:

   * `/etc/designs/<myApp>/page/par`

   Cree un nuevo nodo:

   * Nombre: `cq:authoring`
   * Tipo: `nt:unstructured`


1. En este nodo, cree un nuevo nodo para albergar todas las asignaciones de recursos a componentes:

   * Nombre: `assetToComponentMapping`
   * Tipo: `nt:unstructured`

1. Para cada asignación de recursos a componentes, cree un nodo:

   * Nombre: texto; se recomienda que el nombre indique el recurso y el tipo de componente relacionado; por ejemplo, image
   * Tipo: `nt:unstructured`

   Cada una con las siguientes propiedades:

   * `assetGroup`:

      * Tipo: `String`
      * Valor: el grupo al que pertenece el recurso relacionado; por ejemplo, `media`
   * `assetMimetype`:

      * Tipo: `String`
      * Valor: el tipo mime del recurso relacionado; por ejemplo `image/*`
   * `droptarget`:

      * Tipo: `String`
      * Valor: el objetivo de colocación; por ejemplo, `image`
   * `resourceType`:

      * Tipo: `String`
      * Valor: el recurso de componente relacionado; por ejemplo, `foundation/components/image`
   * `type`:

      * Tipo: `String`
      * Valor: el tipo , por ejemplo, `Images`






Para ver ejemplos, consulte:

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CÓDIGO DE GITHUB

Puede encontrar el código de esta página en GitHub

* [Abra el proyecto aem-project-archetype en GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* Descargue el proyecto como [un archivo ZIP](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/archive/master.zip)

>[!NOTE]
>
>La creación automática de instancias de componentes ahora se puede configurar fácilmente dentro de la interfaz de usuario al utilizar [Componentes principales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=es) y plantillas editables. Consulte [Creación de plantillas de página](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) para obtener más información sobre la definición de los componentes que se asocian automáticamente a determinados tipos de medios.

## Uso de la extensión AEM Brackets {#using-the-aem-brackets-extension}

La variable [Extensión de AEM Brackets](/help/sites-developing/aem-brackets.md) proporciona un flujo de trabajo suave para editar componentes de AEM y bibliotecas de cliente. Se basa en la variable [Brackets](https://brackets.io/) editor de código.

La extensión:

* Facilita la sincronización (no se requiere Maven ni File Vault) para ayudar a aumentar la eficacia del desarrollador y también ayuda a los desarrolladores de front-end con conocimientos AEM limitados a participar en proyectos.
* Proporciona algunas [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) compatibilidad, el lenguaje de plantilla diseñado para simplificar el desarrollo de componentes y aumentar la seguridad.

>[!NOTE]
>
>Brackets es el mecanismo recomendado para crear componentes. Reemplaza la funcionalidad CRXDE Lite - Crear componente , que se diseñó para la IU clásica.

## Migración desde un componente clásico {#migrating-from-a-classic-component}

Al migrar un componente diseñado para su uso con la IU clásica a un componente que se pueda utilizar con la IU táctil (solo o conjuntamente), se deben tener en cuenta los siguientes problemas:

* HTL

   * Uso de [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) no es obligatorio, pero si su componente necesita actualizarse, es el momento ideal para tener en cuenta [migración de JSP a HTL](/help/sites-developing/components-basics.md#htl-vs-jsp).

* Componentes

   * Migrar [ `cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code) código que utiliza funciones específicas de la IU clásica
   * Complemento RTE, para obtener más información, consulte [Configuración del Editor de texto enriquecido](/help/sites-administering/rich-text-editor.md).
   * [Migrar `cq:listener` code](#migrating-cq-listener-code) que utiliza funciones específicas de la IU clásica

* Cuadros de diálogo

   * Deberá crear un cuadro de diálogo nuevo para utilizarlo en la IU táctil. Sin embargo, por motivos de compatibilidad, la IU táctil puede utilizar la definición de un cuadro de diálogo de IU clásica cuando no se ha definido ningún cuadro de diálogo para la IU táctil.
   * La variable [Herramientas de modernización AEM](/help/sites-developing/modernization-tools.md) para ayudarle a ampliar los componentes existentes.
   * [Asignación de ExtJS a los componentes de la interfaz de usuario de Granite](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) proporciona información general práctica sobre xtype y tipos de nodo de ExtJS con sus tipos de recursos equivalentes de Granite UI.
   * Personalización de campos, para obtener más información, consulte la sesión de AEM Gems sobre [Personalización de campos de cuadro de diálogo](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
   * Migración de tipos a [Validación de la interfaz de usuario de Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * Uso de oyentes JS; para obtener más información, consulte [Gestión de eventos de campo](#handling-field-events) y la sesión de AEM Gems sobre [Personalización de campos de cuadro de diálogo](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).

### Migración de código cq:listener {#migrating-cq-listener-code}

Si está migrando un proyecto diseñado para la IU clásica, la variable `cq:listener` (y clientlibs relacionados con componentes) pueden utilizar funciones específicas de la IU clásica (como `CQ.wcm.*`). Para la migración, debe actualizar dicho código utilizando los objetos o funciones equivalentes en la IU táctil.

Si el proyecto se está migrando por completo a la IU táctil, deberá reemplazarlo para que utilice los objetos y funciones relevantes para la IU táctil.

Sin embargo, si el proyecto debe ocuparse tanto de la IU clásica como de la IU táctil durante el período de migración (el escenario habitual), debe implementar un conmutador para diferenciar el código independiente que hace referencia a los objetos adecuados.

Este mecanismo de conmutación se puede implementar de la siguiente manera:

```
if (Granite.author) {
    // touch UI
} else {
    // classic UI
}
```

## Documentar el componente {#documenting-your-component}

Como desarrollador, desea acceder fácilmente a la documentación de componentes para que pueda comprender rápidamente:

* Descripción
* Uso previsto
* Estructura y propiedades del contenido
* API y puntos de extensión expuestos
* Etc.

Por este motivo, es bastante fácil hacer cualquier desglose de documentación existente que tenga disponible dentro del propio componente.

Todo lo que debe hacer es colocar un `README.md` en la estructura de componentes. Este marcador se muestra en la sección [consola de componentes](/help/sites-authoring/default-components-console.md).

![chlimage_1-225](assets/chlimage_1-225.png)

El margen admitido es el mismo que para [fragmentos de contenido](/help/assets/content-fragments-markdown.md).
