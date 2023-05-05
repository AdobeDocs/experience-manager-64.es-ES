---
title: Uso de los adaptadores de Sling
seo-title: Using Sling Adapters
description: Sling ofrece un patrón de adaptador para traducir convenientemente los objetos que implementan la interfaz adaptable
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 15%

---

# Uso de los adaptadores de Sling{#using-sling-adapters}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[Sling](https://sling.apache.org) ofrece un [Patrón de adaptador](https://sling.apache.org/site/adapters.html) para traducir convenientemente los objetos que implementan la variable [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) interfaz. Esta interfaz proporciona un [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) método que traducirá el objeto al tipo de clase que se pasa como argumento.

Por ejemplo, para traducir un objeto Resource al objeto Node correspondiente, simplemente puede hacer lo siguiente:

```java
Node node = resource.adaptTo(Node.class);
```

## Casos de uso {#use-cases}

Hay los siguientes casos de uso:

* Obtenga objetos específicos de la implementación.

   Por ejemplo, una implementación basada en JCR del [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) La interfaz de proporciona acceso al JCR subyacente [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Creación de accesos directos de objetos que requieren que se pasen objetos de contexto internos.

   Por ejemplo, la [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) contiene una referencia al [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), que a su vez es necesario para muchos objetos que funcionarán en función de esa sesión de solicitud, como el [`PageManager`](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) o [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Acceso directo a los servicios.

   Un caso poco frecuente: `sling.getService()` también es simple.

### Valor devuelto nulo {#null-return-value}

`adaptTo()` puede devolver null.

Esto se debe a varios motivos, entre ellos:

* la implementación no admite el tipo de destino
* un adaptador que maneje este caso no está activo (p. ej. debido a la ausencia de referencias de servicio)
* error en la condición interna
* el servicio no está disponible

Es importante que gestione las mayúsculas y minúsculas nulas correctamente. Para las renderizaciones jsp, puede ser aceptable que el jsp falle si esto resulta en un fragmento de contenido vacío.

### Almacenamiento en caché {#caching}

Para mejorar el rendimiento, las implementaciones pueden almacenar en caché el objeto devuelto desde un `obj.adaptTo()` llamada a . Si la variable `obj` es el mismo, el objeto devuelto es el mismo.

Este almacenamiento en caché se realiza para todas las `AdapterFactory` casos basados en .

Sin embargo, no hay ninguna regla general: el objeto podría ser una instancia nueva o una existente. Esto significa que no puede confiar en ninguno de estos comportamientos. Por lo tanto, es importante, especialmente dentro `AdapterFactory`, que los objetos se pueden reutilizar en este escenario.

### Funcionamiento {#how-it-works}

Hay varias maneras de que `Adaptable.adaptTo()` se puede implementar:

* Por el propio objeto; implementar el propio método y asignar a ciertos objetos.
* De [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), que puede asignar objetos arbitrarios.

   Los objetos deben implementar la variable `Adaptable` interfaz y debe ampliar [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (que pasa el `adaptTo` a un administrador central de adaptadores).

   Esto permite los enlaces en la variable `adaptTo` mecanismo para las clases existentes, como `Resource`.

* Una combinación de ambas.

Para el primer caso, los javadocs pueden indicar qué `adaptTo-targets` son posibles. Sin embargo, para subclases específicas como el recurso basado en JCR, a menudo esto no es posible. En este último caso, las implementaciones de `AdapterFactory` normalmente forman parte de las clases privadas de un paquete y, por lo tanto, no están expuestas en una API de cliente ni están enumeradas en javadocs. En teoría, sería posible acceder a todas las `AdapterFactory` implementaciones de [OSGi](/help/sites-deploying/configuring-osgi.md) tiempo de ejecución del servicio y observe sus configuraciones &quot;adaptables&quot; (fuentes y destinos), pero no para asignarlas entre sí. Al final, esto depende de la lógica interna, que debe documentarse. De ahí esta referencia.

## Referencia {#reference}

### Sling {#sling}

[**Recurso**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Si se trata de un recurso basado en nodos JCR o de una propiedad JCR que hace referencia a un nodo.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Propiedad</a></td> 
   <td>Si se trata de un recurso basado en propiedades JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Elemento</a></td> 
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

[**ResourceResolver**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sesión</a></td> 
   <td>La sesión JCR de la solicitud, si se trata de una resolución de recursos basada en JCR (predeterminada).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
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
   <td>Para externalizar direcciones URL absolutas, incluso con el objeto de solicitud .<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequest**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) se adapta a:

Aún no hay destinos, pero implementa Adaptable y podría utilizarse como fuente en una fábrica de adaptadores personalizada.

[**SlingHttpServletResponse**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>Si se trata de una respuesta de reescritura de Sling.</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**Página**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td> 
   <td>Recurso de la página.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">EtiquetadoRecurso</a></td> 
   <td>Recurso etiquetado (= esto).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Nodo de la página.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Todo a lo que se puede adaptar el recurso de la página.</td> 
  </tr> 
 </tbody> 
</table>

[**Componente**](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) se adapta a:

| [Resource](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso del componente. |
|---|---|
| [EtiquetadoRecurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Recurso etiquetado (= esto). |
| [Nodo](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del componente. |
| ... | Todo a lo que se puede adaptar el recurso del componente. |

[**Plantilla**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>Recurso de la plantilla.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">EtiquetadoRecurso</a></td> 
   <td>Recurso etiquetado (= esto).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nodo</a></td> 
   <td>Nodo de esta plantilla.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Todo a lo que se puede adaptar el recurso de la plantilla.</td> 
  </tr> 
 </tbody> 
</table>

#### Seguridad {#security}

[**Autorizable**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html), [**Usuario**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) y [**Grupo**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) adaptarse a:

| [Nodo](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Devuelve el nodo principal del usuario/grupo. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Devuelve el estado de replicación del nodo principal del usuario/grupo. |

#### DAM  {#dam}

[**Activo**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) se adapta a:

| [Resource](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso del recurso. |
|---|---|
| [Nodo](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del recurso. |
| ... | Todo a lo que se puede adaptar el recurso del recurso. |

#### Etiquetado {#tagging}

[**Etiqueta**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) se adapta a:

| [Resource](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso de la etiqueta. |
|---|---|
| [Nodo](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo de la etiqueta. |
| ... | Todo a lo que se puede adaptar el recurso de la etiqueta. |

#### Otro {#other}

Además, Sling / JCR / OCM también proporciona un ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` para OCM personalizado ([Asignación de contenido de objeto](https://jackrabbit.apache.org/object-content-mapping.html)).
