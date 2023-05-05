---
title: Uso de registros
seo-title: Working with Logs
description: Obtenga información sobre cómo solucionar problemas de AEM trabajando con registros.
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 6%

---

# Uso de registros{#working-with-logs}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta sección incluye información detallada sobre los registros disponibles para ayudarle a solucionar el problema.

CRX registra registros detallados. Después de desempaquetar e iniciar QuickStart, puede encontrar los registros en las siguientes ubicaciones:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Activación del nivel de registro de depuración {#activating-the-debug-log-level}

El nivel de registro predeterminado es INFO, es decir, los mensajes DEBUG no se registran.

Para activar el nivel de registro de depuración, utilice el explorador CRX para establecer la variable

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

para depurar. No deje el registro en el nivel de registro DEBUG más tiempo del necesario, ya que genera muchos registros.

Una línea en el archivo de depuración normalmente comienza con DEBUG y, a continuación, proporciona el nivel de registro, la acción del instalador y el mensaje de registro. Por ejemplo:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Los niveles de registro son los siguientes:

| 0 | Error grave | La acción ha fallado y el instalador no puede continuar. |
|---|---|---|
| 1 | Error | La acción ha fallado. La instalación continúa, pero una parte de CRX no se instaló correctamente y no funcionará. |
| 2 | Advertencia | La acción se ha realizado correctamente, pero se han encontrado problemas. CRX puede o no funcionar correctamente. |
| 3 | Información | La acción se ha realizado correctamente. |

## Opción versbose utilizada para la resolución de problemas {#verbose-option-used-for-troubleshooting}

Cuando inicie CRX, puede agregar la opción -v (verbose) a la línea de comandos como en: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Utilice la opción detallada para la resolución de problemas, ya que esta opción muestra algunos de los resultados del registro de inicio rápido en la consola.
