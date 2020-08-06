---
title: Usar rasterizador de PDF
description: Genere miniaturas y representaciones de alta calidad con la biblioteca Adobe PDF Rasterizer.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dea673f8999656a5c5364f74f45eba41dd17b947
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---


# Uso del rasterizador PDF {#using-pdf-rasterizer}

A veces, cuando se cargan archivos PDF o AI de gran tamaño con mucho contenido en Adobe Experience Manager (AEM) Assets, es posible que la biblioteca predeterminada no genere una salida precisa. En estos casos, la biblioteca Rasterizer PDF de Adobe puede generar resultados más fiables y precisos que los de una biblioteca predeterminada.

Adobe recomienda utilizar la biblioteca Rasterizer de PDF para lo siguiente:

* Archivos AI o PDF pesados y con gran contenido.
* Los archivos AI o PDF con miniaturas no se generan de forma predeterminada.
* Archivos AI con colores Pantone Matching System (PMS).

Las miniaturas y previsualizaciones que se generan con el rasterizador de PDF tienen una mejor calidad en comparación con la salida lista para usar y, por lo tanto, proporcionan una experiencia de visualización uniforme en todos los dispositivos. La biblioteca Rasterizer de Adobe PDF no admite conversión de espacio de color. Siempre se envía a RGB independientemente del espacio de color del archivo de origen.

1. Instale el paquete Rasterizer PDF en la instancia de AEM desde Distribución [de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg)software.

   >[!NOTE]
   >
   >La biblioteca Rasterizer PDF solo está disponible para Windows y Linux.

1. Acceda a la consola de flujo de trabajo de AEM Assets desde `https://[AEM_server]:[port]/workflow`.
1. Abra la página de flujo de trabajo de recursos **[!UICONTROL de actualización de]** DAM.
1. Configure lo siguiente para omitir la generación predeterminada de miniaturas y representaciones web para archivos PDF y AI:

   * Abra el paso Proceso **[!UICONTROL de]** miniaturas y agregue `application/pdf` o `application/postscript` en el campo **[!UICONTROL Omitir tipos]** de MIME.

   ![Ski_mime_types-2](assets/skip_mime_types-2.png)

   * En la ficha Imagen **[!UICONTROL habilitada para]** Web, agregue `application/pdf` o `application/postscript` debajo de **[!UICONTROL Omitir Lista]** según sus necesidades.

   ![web_enabled_imageskiplist](assets/web_enabled_imageskiplist.png)

1. Abra el paso **[!UICONTROL Rasterizar representación]** de Previsualización de imagen PDF/AI y elimine el tipo MIME para el que desea omitir la generación predeterminada de representaciones de imágenes de previsualización. Por ejemplo, elimine el tipo MIME *application/pdf*, *application/postscript,* o *application/illustrator* de la lista Tipos **** MIME.

   ![process_words](assets/process_arguments.png)

1. Arrastre el paso Controlador de rasterizador **** PDF desde el panel lateral hasta debajo del paso Miniaturas **[!UICONTROL de]** proceso.
1. Configure los siguientes argumentos para el paso del controlador de rasterizador **** PDF:

   * Tipos Mime: *application/pdf* o *application/postscript*
   * Comandos: `PDFRasterizer -d -p 1 -s 1280 -t PNG -i ${file}`
   * Añadir tamaños de miniaturas: 319:319, 140:100, 48:48. Añada la configuración de miniaturas personalizada, si es necesario.

   Los argumentos de la línea de comandos del `PDFRasterizer` comando pueden incluir lo siguiente:

   **-d**: Marca para permitir la representación suave de texto, ilustraciones vectoriales e imágenes. Crea imágenes de mejor calidad. Sin embargo, si se incluye este parámetro, el comando se ejecuta lentamente y aumenta el tamaño de las imágenes.

   `-p`:: Número de página. El valor predeterminado son todas las páginas. &#39;*&#39; indica todas las páginas.

   **-s**: Dimensión máxima de la imagen (altura o anchura). Se convierte a PPP para cada página. Si las páginas tienen un tamaño diferente, cada página podría escalarse en una cantidad diferente. El valor predeterminado es el tamaño real de la página.

   **-t**: Tipo de imagen de salida. Los tipos válidos son JPEG, PNG, GIF y BMP. El valor predeterminado es JPEG.

   **-i**: Ruta para el PDF de entrada. Es un parámetro obligatorio.

   `-h`: Ayuda

1. Para eliminar representaciones intermedias, seleccione **[!UICONTROL Eliminar representación]** generada.
1. Para permitir que Rasterizar PDF genere representaciones web, seleccione **[!UICONTROL Generar representación]** web.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Especifique la configuración en la ficha Imagen **[!UICONTROL habilitada para]** Web.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Guarde el flujo de trabajo.
1. Para habilitar el rasterizador de PDF para procesar páginas PDF con bibliotecas PDF, abra el modelo **[!UICONTROL DAM Process Subasset]** desde la consola Flujo de trabajo.
1. En el panel lateral, arrastre el paso Controlador de rasterizador de PDF debajo del paso **[!UICONTROL Crear representación]** de imagen habilitada para Web.
1. Configure los siguientes argumentos para el paso del controlador de rasterizador **** PDF:

   * Tipos Mime: `application/pdf` o `application/postscript`
   * Comandos: `PDFRasterizer -d -p 1 -s 1280 -t PNG -i ${file}`
   * Añadir tamaños de miniaturas: 319:319, 140:100, 48:48. Añada la configuración de miniaturas personalizada, si es necesario.

   Los argumentos de la línea de comandos para el comando PDFRasterizer pueden incluir lo siguiente:

   **-d**: Marca para permitir la representación suave de texto, ilustraciones vectoriales e imágenes. Crea imágenes de mejor calidad. Sin embargo, si se incluye este parámetro, el comando se ejecuta lentamente y aumenta el tamaño de las imágenes.

   **-p**: Número de página. El valor predeterminado son todas las páginas. Un asterisco `*` indica todas las páginas.

   **-s**: Dimensión máxima de la imagen (altura o anchura). Se convierte a PPP para cada página. Si las páginas tienen un tamaño diferente, cada página podría escalarse en una cantidad diferente. El valor predeterminado es el tamaño real de la página.

   **-t**: Tipo de imagen de salida. Los tipos válidos son JPEG, PNG, GIF y BMP. El valor predeterminado es JPEG.

   **-i**: Ruta para el PDF de entrada. Es un parámetro obligatorio.

   **-h**: Ayuda

1. Para eliminar representaciones intermedias, seleccione **[!UICONTROL Eliminar representación]** generada.
1. Para permitir que Rasterizar PDF genere representaciones web, seleccione **[!UICONTROL Generar representación]** web.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Especifique la configuración en la ficha **[!UICONTROL Imagen habilitada para]** Web.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Guarde el flujo de trabajo.
1. Cargue un archivo PDF o un archivo AI a AEM Assets. PDF Rasterizer genera las miniaturas y las representaciones web del archivo.
