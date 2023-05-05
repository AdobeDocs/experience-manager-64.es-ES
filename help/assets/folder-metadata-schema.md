---
title: Esquema de metadatos de carpeta
description: Este artículo describe cómo crear un esquema de metadatos para carpetas de recursos en [!DNL Experience Manager] Recursos
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 286a4f26-c0ad-4691-80d8-d17ba1a2dfe0
discoiquuid: 92eacea5-7511-48ce-8a72-ff4552ebb07d
feature: Metadata
role: User,Admin
exl-id: 1bc72dac-41f7-4593-aaea-d48ebd94b43e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 8%

---

# Esquema de metadatos de carpeta {#folder-metadata-schema}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Este artículo describe cómo crear un esquema de metadatos para carpetas de recursos en [!DNL Experience Manager] Recursos.

Adobe Experience Manager Assets permite crear esquemas de metadatos para carpetas de recursos, que definen el diseño y los metadatos que se muestran en las páginas de propiedades de las carpetas.

>[!NOTE]
>
>Esta funcionalidad requiere [!DNL Experience Manager] 6.4 con al menos el Service Pack 2 implementado. Para [!DNL Experience Manager] Detalles del Service Pack 6.4, consulte estos [notas de la versión](/help/release-notes/sp-release-notes.md).

## Agregar un formulario de esquema de metadatos de carpeta {#add-a-folder-metadata-schema-form}

Utilice el editor Forms de Esquemas de metadatos de carpeta para crear y editar esquemas de metadatos para carpetas.

1. Toque o haga clic en el botón [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Recursos]**> **[!UICONTROL Esquemas de metadatos de carpeta]**.
1. En la página Forms Esquema de metadatos de carpeta , pulse o haga clic en **[!UICONTROL Crear]**.
1. Especifique un nombre para el formulario y toque o haga clic en **[!UICONTROL Crear]**. El nuevo formulario de esquema aparece en la página Esquema de Forms.

## Editar formularios de esquema de metadatos de carpeta {#edit-folder-metadata-schema-forms}

Puede editar un formulario de esquema de metadatos nuevo o existente, que incluye lo siguiente:

* Pestañas
* Elementos de formulario dentro de las pestañas.

Puede asignar/configurar estos elementos de formulario a un campo dentro de un nodo de metadatos en el repositorio CRX. Puede agregar nuevas fichas o elementos de formulario al formulario de esquema de metadatos.

1. En la página Esquema de Forms, seleccione el formulario que ha creado y, a continuación, toque o haga clic en el **[!UICONTROL Editar]** de la barra de herramientas.
1. En la página Editor de esquemas de metadatos de carpeta , pulse o haga clic en el **[!UICONTROL +]** para agregar una ficha al formulario. Para cambiar el nombre de la pestaña, toque o haga clic en el nombre predeterminado y especifique el nuevo nombre en **[!UICONTROL Configuración]**.

   ![custom_tab](assets/custom_tab.png)

   Para agregar más pestañas, toque o haga clic en el botón **[!UICONTROL +]** icono. Toque o haga clic **[!UICONTROL X]** para eliminar una pestaña.

1. En la pestaña activa, añada uno o varios componentes de la **[!UICONTROL Generar formulario]** pestaña .

   ![add_components](assets/adding_components.png)

   Si crea varias fichas, toque o haga clic en una ficha concreta para agregar componentes.

1. Para configurar un componente, selecciónelo y modifique sus propiedades en el **[!UICONTROL Configuración]** pestaña .

   Si es necesario, elimine un componente del **[!UICONTROL Configuración]** pestaña .

   ![configure_properties](assets/configure_properties.png)

1. Toque o haga clic **[!UICONTROL Guardar]** en la barra de herramientas para guardar los cambios.

### Componentes para crear formularios {#components-to-build-forms}

La variable **[!UICONTROL Generar formulario]** lista los elementos de formulario que se utilizan en el formulario de esquema de metadatos de la carpeta. La variable **[!UICONTROL Configuración]** muestra los atributos de cada elemento que seleccione en la **[!UICONTROL Generar formulario]** pestaña . Esta es una lista de los elementos de formulario disponibles en la **[!UICONTROL Generar formulario]** pestaña:

| Nombre del componente | Descripción |
|---|---|
| [!UICONTROL Encabezado de sección] | Añada un encabezado de sección para ver una lista de componentes comunes. |
| [!UICONTROL Texto de una sola línea] | Agregue una propiedad de texto de una sola línea. Se almacena como una cadena. |
| [!UICONTROL Texto con varios valores] | Agregue una propiedad de texto de varios valores. Se almacena como una matriz de cadenas. |
| [!UICONTROL Número] | Añada un componente numérico. |
| [!UICONTROL Fecha] | Añada un componente de fecha. |
| [!UICONTROL Lista desplegable] | Añada una lista desplegable. |
| [!UICONTROL Etiquetas estándar] | Añadir una etiqueta. |
| [!UICONTROL Campo oculto] | Añada un campo oculto. Se envía como parámetro de POST cuando se guarda el recurso. |

### Edición de elementos de formulario {#editing-form-items}

Para editar las propiedades de los elementos de formulario, toque o haga clic en el componente y edite todas o un subconjunto de las siguientes propiedades en la **[!UICONTROL Configuración]** pestaña .

**[!UICONTROL Etiqueta de campo]**: Nombre de la propiedad de metadatos que se muestra en la página de propiedades de la carpeta.

**[!UICONTROL Asignar a propiedad]**: Esta propiedad especifica la ruta relativa del nodo de carpeta en el repositorio CRX donde se guarda. Comienza con &quot;**./**&quot;, que indica que la ruta está bajo el nodo de la carpeta.

Los siguientes son los valores válidos para esta propiedad:

* `./jcr:content/metadata/dc:title`: Almacena el valor en el nodo de metadatos de la carpeta como propiedad `dc:title`.

* `./jcr:created`: Muestra la propiedad JCR en el nodo de la carpeta. Si configura estas propiedades en CRXDE, Adobe recomienda marcarlas como Deshabilitar edición, ya que están protegidas. De lo contrario, el error `Asset(s) failed to modify`&#39; se produce cuando se guardan las propiedades del recurso.

Para asegurarse de que el componente se muestra correctamente en el formulario de esquema de metadatos, no incluya un espacio en la ruta de la propiedad.

**[!UICONTROL Ruta de JSON]**: Utilícelo para especificar la ruta del archivo JSON donde especifique pares clave-valor para las opciones.

**[!UICONTROL Marcador de posición]**: Utilice esta propiedad para especificar el texto del marcador de posición correspondiente a la propiedad metadata.

**[!UICONTROL Opciones]**: Utilice esta propiedad para especificar opciones en una lista.

**[!UICONTROL Descripción]**: Utilice esta propiedad para añadir una breve descripción para el componente de metadatos.

**[!UICONTROL Clase]**: Clase de objeto a la que está asociada la propiedad.

## Eliminación de formularios de esquema de metadatos de carpeta {#delete-folder-metadata-schema-forms}

Puede eliminar formularios de esquema de metadatos de carpeta desde la página Forms Esquema de metadatos de carpeta . Para eliminar un formulario, selecciónelo y pulse o haga clic en el icono Eliminar de la barra de herramientas.

![delete_form](assets/delete_form.png)

## Asignar un esquema de metadatos de carpeta {#assign-a-folder-metadata-schema}

Puede asignar un esquema de metadatos de carpeta a una carpeta desde la página Forms del esquema de metadatos de la carpeta o al crear una carpeta.

Si configura un esquema de metadatos para una carpeta, la ruta al formulario de esquema se almacena en la variable `folderMetadataSchema` propiedad del nodo folder en .*/jcr:content*.

### Asignar a un esquema desde la página Esquema de metadatos de carpeta {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Toque o haga clic en el botón [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Recursos]** > **[!UICONTROL Esquemas de metadatos de carpeta]**.
1. En la página Forms Esquema de metadatos de carpeta , seleccione el formulario de esquema que desee aplicar a una carpeta.
1. En la barra de herramientas, toque o haga clic en **[!UICONTROL Aplicar a carpetas]**.

1. Seleccione la carpeta en la que desea aplicar el esquema y, a continuación, toque o haga clic en **[!UICONTROL Aplicar]**. Si ya se ha aplicado un esquema de metadatos en la carpeta, un mensaje de advertencia indicará que está a punto de sobrescribir el esquema de metadatos existente. Toque o haga clic **[!UICONTROL Sobrescribir]**.
1. Abra las propiedades de metadatos de la carpeta a la que aplicó el esquema de metadatos.

   ![folder_properties](assets/folder_properties.png)

   Para ver los campos de metadatos de la carpeta, pulse o haga clic en la pestaña **[!UICONTROL Metadatos de la carpeta]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Asignar un esquema al crear una carpeta {#assign-a-schema-when-creating-a-folder}

Puede asignar un esquema de metadatos de carpeta al crear una carpeta. Si existe al menos un esquema de metadatos de carpeta en el sistema, se muestra una lista adicional en la **[!UICONTROL Crear carpeta]** diálogo. Puede seleccionar el esquema deseado. De forma predeterminada, no hay ningún esquema seleccionado.

1. En el [!DNL Assets] interfaz de usuario, toque o haga clic **[!UICONTROL Crear]** en la barra de herramientas.
1. Especifique un título y un nombre para la carpeta.
1. En la lista Esquema de metadatos de carpeta , seleccione el esquema deseado. A continuación, toque o haga clic en **[!UICONTROL Crear]**.

   ![select_schema](assets/select_schema.png)

1. Abra las propiedades de metadatos de la carpeta a la que aplicó el esquema de metadatos.
1. Para ver los campos de metadatos de la carpeta, pulse o haga clic en la pestaña **[!UICONTROL Metadatos de la carpeta]**.

## Usar el esquema de metadatos de la carpeta {#use-the-folder-metadata-schema}

Abra las propiedades de una carpeta configurada con un esquema de metadatos de carpeta. Se muestra la pestaña **[!UICONTROL Metadatos de carpeta]** en la página de propiedades de la carpeta. Para ver el formulario de esquema de metadatos de la carpeta, seleccione esta pestaña.

Introduzca valores de metadatos en los distintos campos y toque o haga clic en **[!UICONTROL Guardar]** para almacenar los valores. Los valores que especifique se almacenan en el nodo de carpeta del repositorio CRX.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
