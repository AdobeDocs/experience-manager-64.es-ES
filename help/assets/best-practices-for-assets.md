---
title: Prácticas recomendadas para administrar recursos mediante AEM
description: Identifique y cumpla las prácticas recomendadas que mejoran la estabilidad del sistema y el rendimiento bajo carga, según la implementación de AEM Assets y las funciones utilizadas para la ingesta y el procesamiento de recursos.
contentOwner: AG
feature: Administración de activos
role: Arquitecto,Administrador
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Prácticas recomendadas para AEM Assets {#best-practices-for-assets}

Recursos Adobe Experience Manager (AEM) es una parte crucial para ofrecer experiencias de marketing digital de alta calidad que contribuyan al logro de los objetivos comerciales mediante el aumento de la velocidad de contenido. Si trabaja con un gran número de recursos dentro de AEM Assets o carga periódica o periódicamente numerosos recursos, incluidos vídeos y medios dinámicos, la optimización de su experiencia de administración de recursos digitales es fundamental para la eficacia del sistema.

En función de cómo haya posicionado AEM Assets para su organización y de las funciones que utilice en la ingesta de recursos, la generación de variantes de representación y la extracción de metadatos, la identificación y la observancia de las prácticas recomendadas en diferentes áreas mejora en gran medida la estabilidad y el rendimiento del sistema que se encuentra bajo carga.

Después de revisar las siguientes guías, tendrá los conocimientos y herramientas para crear y administrar un sistema de administración de activos empresariales que satisfaga sus necesidades.

* [Guía de ajuste del rendimiento de los ](performance-tuning-guidelines.md)
recursosIncluye un conjunto de prácticas recomendadas que se pueden seguir en cualquier momento de la implementación, incluso después de la publicación, para garantizar que se saca el máximo partido del sistema.
* [Guía de tamaño de ](assets-sizing-guide.md)
recursosAl elaborar las estimaciones para una implementación de Assets, es importante asegurarse de que haya suficientes recursos disponibles en términos de almacenamiento de recursos, CPU, memoria, E/S y rendimiento de red. Para cambiar el tamaño de muchos de estos elementos es necesario comprender cuántos recursos se están cargando en el sistema. Esta guía incluye prácticas recomendadas que ayudan a determinar métricas eficientes para estimar la infraestructura y los recursos necesarios para implementar AEM Assets, así como una herramienta de tamaño.
* [Guía de migración de ](assets-migration-guide.md)
recursosSi desea migrar recursos de su sistema heredado a AEM Assets, debe seguir varios pasos para racionalizar el proceso de migración. La guía de migración incluye prácticas recomendadas sobre las tareas que realiza para AEM los recursos en una forma gradual. Esto incluye aplicar metadatos, generar representaciones y activar los recursos para publicar la implementación.
* [Consideraciones sobre la red de recursosAl gestionar AEM implementación, es importante comprender la topología de la red para comprender el rendimiento de la red, identificar puntos de interrupción y describir la experiencia de usuario esperada. ](assets-network-considerations.md)
El documento Consideraciones de la red de recursos analiza las consideraciones de red al diseñar la implementación de AEM Asset.
* [Guía de monitorización de ](assets-monitoring-best-practices.md)
recursosUna vez implementada la implementación de AEM, debe monitorizar ciertas tareas y el sistema en general para garantizar la integridad del sistema y la eficacia de las operaciones. La guía de monitorización incluye prácticas recomendadas para monitorizar varios aspectos de su sistema.
* (Obsoleto) [Guía de descarga de recursos](assets-offloading-best-practices.md)
La gestión de archivos grandes y flujos de trabajo en ejecución en AEM Assets pueden consumir considerables recursos de CPU, memoria y E/S. La descarga de estas tareas puede reducir las sobrecargas de CPU, memoria y E/S. La guía de descarga de recursos incluye casos de uso recomendados y prácticas recomendadas para la descarga de recursos.
* [AEM prácticas recomendadas de la aplicación de escritorioLa aplicación de escritorio de AEM vincula su solución de administración de recursos digitales (DAM) con su escritorio para que pueda abrir los archivos disponibles en la interfaz de usuario web de AEM directamente en el escritorio. ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
AEM flujo de trabajo fácil de usar de la aplicación de escritorio está habilitado mediante la tecnología de uso compartido de red que ofrecen los sistemas operativos de escritorio. En esta guía se explican las funcionalidades clave y el uso recomendado de AEM aplicación de escritorio.
* [AEM y ](aem-cc-integration-best-practices.md)
prácticas recomendadas para la integración de Creative CloudPuede integrar la implementación de AEM con Creative Cloud de varias formas. Seguir algunas prácticas recomendadas para racionalizar los flujos de trabajo de integración y transferencia de recursos ayuda a lograr la máxima eficacia. Esta guía incluye prácticas recomendadas sobre la integración de AEM Assets con Adobe Creative Cloud.
* (Obsoleto) [AEM a la carpeta de Creative Cloud para compartir prácticas recomendadas](aem-cc-folder-sharing-best-practices.md)
Puede configurar AEM para permitir que los usuarios de DAM compartan carpetas con usuarios de Creative Cloud (CC), de modo que estén disponibles como carpetas compartidas en el servicio Creative Cloud Assets. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de DAM. En esta guía se explican las prácticas recomendadas para aprovechar la AEM a la función de uso compartido de carpetas del Creative Cloud.
