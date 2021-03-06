---
title: Personalización de contenido de AEM Mobile
seo-title: Personalización de contenido de AEM Mobile
description: 'Siga esta página para conocer la función de personalización de contenido de AEM Mobile que permite a los autores de AEM personalizar el contenido de las aplicaciones móviles mediante Adobe Target. '
seo-description: 'Siga esta página para conocer la función de personalización de contenido de AEM Mobile que permite a los autores de AEM personalizar el contenido de las aplicaciones móviles mediante Adobe Target. '
uuid: 9078edd1-8399-485f-8a63-a07e766f7ef9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c9c818dc-c5c4-4a96-94fe-9dc9fe75705b
translation-type: tm+mt
source-git-commit: 64090e3c7cf722f44968467c51291a11aeeec237
workflow-type: tm+mt
source-wordcount: '2701'
ht-degree: 0%

---


# Personalización de contenido de AEM Mobile{#aem-mobile-content-personalization}

>[!NOTE]
>
>Adobe recomienda el uso del Editor de SPA para proyectos que requieren una representación de cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>Este documento forma parte de la [Guía de introducción a AEM Mobile](/help/mobile/getting-started-aem-mobile.md), un punto de partida recomendado para referencia de AEM Mobile.

La función de personalización de contenido de AEM Mobile permite que [AEM Authors](#author) personalice el contenido de la aplicación móvil aprovechando [Adobe Target](https://www.adobe.com/ca/marketing-cloud/testing-targeting.html). Esto permite el envío de ofertas de objetivo para los usuarios de aplicaciones móviles. Adobe Experience Manager Mobile ofrece la capacidad de crear, destinatario y distribuir contenido que proporcionará al usuario contenido específico para sus propios gustos individuales.

Como suele suceder en AEM, para que los autores empiecen a crear este contenido, los administradores y desarrolladores deben preparar primero el entorno.

[AEM ](#administrator) administradores deben establecer una conexión entre AEM Mobile y el Cloud Service de Adobe Target.

Mientras tanto, los [desarrolladores](#developer) de AEM Mobile deben modificar sus scripts existentes para facilitar la creación de contenido dirigido.

## Para administradores {#for-administrators}

Hay varios pasos que deben seguirse para que los autores de contenido puedan generar inicios para crear contenido de destino para las aplicaciones móviles: Se obtiene el conjunto correcto de permisos para usuarios y grupos, se crean servicios en la nube, se configura la aplicación para la actividad y, finalmente, se genera el contenido.

Este artículo lo guiará a través del proceso utilizado para configurar la [Aplicación de referencia híbrida de AEM Mobile](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) para objetivos.

En adelante, se supone que la Aplicación de referencia híbrida de AEM Mobile se ha implementado correctamente y se puede acceder a ella a través del Panel de AEM Mobile.

Antes de que los autores puedan generar contenido de destino dentro de una aplicación, la instancia de AEM debe [configurarse con el Cloud Service de Adobe Target.](/help/mobile/aem-mobile-configuring-cloud-service.md)

### Permisos    {#permissions}

Los usuarios que necesitan acceder a la consola de personalización deben formar parte del grupo `target-activity-authors`.

Se sugiere que, como parte de la configuración de usuarios y grupos, el grupo de actividades de destinatario se agregue al grupo de administradores de aplicaciones. Al agregar el grupo destinatario-actividades-autores, esto permitirá a los usuarios ver la entrada del menú de navegación Personalización.

>[!NOTE]
>
>Olvidar agregar los usuarios o grupos a los que desea tener acceso a la consola de administración de personalización al grupo de autores de actividades de destinatario impedirá que los usuarios vean la consola de personalización.

### Cloud Services{#cloud-services}

Para que el contenido objetivo funcione en aplicaciones móviles, hay dos servicios que deben configurarse: El servicio Adobe Target y el servicio Adobe Mobile Services. El servicio Adobe Target proporciona el motor para procesar solicitudes de cliente y devolver el contenido personalizado. El servicio Adobe Mobile Services proporciona la conexión entre los servicios de Adobe y la aplicación móvil mediante el archivo ADBMobileConfig.json que consume el complemento AMS Cordova. Desde AEM Mobile Panel puede configurar la aplicación agregando los dos servicios.

En el Panel de AEM Mobile, busque Administrar Cloud Services y haga clic en el botón +.

![chlimage_1-38](assets/chlimage_1-38.png)

En el asistente Añadir Cloud Service, seleccione la tarjeta de servicio en la nube &quot;Adobe Target&quot; y haga clic en Siguiente.

![chlimage_1-39](assets/chlimage_1-39.png)

En el menú desplegable Seleccionar una configuración puede crear una nueva configuración o seleccionar una existente. Para crear una nueva configuración, seleccione &quot;Crear configuración&quot; en el menú desplegable. Introduzca un título para la configuración de Destinatario. Introduzca el código de cliente, el correo electrónico y la contraseña asociados a su cuenta de Destinatario. Si no conoce los valores de estos campos, póngase en contacto con la asistencia de Adobe Target. Haga clic en el botón &quot;Verificar&quot; para validar las credenciales. Una vez verificado, haga clic en el botón Enviar para crear el servicio en la nube.

>[!NOTE]
>
>El servicio en la nube que se crea se asocia automáticamente con la aplicación móvil mediante el asistente. El valor de la propiedad cq:cloudserviceconfigs se establece en el nodo jcr:content del nodo del grupo de aplicaciones. Para el ejemplo de aplicación híbrida, se establece en /content/mobileapps/hybrid-reference-app/jcr:content con el valor que apunta al nodo de marco generado automáticamente ubicado en /etc/cloudservices/testandtarget/adobe-destinatario—aem-apps/framework. El nodo de marco tiene dos propiedades definidas de forma predeterminada: sexo y edad. El marco solo se utiliza con la vista previa AEM y no tiene ningún impacto en el dispositivo.

Después de completar el asistente, el mosaico Administrar Cloud Service contendrá el servicio de nube de Destinatario, aunque contiene una advertencia sobre la falta de una cuenta de Adobe Mobile Service.

![chlimage_1-40](assets/chlimage_1-40.png)

### Adobe Mobile Services {#adobe-mobile-services}

Es necesario vincular también una cuenta de Adobe Mobile Services (AMS) a la aplicación; el servicio AMS proporciona el archivo ADBMobileConfig.json necesario que contiene la información del código de cliente de Destinatario. Antes de crear una asociación con la cuenta de AMS, la cuenta de AMS debe ser modificada por un usuario que tenga permisos para AMS.

### Código de cliente {#client-code}

Para iniciar sesión en los servicios de AMS, visite [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), seleccione la aplicación móvil y haga clic en la configuración. Busque el campo Opciones de Destinatario del SDK, coloque el código de cliente en el campo y haga clic en Guardar.

![chlimage_1-41](assets/chlimage_1-41.png)

Ahora que el código de cliente se ha asociado con la aplicación móvil, cuando el servicio en la nube de AMS se configura mediante el Panel de Adobe Mobile, la configuración del servicio se enviará mediante el archivo ADBMobileConfig.json.

### Adobe Mobile Service Cloud Service {#adobe-mobile-service-cloud-service}

Ahora que AMS se ha configurado, es hora de asociar la aplicación móvil en el Panel de Adobe Mobile. En el Panel de AEM Mobile, busque Administrar Cloud Services y haga clic en el botón +.

![chlimage_1-42](assets/chlimage_1-42.png)

Seleccione la tarjeta de Adobe Mobile Services y haga clic en Siguiente.

![chlimage_1-43](assets/chlimage_1-43.png)

En el paso Crear o seleccionar del asistente, seleccione la lista desplegable Servicio móvil y seleccione la entrada Crear configuración. Proporcione un título, compañía, nombre de usuario, contraseña y seleccione el centro de datos adecuado. Si no conoce estos valores, póngase en contacto con el administrador de Adobe Mobile Service para obtenerlos. Una vez completados todos los campos, haga clic en el botón Verificar. El proceso de verificación se dirige a AMS y verifica las credenciales de la cuenta. Una vez realizada la validación, se rellenará una lista de aplicaciones móviles donde se seleccione la aplicación móvil asociada en el menú desplegable. Haga clic en el botón Enviar para completar el asistente. El proceso puede tardar un poco en obtener los datos de configuración y los análisis asociados con la aplicación. Una vez completado el proceso, haga clic en el botón Finalizado del modal para volver al Panel de Adobe Mobile.

Si vuelve al Panel móvil, el mosaico Administrar Cloud Services contendrá el servicio en la nube de AMS. También observará que el mosaico Analizar métricas se rellenará con informes del ciclo vital.

![chlimage_1-44](assets/chlimage_1-44.png)

## Para autores {#for-authors}

**Requisito previo:** Como se ha mencionado anteriormente, los administradores deben configurar la conexión al servicio Adobe Target antes de que los autores puedan generar nuevo contenido de destino.

Una vez que el administrador haya configurado los dos servicios en la nube y el desarrollador haya configurado el controlador mobileappoffers, los autores de contenido ahora pueden generar inicios en la generación de experiencias de objetivo.

La creación de contenido de destino en una aplicación de AEM Mobile sigue un procedimiento similar al de creación de AEM Sites:

Consulte aquí para obtener una descripción general completa de la [creación de contenido de destino en AEM](/help/sites-authoring/personalization.md)

## Para desarrolladores {#for-developers}

AEM desarrolladores que crean aplicaciones móviles deben seguir los patrones que se utilizan habitualmente a lo largo de AEM cuando desarrollan componentes. Aquí, le explicaremos los pasos necesarios para permitir a los autores de contenido crear contenido de objetivo:

### Controladores Adobe Target ContentSync {#adobe-target-contentsync-handlers}

Para entregar contenido al contenido del dispositivo del usuario, se genera mediante la representación de las ofertas creadas por los autores de contenido de AEM. Para gestionar el procesamiento de ofertas de destinatario, hay un nuevo controlador de sincronización de contenido que procesará las ofertas. Utilizando la Aplicación de referencia híbrida como ejemplo, el paquete de contenido en (inglés) contiene ContentSyncConfig con un controlador [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml). El siguiente paso es crucial para procesar ofertas en el dispositivo. El controlador mobileappoffers tiene una propiedad path que identifica la ruta a la actividad de personalización que se va a utilizar para la aplicación.

Por ejemplo, si hay una actividad ubicada en */content/campañas/hybridref* copie esta ruta y péguela como valor en la propiedad *path* del controlador mobileappoffers.

>[!NOTE]
>
>Para la Aplicación de referencia híbrida hay dos controladores mobileappoffers: uno para el desarrollo y otro para las producciones.

Una vez configurada la ruta de actividades en la propiedad path del controlador mobileappoffers, guarde el controlador. El controlador estará listo para procesar ofertas de procesamiento de inicio para nuestros dispositivos móviles.

### Modo de procesamiento {#render-mode}

El controlador mobileappoffers está configurado de forma diferente para la configuración de publicación y desarrollo. Para la configuración de publicación hay una propiedad denominada *modoDeProcesamiento* con un valor de *publish* establecido en el nodo cq:ContentSyncConfig. El controlador mobileappoffers hace referencia al parámetro rendoMode y, si se establece para publicación, modificará la ID de mbox que se crea. De forma predeterminada, los mboxes creados por AEM tienen un valor —author anexado a la ID del mbox. Esto identifica que la actividad no se ha publicado y debe utilizar la campaña no publicada para las resoluciones de la oferta.

Cuando el contenido se escala mediante el Panel de Adobe Mobile, el contenido escalonado se considera contenido listo para la producción y se procesa mediante la configuración de sincronización de contenido que no es de desarrollo. Si se procesa de este modo, se eliminará —author de todos los identificadores de mbox y se espera que una actividad publicada esté disponible en el servidor de Destinatario. Antes de probar el contenido de ensayo, asegúrese de que la actividad se ha publicado.

### Desarrollo de aplicaciones de personalización {#personalization-app-development}

#### Componentes {#components}

La base de cualquier contenido suele ser un componente de página que extiende uno de los componentes de página de AEM base wcm/foundation/components/page o foundation/components/page, en función de si utiliza HTL o JSP. La duración de estos pasos se centrará en el uso del componente wcm/foundation/components/page. La estructura básica del componente de página se divide en varias secuencias de comandos; cada una de ellas proporciona el propósito específico de permitir al desarrollador organizar y anular su código si es necesario. Las dos secuencias de comandos que son de interés para la Personalización son head.html y body.html. Estas dos secuencias de comandos proporcionan un área en la que se puede insertar código para admitir Context Hub, Cloud Services y la creación móvil.

A continuación se ofrece una descripción general de los dos scripts principales utilizados para habilitar la segmentación de contenido.

#### head.html {#head-html}

Para proporcionar al autor la capacidad de destinatario del contenido, es necesario agregar el menú destinatario a la página para que el autor pueda cambiar el contexto del modo de edición al modo de objetivo. Para habilitar esta función, el desarrollador debe modificar la secuencia de comandos head.html para incluir el siguiente fragmento de código cerca de la parte superior de head.html o lo más cerca posible del elemento &lt;title>&lt;/title>.

```xml
<meta data-sly-test="${!wcmmode.disabled}">
    <div data-sly-call="${clientLib.all @ categories='personalization.kernel'}" data-sly-unwrap></div>
    <div data-sly-resource="${'config' @ resourceType='cq/personalization/components/clientcontext_optimized/config'}" data-sly-unwrap></div>
    <div data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}" data-sly-unwrap></div>
</meta>
```

>[!NOTE]
>
>Tenga en cuenta que la secuencia de comandos solo debe incluirse cuando el modo WCM no se haya deshabilitado, de modo que cuando el modo WCM esté deshabilitado (consulte la sección del controlador ContentSync para obtener más información) la secuencia de comandos no se incluirá en el código de la aplicación final.

Para ofrecer a los autores la capacidad de previsualización del contenido de destino, el editor debe poder localizar la configuración del servicio en la nube de Adobe Target. El bloque de código siguiente agrega dos secuencias de comandos importantes. La primera vez que se agrega la capacidad de la página para ubicar el servicio de nube de Destinatario asociado y realizar las llamadas a Adobe Target. El segundo es la adición de la categoría cq.apps.targeting.

La categoría **cq.apps.targeting** anula el componente cq/personalization/component/destinatario predeterminado y utiliza el componente mobileapps/components/destinatario que procesa ofertas específicas para el consumo de aplicaciones móviles. En la sección Componente de Destinatario se analizarán más detalles al respecto.

El código debe agregarse en head.html y colocarse justo antes del final del elemento &lt;/head>.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-include="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" data-sly-unwrap></div>
    <meta data-sly-call="${clientLib.all @ categories='cq.apps.targeting'}" data-sly-unwrap></meta>
</div>
```

>[!NOTE]
>
>Tenga en cuenta que el bloque de código se envuelve dentro de un modo WCM, por lo que no se desactiva, solo entra en juego mientras el autor del contenido está trabajando en la creación de contenido. Los scripts del servicio de nube no se agregarán al código de tiempo de ejecución móvil generado.

#### body.html {#body-html}

Para habilitar al autor del contenido la capacidad de probar diferentes personalidades, la secuencia de comandos body.html debe incluir el siguiente bloque de código como el primer elemento secundario del elemento body.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'clientcontext' @ resourceType='cq/personalization/components/clientcontext_optimized'}" data-sly-unwrap></div>
</div>
```

El último código requerido se encuentra en la parte inferior de body.html. Este bit de código busca el servicio de nube asociado e inserta el código de motor de objetivo correspondiente.

```xml
<div data-sly-test="${!wcmmode.disabled}">
    <div data-sly-resource="${'cloudservices' @ resourceType='cq/cloudserviceconfigs/components/servicecomponents'}" data-sly-unwrap></div>
</div>
```

### Aplicación de referencia {#reference-application}

Se pueden encontrar ejemplos de head.html y body.html en la [Aplicación de referencia híbrida de AEM Mobile](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) que muestra al desarrollador dónde colocar los bloques de script dentro de los dos scripts.

### Controladores de sincronización de contenido {#content-sync-handlers}

Cuando el autor del contenido haya terminado de crear contenido para la aplicación móvil, el siguiente paso es descargar el origen y crear la aplicación, o escenificar el contenido que se va a publicar. Hay varios pasos con los que el desarrollador está involucrado para que esto suceda. Para facilitar la representación del contenido, AEM Mobile utiliza controladores de sincronización de contenido para procesar y empaquetar el contenido. Se ha introducido un nuevo controlador de sincronización de contenido para que el caso de uso Personalización muestre el contenido de destino. El controlador &#39;mobileappoffers&#39; sabe cómo procesar las ofertas de destinatario asociadas que ha creado el autor del contenido. El controlador mobileappoffers extiende el controlador de actualización de páginas abstractas, por lo que muchas de las propiedades son similares. Los detalles del controlador mobileappoffers tienen las siguientes propiedades.

<table>
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td>
   <td><strong>Value</strong></td>
   <td><strong>Descripción</strong></td>
  </tr>
  <tr>
   <td>reescribir</td>
   <td>+ relativeParentPath<p> - "/"</p> </td>
   <td>La propiedad rewrite identifica cómo se deben reescribir las rutas dentro del contenido.</td>
  </tr>
  <tr>
   <td>includePageTypes</td>
   <td><p>"cq/personalization/components/teaserpage",</p> <p>"cq/personalization/components/offer proxy"</p> </td>
   <td>La propiedad includePageTypes es opcional y se establece de forma predeterminada en las páginas que tienen tipos de recursos cq/personalization/components/teaserpage y cq/personalization/components/offer proxy. Estos dos tipos de recursos son los tipos de recursos predeterminados que se utilizan cuando se segmenta el contenido. Si es necesario admitir tipos de recursos adicionales, deben agregarse a la lista de includePageTypes.</td>
  </tr>
  <tr>
   <td>locationRoot</td>
   <td>/content/mobileapps/&lt;app&gt;</td>
   <td>Ubicación de la aplicación.</td>
  </tr>
  <tr>
   <td>tipo</td>
   <td>mobileappoffers</td>
   <td>Nombre del controlador que se está usando como mobileappoffers.</td>
  </tr>
  <tr>
   <td>selector</td>
   <td>tandt</td>
   <td>El selector de tendencias se utiliza para representar el contenido de destino. </td>
  </tr>
  <tr>
   <td>targetRootDirectory</td>
   <td>www</td>
   <td>El directorio raíz en el que se debe conservar el contenido procesado.</td>
  </tr>
  <tr>
   <td>includeImages</td>
   <td>true | false</td>
   <td>Si el valor es true, se procesarán todas las imágenes incluidas en la oferta. Si se omiten las imágenes falsas.</td>
  </tr>
  <tr>
   <td>includeVideos</td>
   <td>true | false</td>
   <td>Si el valor es true, se procesarán todos los vídeos incluidos en la oferta. Si se omitirán los vídeos falsos.</td>
  </tr>
  <tr>
   <td>path</td>
   <td>/content/campañas/&lt;marca&gt;</td>
   <td>Señala la marca de la campaña en la que participan las ofertas. Actualmente, todas las ofertas deben proceder de la misma campaña.</td>
  </tr>
  <tr>
   <td>profundo</td>
   <td>true | false</td>
   <td>Si el valor true se procesa recursivamente en todas las páginas secundarias, si el valor false no se repite. </td>
  </tr>
  <tr>
   <td>extension</td>
   <td>html</td>
   <td>Define la extensión del recurso que se está procesando. Se establece en html de forma que las páginas tengan una extensión .html.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>La [Aplicación de referencia híbrida de AEM Mobile](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) tiene la configuración predeterminada del controlador mobileappoffer. La propiedad path del ejemplo está vacía, ya que depende de la ubicación de la campaña. Una vez que un autor de la Campaña ha creado una Campaña, el administrador de aplicaciones debe asociar la Campaña con el controlador especificando la propiedad path para que apunte a la Campaña.

### Componente de destinatario {#target-component}

Para ayudar a procesar contenido específico para aplicaciones móviles, AEM Mobile utiliza el componente mobileapps/components/destinatario. El componente destinatario móvil amplía el componente cq/personalization/components/destinatario y anula el script engine_tnt.jsp. Al anular engine_tnt.jsp, AEM Mobile puede controlar el HTML generado para el caso de uso de las aplicaciones móviles. Para cada componente dirigido por un autor de contenido, engine_tnt.jsp crea un mbox asociado.

Para cada mbox, se agrega un atributo de **cq-targeting** que permite a los desarrolladores de aplicaciones escribir código personalizado para consumir y usar lo que deseen. La [Aplicación de referencia híbrida de AEM Mobile](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) tiene un ejemplo de directiva angular que utiliza el atributo cq-targeting. El concepto de reemplazo de contenido cuándo y cómo se realiza depende en gran medida del desarrollador de aplicaciones móviles. Hay un SDK de Mobile que se entrega a través de AEM /etc/clientlibs/mobileapps/js/mobileapps.js que proporciona una API para llamar al servicio de Adobe Targeting. Corresponde al desarrollador de la aplicación especificar cuándo debe realizarse dicha llamada según el diseño de su aplicación.

## ¿Qué sigue? {#what-s-next}

1. [Inicio de mi experiencia con la aplicación de AEM Mobile](/help/mobile/starting-aem-phonegap-app.md)
1. [Gestión del contenido de mi aplicación](/help/mobile/phonegap-manage-app-content.md)
1. [Generar mi aplicación](/help/mobile/building-app-mobile-phonegap.md)
1. [Rastree el rendimiento de mi aplicación con Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
1. [Ofrezca una experiencia de aplicación personalizada con Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md)
1. [Enviar mensajes importantes a mis usuarios](/help/mobile/phonegap-push-notifications.md)
