---
title: Personalización del marco de trabajo de Adobe Analytics
seo-title: Personalización del marco de trabajo de Adobe Analytics
description: Personalización del marco de trabajo de Adobe Analytics
seo-description: nulo
uuid: 444a29c2-3b4e-4d21-adc0-5f317ece2b77
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 11c0aac6-a7f6-4d6b-a080-b04643045a64
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 0%

---


# Personalización de Adobe Analytics Framework{#customizing-the-adobe-analytics-framework}

El marco de Adobe Analytics determina la información que se rastrea con Adobe Analytics. Para personalizar el marco predeterminado, utilice javascript para agregar seguimiento personalizado, integrar complementos de Adobe Analytics y cambiar la configuración general dentro del marco utilizado para el seguimiento.

## Acerca del javascript generado para módulos {#about-the-generated-javascript-for-frameworks}

Cuando una página está asociada a un marco de Adobe Analytics y la página incluye [referencias al módulo de Analytics](/help/sites-administering/adobeanalytics.md), se genera automáticamente un archivo analytics.sitecatalyst.js para la página.

El javascript de la página crea un objeto `s_gi`(definido por la biblioteca Adobe Analytics s_code.js) y asigna valores a sus propiedades. El nombre de la instancia del objeto es `s`. Los ejemplos de código que se presentan en esta sección hacen varias referencias a esta variable `s`.

El siguiente código de ejemplo es similar al código de un archivo analytics.sitecatalyst.js:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;
        
s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";

/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

Al utilizar código personalizado de javascript para personalizar el marco, se modifica el contenido de este archivo.

## Configuración de las propiedades de Adobe Analytics {#configuring-adobe-analytics-properties}

Hay varias variables predefinidas dentro de Adobe Analytics que se pueden configurar en un marco**. **Las variables **charset**, **cookieLifetime**, **currencyCode** y **trackInlineStats** se incluyen de forma predeterminada en la lista **Configuración general de análisis**.

![aa-22](assets/aa-22.png)

Puede agregar nombres y valores de variables a la lista. Estas variables predefinidas y cualquier variable que agregue se utilizan para configurar las propiedades del objeto `s` en el archivo analytics.sitecatalyst.js . El siguiente ejemplo muestra cómo se representa la propiedad `prop10` añadida del valor `CONSTANT` en el código javascript:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.prop10= 'CONSTANT';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;
        
s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";
```

Utilice el siguiente procedimiento para añadir variables a la lista:

1. En la página del marco de Adobe Analytics, expanda el área **Configuración general de análisis**.
1. Debajo de la lista de variables, haga clic en Agregar elemento para agregar una variable nueva a la lista.
1. En la celda de la izquierda, introduzca un nombre para la variable, por ejemplo `prop10`.

1. En la columna derecha, introduzca un valor para la variable, por ejemplo `CONSTANT`.

1. Para eliminar una variable, haga clic en el botón (-) situado junto a la variable .

>[!NOTE]
>
>Al introducir variables y valores, asegúrese de que tengan el formato y la escritura correctos, o que las **llamadas no se envíen** con el par valor/variable correcto. Los valores y las variables mal escritas pueden incluso impedir que se realicen llamadas.
>
>Póngase en contacto con su representante de Adobe Analytics para asegurarse de que estas variables estén correctamente configuradas.

>[!CAUTION]
>
>Algunas de las variables de esta lista son **obligatorias** para que las llamadas de Adobe Analytics funcionen correctamente (p. ej. **currencyCode**, **charSet**)
>
>Por lo tanto, incluso si se eliminan de la propia infraestructura, se adjuntarán con un valor predeterminado cuando se realice la llamada de Adobe Analytics.

### Adición de javascript personalizado a un Adobe Analytics Framework {#adding-custom-javascript-to-an-adobe-analytics-framework}

El cuadro de javascript libre del área **Configuración general de análisis** le permite agregar código personalizado a un marco de Adobe Analytics.

![aa-21](assets/aa-21.png)

El código que agregue se añadirá al archivo analytics.sitecatalyst.js . Por lo tanto, puede acceder a la variable `s` , que es una instancia del objeto javascript `s_gi` definido en `s_code.js`. Por ejemplo, añadir el siguiente código equivale a añadir una variable denominada `prop10` del valor `CONSTANT`, que es el ejemplo de la sección anterior:

`s.prop10= 'CONSTANT';`

El código del archivo [analytics.sitecatalyst.js](/help/sites-developing/extending-analytics-components.md) (que incluye el contenido del archivo `s-code.js` de Adobe Analytics) contiene el siguiente código:

`if (s.usePlugins) s.doPlugins(s)`

El siguiente procedimiento muestra cómo utilizar el cuadro de javascript para personalizar el seguimiento de Adobe Analytics. Si su javascript necesita utilizar complementos de Adobe Analytics, [inclúyalos](/help/sites-administering/adobeanalytics.md) en AEM.

1. Agregue el siguiente código javascript al cuadro para que se ejecute `s.doPlugins`:

   ```
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom code here
   }
   s.doPlugins=s_doPlugins;
   ```

   >[!CAUTION]
   >
   >Este código es necesario si desea enviar variables en una llamada de Adobe Analytics que se hayan personalizado de alguna manera que no se puedan realizar a través de la interfaz básica de arrastrar y soltar o a través de javascript en línea en la vista de Adobe Analytics.
   >
   >Si las variables personalizadas están fuera de la función s_doPlugins , se enviarán como *undefined *en la llamada de Adobe Analytics

1. Agregue el código javascript en la función **s_doPlugins**.

En el siguiente ejemplo se concatenan los datos capturados en una página en orden jerárquico, utilizando un separador común de &quot;|&quot;.

Un marco de Adobe Analytics tiene las siguientes configuraciones:

* La variable `prop2` Adobe Analytics está asignada a la propiedad `pagedata.sitesection` del sitio.

* La variable `prop3` Adobe Analytics está asignada a la propiedad `pagedata.subsection` del sitio.

* El siguiente código se agrega al cuadro javascript libre:

   ```
   s.usePlugins=true; 
    function s_doPlugins(s) { 
    s.prop1 = s.prop2+'|'+s.prop3; 
    } 
    s.doPlugins=s_doPlugins;
   ```

* Cuando se visita la página web que utiliza la estructura (o, en modo de edición, se vuelve a cargar o previsualiza la página), se realizan las llamadas a Adobe Analytics.

Por ejemplo, en Adobe Analytics se generan los siguientes valores:

![aa-20](assets/aa-20.png)

### Agregar código personalizado global para todos los marcos de Adobe Analytics {#adding-global-custom-code-for-all-adobe-analytics-frameworks}

Proporcione código javascript personalizado que esté integrado en todos los marcos de Adobe Analytics. Cuando el marco de Adobe Analytics de una página no contiene ningún [javascript de forma libre](/help/sites-administering/adobeanalytics.md) personalizado, el javascript que genera el script /libs/cq/analytics/components/sitecatalyst/config.js.jsp se adjunta al archivo [analytics.sitecatalyst.js](/help/sites-administering/adobeanalytics.md) . De forma predeterminada, la secuencia de comandos no tiene ningún efecto porque está comentada. El código también establece `s.usePlugins` en `false`:

```
/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

El código del archivo analytics.sitecatalyst.js (que incluye el contenido del archivo s_code.js de Adobe Analytics) contiene el siguiente código:

if (s.usePlugins) s.doPlugins(s)

Por lo tanto, su javascript debe establecer `s.usePlugins` en `true` para que se ejecute cualquier código de la función `s_doPlugins`. Para personalizar el código, superponga el archivo config.js.jsp con uno que utilice su propio javascript. Si su javascript necesita utilizar complementos de Adobe Analytics, [inclúyalos](/help/sites-administering/adobeanalytics.md) en AEM.

>[!NOTE]
>
>No edite el archivo /libs/cq/analytics/components/sitecatalyst/config.js.jsp. Algunas tareas de actualización o mantenimiento de AEM pueden volver a instalar el archivo original, eliminando los cambios.

1. En el CRXDE Lite, cree la estructura de carpetas /apps/cq/analytics/components:

   1. Haga clic con el botón derecho en la carpeta /apps y haga clic en Crear > Crear carpeta.
   1. Especifique `cq` como nombre de la carpeta y haga clic en Aceptar.
   1. Del mismo modo, cree las carpetas `analytics` y `components` .

1. Haga clic con el botón derecho en la carpeta `components` que acaba de crear y haga clic en Crear > Crear componente. Especifique los siguientes valores de propiedad:

   * Etiqueta: `sitecatalyst`
   * Título: `sitecatalyst`
   * Super Type: `/libs/cq/analytics/components/sitecatalyst`
   * Agrupar: `hidden`

1. Haga clic en Siguiente varias veces hasta que el botón Aceptar esté habilitado y, a continuación, haga clic en Aceptar.

   El componente sitecatalyst contiene el archivo sitecatalyst.jsp creado automáticamente.

1. Haga clic con el botón derecho en el archivo sitecatalyst.jsp y, a continuación, haga clic en Eliminar.

1. Haga clic con el botón derecho en el componente de sitecatalyst y, a continuación, haga clic en Crear > Crear archivo. Especifique el nombre `config.js.jsp` y haga clic en Aceptar.

   El archivo config.js.jsp se abre automáticamente para su edición.

1. Agregue el siguiente texto al archivo y haga clic en Guardar todo:

   ```java
   <%@page session="true"%>
   /* Plugin Config */
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom plugin code here
   }
   s.doPlugins=s_doPlugins;
   ```

   El código javascript que genera el script /apps/cq/analytics/components/sitecatalyst/config.js.jsp ahora se inserta en el archivo analytics.sitecatalyst.js para todas las páginas que utilizan un marco de Adobe Analytics.

1. Agregue el código javascript que desee ejecutar en la función `s_doPlugins` y haga clic en Guardar todo.

>[!CAUTION]
>
>Si hay texto presente en el javascript de forma libre del marco de una página (incluso solo espacio en blanco), se ignorará config.js.jsp.

### Uso de complementos de Adobe Analytics en AEM {#using-adobe-analytics-plugins-in-aem}

Obtenga el código de javascript para los complementos de Adobe Analytics e inclúyalos en la infraestructura de Adobe Analytics en AEM. Agregue el código a una carpeta de la biblioteca de cliente de la categoría `sitecatalyst.plugins` para que esté disponible para el código javascript personalizado.

Por ejemplo, si integra el complemento `getQueryParams`, puede llamar al complemento desde la función `s_doPlugins` de su javascript personalizado. El siguiente código de ejemplo envía la cadena de consulta en **&quot;pid&quot;** desde la dirección URL del referente como **eVar1**, cuando se activa una llamada de Adobe Analytics.

```
s.usePlugins=true;
function s_doPlugins(s) {
   // take the query string from the referrer
   s.eVar1=s.getQueryParam('pid','',document.referrer); 
}
s.doPlugins=s_doPlugins;
```

AEM instala los siguientes complementos de Adobe Analytics, de modo que estén disponibles de forma predeterminada:

* getQueryParam()
* getPreviousValue()
* split()

La carpeta de biblioteca de cliente /libs/cq/analytics/clientlibs/sitecatalyst/plugins incluye estos complementos en la categoría sitecatalyst.plugins .

>[!NOTE]
>
>Cree una nueva carpeta de biblioteca de cliente para sus complementos. No agregue complementos a la carpeta `/libs/cq/analytics/clientlibs/sitecatalyst/plugins`. Esta práctica garantiza que su contribución a la categoría `sitecatalyst.plugins` no se sobrescriba durante AEM reinstalaciones o tareas de actualización.

Utilice el siguiente procedimiento para crear la carpeta de la biblioteca del cliente para sus complementos. Solo debe realizar este procedimiento una vez. Para agregar un complemento a la carpeta de la biblioteca del cliente, utilice el procedimiento siguiente.

1. En un explorador web, abra CRXDE Lite. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))

1. Haga clic con el botón derecho en la carpeta /apps/my-app/clientlibs y haga clic en Crear > Crear nodo. Introduzca los siguientes valores de propiedad y haga clic en Aceptar:

   * Nombre: Un nombre para la carpeta de la biblioteca del cliente, como my-plugins

   * Tipo: cq:ClientLibraryFolder

1. Seleccione la carpeta de la biblioteca de cliente que acaba de crear y utilice la barra de propiedades inferior derecha para añadir la siguiente propiedad:

   * Nombre: categories
   * Tipo: Cadena
   * Valor: sitecatalyst.plugins
   * Varios: seleccionado

   Haga clic en Aceptar en la ventana Editar para confirmar el valor de la propiedad.

1. Haga clic con el botón derecho en la carpeta de biblioteca de cliente que acaba de crear y haga clic en Crear > Crear archivo. Para el nombre de archivo, escriba js.txt y, a continuación, haga clic en Aceptar.

1. Haga clic en Guardar todo.

Utilice el siguiente procedimiento para obtener el código del complemento, almacenar el código en el repositorio de AEM y agregar el código a la carpeta de la biblioteca del cliente.

1. Inicie sesión en [sc.omniture.com](https://sc.omniture.com) con su cuenta de Adobe Analytics.
1. En la página de aterrizaje, vaya a Ayuda > Página inicial de Ayuda.
1. En la tabla de contenido de la izquierda, haga clic en Complementos de implementación.
1. Haga clic en el vínculo al complemento que desee agregar y, cuando se abra la página, busque el código fuente de javascript para el complemento y, a continuación, seleccione el código y cópielo.

1. Haga clic con el botón derecho en la carpeta de la biblioteca del cliente y, a continuación, haga clic en Crear > Crear archivo. Para el nombre del archivo, escriba el nombre del complemento que está integrando seguido de .js y, a continuación, haga clic en Aceptar. Por ejemplo, si está integrando el complemento getQueryParam , asigne un nombre al archivo getQueryParam.js.

   Cuando crea el archivo, se abre para su edición.

1. Pegue el código javascript del complemento en el archivo, haga clic en Guardar todo y cierre el archivo.

1. Abra el archivo js.txt desde la carpeta de la biblioteca del cliente.

1. En una nueva línea, añada el nombre del archivo que contiene el complemento, por ejemplo getQueryParam.js. A continuación, haga clic en Guardar todo y cierre el archivo.

>[!NOTE]
>
>Al utilizar complementos, asegúrese de integrar también cualquier complemento de soporte; de lo contrario, el complemento javascript no reconocerá las llamadas que realiza a las funciones del complemento de soporte. Por ejemplo, el complemento getPreviousValue() requiere que el complemento split() funcione correctamente.
>  
>El nombre del complemento de soporte también debe agregarse a **js.txt**.
