---
title: Ampliación y configuración del Importador de diseños para páginas de aterrizaje
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: Aprenda a configurar el Importador de diseños para páginas de aterrizaje.
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: b2bfe831-bfaf-43f3-babc-687bf229dd44
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: f8991416-995b-4160-a705-d131e78089ee
exl-id: 4b37c866-30c3-45ff-b7a3-013b69598668
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3526'
ht-degree: 0%

---

# Ampliación y configuración del Importador de diseños para páginas de aterrizaje{#extending-and-configuring-the-design-importer-for-landing-pages}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta sección se describe cómo configurar y, si lo desea, ampliar el importador de diseños para páginas de aterrizaje. El trabajo con páginas de aterrizaje tras la importación se trata en [Páginas de aterrizaje.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**Cómo hacer que el importador de diseños extraiga su componente personalizado**

Estos son los pasos lógicos para que el importador de diseños reconozca su componente personalizado

1. Creación de un TagHandler

   * Un controlador de tags es un POJO que gestiona etiquetas HTML de un tipo específico. El &quot;tipo&quot; de etiquetas de HTML que TagHandler puede gestionar se define mediante la propiedad OSGi &quot;tagpattern.name&quot; de TagHandlerFactory. Esta propiedad OSGi es esencialmente una regex que debería coincidir con la etiqueta HTML de entrada que desea gestionar. Todas las etiquetas anidadas se enviarán al controlador de etiquetas para que las gestione. Por ejemplo, si se registra en un div que contiene un anidado &lt;p> , la variable &lt;p> también se lanzaría a TagHandler y depende de usted cómo desea encargarse de ella.
   * La interfaz del controlador de etiquetas es similar a una interfaz de controlador de contenido SAX. Recibe eventos SAX para cada etiqueta html. Como proveedor del controlador de tags, debe implementar ciertos métodos de ciclo vital a los que el marco del importador de diseños llama automáticamente.

1. Cree su TagHandlerFactory correspondiente.

   * La fábrica del controlador de etiquetas es un componente OSGi (singleton) responsable de generar instancias de su controlador de etiquetas.
   * la fábrica del controlador de etiquetas debe exponer una propiedad OSGi llamada &quot;tagpattern.name&quot;, cuyo valor coincide con la etiqueta HTML de entrada.
   * Si hay varios controladores de etiquetas que coinciden con la etiqueta HTML de entrada, se selecciona el que tenga una clasificación superior. La propia clasificación se expone como una propiedad OSGi **service.ranking**.
   * TagHandlerFactory es un componente OSGi. Todas las referencias que desee proporcionar a TagHandler deben realizarse a través de esta fábrica.

1. Asegúrese de que TagHandlerFactory tenga una clasificación mejor si desea anular la predeterminada.

## Preparación del HTML para la importación {#preparing-the-html-for-import}

Después de crear una página de importador, puede importar la página de aterrizaje de HTML completa. Para importar la página de aterrizaje de HTML, primero debe comprimir su contenido en un paquete de diseño. El paquete de diseño contiene la página de aterrizaje del HTML junto con los recursos a los que se hace referencia (imágenes, css, iconos, scripts, etc.).

La siguiente hoja de referencia proporciona una muestra de cómo preparar al HTML para la importación:

Hoja de referencia de la página de aterrizaje

[Obtener archivo](assets/cheatsheet.zip)

### Diseño y requisitos del archivo zip {#zip-file-layout-and-requirements}

>[!NOTE]
>
>En este punto, los archivos ZIP solo pueden contener una página de HTML o una parte de una página.

A continuación se muestra un diseño de muestra del zip:

* /index.html -> archivo del HTML de la página de aterrizaje
* /css -> para añadir a la clientlib CSS
* /img -> todas las imágenes y recursos
* /js -> para agregar a la clientlib JS

El diseño se basa en el diseño de prácticas recomendadas de HTML5 Boilerplate. Más información en [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>Como mínimo, el paquete de diseño **must** contiene un **index.html** en el nivel raíz. Si la página de aterrizaje que se va a importar también tiene una versión móvil, el zip debe contener un **mobile.index.html** junto con **index.html** en el nivel raíz.

### Preparación del HTML de página de aterrizaje {#preparing-the-landing-page-html}

Para poder importar el HTML, debe añadir un div lienzo al HTML de página de aterrizaje.

El div lienzo es un html **div** con `id="cqcanvas"` que debe insertarse dentro del HTML `<body>` y debe ajustar el contenido que se va a convertir.

A continuación se muestra un fragmento de ejemplo del HTML de página de aterrizaje tras la adición del div lienzo:

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### Preparación del HTML para incluir componentes de AEM editables {#preparing-the-html-to-include-editable-aem-components}

Al importar una página de aterrizaje, tiene la opción de importar la página tal cual, lo que significa que, una vez importada la página de aterrizaje, no puede editar ninguno de los elementos importados en AEM (aún puede añadir componentes de AEM adicionales a la página).

Antes de importar la página de aterrizaje, es posible que desee convertir algunas de las partes de la página de aterrizaje para que sean componentes AEM editables. Esto le permite editar rápidamente partes de la página de aterrizaje incluso después de importar el diseño de la página de aterrizaje.

Para ello, agregue la variable `data-cq-component` al componente apropiado del archivo de HTML que importe.

En la siguiente sección se describe cómo editar el archivo HTML para que pueda convertir ciertas partes de las páginas de aterrizaje en diferentes componentes AEM editables. Los componentes se describen detalladamente en [Componentes de las páginas de aterrizaje](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>El marcado del HTML para convertir partes de la página de aterrizaje en componentes de AEM tiene un formulario largo y una declaración de etiqueta abreviada. Ambas se describen para cada componente.

### Restricciones {#limitations}

Antes de importar, tenga en cuenta las siguientes limitaciones:

### No se conserva ningún atributo como class o id aplicado en la etiqueta &amp;lt;body> {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Si se aplica un atributo como id o class a la etiqueta de cuerpo, por ejemplo `<body id="container">` a continuación, no se conserva después de la importación. Por lo tanto, el diseño que se importe no debe tener dependencias en los atributos aplicados en la variable `<body>` etiqueta.

### Arrastrar y soltar zip {#drag-and-drop-zip}

La carga de archivos zip arrastrados/soltados no es compatible con Internet Explorer y Firefox versión 3.6 y anteriores. Para cargar un diseño con estos navegadores, haga clic en la zona de colocación de archivos para abrir un cuadro de diálogo de carga de archivos y cargar el diseño con ese cuadro de diálogo.

Los navegadores compatibles con &quot;arrastrar y soltar&quot; del zip de diseño son Chrome, Safari5.x, Firefox 4 y versiones posteriores.

### No se admite Modernizr {#modernizr-is-not-supported}

`Modernizr.js` es una herramienta basada en javascript que detecta las capacidades nativas de los navegadores y detecta si son o no adecuadas para elementos html5. Los diseños que utilizan Modernizador para mejorar la compatibilidad con versiones anteriores de distintos navegadores pueden causar problemas de importación en la solución de página de aterrizaje. `Modernizr.js` las secuencias de comandos no son compatibles con el importador de diseños.

### Las propiedades de página no se conservan al importar el paquete de diseño {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Cualquier propiedad de página (por ejemplo, dominio personalizado, aplicación de HTTPS, etc.) configurado para una página (que utiliza la plantilla Página de aterrizaje en blanco) antes de importar el paquete de diseño se pierden después de importar el diseño. Por lo tanto, la práctica recomendada es establecer las propiedades de la página después de importar el paquete de diseño.

### HTML solo se supone un marcado {#html-only-markup-assumed}

Tras la importación, el marcado se saniza por motivos de seguridad y para evitar la importación y publicación de marcas no válidas. Esto supone que el marcado solo de HTML y todas las demás formas de elementos, como el SVG en línea o los componentes web, se filtrarán hacia fuera.

### Texto {#text}

HTML para insertar un componente de texto ( `foundation/components/text`) en el HTML dentro del paquete de diseño:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Al incluir el marcado anterior en el HTML, se realiza lo siguiente:

* Crea un componente de texto AEM editable ( `sling:resourceType=foundation/components/text`) en la página de aterrizaje creada después de importar el paquete de diseño.
* Establece la variable `text` del componente de texto creado al HTML adjunto dentro de la `div`.

**Declaración abreviada de tag de componente**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Texto con una lista**

Para añadir texto con una lista:

* 1st
* 2nd

que se puede editar en el editor RTE:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Texto con color**

Para añadir un texto con color (rosa) que se pueda editar en el editor RTE:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Título {#title}

HTML para insertar un componente de título ( `wcm/landingpage/components/title`) en el HTML dentro del paquete de diseño:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Al incluir el marcado anterior en el HTML, se realiza lo siguiente:

* Crea un componente de título de AEM editable ( `sling:resourceType=wcm/landingpage/components/title`) en la página de aterrizaje creada después de importar el paquete de diseño.
* Establece la variable `jcr:title` propiedad del componente de título creado al texto dentro de la etiqueta de encabezado dentro de div.
* Establece la variable `type` a la etiqueta de encabezado, en este caso `h1`.

El componente de título admite 7 tipos: `h1, h2, h3, h4, h5, h6` y `default`.

**Declaración abreviada de tag de componente**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Imagen {#image}

marcado del HTML para insertar un componente de imagen (foundation/components/image) en el HTML dentro del paquete de diseño:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Al incluir el marcado anterior en el HTML, se realiza lo siguiente:

* Crea un componente de imagen AEM editable ( `sling:resourceType=foundation/components/image`) en la página de aterrizaje creada después de importar el paquete de diseño.
* Establece la variable `fileReference` propiedad del componente de imagen creado a la ruta a la que se importa la imagen especificada en el atributo src.
* Establece la variable `alt` propiedad al valor del atributo alt en la etiqueta img.
* Establece la variable `title` propiedad al valor del atributo title en la etiqueta img.
* Establece la variable `width` propiedad al valor del atributo width de la tag img.
* Establece la variable `height` propiedad al valor del atributo height de la tag img.

**Declaración abreviada de tag de componente:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### La URL absoluta img src no es compatible con el componente de imagen Div {#absolute-url-img-src-not-supported-within-image-component-div}

Si una `<img>` se intenta usar una etiqueta con una dirección url src absoluta para la conversión de componentes, una **UnsupportedTagContentException** se eleva. Por ejemplo, no se admite lo siguiente:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Sin embargo, en el caso de las etiquetas img que no forman parte del div componente imagen, se admiten imágenes de URL absoluta.

### Componentes de llamada a acción {#call-to-action-components}

Puede marcar parte de la página de aterrizaje para importarla como un &quot;componente de llamada a acción editable&quot;; estos componentes de llamada a acción importados se pueden editar después de importar la página de aterrizaje. AEM incluye los siguientes componentes de llamada a acción:

* Vínculo de pulsaciones : le permite agregar un vínculo de texto que, cuando se hace clic, lleva al visitante a una dirección URL de destino.
* Vínculo gráfico: permite agregar una imagen que, al hacer clic, lleve al visitante a una dirección URL de destino.

#### Vínculo de pulsaciones {#click-through-link}

Este componente de llamada a acción se puede utilizar para añadir un vínculo de texto en la página de aterrizaje.

Propiedades compatibles

* Etiqueta, con opciones de negrita, cursiva y subrayado
* URL de destino, admite URL de terceros y de AEM
* Opciones de procesamiento de página (misma ventana, nueva ventana, etc.)

etiqueta de HTML para incluir un componente de pulsaciones en el zip importado. Aquí href se asigna a la dirección URL de destino, &quot;Ver detalles del producto&quot; se asigna a la etiqueta, etc.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

Este componente puede utilizarse en cualquier aplicación independiente o importarse desde zip.

**Declaración abreviada de tag de componente**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Vínculo gráfico {#graphical-link}

Este componente de llamada a acción se puede utilizar para añadir cualquier imagen gráfica con vínculo en la página de aterrizaje. La imagen puede ser un botón simple o cualquier imagen gráfica como fondo. Cuando se hace clic en la imagen, se lleva al usuario a la dirección URL de destino especificada en las propiedades del componente. Forma parte del grupo &quot;Llamada a acción&quot;.

Propiedades compatibles

* Recorte de imagen, rotación
* Texto al pasar el ratón, descripción, tamaño en píxeles
* URL de destino, admite URL de terceros y de AEM
* Opciones de procesamiento de página (misma ventana, nueva ventana, etc.)

etiqueta de HTML para incluir un componente de vínculo gráfico en el zip importado. Aquí href se asignará a la dirección url de destino, img src será la imagen de renderización, &quot;title&quot; se tomará como texto al pasar el ratón, etc.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**Declaración abreviada de tag de componente**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>Para crear un vínculo gráfico de pulsaciones, debe envolver una etiqueta delimitadora y la etiqueta de imagen dentro de un div con `data-cq-component="clickthroughgraphicallink"` atributo.
>
>p. ej. `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>No se admiten otras formas de asociar una imagen con una etiqueta delimitadora mediante CSS; por ejemplo, el siguiente marcado no funcionará:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>con un `css .hasbackground { background-image: pathtoimage }`

### Formulario de posibles clientes {#lead-form}

Un formulario de posibles clientes es un formulario que se utiliza para recopilar información de perfil de un visitante o posible cliente. Esta información se puede almacenar y utilizar más adelante para realizar un marketing eficaz basado en la información. Esta información generalmente incluye título, nombre, correo electrónico, fecha de nacimiento, dirección, interés, etc. Forma parte del grupo &quot;Llamada a acción: formulario de posibles clientes&quot;.

**Funciones admitidas**

* Campos de posibles clientes predefinidos: en la barra de tareas hay disponibles los campos de nombre, apellido, dirección, dob, sexo, acerca de, userId, emailId y botón de envío. Basta con arrastrar y soltar el componente requerido en el formulario de posibles clientes.
* Con la ayuda de estos componentes, el autor puede diseñar un formulario de posibles clientes independiente, estos campos corresponden a los campos del formulario de posibles clientes. En una aplicación zip independiente o importada, el usuario puede agregar campos adicionales utilizando los campos de formulario de posibles clientes cq:form o cta, asignarles un nombre y diseñarlos según los requisitos.
* Asigne campos de formulario de posibles clientes utilizando nombres predefinidos específicos del formulario de posibles clientes de llamada a acción, por ejemplo: firstName para el nombre en el formulario de posibles clientes, etc.
* Los campos que no están asignados al formulario de posibles clientes se asignarán a componentes de cq:form: texto, radio, casilla de verificación, menú desplegable, oculto, contraseña.
* El usuario puede proporcionar el título mediante la etiqueta &quot;label&quot; y el estilo mediante el atributo de estilo &quot;class&quot; (solo disponible para los componentes del formulario de posibles clientes de llamada a acción).
* La página de agradecimiento y la lista de suscripción se pueden proporcionar como parámetros ocultos del formulario (presentes en index.htm) o se pueden añadir o editar desde la barra de edición de &quot;Inicio del formulario de posibles clientes&quot;

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Las restricciones como - obligatorio se pueden proporcionar desde la configuración de edición de cada componente.

etiqueta de HTML para incluir un componente de vínculo gráfico en el zip importado. Aquí &quot;firstName&quot; se asigna a firstName del formulario de posibles clientes, etc., excepto para las casillas de verificación: estas dos casillas de verificación se asignan al componente desplegable cq:form.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

El componente parsys de AEM es un componente contenedor que puede contener otros componentes de AEM. Es posible añadir un componente parsys en el HTML importado. Esto permite al usuario añadir o eliminar componentes de AEM editables a la página de aterrizaje incluso después de importarlos.

El sistema de párrafos permite a los usuarios agregar componentes mediante la barra de tareas.

HTML para insertar un componente parsys ( `foundation/components/parsys`) en el HTML dentro del paquete de diseño:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Al incluir el marcado anterior en el HTML, se hace lo siguiente:

* Inserta un componente parsys AEM (foundation/components/parsys) en la página de aterrizaje creada tras importar el paquete de diseño.
* Inicializa la barra de tareas con los componentes predeterminados. Se pueden añadir nuevos componentes a la página de aterrizaje arrastrando componentes de la barra de tareas al componente parsys.
* Dos componentes de título también forman parte de parsys.

### Destino {#target}

El componente de destino muestra el contenido de una experiencia en la página. Se pueden tener muchas experiencias creadas en una campaña y el componente de destino puede mostrar de forma dinámica contenido de distintas experiencias a varios usuarios que visiten la página.

El código HTML para insertar un componente de destino y también crear experiencias diferentes en una campaña:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## Opciones de importación adicionales {#additional-importing-options}

Además de especificar si los componentes importados son editables AEM los componentes, también puede configurar lo siguiente antes de importar el paquete de diseño:

* Configuración de las propiedades de página extrayendo los metadatos definidos en el HTML importado.
* Especificación de la codificación del conjunto de caracteres en el HTML.
* Superposición de la plantilla de página del importador.

### Configuración de las propiedades de página extrayendo metadatos definidos en el HTML importado {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

El importador de diseños debe extraer y conservar los metadatos siguientes declarados en el encabezado del HTML importado como propiedad &quot;jcr:description&quot;:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

El importador de diseños debe extraer y conservar el atributo Lang establecido en la etiqueta HTML como propiedad &quot;jcr:language&quot;

* &lt;html lang=&quot;en&quot;>

### Especificación de la codificación del conjunto de caracteres en el html {#specifying-the-charset-encoding-in-the-html}

El importador de diseños lee la codificación especificada en el HTML importado. La codificación se puede especificar de la siguiente manera:

`<meta charset="UTF-8">`

*O*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Si no se especifica ninguna codificación en el HTML importado, la codificación predeterminada establecida por el importador de diseños es UTF-8.

### Superposición de plantilla {#overlaying-template}

La plantilla Página de aterrizaje en blanco se puede superponer creando una nueva en: `/apps/<appName>/designimporter/templates/<templateName>`

Se explican los pasos para crear una plantilla nueva en AEM [here](/help/sites-developing/templates.md).

### Referencia a un componente desde la página de aterrizaje {#referring-a-component-from-landing-page}

Supongamos que tiene un componente al que desea hacer referencia en el HTML mediante el atributo data-cq-component de modo que el importador de diseños procese un componente incluido en este lugar. Por ejemplo, si desea hacer referencia al componente de tabla ( `resourceType = /libs/foundation/components/table`). Se debe añadir lo siguiente al HTML:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

La ruta en data-cq-component debe ser el resourceType del componente.

### Prácticas recomendadas {#best-practices}

No se recomienda el uso de selectores CSS similares a los siguientes con elementos marcados para la conversión de componentes durante la importación.

| E > F | elemento secundario F de un elemento E | [Combinador secundario](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | un elemento F precedido inmediatamente por un elemento E | [Combinador de elementos del mismo nivel adyacente](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | un elemento F precedido por un elemento E | [Combinador de elementos similares generales](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | un elemento E, raíz del documento | [Pseudoclases estructurales](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | un elemento E, el elemento secundario n de su elemento principal | [Pseudoclases estructurales](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | un elemento E, el elemento secundario n de su elemento principal, contando a partir del último | [Pseudoclases estructurales](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | un elemento E, el elemento similar n de su tipo | [Pseudoclases estructurales](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | un elemento E, el elemento similar n de su tipo, contando a partir del último | [Pseudoclases estructurales](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Esto se debe a que hay elementos HTML adicionales como &lt;div> se añaden al HTML generado después de la importación.

* No se recomienda utilizar scripts que se basen en una estructura similar a la anterior con elementos marcados para su conversión en componentes AEM.
* Uso de estilos en las etiquetas de marcado para la conversión de componentes como &lt;div data-cq-component=&quot;”&amp;ast;”&quot;> no se recomienda.
* El diseño del diseño debe seguir las prácticas recomendadas de HTML5 Boilerplate. Más información sobre: [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Configuración de módulos OSGI {#configuring-osgi-modules}

Los componentes que exponen propiedades configurables mediante la consola OSGI son los siguientes:

* Importador de diseños de páginas de aterrizaje
* Generador de páginas de aterrizaje
* Generador de páginas de aterrizaje móviles
* Preprocesador de entradas de páginas de aterrizaje

La siguiente tabla describe brevemente las propiedades:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Componente</strong></td> 
   <td><strong>Nombre de propiedad</strong></td> 
   <td><strong>Descripción de la propiedad </strong></td> 
  </tr> 
  <tr> 
   <td>Importador de diseños de páginas de aterrizaje</td> 
   <td>Extraer filtro</td> 
   <td>La lista de expresiones regulares que se utilizará para filtrar archivos de la extracción. <br /> Las entradas de código postal que coinciden con cualquiera de los patrones especificados se excluyen de la extracción</td> 
  </tr> 
  <tr> 
   <td>Generador de páginas de aterrizaje</td> 
   <td>Patrón de archivo</td> 
   <td>El Generador de páginas de aterrizaje se puede configurar para gestionar archivos HTML que coincidan con una expresión regular definida por el patrón de archivos.</td> 
  </tr> 
  <tr> 
   <td>Generador de páginas de aterrizaje móviles</td> 
   <td>Patrón de archivo</td> 
   <td>El Generador de páginas de aterrizaje se puede configurar para gestionar archivos HTML que coincidan con una expresión regular definida por el patrón de archivos.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Grupos de dispositivos</td> 
   <td>Lista de grupos de dispositivos que se van a admitir.</td> 
  </tr> 
  <tr> 
   <td>Preprocesador de entradas de páginas de aterrizaje</td> 
   <td>Patrón de búsqueda </td> 
   <td>Patrón que se va a buscar, en el contenido de las entradas del archivo. Esta expresión regular coincide con el contenido de entrada línea por línea. Al producirse la coincidencia, el texto coincidente se sustituye por el patrón de reemplazo especificado.<br /> <br /> Consulte la nota siguiente sobre las limitaciones actuales del preprocesador de entradas de páginas de aterrizaje.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Patrón de reemplazo</td> 
   <td>Patrón que reemplaza las coincidencias encontradas. Puede usar referencias de grupo regex como $1, $2. Además, este patrón admite palabras clave como {designPath} que se resuelven con el valor real durante la importación.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**Limitación actual del preprocesador de entradas de páginas de aterrizaje:**
>Si necesita realizar cambios en el patrón de búsqueda, al abrir el editor de propiedades felix, debe agregar manualmente caracteres de barra invertida para escapar de los metacaracteres regex. Si no agrega manualmente caracteres de barra invertida, la regex se considera no válida y no reemplaza a la anterior.
>
>Por ejemplo, si la configuración predeterminada es
>
>`/\&ast *CQ_DESIGN_PATH *\*/ *(['"])`
>
>Y necesita reemplazar `CQ_DESIGN_PATH` con `VIPURL` en el patrón de búsqueda, el patrón de búsqueda debería tener este aspecto:
>
>`/\* *VIPURL *\*/ *(['"])`

## Solución de problemas {#troubleshooting}

Al importar el paquete de diseño, puede encontrar varios errores que se describen en esta sección.

### Inicialización de la barra de tareas con los componentes relevantes de la página de aterrizaje {#initialization-of-sidekick-with-landing-page-relevant-components}

Si el paquete de diseño contiene un marcado de componente parsys, después de la importación, la barra de tareas comienza a mostrar los componentes relevantes de la página de aterrizaje. Puede arrastrar y soltar nuevos componentes en el componente parsys de la página de aterrizaje. También puede ir al modo de diseño y añadir nuevos componentes a la barra de tareas.

### Mensajes de error mostrados durante la importación {#error-messages-displayed-during-import}

En caso de errores (por ejemplo, el paquete importado no es un zip válido), la importación del diseño no importará el paquete y, en su lugar, mostrará un mensaje de error en la página, encima del cuadro de arrastrar y soltar. A continuación se indican ejemplos de situaciones de error. Después de corregir el error, puede volver a importar el zip actualizado en la misma página de aterrizaje en blanco. Los distintos escenarios en los que se generan errores son los siguientes:

* El paquete de diseño importado no es un archivo zip válido.
* El paquete de diseño importado no contiene un index.html en el nivel superior.

### Advertencias mostradas tras la importación {#warnings-displayed-after-import}

En caso de advertencias (por ejemplo, HTML hace referencia a imágenes que no existen en el paquete), el importador de diseños importará el zip, pero al mismo tiempo mostrará una lista de problemas/advertencias en el panel de resultados. Al hacer clic en el vínculo problemas , se mostrará una lista de advertencias que indicarán cualquier problema dentro del paquete de diseño. Los siguientes son los escenarios en los que el importador de diseños captura y muestra advertencias:

* HTML hace referencia a imágenes que no existen en el paquete.
* HTML hace referencia a secuencias de comandos que no existen en el paquete.
* HTML hace referencia a estilos que no existen en el paquete.

### ¿Dónde se almacenan los archivos del archivo ZIP en AEM? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Una vez importada la página de aterrizaje, los archivos (imágenes, css, js, etc.) dentro del paquete de diseño se almacenan en la siguiente ubicación de AEM:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Supongamos que la página de aterrizaje se crea en la campaña We.Retail y que el nombre de la página de aterrizaje es **myBlankLandingPage** la ubicación en la que se almacenan los archivos Zip es la siguiente:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Formato no conservado {#formatting-not-preserved}

Al crear su CSS, tenga en cuenta las siguientes limitaciones:

Si un texto e imagen (editable) son como los siguientes:

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

con una CSS aplicada a la clase `box` de la siguiente manera:

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

Entonces `box img` se utiliza en el importador de diseños, parece que la página de aterrizaje resultante no ha conservado el formato. Para solucionar esto, tenga en cuenta que AEM agrega etiquetas div en el CSS y reescriba el código en consecuencia. De lo contrario, algunas reglas CSS no serán válidas.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>Además, los diseñadores deben tener en cuenta que solo el código dentro de la variable **id=cqcanvas** el importador reconoce la etiqueta, de lo contrario el diseño no se conservará.
