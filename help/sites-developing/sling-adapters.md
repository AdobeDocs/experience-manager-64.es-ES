---
title: Usar los adaptadores de Sling
seo-title: Usar los adaptadores de Sling
description: Sling ofrece un patrón de adaptador para traducir convenientemente los objetos que implementan la interfaz adaptable
seo-description: Sling ofrece un patrón de adaptador para traducir convenientemente los objetos que implementan la interfaz adaptable
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: dd996d0bb856b9140d420d03dec446a382d10acd
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 1%

---

# Usar los adaptadores de Sling{#using-sling-adapters}

[](https://sling.apache.org) Slingofrece un  [patrón de adaptador ](https://sling.apache.org/site/adapters.html) para traducir convenientemente objetos que implementan la interfaz  [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) Adaptable. Esta interfaz proporciona un método genérico [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) que traducirá el objeto al tipo de clase que se pasa como argumento.

Por ejemplo, para traducir un objeto Resource al objeto Node correspondiente, simplemente puede hacer lo siguiente:

```java
Node node = resource.adaptTo(Node.class);
```

## Casos de uso {#use-cases}

Hay los siguientes casos de uso:

* Obtenga objetos específicos de la implementación.

   Por ejemplo, una implementación basada en JCR de la interfaz genérica [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) proporciona acceso al JCR subyacente [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Creación de accesos directos de objetos que requieren que se pasen objetos de contexto internos.

   Por ejemplo, la [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) basada en JCR contiene una referencia a la [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) de la solicitud, que a su vez es necesaria para muchos objetos que funcionarán en función de esa sesión de solicitud, como [`PageManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) o [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Acceso directo a los servicios.

   Un caso poco frecuente: `sling.getService()` también es sencillo.

### Valor devuelto nulo {#null-return-value}

`adaptTo()` puede devolver null.

Esto se debe a varios motivos, entre ellos:

* la implementación no admite el tipo de destino
* un adaptador que maneje este caso no está activo (p. ej. debido a la ausencia de referencias de servicio)
* error en la condición interna
* el servicio no está disponible

Es importante que gestione las mayúsculas y minúsculas nulas correctamente. Para las renderizaciones jsp, puede ser aceptable que el jsp falle si esto resulta en un fragmento de contenido vacío.

### Almacenamiento en caché {#caching}

Para mejorar el rendimiento, las implementaciones pueden almacenar en caché el objeto devuelto desde una llamada `obj.adaptTo()`. Si `obj` es el mismo, el objeto devuelto es el mismo.

Este almacenamiento en caché se realiza para todos los casos basados en `AdapterFactory`.

Sin embargo, no hay ninguna regla general: el objeto podría ser una instancia nueva o una existente. Esto significa que no puede confiar en ninguno de estos comportamientos. Por lo tanto, es importante, especialmente dentro de `AdapterFactory`, que los objetos se puedan reutilizar en este escenario.

### Cómo funciona {#how-it-works}

Existen varias maneras de implementar `Adaptable.adaptTo()`:

* Por el propio objeto; implementar el propio método y asignar a ciertos objetos.
* Mediante [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), que puede asignar objetos arbitrarios.

   Los objetos deben implementar la interfaz `Adaptable` y deben ampliar [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (que pasa la llamada `adaptTo` a un administrador central de adaptadores).

   Esto permite vincular al mecanismo `adaptTo` para las clases existentes, como `Resource`.

* Una combinación de ambas.

Para el primer caso, los javadocs pueden indicar qué es posible `adaptTo-targets`. Sin embargo, para subclases específicas como el recurso basado en JCR, a menudo esto no es posible. En este último caso, las implementaciones de `AdapterFactory` suelen formar parte de las clases privadas de un paquete y, por lo tanto, no están expuestas en una API de cliente ni están enumeradas en javadocs. Teóricamente, sería posible acceder a todas las implementaciones `AdapterFactory` desde el tiempo de ejecución del servicio [OSGi](/help/sites-deploying/configuring-osgi.md) y observar sus configuraciones &quot;adaptables&quot; (fuentes y destinos), pero no asignarlas entre sí. Al final, esto depende de la lógica interna, que debe documentarse. De ahí esta referencia.

## Referencia {#reference}

### Sling {#sling}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) El recurso se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Si se trata de un recurso basado en nodos JCR o de una propiedad JCR que hace referencia a un nodo.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Propiedad</a></td> 
   <td>Si se trata de un recurso basado en propiedades JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Elemento</a></td> 
   <td>Si se trata de un recurso basado en JCR (nodo o propiedad).</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Asignar</a></td> 
   <td>Devuelve un mapa de las propiedades, si se trata de un recurso basado en nodos JCR (u otro recurso que admita mapas de valores).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>Devuelve un mapa práctico de las propiedades, si se trata de un recurso basado en nodos JCR (u otros mapas de valores compatibles con recursos). También se puede lograr (más simplemente) utilizando<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (gestiona mayúsculas y minúsculas nulas, etc.).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td>Extensión de <a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> que permite tener en cuenta la jerarquía de recursos al buscar propiedades.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>Si se trata de un recurso basado en nodos JCR y el usuario tiene permisos para modificar propiedades en ese nodo.<br /> Nota: varios mapas persistentes no comparten sus valores.</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>Devuelve el contenido binario de un "archivo"<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) ResourceResolveradapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sesión</a></td> 
   <td>La sesión JCR de la solicitud, si se trata de una resolución de recursos basada en JCR (predeterminada).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Diseñador</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>En función de la sesión JCR, si se trata de una resolución de recursos basada en JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>En función de la sesión JCR, si se trata de una resolución de recursos basada en JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>En función de la sesión JCR, si se trata de una resolución de recursos basada en JCR y si el usuario tiene permisos para acceder a UserManager.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Con autorización</a> </td> 
   <td>El usuario actual.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">Usuario</a><br /> </td> 
   <td>El usuario actual.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">PrivilegeManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">Preferencias</a></td> 
   <td>Preferencias del usuario actual (basadas en la sesión JCR si se trata de una resolución de recursos basada en JCR).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">Servicios de preferencias</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">Externalizador</a></td> 
   <td>Para externalizar direcciones URL absolutas, incluso sin el objeto de solicitud.<br /> </td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequestadapta a:

Aún no hay destinos, pero implementa Adaptable y podría utilizarse como fuente en una fábrica de adaptadores personalizada.

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponseadapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br />  (XML)</td> 
   <td>Si se trata de una respuesta de reescritura de Sling.</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) La página se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Medio</a><br /> </td> 
   <td>Recurso de la página.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">EtiquetadoRecurso</a></td> 
   <td>Recurso etiquetado (= esto).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Nodo de la página.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Todo a lo que se puede adaptar el recurso de la página.</td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) Los componentes se adaptan a:

| [Medio](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso del componente. |
|---|---|
| [EtiquetadoRecurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Recurso etiquetado (= esto). |
| [Nodo](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del componente. |
| ... | Todo a lo que se puede adaptar el recurso del componente. |

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) La plantilla se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Recurso</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>Recurso de la plantilla.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">EtiquetadoRecurso</a></td> 
   <td>Recurso etiquetado (= esto).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Nodo de esta plantilla.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Todo a lo que se puede adaptar el recurso de la plantilla.</td> 
  </tr> 
 </tbody> 
</table>

#### Seguridad {#security}

[**Autorizable**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html),  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) Usuario y  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) Grupo se adaptan a:

| [Nodo](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Devuelve el nodo principal del usuario/grupo. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Devuelve el estado de replicación del nodo principal del usuario/grupo. |

#### DAM  {#dam}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) Assets se adapta a:

| [Medio](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso del recurso. |
|---|---|
| [Nodo](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del recurso. |
| ... | Todo a lo que se puede adaptar el recurso del recurso. |

#### Etiquetado {#tagging}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) Target se adapta a:

| [Medio](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso de la etiqueta. |
|---|---|
| [Nodo](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo de la etiqueta. |
| ... | Todo a lo que se puede adaptar el recurso de la etiqueta. |

#### Otras {#other}

Además, Sling / JCR / OCM también proporciona un ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` para objetos OCM personalizados ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)).
