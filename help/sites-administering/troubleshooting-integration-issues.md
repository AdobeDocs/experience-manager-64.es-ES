---
title: Resolución de problemas de integración
seo-title: Troubleshooting Integration Issues
description: Obtenga información sobre cómo solucionar problemas de integración.
seo-description: Learn how to troubleshoot integration issues.
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
exl-id: 81b8f8c0-7f9d-4748-af07-c550826c19b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 2%

---

# Resolución de problemas de integración{#troubleshooting-integration-issues}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Sugerencias generales para la resolución de problemas {#general-troubleshooting-tips}

### Asegúrese de que no haya errores de JavaScript {#ensure-there-are-no-javascript-errors}

Compruebe si la consola JavaScript del explorador muestra algún error. Los errores no gestionados podrían impedir que el código siguiente se ejecutara correctamente. En caso de que haya errores, compruebe qué secuencia de comandos está causando el error y en qué área. La ruta a la secuencia de comandos puede proporcionar una indicación de la funcionalidad a la que pertenece la secuencia de comandos.

### Inicio de sesión en el nivel de componente {#logging-on-component-level}

En algunos casos, puede resultar útil agregar instrucciones adicionales en el nivel de componente. Como el componente se representa, puede agregar un marcado temporal para mostrar valores de variables que puedan ayudarle a identificar posibles problemas. Por ejemplo:

```
<%
log.info("myVariable={}", myVariable);
%>
  
<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

Para obtener más información sobre el registro, consulte la [Registro](/help/sites-deploying/configure-logging.md) y [Uso de registros de auditoría y archivos de registro](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) páginas.

## Problemas de integración de Analytics {#analytics-integration-issues}

### El Importador de informes causa un alto uso de CPU/memoria {#the-report-importer-causes-high-cpu-memory-usage}

El Importador de informes causa un alto uso de CPU/memoria o causa `OutOfMemoryError` excepciones.

#### Solución {#solution}

Para solucionar este problema, puede probar lo siguiente:

* Asegúrese de que no haya una gran cantidad de PollingImporters registrados (consulte la sección &quot;El cierre tarda mucho tiempo debido a PollingImporter&quot; a continuación).
* Ejecute Importadores de informes en un momento determinado del día utilizando expresiones CRON para la variable `ManagedPollingImporter` configuraciones en la variable [Consola OSGi](/help/sites-deploying/configuring-osgi.md).

Para obtener más información sobre la creación de servicios de importación de datos personalizados en AEM, lea el siguiente artículo [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

### El cierre lleva mucho tiempo debido a PollingImporter {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analytics se ha diseñado teniendo en cuenta un mecanismo de herencia. Normalmente, para habilitar Analytics en un sitio, agregue una referencia a una configuración de Analytics dentro de las propiedades de página [Cloud Services](/help/sites-developing/extending-cloud-config.md) pestaña . A continuación, la configuración se hereda a todas las subpáginas automáticamente sin necesidad de volver a hacer referencia a ella a menos que una página requiera una configuración diferente. Al agregar una referencia a un sitio, también se crean automáticamente varios nodos (12 para AEM 6.3 y anteriores o 6 para AEM 6.4) del tipo `cq;PollConfig` que crea una instancia de PollingImporters utilizada para importar datos de Analytics en AEM. Como resultado:

* Tener muchas páginas que hagan referencia a Analytics provoca una gran cantidad de PollingImporters.
* Además, copiar y pegar páginas con una referencia a una configuración de Analytics produce una duplicación de sus PollingImporters.

#### Solución {#solution-1}

En primer lugar, analizar la variable [error.log](/help/sites-deploying/configure-logging.md) puede proporcionarle información sobre la cantidad de PollingImporters activos o registrados. Por ejemplo:

```
# Count PollingImporter entries

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

En segundo lugar, asegúrese de que solo las páginas principales (superiores en la jerarquía) tengan una referencia de configuración de Analytics.

Para obtener más información sobre la creación de servicios de importación de datos personalizados en AEM, lea el siguiente artículo [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## Problemas de DTM (heredados) {#dtm-legacy-issues}

### La etiqueta de script de la DTM no se representa en el origen de la página {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

La variable [DTM](/help/sites-administering/dtm.md) la etiqueta de script no se incluye correctamente en la página aunque se haya hecho referencia a la configuración en las propiedades de la página [Cloud Services](/help/sites-developing/extending-cloud-config.md) pestaña .

#### Solución {#solution-2}

Para solucionar el problema, puede probar lo siguiente:

* Asegúrese de que las propiedades cifradas se puedan descifrar (tenga en cuenta que el cifrado puede utilizar una clave generada automáticamente diferente en cada instancia de AEM). Para más detalles, lea también [Compatibilidad con cifrado para propiedades de configuración](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Vuelva a publicar las configuraciones encontradas en `/etc/cloudservices/dynamictagmanagement`
* Comprobar ACL en `/etc/cloudservices`. Las ACL deben ser:

   * permitir; jcr:read; webservice-support-servicelibfinder
   * permitir; jcr:read; todos; rep:glob:&amp;ast;/default/&amp;ast;
   * permitir; jcr:read; todos; rep:glob:&amp;ast;/default
   * permitir; jcr:read; todos; rep:glob:&amp;ast;/public/&amp;ast;
   * permitir; jcr:read; todos; rep:glob:&amp;ast;/public

Para obtener más información sobre la administración de ACL, lea la [Administración de usuarios y seguridad](/help/sites-administering/security.md#permissions-in-aem) página.

## Problemas de integración de Target {#target-integration-issues}

### Contenido de destino no visible en el modo de vista previa al utilizar componentes de página personalizados {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Este problema se debe a que los componentes de página personalizados no incluyen las bibliotecas JSP o de cliente correctas que administran las integraciones de DTM de Target.

#### Solución {#solution-3}

Puede probar las siguientes soluciones:

* Asegúrese de que la variable `headlibs.jsp` (si existe `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) incluye lo siguiente:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Asegúrese de que la variable `head.html` (si existe `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **no** incluya selectivamente encabezados de integración específicos como el ejemplo siguiente:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

La variable `servicelibs.jsp` agrega los objetos JavaScript de analytics necesarios y carga las bibliotecas de servicios de nube asociadas con el sitio web. Para el servicio de Target, las bibliotecas se cargan mediante la variable `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

El conjunto de bibliotecas cargadas depende del tipo de biblioteca de cliente de destino ( `mbox.js` o `at.js`) se utiliza en la configuración de Target.

Al utilizar DTM para entregar `mbox.js` o `at.js` asegúrese de que las bibliotecas se cargan antes de que se represente el contenido. El uso de Tag Management Systems que cargan estas bibliotecas de forma asíncrona podría causar problemas al ejecutar el código JavaScript específico de destino.

Para obtener más información, lea la [Desarrollo para contenido de destino](/help/sites-developing/target.md#understanding-the-target-component) página.

### El error &quot;Falta el ID del grupo de informes en la inicialización de AppMeasurement&quot; se muestra en la consola del explorador {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Este problema puede aparecer cuando Adobe Analytics se implementa en el sitio web mediante DTM y utiliza código personalizado. La causa es usar la variable `s = new AppMeasurement()` para crear una instancia de `s` objeto.

#### Solución {#solution-4}

Uso `s_gi` en lugar de `new AppMeasurement` método de creación de instancias. Por ejemplo:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Se muestra aleatoriamente una oferta predeterminada en lugar de la oferta correcta {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Este problema puede tener varias causas:

* Cargando bibliotecas de cliente de Target ( `mbox.js` o `at.js`) de forma asíncrona, el uso de sistemas Tag Management de terceros puede dañar aleatoriamente la segmentación. Se supone que las bibliotecas de Target se cargan sincrónicamente en el encabezado de página. Esto siempre ocurre cuando las bibliotecas se entregan desde AEM.

* Cargando dos bibliotecas de cliente de Target ( `at.js`) simultáneamente, por ejemplo, uno que utiliza DTM y otro que utiliza la configuración de Target en AEM. Esto puede provocar conflictos para la variable `adobe.target` definición si la variable `at.js` las versiones son diferentes.

#### Solución {#solution-5}

Puede probar las siguientes soluciones:

* Asegúrese de que el código de cliente que carga las bibliotecas de tipo DTM (que a su vez carga las bibliotecas de Target) se ejecuta sincrónicamente en la variable [encabezado de página](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* si el sitio está configurado para utilizar DTM para entregar bibliotecas de Target, asegúrese de que la variable **Clientlib entregado por DTM** está marcada en la [Configuración de Target](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) para el sitio.

### Siempre se muestra una oferta predeterminada en lugar de la oferta correcta al usar AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

De serie AEM 6.2 y 6.3 no es compatible con la versión 1.3.0 o posterior de AT.js. Con la versión 1.3.0 de AT.js que introduce la validación de parámetros para sus API, `adobe.target.applyOffer()` requiere un parámetro &quot;mbox&quot; que no proporciona el `atjs-itegration.js` código.

#### Solución {#solution-6}

Para resolver este problema, edite `atjs-itegration.js` y añada `"mbox": mboxName` campo en el objeto de parámetro para `adobe.target.applyOffer()` de la siguiente manera:

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### La página Objetivos y configuración no muestra la sección Fuentes de informes {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

Es muy probable que este problema sea un [Configuración de A4T Analytics Cloud](/help/sites-administering/target-configuring.md) problema de aprovisionamiento.

#### Solución {#solution-7}

Debe verificar que A4T esté correctamente habilitado para su cuenta de Target enviando la siguiente solicitud de verificación a AEM:

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json
 
{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

Si la respuesta contiene la línea `a4tEnabled:false`, contenido [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/contact.html) para que su cuenta esté aprovisionada correctamente.

### API de Target útiles {#helpful-target-apis}

A continuación se presentan dos API de Target que pueden resultar útiles para solucionar problemas de Target:

* Recuperar el punto final de Target para un clientcode determinado

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json
 
{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Recuperar el perfil de un cliente

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>
 
Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```
