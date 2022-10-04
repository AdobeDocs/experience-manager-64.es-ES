---
title: Cambio de los estilos predeterminados de los formularios HTML5
seo-title: Changing default styles of HTML5 forms
description: El estilo de los formularios de HTML5 se basa en CSS. Puede cambiar los estilos predeterminados del formulario.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Cambio de los estilos predeterminados de los formularios HTML5 {#changing-default-styles-of-html-forms}

Los formularios de HTML5 se procesan con las funciones de HTML5 y el estilo del formulario procesado se realiza con CSS. El aspecto predeterminado de los formularios HTML5 es similar a su representación en PDF. Los desarrolladores pueden utilizar CSS personalizada para cambiar el aspecto predeterminado de los formularios HTML5.

Este artículo proporciona información paso a paso para cambiar el estilo de un formulario HTML5 y [Introducción a los estilos](/help/forms/using/css-styles.md) El artículo contiene información detallada sobre varios aspectos relacionados con el estilo de los formularios HTML5. Asegúrese de leer Introducción a los estilos antes de realizar los pasos mencionados en este artículo.

Las dos imágenes siguientes muestran la diferencia entre los estilos predeterminados y personalizados.

![picture-002-small](assets/pictures-002-small.png)

## Estilos de los formularios {#style-your-forms}

1. **Elegir un perfil para agregar estilos personalizados**

   Acceda a la interfaz CRX DE en la URL: **https://&lt;server>:&lt;port>/crx/de** y cree un perfil o elija un perfil existente. Para obtener información sobre cómo crear un perfil, consulte [Creación de un nuevo perfil](/help/forms/using/custom-profile.md)

1. **Crear una hoja de estilos CSS para aplicar estilo a los formularios HTML5**

   Vaya a la carpeta en la que ha creado el procesador de perfiles y cree un archivo de hoja de estilo CSS. Los pasos a seguir son

   1. Haga clic con el botón derecho en la carpeta y seleccione **crear** -> **crear archivo** en el menú
   Para saber qué clases CSS crear para un componente en particular en los formularios HTML5, consulte [Introducción a los estilos](/help/forms/using/css-styles.md).

1. **Incluir la hoja de estilo en el procesador de perfiles**

   Abra la página Procesador de perfiles (archivo jsp) en CRX DE e incluya el archivo CSS en la página, justo debajo de la biblioteca de cliente XFA. Siga estos pasos para incluir el archivo CSS en el perfil.

   1. Busque en la página del procesador la línea siguiente:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Inserte lo siguiente debajo de la línea anterior para incluir la hoja de estilo:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Guarde el archivo.
