---
title: Uso de registros
seo-title: Uso de registros
description: Aprenda a solucionar problemas de AEM trabajando con registros.
seo-description: Aprenda a solucionar problemas de AEM trabajando con registros.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 3%

---


# Uso de registros{#working-with-logs}

Esta sección incluye información detallada sobre los registros disponibles para ayudarle a solucionar problemas.

CRX registra registros detallados. Después de desempaquetar y inicio QuickStart, puede encontrar los registros en las siguientes ubicaciones:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Activación del nivel de registro DEBUG {#activating-the-debug-log-level}

El nivel de registro predeterminado es INFO, es decir, los mensajes DEBUG no se registran.

Para activar el nivel de registro DEBUG, utilice el explorador CRX para establecer la variable

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

para depurar. No deje el registro en el nivel de registro DEBUG más tiempo del necesario, ya que genera muchos registros.

Una línea en el archivo de depuración normalmente inicio con DEBUG y, a continuación, proporciona el nivel de registro, la acción del instalador y el mensaje de registro. Por ejemplo:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Los niveles de registro son los siguientes:

| 0 | Error fatal | Error en la acción y el instalador no puede continuar. |
|---|---|---|
| 1 | Error | Error en la acción. La instalación continúa, pero una parte de CRX no se instaló correctamente y no funcionará. |
| 2 | Advertencia | La acción se ha realizado correctamente, pero se han encontrado problemas. CRX puede funcionar correctamente o no. |
| 3 | Información | La acción se ha realizado correctamente. |

## Opción de búsqueda de soluciones utilizada para la resolución de problemas {#verbose-option-used-for-troubleshooting}

Cuando inicio CRX, puede agregar la opción -v (detallado) a la línea de comandos como en: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Utilice la opción &quot;verbose&quot; para solucionar problemas, ya que esta opción muestra algunos de los resultados del registro de inicio rápido en la consola.
