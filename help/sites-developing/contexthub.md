---
title: ContextHub
seo-title: ContextHub
description: ContextHub es un marco para almacenar, manipular y presentar datos de contexto
seo-description: ContextHub is a framework for storing, manipulating, and presenting context data
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
exl-id: 0a6b815a-5055-4c44-96d1-ff238b4285f3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 3%

---

# ContextHub{#contexthub}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

ContextHub es un marco para almacenar, manipular y presentar datos de contexto. La API de JavaScript del lado del cliente le permite acceder a los datos para personalizar el contenido.

>[!NOTE]
>
>La variable [Implementación de referencia de We.Retail](/help/sites-developing/we-retail.md) implementa ContextHub y puede servir de referencia cuando integra ContextHub en su propio proyecto.

>[!CAUTION]
>
>La ruta que contiene la configuración de ContextHub de muestra que usa el [Implementación de referencia de We.Retail](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) solo debe utilizarse como referencia para crear su propia configuración.
>
>No debe utilizarse en un proyecto como su propia configuración de ContextHub.

## Persistencia {#persistence}

ContextHub almacena datos de contexto persistentes en el cliente. La API de JavaScript de ContextHub le permite acceder a las tiendas para crear, actualizar y eliminar datos según sea necesario. Como tal, ContextHub representa una capa de datos en las páginas.

Cada almacén de ContextHub es una instancia de un tipo de almacén predefinido:

* ContextHub proporciona varios [tipos de almacén de muestras](/help/sites-developing/ch-samplestores.md).
* Usar AEM consolas para [crear tiendas](/help/sites-administering/contexthub-config.md#creating-a-contexthub-store).
* Los desarrolladores pueden [crear tipos de almacén personalizados](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Los desarrolladores pueden [datos de almacenamiento de acceso](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) a través de Javascript.

## Segmentación {#segmentation}

ContextHub incluye un motor de segmentación que administra segmentos y determina qué segmentos se resuelven para el contexto actual. Se definen varios segmentos. Puede utilizar la API de Javascript para [determinar segmentos resueltos](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Presentación {#presentation}

La variable [Barra de herramientas de ContextHub](/help/sites-authoring/ch-previewing.md) permite a los especialistas en marketing y a los autores ver y manipular los datos de almacenamiento para simular la experiencia del usuario al crear páginas. La barra de herramientas está formada por grupos de módulos de IU que proporcionan acceso a los almacenes de ContextHub.

Cada módulo de interfaz de usuario de ContextHub es una instancia de un tipo de módulo predefinido:

* ContextHub proporciona varios [tipos de módulo de muestra](/help/sites-developing/ch-samplemodules.md).
* Usar AEM consolas para [añadir módulos de IU](/help/sites-administering/contexthub-config.md#adding-a-ui-module)y [agruparlos en modos de IU](/help/sites-administering/contexthub-config.md#adding-a-ui-mode).

* Los desarrolladores pueden [crear tipos de módulos personalizados](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Los desarrolladores deben [añadir el componente ContextHub a la página](/help/sites-developing/ch-adding.md).
