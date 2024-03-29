---
title: Administrar procesos
seo-title: Managing Processes
description: La página Lista de procesos muestra los procesos que un usuario ha iniciado o que se iniciaron automáticamente. Obtenga más información sobre la administración de los procesos.
seo-description: The Process List page shows the processes that a user has initiated or that were started automatically. Learn more about managing the processes.
uuid: 4cd17400-681a-4e40-996c-7dda57ce449a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 37e702c2-8716-4360-a3eb-d9877b28cc86
exl-id: 322cc7c2-0f24-4ed9-9af2-61b036324f46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 0%

---

# Administrar procesos {#managing-processes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La página Lista de procesos muestra los procesos que un usuario ha iniciado o que se iniciaron automáticamente.

1. En la consola de administración, haga clic en Servicios > Flujo de trabajo de Forms > Flujo de trabajo de Forms. La lista de procesos muestra la siguiente información:

   **Nombre del proceso - Versión:** Nombre del proceso, tal como se define en Workbench.

   **Aplicación:** Aplicación a la que pertenece el proceso, tal como se define en Workbench.

   **Estado:** Activo significa que el proceso es el activado para la versión del proceso. Inactivo significa que el proceso es una versión antigua que aún tiene instancias de proceso.

   **Fecha de creación:** Fecha y hora en que se implementó el proceso.

1. Haga clic en un nombre de proceso para ver sus instancias de proceso en la página Instancia de proceso .

## Uso de instancias de proceso {#working-with-process-instances}

Si accede a la página Instancia de proceso desde la página Lista de procesos, se enumeran todas las instancias de proceso del proceso seleccionado. Si accede a la página Instancia de proceso después de realizar una búsqueda, solo se muestran las instancias de proceso encontradas.

Para cada instancia de proceso, la lista muestra la siguiente información:

**ID de proceso:** Identificador que asigna el flujo de trabajo de formularios cuando se crea una instancia del proceso (es decir, cuando un usuario o un paso automatizado inician un proceso). Puede utilizar este identificador para rastrear la instancia de proceso a lo largo de su ciclo de vida.

**Nombre del proceso - Versión:** Nombre del proceso, tal como se define en Workbench.

**Estado:** Indica si la instancia de proceso se está ejecutando normalmente, si cambia de estado o si se ha detenido. (Consulte Acerca de los estados de instancias de proceso).

**Fecha de creación:** Fecha y hora en que se creó la instancia de proceso.

**Fecha de actualización:** Fecha y hora en que se cambió por última vez el estado de la instancia de proceso.

Puede realizar las siguientes tareas en la página Instancia de proceso :

* Seleccione una instancia de proceso para ver los detalles sobre ella, como sus operaciones y subprocesos. Cuando selecciona una instancia de proceso, aparece la página Detalles de instancia de proceso .
* Suspender, aprobar o finalizar instancias de proceso.
* Busque una instancia de proceso. Para comenzar una búsqueda, haga clic en Buscar.

### Acerca de los estados de instancias de proceso {#about-process-instance-statuses}

Una instancia de proceso, incluidos los subprocesos, puede tener los siguientes estados:

**COMPLETAR:** Se han completado todas las ramas y operaciones de la instancia de proceso. COMPLETE es el estado final de una instancia de proceso.

**FINALIZACIÓN:** El estado de la instancia de proceso está a punto de cambiar a COMPLETE.

**INICIADO:** La instancia de proceso se ha creado, pero aún no se está ejecutando. INICIATED es el primer estado de una instancia de proceso.

**EJECUTANDO:** La instancia de proceso se está ejecutando normalmente. Puede que haya un paso automatizado en curso o que la instancia de proceso esté recibiendo entradas del usuario o esperando la interacción con el usuario.

**SUSPENDIDO:** La instancia de proceso ha sido suspendida por un administrador o por un paso en el proceso. No se producirán más operaciones hasta que se cambie el estado.

**SUSPENDER:** El estado está a punto de cambiar a SUSPENDIDO. Si se ha diseñado una operación para ignorar solicitudes de suspensión y aún no se ha completado, dicha operación debe completarse antes de que se suspenda la instancia de proceso.

**TERMINADO:** Un administrador ha finalizado la instancia de proceso.

**TERMINACIÓN:** El estado está a punto de cambiar a TERMINADO. Si se ha diseñado una operación para ignorar las solicitudes de finalización y aún no se ha completado, dicha operación debe completarse antes de que finalice la instancia de proceso.

**CANCELAR LA SUSPENSIÓN:** El estado está a punto de cambiar a EN EJECUCIÓN después de SUSPENDER.

>[!NOTE]
>
>Cuando se realiza una solicitud para cambiar el estado de una instancia de proceso (como suspender o finalizar), la solicitud introduce la cola de comandos para el flujo de trabajo de formularios. Según el tamaño de la cola y la velocidad de procesamiento general, es posible que el estado mostrado no cambie hasta que la página se vuelva a cargar una o más veces.

### Suspender o aprobar instancias de proceso {#suspend-or-unsuspend-process-instances}

Si necesita solucionar un problema o si sabe que una instancia de proceso encontrará un problema en un paso posterior debido a alguna condición externa, puede suspender la instancia de proceso temporalmente.

Puede suspender instancias de proceso que tengan el estado EJECUCIÓN.

Después de suspender una instancia de proceso, su estado cambia a SUSPENDING, SUSPENDED y el proceso se detiene en su operación actual. La instancia de proceso permanece en este estado hasta que se cambia el estado a UNSUSPENDED.

Solo las instancias de proceso que tienen el estado SUSPENDIDO se pueden cambiar a SUSPENDIDO.

Al aprobar una instancia de proceso, su estado cambia a RUNNING y continúa con la operación en la que se ha suspendido.

Cuando se suspende una instancia de proceso que ha invocado otros procesos (procesos secundarios) mediante su operación de invocación, también se suspenden los procesos secundarios.

1. En la consola de administración, haga clic en Servicios > Flujo de trabajo de Forms > Flujo de trabajo de Forms.
1. En la página Instancia de proceso , seleccione el proceso y haga clic en Suspender o Aprobar.

### Finalización de instancias de proceso {#terminate-a-process-instances}

Si una operación de una instancia de proceso se ha detenido o ha encontrado alguna otra condición de error, o si necesita forzar una instancia de proceso para que deje de ejecutarse, puede finalizar la instancia de proceso.

Puede finalizar instancias de proceso que tengan cualquier estado.

Cuando finaliza una instancia de proceso, su estado cambia a TERMINATING, luego TERMINATED y el proceso se detiene en su operación actual. No se ejecutan más operaciones y se terminan todas las operaciones y tareas asociadas.

1. En la consola de administración, haga clic en Servicios > Flujo de trabajo de Forms > Flujo de trabajo de Forms.
1. En la página Instancia de proceso , seleccione el proceso y haga clic en Finalizar.

## Trabajo con detalles de instancias de proceso {#working-with-process-instance-details}

La página Detalles de Instancia de Proceso muestra el historial de una instancia de proceso.

El área Resumen muestra información básica sobre la instancia de proceso.

En la pestaña Operations , cada operación de la instancia de proceso se muestra en orden de finalización del primero al último con la siguiente información:

**Nombre de la operación:** Nombre de la operación, tal como se define en Workbench.

**Estado:** Indica si la operación se está ejecutando normalmente o se ha detenido. (Consulte Acerca de los estados de instancias de proceso).

**Nombre de rama:** Nombre de la rama, tal como se define en Workbench.

**Fecha de inicio:** Fecha y hora en que se inició la operación.

**Fecha de finalización:** La fecha y hora en que se completó la operación.

Un subproceso es una instancia de proceso que es iniciada por otro proceso y que se ejecuta independientemente de ese otro proceso. Los subprocesos solo se muestran si se diseñaron como parte del proceso en Workbench. En la ficha Subprocesos , cada subproceso se muestra con la siguiente información:

**ID de proceso:** Este entero positivo que asigna el flujo de trabajo de formularios cuando se crea una instancia del proceso (es decir, cuando un usuario o un paso automatizado inician el proceso). Puede utilizar este identificador para rastrear la instancia de proceso a lo largo de su ciclo vital.

**Nombre del proceso - Versión:** Nombre del proceso, tal como se define en Designer.

**Estado:** Indica si la instancia de proceso se está ejecutando normalmente, si cambia de estado o si se ha detenido. (Consulte Acerca de los estados de instancias de proceso).

**Fecha de creación:** Fecha y hora en que se creó el subproceso.

**Fecha de actualización:** Fecha y hora en que se cambió por última vez el estado del subproceso.

Puede realizar las siguientes tareas en la página Detalles de Instancia de Proceso:

* Seleccione una operación para ver los detalles sobre ella. Cuando se selecciona una operación, aparece la página Detalle de la operación.
* Seleccione un subproceso para ver los detalles sobre él. Cuando se selecciona un subproceso, aparece la página Detalles de Instancia de Proceso.
* Finalice o vuelva a intentar operaciones o subprocesos, según su estado.

### Acerca de los estados de operación {#about-operation-statuses}

Una operación (un paso de un proceso) puede tener los siguientes estados:

**COMPLETAR:** Se completó la operación.

**EJECUTANDO:** La operación se está ejecutando normalmente. Puede estar recibiendo entradas del usuario o esperando la interacción del usuario, o puede que haya un paso automatizado en curso.

**INACTIVADO:** Se produjo un problema mientras se procesaba la operación. Compruebe el error o la excepción en la página Operaciones interrumpidas .

**TERMINADO:** Un administrador finalizó la operación.

### Finalización de operaciones o subprocesos {#terminate-operations-or-subprocesses}

Si una operación o subproceso se ha detenido o ha encontrado alguna otra condición de error, o si necesita forzar una operación o subproceso para que deje de ejecutarse, puede terminarlo.

Puede finalizar una operación que se esté ejecutando.

Cuando finaliza una operación, su estado cambia a TERMINADO. La operación no se completa y la instancia de proceso deja de ejecutarse.

Puede finalizar un subproceso que tenga cualquier estado.

Cuando finaliza un subproceso, su estado cambia a TERMINATING, luego TERMINATED y la instancia del proceso se detiene en sus operaciones actuales. No se ejecutan más operaciones en el subproceso, aunque la instancia de proceso principal sigue ejecutándose.

No se pueden finalizar procesos que tengan elementos de puerta de enlace en el diagrama de proceso. Si intenta finalizar estos tipos de procesos, las operaciones dentro de los elementos de la puerta de enlace no se verán afectadas. Para finalizar operaciones que se encuentran dentro de un elemento de puerta de enlace, debe finalizar las operaciones directamente.

1. En la página Detalles de instancia de proceso , haga clic en la pestaña Operaciones o en la pestaña Subprocesos .
1. Seleccione la operación o el subproceso y haga clic en Finalizar.

### Reintentar una operación {#retry-an-operation}

Puede reintentar la operación que tiene el estado STALLED.

Cuando vuelve a intentar una operación, se envía una solicitud al flujo de trabajo de Forms para reiniciar la operación. Si la solicitud se realiza correctamente, el estado cambia a RUNNING. Si la operación no se puede reiniciar, permanece STALLED y es posible que tenga que terminarla.

1. En la página Detalles de instancia de proceso , haga clic en la pestaña Operaciones .
1. Seleccione la operación y haga clic en Reintentar.

## Uso de operaciones {#working-with-operations}

La página Detalles de la Operación muestra un resumen de una operación de un proceso y sus asignaciones de usuario actuales.

1. En la consola de administración, haga clic en Servicios > Flujo de trabajo de Forms > Flujo de trabajo de Forms.
1. Haga clic en un nombre de proceso para mostrar sus instancias de proceso. Haga clic en una instancia de proceso para mostrar la página Detalles de Instancia de Proceso y, a continuación, seleccione una operación para mostrar la página Detalles de Operación.

   Para cada tarea, la lista muestra la siguiente información:

   **Nombre del proceso - Versión:** Nombre del proceso, tal como se define en Workbench.

   **Aplicación:** Aplicación a la que pertenece el proceso, tal como se define en Workbench.

   **Estado:** Activo significa que el proceso es el activado para la versión del proceso. Inactivo significa que el proceso es una versión antigua que aún tiene instancias de proceso.

   **Fecha de creación:** Fecha y hora en que se implementó el proceso.
