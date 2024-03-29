---
title: Configuración del Editor de texto enriquecido
description: Aprenda a configurar el Editor de texto enriquecido AEM.
contentOwner: AG
exl-id: 2d5e9ada-1567-43dc-ab19-6891e20e1d0b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2695'
ht-degree: 1%

---

# Configuración del Editor de texto enriquecido {#configure-the-rich-text-editor}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El Editor de texto enriquecido (RTE) proporciona a los autores una amplia gama de funciones para editar su contenido de texto. Se proporcionan iconos, cuadros de selección, barras de herramientas y menús para una experiencia de edición de texto WYSIWYG.

Para saber cómo utilizar las funciones RTE para la creación, consulte [Usar el Editor de texto enriquecido para la creación](/help/sites-authoring/rich-text-editor.md). RTE se puede configurar para habilitar, deshabilitar y ampliar las funciones disponibles en los componentes de creación. El siguiente flujo de trabajo ilustra un orden recomendado para completar las tareas de configuración de RTE en Experience Manager.

![Flujo de trabajo típico para configurar el Editor de texto enriquecido](assets/rte_workflow_v1.png)

*Figura: Flujo de trabajo típico para configurar el Editor de texto enriquecido*

## Explicación de la IU táctil y la IU clásica {#understand-touch-enabled-ui-and-classic-ui}

La IU táctil es la IU estándar para AEM. Adobe introducido en la interfaz de usuario táctil con [diseño interactivo](/help/sites-authoring/responsive-layout.md) para el entorno de creación, en la versión 5.6. La IU táctil está diseñada para dispositivos táctiles y de escritorio. La IU difiere considerablemente de la IU clásica original.

![Barra de herramientas del Editor de texto enriquecido en la IU táctil](assets/chlimage_1-404.png)

*Figura: Barra de herramientas del Editor de texto enriquecido en la IU táctil*

![Barra de herramientas del Editor de texto enriquecido en la IU clásica](assets/rtedefault.png)

*Figura: Barra de herramientas del Editor de texto enriquecido en la IU clásica*

>[!MORELIKETHIS]
>
>* [Recomendaciones de la interfaz de usuario](/help/sites-deploying/ui-recommendations.md)
>* Acerca de la desaprobación de la IU clásica, consulte [Notas de la versión de AEM 6.4](/help/release-notes/deprecated-removed-features.md)
>* Para ver las diferencias entre las IU, consulte [IU táctil e IU clásica](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* Para comprender la IU táctil en detalle, consulte [Conceptos de AEM interfaz de usuario táctil](/help/sites-developing/touch-ui-concepts.md)


## Varios modos de edición {#editingmodes}

Los autores pueden crear y editar contenido textual en AEM utilizando los distintos modos de componentes. Las opciones de la barra de herramientas para crear y dar formato al contenido y la experiencia del usuario de los componentes habilitados para RTE en diferentes modos de edición varían según las configuraciones de RTE.

| Modo de edición | Área de edición | Funciones recomendadas para habilitarlas | IU táctil | IU clásica |
|--- |--- |--- |--- |--- |
| En línea | Edición in situ para ediciones rápidas y secundarias; Formato sin abrir un cuadro de diálogo | Características mínimas de RTE | Y | Y |
| Pantalla completa RTE | Cubre toda la página | Todas las funciones RTE requeridas | Y | N |
| Cuadro de diálogo | Cuadro de diálogo sobre el contenido de la página, pero no cubre toda la página | Todas las funciones RTE necesarias en la IU clásica; activar las funciones con cautela en la interfaz de usuario táctil | Y | Y |
| Diálogo de pantalla completa | Igual que el modo de pantalla completa; contiene campos del cuadro de diálogo junto con RTE | Todas las funciones RTE requeridas | Y | N |

>[!NOTE]
>
>La función de edición de origen no está disponible en el modo de edición en línea en la IU táctil. No se pueden arrastrar imágenes en el modo de pantalla completa. Todas las demás funciones funcionan en todos los modos.

### Edición en línea {#inline-editing}

Cuando se abre (con un doble toque o clic lento), el contenido se puede editar dentro de la página. Se presenta una barra de herramientas compacta con opciones básicas.

![Edición en línea con la barra de herramientas básica en la IU táctil](assets/chlimage_1-405.png)

*Figura: Edición en línea con la barra de herramientas básica en la IU táctil*

En la IU clásica, un doble clic lento en el componente permite la edición en línea y un contorno naranja resalta el contenido. Si el buscador de contenido está abierto, se muestra una barra de herramientas con las opciones de formato RTE disponibles en la parte superior de la ventana. Si el Buscador de contenido no está abierto, las opciones de formato no se muestran y solo puede realizar ediciones básicas de texto.

### Edición de pantalla completa {#full-screen-editing}

AEM componentes se pueden abrir en la vista de pantalla completa que oculta el contenido de la página y ocupa la pantalla disponible. Considere la posibilidad de editar en pantalla completa una versión detallada de la edición en línea, ya que ofrece las mejores opciones de edición. Se puede abrir haciendo clic en ![rte_fullscreen](assets/rte_fullscreen.png), en la barra de herramientas compacta al utilizar el modo de edición en línea.

El modo de pantalla completa del cuadro de diálogo proporciona, una barra de herramientas RTE detallada y las opciones y los componentes disponibles en el modo de diálogo. Solo es aplicable a un cuadro de diálogo que contenga RTE junto con otros componentes.

![La barra de herramientas detallada de RTE al editar en modo de pantalla completa en la IU táctil](assets/chlimage_1-406.png)

*Figura: La barra de herramientas detallada de RTE al editar en modo de pantalla completa en la IU táctil*

### Edición del cuadro de diálogo {#dialog-editing}

Cuando se hace doble clic en un componente en la IU clásica, se abre un cuadro de diálogo para editar el contenido. El cuadro de diálogo se abre sobre la página existente. En algunos casos específicos, el cuadro de diálogo se abre como una ventana emergente. Por ejemplo, cuando un componente Texto forma parte de una columna en un diseño de página de varias columnas y el área disponible para el cuadro de diálogo es menor.

![Modo de edición de cuadro de diálogo en la IU táctil](assets/dialog_editing_modetouchui.png)

*Figura: Modo de edición de cuadro de diálogo en la IU táctil*

![Cuadro de diálogo en la IU clásica que contiene una barra de herramientas detallada para editarla](assets/chlimage_1-407.png)

*Figura: Cuadro de diálogo en la IU clásica que contiene una barra de herramientas detallada para editarla*

## Acerca de los complementos RTE y las funciones asociadas {#aboutplugins}

La funcionalidad está disponible a través de una serie de complementos, cada uno con:

* A `features` propiedad:

   * Se utiliza para activar o desactivar la funcionalidad básica de ese complemento.
   * Que se puede configurar mediante un procedimiento estandarizado.

* Cuando corresponda, más propiedades y opciones que requieren una configuración especializada.

Las características básicas del RTE se activan o desactivan por el valor del `features` en un nodo específico del complemento adecuado.

La tabla siguiente muestra los complementos actuales:

* ID de complemento con un vínculo a la documentación de la API. El ID se utiliza como nombre de nodo cuando [activación de un complemento](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Valores permitidos para la variable `features` propiedad.
* Descripción de la funcionalidad proporcionada por el complemento.

| ID del complemento | características | Descripción |
|--- |--- |--- |
| editar | cortar copiar pegar-predeterminado pegar-plaintext pegar-wordhtml | [Cortar, copiar y, los tres modos de pegado](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [findreplace](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | buscar reemplazar | Buscar y reemplazar. |
| [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | subrayado en negrita cursiva | [Formato de texto básico](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [imagen](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | image | Compatibilidad con imágenes básicas (arrastre desde el contenido o el Buscador de contenido). En función del explorador, la compatibilidad con tiene comportamientos diferentes para los autores |
| [keys](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | Para definir este valor, consulte [tamaño de la ficha](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tab-size). |
| [reasons](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifyleft justifycenter justificado | Alineación del párrafo. |
| [vínculos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink desvincular anclaje | [Hipervínculos y anclajes](/help/sites-administering/configure-rich-text-editor-plug-ins.md#link-styles). |
| [listas](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | sangría ordenada sin ordenar | Este complemento controla ambos [sangría y listas](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indent-margin); incluir listas anidadas. |
| [misctools](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | Las herramientas varias permiten a los autores entrar [caracteres especiales](/help/sites-administering/configure-rich-text-editor-plug-ins.md#special-char) o editar el origen del HTML. Además, puede agregar un conjunto [rango de caracteres especiales](/help/sites-administering/configure-rich-text-editor-plug-ins.md#define-range-char) si desea definir su propia lista. |
| Paraformato | paraformat | Los formatos de párrafo predeterminados son Párrafo, Encabezado 1, Encabezado 2 y Encabezado 3 (`<p>`, `<h1>`, `<h2>`y `<h3>`). Puede [añadir más formatos de párrafo](/help/sites-administering/configure-rich-text-editor-plug-ins.md#para-formats) o ampliar la lista. |
| ortografía | texto de comprobación | [Corrector ortográfico según idioma](/help/sites-administering/configure-rich-text-editor-plug-ins.md#add-dict). |
| estilos | estilos | Compatibilidad con estilos mediante una clase CSS. [Agregar nuevos estilos de texto](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles) si desea añadir (o ampliar) su propio rango de estilos para utilizarlo con texto. |
| subsuperíndice | superíndice de subíndice | Extensiones a los formatos básicos, adición de subscript y superscript. |
| tabla | tabla removible insertrow removerow insertcolumn removecolumn cellprops mergecells separtcell selectrow selectcolumns | Consulte [configurar estilos de tabla](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles), si desea agregar sus propios estilos para tablas completas o celdas individuales. |
| deshacer | deshacer rehacer | Tamaño del historial de [deshacer y rehacer](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undo-history) operaciones. |

>[!NOTE]
>
>El complemento de pantalla completa no es compatible con el modo de cuadro de diálogo. Uso del `dialogFullScreen` para configurar la barra de herramientas para el modo de pantalla completa.

## Explicación de las rutas y ubicaciones de configuración {#understand-the-configuration-paths-and-locations}

La variable [modo de edición RTE (y la IU)](#editingmodes) que proporcione a los autores para que decidan la ubicación de los detalles de configuración cuando [activación de los complementos RTE](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin):

| Modo de edición | Ubicación para la IU táctil | Ubicación para la IU clásica |
|---|---|---|
| En línea | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Pantalla completa | `cq:editConfig/cq:inplaceEditing` | No aplicable |
| Cuadro de diálogo | `cq:dialog` | `dialog` |
| Cuadro de diálogo de pantalla completa | `cq:dialog` | No aplicable |

>[!NOTE]
>
>No asigne un nombre al nodo de `cq:inplaceEditing` como `config`. Activado `cq:inplaceEditing` , defina las siguientes propiedades:
>
>* **Nombre**: `configPath`
>* **Tipo**: `String`
>* **Valor**: ruta del nodo que contiene la configuración real
>
>No asigne al nodo de configuración RTE el nombre `config`. De lo contrario, las configuraciones de RTE surten efecto solo para los administradores y no para los usuarios del grupo `content-author`.

Configure las siguientes propiedades que se aplican en el modo de edición de cuadro de diálogo solo en la IU táctil:

* `useFixedInlineToolbar`: Establezca esta propiedad booleana definida en el nodo RTE (una con sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) a `True`, para que la barra de herramientas RTE sea fija en lugar de flotante.

   Cuando esta propiedad es verdadera, la edición de Richtext se inicia, de forma predeterminada, en el evento &quot;foundation-contentloaded&quot;.

   Para evitarlo, establezca la propiedad `customStart` a `True`y déclencheur el evento de inicio de RTE para iniciar la edición de RTE. Cuando esta propiedad es &#39;true&#39;, el comportamiento predeterminado, rte start on click, no funciona.

* `customStart`: Establezca esta propiedad booleana definida en el nodo RTE como `True`, para controlar cuándo iniciar RTE activando el evento `rte-start`.

* `rte-start`: Déclencheur este evento en la variable `contenteditable-div` de RTE, cuándo iniciar la edición de RTE. Esto solo funciona si `customStart` se ha establecido en true.

Cuando se utiliza RTE en el cuadro de diálogo táctil, se establece la propiedad `useFixedInlineToolbar` como true es obligatorio para evitar problemas.

## Personalización de la edición in situ {#customizing-in-place-editing}

Puede definir en qué selector de HTML se inicia el editor de texto configurando las siguientes propiedades:

* **`editElementQuery`** - Definido en `cq:InplaceEditingConfig`, esta propiedad se utiliza para especificar un selector del elemento HTML en el que se iniciará la edición en línea para el componente de texto. Si no se especifica, la edición en línea se inicia directamente en el HTML de componentes de texto.
* **`textPropertyName`** - Definido en `cq:InplaceEditingConfig`, esta propiedad se utiliza para especificar el nombre de la propiedad que se guardará en el nodo de contenido donde el valor de HTML del componente de texto se mantendrá tras la edición en línea.

La propiedad correspondiente para el modo de diálogo es `name`.

## Habilitar las funcionalidades RTE activando complementos {#enable-rte-functionalities-by-activating-plug-ins}

Las funcionalidades de RTE están disponibles a través de una serie de complementos, cada uno con propiedad de características. Puede configurar la propiedad features para habilitar o deshabilitar las distintas funciones de cada complemento.

Para obtener configuraciones detalladas de los complementos RTE, consulte [cómo activar y configurar los complementos RTE](/help/sites-administering/configure-rich-text-editor-plug-ins.md).

Descargue esta configuración de ejemplo para comprender cómo configurar RTE. En este paquete todas las funciones están habilitadas.

[Obtener archivo](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>La variable [Componente de texto de los componentes principales](https://helpx.adobe.com/experience-manager/core-components/using/text.html) permite a los editores de plantillas configurar muchos complementos RTE en la interfaz de usuario como políticas de contenido, lo que elimina la necesidad de una configuración técnica. Las políticas de contenido pueden funcionar con las configuraciones de la interfaz de usuario de RTE como se describe. Para obtener más información, consulte la [Configuración de la interfaz de usuario de RTE y políticas de contenido](/help/sites-administering/rich-text-editor.md#rtecontentpolicies), [Crear plantillas de página](/help/sites-authoring/templates.md)y [Documentación para desarrolladores de componentes principales](https://helpx.adobe.com/experience-manager/core-components/using/developing.html).

>[!NOTE]
>
>Para fines de referencia, los componentes de texto predeterminados (entregados como parte de una instalación estándar) se pueden encontrar en:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>Para crear su propio componente de texto, copie el componente anterior en lugar de editar estos componentes.

## Configurar la barra de herramientas RTE {#dialogfullscreen}

AEM le permite configurar la IU del Editor de texto enriquecido de forma diferente para los distintos modos de edición. A continuación se proporciona la configuración predeterminada. Puede anular estos valores predeterminados según sus necesidades.

Para obtener la mejor experiencia de creación:

* En un cuadro de diálogo flotante, habilite solo los complementos que no tengan una ventana emergente, ya que el cuadro de diálogo flotante es de menor tamaño.
* En el cuadro de diálogo de pantalla completa, habilite todos los complementos necesarios, incluso los complementos con ventanas emergentes más grandes, como el `Paste` complemento. Utilice la variable `dialogFullScreen` configuración descrita a continuación.

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

Para el modo en línea y el modo de pantalla completa se usan distintas configuraciones de interfaz de usuario. La propiedad toolbar se utiliza para especificar los botones de la barra de herramientas. Por ejemplo, si el botón es en sí mismo una función (por ejemplo, `Bold`), se especifica como `PluginName#FeatureName` (por ejemplo, `links#modifylink`). Si el botón es una ventana emergente (que contiene algunas características de un complemento), se especifica como `#PluginName` (por ejemplo, `#format`). Separadores ( | ) entre un grupo de botones se puede especificar con &quot;-&quot;.

El nodo emergente en modo en línea o en pantalla completa contiene una lista de las ventanas emergentes que se utilizan. Cada nodo secundario debajo de `popovers` el nodo recibe el nombre del complemento (por ejemplo, `format`). Tiene una propiedad `items` que contiene una lista de funciones del complemento (por ejemplo, `format#bold`).

## Configuración de la interfaz de usuario RTE y políticas de contenido {#rtecontentpolicies}

Los administradores pueden controlar las opciones de RTE mediante políticas de contenido, por ejemplo, en lugar de realizar la configuración como se ha descrito anteriormente. Las políticas de contenido definen las propiedades de diseño de un componente cuando se utilizan como parte de un [plantilla editable](../sites-authoring/templates.md). Por ejemplo, si se utiliza un componente de texto que utilice el editor de texto enriquecido con una plantilla editable, la política de contenido puede definir que la opción en negrita esté disponible y que haya algunas opciones de formato de párrafo disponibles. Las políticas de contenido se pueden reutilizar y se pueden aplicar en varias plantillas.

A partir de AEM 6.4 Service Pack 3, las opciones disponibles en el flujo RTE descendente desde las configuraciones de interfaz de usuario a las políticas de contenido.

* Los ajustes de configuración de la interfaz de usuario definen qué opciones están disponibles para las políticas de contenido.
* Si la configuración de la interfaz de usuario del RTE se ha eliminado o no permite un elemento, la directiva de contenido no puede configurarlo.
* Un autor solo tiene acceso a las funciones que están disponibles en las configuraciones de interfaz de usuario y en las políticas de contenido.

A modo de ejemplo, puede ver la variable [Documentación del componente principal de texto](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor).

## Personalización de la asignación entre iconos y comandos de la barra de herramientas {#iconstoolbar}

Puede personalizar la asignación entre los iconos de Coral que se muestran en la barra de herramientas de RTE y los comandos disponibles. No puede utilizar ningún otro icono aparte de los iconos de Coral.

1. Creación de un nodo denominado `icons` under `uiSettings/cui`.

1. Cree nodos para iconos individuales debajo de él.
1. En cada uno de los nodos de icono individuales, especifique un icono de Coral y un comando para asignarlo al icono.

A continuación se muestra un fragmento de ejemplo para asignar el comando Bold al icono Coral llamado `textItalic`.

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

En una página, puede incluir la clientlib CoralUI 2 RTE o la clientlib CoralUI 3 RTE . De forma predeterminada, el Editor de texto enriquecido incluye la clientlib CoralUI 3 RTE. Para cambiar a CoralUI 2 RTE, realice los siguientes pasos.

>[!NOTE]
>
>Adobe no recomienda el cambio como práctica recomendada. Cambie a CoralUI 2 RTE como último recurso. Los complementos personalizados para CoralUI 2 RTE funcionan con CoralUI 3 RTE si los complementos no dependen de elementos internos de RTE, como clases. Si utiliza complementos personalizados para CoralUI 3 RTE, utilice `rte.coralui3` biblioteca.

1. Superposición del nodo `/libs/cq/gui/components/authoring/editors/clientlibs/core` under `/apps`y haga lo siguiente:

   * Reemplazar `rte.coralui3` con `rte.coralui2` para la propiedad dependencias.
   * Reemplazar `cq.authoring.editor.core.inlineediting.rte.coralui3` con `cq.authoring.editor.core.inlineediting.rte.coralui2` para la propiedad embed .
   * Reemplazar `cq.authoring.rte.coralui3` con `cq.authoring.rte.coralui2` para la propiedad embed .

1. Superponer los nodos `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` y `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` under `/apps`.

   Quitar categoría `cq.authoring.dialog` from `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` y agréguelo a `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Cambiar cualquier otra dependencia que se incluya en la página de `rte.coralui3` a `rte.coralui2`. Por ejemplo, después de superponer el nodo `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` under `/apps`, cambie cualquier dependencia de `rte.coralui3` a `rte.coralui2`.

1. Superposición del nodo `cq/ui/widgets` under `/apps`. Reemplazar la dependencia `cq.rte` en el nodo `/apps/cq/ui/widgets` con `cq.coralui2.rte`.

>[!NOTE]
>
>CoralUI 2 RTE utiliza plantillas de controladores para los cuadros de diálogo de los complementos. Por lo tanto, la clientlib RTE de CoralUI 2 tenía una dependencia de la clientlib de controladores. CoralUI 3 RTE no utiliza plantillas de controladores y no tiene ninguna dependencia asociada. Si los complementos personalizados utilizan plantillas de controladores, incluya la clientlib de controladores en la página web.

## Información adicional {#further-information}

Para obtener más información sobre la configuración de RTE, consulte la [API de utilidades AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) referencia.

En concreto, para ver los complementos y las opciones relacionadas disponibles:

* La variable [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) proporciona un campo de formulario para editar información de texto con estilo (texto enriquecido). Para conocer todos los parámetros disponibles para el formulario de texto enriquecido, consulte las Opciones de configuración.
* El componente Texto enriquecido proporciona una amplia gama de funciones utilizando complementos enumerados en [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Para cada complemento:

   * Consulte las Funciones para obtener detalles sobre la funcionalidad que se puede habilitar (o deshabilitar).
   * Consulte las Opciones de configuración para ver todos los parámetros disponibles para una configuración detallada del complemento adecuado.

* También hay disponible más información sobre las reglas de HTML para los vínculos.

Las opciones anteriores pueden utilizarse para ampliar y personalizar su propio RTE. Por ejemplo, para enumerar los anclajes disponibles en la página al crear un vínculo, puede proporcionar su propia implementación de la variable `LinkPlugin`.

## Limitaciones conocidas {#known-limitations}

AEM capacidad RTE tiene las siguientes limitaciones:

* Las capacidades de RTE solo se admiten en los cuadros de diálogo de AEM componente. RTE no es compatible con asistentes o formularios base como [Propiedades de página](/help/sites-developing/page-properties-views.md) y [Andamiaje](/help/sites-authoring/scaffolding.md) en la IU táctil.

* AEM no funciona en [Dispositivos híbridos](/help/release-notes/known-issues.md).

* No asigne un nombre al nodo de configuración RTE `config`. De lo contrario, la configuración de RTE surte efecto solo para los administradores y no para los usuarios del grupo `content-author`.

* RTE no admite iframe o iframe en línea para incrustar contenido.

>[!MORELIKETHIS]
>
>* [Configuración de complementos RTE](configure-rich-text-editor-plug-ins.md)
>* [Usar el Editor de texto enriquecido para la creación](../sites-authoring/rich-text-editor.md)
>* [Configuración de RTE para sitios accesibles](rte-accessible-content.md)
>* [Paridad de características en la IU táctil y la IU clásica](../release-notes/touch-ui-features-status.md)
>* [Ejemplo de tutorial para crear un componente de varios campos compuesto](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

