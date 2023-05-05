---
title: Depuración de versiones
seo-title: Version Purging
description: Este artículo describe las opciones disponibles para la depuración de versiones.
seo-description: This article describes the available options for version purging.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: Configuring
exl-id: 357d5f23-3e75-44e3-905f-4efe960858bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 2%

---

# Depuración de versiones{#version-purging}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En una instalación estándar, AEM crea una nueva versión de una página o nodo cuando activa una página después de actualizar el contenido.

>[!NOTE]
>
>Si no se realizan cambios en el contenido, verá el mensaje que indica que la página se ha activado, pero no se creará ninguna versión nueva

Puede crear versiones adicionales si lo solicita utilizando la variable **Versiones** de la barra de tareas. Estas versiones se almacenan en el repositorio y se pueden restaurar si es necesario.

Estas versiones nunca se depuran, por lo que el tamaño del repositorio crecerá con el tiempo y, por lo tanto, debe administrarse.

AEM incluye varios mecanismos para ayudarle a administrar su repositorio:

* el [Administrador de versiones](#version-manager)

   Esto se puede configurar para depurar versiones antiguas cuando se crean versiones nuevas.

* el [Purgar versiones](/help/sites-deploying/monitoring-and-maintaining.md#version-purging) herramienta

   Se utiliza como parte de la supervisión y el mantenimiento del repositorio.

   Le permite intervenir para eliminar versiones antiguas de un nodo o una jerarquía de nodos, según estos parámetros:

   * Número máximo de versiones que se guardarán en el repositorio.

      Cuando se supera este número, se elimina la versión más antigua.

   * La edad máxima de cualquier versión guardada en el repositorio.

      Cuando la antigüedad de una versión supera este valor, se depura del repositorio.

* el [Tarea de mantenimiento de purga de versión](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Puede programar la tarea de mantenimiento Purga de versión para eliminar automáticamente las versiones antiguas. Como resultado, esto minimiza la necesidad de utilizar manualmente las herramientas de purga de versión.

>[!CAUTION]
>
>Para optimizar el tamaño del repositorio, debe ejecutar la tarea de depuración de versiones con frecuencia. La tarea debe programarse fuera del horario laboral cuando haya una cantidad limitada de tráfico.

## Administrador de versiones {#version-manager}

Además de la depuración explícita mediante la herramienta de depuración, el Administrador de versiones se puede configurar para depurar versiones antiguas cuando se crean versiones nuevas.

Para configurar el Administrador de versiones, cree una configuración para:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Las opciones disponibles son las siguientes:

* `versionmanager.createVersionOnActivation` (Booleano, predeterminado: true)

   si se crea una versión cuando se activan las páginas.

   Se crea una versión a menos que el agente de replicación esté configurado para suprimir la creación de versiones, que es respetado por el Administrador de versiones

   Una versión solo se crea si la activación se produce en una ruta contenida en versionmanager.ivPaths (ver abajo).

* `versionmanager.ivPaths` (Cadena[], predeterminado: {&quot;/&quot;})

   rutas en las que las versiones se crean implícitamente en la activación si versionmanager.createVersionOnActivation es true.

* `versionmanager.purgingEnabled` (Booleano, predeterminado: false)

   si se habilita la depuración al crear nuevas versiones

* `versionmanager.purgePaths` (Cadena[], predeterminado: {&quot;/content&quot;})

   en qué rutas se purgan las versiones cuando se crean nuevas versiones.

* `versionmanager.maxAgeDays` (int, predeterminado: 30)

   en la depuración, se eliminará cualquier versión anterior a este valor. Si este valor es menor que 1, la depuración no se realiza en función de la edad de la versión

* `versionmanager.maxNumberVersions` (int, predeterminado 5)

   en la depuración, se eliminará cualquier versión anterior a la n-ª versión más reciente. Si este valor es menor que 1, la depuración no se realiza en función del número de versiones

* `versionmanager.minNumberVersions` (int, 0 predeterminado)

   El número mínimo de versiones que se deben mantener independientemente de la edad. Si este valor se establece en un valor menor que 1, no se retiene ningún número mínimo de versiones.

>[!NOTE]
>
>No se recomienda mantener un gran número de versiones en el repositorio. Por lo tanto, al configurar la operación de depuración de versiones tenga en cuenta que no excluya demasiadas versiones de la depuración de otra manera, el tamaño del repositorio no se optimizará correctamente. Si mantiene un gran número de versiones debido a un requerimiento comercial, póngase en contacto con el servicio de soporte técnico de Adobe para encontrar formas alternativas de optimizar el tamaño del repositorio.

### Combinar opciones de retención {#combining-retention-options}

Las opciones que definen cómo se deben conservar las versiones ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), se puede combinar según sus necesidades.

Por ejemplo, al definir el número máximo de versiones que desea conservar Y la versión más antigua que desea conservar:

* Configuración:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Con:

   * 10 versiones realizadas en los últimos 60 días
   * 3 de esas versiones creadas en los últimos 30 días

* Significará que:

   * Se mantendrán las últimas 3 versiones

Por ejemplo, al definir el número máximo Y mínimo de versiones que se deben conservar Y la versión más antigua que se deben conservar:

* Configuración:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Con:

   * 5 versiones realizadas hace 60 días

* Significará que:

   * Se conservarán 3 versiones

## Herramienta Purgar versiones {#purge-versions-tool}

La variable [Purgar versiones](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) está diseñada para depurar las versiones de un nodo o una jerarquía de nodos en el repositorio. Su principal propósito es ayudarle a reducir el tamaño de su repositorio eliminando versiones antiguas de sus nodos.
