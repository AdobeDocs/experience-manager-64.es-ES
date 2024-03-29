---
title: 'Plantillas de página: estáticas'
seo-title: Page Templates - Static
description: Se utiliza una plantilla para crear una página y define qué componentes se pueden utilizar dentro del ámbito seleccionado
seo-description: A Template is used to create a Page and defines which components can be used within the selected scope
uuid: 86a8ecf8-e0c5-422e-9227-7a24bb5774e3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: a483ac24-cfe7-4156-a3a8-c0f14282490c
exl-id: f313b955-c561-4827-aefc-850e45922f26
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 2%

---

# Plantillas de página: estáticas{#page-templates-static}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Una plantilla se utiliza para crear una página y define qué componentes se pueden utilizar dentro del ámbito seleccionado. Una plantilla es una jerarquía de nodos que tiene la misma estructura que la página que se va a crear, pero sin contenido real.

Cada plantilla le presentará una selección de componentes disponibles para su uso.

* Las plantillas están creadas con [Componentes](/help/sites-developing/components.md);
* Los componentes utilizan utilidades y permiten el acceso a ellas, que se utilizan para representar el contenido.

>[!NOTE]
>
>[Plantillas editables](/help/sites-developing/page-templates-editable.md) también están disponibles y son el tipo recomendado de plantillas para obtener la mayor flexibilidad y las funciones más recientes.

## Propiedades y nodos secundarios de una plantilla {#properties-and-child-nodes-of-a-template}

Una plantilla es un nodo de tipo cq:Template y tiene las siguientes propiedades y nodos secundarios:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nombre <br /> </strong></td> 
   <td><strong>Tipo <br /> </strong></td> 
   <td><strong>Descripción <br /> </strong></td> 
  </tr> 
  <tr> 
   <td>. <br /> </td> 
   <td> cq:Template</td> 
   <td>Plantilla actual. Una plantilla es de tipo nodo cq:Template.<br /> </td> 
  </tr> 
  <tr> 
   <td> allowedChildren </td> 
   <td> Cadena[]</td> 
   <td>Ruta de una plantilla que puede ser secundaria a esta plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> allowedParents</td> 
   <td> Cadena[]</td> 
   <td>Ruta de una plantilla que puede ser una plantilla principal de esta plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> allowedPaths</td> 
   <td> Cadena[]</td> 
   <td>Ruta de una página que puede basarse en esta plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> jcr:created</td> 
   <td> Fecha</td> 
   <td>Fecha de creación de la plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> jcr:description</td> 
   <td> Cadena</td> 
   <td>Descripción de la plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> jcr:title</td> 
   <td> Cadena</td> 
   <td>Título de la plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> clasificación</td> 
   <td> Largo</td> 
   <td>Clasificación de la plantilla. Se utiliza para mostrar la plantilla en la interfaz de usuario de .<br /> </td> 
  </tr> 
  <tr> 
   <td> jcr:content</td> 
   <td> cq:PageContent</td> 
   <td>Nodo que contiene el contenido de la plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> thumbnail.png</td> 
   <td> nt:file</td> 
   <td>Miniatura de la plantilla.<br /> </td> 
  </tr> 
  <tr> 
   <td> icon.png</td> 
   <td> nt:file</td> 
   <td>Icono de la plantilla.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Una plantilla es la base de una página.

Para crear una página, la plantilla debe copiarse (árbol de nodos) `/apps/<myapp>/template/<mytemplate>`) a la posición correspondiente en el árbol de sitios: esto es lo que sucede si se crea una página con la variable **Sitios web** pestaña .

Esta acción de copia también proporciona a la página su contenido inicial (normalmente solo contenido de nivel superior) y la propiedad sling:resourceType, la ruta al componente de página que se utiliza para procesar la página (todo en el nodo secundario jcr:content).

## Cómo se estructuran las plantillas {#how-templates-are-structured}

Hay dos aspectos que se deben tener en cuenta:

* la estructura de la plantilla
* la estructura del contenido producido al utilizar una plantilla

### La estructura de una plantilla {#the-structure-of-a-template}

Una plantilla se crea bajo un nodo de tipo **cq:Template**.

![screen_shot_2012-02-13at63646pm](assets/screen_shot_2012-02-13at63646pm.png)

Se pueden configurar varias propiedades, en particular:

* **jcr:title** - título de la plantilla; aparece en el cuadro de diálogo al crear una página.
* **jcr:description** - descripción de la plantilla; aparece en el cuadro de diálogo al crear una página.

Este nodo contiene un nodo jcr:content (cq:PageContent) que se utiliza como base para el nodo de contenido de las páginas resultantes; esto hace referencia, utilizando sling:resourceType, al componente que se utilizará para procesar el contenido real de una página nueva.

![screen_shot_2012-02-13at64010pm](assets/screen_shot_2012-02-13at64010pm.png)

Este componente se utiliza para definir la estructura y el diseño del contenido cuando se crea una página nueva.

![screen_shot_2012-02-13at64137pm](assets/screen_shot_2012-02-13at64137pm.png)

### El contenido producido por una plantilla {#the-content-produced-by-a-template}

Las plantillas se utilizan para crear páginas de tipo `cq:Page` (como se mencionó anteriormente, una página es un tipo especial de componente). Cada página AEM tiene un nodo estructurado `jcr:content`. Así pues:

* es del tipo cq:PageContent
* es un tipo de nodo estructurado que contiene una definición de contenido definida
* tiene una propiedad `sling:resourceType` para hacer referencia al componente que contiene las secuencias de comandos de sling utilizadas para procesar el contenido

### Plantillas predeterminadas {#default-templates}

AEM incluye una serie de plantillas predeterminadas disponibles de forma predeterminada. En algunos casos, es posible que desee utilizar las plantillas tal cual. En ese caso, debe asegurarse de que la plantilla esté disponible para el sitio web.

Por ejemplo, AEM viene con varias plantillas, incluidas una página de contenido y una página de inicio.

| **Título** | **Componente** | **Ubicación** | **Función** |
|---|---|---|---|
| Página principal | homepage | geometrixx | La plantilla de la página principal de Geometrixx. |
| Página de contenido | contentpage | geometrixx | La plantilla de página de contenido de Geometrixx. |

#### Visualización de plantillas predeterminadas {#displaying-default-templates}

Para ver una lista de todas las plantillas en el repositorio, siga este procedimiento:

1. En el CRXDE Lite, abra el **Herramientas** y haga clic en **Consulta**.

1. En la ficha Consulta
1. Como **Tipo**, seleccione **XPath**.
1. En el campo de entrada **Consulta**, escriba la cadena siguiente:

   //element(&amp;ast;, cq:Template)

1. Haga clic en **Ejecutar**. La lista se muestra en el cuadro de resultados.

En la mayoría de los casos, tomará una plantilla existente y desarrollará una nueva para su propio uso. Consulte [Desarrollo de plantillas de página](#developing-page-templates) para obtener más información.

Para habilitar una plantilla existente para su sitio web y desea que se muestre en la **Crear página** al crear una página directamente debajo de **Sitios web** de la variable **Sitios web** consola, establezca la propiedad allowedPaths del nodo template en: **/content(/.&amp;ast;)?**

## Aplicación de los diseños de plantilla {#how-template-designs-are-applied}

Cuando los estilos se definen en la interfaz de usuario mediante [Modo de diseño](/help/sites-authoring/default-components-designmode.md), el diseño se mantiene en la ruta exacta del nodo de contenido para el que se está definiendo el estilo.

>[!CAUTION]
>
>Adobe recomienda aplicar solo diseños [Modo de diseño](/help/sites-authoring/default-components-designmode.md).
>
>La modificación de diseños en CRX DE, por ejemplo, no es una práctica recomendada y la aplicación de dichos diseños puede variar del comportamiento esperado.

Si los diseños solo se aplican mediante el modo Diseño, las siguientes secciones, [Resolución de la ruta de diseño](/help/sites-developing/page-templates-static.md#design-path-resolution), [Árbol de decisiones](/help/sites-developing/page-templates-static.md#decision-tree)y [Ejemplo](/help/sites-developing/page-templates-static.md#example) no son aplicables.

>[!NOTE]
>
>En esta sección se describe el comportamiento de resolución de ruta de diseño a partir de AEM 6.4.2.0.

### Resolución de la ruta de diseño {#design-path-resolution}

Al procesar contenido basado en una plantilla estática, AEM intentará aplicar el diseño y los estilos más relevantes al contenido en función de una travesía de la jerarquía de contenido.

AEM determina el estilo más relevante para un nodo de contenido en el siguiente orden:

* Si hay un diseño para la ruta completa y exacta del nodo de contenido (como cuando el diseño se define en el modo Diseño), utilice ese diseño.
* Si hay un diseño para el nodo de contenido del elemento principal, utilice ese diseño.
* Si hay un diseño para cualquier nodo en la ruta del nodo de contenido, utilice ese diseño.

En los dos últimos casos, si hay más de un diseño aplicable, utilice el más cercano al nodo de contenido.

### Árbol de decisiones {#decision-tree}

Esta es una representación gráfica de la variable [Resolución de la ruta de diseño](/help/sites-developing/page-templates-static.md#design-path-resolution) lógica.

![design_path_resolution](assets/design_path_resolution.png)

### Ejemplo {#example}

Considere una estructura de contenido simple como se indica a continuación, donde un diseño podría aplicarse a cualquiera de los nodos:

`/root/branch/leaf`

En la tabla siguiente se describe cómo AEM elegir un diseño.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Búsqueda De Diseño Para<br /> </strong></td> 
   <td><strong>Existen diseños para<br /> </strong></td> 
   <td><strong>Diseño elegido<br /> </strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr> 
  <tr> 
   <td><code class="code">leaf
      </code></td> 
   <td><p><code>root</code></p> <p><code>branch</code></p> <p><code>leaf</code></p> </td> 
   <td><code>leaf</code></td> 
   <td>La coincidencia más exacta siempre se toma.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>leaf</code></td> 
   <td><p><code>root</code></p> <p><code>branch</code></p> </td> 
   <td><code>branch</code></td> 
   <td>Volverá a la coincidencia más cercana inferior del árbol.</td> 
  </tr> 
  <tr> 
   <td><code>leaf</code></td> 
   <td><code>root</code></td> 
   <td><code>root</code></td> 
   <td>Si todo lo demás falla, tome lo que queda.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>branch</code></td> 
   <td><code>branch</code></td> 
   <td><code>branch</code></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>branch</code></td> 
   <td><p><code>branch</code></p> <p><code class="code">leaf
       </code></p> </td> 
   <td><code>branch</code></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>branch</code></td> 
   <td><p><code>root</code></p> <p><code class="code">branch
       </code></p> </td> 
   <td><code>branch</code></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>branch</code></td> 
   <td><p><code>root</code></p> <p><code class="code">leaf
       </code></p> </td> 
   <td><code>root</code></td> 
   <td><p>Si no hay una coincidencia exacta, tome la una inferior del árbol.</p> <p>Se supone que esto siempre será aplicable, pero más arriba el árbol puede ser demasiado específico.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Desarrollo de plantillas de página {#developing-page-templates}

AEM plantillas de página son simplemente modelos utilizados para crear páginas nuevas. Pueden contener tan poco contenido inicial como sea necesario, o tanto, su función es crear las estructuras de nodos iniciales correctas, con las propiedades requeridas (principalmente sling:resourceType) configuradas para permitir la edición y el procesamiento.

### Creación de una plantilla nueva (basada en una plantilla existente) {#creating-a-new-template-based-on-an-existing-template}

Huelga decir que una plantilla nueva se puede crear completamente desde cero, pero a menudo una plantilla existente se copiará y actualizará para ahorrarle tiempo y esfuerzo. Por ejemplo, las plantillas de Geometrixx se pueden utilizar para empezar.

Para crear una plantilla nueva basada en una plantilla existente:

1. Copie una plantilla existente (preferiblemente con una definición lo más cercana posible a lo que desea lograr) en un nuevo nodo.

   Las plantillas normalmente se almacenan en **/apps/&lt;website-name>/templates/&lt;template-name>**.

   >[!NOTE]
   >
   >La lista de plantillas disponibles depende de la ubicación de la nueva página y de las restricciones de colocación especificadas en cada plantilla. Consulte [Disponibilidad de plantillas](/help/sites-developing/templates.md#template-availability).

1. Cambie el **jcr:title** del nuevo nodo de plantilla para reflejar su nueva función. También puede actualizar el **jcr:description** si procede. Asegúrese de cambiar la disponibilidad de la plantilla de la página según corresponda.

   >[!NOTE]
   >
   >Si desea que la plantilla se muestre en la variable **Crear página** al crear una página directamente debajo de **Sitios web** de la variable **Sitios web** consola, establezca la variable `allowedPaths` propiedad del nodo de plantilla a: `/content(/.*)?`

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Copie el componente en el que se basa la plantilla (esto se indica con la variable **sling:resourceType** propiedad de la variable **jcr:content** dentro de la plantilla ) para crear una nueva instancia.

   Los componentes normalmente se almacenan en **/apps/&lt;website-name>/components/&lt;component-name>**.

1. Actualice el **jcr:title** y **jcr:description** del nuevo componente.
1. Reemplace thumbnail.png si desea que una nueva imagen en miniatura se muestre en la lista de selección de plantillas (tamaño 128 x 98 px).
1. Actualice el **sling:resourceType** de la plantilla **jcr:content** para hacer referencia al nuevo componente.
1. Realice cualquier cambio adicional en la funcionalidad o el diseño de la plantilla o su componente subyacente.

   >[!NOTE]
   >
   >Los cambios realizados en la variable **/apps/&lt;website>/templates/&lt;template-name>** afectará a la instancia de la plantilla (como en la lista de selección).
   Los cambios realizados en la variable **/apps/&lt;website>/components/&lt;component-name>** afecta a la página de contenido creada al utilizar la plantilla.

   Ahora puede crear una página dentro del sitio web utilizando la nueva plantilla.

>[!NOTE]
La biblioteca de cliente del editor asume la presencia de la variable `cq.shared` espacio de nombres en páginas de contenido y si no hay el error de JavaScript `Uncaught TypeError: Cannot read property 'shared' of undefined` será el resultado.
Todas las páginas de contenido de ejemplo contienen `cq.shared`, por lo que cualquier contenido basado en ellos se incluye automáticamente `cq.shared`. Sin embargo, si decide crear sus propias páginas de contenido desde cero sin basarlas en contenido de muestra, debe asegurarse de incluir la variable `cq.shared` espacio de nombres.
Consulte [Uso de bibliotecas del lado del cliente](/help/sites-developing/clientlibs.md) para obtener más información.

## Disponibilidad de una plantilla existente {#making-an-existing-template-available}

Este ejemplo ilustra cómo permitir que se utilice una plantilla para determinadas rutas de contenido. Las plantillas que están disponibles para el autor de la página al crear páginas nuevas están determinadas por la lógica definida en [Disponibilidad de plantillas](/help/sites-developing/templates.md#template-availability).

1. En CRXDE Lite, vaya a la plantilla que desee utilizar para su página, por ejemplo, la plantilla Newsletter .
1. Cambie el `allowedPaths` propiedad y otras propiedades utilizadas para [disponibilidad de plantillas](/help/sites-developing/templates.md#template-availability). Por ejemplo, `allowedPaths`: `/content/geometrixx-outdoors/[^/]+(/.*)?` significa que esta plantilla está permitida en cualquier ruta bajo `/content/geometrixx-outdoors`.

   ![chlimage_1-252](assets/chlimage_1-252.png)
