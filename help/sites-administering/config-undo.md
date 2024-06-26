---
title: Configuración de Deshacer para la edición de páginas
seo-title: Configuring Undo for Page Editing
description: Obtenga información sobre cómo configurar la compatibilidad con Deshacer para la edición de páginas en AEM.
seo-description: Learn how to configure Undo support for page editing in AEM.
uuid: e5a49587-a2a6-41d5-b449-f7a8f7e4cee6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3cc7efc5-bcb2-41c9-b78b-308f6b7a298e
exl-id: badb7082-3ebf-4bb3-9157-48b8e7ea8ff9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 3%

---

# Configuración de Deshacer para la edición de páginas{#configuring-undo-for-page-editing}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La variable [Servicio OSGi](/help/sites-deploying/configuring-osgi.md)  **Configuración de Deshacer de WCM Day CQ WCM** ( `com.day.cq.wcm.undo.UndoConfigService`) expone varias propiedades que controlan el comportamiento de los comandos deshacer y rehacer para editar páginas.

## Configuración predeterminada {#default-configuration}

En una instalación estándar, la configuración predeterminada se define como propiedades en la variable `sling:OsgiConfig`nodo:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Este nodo contiene `cq.wcm.undo.whitelist` y `cq.wcm.undo.blacklist` propiedades, para las demás propiedades se toman los valores predeterminados.

>[!CAUTION]
>
>You ***must*** no cambie nada en la variable `/libs` ruta.
>
>Esto se debe a que el contenido de `/libs` se sobrescribe la próxima vez que actualice la instancia (y puede sobrescribirse al aplicar una corrección o un paquete de funciones).

## Configuración de Deshacer y Rehacer {#configuring-undo-and-redo}

Puede configurar estas propiedades del servicio OSGi para su propia instancia.

>[!NOTE]
>
>Al trabajar con AEM hay varios métodos para administrar los ajustes de configuración de dichos servicios; see [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

A continuación se enumeran las propiedades tal como se muestran en la consola web, seguidas del nombre del parámetro OSGi correspondiente, junto con una descripción y el valor predeterminado (cuando corresponda):

* **Enable**
( 
`cq.wcm.undo.enabled`)

   * **Descripción**: Determina si los autores de la página pueden deshacer y rehacer cambios.
   * **Predeterminado**: `Selected`
   * **Tipo**: `Boolean`

* **Ruta**
( 
`cq.wcm.undo.path`)

   * **Descripción**: Ruta del repositorio para la persistencia de datos de deshacer binarios. Cuando los autores cambian datos binarios como imágenes, la versión original de los datos se mantiene aquí. Cuando se deshacen los cambios en los datos binarios, estos datos de deshacer binarios se restauran a la página.
   * **Predeterminado**: `/var/undo`
   * **Tipo**: `String`

   >[!NOTE]
   >
   >De forma predeterminada, solo los administradores pueden acceder al `/var/undo` nodo . Los autores pueden realizar operaciones de deshacer y rehacer en contenido binario solo después de que se les haya concedido permiso para acceder a los datos de deshacer binarios.

* **Min. valide**
( 
`cq.wcm.undo.validity`)

   * **Descripción**: Cantidad mínima de tiempo durante el cual se almacenan los datos de deshacer binarios, en horas. Después de este período de tiempo, los datos binarios están disponibles para su eliminación, para conservar el espacio en disco.
   * **Predeterminado**: `10`
   * **Tipo**: `Integer`

* **Etapas**
( 
`cq.wcm.undo.steps`)

   * **Descripción**: Número máximo de acciones de página almacenadas en el historial de deshacer.
   * **Predeterminado**: `20`
   * **Tipo**: `Integer`

* **Persistencia**
( 
`cq.wcm.undo.persistence`)

   * **Descripción**: La clase que persiste en el historial de deshacer. Se proporcionan dos clases de persistencia:

      * `CQ.undo.persistence.WindowNamePersistence`: Persiste el historial utilizando la propiedad window.name .
      * `CQ.undo.persistence.CookiePersistance`: Persiste el historial al usar cookies.
   * **Predeterminado**: `CQ.undo.persistence.WindowNamePersistence`
   * **Tipo**: `String`


* **Modo de persistencia**
( 
`cq.wcm.undo.persistence.mode`)

   * **Descripción**: Determina cuándo se mantiene el historial de deshacer. Seleccione esta opción para mantener el historial de deshacer después de cada edición de página. Borre esta opción para que solo se mantenga cuando se vuelva a cargar una página (por ejemplo, el usuario navega a una página diferente).

      El historial de deshacer persistente utiliza recursos del explorador web. Si el explorador de los usuarios reacciona lentamente a las ediciones de página, intente mantener el historial de deshacer en las recargas de página.

   * **Predeterminado**: `Selected`
   * **Tipo**: `Boolean`

* **Modo marcador**
( 
`cq.wcm.undo.markermode`)

   * **Descripción**: Especifica la pista visual que se utilizará para indicar qué párrafos se ven afectados cuando se produce una acción de deshacer o rehacer. Los siguientes valores son válidos:

      * flash: El indicador de selección de los párrafos parpadea temporalmente.
      * seleccione: El párrafo está seleccionado.
   * **Predeterminado**: `flash`
   * **Tipo**: `String`


* **Buenos componentes**
( 
`cq.wcm.undo.whitelist`)

   * **Descripción**: Lista de componentes que desea que se vean afectados por los comandos deshacer y rehacer. Añada rutas de componentes a esta lista cuando funcionen correctamente con deshacer o rehacer. Añada un asterisco (&amp;ast;) para especificar un grupo de componentes:

      * El siguiente valor especifica el componente de texto base:

         `foundation/components/text`

      * El siguiente valor especifica todos los componentes de base:

         `foundation/components/*`
   * Cuando se ejecuta deshacer o rehacer en un componente que no está en esta lista, aparece un mensaje que indica que el comando puede no ser fiable.

   * **Predeterminado**: La propiedad se rellena con muchos componentes que AEM proporciona.
   * **Tipo**: `String[]`


* **Componentes malos**
( 
`cq.wcm.undo.blacklist`)

   * **Descripción**: Lista de componentes y/o operaciones de componentes que no desea que se vean afectados por el comando Deshacer. Añada componentes y operaciones de componentes que no se comporten correctamente con el comando deshacer:

      * Añada una ruta de componente cuando no desee ninguna de las operaciones del componente en el historial de deshacer, por ejemplo `collab/forum/components/post`
      * Anexe dos puntos (:) y una operación a la ruta cuando desee que esa operación específica se omita del historial de deshacer (otras operaciones funcionan correctamente), por ejemplo `collab/forum/components/post:insertParagraph.`

   >[!NOTE]
   >
   >Cuando una operación está en esta lista, se agrega al historial de deshacer. Los usuarios no pueden deshacer las operaciones que existen antes de una **Componente incorrecto** en el historial de deshacer.

   * Los nombres de operación habituales son los siguientes:

      * `insertParagraph`: El componente se añade a la página.
      * `removeParagraph`: Se elimina el componente.
      * `moveParagraph`: El párrafo se mueve a una ubicación diferente.
      * `updateParagraph`: Se cambian las propiedades del párrafo.
   * **Predeterminado**: La propiedad se rellena con varias operaciones de componentes.
   * **Tipo**: `String[]`
