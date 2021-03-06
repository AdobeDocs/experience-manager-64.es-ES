---
title: Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables
seo-title: Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables
description: AEM Forms le permite agregar nuevas configuraciones regionales para localizar formularios adaptables. Las configuraciones regionales compatibles de forma predeterminada son inglés, francés, alemán y japonés.
seo-description: AEM Forms le permite agregar nuevas configuraciones regionales para localizar formularios adaptables. Las configuraciones regionales compatibles de forma predeterminada son inglés, francés, alemán y japonés.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Formularios adaptables
role: Admin
exl-id: 9f0e7284-ac11-406d-8d8c-7682f1d66fff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Compatibilidad con nuevas configuraciones regionales para la localización de formularios adaptables {#supporting-new-locales-for-adaptive-forms-localization}

## Acerca de los diccionarios de configuración regional {#about-locale-dictionaries}

La localización de formularios adaptables se basa en dos tipos de diccionarios de configuración regional:

**Diccionario específico del** formularioContiene cadenas utilizadas en los formularios adaptables. Por ejemplo, etiquetas, nombres de campos, mensajes de error, descripciones de ayuda, etc. Se administra como un conjunto de archivos XLIFF para cada configuración regional y puede acceder a él en https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Diccionarios** globalesHay dos diccionarios globales, administrados como objetos JSON, en AEM biblioteca de cliente. Estos diccionarios contienen mensajes de error predeterminados, nombres de mes, símbolos de moneda, patrones de fecha y hora, etc. Puede encontrar estos diccionarios en CRXDe Lite en /libs/fd/xfaforms/clientlibs/I18N. Estas ubicaciones contienen carpetas independientes para cada configuración regional. Debido a que los diccionarios globales generalmente no se actualizan con frecuencia, mantener archivos JavaScript separados para cada configuración regional permite a los navegadores almacenarlos en caché y reducir el uso del ancho de banda de red al acceder a diferentes formularios adaptables en el mismo servidor.

### Funcionamiento de la localización del formulario adaptable {#how-localization-of-adaptive-form-works}

Cuando se procesa un formulario adaptable, identifica la configuración regional solicitada mirando los siguientes parámetros en el orden especificado:

* Parámetro de solicitud `afAcceptLang`

   Para anular la configuración regional del explorador de los usuarios, puede pasar el parámetro de solicitud `afAcceptLang` para forzar la configuración regional. Por ejemplo, la siguiente dirección URL obligará a procesar el formulario en la configuración regional de japonés:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* Configuración regional del explorador establecida para el usuario, que se especifica en la solicitud utilizando el encabezado `Accept-Language`.

* Configuración de idioma del usuario especificado en AEM.

Una vez identificada la configuración regional, los formularios adaptables seleccionan el diccionario específico del formulario. Si no se encuentra el diccionario específico del formulario para la configuración regional solicitada, se utiliza el diccionario inglés (en) .

Si no existe una biblioteca de cliente para la configuración regional solicitada, se busca una biblioteca de cliente para el código de idioma presente en la configuración regional. Por ejemplo, si la configuración regional solicitada es `en_ZA` (inglés sudafricano) y la biblioteca de cliente para `en_ZA` no existe, el formulario adaptable utilizará la biblioteca de cliente para `en` (inglés), si existe. Sin embargo, si no existe ninguno, el formulario adaptable utiliza el diccionario para la configuración regional `en`.

## Agregar compatibilidad con la localización para configuraciones regionales no admitidas {#add-localization-support-for-non-supported-locales}

Actualmente, AEM Forms admite la localización de contenido de formularios adaptables en las configuraciones regionales de inglés (en), español (es), francés (fr), italiano (it), alemán (de), japonés (ja), portugués-brasileño (pt-BR, chino- (zh-CN), chino-taiwanés (zh-TW) y coreano (ko-KR).

Para añadir compatibilidad con una nueva configuración regional en el tiempo de ejecución de los formularios adaptables:

1. [Añadir una configuración regional al servicio GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Agregar una biblioteca de cliente XFA para una configuración regional](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Agregar una biblioteca de cliente de formulario adaptable para una configuración regional](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Agregar compatibilidad con la configuración regional para el diccionario](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Reinicio del servidor](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Añadir una configuración regional al servicio de localización de guías {#add-a-locale-to-the-guide-localization-service-br}

1. Ir a `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en para editar el componente **Guide Localization Service**.
1. Agregue la configuración regional que desee agregar a la lista de configuraciones regionales admitidas.

![GuideLocalizationService](assets/configservice.png)

### Agregar una biblioteca de cliente XFA para una configuración regional {#add-xfa-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>`, con la categoría `xfaforms.I18N.<locale>`, y agregue los siguientes archivos a la biblioteca del cliente:

* **I18N.** jsdefine  `xfalib.locale.Strings` para el  `<locale>` tal como se define en  `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.** texto que contiene lo siguiente:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Agregar una biblioteca de cliente de formulario adaptable para una configuración regional {#add-adaptive-form-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>`, con categoría como `guides.I18N.<locale>` y dependencias como `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` y `guide.common`. &quot;

Agregue los siguientes archivos a la biblioteca de cliente:

* **i18n.** jsdefining  `guidelib.i18n`, que tiene patrones de &quot;calendarSymbols&quot;,  `datePatterns`,  `timePatterns`,  `dateTimeSymbols`,  `numberPatterns`,  `numberSymbols`,  `currencySymbols`, para  `typefaces` las especificaciones XFA descritas en  `<locale>` Especificación de configuración regional [ ](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). También puede ver cómo se define para otras configuraciones regionales compatibles en `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.** jsdefining  `guidelib.i18n.strings` y  `guidelib.i18n.LogMessages` para el  `<locale>` definido en  `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.** texto que contiene lo siguiente:

```
i18n.js
LogMessages.js
```

### Agregar compatibilidad con la configuración regional para el diccionario {#add-locale-support-for-the-dictionary-br}

Realice este paso solo si el `<locale>` que está agregando no está entre `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Cree un nodo `nt:unstructured` `languages` en `etc`, si no está presente ya.

1. Agregue una propiedad de cadena de varios valores `languages` al nodo, si no está presente ya.
1. Agregue los `<locale>` valores de configuración regional predeterminados `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr` si no están presentes.

1. Agregue `<locale>` a los valores de la propiedad `languages` de `/etc/languages`.

El `<locale>` aparecerá en `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Reinicio del servidor {#restart-the-server}

Reinicie el servidor de AEM para que la configuración regional añadida entre en vigor.

## Bibliotecas de muestra para agregar compatibilidad con el español {#sample-libraries-for-adding-support-for-spanish}

Bibliotecas de cliente de muestra para agregar compatibilidad con el español

[Obtener archivo](assets/sample.zip)
