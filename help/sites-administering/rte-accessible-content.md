---
title: Configuración de RTE para la producción de sitios accesibles
seo-title: Configuración de RTE para la producción de sitios accesibles
description: Obtenga información sobre cómo configurar el Editor de texto enriquecido AEM para crear sitios accesibles.
seo-description: Obtenga información sobre cómo configurar el Editor de texto enriquecido AEM para crear sitios accesibles.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Configuración de RTE para la producción de sitios accesibles {#configuring-rte-for-producing-accessible-sites}

AEM admite ambos:

* funciones de accesibilidad estándar, incluido texto alternativo para imágenes
* así como funciones adicionales a las que se puede acceder al crear contenido con componentes que utilizan el editor de texto enriquecido (RTE)

>[!NOTE]
>
>* [Guía rápida de WCAG 2.0](/help/managing/qg-wcag.md)
>* [Creación de contenido accesible (conformidad con WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)


Los autores de contenido pueden utilizar funciones de RTE para proporcionar información de accesibilidad al añadir contenido a una página. Esto puede incluir agregar información estructural a través de encabezados y elementos de párrafo.

Puede [configurar y personalizar estas características configurando los complementos RTE](#configuring-the-plugin-features) para el componente. Por ejemplo, el complemento `paraformat` permite agregar elementos semánticos de nivel de bloque adicionales, incluida la ampliación del número de niveles de encabezado admitidos más allá de los `H1`, `H2` y `H3` básicos proporcionados de manera predeterminada.

El RTE está disponible en una variedad de componentes, tanto de la IU táctil como de la clásica. Sin embargo, el componente principal para utilizar RTE es el componente **Texto**.

El componente **Texto** de AEM está disponible tanto para las IU táctiles como para las clásicas. Las siguientes imágenes muestran el editor de texto enriquecido con un rango de complementos habilitados, incluido `paraformat`:

* El componente **Texto** en la IU táctil:

   ![Componente de texto (RTE) en modo de pantalla completa en la IU táctil.](assets/chlimage_1-206.png)

* El componente **Texto** en la IU clásica:

   ![Cuadro de diálogo de edición (RTE) del componente de texto en la IU clásica.](assets/chlimage_1-207.png)

>[!NOTE]
>
>Existen diferencias entre las funciones RTE disponibles en la IU clásica y la IU táctil. Para obtener más información, consulte
>
>* [Complementos y sus funciones](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Complementos y sus funciones: IU táctil](/help/sites-administering/rich-text-editor.md#aboutplugins)

>



## Configuración de las características del complemento {#configuring-the-plugin-features}

Encontrará instrucciones completas sobre cómo configurar el editor de texto enriquecido en la página [Configuración del editor de texto enriquecido](/help/sites-administering/rich-text-editor.md). Esto abarca todos los problemas, incluidos los pasos clave:

* [Complementos y sus funciones](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Ubicaciones de configuración](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Activar un complemento y Configurar la propiedad de funciones](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Configuración de otra funcionalidad del RTE](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Al configurar un complemento dentro de la subrama `rtePlugins` apropiada en el CRXDE Lite (consulte la siguiente imagen), puede activar todas las características o específicas de ese complemento.

![CRXDE Lite que muestra un ejemplo de rtePlugin.](assets/chlimage_1-208.png)

### Ejemplo: Especificación de formatos de párrafo disponibles en el campo de selección RTE {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Los nuevos formatos de bloque semántico pueden estar disponibles para su selección mediante:

1. Según el RTE, determine y navegue a la [ubicación de configuración](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Habilite el campo](/help/sites-administering/rich-text-editor.md) de selección Párrafos; al  [activar el complemento](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Especifique los formatos que desea que estén disponibles en el campo](/help/sites-administering/rich-text-editor.md) de selección Párrafos.
1. Los formatos de párrafo están disponibles para el autor del contenido desde los campos de selección en RTE. Se puede acceder a ellos:

   * Con el icono de párrafo ([pilcrow](https://en.wikipedia.org/wiki/Pilcrow)) en la IU táctil:

   ![Icono de párrafo (pilcrow).](do-not-localize/chlimage_1-7.png)

   * Uso del campo **Formato** (selector desplegable) en la IU clásica.


Con los elementos estructurales disponibles en RTE mediante las opciones de formato de párrafo, AEM ofrece una buena base para el desarrollo de contenido accesible. Los autores de contenido no pueden utilizar RTE para dar formato al tamaño de fuente o a los colores u otros atributos relacionados, lo que impide la creación de formato en línea. En su lugar, deben seleccionar los elementos estructurales adecuados, como encabezados y utilizar estilos globales seleccionados en la opción Estilos. Esto garantiza la limpieza de las opciones de marcado buenas para los usuarios que exploran con sus propias hojas de estilo y contenido correctamente estructurado.

## Uso de la función de edición de origen {#use-of-the-source-edit-feature}

En algunos casos, los autores de contenido encontrarán necesario examinar y ajustar el código fuente HTML creado mediante RTE. Por ejemplo, un fragmento de contenido creado dentro del editor de texto enriquecido puede requerir un marcado adicional para garantizar el cumplimiento de WCAG 2.0. Esto se puede hacer con la opción [de edición de origen](/help/sites-administering/rich-text-editor.md#aboutplugins) de RTE. Puede especificar la función [ `sourceedit` en el complemento `misctools`](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Utilice la función `sourceedit` con cuidado. Los errores de escritura y/o las funciones no compatibles pueden provocar más problemas.

## Añadir compatibilidad con elementos y atributos HTML adicionales {#adding-support-for-additional-html-elements-and-attributes}

Para ampliar aún más las características de accesibilidad de AEM, es posible ampliar los componentes existentes basados en el RTE (como los componentes **Text** y **Table**) con elementos y atributos adicionales.

El siguiente procedimiento ilustra cómo extender el componente **Tabla** con un elemento **Rótulo** que proporciona información sobre una tabla de datos a los usuarios de tecnología de asistencia:

### Ejemplo: Añadir el rótulo al cuadro de diálogo Propiedades de tabla {#example-adding-the-caption-to-the-table-properties-dialog}

En el constructor de `TablePropertiesDialog`, agregue un campo de entrada de texto adicional que se utilice para editar el rótulo. Tenga en cuenta que `itemId` debe configurarse en `caption` (es decir, el nombre del atributo DOM) para administrar automáticamente su contenido.

En **Tabla** debe establecer o quitar explícitamente el atributo del elemento DOM. El valor se pasa por el cuadro de diálogo en el objeto `config`. Tenga en cuenta que los atributos DOM deben configurarse o eliminarse utilizando los métodos `CQ.form.rte.Common` correspondientes ( `com` es un método abreviado para `CQ.form.rte.Common`) a fin de evitar obstáculos comunes con las implementaciones del explorador.

>[!NOTE]
>
>Este procedimiento solo es adecuado para la IU clásica.

### Instrucciones paso a paso {#step-by-step-instructions}

1. Inicio CRXDE Lite. Por ejemplo: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   hasta:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Es posible que deba crear carpetas intermedias si no existen.

1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   hasta:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Abra el siguiente archivo para editarlo (ábralo con doble-clic):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. En el método `constructor`, antes de la lectura de la línea:

   ```
   var dialogRef = this;
   ```

   Añada el siguiente código:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Abra el siguiente archivo:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Añada el siguiente código al final del método `transferConfigToTable`:

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Guarde los cambios con **Guardar todo**

>[!NOTE]
>
>Un campo de texto sin formato no es el único tipo de entrada permitido para el valor del elemento de rótulo. Se puede utilizar cualquier utilidad ExtJS que proporcione el valor del rótulo a través de su método `getValue()`.
>
>Para agregar capacidades de edición para otros elementos y atributos adicionales, asegúrese de que ambos:
>
>* La propiedad `itemId` de cada campo correspondiente se establece en el nombre del atributo DOM correspondiente (`TablePropertiesDialog`).
>* El atributo se establece y/o elimina explícitamente en el elemento DOM (`Table`).

