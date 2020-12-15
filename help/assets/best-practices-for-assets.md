---
title: Prácticas recomendadas para administrar recursos mediante AEM
description: Identifique y cumpla las optimizaciones que mejoran la estabilidad del sistema y el rendimiento bajo carga, según la implementación de AEM Assets y las características utilizadas para la ingesta y el procesamiento de recursos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Prácticas recomendadas para AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets es una parte crucial de la entrega de experiencias de marketing digital de alta calidad que contribuyen al logro de los objetivos comerciales mediante el aumento de la velocidad de contenido. Si trabaja con un gran número de recursos dentro de AEM Assets o carga periódica o periódicamente numerosos recursos, incluidos vídeos y medios dinámicos, la optimización de la experiencia de administración de recursos digitales es fundamental para la eficacia del sistema.

En función de cómo haya posicionado AEM Assets para su organización y de las funciones que utilice en la ingestión de recursos, la generación de representaciones y la extracción de metadatos, la identificación y la adhesión a las prácticas recomendadas en diferentes áreas mejora considerablemente la estabilidad del sistema y el rendimiento bajo carga.

Después de revisar las siguientes guías, tendrá los conocimientos y las herramientas para crear y administrar un sistema de administración de activos empresariales que satisfaga sus necesidades.

* [Guía de ](performance-tuning-guidelines.md)
ajuste del rendimiento de los recursosIncluye un conjunto de prácticas recomendadas que se pueden seguir en cualquier momento de la implementación, incluso después de la activación, para garantizar que se saca el máximo partido del sistema.
* [Guía de ](assets-sizing-guide.md)
tamaño de recursosAl elaborar estimaciones para una implementación de Recursos, es importante asegurarse de que hay suficientes recursos disponibles en cuanto a almacenamiento de recursos, CPU, memoria, E/S y rendimiento de red. Cambiar el tamaño de muchos de estos elementos requiere comprender cuántos recursos se cargan en el sistema. Esta guía incluye optimizaciones que ayudan a determinar métricas eficientes para estimar la infraestructura y los recursos necesarios para implementar AEM Assets, así como una herramienta de cambio de tamaño.
* [Guía ](assets-migration-guide.md)
de migración de recursosSi desea migrar recursos de su sistema heredado a AEM Assets, puede seguir varios pasos para racionalizar el proceso de migración. La guía de migración incluye optimizaciones en cuanto a las tareas que realiza para AEM los recursos de forma gradual. Esto incluye aplicar metadatos, generar representaciones y activar los recursos para publicar la implementación.
* [Consideraciones sobre la red de recursosAl administrar AEM implementación, es importante comprender la topología de la red para comprender el rendimiento de la red, identificar puntos de interrupción y describir la experiencia esperada del usuario. ](assets-network-considerations.md)
El documento Consideraciones de la red de recursos analiza las consideraciones de la red al diseñar la implementación de recursos AEM.
* [Guía ](assets-monitoring-best-practices.md)
de supervisión de recursosUna vez implementada la implementación de AEM, debe supervisar determinadas tareas y el sistema en general para garantizar la integridad del sistema y la eficacia de las operaciones. La guía de monitoreo incluye optimizaciones para monitorear diversos aspectos del sistema.
* (Obsoleto) [Guía de descarga de recursos](assets-offloading-best-practices.md)
La administración de archivos de gran tamaño y flujos de trabajo en ejecución en AEM Assets puede consumir una cantidad considerable de recursos de CPU, memoria y E/S. La descarga de estas tareas puede reducir las cargas de CPU, memoria y E/S. La guía de descarga de recursos incluye casos de uso recomendados y prácticas recomendadas para la descarga de recursos.
* [AEM prácticas recomendadas de la aplicación de escritorioLa aplicación de escritorio de AEM vincula la solución de administración de recursos digitales (DAM) con el escritorio para que pueda abrir los archivos disponibles en la interfaz de usuario web AEM directamente en el escritorio. ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
AEM flujo de trabajo fácil de usar de la aplicación de escritorio se activa mediante la tecnología de uso compartido de red que proporcionan los sistemas operativos de escritorio. Esta guía explica las funciones clave y el uso recomendado de AEM aplicación de escritorio.
* [Prácticas recomendadas de integración de AEM y Creative CloudPuede integrar la implementación de AEM con Creative Cloud de varias formas. ](aem-cc-integration-best-practices.md)
El seguir algunas prácticas recomendadas para optimizar los flujos de trabajo de integración y transferencia de recursos le ayuda a lograr la máxima eficacia. Esta guía incluye optimizaciones para la integración de AEM Assets con Adobe Creative Cloud.
* (Obsoleto) [AEM a la carpeta Creative Cloud para compartir prácticas recomendadas](aem-cc-folder-sharing-best-practices.md)
Puede configurar AEM para permitir que los usuarios de DAM compartan carpetas con usuarios de Creative Cloud (CC), de modo que estén disponibles como carpetas compartidas en el servicio Creative Cloud Assets. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de DAM. En esta guía se explican las prácticas recomendadas para aprovechar la función de uso compartido de carpetas de AEM a Creative Cloud.
