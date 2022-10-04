---
title: Interacción con la red troncal
seo-title: Backbone interaction
description: Información conceptual sobre el uso de modelos JavaScript de red troncal en el espacio de trabajo de AEM Forms.
seo-description: Conceptual information about use of Backbone JavaScript models in AEM Forms workspace.
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
exl-id: f726cb73-732c-4893-bdb5-10ddcf4a340a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Interacción con la red troncal {#backbone-interaction}

La estructura básica es una biblioteca que ayuda a crear y seguir la arquitectura de MVC en aplicaciones web. La idea básica de la estructura básica es organizar la interfaz en vistas lógicas, respaldadas por modelos, cada una de las cuales se puede actualizar de forma independiente cuando cambia el modelo, sin tener que volver a dibujar la página. Para obtener más información sobre la estructura básica, consulte [https://backbonejs.org](https://backbonejs.org/).

Algunos conceptos clave son los siguientes:

**Modelo de red troncal** Contiene datos y la mayoría de la lógica relacionada con estos datos.

**Vista de red troncal** Se utiliza para representar el estado del modelo correspondiente. Una vista de red básica se comporta realmente como un controlador, escuchando eventos de interfaz de usuario como clics de usuarios o modelando eventos (como los datos modificados), y modifica la interfaz de usuario según corresponda.

**plantilla de HTML** Una plantilla de envoltorio que tiene marcadores de posición rellenados por el modelo.

**Espacio de trabajo de AEM Forms** Contiene varios componentes individuales. Cada componente:

* Representa un solo elemento de interfaz de usuario lógico.
* Puede ser una colección de componentes similares.
* Se compone de modelo de la estructura básica, vista de la estructura básica y plantilla de HTML.
* Contiene referencia a un servicio.
* Contiene referencia a las utilidades requeridas.

Cuando se inicializa un componente, se crean los siguientes objetos:

* Se crea una nueva instancia del modelo de red básica para el componente. El servicio se inserta en el modelo.
* Se crea una nueva instancia de la vista de la columna vertebral.
* La instancia del modelo correspondiente, la plantilla de HTML y las utilidades se insertan en la vista.

En la vista de la red troncal, hay un mapa de eventos que asigna los distintos eventos que pueden surgir debido a las interacciones de la interfaz de usuario con un controlador correspondiente. Esta asignación se inicia una vez que se inicializa un componente.

Cuando se inicializa una vista, esta llama a su modelo correspondiente para recuperar datos del servidor. Una vez que todos los datos requeridos por una vista están disponibles, la vista procesa los datos en el formato especificado por la plantilla de HTML. Varias vistas pueden compartir el mismo modelo para la comunicación.

![](do-not-localize/aem_forms_workflow.png)

Un ejemplo:

1. El usuario hace clic en una plantilla de tarea de la lista de tareas.
1. La vista de tareas escucha el clic y llama a la función de renderización en el modelo de tareas.
1. El modelo de tareas llama posteriormente al servicio, que es un punto común para todas las comunicaciones con el servidor de AEM Forms.
1. La clase de servicio llama al extremo REST de AEM Forms para el método de renderización mediante ajax.
1. La llamada de retorno de éxito para esta invocación de Ajax se define en el modelo de tareas.
1. El modelo de tareas genera un evento de red básica cuando se completa la llamada de procesamiento.
1. Otra vista, la vista de detalles de tareas, escucha este suceso desde el modelo de tareas.
1. La vista Detalles de la tarea cambia la plantilla de detalles de la tarea para mostrar la tarea procesada (formulario, detalles, archivos adjuntos, notas, etc.) al usuario.
