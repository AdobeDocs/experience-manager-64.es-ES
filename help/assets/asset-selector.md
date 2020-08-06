---
title: Selector de recursos
description: Obtenga información sobre cómo utilizar el selector de recursos para buscar, filtrar, examinar y recuperar metadatos de recursos dentro de Recursos Adobe Experience Manager (AEM). También aprenderá a personalizar la interfaz del selector de recursos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---


# Asset Selector {#asset-selector}

>[!NOTE]
>
>El Selector de recursos se denominaba Selector [de recursos](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) en versiones anteriores de AEM.

El selector de recursos permite buscar, filtrar y examinar recursos dentro de Recursos Adobe Experience Manager (AEM). También puede recuperar los metadatos de los recursos seleccionados mediante el selector de recursos. Para personalizar la interfaz del selector de recursos, puede iniciarla con parámetros de solicitud admitidos. Estos parámetros establecen el contexto del selector de recursos para un escenario en particular.

Actualmente, puede pasar los parámetros de solicitud `Asset Type` (*Imagen/Vídeo/Texto*) y `Selection mode` (*Único/Múltiple*) como información contextual para el selector de recursos, que permanece intacto durante toda la selección.

El selector de recursos utiliza el mensaje HTML5 **Window.postMessage** para enviar datos del recurso seleccionado al destinatario.

El selector de recursos se basa en el vocabulario del selector de base de Granite. De forma predeterminada, el selector de recursos funciona en el modo Examinar. Sin embargo, puede aplicar filtros utilizando la experiencia de Omniture para restringir la búsqueda de recursos concretos.

Puede integrar cualquier página web (independientemente de si forma parte del contenedor de CQ) con el selector de recursos (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Parámetros contextuales {#contextual-parameters}

Puede pasar los siguientes parámetros de solicitud en una URL para iniciar el selector de recursos en un contexto concreto:

| Nombre | Valores | Ejemplo | Función |
|---|---|---|---|
| sufijo de recurso (B) | Ruta de carpeta como sufijo de recurso en la dirección URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Para iniciar el selector de recursos con una carpeta concreta seleccionada, por ejemplo con la carpeta `/content/dam/we-retail/en/activities` seleccionada, la URL debe tener el formato: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Si necesita que se seleccione una carpeta determinada al iniciar el selector de recursos, pasarla como sufijo de recurso. |
| modo | único, múltiple | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | En varios modos, puede seleccionar varios recursos simultáneamente mediante el selector de recursos. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) de un recurso (también se admite el comodín) | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation&mimetype=*png`</li></ul> | Utilícelo para filtrar recursos en función de tipos MIME |
| el cuadro de diálogo | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Utilice estos parámetros para abrir el selector de recursos como cuadro de diálogo Granito. Esta opción solo se aplica cuando se inicia el selector de recursos mediante Campo de ruta de granito y se configura como URL de pickerSrc. |
| assettype (S) | imágenes, documentos, multimedia, archivos | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=archives`</li> | Utilice esta opción para filtrar los tipos de recursos en función del valor pasado. |
| raíz | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Utilice esta opción para especificar la carpeta raíz del selector de recursos. En este caso, el selector de recursos permite seleccionar solo recursos secundarios (directos/indirectos) en la carpeta raíz. |

## Uso del selector de recursos {#using-the-asset-selector}

1. Para acceder a la interfaz del selector de recursos, vaya a `https://[AEM_server]:[port]/aem/assetpicker`.
1. Vaya a la carpeta que desee y seleccione uno o varios recursos.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   También puede buscar el recurso deseado desde el cuadro OmniSearch y luego seleccionarlo.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Si busca recursos utilizando el cuadro OmniSearch, puede seleccionar varios filtros en el panel **[!UICONTROL Filtros]** para restringir la búsqueda.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Toque o haga clic en **[!UICONTROL Seleccionar]** en la barra de herramientas.
