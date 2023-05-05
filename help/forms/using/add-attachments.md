---
title: Agregar archivos adjuntos
seo-title: Adding attachments
description: Agregue fotografías y notas garabateadas como anotaciones a su tarea en la aplicación de AEM Forms
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 92%

---

# Agregar archivos adjuntos {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Agregar archivos adjuntos en formularios sincronizados con el servidor de flujo de trabajo de AEM Forms (AEM Forms en JEE) {#adding-annotations}

La aplicación de AEM Forms permite adjuntar imágenes, notas garabateadas y notas de texto al formulario sincronizado con el servidor JEE de AEM Forms. Si el formulario se carga desde un servidor del flujo de trabajo de AEM Forms, los archivos adjuntos se agregan al formulario. Puede pulsar el botón de archivos adjuntos ![attachment-app](assets/attachments-app.png) para ver todos los archivos adjuntos de un formulario juntos. La notificación roja especifica el número de archivos adjuntos en el formulario. Si no hay datos adjuntos en el formulario, no verá el botón de notificaciones rojo. Si no hay datos adjuntos en el formulario, al pulsar el botón de archivos adjuntos ![attch](assets/attch.png), verá opciones para adjuntar fotos o garabatos.

Las opciones son las siguientes:

* **[!UICONTROL Galería]**: permite agregar una imagen de las imágenes guardadas en el dispositivo.

* **[!UICONTROL Cámara]**: permite tomar una imagen y agregarla al formulario.

* **[!UICONTROL Notas]**: permite agregar un garabato o una nota de texto. Use ![garabato](assets/scribble.png) para agregar un garabato y el ![teclado](assets/keyboard.png) para agregar una nota de texto.

>[!NOTE]
>
>Los archivos adjuntos agregados por un usuario son visibles para otros usuarios de aplicaciones de AEM Forms. Otros usuarios no pueden eliminar los archivos adjuntos que haya agregado un usuario.

### Pantalla de archivos adjuntos {#the-attachments-screen}

Para ver todos los archivos adjuntos en un lugar, pulse ![attachment-app](assets/attachments-app.png). Aquí puede agregar, cambiar el nombre y eliminar archivos adjuntos.

![Todos los archivos adjuntos en un lugar](assets/attachments-screen.png)

Puede usar el botón **+** de la pantalla de archivos adjuntos para adjuntar otra imagen, garabato o texto.

### Agregar una fotografía {#adding-a-photograph}

Puede utilizar la cámara del dispositivo móvil o guardar imágenes en el dispositivo para adjuntar una imagen en el formulario.

1. Pulse el botón de archivos adjuntos ![attch](assets/attch.png) de la parte inferior de la ventana.
1. Pulse **[!UICONTROL Galería]** o **[!UICONTROL Cámara]** en la ventana emergente que aparece.
1. En función de la opción seleccionada, realice lo siguiente:

   1. Si selecciona **[!UICONTROL Cámara]**.

      Tome una foto. A continuación, pulse el botón **[!UICONTROL Usar]** ![use-pic](assets/use-pic.png).

      O pulse el botón **[!UICONTROL Repetir]** ![retake](assets/retake.png) para volver a tomar la fotografía.

   1. Si selecciona **[!UICONTROL Galería]**.

      Aparecerá el explorador de imágenes del dispositivo. En el explorador de imágenes de su dispositivo, pulse la imagen que desea adjuntar.

### Agregar una nota {#adding-a-note}

La opción **Notas** permite agregar garabatos hechos a mano alzada y archivos adjuntos de texto en el formulario.

1. Pulse el botón de archivos adjuntos ![attch](assets/attch.png) de la parte inferior de la ventana.
1. Pulse **[!UICONTROL Notas]** en la ventana emergente que aparece.
1. En la interfaz de usuario de Notas que se inicia, realice un garabato a mano alzada.

   ![Interfaz de Garabatos](assets/scribble-ui.png)
   **Figura:** *Garabatos*

   Puede utilizar las siguientes opciones en la interfaz de garabatos:

   * **[!UICONTROL Borrar]**: borra la pantalla.
   * **[!UICONTROL Listo]**: Adjunta el guion actual.
   * **[!UICONTROL Cancelar]**: Descarta el guion actual y sale de la interfaz de usuario de Scribble.
   * ![teclado](assets/keyboard.png): borra el garabato y permite agregar una nota de texto.

   ![Teclado en los garabatos de la aplicación de AEM Forms](assets/keyboard-inapp.png)

## Archivos adjuntos en formularios sincronizados con los servidores de AEM Forms sin flujo de trabajo de AEM Forms (AEM Forms en OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Los archivos adjuntos para formularios móviles sincronizados con servidores OSGi de AEM Forms funcionan de forma similar a los servidores JEE de AEM Forms.

Los archivos adjuntos de nivel de formulario no son compatibles con los formularios adaptables cargados en la aplicación desde un servidor OSGi de AEM Forms. Para adjuntar imágenes o notas de texto, active los archivos adjuntos de nivel de campo en el formulario cuando lo cree. Arrastre y suelte el componente de archivo adjunto desde el explorador de componentes del campo.

En el caso de los formularios adaptables, puede ver los archivos adjuntos en el documento de registro (DoR). Consulte, [Generar un documento de registro para formularios adaptables que no sean XFA](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
