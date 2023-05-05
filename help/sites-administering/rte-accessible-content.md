---
title: Configuración de RTE para producir sitios accesibles
seo-title: Configuring RTE for Producing Accessible Sites
description: Aprenda a configurar el Editor de texto enriquecido AEM para que produzca sitios accesibles.
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 2%

---

# Configuración de RTE para producir sitios accesibles {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM admite ambos:

* funciones de accesibilidad estándar, incluido texto alternativo para imágenes
* , así como funciones adicionales a las que se puede acceder al crear contenido con componentes que utilizan el editor de texto enriquecido (RTE)

>[!NOTE]
>
>* [Guía rápida de WCAG 2.0](/help/managing/qg-wcag.md)
>* [Creación de contenido accesible (conformidad con WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)


Los autores de contenido pueden utilizar las funciones de RTE para proporcionar información de accesibilidad al añadir contenido a una página. Esto puede incluir la adición de información estructural a través de encabezados y elementos de párrafo.

Puede [configurar y personalizar estas funciones configurando los complementos RTE](#configuring-the-plugin-features) para el componente. Por ejemplo, la variable `paraformat` complemento le permite añadir elementos semánticos de nivel de bloque adicionales, incluida la ampliación del número de niveles de encabezado admitidos más allá del `H1`, `H2` y `H3` proporcionado de forma predeterminada.

El RTE está disponible en una variedad de componentes tanto de la IU táctil como de la clásica. Sin embargo, el componente principal para utilizar RTE es el **Texto** componente.

La variable **Texto** en AEM está disponible tanto para las IU táctiles como para las clásicas. Las siguientes imágenes muestran el editor de texto enriquecido con una amplia gama de complementos habilitados, incluyendo `paraformat`:

* La variable **Texto** en la IU táctil:

   ![Componente de texto (RTE) en modo de pantalla completa en la IU táctil.](assets/chlimage_1-206.png)

* La variable **Texto** en la IU clásica:

   ![Cuadro de diálogo de edición (RTE) del componente de texto en la IU clásica.](assets/chlimage_1-207.png)

>[!NOTE]
>
>Existen diferencias entre las funciones de RTE disponibles en la IU clásica y la IU táctil. Para obtener más información, consulte
>
>* [Plugins y sus funciones](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Plugins y sus funciones: IU táctil](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## Configuración de las funciones del complemento {#configuring-the-plugin-features}

Las instrucciones completas sobre la configuración de RTE están disponibles en la [Configuración del Editor de texto enriquecido](/help/sites-administering/rich-text-editor.md) página. Esto cubre todos los problemas, incluidos los pasos clave:

* [Plugins y sus funciones](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Ubicaciones de configuración](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Activar un complemento y configurar la propiedad de funciones](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Configuración de otras funciones del RTE](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Configurando un complemento dentro de los `rtePlugins` subrama en CRXDE Lite (consulte la siguiente imagen), puede activar todas las funciones o características específicas para ese complemento.

![CRXDE Lite que muestra un ejemplo rtePlugin.](assets/chlimage_1-208.png)

### Ejemplo: Especificación de los formatos de párrafo disponibles en el campo de selección RTE {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Se pueden hacer disponibles nuevos formatos de bloque semántico para su selección mediante:

1. En función de su RTE, determine y vaya a la [ubicación de configuración](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Habilitar el campo de selección Párrafos](/help/sites-administering/rich-text-editor.md); por [activación del complemento](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Especifique los formatos que desea que estén disponibles en el campo de selección Párrafos](/help/sites-administering/rich-text-editor.md).
1. Los formatos de párrafo están disponibles para el autor de contenido desde los campos de selección en RTE. Se puede acceder a ellas:

   * Uso del párrafo ([pilcrow](https://en.wikipedia.org/wiki/Pilcrow)) en la IU táctil:

   ![Icono de párrafo (pilcrow).](do-not-localize/chlimage_1-7.png)

   * Al usar la variable **Formato** campo (selector desplegable) en la IU clásica.


Con los elementos estructurales disponibles en RTE a través de las opciones de formato de párrafo, AEM ofrece una buena base para el desarrollo de contenido accesible. Los autores de contenido no pueden usar el RTE para dar formato al tamaño de fuente o a los colores u otros atributos relacionados, lo que impide la creación de formato en línea. En su lugar, deben seleccionar los elementos estructurales adecuados, como encabezados y utilizar estilos globales elegidos en la opción Estilos. Esto garantiza una limpieza del marcado y buenas opciones para los usuarios que exploran con sus propias hojas de estilo y contenido correctamente estructurado.

## Uso de la función de edición de origen {#use-of-the-source-edit-feature}

En algunos casos, los autores de contenido encontrarán necesario examinar y ajustar el código fuente del HTML creado mediante RTE. Por ejemplo, un fragmento de contenido creado dentro de RTE puede requerir un marcado adicional para garantizar el cumplimiento de WCAG 2.0. Esto se puede hacer con la variable [editar fuente](/help/sites-administering/rich-text-editor.md#aboutplugins) de RTE. Puede especificar la variable [ `sourceedit` en la función `misctools` plugin](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Utilice la variable `sourceedit` con cuidado. Escribir errores o funciones no admitidas puede provocar más problemas.

## Agregar compatibilidad con elementos y atributos de HTML adicionales {#adding-support-for-additional-html-elements-and-attributes}

Para ampliar aún más las características de accesibilidad de AEM, es posible ampliar los componentes existentes basados en el RTE (como el **Texto** y **Tabla** componentes) con elementos y atributos adicionales.

El siguiente procedimiento ilustra cómo ampliar el **Tabla** componente con un **Pie de ilustración** elemento que proporciona información sobre una tabla de datos para los usuarios de tecnología de asistencia:

### Ejemplo: Adición del rótulo al cuadro de diálogo Propiedades de tabla {#example-adding-the-caption-to-the-table-properties-dialog}

En el constructor del `TablePropertiesDialog`, agregue un campo de entrada de texto adicional que se utilizará para editar el rótulo. Tenga en cuenta que `itemId` debe estar configurado como `caption` (es decir, el nombre del atributo DOM) para gestionar automáticamente su contenido.

En **Tabla** debe establecer o eliminar explícitamente el atributo en/desde el elemento DOM. El cuadro de diálogo pasa el valor en la variable `config` objeto. Tenga en cuenta que los atributos DOM deben configurarse o eliminarse utilizando la variable correspondiente `CQ.form.rte.Common` métodos ( `com` es un método abreviado para `CQ.form.rte.Common`) para evitar obstáculos comunes con las implementaciones de exploradores.

>[!NOTE]
>
>Este procedimiento solo es adecuado para la IU clásica.

### Instrucciones paso a paso {#step-by-step-instructions}

1. Iniciar CRXDE Lite. Por ejemplo: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   hasta:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Es posible que tenga que crear carpetas intermedias si no existen.

1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   hasta:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Abra el siguiente archivo para editarlo (ábralo con doble clic):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. En el `constructor` antes de la lectura de línea:

   ```
   var dialogRef = this;
   ```

   Agregue el siguiente código:

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

1. Agregue el siguiente código al final del `transferConfigToTable` método:

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

1. Guarde los cambios utilizando **Guardar todo**

>[!NOTE]
>
>Un campo de texto sin formato no es el único tipo de entrada permitido para el valor del elemento de rótulo. Cualquier utilidad ExtJS, que proporcione el valor del rótulo a través de su `getValue()` , se puede utilizar.
>
>Para añadir funciones de edición para otros elementos y atributos adicionales, asegúrese de que ambos:
>
>* La variable `itemId` para cada campo correspondiente se establece en el nombre del atributo DOM apropiado (`TablePropertiesDialog`).
>* El atributo se establece o elimina explícitamente en el elemento DOM (`Table`).

