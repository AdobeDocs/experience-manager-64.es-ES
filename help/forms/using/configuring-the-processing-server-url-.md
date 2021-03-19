---
title: Configuración de AEM DS
seo-title: Configuración de AEM DS
description: Debe especificar la URL del servidor de procesamiento antes de enviar un formulario.
seo-description: Debe especificar la URL del servidor de procesamiento antes de enviar un formulario.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Administrador
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Configuración de AEM DS {#configuring-aem-ds-settings}

Este artículo describe cómo configurar **AEM Servicio de configuración de DS**. Esta configuración se puede utilizar en varios escenarios, por ejemplo:

* En la gestión de correspondencia

   * Para configurar el flujo de trabajo de AEM Forms
   * Mientras se utiliza el portal de formularios para el guardado remoto del borrador/envío

* En formularios adaptables para casos en los que el formulario adaptable se envía desde una instancia de publicación

A continuación se indican los pasos para configurar la **[!UICONTROL AEM Configuración de DS]**:

1. Abra el Administrador de configuración en la instancia de publicación mediante la URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. En la ventana **[!UICONTROL Adobe Experience Manager Web Console Configuration]**, busque y haga clic en la opción **[!UICONTROL AEM Configuración de DS]**.

   ![ds_settings](assets/ds_settings.png)

1. La ventana **[!UICONTROL AEM Servicio de configuración de DS]** muestra los ajustes de configuración comunes para AEM componentes de DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Añada la siguiente información en los campos respectivos:

   **[!UICONTROL URL]** del servidor de procesamiento: El servidor de procesamiento es el servidor en el que se debe activar el flujo de trabajo de Forms o AEM. Puede ser la misma que la URL de la instancia de autor de AEM o de la otra URL de servidor (es decir, http:// localhost:port/).

   **[!UICONTROL Nombre]** de usuario del servidor de procesamiento: Nombre de usuario del usuario del flujo de trabajo  [basado en la URL del servidor que se está utilizando]

   **[!UICONTROL Contraseña]** del servidor de procesamiento: Contraseña del usuario del flujo de trabajo

   >[!NOTE]
   >
   >* Al utilizar Forms o AEM flujos de trabajo, antes de realizar cualquier envío desde el servidor de publicación, es necesario configurar el servicio de configuración de DS. De lo contrario, el envío del formulario fallará.

