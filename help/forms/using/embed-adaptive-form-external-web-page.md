---
title: Incrustar formulario adaptable en una página web externa
seo-title: Embed adaptive form in external web page
description: Aprenda a incrustar un formulario adaptable en una página web externa
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
exl-id: 84a46197-9933-4b94-a8e3-e7baf9c644b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 77%

---

# Incrustar formulario adaptable en una página web externa{#embed-adaptive-form-in-external-web-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Aprenda a incrustar un formulario adaptable en una página web externa

Puede [Incrustar formulario adaptable en AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) o una página web alojada fuera de AEM. El formulario adaptable incrustado es completamente funcional, y los usuarios pueden rellenarlo y enviarlo sin abandonar la página. Ayuda al usuario a permanecer en el contexto de otros elementos de la página web e interactuar simultáneamente con el formulario.

## Requisitos previos {#prerequisites}

Realice los siguientes pasos antes de incrustar un formulario adaptable en un sitio web externo:

* Publique el formulario adaptable en la instancia de AEM Publish.
* Cree o identifique una página web en su sitio web para alojar el formulario adaptable. Asegúrese de que la página web pueda [leer archivos jQuery de una CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) o de que tenga una copia local de jQuery incrustada. jQuery es necesario para procesar un formulario adaptable.
* Cuando el servidor de AEM y la página web están en dominios diferentes, realice los pasos que se enumeran en la sección, [permitir que AEM Forms ofrezca formularios adaptables a un sitio de dominios cruzados](#cross-domain-sites).
* [Configuración del proxy inverso](#reveseproxy) para habilitar la comunicación entre la página externa y el servidor de AEM Forms.

## Incrustar formulario adaptable {#embed-adaptive-form}

Puede incrustar un formulario adaptable si inserta algunas líneas de JavaScript en la página web. La API del código envía una solicitud HTTP al servidor de AEM para obtener recursos de formularios adaptables e inserta el formulario adaptable en el contenedor de formulario especificado. Este es un ejemplo de código para incrustar un formulario adaptable en una página externa. No utilice el código como está en un entorno de producción. Personalice el código para que se adapte a su sitio web como usar un iFrame para sitios web que usen su propia versión de jQuery. El uso de iFrame ayuda a evitar conflictos en las versiones de jQuery:


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

   * Cambie el valor de la variable `options.path` con la ruta de la URL de publicación del formulario adaptable. Si el servidor de AEM se ejecuta en una ruta de contexto, asegúrese de que la dirección URL incluya la ruta de contexto. Por ejemplo, el código anterior y el código adaptable de residen en el mismo servidor de aem forms, por lo que el ejemplo utiliza la ruta de contexto del formulario adaptable /content/forms/af/locbasic.html.
   * Reemplace `options.dataRef` por atributos para pasar con la dirección URL. Puede utilizar la variable dataref para [rellenar previamente un formulario adaptable](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Reemplace `options.themePath` por la ruta a una temática distinta a la configurada en el formulario adaptable. También puede especificar la ruta de la temática mediante el atributo de solicitud.
   * `CSS_Selector` es el selector CSS del contenedor de formularios en el que está incrustado el formulario adaptable. Por ejemplo, la clase css .customafsection es el selector de CSS del ejemplo anterior.

El formulario adaptable está incrustado en la página web. Observe lo siguiente en el formulario adaptable integrado:

* El encabezado y el pie de página del formulario adaptable original no se incluyen en el formulario incrustado.
* Los borradores y los formularios enviados están disponibles en la pestaña Borradores y envíos del portal de formularios.
* La acción de envío configurada en el formulario adaptable original se mantendrá en el formulario incrustado.
* Las reglas de los formularios adaptables se conservarán y funcionarán perfectamente en el formulario incrustado.
* La segmentación de experiencias y las pruebas A/B configuradas en el formulario adaptable original no funcionarán en el formulario incrustado.
* Si Adobe Analytics está configurado en el formulario original, los datos de análisis se capturarán en el servidor de Adobe Analytics. Sin embargo, no estará disponible en el informe de análisis de Forms.

## Configuración del proxy inverso  {#reveseproxy}

La página web externa que incrusta el formulario adaptable envía solicitudes al servidor de AEM, que normalmente se encuentra detrás del firewall en una red privada. Para garantizar que las solicitudes se dirijan de forma segura al servidor de AEM, se recomienda configurar un servidor proxy inverso.

Veamos un ejemplo de cómo puede configurar un servidor proxy inverso Apache 2.4 sin Dispatcher. En este ejemplo, alojará el servidor de AEM con la ruta de contexto `/forms` y el mapa `/forms` para el proxy inverso. Garantiza que cualquier solicitud de `/forms` en el servidor de Apache se dirijan a la instancia de AEM. Esta topología ayuda a reducir el número de reglas en la capa de Dispatcher, ya que todas las solicitudes con el prefijo `/forms` se envían al servidor de AEM.

1. Abra el archivo de configuración `httpd.conf` y quite el comentario de las siguientes líneas de código. Como alternativa, puede agregar estas líneas de código en el archivo.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configure las reglas de proxy al agregar las siguientes líneas de código en el archivo de configuración `httpd-proxy.conf`.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Reemplace `[AEM_Instance]` por la URL de publicación del servidor de AEM en las reglas.

Si no monta el servidor AEM en una ruta de contexto, las reglas de proxy en la capa de Apache serán las siguientes:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Si configura cualquier otra topología, asegúrese de agregar las direcciones URL de envío, de relleno previo y de otro tipo a la lista de permitidos de Dispatcher.

## Prácticas recomendadas {#best-practices}

Al incrustar un formulario adaptable en una página web, tenga en cuenta las siguientes prácticas recomendadas:

* Asegúrese de que las reglas de estilo definidas en la página web de CSS no entren en conflicto con el objeto de formulario de CSS. Para evitar conflictos, puede reutilizar la página web de CSS en la temática del formulario adaptable mediante la biblioteca de cliente de AEM. Para obtener información sobre el uso de la biblioteca de cliente en temáticas de formularios adaptables, consulte [Temáticas en AEM Forms](/help/forms/using/themes.md).
* Haga que el contenedor de formularios de la página web utilice la anchura de toda la ventana. Garantiza que las reglas CSS configuradas para dispositivos móviles funcionen sin ningún cambio. Si el contenedor de formularios no tiene la anchura de toda la ventana, deberá escribir un CSS personalizado para que el formulario se adapte a diferentes dispositivos móviles.
* Uso  [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para obtener la representación XML o JSON de los datos de formulario en el cliente.
* Uso [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API para descargar el formulario adaptable del DOM de HTML.
* Configure el encabezado access-control-origin al enviar la respuesta desde el servidor de AEM.

## Permita que AEM Forms ofrezca formularios adaptables a un sitio de dominios cruzados  {#cross-domain-sites}

1. En la instancia de publicación de AEM, vaya al Administrador de configuración de la consola web de AEM en `http://[server]:[port]/system/console/configMgr`.
1. Busque y abra el **Referente de Apache Sling** Configuración del filtro.
1. En el **Hosts permitidos** especifique el dominio en el que reside la página web. Permita que el host realice peticiones POST al servidor de AEM. También puede utilizar una expresión regular para especificar una serie de dominios de aplicación externos.
