---
title: Diseño
seo-title: Layout Design
description: Detalles del diseño explica cómo crear diseños para utilizarlos en sus cartas o comunicaciones interactivas.
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 94%

---

# Diseño {#layout-design}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las plantillas de formulario XFA o XDP permiten crear lo siguiente:

* [Cartas](/help/forms/using/create-letter.md)
* [Canal de impresión](/help/forms/using/web-channel-print-channel.md#printchannel) de [Interactive Communications](/help/forms/using/interactive-communications-overview.md)

* Fragmentos de diseños

Los XDP se diseñan en Adobe Forms Designer. Este artículo contiene detalles cómo diseñar los XDP para crear correspondencias/comunicaciones interactivas eficaces, como dónde utilizar los campos de formulario o las áreas de destino y cuándo usar fragmentos de diseño.

## Creación de un diseño para cartas o para el canal de impresión de Interactive Communications {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Un diseño define el diseño gráfico del canal de una carta o el canal de impresión de una comunicación interactiva. La presentación puede contener campos de formulario típicos, como &quot;Dirección&quot; y &quot;Número de referencia&quot;. También contiene subformularios vacíos que denotan áreas de destino. Cree el diseño en Forms Designer y, al terminar, el especialista en aplicaciones la cargará en un servidor de AEM. Desde allí, puede seleccionar el diseño al crear una plantilla de correspondencia o el canal de impresión de una comunicación interactiva.

![Designer: crear un diseño](assets/claimsubrogationlayout.png)

Siga estos pasos para crear diseños para cartas o el canal de impresión de Interactive Communications:

1. Analice el diseño y determine el contenido que se repite en todas las páginas; normalmente, el encabezado y pie de página pertenecen a esta categoría. Este contenido se coloca en las páginas maestras del diseño. El contenido restante se coloca en las páginas del cuerpo del diseño. En las disposiciones generales de una póliza, el logotipo y la dirección de la compañía se pueden agregar al encabezado y al pie de página de la página maestra. Por ejemplo, los avisos de cancelación utilizan el mismo diseño.
1. Al diseñar las páginas del cuerpo, divida el contenido de las páginas en secciones. Cada sección está diseñada como un subformulario incrustado en el propio diseño o como un diseño de fragmento. Si la sección contiene una tabla, modélela como un fragmento de diseño.
1. Un diseño se puede diseñar de la siguiente forma:

   1. Cree cada sección como un subformulario independiente que contenga todos los elementos de la sección.
   1. Diseñe cada subformulario de sección como secundario al mismo subformulario principal. El diseño del subformulario principal está establecido en una posición variable para permitir que las secciones se desplacen hacia abajo en el caso de que se combinen datos grandes en las secciones anteriores.
   1. La sección Domicilio habitual también se puede reutilizar en otros diseños. Créela como un diseño de fragmento.
   1. La sección Detalles de interés adicionales contiene únicamente dos elementos colocados uno debajo de otro, pueden contener datos grandes y se ha diseñado con una posición variable.
   1. Otras secciones contienen elementos en posiciones específicas, por lo que se crean como diseños de posición fija.
   1. Desglose las secciones en subformularios si contienen elementos con grandes cantidades de datos en posiciones específicas. A continuación, organice los subformularios para obtener el comportamiento deseado.
   1. Agregue un área objetivo de marcador de posición para la sección Domicilio habitual. Este marcador de posición está enlazado al fragmento Domicilio habitual cuando se diseña la carta o la comunicación interactiva.
   1. Cargue el diseño (y el fragmento, si lo hay, que utiliza el diseño) en el servidor de AEM Forms.

## Uso del esquema {#using-schema}

Puede utilizar un esquema en un diseño o un fragmento de diseño, pero no es obligatorio. Si utiliza un esquema, asegúrese de lo siguiente:

1. El diseño y todos los diseños de fragmento utilizados en una carta o comunicación interactiva utilizan el mismo esquema que la carta o la comunicación interactiva.
1. Todos los campos que deben rellenarse con datos están enlazados al esquema.

## Creación de campos relacionados {#creating-relatable-fields}

De forma predeterminada, todos los campos se consideran relacionados con otras fuentes de datos. Si la presentación contiene campos que no están relacionados con una fuente de datos, asigne un nombre al campo con el sufijo &quot;_int&quot; (interno); por ejemplo, pageCount_int.

Un campo relacionado debe:

* ser un &lt;field> o &lt;exclGroup> XFA
* tener una referencia de enlace XFA
* si es un &lt;exclGroup>, debe tener al menos un campo de botón de opción secundario; de lo contrario, no se puede terminar su tipo de valor

Un campo relacionado debe:

* tener un nombre

Un campo relacionado no debe:

* Incluir un sufijo &quot;_int&quot; en su nombre
* Tener el enlace establecido como &quot;ninguno&quot;
* Ser un elemento secundario de un elemento &lt;exclGroup>

Siempre que un campo relacionado cumpla los criterios descritos anteriormente, puede estar en cualquier ubicación y en cualquier profundidad de anidación del diseño. Puede utilizar campos relacionados en las páginas maestras.

Los campos son más flexibles en términos de configuración de diseño que los subformularios de área de destino; sin embargo, están vinculados a un solo tipo de valor. Puede aumentar el tamaño de un campo o establecerlo en una anchura y altura fijas, etc. El módulo o resultado de regla resuelto se inserta en el campo.

## Decidir cuándo usar subformularios y campos de texto {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Utilice un subformulario si desea capturar el contenido de varios módulos en un diseño vertical de flujo superior (varios párrafos o imágenes). El diseño debe controlar el hecho de que el subformulario aumenta en altura para ajustarse al contenido. Si no puede estar seguro de que la longitud del contenido asociado al subformulario o destino nunca va a exceder el espacio reservado para el subformulario en el diseño, cree el subformulario como elemento secundario en un contenedor de subformulario de posición variable. Este proceso garantiza que los objetos de diseño situados debajo del subformulario vayan desplazándose hacia abajo a medida que este crece.

Utilice un campo si desea capturar datos de módulo o datos de elementos del diccionario de datos en el esquema del diseño (porque los campos están enlazados a datos), o para mostrar el contenido del módulo en una página maestra. Recuerde que el contenido de una página maestra no puede desplazarse con el contenido de las páginas del cuerpo, por lo que debe asegurarse de que el campo de imagen se utiliza como logotipo de encabezado. Esta tabla proporciona más criterios para decidir cuándo utilizar un subformulario o un campo en un diseño.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Utilice un subformulario en los siguientes casos:</strong></p> </td> 
   <td><p><strong>Utilice un campo de texto en los siguientes casos:</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Si contiene una combinación de elementos, como el Apellido y el Nombre.</p> </td> 
   <td><p>Si contiene un solo elemento, como un Número de póliza.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Si incluye varios párrafos.</p> </td> 
   <td><p>El texto está ajustado y justificado.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Los grupos de datos repetidos, opcionales y condicionales están enlazados a subformularios para reducir el riesgo de que se produzcan errores de diseño en el caso de utilizar scripts para obtener los mismos resultados.</p> </td> 
   <td><p>Elementos como el logotipo y la dirección de su organización aparecen en todas las páginas de una carta o comunicación interactiva. En ese caso, cree campos de formulario para esos elementos y colóquelos en la página maestra. Si establece el enlace de campo en la opción "Sin enlace de datos", estos campos no aparecen como campos relacionados en el Editor de cartas/comunicaciones interactivas. Si desea relacionar algún tipo de contenido con estos campos, deben tener enlaces.</p> <p>Si la dirección de la compañía contiene más de una línea de datos, utilice el campo de texto con la opción "Permitir líneas múltiples" para representar la dirección en el diseño.</p> <p>Si el tipo de datos de un campo de texto está definido como texto sin formato, se utiliza la versión de texto sin formato de la salida del módulo en lugar de la versión de texto enriquecido (se descarta todo el formato). Para conservar el formato, establezca el tipo de datos del campo de texto en Texto enriquecido.</p> </td> 
  </tr> 
  <tr> 
   <td><p>El texto está en una posición variable</p> </td> 
   <td><p>Los campos de texto y los campos de imagen se utilizan en las páginas maestras. Las páginas maestras no pueden utilizar subformularios como áreas de destino.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Los objetos se agrupan y organizan sin enlazar el subformulario a un elemento de datos</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Hay un campo de texto dentro del subformulario. El subformulario puede crecer y no sobrescribir los objetos que aparecen debajo de él en el diseño.</p> </td> 
   <td><p>Necesita acceder fácilmente a los datos en el proceso de publicación.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuración de elementos repetidos {#setting-up-repetitive-elements}

Si algunos elementos, como el logotipo y la dirección de su organización, aparecen en todas las páginas de una carta o comunicación interactiva, cree campos de formulario para esos elementos y colóquelos en la página maestra. Utilice el enlace Nombre (Nombre de campo) para estos campos.

## Especificar el formato de renderización del servidor {#specify-the-server-nbsp-render-format}

Utilice el formato de renderización del servidor del diseño en Formulario XML dinámico; de lo contrario, las cartas o comunicaciones interactivas basadas en este diseño no se podrán procesar correctamente. De forma predeterminada, el formato de renderización del servidor de Forms Designer está establecido en Formulario XML dinámico. Para asegurarse de que está utilizando el formato correcto:

* En Designer, haga clic en **[!UICONTROL Archivo > Propiedades del formulario > Predeterminado]** y asegúrese de que la configuración Representación/Formato del PDF está establecida en Formulario XML dinámico.
