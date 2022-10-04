---
title: "Tutorial: Crear fragmentos de documento"
seo-title: Create document fragments for Interactive Communication
description: Creación de fragmentos de documento para la comunicación interactiva
seo-description: Create document fragments for Interactive Communication
uuid: 215d09a6-949c-45ef-b2b0-88cd0cb4b99c
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9b78e2b-af7d-49d7-b37f-c96ec732015e
feature: Interactive Communication
exl-id: 50d93998-6393-4607-b89b-5b97aad530a3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1683'
ht-degree: 3%

---

# Tutorial: Crear fragmentos de documento {#tutorial-create-document-fragments}

Creación de fragmentos de documento para la comunicación interactiva

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Este tutorial es un paso en la [Cree su primera comunicación interactiva](/help/forms/using/create-your-first-interactive-communication.md) serie. Se recomienda seguir la serie en secuencia cronológica para comprender, realizar y demostrar el caso de uso completo del tutorial.

Los fragmentos de documento son componentes reutilizables de una correspondencia que se utilizan para componer una comunicación interactiva. Los fragmentos del documento son de los siguientes tipos:

* Texto : un recurso de texto es un fragmento de contenido que consta de uno o más párrafos de texto. Un párrafo puede ser estático o dinámico.
* Lista : Lista es un grupo de fragmentos de documento, que incluyen texto, listas, condiciones e imágenes.
* Condición : las condiciones permiten definir qué contenido se incluye en la comunicación interactiva en función de los datos recibidos del modelo de datos del formulario.

Este tutorial le guía por los pasos para crear varios fragmentos de documento de texto basados en la anatomía proporcionada en [Planificar la comunicación interactiva](/help/forms/using/planning-interactive-communications.md) para obtener más información. Al final de este tutorial, podrá:

* Crear fragmentos de documento
* Crear variables
* Crear y aplicar reglas

![text_document_fragments](assets/text_document_fragments.gif)

A continuación se muestra la lista de fragmentos de documento creados en este tutorial:

* [Detalles de la factura](/help/forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Detalles del cliente](/help/forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Resumen de la factura](/help/forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Resumen de gastos](/help/forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Cada fragmento de documento incluye campos con texto estático, datos recibidos del modelo de datos de formulario y datos introducidos mediante la interfaz de usuario del agente. Todos estos campos se han representado en la variable [Planificar la comunicación interactiva](/help/forms/using/planning-interactive-communications.md) para obtener más información.

Al crear fragmentos de documento en este tutorial, las variables se crean para campos que reciben datos mediante la interfaz de usuario del agente.

Uso **FDM_Create_First_IC**, tal como se describe en la sección [Crear modelo de datos de formulario](create-form-data-model-tutorial.md) , como modelo de datos de formulario para crear fragmentos de documento en este tutorial.

## Paso 1: Crear fragmento de documento Detalles de la factura {#step-create-bill-details-text-document-fragment}

El fragmento de documento Detalles de la factura incluye los siguientes campos:

| Campo | Fuente de datos |
|---|---|
| Nº de factura | IU del agente |
| Período de facturación | IU del agente |
| Fecha de factura | IU del agente |
| Su plan | Modelo de datos de formulario |

Ejecute los siguientes pasos para crear variables para campos con la interfaz de usuario del agente como fuente de datos, crear texto estático y utilizar elementos del modelo de datos de formulario en el fragmento de documento:

1. Select **[!UICONTROL Forms]** > **[!UICONTROL Fragmentos de documento]**.

1. Select **Crear** > **Texto**.
1. Especifique la siguiente información:

   1. Entrar **bill_details_first_ic** como el nombre en la variable **Título** campo . El título se rellena automáticamente en la variable **Nombre** campo .
   1. Select **Modelo de datos de formulario** de la variable **Modelo de datos** para obtener más información.
   1. Select **FDM_Create_First_IC** como modelo de datos del formulario y pulse **Select**.
   1. Pulse **Siguiente**.

1. Seleccione el **Variables** en el panel izquierdo y pulse **Crear**.
1. En el **Crear variable** sección:

   1. Entrar **Invoicenumber** como nombre de la variable.
   1. Select **Cadena** como tipo.
   1. Pulse **Crear**.

   ![variable_create_string](assets/variable_create_string.png)

   Repita los pasos 4 y 5 para crear las siguientes variables:

   * Billperiod: Tipo de cadena
   * Fecha de factura: Tipo de fecha

   ![variables_bill_details](assets/variables_bill_details.png)

1. Cree texto estático para los campos siguientes utilizando el panel derecho:

   * Nº de factura
   * Período de facturación
   * Fecha de factura
   * Su plan

   ![variable_bill_details_static_text](assets/variable_bill_details_static_text.png)

1. Coloque el cursor junto al **Nº de factura** y haga doble clic en el botón **Número de factura** desde la variable **Variables** en el panel izquierdo.
1. Coloque el cursor junto al **Período de facturación** y haga doble clic en el botón **Billperiod** variable.
1. Coloque el cursor junto al **Fecha de factura** y haga doble clic en el botón **Fecha de factura** variable.
1. Seleccione el **Objetos del modelo de datos** en el panel izquierdo.
1. Coloque el cursor junto al **Su plan** y haga doble clic en el botón **cliente** > **customerplan** propiedad.

   ![bill_details_customerplan_fdm](assets/bill_details_customerplan_fdm.png)

1. Haga clic en **Guardar** para crear el fragmento de documento Detalles de la factura.

## Paso 2: Crear fragmento de documento de detalles del cliente {#step-create-customer-details-text-document-fragment}

El fragmento de documento Detalles del cliente incluye los siguientes campos:

| Campo | Fuente de datos |
|---|---|
| Nombre del cliente | Modelo de datos de formulario |
| Dirección | Modelo de datos de formulario |
| Lugar de suministro | IU del agente |
| Código de estado | IU del agente |
| Número de móvil | Modelo de datos de formulario |
| Número de contacto alternativo | Modelo de datos de formulario |
| Número de relación | Modelo de datos de formulario |
| Número de conexiones | IU del agente |

Ejecute los siguientes pasos para crear variables para campos con la interfaz de usuario del agente como fuente de datos, crear texto estático y utilizar elementos del modelo de datos de formulario en el fragmento de documento:

1. Select **[!UICONTROL Forms]** > **[!UICONTROL Fragmentos de documento]**.
1. Select **Crear** > **Texto**.
1. Especifique la siguiente información:

   1. Entrar **customer_details_first_ic** como el nombre en la variable **Título** campo . El título se rellena automáticamente en la variable **Nombre** campo .
   1. Select **Modelo de datos de formulario** de la variable **Modelo de datos** para obtener más información.
   1. Select **FDM_Create_First_IC** como modelo de datos del formulario y pulse **Select**.
   1. Pulse **Siguiente**.

1. Seleccione el **Variables** en el panel izquierdo y pulse **Crear**.
1. En el **Crear variable** sección:

   1. Entrar **Placesupply** como nombre de la variable.
   1. Select **Cadena** como tipo.
   1. Pulse **Crear**.

   Repita los pasos 4 y 5 para crear las siguientes variables:

   * Código de estado: Tipo de número
   * Numeración de conexiones: Tipo de número


1. Seleccione el **Objetos del modelo de datos** , coloque el cursor en el panel derecho y haga doble clic en el botón **cliente** > **name** propiedad.
1. Pulse Intro para mover el cursor a la línea siguiente y haga doble clic en el botón **cliente** > **address** propiedad.
1. Cree texto estático para los campos siguientes utilizando el panel derecho:

   * Número de móvil
   * Número de contacto alternativo
   * Lugar de suministro
   * Número de relación
   * Código de estado
   * Número de conexiones

   ![customer_details_static_text_fdm](assets/customer_details_static_text_fdm.png)

1. Coloque el cursor junto al **Número de móvil** y haga doble clic en el botón **cliente** > **mobilenum** propiedad.
1. Coloque el cursor junto al **Número de contacto alternativo** y haga doble clic en el botón **cliente** > **alternatemobilenumber** propiedad.
1. Coloque el cursor junto al **Número de relación** y haga doble clic en el botón **cliente** > **relation number** propiedad.
1. Seleccione el **Variables** , coloque el cursor junto a la pestaña **Lugar de suministro** y haga doble clic en el botón **Placesupply** variable.
1. Coloque el cursor junto al **Código de estado** y haga doble clic en el botón **Statecode** variable.
1. Coloque el cursor junto al **Número de conexiones** y haga doble clic en el botón **Numeración de conexiones** variable.

   ![customer_details_df2](assets/customer_details_df2.png)

1. Haga clic en **Guardar** para crear el fragmento de documento de texto Detalles del cliente .

## Paso 3: Crear fragmento de documento de resumen de lista {#step-create-bill-summary-text-document-fragment}

El fragmento de documento Resumen de factura incluye los siguientes campos:

| Campo | Fuente de datos |
|---|---|
| Saldo anterior | IU del agente |
| Pagos | IU del agente |
| Ajustes | IU del agente |
| Cargos período de factura actual | Modelo de datos de formulario |
| Importe vencido | IU del agente |
| Fecha de vencimiento | IU del agente |

Ejecute los siguientes pasos para crear variables para campos con la interfaz de usuario del agente como fuente de datos, crear texto estático y utilizar elementos del modelo de datos de formulario en el fragmento de documento:

1. Select **[!UICONTROL Forms]** > **[!UICONTROL Fragmentos de documento]**.
1. Select **Crear** > **Texto**.
1. Especifique la siguiente información:

   1. Entrar **bill_summary_first_ic** como el nombre en la variable **Título** campo . El título se rellena automáticamente en la variable **Nombre** campo .
   1. Select **Modelo de datos de formulario** de la variable **Modelo de datos** para obtener más información.
   1. Select **FDM_Create_First_IC** como modelo de datos del formulario y pulse **Select**.
   1. Pulse **Siguiente**.

1. Seleccione el **Variables** en el panel izquierdo y pulse **Crear**.
1. En el **Crear variable** sección:

   1. Entrar **Saldo anterior** como nombre de la variable.
   1. Select **Número** como tipo.
   1. Pulse **Crear**.

   Repita los pasos 4 y 5 para crear las siguientes variables:

   * Pagos: Tipo de número
   * Ajustes: Tipo de número
   * Importe: Tipo de número
   * Destinado: Tipo de fecha


1. Cree texto estático para los campos siguientes utilizando el panel derecho:

   * Saldo anterior
   * Pagos
   * Ajustes
   * Cargos período de factura actual
   * Importe vencido
   * Fecha de vencimiento
   * Cargos por demora en el pago después de Fecha de Vencimiento es $ 20

   ![bill_summary_static](assets/bill_summary_static.png)

1. Coloque el cursor junto al **Saldo anterior** y haga doble clic en el botón **Saldo anterior** variable.
1. Coloque el cursor junto al **Pagos** y haga doble clic en el botón **Pagos** variable.
1. Coloque el cursor junto al **Ajustes** y haga doble clic en el botón **Ajustes** variable.
1. Coloque el cursor junto al **Importe vencido** y haga doble clic en el botón **Importe** variable.
1. Coloque el cursor junto al **Fecha de vencimiento** y haga doble clic en el botón **Duedate** variable.
1. Seleccione el **Objetos del modelo de datos** , coloque el cursor junto a la pestaña **Cargos período de factura actual** en el panel derecho y haga doble clic en el botón **letras** > **usagecharges** propiedad.

   ![bill_summary_static_variables](assets/bill_summary_static_variables.png)

1. Haga clic en **Guardar** para crear el fragmento de documento de texto Detalles del cliente .

## Paso 4: Crear fragmento de documento Resumen de cargos {#step-create-summary-of-charges-text-document-fragment}

El fragmento de documento Resumen de cargos incluye los siguientes campos:

| Campo | Fuente de datos |
|---|---|
| Cargos de llamada | Modelo de datos de formulario |
| Cargos por llamada de conferencia | Modelo de datos de formulario |
| Cargos por SMS | Modelo de datos de formulario |
| Cargos por Internet móvil | Modelo de datos de formulario |
| Cargos de itinerancia nacionales | Modelo de datos de formulario |
| Cargos de itinerancia internacionales | Modelo de datos de formulario |
| Cargos por Servicios de Valor Agregado | Modelo de datos de formulario |
| Cargos totales | Modelo de datos de formulario |
| TOTAL PAGADO | Modelo de datos de formulario |

Ejecute los siguientes pasos para crear texto estático y utilizar elementos del modelo de datos de formulario en el fragmento de documento:

1. Select **[!UICONTROL Forms]** > **[!UICONTROL Fragmentos de documento]**.
1. Select **Crear** > **Texto**.
1. Especifique la siguiente información:

   1. Entrar **summary_loads_first_ic** como el nombre en la variable **Título** campo . El título se rellena automáticamente en el campo Nombre .
   1. Select **Modelo de datos de formulario** de la variable **Modelo de datos** para obtener más información.
   1. Select **FDM_Create_First_IC** como modelo de datos del formulario y pulse **Select**.
   1. Pulse **Siguiente**.

1. Cree texto estático para los campos siguientes utilizando el panel derecho:

   * Cargos de llamada
   * Cargos por llamada de conferencia
   * Cargos por SMS
   * Cargos por Internet móvil
   * Cargos de itinerancia nacionales
   * Cargos de itinerancia internacionales
   * Cargos por Servicios de Valor Agregado
   * Cargos totales
   * TOTAL PAGADO

   ![summary_loads_static](assets/summary_charges_static.png)

1. Seleccione el **Objetos del modelo de datos** pestaña .
1. Coloque el cursor junto al **Cargos de llamada** y haga doble clic en el botón **letras** > **cargas** propiedad.
1. Coloque el cursor junto al **Cargos por llamada de conferencia** y haga doble clic en el botón **letras** > **recargos** propiedad.
1. Coloque el cursor junto al **Cargos por SMS** y haga doble clic en el botón **letras** > **smscharge** propiedad.
1. Coloque el cursor junto al **Cargos por Internet móvil** y haga doble clic en el botón **letras** > **internetones** propiedad.
1. Coloque el cursor junto al **Cargos de itinerancia nacionales** y haga doble clic en el botón **letras** > **itinerante nacional** propiedad.
1. Coloque el cursor junto al **Cargos de itinerancia internacionales** y haga doble clic en el botón **letras** > **roamingintnl** propiedad.
1. Coloque el cursor junto al **Cargos por Servicios de Valor Agregado** y haga doble clic en el botón **letras** > **lienzo** propiedad.
1. Coloque el cursor junto al **Cargos totales** y haga doble clic en el botón **letras** > **usagecharges** propiedad.
1. Coloque el cursor junto al **TOTAL PAGADO** y haga doble clic en el botón **letras** > **usagecharges** propiedad.

   ![summary_charge_static_fdm](assets/summary_charges_static_fdm.png)

1. Seleccione el texto en la **Cargos por Servicios de Valor Agregado** pulsar y arrastrar **Crear regla** para crear una condición basada en la que se muestra la fila en la comunicación interactiva:
1. En el **Crear regla** ventana emergente:

   1. Select **Modelos y variables de datos** y luego **letras** > **cargas**.
   1. Select **es menor que** como operador.
   1. Select **Número** e introduzca el valor como **60**.

   En función de esta condición, la fila Cargos de servicios de valor añadido solo se muestra si el valor del campo Cargos de llamadas es inferior a 60.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. Haga clic en **Guardar** para crear el fragmento de documento Resumen de cargos .
