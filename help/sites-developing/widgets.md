---
title: Uso y ampliación de utilidades (IU clásica)
seo-title: Using and Extending Widgets (Classic UI)
description: AEM interfaz basada en web utiliza AJAX y otras tecnologías modernas de navegador para permitir a los autores editar y formatear el contenido WYSIWYG directamente en la página web
seo-description: AEM's web-based interface uses AJAX and other modern browser technologies to enable WYSIWYG editing and formatting of content by authors right on the web page
uuid: e8dfa140-dab7-4e08-a790-d703adf86d6f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 508f4fab-dd87-4306-83ae-12e544b8b723
exl-id: c747bfda-e82a-4b2d-a4af-5792bfe82576
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '5187'
ht-degree: 0%

---

# Uso y ampliación de utilidades (IU clásica){#using-and-extending-widgets-classic-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La interfaz basada en la web de Adobe Experience Manager utiliza AJAX y otras tecnologías modernas de navegador para permitir a los autores editar y formatear el contenido WYSIWYG directamente en la página web.

Adobe Experience Manager (AEM) utiliza la variable [ExtJS](https://www.sencha.com/) biblioteca de widgets, que proporciona los elementos de interfaz de usuario altamente pulidos que funcionan en todos los exploradores más importantes y permiten la creación de experiencias de IU de escritorio.

Estos widgets se incluyen en AEM y, además de ser utilizados por AEM mismo, pueden ser utilizados por cualquier sitio web creado con AEM.

Para obtener una referencia completa de todos los widgets disponibles en AEM, consulte la [documentación de la API del widget](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) o a la [lista de xtype existentes](/help/sites-developing/xtypes.md). Además, hay muchos ejemplos que muestran cómo utilizar el marco de ExtJS disponibles en el [Sencha](https://www.sencha.com/products/extjs/examples/) sitio, el propietario de la infraestructura.

Esta página proporciona información sobre cómo utilizar y ampliar las utilidades. En primer lugar, se describe cómo [incluir código de cliente en una página](#including-the-client-sided-code-in-a-page). A continuación, se describen algunos componentes de muestra que se han creado para ilustrar el uso básico y la extensión. Estos componentes están disponibles en la **Uso de las utilidades de ExtJS** paquete en **Uso compartido de paquetes**.

El paquete incluye ejemplos de:

* [Diálogos básicos](#basic-dialogs) creado con utilidades integradas.
* [Diálogos dinámicos](#dynamic-dialogs) se ha creado con utilidades integradas y lógica personalizada de javascript.
* Cuadros de diálogo basados en [widgets personalizados](#custom-widgets).
* A [panel de árbol](#tree-overview) mostrar un árbol JCR debajo de una ruta determinada.
* A [panel cuadrícula](#grid-overview) visualización de datos en formato de tabla.

>[!NOTE]
>
>La IU clásica de Adobe Experience Manager se basa en [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/).

>[!NOTE]
>
>Esta página describe el uso de las utilidades dentro de la IU clásica. El Adobe recomienda aprovechar el [IU táctil](/help/sites-developing/touch-ui-concepts.md) basado en [Interfaz de usuario de Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) y [Interfaz de usuario de Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## Inclusión del código de cliente en una página {#including-the-client-sided-code-in-a-page}

El código javascript del lado del cliente y el código de hoja de estilo deben colocarse en una biblioteca de cliente.

Para crear una biblioteca de cliente:

1. Cree un nodo a continuación `/apps/<project>` con las siguientes propiedades:

   ```
       name="clientlib"
       jcr:mixinTypes="[mix:lockable]"
       jcr:primaryType="cq:ClientLibraryFolder" 
       sling:resourceType="widgets/clientlib" 
       categories="[<category-name>]" 
       dependencies="[cq.widgets]"
   ```

   >[!NOTE]
   >
   >Nota: `<category-name>` es el nombre de la biblioteca personalizada (p. ej. &quot;cq.extjstraining&quot;) y se usa para incluir la biblioteca en la página.

1. Abajo `clientlib` cree el `css` y `js` carpetas (nt:folder).

1. Abajo `clientlib` cree el `css.txt` y `js.txt` archivos (nt:files). Estos archivos .txt enumeran los archivos que se incluyen en la biblioteca.

1. Editar `js.txt`: debe comenzar con &#39; `#base=js`&#39; seguido de la lista de los archivos que agregará el servicio de biblioteca del cliente de CQ, por ejemplo:

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Editar `css.txt`: debe comenzar con &#39; `#base=css`&#39; seguido de la lista de los archivos que agregará el servicio de biblioteca del cliente de CQ, por ejemplo:

   ```
   #base=css
    components.css
   ```

1. Debajo de `js` , coloque los archivos javascript que pertenecen a la biblioteca .

1. Debajo de `css` carpeta, coloque la variable `.css` y los recursos utilizados por los archivos css (p. ej. `my_icon.png`).

>[!NOTE]
>
>El manejo de las hojas de estilo descritas anteriormente es opcional.

Para incluir la biblioteca del cliente en el componente de página jsp:

* para incluir tanto el código de javascript como las hojas de estilo:

   `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`

   donde `<category-nameX>` es el nombre de la biblioteca del lado del cliente.

* para incluir solo código javascript:

   `<ui:includeClientLib js="<category-name>"/>`

Para obtener más información, consulte la descripción del [&lt;ui:includeclientlib>](/help/sites-developing/taglib.md#amp-lt-ui-includeclientlib) etiqueta.

En algunos casos, una biblioteca de cliente solo debería estar disponible en modo de autor y excluirse en modo de publicación. Puede lograrse de la siguiente manera:

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Introducción a los ejemplos {#getting-started-with-the-samples}

Para seguir los tutoriales de esta página, instale el paquete llamado **Uso de las utilidades de ExtJS** en una instancia de AEM local y cree una página de muestra en la que se incluirán los componentes. Para ello:

1. En la instancia de AEM, descargue el paquete llamado **Uso de utilidades de ExtJS (v01)** desde Package Share e instale el paquete. Crea el proyecto `extjstraining` below `/apps` en el repositorio.

1. Incluya la biblioteca de cliente que contiene las secuencias de comandos (js) y la hoja de estilo (css) en la etiqueta head de la página jsp de geometrixx, ya que incluirá los componentes de muestra en una nueva página de la **Geometrixx** rama:

   en **CRXDE Lite** abra el archivo `/apps/geometrixx/components/page/headlibs.jsp` y añada `cq.extjstraining` a la `<ui:includeClientLib>` de la siguiente manera:

   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`

1. Cree una nueva página en la **Geometrixx** rama inferior `/content/geometrixx/en/products` y llamémoslo **Uso de las utilidades de ExtJS**.

1. Vaya al modo de diseño y añada todos los componentes del grupo llamado **Uso de las utilidades de ExtJS** al diseño de la Geometrixx
1. Vuelva al modo de edición: los componentes del grupo **Uso de las utilidades de ExtJS** están disponibles en la barra de tareas.

>[!NOTE]
>
>Los ejemplos de esta página se basan en el contenido de muestra de Geometrixx, que ya no se envía con AEM, y que ha sido reemplazado por We.Retail. Consulte el documento [Implementación de referencia de We.Retail](/help/sites-developing/we-retail.md#we-retail-geometrixx) para obtener información sobre cómo descargar e instalar Geometrixx.

### Cuadros de diálogo básicos {#basic-dialogs}

Los cuadros de diálogo suelen utilizarse para editar contenido, pero también pueden mostrar información. Una manera fácil de ver un cuadro de diálogo completo es acceder a su representación en formato json. Para ello, dirija el navegador a:

`http://localhost:4502/<path-to-dialog>.-1.json`

El primer componente de la variable **Uso de las utilidades de ExtJS** en la barra de tareas se llama **1. Conceptos básicos del cuadro de diálogo** e incluye cuatro cuadros de diálogo básicos creados con utilidades integradas y sin lógica personalizada de javascript. Los cuadros de diálogo se almacenan a continuación `/apps/extjstraining/components/dialogbasics`. Los diálogos básicos son:

* el cuadro de diálogo Completo ( `full` nodo): muestra una ventana con 3 pestañas, cada una con 2 campos de texto.

* el cuadro de diálogo Panel único( `singlepanel` nodo): muestra una ventana con una ficha que tiene 2 campos de texto.
* el cuadro de diálogo Panel múltiple( `multipanel` nodo): su visualización es la misma que el cuadro de diálogo Completo pero está diseñada de forma diferente.
* Cuadro de diálogo Diseño( `design` nodo): muestra una ventana con 2 pestañas. La primera ficha tiene un campo de texto, un menú desplegable y un área de texto contraíble. La segunda ficha tiene un conjunto de campos con 4 campos de texto y un conjunto de campos contraíble con 2 campos de texto.

Incluya la variable **1. Conceptos básicos del cuadro de diálogo** en la página de muestra:

1. Agregue la variable **1. Conceptos básicos del cuadro de diálogo** a la página de muestra desde el **Uso de las utilidades de ExtJS** en la ficha **Barra de tareas**.

1. El componente muestra un título, texto y un **PROPIEDADES** vínculo: haga clic en el vínculo para mostrar las propiedades del párrafo almacenado en el repositorio. Haga clic de nuevo en el vínculo para ocultar las propiedades.

El componente se muestra de la siguiente manera:

![chlimage_1-135](assets/chlimage_1-135.png)

#### Ejemplo 1: Diálogo completo {#example-full-dialog}

La variable **Completa** muestra una ventana con tres pestañas, cada una con dos campos de texto. Es el cuadro de diálogo predeterminado de la variable **Conceptos básicos del cuadro de diálogo** componente. Sus características son:

* Está definido por un nodo: tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog).

* Muestra 3 pestañas (tipo de nodo = `cq:Panel`).
* Cada ficha tiene 2 campos de texto (tipo de nodo = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Se define mediante el nodo :

   `/apps/extjstraining/components/dialogbasics/full`

* Se procesa en formato JSON solicitando:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

El cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Ejemplo 2: Cuadro de diálogo de panel único {#example-single-panel-dialog}

La variable **Panel único** muestra una ventana con una ficha que tiene dos campos de texto. Sus características son:

* Muestra 1 ficha (tipo de nodo = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel))

* La pestaña tiene 2 campos de texto (tipo de nodo = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield))

* Se define mediante el nodo :

   `/apps/extjstraining/components/dialogbasics/singlepanel`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`

* Una ventaja sobre **Diálogo completo** es que se necesita menos configuración.
* Uso recomendado: para cuadros de diálogo simples que muestran información o que solo tienen unos pocos campos.

Para utilizar el cuadro de diálogo Panel único:

1. Reemplace el cuadro de diálogo del **Conceptos básicos del cuadro de diálogo** con el **Panel único** diálogo:

   1. En **CRXDE Lite**, elimine el nodo : `/apps/extjstraining/components/dialogbasics/dialog`
   1. Haga clic en **Guardar todo** para guardar los cambios.
   1. Copie el nodo : `/apps/extjstraining/components/dialogbasics/singlepanel`
   1. Pegue el nodo copiado a continuación: `/apps/extjstraining/components/dialogbasics`
   1. Seleccione el nodo : `/apps/extjstraining/components/dialogbasics/Copy of singlepanel`y renómbrelo `dialog`.

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Ejemplo 3: Diálogo de varios paneles {#example-multi-panel-dialog}

La variable **Varios paneles** tiene la misma visualización que la **Completa** pero se crea de forma diferente. Sus características son:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)).

* Muestra 3 pestañas (tipo de nodo = `cq:Panel`).
* Cada ficha tiene 2 campos de texto (tipo de nodo = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Se define mediante el nodo :

   `/apps/extjstraining/components/dialogbasics/multipanel`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`

* Una ventaja sobre **Diálogo completo** es que tiene una estructura simplificada.

* Uso recomendado: para los cuadros de diálogo multipestaña.

Para utilizar el cuadro de diálogo Panel múltiple:

1. Reemplace el cuadro de diálogo del **Conceptos básicos del cuadro de diálogo** con el **Varios paneles** diálogo:

   siga los pasos descritos para la variable [Ejemplo 2: Cuadro de diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Ejemplo 4: Diálogo enriquecido {#example-rich-dialog}

La variable **Enriquecido** muestra una ventana con dos pestañas. La primera ficha tiene un campo de texto, un menú desplegable y un área de texto contraíble. La segunda ficha tiene un conjunto de campos con cuatro campos de texto y un conjunto de campos contraíble con dos campos de texto. Sus características son:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 2 pestañas (tipo de nodo = `cq:Panel`).
* La primera pestaña tiene un [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) widget con un [`textfield`](/help/sites-developing/xtypes.md#textfield) y [`selection`](/help/sites-developing/xtypes.md#selection) widget con 3 opciones y un contraíble [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) con un [`textarea`](/help/sites-developing/xtypes.md#textarea) para abrir el Navegador.

* La segunda pestaña tiene un [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset) widget con 4 [`textfield`](/help/sites-developing/xtypes.md#textfield) widgets y un contraíble `dialogfieldset` con 2 [`textfield`](/help/sites-developing/xtypes.md#textfield) widgets.

* Se define mediante el nodo :

   `/apps/extjstraining/components/dialogbasics/rich`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

Para usar la variable **Enriquecido** diálogo:

1. Reemplace el cuadro de diálogo del **Conceptos básicos del cuadro de diálogo** con el **Enriquecido** diálogo:

   siga los pasos descritos para la variable [Ejemplo 2: Cuadro de diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Cuadros de diálogo dinámicos {#dynamic-dialogs}

El segundo componente de la variable **Uso de las utilidades de ExtJS** en la barra de tareas se llama **2. Cuadros de diálogo dinámicos** e incluye tres cuadros de diálogo dinámicos que se crean con utilidades integradas y **con lógica personalizada de javascript**. Los cuadros de diálogo se almacenan a continuación `/apps/extjstraining/components/dynamicdialogs`. Los cuadros de diálogo dinámicos son:

* el cuadro de diálogo Cambiar fichas ( `switchtabs` nodo): muestra una ventana con dos pestañas. La primera pestaña tiene una selección de radio con tres opciones: cuando se selecciona una opción, se muestra una pestaña relacionada con la opción. La segunda ficha tiene dos campos de texto.
* el cuadro de diálogo Arbitrario ( `arbitrary` nodo): muestra una ventana con una pestaña. La pestaña tiene un campo para soltar o cargar un recurso y un campo que muestra información sobre la página contenedora y sobre el recurso si se hace referencia a uno.
* el cuadro de diálogo Alternar campos ( `togglefield` nodo): muestra una ventana con una pestaña. La pestaña tiene una casilla de verificación: cuando se marca, se muestra un conjunto de campos con dos campos de texto.

Para incluir el **2. Cuadros de diálogo dinámicos** en la página de muestra:

1. Agregue la variable **2. Cuadros de diálogo dinámicos** a la página de muestra desde el **Uso de las utilidades de ExtJS** en la ficha **Barra de tareas**.

1. El componente muestra un título, texto y un **PROPIEDADES** vínculo: haga clic en para mostrar las propiedades del párrafo almacenado en el repositorio. Haga clic de nuevo para ocultar las propiedades.

El componente se muestra de la siguiente manera:

![chlimage_1-136](assets/chlimage_1-136.png)

#### Ejemplo 1: Cuadro de diálogo Cambiar fichas {#example-switch-tabs-dialog}

La variable **Cambiar fichas** muestra una ventana con dos pestañas. La primera pestaña tiene una selección de radio con tres opciones: cuando se selecciona una opción, se muestra una pestaña relacionada con la opción. La segunda ficha tiene dos campos de texto.

Sus principales características son:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 2 pestañas (tipo de nodo = `cq:Panel`): 1 pestaña de selección, la segunda pestaña depende de la selección de la primera pestaña (3 opciones).
* Tiene 3 pestañas opcionales (tipo de nodo = `cq:Panel`), cada uno tiene 2 campos de texto (tipo de nodo = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)). Solo se muestra una pestaña opcional a la vez.

* Se define mediante la variable `switchtabs` en:

   `/apps/extjstraining/components/dynamicdialogs/switchtabs`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

La lógica se implementa mediante detectores de eventos y código javascript de la siguiente manera:

* El nodo de diálogo tiene un &quot; `beforeshow`&quot; oyente que oculta todas las pestañas opcionales antes de que se muestre el cuadro de diálogo:

   `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`

   `dialog.items.get(0)` obtiene el panel de tabla que contiene el panel de selección y los 3 paneles opcionales.

* La variable `Ejst.x2` se define en la variable `exercises.js` en:

   `/apps/extjstraining/clientlib/js/exercises.js`

* En el `Ejst.x2.manageTabs()` como el valor de `index` es -1, todas las pestañas opcionales están ocultas (i va del 1 al 3).

* La pestaña de selección tiene 2 oyentes: uno que muestra la ficha seleccionada cuando se carga el cuadro de diálogo (&quot; `loadcontent`&quot;) y una que muestre la ficha seleccionada cuando se cambia la selección (&quot; `selectionchanged`&quot;):

   `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`

* En el `Ejst.x2.showTab()` método:

   `field.findParentByType('tabpanel')` obtiene el panel de tabla que contiene todas las pestañas ( `field` representa el widget de selección)

   `field.getValue()` obtiene el valor de la selección, por ejemplo: tab2

   `Ejst.x2.manageTabs()` muestra la ficha seleccionada.

* Cada ficha opcional tiene un oyente que oculta la pestaña en &quot; `render`&quot; evento:

   `render="function(tab){Ejst.x2.hideTab(tab);}"`

* En el `Ejst.x2.hideTab()` método:

   `tabPanel` es el panel de tabla que contiene todas las pestañas

   `index` es el índice de la pestaña opcional

   `tabPanel.hideTabStripItem(index)` oculta la pestaña

Se muestra de la siguiente manera:

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Ejemplo 2: Diálogo arbitrario {#example-arbitrary-dialog}

Muy a menudo, un cuadro de diálogo muestra contenido del componente subyacente. El diálogo descrito aquí, llamado **Arbitrario** , extrae contenido de un componente diferente.

La variable **Arbitrario** muestra una ventana con una ficha. La pestaña tiene dos campos: una para soltar o cargar un recurso y otra que muestre información sobre la página contenedora y sobre el recurso si se ha hecho referencia a uno.

Sus principales características son:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 1 widget de panel de tabla (tipo de nodo = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) con 1 panel (tipo de nodo = `cq:Panel`)

* El panel tiene un widget de archivos inteligentes (tipo de nodo = `cq:Widget`, xtype = [`smartfile`](/help/sites-developing/xtypes.md#smartfile)) y un widget de dibujo del propietario (tipo de nodo = `cq:Widget`, xtype = [`ownerdraw`](/help/sites-developing/xtypes.md#ownerdraw))

* Se define mediante la variable `arbitrary` en:

   `/apps/extjstraining/components/dynamicdialogs/arbitrary`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

La lógica se implementa mediante detectores de eventos y código javascript de la siguiente manera:

* El widget de dibujo de propietario tiene un &quot; `loadcontent`&quot; oyente que muestra información sobre la página que contiene el componente y el recurso al que hace referencia el widget de archivos inteligentes cuando se carga el contenido:

   `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`

   `field` se define con el objeto ownerdraw

   `path` se configura con la ruta de contenido del componente (p. ej.: /content/geometrixx/en/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs)

* La variable `Ejst.x2` se define en la variable `exercises.js` en:

   `/apps/extjstraining/clientlib/js/exercises.js`

* En el `Ejst.x2.showInfo()` método:

   `pagePath` es la ruta de la página que contiene el componente

   `pageInfo` representa las propiedades de página en formato json

   `reference` es la ruta del recurso al que se hace referencia

   `metadata` representa los metadatos del recurso en formato json

   `ownerdraw.getEl().update(html);` muestra el html creado en el cuadro de diálogo

Para usar la variable **Arbitrario** diálogo:

1. Reemplace el cuadro de diálogo del **Diálogo dinámico** con el **Arbitrario** diálogo:

   siga los pasos descritos para la variable [Ejemplo 2: Cuadro de diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-02-01at115300am](assets/screen_shot_2012-02-01at115300am.png)

#### Ejemplo 3: Cuadro de diálogo Alternar campos {#example-toggle-fields-dialog}

La variable **Alternar campos** muestra una ventana con una ficha. La pestaña tiene una casilla de verificación: cuando se marca, se muestra un conjunto de campos con dos campos de texto.

Sus principales características son:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 1 widget de panel de tabla (tipo de nodo = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#textpanel)) con 1 panel (tipo de nodo = `cq:Panel`).

* El panel tiene un widget de selección/casilla de verificación (tipo de nodo = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection), tipo = [`checkbox`](/help/sites-developing/xtypes.md#checkbox)) y un widget de conjunto de cuadros de diálogo contraíble (tipo de nodo = `cq:Widget`, xtype = [`dialogfieldset`](/help/sites-developing/xtypes.md#dialogfieldset)) que está oculto de forma predeterminada, con 2 utilidades de campo de texto (tipo de nodo = `cq:Widget`, xtype = [`textfield`](/help/sites-developing/xtypes.md#textfield)).

* Se define mediante la variable `togglefields` en:

   `/apps/extjstraining/components/dynamicdialogs/togglefields`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

La lógica se implementa mediante detectores de eventos y código javascript de la siguiente manera:

* la pestaña selección tiene 2 oyentes: uno que muestra el conjunto de campos de diálogo cuando se carga el contenido (&quot; `loadcontent`&quot;) y una que muestre el conjunto de campos de diálogo cuando se cambia la selección (&quot; `selectionchanged`&quot;):

   `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`

   `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`

* La variable `Ejst.x2` se define en la variable `exercises.js` en:

   `/apps/extjstraining/clientlib/js/exercises.js`

* En el `Ejst.x2.toggleFieldSet()` método:

   * `box` es el objeto de selección
   * `panel` es el panel que contiene la selección y los widgets dialogfieldset
   * `fieldSet` es el objeto dialogfieldset
   * `show` es el valor de la selección (verdadero o falso)
   * basado en &#39; `show`&#39; el cuadro de diálogo se muestra o no

Para usar la variable **Alternar campos** diálogo:

1. Reemplace el cuadro de diálogo del **Diálogo dinámico** con el **Alternar campos** diálogo:

   siga los pasos descritos para la variable [Ejemplo 2: Cuadro de diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Widgets personalizados {#custom-widgets}

Los widgets listos para usar que se incluyen con AEM deben cubrir la mayoría de los casos de uso. Sin embargo, a veces puede ser necesario crear un widget personalizado para cubrir un requisito específico del proyecto. Los widgets personalizados se pueden crear ampliando los existentes. Para ayudarle a empezar con esta personalización, la variable **Uso de las utilidades de ExtJS** incluye tres cuadros de diálogo que utilizan tres widgets personalizados diferentes:

* el cuadro de diálogo Campos múltiples ( `multifield` ) muestra una ventana con una pestaña. La pestaña tiene un widget de varios campos personalizado que tiene dos campos: un menú desplegable con dos opciones y un campo de texto. Ya que se basa en la configuración predeterminada `multifield` (que solo tiene un campo de texto), tiene todas las características de la `multifield` para abrir el Navegador.

* el cuadro de diálogo Examinar árbol ( `treebrowse` ) muestra una ventana con una ficha que contiene un widget de exploración de rutas: al hacer clic en la flecha, se abre una ventana en la que puede examinar una jerarquía y seleccionar un elemento. A continuación, la ruta del elemento se agrega al campo de ruta y se mantiene cuando se cierra el cuadro de diálogo.
* un cuadro de diálogo basado en el complemento Editor de texto enriquecido (nodo `rteplugin`) que agrega un botón personalizado al Editor de texto enriquecido para insertar texto personalizado en el texto principal. Consiste en un `richtext` de una función personalizada que se añade a través del mecanismo de complementos RTE.

Los widgets personalizados y el complemento se incluyen en el componente llamado **3. Widgets personalizados** del **Uso de las utilidades de ExtJS** paquete. Para incluir este componente en la página de muestra:

1. Agregue la variable **3. Widgets personalizados** a la página de muestra desde el **Uso de las utilidades de ExtJS** en la ficha **Barra de tareas**.

1. El componente muestra un título, texto y, al hacer clic en el botón **PROPIEDADES** , las propiedades del párrafo almacenadas en el repositorio. Al hacer clic de nuevo, se ocultan las propiedades.

   El componente se muestra de la siguiente manera:

![chlimage_1-137](assets/chlimage_1-137.png)

#### Ejemplo 1: Widget de varios campos personalizado {#example-custom-multifield-widget}

La variable **Multicampo personalizado** el cuadro de diálogo basado en widgets muestra una ventana con una ficha. La pestaña tiene un widget multicampo personalizado que, a diferencia del estándar que tiene un campo, tiene dos campos: un menú desplegable con dos opciones y un campo de texto.

La variable **Multicampo personalizado** cuadro de diálogo basado en widgets:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 1 widget de panel de tabla (tipo de nodo = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) que contiene un panel (tipo de nodo = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* El panel tiene un `multifield` widget (tipo de nodo = `cq:Widget`, xtype = [`multifield`](/help/sites-developing/xtypes.md#multifield)).

* La variable `multifield` El widget tiene un campo dconfig (tipo de nodo = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`) que se basa en el xtype personalizado &#39; `ejstcustom`&#39;:

   * &#39; `fieldconfig`&#39; es una opción de configuración de la variable [`CQ.form.MultiField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField) objeto.
   * &#39; `optionsProvider`&#39; es una configuración de la variable `ejstcustom` para abrir el Navegador. Se configura con la variable `Ejst.x3.provideOptions` método definido en `exercises.js` en:

      `/apps/extjstraining/clientlib/js/exercises.js`

      y devuelve 2 opciones.

* Se define mediante la variable `multifield` en:

   `/apps/extjstraining/components/customwidgets/multifield`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

El widget multicampo personalizado (xtype = `ejstcustom`):

* Es un objeto de javascript llamado `Ejst.CustomWidget`.

* Se define en la variable `CustomWidget.js` archivo javascript en:

   `/apps/extjstraining/clientlib/js/CustomWidget.js`

* Amplía el [`CQ.form.CompositeField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField) para abrir el Navegador.

* Tiene 3 campos: `hiddenField` (Campo de texto), `allowField` (ComboBox) y `otherField` (Campo de texto)

* Anulaciones `CQ.Ext.Component#initComponent` para añadir los 3 campos:

   * `allowField` es [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection) objeto de tipo &quot;select&quot;. optionsProvider es una configuración del objeto Selection a la que se crea una instancia con la configuración optionsProvider del widget personalizado definido en el cuadro de diálogo
   * `otherField` es [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) object

* Anula los métodos `setValue`, `getValue` y `getRawValue` de [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField) para establecer y recuperar el valor de CustomWidget con el formato :

   `<allowField value>/<otherField value>, e.g.: 'Bla1/hello'`.

* Se registra como &#39; `ejstcustom`&#39; xtype:

   `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

La variable **Multicampo personalizado** el cuadro de diálogo basado en widgets se muestra de la siguiente manera:

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Ejemplo 2: Widget de rectángulos personalizado {#example-custom-treebrowse-widget}

El **Treebrowse** el cuadro de diálogo basado en widgets muestra una ventana con una ficha que contiene un widget de exploración de rutas personalizado: al hacer clic en la flecha, se abre una ventana en la que puede examinar una jerarquía y seleccionar un elemento. A continuación, la ruta del elemento se agrega al campo de ruta y se mantiene cuando se cierra el cuadro de diálogo.

El cuadro de diálogo de árbol personalizado:

* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`dialog`](/help/sites-developing/xtypes.md#dialog)).

* Muestra 1 widget de panel de tabla (tipo de nodo = `cq:Widget`, xtype = [`tabpanel`](/help/sites-developing/xtypes.md#tabpanel)) que contiene un panel (tipo de nodo = `cq:Widget`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* El panel tiene un widget personalizado (tipo de nodo = `cq:Widget`, xtype = `ejstbrowse`)

* Se define mediante la variable `treebrowse` en:

   `/apps/extjstraining/components/customwidgets/treebrowse`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

El widget de árbol personalizado (xtype = `ejstbrowse`):

* Es un objeto de javascript llamado `Ejst.CustomWidget`.
* Se define en la variable `CustomBrowseField.js` archivo javascript en:

   `/apps/extjstraining/clientlib/js/CustomBrowseField.js`

* Extensiones [`CQ.Ext.form.TriggerField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField).
* Define una ventana de navegación llamada `browseWindow`.

* Anulaciones [`CQ.Ext.form.TriggerField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField#onTriggerClick) para mostrar la ventana de navegación cuando se hace clic en la flecha.
* Define un [`CQ.Ext.tree.TreePanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) objeto:

   * Obtiene sus datos llamando al servlet registrado en `/bin/wcm/siteadmin/tree.json`.
   * Su raíz es &quot; `apps/extjstraining`&quot;.

* Define un `window` objeto ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)):

   * Basado en el panel predefinido.
   * Tiene un **OK** que define el valor de la ruta seleccionada y oculta el panel.

* La ventana está anclada debajo del **Ruta** campo .
* La ruta seleccionada se pasa del campo Examinar a la ventana de `show` evento.

* Se registra como &#39; `ejstbrowse`&#39; xtype:

   `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

Para usar la variable **Pantallas de árbol personalizadas** cuadro de diálogo basado en widgets:

1. Reemplace el cuadro de diálogo del **Widgets personalizados** con el **Pantallas de árbol personalizadas** diálogo:

   siga los pasos descritos para el [Ejemplo 2: Diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente: el cuadro de diálogo se muestra de la siguiente manera:

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Ejemplo 3: Complemento Editor de texto enriquecido (RTE) {#example-rich-text-editor-rte-plug-in}

La variable **Complemento Editor de texto enriquecido (RTE)** el cuadro de diálogo basado en editor de texto enriquecido es un cuadro de diálogo basado en editor de texto enriquecido que tiene un botón personalizado para insertar texto personalizado entre corchetes. El texto personalizado se puede analizar mediante alguna lógica del lado del servidor (no implementada en este ejemplo), por ejemplo para agregar texto definido en la ruta dada:

La variable **Complemento RTE** diálogo basado en:

* Se define mediante el nodo replugin en:

   `/apps/extjstraining/components/customwidgets/rteplugin`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`

* La variable `rtePlugins` el nodo tiene un nodo secundario `inserttext` (tipo de nodo = `nt:unstructured`) que recibe el nombre del complemento. Tiene una propiedad denominada `features`, que define qué características del complemento están disponibles para RTE.

El complemento RTE:

* Es un objeto de javascript llamado `Ejst.InsertTextPlugin`.

* Se define en la variable `InsertTextPlugin.js` archivo javascript en:

   `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`

* Amplía el [`CQ.form.rte.plugins.Plugin`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin) objeto.
* Los siguientes métodos definen la variable [`CQ.form.rte.plugins.Plugin`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin) y se anulan en el complemento de implementación:

   * `getFeatures()` devuelve una matriz de todas las funciones que pone a disposición el complemento.
   * `initializeUI()` agrega el nuevo botón a la barra de herramientas de RTE.
   * `notifyPluginConfig()` muestra título y texto cuando se sitúa el botón sobre él.
   * `execute()` cuando se hace clic en el botón y realiza la acción del complemento: muestra una ventana que se utiliza para definir el texto que se va a incluir.

* `insertText()` inserta un texto utilizando el objeto de diálogo correspondiente `Ejst.InsertTextPlugin.Dialog` (ver más adelante).

* `executeInsertText()` es invocado por el `apply()` método del cuadro de diálogo, que se activa cuando se activa la variable **OK** se hace clic en el botón .

* Se registra como &#39; `inserttext`&#39; plugin:

   `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`

* el `Ejst.InsertTextPlugin.Dialog` define el cuadro de diálogo que se abre cuando se hace clic en el botón del complemento. El cuadro de diálogo consta de un panel, un formulario, un campo de texto y 2 botones (**OK** y **Cancelar**).

Para usar la variable **Complemento Editor de texto enriquecido (RTE)** diálogo basado en:

1. Reemplace el cuadro de diálogo del **Widgets personalizados** con el **Complemento Editor de texto enriquecido (RTE)** diálogo basado en:

   siga los pasos descritos para la variable [Ejemplo 2: Cuadro de diálogo de panel único](#example-single-panel-dialog)

1. Edite el componente.
1. Haga clic en el último icono de la derecha (el que tiene cuatro flechas). Introduzca una ruta y haga clic en **OK**:

   La ruta se muestra entre corchetes (`[]`).

1. Haga clic en **OK** para cerrar el Editor de texto enriquecido.

La variable **Complemento Editor de texto enriquecido (RTE)** el cuadro de diálogo basado se muestra de la siguiente manera:

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>Este ejemplo solo muestra cómo implementar la parte del lado del cliente de la lógica: los marcadores de posición (*[text]*) deben analizarse explícitamente en el lado del servidor (por ejemplo, en el componente JSP).

### Información general de árbol {#tree-overview}

La solución predeterminada [`CQ.Ext.tree.TreePanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel) proporciona representación de IU estructurada en árbol de datos estructurados en árbol. El componente Información general de árbol incluido en la variable **Uso de las utilidades de ExtJS** muestra cómo usar el `TreePanel` para mostrar un árbol JCR debajo de una ruta determinada. La ventana en sí puede acoplarse o desacoplarse. En este ejemplo, la lógica de ventana está incrustada en el jsp del componente entre &lt;script>&lt;/script> etiquetas.

Para incluir el **Información general de árbol** a la página de muestra:

1. Agregue la variable **4. Información general de árbol** a la página de muestra desde el **Uso de las utilidades de ExtJS** en la ficha **Barra de tareas**.

1. El componente muestra:

   * un título, con texto
   * un vínculo **PROPERTIES**: haga clic en para mostrar las propiedades del párrafo almacenado en el repositorio. Haga clic de nuevo para ocultar las propiedades.
   * una ventana flotante con una representación de árbol del repositorio, que se puede expandir.

El componente se muestra de la siguiente manera:

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

El componente Información general de árbol:

* Se define en:

   `/apps/extjstraining/components/treeoverview`

* Su cuadro de diálogo permite establecer el tamaño de la ventana y acoplar/desacoplar la ventana (ver detalles a continuación).

El componente jsp:

* Recupera las propiedades de ancho, alto y acoplado del repositorio.
* Muestra texto sobre el formato de datos de descripción general del árbol.
* Incrusta la lógica de ventana en el jsp del componente entre las etiquetas javascript.
* Se define en:

   `apps/extjstraining/components/treeoverview/content.jsp`

El código javascript incrustado en el componente jsp:

* Define un `tree` intentando recuperar una ventana de árbol de la página.

* Si la ventana que muestra el árbol no existe, `treePanel` ([CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)):

   * `treePanel` contiene los datos que se utilizan para crear la ventana.
   * Los datos se recuperan llamando al servlet registrado en:
      `/bin/wcm/siteadmin/tree.json`

* La variable `beforeload` listener se asegura de que el nodo en el que se ha hecho clic se carga.
* `root``apps/extjstraining`
* `tree` ([`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)) se configura en función del `treePanel`y se muestra con:

   `tree.show();`

* Si la ventana ya existe, se muestra en función del ancho, la altura y las propiedades acopladas recuperadas del repositorio.

El cuadro de diálogo del componente:

* Muestra una ficha con 2 campos para definir el tamaño (anchura y altura) de la ventana de información general del árbol y un campo para acoplar/desacoplar la ventana
* Está definido por un nodo (tipo de nodo = `cq:Dialog`, xtype = [`panel`](/help/sites-developing/xtypes.md#panel)).

* El panel tiene un widget de campo de tamaño (tipo de nodo = `cq:Widget`, xtype = [`sizefield`](/help/sites-developing/xtypes.md#sizefield)) y un widget de selección (tipo de nodo = `cq:Widget`, xtype = [`selection`](/help/sites-developing/xtypes.md#selection), tipo = `radio`) con 2 opciones (true/false)

* Se define mediante el nodo de diálogo en:

   `/apps/extjstraining/components/treeoverview/dialog`

* Se procesa en formato json solicitando:

   `http://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`

* Se muestra de la siguiente manera:

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Información general de cuadrícula {#grid-overview}

Un panel de cuadrícula representa los datos en un formato de tabla de filas y columnas. Se compone de lo siguiente:

* Tienda : el modelo que contiene los registros de datos (filas).
* Modelo de columna : la composición de la columna.
* Ver : encapsula la interfaz de usuario.
* Modelo de selección : el comportamiento de selección.

El componente Información general de cuadrícula incluido en la variable **Uso de las utilidades de ExtJS** paquete muestra cómo mostrar los datos en formato de tabla:

* El ejemplo 1 utiliza datos estáticos.
* El ejemplo 2 utiliza datos recuperados del repositorio.

Para incluir el componente Información general de cuadrícula en la página de muestra:

1. Agregue la variable **5. Información general de cuadrícula** a la página de muestra desde el **Uso de las utilidades de ExtJS** en la ficha **Barra de tareas**.

1. El componente muestra:

   * un título con texto
   * a **PROPIEDADES** vínculo: haga clic en para mostrar las propiedades del párrafo almacenado en el repositorio. Click again to hide the properties.
   * a floating window containing data in tabular format.

El componente se muestra de la siguiente manera:

![](assets/screen_shot_2012-02-01at121109pm.png)

#### Ejemplo 1: Cuadrícula predeterminada {#example-default-grid}

En su versión predeterminada, el componente **Información general de cuadrícula** muestra una ventana con datos estáticos en formato de tabla. En este ejemplo, la lógica está incrustada en el jsp del componente de dos maneras:

* la lógica genérica se define entre etiquetas &lt;script>&lt;/script>
* la lógica específica está disponible en un archivo .js independiente y está vinculada a en jsp. Esta configuración permite cambiar fácilmente entre las dos lógicas (estática/dinámica) mediante el comentario de las etiquetas &lt;script> deseadas.

El componente Información general de cuadrícula :

* Se define en:

   `/apps/extjstraining/components/gridoverview`

* Su cuadro de diálogo permite definir el tamaño de la ventana y acoplar/desacoplar la ventana.

El componente jsp:

* Recupera las propiedades de ancho, alto y acoplado del repositorio.
* Muestra texto como introducción al formato de datos de información general de la cuadrícula.
* Hace referencia al código javascript que define el objeto GridPanel:

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`

   `defaultgrid.js` define algunos datos estáticos como una base para el objeto GridPanel.

* Incrusta código javascript entre etiquetas javascript que define el objeto Window que consume el objeto GridPanel.
* Se define en:

   `apps/extjstraining/components/gridoverview/content.jsp`

El código javascript incrustado en el componente jsp:

* Define el `grid` intentando recuperar el componente de ventana de la página:

   `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`

* If `grid` no existe, un [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) objeto ( `gridPanel`) se define llamando a la función `getGridPanel()` método (consulte a continuación). Este método se define en `defaultgrid.js`.

* `grid` es [`CQ.Ext.Window`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)basado en el panel de cuadrícula predefinido y se muestra: `grid.show();`

* If `grid` ya existe, se muestra en función de la anchura, la altura y las propiedades acopladas recuperadas del repositorio.

El archivo javascript ( `defaultgrid.js`) al que se hace referencia en el componente jsp define la variable `getGridPanel()` método al que llama el script incrustado en el JSP y devuelve un [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) basado en datos estáticos. La lógica es la siguiente:

* `myData` es una matriz de datos estáticos con formato de tabla de 5 columnas y 4 filas.
* `store` es `CQ.Ext.data.Store` objeto que consume `myData`.

* `store` se carga en la memoria:

   `store.load();`

* `gridPanel` es [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) objeto que consume `store`:

   * los anchos de columna se vuelven a asignar en todo momento:

      `forceFit: true`

   * solo se puede seleccionar una fila a la vez:

      `singleSelect:true`

#### Ejemplo 2: Cuadrícula de búsqueda de referencia {#example-reference-search-grid}

Al instalar el paquete, la variable `content.jsp` del **Información general de cuadrícula** muestra una cuadrícula basada en datos estáticos. Es posible modificar el componente para mostrar una cuadrícula con las siguientes características:

* Tiene tres columnas.
* Se basa en los datos recuperados del repositorio llamando a un servlet.
* Las celdas de la última columna se pueden editar. El valor se mantiene en un `test` debajo del nodo definido por la ruta que se muestra en la primera columna.

Como se explica en la sección anterior, el objeto window obtiene su [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) llamando al `getGridPanel()` método definido en la variable `defaultgrid.js` file at `/apps/extjstraining/components/gridoverview/defaultgrid.js`. La variable **Información general de cuadrícula** proporciona una implementación diferente para la variable `getGridPanel()` método, definido en la variable `referencesearch.js` file at `/apps/extjstraining/components/gridoverview/referencesearch.js`. Al cambiar el archivo .js al que se hace referencia en el jsp del componente, la cuadrícula se basará en los datos recuperados del repositorio.

Cambie el archivo .js al que se hace referencia en el componente jsp:

1. En **CRXDE Lite**, en el `content.jsp` del componente, comente la línea que incluye el `defaultgrid.js` para que tenga el siguiente aspecto:

   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`

1. Elimine el comentario de la línea que incluye la variable `referencesearch.js` para que tenga el siguiente aspecto:

   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`

1. Guarde los cambios.
1. Actualice la página de muestra.

El componente se muestra de la siguiente manera:

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

Código javascript al que se hace referencia en el componente jsp (`referencesearch.js`) define el `getGridPanel()` método llamado desde el componente jsp y devuelve un [`CQ.Ext.grid.GridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) , en función de los datos que se recuperan dinámicamente del repositorio. La lógica de `referencesearch.js` define algunos datos dinámicos como una base para el panel de cuadrícula:

* `reader` es [`CQ.Ext.data.JsonReader`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader) objeto que lee la respuesta del servlet en formato json para 3 columnas.

* `cm` es [`CQ.Ext.grid.ColumnModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) para 3 columnas.

   Las celdas de la columna &quot;Prueba&quot; se pueden editar tal como se definen con un editor:

   `editor: new `[`CQ.Ext.form.TextField`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)`({})`

* las columnas se pueden ordenar:

   `cm.defaultSortable = true;`

* `store` es [`CQ.Ext.data.GroupingStore`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore) objeto:

   * obtiene sus datos llamando al servlet registrado en &quot; `/bin/querybuilder.json`&quot; con algunos parámetros utilizados para filtrar la consulta
   * se basa en `reader`, definido previamente
   * la tabla se ordena según el &#39;**jcr:path**&#39; en orden ascendente

* `gridPanel` es [`CQ.Ext.grid.EditorGridPanel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel) objeto que se puede editar:

   * se basa en el `store` y en el modelo de columna `cm`
   * solo se puede seleccionar una fila a la vez:

      `sm: new `[`CQ.Ext.grid.RowSelectionModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)`({singleSelect:true})`

   * el `afteredit` el listener se asegura de que, después de una celda de la sección **Prueba**&quot; se ha editado la columna:

      * la propiedad &#39; `test`&#39; del nodo en la ruta definida por la columna &quot;**jcr:path**&quot; se establece en el repositorio con el valor de la celda
      * si el POST se realiza correctamente, el valor se agrega al objeto `store`; de lo contrario, se rechaza
