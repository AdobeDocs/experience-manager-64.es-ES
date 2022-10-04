---
title: Especificación de las opciones de configuración XCI
seo-title: Specifying XCI configuration options
description: Aprenda a especificar las opciones de configuración de XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 1%

---

# Especificación de las opciones de configuración XCI {#specifying-xci-configuration-options}

Forms le permite especificar un archivo XCI personalizado que utilizará para la renderización. (Consulte [Configuración de ubicaciones para Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) De forma predeterminada, Forms anula algunas de las opciones especificadas en el archivo XCI, entre las que se incluyen las siguientes:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Puede seleccionar opciones que cancelen la anulación de las opciones enumeradas anteriormente, en cuyo caso Forms utilizará los valores especificados en el archivo XCI personalizado.

1. En la consola de administración, haga clic en Servicios > Forms.
1. Active o desactive la casilla de verificación Usar opciones XCI predeterminadas del sistema. Cuando se selecciona esta opción, Forms utiliza sus valores predeterminados para los ajustes de paquetes, creador, productor y compressObjectStream. Cuando se anula la selección de esta opción, Forms utiliza los valores especificados en el archivo XCI personalizado.
1. Haga clic en Guardar.
