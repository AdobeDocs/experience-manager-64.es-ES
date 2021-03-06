---
title: Plantillas de fragmento de contenido
seo-title: Plantillas de fragmento de contenido
description: Las plantillas se seleccionan al crear un fragmento de contenido y proporcionan el nuevo fragmento con la estructura básica, el elemento y la variación
seo-description: Las plantillas se seleccionan al crear un fragmento de contenido y proporcionan el nuevo fragmento con la estructura básica, el elemento y la variación
uuid: 74675e82-26b4-4105-8031-21de51131236
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 8c399a27-abdb-41fb-bd76-f30d22f1d68f
translation-type: tm+mt
source-git-commit: 0e1dc3ea47f03cd2e0cbeb2bf98eeec9ccc5d64f
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 5%

---


# Plantillas de fragmento de contenido{#content-fragment-templates}

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

>[!CAUTION]
>
>[Ahora se recomiendan ](/help/assets/content-fragments-models.md) los modelos de fragmentos de contenido para crear todos los fragmentos.
>
>Los modelos de fragmentos de contenido se utilizan en todos los ejemplos de We.Retail.

Las plantillas se seleccionan al crear un fragmento de contenido. Proporcionan al nuevo fragmento la estructura básica, los elementos y la variación. Las plantillas utilizadas para los fragmentos de contenido están sujetas a Granite Configuration Manager.

Las plantillas integradas se incluyen en:

* `/libs/settings/dam/cfm/templates`

Puede crear plantillas específicas del sitio para fragmentos de contenido en:

* `/apps/settings/dam/cfm/templates`

   Ubicación para superponer plantillas listas para usar o proporcionar plantillas específicas para el cliente y para toda la aplicación que no están pensadas para ampliarse o cambiarse en tiempo de ejecución.

* `/conf/global/settings/dam/cfm/templates`

   La ubicación de las plantillas específicas del cliente para toda la instancia que deben cambiarse en tiempo de ejecución.

El orden de prioridad es (en orden descendente) `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>Usted ***no debe*** cambiar nada en la ruta `/libs`.
>
>Esto se debe a que el contenido de `/libs` se sobrescribe la próxima vez que actualice la instancia (y bien puede sobrescribirse al aplicar una revisión o un paquete de funciones).
>
>El método recomendado para la configuración y otros cambios es:
>
>1. Volver a crear el elemento requerido (es decir, tal como existe en `/libs`) en `/apps`
   >
   >
1. Realice cualquier cambio dentro de `/apps`

>



La estructura básica de una plantilla se encuentra en:

```xml
conf
  global
    settings
      dam
        cfm
          templates
            <template-name>
              ...
```

Con una estructura específica:

```xml
+ <template-name>
    - jcr:primaryType
    - jcr:title
    - jcr:description
    - initialAssociatedContent
    - precreateElements
    - version 
    + elements
        - jcr:primaryType
        + <element-name>
            - jcr:primaryType
            - jcr:title 
            - defaultContent 
            - initialContentType 
            - name 
        ... + other element definitions
    + variations
        - jcr:primaryType 
        + <variation-name>
            - jcr:primaryType 
            - jcr:title 
            - jcr:description
            - name 
        ... + other variation definitions 
```

Más detalles sobre los nodos y sus propiedades son:

* **Plantilla**

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Tipo</th> 
   <th>Value</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<em>template-name</em>&gt;</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Este nodo es la raíz de cada plantilla. Es obligatorio y debe tener un nombre único.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>required<br /> </p> </td> 
   <td>Título de la plantilla (se muestra en el asistente para <strong>Crear fragmento</strong>).</td> 
  </tr> 
  <tr> 
   <td><code>jcr:description</code></td> 
   <td><p><code>String</code></p> <p>opcional</p> </td> 
   <td>Texto que describe el propósito de la plantilla (mostrado en el asistente para <strong>Crear fragmento</strong>).</td> 
  </tr> 
  <tr> 
   <td><code>initialAssociatedContent</code></td> 
   <td><p><code>String[]</code></p> <p>opcional</p> </td> 
   <td>Matriz con rutas a colecciones que se deben asociar a un fragmento de contenido recién creado de forma predeterminada.</td> 
  </tr> 
  <tr> 
   <td><code>precreateElements</code></td> 
   <td><p><code>Boolean</code></p> <p>required</p> </td> 
   <td><p><code>true</code>, si los subrecursos que representan los elementos (excepto el elemento maestro) del fragmento de contenido se deben crear al crear el fragmento de contenido; <em>false</em> si deben crearse "sobre la marcha".</p> <p><strong>Nota</strong>: actualmente, este parámetro debe establecerse en  <code>true</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><code>version</code></td> 
   <td><p><code>Long</code></p> <p>requerido</p> </td> 
   <td><p>Versión de la estructura de contenido; compatible actualmente:</p> <p><strong>Nota</strong>: actualmente, este parámetro debe establecerse en  <code>2</code>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

* **Elementos**

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Tipo</th> 
   <th>Valor</th> 
  </tr> 
  <tr> 
   <td><code>elements</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>requerido</p> </td> 
   <td><p>Nodo que contiene la definición de los elementos del fragmento de contenido. Es obligatorio y debe contener al menos un nodo secundario para el elemento <strong>Main</strong>, pero puede contener [1..n] nodos secundarios.</p> <p>Cuando se utiliza la plantilla, la subrama de elementos se copia en la subrama de modelo del fragmento.</p> <p>El primer elemento (como se ve en el CRXDE Lite) se considera automáticamente el elemento <i>principal</i>; el nombre del nodo es irrelevante y el nodo en sí no tiene una importancia especial, aparte del hecho de que está representado por el recurso principal; los demás elementos se gestionan como subrecursos.</p> </td> 
  </tr> 
 </tbody> 
</table>

* **Nombre de elemento**

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Tipo</th> 
   <th>Valor</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<i>element-name</i>&gt;</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Este nodo define un elemento. Es obligatorio y debe tener un nombre único.</td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>requerido</p> </td> 
   <td>Título del elemento (mostrado en el selector de elementos del editor de fragmentos).</td> 
  </tr> 
  <tr> 
   <td><code>defaultContent</code></td> 
   <td><p><code>String</code></p> <p>opcional</p> <p>predeterminada: ""</p> </td> 
   <td>Contenido inicial del elemento; solo se usa si <code>precreateElements</code><i> = </i><code>true</code></td> 
  </tr> 
  <tr> 
   <td><code>initialContentType</code></td> 
   <td><p><code>String</code></p> <p>opcional</p> <p>predeterminada: <code>text/html</code></p> </td> 
   <td><p>Tipo de contenido inicial del elemento; solo se usa si <code>precreateElements</code><i> = </i><code>true</code>; compatible actualmente:</p> 
    <ul> 
     <li><code>text/html</code></li> 
     <li><code>text/plain</code></li> 
     <li><code>text/x-markdown</code></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>name</code></td> 
   <td><p><code>String</code></p> <p>requerido</p> </td> 
   <td>El nombre interno del elemento; debe ser único para el tipo de fragmento.</td> 
  </tr> 
 </tbody> 
</table>

* **Variaciones**

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Tipo</th> 
   <th>Valor</th> 
  </tr> 
  <tr> 
   <td><code>variations</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>opcional</p> </td> 
   <td>Este nodo opcional contiene la definición de las variaciones iniciales del fragmento de contenido.</td> 
  </tr> 
 </tbody> 
</table>

* **Nombre de la variación**

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Tipo</th> 
   <th>Valor</th> 
  </tr> 
  <tr> 
   <td><code>&lt;<i>variation-name</i>&gt;</code> </td> 
   <td><p><code>nt:unstructured</code></p> <p>requerido si hay un nodo de variación presente</p> </td> 
   <td><p>Define una variación inicial.<br /> De forma predeterminada, la variación se agrega a todos los elementos del fragmento de contenido.</p> <p>La variación tendrá el mismo contenido inicial que el elemento correspondiente (consulte <code class="code">defaultContent/
       initialContentType</code>)</p> </td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><p><code>String</code></p> <p>requerido</p> </td> 
   <td>Título de la variación (se muestra en la ficha <strong>Variación</strong> del editor de fragmentos (carril izquierdo)).</td> 
  </tr> 
  <tr> 
   <td><code>jcr:desciption</code></td> 
   <td><p><code>String</code></p> <p>opcional</p> <p>predeterminada: ""</p> </td> 
   <td>Texto que proporciona una descripción de la variación <span> (se muestra en la ficha <strong>Variación</strong> del editor de fragmentos (carril izquierdo)).</span></td> 
  </tr> 
 </tbody> 
</table>

