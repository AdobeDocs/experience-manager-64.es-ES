---
title: Diseño
seo-title: Layout Design
description: Diseño Detalles del diseño del diseño explica cómo crear diseños para utilizarlos en sus cartas o comunicaciones interactivas.
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 0%

---

# Diseño {#layout-design}

Las plantillas de formulario XFA o XDP son las plantillas para:

* [Cartas](/help/forms/using/create-letter.md)
* [Canal de impresión](/help/forms/using/web-channel-print-channel.md#printchannel) de [Comunicaciones interactivas](/help/forms/using/interactive-communications-overview.md)

* Fragmentos de diseños

Un XDP está diseñado en Adobe Forms Designer. En este artículo se explica cómo diseñar los XDP para crear correspondencias/comunicaciones interactivas eficaces, como dónde utilizar los campos de formulario o las áreas de destino y cuándo utilizar los fragmentos de diseño.

## Creación de un diseño para letras o para el canal de impresión de Interactive Communications {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Un diseño define el diseño gráfico de un canal de letra/impresión de una comunicación interactiva. La presentación puede contener campos de formulario típicos, como &quot;Dirección&quot; y &quot;Número de referencia&quot;. También contiene subformularios vacíos que denotan áreas de destino. Cree la presentación en el diseñador de formularios y cuando termine, el especialista en aplicaciones la cargará en AEM servidor. Desde allí, puede seleccionar el diseño al crear una plantilla de correspondencia o un canal de impresión de una comunicación interactiva.

![Designer: crear un diseño](assets/claimsubrogationlayout.png)

Siga estos pasos para crear diseños para cartas/canal de impresión de Interactive Communications:

1. Analice el diseño y determine el contenido que se repite en todas las páginas; normalmente, el encabezado y pie de página se ajustan a esta categoría. Este contenido se coloca en páginas de formato de diseño. El contenido restante se dirige a las páginas de trabajo del diseño. En una chaqueta de directiva, el logotipo y la dirección de la empresa se pueden agregar al encabezado y al pie de página de la página de formato. Por ejemplo, el Aviso de cancelación utiliza el mismo diseño.
1. Al diseñar páginas de trabajo, divida el contenido de la página en secciones. Cada sección está diseñada como un subformulario incrustado en la propia presentación o como una presentación de fragmento. Si la sección contiene tabla, modele la sección como un fragmento de diseño.
1. Un diseño se puede diseñar de la siguiente manera:

   1. Consiga que cada sección sea un subformulario independiente que contenga todos los elementos de la sección.
   1. Hacer que cada subformulario de sección sea secundario al mismo subformulario principal. La presentación del subformulario principal está definida en posición variable para permitir que las secciones se desplazen por debajo en caso de que los datos grandes se combinen en secciones anteriores.
   1. La residencia principal de la sección también se puede reutilizar en otros diseños. Crearla como un diseño de fragmento.
   1. Sección Los detalles de interés adicionales contienen solo dos elementos colocados uno debajo de otro, pueden contener datos grandes y están diseñados de la forma fluida.
   1. Otras secciones contienen elementos en posiciones específicas, por lo que están diseñados como diseño en posición fija.
   1. Desglose una sección en subformularios si la sección contiene elementos en posiciones específicas y estos elementos contienen grandes cantidades de datos. A continuación, organice los subformularios para lograr el comportamiento deseado.
   1. Para la sección Residencia principal , agregue un área objetivo de marcador de posición. Este marcador de posición está enlazado a la residencia principal del fragmento en el momento del diseño de la carta/comunicación interactiva.
   1. Cargue el diseño (y el fragmento, si lo hay, que utiliza el diseño) en el servidor de AEM Forms.

## Uso del esquema {#using-schema}

Puede utilizar un esquema en un fragmento de diseño o diseño , pero no es obligatorio. Si utiliza un esquema, asegúrese de lo siguiente:

1. El diseño y todos los diseños de fragmento utilizados en una carta/comunicación interactiva utilizan el mismo esquema que la letra/comunicación interactiva.
1. Todos los campos necesarios para rellenarse con datos están enlazados al esquema.

## Creación de campos relacionados {#creating-relatable-fields}

De forma predeterminada, todos los campos se consideran relacionados con otras fuentes de datos. Si la presentación contiene campos que no están relacionados con una fuente de datos, asigne un nombre al campo con un sufijo &quot;_int&quot; (interno); por ejemplo, pageCount_int.

Un campo relacionado debe:

* ser XFA &lt;field> o &lt;exclgroup>
* tienen una referencia de enlace XFA
* si es un &lt;exclgroup>, debe tener al menos un campo de botón de radio secundario; de lo contrario, su tipo de valor no se puede determinar

Un campo relacionado debe:

* tienen un nombre

Un campo relacionado no debe:

* Incluir un sufijo &quot;_int&quot; en su nombre
* tienen el enlace establecido como &quot;ninguno&quot;
* ser hijo de un &lt;exclgroup> element

Siempre que un campo relacionado cumpla los criterios descritos anteriormente, puede estar en cualquier ubicación y en cualquier profundidad de anidación en el diseño. Puede utilizar campos relacionados dentro de las páginas de formato.

Los campos son más flexibles en la configuración de presentación que los subformularios de área de destino; sin embargo, están unidos a un solo tipo de valor. Puede hacer que un campo sea grande o establecerlo en una anchura y altura fijas, etc. El módulo o resultado de regla resuelto se inserta en el campo .

## Decidir cuándo usar subformularios y campos de texto {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Utilice un subformulario si desea capturar contenido de varios módulos en una presentación vertical de flujo superior (varios párrafos o imágenes). La presentación debe controlar el hecho de que el subformulario crece en altura para ajustarse a su contenido. Si no puede estar seguro de que la longitud del contenido asociado al subformulario o destino nunca exceda el espacio reservado para el subformulario en la presentación, cree el subformulario como secundario dentro de un contenedor de subformulario de posición variable. Este proceso garantiza que los objetos de presentación situados debajo del subformulario vayan descendiendo a medida que crezca el subformulario.

Utilice un campo si desea capturar datos de módulo o datos de elementos del diccionario de datos en el esquema del diseño (porque los campos están enlazados a datos) o para mostrar el contenido del módulo en una página de formato. Recuerde que el contenido de una página de formato no puede fluir con el contenido de la página de trabajo, por lo que debe asegurarse de que el campo de imagen se utilice como logotipo de encabezado. Esta tabla proporciona más criterios para decidir cuándo utilizar un subformulario o un campo en una presentación.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Utilizar un subformulario cuando</strong></p> </td> 
   <td><p><strong>Utilizar un campo de texto cuando</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Contiene una combinación de elementos, como un apellido y un nombre</p> </td> 
   <td><p>Contiene un solo elemento, como un número de directiva.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Incluye varios párrafos</p> </td> 
   <td><p>El texto está ajustado y justificado</p> </td> 
  </tr> 
  <tr> 
   <td><p>Los grupos de datos repetitivos, opcionales y condicionales están enlazados a subformularios para reducir el riesgo de errores de diseño que podrían producirse si se utilizan secuencias de comandos para obtener los mismos resultados</p> </td> 
   <td><p>Los elementos como el logotipo y la dirección de su organización aparecen en todas las páginas de una carta o comunicación interactiva. En este caso, cree campos de formulario para esos elementos y colóquelos en la página de formato. Si establece el enlace de campo en "Sin enlace de datos", los campos no aparecen como campos relacionados en el Editor de cartas/comunicaciones interactivas. Si desea relacionar algún tipo de contenido con estos campos, deben tener enlaces.</p> <p>Si la dirección de la empresa contiene más de una línea de datos, utilice el campo de texto con la opción "Permitir líneas múltiples" para representar la dirección de la presentación.</p> <p>Si el tipo de datos de un campo de texto está definido como texto sin formato, se utiliza la versión de texto sin formato de la salida del módulo en lugar de la versión de texto enriquecido (se descarta todo el formato). Para conservar el formato, establezca el tipo de datos del campo de texto en texto enriquecido.</p> </td> 
  </tr> 
  <tr> 
   <td><p>El texto tiene posición variable</p> </td> 
   <td><p>Los campos de texto y los campos de imagen se utilizan en las páginas de formato. Las páginas de formato no pueden utilizar subformularios como áreas de destino.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Los objetos se agrupan y organizan sin enlazar el subformulario a un elemento de datos</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Hay un campo de texto dentro del subformulario. El subformulario puede crecer y no sobrescribir otros objetos debajo de él en la presentación.</p> </td> 
   <td><p>Necesita un acceso fácil a sus datos en el proceso posterior.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuración de elementos repetitivos {#setting-up-repetitive-elements}

Cuando elementos como el logotipo y la dirección de su organización aparezcan en todas las páginas de una carta o comunicación interactiva, cree campos de formulario para esos elementos y colóquelos en la página de formato. Utilice el enlace Nombre (Nombre de campo) para estos campos.

## Especificar el formato de renderización del servidor {#specify-the-server-nbsp-render-format}

Utilizar el formato de renderización del servidor de la presentación en Formulario XML dinámico; de lo contrario, las letras o comunicaciones interactivas basadas en este diseño no se pueden procesar correctamente. De forma predeterminada, el formato de renderización del servidor en Forms Designer está definido como Formulario XML dinámico. Para asegurarse de que está utilizando el formato correcto:

* En Designer, haga clic en **[!UICONTROL Archivo > Propiedades del formulario > Predeterminado]** y asegúrese de que la configuración Representación/Formato del PDF está establecida en Formulario XML dinámico.
