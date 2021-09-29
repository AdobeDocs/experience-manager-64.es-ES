---
title: compatibilidad Camera Raw
description: Obtenga información sobre cómo habilitar la compatibilidad Camera Raw en Adobe Experience Manager Assets.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---

# Usar Camera Raw para procesar imágenes {#camera-raw-support}

Puede habilitar la compatibilidad Camera Raw para procesar formatos de archivo sin procesar, como CR2, NEF y RAF, y procesar las imágenes en formato JPEG. La funcionalidad se admite en Adobe Experience Manager Assets mediante el [paquete Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) disponible en Distribución de software.

>[!NOTE]
>
>La funcionalidad solo admite representaciones JPEG. Es compatible con Windows de 64 bits, Mac OS y RHEL 7.x.

Para activar la compatibilidad Camera Raw en Adobe Experience Manager Assets, siga estos pasos:

1. Descargue el [paquete Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) desde Distribución de software.

1. Acceso `https://[aem_server]:[port]/workflow`. Abra el flujo de trabajo **[!UICONTROL DAM Update Asset]** .

1. Abra el paso **[!UICONTROL Procesar miniaturas]**.

1. Proporcione la siguiente configuración en la pestaña **[!UICONTROL Miniaturas]**:

   * **[!UICONTROL Miniaturas]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Tipos MIME omitidos]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![imagen](assets/chlimage_1-334.png)

1. En la pestaña **[!UICONTROL Web Enabled Image]**, en el campo **[!UICONTROL Skip List]**, especifique `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![imagen](assets/chlimage_1-335.png)

1. En el panel lateral, añada el paso **[!UICONTROL Controlador Camera Raw/DNG]** debajo del paso **[!UICONTROL Creación de miniaturas]**.

1. En el paso **[!UICONTROL Controlador Camera Raw/DNG]**, añada la siguiente configuración en la pestaña **[!UICONTROL Argumentos]**:

   * **[!UICONTROL Tipos]** Mime:  `image/dng` y  `image/x-raw-(.*)`
   * **[!UICONTROL Comando]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Haga clic en **[!UICONTROL Guardar]**.

>[!NOTE]
>
>Asegúrese de que la configuración anterior es la misma que la configuración **[!UICONTROL Ejemplo de Activo de actualización de DAM con la configuración del paso de manejo Camera Raw y DNG]**.

Ahora puede importar archivos sin procesar de cámara en [!DNL Experience Manager] Assets. Después de instalar el paquete Camera Raw y configurar el flujo de trabajo necesario, aparece la opción **[!UICONTROL Ajuste de imagen]** en la lista de paneles laterales.

![chlimage_1-337](assets/chlimage_1-337.png)

*Figura: Opciones del panel lateral*

![chlimage_1-338](assets/chlimage_1-338.png)

*Figura: Utilice la opción para realizar ediciones ligeras en las imágenes*

Después de guardar las ediciones en una imagen Camera Raw, se genera una nueva representación `AdjustedPreview.jpg` para la imagen. Para otros tipos de imagen excepto Camera Raw, los cambios se reflejan en todas las representaciones.

## Prácticas recomendadas, problemas conocidos y limitaciones {#best-practices}

La funcionalidad tiene las siguientes limitaciones:

* La funcionalidad solo admite representaciones JPEG. Es compatible con Windows de 64 bits, Mac OS y RHEL 7.x.
* La reescritura de metadatos no es compatible con los formatos RAW y DNG.
* La biblioteca Camera Raw tiene limitaciones en torno al total de píxeles que puede procesar a la vez. Actualmente, puede procesar un máximo de 65000 píxeles en el lado largo de un archivo o 512 MP independientemente de los criterios que se encuentren primero.
