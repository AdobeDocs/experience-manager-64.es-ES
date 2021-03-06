---
title: Incrustar formulario adaptable en una página web externa
seo-title: Incrustar formulario adaptable en una página web externa
description: Aprenda a incrustar un formulario adaptable en una página web externa
seo-description: Aprenda a incrustar un formulario adaptable en una página web HTML externa
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 2%

---


# Incrustar formulario adaptable en una página web externa{#embed-adaptive-form-in-external-web-page}

Aprenda a incrustar un formulario adaptable en una página web externa

Puede [Incrustar formulario adaptable en una página de AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) o en una página web alojada fuera de AEM. El formulario adaptable integrado es totalmente funcional y los usuarios pueden rellenar y enviar el formulario sin salir de la página. Ayuda al usuario a permanecer en el contexto de otros elementos de la página web e interactuar simultáneamente con el formulario.

## Requisitos previos {#prerequisites}

Realice los siguientes pasos antes de incrustar un formulario adaptable en un sitio web externo:

* Publique el formulario adaptable en la instancia de AEM Publish.
* Cree o identifique una página web en su sitio web para alojar el formulario adaptable. Asegúrese de que la página web pueda [leer archivos jQuery de una CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) o tenga una copia local de jQuery incorporada. jQuery es necesario para procesar un formulario adaptable.
* Cuando AEM servidor y la página web están en dominios diferentes, realice los pasos que se enumeran en la sección [permitir que AEM Forms proporcione formularios adaptables a un sitio de dominios cruzados](#cross-domain-sites).
* [Configure el ](#reveseproxy) proxy inverso para habilitar la comunicación entre la página externa y el servidor de AEM Forms.

## Incrustar formulario adaptable {#embed-adaptive-form}

Puede incrustar un formulario adaptable insertando algunas líneas de JavaScript en la página web. La API del código envía una solicitud HTTP al servidor de AEM para obtener recursos de formulario adaptables e inserta el formulario adaptable en el contenedor de formulario especificado. Este es un ejemplo de código para incrustar un formulario adaptable en una página externa. No utilice el código como está en un entorno de producción. Personalice el código para que se adapte a su sitio web como usar un iFrame para sitios web que usen su propia versión de jQuery. El uso de iFrame ayuda a evitar conflictos en las versiones de jQuery:


1. Incruste el siguiente código en una página web de su sitio web:

   ```html
   <!doctype html>
   <html>
   <head>
    <title>This is the title of the webpage!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
   </head>
   <body>
   <div class="customafsection"/>
   <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
        // options.path refers to the publish URL of the adaptive form
        // For Example: http:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
        // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path 
        var path = options.path;
        path += "/jcr:content/guideContainer.html";
        $.ajax({
            url  : path ,
            type : "GET",
            data : {
                // Set the wcmmode to be disabled
                wcmmode : "disabled"
                // Set the data reference, if any
               // "dataRef": options.dataRef
                // Specify a different theme for the form object
              //  "themeOverride" : options.themepath
            },
            async: false,
            success: function (data) {
                // If jquery is loaded, set the inner html of the container
                // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                // For example: document.getElementById().innerHTML
                if(window.$ && options.CSS_Selector){
                    // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                    $(options.CSS_Selector).html(data);
                }
            },
            error: function (data) {
                // any error handler
            }
        });
    } else {
        if (typeof(console) !== "undefined") {
            console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
        }
    }
    }(options);
   
    </script>
   </body>
   </html>
   ```

1. En el código incrustado:

   * Cambie el valor de la variable `options.path` con la ruta de la URL de publicación del formulario adaptable. Si el servidor de AEM se está ejecutando en una ruta de contexto, asegúrese de que la dirección URL incluya la ruta de contexto. Por ejemplo, el código anterior y el código adaptable de residen en el mismo servidor de aem forms, por lo que el ejemplo utiliza la ruta de contexto del formulario adaptable /content/forms/af/locbasic.html.
   * Reemplace `options.dataRef` por atributos para pasarlos por la dirección URL. Puede utilizar la variable de fuente de datos para [rellenar previamente un formulario adaptable](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Sustituya `options.themePath` por la ruta a un tema distinto del configurado en el formulario adaptable. También puede especificar la ruta del tema mediante el atributo de solicitud.
   * `CSS_Selector` es el selector CSS del contenedor de formulario en el que está incrustado el formulario adaptable. Por ejemplo, la clase css .customafsection es el selector de CSS del ejemplo anterior.

El formulario adaptable está incrustado en la página web. Observe lo siguiente en el formulario adaptable integrado:

* El encabezado y pie de página del formulario adaptable original no se incluyen en el formulario incrustado.
* Los borradores y los formularios enviados están disponibles en la pestaña Borradores y envíos del portal de Forms.
* La acción de envío configurada en el formulario adaptable original se conserva en el formulario incrustado.
* Las reglas de formulario adaptables se conservan y funcionan completamente en el formulario incrustado.
* La segmentación de experiencias y las pruebas A/B configuradas en el formulario adaptable original no funcionan en el formulario incrustado.
* Si Adobe Analytics está configurado en el formulario original, los datos de análisis se capturan en el servidor de Adobe Analytics. Sin embargo, no está disponible en el informe de análisis de Forms.

## Configuración del proxy inverso {#reveseproxy}

La página web externa que incrusta el formulario adaptable envía solicitudes al servidor de AEM, que normalmente se encuentra detrás del servidor de seguridad en una red privada. Para garantizar que las solicitudes se dirijan de forma segura al servidor AEM, se recomienda configurar un servidor proxy inverso.

Veamos un ejemplo de cómo puede configurar un servidor proxy inverso Apache 2.4 sin Dispatcher. En este ejemplo, alojará el servidor de AEM con `/forms` ruta de contexto y asignará `/forms` para el proxy inverso. Garantiza que cualquier solicitud de `/forms` en el servidor Apache se dirija a la instancia de AEM. Esta topología ayuda a reducir el número de reglas en la capa de Dispatcher, ya que todas las solicitudes con el prefijo `/forms` dirigen al servidor de AEM.

1. Abra el archivo de configuración `httpd.conf` y quite el comentario de las siguientes líneas de código. Como alternativa, puede añadir estas líneas de código en el archivo .

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configure las reglas de proxy agregando las siguientes líneas de código en el archivo de configuración `httpd-proxy.conf`.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Sustituya `[AEM_Instance]` por la URL de publicación del servidor de AEM en las reglas.

Si no monta el servidor AEM en una ruta de contexto, las reglas de proxy en la capa Apache serán las siguientes:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Si configura cualquier otra topología, asegúrese de agregar las direcciones URL de envío, de relleno previo y de otro tipo a la lista de permitidos de Dispatcher.

## Prácticas recomendadas {#best-practices}

Al incrustar un formulario adaptable en una página web, tenga en cuenta las siguientes prácticas recomendadas:

* Asegúrese de que las reglas de estilo definidas en la página web CSS no entren en conflicto con el objeto de formulario CSS. Para evitar conflictos, puede reutilizar la página web CSS en el tema del formulario adaptable mediante AEM biblioteca de cliente. Para obtener información sobre el uso de la biblioteca de cliente en temas de formularios adaptables, consulte [Temas en AEM Forms](/help/forms/using/themes.md).
* Haga que el contenedor de formularios de la página web utilice el ancho de toda la ventana. Garantiza que las reglas CSS configuradas para dispositivos móviles funcionen sin ningún cambio. Si el contenedor de formulario no tiene el ancho de toda la ventana, debe escribir CSS personalizada para que el formulario se adapte a diferentes dispositivos móviles.
* Utilice la API [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para obtener la representación XML o JSON de los datos de formulario en el cliente.
* Utilice la API [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para descargar el formulario adaptable del DOM de HTML.
* Configure el encabezado access-control-origin al enviar la respuesta desde AEM servidor.

## Permitir que AEM Forms ofrezca formularios adaptables a un sitio de dominios múltiples {#cross-domain-sites}

1. En AEM instancia de publicación, vaya a AEM Administrador de configuración de la consola web en `http://[server]:[port]/system/console/configMgr`.
1. Busque y abra la configuración del filtro **Apache Sling Referrer**.
1. En el campo **Hosts permitidos**, especifique el dominio en el que reside la página web. Permite que el host realice solicitudes de POST al servidor AEM. También puede utilizar la expresión regular para especificar una serie de dominios de aplicación externos.