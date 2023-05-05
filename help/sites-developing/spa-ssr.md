---
title: SPA y procesamiento en el servidor
seo-title: SPA and Server-Side Rendering
description: "Renderización del lado del SPA y del servidor"
seo-description: null
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
exl-id: 89e45231-885a-4d35-839b-2b50239503ad
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1807'
ht-degree: 2%

---

# SPA y procesamiento en el servidor{#spa-and-server-side-rendering}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>La función Editor de aplicaciones de una sola página (SPA) requiere [AEM 6.4 service pack 2](https://helpx.adobe.com/es/experience-manager/6-4/release-notes/sp-release-notes.html) o posterior.
>
>El Editor de SPA es la solución recomendada para proyectos que requieren SPA procesamiento del lado del cliente basado en el marco de trabajo (por ejemplo, React o Angular).

>[!NOTE]
>
>AEM 6.4.5.0 o posterior es necesario para utilizar las funciones de renderización del lado del servidor de SPA como se describe en este documento.

## Información general {#overview}

Las aplicaciones de una sola página (SPA) pueden ofrecer al usuario experiencias dinámicas y enriquecidas que reaccionan y se comportan de formas familiares, a menudo como las aplicaciones nativas. [Esto se logra confiando en que el cliente cargue el contenido por adelantado y luego haga el trabajo pesado de manejar la interacción del usuario](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) y, de este modo, se minimiza la cantidad de comunicación necesaria entre el cliente y el servidor, lo que hace que la aplicación sea más reactiva.

Sin embargo, esto puede provocar tiempos de carga iniciales más largos, especialmente si el SPA es grande y tiene un contenido enriquecido. Para optimizar los tiempos de carga, parte del contenido se puede representar en el lado del servidor. El uso de la renderización del lado del servidor (SSR) puede acelerar la carga inicial de la página y luego pasar una renderización adicional al cliente.

## Cuándo utilizar SSR {#when-to-use-ssr}

La SSR no es necesaria en todos los proyectos. Aunque AEM admite totalmente la SSR de JS para SPA, Adobe no recomienda implementarla sistemáticamente para cada proyecto.

Al decidir implementar SSR, primero debe estimar qué complejidad adicional, esfuerzo y costo de agregar SSR representa de manera realista para el proyecto, incluido el mantenimiento a largo plazo. Una arquitectura SSR solo debe elegirse cuando el valor añadido exceda claramente los costes estimados.

SSR normalmente proporciona algún valor cuando hay un claro &quot;sí&quot; a cualquiera de las siguientes preguntas:

* **SEO:** ¿Sigue siendo necesario realizar una SSR para que el sitio esté correctamente indexado por los motores de búsqueda que traen tráfico? Tenga en cuenta que los principales rastreadores de motores de búsqueda ahora evalúan JS.
* **Velocidad de página:** ¿La SSR proporciona una mejora de velocidad mensurable en entornos reales y contribuye a la experiencia del usuario general?

Solo cuando al menos una de estas dos preguntas se responde con un claro &quot;sí&quot; para el proyecto, Adobe recomienda implementar SSR. Las secciones siguientes describen cómo hacerlo mediante Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-io-runtime}

Si [estar seguro de que su proyecto requiere la implementación de SSR](#when-to-use-ssr), la solución recomendada de Adobe es utilizar Adobe I/O Runtime.

Para obtener más información sobre Adobe I/O Runtime, consulte

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - para una descripción general del servicio
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) : para obtener documentación detallada sobre la plataforma

Las secciones siguientes detallan cómo se puede utilizar Adobe I/O Runtime para implementar SSR para su SPA en dos modelos diferentes:

* [Flujo de comunicación AEM](#aem-driven-communication-flow)
* [Flujo de comunicación impulsado por el Adobe I/O en tiempo de ejecución](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe recomienda un espacio de trabajo de Adobe I/O Runtime independiente por entorno (etapa, producto, prueba, etc.). Esto permite patrones típicos del ciclo de vida del desarrollo de sistemas (SDLC) con distintas versiones de una sola aplicación implementada en diferentes entornos. Consulte el documento [CI/CD para aplicaciones de Project App Builder](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) para obtener más información.
>
>No se necesita un espacio de trabajo independiente por instancia (autor, publicación) a menos que haya diferencias en la implementación de tiempo de ejecución por tipo de instancia.

## Configuración del procesador de contenido remoto {#remote-content-renderer-configuration}

AEM saber dónde se puede recuperar el contenido procesado de forma remota. Independientemente de [qué modelo elige implementar para SSR](#adobe-io-runtime), deberá especificar cómo AEM acceder a este servicio de procesamiento remoto.

Esto se realiza mediante la variable **RemoteContentRenderer - Fábrica de configuración** Servicio OSGi. Busque la cadena &quot;RemoteContentRenderer&quot; en la consola de configuración de la consola web en `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Los campos siguientes están disponibles para la configuración:

* **Patrón de ruta de contenido** - Expresión regular para que coincida con una parte del contenido, si es necesario
* **URL de extremo remoto** - URL del punto final responsable de la generación del contenido
   * Utilice el protocolo HTTPS protegido si no está en la red local.
* **Encabezados de solicitud adicionales** - Encabezados adicionales que se añadirán a la solicitud enviada al extremo remoto
   * Patrón: `key=value`
* **Tiempo de espera de la solicitud** - Tiempo de espera de solicitud de host remoto en milisegundos

>[!NOTE]
>
>Independientemente de si decide implementar la variable [Flujo de comunicación AEM](#aem-driven-communication-flow) o [Flujo impulsado por Adobe I/O Runtime](#adobe-io-driven-communication-flow), debe definir una configuración del procesador de contenido remoto.
>
>Esta configuración también debe definirse si elige [usar un servidor Node.js personalizado](#using-node-js).

>[!NOTE]
>
>Esta configuración aprovecha el [Procesador de contenido remoto](#remote-content-renderer), que tiene opciones de extensión y personalización adicionales disponibles.

## Flujo de comunicación AEM {#aem-driven-communication-flow}

Cuando se utiliza SSR, la variable [flujo de trabajo de interacción de componentes](/help/sites-developing/spa-overview.md#workflow) de SPA en AEM incluye una fase en la que Adobe I/O Runtime genera el contenido inicial de la aplicación.

1. El navegador solicita el contenido SSR a AEM.
1. AEM publica el modelo en Adobe I/O Runtime.
1. Adobe I/O Runtime devuelve el contenido generado
1. AEM sirve al HTML devuelto por Adobe I/O Runtime a través de la plantilla HTL del componente de página back-end.

![server-side-rendering-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Flujo de comunicación impulsado por Adobe I/O Runtime {#adobe-io-driven-communication-flow}

La sección [Flujo de comunicación AEM](#aem-driven-communication-flow) describe la implementación estándar y recomendada de la renderización del lado del servidor con respecto a la SPA en AEM, donde AEM realiza la inicialización y entrega del contenido.

Alternativamente, SSR puede implementarse para que Adobe I/O Runtime sea responsable del arranque, revirtiendo efectivamente el flujo de comunicación.

Ambos modelos son válidos y son compatibles con AEM. Sin embargo, hay que tener en cuenta las ventajas y desventajas de cada uno antes de aplicar un modelo determinado.

| Agrupamiento | Ventajas | Desventajas |
|---|---|---|
| a través de AEM | AEM administra las bibliotecas de inyección donde sea necesario<br>Los recursos sólo deben mantenerse en AEM | Posiblemente no esté familiarizado con SPA desarrollador |
| a través de Adobe I/O Runtime | Más familiarizado con los desarrolladores de SPA | Los recursos de Clientlib requeridos por la aplicación, como CSS y JavaScript, deberán estar disponibles para el desarrollador de AEM a través del [`allowProxy` property](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>Los recursos deben sincronizarse entre AEM y Adobe I/O Runtime<br>Para habilitar la creación de la SPA, puede ser necesario un servidor proxy para Adobe I/O Runtime |

## Planificación de SSR {#planning-for-ssr}

Por lo general, solo una parte de una aplicación debe representarse en el servidor. El ejemplo común es que el contenido que se mostrará encima del pliegue en la carga inicial de la página debe representarse en el servidor. Esto ahorra tiempo al enviar al cliente contenido ya procesado. A medida que el usuario interactúa con el SPA, el cliente procesa el contenido adicional.

Al considerar la implementación del procesamiento del lado del servidor para su SPA, debe revisar qué partes de la aplicación requerirán reenvío del lado del servidor.

## Desarrollo de una SPA mediante SSR {#developing-an-spa-using-ssr}

SPA componentes podrían ser procesados por el cliente (en el navegador) o por el servidor. Cuando se procesa en el servidor, las propiedades del explorador, como el tamaño de la ventana y la ubicación, no están presentes. Por lo tanto, SPA componentes deben ser isomórficos, sin suponer dónde se procesarán.

Para aprovechar SSR, deberá implementar su código en AEM así como en Adobe I/O Runtime, que es responsable de la renderización del lado del servidor. La mayoría del código será el mismo, pero las tareas específicas del servidor diferirán.

## SSR para SPA en AEM {#ssr-for-spas-in-aem}

El SSR para SPA en AEM requiere Adobe I/O Runtime, que se llama para la renderización del servidor de contenido de la aplicación. Dentro de HTL de la aplicación, se llama a un recurso en Adobe I/O Runtime para procesar el contenido.

Del mismo modo que AEM admite los marcos de SPA Angular y React de forma predeterminada, el procesamiento en el servidor también se admite para aplicaciones de Angular y React. Para más detalles, consulte la documentación de NPM para ambos marcos.

* Reacción: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Para ver un ejemplo simplista, consulte la [Aplicación de diario We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Procesa el servidor de aplicaciones completo. Aunque este no es un ejemplo real, sí ilustra lo que se necesita para implementar la SSR.

>[!CAUTION]
>La variable [Aplicación de diario We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) es solo para fines de demostración y, por lo tanto, utiliza Node.js como ejemplo simple en lugar de la Adobe I/O Runtime recomendada. Este ejemplo no debe utilizarse para ningún trabajo de proyecto.

>[!NOTE]
>Cualquier proyecto AEM debería aprovechar el [Tipo de archivo del proyecto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=es), que admite proyectos de SPA que utilizan React o Angular y aprovecha el SDK de SPA.

## Uso de Node.js {#using-node-js}

Adobe I/O Runtime es la solución recomendada para implementar SSR para SPA en AEM.

Para las instancias de AEM locales, también es posible implementar SSR mediante una instancia de Node.js personalizada de la misma manera que se describió anteriormente. Aunque el Adobe lo admite, no se recomienda.

Node.js no es compatible con instancias de AEM alojadas en Adobe.

>[!NOTE]
>
>Si SSR debe implementarse mediante Node.js, Adobe recomienda una instancia de Node.js independiente para cada entorno AEM (autor, publicación, etapa, etc.).

## Procesador de contenido remoto {#remote-content-renderer}

La variable [Configuración del procesador de contenido remoto](#remote-content-renderer-configuration) que es necesario para utilizar SSR con su SPA en AEM toque en un servicio de renderización más generalizado que se puede ampliar y personalizar para satisfacer sus necesidades.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` es un servicio OSGi para recuperar contenido procesado en un servidor remoto, como desde el Adobe I/O. El contenido enviado al servidor remoto se basa en el parámetro de solicitud pasado.

`RemoteContentRenderingService` se puede insertar mediante la inversión de dependencias en un modelo Sling personalizado o servlet cuando se requiere una manipulación de contenido adicional.

Este servicio lo utiliza internamente el [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

La variable `RemoteContentRendererRequestHandlerServlet` se puede utilizar para configurar la solicitud mediante programación. `DefaultRemoteContentRendererRequestHandlerImpl`, la implementación predeterminada del controlador de solicitud proporcionada, le permite crear varias configuraciones OSGi para asignar una ubicación en la estructura de contenido a un punto final remoto.

Para agregar un controlador de solicitud personalizado, implemente el `RemoteContentRendererRequestHandler` interfaz. Asegúrese de establecer la variable `Constants.SERVICE_RANKING` propiedad component a un entero mayor que 100, que es la clasificación del `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configuración de la configuración OSGi del controlador predeterminado {#configure-default-handler}

La configuración del controlador predeterminado debe configurarse como se describe en la sección [Configuración del procesador de contenido remoto](#remote-content-renderer-configuration).

### Uso del procesador de contenido remoto {#usage}

Para que un servlet recupere y devuelva contenido que se puede insertar en la página:

1. Asegúrese de que el servidor remoto es accesible.
1. Agregue uno de los siguientes fragmentos a la plantilla HTL de un componente AEM.
1. De forma opcional, cree o modifique las configuraciones de OSGi.
1. Explorar el contenido del sitio

Normalmente, la plantilla HTL de un componente de página es el destinatario principal de dicha función.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Requisitos  {#requirements}

Los servlets aprovechan el Exportador del modelo de Sling para serializar los datos del componente. De forma predeterminada, ambas variables `com.adobe.cq.export.json.ContainerExporter` y `com.adobe.cq.export.json.ComponentExporter` son compatibles con los adaptadores del modelo Sling. Si es necesario, puede añadir clases en las que se debe adaptar la solicitud para utilizar la variable `RemoteContentRendererServlet` y la implementación de `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. Las clases adicionales deben ampliar el `ComponentExporter`.
