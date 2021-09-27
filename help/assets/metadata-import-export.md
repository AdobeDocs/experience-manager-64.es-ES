---
title: Importación y exportación de metadatos masivos
description: Este artículo describe cómo importar y exportar metadatos de forma masiva.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: 2b3a6972d703314d56d3dc711fb6a514cb1942d5
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 9%

---

# Importación y exportación masivas de metadatos {#bulk-metadata-import-and-export}

AEM Assets permite importar metadatos de recursos de forma masiva mediante un archivo CSV. Puede realizar actualizaciones masivas de los recursos cargados recientemente o de los existentes mediante la importación de un archivo CSV. También puede introducir metadatos de recursos de forma masiva desde sistemas de terceros en formato CSV.

## Importar metadatos {#import-metadata}

La importación de metadatos es asíncrona y no impide el rendimiento del sistema. La actualización simultánea de los metadatos de varios recursos puede requerir muchos recursos debido a XMP actividad de reescritura si se marca el indicador de flujo de trabajo. Planifique una importación de este tipo durante el uso limitado del servidor para evitar que otros usuarios afecten al rendimiento.

>[!NOTE]
>
>Para importar metadatos en áreas de nombres personalizadas, registre primero las áreas de nombres.

Para importar metadatos de forma masiva, siga estos pasos:

1. Vaya a la interfaz de usuario de Assets y pulse o haga clic en **[!UICONTROL Crear]** en la barra de herramientas.
1. En el menú, seleccione **[!UICONTROL Metadatos]**.
1. En la página **[!UICONTROL Importación de metadatos]**, pulse o haga clic en **[!UICONTROL Seleccionar archivo]**.  Seleccione el archivo CSV con los metadatos.
1. Asegúrese de que el archivo CSV contiene los siguientes parámetros:

   | Parámetros de importación de metadatos | Descripción |
   |:---|:---|
   | [!UICONTROL Tamaño del lote] | Número de recursos de un lote para los que se van a importar metadatos. El valor predeterminado es 50. El valor máximo es 100. |
   | [!UICONTROL Separador de campos] | El valor predeterminado es `,`, una coma. Puede especificar cualquier otro carácter. |
   | [!UICONTROL Delimitador de varios valores] | Separador para valores de metadatos. El valor predeterminado es `|` - una barra vertical. |
   | [!UICONTROL Lanzar flujos de trabajo] | False de forma predeterminada. Cuando se establece en true y la configuración predeterminada está en vigor para `DAM Metadata WriteBack Workflow` (que escribe metadatos en los datos de XMP binarios). La activación de los flujos de trabajo afecta al rendimiento del sistema. |
   | [!UICONTROL Nombre de columna de ruta de activos] | Define el nombre de columna del archivo CSV con recursos. |

1. Toque o haga clic en **[!UICONTROL Importar]** desde la barra de herramientas. Una vez importados los metadatos, se envía una notificación a la bandeja de entrada de notificaciones. Vaya a la página de propiedades del recurso y compruebe si los valores de metadatos se importan correctamente para los recursos.

Para agregar fecha y marca de hora al importar metadatos, use el formato `YYYY-MM-DDThh:mm:ss.fff-00:00` para fecha y hora. La fecha y la hora están separadas por `T`, `hh` es horas en formato de 24 horas, `fff` es nanosegundos y `-00:00` es desplazamiento de zona horaria. Por ejemplo, `2020-03-26T11:26:00.000-07:00` es el 26 de marzo de 2020 a las 11:26:00.000 AM, hora del PST.

>[!CAUTION]
>
>Si el formato de fecha no coincide con `YYYY-MM-DDThh:mm:ss.fff-00:00`, no se establecen los valores de fecha. Los formatos de fecha del archivo CSV de metadatos exportado tienen el formato `YYYY-MM-DDThh:mm:ss-00:00`. Si desea importarla, conviértala al formato aceptable añadiendo el valor de nanosegundos indicado por `fff`.

## Exportar metadatos {#export-metadata}

Algunos casos de uso para exportar metadatos de forma masiva son:

* Importe los metadatos en un sistema de terceros al migrar recursos.
* Comparta metadatos de recursos con un equipo de proyecto más amplio.
* Probar o auditar los metadatos para comprobar el cumplimiento.
* Externalice los metadatos para una localización independiente.

Puede exportar metadatos de varios recursos en formato CSV. Los metadatos se exportan de forma asíncrona y no afectan al rendimiento del sistema. Para exportar metadatos, AEM atraviesa las propiedades del nodo de recursos `jcr:content/metadata` y sus nodos secundarios y exporta las propiedades de metadatos en un archivo CSV.

Para exportar metadatos de varios recursos de forma masiva, siga estos pasos:

1. Seleccione la carpeta de recursos que contiene los recursos para los que desea exportar metadatos. En la barra de herramientas, seleccione **[!UICONTROL Export metadata]**.

1. En el cuadro de diálogo [!UICONTROL Exportación de metadatos], especifique un nombre para el archivo CSV. Para exportar metadatos de recursos en subcarpetas, seleccione **[!UICONTROL Incluir recursos en subcarpetas]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Seleccione las opciones que desee. Proporcione un nombre de archivo y, si es necesario, una fecha.
1. En **[!UICONTROL Properties to be export]**, especifique si desea exportar todas las propiedades o propiedades específicas. Si elige **[!UICONTROL Propiedades selectivas]** que se exportarán, agregue las propiedades que desee.

1. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Exportar]**. Un mensaje confirma que se exportan los metadatos. Cierre el mensaje.

1. Abra la notificación de la bandeja de entrada para el trabajo de exportación. Seleccione el trabajo y haga clic en **[!UICONTROL Abrir]** en la barra de herramientas. Para descargar el archivo CSV con los metadatos, pulse o haga clic en **[!UICONTROL Descargar CSV]** desde la barra de herramientas. Haga clic en **[!UICONTROL Cerrar]**.

   ![csv_download](assets/csv_download.png)
