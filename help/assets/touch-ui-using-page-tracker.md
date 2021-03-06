---
title: Uso del rastreador de páginas e Incrustar código en páginas web
description: Aprenda a incluir el rastreador de páginas e incrustar códigos JavaScript en el código del sitio web para permitir que Adobe Analytics capture los datos de uso alrededor de los recursos.
contentOwner: AG
feature: Asset Reports
role: Architect,Admin
exl-id: b0154c9c-a671-43fb-8733-274a35307a34
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Uso del rastreador de páginas e Incrustar código en páginas web {#using-page-tracker-and-embed-code-in-web-pages}

El rastreador de páginas es un fragmento de código JavaScript que se incluye en el código de los sitios web de terceros para permitir que Adobe Analytics capture los datos de uso relacionados con los activos de Adobe Experience Manager en estos sitios web.

Para capturar eventos, como clics, etc. específicos de los recursos, también debe incluir el código de incrustación en el código de sitios web de terceros.

El siguiente código de ejemplo muestra el aspecto que tiene una página web que contiene tanto el código del rastreador de páginas como el código incrustado:

```
<!DOCTYPE html>
<html>
    <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in milliseconds
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","xxxx","xxx","list1","eVar3","event8","event7");
            </script>

    </head>

    <body>

                                <img
            src="https://10.41.52.147:4502/xxxx/content/dam/test/abc.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
                <img
                    src="http://localhost/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
</html>
```

## Adición de código de Rastreador de páginas {#adding-page-tracker-code}

El código del rastreador de páginas se agrega dentro de la sección del encabezado del código del sitio web. El siguiente fragmento de código muestra el código Rastreador de páginas incluido en una página web de muestra:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>
 </head>
```

## Adición de código incrustado {#adding-embed-code}

El código incrustado se agrega al cuerpo del código del sitio web. El siguiente fragmento de código muestra el código incrustado incluido en una página web de ejemplo:

```xml
<body>

      <img
            src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
           <img
                    src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
```
