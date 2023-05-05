---
title: Agregar ContextHub a páginas y acceder a tiendas
seo-title: Adding ContextHub to Pages and Accessing Stores
description: Agregue ContextHub a sus páginas para habilitar las funciones de ContextHub y vincular a las bibliotecas JavaScript de ContextHub
seo-description: Add ContextHub to your pages to enable the ContextHub features and to link to the ContextHub Javascript libraries
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# Agregar ContextHub a páginas y acceder a tiendas {#adding-contexthub-to-pages-and-accessing-stores}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Agregue ContextHub a sus páginas para habilitar las funciones de ContextHub y vincular a las bibliotecas JavaScript de ContextHub

La API de JavaScript de ContextHub proporciona acceso a los datos de contexto que administra ContextHub. En esta página se describen brevemente las principales funciones de la API para acceder y manipular los datos de contexto. Siga los vínculos a la documentación de referencia de la API para ver información detallada y ejemplos de código.

## Adición de ContextHub a un componente de página {#adding-contexthub-to-a-page-component}

Para habilitar las funciones de ContextHub y vincular a las bibliotecas de JavaScript de ContextHub, incluya el componente contexthub en la `head` de su página. El código JSP del componente de página se parece al siguiente ejemplo:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Tenga en cuenta que también debe configurar si la barra de herramientas de ContextHub aparece en el modo de vista previa. Consulte [Mostrar y ocultar la interfaz de usuario de ContextHub](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Acerca de las tiendas de ContextHub {#about-contexthub-stores}

Utilice los almacenes de ContextHub para conservar los datos de contexto. ContextHub proporciona los siguientes tipos de tiendas que forman la base de todos los tipos de tiendas:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Todos los tipos de tienda son extensiones de [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Clase . Para obtener información sobre la creación de un nuevo tipo de almacén, consulte [Creación de tiendas personalizadas](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Para obtener información sobre los tipos de almacén de muestra, consulte [Ejemplos de candidatos a la tienda de ContextHub](/help/sites-developing/ch-samplestores.md).

### Modos de persistencia {#persistence-modes}

Los almacenes de ContextHub utilizan uno de los siguientes modos de persistencia:

* **Local:** Utiliza HTML5 localStorage para mantener los datos. El almacenamiento local se mantiene en el explorador en todas las sesiones.
* **Sesión:** Utiliza sessionStorage de HTML5 para mantener los datos. El almacenamiento de sesión se mantiene durante la sesión del explorador y está disponible para todas las ventanas del explorador.
* **Cookie:** Utiliza la compatibilidad nativa de cookies del explorador para el almacenamiento de datos. Los datos de cookies se envían desde y hacia el servidor en solicitudes HTTP.
* **Window.name:** Utiliza la propiedad window.name para mantener los datos.
* **Memoria:** Utiliza un objeto Javascript para mantener los datos.

De forma predeterminada, ContextHub utiliza el modo de persistencia local. Si el explorador no admite o no permite HTML5 localStorage, se utiliza la persistencia de sesión. Si el explorador no admite o no permite HTML5 sessionStorage, se utiliza la persistencia Window.name.

### Almacenar datos {#store-data}

Internamente, el almacenamiento de datos forma una estructura de árbol, que permite agregar valores como tipos primarios u objetos complejos. Cuando se agregan objetos complejos a los almacenes, las propiedades de objeto forman ramas en el árbol de datos. Por ejemplo, el siguiente objeto complejo se agrega a una ubicación de almacén vacía denominada:

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

La estructura de árbol define los elementos de datos del almacén como pares clave/valor. En el ejemplo anterior, la clave `/number` corresponde al valor `321`y la clave `/data/country` corresponde al valor `Switzerland`.

### Manipulación de objetos {#manipulating-objects}

ContextHub proporciona [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) para manipular objetos de JavaScript. Utilice las funciones de esta clase para manipular objetos de JavaScript antes de agregarlos a una tienda o después de obtenerlos de una tienda.

Además, la variable [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) proporciona funciones para serializar objetos en cadenas y deserializar cadenas en objetos. Utilice esta clase para gestionar datos JSON para admitir exploradores que no incluyan de forma nativa el `JSON.parse` y `JSON.stringify` funciones.

## Interactuar con las tiendas de ContextHub {#interacting-with-contexthub-stores}

Utilice la variable [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) Objeto Javascript para obtener un almacén como objeto Javascript. Una vez obtenido el objeto de almacén, puede manipular los datos que contiene. Utilice la variable [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) o [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) para obtener el almacén.

### Acceso a los datos del almacén {#accessing-store-data}

La variable [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) La clase Javascript define varias funciones para interactuar con datos de almacenamiento. Las siguientes funciones almacenan y recuperan varios elementos de datos contenidos en objetos:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Los elementos de datos individuales se almacenan como un conjunto de pares clave/valor. Para almacenar y recuperar valores, especifique la clave correspondiente:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Tenga en cuenta que los candidatos de tiendas personalizadas pueden definir funciones adicionales que proporcionan acceso a los datos de almacenamiento.

>[!NOTE]
>
>De forma predeterminada, ContextHub no tiene en cuenta el inicio de sesión que se está utilizando en los servidores de publicación y ContextHub considera a estos usuarios como &quot;anónimos&quot;.
>
>Puede hacer que ContextHub sepa de los usuarios que iniciaron sesión cargando el almacén de perfiles tal como se implementa en la variable [Sitio de referencia de We.Retail](/help/sites-developing/we-retail.md). Consulte la [código relevante en GitHub aquí](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Eventos de ContextHub {#contexthub-eventing}

ContextHub incluye un marco de eventos que le permite reaccionar automáticamente al almacenar eventos. Cada objeto de almacén contiene un [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) objeto que está disponible como [`eventing`](/help/sites-developing/contexthub-api.md#eventing) propiedad. Utilice la variable [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) o [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) para enlazar una función de JavaScript a un evento de tienda.

## Uso de ContextHub para manipular cookies {#using-context-hub-to-manipulate-cookies}

La API de JavaScript de Context Hub proporciona compatibilidad con exploradores múltiples para administrar cookies de exploradores. La variable [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) namespace define varias funciones para crear, manipular y eliminar cookies.

## Determinación de segmentos de ContextHub resueltos {#determining-resolved-contexthub-segments}

El motor de segmentos de ContextHub permite determinar cuál de los segmentos registrados se resuelve en el contexto actual. Utilice la función getResolvedSegments de la función [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) para recuperar segmentos resueltos. A continuación, utilice el `getName` o `getPath` de la función [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) para probar un segmento.

### Segmentos instalados {#installed-segments}

Los segmentos de ContextHub se instalan debajo de `/conf/we-retail/settings/wcm/segments` nodo .

* femenino
* mujer sobre 30
* hembra menor de 30 años
* masculino
* macho sobre 30
* varón menor de 30 años
* order-value-75-to-100
* order-value-over-100
* más de 30
* verano
* mujer de verano
* verano-mujer-sobre-30
* verano-mujer-menor de 30 años
* verano masculino
* verano-hombre-sobre-30
* verano-hombre-menor de 30 años
* menor de 30 años
* invierno
* hembra de invierno
* invierno-mujer-más-30
* invierno-mujer-menor de 30 años
* invierno masculino
* winter-male-over-30
* invierno-hombre-menor de 20 años

Las reglas que se utilizan para resolver estos segmentos se resumen de la siguiente manera:

* El hombre o la mujer se determina a partir del `gender` elemento de datos del [perfil](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) tienda.

* La edad se determina a partir del elemento de datos age del almacén de perfiles.
* La estación se determina a partir del elemento de datos de latitud del [geolocalización](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) y el elemento de datos del mes del almacén de surferinfo.

>[!WARNING]
>
>Los segmentos instalados se proporcionan como configuraciones de referencia para ayudarle a crear su propia configuración dedicada para su proyecto y, como tal, no debe utilizarse directamente.

## Registro de mensajes de depuración para ContextHub {#logging-debug-messages-for-contexthub}

Configuración del servicio OSGi de ContextHub de Adobe Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) para registrar mensajes de depuración detallados que sean útiles para el desarrollo.

Para configurar el servicio, puede utilizar el [Consola web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o use un [Nodo JCR en el repositorio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Consola web: Para registrar mensajes de depuración, seleccione la propiedad Debug .
* Nodo JCR: Para registrar mensajes de depuración, establezca el booleano `com.adobe.granite.contexthub.debug` propiedad a `true`.

## Consulte Información general sobre el marco de ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub proporciona un [página de diagnóstico](/help/sites-developing/ch-diagnostics.md) donde puede ver información general del marco de ContextHub.
