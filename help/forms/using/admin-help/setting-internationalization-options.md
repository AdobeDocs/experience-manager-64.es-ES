---
title: Configurar las opciones de internacionalización
seo-title: Setting internationalization options
description: Aprenda a especificar la configuración regional utilizada para procesar formularios y a especificar el conjunto de caracteres utilizado para codificar el flujo de salida.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 6%

---

# Configurar las opciones de internacionalización{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Especificar la configuración regional utilizada para procesar formularios {#specify-the-locale-used-to-render-forms}

Puede especificar la configuración regional que se utilizará al procesar un formulario de PDF. Los campos de un formulario de PDF utilizan la configuración regional especificada para mostrar los datos. Por ejemplo, si la configuración regional está definida en alemán, el formulario utiliza separadores decimales alemanes para los valores numéricos. La configuración regional también se utiliza para enviar mensajes de validación a dispositivos cliente, como exploradores web, como parte de transformaciones de HTML.

1. En la consola de administración, haga clic en Servicios > Forms.
1. En Internacionalización, en la lista Idioma, seleccione la configuración regional utilizada para procesar un formulario. El valor predeterminado es inglés (Estados Unidos).
1. Haga clic en Guardar.

## Especifique el conjunto de caracteres utilizado para codificar el flujo de salida {#specify-the-character-set-used-to-encode-the-output-stream}

1. En Internacionalización, en la lista Conjunto de caracteres, seleccione un conjunto de caracteres. Esta configuración depende de la API utilizada, renderHTMLForm o renderPDFForm. Para especificar un conjunto de caracteres que no sea el enumerado, seleccione Personalizado y especifique un valor de codificación en el cuadro que se muestra.

   Para transformaciones de HTML, AEM formularios admite valores de codificación de caracteres definidos por el `java.nio.charset` paquete. Si sFormPreference es PDFForm, solo se admiten conjuntos de caracteres específicos. El conjunto de caracteres debe ser un nombre canónico válido. El valor predeterminado es ISO-8859-1.

1. Haga clic en Guardar.
