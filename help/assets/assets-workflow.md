---
title: Aplicar flujos de trabajo para procesar recursos digitales
description: Aprenda a aplicar flujos de trabajo a recursos, carpetas y colecciones en Recursos AEM para procesar sus recursos digitales.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Aplicación de flujos de trabajo a recursos {#applying-workflows-to-assets}

La aplicación de flujos de trabajo a recursos digitales es la misma que para las páginas de sitios web. Para obtener una guía completa sobre cómo crear y utilizar flujos de trabajo en AEM, consulte [Inicio de flujos de trabajo](../sites-authoring/workflows-participating.md).

Utilice los flujos de trabajo en recursos digitales para activar el recurso o crear marcas de agua. Muchos de los flujos de trabajo de los recursos se activan automáticamente. Por ejemplo, el flujo de trabajo que crea automáticamente una representación después de editar una imagen se activa automáticamente.

Si un flujo de trabajo disponible en la IU clásica no está disponible en la IU táctil, como Solicitud de activación y Solicitud de desactivación, consulte [Hacer que los modelos de flujo de trabajo estén disponibles en la IU](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)táctil.

## Aplicación de un flujo de trabajo a un recurso de AEM {#applying-a-workflow-to-an-aem-asset}

Para obtener más información sobre la aplicación de un flujo de trabajo a un recurso de AEM, consulte [Inicio de un flujo de trabajo en un recurso](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset).

## Aplicación de un flujo de trabajo a varios recursos {#applying-a-workflow-to-multiple-assets}

1. Desde la consola Recursos, vaya a la ubicación de los recursos para los que desea iniciar un flujo de trabajo y seleccione los recursos.
1. Haga clic en el icono de GlobalNav y elija **[!UICONTROL Línea de tiempo]** en el menú para mostrar la línea de tiempo.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. Haga clic en **[!UICONTROL Iniciar flujo de trabajo]**.
1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Opcional) Especifique un título para el flujo de trabajo, que se puede utilizar para hacer referencia a la instancia de flujo de trabajo.
1. Haga clic en **[!UICONTROL Iniciar]** y, a continuación, en **[!UICONTROL Confirmar]** en el cuadro de diálogo. El flujo de trabajo se ejecuta en todos los recursos seleccionados.

## Aplicación de un flujo de trabajo a varias carpetas {#applying-a-workflow-to-multiple-folders}

El procedimiento para aplicar un flujo de trabajo a varias carpetas es similar al procedimiento para aplicar un flujo de trabajo a varios recursos. Seleccione las carpetas en la consola Recursos y realice los pasos 2 a 7 del procedimiento [Aplicación de un flujo de trabajo a varios recursos](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Aplicación de un flujo de trabajo a una colección {#applying-a-workflow-to-a-collection}

Para obtener más información sobre cómo aplicar un flujo de trabajo a una colección, consulte [Ejecución de un flujo de trabajo en una colección](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).
