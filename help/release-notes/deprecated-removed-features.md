---
title: Funciones en desuso y eliminadas
description: Notas de versión específicas de las funciones en desuso y eliminadas de Adobe Experience Manager 6.4.
translation-type: tm+mt
source-git-commit: 8e82c691affe3b2c4108beec394cc0ba2d607b61
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 26%

---


# Funciones en desuso y eliminadas {#deprecated-and-removed-features}

Adobe evalúa constantemente las capacidades de los productos para renovar o sustituir las funciones más antiguas con alternativas modernas que mejoren el valor general del cliente, siempre teniendo en cuenta la compatibilidad con versiones anteriores.

Para comunicar la eliminación o el reemplazo inminente de las capacidades de AEM, se aplican las siguientes reglas:

1. Primero se anuncia el desuso. Aunque están en desuso, las capacidades siguen estando disponibles, pero no se mejorarán aún más.
1. La eliminación de las capacidades en desuso ocurrirá en la siguiente versión principal, como mínimo. Se anunciará la fecha real de la eliminación.

Este proceso proporciona a los clientes un ciclo de lanzamiento para adaptar su implementación a una nueva versión o a la siguiente versión de una capacidad en desuso, antes de eliminarla.

## Funciones en desuso {#deprecated-features}

La tabla siguiente lista las funciones y funciones que se han marcado como obsoletas con AEM 6.4. Por lo general, las funciones que se planea eliminar en una versión futura se definen en primer lugar como obsoletas, con una alternativa proporcionada.

Se recomienda a los clientes que comprueben si utilizan la función o capacidad en su implementación actual, y que planifiquen el cambio de la implementación y usen la alternativa proporcionada.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Área | Función | Reemplazo |
|---|---|---|
| IU | Adobe no tiene previsto realizar más mejoras en la interfaz de usuario clásica. AEM 6.4 tiene la interfaz de usuario clásica incluida y los clientes que actualicen desde versiones anteriores pueden seguir utilizándola. Tenga en cuenta que la interfaz de usuario clásica será totalmente compatible mientras esté en desuso. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Editor de página) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Se recomienda a los clientes que cambien para utilizar la nueva interfaz de usuario de AEM. |
| Componentes | Adobe no planea realizar más mejoras en los componentes de base que se enumeran a continuación. AEM 6.4 incluye los componentes de base, y los clientes que actualicen desde versiones anteriores pueden seguir usándolos tal cual. Tenga en cuenta que los componentes básicos serán totalmente compatibles mientras estén en desuso. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> fundación/componentes/cuenta/contraseña </li> <li> base/componentes/cuenta/confirmación de solicitud </li> <li> foundation/components/adaptiveimage </li> <li> base/componentes/enfoque de recursos </li> <li> base/componentes/ruta de exploración </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listados </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> base/componentes/lista móvil </li> <li> foundation/components/mobilelogo </li> <li> base/componentes/referencia móvil </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Se recomienda a los clientes que utilicen los componentes principales para futuros proyectos. No es necesario cambiar los sitios existentes. |
| Componentes | Adobe no planea realizar más mejoras en los componentes de base que se enumeran a continuación. AEM 6.4 incluye los componentes de base, y los clientes que actualicen desde versiones anteriores pueden seguir usándolos tal cual. Tenga en cuenta que los componentes básicos serán totalmente compatibles mientras estén en desuso. <ul><li>base/componentes/temporización</li></ul> | El Adobe no planea proporcionar una sustitución. |
| Portal Director | El Portal Director es un conjunto de funciones que permite alojar AEM contenido a través de Portlet en servidores de terceros. Adobe no planea realizar más mejoras en la función Portal Director en la ubicación que se indica a continuación. AEM 6.4 incluye el portal Director y los clientes que actualicen desde versiones anteriores pueden seguir usándolo tal cual. Tenga en cuenta que Portal Direct sigue siendo totalmente compatible mientras está en desuso. <ul><li>/libs/portal/director</li></ul> | El Adobe no planea proporcionar una sustitución. |
| Componente Portlet | Portlet Components bajo /foundation/components/portlet permite alojar portlets JSR en AEM como componentes. Adobe no planea realizar más mejoras en la función Componente Portlet. AEM 6.4 incluye el componente Portlet, y los clientes que actualicen desde versiones anteriores pueden seguir usándolo tal cual. Tenga en cuenta que el componente Portlet sigue siendo totalmente compatible mientras está en desuso. | El Adobe no planea proporcionar una sustitución. |
| Forms | La compatibilidad con el servicio Adobe Central Migration Bridge ha quedado obsoleta, ya que el producto Adobe Central ya no es compatible. | Sin reemplazo |
| Forms | Uso desaprobado de JSONObject en Consulta y OperationOptions. Las siguientes API están en desuso: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Uso de la `IValueMap` API |
| Forms | Servicio de puente de migración central obsoleto. | No se ofrece reemplazo. |
| Assets | La descarga de recursos ha quedado obsoleta a partir de AEM 6.4. |  |
| Desarrolladores | Biblioteca de cliente de guion bajo/guion bajo. Adobe no planea seguir manteniendo y actualizando la biblioteca de clientes Lodash/underscore que se envía como parte de la distribución (Quickstart) | Adobe recomienda a los clientes que aún requieren Lodash/underscore para su código que lo añadan a su base de código de proyecto. |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## Funciones eliminadas {#removed-features}

La tabla siguiente lista las funciones y capacidades que se han eliminado de la AEM 6.4. Las versiones anteriores tenían estas capacidades marcadas como obsoletas.

| Área | Función | Reemplazo |
|---|---|---|
| Analytics Activity Map | La versión de Activity Map que está incluida en AEM. | Debido a los cambios de seguridad de la API de Adobe Analytics, ya no es posible utilizar la versión de Activity Map incluida en AEM. The [ActivityMap plug-in provided by Adobe Analytics](https://docs.adobe.com/content/help/es-ES/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.translate.html) should now be used. |
| Componentes-Forms | Captcha de formulario (foundation/components/form/captcha) | Utilice el componente ReCaptcha de Google en su lugar |
| Componentes | Presentación de diapositivas (base/componentes/proyección de diapositivas) | Sin reemplazo |
| Componentes | Flash (foundation/components/flash) | Sin reemplazo |
| Componentes | Se ha eliminado la compatibilidad con la reproducción de archivos SWF en el componente de vídeo (foundation/components/video) | Utilice formatos de vídeo basados en ninguno flash. |
| Componentes | Tabla de productos (comercio/componentes/tabla de productos) | Sin reemplazo |
| Administración de tareas | Administración de Tareas de la IU clásica (/libs/cq/taskmanagement/content/taskmanager.html) | Desaprobado desde 6.0. Utilice la nueva administración de tareas que se combina con la interfaz de usuario del flujo de trabajo. |
| Flujo de trabajo | Interfaz de usuario de notificaciones utilizada entre 5.6 y 6.2 (/libs/cq/workflow/content/notifications.html) | Bandeja de entrada de flujo de trabajo /aem/inbox |
| Forms | Se ha eliminado el Export PDF al formato PDF/E-1 mediante PDF Generator. | PDF Generator sigue siendo compatible con la exportación de PDF a los formatos PDF/A-1a/b, PDF/A-2a/b y PDF/A-3a/b. |
| Forms | Se ha eliminado la compatibilidad con imágenes dentro de fragmentos de documento. | Las comunicaciones interactivas permiten utilizar imágenes directamente en canales impresos y Web. |
| Forms | Actualización fuera del lugar | No hay soporte para realizar la actualización fuera del lugar |
| Forms | Transferir para migraciones de TarMK a DocumentMK | Puede exportar los datos de sistemas anteriores y luego importarlos en un sistema de configuración reciente. Para obtener instrucciones detalladas, consulte AEM Forms en documentación de actualización de JEE |
| Forms | AEM Forms en el instalador de 32 bits JEE no está disponible. | Adobe ha dejado de enviar AEM Forms en el instalador de 32 bits JEE. Puede seguir utilizando el instalador de 64 bits para instalar AEM Forms en JEE. |
| Forms | Se ha eliminado la compatibilidad con el uso de imágenes DAM en el componente Fragmento de Documento. | Puede utilizar los componentes Imagen y Gráfico en el canal de impresión de la comunicación interactiva. Si utiliza el componente de fragmento de documento de documento adaptable en formularios adaptables, dejará de funcionar después de actualizar a AEM 6.4 Forms. |
| Forms | Se ha eliminado la función Documentos adaptables | Puede utilizar la función de comunicaciones interactivas para crear comunicaciones impresas y basadas en Web. Si utiliza Documentos adaptables, instale el paquete de compatibilidad para seguir utilizando documentos adaptables existentes |
| Forms | Se ha eliminado AEM Forms en la página de aterrizaje específica de JEE. | La página de aterrizaje de AEM Forms en JEE se sustituye por AEM página de aterrizaje (/aem/start.html) |
| Forms | Se ha eliminado la compatibilidad con Captcha predeterminada | Utilice el servicio reCAPTCHA de Google. |
| Forms | Se ha eliminado la compatibilidad con campos Flash en AEM Designer. AEM Designer no permite editar campos Flash utilizados en un formulario. | Puede utilizar AEM Designer lanzado para una versión anterior para editar estos formularios. |
| Communities | Se ha eliminado la compatibilidad con la verificación de Captcha. | Utilice la integración captcha personalizada (como reCAPTCHA por Google) para la verificación. |

## Anuncio previo para la siguiente versión {#pre-announcement-for-next-release}

La tabla siguiente proporciona una lista de los cambios para futuras versiones, que no se han desaprobado pero que pueden afectar a los clientes. Se proporcionan con fines de planificación.

| Área | Función | Anuncio |
|---|---|---|
| Compatibilidad con navegadores | Microsoft Internet Explorer | AEM 6.4 es la última versión que admite Microsoft Internet Explorer 11. |
| Foundation | Marco de interfaz de usuario | Adobe dejará de utilizar los componentes de Coral UI 2 en 2019. AEM 6.4 se basa completamente en la IU de Coral 3 (introducida con AEM 6.2). Adobe recomienda a sus clientes y socios que hayan creado IU personalizadas con Coral 2 que las refactoricen a Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/dialog-conversion.md). |
