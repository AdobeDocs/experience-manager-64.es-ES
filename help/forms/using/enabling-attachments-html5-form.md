---
title: Activar archivos adjuntos en un formulario HTML5
seo-title: Enabling attachments for an HTML5 form
description: De forma predeterminada, la compatibilidad con los archivos adjuntos de los formularios HTML5 está deshabilitada.
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 68%

---

# Activar archivos adjuntos en un formulario HTML5 {#enabling-attachments-for-an-html-form}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede cargar, previsualizar y enviar archivos adjuntos con formularios HTML5. De forma predeterminada, la compatibilidad con los archivos adjuntos está deshabilitada. Para habilitar la compatibilidad de datos adjuntos, haga lo siguiente:

1. Cree un [perfil personalizado](/help/forms/using/custom-profile.md) con la propiedad mutiselect string `mfAttachmentOptions`.
1. En el perfil personalizado, especifique las propiedades `fileSizeLimit`, `multiSelect`y `buttonTex`t para configurar las opciones del widget de archivos adjuntos. Si es necesario, también puede especificar más propiedades personalizadas.

1. En el perfil personalizado, utilice las siguientes configuraciones:

   * **multiSelect** -> true o false (verdadero de forma predeterminada)
   * **fileSizeLimit** -> value_in_mb (digamos 5) (2 MB de forma predeterminada)
   * **buttonText** -> Texto del botón para la ventana emergente (&quot;Adjuntar&quot; de forma predeterminada)
   * **accept** -> tipos de archivo que aceptar (&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot; de forma predeterminada)

   >[!NOTE]
   >
   >En Microsoft Internet Explorer 9, los usuarios pueden adjuntar archivos que superen el límite especificado. Es un problema conocido.

1. Utilice el [editor de metadatos](/help/forms/using/manage-form-metadata.md) para seleccionar el perfil personalizado que ha creado anteriormente para los formularios HTML5.
1. Procese la plantilla de formulario con un perfil personalizado y el icono de archivos adjuntos aparecerá en la barra de herramientas de formularios.

   >[!NOTE]
   >
   >De forma predeterminada, el portal de formularios proporciona un perfil personalizado con la capacidad Borradores y archivos adjuntos habilitada. Para obtener más información sobre el perfil **Guardar como borrador**, consulte [Guardar formularios HTML5 como borrador](/help/forms/using/saving-html5-form-draft.md).

1. Haga clic en el icono de datos adjuntos y aparecerá un cuadro de diálogo de selección de datos adjuntos. Examine y seleccione el archivo adjunto y haga clic en **Adjuntar**.

   >[!NOTE]
   >
   >Para obtener una vista previa de un archivo adjunto, haga clic en su nombre.

   >[!NOTE]
   >
   >La opción de vista previa del archivo no está disponible para usuarios anónimos.

## Formato de envío de datos adjuntos {#attachment-submission-format}

Cuando los archivos adjuntos están habilitados, el formulario HTML5 envía datos de varias partes. Los datos de envío de varias partes tienen dos partes **dataXml** y **archivos adjuntos**.

>[!NOTE]
>
>Para la compatibilidad con versiones anteriores, si la opción `mfAllowAttachments` está desactivada, los formularios HTML5 no enviarán los datos de varias partes. Envía xml de datos simples en el formato **application/xml**.

Si el indicador mfAllowAttachments está activado, el [servicio enviar servicio proxy](/help/forms/using/service-proxy.md) también publicará datos de varias partes con dataXml y archivos adjuntos.
