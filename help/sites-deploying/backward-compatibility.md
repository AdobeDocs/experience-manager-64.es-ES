---
title: Compatibilidad con versiones anteriores en AEM 6.4
seo-title: Compatibilidad con versiones anteriores en AEM 6.4
description: Obtenga información sobre cómo mantener las aplicaciones y configuraciones compatibles con AEM 6.4
seo-description: Obtenga información sobre cómo mantener las aplicaciones y configuraciones compatibles con AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---


# Compatibilidad con versiones anteriores en AEM 6.4{#backward-compatibility-in-aem}

## Información general {#overview}

>[!NOTE]
>
>Para obtener una lista de los cambios de contenido y configuración que no están dentro del ámbito del paquete de compatibilidad, consulte [Reestructuración del repositorio en AEM 6.4](/help/sites-deploying/repository-restructuring.md).

En AEM 6.4, todas las características se han desarrollado teniendo en cuenta la compatibilidad con versiones anteriores.

En la mayoría de los casos, los clientes que ejecutan AEM 6.3 no deben cambiar el código o las personalizaciones al realizar la actualización. Para los clientes de AEM 6.1 y 6.2, no hay cambios de ruptura adicionales que los que se enfrentarían durante una actualización a 6.3.

Para las excepciones en las que las funciones no se podían mantener compatibles con versiones anteriores, se puede lograr la compatibilidad con versiones anteriores de paquetes y contenido instalando un paquete de compatibilidad para la versión 6.3 (consulte cómo configurarlo a continuación para obtener más información sobre dónde descargar). Este paquete de compatibilidad restaurará la compatibilidad para las aplicaciones compatibles con AEM 6.3.

El paquete de compatibilidad le permite ejecutar AEM en modo de compatibilidad y diferir el desarrollo personalizado con las nuevas funciones de AEM:

>[!NOTE]
>
>Tenga en cuenta que el paquete de compatibilidad es solo una solución temporal para retrasar el desarrollo necesario para ser compatible con AEM 6.4. Se recomienda solo como última opción si no puede abordar los problemas de compatibilidad mediante el desarrollo inmediatamente después de la actualización. Se recomienda cambiar al modo nativo y desinstalar el paquete de compatibilidad una vez que decida continuar con el desarrollo personalizado basado en la versión 6.4 y disponer de la funcionalidad completa de la versión 6.4.

![screen_shot_2018-04-05at4339pm](assets/screen_shot_2018-04-05at43339pm.png)

El paquete de compatibilidad tiene dos modos: **Enrutamiento habilitado** y **Enrutamiento deshabilitado**.

Esto permite ejecutar AEM 6.4 en tres modos:

**Modo nativo:**

El modo nativo es para clientes que desean utilizar todas las nuevas funciones de AEM 6.4 y están listos para hacer algo de desarrollo para que sus personalizaciones funcionen con todas las nuevas funciones.

Esto significa que es posible que tenga que realizar ajustes en la aplicación inmediatamente después de la actualización.

**Modo de compatibilidad: Paquete de compatibilidad instalado con enrutamiento habilitado**

El modo de compatibilidad es para clientes que tienen personalizaciones de interfaces que no son compatibles con versiones anteriores. Esto permite que la AEM se ejecute en modo de compatibilidad y que se aplace el desarrollo personalizado necesario para las nuevas funciones de AEM que no son compatibles con algunos de sus códigos personalizados.

**Modo heredado: Paquete de compatibilidad instalado con enrutamiento deshabilitado**

El modo heredado es para clientes que tienen interfaces personalizadas basadas en código heredado o obsoleto de AEM que se ha movido fuera del paquete de compatibilidad.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Configuración {#how-to-set-up}

El paquete de compatibilidad de AEM 6.3 se puede instalar como paquete mediante el Administrador de paquetes. Puede descargar el [AEM paquete de compatibilidad 6.3 del sitio Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63).

Una vez instalado el paquete de compatibilidad, el enrutamiento se puede habilitar o deshabilitar utilizando un conmutador en la configuración OSGI como se muestra a continuación:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Una vez instalado y configurado el paquete de compatibilidad, las funciones se utilizan en función del modo de compatibilidad seleccionado.
