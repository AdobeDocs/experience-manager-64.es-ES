---
title: Cambiar los estilos predeterminados de los formularios HTML5
seo-title: Changing default styles of HTML5 forms
description: El estilo de los formularios HTML5 se basa en CSS. Puede cambiar los estilos predeterminados del formulario.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 88%

---

# Cambiar los estilos predeterminados de los formularios HTML5 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los formularios HTML5 se procesan con las funciones HTML5 y el estilo del formulario procesado se realiza con CSS. El aspecto predeterminado de los formularios HTML5 es similar a su representación en PDF. Los desarrolladores pueden utilizar CSS personalizadas para cambiar el aspecto predeterminado de los formularios HTML5.

Este artículo proporciona información paso a paso para cambiar el estilo de un formulario HTML5 y el artículo [Introducción a los estilos](/help/forms/using/css-styles.md) contiene información detallada sobre varios aspectos relacionados con el estilo de los formularios HTML5. Asegúrese de leer Introducción a los estilos antes de realizar los pasos mencionados en este artículo.

Las dos imágenes siguientes muestran la diferencia entre los estilos predeterminados y los personalizados.

![picture-002-small](assets/pictures-002-small.png)

## Aplicar estilo a los formularios {#style-your-forms}

1. **Elija un perfil al que agregar estilos personalizados**

   Acceda a la interfaz CRX DE en la URL: **https://&lt;server>:&lt;port>/crx/de** y cree un perfil o elija uno existente. Para obtener información sobre cómo crear un perfil, consulte [Crear un perfil nuevo](/help/forms/using/custom-profile.md).

1. **Crear una hoja de estilos CSS para aplicar estilo a los formularios HTML5**

   Navegue hasta la carpeta en la que ha creado el procesador de perfiles y cree un archivo de hoja de estilo CSS. Los pasos a seguir son los siguientes:

   1. Haga clic con el botón derecho en la carpeta y seleccione **crear** -> **crear archivo** en el menú
   Para saber qué clases CSS crear para un componente en particular en los formularios HTML5, consulte [Introducción a los estilos](/help/forms/using/css-styles.md).

1. **Incluya la hoja de estilo en el procesador de perfiles**

   Abra la página Procesador de perfiles (archivo jsp) en CRX DE e incluya el archivo CSS en la página, justo debajo de la biblioteca de cliente XFA. Siga estos pasos para incluir el archivo CSS en el perfil.

   1. Busque la siguiente línea en la página del procesador:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Inserte lo siguiente debajo de la línea anterior para incluir la hoja de estilo:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Guarde el archivo.
