---
title: Edición masiva de metadatos de varios recursos y colecciones
description: Obtenga información sobre cómo editar los metadatos de muchos recursos y colecciones simultáneamente para propagar rápidamente los cambios habituales en los metadatos.
contentOwner: AG
feature: Asset Management,Metadata,Collections
role: User
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 14%

---

# Administrar varios recursos y colecciones {#managing-multiple-assets-and-collections}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Obtenga información sobre cómo editar los metadatos de varios recursos y colecciones simultáneamente para propagar rápidamente los cambios habituales en los metadatos.

Recursos de Adobe Enterprise Manager le permite editar simultáneamente los metadatos de varios recursos para que pueda propagar rápidamente los cambios comunes de metadatos a los recursos de forma masiva. También puede editar los metadatos de varias colecciones de forma masiva.

Utilice la página de propiedades para realizar cambios en los metadatos de varios recursos o colecciones:

* Cambiar propiedades de metadatos a un valor común
* Añadir o modificar etiquetas

Para personalizar la página de propiedades de metadatos, como agregar, modificar o eliminar propiedades de metadatos, utilice el editor de esquemas.

>[!NOTE]
>
>Los métodos de edición por lotes funcionan con los recursos disponibles en una carpeta o en una colección. Para los recursos disponibles en todas las carpetas o que coinciden con criterios comunes, es posible actualizar los metadatos de forma masiva a partir de los resultados de búsqueda de recursos.

## Editar propiedades de metadatos de varios recursos {#editing-metadata-properties-of-multiple-assets}

1. En la interfaz de usuario de Assets, vaya a la ubicación de los recursos que desee editar.
1. Seleccione los recursos para los que desea editar propiedades comunes.
1. En la barra de herramientas, haga clic en **[!UICONTROL Propiedades]** para abrir la página de propiedades de los recursos seleccionados.
1. Modifique las propiedades de metadatos de los recursos seleccionados en las distintas pestañas.
1. Para ver los metadatos de un recurso específico, cancele la selección de los recursos restantes de la lista. Si cancela la selección de algunos recursos en la [!UICONTROL Propiedades] , los metadatos de estos recursos no se actualizan.
1. Para seleccionar un esquema de metadatos diferente para los recursos, haga clic en **[!UICONTROL Configuración]** en la barra de herramientas y seleccione un esquema. Haga clic en **[!UICONTROL Guardar y cerrar]**.
1. Para anexar los nuevos metadatos con los metadatos existentes en los campos que contienen varios valores, seleccione el **[!UICONTROL modo Anexar]**. Si no selecciona esta opción, los metadatos nuevos sustituirán a los metadatos existentes en los campos. Haga clic en **[!UICONTROL Enviar]**.

![El esquema de metadatos se aplica de forma masiva a varios recursos](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>En el caso de los campos de un solo valor, los nuevos metadatos no se anexan al valor existente en el campo aunque seleccione el modo **[!UICONTROL Anexar]**.

## Configuración del límite de actualización de metadatos masivos {#configure-limit-for-bulk-metadata-update}

Para evitar una situación similar a DOS, [!DNL Experience Manager] limita el número de parámetros admitidos en una solicitud de Sling. Al actualizar los metadatos de muchos recursos de una sola vez, puede que llegue al límite y los metadatos no se actualicen para obtener más recursos. [!DNL Experience Manager] genera la siguiente advertencia en los registros:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Para cambiar el límite, acceda a **[!UICONTROL Herramientas > Operaciones > Consola web]** y cambiar el valor de [!UICONTROL Máximo de parámetros de POST] en [!UICONTROL Administración de parámetros de solicitud de Apache Sling] Configuración de OSGi.

>[!MORELIKETHIS]
>
>* [Editar metadatos de varias colecciones de forma masiva](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

