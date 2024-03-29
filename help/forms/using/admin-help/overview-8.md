---
title: Descripción general del servicio de salida
seo-title: Overview of output service
description: Output permite combinar datos de formulario XML con un diseño de formulario creado en Designer para crear una secuencia de salida de documento en varios formatos.
seo-description: Output lets you merge XML form data with a form design created in Designer to create a document output stream in various formats.
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
exl-id: 00ca8bdf-77be-4f4c-a3d3-d61d13eeba7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 8%

---

# Descripción general del servicio de salida {#overview-of-output-service}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Output permite combinar datos de formulario XML con un diseño de formulario creado en Designer para crear una secuencia de salida de documento en varios formatos. El flujo de salida se puede enviar a una impresora de red, una impresora local o un archivo de disco

Puede utilizar la página Salida en la consola de administración para administrar el servicio Salida. Los ajustes que configure se utilizan en tiempo de ejecución cuando los ajustes equivalentes no se especificaron a través de la API de formularios AEM. La configuración realizada mediante el SDK de AEM forms anula la configuración establecida mediante la consola de administración.

Para obtener información adicional sobre el servicio Output , consulte [Referencia de servicios](https://www.adobe.com/go/learn_aemforms_services_61).

En las páginas Salida de la consola de administración, puede realizar varias tareas:

* Especifique conjuntos de caracteres para la internacionalización. (Consulte [Cambiar el conjunto de caracteres](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* Especifique rutas absolutas y relativas para direcciones URL, URI, XCI y ubicaciones de archivos. (Consulte [Especificar ubicaciones de archivos para la salida](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* Configure tamaños y políticas de caché. (Consulte [Especificación del modo de caché](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) y [Configuración de la caché](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* Haga que las fuentes estén disponibles en el servidor de aplicaciones. (Consulte [Hacer que las fuentes estén disponibles](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* Especificar fuentes para incrustar. (Consulte [Especificar fuentes para incrustar](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* Especificar las opciones de configuración XCI. (Consulte [Especificar las opciones de configuración XCI](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* Especificar la configuración de seguridad. (Consulte [Especificar la configuración de seguridad](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

Después de cambiar la configuración, haga clic en Guardar para aplicarla a Salida. No es necesario reiniciar el servidor para que los cambios surtan efecto, pero es posible que tenga que reiniciar el servicio Output al configurar la caché.
