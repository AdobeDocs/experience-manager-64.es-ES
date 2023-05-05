---
title: Prácticas recomendadas para administrar recursos mediante AEM
description: Identifique y cumpla las prácticas recomendadas que mejoran la estabilidad del sistema y el rendimiento bajo carga, según [!DNL Experience Manager] Implementación de recursos y funciones que se utilizan para la ingesta y el procesamiento de recursos.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Prácticas recomendadas para [!DNL Experience Manager] Recursos {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets es una parte crucial de la oferta de experiencias de marketing digital de alta calidad que contribuyen al logro de los objetivos comerciales mediante el aumento de la velocidad de contenido. Si trabaja con un gran número de recursos dentro de [!DNL Assets] o cargar de forma regular/periódica numerosos recursos, incluidos vídeos y medios dinámicos, la optimización de la experiencia de administración de recursos digitales es fundamental para la eficacia del sistema.

Según la posición [!DNL Assets] para su organización y las funciones que utiliza en la ingesta de recursos, la generación de representaciones y la extracción de metadatos, identificar y cumplir las prácticas recomendadas en diferentes áreas mejora en gran medida la estabilidad del sistema y el rendimiento bajo carga.

Después de revisar las siguientes guías, tendrá los conocimientos y herramientas para crear y administrar un sistema de administración de activos empresariales que satisfaga sus necesidades.

* [Guía de ajuste del rendimiento de los activos](performance-tuning-guidelines.md)
Incluye un conjunto de prácticas recomendadas que se pueden seguir en cualquier momento de la implementación, incluso después de su lanzamiento, para asegurarse de sacar el máximo partido de su sistema.
* [Guía de tamaño de recursos](assets-sizing-guide.md)
Al elaborar las estimaciones para una implementación de Assets, es importante asegurarse de que haya suficientes recursos disponibles en términos de almacenamiento de recursos, CPU, memoria, E/S y rendimiento de red. Para cambiar el tamaño de muchos de estos elementos es necesario comprender cuántos recursos se están cargando en el sistema. Esta guía incluye prácticas recomendadas que ayudan a determinar métricas eficientes para estimar la infraestructura y los recursos necesarios para la implementación [!DNL Experience Manager] Recursos, así como una herramienta de ajuste de tamaño.
* [Guía de migración de recursos](assets-migration-guide.md)
Si desea migrar recursos de su sistema heredado a [!DNL Experience Manager] Recursos, hay que considerar varios pasos para racionalizar el proceso de migración. La guía de migración incluye prácticas recomendadas sobre las tareas que realiza para incorporar los recursos a [!DNL Experience Manager] de manera gradual. Esto incluye aplicar metadatos, generar representaciones y activar los recursos para publicar la implementación.
* [Consideraciones sobre la red de recursos](assets-network-considerations.md)
Al manipular [!DNL Experience Manager] implementación, comprender la topología de red es importante para comprender el rendimiento de la red, identificar puntos de interrupción y describir la experiencia de usuario esperada. El documento Consideraciones de la red de recursos analiza las consideraciones de la red al diseñar el [!DNL Experience Manager] Implementación de recursos.
* [Guía de monitorización de activos](assets-monitoring-best-practices.md)
Después de [!DNL Experience Manager] implementación, debe monitorizar ciertas tareas y el sistema en general para garantizar la integridad y eficacia del sistema. La guía de monitorización incluye prácticas recomendadas para monitorizar varios aspectos de su sistema.
* (obsoleto) [Guía de descarga de recursos](assets-offloading-best-practices.md)
Gestión de archivos grandes y ejecución de flujos de trabajo en [!DNL Experience Manager] Los recursos pueden consumir considerables recursos de CPU, memoria y E/S. La descarga de estas tareas puede reducir las sobrecargas de CPU, memoria y E/S. La guía de descarga de recursos incluye casos de uso recomendados y prácticas recomendadas para la descarga de recursos.
* [[!DNL Experience Manager] prácticas recomendadas para las aplicaciones de escritorio](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] la aplicación de escritorio vincula la solución de administración de recursos digitales (DAM) con el escritorio para que pueda abrir los archivos disponibles en la [!DNL Experience Manager] interfaz de usuario web directamente en el escritorio. [!DNL Experience Manager] el flujo de trabajo fácil de usar de la aplicación de escritorio está habilitado mediante la tecnología de uso compartido de red que ofrecen los sistemas operativos de escritorio. En esta guía se explican las funcionalidades clave y el uso recomendado de [!DNL Experience Manager] aplicación de escritorio.
* [[!DNL Experience Manager] y prácticas recomendadas para la integración de Creative Cloud](aem-cc-integration-best-practices.md)
Puede integrar su [!DNL Experience Manager] implementación con Creative Cloud de varias formas. Seguir algunas prácticas recomendadas para racionalizar los flujos de trabajo de integración y transferencia de recursos ayuda a lograr la máxima eficacia. Esta guía incluye prácticas recomendadas sobre la integración [!DNL Experience Manager] Recursos con Adobe Creative Cloud.
* (obsoleto) [[!DNL Experience Manager] a las prácticas recomendadas de uso compartido de carpetas de Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Puede configurar [!DNL Experience Manager] para permitir que los usuarios de DAM compartan carpetas con usuarios de Creative Cloud, de modo que estén disponibles como carpetas compartidas en el servicio de Creative Cloud Assets. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de DAM. En esta guía se explican las prácticas recomendadas para aprovechar el [!DNL Experience Manager] a la función de uso compartido de carpetas de Creative Cloud.
