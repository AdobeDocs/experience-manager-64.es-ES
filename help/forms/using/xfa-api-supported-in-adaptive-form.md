---
title: Compatibilidad con XFA en formularios adaptables basados en XDP
seo-title: XFA support in XDP-based adaptive forms
description: Enumera los eventos XFA admitidos, las propiedades, los scripts y la validación en los formularios adaptables.
seo-description: Lists supported XFA events, properties, scripts, and validation in adaptive forms.
uuid: 2f976de3-2cdf-4bbb-acd1-048a498930f0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: eaf60421-097e-4feb-b661-433a512470ab
feature: Adaptive Forms
exl-id: 86596819-8108-409e-af14-4634e8a1959d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 96%

---

# Compatibilidad con XFA en formularios adaptables basados en XDP {#xfa-support-in-xdp-based-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Los formularios adaptables son compatibles con varios eventos, propiedades, scripts y validaciones XFA definidos en un archivo XDP, incluidos los siguientes:

* ejecución de los scripts definidos en los eventos del archivo XDP;
* captura de los valores y las propiedades de comportamiento predeterminados para los campos del archivo XDP;
* ejecución de los scripts de validación definidos en el archivo XDP.

Cuando se crea un formulario adaptable basado en un archivo XDP, las propiedades, los eventos y las validaciones se rellenan automáticamente en la interfaz de usuario de Autor del formulario. Sin embargo, los autores de formularios pueden invalidar algunos de estos elementos para crear una experiencia alternativa.

Este artículo enumera los eventos, las propiedades y las validaciones XFA admitidos en los formularios adaptables, y explica cómo anularlos.

## Elementos XFA compatibles y su asignación en formularios adaptables {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Campos {#fields}

Cuando se crea un formulario adaptable con un archivo XDP, se puede arrastrar y colocar un campo XFA en él. En la tabla siguiente se muestra cómo se asignan los campos XFA a los campos de formulario adaptable.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Campo o contenedor XFA</strong></p> </td> 
   <td><p><strong>Componente del formulario adaptable correspondiente</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Botón </p> </td> 
   <td><p>Botón</p> </td> 
  </tr>
  <tr>
   <td><p>Casilla de verificación </p> </td> 
   <td><p>Casilla de verificación</p> </td> 
  </tr>
  <tr>
   <td><p>Cuadro de lista </p> </td> 
   <td><p>Lista desplegable</p> </td> 
  </tr>
  <tr>
   <td><p>Campo de fecha y hora </p> </td> 
   <td><p>Selector de fecha</p> </td> 
  </tr>
  <tr>
   <td><p>Firma manuscrita</p> </td> 
   <td><p>Firma manuscrita</p> </td> 
  </tr>
  <tr>
   <td><p>Campo numérico </p> </td> 
   <td><p>Cuadro numérico</p> </td> 
  </tr>
  <tr>
   <td><p>Campo decimal</p> </td> 
   <td><p>Cuadro numérico</p> </td> 
  </tr>
  <tr>
   <td><p>Campo de texto </p> </td> 
   <td><p>Cuadro de texto</p> </td> 
  </tr>
  <tr>
   <td><p>Campo de contraseña </p> </td> 
   <td><p>Cuadro de contraseña</p> </td> 
  </tr>
  <tr>
   <td><p>Imagen</p> </td> 
   <td><p>Imagen</p> </td> 
  </tr>
  <tr>
   <td><p>Texto</p> </td> 
   <td><p>Texto</p> </td> 
  </tr>
  <tr>
   <td><p>Subformulario </p> </td> 
   <td><p>Panel</p> </td> 
  </tr>
  <tr>
   <td><p>Área (grupo)</p> </td> 
   <td><p>Panel</p> </td> 
  </tr>
  <tr>
   <td><p>Conjunto de subformularios </p> </td> 
   <td><p>Panel</p> </td> 
  </tr>
 </tbody>
</table>

### Propiedades {#properties}

La siguiente tabla muestra cómo se comportan los distintos scripts XFA definidos en archivos XDP en los formularios adaptables.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Propiedades de los componentes XFA</strong></p> </td> 
   <td><p><strong>Comportamiento correspondiente en formularios adaptables</strong></p> </td> 
  </tr>
  <tr>
   <td><p>somExpression </p> </td> 
   <td><p>Asignado a la propiedad Bind reference (bindRef) en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>presence </p> </td> 
   <td><p>Asignado a la propiedad visible en el formulario adaptable. Puede anularlo utilizando la expresión Visibility.</p> </td> 
  </tr>
  <tr>
   <td><p>access </p> </td> 
   <td><p>Asignado a la propiedad enabled en el formulario adaptable. Puede anularlo utilizando la expresión Access.</p> </td> 
  </tr>
  <tr>
   <td><p>Accesibilidad: función </p> </td> 
   <td><p>Asignado a la propiedad role en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>Accesibilidad: speakPriority </p> </td> 
   <td><p>Asignado a la propiedad speakPriority en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>Accesibilidad: speakText</p> </td> 
   <td><p>Asignado al texto de accesibilidad personalizado en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>Accesibilidad: toolTip </p> </td> 
   <td><p>Asignado a la propiedad Short description en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>caption<em> (Todos los tipos de campo)</em></p> </td> 
   <td><p>Asignado a la propiedad Title en Formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>displayFormat<em> (Todos los tipos de campo)</em></p> </td> 
   <td><p>Asignado al patrón de visualización en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>rawValue<em> (Todos los tipos de campo)</em></p> </td> 
   <td><p>Asignado a la propiedad value en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>items<em> (Cuadro de lista, casilla de verificación)</em></p> </td> 
   <td><p>Asignado a la propiedad options en el formulario adaptable. Puede anularlo utilizando la expresión Options.</p> </td> 
  </tr>
  <tr>
   <td><p>maxChar<em> (Campo de texto)</em></p> </td> 
   <td><p>Asignado a la propiedad Maximum character allowed en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>multiline<em> (Campo de texto)</em></p> </td> 
   <td><p>Asignado a la propiedad Allow multiple lines en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>fracDigit<em> (Campo numérico, Campo decimal)</em></p> </td> 
   <td><p>Asignado a la propiedad Frac digit en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>leadDigit<em> (Campo numérico, Campo decimal)</em></p> </td> 
   <td><p>Asignado a la propiedad Lead digits en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>multiSelect<em> (Cuadro de lista)</em></p> </td> 
   <td><p>Asignado a la propiedad Allows multiple selection en el formulario adaptable.</p> </td> 
  </tr>
 </tbody>
</table>

### Scripts {#scripts}

La siguiente tabla muestra cómo se comportan los distintos scripts XFA definidos en archivos XDP en los formularios adaptables.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Eventos de script XFA</strong></p> </td> 
   <td><p><strong>Comportamiento correspondiente en formularios adaptables</strong></p> </td> 
  </tr>
  <tr>
   <td><p>initialize </p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>calculate</p> </td> 
   <td><p>Asignado a la expresión Calculate en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>validate </p> </td> 
   <td><p>Asignado a la expresión Validation en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>validationState </p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.<br /> </p> </td> 
  </tr>
  <tr>
   <td><p>exit </p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>click (Campos de botón)</p> </td> 
   <td><p>Asignado a la expresión Click del botón.</p> </td> 
  </tr>
  <tr>
   <td><p>Compatibilidad con scripts del lado del servidor</p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>Compatibilidad con servicios web</p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.</p> </td> 
  </tr>
  <tr>
   <td><p>change (Campo de anotaciones, botón de opción, casilla de verificación)</p> </td> 
   <td><p>Este script se ejecuta durante el tiempo de ejecución y no se puede anular en el formulario adaptable.</p> </td> 
  </tr>
 </tbody>
</table>

### Validaciones {#validations}

La siguiente tabla muestra cómo se asignan las validaciones XFA a las validaciones de los formularios adaptables.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Validación XFA</strong></p> </td> 
   <td><p><strong>Validación correspondiente en el formulario adaptable</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Patrón de validación (formatTest)</p> </td> 
   <td><p>validatePictureClause</p> </td> 
  </tr>
  <tr>
   <td><p>Mensaje del patrón de validación (formatTestMessage)</p> </td> 
   <td><p>validatePictureMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Obligatorio (nullTest)</p> </td> 
   <td><p>mandatory </p> </td> 
  </tr>
  <tr>
   <td><p>Mensaje vacío (nullTestMessage) </p> </td> 
   <td><p>mandatoryMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Validar script (scriptTest)</p> </td> 
   <td><p>validateExp</p> </td> 
  </tr>
  <tr>
   <td><p>Mensaje del script de validación (scriptTestMessage)</p> </td> 
   <td><p>validateMessage</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>No se puede anular la propiedad mandatory del grupo de botones de opción y de casillas de verificación del formulario adaptable enlazados a los botones de verificación XFA.
