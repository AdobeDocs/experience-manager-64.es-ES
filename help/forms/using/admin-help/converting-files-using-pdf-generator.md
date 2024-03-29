---
title: Convertir archivos mediante el generador de PDF
seo-title: Converting files using PDF Generator
description: Obtenga información sobre cómo convertir archivos mediante el Generador de PDF.
seo-description: Learn how to convert files using PDF Generator.
uuid: 295afb8f-130a-44f5-b0ab-e4c93c0c9e52
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 999ae2be-56ba-48c1-861b-8d4c991a0206
feature: PDF Generator
exl-id: 3eecff45-405f-482f-b0de-acf6557a7813
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 3%

---

# Convertir archivos mediante el generador de PDF{#converting-files-using-pdf-generator}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede utilizar las páginas web de Generador de PDF para convertir archivos.

## Creación de un archivo de PDF {#create-a-pdf-file}

1. En la consola de administración, haga clic en Servicios > Generador de PDF > Crear PDF.
1. Haga clic en Examinar para buscar y seleccionar el archivo.

   >[!NOTE]
   >
   >El Generador de PDF puede detectar automáticamente el tipo de archivo de los archivos .doc, .xls, .ppt y .rtf, incluso cuando el nombre de archivo no tiene la extensión de archivo. Esta función no funciona con archivos .docx, .xlsx y .pptx.

1. En Configuración, seleccione Usar configuración personalizada o Cargar archivo de configuración.

   * Si utiliza una configuración personalizada, seleccione una configuración de Adobe PDF, una configuración de seguridad y una configuración de tipo de archivo, y especifique un tiempo de espera.

      La configuración de Adobe PDF solo se aplica a PS-to-PDF, EPS-to-PDF, PRN-to-PDF, Image-to-PDF con OCR activado y conversiones de nativo a PDF. La configuración de tiempo de espera especifica el tiempo máximo que tarda la conversión en completarse. El valor predeterminado es de 270 segundos. Estos ajustes no se utilizan durante las conversiones de imagen a PDF y de OpenOffice a PDF.

   * Si está cargando un archivo de configuración, escriba su ruta y nombre en el cuadro o haga clic en Examinar para buscar y seleccionar el archivo.

1. (Opcional) En XMP Archivo de metadatos, escriba la ruta y el nombre del archivo de XMP o haga clic en Examinar para buscar y seleccionar el archivo. Se puede utilizar un archivo XMP para incluir información de metadatos estándar. (Consulte [Acerca de los archivos XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Haga clic en Crear. Cuando se crea el archivo, aparece un vínculo a él. Si se produce un error durante la conversión, aparece una advertencia. Si está creando un archivo Postscript, la advertencia también contiene un vínculo al archivo de registro.
1. Haga clic en el vínculo del archivo PDF. El archivo se abre en Acrobat.

### Acerca de los archivos XMP {#about-xmp-files}

Los documentos de PDF que crea el Generador de PDF en Acrobat 5.0 o posterior contienen metadatos de documento en formato XML. *Metadatos* incluye información sobre el documento y su contenido, como el nombre del autor, palabras clave e información de copyright que las utilidades de búsqueda pueden utilizar.

Los metadatos del documento contienen (entre otros) información que también aparece en la ficha Descripción del cuadro de diálogo Propiedades del documento en Acrobat. Los cambios realizados en la ficha Descripción se reflejan en los metadatos del documento. Los metadatos de documento se pueden ampliar y modificar utilizando productos de terceros.

Adobe Extensible Metadata Platform (XMP) proporciona a las aplicaciones de Adobe un marco XML común que estandariza la creación, el procesamiento y el intercambio de metadatos de documentos entre los flujos de trabajo de publicación. Puede guardar e importar el código fuente XML de metadatos del documento en formato XMP, lo que facilita el uso compartido de metadatos entre varios documentos. Para obtener más información sobre XMP archivos, consulte [Plataforma de metadatos extensible (XMP)](https://www.adobe.com/products/xmp/) y [Centro de desarrolladores XMP Adobe](https://www.adobe.com/devnet/xmp.html).

Puede crear archivos XMP en Acrobat.

## Convertir un archivo HTML o ZIP en PDF {#convert-an-html-file-or-zip-file-to-pdf}

Puede utilizar el Generador de PDF para convertir los siguientes tipos de archivos a Adobe PDF:

* Los archivos HTML, que se pueden convertir cargando un archivo HTML o especificando la dirección URL de una página web o sitio web.
* Archivos archivados (ZIP), que pueden contener archivos de HTML, archivos de imagen o ambos.

Si el archivo ZIP contiene más de un archivo HTML en el nivel inferior de su jerarquía de carpetas, el archivo ZIP también debe contener un archivo index.htm o index.html.

>[!NOTE]
>
>La función de HTML a PDF requiere ciertas fuentes en el directorio de fuentes del sistema. En sistemas Linux, Solaris y AIX, el directorio de fuentes del sistema debe contener la fuente Courier. En sistemas Windows, el directorio de fuentes del sistema debe contener Times New Roman.

>[!NOTE]
>
>Para cargar un archivo desde el sistema de archivos local, utilice la opción Cargar archivo en la página HTML a PDF .

1. En la consola de administración, haga clic en Servicios > Generador de PDF > HTML a PDF.
1. Especifique el archivo que desea convertir realizando una de las siguientes tareas:

   * En Cargar archivo, escriba la ruta y el nombre de archivo del archivo HTML o ZIP, o haga clic en Examinar para localizarlo y seleccionarlo.
   * En el cuadro Especificar URL, escriba la dirección URL de la página o sitio web que desea convertir.

   >[!NOTE]
   >
   >El archivo que está convirtiendo debe tener una extensión de nombre de archivo .html, .htm o .zip.

1. Especifique los ajustes de configuración:

   * Para usar la configuración personalizada, seleccione Usar configuración personalizada, especifique la configuración de seguridad y tipo de archivo y especifique un valor de tiempo de espera. El valor predeterminado es 270 segundos.
   >[!NOTE]
   >
   >Si ha configurado el servicio Generar PDF para utilizar Acrobat WebCapture, la configuración de tipo de archivo que seleccione en esta página no afectará al PDF producido. En su lugar, realice los cambios correspondientes a la versión de Acrobat instalada en el servidor.

   * Para usar un archivo de configuración existente, seleccione Cargar archivo de configuración y haga clic en Examinar para ir a la ubicación del archivo.


1. Para cargar un archivo XMP, haga clic en Examinar y vaya a la ubicación del archivo. Se puede utilizar un archivo XMP para incluir información de metadatos estándar. (Consulte [Acerca de los archivos XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Haga clic en Crear. Cuando se crea el archivo, aparece un vínculo al archivo PDF.
1. Haga clic en el vínculo para ver el documento del PDF en Acrobat.

## Exportar un archivo PDF a otro formato de archivo (solo Windows) {#export-a-pdf-file-to-another-file-format-windows-only}

Puede exportar archivos de PDF a varios formatos de archivo, tal como se describe en el capítulo Generar servicio de PDF de [Referencia de servicios](https://www.adobe.com/go/learn_aemforms_services_63).

1. En la consola de administración, haga clic en Servicios > Generador de PDF > Export PDF.
1. Haga clic en Examinar para buscar el archivo PDF que desea exportar.
1. En el archivo Export PDF que desea enumerar, seleccione el formato al que desea exportar el archivo PDF.
1. En el cuadro Especificar un tiempo de espera, introduzca el tiempo de espera antes de que se agote el tiempo de espera de la aplicación. El valor predeterminado es 270 segundos.

   El tiempo de conversión que se muestra cuando se convierte el archivo puede ser mayor que el valor especificado aquí. El tiempo de conversión incluye el tiempo de espera para el subproceso o proceso, el tiempo necesario para convertir el archivo y el tiempo que tarda el convertidor de reserva (si corresponde). hora. El valor Especificar un tiempo de espera es solo el tiempo que se tarda en convertir el archivo.

1. (Opcional) En la **Especificar perfil de Preflight personalizado** , haga clic en Examinar y seleccione una [perfil de comprobación previa personalizado](https://helpx.adobe.com/es/acrobat/using/preflight-profiles-acrobat-pro.html). Los perfiles de comprobación previa solo se utilizan al convertir documentos al formato de archivo PDF (PDF/A).
1. Haga clic en Exportar. Cuando se completa la conversión, aparece un vínculo al archivo exportado.
1. Haga clic en el vínculo para ver el archivo convertido.

## Optimizar un PDF (solo Windows) {#optimize-a-pdf}

El Generador de PDF permite reducir el tamaño de los archivos PDF.

>[!NOTE]
>
>Al optimizar un documento firmado digitalmente, se eliminan e invalidan las firmas digitales.

1. En la consola de administración, haga clic en Servicios > Generador de PDF > Optimize PDF.
1. Haga clic en Examinar para buscar el archivo PDF que desea optimizar.
1. Especifique los ajustes de configuración:

   * Para usar la configuración personalizada, seleccione Usar configuración personalizada, especifique la configuración del tipo de archivo y un valor de tiempo de espera. El valor predeterminado es 270 segundos.
   * Para usar un archivo de configuración existente, seleccione Cargar archivo de configuración y haga clic en Examinar para ir a la ubicación del archivo.

1. Haga clic en Crear.
