---
title: Administrar recursos de vídeo
description: Obtenga información sobre cómo cargar, previsualizar, anotar y publicar recursos de vídeo.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 9%

---

# Administrar recursos de vídeo {#managing-video-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Obtenga información sobre cómo administrar y editar los recursos de vídeo en Adobe Experience Manager Assets. Además, si tiene licencia para usar Dynamic Media, consulte la [Documentación de vídeo de Dynamic Media](video.md).

## Cargar y previsualizar recursos de vídeo {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] Assets genera vistas previas para recursos de vídeo con la extensión MP4. Si el formato del recurso no es MP4, instale el paquete FFmpeg para generar una vista previa. FFmpeg crea representaciones de vídeo de tipo OGG y MP4. Puede obtener una vista previa de estas representaciones en el [!DNL Experience Manager] Interfaz de usuario de recursos.

1. En la carpeta o subcarpetas de Recursos digitales, vaya a la ubicación en la que desee agregar recursos digitales.
1. Para cargar el recurso, toque o haga clic en **[!UICONTROL Crear]** en la barra de herramientas y, a continuación, seleccione **[!UICONTROL Archivos]**. Como alternativa, suéltelo directamente en el área de recursos. Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets) para obtener más información sobre la operación de carga.
1. Para obtener una vista previa de un vídeo en la vista de tarjeta, pulse el botón **[!UICONTROL Play]** en el recurso de vídeo.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Puede pausar o reproducir vídeo en la **[!UICONTROL Tarjeta]** solo vista. El botón Reproducir/Pausa no está disponible en la **[!UICONTROL Lista]** vista.

1. Toque . **[!UICONTROL Editar]** en la tarjeta para previsualizar el vídeo en la **[!UICONTROL Detalles]** vista.

   El vídeo se reproduce en el reproductor de vídeo nativo del explorador. Puede reproducir, pausar, controlar el volumen y hacer zoom en el vídeo hasta la pantalla completa.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configuración para cargar recursos de más de 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

De forma predeterminada, la variable [!DNL Experience Manager] Assets no permite cargar ningún recurso que supere los 2 GB debido a un límite de tamaño de archivo. Sin embargo, puede sobrescribir este límite entrando en CRXDE Lite y creando un nodo en el `/apps` directorio. El nodo debe tener el mismo nombre de nodo, estructura de directorio y propiedades de nodo comparables de order.

Además de [!DNL Experience Manager] Configuración de recursos, cambie las siguientes configuraciones para cargar recursos de gran tamaño:

* Aumente el tiempo de caducidad del token. Consulte [!UICONTROL Servlet Adobe Granite CSRF] en la consola web en `https://[aem_server]:[port]/system/console/configMgr`. Para obtener más información, consulte [Protección CSRF](/help/sites-developing/csrf-protection.md).
* Aumente el `receiveTimeout` en la configuración de Dispatcher. Para obtener más información, consulte [Configuración de Dispatcher de Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>La variable [!DNL Experience Manager] La interfaz de usuario clásica no tiene una restricción de tamaño de archivo de dos gigabytes. Además, el flujo de trabajo completo para vídeo de gran tamaño no es totalmente compatible.

Para configurar un límite de tamaño de archivo más alto, realice los pasos siguientes en la sección `/apps` directorio.

1. En AEM, pulse **[!UICONTROL Herramientas > General > CRXDE Lite]**.
1. En el **[!UICONTROL CRXDE Lite]** , en la ventana de directorio de la izquierda, vaya a `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Para ver la ventana del directorio, pulse `>>` icono.
1. En la barra de herramientas, pulse **[!UICONTROL Nodo de superposición]**. También puede seleccionar **[!UICONTROL Nodo de superposición]** en el menú contextual.
1. En el cuadro de diálogo **[!UICONTROL Nodo de superposición]**, pulse **[!UICONTROL Aceptar]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Actualice el explorador. El nodo de superposición `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` está seleccionado.
1. En el **[!UICONTROL Propiedades]** , introduzca el valor apropiado en bytes para aumentar el límite de tamaño al tamaño deseado. Por ejemplo, introduzca `32212254720` para aumentar el límite de tamaño a 30 GB.

1. En la barra de herramientas, pulse **[!UICONTROL Guardar todo]**.
1. En AEM, pulse **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. En el **[!UICONTROL Paquetes de la consola web de Adobe Experience Manager]** en el **[!UICONTROL Nombre]** de la tabla, busque y toque **[!UICONTROL Controlador de trabajos de proceso externo de flujo de trabajo de Granite de Adobe]**.
1. En el **[!UICONTROL Controlador de trabajos de proceso externo de flujo de trabajo de Granite de Adobe]** , establezca los segundos para ambas **[!UICONTROL Tiempo de espera predeterminado]** y **[!UICONTROL Tiempo de espera máximo]** campos a `18000` (cinco horas).
1. Pulse **[!UICONTROL Guardar]**.
1. En AEM, pulse **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. En el **[!UICONTROL Modelos de flujo de trabajo]** página, seleccione **[!UICONTROL Codificar vídeo de Dynamic Media]** y, a continuación, toque **[!UICONTROL Editar]**.
1. En el **[!UICONTROL Flujo de trabajo]** , toque dos veces el botón **[!UICONTROL Proceso del servicio de vídeo de Dynamic Media]** componente.
1. En el cuadro de diálogo **[!UICONTROL Propiedades del paso]**, en la pestaña **[!UICONTROL Común]**, expanda **[!UICONTROL Configuración avanzada]**.
1. En el campo **[!UICONTROL Tiempo de espera]**, especifique un valor de `18000` y, a continuación, pulse **[!UICONTROL Aceptar]** para volver a la página de flujo de trabajo de **[!UICONTROL codificación de vídeo de Dynamic Media]**.
1. Cerca de la parte superior de la página, debajo de la variable **[!UICONTROL Codificar vídeo de Dynamic Media]** título de página, toque **[!UICONTROL Guardar]**.

## Publicar recursos de vídeo {#publishing-video-assets}

Una vez publicados los recursos de vídeo, quedan disponibles para su inclusión en una página web mediante una URL o incrustación en una página web. Consulte [Publicar recursos](publishing-dynamicmedia-assets.md).

## Anotar recursos de vídeo {#annotating-video-assets}

1. En la consola Recursos, pulse el botón **[!UICONTROL Editar]** en la tarjeta del recurso para mostrar la página de detalles del recurso.
1. Toque . **[!UICONTROL Vista previa]** para reproducir el vídeo.
1. Para realizar anotaciones en el vídeo, pulse el botón **[!UICONTROL Anotar]** botón. Se añade una anotación en el punto de tiempo (fotograma) concreto del vídeo.

   Mientras realiza anotaciones, puede dibujar en el lienzo e incluir un comentario con el dibujo. Los comentarios se guardan automáticamente en Adobe Experience Manager Assets.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Para salir del asistente de anotaciones, pulse **[!UICONTROL Cerrar]**.

1. Para ir a un punto específico del vídeo, especifique el tiempo en segundos en el campo de texto y haga clic en **[!UICONTROL Jump]**. Por ejemplo, para omitir los primeros 20 segundos de vídeo, introduzca `20` en el campo de texto.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Haga clic en una anotación para verla en la cronología. Toque **[!UICONTROL Eliminar]** para eliminar la anotación de la línea de tiempo.

   ![chlimage_1-206](assets/chlimage_1-206.png)
