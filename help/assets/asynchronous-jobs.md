---
title: Configure operaciones asincrónicas en [!DNL Adobe Experience Manager].
description: Complete asincrónicamente algunas tareas con muchos recursos para optimizar el rendimiento en [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Operaciones asincrónicas {#asynchronous-operations}

Para reducir el impacto negativo en el performance, [!DNL Adobe Experience Manger Assets] procesa de manera asincrónica ciertas operaciones de activos de larga duración y con gran cantidad de recursos. El procesamiento asincrónico implica poner en cola varias tareas y, finalmente, ejecutarlas en serie, según la disponibilidad de los recursos del sistema. Estas operaciones incluyen:

* Eliminar muchos recursos.
* Desplazar muchos recursos o recursos con muchas referencias.
* Exportación e importación masiva de metadatos de recursos.

Puede vista el estado de las tareas asincrónicas desde la página **[!UICONTROL Estado del trabajo asincrónico]**.

>[!NOTE]
>
>De forma predeterminada, las tareas [!DNL Assets] se ejecutan en paralelo. Si `N` es el número de núcleos de CPU, las tareas `N/2` se pueden ejecutar en paralelo de forma predeterminada. Para utilizar la configuración personalizada para la cola de tareas, modifique la configuración **[!UICONTROL Cola predeterminada de la operación asincrónica]** desde la [!UICONTROL Consola web]. Para obtener más información, consulte [configuraciones de cola](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitorear el estado de las operaciones asincrónicas {#monitoring-the-status-of-asynchronous-operations}

Siempre que [!DNL Assets] procesa una operación de forma asincrónica, recibirá una notificación en su [!DNL Experience Manager] [Bandeja de entrada](/help/sites-authoring/inbox.md) y por correo electrónico. Para ver en detalle el estado de las operaciones asincrónicas, vaya a la página **[!UICONTROL Estado del trabajo asincrónico]**.

1. En la interfaz [!DNL Experience Manager], haga clic en **[!UICONTROL Operaciones]** > **[!UICONTROL Trabajos]**.

1. En la página **[!UICONTROL Estado del trabajo asincrónico]**, revise los detalles de las operaciones.

   ![Estado y detalles de las operaciones asincrónicas](assets/job_status.png)

   Para determinar el progreso de una operación, consulte la columna **[!UICONTROL Estado]**. Según el progreso, se muestra uno de los siguientes estados:

   * **[!UICONTROL Activo]**: Se está procesando la operación.
   * **[!UICONTROL Correcto]**: Se completó la operación.
   * **[!UICONTROL Fallo]** o **[!UICONTROL Error]**: No se pudo procesar la operación.
   * **[!UICONTROL Programado]**: La operación está programada para procesarse más tarde.

1. Para detener una operación activa, selecciónela en la lista y haga clic en **[!UICONTROL Detener]** ![icono de detención](assets/do-not-localize/stop_icon.svg) en la barra de herramientas.

1. Para vista de detalles adicionales, por ejemplo, descripción y registros, seleccione la operación y haga clic en **[!UICONTROL Abrir]** ![open_icon](assets/do-not-localize/edit_icon.svg) en la barra de herramientas. Se muestra la página de detalles de la tarea.

   ![Detalles de una tarea de importación de metadatos](assets/job_details.png)

1. Para eliminar la operación de la lista, seleccione **[!UICONTROL Eliminar]** en la barra de herramientas. Para descargar los detalles en un archivo CSV, haga clic en **[!UICONTROL Descargar]**.

   >[!NOTE]
   >
   >No puede eliminar una tarea si su estado está activo o en cola.

## Purgar tareas finalizadas {#purge-completed-tasks}

[!DNL Experience Manager Assets] ejecuta una tarea de depuración todos los días a las 1.00 horas para eliminar tareas asincrónicas completadas que tienen más de un día de antigüedad.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Puede modificar la programación de la tarea de depuración y la duración durante la cual se conservan los detalles de las tareas completadas antes de que se eliminen. También puede configurar el número máximo de tareas completadas para las que se conservan los detalles en cualquier momento.

1. En la interfaz [!DNL Experience Manager], haga clic en **[!UICONTROL Herramientas]** > **[!UICONTROL Operaciones]** > **[!UICONTROL Consola Web]**.
1. Abra la tarea **[!UICONTROL Depuración de trabajos asincrónicos de Adobe CQ DAM programada]**.
1. Especifique el número de umbral de días después de los cuales se eliminan las tareas completadas y el número máximo de tareas para las que se conservan los detalles en el historial. Guarde los cambios.

   ![Configuración para programar la depuración de tareas asincrónicas](assets/purge_job.png)

## Configurar umbral para operaciones de eliminación asincrónica {#configure-thresholds-for-asynchronous-delete-operations}

Si el número de recursos o carpetas que se van a eliminar supera el número de umbral establecido, la operación de eliminación se realiza de forma asíncrona.

1. En la interfaz [!DNL Experience Manager], haga clic en **[!UICONTROL Herramientas]** > **[!UICONTROL Operaciones]** > **[!UICONTROL Consola Web]**.
1. En la [!UICONTROL Consola Web], abra la configuración **[!UICONTROL Procesamiento de trabajo de operación de eliminación asincrónica]**.
1. En el cuadro **[!UICONTROL Número de umbral de recursos]**, especifique los números de umbral para eliminar de forma asíncrona recursos, carpetas o referencias. Guarde los cambios.

   ![Establecer el límite de umbral para la tarea de eliminación de recursos](assets/delete_threshold.png)

## Configurar umbral para operaciones de movimiento asincrónico {#configure-thresholds-for-asynchronous-move-operations}

Si el número de recursos, carpetas o referencias que se van a mover supera el número de umbral establecido, la operación de movimiento se realiza de forma asíncrona.

1. En la interfaz [!DNL Experience Manager], haga clic en **[!UICONTROL Herramientas]** > **[!UICONTROL Operaciones]** > **[!UICONTROL Consola Web]**.
1. En la [!UICONTROL Consola Web], abra la configuración **[!UICONTROL Procesamiento de trabajo de operación de movimiento asincrónico]**.
1. En el cuadro **[!UICONTROL Número de umbral de recursos/referencias]**, especifique los números de umbral para mover de forma asíncrona recursos, carpetas o referencias. Guarde los cambios.

   ![Establecer el límite de umbral para que la tarea mueva recursos](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configure el correo electrónico en el Experience Manager](/help/sites-administering/notification.md).
>* [Importe y exporte metadatos de recursos de manera masiva](/help/assets/metadata-import-export.md).

