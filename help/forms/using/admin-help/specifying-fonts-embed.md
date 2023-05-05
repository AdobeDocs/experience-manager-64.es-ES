---
title: Especificar fuentes para incrustar
seo-title: Specifying fonts to embed
description: Aprenda a especificar fuentes para incrustar.
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 6%

---

# Especificar fuentes para incrustar {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede especificar qué fuentes se incrustan siempre o nunca se incrustan en los formularios que genera el servicio de Forms. La incrustación de fuentes aumenta el tamaño de archivo de los formularios. Incruste fuentes inusuales que los usuarios rara vez tienen en sus sistemas. No incruste fuentes comunes que normalmente tienen instaladas.

>[!NOTE]
>
>Si ha especificado un archivo XCI personalizado para Forms, la opción de incrustar fuente en el archivo XCI anula esta configuración. (Consulte [Configuración de ubicaciones para Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. En la consola de administración, haga clic en **[!UICONTROL Servicios > Forms]**.
1. En **[!UICONTROL Configuración de incrustación de fuentes]**, en el **[!UICONTROL Incrustar siempre fuentes]** , escriba los nombres de las fuentes que desea incrustar con los formularios separados por comas. Las fuentes que especifique solo se incrustarán en el formulario generado si se utilizan en el formulario. Esta configuración se ignora si la opción incrustar fuente se ha activado en el archivo XCI pasado al servicio porque, en ese caso, todas las fuentes utilizadas en el PDF siempre están incrustadas.
1. En el **[!UICONTROL No incrustar nunca fuentes]** , escriba los nombres de las fuentes que no se van a incrustar en los formularios separados por comas. Las fuentes que especifique no están incrustadas en el PDF, aunque se utilicen en el PDF generado. Esta configuración se ignora si la opción incrustar fuente se ha desactivado en el archivo XCI pasado al servicio porque, en ese caso, ninguna de las fuentes utilizadas en el PDF está incrustada.
1. Haga clic en **[!UICONTROL Guardar]**.
