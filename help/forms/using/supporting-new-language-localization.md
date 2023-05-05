---
title: Compatibilidad con configuraciones regionales nuevas para la localización de formularios adaptables
seo-title: Supporting new locales for adaptive forms localization
description: AEM Forms le permite agregar configuraciones regionales nuevas para localizar formularios adaptables. Las configuraciones regionales compatibles de forma predeterminada son Inglés, Francés, Alemán y Japonés.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. The supported locales by default are English, French, German, and Japanese.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Adaptive Forms
role: Admin
exl-id: 9f0e7284-ac11-406d-8d8c-7682f1d66fff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 80%

---

# Compatibilidad con configuraciones regionales nuevas para la localización de formularios adaptables {#supporting-new-locales-for-adaptive-forms-localization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de los diccionarios de configuración regional {#about-locale-dictionaries}

La localización de formularios adaptables se basa en dos tipos de diccionarios de configuración regional:

**El diccionario específico del formulario**: contiene cadenas utilizadas en formularios adaptables. Por ejemplo, etiquetas, nombres de campo, mensajes de error, descripciones de ayuda, etc. Se administra como un conjunto de archivos XLIFF para cada configuración regional y puede acceder a él en https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Los diccionarios globales**: hay dos diccionarios globales, administrados como objetos JSON en la biblioteca de cliente de AEM. Estos diccionarios contienen mensajes de error predeterminados, nombres de mes, símbolos de moneda, patrones de fecha y hora, etc. Puede encontrar estos diccionarios en CRXDe Lite en /libs/fd/xfaforms/clientlibs/I18N. Estas ubicaciones contienen carpetas independientes para cada configuración regional. Dado que los diccionarios globales no suelen actualizarse con frecuencia, utilizar archivos JavaScript independientes para cada configuración regional permite a los exploradores almacenarlos en caché y reducir el uso del ancho de banda de red al acceder a diferentes formularios adaptables en el mismo servidor.

### Funcionamiento de la localización del formulario adaptable {#how-localization-of-adaptive-form-works}

Cuando se procesa un formulario adaptable, identifica la configuración regional solicitada mirando los siguientes parámetros en el orden especificado:

* Parámetro de solicitud `afAcceptLang`

   Para anular la configuración regional del explorador de los usuarios, puede pasar la variable `afAcceptLang` para forzar la configuración regional. Por ejemplo, la siguiente URL obligará a representar el formulario en la configuración regional Japonés:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* La configuración regional del explorador establecida para el usuario, que se especifica en la solicitud utilizando el encabezado `Accept-Language`.

* La configuración de idioma del usuario especificada en AEM.

Una vez identificada la configuración regional, el formulario adaptable selecciona el diccionario específico del formulario. Si no se encuentra el diccionario específico del formulario para la configuración regional solicitada, se utiliza el diccionario inglés (en) .

Si no existe una biblioteca de cliente para la configuración regional solicitada, se busca una biblioteca de cliente para el código de idioma presente en la configuración regional. Por ejemplo, si la configuración regional solicitada es `en_ZA` (Inglés sudafricano) y la biblioteca de cliente de `en_ZA` no existe, el formulario adaptable utilizará la biblioteca de cliente de `en` (Inglés), si existe. Sin embargo, si no existe ninguna biblioteca, el formulario adaptable utilizará el diccionario de la configuración regional `en`.

## Agregar compatibilidad con la localización para configuraciones regionales no admitidas {#add-localization-support-for-non-supported-locales}

Actualmente, AEM Forms admite la localización de contenido de formularios adaptables en las configuraciones regionales de inglés (en), español (es), francés (fr), italiano (it), alemán (de), japonés (ja), portugués-brasileño (pt-BR, chino- (zh-CN), chino-taiwanés (zh-TW) y coreano (ko-KR).

Para agregar compatibilidad con una nueva configuración regional en el tiempo de ejecución de un formulario adaptable, haga lo siguiente:

1. [Añada una configuración regional al servicio GuideLocalizationService.](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Agregar una biblioteca de cliente XFA para una configuración regional.](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Agregue la biblioteca de cliente del formulario adaptable para una configuración regional.](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Agregar la compatibilidad con la configuración regional del diccionario.](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Reiniciar el servidor](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Añadir una configuración regional al servicio de localización de guías {#add-a-locale-to-the-guide-localization-service-br}

1. Vaya a `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en para editar el componente **Servicio de localización de guías**.
1. Agregue la configuración regional que desee añadir a la lista de configuraciones regionales admitidas.

![Servicio de localización de guías](assets/configservice.png)

### Agregar una biblioteca de cliente XFA para una configuración regional. {#add-xfa-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>` con la categoría `xfaforms.I18N.<locale>` y agregue los siguientes archivos a la biblioteca de cliente:

* **I18N.js** definiendo `xfalib.locale.Strings` para `<locale>`, tal como se define en `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt**, que contiene lo siguiente:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Agregue la biblioteca de cliente del formulario adaptable para una configuración regional. {#add-adaptive-form-client-library-for-a-locale-br}

Cree un nodo de tipo `cq:ClientLibraryFolder` en `etc/<folderHierarchy>` con la categoría `guides.I18N.<locale>` y las dependencias `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` y `guide.common`.

Agregue los siguientes archivos a la biblioteca de cliente:

* **i18n.js**, definiendo `guidelib.i18n` con los patrones de “calendarSymbols” `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols` y `typefaces` para `<locale>` según las especificaciones XFA descritas en [Especificación de la configuración regional](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). También puede ver cómo se define para otras configuraciones regionales compatibles en `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.js**, definiendo `guidelib.i18n.strings` y `guidelib.i18n.LogMessages` para `<locale>` tal como se define en `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.txt**, que contiene lo siguiente:

```
i18n.js
LogMessages.js
```

### Agregar la compatibilidad con la configuración regional del diccionario. {#add-locale-support-for-the-dictionary-br}

Realice este paso solo si la configuración regional `<locale>` que está agregando que no está entre `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` y `ko-kr`.

1. Cree un nodo `languages` `nt:unstructured` en `etc`, si no está presente.

1. Agregue una propiedad de cadena de varios valores `languages` al nodo, si no está presente ya.
1. Agregue los valores de configuración regional predeterminados `<locale>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` y `ko-kr`, si no están presentes.

1. Agregue `<locale>` a los valores de la propiedad `languages` de `/etc/languages`.

`<locale>` aparecerá en `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Reiniciar el servidor {#restart-the-server}

Reinicie el servidor de AEM para aplicar la configuración regional añadida.

## Bibliotecas de ejemplo para agregar compatibilidad con Español {#sample-libraries-for-adding-support-for-spanish}

Bibliotecas de cliente de ejemplo para agregar compatibilidad con Español

[Obtener archivo](assets/sample.zip)
