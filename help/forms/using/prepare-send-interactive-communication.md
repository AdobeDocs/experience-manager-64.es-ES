---
title: Preparar y enviar comunicaciones interactivas mediante la interfaz de usuario del agente
seo-title: Prepare and send Interactive Communication using the Agent UI
description: La interfaz de usuario del agente permite a los agentes preparar y enviar una comunicación interactiva al proceso de publicación. El agente realiza las modificaciones necesarias según lo permitido y envía la comunicación interactiva a un proceso de publicación, como el correo electrónico o la impresión.
seo-description: Prepare and send Interactive Communication using the Agent UI
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interactive Communication
exl-id: 5ec33ef5-1722-4d29-9979-d8da32923e66
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 97%

---

# Preparar y enviar comunicaciones interactivas mediante la interfaz de usuario del agente {#prepare-and-send-interactive-communication-using-the-agent-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La interfaz de usuario del agente permite a los agentes preparar y enviar una comunicación interactiva al proceso de publicación. El agente realiza las modificaciones necesarias según lo permitido y envía la comunicación interactiva a un proceso de publicación, como el correo electrónico o la impresión.

## Información general {#overview}

Una vez creada una comunicación interactiva, el agente puede abrirla en la interfaz de usuario del agente y preparar una copia específica para el destinatario introduciendo datos y administrando el contenido y los archivos adjuntos. Por último, puede enviar la comunicación interactiva a un proceso de publicación.

Cuando prepara la comunicación interactiva mediante la interfaz de usuario del agente, este administra los siguientes aspectos de la comunicación interactiva en la interfaz de usuario antes de enviarla a un proceso de publicación:

* **Datos**: la pestaña Datos de la interfaz de usuario del agente muestra todas las variables editables por el agente y las propiedades del modelo de datos de formulario desbloqueadas en la comunicación interactiva. Estas variables o propiedades se crean al editar o crear los fragmentos de documento incluidos en la comunicación interactiva. La pestaña Datos incluye también todos los campos creados en la plantilla del canal de impresión o XDP. La pestaña Datos aparece únicamente cuando el agente puede editar alguna variable, propiedad del modelo de datos de formulario o campo de la comunicación interactiva.
* **Contenido**: en la pestaña Contenido, el agente administra el contenido de la comunicación interactiva, como los fragmentos de documento y las variables de contenido. El agente puede realizar los cambios en el fragmento de documento según lo permitido en las propiedades de esos fragmentos de documento al crear la comunicación interactiva. El agente también puede reordenar, agregar o quitar un fragmento de documento y añadir saltos de página, si se le permite.
* **Archivos adjuntos**: la pestaña Archivos adjuntos aparece en la interfaz de usuario del agente únicamente si la comunicación interactiva tiene archivos adjuntos o si el agente tiene acceso a la biblioteca. El agente puede poseer los permisos necesarios para cambiar o editar los archivos adjuntos, o carecer de ellos.

## Preparación de la comunicación interactiva mediante la interfaz de usuario del agente {#prepare-interactive-communication-using-the-agent-ui}

1. Seleccione **[!UICONTROL Forms]** > **[!UICONTROL Formularios y documentos]**.
1. Seleccione la comunicación interactiva adecuada y pulse **[!UICONTROL Abrir la interfaz de usuario del agente]**.

   >[!NOTE]
   >
   >La interfaz de usuario del agente solo está disponible si la comunicación interactiva seleccionada contiene un canal de impresión.

   ![abrir_iu_del_agente](assets/openagentiui.png)

   En función del contenido y de las propiedades de la comunicación interactiva, la interfaz de usuario del agente aparece con las tres pestañas siguientes: Datos, Contenido y Archivos adjuntos.

   ![pestañas_iu_del_agente](assets/agentuitabs.png)

   Comience a introducir los datos y a administrar el contenido y los archivos adjuntos.

### Introducir datos {#enter-data}

1. En la pestaña Datos, introduzca los datos de las variables, las propiedades del modelo de datos de formulario y los campos de la plantilla de impresión (XDP), según los requisitos. Complete todos los campos obligatorios marcados con un asterisco (*) para habilitar el botón **Enviar**.

   Pulse el valor de un campo de datos en la vista previa de la comunicación interactiva para resaltar el campo de datos correspondiente en la pestaña Datos o viceversa.

### Administrar contenido {#manage-content}

En la pestaña Contenido, administre el contenido de la comunicación interactiva, como los fragmentos de documento y las variables de contenido.

1. Seleccione **[!UICONTROL Contenido]**. Aparece la pestaña Contenido de la comunicación interactiva.

   ![pestaña_contenido_iu_agente](assets/agentuicontenttab.png)

1. Edite los fragmentos de documento según los requisitos en la pestaña Contenido. Para enfocar el fragmento relevante en la jerarquía de contenido, puede tocar la línea o el párrafo correspondiente en la vista previa de la comunicación interactiva o pulsar directamente en el fragmento desde la jerarquía de contenido.

   Por ejemplo, el fragmento de documento con la línea &quot;Realizar un pago en línea ahora ...&quot; está seleccionado en la vista previa del gráfico que aparece a continuación, y se ha seleccionado el mismo fragmento de documento en la pestaña Contenido

   ![enfoque_módulo_contenido](assets/contentmodulefocus.png)

   Si pulsa Resaltar los módulos seleccionados en el contenido ( ![ccr_resaltar_módulos_seleccionados_en_contenido](assets/highlightselectedmodulesincontentccr.png)) en la parte superior izquierda de la vista previa de las pestañas Contenido o Datos, puede deshabilitar o habilitar la funcionalidad para ir al fragmento de documento pulsando o seleccionando el texto, el párrafo o el campo de datos relevantes en la vista previa.

   Los fragmentos que el agente puede editar al crear la comunicación interactiva incluyen el icono Editar contenido seleccionado ( ![icono_editar_contenido_seleccionado](assets/iconeditselectedcontent.png)). Pulse el icono Editar contenido seleccionado para iniciar el fragmento en el modo Edición y realizar cambios en él. Utilice las siguientes opciones para dar formato y administrar el texto:

   * [Opciones de formato](#formattingtext)

      * [Copiar y pegar texto con formato de otras aplicaciones](#pasteformattedtext)
      * [Resaltar fragmentos del texto](#highlightemphasize)
   * [Caracteres especiales](#specialcharacters)
   * [Métodos abreviados de teclado](/help/forms/using/keyboard-shortcuts.md)

   Para obtener más información sobre las acciones disponibles en los diferentes fragmentos de documento de la interfaz de usuario del agente, consulte [Acciones e información disponible en la interfaz de usuario del agente](#actionsagentui).

1. Para añadir un salto de página a la salida de impresión de la comunicación interactiva, coloque el cursor en el punto en el que desea insertar un salto de página y seleccione Salto de página antes o Salto de página después ( ![salto_de_página_antes_después](assets/pagebreakbeforeafter.png)).

   En la comunicación interactiva se inserta un marcador de posición de salto de página explícito. Para ver cómo afectan los saltos de página explícitos a la comunicación interactiva, consulte la vista previa de impresión.

   ![salto_de_página_explícito](assets/explicitpagebreak.png)

   Continúe administrando los archivos adjuntos de la comunicación interactiva.

### Administrar archivos adjuntos {#manage-attachments}

1. Seleccione **[!UICONTROL Archivo adjunto]**. La interfaz de usuario del agente muestra los archivos adjuntos disponibles tal como están configurados al crear la comunicación interactiva.

   Puede optar por no enviar un archivo adjunto junto con la comunicación interactiva tocando el icono Ver, y puede pulsar la cruz que aparece en el archivo para eliminarlo (si el agente puede eliminar u ocultar los archivos adjuntos) de la comunicación interactiva. Los iconos Ver y Eliminar están desactivados en los archivos adjuntos especificados como obligatorios al crear la comunicación interactiva.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. Pulse el icono Acceder a la biblioteca (![libraryaccess](assets/libraryaccess.png)) para acceder a la biblioteca de contenido e insertar recursos DAM como archivos adjuntos.

   >[!NOTE]
   >
   >El icono Acceder a la biblioteca solo está disponible si el acceso a la biblioteca estaba habilitado al crear la comunicación interactiva (en las propiedades del contenedor de documentos del canal de impresión).

1. Si el orden de los archivos adjuntos no estaba bloqueado al crear la comunicación interactiva, puede reordenarlos seleccionando un archivo y pulsando las flechas abajo y arriba.
1. Utilice las opciones Vista previa en la web y Vista previa de impresión para ver si las dos salidas se ajustan a sus necesidades.

   Si está satisfecho con las vistas previas, pulse **[!UICONTROL Enviar]** para enviar la comunicación interactiva a un proceso de publicación. Si desea realizar cambios, salga de la vista previa para llevarlos a cabo.

## Aplicar formato al texto {#formattingtext}

Al editar un fragmento de texto en la interfaz de usuario del agente, la barra de herramientas cambia según el tipo de ediciones que decida realizar: Fuente, Párrafo o Lista.

![tipo_de_formato_barra_herramientas](assets/typeofformattingtoolbar.png) ![Barra de herramientas Fuente](do-not-localize/fonttoolbar.png)

Barra de herramientas Fuente

![Barra de herramientas Párrafo](do-not-localize/paragraphtoolbar.png)

Barra de herramientas Párrafo

![Barra de herramientas Lista](do-not-localize/listtoolbar.png)

Barra de herramientas Lista

### Resaltar partes del texto {#highlightemphasize}

Para resaltar fragmentos de texto en un fragmento editable, seleccione el texto y pulse Color de resaltado.

![highlighttextagentui](assets/highlighttextagentui.png)

### Pegar texto con formato {#pasteformattedtext}

![pastedtext](assets/pastedtext.png)

### Insertar caracteres especiales en el texto {#specialcharacters}

La interfaz de usuario del agente ha incorporado la compatibilidad con 210 caracteres especiales. El administrador puede [agregar compatibilidad con caracteres especiales adicionales o personalizados usando la personalización](/help/forms/using/custom-special-characters.md).

#### Envío de archivos adjuntos {#attachmentdelivery}

* Cuando la comunicación interactiva se procesa mediante API del lado del servidor como un PDF interactivo o no interactivo, el PDF procesado contiene archivos adjuntos como archivos adjuntos del PDF.
* Cuando se carga un proceso de publicación asociado a una comunicación interactiva como parte de la opción Enviar mediante la interfaz de usuario del agente, los archivos adjuntos se pasan como el parámetro List&lt;com.adobe.idp.Document> inAttachmentDocs.
* Los flujos de trabajo del mecanismo de envío, como el correo electrónico y la impresión, también proporcionan archivos adjuntos con la versión PDF de la comunicación interactiva.

## Acciones e información disponible en la interfaz de usuario del agente {#actionsagentui}

### Fragmentos de documento {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **Flechas arriba/abajo**: permiten mover fragmentos de documento hacia arriba o hacia abajo en la comunicación interactiva.
* **Eliminar**: si dispone de los permisos necesarios, elimina el fragmento del documento de la comunicación interactiva.
* **Salto de página antes** (aplicable a los fragmentos secundarios del área de destino): inserta un salto de página antes del fragmento de documento.
* **Sangría**: aumenta o disminuye la sangría de un fragmento de documento.
* **Salto de página después** (aplicable a los fragmentos secundarios del área de destino): inserta un salto de página después del fragmento de documento.

![opciones_fragmento_documento](assets/docfragoptions.png)

* Editar (solo fragmentos de texto): abre el editor de texto enriquecido para editar el fragmento de documento de texto. Para obtener más información, consulte [Formato del texto](#formattingtext).

* Selección (icono en forma de ojo): incluye o excluye el fragmento de documento de la comunicación interactiva.
* Valores no rellenados (información): indica el número de variables no rellenadas del fragmento de documento.

### Fragmentos de documento de lista {#list-document-fragments}

![opciones_lista](assets/listoptions.png)

* Insertar línea en blanco: inserta una nueva línea en blanco.
* Selección (icono en forma de ojo): incluye o excluye el fragmento de documento de la comunicación interactiva.
* Omitir viñetas/numeraciones: active esta opción para omitir las viñetas o la numeración en el fragmento de documento de lista.
* Valores no rellenados (información): indica el número de variables no rellenadas del fragmento de documento.
