---
title: Editor de texto enriquecido
seo-title: Editor de texto enriquecido
description: El editor de texto enriquecido es un bloque de creación básico para introducir contenido textual en AEM.
seo-description: El editor de texto enriquecido es un bloque de creación básico para introducir contenido textual en AEM.
uuid: 42001071-f7a7-475d-8aab-a8054303db68
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: adc697e1-4a1c-4985-8690-79ed77736fec
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '1814'
ht-degree: 90%

---


# Editor de texto enriquecido{#rich-text-editor}

El editor de texto enriquecido es un bloque de creación básico para introducir contenido textual en AEM. Constituye la base de diversos componentes, que incluyen:

* Texto
* Imagen de texto
* Tabla

## Editor de texto enriquecido {#rich-text-editor-2}

El cuadro de diálogo de edición WYSIWYG proporciona una amplia variedad de funcionalidades:

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>Las características disponibles pueden configurarse para proyectos individuales; por lo tanto, podrían variar para su instalación.

## Edición local {#in-place-editing}

Además del modo de edición de texto enriquecido basado en cuadros de diálogo, AEM también proporciona un modo de edición in situ, que permite la edición directa de texto tal y como aparece en el diseño de la página.

Haga clic dos veces en un párrafo (un doble clic lento) para entrar al modo de edición in situ (el borde del componente ahora estará de color naranja).

Podrá editar directamente el texto en la página, en vez de en el interior de una ventana de un cuadro de diálogo. Simplemente realice los cambios y se guardarán automáticamente.

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>Si tiene abierto el buscador de contenido, se mostrará una barra de herramientas con las opciones de formato RTE en la parte superior de la ficha (como se muestra arriba).
>
>Si el buscador de contenido no está abierto, no se mostrará la barra de herramientas.

Actualmente, el modo de edición directamente está habilitado para elementos de página generados por los componentes **Texto** y **Título**.

>[!NOTE]
>
>El componente **Título** está diseñado para contener texto corto sin saltos de línea. Cuando edite un título en modo de edición in situ, al especificar un salto de línea se abrirá un nuevo componente **Texto** debajo del título.

## Funciones del Editor de texto enriquecido {#features-of-the-rich-text-editor}

The Rich Text Editor provides a range of featues, these [depend on the configuration](/help/sites-administering/rich-text-editor.md) of the individual component. The features are available for both the touch-optimized and classic UI.

### Formatos de carácter básicos {#basic-character-formats}

![](do-not-localize/cq55_rte_basicchars.png)

Aquí puede aplicar formato a caracteres que ha seleccionado (resaltado); algunas opciones también tienen teclas de métodos abreviados.

* Negrita (Ctrl-B)
* Cursiva (Ctrl-I)
* Subrayado (Ctrl-U)
* Subíndice
* Superíndice

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

Todos funcionan como conmutadores; por lo tanto, si vuelve a seleccionar, se quita el formato.

### Formatos y estilos predefinidos {#predefined-styles-and-formats}

![cq55_rte_stylesparagraph](assets/cq55_rte_stylesparagraph.png)

Su instalación puede incluir estilos y formatos predefinidos. Están disponibles con las listas desplegables **Estilo** y **Formato**, y pueden aplicarse a texto seleccionado.

Se puede aplicar un estilo a una cadena específica (un estilo se correlaciona con CSS):

![cq55_rte_style_use](assets/cq55_rte_styles_use.png)

Mientras que se aplica un formato a todo el texto del párrafo (un formato está basado en HTML):

![cq55_rte_paragraph_use](assets/cq55_rte_paragraph_use.png)

Un formato específico puede cambiarse solamente (el valor predeterminado es **Párrafo**).

Se puede quitar un estilo; coloque el cursor dentro del texto al que se aplicó el estilo y haga clic en el icono Quitar:

>[!CAUTION]
>
>No vuelva a seleccionar realmente ninguna parte del texto al que se aplicó el estilo o el icono se desactivará.

### Cortar, copiar, pegar {#cut-copy-paste}

![](do-not-localize/cq55_rte_cutcopypaste.png)

Están disponibles las funciones estándar de **Cortar** y **Copiar**. Se proporcionan varias opciones de **Pegar** para adaptarse a los diferentes formatos.

* Cortar (**Ctrl-X**)
* Copiar (**Ctrl-C**)
* Pegar

   Este es el mecanismo de pegado predeterminado (**Ctrl-V**) para el componente; cuando se instala como viene de fábrica, está configurado para “Pegar desde Word”.

* Pegar como texto

   Quita todo estilo y formato para pegar únicamente texto sin formato.

* Pegar desde Word

   Pega el contenido como HTML (con algunas modificaciones de formato necesarias).

### Deshacer, Rehacer {#undo-redo}

![](do-not-localize/cq55_rte_undoredo.png)

AEM lleva un registro de las últimas 50 acciones realizadas en el componente actual en orden cronológico. Es posible deshacer estas acciones (y luego rehacerlas) en orden estricto si es necesario.

>[!CAUTION]
>
>El historial se conserva únicamente durante la sesión de edición actual. Se reinicia cada vez que se abre el componente para editar.

>[!NOTE]
>
>Cincuenta es el número predeterminado de tareas. Este valor puede variar en su instalación.

### Alineación {#alignment}

![](do-not-localize/cq55_rte_alignment.png)

El texto puede alinearse a la izquierda, al medio o a la derecha.

![cq55_rte_align_use](assets/cq55_rte_alignment_use.png)

### Sangría {#indentation}

![](do-not-localize/cq55_rte_indent.png)

Es posible aumentar o reducir la sangría de un párrafo. Se aplicará sangría al párrafo seleccionado, todo nuevo texto especificado retendrá el nivel de sangría actual.

![cq55_rte_indent_use](assets/cq55_rte_indent_use.png)

### Listas {#lists}

![](do-not-localize/cq55_rte_lists.png)

Dentro del texto pueden crearse tanto listas numeradas como listas con viñetas. Seleccione el tipo de lista y comience a escribir o resalte el texto que desee convertir. En ambos casos, un salto de línea generará un nuevo elemento de lista.

Pueden crearse listas anidadas aplicando sangría a uno o varios elementos de lista.

El estilo de una lista puede cambiar con solo colocar el cursor dentro de ella y luego seleccionar el otro estilo. Una sublista también puede tener un estilo diferente a la lista que la contiene. Este puede aplicarse una vez que se ha creado la sublista (mediante sangría).

![cq55_rte_listas_use](assets/cq55_rte_lists_use.png)

### Vínculos {#links}

![](do-not-localize/cq55_rte_links.png)

Un vínculo a una URL (ya sea dentro del sitio web o una ubicación externa) se genera al resaltar el texto requerido y luego hacer clic en el icono **Hipervínculo:**

![](do-not-localize/chlimage_1-12.png)

Un cuadro de diálogo permitirá especificar la URL de destino; también si debería abrirse en una nueva ventana.

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

Puede hacer lo siguiente:

* escribir un URI directamente
* usar el mapa del sitio para seleccionar una página dentro del sitio web
* escribir el URI y añadir el anclaje de destino; por ejemplo, `www.TargetUri.org#AnchorName`
* escribir un anclaje únicamente (para hacer referencia a &quot;la página actual&quot;); por ejemplo, `#anchor`
* buscar una página en el buscador de contenido, luego arrastrar y colocar el icono de página en el cuadro de diálogo Hipervínculo

>[!NOTE]
>
>El URI puede añadirse delante con cualquiera de los protocolos configurados para la instalación. In a standard installation these are `https://`, `ftp://`, and `mailto:`. Los protocolos que no estén configurados para la instalación serán rechazados y marcados como no válidos.


Para anular el vínculo, posicione el cursor en cualquier parte dentro del texto del vínculo y haga clic en el icono **Desvincular:**

![](do-not-localize/chlimage_1-13.png)

### Anclajes {#anchors}

![](do-not-localize/cq55_rte_anchor.png)

Se puede crear un anclaje en cualquier parte dentro del texto al posicionar el cursor o al seleccionar texto. A continuación, haga clic en el icono **Anclaje** para abrir el cuadro de diálogo.

Especifique el nombre del anclaje y haga clic en **Aceptar** para guardar.

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

El anclaje se muestra cuando se edita el componente y ahora se puede usar dentro de un destino para vínculos.

![chlimage_1-145](assets/chlimage_1-145.png)

### Buscar y reemplazar {#find-and-replace}

![](do-not-localize/cq55_rte_findreplace.png)

AEM contiene las funciones **Buscar** y **Reemplazar**.

Ambas tienen un botón **Buscar siguiente** para buscar el texto especificado en el componente abierto. También puede especificar si necesita que haya coincidencia con mayúsculas y minúsculas.

La búsqueda siempre comenzará desde la posición del cursor actual dentro del texto. Cuando se llegue al final del componente, un mensaje le informará de que la siguiente operación de búsqueda comenzará desde arriba.

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

La opción **Reemplazar** permite **Buscar** y luego **Reemplazar** una instancia individual con el texto especificado, o **Reemplazar todas** las instancias en el componente actual.

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png)

### Imágenes {#images}

Es posible arrastrar imágenes desde el buscador de contenido para agregarlas al texto.

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM también ofrece componentes especializados para una configuración de imagen más detallada. Por ejemplo, tiene a su disposición los componentes **Imagen** e **Imagen de texto.**

### Corrector ortográfico {#spelling-checker}

![](do-not-localize/cq55_rte_spellchecker.png)

La revisión ortográfica revisará todo el texto en el componente actual.

Los errores ortográficos quedarán resaltados:

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>La revisión ortográfica se realiza en el idioma del sitio web empleando la propiedad de idioma del subárbol o extrayendo el idioma de la URL. Por ejemplo, la rama `en` se revisa en inglés y la rama `de`, en alemán.

### Tablas {#tables}

Las tablas están disponibles tanto:

* Como el componente **Tabla**

   ![chlimage_1-146](assets/chlimage_1-146.png)

* Desde el componente **Texto**

   ![](do-not-localize/chlimage_1-14.png)

   >[!NOTE]
   >
   >Although tables are available in the RTE, it is recommended to use the **Table** component when creating tables.

En los componentes **Texto** y **Tabla**, la funcionalidad de tabla está disponible mediante el menú contextual (generalmente el botón derecho del ratón) donde se hace clic dentro de la tabla. Por ejemplo:

![cq55_rte_tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>En el componente **Tabla**, también hay disponible una barra de herramientas especializada, que incluye diversas funciones de editor de texto enriquecido estándar, junto con un subconjunto de las funciones específicas de las tablas.

Las funciones específicas de las tablas son:

<table> 
 <tbody> 
  <tr> 
   <td><a href="#table-properties">Propiedades de tabla</a><br /> </td> 
  </tr> 
  <tr> 
   <td><a href="#cell-properties">Propiedades de celda<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-rows">Agregar o eliminar filas<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-columns">Agregar o eliminar columnas<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#selecting-entire-rows-or-columns">Selección de filas o columnas enteras<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#merge-cells">Combinar celdas<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#split-cells">Dividir celdas<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#creating-nested-tables">Tablas anidadas</a></td> 
  </tr> 
  <tr> 
   <td><a href="#remove-table">Quitar tabla</a> </td> 
  </tr> 
 </tbody> 
</table>

#### Propiedades de tabla {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

Las propiedades básicas de la tabla pueden configurarse antes de hacer clic en **Aceptar** para guardar:

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **Anchura**

   La anchura total de la tabla.

* **Altura**

   La altura total de la tabla.

* **Borde**

   El tamaño del borde de la tabla.

* **Margen de celdas**

   Define el espacio en blanco entre el contenido de la celda y sus bordes.

* **Espaciado de celdas**

   Define la distancia entre las celdas.

>[!NOTE]
>
>La **Anchura**, **Altura** y ciertas propiedades de celda se pueden definir en:
>
>* píxeles
>* porcentajes


>[!CAUTION]
>
>Adobe recomienda enfáticamente definir la **anchura** de la tabla.

#### Propiedades de celda {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

Es posible configurar las propiedades de una celda específica o serie de celdas:

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **Ancho**
* **Altura**
* **Alineación horizontal** - Izquierda, Centro o Derecha
* **Alineación** vertical: superior, medio, inferior o de línea de base
* **Tipo** de celda: datos o encabezado
* **Aplicar a:**
   * Celda única
   * Toda la fila
   * Toda la columna

#### Agregar o eliminar filas {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

Las filas pueden agregarse encima o debajo de la fila actual.

También puede eliminarse la fila actual.

#### Agregar o eliminar columnas {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

Las columnas pueden agregarse a la izquierda o a la derecha de la columna actual.

También puede eliminarse la columna actual.

#### Selección de filas o columnas enteras {#selecting-entire-rows-or-columns}

![chlimage_1-147](assets/chlimage_1-147.png)

Selecciona toda la fila o columna actual. Hay acciones específicas (por ejemplo, combinar) disponibles.

#### Combinar celdas {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* Si seleccionó un grupo de celdas, puede combinarlas en una sola.
* Si tiene una sola celda seleccionada, puede combinarla con la celda ubicada a la derecha o debajo.

#### Dividir celdas {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

Seleccione una celda única para dividirla:

* Dividir una celda horizontalmente generará una nueva celda a la derecha de la celda actual, dentro de la columna actual.
* Dividir una celda verticalmente generará una nueva celda debajo de la celda actual, pero dentro de la fila actual.

#### Crear tablas anidadas {#creating-nested-tables}

![chlimage_1-148](assets/chlimage_1-148.png)

Crear una tabla anidada creará una nueva tabla autocontenida dentro de la celda actual.

>[!NOTE]
>
>El navegador determina cierto comportamiento adicional:
>
>* Windows IE: use Ctrl + clic con el botón principal del ratón (generalmente el izquierdo) para seleccionar varias celdas.
>* Firefox: arrastre el ratón para seleccionar un rango de celdas.

>



#### Quitar tabla {#remove-table}

![cq55_rte_removetable](assets/cq55_rte_removetable.png)

Esta acción quitará la tabla desde el interior del componente **Texto**.

### Caracteres especiales {#special-characters}

![](do-not-localize/cq55_rte_specialchars.png)

Se pueden hacer disponibles caracteres especiales para su editor de texto enriquecido, los cuales podrían variar con la instalación.

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

Coloque el puntero encima para ver una versión ampliada del carácter, y luego haga clic para incluirlo en la ubicación actual en el texto.

### Modo de edición de origen {#source-editing-mode}

![](do-not-localize/cq55_rte_sourceedit.png)

El modo de edición de fuente permite ver y editar el HTML subyacente del componente.

Por lo tanto, el texto:

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

Tendrá el siguiente aspecto en el modo de origen (a menudo el origen es mucho más largo, por lo que tendrá que desplazarse):

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>Cuando se sale del modo de origen, AEM hace ciertas comprobaciones de validación (por ejemplo, garantizar que el texto esté contenido o anidado correctamente en bloques). Esto puede generar cambios en sus modificaciones.

