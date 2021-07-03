---
title: Esquemas de metadatos
description: 'El esquema de metadatos define el diseño de la página de propiedades y las propiedades de metadatos que se muestran para los recursos. Obtenga información sobre cómo crear un esquema de metadatos personalizado, editar un esquema de metadatos y cómo aplicar un esquema de metadatos a los recursos.  '
contentOwner: AG
feature: Metadatos
role: User,Admin
exl-id: 82f42bb3-2c01-407c-a41b-9abe7be4660e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 12%

---

# Esquemas de metadatos {#metadata-schemas}

En [!DNL Experience Manager Assets], un esquema de metadatos define el diseño de la página de propiedades y las propiedades de metadatos que se muestran para los recursos que utilizan el esquema en particular. Las propiedades de metadatos incluyen título, descripción, tipos MIME, etiquetas, etc. Puede utilizar el editor de Forms de esquemas de metadatos para modificar esquemas existentes o añadir esquemas de metadatos personalizados.

Para ver y editar la página de propiedades de un recurso, siga estos pasos:

1. Toque o haga clic en **[!UICONTROL Ver propiedades]** desde las acciones rápidas en el mosaico de recursos en la vista de tarjeta.

   ![chlimage_1-170](assets/chlimage_1-170.png)

   Como alternativa, seleccione un recurso y, a continuación, toque o haga clic en el icono **[!UICONTROL Propiedades]** de la barra de herramientas.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Puede editar las distintas propiedades de metadatos editables en las pestañas disponibles. Sin embargo, no puede modificar el recurso [!UICONTROL Type] en la pestaña [!UICONTROL Basic] de la página de propiedades.

   ![chlimage_1-172](assets/chlimage_1-172.png)

   Para modificar el tipo MIME de un recurso, utilice un formulario de esquema de metadatos personalizado o modifique un formulario existente. Consulte [Edición del esquema de metadatos Forms](metadata-schemas.md#editing-metadata-schema-forms) para obtener más información. Si modifica el esquema de metadatos para un determinado tipo MIME, se modifican el diseño de la página de propiedades de los recursos con el tipo MIME actual y todos los subtipos de recursos. Por ejemplo, modificar un esquema `jpeg` en `default/image` solo modifica el diseño de metadatos (propiedades de recursos) para los recursos con tipo MIME `IMAGE/JPEG`. Sin embargo, si edita el esquema predeterminado, los cambios modificarán el diseño de metadatos para todos los tipos de recursos.

## Formularios de esquema de metadatos {#default-metadata-schema-forms}

Para ver una lista de formularios/plantillas, en la interfaz [!DNL Experience Manager] vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Assets]** > **[!UICONTROL Esquemas de metadatos]**.

[!DNL Experience Manager] proporciona las siguientes plantillas de formulario de esquema de metadatos:

| Plantillas |  | Descripción |
|---|---|---|
| [!UICONTROL predeterminada] |  | Formulario de esquema de metadatos base para los recursos. |
|  | Los siguientes formularios secundarios heredan las propiedades del formulario [!UICONTROL predeterminado]: |  |
|  | <ul><li> [!UICONTROL dm_video]</li></ul> | Formulario de esquema para vídeos de Dynamic Media. |
|  | <ul><li> [!UICONTROL image]</li></ul> | Formulario de esquema para recursos con el tipo MIME &quot;image&quot;, por ejemplo, image/jpeg, image/png, etc. <br> La   forma de imagen tiene las siguientes plantillas de formulario secundarias: <ul><li> [!UICONTROL jpeg]: Formulario de esquema para recursos con subtipo  [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: Formulario de esquema para los recursos con subtipo  [!UICONTROL tiff].</li></ul> |
|  | <ul><li> [!UICONTROL aplicación]</li></ul> | Formulario de esquema para recursos con tipo MIME &quot;aplicación&quot;, por ejemplo application/ pdf, application/ zip, etc. <br>[!UICONTROL pdf]: Formulario de esquema para recursos con subtipo pdf. |
|  | <ul><li>[!UICONTROL vídeo]</li></ul> | Formulario de esquema para recursos con tipo MIME &quot;video&quot;, como video/avi, video/mp4, etc. |
| [!UICONTROL colección] |  | Formulario de esquema para colecciones. |
| [!UICONTROL contentfragment] |  | Formulario de esquema para fragmentos de contenido. |
| [!UICONTROL formularios] |  | Este formulario de esquema está relacionado con [Adobe Experience Manager Forms](/help/forms/home.md). |

>[!NOTE]
>
>Para ver los formularios secundarios de un formulario de esquema, toque o haga clic en el nombre del formulario de esquema.

## Agregar un formulario de esquema de metadatos {#adding-a-metadata-schema-form}

1. Para agregar una plantilla personalizada a la lista, haga clic en **[!UICONTROL Crear]** en la barra de herramientas.

   >[!NOTE]
   >
   >Las plantillas actualizadas muestran un icono de bloqueo antes de ellas. Si personaliza cualquiera de las plantillas, desaparece el icono de bloqueo antes de la plantilla.

1. En el cuadro de diálogo, introduzca el título del formulario de esquema y haga clic en **[!UICONTROL Create]** para completar el proceso de creación del formulario.

   ![chlimage_1-174](assets/chlimage_1-174.png)

## Edición de formularios de esquema de metadatos {#editing-metadata-schema-forms}

Puede editar un formulario de esquema de metadatos nuevo o existente. El formulario de esquema de metadatos incluye lo siguiente:

* Pestañas
* Elementos de formulario dentro de las pestañas.

Puede asignar/configurar estos elementos de formulario a un campo dentro de un nodo de metadatos en el repositorio CRX.

Puede agregar nuevas fichas o elementos de formulario al formulario de esquema de metadatos. Las fichas y los elementos de formulario derivados del elemento principal están en estado bloqueado. No se pueden modificar en el nivel secundario.

1. En la página **[!UICONTROL Schema Forms]**, active la casilla de verificación situada antes de un formulario y, a continuación, haga clic en **[!UICONTROL Edit]** en la barra de herramientas.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. En la página **[!UICONTROL Editor de esquemas de metadatos]**, personalice la página de propiedades del recurso arrastrando uno o varios componentes de la lista de tipos de componentes de la pestaña **[!UICONTROL Generar formulario]** a **[!UICONTROL Básico]**.

   ![chlimage_1-176](assets/chlimage_1-176.png)

1. Para configurar un componente, selecciónelo y modifique sus propiedades en la pestaña **[!UICONTROL Settings]**.

### Componentes de la ficha Generar formulario {#components-within-the-build-form-tab}

La ficha **[!UICONTROL Generar formulario]** enumera los elementos de formulario que utiliza en el formulario de esquema. La pestaña **[!UICONTROL Settings]** proporciona los atributos de cada elemento que seleccione en la ficha **[!UICONTROL Generar formulario]**. La tabla siguiente muestra los elementos de formulario disponibles en la ficha **[!UICONTROL Generar formulario]**:

| Nombre del componente | Descripción |
|---|---|
| [!UICONTROL Sección de encabezado] | Añada un encabezado de sección para ver una lista de componentes comunes. |
| [!UICONTROL Texto de una sola línea] | Agregue una propiedad de texto de una sola línea. Se almacena como una cadena. |
| [!UICONTROL Texto con varios valores] | Agregue una propiedad de texto de varios valores. Se almacena como una matriz de cadenas. |
| [!UICONTROL Número] | Añada un componente numérico. |
| [!UICONTROL Fecha] | Añada un componente de fecha. |
| [!UICONTROL Lista desplegable] | Añada una lista desplegable. |
| [!UICONTROL Etiquetas estándar] | Añadir una etiqueta. |
| [!UICONTROL Etiquetas inteligentes] | Añada a las capacidades de búsqueda de aumento añadiendo automáticamente etiquetas de metadatos. |
| [!UICONTROL Campo oculto] | Añada un campo oculto. Se envía como parámetro de POST cuando se guarda el recurso. |
| [!UICONTROL Recurso al que se hace referencia en] | Añada este componente para ver la lista de recursos a los que hace referencia el recurso. |
| [!UICONTROL Referencia de recursos] | Agregar para mostrar una lista de recursos que hacen referencia al recurso. |
| [!UICONTROL Referencias de productos] | Agregar para mostrar la lista de productos vinculados al recurso. |
| [!UICONTROL Clasificación del recurso] | Añada para mostrar las opciones de clasificación del recurso. |
| [!UICONTROL Metadatos de contexto] | Añadir para controlar la visualización de otras pestañas de metadatos en la página de propiedades de los recursos. |

### Editar el componente de metadatos {#editing-the-metadata-component}

Para editar las propiedades de un componente de metadatos en el formulario, haga clic en el componente y edite todas o un subconjunto de las siguientes propiedades en la pestaña **[!UICONTROL Settings]**.

**Etiqueta** de campo: Nombre de la propiedad de metadatos que se muestra en la página de propiedades del recurso.

**Asignar a propiedad**: Esta propiedad especifica la ruta/nombre relativo al nodo de recurso donde se guarda en el repositorio CRX. Comienza con `./` porque indica que la ruta está bajo el nodo del recurso.

Los siguientes son los valores válidos para esta propiedad:

* `./jcr:content/metadata/dc:title`: Almacena el valor en el nodo de metadatos del recurso como propiedad `dc:title`.

* `./jcr:created`: Muestra la propiedad JCR en el nodo del recurso. Si configura estas propiedades en propiedades de vista, le recomendamos que las marque como Deshabilitar edición, ya que están protegidas. De lo contrario, el error [!UICONTROL Asset(s) no pudo modificar los resultados] al guardar las propiedades del recurso.

Para asegurarse de que el componente se muestra correctamente en el formulario de esquema de metadatos, la ruta de la propiedad no debe incluir espacios.

**Marcador de posición**: Utilice esta propiedad para especificar el texto del marcador de posición correspondiente a la propiedad metadata.

**Requerido**: Utilice esta propiedad para marcar una propiedad de metadatos como obligatoria en la página de propiedades.

**Desactivar edición**: Utilice esta propiedad para que una propiedad de metadatos no se pueda editar en la página de propiedades.

**Mostrar Campo Vacío En Solo** Lectura: Marque esta propiedad para mostrar una propiedad de metadatos en la página de propiedades aunque no tenga ningún valor. De forma predeterminada, cuando una propiedad de metadatos no tiene ningún valor, no aparece en la página de propiedades.

**Mostrar lista ordenada**: Utilice esta propiedad para mostrar una lista ordenada de opciones

**Opciones**: Utilice esta propiedad para especificar opciones en una lista

**Descripción** : Utilice esta propiedad para añadir una breve descripción para el componente de metadatos.

**Clase**: Clase de objeto a la que está asociada la propiedad.

**Icono Eliminar** Haga clic en este icono para eliminar un componente del formulario de esquema.

>[!NOTE]
>
>El componente Campo oculto no incluye estos atributos. En su lugar, incluye propiedades como Nombre, Valor, Etiqueta de campo y Descripción. Los valores del componente Campo oculto se envían como parámetro de POST cada vez que se guarda el recurso. No se guarda como metadatos para el recurso.

Si selecciona la opción **[!UICONTROL Obligatorio]**, puede buscar recursos que no tengan metadatos obligatorios. En el panel **[!UICONTROL Filtros]**, expanda el predicado **[!UICONTROL Validación de metadatos]** y seleccione la opción **[!UICONTROL No válido]**. Los resultados de la búsqueda muestran los recursos que carecen de metadatos obligatorios configurados a través del formulario de esquema.

![chlimage_1-178](assets/chlimage_1-178.png)

Si agrega el componente Metadatos contextuales a cualquier ficha de cualquier formulario de esquema, el componente aparece como una lista en la página de propiedades de los recursos a los que se aplica el esquema en particular. La lista incluye todas las demás fichas excepto la ficha a la que se aplicó el componente Metadatos contextuales . Actualmente, esta función proporciona funcionalidad básica para controlar la visualización de metadatos en función del contexto.

![chlimage_1-179](assets/chlimage_1-179.png)

Para incluir cualquier pestaña en la página de propiedades además de la pestaña donde se aplica el componente Metadatos contextuales, seleccione la pestaña de la lista. La pestaña se agrega a la página de propiedades.

![chlimage_1-180](assets/chlimage_1-180.png)

### Especificar propiedades en un archivo JSON {#specifying-properties-in-json-file}

En lugar de especificar propiedades para las opciones de la pestaña **[!UICONTROL Configuración]**, puede definir las opciones de un archivo JSON especificando los pares de clave-valor correspondientes. Especifique la ruta del archivo JSON en el campo **[!UICONTROL Ruta de JSON]**.

### Agregar o eliminar una ficha del formulario de esquema {#adding-deleting-a-tab-in-the-schema-form}

El editor de esquemas permite agregar o eliminar una pestaña. El formulario de esquema predeterminado incluye las pestañas **[!UICONTROL Básico]**, **[!UICONTROL Avanzado]**, **[!UICONTROL IPTC]** y **[!UICONTROL Extensión IPTC]** de forma predeterminada.

![chlimage_1-181](assets/chlimage_1-181.png)

Haga clic en `+` para agregar una nueva pestaña en un formulario de esquema. De forma predeterminada, la nueva pestaña tiene el nombre `Unnamed-1`. Puede modificar el nombre desde la pestaña **[!UICONTROL Settings]**. Haga clic en `X` para eliminar una pestaña.

![chlimage_1-182](assets/chlimage_1-182.png)

## Eliminación de formularios de esquema de metadatos {#deleting-metadata-schema-forms}

AEM permite eliminar solo los formularios de esquema personalizados. No permite eliminar los formularios o plantillas de esquema predeterminados. Sin embargo, puede eliminar cualquier cambio personalizado en estos formularios.

Para eliminar un formulario, seleccione un formulario y haga clic en el icono **[!UICONTROL Delete]**.

>[!NOTE]
>
>Después de eliminar los cambios personalizados en un formulario predeterminado, el icono de bloqueo vuelve a aparecer en la interfaz del esquema de metadatos para indicar que el formulario ha vuelto a su estado predeterminado.

>[!NOTE]
>
>No se pueden eliminar los formularios de esquema de metadatos predefinidos en AEM Assets.

## Formularios de esquema para tipos MIME {#schema-forms-for-mime-types}

AEM Assets proporciona formularios predeterminados para varios tipos de MIME predeterminados. Sin embargo, puede agregar formularios personalizados para recursos de varios tipos de MIME.

### Agregar nuevos formularios para tipos MIME {#adding-new-forms-for-mime-types}

Cree un nuevo formulario bajo el tipo de formulario correspondiente. Por ejemplo, para agregar una nueva plantilla para el subtipo `image/png`, cree el formulario en los formularios `image`. El título del formulario de esquema es el nombre del subtipo. En este caso, el título es `png`.

### Usar una plantilla de esquema existente para varios tipos MIME {#using-an-existing-schema-template-for-various-mime-types}

Puede utilizar una plantilla existente para un tipo MIME diferente. Por ejemplo, utilice el formulario `image/jpeg` para los recursos de tipo MIME `image/png`.

En este caso, cree un nuevo nodo en `/etc/dam/metadataeditor/mimetypemappings` en el repositorio CRX. Especifique un nombre para el nodo y defina las siguientes propiedades:

| Nombre | Descripción | Tipo | Value |
|---|---|---|---|
| `exposedmimetype` | Nombre del formulario existente a asignar | `String` | `image/jpeg` |
| `mimetypes` | Lista de tipos MIME que utilizan el formulario definido en el atributo `exposedmimetype` | `String` | `image/png` |

AEM Assets asigna los siguientes tipos MIME y formularios de esquema:

| Formulario de esquema | Tipos MIME |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Conceder acceso a esquemas de metadatos {#granting-access-to-metadata-schemas}

La función de esquema de metadatos solo está disponible para administradores. Sin embargo, los administradores pueden proporcionar acceso a usuarios que no sean administradores si proporcionan permisos de **[!UICONTROL Crear]**, **[!UICONTROL Modificar]** y **[!UICONTROL Eliminar]** en la carpeta `/conf`.

## Aplicar metadatos específicos de carpetas {#applying-folder-specific-metadata}

AEM Assets permite definir una variante de un esquema de metadatos y aplicarla a una carpeta específica.

Por ejemplo, puede definir una variante del esquema de metadatos predeterminado y aplicarla a una carpeta. Cuando se aplica el esquema modificado, anula el esquema de metadatos predeterminado original que se aplica a los recursos de la carpeta.

Solo los recursos cargados en la carpeta a la que se aplica este esquema se ajustan a los metadatos modificados definidos en el esquema de metadatos de la variante.

Los recursos de otras carpetas donde se aplica el esquema original siguen ajustándose a los metadatos definidos en el esquema original.

La herencia de metadatos por recursos se basa en el esquema que se aplica a la carpeta de primer nivel de la jerarquía. En otras palabras, si una carpeta no contiene subcarpetas, los recursos de la carpeta heredan los metadatos del esquema aplicado a la carpeta.

Si la carpeta tiene una subcarpeta, los recursos de la subcarpeta heredan los metadatos del esquema aplicado en el nivel de subcarpeta si se aplica un esquema diferente en el nivel de subcarpeta. Sin embargo, si no se aplica ningún esquema o el mismo esquema en el nivel de subcarpeta, los recursos de subcarpeta heredan los metadatos del esquema aplicado en el nivel de carpeta principal.

1. Haga clic en el logotipo de AEM y, a continuación, vaya a **[!UICONTROL Herramientas > Assets > Esquemas de metadatos]**. Se muestra la página **[!UICONTROL Formularios de esquema de metadatos]**.
1. Seleccione la casilla de verificación situada antes de un formulario, por ejemplo el formulario de metadatos predeterminado, y pulse o haga clic en el icono **[!UICONTROL Copiar]** y guárdelo como un formulario personalizado. Especifique un nombre personalizado para el formulario, por ejemplo `my_default`. También puede crear un formulario personalizado.

   ![chlimage_1-184](assets/chlimage_1-184.png)

1. En la página **[!UICONTROL Metadata Schema Forms]**, seleccione el formulario `my_default` y, a continuación, haga clic en **[!UICONTROL Editar]**.

1. En la página **[!UICONTROL Editor de esquemas de metadatos]**, agregue un campo de texto al formulario de esquema. Por ejemplo, agregue un campo con la etiqueta **[!UICONTROL Category]**.

   ![chlimage_1-186](assets/chlimage_1-186.png)

1. Haga clic en **[!UICONTROL Guardar]**. El formulario modificado se muestra en la página **[!UICONTROL Forms]** del esquema de metadatos.
1. Pulse o haga clic **[!UICONTROL Aplicar a las carpetas]** en la barra de herramientas para aplicar los metadatos personalizados a una carpeta.

   ![chlimage_1-187](assets/chlimage_1-187.png)

1. Seleccione la carpeta en la que desea aplicar el esquema modificado y, a continuación, pulse o haga clic en **[!UICONTROL Aplicar]**.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Si se ha aplicado el otro esquema de metadatos a la carpeta, aparece un mensaje en el que se advierte que está a punto de sobrescribir el esquema de metadatos existente. Haga clic en **[!UICONTROL Sobrescribir]**.
1. Haga clic en **[!UICONTROL OK]** para cerrar el mensaje de éxito.
1. Vaya a la carpeta a la que aplicó el esquema de metadatos modificado.

## Definición de metadatos obligatorios {#defining-mandatory-metadata}

Puede definir campos obligatorios a nivel de carpeta, que se aplican a los recursos que se cargan en la carpeta. Si carga recursos con metadatos que faltan para los campos obligatorios definidos anteriormente, en la vista Tarjeta aparecerá una indicación visual de los metadatos que faltan en los recursos.

>[!NOTE]
>
>Un campo de metadatos se puede definir como obligatorio en función del valor de otro campo. En la vista Tarjetas, AEM no muestra el mensaje de advertencia sobre la falta de metadatos para estos campos de metadatos obligatorios.

1. Haga clic en el logotipo de AEM y, a continuación, vaya a **[!UICONTROL Herramientas > Assets > Esquemas de metadatos]**. Se muestra la página **[!UICONTROL Formularios de esquema de metadatos]**.
1. Guarde el formulario de metadatos predeterminado como un formulario personalizado. Por ejemplo, guárdelo como `my_default`.

   ![chlimage_1-189](assets/chlimage_1-189.png)

1. Edite el formulario personalizado. Añada un campo obligatorio. Por ejemplo, agregue un campo **Category** y haga que el campo sea obligatorio.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Haga clic en **[!UICONTROL Guardar]**. El formulario modificado se muestra en la página **[!UICONTROL Forms]** del esquema de metadatos. Para aplicar los metadatos personalizados a una carpeta, seleccione el formulario y pulse o haga clic en **[!UICONTROL Aplicar a las carpetas]** en la barra de herramientas.

1. Vaya a la carpeta y cargue algunos recursos con metadatos que faltan para el campo obligatorio que ha agregado al formulario personalizado. La vista de tarjeta de los recursos muestra un mensaje para los metadatos que faltan para el campo obligatorio.

   ![chlimage_1-192](assets/chlimage_1-192.png)

1. (Opcional) Acceda a `http://[server]:[port]/system/console/components/`. Configure y habilite el componente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` que está deshabilitado de forma predeterminada. Establezca una frecuencia con la que AEM compruebe la validez de los metadatos en los recursos.
Esta configuración añade una propiedad `hasValidMetadata` a jcr:content de los recursos. Con esta propiedad, AEM filtrar los resultados en una búsqueda.

>[!NOTE]
>
>Si se agrega un recurso después de la comprobación programada, el recurso no se marca con `hasValidMetadata` hasta la siguiente comprobación programada. Los recursos no aparecen en los resultados de búsqueda intermedios.

>[!CAUTION]
>
>Las comprobaciones de validación de metadatos requieren muchos recursos y pueden afectar al rendimiento del sistema. Programe las comprobaciones según corresponda. Si la implementación AEM tiene problemas de rendimiento, intente deshabilitar este trabajo.
