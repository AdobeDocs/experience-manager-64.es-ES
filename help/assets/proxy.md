---
title: Desarrollo de proxy de recursos
description: 'Un proxy es una instancia AEM que utiliza trabajadores proxy para procesar trabajos. Obtenga información sobre cómo configurar un proxy AEM, las operaciones compatibles, los componentes proxy y cómo desarrollar un trabajador proxy personalizado. '
contentOwner: AG
feature: Procesamiento de recursos
role: Admin, Architect
exl-id: c7511326-697e-4749-ab46-513cdbaa00d8
source-git-commit: fc725206728e238ab9da1fb30cee8fb407257b62
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Desarrollo de proxy de recursos {#assets-proxy-development}

Adobe Experience Manager (AEM) Assets utiliza un proxy para distribuir el procesamiento de determinadas tareas.

Un proxy es una instancia específica (y a veces independiente) AEM que utiliza los trabajadores proxy como procesadores responsables de gestionar un trabajo y crear un resultado. Un trabajador proxy puede utilizarse para una amplia variedad de tareas. En el caso de un proxy AEM Assets, se puede utilizar para cargar recursos para procesarlos en AEM Assets. Por ejemplo, el [IDS proxy worker](indesign.md) utiliza un InDesign Server para procesar archivos para utilizarlos en AEM Assets.

Cuando el proxy es una instancia de AEM independiente, esto ayuda a reducir la carga en las instancias de creación de AEM. De forma predeterminada, AEM Assets ejecuta las tareas de procesamiento de recursos en la misma JVM (externalizada mediante proxy) para reducir la carga en la instancia de creación de AEM.

## Proxy (acceso HTTP) {#proxy-http-access}

Hay un proxy disponible a través del servlet HTTP cuando está configurado para aceptar trabajos de procesamiento en: `/libs/dam/cloud/proxy`. Este servlet crea un trabajo de sling a partir de los parámetros registrados. A continuación, esto se agrega a la cola de trabajos del proxy y se conecta al trabajador del proxy adecuado.

### Operaciones compatibles {#supported-operations}

* `job`

   **Requisitos**: el parámetro  `jobevent` debe establecerse como mapa de valores serializado. Se utiliza para crear un `Event` para un procesador de trabajos.

   **Resultado**: Agrega un nuevo trabajo. Si se realiza correctamente, se devuelve un identificador de trabajo único.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Requisitos**: se  `jobid` debe configurar el parámetro .

   **Resultado**: Devuelve una representación JSON del nodo de resultado creado por el procesador de trabajos.

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **Requisitos**: se debe establecer el parámetro jobid .

   **Resultado**: Devuelve un recurso asociado al trabajo dado.

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **Requisitos**: se debe establecer el parámetro jobid .

   **Resultados**: Elimina un trabajo si se encuentra.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Trabajador de proxy {#proxy-worker}

Un trabajador proxy es un procesador responsable de gestionar un trabajo y crear un resultado. Los trabajadores residen en la instancia de proxy y deben implementar [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) para que se reconozca como trabajador de proxy.

>[!NOTE]
>
>El trabajador debe implementar [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) para que se reconozca como trabajador proxy.

### API de cliente {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) está disponible como servicio de OSGi que proporciona métodos para crear trabajos, eliminarlos y obtener resultados de esos trabajos. La implementación predeterminada de este servicio (`JobServiceImpl`) utiliza el cliente HTTP para comunicarse con el servlet proxy remoto.

El siguiente es un ejemplo de uso de API:

```java
@Reference
 JobService proxyJobService;

 // to create a new job
 final Hashtable props = new Hashtable();
 props.put("someproperty", "some value");
 props.put(JobUtil.PROPERTY_JOB_TOPIC, "myworker/job"); // this is an identifier of the worker
 final String jobId = proxyJobService.addJob(props, new Asset[]{asset});

 // to check status (returns JobService.STATUS_FINISHED or JobService.STATUS_INPROGRESS)
 int status = proxyJobService.getStatus(jobId)

 // to get the result
 final String jsonString = proxyJobService.getResult(jobId);

 // to remove job and cleanup
 proxyJobService.removeJob(jobId);
```

### Configuraciones de Cloud Service {#cloud-service-configurations}

>[!NOTE]
>
>La documentación de referencia para la API proxy está disponible en [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/commons/proxy/package-summary.html).

Tanto las configuraciones de trabajo proxy como las de proxy están disponibles mediante configuraciones de servicios en la nube a las que se puede acceder desde la consola de AEM Assets **Tools** o en `/etc/cloudservices/proxy`. Se espera que cada trabajador proxy agregue un nodo en `/etc/cloudservices/proxy` para detalles de configuración específicos del trabajador (por ejemplo, `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Consulte [Configuración del trabajo proxy de Indesign Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) y [configuración de Cloud Services](../sites-developing/extending-cloud-config.md) para obtener más información.

El siguiente es un ejemplo de uso de API:

```java
@Reference(policy = ReferencePolicy.STATIC)
 ProxyConfig proxyConfig;
 
 // to get proxy config
 Configuration cloudConfig = proxyConfig.getConfiguration();
 final String value = cloudConfig.get("someProperty", "defaultValue");

 // to get worker config
 Configuration cloudConfig = proxyConfig.getConfiguration("workername");
 final String value = cloudConfig.get("someProperty", "defaultValue");
```

### Desarrollo de un Trabajador de Proxy Personalizado {#developing-a-customized-proxy-worker}

El [IDS proxy worker](indesign.md) es un ejemplo de un programa de trabajo de proxy de AEM Assets que ya se ha proporcionado de forma predeterminada para externalizar el procesamiento de los recursos de Indesign.

También puede desarrollar y configurar su propio trabajador proxy de AEM Assets para crear un trabajador especializado que distribuya y externalice sus tareas de procesamiento de AEM Assets.

La configuración de su propio trabajador proxy personalizado requiere que:

* Configure e implemente (mediante eventos de Sling):

   * un tema de trabajo personalizado
   * un controlador de eventos de trabajo personalizado

* A continuación, utilice la API de JobService para:

   * envíe su trabajo personalizado al proxy
   * administrar su trabajo

* Si desea utilizar el proxy desde un flujo de trabajo, debe implementar un paso externo personalizado mediante la API WorkflowExternalProcess y la API JobService.

El diagrama y los pasos siguientes detallan cómo continuar:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>En los pasos siguientes, los equivalentes de Indesign se indican como ejemplos de referencia.

1. Se utiliza un [trabajo de Sling](https://sling.apache.org/site/eventing-and-jobs.html), por lo que debe definir un tema de trabajo para su caso de uso.

   Como ejemplo, consulte `IDSJob.IDS_EXTENDSCRIPT_JOB` para el programa de trabajo del proxy IDS.

1. El paso externo se utiliza para almacenar en déclencheur el evento y luego esperar hasta que finalice; esto se hace sondeando en el id. Debe desarrollar su propio paso para implementar la nueva funcionalidad.

   Implemente un `WorkflowExternalProcess`, luego use la API de JobService y el tema de su trabajo para preparar un evento de trabajo y enviarlo al JobService (un servicio OSGi).

   Como ejemplo, consulte `INDDMediaExtractProcess`.java para el programa de trabajo del proxy IDS.

1. Implemente un controlador de trabajo para su tema. Este controlador requiere desarrollo para que realice su acción específica y se considere la implementación del trabajador.

   Como ejemplo, consulte `IDSJobProcessor.java` para el programa de trabajo del proxy IDS.

1. Utilice `ProxyUtil.java` en dam-commons. Esto le permite enviar trabajos a los trabajadores usando el proxy de la represa.

>[!NOTE]
>
>Lo que el marco de proxy de AEM Assets no proporciona de forma predeterminada es el mecanismo de agrupación.
>
>La integración de InDesign permite el acceso a un grupo de servidores de indesign (IDSPool). Este agrupamiento es específico de la integración de Indesign y no forma parte del marco de proxy de AEM Assets.

>[!NOTE]
>
>Sincronización de resultados:
>
>Con n instancias que utilizan el mismo proxy, el resultado de procesamiento permanece con el proxy. Es tarea del cliente (AEM Author) solicitar el resultado utilizando el mismo identificador de trabajo único que se da al cliente en la creación de trabajos. El proxy simplemente realiza el trabajo y mantiene el resultado listo para ser solicitado.
