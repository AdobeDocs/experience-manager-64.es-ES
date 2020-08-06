---
title: Prácticas recomendadas de descarga de recursos
description: Casos de uso recomendados y prácticas recomendadas para descargar flujos de trabajo de replicación e ingestión de recursos en AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# Prácticas recomendadas de descarga de recursos {#assets-offloading-best-practices}

>[!WARNING]
>
>Esta función está en desuso AEM la versión 6.4 y se elimina en la AEM 6.5. Planifique en consecuencia.

La administración de archivos de gran tamaño y flujos de trabajo en ejecución en Adobe Experience Manager (AEM) Assets puede consumir considerables recursos de CPU, memoria y E/S. En particular, el tamaño de los recursos, los flujos de trabajo, el número de usuarios y la frecuencia con la que se realiza la ingesta de recursos pueden afectar al rendimiento general del sistema. Las operaciones con mayor uso de recursos incluyen AEM flujos de trabajo de replicación e ingestión de recursos. El uso intensivo de estos flujos de trabajo en una sola instancia de creación de AEM puede afectar negativamente a la eficacia de la creación.

La descarga de estas tareas a instancias de trabajo dedicadas puede reducir los gastos de CPU, memoria y E/S. En general, la idea detrás de la descarga es distribuir tareas que consuman recursos intensivos de CPU/memoria/E a instancias de trabajo dedicadas. Las siguientes secciones incluyen casos de uso recomendados para la descarga de recursos.

## Descarga de AEM Assets {#aem-assets-offloading}

AEM Assets implementa una extensión de flujo de trabajo específica de recursos nativa para la descarga. Se basa en la extensión genérica del flujo de trabajo que proporciona el marco de descarga, pero incluye funciones adicionales específicas de los recursos en la implementación. El objetivo de la descarga de recursos es ejecutar eficazmente el flujo de trabajo de recursos de actualización de DAM en un recurso cargado. La descarga de recursos le permite obtener un bueno control de los flujos de trabajo de ingestión.

## Componentes de descarga de AEM Assets {#aem-assets-offloading-components}

En el diagrama siguiente se muestran los componentes principales del proceso de descarga de recursos:

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM Update Asset Offloading workflow {#dam-update-asset-offloading-workflow}

El flujo de trabajo de descarga de recursos de actualización de DAM se ejecuta en el servidor principal (autor) en el que el usuario carga los recursos. Este flujo de trabajo se activa mediante un iniciador de flujo de trabajo normal. En lugar de procesar el recurso cargado, este flujo de trabajo de descarga crea un nuevo trabajo con el tema *com/adobe/granite/workflow/offloading*. El flujo de trabajo de descarga agrega el nombre del flujo de trabajo de destinatario: el flujo de trabajo de recursos de actualización de DAM en este caso y la ruta del recurso a la carga útil del trabajo. Después de crear el trabajo de descarga, el flujo de trabajo de descarga en la instancia principal espera hasta que se ejecute el trabajo de descarga.

### Administrador de trabajos {#job-manager}

El administrador de trabajos distribuye nuevos trabajos a instancias de trabajador. Al diseñar el mecanismo de distribución, es importante tener en cuenta la habilitación de temas. Los trabajos solo se pueden asignar a instancias en las que el tema del trabajo está activado. Deshabilite el tema `com/adobe/granite/workflow/offloading` en el principal y habilite el trabajo en el trabajador para asegurarse de que el trabajo está asignado al trabajador.

### AEM descarga {#aem-offloading}

El marco de descarga identifica los trabajos de descarga de flujo de trabajo asignados a instancias de trabajador y utiliza la replicación para transportarlos físicamente, incluida su carga útil (por ejemplo, imágenes que se van a ingerir), a los trabajadores.

### Consumidor de trabajo de descarga de flujo de trabajo {#workflow-offloading-job-consumer}

Una vez que se ha escrito un trabajo en el trabajador, el administrador de trabajos llama al consumidor del trabajo responsable del tema *com/adobe/granite/workflow/offloading* . A continuación, el consumidor del trabajo ejecuta el flujo de trabajo de recursos de actualización de DAM en el recurso.

## Topología de Sling {#sling-topology}

La topología de Sling agrupa AEM instancias y les permite ser conscientes entre sí, independientemente de la persistencia subyacente. Esta característica de la topología Sling permite crear topologías para escenarios no agrupados, agrupados y mixtos. Una instancia puede exponer propiedades a toda la topología. El marco proporciona llamadas de retorno para escuchar los cambios en la topología (instancias y propiedades). La topología Sling proporciona la base para los trabajos distribuidos Sling.

### Creación de trabajos distribuidos {#sling-distributed-jobs}

La división de trabajos distribuidos facilita la distribución de trabajos entre un conjunto de instancias que son miembros de la topología. Los trabajos de Sling se basan en la idea de las capacidades. Un trabajo se define por su tema de trabajo. Para ejecutar un trabajo, una instancia debe proporcionar un consumidor de trabajo para un tema de trabajo específico. El tema de trabajo es el principal controlador del mecanismo de distribución.

Los trabajos solo se distribuyen a instancias que proporcionan un consumidor de trabajo para el tema. Al habilitar o deshabilitar los consumidores de trabajos en una instancia, puede definir las capacidades de una instancia e influir en el mecanismo de distribución. Los consumidores de trabajo disponibles de una instancia se transmiten a toda la topología.

En este contexto, el término distribución significa la asignación de un trabajo a una instancia específica que proporciona un consumidor de trabajo. La asignación a una instancia se almacena en el repositorio. En otras palabras, los trabajos distribuidos de Sling se pueden asignar a cualquier instancia de la topología de forma predeterminada. Sin embargo, otros trabajos solo se pueden ejecutar con instancias que compartan el mismo repositorio. Esto implica que estos trabajos solo pueden ejecutarse en instancias que formen parte del mismo clúster. Los trabajos asignados a instancias de un clúster diferente no se ejecutan.

### Granite offloading framework {#granite-offloading-framework}

El marco de descarga Granite complementa la distribución de trabajos Sling para ejecutar trabajos asignados a instancias no agrupadas. No realiza ninguna distribución (asignación de instancia). Sin embargo, identifica los trabajos de Sling que se distribuyeron a instancias no agrupadas y los transporta a la instancia de destinatario para su ejecución. Actualmente, la descarga utiliza la replicación para realizar este transporte de trabajo. Para ejecutar un trabajo, la descarga define la entrada y la salida, que luego se combinan con el trabajo para generar la carga útil del trabajo.

La sling de los trabajos distribuidos proporciona el marco de trabajo y distribución. La descarga de granito sólo se ocupa del transporte en el caso especial en que los trabajos se distribuyen a instancias no agrupadas.

Además del transporte, el sistema de descarga ofrece una ampliación del motor de flujos de trabajo. Permite al marco crear trabajos distribuidos como parte de un flujo de trabajo y esperar a que se completen, antes de que avance el flujo de trabajo. Se implementa mediante la API de paso externo del flujo de trabajo del motor de flujos de trabajo. Una de las extensiones facilita la distribución genérica de flujos de trabajo. No se admite la distribución de pasos de flujo de trabajo únicos.

El marco de descarga también incluye una interfaz de usuario para visualizar y controlar la habilitación de temas de trabajo en toda la topología. La interfaz de usuario le permite configurar convenientemente la habilitación de temas de los trabajos distribuidos de Sling. También puede configurar la descarga sin la interfaz de usuario.

## Directrices generales y prácticas recomendadas para la descarga de activos {#general-guidance-and-best-practices-for-asset-offloading}

Cada implementación es única y, como tal, no existe una configuración de descarga única para todos los casos. Las siguientes secciones proporcionan orientación y optimizaciones sobre la descarga de ingesta de recursos.

La descarga de activos también impone gastos generales al sistema, incluidos los gastos generales de funcionamiento. Si se producen problemas con la carga de ingestión de recursos, Adobe recomienda mejorar primero la configuración sin descargar. Considere las siguientes opciones antes de pasar a la descarga de recursos:

* Escalar hardware
* Optimizar flujos de trabajo
* Usar flujos de trabajo transitorios
* Limitar el número de núcleos utilizados para los flujos de trabajo

Si llega a la conclusión de que la descarga de recursos es un método adecuado para usted, Adobe proporciona las siguientes instrucciones:

* Se recomienda una implementación basada en TarMK
* La descarga de recursos basada en TarMK no está diseñada para una amplia escala horizontal
* Garantizar que el rendimiento de la red entre el autor y los trabajadores sea satisfactorio

### Implementación de descarga de recursos recomendada {#recommended-assets-offloading-deployment}

Con AEM y Oak, existen varios escenarios de implementación posibles. Para la descarga de recursos, se recomienda una implementación basada en TarMK con un almacén de datos compartido. El diagrama siguiente describe la implementación recomendada:

![chlimage_1-56](assets/chlimage_1-56.png)

Para obtener más información sobre la configuración de un almacén de datos, consulte [Configuración de almacenes de nodos y almacenes de datos en AEM](../sites-deploying/data-store-config.md).

### Desactivación de la administración automática de agentes {#turning-off-automatic-agent-management}

Adobe recomienda desactivar la administración automática de agentes porque no admite replicación sin binarios y puede causar confusión al configurar una nueva topología de descarga. Además, no soporta automáticamente el flujo de replicación hacia adelante requerido por la replicación sin binarios.

1. Abra Configuration Manager desde la dirección URL `http://localhost:4502/system/console/configMgr`.
1. Abra la configuración para `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Deshabilite la administración automática de agentes.

### Uso de la replicación avanzada {#using-forward-replication}

De forma predeterminada, el transporte de descarga utiliza la replicación inversa para recuperar los recursos descargados del programa de trabajo al principal. Los agentes de replicación inversa no admiten replicación sin binarios. Debe configurar la descarga para que utilice la replicación de reenvío a fin de que los recursos descargados vuelvan del programa de trabajo al primario.

1. Si va a realizar la migración desde la configuración predeterminada mediante la replicación inversa, deshabilite o elimine todos los agentes denominados &quot; `offloading_outbox`&quot; y &quot; `offloading_reverse_*`&quot; en el programa de trabajo y en el programa de trabajo principal, donde &amp;ast; representa el identificador Sling de la instancia de destinatario.
1. En cada programa de trabajo, cree un nuevo agente de replicación avanzada que apunte al programa principal. El procedimiento es el mismo que crear agentes de reenvío de principal a trabajador. Consulte [Creación de agentes de replicación para descarga](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) para obtener instrucciones sobre cómo configurar agentes de replicación de descarga.
1. Abra la configuración para `OffloadingDefaultTransporter` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Cambiar el valor de la propiedad `default.transport.agent-to-master.prefix` de `offloading_reverse` a `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Uso del almacén de datos compartido y la replicación sin binarios entre el autor y los trabajadores  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

Se recomienda el uso de replicación sin binarios para reducir la sobrecarga de transporte de descarga de recursos. Para saber cómo configurar la replicación sin binarios para un almacén de datos compartido, consulte [Configuración de almacenes de nodos y almacenes de datos en AEM](/help/sites-deploying/data-store-config.md). El procedimiento no es diferente para la descarga de recursos, excepto que incluye otros agentes de replicación. Debido a que la replicación sin binarios sólo funciona con agentes de replicación de avanzada, también debe utilizar la replicación de reenvío para todos los agentes de descarga.

### Desactivación de paquetes de transporte {#turning-off-transport-packages}

De forma predeterminada, la descarga crea un paquete de contenido que contiene el trabajo de descarga y la carga útil del trabajo (el recurso original) y transporta este paquete de descarga único mediante una única solicitud de replicación. La creación de estos paquetes de descarga es contraproducente al usar replicación sin binarios, ya que los binarios se serializan nuevamente en el paquete al crear el paquete. El uso de estos paquetes de transporte se puede desactivar, lo que provoca que el trabajo de descarga y la carga útil se transporten en varias solicitudes de replicación, una por cada entrada de carga útil. De esta manera, se puede utilizar el beneficio de la replicación sin binarios.

1. Abra la configuración de componentes del componente *OffloadingDefaultTransporter* en [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Deshabilite la propiedad *Replication Package (default.Transport.contentpackage)*.

### Desactivación del transporte del modelo de flujo de trabajo {#disabling-the-transport-of-workflow-model}

De forma predeterminada, el flujo de trabajo de descarga *de recursos de actualización de* DAM agrega el modelo de flujo de trabajo para llamar al trabajador a la carga útil de trabajo. Debido a que este flujo de trabajo sigue de forma predeterminada el modelo *DAM Update Asset* incorporado, esta carga útil adicional se puede eliminar.

Si el modelo de flujo de trabajo está desactivado desde la carga útil del trabajo, asegúrese de distribuir los cambios al modelo de flujo de trabajo al que se hace referencia mediante otras herramientas, como el administrador de paquetes.

Para desactivar el transporte del modelo de flujo de trabajo, modifique el flujo de trabajo de descarga de recursos de actualización de DAM.

1. Abra la consola de flujo de trabajo desde [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Abra la ficha Modelos.
1. Abra el modelo de flujo de trabajo de descarga de recursos de actualización DAM.
1. Abra las propiedades de paso para el paso Descarga del flujo de trabajo DAM.
1. Abra la ficha Argumentos y anule la selección de las opciones Añadir modelo a entrada y Añadir modelo a salida.
1. Guarde los cambios en el modelo.

### Optimización del intervalo de sondeo {#optimizing-the-polling-interval}

La descarga del flujo de trabajo se implementa mediante un flujo de trabajo externo en el servidor primario, que sondea la finalización del flujo de trabajo descargado en el programa de trabajo. El intervalo de sondeo predeterminado para los procesos de flujo de trabajo externo es de cinco segundos. Adobe recomienda aumentar el intervalo de sondeo del paso de descarga de recursos a al menos 15 segundos para reducir la sobrecarga de descarga en el elemento principal.

1. Abra la consola de flujo de trabajo desde [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Abra la ficha Modelos.
1. Abra el modelo de flujo de trabajo de descarga de recursos de actualización DAM.
1. Abra las propiedades de paso del paso Descarga del flujo de trabajo DAM.
1. Abra la ficha Commons y ajuste el valor de la propiedad Period.
1. Guarde los cambios en el modelo.

## Más recursos {#more-resources}

Este documento se centra en la descarga de recursos. A continuación se muestra una documentación adicional sobre la descarga:

* [Descarga de trabajos](/help/sites-deploying/offloading.md)
* [Descarga del flujo de trabajo de recursos](/help/sites-administering/workflow-offloader.md)

