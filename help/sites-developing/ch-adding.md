---
title: Añadir ContextHub en páginas y acceder a tiendas
seo-title: Añadir ContextHub en páginas y acceder a tiendas
description: Añada ContextHub en sus páginas para habilitar las funciones de ContextHub y vincular a las bibliotecas de Javascript de ContextHub
seo-description: Añada ContextHub en sus páginas para habilitar las funciones de ContextHub y vincular a las bibliotecas de Javascript de ContextHub
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---


# Añadir ContextHub en páginas y acceder a tiendas {#adding-contexthub-to-pages-and-accessing-stores}

Añada ContextHub en sus páginas para habilitar las funciones de ContextHub y vincular a las bibliotecas de Javascript de ContextHub

La API de JavaScript de ContextHub proporciona acceso a los datos de contexto que administra ContextHub. En esta página se describen brevemente las principales funciones de la API para acceder a los datos de contexto y manipularlos. Siga los vínculos a la documentación de referencia de la API para ver información detallada y ejemplos de código.

## Añadir ContextHub en un componente de página {#adding-contexthub-to-a-page-component}

Para habilitar las funciones de ContextHub y vincular a las bibliotecas de Javascript de ContextHub, incluya el componente contexthub en la `head` sección de la página. El código JSP del componente de página es similar al siguiente ejemplo:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Tenga en cuenta que también debe configurar si la barra de herramientas de ContextHub aparece en modo de Previsualización. Consulte [Mostrar y ocultar la interfaz de usuario](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui)de ContextHub.

## Acerca de las tiendas de ContextHub {#about-contexthub-stores}

Utilice los almacenes de ContextHub para conservar los datos de contexto. ContextHub proporciona los siguientes tipos de tiendas que forman la base de todos los tipos de tiendas:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Todos los tipos de tienda son extensiones de la [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) clase. Para obtener información sobre la creación de un nuevo tipo de almacén, consulte [Creación de tiendas](/help/sites-developing/ch-extend.md#creating-custom-store-candidates)personalizadas. Para obtener información sobre los tipos de almacén de muestra, consulte [Ejemplo de candidatos a la tienda de ContextHub](/help/sites-developing/ch-samplestores.md).

### Modos de persistencia {#persistence-modes}

Las tiendas de Context Hub utilizan uno de los siguientes modos de persistencia:

* **Local:** Utiliza el almacenamiento local de HTML5 para conservar los datos. El almacenamiento local se mantiene en el navegador en todas las sesiones.
* **Sesión:** Utiliza sessionStorage de HTML5 para conservar los datos. El almacenamiento de sesión se mantiene durante toda la sesión del explorador y está disponible para todas las ventanas del explorador.
* **Cookie:** Utiliza la compatibilidad nativa del explorador con las cookies para el almacenamiento de datos. Los datos de cookies se envían desde y hacia el servidor en solicitudes HTTP.
* **Window.name:** Utiliza la propiedad window.name para conservar los datos.
* **Memoria:** Utiliza un objeto Javascript para conservar datos.

De forma predeterminada, Context Hub utiliza el modo de persistencia local. Si el explorador no admite o no permite el almacenamiento local de HTML5, se utiliza la persistencia de sesión. Si el navegador no admite o no permite HTML5 sessionStorage, se utiliza la persistencia Window.name.

### Almacenar datos {#store-data}

Internamente, el almacenamiento de datos forma una estructura de árbol, lo que permite agregar valores como tipos primarios u objetos complejos. Cuando se agregan objetos complejos a los almacenes, las propiedades del objeto se ramifican en el árbol de datos. Por ejemplo, se agrega el siguiente objeto complejo a una tienda vacía denominada location:

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

La estructura de árbol de los datos del almacén se puede conceptualizar de la siguiente manera:

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

La estructura de árbol define los elementos de datos del almacén como pares clave/valor. En el ejemplo anterior, la clave `/number` corresponde al valor `321`, y la clave `/data/country` corresponde al valor `Switzerland`.

### Manipulación de objetos {#manipulating-objects}

ContextHub proporciona la [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) clase para manipular objetos de JavaScript. Utilice las funciones de esta clase para manipular objetos de JavaScript antes de agregarlos a una tienda o después de obtenerlos de una tienda.

Además, la [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) clase proporciona funciones para serializar objetos en cadenas y deserializar cadenas en objetos. Utilice esta clase para gestionar datos JSON para admitir exploradores que no incluyen de forma nativa las `JSON.parse` funciones y `JSON.stringify` .

## Interacción con las tiendas de ContextHub {#interacting-with-contexthub-stores}

Utilice el objeto [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) Javascript para obtener una tienda como objeto Javascript. Una vez obtenido el objeto store, puede manipular los datos que contiene. Utilice la [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) función o la [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) para obtener la tienda.

### Acceso a los datos del almacén {#accessing-store-data}

La clase [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Javascript define varias funciones para interactuar con los datos del almacén. Las siguientes funciones almacenan y recuperan varios elementos de datos contenidos en objetos:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Los elementos de datos individuales se almacenan como un conjunto de pares clave/valor. Para almacenar y recuperar valores, especifique la clave correspondiente:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Tenga en cuenta que los candidatos del almacén personalizado pueden definir funciones adicionales que proporcionan acceso para almacenar datos.

>[!NOTE]
>
>De forma predeterminada, ContextHub no tiene en cuenta el inicio de sesión que se está usando en los servidores de publicación y ContextHub considera a estos usuarios como &quot;anónimos&quot;.
>
>Puede hacer que ContextHub conozca a los usuarios que iniciaron sesión cargando la tienda de perfiles tal como se implementó en el sitio [de referencia](/help/sites-developing/we-retail.md)We.Retail. Consulte el código [relevante en GitHub aquí](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Evento de ContextHub {#contexthub-eventing}

ContextHub incluye una estructura de evento que le permite reaccionar automáticamente a los eventos de la tienda. Cada objeto store contiene un [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) objeto que está disponible como [`eventing`](/help/sites-developing/contexthub-api.md#eventing) propiedad del almacén. Utilice la función [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) o [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) para enlazar una función de Javascript a un evento de almacenamiento.

## Uso de Context Hub para manipular cookies {#using-context-hub-to-manipulate-cookies}

La API de JavaScript de Context Hub proporciona compatibilidad con distintos exploradores para la gestión de cookies de navegador. La [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) Área de nombres define varias funciones para crear, manipular y eliminar cookies.

## Determinación de segmentos de ContextHub resueltos {#determining-resolved-contexthub-segments}

El motor de segmentos de ContextHub permite determinar qué segmentos registrados se resuelven en el contexto actual. Utilice la función getResolvedSegments de la [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) clase para recuperar segmentos resueltos. A continuación, utilice la `getName` función o `getPath` de la [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) clase para probar un segmento.

### Segmentos instalados {#installed-segments}

Los segmentos de ContextHub se instalan debajo del `/conf/we-retail/settings/wcm/segments` nodo.

* femenino
* hembra sobre 30
* hembra menor de 30 años
* masculino
* macho sobre 30
* macho menor de 30 años
* order-value-75-to-100
* order-value-over-100
* más de 30
* verano
* verano-mujer
* verano-mujer-sobre-30
* verano-mujer-menor de 30 años
* verano (hombre)
* verano-hombre-sobre-30
* verano-hombre-menor de 30 años
* menor de 30 años
* invierno
* invierno-mujer
* invierno-mujer-sobre-30
* invierno-mujer-menor de 30 años
* invierno masculino
* invierno-hombre-sobre-30
* invierno-hombre-menor de 20 años

Las reglas que se utilizan para resolver estos segmentos se resumen de la siguiente manera:

* Las mujeres o los hombres se determinan a partir del elemento de `gender` datos del almacén de [perfiles](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) .

* La edad se determina a partir del elemento de datos de edad del almacén de perfiles.
* La estación se determina a partir del elemento de datos de latitud del [almacén de geolocalización](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) y del elemento de datos del mes del almacén de surferinfo.

>[!WARNING]
>
>Los segmentos instalados se proporcionan como configuraciones de referencia para ayudarle a crear su propia configuración dedicada para su proyecto y, como tal, no debe utilizarse directamente.

## Registro de mensajes de depuración para ContextHub {#logging-debug-messages-for-contexthub}

Configure el servicio OSGi de ContextHub de Adobe Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) para registrar mensajes de depuración detallados que sean útiles para el desarrollo.

Para configurar el servicio, puede utilizar la consola [](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) web o un nodo [JCR en el repositorio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Consola web: Para registrar mensajes de depuración, seleccione la propiedad Debug.
* Nodo JCR: Para registrar mensajes de depuración, establezca la propiedad booleana `com.adobe.granite.contexthub.debug` en `true`.

## Vea una descripción general de ContextHub Framework {#see-an-overview-of-the-contexthub-framework}

ContextHub proporciona una página [de](/help/sites-developing/ch-diagnostics.md) diagnóstico en la que puede ver información general sobre el marco de ContextHub.
