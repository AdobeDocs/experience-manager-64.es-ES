---
title: Creación de formularios adaptables mediante el esquema JSON
seo-title: Creación de formularios adaptables mediante el esquema JSON
description: 'Los formularios adaptables pueden utilizar el esquema JSON como modelo de formulario, lo que le permite aprovechar los esquemas JSON existentes para crear formularios adaptables. '
seo-description: 'Los formularios adaptables pueden utilizar el esquema JSON como modelo de formulario, lo que le permite aprovechar los esquemas JSON existentes para crear formularios adaptables. '
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 4%

---


# Creación de formularios adaptables mediante el esquema JSON {#creating-adaptive-forms-using-json-schema}

## Requisitos previos {#prerequisites}

La creación de un formulario adaptable utilizando un esquema JSON como modelo de formulario requiere una comprensión básica del esquema JSON. Se recomienda leer el siguiente contenido antes de este artículo.

* [Creación de un formulario adaptable](/help/forms/using/creating-adaptive-form.md)
* [Esquema JSON](https://json-schema.org/)

## Uso de un esquema JSON como modelo de formulario {#using-a-json-schema-as-form-model}

AEM Forms admite la creación de un formulario adaptable mediante el uso de un esquema JSON existente como modelo de formulario. Este esquema JSON representa la estructura en la que el sistema back-end de su organización produce o consume datos. El esquema JSON que utilice debe cumplir con las especificaciones [v4](https://json-schema.org/draft-04/schema).

Las características clave del uso de un esquema JSON son:

* La estructura del JSON se muestra como un árbol en la pestaña Buscador de contenido en el modo de creación de un formulario adaptable. Puede arrastrar y agregar un elemento de la jerarquía JSON al formulario adaptable.
* Puede rellenar previamente el formulario utilizando JSON que cumpla con el esquema asociado.
* Al enviar, los datos introducidos por el usuario se envían como JSON que se adhieren al esquema asociado.

Un esquema JSON consta de tipos de elementos simples y complejos. Los elementos tienen atributos que agregan reglas al elemento. Cuando estos elementos y atributos se arrastran a un formulario adaptable, se asignan automáticamente al componente de formulario adaptable correspondiente.

Esta asignación de elementos JSON con componentes de formulario adaptables es la siguiente:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Elemento, propiedades o atributos JSON</strong></th> 
   <th><strong>Componente de formulario adaptable</strong></th> 
  </tr> 
  <tr> 
   <td><p>Propiedades de cadena con restricción enum y enumNames.</p> <p>Sintaxis,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td><p>Componente desplegable:</p> 
    <ul> 
     <li>Los valores enumerados en enumNames se muestran en el cuadro desplegable.</li> 
     <li>Los valores enumerados en la enumeración se utilizan para el cálculo.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Propiedad de cadena con restricción de formato. Por ejemplo, correo electrónico y fecha.</p> <p>Sintaxis,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>El componente Correo electrónico se asigna cuando el tipo es cadena y el formato es correo electrónico.</li> 
     <li>El componente de cuadro de texto con validación se asigna cuando el tipo es cadena y el formato es nombre de host.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Campo de texto<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>number, propiedad<br /> </td> 
   <td>Campo numérico con subtipo definido como flotante<br /> </td> 
  </tr> 
  <tr> 
   <td>integer property<br /> </td> 
   <td>Campo numérico con subtipo definido como entero<br /> </td> 
  </tr> 
  <tr> 
   <td>propiedad booleana<br /> </td> 
   <td>Cambiar<br /> </td> 
  </tr> 
  <tr> 
   <td>propiedad object<br /> </td> 
   <td>Panel<br /> </td> 
  </tr> 
  <tr> 
   <td>propiedad array</td> 
   <td>Panel repetible con mínimo y máximo igual a minItems y maxItems respectivamente. Solo se admiten matrices homogéneas. Por lo tanto, la restricción de elementos debe ser un objeto y no una matriz.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Propiedades de esquema comunes {#common-schema-properties}

El formulario adaptable utiliza la información disponible en el esquema JSON para asignar cada campo generado. En particular:

* La propiedad title sirve como etiqueta para los componentes de formulario adaptables.
* La propiedad description se define como una descripción larga para un componente de formulario adaptable.
* La propiedad predeterminada sirve como valor inicial de un campo de formulario adaptable.
* La propiedad maxLength se establece como atributo maxlength del componente de campo de texto.
* Las propiedades Minimum, Maximum, UniqueMinimum y exclusivoMaximum se utilizan para el componente Cuadro numérico.
* Para admitir el intervalo para el componente DatePicker, se proporcionan las propiedades adicionales del esquema JSON minDate y maxDate .
* Las propiedades minItems y maxItems se utilizan para restringir el número de elementos/campos que se pueden agregar o eliminar de un componente de panel.
* La propiedad readOnly establece el atributo de sólo lectura de un componente de formulario adaptable.
* La propiedad requerida marca el campo de formulario adaptable como obligatorio, mientras que en el caso de panel (donde el tipo es objeto), los datos JSON enviados finales tienen campos con el valor vacío correspondiente a ese objeto.
* La propiedad pattern se define como el patrón de validación (expresión regular) en forma adaptable.
* La extensión del archivo de esquema JSON debe conservarse como .schema.json. Por ejemplo, &lt;filename>.schema.json.

## Ejemplo de esquema JSON {#sample-json-schema}

Este es un ejemplo de esquema JSON.

```
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Definiciones de esquema reutilizables {#reusable-schema-definitions}

Las claves de definición se utilizan para identificar esquemas reutilizables. Las definiciones de esquema reutilizables se utilizan para crear fragmentos. Es similar a identificar tipos complejos en XSD. A continuación se muestra un ejemplo de esquema JSON con definiciones:

```
{
  "$schema": "https://json-schema.org/draft-04/schema#",
 
  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },
 
  "type": "object",
 
  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

El ejemplo anterior define un registro de cliente, en el que cada cliente tiene una dirección de envío y de facturación. La estructura de ambas direcciones es la misma (las direcciones tienen una dirección de calle, una ciudad y un estado), por lo que es aconsejable no duplicar las direcciones. También facilita la adición y eliminación de campos para cualquier cambio futuro.

## Preconfiguración de campos en la definición de esquema JSON {#pre-configuring-fields-in-json-schema-definition}

Puede utilizar la propiedad **aem:afProperties** para preconfigurar el campo Esquema JSON para asignarlo a un componente de formulario adaptable personalizado. A continuación se muestra un ejemplo:

```
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Límite de valores aceptables para un componente de formulario adaptable {#limit-acceptable-values-for-an-adaptive-form-component}

Puede añadir las siguientes restricciones a los elementos del esquema JSON para limitar los valores aceptables para un componente de formulario adaptable:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Propiedad Schema</strong></p> </td> 
   <td><p><strong>Tipo de datos</strong></p> </td> 
   <td><p><strong>Descripción</strong></p> </td> 
   <td><p><strong>Componente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>maximum</code></p> </td> 
   <td><p>Cadena</p> </td> 
   <td><p>Especifica el límite superior de los valores numéricos y las fechas. De forma predeterminada, se incluye el valor máximo.</p> </td> 
   <td> 
    <ul> 
     <li>Cuadro numérico</li> 
     <li>Stepper numérico<br /> </li> 
     <li>Selector de fecha</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minimum</code></p> </td> 
   <td><p>Cadena</p> </td> 
   <td><p>Especifica el límite inferior de valores numéricos y fechas. De forma predeterminada, se incluye el valor mínimo.</p> </td> 
   <td> 
    <ul> 
     <li>Cuadro numérico</li> 
     <li>Stepper numérico</li> 
     <li>Selector de fecha</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMaximum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Si es true, el valor numérico o la fecha especificados en el componente del formulario deben ser menores que el valor numérico o la fecha especificados para la propiedad máxima.</p> <p>Si es false, el valor numérico o la fecha especificados en el componente del formulario deben ser menores o iguales que el valor numérico o la fecha especificados para la propiedad maximum.</p> </td> 
   <td> 
    <ul> 
     <li>Cuadro numérico</li> 
     <li>Stepper numérico</li> 
     <li>Selector de fecha</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMinimum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Si es true, el valor numérico o la fecha especificados en el componente del formulario deben ser buenos que el valor numérico o la fecha especificados para la propiedad Minimum.</p> <p>Si es false, el valor numérico o la fecha especificados en el componente del formulario deben ser buenos o iguales al valor numérico o la fecha especificados para la propiedad Minimum.</p> </td> 
   <td> 
    <ul> 
     <li>Cuadro numérico</li> 
     <li>Stepper numérico</li> 
     <li>Selector de fecha</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minLength</code></p> </td> 
   <td><p>Cadena</p> </td> 
   <td><p>Especifica el número mínimo de caracteres permitidos en un componente. La longitud mínima debe ser igual o buena que cero.</p> </td> 
   <td> 
    <ul> 
     <li>Cuadro de texto</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>maxLength</code></td> 
   <td>Cadena</td> 
   <td>Especifica el número máximo de caracteres permitidos en un componente. La longitud máxima debe ser igual o buena a cero.</td> 
   <td> 
    <ul> 
     <li>Cuadro de texto</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>Cadena</p> </td> 
   <td><p>Especifica la secuencia de los caracteres. Un componente acepta los caracteres si se ajustan al patrón especificado.</p> <p>La propiedad pattern se asigna al patrón de validación del componente de formulario adaptable correspondiente.</p> </td> 
   <td> 
    <ul> 
     <li>Todos los componentes de formularios adaptables asignados a un esquema XSD </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Cadena</td> 
   <td>Especifica el número máximo de elementos de una matriz. Los elementos máximos deben ser iguales o buenos a cero.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Cadena</td> 
   <td>Especifica el número mínimo de artículos de una matriz. Los elementos mínimos deben ser iguales o buenos que cero.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## Construcciones no compatibles {#non-supported-constructs}

Los formularios adaptables no admiten las siguientes construcciones de esquema JSON:

* Tipo nulo
* Tipos de unión, como cualquier, y
* OneOf, AnyOf, AllOf y NOT
* Solo se admiten matrices homogéneas. Por lo tanto, la restricción de elementos debe ser un objeto y no una matriz.

## Preguntas frecuentes {#frequently-asked-questions}

**¿Por qué no puedo arrastrar elementos individuales de un subformulario (estructura generada a partir de cualquier tipo complejo) para subformularios repetibles (los valores minOccours o maxOccurs son buenos a 1)?**

En un subformulario repetible, debe utilizar el subformulario completo. Si solo desea campos selectivos, utilice toda la estructura y elimine los no deseados.

**Tengo una estructura compleja y larga en el Buscador de Contenido. ¿Cómo puedo encontrar un elemento específico?**

Tiene dos opciones:

* Desplácese por la estructura de árbol
* Utilice el cuadro Buscar para buscar un elemento

