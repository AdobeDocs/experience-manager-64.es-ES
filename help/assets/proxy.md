---
title: Desarrollo de proxy de recursos
description: Un proxy es un [!DNL Experience Manager] instancia que utiliza trabajadores proxy para procesar trabajos. Obtenga información sobre cómo configurar un [!DNL Experience Manager] proxy, operaciones compatibles, componentes proxy y cómo desarrollar un trabajador proxy personalizado.
contentOwner: AG
feature: Asset Processing
role: Admin, Architect
exl-id: c7511326-697e-4749-ab46-513cdbaa00d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 1%

---

# Desarrollo de proxy de recursos {#assets-proxy-development}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets utiliza un proxy para distribuir el procesamiento de determinadas tareas.

Un proxy es específico (y a veces independiente) [!DNL Experience Manager] instancia que utiliza trabajadores proxy como procesadores responsables de gestionar un trabajo y crear un resultado. Un trabajador proxy puede utilizarse para una amplia variedad de tareas. En el caso de un [!DNL Experience Manager] El proxy de recursos se puede utilizar para cargar recursos para procesarlos en [!DNL Experience Manager] Recursos. Por ejemplo, la variable [Trabajador de proxy IDS](indesign.md) utiliza un InDesign Server para procesar archivos que se pueden usar en [!DNL Experience Manager] Recursos.

Cuando el proxy es un [!DNL Experience Manager] esto ayuda a reducir la carga en la [!DNL Experience Manager] crear instancias. De forma predeterminada, [!DNL Experience Manager] Assets ejecuta las tareas de procesamiento de recursos en la misma JVM (externalizada mediante proxy) para reducir la carga en la [!DNL Experience Manager] crear instancia.

## Proxy (acceso HTTP) {#proxy-http-access}

Hay un proxy disponible a través del servlet HTTP cuando está configurado para aceptar trabajos de procesamiento en: `/libs/dam/cloud/proxy`. Este servlet crea un trabajo de sling a partir de los parámetros registrados. A continuación, esto se agrega a la cola de trabajos del proxy y se conecta al trabajador del proxy adecuado.

### Operaciones compatibles {#supported-operations}

* `job`

   **Requisitos**: el parámetro `jobevent` debe establecerse como mapa de valores serializado. Se utiliza para crear un `Event` para un procesador de trabajos.

   **Resultado**: Agrega un nuevo trabajo. Si se realiza correctamente, se devuelve un identificador de trabajo único.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Requisitos**: el parámetro `jobid` debe estar configurado.

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

Un trabajador proxy es un procesador responsable de gestionar un trabajo y crear un resultado. Los trabajadores residen en la instancia de proxy y deben implementar [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) para ser reconocido como trabajador proxy.

>[!NOTE]
>
>El trabajador debe implementar [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) para ser reconocido como trabajador proxy.

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

Las configuraciones de trabajo proxy y proxy están disponibles a través de configuraciones de servicios en la nube, a las que se puede acceder desde [!DNL Experience Manager] Recursos **Herramientas** consola o en `/etc/cloudservices/proxy`. Se espera que cada trabajador proxy agregue un nodo en `/etc/cloudservices/proxy` para detalles de configuración específicos del trabajador (por ejemplo, `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Consulte [Configuración del trabajo proxy de Indesign Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) y [Configuración de Cloud Services](../sites-developing/extending-cloud-config.md) para obtener más información.

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

La variable [Trabajador de proxy IDS](indesign.md) es un ejemplo de [!DNL Experience Manager] Trabajador de proxy de recursos que ya se ha proporcionado de forma predeterminada para externalizar el procesamiento de recursos de Indesign.

También puede desarrollar y configurar sus propios [!DNL Experience Manager] Trabajador de proxy de recursos para crear un trabajador especializado para distribuir y externalizar su [!DNL Experience Manager] Tareas de procesamiento de recursos.

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

1. A [Trabajo de Sling](https://sling.apache.org/site/eventing-and-jobs.html) por lo que debe definir un tema de trabajo para su caso de uso.

   Como ejemplo, consulte `IDSJob.IDS_EXTENDSCRIPT_JOB` para el programa de trabajo del proxy IDS.

1. El paso externo se utiliza para almacenar en déclencheur el evento y luego esperar hasta que finalice; esto se hace sondeando en el id. Debe desarrollar su propio paso para implementar la nueva funcionalidad.

   Implemente un `WorkflowExternalProcess`, utilice la API de JobService y el tema de su trabajo para preparar un evento de trabajo y enviarlo al JobService (un servicio de OSGi).

   Como ejemplo, consulte `INDDMediaExtractProcess`.java para el programa de trabajo del proxy IDS.

1. Implemente un controlador de trabajo para su tema. Este controlador requiere desarrollo para que realice su acción específica y se considere la implementación del trabajador.

   Como ejemplo, consulte `IDSJobProcessor.java` para el programa de trabajo del proxy IDS.

1. Utilizar `ProxyUtil.java` en dam-commons. Esto le permite enviar trabajos a los trabajadores usando el proxy de la represa.

>[!NOTE]
>
>Qué es [!DNL Experience Manager] El marco de proxy de recursos no proporciona de serie es el mecanismo de agrupación.
>
>La integración de InDesign permite el acceso a un grupo de servidores de indesign (IDSPool). Este agrupamiento es específico de la integración de Indesign y no forma parte del [!DNL Experience Manager] Marco de proxy de recursos.

>[!NOTE]
>
>Sincronización de resultados:
>
>Con n instancias que utilizan el mismo proxy, el resultado de procesamiento permanece con el proxy. Es el trabajo del cliente ([!DNL Experience Manager] Autor) para solicitar el resultado utilizando el mismo identificador de trabajo único que se dio al cliente en la creación de trabajos. El proxy simplemente realiza el trabajo y mantiene el resultado listo para ser solicitado.
