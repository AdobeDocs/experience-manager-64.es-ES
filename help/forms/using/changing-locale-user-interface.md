---
title: Cambio de la configuración regional de la interfaz de usuario del espacio de trabajo de AEM Forms
seo-title: Changing the locale of AEM Forms workspace user interface
description: Cómo modificar el espacio de trabajo de AEM Forms para localizar texto, categorías contraídas, colas y procesos, y el selector de fechas en la interfaz.
seo-description: How to modify the AEM Forms workspace to localize text, collapsed categories, queues, and processes, and the date picker on the interface.
uuid: f8e7d399-98d9-4655-b51f-0346a5713f06
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: e4ca8188-fb9a-44bf-8437-a98abaa7521a
exl-id: 9968f399-454b-4cb2-b6af-2c16428ca7b4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Cambio de la configuración regional de la interfaz de usuario del espacio de trabajo de AEM Forms {#changing-the-locale-of-aem-forms-workspace-user-interface}

El espacio de trabajo de AEM Forms es compatible de serie con los idiomas inglés, francés, alemán y japonés. También permite localizar la interfaz de usuario del espacio de trabajo de AEM Forms en cualquier otro idioma.

Para localizar la interfaz de usuario del espacio de trabajo de AEM Forms en el idioma que elija:

* Localice el texto del espacio de trabajo de AEM Forms.
* Localice las categorías contraídas, las colas y los procesos.
* Localizar selector de fechas

Antes de realizar los pasos anteriores, asegúrese de seguir los pasos enumerados en [Pasos genéricos para la personalización del espacio de trabajo de AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Para cambiar el idioma de la pantalla de inicio de sesión del espacio de trabajo de AEM Forms, consulte [Creación de una nueva pantalla de inicio de sesión](/help/forms/using/creating-new-login-screen.md).

## Localización de texto {#localizing-text}

Realice los siguientes pasos para agregar compatibilidad con un idioma *Nuevo* y el código de configuración regional del navegador *nw*.

1. Inicie sesión en el CRXDE Lite.

   La dirección URL predeterminada del CRXDE Lite es `https://[server]:[port]/lc/crx/de/index.jsp`.

1. Vaya a la ubicación `apps/ws/locales` y crear una carpeta nueva `nw.`
1. Copiar el archivo `translation.json`desde la ubicación `/apps/ws/locales/en-US` a ubicación `/apps/ws/locales/nw`.
1. Vaya a `/apps/ws/locales/nw` y abrir `translation.json` para editar. Realice cambios específicos de la configuración regional en el archivo translation.json.

   Los siguientes ejemplos contienen el archivo translation.json para las configuraciones regionales en inglés y francés del espacio de trabajo de AEM Forms.

   ![translation_json_in_es](assets/translation_json_in_en.png) ![translation_json_in_fr](assets/translation_json_in_fr.png)

## Localización de categorías, colas y procesos contraídos {#localizing-collapsed-categories-queues-and-processes}

El espacio de trabajo de AEM Forms utiliza imágenes para mostrar encabezados de categorías, colas y procesos. Se necesita un paquete de desarrollo para localizar estos encabezados. Para obtener información detallada sobre la creación de paquetes de desarrollo, consulte [Creación del código de espacio de trabajo de AEM Forms.](introduction-customizing-html-workspace.md#building-html-workspace-code)

En los pasos siguientes, se da por hecho que los nuevos archivos de imagen localizados son *Categories_nw.png*, *Queue_nw.png* y *Processes_nw.png*. La anchura recomendada de las imágenes es de 19 píxeles.

>[!NOTE]
>
>Para encontrar el código de configuración regional del idioma del navegador. Abra `https://[server]:[port]/lc/libs/ws/Locale.html`.

![contraer_paneles_imagen](assets/collapsing_panels_image.png)

Siga estos pasos para localizar las imágenes:

1. Con un cliente WebDAV, coloque los archivos de imagen en la variable */apps/ws/images* carpeta.
1. Vaya a */apps/ws/css*. Apertura *newStyle.css* para editar y añadir las siguientes entradas:

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Realice todos los cambios semánticos enumerados en la [Personalización de Workspace](/help/forms/using/introduction-customizing-html-workspace.md) artículo.
1. Vaya a la *js/runtime/utilidad* y abra el archivo usuariesession.js* para editarlo.
1. Busque el código que aparece en el bloque de código original y añada la condición *lang !== &#39;nw&#39;* a la sentencia if :

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Localización del selector de fechas {#localizing-date-picker}

Se necesita un paquete de desarrollo para localizar la API *datepicker *API. Para obtener información detallada sobre la creación de paquetes de desarrollo, consulte [Creación del código de espacio de trabajo de AEM Forms](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Descargue y extraiga el [Paquete de IU de jQuery](https://jqueryui.com/download/all/), vaya a *&lt;extracted jquery=&quot;&quot; ui=&quot;&quot; package=&quot;&quot;>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Copie el archivo jquery.ui.datepicker-nw.js para el código de configuración regional ahora en apps/ws/js/libs/jqueryui y realice cambios específicos de configuración regional en el archivo .
1. Vaya a `apps/ws/js` y abra el `jquery.ui.datepicker-nw.js` para editar.
1. En el archivo main.js, cree un alias para `jquery.ui.datepicker-nw.js.` El código para crear un alias para la variable `jquery.ui.datepicker-nw.js` es:

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Usar alias `jqueryuidatepickernw` para incluir el `jquery.ui.datepicker-nw.js` en todos los archivos que utilizan datepicker. El selector de fecha se utiliza en los siguientes archivos:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   El código de ejemplo siguiente muestra cómo añadir la entrada jquery.ui.datepicker-nw.js:

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. En todos los archivos que utilizan la API del selector de fecha, cambie la configuración predeterminada de la API del selector de fecha. La API del selector de fecha se utiliza en los siguientes archivos:

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Cambie el siguiente código para agregar la nueva configuración regional:

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

hasta

```
if (locale === 'ja-JP') {
    $.datepicker.setDefaults($.datepicker.regional.ja);
} else if (locale === 'de-DE') {
    $.datepicker.setDefaults($.datepicker.regional.de);
} else if (locale === 'fr-FR') {
    $.datepicker.setDefaults($.datepicker.regional.fr);
} else if (locale === 'nw') {
    $.datepicker.setDefaults($.datepicker.regional.nw);
} else {
    $.datepicker.setDefaults($.datepicker.regional['']);
}
```
