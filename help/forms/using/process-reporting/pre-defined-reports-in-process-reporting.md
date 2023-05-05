---
title: Informes predefinidos en informes de proceso
seo-title: Pre-defined reports in Process Reporting
description: Consulte datos de proceso de AEM Forms en JEE para crear informes sobre los procesos de larga duración, la duración de los procesos y el volumen del flujo de trabajo.
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 96%

---

# Informes predefinidos en informes de proceso {#pre-defined-reports-in-process-reporting}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Forms Process Reporting incluye los siguientes informes *predeterminados*:

* **[Procesos de larga duración](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: un informe de todos los procesos de AEM Forms que han tardado más tiempo del especificado en completarse.

* **[Gráfico de duración del proceso](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: un informe de un proceso de AEM Forms especificado en función de su duración.

* **[Volumen del flujo de trabajo](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: un informe de las instancias en ejecución y las instancias completadas del proceso especificado por fecha.

## Procesos de larga duración {#long-running-processes}

El informe Procesos de larga duración muestra los procesos de AEM Forms que han tardado más tiempo del especificado en completarse.

### Ejecutar un informe Procesos de larga duración {#to-execute-a-long-running-process-report-br}

1. Para ver la lista de informes predefinidos en informes de proceso, haga clic en el nodo **Informes** en la vista de árbol de **Process Reporting**.
1. Haga clic en el nodo de informes **Procesos de larga duración**.

   ![nodo_larga_duración](assets/long_running_node.png)

   Al seleccionar un informe, el panel **Parámetros de informe** se muestra a la derecha de la vista de árbol.

   ![Panel Parámetros de informe de Procesos de larga ejecución](assets/report_parameters_panel.png)

   Parámetros:

   * **Duración** (*obligatorio*): especifique una duración y una unidad de tiempo. Muestre todos los procesos de AEM Forms que se han ejecutado durante más tiempo del especificado.
   * **Se inició después de** (*opcional*): seleccione una fecha. Filtre el informe para mostrar las instancias de proceso que se han iniciado después de la fecha especificada.
   * **Se inició antes de** (*opcional*): seleccione una fecha. Filtre el informe para mostrar las instancias de proceso que se iniciaron antes de la fecha especificada.

1. Haga clic en **Ir** para ejecutar el informe.

   El informe se muestra en el panel **Informe** que aparece en la parte derecha de la ventana **Process Reporting**.

   ![procesos_larga_duración](assets/long_running_processes.png)

   Utilice las opciones de la esquina superior derecha del panel **Informe** para realizar las siguientes operaciones en el informe.

   * **Actualizar**: actualiza el informe con los datos más recientes disponibles en el almacenamiento.
   * **Cambiar el color de la leyenda**: seleccione y cambie el color de la leyenda del informe.
   * **Exportar a CSV**: exporte y descargue los datos del informe en un archivo separado por comas.

## Informe Duración del proceso {#process-duration-report-br}

El informe Duración del proceso muestra el número de instancias de un proceso de Forms en función del número de días que se ha ejecutado cada instancia.

### Ejecutar un informe Duración del proceso {#to-execute-a-process-duration-report-br}

1. Para ver los informes predefinidos en informes de proceso, haga clic en el nodo **Informes** de la vista de árbol de **Process Reporting**.
1. Haga clic en el nodo de informes **Duración de los procesos**.

   ![nodo_duración_proceso](assets/process_duration_node.png)

   Al seleccionar un informe, el panel **Parámetros de informe** se muestra a la derecha de la vista de árbol.

   ![Panel Parámetros de informe de Procesos de larga ejecución](assets/process_duration_params.png)

   Parámetros:

   * **Seleccionar proceso** (*obligatorio*): seleccione un proceso de AEM Forms.

1. Haga clic en **Ir** para ejecutar el informe.

   El informe se muestra en el panel **Informe** que aparece en la parte derecha de la ventana Process Reporting.

   ![process_duration_report](assets/process_duration_report.png)

   Utilice las opciones de la esquina superior derecha del panel **Informe** para realizar las siguientes operaciones en el informe.

   * **Actualizar**: actualiza el informe con los datos más recientes disponibles en el almacenamiento.
   * **Cambiar el color de la leyenda**: seleccione y cambie el color de la leyenda del informe.
   * **Exportar a CSV**: exporte y descargue los datos del informe en un archivo separado por comas.

## Informe Volumen del flujo de trabajo {#workflow-volume-report}

El informe Volumen del flujo de trabajo muestra el número de instancias de un proceso de AEM Forms que se ejecutan actualmente y las que se han completado en función del día del calendario.

### Para ejecutar un informe Volumen del flujo de trabajo {#to-execute-a-workflow-volume-report-br}

1. Para ver los informes predefinidos en informes de proceso, haga clic en el nodo **Informes** de la vista de árbol de **Process Reporting**.
1. Haga clic en el nodo de informes **Volumen del flujo de trabajo**.

   ![nodo_volumen_flujo_trabajo](assets/workflow_volume_node.png)

   Al seleccionar un informe, el panel **Parámetros de informe** se muestra a la derecha de la vista de árbol.

   ![Panel Parámetros de informe de Procesos de larga ejecución](assets/workflow_volume_params.png)

   Parámetros:

   * **Seleccionar proceso** (*obligatorio*): seleccione un proceso de AEM Forms.
   * **Se inició después de** (*opcional*): seleccione una fecha. Filtra el informe para mostrar las instancias de proceso que se iniciaron después de la fecha especificada.
   * **Se inició antes de** (*opcional*): seleccione una fecha. Filtra el informe para mostrar las instancias de proceso que se iniciaron antes de la fecha especificada.

1. Haga clic en **Ir** para ejecutar el informe.

   El informe se muestra en el panel **Informe** que aparece en la parte derecha de la ventana **Process Reporting**.

   ![informe_volumen_flujo_trabajo](assets/workflow_volume_report.png)

   Utilice las opciones de la esquina superior derecha del panel **Informe** para realizar las siguientes operaciones en el informe.

   * **Actualizar**: actualiza el informe con los datos más recientes disponibles en el almacenamiento.
   * **Cambiar el color de la leyenda**: seleccione y cambie el color de la leyenda del informe.
   * **Exportar a CSV**: exporte y descargue los datos del informe en un archivo separado por comas.
