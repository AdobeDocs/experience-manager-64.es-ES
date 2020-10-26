---
title: NO PUBLIQUE, PERO NO DELETE Personalización De Modelos De Fragmento De Contenido
seo-title: Personalización de modelos de fragmentos de contenido
description: Los modelos de fragmento de contenido se pueden personalizar y ampliar.
seo-description: Los modelos de fragmento de contenido se pueden personalizar y ampliar.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# NO PUBLIQUE, PERO NO DELETE Personalización De Modelos De Fragmento De Contenido{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

El editor del modelo de fragmentos de contenido es un asistente basado en `Formbuilder`, heredado de:

`granite/ui/components/foundation/form/formbuilder`

Este componente tiene las herramientas necesarias para procesar la interfaz de arrastrar y soltar del editor de modelos, con tipos de datos y propiedades para cada uno.

## Ubicaciones {#locations}

Los modelos se guardan y se crean en `/conf`, en una carpeta que tiene activada la propiedad [Modelos de fragmento de](/help/assets/content-fragments-models.md#enable-content-fragment-models) contenido. Esta configuración también se puede ver en las Propiedades **de** configuración, a las que se puede acceder desde el explorador **[de configuración](/help/sites-administering/configurations.md)**.

1. Vaya al explorador a través de **Herramientas**, **General**, Navegador **de** configuración. Por ejemplo, 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. En el navegador, seleccione la configuración adecuada y, a continuación, **Propiedades** en la barra de herramientas.

   Por ejemplo, las propiedades de `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

En la consola de modelos, aparecerán todas las carpetas con la propiedad Modelos **de fragmento de** contenido. Navegar mediante **Herramientas**, **Recursos**, Modelos **de fragmentos** de contenido; por ejemplo, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Un usuario puede [crear un modelo](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) de fragmento de contenido mediante el asistente **Crear modelo** (mediante **Crear** desde la consola).

>[!CAUTION]
>
>No ***debe*** cambiar nada en la `/libs` ruta.
>
>Esto se debe a que el contenido de `/libs` se sobrescribe la próxima vez que actualice la instancia (y puede sobrescribirse al aplicar una revisión o un paquete de funciones).

## Estructura de un modelo {#structure-of-a-model}

El asistente creará una entrada con esta estructura:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Todos los modelos se guardan en subcarpetas de esta carpeta.

* `jcr:content`

   Cada modelo contiene un `jcr:content` nodo que:

   * contiene propiedades de información sobre el modelo como `jcr:title`, `lastModified`, `lastModifiedBy`
   * normalmente tiene el `sling:ResourceType` de `dam/cfm/models/console/components/data/entity/default`,

      con el `sling:ResourceSuperType` de `dam/cfm/models/console/components/data/entity`

* `model`

   El `model` nodo contiene una propiedad `dataTypesConfig`, utilizada para determinar los tipos de datos utilizados en el editor de modelos.

* `items`

   Bajo el `items` nodo, se guardan todos los tipos de datos agregados al modelo (como arrastrados y soltados en el editor de modelos). A cada elemento se le asigna un nombre de nodo aleatorio, pero para que el editor de fragmentos de contenido funcione con este modelo, cada elemento debe tener una `name` propiedad. Además, en este nodo se guardan todas las propiedades de configuración de un tipo de datos concreto, incluidas las propiedades predeterminadas necesarias para procesar los componentes.

>[!CAUTION]
>
>Todos los tipos de datos arrastrados y soltados en un editor de modelos, y como tales creados en instancias, **deben** tener la `name` propiedad introducida por el usuario.
>
>Esto se ve como Nombre **de propiedad &amp;ast;** en la ficha **Propiedades** del editor de modelos.

## Estructura del Editor de modelos {#structure-of-the-model-editor}

El Editor **del modelo de fragmento de** contenido consta de dos partes:

* El panel previsualización, o vista, del lado izquierdo, donde puede soltar elementos. Así pues:

   * Muestra una previsualización del tipo **de** datos en el que se crea una instancia.
   * Permite realizar pedidos dentro del Editor de modelos.

* Las fichas Tipos **de** datos/**Propiedades** del panel de la derecha. Así pues:

   * Muestra una lista de tipos de datos que se pueden arrastrar y crear instancias.
   * Para el editor de modelos incorporado, la lista está presente en:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Todos los tipos de datos procesados tienen dos etiquetas de secuencia de comandos que, al crearse una instancia, formarán la vista (el componente procesado en el lado izquierdo) y la ficha **Propiedades** , que define las propiedades que un usuario puede definir para un componente determinado.

>[!CAUTION]
>
>No ***debe*** cambiar nada en la `/libs` ruta.
>
>Esto se debe a que el contenido de `/libs` se sobrescribe la próxima vez que actualice la instancia (y puede sobrescribirse al aplicar una revisión o un paquete de funciones).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Cuando se crea una instancia de un tipo de datos, se crean entradas HTML para cada propiedad que el componente necesita representarse en un fragmento de contenido. Por ejemplo:

* **Nombre de propiedad &amp;ast;** ( `name`): actúa como identificador de componentes

* **Representar como** ( `metaType`): escriba el componente que se procesará como

* **Descripción** ( `fieldDescription`): descripción del componente en el fragmento de contenido

* y otros.

