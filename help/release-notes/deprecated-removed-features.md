---
title: Funciones en desuso y eliminadas
seo-title: Funciones en desuso y eliminadas
description: Notas de versión específicas de las funciones en desuso y eliminadas de Adobe Experience Manager 6.4.
seo-description: Notas de versión específicas de las funciones en desuso y eliminadas de Adobe Experience Manager 6.4.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: d79b5f7204cb7a00cef6d31a1fdd2cbe93a6cfbe

---


# Funciones en desuso y eliminadas {#deprecated-and-removed-features}

Adobe evalúa constantemente las capacidades de los productos para renovar o sustituir las funciones más antiguas con alternativas modernas que mejoren el valor general del cliente, siempre teniendo en cuenta la compatibilidad con versiones anteriores.

Para comunicar la eliminación o el reemplazo inminente de las capacidades de AEM, se aplican las siguientes reglas:

1. Primero se anuncia el desuso. Aunque estén en desuso, las capacidades aún están disponibles, pero ya no serán mejoradas.
1. La eliminación de las capacidades en desuso ocurrirá en la siguiente versión principal, como mínimo. Se anunciará la fecha real de la eliminación.

Este proceso proporciona a los clientes un ciclo de lanzamiento para adaptar su implementación a una nueva versión o a la siguiente versión de una capacidad en desuso, antes de eliminarla.

## Funciones en desuso {#deprecated-features}

Esta sección detalla las funciones y capacidades en desuso de AEM 6.4. Normalmente, las funciones que se quieren eliminar de una versión futura se establecen primero en desuso y, a continuación, se proporciona una alternativa.

Se recomienda a los clientes que comprueben si utilizan la función o capacidad en su implementación actual, y que planifiquen el cambio de la implementación y usen la alternativa proporcionada.

<table> 
 <tbody>
  <tr>
   <td>Área</td> 
   <td>Función</td> 
   <td>Reemplazo</td> 
  </tr>
  <tr>
   <td>IU</td> 
   <td><p>Adobe no tiene previsto realizar más mejoras en la interfaz de usuario clásica. AEM 6.4 tiene la interfaz de usuario clásica incluida y los clientes que actualicen desde versiones anteriores pueden seguir utilizándola. Tenga en cuenta que la interfaz de usuario clásica será totalmente compatible mientras esté en desuso. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Editor de páginas)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Se recomienda a los clientes que cambien para utilizar la nueva interfaz de usuario de AEM.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td><p>Adobe no planea realizar más mejoras en los componentes de base que se indican a continuación. AEM 6.4 incluye los componentes de base y los clientes que actualicen desde versiones anteriores pueden seguir utilizándolos tal cual. Tenga en cuenta que los componentes básicos serán totalmente compatibles mientras estén en desuso. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>fundación/componentes/cuenta/contraseña</li> 
     <li>base/componentes/cuenta/confirmación de solicitud</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>base/componentes/enfoque de recursos</li> 
     <li>base/componentes/ruta de exploración</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listados</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>base/componentes/lista móvil</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>base/componentes/referencia móvil</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Se recomienda a los clientes que utilicen los componentes principales para futuros proyectos. No es necesario cambiar los sitios existentes.</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td><p>Adobe no planea realizar más mejoras en los componentes de base que se indican a continuación. AEM 6.4 incluye los componentes de base y los clientes que actualicen desde versiones anteriores pueden seguir utilizándolos tal cual. Tenga en cuenta que los componentes básicos serán totalmente compatibles mientras estén en desuso.</p> 
    <ul> 
     <li>base/componentes/temporización</li> 
    </ul> </td> 
   <td>En el momento de escribir esto, no está planeado proporcionar un reemplazo.</td> 
  </tr>
  <tr>
   <td>Director de portal</td> 
   <td><p>El director del portal es un conjunto de funciones que permite alojar contenido de AEM a través de Portlet en servidores de terceros.</p> <p>Adobe no planea realizar más mejoras en la función de director del portal en la ubicación que se muestra a continuación. AEM 6.4 incluye el director del portal y los clientes que actualicen desde versiones anteriores pueden seguir usándolo tal cual. Tenga en cuenta que Portal Direct sigue siendo totalmente compatible mientras está en desuso.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>En el momento de escribir esto, no está planeado proporcionar un reemplazo.</td> 
  </tr>
  <tr>
   <td>Componente Portlet</td> 
   <td><p>Portlet Components en /foundation/components/portlet permite alojar portlets JSR en AEM como componentes.</p> <p>Adobe no planea realizar más mejoras en la función Componente Portlet. AEM 6.4 incluye el componente Portlet y los clientes que actualicen desde versiones anteriores pueden seguir usándolo tal cual. Tenga en cuenta que el componente Portlet sigue siendo totalmente compatible mientras está en desuso.</p> </td> 
   <td>En el momento de escribir esto, no está planeado proporcionar un reemplazo.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>La compatibilidad con el servicio Adobe Central Migration Bridge ha quedado obsoleta, ya que el producto Adobe Central ya no es compatible.</p> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Recursos</td> 
   <td><p>La descarga de recursos ha quedado obsoleta a partir de AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funciones eliminadas {#removed-features}

Esta sección lista las funciones y funciones que se han eliminado de AEM 6.4. Las versiones anteriores tenían estas capacidades marcadas como obsoletas.

<table> 
 <tbody>
  <tr>
   <td><strong>Área</strong></td> 
   <td><strong>Función</strong></td> 
   <td><strong>Reemplazo</strong></td> 
  </tr>
  <tr>
   <td>Mapa de Actividad de Analytics</td> 
   <td>Versión del mapa de Actividad que se incluye en AEM.</td> 
   <td>Debido a los cambios de seguridad de la API de Adobe Analytics, ya no es posible utilizar la versión de Activity Map incluida en AEM.<br><br>Ahora debe utilizarse el complemento <a href="https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">ActivityMap proporcionado por Adobe Analytics</a> .</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Captcha<br /> de formulario (foundation/components/form/captcha)</td> 
   <td>Utilice el componente ReCaptcha de Google en su lugar</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Presentación<br /> de diapositivas (base/componentes/proyección de diapositivas)</td> 
   <td>Sin reemplazo</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Flash<br /> (foundation/components/flash)</td> 
   <td>Sin reemplazo</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Se ha eliminado la compatibilidad con la reproducción de archivos SWF en el componente<br /> de vídeo (foundation/components/video)</td> 
   <td>Utilice formatos de vídeo basados en ninguno flash.</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Tabla<br /> de productos (comercio/componentes/tabla de productos)</td> 
   <td>Sin reemplazo</td> 
  </tr>
  <tr>
   <td>Administración de tareas</td> 
   <td>Administración<br /> de Tareas de la IU clásica (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>Desaprobado desde 6.0. Utilice la nueva administración de tareas que se combina con la interfaz de usuario del flujo de trabajo.</td> 
  </tr>
  <tr>
   <td>Flujo de trabajo</td> 
   <td>Interfaz de usuario de notificaciones utilizada entre 5.6 y 6.2<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>Bandeja de entrada de workflow /aem/inbox</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Se ha eliminado la exportación de PDF a formato PDF/E-1 mediante PDF Generator.</td> 
   <td>PDF Generator sigue siendo compatible con la exportación de PDF a los formatos PDF/A-1a/b, PDF/A-2a/b y PDF/A-3a/b.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Se ha eliminado la compatibilidad con el servicio AEM Captcha predeterminado en formularios adaptables. </td> 
   <td>Usa ReCaptcha por Google en su lugar.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Se ha eliminado la compatibilidad con imágenes dentro de fragmentos de documento. </td> 
   <td>Las comunicaciones interactivas permiten utilizar imágenes directamente en canales impresos y Web.<br /> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td> Actualización fuera del lugar </td> 
   <td>No hay soporte para realizar la actualización fuera del lugar <br/> </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Transferir para migraciones de TarMK a DocumentMK </td> 
   <td> Puede exportar los datos de sistemas anteriores y luego importarlos en un sistema de configuración reciente. Para obtener instrucciones detalladas, consulte Documentos de actualización de AEM Forms en JEE <br/> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
 <td>AEM Forms en el instalador de 32 bits JEE no está disponible.</td> 
   <td>Adobe ha dejado de enviar AEM Forms en el instalador de 32 bits JEE. Puede seguir utilizando el instalador de 64 bits para instalar AEM Forms en JEE. </td>  
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Se ha eliminado la compatibilidad con el uso de imágenes DAM en el componente Fragmento de Documento.</td> 
    <td> Puede utilizar los componentes Imagen y Gráfico en el canal de impresión de la comunicación interactiva. Si utiliza el componente de fragmento de documento de documento adaptable en formularios adaptables, dejará de funcionar después de actualizar a AEM 6.4 Forms. </td>  
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Se ha eliminado la función Documentos adaptables</td> 
   <td> Puede utilizar la función de comunicaciones interactivas para crear comunicaciones impresas y basadas en Web. <br/> </td> 
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Se han eliminado los formularios AEM en una página de aterrizaje específica de JEE.</td> 
    <td>AEM Forms en la página de aterrizaje JEE se sustituye por la página de aterrizaje AEM (/aem/start.html) </td>  
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Se ha eliminado la compatibilidad con Captcha predeterminada</td> 
   <td>Utilice el servicio reCAPTCHA de Google.</td> 
  </tr>
  <tr>
   <td>Communities</td> 
   <td>Se ha eliminado la compatibilidad con la verificación de Captcha.</td> 
   <td>Utilice la integración captcha personalizada (como reCAPTCHA por Google) para la verificación.</td> 
  </tr>
 </tbody>
</table>

## Anuncio previo para la siguiente versión {#pre-announcement-for-next-release}

Esta sección se utiliza para anunciar con antelación los cambios en futuras versiones, que no se consideran en desuso, pero que afectarán a los clientes. Se proporcionan con fines de planificación.

<table> 
 <tbody>
  <tr>
   <td>Área<br /> </td> 
   <td>Función<br /> </td> 
   <td>Anuncio</td> 
  </tr>
  <tr>
   <td>Compatibilidad con navegadores</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4 es la última versión que admite Microsoft Internet Explorer 11.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>Marco de interfaz de usuario</td> 
   <td>Adobe dejará de utilizar los componentes de Coral UI 2 en 2019. AEM 6.4 se basa completamente en la interfaz de usuario de Coral 3 (incluida con AEM 6.2). Adobe recomienda a sus clientes y socios que hayan creado IU personalizadas con Coral 2 que las refactoricen a Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
