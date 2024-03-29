---
title: Desarrollo y ampliación de flujos de trabajo
seo-title: Developing and Extending Workflows
description: AEM proporciona varias herramientas y recursos para crear modelos de flujo de trabajo, desarrollar pasos de flujo de trabajo e interactuar mediante programación con flujos de trabajo
seo-description: AEM provides several tools and resources for creating workflow models, developing workflow steps, and for programmatically interacting with workflows
uuid: 5a857589-3b13-4519-bda2-b1dab6005550
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 8954e3df-3afa-4d53-a7e1-255f3b8f499f
exl-id: 4f9bd75c-9d54-4cd6-9d73-5d580be5a9e8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1548'
ht-degree: 4%

---

# Desarrollo y ampliación de flujos de trabajo{#developing-and-extending-workflows}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM proporciona varias herramientas y recursos para crear modelos de flujo de trabajo, desarrollar pasos de flujo de trabajo e interactuar mediante programación con flujos de trabajo.

Los flujos de trabajo permiten automatizar procesos para administrar recursos y publicar contenido en el entorno de AEM. Los flujos de trabajo constan de una serie de pasos, y cada paso realiza una tarea discreta. Puede utilizar la lógica y los datos de tiempo de ejecución para tomar decisiones sobre cuándo puede continuar un proceso y seleccionar el siguiente paso de uno de los múltiples pasos posibles.

Por ejemplo, los procesos empresariales para crear y publicar páginas web incluyen las tareas de aprobación y cierre de sesión realizadas por varios participantes. Estos procesos se pueden modelar utilizando flujos de trabajo AEM y aplicar a contenido específico.

A continuación se tratan los aspectos clave, mientras que en las páginas siguientes se incluyen más detalles:

* [Creación de modelos de flujo de trabajo](/help/sites-developing/workflows-models.md)
* [Ampliación de la funcionalidad del flujo de trabajo](/help/sites-developing/workflows-customizing-extending.md)
* [Interactuar con flujos de trabajo mediante programación](/help/sites-developing/workflows-program-interaction.md)
* [Referencia de pasos de flujo de trabajo](/help/sites-developing/workflows-step-ref.md)
* [Referencia del proceso de flujo de trabajo](/help/sites-developing/workflows-process-ref.md)
* [Prácticas recomendadas del flujo de trabajo](/help/sites-developing/workflows-best-practices.md)

>[!NOTE]
>
>Para obtener información acerca de:
>
>* Participar en flujos de trabajo, consulte [Uso de flujos de trabajo](/help/sites-authoring/workflows.md).
>* Administración de flujos de trabajo e instancias de flujo de trabajo, consulte [Administración de flujos de trabajo](/help/sites-administering/workflows.md).
>* Para un artículo comunitario completo, véase [Modificación de recursos digitales mediante flujos de trabajo de Adobe Experience Manager.](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)
>* Consulte la [Seminario web de consultas a expertos de AEM sobre flujos de trabajo](https://bit.ly/ATACE218).
>* Para un artículo comunitario completo, véase [Creación de un paso de participante dinámico de Adobe Experience Manager 6.3 personalizado](https://helpx.adobe.com/experience-manager/using/dynamic-steps-aem63.html).
>* Cambios en las ubicaciones de la información consulte [Reestructuración de repositorios en AEM 6.4](/help/sites-deploying/repository-restructuring.md) y [Prácticas recomendadas del flujo de trabajo: ubicaciones](/help/sites-developing/workflows-best-practices.md#locations).
>


## Modelo {#model}

A `WorkflowModel` representa una definición (modelo) de un flujo de trabajo. Está hecho de `WorkflowNodes` y `WorkflowTransitions`. Las transiciones conectan los nodos y definen la variable *flujo*. El modelo siempre tiene un nodo de inicio y un nodo final.

### Modelo de tiempo de ejecución {#runtime-model}

Los modelos de flujo de trabajo tienen versiones. Cuando ejecute una instancia de flujo de trabajo, utilizará (y mantendrá) el modelo de tiempo de ejecución del flujo de trabajo (como disponible en el momento en que se inició el flujo de trabajo).

Un modelo de tiempo de ejecución es [generado cuando **Sincronización** se activa en el editor de modelos de flujo de trabajo](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model).

Edita al modelo de flujo de trabajo que se produce y/o a los modelos de tiempo de ejecución que se generan, *after* la instancia específica iniciada no se aplicará a esa instancia.

>[!CAUTION]
>
>Los pasos realizados son los definidos por la variable [modelo runtime](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model); esto se genera en el momento en que se genera la variable **Sincronización** se activa en el editor de modelos de flujo de trabajo.
>
>Si el modelo de flujo de trabajo se cambia después de este momento (sin **Sincronización** que se activan), la instancia de tiempo de ejecución no reflejará esos cambios. Solo los modelos de tiempo de ejecución generados después de la actualización reflejarán los cambios. Las excepciones son los scripts ECMA subyacentes, que se mantienen solo una vez que se realizan cambios en ellos.

### Paso {#step}

Cada paso realiza una tarea discreta. Existen diferentes tipos de pasos de flujo de trabajo:

* Participante (usuario/grupo): Estos pasos generan un elemento de trabajo y lo asignan a un usuario o grupo. Un usuario debe completar el elemento de trabajo para avanzar en el flujo de trabajo.
* Proceso (Script, llamada de método Java): El sistema ejecuta automáticamente estos pasos. Una secuencia de comandos ECMA o una clase Java implementan el paso . Los servicios se pueden desarrollar para escuchar eventos de flujo de trabajo especiales y realizar tareas según la lógica empresarial.
* Contenedor (Subflujo de trabajo): Este tipo de paso inicia otro modelo de flujo de trabajo.
* O Dividir/Unir: Utilice la lógica para decidir qué paso ejecutar a continuación en el flujo de trabajo.
* Y Dividir/Unir: Permite ejecutar varios pasos simultáneamente.

Todos los pasos comparten las siguientes propiedades comunes: `Autoadvance` y `Timeout` alertas (lista de comandos).

### Transición {#transition}

A `WorkflowTransition` representa una transición entre dos `WorkflowNodes` de `WorkflowModel`.

* Define el vínculo entre dos pasos consecutivos.
* Es posible aplicar reglas.

### WorkItem {#workitem}

A `WorkItem` es la unidad que pasa a través de un `Workflow` instancia de un `WorkflowModel`. Contiene el `WorkflowData` que la instancia actúa en y una referencia a la variable `WorkflowNode` que describe el paso subyacente del flujo de trabajo.

* Se utiliza para identificar la tarea y se coloca en la bandeja de entrada correspondiente.
* Una instancia de flujo de trabajo puede tener una o varias `WorkItems` al mismo tiempo (según el modelo de flujo de trabajo).
* La variable `WorkItem` hace referencia a la instancia de flujo de trabajo.
* En el repositorio, la variable `WorkItem` se almacena debajo de la instancia de flujo de trabajo.

### Carga útil {#payload}

Hace referencia al recurso que debe avanzarse a través de un flujo de trabajo.

La implementación de carga útil hace referencia a un recurso en el repositorio (por ruta, UUID o URL) o por un objeto java serializado. Hacer referencia a un recurso en el repositorio es muy flexible y junto con sling es muy productivo; por ejemplo, el nodo al que se hace referencia se puede representar como un formulario.

### Ciclo de vida {#lifecycle}

Se crea al iniciar un nuevo flujo de trabajo (eligiendo el modelo de flujo de trabajo correspondiente y definiendo la carga útil) y finaliza cuando se procesa el nodo final.

Las siguientes acciones son posibles en una instancia de flujo de trabajo:

* Terminar
* Suspender
* Reanudar
* Reiniciar

Las instancias completadas y terminadas se archivan.

### Bandeja de entrada {#inbox}

Cada cuenta de usuario tiene su propia bandeja de entrada de flujo de trabajo en la que se asigna la variable `WorkItems` son accesibles.

La variable `WorkItems` se asignan directamente a la cuenta de usuario o al grupo al que pertenecen.

### Tipos de flujo de trabajo {#workflow-types}

Existen varios tipos de flujo de trabajo, como se indica en la consola Modelos de flujo de trabajo :

![wf-upgrade-03](assets/wf-upgraded-03.png)

* **Predeterminado**

   Estos son los flujos de trabajo listos para usar incluidos en una instancia de AEM estándar.

* Flujos de trabajo personalizados (sin indicador en la consola)

   Son flujos de trabajo que se han creado como nuevos o a partir de flujos de trabajo listos para usar que se han superpuesto con personalizaciones.

* **Heredado**

   Flujos de trabajo creados en una versión anterior de AEM. Se pueden conservar durante una actualización o exportar como paquete de flujo de trabajo desde la versión anterior y luego importarlos a la nueva versión.

### Flujos de trabajo transitorios {#transient-workflows}

Los flujos de trabajo estándar guardan información de tiempo de ejecución (historial) durante su ejecución. También puede definir un modelo de flujo de trabajo como **Transitorio** para evitar que esta historia persista. Se utiliza para ajustar el rendimiento, ya que ahorra o evita el tiempo o los recursos utilizados para mantener la información.

Los flujos de trabajo transitorios se pueden utilizar para cualquier flujo de trabajo que:

* se ejecutan a menudo.
* no necesitan el historial del flujo de trabajo.

Se introdujeron flujos de trabajo transitorios para cargar un gran número de recursos, donde la información de los recursos es importante, pero no el historial de tiempo de ejecución del flujo de trabajo.

>[!NOTE]
>
>Consulte [Creación de un flujo de trabajo transitorio](/help/sites-developing/workflows-models.md#creating-a-transient-workflow) para obtener más información.

>[!CAUTION]
>
>Cuando un modelo de flujo de trabajo se ha marcado como transitorio, existen algunos escenarios en los que la información de tiempo de ejecución se mantendrá:
>
>* El tipo de carga útil (por ejemplo, vídeo) requiere pasos externos para el procesamiento; en estos casos, el historial de tiempo de ejecución es necesario para la confirmación del estado.
>* El flujo de trabajo introduce un **División AND**; en estos casos, el historial de tiempo de ejecución es necesario para la confirmación del estado.
>* Cuando el flujo de trabajo transitorio entra en un paso del participante, cambia de modo (durante la ejecución) a no transitorio; como la tarea se pasa a una persona, el historial debe conservarse
>


>[!CAUTION]
>
>Dentro de un flujo de trabajo transitorio no debe utilizar una **Ir al paso**.
>
>Esto es como el **Ir al paso** crea un trabajo de sling para continuar con el flujo de trabajo en el `goto` punto. Esto impide que el flujo de trabajo sea transitorio y genera un error en el archivo de registro.
>
>Para tomar decisiones en un flujo de trabajo transitorio, puede utilizar la variable **División OR**.

>[!NOTE]
>
>Consulte [Prácticas recomendadas para recursos](/help/assets/performance-tuning-guidelines.md#transient-workflows) para obtener más información sobre cómo afectan los flujos de trabajo transitorios al rendimiento de los recursos.

### Compatibilidad con varios recursos {#multi-resource-support}

Activación **Compatibilidad con varios recursos** para el modelo de flujo de trabajo, se inicia una sola instancia de flujo de trabajo incluso cuando se seleccionan varios recursos; se adjuntarán como paquete.

If **Compatibilidad con varios recursos** no está activada para el modelo de flujo de trabajo y se seleccionan varios recursos, se inicia una instancia de flujo de trabajo individual para cada recurso.

>[!NOTE]
>
>Consulte [Configuración de un flujo de trabajo para compatibilidad con varios recursos](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) para obtener más información.

### Etapas del flujo de trabajo {#workflow-stages}

Las etapas del flujo de trabajo ayudan a visualizar el progreso de un flujo de trabajo al administrar tareas. Se pueden utilizar para proporcionar una descripción general de hasta dónde alcanza el flujo de trabajo mediante el procesamiento, ya que cuando se ejecuta el flujo de trabajo, el usuario puede ver el progreso descrito por **Prueba** (a diferencia de los pasos individuales).

Como los nombres de paso individuales pueden ser específicos y técnicos, los nombres de escenario se pueden definir para proporcionar una vista conceptual del progreso del flujo de trabajo.

Por ejemplo, para un flujo de trabajo con seis pasos y cuatro etapas:

1. Puede [configure las fases del flujo de trabajo (que muestran el progreso del flujo de trabajo) y luego asigne la fase adecuada a cada paso del flujo de trabajo](/help/sites-developing/workflows-models.md#configuring-workflow-stages-that-show-workflow-progress):

   * Se pueden crear varios nombres de escenario.
   * A continuación, se asigna un nombre de escenario individual a cada paso (se puede asignar un nombre de escenario a uno o varios pasos).

   | **Nombre del paso** | **Etapa (asignada al paso)** |
   |---|---|
   | Etapa 1 | Crear |
   | Etapa 2 | Crear |
   | Etapa 3 | Revisión |
   | Etapa 4 | Aprobar |
   | Etapa 5 | Completar |
   | Etapa 6 | Completar |

1. Cuando se ejecuta el flujo de trabajo, el usuario puede ver el progreso según los nombres de las fases (en lugar de los nombres de las etapas). El progreso del flujo de trabajo se muestra en la variable [Ficha INFORMACIÓN DEL FLUJO DE TRABAJO de la ventana de detalles de la tarea del elemento de trabajo](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) en la [Bandeja de entrada](/help/sites-authoring/inbox.md).

### Flujos de trabajo y Forms {#workflows-and-forms}

Normalmente, los flujos de trabajo se utilizan para procesar los envíos de formularios en AEM. Esto puede ser con la variable [componentes principales componentes de formulario](https://helpx.adobe.com/experience-manager/core-components/using/form-container.html) disponible en una instancia de AEM estándar o con la variable [Solución AEM Forms](/help/forms/using/aem-forms-workflow.md).

Al crear un nuevo formulario, el envío del formulario puede asociarse fácilmente con un modelo de flujo de trabajo; por ejemplo, para almacenar el contenido en una ubicación concreta del repositorio o para notificar al usuario sobre el envío del formulario y su contenido.

### Flujos de trabajo y traducción {#workflows-and-translation}

Los flujos de trabajo también son parte integral de [Traducción](/help/sites-administering/translation.md) proceso.
