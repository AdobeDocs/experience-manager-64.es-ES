---
title: Integración de Adobe Sign con AEM Forms
seo-title: Integración de Adobe Sign con AEM Forms
description: Obtenga información sobre cómo configurar Adobe Sign para AEM Forms
seo-description: Obtenga información sobre cómo configurar Adobe Sign para AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Adobe Sign
translation-type: tm+mt
source-git-commit: 5944eab0bf38551970685eaa98d90c4459720245
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---


# Integrar Adobe Sign con AEM Forms {#integrate-adobe-sign-with-aem-forms}

Adobe Sign permite los flujos de trabajo de firma electrónica para formularios adaptables. Las firmas electrónicas mejoran los flujos de trabajo para procesar documentos para áreas legales, de ventas, de nómina, de gestión de recursos humanos y muchas otras áreas.

En un escenario típico de Adobe Sign y formularios adaptables, un usuario rellena un formulario adaptable para **solicitar un servicio**. Por ejemplo, una solicitud de tarjeta de crédito y un formulario de beneficios para los ciudadanos. Cuando un usuario rellena, envía y firma el formulario de solicitud, este se envía al proveedor de servicios para que realice más acciones. El proveedor de servicios revisa la aplicación y utiliza Adobe Sign para marcar la aplicación aprobada. Para habilitar flujos de trabajo de firma electrónica similares, puede integrar Adobe Sign con AEM Forms.

Para utilizar Adobe Sign con AEM Forms, configure Adobe Sign en AEM Cloud Services:

## Requisitos previos {#prerequisites}

Para integrar Adobe Sign con AEM Forms, es necesario lo siguiente:

* Una cuenta de desarrollador activa de [Adobe Sign.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Un servidor AEM Forms [SSL habilitado](/help/sites-administering/ssl-by-default.md).
* Una [aplicación de API de Adobe Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credenciales (ID de cliente y Secreto de cliente) de la aplicación de API de Adobe Sign.
* Al reconfigurar, elimine la configuración de Adobe Sign existente de las instancias de autor y publicación.
* Utilice la [clave criptográfica idéntica](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) para las instancias de autor y publicación.

## Configuración de Adobe Sign con AEM Forms {#configure-adobe-sign-with-aem-forms}

Una vez cumplidos los requisitos previos, realice los siguientes pasos para configurar Adobe Sign con AEM Forms en la instancia de autor:

1. En la instancia de autor de AEM Forms, vaya a **Tools** ![hammer](assets/hammer.png) > **General** > **Configuration Browser**.
   * Consulte la [Documentación del explorador de configuración](/help/sites-administering/configurations.md) para obtener más información.
1. En la página **[!UICONTROL Explorador de configuración]**, pulse **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]**, especifique un **[!UICONTROL Título]** para la configuración, habilite **[!UICONTROL Configuraciones de nube]** y pulse **[!UICONTROL Crear]**. Crea un contenedor de configuración para servicios en la nube.
1. Vaya a **Tools** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign** y seleccione el contenedor de configuración que creó en el paso anterior.

   >[!NOTE]
   >
   >Puede ejecutar los pasos 1-4 para crear un nuevo contenedor de configuración y una configuración de Adobe Sign en el contenedor o utilizar la carpeta `global` existente en **Herramientas** ![martillo](assets/hammer.png) > **Cloud Services** > **Adobe Sign**. Si crea la configuración en el nuevo contenedor de configuración, asegúrese de especificar el nombre del contenedor en el campo **[!UICONTROL Contenedor de configuración]** al crear un formulario adaptable.

   >[!NOTE]
   Asegúrese de que la dirección URL de la página de configuración de los servicios de nube comience por **HTTPS**. Si no es así, [habilite SSL](/help/sites-administering/ssl-by-default.md) para el servidor de AEM Forms.

1. En la página de configuración, pulse **[!UICONTROL Crear]** para crear la configuración de Adobe Sign en AEM Forms.
1. En la pestaña **[!UICONTROL General]** de la página **[!UICONTROL Crear configuración de Adobe Sign]**, especifique un **Nombre** para la configuración y pulse **Siguiente**. Si lo desea, puede especificar un título y examinar para seleccionar una miniatura para la configuración.

1. Copie la dirección URL de la ventana actual del explorador en un bloc de notas. Es necesario configurar la aplicación Adobe Sign con AEM Forms.

1. Configure los ajustes de OAuth para la aplicación Adobe Sign:

   1. Abra una ventana del explorador e inicie sesión en la cuenta de desarrollador de Adobe Sign.
   1. Seleccione la aplicación configurada para AEM Forms y pulse Configurar OAuth para la aplicación.
   1. En el cuadro **Redirigir URL**, añada la URL HTTPS copiada en el paso anterior y haga clic en **Guardar**.
   1. Habilite la siguiente configuración de OAuth para la aplicación Adobe Sign y haga clic en **Guardar**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Para obtener información paso a paso sobre la configuración de OAuth para una aplicación de Adobe Sign y obtener las claves, consulte [Configuración de autenticación para la documentación para desarrolladores de la aplicación](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) .

   ![Configuración de OAuth](assets/oauthconfig_new.png)

1. Vuelva a la página **Crear configuración de Adobe Sign**. En la pestaña **[!UICONTROL Settings]** , el campo **[!UICONTROL OAuth URL]** menciona la siguiente dirección URL predeterminada:

   `https://secure.na1.echosign.com/public/oauth`

   donde:

   **na1** hace referencia al uso compartido predeterminado de la base de datos.

   Puede modificar el valor del compartido de la base de datos. Reinicie el servidor para poder utilizar el nuevo valor para el uso compartido de la base de datos.

1. Especifique el **ID del cliente** (también denominado ID de aplicación) y el **Secreto del cliente**. Seleccione la opción **Enable Adobe Sign for attachment also** para anexar los archivos adjuntos a un formulario adaptable al documento correspondiente de Adobe Sign enviado para firmar.

   Toque **[!UICONTROL Conectarse a Adobe Sign]**. Cuando se le soliciten credenciales, proporcione el nombre de usuario y la contraseña de la cuenta utilizada al crear la aplicación de Adobe Sign.

   Toque **[!UICONTROL Crear]** para crear la configuración de Adobe Sign.

1. Abra AEM consola web. La dirección URL es `https://'[server]:[port]'/system/console/configMgr`
1. Abra **Servicio de configuración común de Forms.**
1. En el campo **Permitir**, **seleccione** Todos los usuarios: todos los usuarios, anónimos o conectados, pueden obtener una vista previa de los archivos adjuntos, verificar y firmar formularios y hacer clic en **Guardar.** La instancia de autor está configurada para utilizar Adobe Sign.
1. Utilice [replication](/help/sites-deploying/replication.md) para crear una configuración idéntica en las instancias de publicación correspondientes.

Ahora, Adobe Sign está integrado con AEM Forms y listo para usar en formularios adaptables. Para [utilizar el servicio Adobe Sign en un formulario adaptable](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), especifique el contenedor de configuración creado anteriormente en las propiedades del formulario adaptable.

## Configure el programador de Adobe Sign para sincronizar el estado de firma {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un formulario adaptable habilitado para Adobe Sign solo se envía una vez que todos los firmantes hayan completado el proceso de firma. De forma predeterminada, los servicios del programador de Adobe Sign están programados para comprobar la respuesta del firmante (encuesta) cada 24 horas. Puede cambiar el intervalo predeterminado para su entorno. Realice los siguientes pasos para cambiar el intervalo predeterminado:

1. Inicie sesión en el servidor de AEM Forms con credenciales de administrador y vaya a **Tools** > **Operations** > **Web Console**.

   También puede abrir la siguiente URL en una ventana del explorador:
   `https://[localhost]:'port'/system/console/configMgr`

1. Busque y abra la opción **Adobe Sign Configuration Service**. Especifique una [expresión de cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) en el campo **Expresión del programador de actualización de estado** y haga clic en **Guardar**. Por ejemplo, para ejecutar el servicio de configuración diariamente a las 00:00 a.m., especifique `0 0 0 1/1 * ? *` en el campo **Expresión del programador de actualización de estado**.

El intervalo predeterminado para sincronizar el estado de Adobe Sign ahora cambia.

## Artículos relacionados {#related-articles}

* [Uso de Adobe Sign en un formulario adaptable](../../forms/using/working-with-adobe-sign.md)
* [Uso de Adobe Sign con AEM Forms (vídeo)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integración de Adobe Sign con AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
