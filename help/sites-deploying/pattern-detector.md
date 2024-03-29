---
title: Evaluación de la complejidad de la actualización con Pattern Detector
seo-title: Assessing the Upgrade Complexity with the Pattern Detector
description: Aprenda a utilizar Pattern Detector para evaluar la complejidad de la actualización.
seo-description: Learn how to use the Pattern Detector to assess the complexity of your upgrade.
uuid: 4fcfdb16-3183-442a-aa5b-5f9c4fb7e091
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 8cdcfd3a-7003-4cce-97f4-da7a1a887d1b
feature: Upgrading
exl-id: 375e202c-21d4-41f1-a2d5-592ac95c8f25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 4%

---

# Evaluación de la complejidad de la actualización con Pattern Detector{#assessing-the-upgrade-complexity-with-the-pattern-detector}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Esta función le permite comprobar si las instancias de AEM existentes son actualizables detectando patrones en uso que:

1. Infringir ciertas reglas y se realizan en áreas que se verán afectadas o sobrescritas por la actualización
1. Utilice una función AEM 6.x o una API que no sea compatible con versiones anteriores de la AEM 6.4 y que pueda romperse después de la actualización.

Esto podría servir como una evaluación de las actividades de desarrollo que se realizan para actualizar a la AEM 6.4.

## Configuración {#how-to-set-up}

El detector de patrones se libera por separado como un [un paquete](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/pd-all-aem65)  trabajar en cualquier versión de AEM de origen de 6.1 a 6.5, segmentando AEM actualización a 6.5. Se puede instalar utilizando la variable [Administrador de paquetes](https://helpx.adobe.com/es/experience-manager/6-5/sites/administering/using/package-manager.html).

## Usos {#how-to-use}

>[!NOTE]
>
>Pattern Detector puede ejecutarse en cualquier entorno, incluidas las instancias de desarrollo local. Sin embargo, para:
>
>* aumentar la tasa de detección
>* evite cualquier ralentización en instancias críticas para el negocio\
   >al mismo tiempo, se recomienda ejecutarlo **en entornos de ensayo** que estén lo más cerca posible de las de producción en las áreas de aplicaciones de usuario, contenido y configuraciones.


Puede utilizar varios métodos para comprobar la salida del detector de patrones:

* **A través de la consola Felix Inventory:**

1. Vaya a la consola web de AEM navegando hasta: https://<i></i>serveraddress:serverport/system/console/configMgr
1. Select **Estado: detector de patrones** como se muestra en la siguiente imagen:

   ![captura de pantalla-2018-2-5pattern-detector](assets/screenshot-2018-2-5pattern-detector.png)

* **A través de una interfaz JSON normal o basada en texto reactivo**

* **A través de una interfaz de líneas JSON reactiva**, que genera un documento JSON independiente en cada línea.

Estos dos métodos se detallan a continuación:

## Interfaz reactiva {#reactive-interface}

La interfaz reactiva permite el procesamiento del informe de infracción en cuanto se detecta una sospecha.

El resultado está disponible actualmente en 2 direcciones URL:

1. Interfaz de texto sin formato
1. Interfaz JSON

## Gestión de la interfaz de texto sin formato {#handling-the-plain-text-interface}

La información de la salida tiene el formato de una serie de entradas de eventos. Hay dos canales: uno para publicar infracciones y otro para publicar el progreso actual.

Se pueden obtener utilizando los siguientes comandos:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep SUSPICION
```

El resultado tendrá este aspecto:

```
2018-02-13T14:18:32.071+01:00 [SUSPICION] The pattern=ECU/extraneous.content.usage was found by detector=ContentAccessDetector with id=a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f message="Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid". More info at=https://www.adobe.com/go/aem6_EC
```

El progreso se puede filtrar usando la variable `grep` comando:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep PROGRESS
```

Lo que resulta en la siguiente salida:

```
2018-02-13T14:19:26.909+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=45780/16 MB items, found=0 suspicions so far in period=PT5.005S (throughput=34667 items/sec)
2018-02-13T14:19:31.904+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=106050/39 MB items, found=0 suspicions so far in period=PT10S (throughput=23378 items/sec)
2018-02-13T14:19:35.685+01:00 [PROGRESS] Finished in period=PT13.782
```

## Gestión de la interfaz JSON {#handling-the-json-interface}

Del mismo modo, JSON se puede procesar mediante el [herramienta jq](https://stedolan.github.io/jq/) tan pronto como se publique.

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == true)'
```

Con la salida:

```
{
  "timestamp": "2018-02-13T14:20:18.894+01:00",
  "suspicion": true,
  "pattern": {
    "code": "ECU",
    "type": "extraneous.content.usage",
    "detective": "ContentAccessDetector",
    "moreInfo": "https://www.adobe.com/go/aem6_ECU"
  },
  "item": {
    "id": "a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f",
    "message": "Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid"
  }
}
```

El progreso se registra cada 5 segundos y se puede recuperar excluyendo otros mensajes que no sean los marcados como sospechas:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == false)'
```

Con la salida:

```
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:17.279+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 57209,
    "itemsAnalysedSize": "26 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT5.003S",
    "elapsedTimeMilliseconds": 5003,
    "itemsPerSecond": 36965
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:22.276+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 113194,
    "itemsAnalysedSize": "46 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT10S",
    "elapsedTimeMilliseconds": 10000,
    "itemsPerSecond": 24092
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:25.762+01:00",
  "type": "FINISHED",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 140744,
    "itemsAnalysedSize": "63 MB",
    "suspicionsFound": 1
  },
  "progress": {
    "elapsedTime": "PT13.486S",
    "elapsedTimeMilliseconds": 13486,
    "itemsPerSecond": 19907
  }
}
{
  "suspicion": false,
  "type": "SUMMARY",
  "suspicionsFound": 1,
  "totalTime": "PT13.487S"
}
```

>[!NOTE]
>
>El método recomendado es guardar toda la salida de curl en el archivo y luego procesarla mediante `jq` o `grep` para filtrar el tipo de información.

## Ámbito de detección {#scope}

El detector de patrones actual permite comprobar:

* Las exportaciones e importaciones de paquetes OSGi no coinciden
* Superusos de tipos de recursos de Sling y supertipos (con superposiciones de contenido de ruta de búsqueda)
* definiciones de índices Oak (compatibilidad)
* Paquetes VLT (sobreutilización)
* rep:Compatibilidad de nodos de usuario (en el contexto de la configuración de OAuth)
