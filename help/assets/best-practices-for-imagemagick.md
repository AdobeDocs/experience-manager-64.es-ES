---
title: Instale y configure ImageMagick para que funcione con [!DNL Experience Manager] Recursos
description: Obtenga información sobre el software ImageMagick, cómo instalarlo, configurar el paso del proceso de la línea de comandos y utilizarlo para editar, componer y generar miniaturas de imágenes.
contentOwner: AG
feature: Renditions,Developer Tools
role: Admin
exl-id: 9aeda88a-fd66-4fad-b496-3352a6ecab81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 2%

---

# Instale y configure ImageMagick para que funcione con [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

ImageMagick es un complemento de software para crear, editar, componer o convertir imágenes de mapa de bits. Puede leer y escribir imágenes en varios formatos (más de 200), como PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF y SVG. Utilice ImageMagick para cambiar el tamaño, girar, espejar, rotar, distorsionar, distorsionar y transformar imágenes. También puede ajustar los colores de la imagen, aplicar diversos efectos especiales o dibujar texto, líneas, polígonos, elipses y curvas mediante ImageMagick.

Utilice el controlador de medios de Adobe Experience Manager desde la línea de comandos para procesar imágenes a través de ImageMagick. Para trabajar con varios formatos de archivo usando ImageMagick, consulte [Prácticas recomendadas de los formatos de archivo de recursos](assets-file-format-best-practices.md). Para obtener información sobre todos los formatos de archivo compatibles, consulte [Formatos compatibles con Assets](assets-formats.md).

Para procesar archivos de gran tamaño con ImageMagick, considere requisitos de memoria superiores a los habituales, posibles cambios necesarios en las políticas de IM y el impacto general en el rendimiento. Los requisitos de memoria dependen de diversos factores, como la resolución, la profundidad de bits, el perfil de color y el formato de archivo. Si tiene intención de procesar archivos muy grandes mediante ImageMagick, realice una evaluación comparativa correcta de la variable [!DNL Experience Manager] servidor. Al final se proporcionan algunos recursos útiles.

>[!NOTE]
>
>Si está utilizando [!DNL Experience Manager] en Adobe Managed Services (AMS), póngase en contacto con el servicio de asistencia al cliente de Adobe si tiene pensado procesar muchos archivos de PSD o PSB de gran tamaño. Es posible que el Experience Manager no procese archivos PSB de muy alta resolución que tengan más de 30000 x 23000 píxeles.

## Instalar ImageMagick {#installing-imagemagick}

Hay varias versiones de los archivos de instalación de ImageMagic disponibles para varios sistemas operativos. Utilice la versión apropiada para su sistema operativo.

1. Descargue los [Archivos de instalación de ImageMagick](https://www.imagemagick.org/script/download.php) para su sistema operativo.
1. Para instalar ImageMagick en el disco que aloja el [!DNL Experience Manager] , inicie el archivo de instalación.

1. Establezca la variable de ruta Entorno en el directorio de instalación de ImageMagic.
1. Para comprobar si la instalación se ha realizado correctamente, ejecute el `identify -version` comando.

## Configuración del paso del proceso de la línea de comandos {#set-up-the-command-line-process-step}

Puede configurar el paso del proceso de la línea de comandos para su caso de uso específico. Realice estos pasos para generar una imagen y miniaturas invertidas (140 x 100, 48 x 48, 319 x 319 y 1280 x 1280) cada vez que agregue un archivo de imagen de JPEG a `/content/dam` en el [!DNL Experience Manager] servidor:

1. En el [!DNL Experience Manager] servidor, vaya a la consola Flujo de trabajo (`https://[aem_server]:[Port]/workflow`) y abra el **[!UICONTROL Recurso de actualización DAM]** modelo de flujo de trabajo.
1. En el **[!UICONTROL Recurso de actualización DAM]** modelo de flujo de trabajo, abra **[!UICONTROL Miniaturas de EPS (con tecnología ImageMagick)]** paso a paso.
1. En el **[!UICONTROL Pestaña Argumentos]**, agregue `image/jpeg` a **[!UICONTROL Tipos de MIME]** lista.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. En el **[!UICONTROL Comandos]** , introduzca el siguiente comando:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Seleccione el **[!UICONTROL Eliminar representación generada]** y **[!UICONTROL Generar representación web]** indicadores.

   ![select_flag](assets/select_flags.png)

1. En el **[!UICONTROL Imagen habilitada para web]** , especifique los detalles de la representación con dimensiones de 1280x1280 píxeles. Además, especifique i *imagen/jpeg* en el **[!UICONTROL Tipo de miimettipo]** en la ventana

   ![web_enabled_image](assets/web_enabled_image.png)

1. Toque o haga clic **[!UICONTROL OK]** para guardar los cambios.

   >[!NOTE]
   >
   >La variable `convert` puede que no se ejecute con ciertas versiones de Windows (por ejemplo, Windows SE), ya que está en conflicto con el comando nativo `convert` que forma parte de la instalación de Windows. En este caso, mencione la ruta completa de la utilidad ImageMagick. Por ejemplo, especifique,
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Abra el **[!UICONTROL Miniaturas de proceso]** y añada el tipo MIME `image/jpeg` under **[!UICONTROL Omitir tipos de mime]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. En el **[!UICONTROL Imagen habilitada para web]** , agregue el tipo MIME `image/jpeg` en el **[!UICONTROL Omitir lista]**. Toque o haga clic **[!UICONTROL OK]** para guardar los cambios.

   ![web_enabled](assets/web_enabled.png)

1. Guarde el flujo de trabajo.
1. Para comprobar si ImageMagic es capaz de procesar imágenes correctamente, cargue una imagen de JPG en [!DNL Assets]. Compruebe si se ha generado una imagen invertida y las representaciones para ella.

## Mitigar vulnerabilidades de seguridad {#mitigating-security-vulnerabilities}

Hay varias vulnerabilidades de seguridad asociadas con el uso de ImageMagick para procesar imágenes. Por ejemplo, el procesamiento de imágenes enviadas por el usuario implica el riesgo de ejecución de código remoto (RCE).

Además, varios complementos de procesamiento de imágenes dependen de la biblioteca ImageMagick, que incluye, entre otras cosas, imagick de PHP, rmagick y paperclip de Ruby y imagemagick de Node.js.

Si utiliza ImageMagick o una biblioteca afectada, Adobe recomienda mitigar las vulnerabilidades conocidas realizando al menos una de las siguientes tareas (pero preferiblemente ambas):

1. Compruebe que todos los archivos de imagen empiecen por el valor esperado [&quot;bytes mágicos&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) correspondiente a los tipos de archivo de imagen compatibles antes de enviarlos a ImageMagick para su procesamiento.
1. Utilice un archivo de directiva para deshabilitar los codificadores vulnerables de ImageMagick. La política global para ImageMagick se encuentra en `/etc/ImageMagick`.

>[!MORELIKETHIS]
>
>* [Prácticas recomendadas para procesar varios formatos de archivo mediante [!DNL Assets]](assets-file-format-best-practices.md)
>* [Opciones de línea de comandos para ImageMagick](https://www.imagemagick.org/script/command-line-options.php)
>* [Ejemplos básicos y avanzados de uso de ImageMagick](https://www.imagemagick.org/Usage/)
>* [Ajuste del rendimiento de los recursos para ImageMagick](performance-tuning-guidelines.md)
>* [Lista completa de formatos de archivo admitidos por [!DNL Assets]](assets-formats.md)
>* [Explicación de los formatos de archivo y el coste de memoria de las imágenes](https://www.scantips.com/basics1d.html)

