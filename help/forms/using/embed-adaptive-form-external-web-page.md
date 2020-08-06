---
title: Incrustar formulario adaptable en una página web externa
seo-title: Incrustar formulario adaptable en una página web externa
description: Aprenda a incrustar un formulario adaptable en una página web externa
seo-description: Aprenda a incrustar un formulario adaptable en una página web HTML externa
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---


# Incrustar formulario adaptable en una página web externa{#embed-adaptive-form-in-external-web-page}

Aprenda a incrustar un formulario adaptable en una página web externa

Puede [incrustar un formulario adaptable en una página de AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) o en una página web alojada fuera de AEM. El formulario adaptable incrustado es totalmente funcional y los usuarios pueden rellenar y enviar el formulario sin salir de la página. Ayuda al usuario a permanecer en el contexto de otros elementos de la página web e interactuar simultáneamente con el formulario.

## Requisitos previos {#prerequisites}

Realice los siguientes pasos antes de incrustar un formulario adaptable en un sitio web externo:

* Publique el formulario adaptable en la instancia de AEM Publish.
* Cree o identifique una página web en el sitio web para alojar el formulario adaptable. Asegúrese de que la página web pueda [leer archivos jQuery desde una CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) o tenga una copia local de jQuery incorporada. jQuery es necesario para procesar un formulario adaptable.
* Cuando AEM servidor y la página web se encuentren en distintos dominios, lleve a cabo los pasos enumerados en la sección , [permita que AEM Forms ofrezca formularios adaptables a un sitio](#cross-domain-sites)de varios dominios.
* [Configure el proxy](#reveseproxy) inverso para habilitar la comunicación entre la página externa y el servidor de AEM Forms.

## Incrustar formulario adaptable {#embed-adaptive-form}

Puede incrustar un formulario adaptable insertando algunas líneas de JavaScript en la página web. La API del código envía una solicitud HTTP al servidor de AEM para recursos de formulario adaptables e inserta el formulario adaptable en el contenedor de formulario especificado. Este es un código de ejemplo para incrustar un formulario adaptable en una página externa. No utilice el código como está en un entorno de producción. Personalice el código para que se adapte a su sitio web, como usar un iFrame para sitios web que utilizan su propia versión de jQuery. El uso de iFrame ayuda a evitar conflictos en las versiones de jQuery:


1. Incruste el siguiente código en una página web de su sitio web:

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>¡Este es el título de la página web!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>Esta sección se sustituye por el formulario adaptable.</p>


    &lt;script>
    var options = {path:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;&quot;, themepath:&quot;&quot;, CSS_Selector:&quot;.customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
    // options.path hace referencia a la URL de publicación del formulario adaptable
    // Por Ejemplo: http:myserver:4503/content/forms/af/ABC, donde ABC es el formulario
    adaptable/ Nota: Si AEM servidor se está ejecutando en una ruta de contexto, la dirección URL del formulario adaptable debe contener la ruta de
    ruta de acceso del contexto = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url : path ,
    type : &quot;GET&quot;,
    datos: {
    // Configure el wcmmode para que sea
    disabledwcmmode : &quot;disabled&quot;
    // Configure la referencia de datos, si existe
    // &quot;dataRef&quot;: options.dataRef
    // Especifique un tema diferente para el objeto
    de formulario// &quot;topicOverride&quot;: options.themepath
    },
    async: false,
    success: function (data) {
    // Si jquery está cargada, establezca el HTML interno del contenedor
    // Si jquery no está cargada, utilice las API proporcionadas por documento para establecer el HTML interno pero estas API no evaluarían la etiqueta de script en HTML según la especificación
    HTML5// Por ejemplo: documento.getElementById().
    innerHTMLif(window.$ &amp;&amp; options.CSS_Selector){
    // La API HTML de jquery extrae las etiquetas, actualiza el DOM y evalúa el código incrustado en la etiqueta de script.
    $(options.CSS_Selector).html(data);
    }
    },
    error: function (data) {
    // cualquier controlador
    de error}
    });
    } else {
    if (typeof(console) !== &quot;undefined&quot;) {
    console.log(&quot;Ruta del formulario adaptable no especificada para loadAdaptiveForm&quot;);
    }
    }
    }(options);
    
    &lt;/script>
</body>
</html>
   ```

1. En el código incrustado:

   * Cambie el valor de la `options.path` variable por la ruta de la URL de publicación del formulario adaptable. Si el servidor de AEM se está ejecutando en una ruta de contexto, asegúrese de que la dirección URL incluye la ruta de contexto. Por ejemplo, el código anterior y el código adaptable de residen en el mismo servidor de formularios aem, de modo que el ejemplo utiliza la ruta de contexto del formulario adaptable /content/forms/af/locbasic.html.
   * Reemplazar `options.dataRef` por atributos para pasar por la dirección URL. Puede utilizar la variable dataref para [rellenar previamente un formulario](/help/forms/using/prepopulate-adaptive-form-fields.md)adaptable.
   * Reemplazar `options.themePath` por la ruta de un tema distinto del configurado en el formulario adaptable. También puede especificar la ruta del tema mediante el atributo de solicitud.
   * `CSS_Selector` es el selector de CSS del contenedor de formulario en el que se incrusta el formulario adaptable. Por ejemplo, la clase css .customafsection es el selector de CSS del ejemplo anterior.

El formulario adaptable se incrusta en la página web. Observe lo siguiente en el formulario adaptable incrustado:

* El encabezado y el pie de página del formulario adaptable original no se incluyen en el formulario incrustado.
* Los borradores y los formularios enviados están disponibles en la ficha Borradores y envíos del portal de Forms.
* La acción de envío configurada en el formulario adaptable original se conserva en el formulario incrustado.
* Las reglas de formulario adaptables se conservan y funcionan completamente en el formulario incrustado.
* La segmentación de experiencias y las pruebas A/B configuradas en el formulario adaptable original no funcionan en el formulario incrustado.
* Si Adobe Analytics está configurado en el formulario original, los datos de análisis se capturan en el servidor de Adobe Analytics. Sin embargo, no está disponible en el informe de análisis de Forms.

## Configurar proxy inverso  {#reveseproxy}

La página web externa que incrusta el formulario adaptable envía solicitudes al servidor de AEM, que normalmente se encuentra detrás del servidor de seguridad en una red privada. Para asegurarse de que las solicitudes se dirigen de forma segura al servidor AEM, se recomienda configurar un servidor proxy inverso.

Veamos un ejemplo de cómo configurar un servidor proxy inverso Apache 2.4 sin despachante. En este ejemplo, alojará el servidor de AEM con ruta de `/forms` contexto y asignación `/forms` para el proxy inverso. Garantiza que cualquier solicitud de `/forms` en el servidor Apache se dirija a la instancia de AEM. Esta topología ayuda a reducir el número de reglas en la capa de distribuidor, ya que todas las solicitudes tienen el prefijo `/forms` route al servidor de AEM.

1. Abra el archivo de configuración y quite el comentario de las siguientes líneas de código. `httpd.conf` Como alternativa, puede agregar estas líneas de código en el archivo.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configure las reglas de proxy agregando las siguientes líneas de código en el archivo de configuración `httpd-proxy.conf` .

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Reemplazar `[AEM_Instance`] con la URL de publicación del servidor de AEM en las reglas.

Si no monta el servidor de AEM en una ruta de contexto, las reglas de proxy en la capa Apache serán las siguientes:

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
>Si configura cualquier otra topología, asegúrese de agregar las direcciones URL de envío, rellenado previo y otras a la lista de permitidos en la capa del despachante.

## Best practices {#best-practices}

Al incrustar un formulario adaptable en una página web, tenga en cuenta las siguientes prácticas recomendadas:

* Asegúrese de que las reglas de estilo definidas en la CSS de la página web no entran en conflicto con la CSS del objeto de formulario. Para evitar conflictos, puede reutilizar la CSS de la página web en el tema del formulario adaptable mediante AEM biblioteca de cliente. Para obtener información sobre el uso de la biblioteca de cliente en temáticas de formularios adaptables, consulte [Temáticas en AEM Forms](/help/forms/using/themes.md).
* Haga que el contenedor de formulario de la página web utilice el ancho completo de la ventana. Garantiza que las reglas CSS configuradas para dispositivos móviles funcionen sin ningún cambio. Si el contenedor de formulario no tiene el ancho completo de la ventana, debe escribir CSS personalizada para que el formulario se adapte a distintos dispositivos móviles.
* Utilice la API [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para obtener la representación XML o JSON de los datos de formulario en el cliente.
* Utilice la API [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para descargar el formulario adaptable desde HTML DOM.
* Configure el encabezado access-control-origen al enviar la respuesta desde AEM servidor.

## Permitir que AEM Forms ofrezca formularios adaptables a un sitio de varios dominios  {#cross-domain-sites}

1. En AEM instancia de autor, vaya a AEM Administrador de configuración de la consola web en `http://[server]:[port]/system/console/configMgr`.
1. Busque y abra la configuración del filtro de Remitente del reenvío **** Apache Sling.
1. En el campo Hosts **** permitidos, especifique el dominio en el que se encuentra la página web. Permite que el host realice solicitudes de POST al servidor AEM. También puede utilizar la expresión regular para especificar una serie de dominios de aplicación externos.