---
title: Generar documento de registro para formularios adaptables
seo-title: Generate Document of Record for adaptive forms
description: Explica cómo se puede generar una plantilla para un documento de registro (DoR) para formularios adaptables.
seo-description: Explains how you can generate a template for a document of record (DoR) for adaptive forms.
uuid: 6c0664a4-a2eb-4ec5-bad0-cf4e2f4fe83d
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 1e533a8c-f200-40ca-b170-0e9abee8513e
noindex: true
feature: Adaptive Forms
exl-id: 2e7944e5-976e-49d2-a8d2-76c5868a92a2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2758'
ht-degree: 18%

---

# Generar documento de registro para formularios adaptables {#generate-document-of-record-for-adaptive-forms}

## Información general {#overview}

Después de enviar un formulario, los clientes generalmente desean mantener un registro, impreso o en formato de documento, de la información que han rellenado en el formulario para su futura referencia. Esto se denomina documento de registro.

En este artículo se explica cómo generar un documento de registro para formularios adaptables.

>[!NOTE]
>
>La generación automática de documentos de registro no es compatible con formularios adaptables basados en XFA. Sin embargo, puede utilizar el XDP utilizado para crear el formulario adaptable como documento de registro.

## Tipos de formularios adaptables y sus documentos de registro {#adaptive-form-types-and-their-documents-of-record}

Al crear un formulario adaptable, puede seleccionar un modelo de formulario. Las opciones son las siguientes:

* [Plantillas de formulario](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)

   Permite seleccionar una plantilla XFA para el formulario adaptable. Al seleccionar una plantilla XFA, puede utilizar el archivo XDP asociado para el documento de registro como se describe anteriormente.

* [Esquema XML](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)

   Permite seleccionar una definición de esquema XML para el formulario adaptable. Al seleccionar un esquema XML para el formulario adaptable, puede:

   * Asocie una plantilla XFA para el documento de registro. Asegúrese de que la plantilla XFA asociada utiliza el mismo esquema XML que el formulario adaptable
   * Generar automáticamente documento de registro

* Ninguno

   Permite crear un formulario adaptable sin un modelo de formulario. El documento de registro se genera automáticamente para el formulario adaptable.

Cuando seleccione un modelo de formulario, configure el documento de registro mediante las opciones disponibles en Configuración de plantilla de documento de registro. Consulte [Documento de configuración de plantilla de registro](#document-of-record-template-configuration).

## Documento de registro generado automáticamente {#automatically-generated-document-of-record}

Un documento de registro permite a los clientes conservar una copia del formulario enviado para su impresión. Cuando se genera automáticamente un documento de registro, cada vez que se cambia el formulario, su documento de registro se actualiza inmediatamente. Por ejemplo, se elimina el campo de edad de los clientes que seleccionan Estados Unidos de América como país. Cuando estos clientes generan un documento de registro, el campo de edad no es visible para ellos en el documento de registro.

El documento de registro generado automáticamente tiene las siguientes ventajas:

* Se encarga del enlace de datos.
* Oculta automáticamente los campos marcados que se excluyen del documento de registro en el momento del envío. No se requiere esfuerzo adicional.
* Ahorra tiempo para diseñar una plantilla de documento de registro.
* Le permite probar diferentes estilos y apariencia utilizando diferentes plantillas base y elegir el mejor estilo y apariencia para el Documento de registro. Las apariencias de estilo son opcionales y, si no se especifica el estilo, los estilos del sistema se establecen de forma predeterminada.
* Garantiza que cualquier cambio en el formulario se refleje inmediatamente en el documento de registro.

## Componentes para generar automáticamente un documento de registro {#components-to-automatically-generate-a-document-of-record}

Para generar un documento de registro para formularios adaptables, se necesitan los siguientes componentes:

**Formulario adaptable** Formulario adaptable para el que se desea generar un documento de registro.

**Plantilla base (recomendada)** Plantilla XFA (archivo XDP) creada en AEM Designer. La plantilla base se utiliza para especificar la información de estilo y marca para la plantilla de documento de registro.

Consulte [Plantilla base de un documento de registro](#base-template-of-a-dor)

>[!NOTE]
>
>La plantilla básica de un documento de registro también se denomina metamotrella de un documento de registro.

**Documento de plantilla de registro** Plantilla XFA (archivo XDP) generada a partir de un formulario adaptable.

Consulte [Documento de configuración de plantilla de registro](#document-of-record-template-configuration).

**Datos de formulario** Información rellenada por un usuario en el formulario adaptable. Se combina con la plantilla de documento de registro para generar el documento de registro.

## Asignación de elementos de formulario adaptables {#mapping-of-adaptive-form-elements}

Las siguientes secciones describen cómo aparecen los elementos de formulario adaptables en el documento de registro.

### Campos {#fields}

<table> 
 <tbody> 
  <tr> 
   <th>Componente de formulario adaptable</th> 
   <th>Componente XFA correspondiente</th> 
   <th>¿Se incluye de forma predeterminada en la plantilla de documento de registro?</th> 
   <th>Notas</th> 
  </tr> 
  <tr> 
   <td>Botón</td> 
   <td>Botón</td> 
   <td>false</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Casilla de verificación</td> 
   <td>Casilla de verificación</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Selector de fecha</td> 
   <td>Campo de fecha y hora</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Lista desplegable</td> 
   <td>Lista desplegable</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Firma manuscrita</td> 
   <td>Firma manuscrita</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Cuadro numérico</td> 
   <td>Campo numérico</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Cuadro de contraseña</td> 
   <td>Campo de contraseña</td> 
   <td>false</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Botón de opción</td> 
   <td>Botón de opción</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Cuadro de texto</td> 
   <td>Campo de texto</td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Botón Restablecer</td> 
   <td>Botón Restablecer</td> 
   <td>false</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Botón Enviar</td> 
   <td><p>Botón de envío por correo electrónico</p> <p>Botón Enviar HTTP</p> </td> 
   <td>false</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Términos y condiciones</td> 
   <td> </td> 
   <td>true</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Archivo adjunto</td> 
   <td> </td> 
   <td>false</td> 
   <td>No disponible en la plantilla de documento de registro. Sólo disponible en documento de registro mediante archivos adjuntos.</td> 
  </tr> 
 </tbody> 
</table>

### Contenedores {#containers}

<table> 
 <tbody> 
  <tr> 
   <th>Componente de formulario adaptable</th> 
   <th>Componente XFA correspondiente</th> 
   <th>Notas</th> 
  </tr> 
  <tr> 
   <td>Panel<br /> </td> 
   <td>Subformulario<br /> </td> 
   <td>El panel repetible se asigna a un subformulario repetible.</td> 
  </tr> 
 </tbody> 
</table>

### Componentes estáticos {#static-components}

| Componente de formulario adaptable | Componente XFA correspondiente | Notas |
|---|---|---|
| Imagen | Imagen | Los componentes TextDraw e Image, tanto enlazados como no enlazados, siempre aparecen en el documento de registro de un formulario adaptable basado en XSD, a menos que se excluya mediante la configuración del documento de registro. |
| Texto | Texto |

>[!NOTE]
>
>En la IU clásica, se obtienen distintas pestañas para editar las propiedades de los campos.

### Tablas {#tables}

Los componentes de tabla de formularios adaptables, como encabezado, pie de página y asignación de filas, corresponden a los componentes XFA correspondientes. Puede asignar paneles repetibles a tablas en documento de registro.

## Plantilla base de un documento de registro {#base-template-of-a-document-of-record}

La plantilla base proporciona información de estilo y apariencia al documento de registro. Permite personalizar el aspecto predeterminado del documento de registro generado automáticamente. Por ejemplo, desea agregar el logotipo de su empresa en el encabezado y la información de copyright en el pie de página del documento de registro. La página de formato de la plantilla base se utiliza como página de formato para la plantilla de documento de registro. La página de formato puede tener información como encabezado de página, pie de página y número de página que se puede aplicar al documento de registro. Puede aplicar dicha información al documento de registro utilizando la plantilla base para la generación automática del documento de registro. El uso de una plantilla base permite cambiar las propiedades predeterminadas de los campos.

Siga [Convenciones de plantilla base](#base-template-conventions) al diseñar la plantilla base.

## Convenciones de plantilla base {#base-template-conventions}

Se utiliza una plantilla base para definir el encabezado, pie de página, estilo y apariencia de un documento de registro. El encabezado y pie de página pueden incluir información como el logotipo de la empresa y la información de copyright. La primera página de formato de la plantilla base se copia y se utiliza como página de formato para el documento de registro, que contiene el encabezado, pie de página, número de página o cualquier otra información que deba aparecer en todas las páginas del documento de registro. Si utiliza una plantilla base que no se ajuste a las convenciones de plantilla base, la primera página de formato de la plantilla base se utilizará en la plantilla de documento de registro. Se recomienda encarecidamente que diseñe la plantilla base según sus convenciones y que la utilice para generar automáticamente el documento de registro.

**Convenciones de la página maestra**

* En la plantilla base, debe asignar un nombre al subformulario raíz como `AF_METATEMPLATE` y la página de formato como `AF_MASTERPAGE`.

* La página de formato con el nombre `AF_MASTERPAGE` ubicado bajo el `AF_METATEMPLATE` el subformulario raíz tiene preferencia para extraer información de encabezado, pie de página y estilo.

* Si `AF_MASTERPAGE` no existe, se utiliza la primera página maestra presente en la plantilla base.

**Convenciones de estilo para campos**

* Para aplicar estilo en los campos del documento de registro, la plantilla base proporciona campos ubicados en la variable `AF_FIELDSSUBFORM` subdesde en el `AF_METATEMPLATE` subformulario raíz.

* Las propiedades de estos campos se aplican a los campos del documento de registro. Estos campos deben seguir la convención de nomenclatura de `AF_<name of field in all caps>_XFO`. Por ejemplo, el nombre de campo de la casilla de verificación debe ser `AF_CHECKBOX_XFO`.

Para crear una plantilla base, haga lo siguiente en AEM Designer.

1. Haga clic en **Archivo > Nuevo**.
1. Seleccione la opción **Basado en una plantilla**.

1. Seleccione la categoría **Formulario - Documento de registro**.
1. Seleccione **Plantilla base de documento de registro**.
1. Haga clic en **Siguiente** y proporcione la información requerida.

1. (Opcional) Modifique el estilo y el aspecto de los campos que desea aplicar en los campos del documento de registro.
1. Guarde el formulario.

Ahora puede utilizar el formulario guardado como plantilla base para el documento de registro.\
No modifique ni elimine ningún script presente en la plantilla base.

**Modificación de la plantilla base**

* Si no aplica ningún estilo a los campos de la plantilla base, es aconsejable eliminar esos campos de la plantilla base para que todas las actualizaciones a la plantilla base se recojan automáticamente.
* Al modificar la plantilla base, no elimine, agregue ni modifique scripts.

>[!NOTE]
>
>Diseñe una plantilla base utilizando convenciones y siguiendo estrictamente los pasos anteriores.

## Configuración de la plantilla de un documento de registro {#document-of-record-template-configuration}

Configure la plantilla de documento de registro del formulario para que sus clientes puedan descargar una copia del formulario enviado que sea fácil de imprimir. Un archivo XDP sirve como documento de la plantilla de registro. El documento de la descarga de los clientes de registro tiene un formato de acuerdo con el diseño especificado en el archivo XDP.

Realice los siguientes pasos para configurar un documento de registro para formularios adaptables:

1. En AEM instancia de autor, haga clic en **Forms > Forms y documentos.**
1. Seleccione un formulario y haga clic en **Ver propiedades**.
1. En la ventana Propiedades, pulse **Modelo de formulario**.

   También puede seleccionar un modelo de formulario al crear un formulario.

   >[!NOTE]
   >
   >En la ficha Modelo de formulario, asegúrese de seleccionar **Esquema** o **Ninguna** de la variable **Seleccionar de** lista desplegable. **[!UICONTROL El documento de registro no es compatible con los formularios adaptables o basados en XFA con la plantilla de formulario como modelo de formulario.]**

1. En la sección Configuración de plantilla de documento de registro de la ficha Modelo de formulario, seleccione una de las siguientes opciones.

   **Ninguna** Seleccione esta opción si no desea configurar el documento de registro para el formulario.

   **Asociar plantilla de formulario como plantilla de documento de registro** Seleccione esta opción si tiene un archivo XDP que desea utilizar como plantilla para el documento de registro. Al seleccionar esta opción, se muestran todos los archivos XDP disponibles en el repositorio de AEM Forms. Seleccione el archivo apropiado.

   El archivo XDP seleccionado se asocia con el formulario adaptable.

   **Generar documento de registro** Seleccione esta opción para utilizar un archivo XDP como plantilla base para definir el estilo y el aspecto del documento de registro. Al seleccionar esta opción, se muestran todos los archivos XDP disponibles en el repositorio de AEM Forms. Seleccione el archivo apropiado.

   **[!UICONTROL Seleccione esta opción para utilizar un archivo XDP como plantilla base para definir el estilo y el aspecto del documento de registro. Al seleccionar esta opción, se muestran todos los archivos XDP disponibles en el repositorio de AEM Forms. Seleccione el archivo apropiado.]**

   **Seleccione Plantilla de Forms como plantilla base para generar Documento de registro** Seleccione esta opción para utilizar un archivo XDP como plantilla base para definir el estilo y el aspecto del documento de registro. Al seleccionar esta opción, se muestran todos los archivos XDP disponibles en el repositorio de AEM Forms. Seleccione el archivo apropiado.

   >[!NOTE]
   >
   >Asegúrese de que el esquema utilizado para crear un formulario adaptable y un esquema (esquema de datos) del formulario XFA sea el mismo si:
   >
   >* El formulario adaptable se basa en esquemas
   >* Utiliza **Asociar plantilla de formulario como plantilla de documento de registro** opción para documento de registro


1. Haga clic en **Listo.**

## Personalización de la información de marca en el documento de registro {#customize-the-branding-information-in-document-of-record}

Durante la generación de un documento de registro, puede cambiar la información de marca del documento de registro en la ficha Documento de registro. La pestaña Documento de registro incluye opciones como logotipo, apariencia, diseño, encabezado y pie de página, exención de responsabilidad y si desea incluir o no las opciones de casillas de verificación y botones de opción no seleccionadas.

Para localizar la información de marca que introduce en la ficha Documento de registro, debe asegurarse de que la configuración regional del explorador esté correctamente configurada. Para personalizar la información de marca del documento de registro, complete los siguientes pasos:

1. Seleccione un panel (panel raíz) en el documento de registro y, a continuación, pulse ![configure](assets/configure.png).
1. Pulse ![dortab](assets/dortab.png). Aparecerá la pestaña Documento de registro.
1. Seleccione la plantilla predeterminada o una plantilla personalizada para procesar el documento de registro. Si selecciona la plantilla predeterminada, aparece una vista previa en miniatura del documento de registro debajo de la lista desplegable Plantilla.

   ![brandingtemplate](assets/brandingtemplate.png)

   Si elige seleccionar una plantilla personalizada, busque y seleccione un XDP en el servidor de AEM Forms. Si desea utilizar una plantilla que no esté ya en el servidor de AEM Forms, primero debe cargar el XDP en el servidor de AEM Forms.

1. En función de si selecciona una plantilla predeterminada o personalizada, algunas o todas las propiedades siguientes aparecen en la ficha Documento de registro. Especifíquelas correctamente:

   * **Imagen del logotipo**: Puede elegir usar la imagen del logotipo desde el formulario adaptable, elegir una de DAM o cargar una desde el equipo.
   * **Título del formulario**
   * **Texto de encabezado**
   * **Etiqueta de la exención de responsabilidad**
   * **Exención de responsabilidad**
   * **Texto de la exención de responsabilidad**
   * **Color de énfasis**: el color en el que se representa el texto del encabezado y las líneas de separación en el documento o registro PDF.
   * **Familia de fuentes**: Familia de fuentes del texto en el PDF del documento de registro
   * **Para componentes de casilla de verificación y botones de radio, mostrar solo los valores seleccionados**
   * **Separador para varios valores seleccionados**
   * **Incluir objetos de formulario que no están enlazados al modelo de datos**
   * **Excluir campos ocultos del documento de registro**
   * **Ocultar descripción de paneles**

   >[!NOTE]
   >
   >Si utiliza una plantilla de formulario adaptable creada con una versión de Designer anterior a la 6.3 para que funcionen las propiedades Color de acento y Familia de fuentes, asegúrese de que lo siguiente está presente en la plantilla de formulario adaptable en el subformulario raíz:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Para guardar los cambios de personalización de marca, pulse Listo.

## Diseños de tablas y columnas para paneles del documento de registro {#table-and-column-layouts-for-panels-in-document-of-record}

El formulario adaptable puede ser largo y tener varios campos de formulario. Es posible que no desee guardar un documento de registro como una copia exacta del formulario adaptable. Ahora puede elegir una tabla o una presentación de columna para guardar uno o más paneles de formulario adaptables en el PDF de documentos.

Antes de generar un documento de registro, en la configuración de un panel, seleccione Presentación del documento de registro para ese panel como Tabla o Columna. Los campos del panel se organizan en consecuencia en el documento de registro.

![Campos de un panel procesado en una presentación de tabla en el documento de registro](assets/dortablelayout.png)

Campos de un panel procesado en una presentación de tabla en el documento de registro

![Campos de un panel procesado en una presentación de columna del documento de registro](assets/dorcolumnlayout.png)

Campos de un panel procesado en una presentación de columna del documento de registro

## Configuración del documento de registro {#document-of-record-settings}

La configuración del documento de registro permite elegir las opciones que desea incluir en el documento de registro. Por ejemplo, un banco acepta el nombre, la edad, el número de la seguridad social y el número de teléfono en un formulario. El formulario genera un número de cuenta bancaria y detalles de sucursal. Puede elegir mostrar únicamente el nombre, el número de la seguridad social, la cuenta bancaria y los detalles de sucursal en el documento de registro.

El documento de configuración de registro de un componente está disponible en sus propiedades. Para acceder a las propiedades de un componente, seleccione el componente y haga clic en ![cmppr](assets/cmppr.png) en la superposición. Las propiedades se enumeran en la barra lateral y puede encontrar la siguiente configuración en ella.

**Configuración del nivel de campo**

* **Excluir Del Documento De Registro**: Si se establece la propiedad true, se excluye el campo del documento de registro. Se trata de una propiedad que puede ser script y que se llama `excludeFromDoR`. Su comportamiento depende de la propiedad de nivel de formulario **Excluir campos del documento de registro si están ocultos**.

* **Mostrar panel como tabla:** Al establecer la propiedad, se muestra el panel como tabla en el documento de registro si el panel tiene menos de 6 campos. Solo aplicable para paneles.
* **Excluir título del documento de registro:** La configuración de la propiedad excluye el título del panel o tabla del documento de registro. Aplicable solo para paneles y tablas.
* **Excluir descripción del documento de registro:** La configuración de la propiedad excluye la descripción del panel/tabla del documento de registro. Aplicable solo para paneles y tablas.

**Configuración del nivel de formulario**

* **Incluir campos no enlazados en DoR:** La configuración de la propiedad incluye campos no enlazados del formulario adaptable basado en esquema del documento de registro. De forma predeterminada, es True.
* **Excluir campos del documento de registro si están ocultos:** al establecer la propiedad, se anula el comportamiento de la propiedad de nivel de campo “Excluir del documento de registro” cuando no es True. Si los campos están ocultos en el momento del envío del formulario, se excluirán del documento de registro si la propiedad está establecida en true, siempre que la propiedad &quot;Excluir del documento de registro&quot; no esté establecida.

## Consideraciones clave al trabajar con un documento de registro {#key-considerations-when-working-with-document-of-record}

Tenga en cuenta las siguientes consideraciones y limitaciones al trabajar en el documento de registro para formularios adaptables.

* Las plantillas de documento de registro no admiten texto enriquecido. Por lo tanto, cualquier texto enriquecido del formulario adaptable estático o de la información rellenada por el usuario final aparece como texto sin formato en el documento de registro.
* Los fragmentos de documento en un formulario adaptable no aparecen en el documento de registro. Sin embargo, se admiten fragmentos de formulario adaptables.
* el documento de registro se utiliza sólo para imprimir.
* No se admite el enlace de contenido en el documento de registro generado para el formulario adaptable basado en el esquema XML.
* No se admite el enlace de contenido en el documento de registro generado para el formulario adaptable basado en el esquema XML.
* La versión localizada del documento de registro se crea bajo demanda para una configuración regional cuando el usuario solicita la renderización del documento de registro. La localización del documento de registro se produce junto con la localización del formulario adaptable. Para obtener más información sobre la localización de documentos de registro y formularios adaptables, consulte [Uso de AEM flujo de trabajo de traducción para localizar formularios adaptables y documento de registro](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).
