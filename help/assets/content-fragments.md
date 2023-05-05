---
title: Trabajar con fragmentos de contenido
seo-title: Working with Content Fragments
description: Descubra cómo los fragmentos de contenido le permiten diseñar, crear, depurar y utilizar contenido independiente de las páginas.
seo-description: Learn how Content Fragments allow you to design, create, curate and use page-independent content.
uuid: aa5acda2-4c20-4fe7-929d-6c065b252cf2
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 22ae0d3a-083f-40e4-bf4a-7a755ae9e312
exl-id: e2804707-7b75-4fae-937e-9e258481878f
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 74%

---

# Trabajar con fragmentos de contenido {#working-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

Los fragmentos de contenido de Adobe Experience Manager (AEM) le permiten diseñar, crear, depurar y [publicar contenido independiente de la página](/help/sites-authoring/content-fragments.md). Permiten preparar contenido listo para usar en varias ubicaciones o en varios canales.

Los fragmentos de contenido también se pueden entregar en formato JSON, utilizando las capacidades de exportación del Modelo Sling (JSON) de los componentes principales de AEM. Esta forma de entrega:

* permite utilizar el componente para administrar qué elementos enviar de un fragmento.
* permite la entrega por lotes, añadiendo varios componentes principales de fragmento de contenido en la página que se utiliza para la entrega de API.

Esta y las siguientes páginas tratan sobre las tareas para crear, configurar y mantener sus fragmentos de contenido:

* [Administración de fragmentos de contenido](content-fragments-managing.md): cree sus fragmentos de contenido; a continuación, edite, publique y haga referencias.

* [Modelos de fragmento de contenido](content-fragments-models.md): activar, crear y definir sus modelos

* [Variaciones, creación de contenido de fragmentos](content-fragments-variations.md): cree el contenido del fragmento y variaciones del principal

* [Markdown](content-fragments-markdown.md): uso de la sintaxis de markdown para el fragmento

* [Uso de contenido asociado](content-fragments-assoc-content.md): añadir contenido asociado

* [Metadatos, propiedades del fragmento](content-fragments-metadata.md): visualización y edición de las propiedades del fragmento

>[!NOTE]
>
>Estas páginas deben leerse junto con [Creación de páginas con fragmentos de contenido](/help/sites-authoring/content-fragments.md).

El número de canales de comunicación aumenta de forma anual. Normalmente, los canales hacen referencia al mecanismo de entrega, ya sea como los siguientes:

* canal físico; p. ej., escritorio o móvil.
* Forma de entrega en un canal físico; por ejemplo, la “página de detalles del producto”, la “página de categoría del producto” para escritorio o la “web móvil”, la “aplicación móvil” para móvil.

Sin embargo, probablemente no desea utilizar exactamente el mismo contenido para todos los canales y necesita optimizar su contenido según el canal específico.

Los fragmentos de contenido le permiten lo siguiente:

* Pensar en cómo llegar a las audiencias de destino de forma eficaz en todos los canales.
* Crear y administrar contenido editorial neutro para el canal.
* Creargrupos de contenido para una amplia gama de canales.
* Diseñar variaciones de contenido para canales específicos.
* Agregar imágenes al texto insertando recursos (fragmentos de medios mixtos).

Estos fragmentos de contenido se pueden ensamblar para ofrecer experiencias en una variedad de canales.

## Fragmentos de contenido y servicios de contenido {#content-fragments-and-content-services}

Los servicios de contenido de AEM están diseñados para generalizar la descripción y la entrega de contenido desde o hacia AEM, más allá del enfoque en las páginas web.

Proporcionan la entrega de contenido a canales que no son páginas web de AEM tradicionales, mediante métodos estandarizados que cualquier cliente puede consumir. Estos canales pueden incluir lo siguiente:

* Aplicaciones de una sola página
* Aplicaciones móviles nativas
* Otros canales y puntos de contacto externos a AEM

La entrega se realiza en formato JSON.

Los fragmentos de contenido de AEM se pueden usar para describir y administrar el contenido estructurado. El contenido estructurado se define en modelos que pueden contener una variedad de tipos de contenido; incluido texto, datos numéricos, booleanos, fecha y hora, etc.

Junto con las capacidades de exportación de JSON de los componentes principales de AEM, este contenido estructurado se puede utilizar para entregar contenido de AEM a canales que no sean páginas de AEM.

>[!NOTE]
>
>Los **fragmentos de contenido** y los **[fragmentos de experiencias](/help/sites-authoring/experience-fragments.md)** son funciones distintas de AEM:
>
>* **Fragmentos de contenido** son contenido editorial, principalmente texto e imágenes relacionadas. Son contenido puro, sin diseño ni diseño.
>* Los **fragmentos de experiencias** son contenidos plenamente diseñados; un fragmento de una página web. 
>
>Los fragmentos de experiencias pueden incluir contenido en forma de fragmentos, pero no lo contrario.
>
>Para obtener más información, consulte también [Explicación de los fragmentos de contenido y de experiencias en AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>Los fragmentos de contenido no están disponibles en la IU clásica.
>
>El componente Fragmento de contenido se puede ver en la barra de tareas de la IU clásica, pero no hay más funciones disponibles.

>[!NOTE]
>
>AEM también admite la traducción del contenido del fragmento. Consulte [Creación de proyectos de traducción para fragmentos de contenido](creating-translation-projects-for-content-fragments.md) para obtener más información.

## Tipos de fragmento de contenido {#types-of-content-fragment}

Los fragmentos de contenido pueden ser:

* Fragmentos simples

   * No tienen estructura predefinida. Solo contienen texto e imágenes.
   * Se basan en la plantilla Fragmento simple .

* Fragmentos que contienen contenido estructurado

   * Se basan en un [Modelo de fragmento de contenido](content-fragments-models.md), que predefine una estructura para el fragmento resultante.
   * También se pueden usar para realizar servicios de contenido usando el exportador JSON.

## Tipo de contenido {#content-type}

Los fragmentos de contenido son lo siguiente:

* Se almacenan como **Recursos**:

   * Los fragmentos de contenido (y sus variaciones) se pueden crear y mantener a partir del **Recursos** consola.
   * Se crean y editan en el editor de fragmentos de contenido.

* Se usan en el [editor de páginas mediante el componente Fragmento de contenido](/help/sites-authoring/content-fragments.md) (componente de referencia):

   * El componente **Fragmento de contenido** está disponible para los autores de páginas. Les permite hacer referencia y entregar el fragmento de contenido requerido en formato HTML o JSON.

Los fragmentos de contenido son una estructura de contenido que:

* No tiene diseño (es posible aplicar algo de formato de texto en el modo Texto enriquecido).
* Incluye una o más [partes constitutivas](#constituent-parts-of-a-content-fragment).
* Puede [contener imágenes o estar conectada a ellas](#fragments-with-visual-assets).
* Puede usar [contenido intermedio](#in-between-content-when-page-authoring-with-content-fragments) cuando está referenciada en una página.

* Es independiente del mecanismo de entrega (es decir, página, canal).

### Fragmentos con recursos visuales {#fragments-with-visual-assets}

Para que los autores tengan un mayor control sobre su contenido, las imágenes se pueden añadir o integrar con un fragmento de contenido.

Los recursos se pueden utilizar con un fragmento de contenido de varias formas, cada una con sus ventajas:

* **Insertan recursos** en un fragmento (fragmentos de medios mixtos)

   * Son una parte integral del fragmento (consulte [Partes constitutivas de un fragmento de contenido](#constituent-parts-of-a-content-fragment)).
   * Definen la posición del recurso.
   * Consulte [Inserción de recursos en el fragmento](content-fragments-variations.md#inserting-assets-into-your-fragment) en el editor de fragmentos para obtener más información.

   >[!NOTE]
   >
   >Los recursos visuales insertados en el propio fragmento de contenido se adjuntan al párrafo anterior. Cuando se añade el fragmento a una página, estos recursos se mueven en relación con ese párrafo al agregarse contenido intermedio.

* **Contenido asociado**

   * Están conectados a un fragmento; pero no una parte fija de este (consulte [Partes constitutivas de un fragmento de contenido](#constituent-parts-of-a-content-fragment)).
   * Permiten cierta flexibilidad de posicionamiento.
   * Están fácilmente disponibles para su uso (como contenido intermedio) al utilizar el fragmento en una página.
   * Consulte [Contenido asociado](content-fragments-assoc-content.md) para obtener más información.

* Recursos disponibles desde el **explorador de Assets** del editor de páginas

   * Permiten flexibilidad total para la selección de un recurso.
   * Permiten cierta flexibilidad de posicionamiento.
   * No proporcionan el concepto de aprobarse para un fragmento específico.
   * Consulte el [Explorador de recursos](/help/sites-authoring/author-environment-tools.md#assets-browser) para obtener más información.

### Partes constitutivas de un fragmento de contenido {#constituent-parts-of-a-content-fragment}

Los activos de fragmento de contenido están formados por las siguientes partes (directa o indirectamente):

* **Elementos de fragmento**

   * Los elementos se correlacionan con los campos de datos que tienen contenido.
   * Para fragmentos con contenido estructurado, se utiliza un modelo de contenido para crear el fragmento de contenido. Los elementos (campos) especificados en el modelo definen la estructura del fragmento. Estos elementos (campos) pueden ser de varios tipos de datos.
   * Para fragmentos simples:

      * El contenido se incluye en uno o más campos de texto multilínea o en elementos.
      * Los elementos se definen en la plantilla de fragmento (no se puede definir al crear el fragmento, consulte [Plantillas de fragmento de contenido](/help/sites-developing/content-fragment-templates.md)).

* **Párrafos de fragmento**

   * Bloques de texto, que son:

      * separado por espacios verticales (retorno de carro)
      * en elementos de texto multilínea; en fragmentos simples o estructurados
   * En los modos [Texto enriquecido](content-fragments-variations.md#rich-text) y [Markdown](content-fragments-variations.md#markdown), un párrafo se puede formatear como un encabezado, en cuyo caso, ese párrafo y el siguiente se unirán como una sola unidad.
   * Habilite el control de contenido durante la creación de páginas.


* **Recursos insertados en un fragmento (fragmentos de medios mixtos)**

   * Recursos (imágenes) insertados en el fragmento real y usados como contenido interno de un fragmento.
   * Están incrustados en el sistema de párrafos del fragmento.
   * Se les puede dar formato cuando el [fragmento se utiliza/referencia en una página](/help/sites-authoring/content-fragments.md).
   * Solo se pueden agregar, eliminar o mover dentro de un fragmento con el editor de fragmentos. Estas acciones no se pueden llevar a cabo en el editor de páginas.
   * Solo se pueden agregar, eliminar o mover dentro de un fragmento mediante [Formato de texto enriquecido en el editor de fragmentos](content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Solo se puede añadir a elementos de texto multilínea (cualquier tipo de fragmento).
   * Se adjuntan al texto anterior (párrafo).

   >[!CAUTION]
   >
   >Se puede eliminar (sin querer) de un fragmento cambiando al formato de texto sin formato.

   >[!NOTE]
   >
   >Los recursos también se pueden añadir como [contenido adicional (intermedio)](/help/sites-authoring/content-fragments.md#using-associated-content) al utilizar un fragmento en una página, usando contenido asociado o recursos del explorador Recursos.

* **Contenido asociado**

   * Es contenido externo a un fragmento, pero con relevancia editorial para él. Normalmente, imágenes, vídeos u otros fragmentos.
   * Los recursos individuales de la colección están disponibles para su uso con el fragmento en el editor de páginas, cuando se añada a una página. Esto significa que son opcionales, según los requisitos del canal específico.
   * Los recursos están [asociados a fragmentos mediante colecciones](content-fragments-assoc-content.md); las colecciones asociadas permiten al autor decidir qué recursos emplear cuando esté creando la página.

      * Las colecciones se pueden asociar a fragmentos a través de plantillas, como contenido predeterminado o por medio de autores durante la creación de fragmentos.
      * Las [Colecciones de recursos (DAM)](managing-collections-touch-ui.md) son la base del contenido asociado de los fragmentos.
   * De forma opcional, también puede añadir el fragmento a una colección para ayudar en el seguimiento.


* **Metadatos de fragmento**

   * Utilice los [Esquemas de metadatos de recursos](metadata.md).
   * Las etiquetas se pueden crear cuando hace lo siguiente:

      * Crea el fragmento
      * O luego:

         * Al visualizar o editar las **Propiedades** del fragmento desde la consola
         * Editando los **Metadatos** en el editor de fragmentos

   >[!CAUTION]
   >
   >Los perfiles de procesamiento de metadatos no se aplican a los fragmentos de contenido.

* **Principal**

   * Una parte integral del fragmento

      * Cada fragmento de contenido tiene una instancia de Principal.
      * El Principal no se puede eliminar.
   * Se puede acceder al Principal en el editor de fragmentos, en **[Variaciones](content-fragments-variations.md)**.
   * El Principal no es una variación como tal, sino la base de todas las variaciones.


* **Variaciones**

   * Representaciones de texto de fragmento específicas para fines editoriales; pueden estar relacionadas con el canal, pero no es obligatorio, y también pueden ser para modificaciones locales específicas.
   * Se crean como copias del **Principal**, pero se pueden editar según sea necesario; normalmente, el contenido se superpone entre las propias variaciones.
   * Se puede definir durante la creación de fragmentos o predefinirse en plantillas de fragmento.
   * Almacenadas en el fragmento para evitar la dispersión de copias de contenido.
   * Las variaciones se pueden [sincronizar](content-fragments-variations.md#synchronizing-with-master) con el Principal si se actualizó el contenido principal.
   * Pueden [resumirse](content-fragments-variations.md#summarizing-text) para truncar rápidamente el texto a una longitud predefinida.
   * Disponibles en la pestaña [Variaciones](content-fragments-variations.md) del editor de fragmentos.

### Contenido intermedio al crear páginas con fragmentos de contenido {#in-between-content-when-page-authoring-with-content-fragments}

Contenido intermedio:

* Está disponible para su uso en el [editor de páginas al trabajar con fragmentos de contenido](/help/sites-authoring/content-fragments.md).
* Es [contenido adicional añadido dentro del flujo de un fragmento](/help/sites-authoring/content-fragments.md#adding-in-between-content) una vez que se ha utilizado o se ha hecho referencia a él en una página.
* El contenido intermedio se puede añadir a cualquier fragmento donde solo haya un elemento visible.
* Se puede utilizar contenido asociado, así como recursos o componentes del explorador adecuado.

>[!CAUTION]
>
>El contenido intermedio es contenido de página. No se almacena en el fragmento de contenido.

### Requerido por fragmentos {#required-by-fragments}

Para crear, editar y utilizar fragmentos de contenido también necesita:

* **Modelo de contenido**

   * Son [activada y, a continuación, creada mediante Herramientas](content-fragments-models.md).
   * Requerido para [crear un fragmento estructurado](content-fragments-managing.md#creating-content-fragments).
   * Define la estructura de un fragmento (título, elementos de contenido, definiciones de etiquetas).
   * Las definiciones de los modelos de contenido requieren un título y un elemento de datos; todo lo demás es opcional. El modelo define un ámbito mínimo del fragmento y el contenido predeterminado, si corresponde. Los autores no pueden cambiar la estructura definida al crear contenido de fragmento.

* **Plantilla de fragmento**

   * Requerido para [crear un fragmento simple](content-fragments-managing.md#creating-content-fragments).
   * Normalmente [se desarrolla durante la ejecución del proyecto](/help/sites-developing/content-fragment-templates.md); no se puede crear durante la creación.
   * Define las propiedades básicas de un fragmento simple (título, número de elementos de texto, definiciones de etiquetas).
   * Las definiciones de plantilla requieren un título y un elemento de texto; todo lo demás es opcional. La plantilla define un ámbito mínimo del fragmento y el contenido predeterminado, si corresponde. Posteriormente, los autores pueden ampliar un fragmento más allá de lo definido en la plantilla.

* **Componente Fragmento de contenido**

   * Instrumental para entregar el fragmento en formato HTML o JSON.
   * Requerido para [hacer referencia al fragmento en una página](/help/sites-authoring/content-fragments.md).
   * Responsable del diseño y entrega de un fragmento; es decir, de los canales.
   * Los fragmentos necesitan uno o más componentes dedicados para definir el diseño y proporcionar algunos o todos los elementos/variaciones y el contenido asociado.
   * Al arrastrar un fragmento a una página en la creación, se asociará automáticamente el componente requerido.

## Uso de ejemplo {#example-usage}

Un fragmento, con sus elementos y variaciones, se puede utilizar para crear contenido coherente para varios canales. Al diseñar el fragmento, debe tener en cuenta qué se utilizará y dónde.

### Ejemplo de We.Retail {#we-retail-sample}

Se puede ver un fragmento de ejemplo en:

[http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)
