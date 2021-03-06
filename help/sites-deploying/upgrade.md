---
title: Actualización a AEM 6.4
seo-title: Actualización a AEM 6.4
description: Obtenga información sobre los conceptos básicos para actualizar una instalación de AEM anterior a AEM 6.4.
seo-description: Obtenga información sobre los conceptos básicos para actualizar una instalación de AEM anterior a AEM 6.4.
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: Actualización
exl-id: 791da16c-bf2c-47a9-86a4-0a601a1b017e
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---

# Actualización a AEM 6.4{#upgrading-to-aem}

En esta sección, tratamos la actualización de una instalación AEM a la AEM 6.4:

* [Planificación de la actualización](/help/sites-deploying/upgrade-planning.md)
* [Evaluación de la complejidad de la actualización con Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Compatibilidad con versiones anteriores en AEM 6.4](/help/sites-deploying/backward-compatibility.md)
* [Procedimiento de actualización](/help/sites-deploying/upgrade-procedure.md)
* [Actualización de código y personalizaciones](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Tareas de mantenimiento previas a la actualización](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Realización de una actualización in situ](/help/sites-deploying/in-place-upgrade.md)
* [Comprobación y solución de problemas posteriores a la actualización](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Actualizaciones sostenibles](/help/sites-deploying/sustainable-upgrades.md)
* [Migración de contenido diferido](/help/sites-deploying/lazy-content-migration.md)
* [Reestructuración de repositorios en AEM 6.4](/help/sites-deploying/repository-restructuring.md)

Para facilitar la referencia a los AEM casos involucrados en estos procedimientos, se utilizan los siguientes términos en estos artículos:

* La instancia *source* es la instancia de AEM desde la que está actualizando.
* La instancia *target* es a la que está actualizando.

>[!NOTE]
>
>Como parte de los esfuerzos por mejorar la fiabilidad de las actualizaciones, AEM 6.4 ha pasado por una reestructuración completa de los repositorios. Para obtener más información sobre cómo alinearse con la nueva estructura, consulte [Reestructuración del repositorio en AEM 6.4](/help/sites-deploying/repository-restructuring.md)

## ¿Qué ha cambiado? {#what-has-changed}

A continuación se indican los cambios más importantes que se han producido en las últimas versiones de AEM:

AEM 6.0 introdujo el nuevo repositorio de Jackrabbit Oak. Los administradores de persistencia se reemplazaron por [Micro Kernels](/help/sites-deploying/recommended-deploys.md). A partir de la versión 6.1, CRX2 ya no es compatible. Se debe ejecutar una herramienta de migración llamada crx2oak para migrar repositorios CRX2 de instancias 5.6.1. Para obtener más información, consulte [Uso de la herramienta de migración CRX2OAK](/help/sites-deploying/using-crx2oak.md).

Si se va a utilizar Assets Insights y se está actualizando desde una versión anterior a AEM 6.2, los recursos deben migrarse y deben generarse ID a través de un bean JMX. En nuestras pruebas internas, se migraron 125.000 activos en un entorno TarMK en una hora, pero los resultados pueden variar.

AEM 6.3 introdujo un nuevo formato para el `SegmentNodeStore`, que es la base de la implementación de TarMK. Si está actualizando desde una versión anterior a AEM 6.3, esto requerirá una migración del repositorio como parte de la actualización, lo que implica downtime del sistema.

Adobe Engineering estima que esto será de unos 20 minutos. Tenga en cuenta que la reindexación no será necesaria. Además, se ha lanzado una nueva versión de la herramienta crx2oak para trabajar con el nuevo formato de repositorio.

**Esta migración no es necesaria si se actualiza de AEM 6.3 a AEM 6.4.**

Las tareas de mantenimiento previas a la actualización se han optimizado para admitir la automatización.

Las opciones de uso de la línea de comandos de la herramienta crx2oak se han cambiado para que sean fáciles de usar y admitan más rutas de actualización.

Las comprobaciones posteriores a la actualización también han permitido facilitar la automatización.

La recolección periódica de basura de revisiones y la recolección de basura en el almacén de datos son ahora tareas de mantenimiento rutinarias que deben realizarse periódicamente. Con la introducción de AEM 6.3, Adobe apoya y recomienda la limpieza de revisión en línea. Consulte [Limpieza de revisión](/help/sites-deploying/revision-cleanup.md) para obtener información sobre cómo configurar estas tareas.

**AEM 6.4** presenta el  [detector de ](/help/sites-deploying/pattern-detector.md) patrones para evaluar la complejidad de la actualización a medida que comienza a planificar la actualización. 6.4 también se centra especialmente en la [compatibilidad con versiones anteriores](/help/sites-deploying/backward-compatibility.md) de las funciones. Por último, también se añaden las prácticas recomendadas para [upgrades sostenibles](/help/sites-deploying/sustainable-upgrades.md).

Para obtener más información sobre los cambios que se han producido en las versiones AEM recientes, consulte las notas de la versión completas:

* [https://helpx.adobe.com/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/es/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/experience-manager/6-4/release-notes.html)

## Información general sobre la actualización {#upgrade-overview}

La actualización de AEM es un proceso de varios pasos, a veces de varios meses. La siguiente descripción se ha proporcionado como una descripción general de lo que se incluye en un proyecto de actualización y el contenido que se ha incluido en esta documentación:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Flujo de actualización con mejoras de actualización de la versión 6.4 {#upgrade-overview-1}

El diagrama siguiente captura el flujo recomendado general para resaltar el enfoque de actualización. Tenga en cuenta la referencia a las nuevas funciones que hemos introducido. La actualización debe comenzar con Pattern Detector (consulte [Evaluación de la complejidad de la actualización con Pattern Detector](/help/sites-deploying/pattern-detector.md)), que debería permitirle decidir la ruta que desea seguir para la compatibilidad con AEM 6.4 en función de los patrones del informe generado.

En la versión 6.4 se prestó gran atención a mantener todas las nuevas funciones compatibles con versiones anteriores, pero en los casos en que siga habiendo algunos problemas de compatibilidad con versiones anteriores, el modo de compatibilidad le permite aplazar temporalmente el desarrollo para mantener el código personalizado compatible con la versión 6.4. Este método le ayuda a evitar el esfuerzo de desarrollo inmediatamente después de la actualización (consulte [Compatibilidad con versiones anteriores en la AEM 6.4](/help/sites-deploying/backward-compatibility.md)).

Por último, en su ciclo de desarrollo 6.4, las funciones introducidas en Actualizaciones sostenibles (consulte [Actualizaciones sostenibles](/help/sites-deploying/sustainable-upgrades.md)) le ayudan a seguir las prácticas recomendadas para hacer que las futuras actualizaciones sean aún más eficientes y fluidas.

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
