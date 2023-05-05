---
title: Especificar las opciones de configuración XCI
seo-title: Specify XCI configuration options
description: Aprenda a especificar las opciones de configuración de XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 10%

---

# Especificar las opciones de configuración XCI {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Output permite especificar un archivo XCI personalizado que utiliza para el procesamiento. (Consulte [Especificar ubicaciones de archivos para la salida](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) De forma predeterminada, Output anula algunas de las opciones especificadas en el archivo XCI, entre las que se incluyen las siguientes:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Puede seleccionar las opciones que cancelan la anulación de las opciones enumeradas anteriormente, en cuyo caso Output utiliza los valores especificados en el archivo XCI personalizado.

1. En la consola de administración, haga clic en Servicios > salida.
1. Active o desactive la casilla de verificación Usar opciones XCI predeterminadas del sistema. Cuando se selecciona esta opción, Output utiliza sus valores predeterminados para los ajustes de paquetes, creador, productor y compressObjectStream. Cuando se anula la selección de esta opción, Output utiliza los valores especificados en el archivo XCI personalizado.
1. Haga clic en Guardar.
