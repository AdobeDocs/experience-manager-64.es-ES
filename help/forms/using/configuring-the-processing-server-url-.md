---
title: Configuración de AEM DS
seo-title: Configuring AEM DS settings
description: Debe especificar la URL del servidor de procesamiento antes de enviar un formulario.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Configuración de AEM DS {#configuring-aem-ds-settings}

Este artículo describe cómo configurar **Servicio de configuración de AEM DS**. Esta configuración se puede utilizar en varios escenarios, por ejemplo:

* En la gestión de correspondencia

   * Para configurar el flujo de trabajo de AEM Forms
   * Mientras se utiliza el portal de formularios para el guardado remoto del borrador/envío

* En formularios adaptables para casos en los que el formulario adaptable se envía desde una instancia de publicación

A continuación se indican los pasos para configurar la variable **[!UICONTROL Configuración de AEM DS]**:

1. Abra el Administrador de configuración en la instancia de publicación mediante la URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. En el **[!UICONTROL Configuración de la consola web de Adobe Experience Manager]** , busque y haga clic en **[!UICONTROL Configuración de AEM DS]** .

   ![ds_settings](assets/ds_settings.png)

1. La variable **[!UICONTROL Servicio de configuración de AEM DS]** muestra los ajustes de configuración comunes de AEM componentes DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Añada la siguiente información en los campos respectivos:

   **[!UICONTROL URL del servidor de procesamiento]**: El servidor de procesamiento es el servidor en el que se debe activar el flujo de trabajo de Forms o AEM. Puede ser la misma que la URL de la instancia de autor de AEM o de la otra URL de servidor (es decir, http:// localhost:port/).

   **[!UICONTROL Nombre de usuario del servidor de procesamiento]**: Nombre de usuario del usuario del flujo de trabajo [en función de la URL del servidor que se esté utilizando]

   **[!UICONTROL Contraseña del servidor de procesamiento]**: Contraseña del usuario del flujo de trabajo

   >[!NOTE]
   >
   >* Al utilizar Forms o AEM flujos de trabajo, antes de realizar cualquier envío desde el servidor de publicación, es necesario configurar el servicio de configuración de DS. De lo contrario, el envío del formulario fallará.

