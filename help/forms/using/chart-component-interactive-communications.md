---
title: Usar gráficos en comunicaciones interactivas
seo-title: Chart component in Interactive Communications
description: Mediante gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender
seo-description: AEM Forms provides a chart component that you can use to create charts in your Interactive Communication. This document explains basic and agent configurations of the chart component.
uuid: dedd670c-030b-4497-bbcb-3ad935cebcda
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 16c7e698-258d-4e63-9828-f538dc7d3294
feature: Interactive Communication
exl-id: 99077042-cba9-4429-b1e0-830739de5939
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 31%

---

# Usar gráficos en comunicaciones interactivas {#using-charts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Mediante gráficos de una comunicación interactiva, puede condensar grandes cantidades de información en un formato visual fácil de analizar y comprender

Un gráfico es una representación visual de los datos. Condensa grandes cantidades de información en un formato visual fácil de entender, lo que permite a los destinatarios de la comunicación interactiva visualizar, interpretar y analizar mejor los datos complejos.

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

1. Pulse el componente de gráfico en el editor de comunicación interactiva y, en la barra de herramientas Componente, seleccione **[!UICONTROL Configure (]** ![configure_icon](assets/configure_icon.png)).

   La barra lateral Propiedades aparece con las propiedades básicas del gráfico enfocado.

   ![Propiedades básicas de un gráfico de tipo línea en el canal Imprimir](assets/chart_basicproperties.png)
   **Figura:** *Propiedades básicas de un gráfico de tipo de línea en el canal de impresión*

   ![Propiedades básicas de un gráfico de tipo línea en el canal Web](assets/basicpropertieswebchannel.png)
   **Figura:** *Propiedades básicas de un gráfico de tipo de línea en el canal web*

1. Configure las propiedades básicas del gráfico para el canal de impresión y el canal web. Aparte de las propiedades comunes, existen propiedades específicas para la impresión y el canal web y el tipo de gráfico.

   * **[!UICONTROL Nombre]**: Nombre del objeto de gráfico. El nombre del gráfico que especifique aquí no aparece en el resultado del gráfico, sino que se utiliza en las reglas para hacer referencia al gráfico.
   * **[!UICONTROL Tipo de gráfico]**: Especifique el tipo de gráfico: Circular, Columna, Anillo, Línea, Línea y Punto, Punto o Área.
   * **[!UICONTROL Ocultar objeto]**: Seleccione para ocultar el gráfico en la salida final.
   * Especifique lo siguiente para **[!UICONTROL eje x]** y **[!UICONTROL eje Y]**:

      * **[!UICONTROL Título]**: Especifique los títulos de los ejes X e Y que se mostrarán en la Comunicación interactiva.
      * **[!UICONTROL Objeto de modelo de datos *]**: Examine y seleccione los objetos del modelo de datos para el eje X e Y del gráfico desde el modelo de datos de formulario especificado al crear la comunicación interactiva. Elija dos propiedades de tipo colección/matriz del mismo objeto del modelo de datos principal que tengan sentido en relación mutua para trazar en el eje X e Y de un gráfico.
      * **[!UICONTROL Función]**: Para utilizar funciones estadísticas para calcular los valores del eje, seleccione la función del eje X/Y. Para obtener más información sobre las funciones, consulte [Uso de funciones en el gráfico](#usefunction) y [Ejemplo 2: Aplicación de las funciones de suma y media en un gráfico de líneas](#applicationsumfrequency).

   >[!NOTE]
   >
   >Para el canal de impresión, en el eje X, el objeto de modelo de datos que enlace debe ser de tipo Número, Cadena o Fecha. En el eje Y, el objeto de modelo de datos que enlace debe ser del tipo Number . Se recomienda utilizar la leyenda del lado derecho en el canal de impresión.

   Para obtener más información sobre las propiedades del gráfico, consulte [Propiedades básicas de los gráficos](#basicpropertiescharts).

1. (Canal de impresión solamente) En Configuración del agente, especifique si es obligatorio que el agente use este gráfico. Si **[!UICONTROL Es obligatorio que el agente utilice este gráfico]** no está seleccionada, el agente puede tocar el icono de ojo del gráfico en la pestaña Contenido de la interfaz de usuario del agente para mostrar u ocultar el gráfico.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. En la barra lateral Propiedades, pulse ![done_icon](assets/done_icon.png).

   Vista previa para ver el aspecto y los datos del gráfico. Vuelva para volver a configurar las propiedades del gráfico, si es necesario.

1. Vuelva a realizar otros cambios en la Comunicación interactiva.

## Ejemplo 1: Salida de gráfico en imprimir y web {#chartoutputprintweb}

En la ficha Básico , se define el tipo de gráfico, las propiedades del modelo de datos del formulario de origen que contienen datos, las etiquetas que se van a trazar en el eje x y el eje y del gráfico y, opcionalmente, la función estadística para calcular los valores para trazar en el gráfico.

Comprendamos en detalle la información mínima requerida en las propiedades básicas, con la ayuda de un extracto de tarjeta de crédito generado mediante una Comunicación interactiva. Imagine que quiere generar un gráfico para mostrar la cantidad de gastos diferentes en la instrucción. Quiere utilizar diferentes tipos de gráficos para la impresión y la salida web de la comunicación interactiva.

Para lograr esto, debe especificar:

* **[!UICONTROL Tipo de gráfico]** - en este ejemplo, Columna para el canal de impresión y Anillo para el canal web
* **[!UICONTROL Objetos del modelo de datos]** como origen para los ejes X e Y del gráfico: en este ejemplo, importe de la transacción para el eje X y nombre del gasto para el eje Y
* **[!UICONTROL Título]** para los ejes X e Y (para el gráfico de tipo Columna en el canal de impresión solo en este ejemplo): en este ejemplo, Importe ($) para el eje X y Gastos para el eje Y.
* **[!UICONTROL Dirección de la etiqueta]** (para el gráfico de tipo Columna en el canal de impresión solo en este ejemplo): en este ejemplo `Tilt Left`

* **[!UICONTROL Información de objeto]** para mostrar al pasar el ratón sobre un gasto (solo canal web): en este ejemplo `${x}: $ ${y}`, que se muestra como `[Expense Label: $ Amount]` (Ejemplo: Visita al parque temático: $ 315)

![Gráfico de columnas en la salida de impresión de una comunicación interactiva](assets/chartprintchannel.png)
**Figura:** *Gráfico de columnas en la salida de impresión de una comunicación interactiva*

**A.** Eje Y: cantidad recuperada de la propiedad del modelo de datos del formulario y de la propiedad Título establecida en Importe ($) **B.** Dirección de etiqueta del eje X definido como Inclinar a la izquierda **C.** Eje X: la descripción del gasto se obtiene de la propiedad del modelo de datos del formulario y de la propiedad Título establecida en Gasto

![Gráfico circular en la salida web de una comunicación interactiva](assets/chartwebchannel.png)
**Figura:** *Gráfico circular en la salida web de una comunicación interactiva*

**A.** Se establece la propiedad Radio interior del anillo **B.** Mostrar la propiedad Leyenda está seleccionada y la propiedad Posición de Leyenda está establecida a la derecha **C.** La información del objeto muestra el detalle del elemento al pasar el ratón sobre él: La información del objeto está establecida en ${x}: ${y}

## Ejemplo 2: Aplicar las funciones Suma y Frecuencia en un gráfico de líneas {#applicationsumfrequency}

Al aplicar funciones en un gráfico, se pueden representar datos que el modelo de datos de formulario no proporciona directamente. En este ejemplo, utilizamos un ejemplo de instrucción de un extracto de tarjetas de crédito para comprender cómo se pueden aplicar las funciones Suma y Frecuencia al gráfico.

![Gráfico de líneas sin función con tres transacciones &quot;Bed and Breakfast&quot;](assets/creditcarddatalinechartcopy.png)
**Figura:** *Gráfico de líneas sin función con tres transacciones &quot;Bed and Breakfast&quot;*

### Función Suma {#sum-function}

Puede aplicar la función Suma para agregar valores de varias instancias de la misma propiedad de datos y mostrarlos solo una vez. Por ejemplo, en el gráfico siguiente, la función Suma se aplica en el eje Y para sumar la cantidad de las tres transacciones de Bed and Breakfast (99,45 dólares, 78 dólares y 12 dólares) y mostrar solo una transacción (189,45 dólares).

La función Suma puede hacer que el gráfico sea más útil cuando desea recopilar y mostrar la suma para muchas instancias de la misma propiedad de datos.

![creditcardchartsumfunctioncopy](assets/creditcardchartsumfunctioncopy.png)

### Función Frecuencia {#frequency-function}

La función Frequency devuelve el número de valores en los ejes X o Y para un valor determinado en el otro eje. Con la aplicación de la función Frequency en el eje y (Amount/TransAmount), el gráfico muestra que ha habido tres ocurrencias de transacciones de Bed and Breakfast y una ocurrencia del resto de tipos de transacciones.

![creditcardchartfreencyfunctioncopy](assets/creditcardchartfrequencyfunctioncopy.png)

## Propiedades básicas de los gráficos {#basicpropertiescharts}

En la ficha Básico , puede configurar las siguientes propiedades:

**Nombre** Identificador del elemento de gráfico. El nombre no está visible en el gráfico, pero ayuda a hacer referencia al elemento desde otros componentes, secuencias de comandos y expresiones SOM.

**Título (solo canal de impresión)** Especifica el título del gráfico.

**Tipo de gráfico** Especifica el tipo de gráfico que desea generar. Las opciones disponibles son circular, columna, anillo, barra (solo canal web), línea, línea y punto, punto y área. Para obtener más información, consulte Ejemplo 1: Salida de gráfico en impresión y web.

**Eje X > Título** Especifica el título del eje x.

**Eje X > Objeto del modelo de datos &amp;ast;** Especifique el nombre del elemento de recopilación del modelo de datos de formulario que se va a trazar en el eje x.

**Eje X > Función** Especifica la función estadística/personalizada que se utilizará para calcular los valores en el eje x. Para obtener más información sobre las funciones, consulte Uso de funciones en gráficos y Ejemplo 2: Aplicación de las funciones suma y media en un gráfico de líneas.

**Eje X > Dirección de etiqueta** Dirección de la etiqueta del gráfico en el canal de impresión. Si elige la dirección de la etiqueta como Rotación personalizada, aparecerá el campo Ángulo de rotación personalizado (grados). En el campo Ángulo de rotación personalizado (grados), puede elegir el ángulo de giro en pasos de 15 grados.

**Eje Y > Título** Especifica el título del eje Y.

**Eje Y > Objeto del modelo de datos &amp;ast;** Especifica el elemento de colección del modelo de datos de formulario que se va a trazar en el eje Y. En el canal Imprimir, el objeto del modelo de datos para el eje Y debe ser del tipo Número.

**Eje Y > Función** Especifica la función estadística/personalizada que se utilizará para calcular los valores en el eje Y. Para obtener más información sobre las funciones, consulte Uso de funciones en gráficos y Ejemplo 2: Aplicación de las funciones suma y media en un gráfico de líneas.

**Mostrar leyenda** Muestra una leyenda para el gráfico circular o circular cuando está habilitada.

**Posición de la leyenda** Especifica la posición del pie de ilustración con respecto al gráfico. Las opciones disponibles son Derecha, Izquierda, Superior e Inferior.

**Altura (solo canal de impresión)** Altura del gráfico en píxeles.

**Anchura (solo canal de impresión)** Anchura del gráfico en píxeles.

>[!NOTE]
>
>Puede controlar la anchura del gráfico en el canal Web mediante la capa de estilo o al aplicar una temática.

**Información del objeto (solo canal web)** Especifica el formato en el que aparece la información de objeto al pasar el ratón sobre un punto de datos del gráfico en el canal web. El valor predeterminado es \${x}(\${y}). Según el tipo de gráfico, cuando señala el ratón sobre un punto, barra o fracción del gráfico, las variables \${x} y \${y} se sustituyen de forma dinámica por los valores correspondientes del eje x y del eje y y y se muestran en la información del objeto.

Para deshabilitar la información del objeto, deje en blanco el campo Información del objeto. Esta opción no se aplica a los gráficos de líneas y áreas. Por ejemplo, consulte [Ejemplo 1: Salida de gráfico en imprimir y web](#chartoutputprintweb).

**Clase CSS (solo canal web)** Especifique el nombre de una clase CSS en el campo de clase CSS para aplicar estilo personalizado al gráfico.

**Salto de página obligatorio antes de (canal de impresión solamente)** Seleccione para agregar un salto de página obligatorio antes del gráfico y coloque el gráfico sobre una nueva página.

**Salto de página obligatorio después de (canal de impresión solamente)** Seleccione para agregar un salto de página obligatorio después del gráfico y coloque el contenido que sigue al gráfico en la parte superior de una nueva página.

**Sangría (solo canal de impresión)** Especifique la sangría del gráfico desde la izquierda de la página.

**Configuraciones específicas de gráficos** Además de las configuraciones comunes, están disponibles las siguientes configuraciones específicas del gráfico:

* **Radio interior**: disponible para gráficos circulares para especificar el radio (en píxeles) del círculo interior del gráfico.
* **Color de línea**: disponible para gráficos de líneas, líneas y puntos y áreas para especificar el valor hexadecimal del color de la línea del gráfico.
* **Color de punto**: disponible para gráficos de puntos y líneas y puntos para especificar el valor hexadecimal del color de los puntos del gráfico.

* **Color de área**: disponible para gráficos de área para especificar el valor hexadecimal del color para el área bajo la línea del gráfico.

## Usar funciones en el gráfico {#usefunction}

Puede configurar un gráfico para que utilice funciones estadísticas a fin de calcular los valores a partir de los datos de origen para trazar en el gráfico. Al aplicar funciones en un gráfico, se pueden representar datos que el modelo de datos de formulario no proporciona directamente.

Aunque el componente Gráfico incluye algunas funciones integradas, puede escribir sus propias funciones y ponerlas a disposición para su uso en la configuración de gráficos del canal Web.

![gráfico de funciones](assets/functionchart.png)

>[!NOTE]
>
>Puede utilizar funciones para calcular valores para ejes X o Y en un gráfico.

### Funciones predeterminadas {#default-functions}

Las siguientes funciones están disponibles de forma predeterminada con el componente Gráfico:

**Media (media)** Devuelve la media de los valores del eje X o Y para un valor determinado del otro eje.

**Suma** Devuelve la suma de todos los valores del eje X o Y para un valor determinado del otro eje.

**Máximo** Devuelve el máximo de los valores del eje X o Y para un valor determinado del otro eje.

**Frecuencia** Devuelve el número de valores en el eje X o Y para un valor determinado del otro eje.

**Rango** Devuelve la diferencia entre el máximo y el mínimo de los valores del eje X o Y para un valor determinado del otro eje.

**Mediana** Devuelve el valor que separa los valores más altos e inferiores a la mitad en los ejes X o Y para un valor determinado en el otro eje.

**Mínimo** Devuelve el mínimo de los valores del eje X o Y para un valor determinado del otro eje.

**Modo** Devuelve el valor con la mayoría de las incidencias en el eje X o Y para un valor determinado en el otro eje

### Funciones personalizadas en el canal Web {#custom-functions-in-web-channel}

Además de utilizar las funciones predeterminadas en los gráficos, puede escribir funciones personalizadas en JavaScript™ y ponerlas a disposición en la lista de funciones del componente Gráfico para el canal Web.

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

1. Agregue la función personalizada en la biblioteca de cliente asociada a la comunicación interactiva correspondiente. Para obtener más información, consulte [Configurar la acción Enviar](/help/forms/using/configuring-submit-actions.md) y [Usar bibliotecas del lado del cliente](/help/sites-developing/clientlibs.md).

1. Para mostrar la función personalizada en la lista desplegable Función, en CRXDe Lite, cree un nodo `nt:unstructured` en la carpeta apps con las siguientes propiedades:

   * Agregar propiedad `guideComponentType` con valor como `fd/af/reducer`. (obligatorio)
   * Agregue la propiedad `value` a un nombre completo de la función personalizada JavaScript™. (obligatorio) y establezca su valor en el nombre de la función personalizada, como Multiplicar.
   * Agregue la propiedad `jcr:description` con el valor que desea mostrar como nombre de la función personalizada que aparece en la lista desplegable Función. Por ejemplo, **Multiplicar**.
   * Agregue la propiedad `qtip` con valor que será una breve descripción de la función personalizada. Aparece como información del objeto al pasar el puntero sobre el nombre de la función en la lista desplegable **Función**.

1. Haga clic en **Guardar todo** para guardar la configuración.

La función ahora está disponible para usarla en el gráfico.
