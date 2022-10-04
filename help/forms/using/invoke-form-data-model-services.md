---
title: API para invocar el servicio del modelo de datos de formulario desde formularios adaptables
seo-title: API to invoke form data model service from adaptive forms
description: Explica la API de invokeWebServices que puede utilizar para invocar servicios web escritos en WSDL desde un campo de formulario adaptable.
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 48%

---

# API para invocar el servicio del modelo de datos de formulario desde formularios adaptables {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Información general {#overview}

AEM Forms permite a los autores de formularios simplificar y mejorar aún más la experiencia de cumplimentación de formularios invocando los servicios configurados en un modelo de datos de formulario desde un campo de formulario adaptable. Para invocar un servicio del modelo de datos, puede crear una regla en el Editor visual o especificar un JavaScript utilizando la API `guidelib.dataIntegrationUtils.executeOperation` en el Editor de código del [Editor de reglas](/help/forms/using/rule-editor.md).

Este documento explica cómo escribir un JavaScript usando la API `guidelib.dataIntegrationUtils.executeOperation` para invocar un servicio.

## Uso de la API {#using-the-api}

La variable `guidelib.dataIntegrationUtils.executeOperation` API invoca un servicio desde un campo de formulario adaptable. La sintaxis de la API es la siguiente:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

La API requiere los siguientes parámetros.

| Parámetro | Descripción |
|---|---|
| `operationInfo` | Estructura para especificar el identificador del modelo de datos de formulario, el título de la operación y el nombre de la operación |
| `inputs` | Estructura para especificar objetos de formulario cuyos valores se introducen en la operación de servicio |
| `outputs` | Estructura para especificar los objetos de formulario que se rellenarán con los valores devueltos por la operación de servicio |

La estructura de la API `guidelib.dataIntegrationUtils.executeOperation` especifica los detalles de la operación del servicio. La sintaxis de la estructura es la siguiente:

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

La estructura de la API especifica los siguientes detalles sobre la operación del servicio.

<table> 
 <tbody> 
  <tr> 
   <th>Parámetro</th> 
   <th>Descripción</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>Especifique la ruta del repositorio al modelo de datos del formulario, incluido su nombre</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>Especificar el nombre de la operación de servicio que se va a ejecutar</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>Asignación de uno o varios objetos de formulario a los argumentos de entrada para la operación de servicio</td> 
  </tr> 
  <tr> 
   <td>Salida</td> 
   <td>Asignación de uno o varios objetos de formulario a valores de salida de la operación de servicio para rellenar campos de formulario<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Script de ejemplo para invocar un servicio {#sample-script-to-invoke-a-service}

El siguiente script de ejemplo utiliza la API `guidelib.dataIntegrationUtils.executeOperation` para invocar la operación de servicio `getAccountById` configurada en el modelo de datos de formulario `employeeAccount`.

La operación `getAccountById` toma el valor del campo del formulario `employeeID` como entrada para el argumento `empId` y devuelve el nombre del empleado y el número y el saldo de la cuenta del empleado correspondiente. Los valores de salida se rellenan en los campos del formulario especificados. Por ejemplo, el valor del argumento `name` se rellena en el elemento de formulario `fullName`, y el valor del argumento `accountNumber` argumento en el elemento de formulario `account`.

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```
