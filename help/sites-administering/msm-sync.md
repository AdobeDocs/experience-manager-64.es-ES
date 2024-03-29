---
title: Configuración de la sincronización de Live Copy
seo-title: Configuring Live Copy Synchronization
description: Obtenga más información sobre la configuración de la sincronización de Live Copy.
seo-description: Learn about configuring Live Copy Synchronization.
uuid: a14fab89-fd1c-4fec-a9e0-9f6511f764a6
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c491f0f3-375d-4203-bdf3-234987bbf685
feature: Multi Site Manager
exl-id: 42b92993-abde-4ae4-8f0d-44166a3ea22e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2731'
ht-degree: 28%

---

# Configuración de la sincronización de Live Copy{#configuring-live-copy-synchronization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Realice las siguientes tareas para controlar cómo y cuándo se sincronizan las copias en vivo con el contenido de origen.

* Decida si las configuraciones de lanzamiento existentes cumplen los requisitos o si necesita crear una o más.
* Especifique las opciones de configuración de lanzamiento que se utilizarán para las Live Copies.

## Configuraciones de lanzamiento personalizadas e instaladas {#installed-and-custom-rollout-configurations}

Esta sección proporciona información sobre las configuraciones de lanzamiento instaladas y las acciones de sincronización que utilizan, así como sobre cómo crear configuraciones personalizadas si es necesario.

>[!CAUTION]
>
>La actualización o el cambio de una configuración de lanzamiento predeterminada (instalada) es **not** recomendado. Si hay algún requisito para una acción en directo personalizada, debe añadirse en una configuración de despliegue personalizada.

### Desplegar Déclencheur {#rollout-triggers}

Cada configuración de lanzamiento utiliza un activador de lanzamiento que hace que se produzca el lanzamiento. Las configuraciones de lanzamiento pueden utilizar uno de los siguientes déclencheur:

* **Al despliegue**: La variable **Despliegue** se utiliza en la página de impresión azul o en la página de **Sincronizar** se utiliza en la página Live Copy.

* **En la modificación**: la página de origen se modifica.

* **En la activación**: la página de origen se activa.

* **En la desactivación**: la página de origen se desactiva.

>[!NOTE]
>
>Recuerde que el uso del activador En la modificación puede afectar al rendimiento. Consulte [las prácticas recomendadas de MSM](/help/sites-administering/msm-best-practices.md#onmodify) para obtener más información.

### Configuraciones de lanzamiento instaladas {#installed-rollout-configurations}

En la tabla siguiente se enumeran las configuraciones de lanzamiento que se instalan con AEM. La tabla incluye las acciones de activación y sincronización de cada configuración de lanzamiento. Si las acciones de configuración de lanzamiento instaladas no cumplen sus requisitos, puede [crear una nueva configuración de lanzamiento](#creating-a-rollout-configuration).

<table> 
 <tbody> 
  <tr> 
   <th>Nombre</th> 
   <th>Descripción</th> 
   <th>Activador</th> 
   <th>Acciones de sincronización<br /> <br /> consulte también <a href="#installed-synchronization-actions">Acciones de sincronización instaladas</a></th> 
  </tr> 
  <tr> 
   <td>Configuración de lanzamiento estándar</td> 
   <td>La configuración de lanzamiento estándar permite iniciar procesos de lanzamiento con el activador de lanzamientos, y ejecuta acciones como crear, actualizar, eliminar contenido y ordenar nodos secundarios.</td> 
   <td>En el despliegue</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> ReferencesUpdate<br /> productUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Activar si se activa el modelo</td> 
   <td>Publica la Live Copy cuando se publica el origen.</td> 
   <td>En la activación</td> 
   <td>targetActivate</td> 
  </tr> 
  <tr> 
   <td>Desactivar si se desactiva el modelo</td> 
   <td>Desactiva la Live Copy cuando se desactiva el origen.</td> 
   <td>Al desactivar</td> 
   <td>targetDeactivate<br /> </td> 
  </tr> 
  <tr> 
   <td>Insertar al modificar</td> 
   <td><p>Inserta el contenido en la Live Copy cuando se modifica el origen.</p> <p>Utilice esta configuración de lanzamiento con moderación, ya que utiliza el déclencheur On Modification .</p> </td> 
   <td>En la modificación</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> ReferencesUpdate<br /> orderChildren<br /> </td> 
  </tr> 
  <tr> 
   <td>Insertar al modificar (superficial)</td> 
   <td><p>Inserta el contenido en la Live Copy cuando se modifica la página del modelo, sin actualizar las referencias (por ejemplo, para copias superficiales).</p> <p>Utilice esta configuración de lanzamiento con moderación, ya que utiliza el déclencheur On Modification .</p> </td> 
   <td>En la modificación</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Promocionar lanzamiento</td> 
   <td>Configuración de lanzamiento estándar para promocionar páginas con dicho fin.</td> 
   <td>En el despliegue</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> ReferencesUpdate<br /> orderChildren<br /> markLiveRelationship</td> 
  </tr> 
  <tr> 
   <td>Configuración del lanzamiento del contenido de la página del catálogo</td> 
   <td>Aplica plantillas de página de un modelo de catálogo.</td> 
   <td>En el despliegue</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> ReferencesUpdate<br /> productCreateUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Configuración de despliegue de actualización de la página del catálogo</td> 
   <td>Aplica propiedades de destino de un modelo de catálogo. Debe ejecutarse después de la configuración de lanzamiento del contenido de la página del catálogo.</td> 
   <td>En el despliegue</td> 
   <td>catalogRolloutHooks</td> 
  </tr> 
  <tr> 
   <td>Configuración de despliegue de publicaciones de DPS</td> 
   <td>La configuración de lanzamiento de publicación de DPS permite iniciar el proceso de implementación en el déclencheur de lanzamiento, al mismo tiempo que se excluyen las propiedades de enlace de FolioProducer en el lanzamiento inicial</td> 
   <td>En el despliegue</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> ReferencesUpdate<br /> orderChildren<br /> dpsMetadataFilter</td> 
  </tr> 
  <tr> 
   <td>Configuración de lanzamiento de catálogo heredada (5.6.0)</td> 
   <td>Obsoleto. Use el generador de catálogos en lugar de los medios convencionales para los lanzamientos de catálogos.</td> 
   <td>En el despliegue</td> 
   <td>editProperties</td> 
  </tr> 
 </tbody> 
</table>

### Acciones de sincronización instaladas {#installed-synchronization-actions}

En la tabla siguiente se enumeran las acciones de sincronización que se instalan con AEM. Si las acciones instaladas no cumplen los requisitos, puede [Crear una nueva acción de sincronización](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).

<table> 
 <tbody> 
  <tr> 
   <th>Nombre de la acción</th> 
   <th>Descripción</th> 
   <th>Propiedades<br /> </th> 
  </tr> 
  <tr> 
   <td>contentCopy</td> 
   <td>Cuando los nodos del origen no existen en la Live Copy, los copia en la Live Copy. <a href="#excluding-properties-and-node-types-from-synchronization">Configure el servicio de acción de copia de contenido de CQ MSM</a> para especificar los tipos de nodo, los elementos de párrafo y las propiedades de página que se excluirán. <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentDelete</td> 
   <td><p>Elimina los nodos de la Live Copy que no existen en el origen. <a href="#excluding-properties-and-node-types-from-synchronization">Configure el servicio de acción de eliminación de contenido de CQ MSM</a> para especificar los tipos de nodo, los elementos de párrafo y las propiedades de página que se excluirán. </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentUpdate</td> 
   <td>Actualiza el contenido de la Live Copy con los cambios del origen. <a href="#excluding-properties-and-node-types-from-synchronization">Configure el servicio de acción de actualización de contenido de CQ MSM</a> para especificar los tipos de nodo, los elementos de párrafo y las propiedades de página que se excluirán. <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>editProperties</td> 
   <td><p>Edita las propiedades de la Live Copy. La propiedad editMap determina qué propiedades se editan y su valor. El valor de la propiedad editMap debe utilizar el siguiente formato:</p> <p><code>[property_name_1]#[current_value]#</code>[new_value],<br /> <code>[property_name_2]#[current_value]#</code>[new_value],<br /> ... ,<br /> <code>[property_name_n]#[current_value]#</code>[new_value]</p> <p>La variable <code>current_value</code> y <code>new_value</code> los elementos son expresiones regulares. <br /> </p> <p>Por ejemplo, considere el siguiente valor para editMap:</p> <p><code>sling:resourceType#/</code>(contentpage|homepage)#/<br /> mobilecontentpage,<br /> cq:template#/contentpage#/mobilecontentpage</p> <p>Este valor edita las propiedades de los nodos de Live Copy de la siguiente manera:</p> 
    <ul> 
     <li>La variable <code>sling:resourceType</code> propiedades que se establecen como <code>contentpage</code> o <code>homepage</code> están configurados en <code>mobilecontentpage.</code></li> 
     <li>Las propiedades <code>cq:template</code> definidas en <code>contentpage</code> se establecen como <code>mobilecontentpage.</code></li> 
    </ul> </td> 
   <td><p> </p> <p>editMap: (Cadena) Identifica la propiedad, el valor actual y el nuevo valor. Consulte la Descripción para obtener más información.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>notify</td> 
   <td>Envía un evento de página que indica que la página se ha desplegado. Para recibir notificaciones, primero debe suscribirse a eventos de lanzamiento.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>orderChildren</td> 
   <td>En la Live Copy, ordena los elementos secundarios (nodos) según el orden del modelo<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ReferencesUpdate</td> 
   <td><p>En la Live Copy, esta acción de sincronización actualiza referencias como vínculos.<br /> Busca rutas en las páginas de Live Copy que apuntan a un recurso dentro del modelo. Cuando se encuentra, actualiza la ruta de acceso para que apunte al recurso relacionado dentro de la Live Copy (en lugar del modelo). Las referencias que tienen los destinos fuera del modelo no cambian.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">Configure el servicio de acción de actualización de referencias de CQ MSM</a> para especificar los tipos de nodo, los elementos de párrafo y las propiedades de página que se excluirán. </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetVersion</td> 
   <td><p>Crea una versión de la Live Copy.</p> <p>Esta acción debe ser la única acción de sincronización incluida en una configuración de lanzamiento.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetActivate</td> 
   <td><p>Activa la Live Copy.</p> <p>Esta acción debe ser la única acción de sincronización incluida en una configuración de lanzamiento.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetDeactivate</td> 
   <td><p>Desactiva la Live Copy.</p> <p>Esta acción debe ser la única acción de sincronización incluida en una configuración de lanzamiento.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>flujo de trabajo</td> 
   <td><p>Inicia el flujo de trabajo definido por la propiedad target (solo para páginas) y toma la Live Copy como carga útil.</p> <p>La ruta de destino es la ruta del nodo del modelo.</p> </td> 
   <td>target: (Cadena) La ruta al modelo de flujo de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td>mandatory</td> 
   <td><p>Establece el permiso de varias ACL en la página de Live Copy como de solo lectura para un grupo de usuarios específico. Se configuran las siguientes ACL:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_REMOVE</li> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>Utilice esta acción solo para páginas.</p> </td> 
   <td>target: (Cadena) El ID del grupo para el que está estableciendo permisos. <br /> </td> 
  </tr> 
  <tr> 
   <td>mandatoryContent</td> 
   <td><p>Establece el permiso de varias ACL en la página de Live Copy como de solo lectura para un grupo de usuarios específico. Se configuran las siguientes ACL:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>Utilice esta acción solo para páginas.</p> </td> 
   <td>target: (Cadena) El ID del grupo para el que está estableciendo permisos. </td> 
  </tr> 
  <tr> 
   <td>mandatoryStructure</td> 
   <td>Establece el permiso de la ACL ActionSet.ACTION_NAME_REMOVE en la página de Live Copy como de solo lectura para un grupo de usuarios específico. Utilice esta acción solo para páginas.</td> 
   <td>target: (Cadena) El ID del grupo para el que está estableciendo permisos. </td> 
  </tr> 
  <tr> 
   <td>VersionCopyAction</td> 
   <td>Si el modelo o la página de origen se han publicado al menos una vez, crea una página de Live Copy con la versión publicada. Nota: esta acción solo está disponible para crear una página de Live Copy basada en una página de origen publicada, no para actualizar una página de Live Copy existente. </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>PageMoveAction</td> 
   <td><p>PageMoveAction se aplica cuando una página se ha movido en el modelo.</p> <p>La acción copia la página de LiveCopy (relacionada) en lugar de moverla desde la ubicación antes de moverla a la ubicación posterior.</p> <p>PageMoveAction no cambia la página de LiveCopy en la ubicación anterior al desplazamiento. Por lo tanto, para configuraciones de RolloutConfigurations consecutivas, tiene el estado de un LiveRelationship sin modelo.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">Configure el servicio de acción de traslado de páginas de CQ MSM</a> para especificar los tipos de nodo, los elementos de párrafo y las propiedades de página que se excluirán. </p> <p>Esta acción debe ser la única acción de sincronización incluida en una configuración de lanzamiento.</p> </td> 
   <td><p>prop_referenceUpdate: (Booleano) Configúrelo en true para actualizar las referencias. El valor predeterminado es true.</p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>productCreateUpdate</td> 
   <td>Crea o actualiza recursos de producto dentro de un catálogo. Esta acción está pensada para utilizarse en una de las siguientes situaciones: 
    <ul> 
     <li>Generación o implementación de un catálogo (o sección de catálogo)</li> 
     <li>Un usuario restaura la herencia de sincronización de un componente de producto.</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>markLiveRelationship</td> 
   <td>Indica que existe una relación activa para el contenido creado para launch.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>catalogRolloutHooks</td> 
   <td>Ejecuta enlaces de lanzamiento específicos de la generación de catálogos. Llama a los métodos executePageRolloutHooks y executeProductRolloutHooks del objeto CatalogGenerator.<br /> Consulte com.adobe.cq.commerce.pim.api.CatalogGenerator en los Javadocs de AEM.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>productUpdate</td> 
   <td>Actualiza las páginas del producto en una Live Copy de un catálogo de productos</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

### Creación de una configuración de lanzamiento {#creating-a-rollout-configuration}

Puede [crear una configuración de lanzamiento](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) cuando las configuraciones de lanzamiento instaladas no cumplen los requisitos de la aplicación:

* [Crear la configuración de lanzamiento](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
* [Agregar acciones de sincronización a la configuración de lanzamiento](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

A continuación, la nueva configuración de lanzamiento estará disponible cuando configure las opciones de configuración de lanzamiento en un modelo o una página de Live Copy.

### Exclusión de propiedades y tipos de nodos de la sincronización {#excluding-properties-and-node-types-from-synchronization}

Puede configurar varios servicios de OSGi que admitan las acciones de sincronización correspondientes para que no afecten a los tipos de nodos y propiedades específicos. Por ejemplo, muchas propiedades y subnodos relacionados con el funcionamiento interno de AEM no deben incluirse en una Live Copy. Solo se debe copiar el contenido relevante para el usuario de la página.

Al trabajar con AEM hay varios métodos para administrar los ajustes de configuración de dichos servicios; see [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

En la tabla siguiente se enumeran las acciones de sincronización para las que se pueden especificar los nodos que se excluirán. La tabla proporciona los nombres de los servicios que se van a configurar mediante la consola web y el PID para configurar mediante un nodo de repositorio.

| Acción de sincronización | Nombre del servicio en la consola web | PID de servicio |
|---|---|---|
| contentCopy | Acción de copia de contenido de CQ MSM | com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory |
| contentDelete | Acción de eliminación de contenido de CQ MSM | com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory |
| contentUpdate | Acción de actualización de contenido de CQ MSM | com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory |
| PageMoveAction | Acción de movimiento de página de CQ MSM | com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory |
| ReferencesUpdate | Acción de actualización de referencias de CQ MSM | com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory |

En la tabla siguiente se describen las propiedades que se pueden configurar:

<table> 
 <tbody> 
  <tr> 
   <th>Propiedad de la consola web/propiedad OSGi</th> 
   <th>Descripción</th> 
  </tr> 
  <tr> 
   <td><p>Tipos de nodos excluidos</p> <p>cq.wcm.msm.action.excludednodetypes</p> </td> 
   <td>Expresión regular que coincide con los tipos de nodos que se van a excluir de la acción de sincronización.</td> 
  </tr> 
  <tr> 
   <td><p>Elementos de párrafo excluidos</p> <p>cq.wcm.msm.action.excludedparagraphitems</p> </td> 
   <td>Expresión regular que coincide con los elementos de párrafo que se van a excluir de la acción de sincronización.</td> 
  </tr> 
  <tr> 
   <td><p>Propiedades de página excluidas</p> <p>cq.wcm.msm.action.excludedprops</p> </td> 
   <td>Expresión regular que coincide con las propiedades de página que se van a excluir de la acción de sincronización.</td> 
  </tr> 
  <tr> 
   <td><p>Tipos de nodos de Mixin ignorados</p> <p>cq.wcm.msm.action.ignoredMixin</p> </td> 
   <td>Disponible solo para la acción de actualización de contenido de CQ MSM. Expresión regular que coincide con los nombres de los tipos de nodos de mezcla que se van a excluir de la acción de sincronización.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>En la IU clásica, el icono de bloqueo que aparece en el cuadro de diálogo Propiedades de página para las páginas de LiveCopy no refleja la configuración de la propiedad Propiedades de página excluidas . El icono de bloqueo aparece incluso para las propiedades que se excluyen de la acción de sincronización.

>[!NOTE]
>
>En la IU táctil, consulte también [Configuración de los bloqueos de MSM en las propiedades de página)](/help/sites-developing/extending-msm.md).

#### Acción de actualización de contenido de CQ MSM: exclusiones {#cq-msm-content-update-action-exclusions}

De forma predeterminada, se excluyen varias propiedades y tipos de nodo, que se definen en la configuración OSGi de **Acción de actualización de contenido de CQ MSM**, en **Propiedades de página excluidas**.

De forma predeterminada, las propiedades que coinciden con las siguientes expresiones regulares se excluyen (es decir, no se actualizan) en el despliegue:

![chlimage_1-18](assets/chlimage_1-18.png)

Puede cambiar las expresiones que definen la lista de exclusión según sea necesario.

Por ejemplo, si quiere que el **título** de la página se incluya en los cambios considerados para el lanzamiento, elimine `jcr:title` de las exclusiones. Por ejemplo, con la expresión regular:

`jcr:(?!(title)$).*`

### Configuración de la sincronización de actualización de referencias {#configuring-synchronization-for-updating-references}

Puede configurar varios servicios de OSGi que admitan las acciones de sincronización correspondientes relacionadas con la actualización de referencias.

Al trabajar con AEM hay varios métodos para administrar los ajustes de configuración de dichos servicios; see [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

En la siguiente tabla se enumeran las acciones de sincronización para las que se puede especificar la actualización de referencia. La tabla proporciona los nombres de los servicios que se van a configurar mediante la consola web y el PID para configurar mediante un nodo de repositorio.

<table> 
 <tbody> 
  <tr> 
   <th>Propiedad de la consola web/propiedad OSGi</th> 
   <th>Descripción</th> 
  </tr> 
  <tr> 
   <td><p>Actualizar referencia en LiveCopies anidadas</p> <p>cq.wcm.msm.impl.action.referencesupdate.prop_updateNested</p> </td> 
   <td>Solo está disponible para la acción de actualización de referencias de CQ MSM. Seleccione esta opción (consola web) o establezca esta propiedad booleana como verdadera (configuración del repositorio) para reemplazar las referencias que se dirigen a cualquier recurso que se encuentre dentro de la rama de la LiveCopy más importante.</td> 
  </tr> 
  <tr> 
   <td><p>Actualizar páginas de referencia</p> <p>cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate</p> </td> 
   <td>Solo disponible para la acción de movimiento de página de CQ MSM. Seleccione esta opción (consola web) o establezca esta propiedad booleana como <code>true</code> (configuración del repositorio) para actualizar cualquier referencia a la que se utilice la página original en lugar de hacer referencia a la página de LiveCopy.</td> 
  </tr> 
 </tbody> 
</table>

## Especificación de las opciones de configuración de lanzamiento que se van a utilizar {#specifying-the-rollout-configurations-to-use}

MSM le permite especificar conjuntos de configuraciones de lanzamiento que se utilizan generalmente y, cuando sea necesario, puede anularlos para Live Copies específicas. MSM proporciona varias ubicaciones para especificar las opciones de configuración de lanzamiento que se deben utilizar. La ubicación determina si la configuración se aplica a una Live Copy específica.

La siguiente lista de ubicaciones en las que puede especificar las opciones de configuración de lanzamiento que desea utilizar describe cómo MSM determina qué opciones de configuración de lanzamiento utilizar para una Live Copy:

* **[Propiedades de la página Live Copy](/help/sites-administering/msm-sync.md#setting-the-rollout-configurations-for-a-live-copy-page):** Cuando se configura una página de Live Copy para que utilice una o más opciones de configuración de lanzamiento, MSM utiliza esas opciones de configuración de lanzamiento.
* **[Propiedades de la página de modelo](/help/sites-administering/msm-sync.md#setting-the-rollout-configuration-for-a-blueprint-page):** Cuando una Live Copy se basa en un modelo y la página de Live Copy no está configurada con una configuración de lanzamiento, se utiliza la configuración de lanzamiento asociada a la página de origen del modelo.
* **Propiedades de la página principal de Live Copy:** Cuando ni la página de Live Copy ni la página de origen del modelo están configuradas con una configuración de lanzamiento, se utiliza la configuración de lanzamiento que se aplica a la página principal de la página de Live Copy.
* **[Sistema predeterminado](/help/sites-administering/msm-sync.md#setting-the-system-default-rollout-configuration):** Cuando no se puede determinar la configuración de lanzamiento de la página principal de la Live Copy, se utiliza la configuración de lanzamiento predeterminada del sistema.

Por ejemplo, un modelo utiliza el sitio de referencia We.Retail como contenido de origen. Se crea un sitio a partir del modelo. Cada elemento de la siguiente lista describe un escenario diferente con respecto al uso de las configuraciones de lanzamiento:

* Ninguna de las páginas de modelo o las páginas de Live Copy están configuradas para utilizar una configuración de lanzamiento. MSM utiliza la configuración de lanzamiento predeterminada del sistema para todas las páginas de Live Copy.
* La página raíz del sitio de referencia de We.Retail se configura con varias configuraciones de lanzamiento. MSM utiliza estas configuraciones de lanzamiento para todas las páginas de Live Copy.
* La página raíz del sitio de referencia de We.Retail se configura con varias configuraciones de lanzamiento y la página raíz del sitio de Live Copy se configura con un conjunto diferente de configuraciones de lanzamiento. MSM utiliza las configuraciones de lanzamiento configuradas en la página raíz del sitio de Live Copy.

### Configuración de las opciones de configuración de lanzamiento para una página de Live Copy {#setting-the-rollout-configurations-for-a-live-copy-page}

Configure una página de Live Copy con las opciones de configuración de lanzamiento que se usarán cuando se implemente la página de origen. Las páginas secundarias heredan la configuración de forma predeterminada. Al configurar la configuración de lanzamiento para su uso, anula la configuración que hereda la página de Live Copy de su elemento principal.

También puede configurar las opciones de configuración de lanzamiento para una página de Live Copy cuando [crear la Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page).

1. Utilice la variable **Sitios** para seleccionar la página de Live Copy.

1. En la barra de herramientas, seleccione **Propiedades**.
1. Abra la pestaña **Live Copy**.

   La sección **Configuración** muestra las opciones de configuración de lanzamiento que hereda la página.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Si es necesario, ajuste la marca de **Herencia de Live Copy**. Si se selecciona, la configuración de Live Copy es efectiva en todos los elementos secundarios.

1. Borre la variable **Heredar Configuración De Despliegue Del Principal** y, a continuación, seleccione una o varias opciones de configuración de lanzamiento de la lista.

   Las configuraciones de lanzamiento seleccionadas aparecen debajo de la lista desplegable.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Toque o haga clic en **Guardar**.

### Configuración del lanzamiento de una página de modelo {#setting-the-rollout-configuration-for-a-blueprint-page}

Configure una página de modelo con las configuraciones de lanzamiento que se usarán cuando se implemente la página de modelo.

Tenga en cuenta que las páginas secundarias de la página de modelo heredan la configuración. Al configurar la configuración de lanzamiento para su uso, podría anular la configuración que la página hereda de su elemento principal.

1. Utilice la consola **Sitios** para seleccionar la página de modelo.
1. En la barra de herramientas, seleccione **Propiedades**.
1. Abra la pestaña **Modelo**.
1. Seleccione una o más **opciones de configuración de lanzamiento** con el selector desplegable.
1. Para almacenar las actualizaciones, seleccione **Guardar**.

### Opciones de la configuración de lanzamiento predeterminada del sistema {#setting-the-system-default-rollout-configuration}

Especifique una configuración de lanzamiento para utilizarla como predeterminada del sistema. Para especificar el valor predeterminado, configure el servicio OSGi:

* **Administrador de relaciones en directo de CQ WCM Day**
el PID de servicio es 
`com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Configure el servicio mediante la variable [Consola web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o [nodo del repositorio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* En la consola web, el nombre de la propiedad que se va a configurar es Configuración de despliegue predeterminada.
* Mediante un nodo del repositorio, el nombre de la propiedad que se va a configurar es `liverelationshipmgr.relationsconfig.default`.

Establezca este valor de la propiedad en la ruta de la configuración de lanzamiento que se utilizará como valor predeterminado del sistema. El valor predeterminado es `/libs/msm/wcm/rolloutconfigs/default`, que es la **Configuración de despliegue estándar**.
