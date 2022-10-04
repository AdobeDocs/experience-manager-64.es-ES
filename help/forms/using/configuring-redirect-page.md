---
title: Configuración de la página de redireccionamiento
seo-title: Configuring redirect page
description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores de formularios pueden configurar al crear el formulario.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 42%

---

# Configuración de la página de redireccionamiento {#configuring-redirect-page}

Los autores de formularios pueden configurar una página para cada formulario, a la cual se redirigirá a los usuarios una vez enviado.

1. En el modo de edición, seleccione un componente y, a continuación, pulse ![field-level](assets/field-level.png) > **Contenedor de formulario adaptable** y haga clic en ![cmppr](assets/cmppr.png).

1. En la barra lateral, haga clic en **Envío**.

1. Proporcione la dirección URL de la página de redireccionamiento en Página de agradecimiento en la sección Envío .
1. De forma opcional, en Acción de envío, puede configurar el parámetro que se pasará a la página de redireccionamiento para la acción Enviar a extremo REST.

![Configuración de la página de redireccionamiento](assets/thank-you-setting-1.png)
**Figura:** *Redirigir la configuración de la página*

Los autores de formularios pueden utilizar los siguientes parámetros, los cuales se pasan a la página de agradecimiento. Para todas las acciones de envío disponibles, `status` y `owner` se pasan. Además de estos dos parámetros, se pasan algunos parámetros adicionales para las siguientes acciones de envío:

* **Acción Almacenar contenido** (obsoleto) : `contentPath`: se pasa la ruta del nodo en el repositorio donde se almacenan los datos enviados.

* **Acción del PDF del almacén** (obsoleto) : `contentPath`—de los datos enviados y la ruta al nodo que almacena el archivo PDF en el repositorio—se pasa.

* **Enviar al flujo de trabajo de Forms**: Se pasan los parámetros de salida devueltos por el flujo de trabajo de formularios.

* **Enviar a extremo REST**: se pasan los parámetros añadidos para la asignación de campos en uso a parámetros. `status` y `owner` no se pasan en esta acción de envío. Para obtener más información, consulte [Configuración de la acción de envío de extremo Submit to REST](/help/forms/using/configuring-submit-actions.md).
