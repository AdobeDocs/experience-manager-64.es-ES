---
title: Procesar recursos para llevar a cabo procesos de negocios, realizar auditorías, lograr el cumplimiento de normas y mantener la solidez básica
description: Procesamiento de recursos para convertir formatos, crear representaciones, administrar recursos, validar recursos y ejecutar flujos de trabajo.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 73d440198028bfa6b47e9fde13f3a354a1b8445f
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 2%

---


# Procesar recursos digitales {#process-assets}

[!DNL Adobe Experience Manager Assets] le permite trabajar en sus recursos digitales de muchas maneras para permitir un procesamiento sólido de los recursos. Puede utilizar los métodos de procesamiento disponibles o ampliar los métodos para garantizar la finalización completa de los procesos empresariales mediante, auditorías y cumplimiento de normas, descubrimiento y distribución de los recursos digitales y la sanidad básica de los mismos. Puede hacer todo esto mientras se alcanza la escala y personalización necesarias.

## Comprender los flujos de trabajo {#understand-workflows}

Para el procesamiento de recursos, [!DNL Experience Manager] utiliza flujos de trabajo. Los flujos de trabajo ayudan a automatizar las actividades o la lógica empresarial. De forma predeterminada, se proporcionan pasos granulares para realizar tareas específicas y los desarrolladores pueden crear sus propios pasos personalizados. Estos pasos se pueden combinar en un orden lógico para crear flujos de trabajo. Por ejemplo, un flujo de trabajo puede aplicar automáticamente marcas de agua en las imágenes cargadas según criterios específicos como metadatos incrustados en la imagen, carpeta en la que se carga, resolución de la imagen, etc. Otro ejemplo es un flujo de trabajo configurado para marcar imágenes de forma que se puedan satisfacer simultáneamente varias necesidades de administración de recursos, como agregar metadatos, crear representaciones, agregar etiquetas inteligentes para la detección de recursos, publicar en un almacén de datos, configurar permisos para el acceso de usuarios, etc.

## Flujos de trabajo predeterminados disponibles en Experience Manager {#default-workflows}

De forma predeterminada, todos los recursos cargados se procesan mediante el flujo de trabajo [!UICONTROL Recurso de actualización de DAM]. El flujo de trabajo se ejecuta para cada recurso cargado y lleva a cabo tareas básicas de administración de recursos, como la generación de representaciones, la reescritura de metadatos, la extracción de páginas, la extracción de medios y la transcodificación.

Para ver los distintos modelos de flujo de trabajo disponibles de forma predeterminada, consulte [!UICONTROL Herramientas > Flujo de trabajo > Modelos] en [!DNL Experience Manager].

![Parte del flujo de trabajo predeterminado](assets/aem-default-workflows.png)

*Figura: Algunos de los flujos de trabajo predeterminados disponibles en  [!DNL Experience Manager].*

## Aplicar flujos de trabajo a los recursos {#applying-workflows-to-assets}

La aplicación de flujos de trabajo a los recursos digitales es la misma que para las páginas del sitio web. Para obtener una guía completa sobre cómo crear y utilizar flujos de trabajo, consulte [flujos de trabajo de inicio](/help/sites-authoring/workflows-participating.md).

Utilice flujos de trabajo en recursos digitales para activar el recurso o crear marcas de agua. Muchos de los flujos de trabajo de los recursos se activan automáticamente. Por ejemplo, el flujo de trabajo que crea automáticamente una representación después de editar una imagen se activa automáticamente.

>[!NOTE]
>
>Si un flujo de trabajo disponible en la IU clásica no está disponible en la IU táctil, como [!UICONTROL Solicitud de activación] y [!UICONTROL Solicitud de desactivación], consulte [modelos de flujo de trabajo](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Aplicar un flujo de trabajo a un recurso AEM {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Para aplicar un flujo de trabajo a un recurso, siga estos pasos:

1. Vaya a la ubicación del recurso para el que desea realizar el inicio de un flujo de trabajo y haga clic en el recurso para abrir la página de recursos.

1. Vaya a la ubicación del recurso para el que desea realizar el inicio de un flujo de trabajo y haga clic en el recurso para abrir la página de recursos. Seleccione **[!UICONTROL Línea de tiempo]** en el menú para mostrar la línea de tiempo.

   ![línea de tiempo-2](assets/timeline-2.png)

1. Haga clic en **[!UICONTROL Acciones]** en la parte inferior para abrir la lista de acciones disponibles para el recurso.

1. Haga clic en **[!UICONTROL Flujo de trabajo de Inicio]** desde la lista.

1. En el cuadro de diálogo **[!UICONTROL Flujo de trabajo de Inicio]**, seleccione un modelo de flujo de trabajo de la lista.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Opcional) Especifique un título para el flujo de trabajo, que se puede utilizar para hacer referencia a la instancia de flujo de trabajo.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Haga clic en **[!UICONTROL Inicio]** y, a continuación, haga clic en **[!UICONTROL Continuar]** en el cuadro de diálogo para confirmar. Cada paso del flujo de trabajo se muestra en la cronología como un evento.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Aplicar un flujo de trabajo a varios recursos {#applying-a-workflow-to-multiple-assets}

1. Desde la consola Recursos, desplácese hasta la ubicación de los recursos para los que desea realizar el inicio en un flujo de trabajo y seleccione los recursos. Seleccione **[!UICONTROL Línea de tiempo]** en el menú para mostrar la línea de tiempo.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Haga clic en **[!UICONTROL Acciones]** en la parte inferior.

1. Haga clic en **[!UICONTROL Flujo de trabajo de Inicio]**. En el cuadro de diálogo **[!UICONTROL Flujo de trabajo de Inicio]**, seleccione un modelo de flujo de trabajo de la lista.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Opcional) Especifique un título para el flujo de trabajo, que se puede utilizar para hacer referencia a la instancia de flujo de trabajo.

1. Haga clic en **[!UICONTROL Iniciar]** y, a continuación, en **[!UICONTROL Confirmar]** en el cuadro de diálogo. El flujo de trabajo se ejecuta en todos los recursos seleccionados.

## Aplicar un flujo de trabajo a varias carpetas {#applying-a-workflow-to-multiple-folders}

El procedimiento para aplicar un flujo de trabajo a varias carpetas es similar al procedimiento para aplicar un flujo de trabajo a varios recursos. Seleccione las carpetas en la consola Recursos y realice los pasos 2 a 7 del procedimiento [aplicar un flujo de trabajo a varios recursos](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Aplicar un flujo de trabajo a una colección {#applying-a-workflow-to-a-collection}

Para obtener más información sobre cómo aplicar un flujo de trabajo a una colección, consulte [aplicar un flujo de trabajo a una colección](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Inicio automático de un flujo de trabajo para procesar los recursos de forma condicional {#auto-execute-workflow-on-some-assets}

Los administradores pueden configurar el flujo de trabajo para ejecutar y procesar automáticamente recursos en función de condiciones predefinidas. La funcionalidad es útil para usuarios de la línea de negocios y especialistas en mercadotecnia, por ejemplo, para crear un flujo de trabajo personalizado en carpetas específicas. Supongamos que todos los activos de la sesión fotográfica de una agencia se pueden marcar con agua o que todos los recursos cargados por un operador independiente se pueden procesar para crear representaciones específicas.

Para un modelo de flujo de trabajo, los usuarios pueden crear un iniciador de flujo de trabajo que lo ejecute. Un iniciador de flujo de trabajo supervisa los cambios en el repositorio de contenido y ejecuta el flujo de trabajo cuando se cumplen las condiciones predefinidas. Los administradores pueden proporcionar acceso a los especialistas en marketing para crear flujos de trabajo y configurar el iniciador. Los usuarios pueden modificar el flujo de trabajo predeterminado [!UICONTROL Recurso de actualización de DAM] para agregar los pasos adicionales necesarios para procesar recursos específicos. El flujo de trabajo se ejecuta en todos los recursos cargados recientemente. Utilice uno de los siguientes métodos para limitar la ejecución de los pasos adicionales en recursos específicos:

* Haga una copia del flujo de trabajo [!UICONTROL DAM Update Asset] y modifíquelo para que se ejecute en una jerarquía de carpetas específica. Este método resulta útil para algunas carpetas.
* Los pasos de procesamiento adicionales se pueden agregar utilizando una [división OR](/help/sites-developing/workflows-step-ref.md#or-split) como condición aplicable a tantas carpetas como sea necesario.

## Prácticas recomendadas y limitaciones {#best-practices-limitations-tips}

* Tenga en cuenta sus necesidades para todos los tipos de representaciones al diseñar flujos de trabajo. Si no prevé la necesidad de una representación en el futuro, elimine el paso de creación del flujo de trabajo. Las representaciones no se pueden eliminar de forma masiva posteriormente. Las representaciones no deseadas pueden ocupar mucho espacio en almacenamiento después de un uso prolongado de [!DNL Experience Manager]. Para recursos individuales, puede quitar las representaciones manualmente de la interfaz de usuario. Para varios recursos, puede personalizar [!DNL Experience Manager] para eliminar representaciones específicas o eliminar los recursos y volver a cargarlos.
* De forma predeterminada, el flujo de trabajo [!UICONTROL Recurso de actualización de DAM] incluye algunos pasos para crear miniaturas y representaciones web. Si se eliminan las representaciones predeterminadas del flujo de trabajo, la interfaz de usuario de [!DNL Assets] no se representa correctamente.

>[!MORELIKETHIS]
>
>* [Aplicar y participar en flujos de trabajo](/help/sites-authoring/workflows.md)
>* [Creación de modelos de flujo de trabajo y ampliación de la funcionalidad de flujo de trabajo](/help/sites-developing/workflows.md)
>* [Métodos para ejecutar flujos de trabajo](/help/sites-administering/workflows-starting.md)
>* [Prácticas recomendadas del flujo de trabajo](/help/sites-developing/workflows-best-practices.md)
>* [Artículo de comunidad sobre la modificación de recursos mediante flujo de trabajo](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)

