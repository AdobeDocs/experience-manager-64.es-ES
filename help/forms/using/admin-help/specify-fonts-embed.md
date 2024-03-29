---
title: Especificar fuentes para incrustar
seo-title: Specify fonts to embed
description: Aprenda a especificar fuentes para incrustar.
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 6%

---

# Especificar fuentes para incrustar{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede especificar qué fuentes se incrustan siempre o nunca se incrustan en los formularios utilizados por Output. La incrustación de fuentes aumenta el tamaño de archivo de los formularios. Incruste fuentes inusuales que los usuarios probablemente no tengan en sus sistemas y no incruste fuentes comunes que tendrán instaladas.

>[!NOTE]
>
>Si ha especificado un archivo XCI personalizado para Output, la opción incrustar fuente del archivo XCI anula esta configuración. (Consulte [Especificar ubicaciones de archivos para la salida](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. En la consola de administración, haga clic en Servicios > salida.
1. En Configuración de incrustación de fuentes, en el cuadro Incrustar siempre fuentes, escriba los nombres de las fuentes que desee incrustar en los formularios separados por comas. Las fuentes que especifique solo se incrustarán en el formulario generado si se utilizan en el formulario. Esta configuración se ignora si la opción incrustar fuente se ha activado en el archivo XCI pasado al servicio. En ese caso, todas las fuentes utilizadas en el PDF siempre están incrustadas.
1. En el cuadro No incrustar nunca fuentes, escriba los nombres de las fuentes que no se van a incrustar en los formularios separados por comas. Las fuentes que especifique no están incrustadas en el PDF, aunque se utilicen en el PDF generado. Esta configuración se ignora si la opción incrustar fuente se ha desactivado en el archivo XCI pasado al servicio. En ese caso, ninguna de las fuentes utilizadas en el PDF está incrustada.
1. Haga clic en Guardar.
