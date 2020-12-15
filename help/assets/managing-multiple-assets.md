---
title: Edición masiva de metadatos de varios recursos y colecciones
description: Descubra cómo editar los metadatos de muchos recursos y colecciones de forma simultánea para propagar rápidamente los cambios comunes de metadatos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 97bb17ce719f82449e28f9b32eb651b632b0f8b5
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 12%

---


# Administrar varios recursos y colecciones {#managing-multiple-assets-and-collections}

Descubra cómo editar los metadatos de varios recursos y colecciones simultáneamente para propagar rápidamente los cambios comunes de metadatos.

Recursos de Adobe Enterprise Manager (AEM) le permite editar simultáneamente los metadatos de varios recursos para que pueda propagar rápidamente cambios comunes de metadatos a los recursos de forma masiva. También puede editar los metadatos de varias colecciones de forma masiva.

Utilice la página de propiedades para realizar cambios en los metadatos de varios recursos o colecciones:

* Cambiar las propiedades de metadatos a un valor común
* Añadir o modificar etiquetas

Para personalizar la página de propiedades de metadatos, incluida la adición, modificación y eliminación de propiedades de metadatos, utilice el editor de Esquema.

>[!NOTE]
>
>Los métodos de edición masiva funcionan para los recursos disponibles en una carpeta o una colección. En el caso de los recursos disponibles en distintas carpetas o que cumplen un criterio común, es posible actualizar los metadatos de forma masiva a partir de los resultados de búsqueda de recursos.

## Editar propiedades de metadatos de varios recursos {#editing-metadata-properties-of-multiple-assets}

1. En la interfaz de usuario de Recursos, navegue a la ubicación de los recursos que desee editar.
1. Seleccione los recursos para los que desea editar propiedades comunes.
1. En la barra de herramientas, toque o haga clic en el icono **[!UICONTROL Propiedades]** para abrir la página de propiedades de los recursos seleccionados.

   >[!NOTE]
   >
   >Cuando se seleccionan varios recursos, se selecciona el formulario principal común más bajo para los recursos. En otras palabras, la página de propiedades solo muestra los campos de metadatos comunes en las páginas de propiedades de todos los recursos individuales.

1. Modifique las propiedades de metadatos de los recursos seleccionados en las distintas fichas.
1. Para vista del editor de metadatos de un recurso específico, anule la selección de los recursos restantes de la lista. Los campos del editor de metadatos se rellenan con los metadatos del recurso concreto.

   >[!NOTE]
   >
   >* En la página de propiedades, puede quitar recursos de la lista de recursos anulándolos. La lista de recursos tiene todos los recursos seleccionados de forma predeterminada. Los metadatos de los recursos que se eliminan de la lista no se actualizan.
   >* En la parte superior de la lista assets, active la casilla de verificación situada cerca de **Título** para alternar entre seleccionar los recursos y borrar la lista.


1. Para seleccionar otro esquema de metadatos para los recursos, toque o haga clic en el icono **[!UICONTROL Configuración]** de la barra de herramientas y seleccione el esquema que desee.
1. Guarde los cambios.
1. Para anexar los nuevos metadatos con los metadatos existentes en los campos que contienen varios valores, seleccione el **[!UICONTROL modo Anexar]**. Si no selecciona esta opción, los metadatos nuevos sustituirán a los metadatos existentes en los campos. Pulse o haga clic en **[!UICONTROL Enviar]**.

   >[!CAUTION]
   >
   >En el caso de los campos de un solo valor, los nuevos metadatos no se anexan al valor existente en el campo aunque seleccione el modo **[!UICONTROL Anexar]**.

## Configurar límite para la actualización masiva de metadatos {#configure-limit-for-bulk-metadata-update}

Para evitar una situación similar a DOS, AEM limita el número de parámetros admitidos en una solicitud de Sling. Al actualizar los metadatos de muchos recursos de una sola vez, es posible que se alcance el límite y que los metadatos no se actualicen para más recursos. AEM genera la siguiente advertencia en los registros:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Para cambiar el límite, acceda a **[!UICONTROL Herramientas > Operaciones > Consola Web]** y cambie el valor de [!UICONTROL Parámetros máximos de POST] en [!UICONTROL Administración de parámetros de solicitud de Apache Sling] Configuración de OSGi.

>[!MORELIKETHIS]
>
>* [Editar metadatos de varias colecciones de forma masiva](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)