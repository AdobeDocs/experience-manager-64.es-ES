---
title: Configuración de la página de redireccionamiento
seo-title: Configuración de la página de redireccionamiento
description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores de formularios pueden configurar al crear el formulario.
seo-description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores de formularios pueden configurar al crear el formulario.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Configuración de la página de redireccionamiento {#configuring-redirect-page}

Los autores de formularios pueden configurar una página para cada formulario, a la que se redirige a los usuarios después de enviar un formulario.

1. En el modo de edición, seleccione un componente, luego haga clic en ![Contenedor de campo](assets/field-level.png) > **Formulario adaptable** y, a continuación, haga clic en ![cmppr](assets/cmppr.png).

1. En la barra lateral, haga clic en **Envío**.

1. Proporcione la dirección URL de la página de redireccionamiento en Página de agradecimiento en la sección Envío.
1. Opcionalmente, en Enviar acción, para la acción de extremo Enviar a REST, puede configurar el parámetro que se pasará a la página de redirección.

![Redirigir ](assets/thank-you-setting-1.png)
**configuración de páginaFigura:** *Redirigir configuración de página*

Los autores de formularios pueden utilizar los siguientes parámetros que se pasan a la página de agradecimiento. Para todas las acciones de envío disponibles, se pasan los parámetros `status` y `owner`. Además de estos dos parámetros, se pasan algunos parámetros adicionales para las siguientes acciones de envío:

* **Acción**  de almacenamiento de contenido (desaprobada):  `contentPath`se pasa la ruta del nodo del repositorio en el que se almacenan los datos enviados.

* **Acción**  de almacenar PDF (desaprobada):  `contentPath`—de los datos enviados y de la ruta al nodo que almacena el archivo PDF en el repositorio— se pasa.

* **Enviar al flujo de trabajo** de Forms: Se pasan los parámetros de salida devueltos por el flujo de trabajo de formularios.

* **Enviar al extremo** REST: Se pasan los parámetros añadidos para la asignación de parámetros en el campo. `status` y  `owner` los parámetros no se pasan en esta acción de envío. Para obtener más información, consulte [Configuración de la acción Enviar a envío de extremo REST](/help/forms/using/configuring-submit-actions.md).

