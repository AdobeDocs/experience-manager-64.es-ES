---
title: Información general sobre los informes de transacciones
seo-title: Transaction Reports Overview
description: Mantenga un recuento de todos los formularios enviados, la comunicación interactiva representada, los documentos convertidos en un formato a otro, y más
seo-description: Keep a count of all the forms submitted, interactive communication rendered, Documents converted to one format to another, and more
uuid: b40220e6-88c8-4507-b228-6c57d9b54422
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 1fb11e02-d8f1-41a0-8e23-cb890b4e2244
exl-id: a545aa0a-9d71-48ba-ba3e-ed30a7e34f3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 95%

---

# Información general sobre los informes de transacciones {#transaction-reports-overview}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Mantenga un recuento de todos los formularios enviados, la comunicación interactiva representada, los documentos convertidos en un formato a otro, y más

## Introducción {#introduction}

Los informes de transacciones de AEM Forms permiten mantener un recuento de todas las transacciones realizadas desde una fecha especificada en su implementación de AEM Forms. El objetivo es proporcionar información sobre el uso del producto y ayudar a las partes interesadas empresariales a comprender sus volúmenes de procesamiento digital. Algunos ejemplos de transacciones son:

* Envío de un formulario adaptable, un formulario HTML5 o un conjunto de formularios
* Representación de una versión impresa o web de una comunicación interactiva
* Conversión de un documento de un formato de archivo a otro

Para obtener más información sobre lo que se considera una transacción, consulte [API facturables](/help/forms/using/transaction-reports-billable-apis.md).

El registro de transacciones está desactivado de forma predeterminada. Puede [habilitar el registro de transacciones](/help/forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) desde la consola web de AEM. Puede ver informes de transacciones sobre instancias de autor, procesamiento o publicación. Ver informes de transacciones sobre instancias de autor o procesamiento para una suma agregada de todas las transacciones. Ver informes de transacciones en las instancias de publicación para un recuento de todas las transacciones que se realizan solamente en esa instancia de publicación desde la que se ejecuta el informe.

No cree contenido (crear formularios adaptables, comunicación interactiva, temáticas y otras actividades de creación) ni procese documentos (utilizar flujos de trabajo, servicios de documentos y otras actividades de procesamiento) en la misma instancia de AEM. Mantener la grabación de transacciones deshabilitada para los servidores de AEM Forms utilizados para crear contenido. Mantener la grabación de transacciones habilitada para los servidores de AEM Forms utilizados para procesar documentos.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Una transacción permanece en el búfer durante un período especificado (tiempo de búfer de vaciado + tiempo de replicación inversa). De forma predeterminada, el recuento de transacciones tarda aproximadamente 90 segundos en reflejarse en el informe de transacciones.

Las acciones como enviar un formulario PDF, utilizar la interfaz de usuario del agente para obtener una vista previa de una comunicación interactiva o usar los métodos de envío de formulario no estándar no se contabilizan como transacciones. AEM Forms proporciona un API para registrar esas transacciones. Llame al API desde sus implementaciones personalizadas y registrar una transacción.

## Topología admitida {#supported-topology}

Los informes de transacciones solo están disponibles en AEM Forms en el entorno OSGi. Admite autor-publicación, autor-procesamiento-publicación y procesar solo topologías. Por ejemplo, para las topologías, consulte [Topologías de arquitectura e implementación para AEM Forms](/help/forms/using/transaction-reports-overview.md).

El recuento de transacciones se replica de forma inversa de las instancias de publicación a las instancias de autor o procesamiento. A continuación se muestra una topología indicativa de autor-publicación:

![topología simple de publicación del autor](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>Los informes de transacciones de AEM Forms no admiten topologías que contengan solo instancias de publicación.

### Directrices para utilizar informes de transacciones {#guidelines-for-using-transaction-reports}

* Deshabilite los informes de transacciones en todas las instancias de autor, ya que los informes de instancias de autor incluyen transacciones registradas durante las actividades de creación.
* Habilite la opción **Mostrar transacciones solo de publicación** en la instancia de autor para ver las transacciones acumulativas de todas las instancias de publicación. También puede ver informes de transacciones en cada instancia de publicación para transacciones reales solo en esa instancia de publicación en particular.
* No utilice instancias de autor para ejecutar flujos de trabajo y procesar documentos.
* Antes de usar los informes de transacciones, si cuenta con una topología con servidores de publicación, asegúrese de que la replicación inversa esté habilitada para todas las instancias de publicación.
* Los datos de transacción se replican de forma inversa de una instancia de publicación a la instancia de autor o procesamiento correspondiente. El autor o la instancia de procesamiento no pueden replicar más datos en otra instancia. Por ejemplo, si tiene la topología autor-procesamiento-publicación, los datos de transacción agregados se replican solo en la instancia de procesamiento.

## Artículos relacionados {#related-articles}

* [Ver y comprender los informes de transacciones](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [API facturables de informes de transacciones](/help/forms/using/transaction-reports-billable-apis.md)
* [Registrar una transacción para implementaciones personalizadas](/help/forms/using/record-transaction-custom-implementation.md)
