---
title: Conceptos de la IU táctil AEM
seo-title: Concepts of the AEM Touch-Enabled UI
description: Con AEM Adobe 5.6 se ha introducido una nueva IU táctil con un diseño interactivo para el entorno de creación
seo-description: With AEM 5.6 Adobe introduced a new touch-optimized UI with responsive design for the author environment
uuid: 8ec6514e-f623-40be-a7bf-2e85bf4385ca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8c7e5667-14c5-40f3-968a-c574b04671e3
exl-id: a89cf964-cc9f-46d7-afd8-150d48948513
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2233'
ht-degree: 1%

---

# Conceptos de la IU táctil AEM{#concepts-of-the-aem-touch-enabled-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Con AEM Adobe 5.6 se ha introducido una nueva IU táctil con [diseño interactivo](/help/sites-authoring/responsive-layout.md) para el entorno de creación. Esto difiere considerablemente de la IU clásica original, ya que está diseñada para funcionar tanto en dispositivos táctiles como de escritorio.

Esta IU táctil es ahora la IU estándar para AEM y sustituye a la IU clásica.

>[!NOTE]
>
>La IU táctil es la IU estándar para AEM, aunque la IU clásica sigue siendo compatible.

La IU táctil incluye:

* Encabezado de grupo que:

   * Muestra el logotipo
   * Proporciona un vínculo a la navegación global
   * Proporciona un vínculo a otras acciones genéricas; como Búsqueda, Ayuda, Soluciones de Marketing Cloud, Notificaciones y Configuración de usuario.

* El carril izquierdo (se muestra cuando es necesario y se puede ocultar), que puede mostrar:

   * Escala de cronología
   * Referencias
   * Filtros

* El encabezado de navegación, que también es sensible al contexto y puede mostrar:

   * Indica la consola que está utilizando o la ubicación dentro de esa consola
   * Selección del carril izquierdo
   * Rutas de exploración
   * Acceso adecuado **Crear** acciones
   * Ver selecciones

* El área de contenido que:

   * Enumera los elementos de contenido (ya sean páginas, recursos, publicaciones en foros, etc.)
   * Se puede formatear como se solicite, por ejemplo, columna, tarjeta o lista
   * Utiliza un diseño interactivo (la pantalla cambia de tamaño automáticamente según el dispositivo o el tamaño de la ventana)
   * Utiliza el desplazamiento infinito (no más paginación, todos los elementos se enumeran en una ventana)

![chlimage_1-183](assets/chlimage_1-183.png)

>[!NOTE]
>
>Casi todas las funcionalidades de AEM se han portado a la IU táctil. Sin embargo, en algunos casos limitados, la funcionalidad volverá a la IU clásica. Consulte [Estado de las funciones de la interfaz de usuario táctil](/help/release-notes/touch-ui-features-status.md) para obtener más información.

La IU táctil ha sido diseñada por Adobe para ofrecer coherencia en la experiencia del usuario en varios productos. Se basa en:

* **Interfaz de usuario de Coral** (CUI) una implementación del estilo visual de Adobe para la IU táctil. La interfaz de usuario de Coral proporciona todo lo que su producto, proyecto o aplicación web necesita para adoptar el estilo visual de la interfaz de usuario.
* **Interfaz de usuario de Granite** los componentes se crean con la interfaz de usuario de Coral.

Los principios básicos de la IU táctil son:

* Móvil primero (con el escritorio en mente)
* Diseño interactivo
* Visualización relevante para el contexto
* Reutilizable
* Incluir documentación de referencia incrustada
* Incluir pruebas incrustadas
* Diseño de abajo arriba para garantizar que estos principios se apliquen a cada elemento y componente

Para obtener más información general sobre la estructura de la IU táctil, consulte el artículo [Estructura de la interfaz de usuario táctil AEM](/help/sites-developing/touch-ui-structure.md).

## Pila de tecnología AEM {#aem-technology-stack}

AEM utiliza la plataforma Granite como base y la plataforma Granite incluye, entre otras cosas, el Repositorio de Contenido Java.

![chlimage_1-184](assets/chlimage_1-184.png)

## Granite {#granite}

Granite es la pila web abierta de Adobe que proporciona varios componentes, entre los que se incluyen:

* Un iniciador de aplicación
* Un marco OSGi en el que todo está implementado
* Varios servicios de compendio OSGi para apoyar las aplicaciones de construcción
* Un marco de registro completo que proporciona varias API de registro
* Implementación del repositorio CRX de la especificación de la API JCR
* El marco web Apache Sling
* Partes adicionales del producto CRX actual

>[!NOTE]
>
>Granite se ejecuta como un proyecto de desarrollo abierto dentro del Adobe: las contribuciones al código, los debates y los problemas se realizan desde toda la compañía.
>
>Sin embargo, Granite es **not** un proyecto de código abierto. Está fuertemente basado en varios proyectos de código abierto (Apache Sling, Felix, Jackrabbit y Lucene en particular), pero el Adobe traza una línea clara entre lo que es público y lo que es interno.

## Interfaz de usuario de Granite {#granite-ui}

La plataforma de ingeniería de Granite también proporciona un marco de IU base. Los principales objetivos son:

* Proporcionar widgets de IU granulares
* Implemente los conceptos de la interfaz de usuario e ilustre las prácticas recomendadas (representación de listas largas, filtrado de listas, CRUD de objetos, asistentes CUD...).
* Proporcionar una interfaz de usuario de administración ampliable y basada en complementos

Cumplen los requisitos:

* Respetar &quot;móvil primero&quot;
* Ser extensible
* Sea fácil de anular

![](assets/chlimage_1-185.png)

La interfaz de usuario de Granite:

* Utiliza la arquitectura RESTful de Sling
* Implementa bibliotecas de componentes diseñadas para crear aplicaciones web centradas en el contenido
* Proporciona widgets de IU granulares
* Proporciona una interfaz de usuario estándar predeterminada
* Es extensible
* Está diseñado tanto para dispositivos móviles como de escritorio (primero respeta el móvil)
* Puede utilizarse en cualquier plataforma, producto o proyecto basado en Granite; p AEM

![chlimage_1-186](assets/chlimage_1-186.png)

* [Componentes básicos de Granite UI](#granite-ui-foundation-components)

   Otras bibliotecas pueden usar o ampliar esta biblioteca de componentes de base.

* [Componentes de administración de Granite UI](#granite-ui-administration-components)

### Lado del cliente frente al servidor {#client-side-vs-server-side}

La comunicación cliente-servidor en la interfaz de usuario de Granite consiste en hipertexto, no en objetos, por lo que no es necesario que el cliente entienda la lógica empresarial

* El servidor enriquece el HTML con datos semánticos
* El cliente enriquece el hipertexto con hipermedios (interacción)

![chlimage_1-187](assets/chlimage_1-187.png)

#### Lado del cliente {#client-side}

Esto utiliza una extensión del vocabulario del HTML, siempre que el autor pueda expresar su intención de crear un webapp interactivo. Este es un enfoque similar a [WAI-ARIA](https://www.w3.org/TR/wai-aria/) y [microformatos](http://microformats.org/).

Consiste principalmente en una colección de patrones de interacción (por ejemplo, el envío asincrónico de un formulario) que son interpretados por códigos JS y CSS, que se ejecutan en el lado del cliente. La función del lado del cliente es mejorar el marcado (dado como el soporte multimedia del servidor) para la interactividad.

El lado del cliente es independiente de cualquier tecnología de servidor. Siempre que el servidor proporcione el marcado adecuado, el lado del cliente puede cumplir su función.

Actualmente, los códigos JS y CSS se entregan como Granite [clientlibs](/help/sites-developing/clientlibs.md) en la categoría :

`granite.ui.foundation and granite.ui.foundation.admin`

Se entregan como parte del paquete de contenido:

`granite.ui.content`

#### Servidor {#server-side}

Esto se forma mediante una colección de componentes de Sling que permiten al autor *componer* un webapp rápido. El desarrollador desarrolla componentes, el autor ensamblan los componentes para que sean una aplicación web. La función del lado del servidor es proporcionar al cliente la asequibilidad de los hipermedios (marcado).

Actualmente, los componentes se encuentran en el repositorio de Granite, en:

`/libs/granite/ui/components/foundation`

Esto se entrega como parte del paquete de contenido:

`granite.ui.content`

### Diferencias con la IU clásica {#differences-with-the-classic-ui}

Las diferencias entre la interfaz de usuario de Granite y ExtJS (utilizado para la IU clásica) también son de interés:

<table> 
 <tbody> 
  <tr> 
   <td><strong>ExtJS</strong></td> 
   <td><strong>Interfaz de usuario de Granite</strong></td> 
  </tr> 
  <tr> 
   <td>Llamada de procedimiento remoto<br /> </td> 
   <td>Transiciones de estado</td> 
  </tr> 
  <tr> 
   <td>Objetos de transferencia de datos</td> 
   <td>Hipermedia</td> 
  </tr> 
  <tr> 
   <td>El cliente conoce los internos del servidor</td> 
   <td>El cliente no conoce los internos</td> 
  </tr> 
  <tr> 
   <td>"Cliente ligero"</td> 
   <td>"Cliente ligero"</td> 
  </tr> 
  <tr> 
   <td>Bibliotecas de cliente especializadas</td> 
   <td>Bibliotecas de cliente universales</td> 
  </tr> 
 </tbody> 
</table>

### Componentes básicos de Granite UI {#granite-ui-foundation-components}

La variable [Componentes básicos de Granite UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) proporciona los componentes básicos necesarios para crear cualquier interfaz de usuario. Entre otros:

* Botón
* Hipervínculo
* Avatar del usuario

Los componentes de base se encuentran en:

`/libs/granite/ui/components/foundation`

Esta biblioteca contiene un componente de interfaz de usuario de Granite para cada elemento Coral. Un componente está impulsado por contenido, con su configuración residiendo en el repositorio. Esto permite componer una aplicación de interfaz de usuario de Granite sin escribir a mano el marcado del HTML.

Función:

* Modelo de componente para elementos HTML
* Composición de componentes
* Pruebas automáticas de unidades y funcionalidades

Implementación:

* Composición y configuración basadas en repositorios
* Aprovechamiento de las instalaciones de pruebas proporcionadas por la plataforma Granite
* Plantilla JSP

Otras bibliotecas pueden usar o ampliar esta biblioteca de componentes de base.

### Componentes de interfaz de usuario de ExtJS y Granite correspondientes {#extjs-and-corresponding-granite-ui-components}

Al actualizar el código de ExtJS para utilizar la interfaz de usuario de Granite, la siguiente lista proporciona una descripción general práctica de los xtype y tipos de nodo de ExtJS con sus tipos de recursos equivalentes de la interfaz de usuario de Granite.

| **ExtJS xtype** | **Tipo de recurso de la interfaz de usuario de Granite** |
|---|---|
| `button` | `granite/ui/components/foundation/form/button` |
| `checkbox` | `granite/ui/components/foundation/form/checkbox` |
| `componentstyles` | `cq/gui/components/authoring/dialog/componentstyles` |
| `cqinclude` | `granite/ui/components/foundation/include` |
| `datetime` | `granite/ui/components/foundation/form/datepicker` |
| `dialogfieldset` | `granite/ui/components/foundation/form/fieldset` |
| `hidden` | `granite/ui/components/foundation/form/hidden` |
| `html5smartfile, html5smartimage` | `granite/ui/components/foundation/form/fileupload` |
| `multifield` | `granite/ui/components/foundation/form/multifield` |
| `numberfield` | `granite/ui/components/foundation/form/numberfield` |
| `pathfield, paragraphreference` | `granite/ui/components/foundation/form/pathbrowser` |
| `selection` | `granite/ui/components/foundation/form/select` |
| `sizefield` | `cq/gui/components/authoring/dialog/sizefield` |
| `tags` | `granite/ui/components/foundation/form/autocomplete` `cq/gui/components/common/datasources/tags` |
| `textarea` | `granite/ui/components/foundation/form/textarea` |
| `textfield` | `granite/ui/components/foundation/form/textfield` |

| **Tipo de nodo** | **Tipo de recurso de la interfaz de usuario de Granite** |
|---|---|
| `cq:WidgetCollection` | `granite/ui/components/foundation/container` |
| `cq:TabPanel` | `granite/ui/components/foundation/container` `granite/ui/components/foundation/layouts/tabs` |
| `cq:panel` | `granite/ui/components/foundation/container` |

### Componentes de administración de Granite UI {#granite-ui-administration-components}

La variable [Componentes de administración de Granite UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) aproveche los componentes de base para proporcionar componentes genéricos que cualquier aplicación de administración puede implementar. Entre ellos se incluyen:

* Barra de navegación global
* Carril (esqueleto)
* Panel de búsqueda

Función:

* Aspecto unificado para aplicaciones de administración
* Rad para aplicaciones de administración

Implementación:

* Componentes predefinidos que utilizan los componentes de base
* Los componentes se pueden personalizar

## Interfaz de usuario de Coral {#coral-ui}

La IU de Coral (CUI) es una implementación del estilo visual de Adobe para la IU táctil, que se ha diseñado para proporcionar coherencia en la experiencia del usuario en varios productos. La IU de Coral proporciona todo lo necesario para adoptar el estilo visual utilizado en el entorno de creación.

>[!CAUTION]
>
>Coral UI es una biblioteca de IU disponible para los clientes de AEM para crear aplicaciones e interfaces web dentro de los límites de su uso con licencia del producto.
>
>El uso de la IU de Coral solo está permitido:
>
>* Cuando se ha enviado y empaquetado con AEM.
>* Se utiliza al ampliar la IU existente del entorno de creación.
>* Adobe de garantías corporativas, anuncios y presentaciones.
>* La interfaz de usuario de las aplicaciones con marca de Adobe (la fuente no debe estar fácilmente disponible para otros usos).
>* Con personalizaciones menores.
>
>El uso de la IU de Coral debe evitarse en:
>
>* Documentos y otros artículos no relacionados con el Adobe.
>* Entornos de creación de contenido (donde otros pueden generar los elementos anteriores).
>* Aplicaciones/componentes/páginas web que no están claramente conectadas al Adobe.
>


La interfaz de usuario de Coral es una colección de componentes básicos para el desarrollo de aplicaciones web.

![chlimage_1-188](assets/chlimage_1-188.png)

Diseñado para ser modular desde el principio, cada módulo forma una capa distinta basada en su función principal. Aunque las capas se han diseñado para apoyarse mutuamente, también pueden utilizarse de forma independiente si es necesario. Esto permite implementar la experiencia de usuario de Coral en cualquier entorno compatible con HTML.

Con la interfaz de usuario de Coral no es obligatorio utilizar un modelo de desarrollo o una plataforma particulares. El objetivo principal de Coral es proporcionar un marcado HTML5 unificado y limpio, independiente del método real utilizado para emitir este marcado. Esto puede utilizarse para el procesamiento del lado del cliente o del servidor, plantillas, JSP, PHP o incluso aplicaciones RIA de Flash de Adobe, por nombrar solo algunas.

### Elementos de HTML: la capa de marcado {#html-elements-the-markup-layer}

Los elementos HTML proporcionan un aspecto común para todos los elementos de la interfaz de usuario base (incluida la barra de navegación, el botón, el menú, el carril, entre otros).

En el nivel más básico, un elemento HTML es una etiqueta HTML con un nombre de clase dedicado. Los elementos más complejos pueden estar compuestos por varias etiquetas, anidadas entre sí (de forma específica).

El CSS se utiliza para proporcionar el aspecto real. Para que sea posible personalizar fácilmente la apariencia (por ejemplo, en el caso de la promoción de la marca), los valores de estilo reales se declaran como variables expandidas por el [LESS](https://lesscss.org/) preprocesador durante el tiempo de ejecución.

Función:

* Proporcionar elementos básicos de la interfaz de usuario con una apariencia común
* Proporcionar el sistema de cuadrícula predeterminado

Implementación:

* etiquetas HTML con estilos inspirados en [bootstrap](https://twitter.github.com/bootstrap/)
* Las clases se definen en archivos LESS
* Los iconos se definen como sprites de fuente

Por ejemplo, el marcado:

```xml
<button class="btn btn-large btn-primary" type="button">Large button</button> 
<button class="btn btn-large" type="button">Large button</button>
```

Se muestra como:

![chlimage_1-189](assets/chlimage_1-189.png)

La apariencia se define en LESS, y se vincula a un elemento con un nombre de clase dedicado (el siguiente extracto se ha acortado en aras de la brevedad):

```xml
.btn {
    font-size: @baseFontSize; 
    line-height: @baseLineHeight; 
    .buttonBackground(@btnBackground,
                                @btnBackgroundHighlight,
                                @grayDark, 0 1px 1px rgba(255,255,255,.75));
```

Los valores reales se definen en un archivo de variable LESS (se ha abreviado el siguiente extracto en aras de la brevedad):

```xml
@btnBackgroundHighlight: darken(@white, 10%); 
@btnPrimaryBackgroundHighlight: spin(@btnPrimaryBackground, 20%); 
@baseFontSize: 17px;
@baseFontFamily: @sansFontFamily;
```

### Complementos de elementos {#element-plugins}

Muchos de los elementos del HTML deberán mostrar algún tipo de comportamiento dinámico, como abrir y cerrar menús emergentes. Esta es la función de los complementos de elemento, que realizan estas tareas manipulando el DOM mediante JavaScript.

Un complemento puede ser:

* Diseñado para funcionar con un elemento DOM específico. Por ejemplo, un complemento de cuadro de diálogo espera encontrar `DIV class=dialog`
* Genérico por naturaleza. Por ejemplo, un administrador de diseños proporciona un diseño para cualquier lista de `DIV` o `LI` elementos

El comportamiento del complemento se puede personalizar con parámetros mediante:

* Pasar los parámetros mediante una llamada de javascript
* Uso de `data-*` atributos vinculados al marcado del HTML

Aunque el desarrollador puede seleccionar el mejor enfoque para cualquier complemento, la regla general es utilizar:

* `data-*` atributos para opciones relacionadas con el diseño del HTML. Por ejemplo, para especificar el número de columnas
* Opciones/clases de API para funciones relacionadas con los datos. Por ejemplo, construir la lista de elementos para mostrar

Se utiliza el mismo concepto para implementar la validación del formulario. Para un elemento que desea validar, debe especificar el formulario de entrada requerido como personalizado `data-*` atributo. A continuación, este atributo se utiliza como opción para un complemento de validación.

>[!NOTE]
>
>La validación del formulario nativo de HTML5 debe utilizarse siempre que sea posible y/o expandirse a partir de ella.

Función:

* Proporcionar comportamiento dinámico para elementos de HTML
* Proporcionar diseños personalizados no posibles con CSS pura
* Realizar validación del formulario
* Realizar manipulación DOM avanzada

Implementación:

* Complemento jQuery, vinculado a elementos DOM específicos
* Uso `data-*` atributos para personalizar el comportamiento

Un extracto de ejemplo de marcado (observe las opciones especificadas como data&amp;ast; atributos):

```xml
<ul data-column-width="220" data-layout="card" class="cards">
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png"> 
      <div class="caption">
        <h4>Toolbar</h4>
          <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png"> 
      <div class="caption">
        <h4>Toolbar</h4>
        <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
```

Llamada al complemento jQuery:

```
$(‘.cards’).cardlayout ();
```

Esto se mostrará como:

![chlimage_1-190](assets/chlimage_1-190.png)

La variable `cardLayout` el complemento presenta el `UL` elementos basados en sus alturas respectivas y teniendo en cuenta también la anchura del elemento principal.

### Widgets de elementos del HTML {#html-elements-widgets}

Un widget combina uno o más elementos básicos con un complemento de javascript para formar elementos de IU de &quot;nivel superior&quot;. Esto puede implementar un comportamiento más complejo y también una apariencia más compleja de la que podría ofrecer un solo elemento. Algunos ejemplos son el selector de etiquetas o los widgets de raíl.

Un widget puede almacenar en déclencheur y escuchar eventos personalizados para cooperar con otras utilidades de la página. Algunas utilidades son en realidad utilidades nativas de jQuery que utilizan los elementos del HTML de Coral.

Función:

* Implementar elementos de interfaz de usuario de nivel superior que muestren un comportamiento complejo
* Activación y gestión de eventos

Implementación:

* Complemento jQuery + marcado de HTML
* Puede utilizar plantillas del lado del cliente/servidor

El ejemplo de marcado es:

```
<input type="text" name="tags" placeholder="Tags" class="tagManager"/>
```

Llamada al complemento jQuery (con opciones):

```
$(".tagManager").tagsManager({
        prefilled: ["Pisa", "Rome"] })
```

El complemento emite el marcado del HTML (este marcado utiliza elementos básicos, que pueden utilizar otros complementos internamente):

```
<span>Pisa</span>
<a title="Removing tag" tagidtoremove="0"
   id="myRemover_0" class="myTagRemover" href="#">x</a></span>

<span id="myTag_1" class="myTag"><span>Rome</span>
<a title="Removing tag" tagidtoremove="1"
   id="myRemover_1" class="myTagRemover" href="#">x</a></span>

<input type="text" data-original-title="" class="input-medium tagManager"
       placeholder="Tags" name="tags" data-provide="typeahead" data-items="6"
       autocomplete="off">
```

Esto se mostrará como:

![chlimage_1-191](assets/chlimage_1-191.png)

### Biblioteca de utilidades {#utility-library}

Esta biblioteca es una colección de complementos de ayuda de javascript y/o funciones que son:

* IU independiente
* Sin embargo, es crucial para crear aplicaciones web con todas las funciones

Estos incluyen el manejo de XSS y el bus de evento.

Aunque los complementos y las utilidades del elemento HTML pueden depender de la funcionalidad proporcionada por la biblioteca de utilidades, la biblioteca de utilidades no puede tener dependencia fuerte de los elementos ni de las utilidades.

Función:

* Proporcionar funcionalidad común
* Implementación del bus de evento
* Plantillas del lado del cliente
* XSS

Implementación:

* Complementos jQuery o módulos JavaScript compatibles con AMD
