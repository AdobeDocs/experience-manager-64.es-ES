---
title: Configurar la página de redireccionamiento
seo-title: Configuring redirect page
description: Después de rellenar un formulario adaptable, los usuarios pueden ser redirigidos a una página web que los autores del formulario pueden configurar mientras lo crean..
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 88%

---

# Configurar la página de redireccionamiento {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los autores de formularios pueden configurar una página para cada formulario, a la cual se redirigirá a los usuarios una vez enviado.

1. En el modo de edición, seleccione un componente y, a continuación, pulse ![field-level](assets/field-level.png) > **Contenedor de formulario adaptable** y haga clic en ![cmppr](assets/cmppr.png).

1. En la barra lateral, haga clic en **Envío**.

1. Proporcione la URL de la página de redirección en la sección Presentación de la página de agradecimiento.
1. De forma opcional, en Acción de envío, puede configurar el parámetro que se pasará a la página de redireccionamiento para la acción Enviar a extremo REST.

![Configuración de la página de redireccionamiento](assets/thank-you-setting-1.png)
**Figura:** *Redirigir la configuración de la página*

Los autores de formularios pueden utilizar los siguientes parámetros, los cuales se pasan a la página de agradecimiento. Los parámetros `status` y `owner` se aprueban para todas las acciones de envío disponibles. Además de estos dos parámetros, se aprueban algunos parámetros adicionales para las siguientes acciones de envío:

* **Acción Almacenar contenido** (obsoleto) `contentPath`: se aprueba la ruta del nodo en el repositorio donde se almacenan los datos enviados.

* **Acción Almacenar PDF** (obsoleto): `contentPath`de los datos enviados y la ruta al nodo que almacena el archivo PDF en el repositorio, se aprueba 

* **Enviar al flujo de trabajo de Forms**: se aprueban los parámetros de salida devueltos por el flujo de trabajo de Forms.

* **Enviar a extremo REST**: se aprueban los parámetros agregados para la asignación de campos en uso a parámetros. Los parámetros `status` y `owner` no se aprueban en esta acción de envío. Para obtener más información, consulte [Configurar la acción Enviar al punto final REST](/help/forms/using/configuring-submit-actions.md).
