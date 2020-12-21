---
title: Uso de gráficos en Interactive Communications
seo-title: Componente de gráfico en Interactive Communications
description: 'Mediante los gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender  '
seo-description: AEM Forms proporciona un componente de gráfico que puede utilizar para crear gráficos en la comunicación interactiva. Este documento explica las configuraciones básicas y de agente del componente de gráfico.
uuid: dedd670c-030b-4497-bbcb-3ad935cebcda
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 16c7e698-258d-4e63-9828-f538dc7d3294
translation-type: tm+mt
source-git-commit: f86765084981cda1e255834bf83be0ff8a7a2a02
workflow-type: tm+mt
source-wordcount: '2423'
ht-degree: 0%

---


# Uso de gráficos en Interactive Communications {#using-charts-in-interactive-communications}

Mediante los gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender

Un gráfico o un gráfico es una representación visual de los datos. Condensa grandes cantidades de información en un formato visual fácil de entender, lo que permite que los destinatarios de la Comunicación interactiva visualicen, interpreten y analicen mejor los datos complejos.

Al crear una comunicación interactiva, puede agregar gráficos para representar visualmente datos bidimensionales del modelo de datos de formulario de la comunicación interactiva. El componente Gráfico permite agregar y configurar los siguientes tipos de gráficos:

* Circular
* Columna
* Gráfico de sectores
* Barra (solo canal web)
* Línea
* Línea y punto
* Punto
* Área

## Añadir y configurar gráficos en una comunicación interactiva {#add-and-configure-chart-in-an-interactive-communication}

Complete los siguientes pasos para agregar un gráfico a una comunicación interactiva:

1. En la barra lateral de componentes, arrastre y suelte el componente Gráfico en una de las siguientes opciones de impresión o canal web de una comunicación interactiva:

   * Canal de impresión: Área de destinatario y campo Imagen
   * Canal web: Área de panel y Destinatario

   El componente Gráfico colocado crea un marcador de posición para un gráfico.

1. Toque el componente de gráfico en el editor de Comunicación interactiva y, en la barra de herramientas Componente, seleccione **[!UICONTROL Configurar (]** ![configurar_icono](assets/configure_icon.png)).

   La barra lateral de propiedades aparece con las propiedades básicas del gráfico en el foco.

   ![Propiedades básicas de un gráfico de tipo de línea en el canal de impresión](assets/chart_basicproperties.png)
   **Figura:Propiedades** *básicas de un gráfico de tipo de línea en el canal de impresión*

   ![Propiedades básicas de un gráfico de tipo de línea en el canal web](assets/basicpropertieswebchannel.png)
   **Figura:Propiedades** *básicas de un gráfico de tipos de línea en el canal web*

1. Configure las propiedades básicas del gráfico para el canal de impresión y el canal web. Aparte de las propiedades comunes, existen propiedades específicas de impresión y canal web y del tipo de gráfico.

   * **[!UICONTROL Nombre]**: Nombre del objeto de gráfico. El nombre del gráfico que especifique aquí no aparece en el resultado del gráfico, sino que se utiliza en las reglas para hacer referencia al gráfico.
   * **[!UICONTROL Tipo]** de gráfico: Especifique el tipo de gráfico: Circular, Columna, Tono, Línea, Línea y Punto, Punto o Área.
   * **[!UICONTROL Ocultar objeto]**: Seleccione esta opción para ocultar el gráfico en el resultado final.
   * Especifique lo siguiente para **[!UICONTROL eje x]** y **[!UICONTROL eje y]**:

      * **[!UICONTROL Título]**: Especifique los títulos de los ejes X e Y que se mostrarán en la Comunicación interactiva.
      * **[!UICONTROL Objeto del modelo de datos *]**: Examine y seleccione los objetos del modelo de datos para los ejes X e Y del gráfico desde el modelo de datos de formulario especificado al crear la comunicación interactiva. Elija dos propiedades de colección/tipo de matriz del mismo objeto del modelo de datos principal que sean significativas en relación mutua para trazar en los ejes X e Y de un gráfico.
      * **[!UICONTROL Función]**: Para utilizar funciones estadísticas para calcular los valores en el eje, seleccione una función para el eje X / Y. Para obtener más información sobre las funciones, consulte [Utilizar funciones en el gráfico](#usefunction) y [Ejemplo 2: Aplicación de funciones de suma y media en un gráfico de líneas](#applicationsumfrequency).

   >[!NOTE]
   >
   >En el caso del canal de impresión, en el eje X, el objeto del modelo de datos que se enlace debe ser de tipo Número, Cadena o Fecha. En el eje Y, el objeto del modelo de datos que se enlace debe ser del tipo Número. Se recomienda utilizar la leyenda del lado derecho en el canal de impresión.

   Para obtener más información sobre las propiedades del gráfico, consulte [Propiedades básicas en gráficos](#basicpropertiescharts).

1. (Solo canal de impresión) En Configuración del agente, especifique si es obligatorio que el agente utilice este gráfico. Si la opción i **[!UICONTROL t es obligatoria para que el agente utilice este gráfico]** no está seleccionada, el agente puede tocar el icono de ojo del gráfico en la ficha Contenido de la interfaz de usuario del agente para mostrar u ocultar el gráfico.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. En la barra lateral Propiedades, toque ![done_icon](assets/done_icon.png).

   Previsualización para ver el aspecto y los datos del gráfico. Vuelva para volver a configurar las propiedades del gráfico, si es necesario.

1. Vuelva a realizar otros cambios en la Comunicación interactiva.

## Ejemplo 1: Salida de gráfico en impresión y Web {#chartoutputprintweb}

En la ficha Básico, se define el tipo de gráfico, las propiedades del modelo de datos del formulario de origen que contienen datos, las etiquetas que se van a trazar en los ejes X e Y del gráfico y, opcionalmente, la función estadística para calcular los valores para trazar en el gráfico.

Comprendamos en detalle la información mínima requerida en las propiedades básicas, con la ayuda de un extracto de tarjeta de crédito generado mediante una comunicación interactiva. Considere que desea generar un gráfico que muestre la cantidad de gastos diferentes en el estado. Desea utilizar diferentes tipos de gráficos para impresión y salida web de la Comunicación interactiva.

Para lograrlo, debe especificar:

* **[!UICONTROL Tipo]**  de gráfico: en este ejemplo, Columna para el canal de impresión y Salida para el canal web
* **[!UICONTROL Objetos del modelo de datos]** como origen para los ejes X e Y del gráfico; en este ejemplo, Importe de transacción para el eje X y Nombre de gasto para el eje Y
* **** Título para los ejes X e Y (para el gráfico de tipo Columna en el canal de impresión solo en este ejemplo): en este ejemplo, Importe ($) para el eje X y Gasto para el eje Y.
* **[!UICONTROL Dirección]**  de etiqueta (para el gráfico de tipo Columna en el canal de impresión solo en este ejemplo): en este ejemplo  `Tilt Left`

* **** Herramienta para mostrar al pasar el ratón sobre un gasto (solo canal web); en este ejemplo  `${x}: $ ${y}`, que se muestra como  `[Expense Label: $ Amount]` (Ejemplo: Visita al parque temático: 315 $)

![Gráfico de columnas en la salida de impresión de una ](assets/chartprintchannel.png)
**comunicación interactivaFigura:Gráfico de** *columnas en la salida de impresión de una comunicación interactiva*

**Eje A.** Y: cantidad recuperada de la propiedad del modelo de datos del formulario y la propiedad Title establecida en Amount ($)  **B.** Label Dirección del eje X definido en Tilt Left Eje  **C.** X - Descripción de gastos recuperada de la propiedad del modelo de datos del formulario y propiedad Title establecida en Cost

![Gráfico circular en la salida web de una ](assets/chartwebchannel.png)
**comunicación interactivaFigura:** *Gráfico circular en la salida web de una comunicación interactiva*

**A.** Inner Radius property of the donut is set  **B.** Show Legend property is selected and Legend Position property is set to Right  **C.** Tooltip muestra el detalle del elemento al pasar el ratón sobre - Tooltip está establecido en ${x}: $ ${y}

## Ejemplo 2: Aplicación de las funciones Suma y Frecuencia en un gráfico de líneas {#applicationsumfrequency}

Mediante la aplicación de funciones en un gráfico, puede trazar datos que el modelo de datos de formulario no proporciona directamente. En este ejemplo, utilizamos un ejemplo de extracto de tarjeta de crédito para comprender cómo se pueden aplicar las funciones Suma y Frecuencia al gráfico.

![Gráfico de líneas sin función con tres ](assets/creditcarddatalinechartcopy.png)
**transacciones &quot;Bed and Breakfast&quot; Figura:** *Gráfico de líneas sin función con tres transacciones &quot;Bed and Breakfast&quot;*

### Función de suma {#sum-function}

Puede aplicar la función sum para agregar valores de varias instancias de la misma propiedad de datos y mostrarlos solo una vez. Por ejemplo: en el gráfico siguiente, la función Suma se aplica en el eje Y para sumar la cantidad de las tres transacciones de Bed and Breakfast (99,45 $, 78 $ y 12 $) y mostrar sólo una transacción (189,45 $).

La función Sum puede hacer que el gráfico sea más útil cuando se desea intercalar y mostrar la suma para muchas instancias de la misma propiedad de datos.

![creditcardchartsumfunctioncopy](assets/creditcardchartsumfunctioncopy.png)

### Función de frecuencia {#frequency-function}

La función Frecuencia devuelve el número de valores en el eje X o Y para un valor determinado en el otro eje. Con la aplicación de la función Frecuencia en el eje Y (Amount/TransAmount), el gráfico muestra que ha habido tres incidencias de transacciones de Bed and Breakfast y una incidencia del resto de tipos de transacciones.

![creditcardchartfreencifunction_copy](assets/creditcardchartfrequencyfunctioncopy.png)

## Propiedades básicas de los gráficos {#basicpropertiescharts}

En la ficha Básico, puede configurar las siguientes propiedades:

**** NombreIdentificador del elemento de gráfico. El nombre no está visible en el gráfico, pero ayuda a hacer referencia al elemento desde otros componentes, secuencias de comandos y expresiones SOM.

**Título (solo canal de impresión)** Especifica el título del gráfico.

**Tipo de** gráficoEspecifica el tipo de gráfico que desea generar. Las opciones disponibles son circular, columna, anillo, barra (solo canal web), línea, línea y punto, punto y área. Para obtener más información, consulte Ejemplo 1: Salida de gráfico en impresión y Web.

**Eje X >** TítuloEspecifica el título del eje X.

**Eje X > Objeto del modelo de datos &amp;último;** Especifique el nombre del elemento de recopilación del modelo de datos de formulario que se va a trazar en el eje X.

**Eje X >** FunciónEspecifica la función estadística/personalizada que se utilizará para calcular los valores en el eje X. Para obtener más información sobre las funciones, consulte Uso de funciones en el gráfico y Ejemplo 2: Aplicación de funciones de suma y media en un gráfico de líneas.

**Eje X >** Dirección de etiquetaDirección de la etiqueta del gráfico en el canal de impresión. Si elige la dirección de la etiqueta como Rotación personalizada, aparece el campo Ángulo de rotación personalizado (grados). En el campo Ángulo de rotación personalizado (grados), puede elegir un ángulo de rotación en pasos de 15 grados.

**Eje Y >** TítuloEspecifica el título del eje Y.

**Eje Y > Objeto del modelo de datos &amp;último;** Especifica el elemento de recopilación del modelo de datos de formulario que se va a trazar en el eje Y. En el canal Imprimir, el objeto del modelo de datos para el eje Y debe ser del tipo Número.

**Eje Y >** FunciónEspecifica la función estadística/personalizada que se utilizará para calcular los valores en el eje Y. Para obtener más información sobre las funciones, consulte Uso de funciones en el gráfico y Ejemplo 2: Aplicación de funciones de suma y media en un gráfico de líneas.

**Mostrar** leyendaMuestra una leyenda para el gráfico circular o circular cuando está activada.

**Posición** de leyendaEspecifica la posición de la leyenda con respecto al gráfico. Las opciones disponibles son Derecha, Izquierda, Superior e Inferior.

**Altura (solo canal de impresión)** Altura del gráfico en píxeles.

**Anchura (solo canal de impresión)** Anchura del gráfico en píxeles.

>[!NOTE]
>
>Puede controlar la anchura del gráfico en el canal web con la capa de estilo o aplicando un tema.

**Información del objeto (solo canal web)**  Especifica el formato en el que aparece la información del objeto al pasar el ratón sobre un punto de datos en el gráfico del canal web. El valor predeterminado es \${x}(\${y}). Según el tipo de gráfico, cuando se señala el ratón en un punto, una barra o una fracción del gráfico, las variables \${x} y \${y} se reemplazan dinámicamente con los valores correspondientes en los ejes X e Y y y se muestran en la información del objeto.

Para desactivar la información del objeto, deje el campo Información del objeto en blanco. Esta opción no se aplica a los gráficos de líneas y áreas. Por ejemplo, consulte [Ejemplo 1: Salida de gráfico en impresión y Web](#chartoutputprintweb).

**Clase CSS (solo canal Web)** Especifique el nombre de una clase CSS en el campo de clase CSS para aplicar estilo personalizado al gráfico.

**Salto de página obligatorio antes (solo canal de impresión)** Seleccione esta opción para agregar un salto de página obligatorio antes del gráfico y colocar el gráfico en la parte superior de una nueva página.

**Salto de página obligatorio después de (solo canal de impresión)** Seleccione esta opción para agregar un salto de página obligatorio después del gráfico y coloque el contenido siguiente al gráfico en la parte superior de una nueva página.

**Sangría (solo canal de impresión)** Especifique la sangría del gráfico desde la izquierda de la página.

**Configuraciones específicas del gráficoAdemás de las configuraciones comunes, están disponibles las siguientes configuraciones específicas del gráfico:** 

* **Radio interior**: disponible para gráficos circulares para especificar el radio (en píxeles) del círculo interior del gráfico.
* **Color** de línea: disponible para gráficos de líneas, líneas y puntos, y de áreas para especificar el valor hexadecimal del color de la línea en el gráfico.
* **Color** del punto: disponible para gráficos de puntos y líneas y puntos para especificar el valor hexadecimal del color de los puntos del gráfico.

* **Color** de área: disponible para gráficos de área para especificar el valor hexadecimal del color para el área bajo la línea en el gráfico.

## Usar funciones en el gráfico {#usefunction}

Puede configurar un gráfico para que utilice funciones estadísticas a fin de calcular los valores de los datos de origen para trazar en el gráfico. Mediante la aplicación de funciones en un gráfico, puede trazar datos que el modelo de datos de formulario no proporciona directamente.

Aunque el componente Gráfico incluye algunas funciones integradas, puede escribir sus propias funciones y hacerlas disponibles para su uso en la configuración de gráficos del canal Web.

![functionChart](assets/functionchart.png)

>[!NOTE]
>
>Puede utilizar funciones para calcular valores para ejes X o Y en un gráfico.

### Funciones predeterminadas {#default-functions}

Las siguientes funciones están disponibles de forma predeterminada con el componente Gráfico:

**Media (Promedio)** Devuelve la media de los valores en los ejes X o Y de un valor determinado en el otro eje.

**** SumaDevuelve la suma de todos los valores del eje X o Y para un valor determinado del otro eje.

**** MáximoDevuelve el máximo de los valores del eje X o Y para un valor determinado del otro eje.

**** FrecuenciaDevuelve el número de valores en el eje X o Y para un valor determinado en el otro eje.

**** IntervaloDevuelve la diferencia entre el máximo y el mínimo de los valores en los ejes X e Y para un valor determinado en el otro eje.

**** MedianaDevuelve el valor que separa los valores más altos e inferiores a la mitad en el eje X o Y para un valor determinado en el otro eje.

**** MínimoDevuelve el mínimo de los valores en los ejes X o Y para un valor determinado en el otro eje.

**** ModeDevuelve el valor con la mayor cantidad de incidencias en el eje X o Y de un valor determinado en el otro eje

### Funciones personalizadas en el canal web {#custom-functions-in-web-channel}

Además de utilizar las funciones predeterminadas en los gráficos, puede escribir funciones personalizadas en JavaScript™ y hacerlas disponibles en la lista de funciones en el componente Gráfico para el canal Web.

Una función toma una matriz o valores y un nombre de categoría como entradas y devuelve un valor. Por ejemplo:

```
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Una vez que haya escrito una función personalizada, haga lo siguiente para que esté disponible para su uso en la configuración del gráfico:

1. Añada la función personalizada en la biblioteca del cliente asociada a la comunicación interactiva pertinente. Para obtener más información, consulte [Configuración de la acción Enviar](/help/forms/using/configuring-submit-actions.md) y [Uso de bibliotecas del lado del cliente](/help/sites-developing/clientlibs.md).

1. Para mostrar la función personalizada en la lista desplegable Función, en CRXDe Lite, cree un nodo `nt:unstructured` en la carpeta de aplicaciones con las siguientes propiedades:

   * Añada la propiedad `guideComponentType` con el valor `fd/af/reducer`. (obligatorio)
   * Añada la propiedad `value` a un nombre completo de la función personalizada de JavaScript™. (obligatorio) y establezca su valor en el nombre de la función personalizada, como Multiplicar.
   * Añada la propiedad `jcr:description` con el valor que desea mostrar como nombre de la función personalizada que aparece en la lista desplegable Función. Por ejemplo, **Multiplicar**.
   * Añada la propiedad `qtip` con un valor que será una breve descripción de la función personalizada. Aparece como información de objeto al pasar el puntero sobre el nombre de la función en la lista desplegable **Function**.

1. Haga clic en **Guardar todo** para guardar la configuración.

La función ahora está disponible para su uso en el gráfico.