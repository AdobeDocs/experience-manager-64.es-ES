---
title: Creación y consumo de trabajos para descarga
seo-title: Creating and Consuming Jobs for Offloading
description: La función Apache Sling Discovery proporciona una API de Java que le permite crear trabajos de JobManager y servicios de JobConsumer que los consumen
seo-description: The Apache Sling Discovery feature provides a Java API that enables you to create JobManager jobs and JobConsumer services that consume them
uuid: d6a5beb0-0618-4b61-9b52-570862eac920
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: e7b6b9ee-d807-4eb0-8e96-75ca1e66a4e4
exl-id: ec5253cd-7f1e-4408-9765-8aaa9a81095c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 1%

---

# Creación y consumo de trabajos para descarga{#creating-and-consuming-jobs-for-offloading}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La función Apache Sling Discovery proporciona una API de Java que le permite crear trabajos de JobManager y servicios de JobConsumer que los consumen.

Para obtener información sobre la creación de topologías de descarga y la configuración del consumo de temas, consulte [Descarga de trabajos](/help/sites-deploying/offloading.md).

## Gestión de cargas de trabajo {#handling-job-payloads}

El marco de descarga define dos propiedades de trabajo que se utilizan para identificar la carga útil de trabajo. Los agentes de replicación de descarga utilizan estas propiedades para identificar los recursos que se replicarán en las instancias de la topología:

* `offloading.job.input.payload`: Lista de rutas de contenido separadas por coma. El contenido se duplica en la instancia que ejecuta el trabajo.
* `offloading.job.output.payload`: Lista de rutas de contenido separadas por coma. Cuando finaliza la ejecución del trabajo, la carga útil del trabajo se duplica en estas rutas en la instancia que creó el trabajo.

Utilice la variable `OffloadingJobProperties` enum para hacer referencia a los nombres de propiedad:

* `OffloadingJobProperties.INPUT_PAYLOAD.propertyName()`
* `OffloadingJobProperties.OUTPUT_PAYLOAD.propetyName()`

Los trabajos no requieren cargas útiles. Sin embargo, la carga útil es necesaria si el trabajo requiere la manipulación de un recurso y el trabajo se descarga a un equipo que no creó el trabajo.

## Creación de trabajos para descarga {#creating-jobs-for-offloading}

Cree un cliente que llame al método JobManager.addJob para crear un trabajo que ejecute JobConsumer seleccionado automáticamente. Proporcione la siguiente información para crear el trabajo:

* Tema: El tema del trabajo.
* Nombre: (Opcional)
* Mapa de propiedades: A `Map<String, Object>` objeto que contiene cualquier cantidad de propiedades, como las rutas de carga útil de entrada y las rutas de carga útil de salida. Este objeto Map está disponible para el objeto JobConsumer que ejecuta el trabajo.

El siguiente servicio de ejemplo crea un trabajo para un tema determinado y una ruta de carga útil de entrada.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import java.util.HashMap;

import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;

import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.ResourceResolver;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class JobGeneratorImpl implements JobGenerator  {

 @Reference
 private JobManager jobManager;
 @Reference ResourceResolverFactory resolverFactory;

 public String createJob(String topic, String payload) throws Exception {
  Job offloadingJob;

  ResourceResolver resolver = resolverFactory.getResourceResolver(null);
  if(resolver.getResource(payload)!=null){

   HashMap<String, Object> jobprops = new HashMap<String, Object>();
   jobprops.put(OffloadingJobProperties.INPUT_PAYLOAD.propertyName(), payload);

   offloadingJob = jobManager.addJob(topic, null, jobprops);
  } else {
   throw new Exception("Payload for job cannot be found");
  }
  if (offloadingJob == null){
   throw new Exception ("Offloading job could not be created");
  }
  return offloadingJob.getId();
 }
}
```

El registro contiene el siguiente mensaje cuando se llama a JobGeneratorImpl.createJob para la variable `com/adobe/example/offloading` y `/content/geometrixx/de/services` carga útil:

```shell
10.06.2013 15:43:33.868 *INFO* [JobHandler: /etc/workflow/instances/2013-06-10/model_1554418768647484:/content/geometrixx/en/company] com.adobe.example.offloading.JobGeneratorImpl Received request to make job for topic com/adobe/example/offloading and payload /content/geometrixx/de/services
```

## Desarrollo de un consumidor de trabajo {#developing-a-job-consumer}

Para consumir trabajos, desarrolle un servicio OSGi que implemente la variable `org.apache.sling.event.jobs.consumer.JobConsumer` interfaz. Identifique con el tema que desea consumir con el `JobConsumer.PROPERTY_TOPICS` propiedad.

El siguiente ejemplo de implementación de JobConsumer se registra con la variable `com/adobe/example/offloading` tema. El consumidor simplemente establece la propiedad Consumed del nodo de contenido de carga útil en true.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;
import org.apache.sling.event.jobs.consumer.JobConsumer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Session;
import javax.jcr.Node;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class MyJobConsumer implements JobConsumer {

 public static final String TOPIC = "com/adobe/example/offloading";

 @Property(value = TOPIC)
 static final String myTopic = JobConsumer.PROPERTY_TOPICS; 

 @Reference
 private ResourceResolverFactory resolverFactory;

 @Reference
 private JobManager jobManager;

 private final Logger log = LoggerFactory.getLogger(getClass());

 public JobResult process(Job job) {
  JobResult result = JobResult.FAILED;
  String topic = job.getTopic();
  log.info("Consuming job of topic: {}", topic);
  String payloadIn =  (String) job.getProperty(OffloadingJobProperties.INPUT_PAYLOAD.propertyName());
  String payloadOut =  (String) job.getProperty(OffloadingJobProperties.OUTPUT_PAYLOAD.propertyName());

  log.info("Job has Input Payload {} and Output Payload {}",payloadIn, payloadOut);

  ResourceResolver resolver = null;
  try {
   resolver = resolverFactory.getAdministrativeResourceResolver(null);
   Session session = resolver.adaptTo(Session.class);
   Node inNode = session.getNode(payloadIn);
   inNode.getNode(Node.JCR_CONTENT).setProperty("consumed",true);
   result = JobResult.OK;
  }catch (Exception e){
   log.info("ERROR -- JOB RESULT IS FAILURE " + e.getMessage());
   result = JobResult.FAILED;
  }
  log.info("Job OK for payload {}",payloadIn);
  return result;
 }
}
```

La clase MyJobConsumer genera los siguientes mensajes de registro para una carga útil de entrada de /content/geometrixx/de/services:

```shell
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Consuming job of topic: com/adobe/example/offloading
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job has Input Payload /content/geometrixx/de/services and Output Payload /content/geometrixx/de/services
10.06.2013 16:02:40.884 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job OK for payload /content/geometrixx/de/services
```

La propiedad Consumed se puede observar usando el CRXDE Lite :

![chlimage_1-25](assets/chlimage_1-25.png)

## Maven Dependencias {#maven-dependencies}

Agregue las siguientes definiciones de dependencia al archivo pom.xml para que Maven pueda resolver las clases relacionadas con la descarga.

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.event</artifactId>
   <version>3.1.5-R1485539</version>
   <scope>provided</scope> 
</dependency>
<dependency>
   <groupId>com.adobe.granite</groupId>
   <artifactId>com.adobe.granite.offloading.core</artifactId>
   <version>1.0.4</version>
   <scope>provided</scope>
</dependency>
```

Los ejemplos anteriores también requerían las siguientes definiciones de dependencias:

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.api</artifactId>
   <version>2.4.3-R1488084</version>
   <scope>provided</scope>
</dependency>

<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
   <version>2.0.0</version>
   <scope>provided</scope>
</dependency>
```
