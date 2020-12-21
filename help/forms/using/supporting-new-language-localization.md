---
title: Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables
seo-title: Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables
description: AEM Forms le permite agregar nuevas configuraciones regionales para localizar formularios adaptables. Las configuraciones regionales admitidas de forma predeterminada son inglés, francés, alemán y japonés.
seo-description: AEM Forms le permite agregar nuevas configuraciones regionales para localizar formularios adaptables. Las configuraciones regionales admitidas de forma predeterminada son inglés, francés, alemán y japonés.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
translation-type: tm+mt
source-git-commit: c5a78d6c2b8a55cad6266e86e9b990cafc038431
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---


# Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables {#supporting-new-locales-for-adaptive-forms-localization}

## Acerca de los diccionarios de configuración regional {#about-locale-dictionaries}

La localización de formularios adaptables se basa en dos tipos de diccionarios de configuración regional:

**Diccionario específico del formularioContiene cadenas utilizadas en formularios adaptables.** Por ejemplo, etiquetas, nombres de campo, mensajes de error, descripciones de ayuda, etc. Se administra como un conjunto de archivos XLIFF para cada configuración regional y puede acceder a ellos en https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Diccionarios globalesHay dos** diccionarios globales, administrados como objetos JSON, en AEM biblioteca del cliente. Estos diccionarios contienen mensajes de error predeterminados, nombres de mes, símbolos de moneda, patrones de fecha y hora, etc. Puede encontrar estos diccionarios en CRXDe Lite en /libs/fd/xfaforms/clientlibs/I18N. Estas ubicaciones contienen carpetas independientes para cada configuración regional. Debido a que los diccionarios globales generalmente no se actualizan con frecuencia, mantener archivos JavaScript separados para cada configuración regional permite a los navegadores almacenarlos en caché y reducir el uso del ancho de banda de la red al acceder a diferentes formularios adaptables en el mismo servidor.

### Cómo funciona la localización de formularios adaptables {#how-localization-of-adaptive-form-works}

Cuando se procesa un formulario adaptable, identifica la configuración regional solicitada observando los siguientes parámetros en el orden especificado:

* Parámetro de solicitud `afAcceptLang`

   Para anular la configuración regional del explorador de los usuarios, puede pasar el parámetro de solicitud `afAcceptLang` para forzar la configuración regional. Por ejemplo, la siguiente URL obligará a procesar el formulario en la configuración regional japonesa:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* Configuración regional del explorador establecida para el usuario, que se especifica en la solicitud mediante el encabezado `Accept-Language`.

* Configuración de idioma del usuario especificado en AEM.

Una vez identificada la configuración regional, los formularios adaptables seleccionan el diccionario específico del formulario. Si no se encuentra el diccionario específico del formulario para la configuración regional solicitada, se utiliza el diccionario inglés (en).

Si no existe una biblioteca de cliente para la configuración regional solicitada, busca una biblioteca de cliente para el código de idioma presente en la configuración regional. Por ejemplo, si la configuración regional solicitada es `en_ZA` (inglés sudafricano) y la biblioteca de cliente para `en_ZA` no existe, el formulario adaptable utilizará la biblioteca del cliente para `en` (inglés), si existe. Sin embargo, si no existe ninguno, el formulario adaptable utiliza el diccionario para la configuración regional `en`.

## Añadir compatibilidad con localizaciones para configuraciones regionales no admitidas {#add-localization-support-for-non-supported-locales}

Actualmente, AEM Forms admite la localización de contenido de formularios adaptables en inglés (en), español (es), francés (fr), italiano (it), alemán (de), japonés (ja), portugués-brasileño (pt-BR, chino-CN), chino-taiwanés (zh-TW) y coreano (ko-KR).

Para añadir compatibilidad con una nueva configuración regional en tiempo de ejecución de formularios adaptables:

1. [Añadir una configuración regional al servicio GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Añadir la biblioteca de cliente XFA para una configuración regional](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Añadir la biblioteca del cliente de formularios adaptables para una configuración regional](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Añadir la compatibilidad de configuración regional con el diccionario](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Reinicie el servidor](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Añadir una configuración regional al servicio de Localización de guía {#add-a-locale-to-the-guide-localization-service-br}

1. Ir a `https://[server]:[port]/system/console/configMgr`.
1. Haga clic para editar el componente **Guide Localización Service**.
1. Añada la configuración regional que desee agregar a la lista de configuraciones regionales admitidas.

![GuideLocalizationService](assets/configservice.png)

### Añadir la biblioteca de cliente XFA para una configuración regional {#add-xfa-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>`, con la categoría `xfaforms.I18N.<locale>`, y agregue los siguientes archivos a la biblioteca del cliente:

* **I18N.** jsdefiniendo  `xfalib.locale.Strings` para los  `<locale>` definidos en  `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.** txtque contiene lo siguiente:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Añadir la biblioteca de cliente de formulario adaptable para una configuración regional {#add-adaptive-form-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>`, con categoría como `guides.I18N.<locale>` y dependencias como `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` y `guide.common`. &quot;

Añada los siguientes archivos a la biblioteca del cliente:

* **i18n.** jsdefine  `guidelib.i18n`, con patrones de &quot;calendarSymbols&quot;,  `datePatterns`,  `timePatterns`,  `dateTimeSymbols`,  `numberPatterns`,  `numberSymbols`,  `currencySymbols`para las especificaciones  `typefaces`   `<locale>`   [ ](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf)de XFA descritas en la Especificación de Conjunto Locale. También puede ver cómo se define para otras configuraciones regionales admitidas en `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.** jsdefiniendo  `guidelib.i18n.strings` y  `guidelib.i18n.LogMessages` para los  `<locale>` definidos en  `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.** txtque contiene lo siguiente:

```
i18n.js
LogMessages.js
```

### Añadir la compatibilidad de configuración regional para el diccionario {#add-locale-support-for-the-dictionary-br}

Realice este paso sólo si el `<locale>` que está agregando no se encuentra entre `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Cree un nodo `nt:unstructured` `languages` en `etc`, si no está presente ya.

1. Añada una propiedad de cadena con varios valores `languages` en el nodo, si no está presente ya.
1. Añada los `<locale>` valores de configuración regional predeterminados `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si no está presente ya.

1. Añada `<locale>` a los valores de la propiedad `languages` de `/etc/languages`.

El `<locale>` aparecerá en `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Reinicie el servidor {#restart-the-server}

Reinicie el servidor de AEM para que la configuración regional agregada entre en vigor.

## Bibliotecas de muestra para agregar compatibilidad con español {#sample-libraries-for-adding-support-for-spanish}

Bibliotecas cliente de muestra para agregar compatibilidad con español

[Obtener archivo](assets/sample.zip)
