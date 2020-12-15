---
title: Administrar fragmentos de contenido
seo-title: Administrar fragmentos de contenido
description: Los fragmentos de contenido se almacenan como recursos, por lo que se administran principalmente desde la consola Recursos.
seo-description: Los fragmentos de contenido se almacenan como recursos, por lo que se administran principalmente desde la consola Recursos.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
translation-type: tm+mt
source-git-commit: 5ba23738118d7944026f405110e25b6a7f90866b
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 11%

---


# Administrar fragmentos de contenido {#managing-content-fragments}

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

Los fragmentos de contenido se almacenan como **[!UICONTROL Recursos]**, por lo que se administran principalmente desde la consola **[!UICONTROL Recursos]**.

>[!NOTE]
>
>A continuación, los fragmentos de contenido se utilizan con las páginas de creación; consulte [Creación de páginas con fragmentos de contenido](/help/sites-authoring/content-fragments.md).

## Creación de fragmentos de contenido {#creating-content-fragments}

### Creación de un modelo de contenido {#creating-a-content-model}

[Los ](content-fragments-models.md) modelos de fragmentos de contenido se pueden habilitar y crear antes de crear fragmentos de contenido con contenido estructurado.

>[!NOTE]
>
>Consulte [Desarrollo de fragmentos de contenido](/help/sites-developing/customizing-content-fragments.md) para obtener más información sobre plantillas. se utiliza para fragmentos de contenido sencillos.

### Creación de un fragmento de contenido {#creating-a-content-fragment}

El método para crear un fragmento de contenido es (básicamente) el mismo para fragmentos simples y estructurados:

1. Vaya a la carpeta **[!UICONTROL Assets]** en la que desea crear el fragmento.
1. Seleccione **[!UICONTROL Crear]** y, a continuación, **[!UICONTROL Fragmento de contenido]** para abrir el asistente.
1. El primer paso del asistente requiere que especifique la base del nuevo fragmento.

   * Puede ser:

      * [Plantilla](/help/sites-developing/content-fragment-templates.md) : por ejemplo, Fragmento  **[!UICONTROL simple]**
      * [Modelo](content-fragments-models.md) : se utiliza para crear un fragmento que requiere contenido estructurado; por ejemplo, el modelo  **** Airportmodel
   * Se muestran todas las plantillas y modelos disponibles.

   Después de la selección, utilice **[!UICONTROL Siguiente]** para continuar.

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

         Obligatorio; se derivará automáticamente del título, pero se puede actualizar.


1. Seleccione **[!UICONTROL Crear]** para completar la acción y, a continuación, **[!UICONTROL Abra]** el fragmento para editarlo o vuelva a la consola pulsando **[!UICONTROL Listo]**.

## Acciones para un fragmento de contenido {#actions-for-a-content-fragment}

En la consola **[!UICONTROL Assets]** hay una serie de acciones disponibles para los fragmentos de contenido, ya sea:

* Desde la barra de herramientas; después de seleccionar el fragmento, todas las acciones correspondientes estarán disponibles.
* Como [acciones rápidas](/help/sites-authoring/basic-handling.md#quick-actions); un subconjunto de acciones disponible para las tarjetas de fragmento individuales.

![cfm-6420-17](assets/cfm-6420-17.png)

Seleccione el fragmento para mostrar la barra de herramientas con las acciones correspondientes:

* **[!UICONTROL Descargar]**

   * Guarde el fragmento como archivo ZIP; puede definir si desea incluir elementos, variaciones y metadatos.

* **[!UICONTROL Crear]**
* **[!UICONTROL Cierre de compra]**
* **[!UICONTROL Propiedades]**

   * Permite realizar vistas o editar los metadatos del fragmento.

* **[!UICONTROL Editar]**

   * Le permite [abrir el fragmento para editar contenido](content-fragments-variations.md) junto con sus elementos, variaciones, contenido asociado y metadatos.

* **[!UICONTROL Administrar etiquetas]**
* **[!UICONTROL A la colección]**

   * Añada el fragmento en una colección.
   * Esto también se puede hacer cuando [asocia una colección con el fragmento](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL Copiar/Pegar]**
* **[!UICONTROL Mover]**
* **[!UICONTROL Publicación rápida]**
* **[!UICONTROL Administrar publicación]**
* **[!UICONTROL Eliminar]**

>[!NOTE]
>
>Muchas de ellas son [acciones estándar para Assets](managing-assets-touch-ui.md) y/o la [aplicación de escritorio](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

## Apertura del Editor de fragmentos {#opening-the-fragment-editor}

Para abrir el fragmento y editarlo:

>[!CAUTION]
>
>Para editar un fragmento de contenido necesita [los permisos correspondientes](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Póngase en contacto con el administrador del sistema si tiene problemas.

1. Utilice la consola **[!UICONTROL Assets]** para desplazarse a la ubicación del fragmento de contenido.
1. Abra el fragmento para editarlo mediante una de las acciones siguientes:

   * Al tocar o hacer clic en el vínculo de fragmento o fragmento (esto depende de la vista de la consola).
   * Seleccione el fragmento y, a continuación, **[!UICONTROL Editar]** desde la barra de herramientas.

   Se abrirá el editor de fragmentos:

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Se mostrará un mensaje cuando ya se haga referencia al fragmento en una página de contenido.
      >
      >
   2. El panel lateral puede ocultarse o mostrarse mediante el icono **[!UICONTROL Alternar panel lateral]**.


1. Navegue por los tres modos utilizando los iconos del panel lateral:

   * Variaciones: [Edición del contenido](#editing-the-content-of-your-fragment) y [Administración de las variaciones](#creating-and-managing-variations-within-your-fragment)
   * [Anotaciones](content-fragments-variations.md#annotating-a-content-fragment)
   * [Contenido asociado](#associating-content-with-your-fragment)
   * [Metadatos](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. Después de realizar cambios, utilice **[!UICONTROL Guardar]** o **[!UICONTROL Cancelar]** según sea necesario.

   >[!NOTE]
   >
   >Tanto **[!UICONTROL Guardar]** como **[!UICONTROL Cancelar]** le sacarán del editor; consulte [Guardar, Cancelar y Versiones](#save-cancel-and-versions) para obtener información completa sobre cómo funcionan ambas opciones para los fragmentos de contenido.

## Guardar, Cancelar y Versiones {#save-cancel-and-versions}

>[!NOTE]
>
>Las versiones también se pueden [crear, comparar y revertir desde la línea de tiempo](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments).

El editor tiene dos opciones:

* **[!UICONTROL Guardar]**

   Guardará los cambios más recientes y saldrá del editor.

   >[!CAUTION]
   >
   >Para editar un fragmento de contenido necesita [los permisos correspondientes](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Póngase en contacto con el administrador del sistema si tiene problemas.

   >[!NOTE]
   >
   >Es posible permanecer en el editor, realizando una serie de cambios, antes de seleccionar **[!UICONTROL Guardar]**.

   >[!CAUTION]
   >
   >Además de simplemente guardar los cambios, **[!UICONTROL Guardar]** también actualiza las referencias y garantiza que el despachante se borre según sea necesario. Estos cambios pueden llevar tiempo para procesarse. Debido a esto, puede haber un impacto en el rendimiento de un sistema grande/complejo/sobrecargado.
   >
   >
   >Tenga esto en cuenta cuando utilice **[!UICONTROL Guardar]** y luego vuelva a introducir rápidamente el editor de fragmentos para realizar y guardar más cambios.

* **[!UICONTROL Cancelar]**

   Saldrá del editor sin guardar los cambios más recientes.

Al editar el fragmento de contenido, AEM crea automáticamente versiones para garantizar que el contenido anterior se pueda restaurar si **[!UICONTROL cancela]** los cambios:

1. Cuando se abre un fragmento de contenido para editarlo AEM comprueba la existencia del token basado en cookies que indica si existe una *sesión de edición*:

   1. Si se encuentra el token, el fragmento se considera parte de la sesión de edición existente.
   1. Si el token *no* está disponible y el usuario inicio el contenido que está editando, se crea una versión y se envía un token para esta nueva sesión de edición al cliente, donde se guarda en una cookie.

1. Aunque existe una sesión de edición *activa*, el contenido que se está editando se guarda automáticamente cada 600 segundos (predeterminado).

   >[!NOTE]
   >
   >El intervalo de guardado automático se puede configurar mediante el mecanismo `/conf`.
   >
   >Valor predeterminado, consulte:
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. Si el usuario selecciona **[!UICONTROL Cancelar]** la edición, se restaura la versión creada en el inicio de la sesión de edición y se elimina el token para finalizar la sesión de edición.
1. Si el usuario selecciona **[!UICONTROL Guardar]** las ediciones, los elementos o variaciones actualizados se conservan y se elimina el token para finalizar la sesión de edición.

## Edición del contenido del fragmento {#editing-the-content-of-your-fragment}

Una vez abierto el fragmento, puede utilizar la ficha [Variaciones](content-fragments-variations.md) para crear el contenido.

## Creación y administración de variaciones dentro del fragmento {#creating-and-managing-variations-within-your-fragment}

Una vez creado el contenido principal, puede crear y administrar [Variaciones](content-fragments-variations.md) de dicho contenido.

## Asociación de contenido con el fragmento {#associating-content-with-your-fragment}

También puede [asociar contenido](content-fragments-assoc-content.md) con un fragmento. Esto proporciona una conexión para que los recursos (es decir, las imágenes) se puedan utilizar (opcionalmente) con el fragmento cuando se agregan a una página de contenido.

## Visualización y edición de metadatos (propiedades) del fragmento {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Puede vista y edición de las propiedades de un fragmento mediante la ficha [[!UICONTROL Metadatos]](content-fragments-metadata.md).

## Cronología para fragmentos de contenido {#timeline-for-content-fragments}

Además de las opciones estándar, [Timeline](managing-assets-touch-ui.md#timeline) proporciona información y acciones específicas de los fragmentos de contenido:

* Información de vista sobre versiones, comentarios y anotaciones
* Acciones para versiones

   * **[[!UICONTROL Revertir a esta versión]](#reverting-to-a-version)**  (seleccione un fragmento existente y, a continuación, una versión específica)
   * **[[!UICONTROL Comparar con actual]](#comparing-fragment-versions)**  (seleccione un fragmento existente y, a continuación, una versión específica)
   * Añadir una **[!UICONTROL etiqueta]** y/o **[!UICONTROL comentario]** (seleccionar un fragmento existente y luego una versión específica)
   * **[!UICONTROL Guardar como versión]**  (seleccione un fragmento existente y, a continuación, la flecha hacia arriba en la parte inferior de la línea de tiempo)

* Acciones para anotaciones

   * **[!UICONTROL Eliminar]**

>[!NOTE]
>
>Los comentarios son:
>
>* Funcionalidad estándar para todos los recursos
>* Realizado en la línea de tiempo
>* Relacionado con el recurso de fragmento

>
>
Las anotaciones (para fragmentos de contenido) son:
>
>* Introducido en el editor de fragmentos
>* Específico para un segmento seleccionado de texto dentro del fragmento


Por ejemplo:

![cfm-6420-19](assets/cfm-6420-19.png)

## Comparación de versiones de fragmento {#comparing-fragment-versions}

La acción **[!UICONTROL Comparar con actual]** está disponible en la [[!UICONTROL cronología]](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments) después de seleccionar una versión específica.

Se abrirá:

* la versión **[!UICONTROL Actual]** (más reciente) (izquierda)

* la versión seleccionada **v&lt;*x.y*>** (derecha)

Se mostrarán en paralelo, donde:

* Se resaltan todas las diferencias

   * Texto eliminado: rojo
   * Texto insertado: verde
   * Texto reemplazado - azul

* El icono de pantalla completa le permite abrir cualquiera de las versiones por su cuenta; a continuación, vuelva a la vista paralela
* Puede **[!UICONTROL revertir]** a la versión específica
* **** Donewill le devolverá a la consola

>[!NOTE]
>
>No se puede editar el contenido del fragmento al comparar fragmentos.

![cfm-6420-20](assets/cfm-6420-20.png)

## Revertir a una versión {#reverting-to-a-version}

Puede volver a una versión específica del fragmento:

* Directamente desde la [[!UICONTROL Línea de tiempo]](content-fragments-managing.md#timeline-for-content-fragments).

   Seleccione la versión requerida y, a continuación, la acción **[!UICONTROL Revertir a esta versión]**.

* Mientras [compara una versión con la versión actual](content-fragments-managing.md#comparing-fragment-versions) puede **[!UICONTROL Revertir]** a la versión seleccionada.

## Publicación y referencia de un fragmento {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Si el fragmento se basa en un modelo, debe asegurarse de que el modelo [se ha publicado](content-fragments-models.md#publishing-a-content-fragment-model).
>
>Si publica un fragmento de contenido para el que el modelo aún no se ha publicado, una lista de selección lo indicará y el modelo se publicará con el fragmento.

Los fragmentos de contenido deben publicarse para su uso en el entorno de publicación. Pueden publicarse:

* Después de la creación; desde la consola **[!UICONTROL Assets]**.
* Cuando [publica una página que utiliza el fragmento](/help/sites-authoring/content-fragments.md#publishing); el fragmento se enumerará en las referencias de página.

>[!CAUTION]
>
>Después de publicar un fragmento o de hacer referencia a él, AEM mostrará una advertencia cuando un autor abra el fragmento para editarlo de nuevo. Esto sirve para advertir que los cambios en el fragmento también afectarán a las páginas a las que se hace referencia.

## Eliminación de un fragmento {#deleting-a-fragment}

Para eliminar un fragmento:

1. En la consola **[!UICONTROL Assets]** navegue a la ubicación del fragmento de contenido.
1. Seleccione el fragmento.

   >[!NOTE]
   >
   >La acción **[!UICONTROL Eliminar]** no está disponible como acción rápida.

1. Seleccione **[!UICONTROL Eliminar]** en la barra de herramientas.
1. Confirme la acción **[!UICONTROL Eliminar]**.

   >[!CAUTION]
   >
   >Si ya se hace referencia al fragmento en una página, verá un mensaje de advertencia y será necesario para confirmar que desea continuar con la **[!UICONTROL eliminación forzada]**. El fragmento, junto con su componente de fragmento de contenido, se eliminará de cualquier página de contenido.

