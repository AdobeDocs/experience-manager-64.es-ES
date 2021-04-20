---
title: Modelos de fragmento de contenido
seo-title: Modelos de fragmento de contenido
description: Los modelos de fragmento de contenido se utilizan para crear fragmentos de contenido con contenido estructurado.
seo-description: Los modelos de fragmento de contenido se utilizan para crear fragmentos de contenido con contenido estructurado.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
exl-id: 39ed07ec-54a6-4387-8435-e891726c411c
feature: Content Fragments
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 13%

---

# Modelos de fragmento de contenido {#content-fragment-models}

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](../release-notes/sp-release-notes.md).

Los modelos de fragmento de contenido definen la estructura de contenido para los [fragmentos de contenido](content-fragments.md).

## Habilitar modelos de fragmento de contenido {#enable-content-fragment-models}

>[!CAUTION]
>
>Si no habilita **[!UICONTROL Modelos de fragmento de contenido]**, la opción **[!UICONTROL Crear]** no estará disponible para crear nuevos modelos.

Para habilitar los modelos de fragmento de contenido, debe:

* Habilitar el uso de modelos de fragmento de contenido en el administrador de configuración
* Aplique la configuración a la carpeta Assets

### Habilitar los modelos de fragmento de contenido en el Administrador de configuración {#enable-content-fragment-models-in-configuration-manager}

Para [crear un nuevo modelo de fragmento de contenido](#creating-a-content-fragment-model) primero debe **habilitarlos** mediante el Administrador de configuración:

1. Vaya a **[!UICONTROL Herramientas]**, **[!UICONTROL General]**, luego abra el **[!UICONTROL Explorador de configuración]**.
   * Consulte la [Documentación del explorador de configuración](/help/sites-administering/configurations.md) para obtener más información.
1. Seleccione la ubicación adecuada para su sitio web.
1. Utilice **[!UICONTROL Crear]** para abrir el cuadro de diálogo, donde:

   1. Especifique un **[!UICONTROL Título]**.
   1. Seleccione **[!UICONTROL Modelos de fragmento de contenido]** para habilitar su uso.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Seleccione **[!UICONTROL Create]** para guardar la definición.

### Aplicar la configuración a la carpeta de recursos {#apply-the-configuration-to-your-assets-folder}

Cuando la configuración **[!UICONTROL global]** está habilitada para los modelos de fragmento de contenido, cualquier modelo que creen los usuarios se puede usar en cualquier carpeta de Assets.

Para utilizar otras configuraciones (es decir, excluyendo global) con una carpeta de Assets comparable, debe definir la conexión. Esto se realiza mediante **[!UICONTROL Configuración]** en la pestaña **[!UICONTROL Cloud Services]** de las **[!UICONTROL Propiedades de la carpeta]** correspondiente.

## Creación de un modelo de fragmento de contenido {#creating-a-content-fragment-model}

1. Vaya a **[!UICONTROL Herramientas]**, **[!UICONTROL Recursos]** y, a continuación, abra **[!UICONTROL Modelos de fragmento de contenido]**.
1. Vaya a la carpeta correspondiente a su [configuración](#enable-content-fragment-models).
1. Utilice **[!UICONTROL Crear]** para abrir el asistente.

   >[!CAUTION]
   >
   >Si el [uso de modelos de fragmento de contenido no se ha habilitado](#enable-content-fragment-models), la opción **Crear** no estará disponible.

1. Especifique el **[!UICONTROL Título del modelo]**. También puede agregar una **[!UICONTROL descripción]** si fuera necesario.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Utilice **[!UICONTROL Crear]** para guardar el modelo vacío. Un mensaje indicará el éxito de la acción, puede seleccionar **[!UICONTROL Abrir]** para editar inmediatamente el modelo o **[!UICONTROL Listo]** para volver a la consola.

## Definición del modelo de fragmento de contenido {#defining-your-content-fragment-model}

El modelo de fragmento de contenido define de forma eficaz la estructura de los fragmentos de contenido resultantes. Con el editor de modelos puede añadir y configurar los campos obligatorios:

>[!CAUTION]
>
>Editar un modelo de fragmento de contenido existente puede afectar a los fragmentos dependientes.

1. Vaya a **[!UICONTROL Herramientas]**, **[!UICONTROL Recursos]** y, a continuación, abra **[!UICONTROL Modelos de fragmento de contenido]**.

1. Vaya a la carpeta que contiene el modelo de fragmento de contenido.
1. Abra el modelo necesario para **[!UICONTROL Edit]**; utilice la acción rápida o seleccione el modelo y, a continuación, la acción en la barra de herramientas.

   Una vez abierto, el editor de modelos muestra:

   * a la izquierda: campos ya definidos
   * right: **[!UICONTROL Tipos de datos]** disponibles para crear campos (y **[!UICONTROL Propiedades]** para su uso una vez creados los campos)

   >[!NOTE]
   >
   >Cuando un campo es **Requerido**, la **Etiqueta** indicada en el panel izquierdo se marcará con un asterisco (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **Adición de un campo**

   * Arrastre un tipo de datos requerido a la ubicación requerida para un campo:

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * Una vez agregado un campo al modelo, el panel derecho mostrará las **Propiedades** que se pueden definir para ese tipo de datos en particular. Aquí puede definir lo que se requiere para ese campo. Por ejemplo:

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **Eliminación de un campo**

   Seleccione el campo requerido y, a continuación, toque o haga clic en el icono de la papelera. Se le solicitará que confirme la acción.

   ![cf-32](assets/cf-32.png)

1. Después de agregar todos los campos obligatorios y definir las propiedades, utilice **[!UICONTROL Guardar]** para mantener la definición. Por ejemplo:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Eliminación de un modelo de fragmento de contenido {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>La eliminación de un modelo de fragmento de contenido puede afectar a los fragmentos dependientes.

Para eliminar un modelo de fragmento de contenido:

1. Vaya a **[!UICONTROL Herramientas]**, **[!UICONTROL Recursos]** y, a continuación, abra **[!UICONTROL Modelos de fragmento de contenido]**.

1. Vaya a la carpeta que contiene el modelo de fragmento de contenido.
1. Seleccione el modelo, seguido de **[!UICONTROL Delete]** en la barra de herramientas.

   >[!NOTE]
   >
   >Si se hace referencia al modelo, se envía una advertencia. Tome las medidas adecuadas.

## Publicación de un modelo de fragmento de contenido {#publishing-a-content-fragment-model}

Los modelos de fragmento de contenido deben publicarse cuando se publican fragmentos de contenido dependientes, o antes de hacerlo.

Para publicar un modelo de fragmento de contenido:

1. Vaya a **[!UICONTROL Herramientas]**, **[!UICONTROL Recursos]** y, a continuación, abra **[!UICONTROL Modelos de fragmento de contenido]**.

1. Vaya a la carpeta que contiene el modelo de fragmento de contenido.
1. Seleccione el modelo, seguido de **[!UICONTROL Publish]** en la barra de herramientas.

   >[!NOTE]
   >
   >Si publica un fragmento de contenido para el que el modelo aún no se ha publicado, una lista de selección lo indicará y el modelo se publicará con el fragmento.
