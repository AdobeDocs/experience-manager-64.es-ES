---
title: Preguntas más frecuentes sobre formularios HTML5
seo-title: Frequently asked questions (FAQ) for HTML5 forms
description: Preguntas más frecuentes sobre la presentación, la compatibilidad con scripts y el ámbito de los formularios HTML5.
seo-description: Frequently Asked Questions (FAQ) about layout, scripting support, and scope of HTML5 forms.
uuid: 55d8cc65-ddf1-48bd-8307-06f562ee8c3a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: fbe70162-ced6-4989-9322-e12772edbcbc
feature: Mobile Forms
exl-id: b7f0b209-3970-49ad-a1d8-5a053be0d2bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 85%

---

# Preguntas más frecuentes sobre formularios HTML5 {#frequently-asked-questions-faq-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Existen preguntas más frecuentes (FAQ) sobre la presentación, la compatibilidad con scripts y el ámbito de los formularios HTML5.

## Diseño {#layout}

1. ¿Por qué los códigos de barras y los campos de firma no aparecen en mi formulario?

   Respuesta: Los campos de códigos de barras y firmas no son relevantes en los escenarios HTML o móviles. Estos campos aparecen como un área no interactiva. Sin embargo, AEM Forms Designer proporciona un nuevo campo de garabato de firma que se puede utilizar en lugar del campo de firma. También se puede agregar un [widget personalizado](/help/forms/using/custom-widgets.md) para códigos de barras e integrarlo.

1. ¿Se admite texto enriquecido para el campo de texto XFA?

   Respuesta: El campo XFA, que permite contenido enriquecido en AEM Forms Designer, no es compatible y se representa como texto normal sin que sea posible aplicarle estilo desde la interfaz de usuario. Además, los campos XFA con propiedad comb se muestran como un campo normal, aunque aún hay restricciones en el número de caracteres permitidos en función del valor de los dígitos comb.

1. ¿Existen limitaciones en cuanto al uso de subformularios repetibles?

   Respuesta: Los subformularios repetibles deben tener un recuento inicial de 1 o más. Los subformularios repetibles con un recuento inicial de cero no son compatibles. También puede utilizar un subformulario repetible y no mostrarlo cuando se cargue el formulario. Para conseguir el caso de uso:

   1. Defina el recuento inicial del subformulario repetible en 1.

      ![intial-count](assets/intial-count.png)

   1. Utilice el evento initialize del formulario para ocultar la instancia principal del subformulario. Por ejemplo, el siguiente código oculta la instancia principal del subformulario al inicializarlo. También comprueba el tipo de aplicación para garantizar que el script se ejecute únicamente en el lado del cliente:

      ```
      if ((xfa.host.appType == "HTML 5" || xfa.host.appType == "Exchange-Pro" || xfa.host.appType == "Reader")&&(_RepeatSubform.count == 1)&&(form1.Page1.Subform1.RepeatSubform.Key.rawValue == null)) {
      RepeatSubform.presence = "hidden";
      }  
      ```

   1. Abra el script para agregar una instancia del subformulario para editar. Agregue el código como se muestra a continuación para agregar una instancia del script del subformulario.

      El siguiente código comprueba la instancia oculta del subformulario. Si se encuentra la instancia oculta del subformulario, elimínela e inserte una nueva instancia del subformulario. Si no encuentra la instancia oculta del subformulario, simplemente inserte una nueva instancia.

      ```
      if (RepeatSubform.presence == "hidden")
      { 
      RepeatSubform.instanceManager.insertInstance(0);
      RepeatSubform.instanceManager.removeInstance(1);
      }
      else
      {
      RepeatSubform.instanceManager.addInstance(1);
      }
      ```

   1. Abra el script para quitar una instancia del subformulario y editarla. Agregue el código como se indica a continuación para quitar una instancia del script del subformulario.

      El código comprueba el recuento de los subformularios. Si el recuento del subformulario alcanza 1, el código oculta el subformulario en lugar de eliminarlo.

      ```
      if (RepeatSubform.instanceManager.count == 1) {
      RepeatSubform.presence = "hidden";
      } else {
      RepeatSubform.instanceManager.removeInstance(RepeatSubform.instanceManager.count - 1);
      }
      ```

   1. Abra el evento de envío previo del formulario para editarlo. Agregue el siguiente script al evento para quitar la instancia oculta del script antes de editar. Evita enviar datos del subformulario ocultos al enviarlo.

      ```
      if(RepeatSubform.instanceManager.count == 1 && RepeatSubform.presence == "hidden") {
      RepeatSubform.instanceManager.removeInstance(0);
      }
      ```

1. ¿Existen limitaciones en cuanto al uso de subformularios ocultos?

   Respuesta: Un subformulario oculto con una jerarquía compleja que se divide entre páginas causa problemas de diseño. Una solución consiste en marcar el subformulario como visible inicialmente y luego ocultarlo en un script de inicialización basado en alguna lógica o datos.

1. ¿Por qué parte del texto está truncado o se muestra incorrectamente en HTML5?

   Respuesta: Cuando no se ha dado espacio suficiente a un elemento de texto Dibujar o Pie de ilustración para mostrar contenido, el texto aparecerá truncado en la representación de formularios móviles. Este truncamiento también está visible en la vista Diseño de AEM Forms Designer. Aunque este truncamiento se puede controlar en los PDF, no se puede administrar en los formularios HTML5. Para evitar el problema, proporcione espacio suficiente para Dibujar o Pie de ilustración para que no se trunque en el modo de diseño de AEM Forms Designer.

1. Veo problemas de diseño relacionados con la falta de contenido o contenido superpuesto. ¿Por qué ocurre esto?

   Respuesta: Si hay un elemento Dibujar texto o Dibujar imagen junto con otro elemento superpuesto en la misma posición (por ejemplo, un rectángulo), el contenido Dibujar texto no estará visible si se presenta más adelante en el orden del documento (en la vista Jerarquía de AEM Forms Designer). El PDF admite capas transparentes, pero los HTML/exploradores no las admiten.

1. ¿Por qué algunas fuentes se muestran en el formulario HTML de forma diferente a las utilizadas al diseñar el formulario?

   Respuesta: Los formularios HTML5 no incrustan fuentes (a diferencia de los PDF forms en los que las fuentes están incrustadas dentro del formulario). Para que la versión HTML del formulario se represente como se espera, asegúrese de que las fuentes especificadas en el XDP estén disponibles en el servidor y en el equipo cliente. Si las fuentes requeridas no están disponibles en el servidor, se utilizan fuentes de reserva. Además, si utiliza fuentes en la plantilla de formulario que no están disponibles en el dispositivo cliente, se utilizarán las fuentes predeterminadas del explorador para procesar el texto.

1. ¿Se admiten los atributos vAlign y hAlign en los formularios HTML?

   Sí, se admiten los atributos vAlign y hAlign . El atributo vAlign no es compatible con Internet Explorer ni con los campos multilínea.

1. ¿Los formularios HTML5 admiten caracteres hebreos?

   Los formularios de HTML5 admiten caracteres hebreos en todos los navegadores excepto en Microsoft Internet Explorer.

1. ¿Los formularios HTML5 tienen limitaciones en los campos numéricos?

   Respuesta: Sí, los formularios HTML5 tienen algunas limitaciones. Si el número de dígitos es mayor que el recuento especificado en la cláusula de formato, los números no se localizarán y se mostrarán en la configuración regional en inglés.

1. ¿Por qué los formularios HTML son más grandes que los PDF?

   Para procesar un XDP en un formulario de HTML, se requieren muchas estructuras de datos intermedias y objetos como dom de formulario, dom de datos y dom de presentación.

   Para los formularios PDF, Adobe Acrobat tiene un motor XTG integrado para crear objetos y estructuras de datos intermedias. Acrobat también se encarga del diseño y de los scripts.

   Para los formularios HTML5, los exploradores no tienen ningún motor XTG incorporado para crear estructuras de datos intermedias y objetos a partir de bytes XDP sin procesar. Por tanto, para los formularios HTML5, las estructuras intermedias se generan en el servidor y se envían al cliente. En el cliente, el script basado en javascript y el motor de diseño utilizan estas estructuras intermedias.

   El tamaño de la estructura intermedia depende del tamaño del XDP original y de los datos combinados con el XDP.

1. ¿Hay alguna limitación con respecto al uso de tablas en mi xdp?

   Respuesta: Las tablas complejas causan problemas en el procesamiento.

   * No se admite la sección (SubformSet) dentro de una tabla.
   * Las filas de encabezado o pie de página de algunas tablas se marcan para repetición. Dividir estas tablas en varias páginas puede dar algunos problemas.

1. ¿Las tablas accesibles tienen limitaciones?

   Respuesta: Sí, las tablas accesibles tienen las siguientes limitaciones:

   * No se admiten tablas anidadas ni subformularios dentro de una tabla.
   * Los encabezados solo se admiten para las columnas superior o izquierda de la tabla. Los encabezados no son compatibles con los elementos de la tabla intermedia. Puede aplicar encabezados a varios encabezados de fila y columna siempre que se admitan todas estas filas y columnas junto con la fila superior o la columna situada más a la izquierda de la tabla.
   * `Rowspan` y `colspan` no se admiten desde una ubicación aleatoria dentro de la tabla.
   * No se puede agregar ni eliminar dinámicamente la instancia de filas que contienen elementos con un valor de extensión mayor a 1.

1. ¿Cuál es el orden de lectura de la información del objeto y el pie de ilustración para los lectores de pantalla?

   * Cuando están presentes tanto el pie de ilustración como la información del objeto, se lee solamente el pie de ilustración. Si el pie de ilustración no está disponible, se lee la información del objeto. También puede especificar la prioridad para la lectura en un XDP mediante Forms Designer 
   * Cuando pasa el ratón por encima de un elemento, se muestra la información del objeto. Si la información del objeto no está disponible, se muestra texto de voz. Si el texto de voz no está disponible, se muestra el nombre del campo.

1. Cuando pasa el ratón por encima de un campo, se muestra la información del objeto. ¿Cómo deshabilitarlo?

   Para desactivar la información del objeto al pasar el cursor por encima, seleccione ninguna en el panel de accesibilidad de Designer.

1. En Designer, los usuarios pueden configurar las propiedades de apariencia personalizadas del botón de radio y las casillas de verificación. ¿Los formularios HTML5 tienen en cuenta estas propiedades de apariencia personalizadas al procesar los formularios?

   Respuesta: Los formularios HTML5 ignoran las propiedades de apariencia personalizadas del botón de radio y de las casillas de verificación. Los botones de radio y las casillas de verificación aparecen según las especificaciones del explorador subyacente.

1. Cuando se abre un formulario HTML5 en un explorador compatible, el borde de los campos colocados de forma adyacente no se alinea correctamente o los subformularios aparecen superpuestos. Cuando se obtiene una vista previa del mismo formulario HTML5 en Forms Designer, los campos y la presentación no aparecen mal alineados y los subformularios aparecen en la posición correcta. ¿Cómo solucionar el problema?

   Cuando un subformulario está configurado con una posición variable del contenido y el subformulario tiene un elemento de borde oculto, el borde de los campos colocados adyacentemente no se alinea correctamente o los subformularios parecen superpuestos. Para resolver el problema, puede quitar o comentar el elemento oculto &lt;border> del XDP correspondiente. Por ejemplo, el siguiente elemento &lt;border> está marcado como un comentario:

   ```xml
               <!--<border>
                  <edge presence="hidden"/>
                  <corner thickness="0.175mm" presence="hidden"/>
               </border> -->
   ```

## Crear scripts {#scripting}

1. ¿Existen limitaciones en la implementación de JavaScript para HTML Forms?

   Respuesta:

   * La compatibilidad con el script xfa.connectionSet es limitada. Para connectionSet, solo se admite la invocación del servicio web en el lado del servidor. Para obtener información detallada, consulte [Compatibilidad de scritps](/help/forms/using/scripting-support.md).
   * No se admiten $record ni $data en scripts del lado del cliente. Sin embargo, si los scripts se escriben en un bloque formReady, layoutReady, seguirán funcionando porque se ejecutan en el servidor.
   * No se admiten scripts específicos de elementos XFA Draw, como cambiar el texto Dibujar (o el texto del Pie de ilustración en el caso de campos).

1. ¿Hay alguna limitación en el uso de formCalc?

   Respuesta: Actualmente solo se implementa un subconjunto de los scripts formCalc. Para obtener información detallada, consulte [Compatibilidad de scritps](/help/forms/using/scripting-support.md).

1. ¿Existe alguna convención de nombres recomendada y hay alguna palabra clave reservada que se pueda evitar?

   * En AEM Forms Designer, se recomienda no comenzar el nombre de un objeto (como un subformulario o un campo de texto) con un guion bajo (_). Para utilizar guiones bajos al principio del nombre, agregue un prefijo después del guión bajo, *_&lt;prefix>&lt;objectname>. *
   * Todas las API de formularios HTML5 son palabras clave reservadas. Para las API y funciones personalizadas, utilice un nombre que no sea idéntico al de las [API de formularios HTML5](/help/forms/using/scripting-support.md).

1. ¿Los formularios HTML5 admiten campos flotantes?

   Sí, HTML5 Forms admite campos flotantes. Para habilitar los campos flotantes, agregue la siguiente propiedad al perfil de procesamiento:

   >[!NOTE]
   >
   >De forma predeterminada, los campos no están habilitados para flotar. Puede utilizar Forms Designer para establecer la propiedad flotante de los campos.

   1. Abra la lista CRXde y navegue hasta el nodo `/content/xfaforms/profiles/default`.
   1. Agregue una propiedad `mfDataDependentFloatingField` de tipo Cadena y establezca el valor de la propiedad en `true`**.**
   1. Haga clic en **Guardar todo**. Ahora los campos flotantes están habilitados para los formularios HTML mediante el perfil de procesamiento actualizado.

      >[!NOTE]
      >
      >Para habilitar campos flotantes para un formulario específico sin actualizar el perfil de procesamiento, pase la propiedad mfDataDependentFloatingField=true como parámetro de URL.

1. ¿Los formularios HTML5 ejecutan el script de inicialización y el evento de formulario preparado varias veces?

   Sí, las secuencias de comandos de inicialización y los sucesos preparados para el formulario se ejecutan varias veces, al menos una vez en el servidor y otra en el lado del cliente. Se recomienda escribir scripts como eventos initialize o form:ready basados en alguna lógica empresarial (datos de formulario o campo) para que la acción se realice en función del estado de los datos y del potencial idempotent (si los datos son iguales).

## Diseñar XDP {#designing-xdp}

1. ¿Hay alguna palabra clave reservada en los formularios HTML5?

   Respuesta: Todas las API de formularios HTML5 son palabras clave reservadas. Para las API y funciones personalizadas, utilice un nombre que no sea idéntico al de las [API de formularios HTML5](/help/forms/using/scripting-support.md). Aparte de las palabras clave reservadas, si utiliza nombres de objeto que comiencen con un guion bajo (_), se recomienda agregar un prefijo único después del guion bajo. Agregar un prefijo ayuda a evitar cualquier posible conflicto con las API internas de formularios HTML5. Por ejemplo, `_fpField1`. 
