---
title: Crear una comunicación interactiva
seo-title: Create an Interactive Communication
description: Cree una comunicación interactiva con el editor de comunicaciones interactivas. Utilice la funcionalidad de arrastrar y soltar para crear la comunicación interactiva y previsualizar las salidas de impresión y web en diferentes tipos de dispositivos.
seo-description: Create an Interactive Communication using the Interactive Communication editor. Use drag-and-drop functionality to build the Interactive Communication, and preview both print and web outputs on different device types.
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
feature: Interactive Communication
exl-id: a65b775d-040c-4069-b43a-6815be959b31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3156'
ht-degree: 83%

---

# Crear una comunicación interactiva  {#create-an-interactive-communication}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cree una comunicación interactiva con el editor de comunicaciones interactivas. Utilice la funcionalidad de arrastrar y soltar para crear la comunicación interactiva y previsualizar las salidas de impresión y web en diferentes tipos de dispositivos.

## Información general {#overview}

Comunicaciones interactivas centraliza y administra la creación, la combinación y la entrega de correspondencia personalizada e interactiva. Utilice la impresión como canal maestro para la web, puede minimizar la duplicación de esfuerzos al crear la salida web de la comunicación interactiva.

### Requisitos previos {#prerequisites}

Los siguientes son los requisitos previos para crear una comunicación interactiva:

* Configure un [Modelo de datos de formulario](/help/forms/using/data-integration.md) que contenga datos de prueba o una fuente de datos real, como una instancia de Microsoft® Dynamics.
* Asegúrese de tener los [Fragmentos de documento](/help/forms/using/document-fragments.md).
* Asegúrese de que tiene [Plantillas para impresión y canal Web](/help/forms/using/web-channel-print-channel.md).
* Asegúrese de que dispone de la [temática](/help/forms/using/themes.md) necesario para el canal Web.

## Crear comunicación interactiva {#createic}

1. Inicie sesión en la instancia de autor de AEM y navegue hasta **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formularios]** > **[!UICONTROL Formularios y documentos]**.
1. Pulse **[!UICONTROL Crear]** y seleccione **[!UICONTROL Comunicación interactiva]**. Aparecerá la página Crear comunicación interactiva.

   ![create-interactive-communication](assets/create-interactive-communication.png)

1. Especifique la siguiente información. :

   * **[!UICONTROL Título]**: escriba el título de la comunicación interactiva.
   * **[!UICONTROL Nombre*]**: El nombre de la comunicación interactiva se deriva del título que introduzca. Edítela si es necesario.
   * **[!UICONTROL Descripción]**: escriba una descripción sobre la comunicación interactiva.
   * **[!UICONTROL Modelo de datos de formulario*]**: Busque y seleccione el modelo de datos de formulario. Para obtener más información sobre el modelo de datos de formulario, consulte [Integración de datos de AEM Forms](/help/forms/using/data-integration.md).
   * **[!UICONTROL Servicio de rellenado previo]**: seleccione el servicio de rellenado previo para recuperar los datos y rellenar previamente la comunicación interactiva.
   * **[!UICONTROL Tipo de proceso posterior]**: puede seleccionar habilitar AEM o flujo de trabajo de Forms cuando se envíe la comunicación interactiva. Seleccione el tipo de flujo de trabajo que desea activar.
   * **[!UICONTROL Proceso posterior]**: seleccione el nombre del flujo de trabajo que desea activar. Cuando seleccione el flujo de trabajo de AEM, proporcione una ruta de datos adjuntos, una ruta de diseño, una ruta del PDF, una ruta de datos de impresión y una ruta de datos web.
   * **[!UICONTROL Etiquetas]**: seleccione las etiquetas que desea aplicar a la comunicación interactiva. También puede escribir un nombre de etiqueta nuevo/personalizado y pulsar Entrar para crearlo.
   * **[!UICONTROL Autor]**: el nombre del autor se toma automáticamente del nombre de usuario que ha iniciado sesión.
   * **[!UICONTROL Fecha de publicación:]** escriba la fecha de publicación de la comunicación interactiva.
   * **[!UICONTROL Cancelar publicación]**: escriba la fecha para cancelar la publicación de la comunicación interactiva.

1. Pulse **[!UICONTROL Siguiente]**. Aparecerá la pantalla para especificar los detalles de los canales web y de impresión.
1. Escriba lo siguiente:

   * **[!UICONTROL Imprimir]**: seleccione esta opción para generar el canal Imprimir de la comunicación interactiva.
   * **[!UICONTROL Imprimir plantilla*:]** Busque y seleccione un XDP como plantilla de impresión.
   * **[!UICONTROL Utilice Imprimir Como Principal Para El Canal Web:]** Seleccione esta opción para crear el canal web sincronizado con el canal de impresión. El uso del canal Imprimir como principal para el canal Web garantiza que el contenido y el enlace de datos del canal Web se deriven del canal Imprimir y que los cambios realizados en este se reflejen en el canal Web al pulsar Sincronizar. Sin embargo, se permite a los autores romper la herencia de componentes específicos del canal Web, según sea necesario. Para obtener más información, consulte [Sincronizar el canal Web con el canal Imprimir](/help/forms/using/create-interactive-communication.md#synchronize).
   * **[!UICONTROL Web:]** Seleccione esta opción para generar el canal web o la salida interactiva de la comunicación interactiva.
   * **[!UICONTROL Plantilla web de comunicación interactiva*:]** Busque y seleccione la plantilla web .
   * **[!UICONTROL Tema]** y **[!UICONTROL Seleccionar tema*]**: Busque y seleccione el tema para darle estilo al canal web de la comunicación interactiva. Para obtener más información, consulte [Temáticas en AEM Forms](/help/forms/using/themes.md).
   Para obtener más información sobre el canal Imprimir y el canal Web, consulte [Canal de impresión y canal Web](/help/forms/using/web-channel-print-channel.md).

1. Pulse **[!UICONTROL Crear]**. Se creará la comunicación interactiva y aparecerá un cuadro de alerta. Pulse **[!UICONTROL Editar]** para comenzar a crear el contenido de la comunicación interactiva, tal como se explica en [Agregar contenido mediante la interfaz de usuario de creación de comunicaciones interactivas](#step2). También puede pulsar **[!UICONTROL Listo]** y elegir editar la comunicación interactiva más adelante.

## Agregar contenido a la comunicación interactiva {#step2}

Después de crear una comunicación interactiva, puede utilizar la interfaz de creación de comunicaciones interactivas para crear su contenido.

Para obtener más información sobre la interfaz de creación de comunicaciones interactivas, consulte [Introducción a la creación de comunicaciones interactivas](/help/forms/using/introduction-interactive-communication-authoring.md).

1. La interfaz de creación de comunicaciones interactivas se inicia al pulsar Editar como se menciona en [Crear comunicación interactiva](#createic). También puede navegar hasta un recurso de comunicación interactiva existente en AEM, seleccionarlo y pulsar **[!UICONTROL Editar]** para iniciar la interfaz de creación de comunicaciones interactivas.

   De forma predeterminada, aparecerá el canal Imprimir de la comunicación interactiva, a menos que esta sea solo de canal Web. El canal Imprimir de la comunicación interactiva muestra las áreas de destino, tal como están disponibles en la plantilla de canal Imprimir/XDP seleccionada. En estas áreas y campos de destino, puede agregar componentes o recursos.

1. Con el canal Imprimir seleccionado, seleccione la pestaña **[!UICONTROL Componentes]**. Los siguientes componentes están disponibles en el canal Imprimir:

   | **Componente** | **Funcionalidad** |
   |---|---|
   | Gráfico | Agrega un gráfico que puede usar en comunicaciones interactivas para la representación visual de datos bidimensionales recuperados de una colección de modelos de datos de formulario. Para obtener más información, consulte [Usar gráficos en comunicaciones interactivas](/help/forms/using/chart-component-interactive-communications.md). |
   | Fragmento de documento | Permite agregar un componente reutilizable, como texto, listas o condiciones, a una comunicación interactiva. El componente agregado puede estar basado en el modelo de datos de formulario o no. |
   | Imagen | Permite insertar una imagen. |

   Arrastre y suelte los componentes en la comunicación interactiva y configúrelos según sea necesario.

1. Con el canal Imprimir seleccionado, vaya a la pestaña **[!UICONTROL Recursos]** y aplique el filtro para mostrar solo los recursos que desee ver.

   Con el explorador de recursos, también puede arrastrar y soltar recursos directamente en las áreas de destino de comunicaciones interactivas.

   ![assets-docfragments](assets/assets-docfragments.png)

1. Arrastre y suelte los fragmentos del documento en la comunicación interactiva. A continuación se muestran los tipos de fragmentos de documento que puede utilizar en el canal Imprimir de comunicaciones interactivas.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tipo de fragmento de documento</strong></td> 
   <td><strong>Ejemplo de propósito</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Texto</a></td> 
   <td>Texto para añadir dirección, correo electrónico del destinatario y texto del cuerpo de la carta </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Condición</a></td> 
   <td>Condición para agregar la imagen de encabezado adecuada a la comunicación en función del tipo de directiva: Standard o Premium. <br /> </td> 
  </tr> 
  <tr> 
   <td>Lista</td> 
   <td>Grupo de fragmentos de documento, incluidos texto, condiciones, otras listas e imágenes. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Para obtener más información sobre los fragmentos de documento, consulte [Fragmentos de documento](/help/forms/using/document-fragments.md).

1. Para configurar el enlace de variables, pulse una variable y seleccione ![configure_icon](assets/configure_icon.png) (Configurar) y, a continuación, configure las propiedades del enlace en el panel Propiedades de la barra lateral.

   * **[!UICONTROL Ninguna]**: el agente rellenará el valor de la variable.
   * **[!UICONTROL Fragmento de texto]**: si está seleccionado, puede buscar y seleccionar un fragmento de documento de texto cuyo contenido se procese en el campo. Solo esos fragmentos de documento de texto pueden enlazarse a variables que no tengan variables dentro.
   * **[!UICONTROL Objeto de modelo de datos]**: seleccione una propiedad del modelo de datos de formulario cuyo valor se rellene en el campo.
   También puede elegir configurar el fragmento del documento de texto correspondiente. El panel Propiedades muestra la lista de variables del fragmento de documento de texto. Puede tocar ![editar](assets/edit.png) (Editar) al lado del nombre de una variable para mostrar la configuración de edición de esa variable.

1. Para agregar una tabla, con el canal Imprimir seleccionado, en la pestaña **[!UICONTROL Recursos]** aplique el filtro para mostrar solo los fragmentos de diseño. Arrastre y suelte el fragmento de diseño necesario en la comunicación interactiva. Un fragmento de diseño se basa en un XDP y se puede utilizar para crear diseños gráficos o tablas estáticas y dinámicas en comunicaciones interactivas que se rellenen con datos dinámicos.

   Ejemplo: Una tabla de diseño para mostrar la prima bruta, el descuento por fidelidad % y la disponibilidad de asistencia de emergencia en carretera para las directivas antiguas y nuevas.

   Para obtener más información sobre fragmentos de diseño, consulte [Fragmentos de documento](/help/forms/using/document-fragments.md).

1. Con el canal Imprimir seleccionado, en la pestaña **[!UICONTROL Recursos]** aplique el filtro para mostrar imágenes. Arrastre y suelte las imágenes necesarias en la comunicación interactiva, como el logotipo de la empresa.

   Además, administre lo siguiente en la comunicación interactiva:

   * [Agregar y configurar gráficos](/help/forms/using/chart-component-interactive-communications.md)
   * [Sincronizar el canal Web con el canal Imprimir](/help/forms/using/create-interactive-communication.md#synchronize)

      * Sincronización automática
      * Cancelar herencia
      * Volver a habilitar la herencia
      * Sincronizar
   * [Archivos adjuntos y acceso a la biblioteca](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [Propiedades del campo XDP/Diseño](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Agregar reglas a los componentes](/help/forms/using/create-interactive-communication.md#rules)


1. Cambie a **[!UICONTROL Canal web]**. El canal Web aparecerá en el editor de comunicaciones interactivas. Cuando cambie del canal Imprimir al canal Web por primera vez, se producirá la sincronización automática. Para obtener más información, consulte [Sincronizar el canal Web desde el canal Imprimir](/help/forms/using/create-interactive-communication.md#synchronize).

   Dado que en este ejemplo utilizamos Imprimir como principal para la web, los marcadores de posición del canal Imprimir el contenido y el enlace de datos se sincronizan con el canal Web. Sin embargo, puede cambiar y personalizar el contenido específico del canal web según sea necesario.

   ![webchannelassets](assets/webchannelassets.png)

1. Para agregar componentes adicionales al canal Web, con el canal Web seleccionado, pulse **[!UICONTROL Componentes]**. Arrastre y suelte los componentes en el canal Web de la comunicación interactiva según sea necesario y proceda a configurarlos.

   | Componentes | Funcionalidad |
   |---|---|
   | Gráfico | Agrega un gráfico que se puede usar en comunicaciones interactivas para la representación visual de datos bidimensionales recuperados de una colección de modelos de datos de formulario. Para obtener más información, consulte [Usar el componente de gráfico](/help/forms/using/chart-component-interactive-communications.md). |
   | Fragmento de documento | Permite añadir un componente, texto, lista o condición reutilizables a una comunicación interactiva. El componente reutilizable que agregue a una comunicación interactiva puede estar basado en el modelo de datos de formulario o carecer de él. |
   | Imagen | Permite insertar una imagen. |
   | Panel | El componente Panel es un marcador de posición para agrupar otros componentes y controla cómo se coloca un grupo de componentes, como acordeón y pestañas, en la comunicación interactiva. El componente Panel también le permite hacer que un grupo de componentes se repita para el usuario final, por ejemplo, en varias entradas obligatorias para rellenar credenciales educativas. |
   | Tabla | Agrega una tabla que le permite organizar los datos en filas y columnas. |
   | Área de destino | Inserta un área de destino en un canal web para organizar los componentes específicos de ese canal. El área de destino es un contenedor sin formato que le permite agrupar componentes específicos de canales web. |
   | Texto | Agrega texto enriquecido al canal Web de una comunicación interactiva. El texto también puede utilizar objetos del modelo de datos de formulario para hacer que el contenido sea dinámico. |

1. Si es necesario, inserte recursos en el canal Web.

   Puede [previsualizar la comunicación interactiva](#previewic) para ver el aspecto de las salidas de impresión y web de la comunicación interactiva y aplicar los cambios necesarios.

## Previsualizar la comunicación interactiva {#previewic}

Puede usar la variable **[!UICONTROL Vista previa]** para evaluar el aspecto de la comunicación interactiva. El canal Web de comunicaciones interactivas también ofrece la opción de emular la experiencia de una comunicación interactiva para varios dispositivos. Por ejemplo, iPhone, iPad y escritorio. Puede usar ambas reglas, **[!UICONTROL Vista previa]** y **[!UICONTROL Emulador]** ![regla](assets/ruler.png) junto con otras opciones para obtener una vista previa de las salidas web para dispositivos con diferentes tamaños de pantalla. Los datos de ejemplo de la vista previa se rellenan desde el modelo de datos de formulario especificado.

1. Seleccione el canal (de impresión o web) para obtener una vista previa y pulse Previsualizar. Aparecerá la comunicación interactiva.

   >[!NOTE]
   >
   >La vista previa se rellenará con los datos de ejemplo del modelo de datos de formulario especificado. Para obtener más información sobre la vista previa de la comunicación interactiva con otros datos o el uso del servicio de rellenado previo, consulte [Usar el modelo de datos de formulario](/help/forms/using/using-form-data-model.md) y [Trabajar con el modelo de datos de formulario](/help/forms/using/work-with-form-data-model.md).

1. Para el canal Web, utilice ![reglas](assets/ruler.png) para ver el aspecto de la comunicación interactiva en varios dispositivos.

   ![webchannelpreview](assets/webchannelpreview.png)

Además, puede [Preparar y enviar comunicaciones interactivas mediante la interfaz de usuario de Agente](/help/forms/using/prepare-send-interactive-communication.md).

## Configuración de propiedades en la comunicación interactiva  {#configuring-properties-in-interactive-communication}

### Archivos adjuntos y acceso a la biblioteca {#attachmentslibrary}

En el canal Imprimir, puede configurar los archivos adjuntos y el acceso a la biblioteca para permitir que el agente administre los archivos adjuntos en la interfaz de usuario de Agente para la comunicación interactiva:

1. En el canal IImprimir, resalte el contenedor de documentos y pulse **[!UICONTROL Propiedades]**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   El panel Propiedades aparecerá en la barra lateral.

   ![propertiesattachments](assets/propertiesattachments.png)

1. Expanda los **[!UICONTROL Archivos adjuntos]** y especifique las siguientes propiedades:

   * **[!UICONTROL Permitir acceso a la biblioteca]**: seleccione esta opción para habilitar el acceso a la biblioteca al agente en la interfaz de usuario de Agente. Si está activada, el agente podrá agregar archivos de la biblioteca mientras prepara la comunicación interactiva.
   * **[!UICONTROL Permitir reordenar archivos adjuntos]**: seleccione esta opción para permitir que el agente vuelva a ordenar los archivos adjuntos con la comunicación interactiva.
   * **[!UICONTROL Número máximo de archivos adjuntos permitidos]**: especifique el número máximo de archivos adjuntos permitidos con la comunicación interactiva.
   * **[!UICONTROL Archivos que se van a adjuntar]**: pulse **[!UICONTROL Agregar]**, busque los archivos que desea adjuntar y especifique lo siguiente:

      * **[!UICONTROL Adjuntar este archivo al documento de forma predeterminada]**: puede cambiar esta opción solo si el archivo adjunto no es obligatorio.
      * **[!UICONTROL Obligatorio:]** el agente no podrá quitar el archivo adjunto en la interfaz de usuario de Agente.
   ![attachfiles](assets/attachfiles.png)

1. Pulse **[!UICONTROL Listo]**.

### Propiedades del campo XDP/Diseño {#xdplayoutfieldproperties}

1. Al editar el canal Imprimir de una comunicación interactiva, pase el ratón sobre un campo creado en la plantilla del canal Imprimir y seleccione ![configure_icon](assets/configure_icon.png) (Configurar).

   El cuadro de diálogo Propiedades aparecerá en la barra lateral.

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. Especifique lo siguiente:

   * **[!UICONTROL Nombre]**: nombre del nodo JCR.
   * **[!UICONTROL Título]**: escriba un título que sea visible para el agente en la interfaz de usuario de Agente y en el árbol del contenedor de documentos.
   * **[!UICONTROL Tipo de enlace]**: seleccione uno de los siguientes tipos de enlace para el campo.

      * Ninguno: el agente rellenará el valor de la propiedad.
      * Fragmento de texto: Si está seleccionado, puede examinar y seleccionar un fragmento de documento de texto cuyo contenido se procese en el campo.
      * Objeto del modelo de datos: seleccione una propiedad del modelo de datos de formulario cuyo valor se rellene en el campo.
   * **[!UICONTROL Valores predeterminados]**: el valor predeterminado garantiza que el campo no esté vacío cuando no haya ningún valor proporcionado por el objeto del modelo de datos especificado o el fragmento de texto. Si el tipo de enlace de datos es Ninguno, el valor predeterminado se rellenará previamente en el campo.
   * **[!UICONTROL Editable por el agente]**: seleccione esta opción para permitir que el agente edite el valor en el campo de la interfaz de usuario de Agente. Esta configuración no es aplicable si el tipo de enlace es un fragmento de texto.
   * **[!UICONTROL Etiqueta]**: especifique una cadena de texto que se muestre con el campo al agente en la interfaz de usuario de Agente. Esta configuración no es aplicable si el tipo de enlace es un fragmento de texto.
   * **[!UICONTROL Información del objeto]**: escriba una cadena de texto que sea visible al pasar el ratón por encima del agente en la interfaz de usuario de Agente. Esta configuración no es aplicable si el tipo de enlace es un fragmento de texto.
   * **[!UICONTROL Obligatorio]**: seleccione esta opción para que el campo sea obligatorio para el agente. Esta configuración no es aplicable si el tipo de enlace es un fragmento de texto.
   * **[!UICONTROL Permitir varias líneas]**: seleccione este campo para permitir varias líneas de texto como entrada en el campo. Esta configuración no es aplicable si el tipo de enlace es un fragmento de texto.


1. Pulse ![done_icon](assets/done_icon.png).

## Aplicar reglas a los componentes de comunicaciones interactivas {#rules}

Para condicionalizar componentes o contenido en la comunicación interactiva, pulse el componente o fragmento de contenido y seleccione ![createruleicon](assets/createruleicon.png) (Crear regla) para iniciar el Editor de reglas.

Para obtener más información, consulte:

* [Editor de reglas](/help/forms/using/rule-editor.md)
* [Introducción a la creación de comunicaciones interactivas](/help/forms/using/introduction-interactive-communication-authoring.md)

## Usar tablas {#tables}

### Tablas dinámicas en comunicaciones interactivas {#dynamic-tables-in-interactive-communication}

Puede agregar tablas dinámicas en la comunicación interactiva mediante fragmentos de diseño. Los siguientes pasos utilizan un ejemplo de instrucción de extracto de una tarjeta de crédito para ilustrar el uso de un fragmento de diseño para crear una tabla dinámica en una comunicación interactiva.

1. Asegúrese de que el fragmento de diseño necesario para crear la tabla esté disponible en AEM.
1. En el canal Imprimir de la comunicación interactiva, arrastre y suelte un fragmento de diseño (con una tabla de varias columnas) en un área de destino desde el explorador de recursos.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Aparecerá una tabla en el área de diseño de la comunicación interactiva.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Especifique el enlace de los datos para cada una de las celdas de la tabla. Para crear una fila repetible, inserte las propiedades del modelo de datos de formulario en la fila que pertenezca a una propiedad de colección común.

   1. Pulse sobre una celda de la tabla y seleccione ![configure_icon](assets/configure_icon.png) (Configurar).

      El cuadro de diálogo Propiedades aparecerá en la barra lateral.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Configure las propiedades:

      * **[!UICONTROL Nombre]**: nombre del nodo JCR.
      * **[!UICONTROL Título]**: escriba un título que sea visible en el editor de comunicaciones interactivas.
      * **[!UICONTROL Tipo de enlace]**&amp;ast;: Seleccione uno de los siguientes tipos de enlace para el campo .

         * **[!UICONTROL Ninguno]**
         * **[!UICONTROL Objeto del modelo de datos]**: El valor de una propiedad del modelo de datos de formulario se rellena en el campo .
      * **[!UICONTROL Objeto de modelo de datos]**: propiedad del modelo de datos de formulario cuyo valor se rellena en el campo.
      * **[!UICONTROL Valor predeterminado]**: el valor predeterminado garantiza que el campo no esté vacío cuando el objeto del modelo de datos especificado no proporcione ningún valor. El valor predeterminado se rellena previamente en el campo .
      * **[!UICONTROL Editable por el agente]**: seleccione esta opción para permitir que el agente edite el valor en el campo de la interfaz de usuario de Agente.
   1. Pulse ![done_icon](assets/done_icon.png).



1. Previsualice la comunicación interactiva para ver la tabla representada con los datos.

   ![lf_preview](assets/lf_preview.png)

### Tablas solo de canal Web {#web-channel-only-tables}

Puede crear una tabla dinámica solo de canal Web en una comunicación interactiva mediante una propiedad del modelo de datos de tipo Colección. Esta tabla es una representación de las propiedades secundarias de una propiedad Colección. Solo se pueden editar las propiedades de formato de las distintas celdas de la tabla.

1. Cambie al canal Web y, a continuación, elija mostrar el explorador de fuentes de datos.
1. Arrastre y suelte una propiedad de colección en un subformulario.

   Se creará una tabla en el subformulario.

1. Obtenga una vista previa de la tabla en la vista previa web de la comunicación interactiva.

## Sincronizar el canal Web con el canal Imprimir {#synchronize}

Al seleccionar Imprimir como maestro para el canal web al crear una comunicación interactiva, el canal web se crea de forma sincronizada con el canal de impresión y el contenido y el enlace de datos del canal web se derivan del canal de impresión y los cambios realizados en el canal de impresión se reflejan en el canal web al pulsar Sincronizar.

Sin embargo, se permite a los autores romper la herencia de los componentes del canal Web, según sea necesario.
![printweb_2-3](assets/printweb_2-3.png)
[Haga clic para ampliar](assets/printweb_2-3.png)

![Imprimir y canales web en el editor de comunicación interactiva](assets/printweb_2-1.png)

### Sincronización automática {#auto-sync}

Si utiliza el canal Imprimir como el principal del canal Web y cambia al canal Web desde el canal Imprimir, se produce la sincronización automática. La sincronización automática lleva los marcadores de posición, el contenido y el enlace de datos al canal web desde el canal Imprimir. Dependiendo de la complejidad y el contenido de su Comunicación interactiva, la sincronización automática puede tardar un poco.

>[!NOTE]
>
>Al sincronizar los canales, se sincronizan únicamente los fragmentos de documento, las imágenes, las condiciones, las listas y los fragmentos de diseño del canal Imprimir al canal Web. Los subformularios o nodos principales de que incluyan estos elementos no se sincronizan.

### Cancelar herencia {#cancel-inheritance}

En el canal Web, los componentes se incrustan en las áreas de destino.

Pase el ratón sobre el área de destino relevante en el canal Web y seleccione ![cancelinheritance](assets/cancelinheritance.png) (Cancelar herencia) y, a continuación, en el cuadro de diálogo Cancelar herencia, pulse **[!UICONTROL Sí]**.

La herencia de los componentes dentro del área de destino se cancela y ahora puede editarlos según sea necesario.

### Volver a habilitar la herencia {#re-enable-inheritance}

En el canal Web, si ha cancelado la herencia de un componente, puede volver a activarla. Para volver a habilitar la herencia, pase el ratón sobre el límite del área de destino correspondiente que incluye el componente y pulse ![reenableinheritance](assets/reenableinheritance.png).

Aparecerá el cuadro de diálogo Revertir herencia.

![revertinheritance](assets/revertinheritance.png)

Si es necesario, seleccione **[!UICONTROL Sincronizar la página después de revertir la herencia]**. Seleccione esta opción para sincronizar toda la comunicación interactiva. Si no selecciona esta opción, solo se sincronizará el área de destino correspondiente al restablecer la herencia.

Pulse **[!UICONTROL Sí]**.

### Sincronizar {#synchronize-1}

Si utiliza Imprimir como maestro para el canal web y realiza cambios en el canal de impresión, puede pulsar Sincronizar para traer los cambios recién realizados al canal web.

1. Para sincronizar el canal web con el canal de impresión, pulse **[!UICONTROL Sincronizar]**.

   Aparece el cuadro de diálogo Sincronizar contenido desde el canal maestro .

   ![synizecontentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. Pulse una de las siguientes acciones:

   * **[!UICONTROL Descartar cambios]**: Descarta todos los cambios realizados en el canal web independientemente de los cambios realizados en el canal web.
   * **[!UICONTROL Conservar cambios]**: Sincroniza el contenido solo para las áreas de destino en las que no se cancela la herencia.
