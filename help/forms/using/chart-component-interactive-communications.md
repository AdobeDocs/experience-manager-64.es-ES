---
title: Uso de gráficos en Interactive Communications
seo-title: Componente gráfico en Interactive Communications
description: 'Mediante gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender  '
seo-description: AEM Forms proporciona un componente de gráfico que puede utilizar para crear gráficos en la comunicación interactiva. Este documento explica las configuraciones básicas y de agente del componente de gráfico.
uuid: dedd670c-030b-4497-bbcb-3ad935cebcda
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 16c7e698-258d-4e63-9828-f538dc7d3294
feature: Comunicación interactiva
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2425'
ht-degree: 0%

---


# Uso de gráficos en Interactive Communications {#using-charts-in-interactive-communications}

Mediante gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender

Un gráfico o un gráfico es una representación visual de los datos. Condensa grandes cantidades de información en un formato visual fácil de entender, lo que permite a los destinatarios de la comunicación interactiva visualizar, interpretar y analizar mejor los datos complejos.

Mientras crea una comunicación interactiva, puede agregar gráficos para representar visualmente los datos bidimensionales del modelo de datos de formulario de la comunicación interactiva. El componente Gráfico permite añadir y configurar los siguientes tipos de gráficos:

* Circular
* Columna
* Gráfico de sectores
* Barra (solo canal web)
* Línea
* Línea y punto
* Punto
* Área

## Agregar y configurar un gráfico en una comunicación interactiva {#add-and-configure-chart-in-an-interactive-communication}

Complete los siguientes pasos para agregar un gráfico a una comunicación interactiva:

1. En la barra lateral de Componentes, arrastre y suelte el componente Gráfico en uno de los siguientes canales de impresión o web de una comunicación interactiva:

   * Canal de impresión: Área de objetivo y campo de imagen
   * Canal web: Panel y área de destino

   El componente Gráfico colocado crea un marcador de posición para un gráfico.

1. Pulse el componente de gráfico en el editor de comunicación interactiva y, en la barra de herramientas Componente, seleccione **[!UICONTROL Configurar (]** ![configurar_icono](assets/configure_icon.png)).

   La barra lateral Propiedades aparece con las propiedades básicas del gráfico enfocado.

   ![Propiedades básicas de un gráfico de tipo de línea en el canal de impresión](assets/chart_basicproperties.png)
   **Figura:** *Propiedades básicas de un gráfico de tipo de línea en el canal de impresión*

   ![Propiedades básicas de un gráfico de tipo de línea en el canal web](assets/basicpropertieswebchannel.png)
   **Figura:** *Propiedades básicas de un gráfico de tipo de línea en el canal web*

1. Configure las propiedades básicas del gráfico para el canal de impresión y el canal web. Aparte de las propiedades comunes, existen propiedades específicas para la impresión y el canal web y el tipo de gráfico.

   * **[!UICONTROL Nombre]**: Nombre del objeto de gráfico. El nombre del gráfico que especifique aquí no aparece en el resultado del gráfico, sino que se utiliza en las reglas para hacer referencia al gráfico.
   * **[!UICONTROL Tipo]** de gráfico: Especifique el tipo de gráfico: Circular, Columna, Anillo, Línea, Línea y Punto, Punto o Área.
   * **[!UICONTROL Ocultar objeto]**: Seleccione para ocultar el gráfico en la salida final.
   * Especifique lo siguiente para **[!UICONTROL x-axis]** y **[!UICONTROL y-axis]**:

      * **[!UICONTROL Título]**: Especifique los títulos de los ejes X e Y que se mostrarán en la Comunicación interactiva.
      * **[!UICONTROL Objeto Modelo de datos *]**: Examine y seleccione los objetos del modelo de datos para el eje X e Y del gráfico desde el modelo de datos de formulario especificado al crear la comunicación interactiva. Elija dos propiedades de tipo colección/matriz del mismo objeto del modelo de datos principal que tengan sentido en relación mutua para trazar en el eje X e Y de un gráfico.
      * **[!UICONTROL Función]**: Para utilizar funciones estadísticas para calcular los valores del eje, seleccione la función del eje X/Y. Para obtener más información sobre las funciones, consulte [Uso de funciones en el gráfico](#usefunction) y [Ejemplo 2: Aplicación de funciones de suma y media en un gráfico de líneas](#applicationsumfrequency).

   >[!NOTE]
   >
   >Para el canal de impresión, en el eje X, el objeto de modelo de datos que enlace debe ser de tipo Número, Cadena o Fecha. En el eje Y, el objeto de modelo de datos que enlace debe ser del tipo Number . Se recomienda utilizar la leyenda del lado derecho en el canal de impresión.

   Para obtener más información sobre las propiedades del gráfico, consulte [Propiedades básicas de los gráficos](#basicpropertiescharts).

1. (Canal de impresión solamente) En Configuración del agente, especifique si es obligatorio que el agente use este gráfico. Si la opción **[!UICONTROL t Is Mandatory For the Agent To Use This Chart]** no está seleccionada, el agente puede tocar el icono de ojo del gráfico en la pestaña Content de la interfaz de usuario del agente para mostrar u ocultar el gráfico.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. En la barra lateral Propiedades, pulse ![done_icon](assets/done_icon.png).

   Vista previa para ver el aspecto y los datos del gráfico. Vuelva para volver a configurar las propiedades del gráfico, si es necesario.

1. Vuelva a realizar otros cambios en la Comunicación interactiva.

## Ejemplo 1: Salida de gráfico en impresión y Web {#chartoutputprintweb}

En la ficha Básico , se define el tipo de gráfico, las propiedades del modelo de datos del formulario de origen que contienen datos, las etiquetas que se van a trazar en el eje x y el eje y del gráfico y, opcionalmente, la función estadística para calcular los valores para trazar en el gráfico.

Comprendamos en detalle la información mínima requerida en las propiedades básicas, con la ayuda de un extracto de tarjeta de crédito generado mediante una Comunicación interactiva. Tenga en cuenta que desea generar un gráfico para mostrar la cantidad de gastos diferentes en el estado. Desea utilizar diferentes tipos de gráficos para la impresión y la salida web de la comunicación interactiva.

Para lograr esto, debe especificar:

* **[!UICONTROL Tipo de gráfico]** : en este ejemplo, Columna para el canal de impresión y Anillo para el canal web
* **[!UICONTROL Objetos del modelo de]** datos como fuente para los ejes X e Y del gráfico. En este ejemplo, Cantidad de transacción para el eje X y Nombre de gasto para el eje Y
* **** Título para el eje X e Y (para el gráfico de tipo Columna en el canal de impresión solo en este ejemplo): en este ejemplo, Cantidad ($) para el eje X y Gastos para el eje Y.
* **[!UICONTROL Dirección de la etiqueta]**  (para el gráfico de tipo columna del canal de impresión solo en este ejemplo): en este ejemplo  `Tilt Left`

* **** Información sobre herramientas para mostrar al pasar el ratón sobre un gasto (solo canal web): en este ejemplo  `${x}: $ ${y}`, que se muestra como  `[Expense Label: $ Amount]` (Ejemplo: Visita al parque temático: $ 315)

![Gráfico de columnas en la salida de impresión de una ](assets/chartprintchannel.png)
**Comunicación interactivaFigura:** *Gráfico de columnas en la salida de impresión de una Comunicación interactiva*

**Eje A.** Y: cantidad recuperada de la propiedad del modelo de datos del formulario y de la propiedad Título establecida en Importe ($)  **B.** Dirección de etiqueta del eje X definida en Inclinar a la izquierda Eje  **C.** X: descripción de gastos recuperada de la propiedad del modelo de datos del formulario y de la propiedad Título establecida en Gasto

![Gráfico circular en la salida web de una ](assets/chartwebchannel.png)
**comunicación interactivaFigura:** *Gráfico circular en la salida web de una comunicación interactiva*

**A.** La propiedad Radio interior de la rosca está establecida  **B.** La propiedad Mostrar leyenda está seleccionada y la propiedad Posición de leyenda está establecida a la derecha  **C.**  La información de objeto muestra el detalle del elemento al pasar el ratón. La información de objeto está establecida a ${x}: ${y}

## Ejemplo 2: Aplicación de las funciones Suma y Frecuencia en un gráfico de líneas {#applicationsumfrequency}

Al aplicar funciones en un gráfico, se pueden representar datos que el modelo de datos de formulario no proporciona directamente. En este ejemplo, utilizamos un ejemplo de extracto de tarjetas de crédito para comprender cómo se pueden aplicar las funciones Suma y Frecuencia al gráfico.

![Gráfico de líneas sin función con tres ](assets/creditcarddatalinechartcopy.png)
**transacciones de &quot;bed and breakfast&quot;Figura:** *Gráfico de líneas sin función con tres transacciones de &quot;Bed and Breakfast&quot;*

### Función Sum {#sum-function}

Puede aplicar la función sum para agregar valores de varias instancias de la misma propiedad de datos y mostrarlos solo una vez. Por ejemplo, en el gráfico siguiente, la función Suma se aplica en el eje Y para sumar la cantidad de las tres transacciones de Bed and Breakfast (99,45 dólares, 78 dólares y 12 dólares) y mostrar solo una transacción (189,45 dólares).

La función Sum puede hacer que el gráfico sea más útil cuando desea recopilar y mostrar la suma para muchas instancias de la misma propiedad de datos.

![creditcardchartsumfunctioncopy](assets/creditcardchartsumfunctioncopy.png)

### Función de frecuencia {#frequency-function}

La función Frequency devuelve el número de valores en los ejes X o Y para un valor determinado en el otro eje. Con la aplicación de la función Frequency en el eje y (Amount/TransAmount), el gráfico muestra que ha habido tres ocurrencias de transacciones de Bed and Breakfast y una ocurrencia del resto de tipos de transacciones.

![creditcardchartfreencyfunctioncopy](assets/creditcardchartfrequencyfunctioncopy.png)

## Propiedades básicas de los gráficos {#basicpropertiescharts}

En la ficha Básico , puede configurar las siguientes propiedades:

**** NombreIdentificador del elemento de gráfico. El nombre no está visible en el gráfico, pero ayuda a hacer referencia al elemento desde otros componentes, secuencias de comandos y expresiones SOM.

**Título (solo canal de impresión)** Especifica el título del gráfico.

**Tipo de** gráficoEspecifica el tipo de gráfico que desea generar. Las opciones disponibles son circular, columna, anillo, barra (solo canal web), línea, línea y punto, punto y área. Para obtener más información, consulte Ejemplo 1: Salida de gráfico en impresión y web.

**Eje X >** TítuloEspecifica el título del eje x.

**Eje X > Objeto del modelo de datos &amp;ast;** especifique el nombre del elemento de colección del modelo de datos de formulario que se va a trazar en el eje x.

**Eje X >** FunciónEspecifica la función estadística/personalizada que se utilizará para calcular los valores en el eje x. Para obtener más información sobre las funciones, consulte Uso de funciones en gráficos y Ejemplo 2: Aplicación de las funciones suma y media en un gráfico de líneas.

**Eje X >** Dirección de etiquetaDirección de la etiqueta del gráfico en el canal de impresión. Si elige la dirección de la etiqueta como Rotación personalizada, aparecerá el campo Ángulo de rotación personalizado (grados). En el campo Ángulo de rotación personalizado (grados), puede elegir el ángulo de giro en pasos de 15 grados.

**Eje Y >** TítuloEspecifica el título del eje Y.

**Eje Y > Objeto del modelo de datos &amp;ast;**  Especifica el elemento de colección del modelo de datos de formulario que se va a trazar en el eje Y. En el canal Imprimir, el objeto del modelo de datos para el eje Y debe ser del tipo Número.

**Eje Y >** FunciónEspecifica la función estadística/personalizada que se utilizará para calcular los valores en el eje Y. Para obtener más información sobre las funciones, consulte Uso de funciones en gráficos y Ejemplo 2: Aplicación de las funciones suma y media en un gráfico de líneas.

**Mostrar** leyendaMuestra una leyenda para el gráfico circular o circular cuando está habilitada.

**Posición de** leyendaEspecifica la posición de la leyenda con respecto al gráfico. Las opciones disponibles son Derecha, Izquierda, Superior e Inferior.

**Altura (solo canal de impresión)** Altura del gráfico en píxeles.

**Anchura (solo canal de impresión)** Anchura del gráfico en píxeles.

>[!NOTE]
>
>Puede controlar la anchura del gráfico en el canal web mediante la capa de estilo o aplicando un tema.

**Información del objeto (solo canal web)**  Especifica el formato en el que aparece la información del objeto al pasar el ratón sobre un punto de datos del gráfico del canal web. El valor predeterminado es \${x}(\${y}). Según el tipo de gráfico, cuando señala el ratón sobre un punto, barra o fracción del gráfico, las variables \${x} y \${y} se sustituyen de forma dinámica por los valores correspondientes del eje x y del eje y y y se muestran en la información del objeto.

Para desactivar la información del objeto, deje el campo Información del objeto en blanco. Esta opción no se aplica a los gráficos de líneas y áreas. Por ejemplo, consulte [Ejemplo 1: Salida de gráfico en impresión y Web](#chartoutputprintweb).

**Clase CSS (solo canal web)** Especifique el nombre de una clase CSS en el campo de clase CSS para aplicar estilo personalizado al gráfico.

**Salto de página obligatorio antes (solo canal de impresión)**  Seleccione esta opción para agregar un salto de página obligatorio antes del gráfico y coloque el gráfico sobre una nueva página.

**Salto de página obligatorio después de (canal de impresión solamente)**  Seleccione esta opción para agregar un salto de página obligatorio después del gráfico y coloque el contenido que sigue al gráfico sobre una nueva página.

**Sangría (solo canal de impresión)** Especifique la sangría del gráfico desde la izquierda de la página.

**Configuraciones específicas del** gráfico Además de configuraciones comunes, están disponibles las siguientes configuraciones específicas del gráfico:

* **Radio interior**: disponible para gráficos circulares para especificar el radio (en píxeles) del círculo interior del gráfico.
* **Color** de línea: disponible para gráficos de líneas, líneas y puntos y áreas para especificar el valor hexadecimal del color de la línea del gráfico.
* **Color** de punto: disponible para gráficos de puntos y líneas y puntos para especificar el valor hexadecimal del color de los puntos del gráfico.

* **Color** de área: disponible para gráficos de área para especificar el valor hexadecimal del color para el área bajo la línea del gráfico.

## Uso de funciones en el gráfico {#usefunction}

Puede configurar un gráfico para que utilice funciones estadísticas a fin de calcular los valores a partir de los datos de origen para trazar en el gráfico. Al aplicar funciones en un gráfico, se pueden representar datos que el modelo de datos de formulario no proporciona directamente.

Aunque el componente Gráfico incluye algunas funciones integradas, puede escribir sus propias funciones y ponerlas a disposición para su uso en la configuración de gráficos del canal Web.

![gráfico de funciones](assets/functionchart.png)

>[!NOTE]
>
>Puede utilizar funciones para calcular valores para ejes X o Y en un gráfico.

### Funciones predeterminadas {#default-functions}

Las siguientes funciones están disponibles de forma predeterminada con el componente Gráfico :

**Media (Average)** Devuelve el promedio de los valores en el eje X o Y para un valor determinado en el otro eje.

**** SumDevuelve la suma de todos los valores del eje X o Y para un valor determinado del otro eje.

**** MaximumDevuelve el máximo de los valores en el eje X o Y para un valor determinado en el otro eje.

**** FrequencyDevuelve el número de valores en el eje X o Y para un valor determinado en el otro eje.

**** RangeDevuelve la diferencia entre el máximo y el mínimo de los valores en el eje X o Y para un valor determinado en el otro eje.

**** MedianaDevuelve el valor que separa los valores más altos e inferiores a la mitad en los ejes X o Y para un valor determinado en el otro eje.

**** MinimumDevuelve el mínimo de los valores del eje X o Y para un valor determinado del otro eje.

**** ModeDevuelve el valor con la mayoría de las incidencias en el eje X o Y para un valor determinado del otro eje

### Funciones personalizadas en el canal web {#custom-functions-in-web-channel}

Además de utilizar las funciones predeterminadas en los gráficos, puede escribir funciones personalizadas en JavaScript™ y ponerlas a disposición en la lista de funciones del componente Gráfico para el canal web.

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

Una vez que haya escrito una función personalizada, haga lo siguiente para que esté disponible para usarla en la configuración del gráfico:

1. Añada la función personalizada en la biblioteca de cliente asociada a la comunicación interactiva correspondiente. Para obtener más información, consulte [Configuración de la acción de envío](/help/forms/using/configuring-submit-actions.md) y [Uso de bibliotecas del lado del cliente](/help/sites-developing/clientlibs.md).

1. Para mostrar la función personalizada en la lista desplegable Función, en CRXDe Lite, cree un nodo `nt:unstructured` en la carpeta de aplicaciones con las siguientes propiedades:

   * Agregue la propiedad `guideComponentType` con el valor `fd/af/reducer`. (obligatorio)
   * Agregue la propiedad `value` a un nombre completo de la función personalizada de JavaScript™. (obligatorio) y establezca su valor en el nombre de la función personalizada, como Multiply.
   * Agregue la propiedad `jcr:description` con el valor que desea mostrar como nombre de la función personalizada que aparece en la lista desplegable Función. Por ejemplo, **Multiply**.
   * Agregue la propiedad `qtip` con un valor que sea una breve descripción de la función personalizada. Aparece como información de objeto al pasar el puntero sobre el nombre de función en la lista desplegable **Function**.

1. Haga clic en **Guardar todo** para guardar la configuración.

La función ahora está disponible para su uso en el gráfico.