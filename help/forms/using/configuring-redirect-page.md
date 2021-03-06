---
title: Configuración de la página de redireccionamiento
seo-title: Configuración de la página de redireccionamiento
description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores de formularios pueden configurar al crear el formulario.
seo-description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores de formularios pueden configurar al crear el formulario.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Configuración de la página de redireccionamiento {#configuring-redirect-page}

Los autores de formularios pueden configurar una página para cada formulario, a la que se redirige a los usuarios después de enviar el formulario.

1. En el modo de edición, seleccione un componente, haga clic en ![field-level](assets/field-level.png) > **Adaptive Form Container** y, a continuación, haga clic en ![cmppr](assets/cmppr.png).

1. En la barra lateral, haga clic en **Envío**.

1. Proporcione la dirección URL de la página de redireccionamiento en Página de agradecimiento en la sección Envío .
1. De forma opcional, en Enviar acción, para la acción de extremo Enviar a REST, puede configurar el parámetro que se pasará a la página de redirección.

![Redirigir la ](assets/thank-you-setting-1.png)
**configuración de la páginaFigura:** *Redirigir la configuración de la página*

Los autores de formularios pueden utilizar los siguientes parámetros que se pasan a la página de agradecimiento. Para todas las acciones de envío disponibles, se pasan los parámetros `status` y `owner` . Además de estos dos parámetros, se pasan algunos parámetros adicionales para las siguientes acciones de envío:

* **Acción Almacenar contenido**  (obsoleto) :  `contentPath`: se pasa la ruta del nodo en el repositorio donde se almacenan los datos enviados.

* **acción Almacenar PDF**  (obsoleto) :  `contentPath`—de los datos enviados y la ruta al nodo que almacena el archivo PDF en el repositorio— se pasa.

* **Enviar al flujo de trabajo** de Forms: Se pasan los parámetros de salida devueltos por el flujo de trabajo de formularios.

* **Enviar al extremo** REST: Se pasan los parámetros añadidos para la asignación de parámetros en el campo a . `status` Los  `owner` parámetros y no se pasan en esta acción de envío. Para obtener más información, consulte [Configuración de la acción de envío del extremo Submit to REST](/help/forms/using/configuring-submit-actions.md).

