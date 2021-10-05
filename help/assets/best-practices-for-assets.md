---
title: Prácticas recomendadas para administrar recursos mediante AEM
description: Identifique y cumpla las prácticas recomendadas que mejoran la estabilidad del sistema y el rendimiento bajo carga, según la implementación de  [!DNL Experience Manager] Assets y las funciones utilizadas para la ingesta y el procesamiento de recursos.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: d750c852b6367d753d18be57c8910bf5671fd5e8
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Prácticas recomendadas para [!DNL Experience Manager] Assets {#best-practices-for-assets}

Adobe Experience Manager Assets es una parte crucial de la oferta de experiencias de marketing digital de alta calidad que contribuyen al logro de los objetivos comerciales mediante el aumento de la velocidad de contenido. Si trabaja con un gran número de recursos dentro de [!DNL Assets] o carga periódica o regularmente varios recursos, incluidos vídeos y medios dinámicos, la optimización de su experiencia de administración de recursos digitales es fundamental para la eficacia del sistema.

Dependiendo de cómo haya posicionado [!DNL Assets] para su organización y de las funciones que utilice en la ingesta de recursos, la generación de variantes de representación y la extracción de metadatos, identificar y cumplir las prácticas recomendadas en diferentes áreas mejora considerablemente la estabilidad del sistema y el rendimiento bajo carga.

Después de revisar las siguientes guías, tendrá los conocimientos y herramientas para crear y administrar un sistema de administración de activos empresariales que satisfaga sus necesidades.

* [Guía de ajuste del rendimiento de los ](performance-tuning-guidelines.md)
recursosIncluye un conjunto de prácticas recomendadas que se pueden seguir en cualquier momento de la implementación, incluso después de la publicación, para garantizar que se saca el máximo partido del sistema.
* [Guía de tamaño de ](assets-sizing-guide.md)
recursosAl elaborar las estimaciones para una implementación de Assets, es importante asegurarse de que haya suficientes recursos disponibles en términos de almacenamiento de recursos, CPU, memoria, E/S y rendimiento de red. Para cambiar el tamaño de muchos de estos elementos es necesario comprender cuántos recursos se están cargando en el sistema. Esta guía incluye prácticas recomendadas que ayudan a determinar métricas eficientes para estimar la infraestructura y los recursos necesarios para implementar [!DNL Experience Manager] Assets, así como una herramienta de tamaño.
* [Guía de migración de ](assets-migration-guide.md)
recursosSi desea migrar recursos del sistema heredado a  [!DNL Experience Manager] Assets, debe considerar la posibilidad de seguir varios pasos para racionalizar el proceso de migración. La guía de migración incluye prácticas recomendadas sobre las tareas que realiza para incorporar los recursos a [!DNL Experience Manager] de forma gradual. Esto incluye aplicar metadatos, generar representaciones y activar los recursos para publicar la implementación.
* [Consideraciones sobre la red de ](assets-network-considerations.md)
recursosAl gestionar la  [!DNL Experience Manager] implementación, es importante comprender la topología de la red para comprender el rendimiento de la red, identificar los puntos de interrupción y describir la experiencia de usuario esperada. El documento Consideraciones de la red de recursos analiza las consideraciones de red al diseñar la implementación de [!DNL Experience Manager] recursos.
* [Guía de monitorización de ](assets-monitoring-best-practices.md)
recursosUna vez implementada la  [!DNL Experience Manager] implementación, debe monitorizar ciertas tareas y el sistema en general para garantizar la integridad del sistema y la eficacia de las operaciones. La guía de monitorización incluye prácticas recomendadas para monitorizar varios aspectos de su sistema.
* (Obsoleto) [Guía de descarga de recursos](assets-offloading-best-practices.md)
La administración de archivos grandes y flujos de trabajo en ejecución en [!DNL Experience Manager] Assets pueden consumir considerables recursos de CPU, memoria y E/S. La descarga de estas tareas puede reducir las sobrecargas de CPU, memoria y E/S. La guía de descarga de recursos incluye casos de uso recomendados y prácticas recomendadas para la descarga de recursos.
* [[!DNL Experience Manager] prácticas recomendadas para las aplicaciones de escritorio](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] la aplicación de escritorio vincula la solución de administración de recursos digitales (DAM) con el escritorio para que pueda abrir los archivos disponibles en la interfaz de usuario  [!DNL Experience Manager] web directamente en el escritorio. [!DNL Experience Manager] el flujo de trabajo fácil de usar de la aplicación de escritorio está habilitado mediante la tecnología de uso compartido de red que ofrecen los sistemas operativos de escritorio. Esta guía explica las funcionalidades clave y el uso recomendado de la aplicación de escritorio [!DNL Experience Manager].
* [[!DNL Experience Manager] y ](aem-cc-integration-best-practices.md)
prácticas recomendadas para la integración de Creative CloudPuede integrar la  [!DNL Experience Manager] implementación con Creative Cloud de varias formas. Seguir algunas prácticas recomendadas para racionalizar los flujos de trabajo de integración y transferencia de recursos ayuda a lograr la máxima eficacia. Esta guía incluye prácticas recomendadas sobre la integración de [!DNL Experience Manager] Assets con Adobe Creative Cloud.
* (Obsoleto) [[!DNL Experience Manager] a la carpeta de Creative Cloud para compartir prácticas recomendadas](aem-cc-folder-sharing-best-practices.md)
Puede configurar [!DNL Experience Manager] para permitir que los usuarios de DAM compartan carpetas con usuarios de Creative Cloud, de modo que estén disponibles como carpetas compartidas en el servicio Recursos de Creative Cloud. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de DAM. En esta guía se explican las prácticas recomendadas para aprovechar la función de uso compartido de [!DNL Experience Manager] en carpetas del Creative Cloud.
