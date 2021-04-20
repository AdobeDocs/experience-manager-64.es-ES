---
title: Marca de agua personalizada en la vista previa del PDF de letras
seo-title: Marca de agua personalizada en la vista previa del PDF de letras
description: Aprenda a crear una marca de agua personalizada en la vista previa del PDF de letras.
seo-description: Aprenda a crear una marca de agua personalizada en la vista previa del PDF de letras.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Marca de agua personalizada en la vista previa en PDF de letras {#custom-watermark-in-letter-pdf-preview}

## Información general {#overview}

En la interfaz de usuario Crear correspondencia, los usuarios del agente previsualizan la correspondencia en la forma final en la que se envía al posprocesamiento, por ejemplo para correo electrónico o impresión.

Para evitar el uso no autorizado de estos datos, las organizaciones pueden imponer una marca de agua en la vista previa del PDF. La marca de agua predeterminada es &quot;PREVIEW&quot;, que aparece en el PDF.

Para habilitar la marca de agua en la vista previa del PDF, seleccione la opción **[!UICONTROL Aplicar marca de agua]** durante la vista previa en **[!UICONTROL Configuraciones de administración de correspondencia]** en `https://[server]:[port]/system/console/configMgr`.

![marca de agua predeterminada](assets/default-watermark.png)

Puede seguir los pasos siguientes para personalizar el texto y el aspecto de la marca de agua:

## Personalice la marca de agua en la vista previa de PDF en la IU Crear correspondencia {#customizewatermark-}

1. Vaya a `https://[server]:[port]/[ContextPath]/crx/de` e inicie sesión como administrador.
1. En la carpeta de aplicaciones, cree una carpeta con el nombre **[!UICONTROL vista previa de marca de agua]** con una ruta/estructura similar a la carpeta de marca de agua de la vista previa en la carpeta de bibliotecas:

   1. Haga clic con el botón derecho en la carpeta **vista previa **marca de agua **en la siguiente ruta y seleccione **Nodo de superposición**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Asegúrese de que el cuadro de diálogo Nodo de superposición tiene los siguientes valores:

      **Ruta:** /libs/fd/cm/configFiles/previewwatermark

      **Ubicación de superposición:** /apps/

      **Coincidir tipos de nodo:** activado

      >[!NOTE]
      >
      >No realice cambios en la rama /libs. Cualquier cambio que realice puede perderse, ya que esta rama puede cambiar siempre que:
      >
      >* Actualice en su instancia
      >* Aplicar una corrección
      >* Instalación de un paquete de características


   1. Haga clic en **Aceptar** y, a continuación, haga clic en **Guardar todo**. La carpeta **[!UICONTROL previewwatermark]** se crea en la ruta especificada.

1. Copie y pegue el archivo dx de la carpeta &quot;/libs/fd/cm/configFiles/previewwatermark&quot; en la carpeta &quot;/apps/fd/cm/configFiles/previewwatermark&quot; y haga clic en **[!UICONTROL Guardar todo]**.
1. Realice los cambios deseados en el archivo ddx en /apps/fd/cm/configFiles/previewwatermark/.

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   Para obtener información sobre la personalización del aspecto, el texto y la alineación de las marcas de agua, consulte Adición y eliminación de marcas de agua y fondos en el documento [Assembler Service y DDX Reference](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf).

   >[!NOTE]
   >
   >En el archivo dx, las referencias a resultado y origen deben permanecer sin cambiar a output.pdf y input.pdf. El nombre del ddx del archivo tampoco debe cambiarse.

1. Haga clic en **Guardar todo**.

