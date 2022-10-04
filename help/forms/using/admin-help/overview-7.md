---
title: Aspectos básicos de la configuración de formularios
seo-title: Basics of configuring forms
description: Obtenga información sobre los distintos servicios de formularios que le ayudan a crear aplicaciones interactivas de captura de datos.
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Aspectos básicos de la configuración de formularios {#basics-of-configuring-forms}

El servicio Forms permite crear aplicaciones cliente de captura de datos interactivas que validen, procesan, transforman y entregan formularios creados normalmente en Designer. Los autores de formularios desarrollan un único diseño de formulario que el servicio Forms procesa en varios formatos:

* como PDF en Adobe Reader o en un explorador
* como HTML en varios entornos de navegador, incluida una renderización XHTML 1.0 compatible
* como guías de formulario en varios entornos de navegador que admiten el Flash Player de Adobe.

Para obtener información adicional sobre el servicio Forms, consulte [Referencia de servicios](https://www.adobe.com/go/learn_aemforms_services_63).

Mediante la página Forms de la consola de administración, puede configurar el comportamiento del servicio Forms. Esta configuración se aplica a todas las invocaciones del servicio. Cualquier parámetro enviado a través del SDK de AEM forms anula la configuración establecida en la consola de administración; sin embargo, sólo afectan a esa invocación en particular.

Después de cambiar la configuración de Forms en la consola de administración, haga clic en Guardar. No es necesario reiniciar el servidor para que los cambios surtan efecto. Sin embargo, es posible que tenga que detener y reiniciar el servicio Forms al configurar los ajustes del modo de caché. (Consulte [Inicio y parada de servicios](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
