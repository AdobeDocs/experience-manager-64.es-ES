---
title: Administrar fragmentos de contenido
seo-title: Managing Content Fragments
description: Los fragmentos de contenido se almacenan como recursos, por lo que se administran principalmente desde la consola Recursos.
seo-description: Content Fragments are stored as Assets, so are primarily managed from the Assets console.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
exl-id: b21ba7a1-6e6f-4b95-9336-b49f7e932af5
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 63%

---

# Administrar fragmentos de contenido {#managing-content-fragments}

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

Los fragmentos de contenido se almacenan como **[!UICONTROL Recursos]**, por lo que se administran principalmente desde la variable **[!UICONTROL Recursos]** consola.

>[!NOTE]
>
>A continuación, los fragmentos de contenido se utilizan con las páginas de creación; see [Creación de páginas con fragmentos de contenido](/help/sites-authoring/content-fragments.md).

## Creación de fragmentos de contenido {#creating-content-fragments}

### Creación de un modelo de contenido {#creating-a-content-model}

Los [Modelos de fragmento de contenido](content-fragments-models.md) se pueden habilitar y crear, antes de crear fragmentos de contenido con contenido estructurado.

>[!NOTE]
>
>Consulte [Desarrollo de fragmentos de contenido](/help/sites-developing/customizing-content-fragments.md) para más información sobre las plantillas; se utiliza para fragmentos de contenido simples.

### Creación de un fragmento de contenido {#creating-a-content-fragment}

El método para crear un fragmento de contenido es (básicamente) el mismo para fragmentos simples y estructurados:

1. Vaya a la carpeta **[!UICONTROL Assets]** en la que desea crear el fragmento.
1. Seleccione **[!UICONTROL Crear]** y, a continuación, **[!UICONTROL Fragmento de contenido]** para abrir el asistente.
1. El primer paso del asistente requiere que especifique la base del nuevo fragmento.

   * Puede ser un:

      * [Plantilla](/help/sites-developing/content-fragment-templates.md) - por ejemplo **[!UICONTROL Fragmento simple]**
      * [Modelo](content-fragments-models.md) - se utiliza para crear un fragmento que requiere contenido estructurado; por ejemplo, la variable **Aeropuerto** model
   * Se muestran todas las plantillas y modelos disponibles.

   Tras la selección, utilice **[!UICONTROL Siguiente]** para continuar.

   ![cfm-6420-15](assets/cfm-6420-15.png)

1. En el paso **[!UICONTROL Propiedades]**, especifique:

   * **[!UICONTROL Básico]**

      * **[!UICONTROL Título]**

         El título del fragmento.

         Obligatorio.

      * **[!UICONTROL Descripción]**
      * **[!UICONTROL Etiquetas]**
   * **[!UICONTROL Avanzado]**

      * **[!UICONTROL Nombre]**

         El nombre; se utilizará para formar la dirección URL.

         Obligatorio; se derivan automáticamente del título, pero se pueden actualizar.


1. Seleccione **[!UICONTROL Crear]** para completar la acción y, a continuación, **[!UICONTROL Abra]** el fragmento para editarlo o vuelva a la consola pulsando **[!UICONTROL Listo]**.

## Acciones para un fragmento de contenido {#actions-for-a-content-fragment}

En el **[!UICONTROL Recursos]** Una serie de acciones están disponibles para los fragmentos de contenido:

* Desde la barra de herramientas; después de seleccionar el fragmento, están disponibles todas las acciones adecuadas.
* Como [acciones rápidas](/help/sites-authoring/basic-handling.md#quick-actions); un subconjunto de acciones disponibles para las tarjetas de fragmento individuales.

![cfm-6420-17](assets/cfm-6420-17.png)

Seleccione el fragmento para mostrar la barra de herramientas con las acciones aplicables:

* **[!UICONTROL Descargar]**

   * Guarde el fragmento como archivo ZIP; puede definir si desea incluir elementos, variables y metadatos.

* **[!UICONTROL Crear]**
* **[!UICONTROL Cierre de compra]**
* **[!UICONTROL Propiedades]**

   * Permite ver o editar los metadatos del fragmento.

* **[!UICONTROL Editar]**

   * Permite [abrir el fragmento para editar contenido](content-fragments-variations.md) junto con sus elementos, variaciones, contenido asociado y metadatos.

* **[!UICONTROL Administrar etiquetas]**
* **[!UICONTROL A la colección]**

   * Agregue el fragmento a una colección.
   * Esto también se puede hacer cuando [asociación de una colección con el fragmento](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL Copiar/pegar]**
* **[!UICONTROL Mover]**
* **[!UICONTROL Publicación rápida]**
* **[!UICONTROL Administrar publicación]**
* **[!UICONTROL Eliminar]**

>[!NOTE]
>
>Muchos de estos [acciones estándar para Assets](managing-assets-touch-ui.md) y/o [aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=es).

## Apertura del editor de fragmentos {#opening-the-fragment-editor}

Abra el fragmento para su edición:

>[!CAUTION]
>
>Para editar un fragmento de contenido, son necesarios [los permisos adecuados](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Si tiene algún problema, póngase en contacto con el administrador del sistema.

1. Utilice la variable **[!UICONTROL Recursos]** para desplazarse a la ubicación del fragmento de contenido.
1. Abra el fragmento para editarlo mediante:

   * Tocando o haciendo clic en el fragmento o vínculo de fragmento (depende de la vista de la consola).
   * Selección del fragmento y, a continuación, **[!UICONTROL Editar]** en la barra de herramientas.

   Se abrirá el editor de fragmentos:

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Se mostrará un mensaje cuando ya se haga referencia al fragmento en una página de contenido.
   >
   >2. El panel lateral puede ocultarse o mostrarse utilizando el icono **[!UICONTROL Alternar panel lateral]**.


1. Desplácese por los tres modos utilizando los iconos del panel lateral:

   * Variaciones: [Edición del contenido](#editing-the-content-of-your-fragment) y [Administración de variaciones](#creating-and-managing-variations-within-your-fragment)
   * [Anotaciones](content-fragments-variations.md#annotating-a-content-fragment)
   * [Contenido asociado](#associating-content-with-your-fragment)
   * [Metadatos](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. Después de realizar los cambios, utilice **[!UICONTROL Guardar]** o **[!UICONTROL Cancelar]** según sea necesario.

   >[!NOTE]
   >
   >Tanto **[!UICONTROL Guardar]** como **[!UICONTROL Cancelar]** le sacarán del editor; consulte [Guardar, Cancelar y Versiones](#save-cancel-and-versions) para obtener información completa sobre cómo funcionan ambas opciones para los fragmentos de contenido.

## Guardar, cancelar y versiones {#save-cancel-and-versions}

>[!NOTE]
>
>Las versiones también pueden ser [creadas, comparadas y revertidas desde la cronología](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments).

El editor tiene dos opciones:

* **[!UICONTROL Guardar]**

   Guardará los cambios más recientes y cerrará el editor.

   >[!CAUTION]
   >
   >Para editar un fragmento de contenido, son necesarios [los permisos adecuados](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Si tiene algún problema, póngase en contacto con el administrador del sistema.

   >[!NOTE]
   >
   >Es posible permanecer en el editor, realizando una serie de cambios, antes de seleccionar **[!UICONTROL Guardar]**.

   >[!CAUTION]
   >
   >Además de guardar los cambios, **[!UICONTROL Guardar]** también actualiza todas las referencias y garantiza que el despachante se vacíe según sea necesario. Estos cambios pueden tardar un tiempo en procesarse. Debido a esto, puede haber un impacto en el rendimiento de un sistema grande/complejo/con gran carga.
   >
   >
   >Tenga esto en cuenta al utilizar **[!UICONTROL Guardar]** y, a continuación, reintroduciendo rápidamente el editor de fragmentos para realizar y guardar más cambios.

* **[!UICONTROL Cancelar]**

   Saldrá del editor sin guardar los cambios más recientes.

Mientras edita el fragmento de contenido AEM crea versiones automáticamente para garantizar que el contenido anterior se pueda restaurar si **[!UICONTROL Cancelar]** los cambios:

1. Cuando se abre un fragmento de contenido para editarlo, AEM comprueba la existencia del token basado en cookies que indica si existe una *sesión de edición*:

   1. Si se encuentra el token, el fragmento se considera parte de la sesión de edición existente.
   1. Si el token *no* está disponible y el usuario empieza a editar contenido, se crea una versión y se envía un token para esta nueva sesión de edición al cliente, donde se guarda en una cookie.

1. Mientras que haya una sesión de edición *activa*, el contenido que se está editando se guarda automáticamente cada 600 segundos (valor predeterminado).

   >[!NOTE]
   >
   >El intervalo de guardado automático se puede configurar usando el mecanismo `/conf`.
   >
   >Valor predeterminado, consulte:
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. Si el usuario selecciona **[!UICONTROL Cancelar]** Al editar, se restaura la versión creada al principio de la sesión de edición y se elimina el token para finalizar la sesión de edición.
1. Si el usuario selecciona **[!UICONTROL Guardar]** las ediciones, los elementos/variaciones actualizados se mantienen y se elimina el token para finalizar la sesión de edición.

## Edición del contenido del fragmento {#editing-the-content-of-your-fragment}

Una vez que haya abierto el fragmento, puede usar la pestaña [Variaciones](content-fragments-variations.md) para crear el contenido.

## Creación y administración de variaciones dentro del fragmento {#creating-and-managing-variations-within-your-fragment}

Una vez creado el contenido principal, puede crear y administrar, [Variaciones](content-fragments-variations.md) de ese contenido.

## Asociación del contenido al fragmento {#associating-content-with-your-fragment}

También puede [asociar contenido](content-fragments-assoc-content.md) con un fragmento. Esto proporciona una conexión para que los recursos (es decir, las imágenes) se puedan utilizar (opcionalmente) con el fragmento cuando se añada a una página de contenido.

## Visualización y edición de los metadatos (propiedades) del fragmento {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Puede ver y editar las propiedades de un fragmento utilizando la pestaña [[!UICONTROL Metadatos]](content-fragments-metadata.md).

## Cronología de los fragmentos de contenido {#timeline-for-content-fragments}

Además de las opciones estándar, [Cronología](managing-assets-touch-ui.md#timeline) proporciona información y acciones específicas para fragmentos de contenido:

* Ver información sobre versiones, comentarios y anotaciones
* Acciones para las versiones

   * **[[!UICONTROL Revertir a esta versión]](#reverting-to-a-version)** (seleccione un fragmento existente y, a continuación, una versión específica)
   * **[[!UICONTROL Comparar con actual]](#comparing-fragment-versions)** (seleccione un fragmento existente y, a continuación, una versión específica)
   * Agregue una **[!UICONTROL Etiqueta]** o un **[!UICONTROL Comentario]** (seleccione un fragmento existente y, a continuación, una versión específica)
   * **[!UICONTROL Guardar como versión]** (seleccione un fragmento existente y, a continuación, la flecha hacia arriba en la parte inferior de la cronología)

* Acciones para anotaciones

   * **[!UICONTROL Eliminar]**

>[!NOTE]
>
>Los comentarios son lo siguiente:
>
>* De funcionalidad estándar para todos los recursos
>* Realizados en la cronología
>* Relacionados con el recurso de fragmento
>
>Las anotaciones (para fragmentos de contenido) son lo siguiente:
>
>* Introducidas en el editor de fragmentos
>* Específicas para un segmento seleccionado de texto dentro del fragmento


Por ejemplo:

![cfm-6420-19](assets/cfm-6420-19.png)

## Comparación de versiones de fragmento {#comparing-fragment-versions}

La acción **[!UICONTROL Comparar con actual]** está disponible en la [[!UICONTROL Cronología] después de seleccionar una versión específica.](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments)

Se abre lo siguiente:

* el **[!UICONTROL Actual]** (última) versión (izquierda)

* la versión seleccionada **v&lt;*x.y*>** (derecha)

Se mostrarán en paralelo, donde:

* Se resaltan todas las diferencias

   * Texto eliminado en rojo
   * Texto insertado en verde
   * Texto reemplazado en azul

* El icono de pantalla completa le permite abrir cualquiera de las versiones por su cuenta; a continuación, vuelva a la vista paralela
* Puede **[!UICONTROL Revertir]** a la versión específica
* **[!UICONTROL Listo]** le devolverá a la consola

>[!NOTE]
>
>No se puede editar el contenido del fragmento al comparar fragmentos.

![cfm-6420-20](assets/cfm-6420-20.png)

## Reversión a una versión  {#reverting-to-a-version}

Puede volver a una versión específica del fragmento:

* Directamente desde la [[!UICONTROL Cronología]](content-fragments-managing.md#timeline-for-content-fragments).

   Seleccione la versión requerida y, a continuación, la acción **[!UICONTROL Revertir a esta versión]**.

* Mientras [compara una versión con la versión actual](content-fragments-managing.md#comparing-fragment-versions) puede **[!UICONTROL Revertir]** a la versión seleccionada.

## Publicación y referencia de un fragmento {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Si el fragmento se basa en un modelo, debe asegurarse de que [el modelo se ha publicado](content-fragments-models.md#publishing-a-content-fragment-model).
>
>Si publica un fragmento de contenido para el que el modelo aún no se ha publicado, la lista de selección lo indicará y el modelo se publicará con el fragmento.

Los fragmentos de contenido deben publicarse para su uso en el entorno de publicación. Se pueden publicar:

* Después de la creación; de la variable **[!UICONTROL Recursos]** consola.
* Cuando [publicar una página que utilice el fragmento](/help/sites-authoring/content-fragments.md#publishing); el fragmento se enumerará en las referencias de página.

>[!CAUTION]
>
>Después de publicar un fragmento o de hacer referencia a él, AEM mostrará una advertencia cuando un autor abra el fragmento para editarlo de nuevo. Esto sirve para advertir que los cambios en el fragmento también afectarán a las páginas a las que se hace referencia.

## Eliminación de un fragmento {#deleting-a-fragment}

Para eliminar un fragmento:

1. En la consola **[!UICONTROL Recursos]** vaya a la ubicación del fragmento de contenido.
1. Seleccione el fragmento.

   >[!NOTE]
   >
   >La acción **[!UICONTROL Eliminar]** no se encuentra disponible como Acción rápida.

1. En la barra de herramientas, seleccione **[!UICONTROL Eliminar]**.
1. Confirme la acción **[!UICONTROL Eliminar]**.

   >[!CAUTION]
   >
   >Si ya se hace referencia al fragmento en una página, verá un mensaje de advertencia y será necesario para confirmar que desea continuar con la **[!UICONTROL eliminación forzada]**. El fragmento, junto con su componente de fragmento de contenido, se eliminará de cualquier página de contenido.
