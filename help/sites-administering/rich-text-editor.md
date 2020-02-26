---
title: Configuración del editor de texto enriquecido
seo-title: Configuración del editor de texto enriquecido
description: Aprenda a configurar el editor de texto enriquecido de AEM.
seo-description: Aprenda a configurar el editor de texto enriquecido de AEM.
uuid: 82d2fe41-676a-4a49-939f-13374b9d869f
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 9248d09c-b749-4aca-9167-1707c1dd8a53
translation-type: tm+mt
source-git-commit: 01a748a6f6f92c752fc6a14005f236fee304c2eb

---


# Configure the Rich Text Editor {#configure-the-rich-text-editor}

El editor de texto enriquecido (RTE) ofrece a los autores una amplia gama de funciones para editar su contenido de texto. Se proporcionan iconos, cuadros de selección, barras de herramientas y menús para una experiencia de edición de texto WYSIWYG.

RTE se puede configurar para habilitar, deshabilitar y ampliar las funciones disponibles en los componentes de creación. Para saber cómo utilizar las funciones RTE para la creación, consulte [Uso del editor de texto enriquecido para la creación](/help/sites-authoring/rich-text-editor.md).

El flujo de trabajo siguiente ilustra el orden recomendado para completar las tareas de configuración RTE.

![Flujo de trabajo habitual para configurar el Editor de texto enriquecido](assets/rte_workflow_v1.png)

**** Figura: Flujo de trabajo *típico para configurar el Editor de texto enriquecido*

## Comprender la IU táctil y la IU clásica {#understand-touch-enabled-ui-and-classic-ui}

La IU táctil es la IU estándar para AEM. Adobe ha introducido la IU táctil en la versión 5.6 con un diseño [](/help/sites-authoring/responsive-layout.md) interactivo para el entorno de creación.La IU táctil está diseñada para dispositivos táctiles y de escritorio. La IU difiere considerablemente de la IU clásica original.

![Barra de herramientas del Editor de texto enriquecido en la IU táctil](assets/chlimage_1-404.png)

**** Figura: Barra de herramientas del Editor de texto *enriquecido en la IU táctil*

![Barra de herramientas del Editor de texto enriquecido en la IU clásica](assets/rtedefault.png)

**** Figura: Barra de herramientas del Editor de texto *enriquecido en la IU clásica*

**Consulte también**:

* [Recomendaciones de la interfaz de usuario](/help/sites-deploying/ui-recommendations.md)
* Acerca de la desaprobación de la IU clásica, consulte Notas de la versión de [AEM 6.4](/help/release-notes/deprecated-removed-features.md)
* Para ver las diferencias entre las IU, consulte IU [táctil y IU clásica](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
* Para comprender la IU táctil en detalle, consulte [Conceptos de la IU táctil de AEM](/help/sites-developing/touch-ui-concepts.md)

## Diversos modos de edición {#editingmodes}

Los autores pueden crear y editar contenido textual en AEM utilizando los distintos modos de componentes. Las opciones de la barra de herramientas para crear y dar formato al contenido y la experiencia del usuario de los componentes habilitados para RTE en diferentes modos de edición varían según las configuraciones de RTE.

<table> 
 <tbody> 
  <tr> 
   <th>Modo de edición</th> 
   <th>Área de edición</th> 
   <th>Funciones recomendadas para habilitarlas<br /> </th> 
   <th>IU táctil</th> 
   <th>IU clásica</th> 
  </tr> 
  <tr> 
   <td>En línea</td> 
   <td>Edición in situ para ediciones rápidas y secundarias; Formato sin abrir un cuadro de diálogo</td> 
   <td>Características mínimas de RTE</td> 
   <td>Y</td> 
   <td>Y</td> 
  </tr> 
  <tr> 
   <td>RTE pantalla completa</td> 
   <td>Abarca toda la página<br /> </td> 
   <td>Todas las funciones RTE necesarias<br /> </td> 
   <td>Y</td> 
   <td>N<br /> </td> 
  </tr> 
  <tr> 
   <td>Cuadro de diálogo</td> 
   <td>Cuadro de diálogo en la parte superior del contenido de la página pero no cubre toda la página</td> 
   <td>Todas las funciones RTE necesarias en la IU clásica; activar correctamente las funciones en la IU táctil<br /> </td> 
   <td>Y</td> 
   <td>Y</td> 
  </tr> 
  <tr> 
   <td>Pantalla completa del cuadro de diálogo<br /> </td> 
   <td>Igual que el modo de pantalla completa; contiene campos del cuadro de diálogo junto con RTE<br /> </td> 
   <td>Todas las funciones RTE necesarias</td> 
   <td>Y</td> 
   <td>N</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>La función de edición de origen no está disponible en el modo de edición en línea en la IU táctil. No puede arrastrar imágenes en el modo de pantalla completa. Todas las demás funciones funcionan en todos los modos.

### Edición en línea {#inline-editing}

Cuando se abre (con un doble toque o clic lento), el contenido se puede editar dentro de la página. Se presenta una barra de herramientas compacta con opciones básicas.

![Edición en línea con la barra de herramientas básica en la IU táctil](assets/chlimage_1-405.png)

**** Figura: Edición *en línea con una barra de herramientas básica en la IU táctil*

En la IU clásica, un doble clic lento en el componente permite la edición en línea y un contorno naranja resalta el contenido. Si Content Finder está abierto, se muestra una barra de herramientas con las opciones de formato RTE disponibles en la parte superior de la ventana. Si Content Finder no está abierto, las opciones de formato no se muestran y solo puede realizar ediciones básicas de texto.

### Full screen editing {#full-screen-editing}

Los componentes de AEM se pueden abrir en una vista de pantalla completa que oculta el contenido de la página y ocupa la pantalla disponible. Considere la posibilidad de editar en pantalla completa una versión detallada de la edición en línea, ya que ofrece la mayor cantidad de opciones de edición. Se puede abrir haciendo clic en ![rte_fullscreen](assets/rte_fullscreen.png), desde la barra de herramientas compacta cuando se utiliza el modo de edición en línea.

El modo de pantalla completa del cuadro de diálogo proporciona una barra de herramientas RTE detallada y las opciones y los componentes disponibles en el modo de cuadro de diálogo. Solo se aplica a un cuadro de diálogo que contenga RTE junto con otros componentes.

![Barra de herramientas RTE detallada al editar en modo de pantalla completa en la IU táctil](assets/chlimage_1-406.png)

**** Figura: *La barra de herramientas detallada de RTE al editar en modo de pantalla completa en la IU táctil*

### Edición de cuadro de diálogo {#dialog-editing}

Cuando se hace doble clic en un componente en la IU clásica, se abre un cuadro de diálogo para editar el contenido. El cuadro de diálogo se abre sobre la página existente. En algunos casos específicos, el cuadro de diálogo se abre como una ventana emergente. Por ejemplo, cuando un componente Texto forma parte de una columna en un diseño de página de varias columnas y el área disponible para el cuadro de diálogo es menor.

![Modo de edición de cuadro de diálogo en la IU táctil](assets/dialog_editing_modetouchui.png)

**** Figura: Modo de edición *del cuadro de diálogo en la IU táctil*

![Cuadro de diálogo en la IU clásica que contiene una barra de herramientas detallada para la edición](assets/chlimage_1-407.png)

**** Figura: Cuadro de *diálogo en la IU clásica que contiene una barra de herramientas detallada para editarla*

## Acerca de los complementos RTE y las funciones asociadas {#aboutplugins}

La funcionalidad está disponible mediante una serie de complementos, cada uno con:

* Una `features` propiedad:

   * Se utiliza para activar o desactivar la funcionalidad básica de ese complemento.
   * Esto se puede configurar mediante un procedimiento estandarizado.

* Cuando proceda, más propiedades y opciones que requieren una configuración especializada.

Las funciones básicas de RTE se activan o desactivan por el valor de la `features` propiedad en un nodo específico del complemento adecuado.

En la tabla siguiente se muestran los complementos actuales y se muestran:

* ID de complementos con un vínculo a la documentación de API. El ID se utiliza como nombre de nodo al [activar un complemento](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Valores permitidos para la `features` propiedad.
* Descripción de la funcionalidad proporcionada por el complemento.

<table> 
 <tbody> 
  <tr> 
   <td><p>ID<br /> del complemento <br /> </p> </td> 
   <td><p>features<br /> <br /> </p> </td> 
   <td><p>Descripción<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>editar</p> </td> 
   <td><p>cortar<br /> copiar<br /> pegar-predeterminado<br /> pegar-plaintext<br /> pegar-wordhtml</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="_blank">Cortar, copiar y pegar los tres modos</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin">findreplace</a></p> </td> 
   <td><p>find<br /> replace</p> </td> 
   <td><p>Buscar y reemplazar.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin">format</a></p> </td> 
   <td><p>negrita<br /> cursiva<br /> subrayado</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="_blank">Formato</a>de texto básico.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin">imagen</a></p> </td> 
   <td><p>imagen</p> </td> 
   <td><p>Defina algunas propiedades de imagen, como alineación y texto alternativo. La compatibilidad básica para arrastrar y soltar imágenes desde Content Finder funciona sin este complemento.</p> <p><em>Nota</em>: El comportamiento de creación puede variar con el explorador. Por ejemplo, Mozilla Firefox ofrece capacidades de cambio de tamaño, pero Google Chrome no.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin">claves</a></p> </td> 
   <td><p> </p> </td> 
   <td><p>Para definir este valor, consulte Tamaño <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#tabsize" target="_blank">de tabulación</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin">justify</a></p> </td> 
   <td><p>justifyleft<br /> justifycenter<br /> justificante Copyright</p> </td> 
   <td><p>Alineación de párrafo.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin">vínculos</a></p> </td> 
   <td><p>modifylink<br /> desvincular<br /> anclaje</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#linkstyles" target="_blank">Hipervínculos y anclajes</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin">listas</a></p> </td> 
   <td><p>sangría<br /> sin orden<br /><br /> ordenada</p> </td> 
   <td><p>Este complemento controla tanto la <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#indentmargin" target="_blank">sangría como las listas</a>; incluidas las listas anidadas.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin">misctools</a></p> </td> 
   <td><p>specialchars<br /> sourceedit</p> </td> 
   <td>Varias herramientas permiten a los autores introducir caracteres <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#spchar" target="_blank"></a> especiales o editar el origen HTML. Además, puede agregar un <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#definerangechar" target="_blank">rango completo de caracteres</a> especiales si desea definir su propia lista.</td> 
  </tr> 
  <tr> 
   <td><p>Paraformat</p> </td> 
   <td><p>parformat</p> </td> 
   <td>Los formatos de párrafo predeterminados son Párrafo, Encabezado 1, Encabezado 2 y Encabezado 3 (&lt;p&gt;, &lt;h1&gt;, &lt;h2&gt; y &lt;h3&gt;). Puede <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#paraformats" target="_blank">agregar más formatos</a> de párrafo o ampliar la lista.</td> 
  </tr> 
  <tr> 
   <td><p>spellcheck</p> </td> 
   <td><p>texto de comprobación</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#adddict" target="_blank">Corrector ortográfico</a>con conocimiento del idioma.</p> </td> 
  </tr> 
  <tr> 
   <td><p>estilos</p> </td> 
   <td><p>estilos</p> </td> 
   <td>Compatibilidad con estilos mediante una clase CSS. <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="-blank">Agregue nuevos estilos</a> de texto si desea agregar (o ampliar) su propia gama de estilos para utilizarlos con texto.</td> 
  </tr> 
  <tr> 
   <td><p>subsuperíndice</p> </td> 
   <td><p>superíndice de subíndice<br /></p> </td> 
   <td><p>Extensiones a los formatos básicos, agregando sub-y-super-script.</p> </td> 
  </tr> 
  <tr> 
   <td><p>tabla</p> </td> 
   <td><p>tabla<br /> insertar extraíble<br /> quitar<br /> quitar insertar<br /> columna<br /> quitar columna<br /> celda props<br /> mergecells<br /> dividir celda<br /> seleccionar filas<br /> seleccionar columnas</p> </td> 
   <td>Consulte <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles" target="_blank">Configuración de estilos</a>de tabla si desea agregar sus propios estilos para tablas enteras o celdas individuales.</td> 
  </tr> 
  <tr> 
   <td><p>deshacer</p> </td> 
   <td><p>undo<br /> redo</p> </td> 
   <td>Tamaño del historial de las operaciones de <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#undohistory" target="_blank">deshacer y rehacer</a> .</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>El complemento de pantalla completa no es compatible con el modo de cuadro de diálogo. Uso de la `dialogFullScreen` configuración para configurar la barra de herramientas para el modo de pantalla completa.

## Conocer las rutas y ubicaciones de configuración {#understand-the-configuration-paths-and-locations}

El [modo de edición RTE (y la interfaz de usuario)](#editingmodes) que proporciona a los autores decide la ubicación de los detalles de configuración al [activar los complementos](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)RTE:

| Modo de edición | Ubicación para la IU táctil | Ubicación para la IU clásica |
|---|---|---|
| En línea | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Pantalla completa | `cq:editConfig/cq:inplaceEditing` | No aplicable |
| Cuadro de diálogo | `cq:dialog` | `dialog` |
| Cuadro de diálogo de pantalla completa | `cq:dialog` | No aplicable |

>[!NOTE]
>
>No asigne un nombre al nodo en `cq:inplaceEditing` como `config`. En el `cq:inplaceEditing` nodo, defina las siguientes propiedades:
>
>* **Nombre**: `configPath`
   >
   >
* **Tipo**: `String`
   >
   >
* **Valor**: ruta del nodo que contiene la configuración real
>
>
No asigne un nombre al nodo de configuración RTE como `config`. De lo contrario, las configuraciones de RTE surtirán efecto únicamente para los administradores y no para los usuarios del grupo `content-author`.

Configure las siguientes propiedades que se aplican en el modo de edición de cuadro de diálogo solo en la IU táctil:

* `useFixedInlineToolbar`:: Establezca esta propiedad booleana definida en el nodo RTE (uno con sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) en `True`, para que la barra de herramientas RTE sea fija en lugar de flotante.

   Cuando esta propiedad es verdadera, la edición de Richtext se inicia, de forma predeterminada, en el evento &quot;foundation-contentloaded&quot;.

   Para evitar esto, establezca la propiedad `customStart` en `True`y active el evento &#39;rte-start&#39; para iniciar la edición RTE. Cuando esta propiedad es &#39;true&#39;, el comportamiento predeterminado, la velocidad de inicio al hacer clic, no funciona.

* `customStart`:: Establezca esta propiedad booleana definida en el nodo RTE en `True`, para controlar cuándo iniciar RTE activando el evento `rte-start`.

* `rte-start`:: Activar este evento en el `contenteditable-div` servidor RTE, cuándo empezar a editar RTE. Esto solo funciona si `customStart` se ha establecido en true.

Cuando se utiliza RTE en el cuadro de diálogo táctil, es obligatorio establecer la propiedad `useFixedInlineToolbar` en true para evitar problemas.

## Activar las funcionalidades RTE mediante la activación de complementos {#enable-rte-functionalities-by-activating-plug-ins}

Las funcionalidades RTE están disponibles a través de una serie de complementos, cada uno con propiedad de características. Puede configurar la propiedad features para habilitar o deshabilitar las diversas características de cada complemento.

Para obtener configuraciones detalladas de los complementos RTE, consulte [cómo activar y configurar los complementos](/help/sites-administering/configure-rich-text-editor-plug-ins.md)RTE.


Descargue esta configuración de muestra para comprender cómo configurar RTE. En este paquete todas las funciones están habilitadas.

[Obtener archivo](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>El componente [de texto Componentes](https://helpx.adobe.com/experience-manager/core-components/using/text.html) principales permite a los editores de plantillas configurar muchos complementos RTE en la interfaz de usuario como políticas de contenido, lo que elimina la necesidad de una configuración técnica. Las políticas de contenido pueden funcionar con las configuraciones de interfaz de usuario RTE como se describe. Para obtener más información, consulte la configuración de la interfaz de usuario de [RTE y las políticas](/help/sites-administering/rich-text-editor.md#rtecontentpolicies)de contenido, [Creación de plantillas](/help/sites-authoring/templates.md)de página y documentación [para desarrolladores de componentes](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)principales.

>[!NOTE]
>
>Para fines de referencia, los componentes de texto predeterminados (entregados como parte de una instalación estándar) se encuentran en:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>
Para crear su propio componente de texto, copie el componente anterior en lugar de editar estos componentes.

## Configurar barra de herramientas RTE {#dialogfullscreen}

AEM le permite configurar la IU para el Editor de texto enriquecido de forma diferente para los distintos modos de edición. A continuación se proporciona la configuración predeterminada. Puede anular estos valores predeterminados según sus necesidades.

Para disfrutar de la mejor experiencia de creación:

* En un cuadro de diálogo flotante, habilite solo los complementos que no tengan una ventana emergente, ya que el cuadro de diálogo flotante tiene un tamaño menor.
* En el cuadro de diálogo de pantalla completa, habilite todos los complementos necesarios, incluso los complementos con una ventana emergente más grande, como el `Paste` complemento. Utilice la `dialogFullScreen` configuración que se describe a continuación.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Para el modo en línea y el modo de pantalla completa se utilizan diferentes ajustes de IU. La propiedad toolbar se utiliza para especificar los botones de la barra de herramientas. Por ejemplo, si el botón es en sí mismo una función (por ejemplo, `Bold`), se especifica como `PluginName#FeatureName` (por ejemplo, `links#modifylink`). Si el botón es una ventana emergente (que contiene algunas características de un complemento), se especifica como `#PluginName` (por ejemplo, `#format`). Separadores (| ) entre un grupo de botones se puede especificar con &#39;-&#39;.

El nodo emergente en el modo en línea o en pantalla completa contiene una lista de las ventanas emergentes que se utilizan. Cada nodo secundario bajo el `popovers` nodo recibe el nombre del complemento (por ejemplo, `format`). Tiene una propiedad `items` que contiene una lista de características del complemento (por ejemplo, `format#bold`).

## Configuración de la interfaz de usuario RTE y directivas de contenido {#rtecontentpolicies}

Los administradores pueden controlar las opciones de RTE mediante políticas de contenido, por ejemplo, en lugar de realizar la configuración como se ha descrito anteriormente. Las políticas de contenido definen las propiedades de diseño de un componente cuando se utilizan como parte de una plantilla [](../sites-authoring/templates.md)editable. Por ejemplo, si se utiliza un componente de texto que utiliza RTE con una plantilla editable, la política de contenido puede definir que la opción de negrita esté disponible y que haya algunas opciones de formato de párrafo disponibles. Las políticas de contenido son reutilizables y se pueden aplicar en varias plantillas.

A partir de AEM 6.4 Service Pack 3, las opciones disponibles en el flujo RTE desde las configuraciones de la interfaz de usuario hasta las políticas de contenido.

* La configuración de la interfaz de usuario define las opciones disponibles para las directivas de contenido.
* Si la configuración de la interfaz de usuario de RTE se elimina o no activa un elemento, la directiva de contenido no puede configurarlo.
* Un autor solo tiene acceso a la funcionalidad que están disponibles en las configuraciones de la interfaz de usuario y en las políticas de contenido.

Como ejemplo, puede ver la documentación [del componente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)Texto principal.

## Personalización de la asignación entre iconos y comandos de la barra de herramientas {#iconstoolbar}

Puede personalizar la asignación entre los iconos de Coral que se muestran en la barra de herramientas de RTE y los comandos disponibles. No puede utilizar ningún otro icono aparte de los iconos de Coral.

1. Cree un nodo con el nombre `icons` debajo de `uiSettings/cui`.

1. Cree nodos para iconos individuales debajo de él.
1. En cada uno de los nodos de icono individuales, especifique un icono de Coral y un comando para asignarlo al icono.

A continuación se muestra un fragmento de ejemplo para asignar el comando Negrita al icono Coral denominado `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## Cambiar al editor de texto enriquecido CoralUI 2 {#switch-to-coralui-rich-text-editor}

En una página, puede incluir la clientlib CoralUI 2 RTE o la clientlib CoralUI 3 RTE. De forma predeterminada, el Editor de texto enriquecido incluye la clientlib CoralUI 3 RTE. Para cambiar a CoralUI 2 RTE, realice los siguientes pasos.

>[!NOTE]
>
>Adobe no recomienda el cambio como práctica recomendada. Cambie a CoralUI 2 RTE como último recurso. Los complementos personalizados para CoralUI 2 RTE funcionan con CoralUI 3 RTE si los complementos no dependen de elementos internos de RTE, como clases. Si utiliza complementos personalizados para CoralUI 3 RTE, utilice `rte.coralui3` library.

1. Superponga el nodo `/libs/cq/gui/components/authoring/editors/clientlibs/core` debajo de `/apps`y haga lo siguiente:

   * Replace `rte.coralui3` with `rte.coralui2` for the dependencies property.
   * Replace `cq.authoring.editor.core.inlineediting.rte.coralui3` with `cq.authoring.editor.core.inlineediting.rte.coralui2` for the embed property.
   * Replace `cq.authoring.rte.coralui3` with `cq.authoring.rte.coralui2` for the embed property.

1. Superponga los nodos `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` y `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` debajo de `/apps`.

   Elimine la categoría `cq.authoring.dialog` de `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` y agréguela a `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Cambie cualquier otra dependencia que se incluya en la página de `rte.coralui3` a `rte.coralui2`. Por ejemplo, después de superponer el nodo `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` debajo de `/apps`, cambie cualquier dependencia de él de `rte.coralui3` a `rte.coralui2`.

1. Superponga el nodo `cq/ui/widgets` debajo de `/apps`. Reemplazar la dependencia `cq.rte` en el nodo `/apps/cq/ui/widgets` por `cq.coralui2.rte`.

>[!NOTE]
>
>CoralUI 2 RTE utiliza plantillas de controladores para los cuadros de diálogo de complementos. Por lo tanto, la clientlib CoralUI 2 RTE dependía de la clientlib de controladores. CoralUI 3 RTE no utiliza plantillas de controladores y no tiene ninguna dependencia asociada. Si los complementos personalizados utilizan plantillas de controladores, incluya la clientlib de controladores en la página web.

## Información adicional {#further-information}

Para obtener más información sobre la configuración de RTE, consulte la referencia de la API [de utilidades de](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) AEM.

En particular, para ver los complementos y las opciones relacionadas disponibles:

* El componente [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) proporciona un campo de formulario para editar información de texto con estilo (texto enriquecido). Para conocer todos los parámetros disponibles para el formulario de texto enriquecido, consulte Opciones de configuración.
* El componente RichText proporciona una amplia gama de funciones mediante complementos enumerados en [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Para cada complemento:

   * consulte las Funciones para obtener detalles sobre la funcionalidad que se puede habilitar (o deshabilitar)
   * Consulte las Opciones de configuración para ver todos los parámetros disponibles para la configuración detallada del complemento apropiado

* También hay disponible más información sobre las reglas HTML para los vínculos.

Las opciones anteriores pueden utilizarse para ampliar y personalizar su propio RTE. Por ejemplo, para enumerar los anclajes disponibles en la página al crear un vínculo, puede proporcionar su propia implementación del `LinkPlugin`.

## Limitaciones conocidas {#known-limitations}

La capacidad de AEM RTE tiene las siguientes limitaciones:

* Las funciones RTE solo se admiten en los cuadros de diálogo de componentes de AEM. RTE no se admite en asistentes o formularios de base como Propiedades [de](../sites-developing/page-properties-views.md) página y [Andamiaje](../sites-authoring/scaffolding.md) en la IU táctil.

* AEM no funciona en dispositivos [híbridos](../release-notes/known-issues.md).

* No asigne un nombre al nodo de configuración RTE `config`. De lo contrario, la configuración RTE solo se aplica a los administradores y no a los usuarios del grupo `content-author`.

* RTE no admite iframe o iframe en línea para incrustar contenido.

>[!MORELIKETHIS]
>
>* [Configuración de complementos RTE](configure-rich-text-editor-plug-ins.md)
>* [Usar editor de texto enriquecido para la creación](../sites-authoring/rich-text-editor.md)
>* [Configurar RTE para sitios accesibles](rte-accessible-content.md)
>* [Paridad de funciones de IU táctil y de IU clásica](../release-notes/touch-ui-features-status.md)
>* [Ejemplo de tutorial para crear un componente de varios campos compuesto](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

