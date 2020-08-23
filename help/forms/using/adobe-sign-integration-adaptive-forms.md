---
title: Integrar Adobe Sign con AEM Forms
seo-title: Integrar Adobe Sign con AEM Forms
description: Obtenga información sobre cómo configurar Adobe Sign para AEM Forms
seo-description: Obtenga información sobre cómo configurar Adobe Sign para AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---


# Integrar Adobe Sign con AEM Forms {#integrate-adobe-sign-with-aem-forms}

Obtenga información sobre cómo configurar Adobe Sign para AEM Forms

Adobe Sign permite flujos de trabajo de firma electrónica para formularios adaptables. Las firmas electrónicas mejoran los flujos de trabajo para procesar documentos legales, de ventas, de nómina de pagos, de gestión de recursos humanos y muchas otras áreas.

En un escenario típico de Adobe Sign y formularios adaptables, un usuario rellena un formulario adaptable para aplicar a un servicio. Por ejemplo, una solicitud de tarjeta de crédito y un formulario de beneficios para el ciudadano. Cuando un usuario rellena, envía y firma el formulario de solicitud, éste se envía al proveedor de servicio para que realice más acciones. Proveedor de servicio revisa la aplicación y utiliza Adobe Sign para marcar la aplicación aprobada. Para habilitar flujos de trabajo de firma electrónica similares, puede integrar Adobe Sign con AEM Forms.

Para usar Adobe Sign con AEM Forms, configure Adobe Sign en los servicios de nube de AEM:

## Requisitos previos {#prerequisites}

Para integrar Adobe Sign con AEM Forms, es necesario lo siguiente:

* Cuenta [de desarrollador de](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)Adobe Sign activa.
* Un servidor [SSL habilitado](/help/sites-administering/ssl-by-default.md) para AEM Forms.
* Una aplicación [API de](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md)Adobe Sign.
* Credenciales (ID de cliente y Secreto de cliente) de la aplicación API de Adobe Sign.

## Configurar Adobe Sign con AEM Forms {#configure-adobe-sign-with-aem-forms}

Una vez que se hayan establecido los requisitos previos, realice los siguientes pasos para configurar Adobe Sign con AEM Forms en la instancia de autor:

1. En la instancia de autor de AEM Forms, vaya a **[!UICONTROL Herramientas** ![martillo](assets/hammer.png) > **General** > **Navegador]** de configuración.
1. En la página **[!UICONTROL Navegador]** de configuración, toque **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]** , especifique un **[!UICONTROL Título]** para la configuración, habilite Configuraciones **[!UICONTROL de]** nube y toque **[!UICONTROL Crear]**. Crea un contenedor de configuración para los servicios en la nube.
1. Vaya a **[!UICONTROL Herramientas** ![martillo](assets/hammer.png) > **Cloud Services** > **Adobe Sign]** y seleccione el contenedor de configuración que ha creado en el paso anterior.

   >[!NOTE]
   >
   >Asegúrese de que la dirección URL de la página de configuración de servicios en la nube inicio con **HTTPS**. Si no es así, [habilite SSL](/help/sites-administering/ssl-by-default.md) para el servidor de AEM Forms.

1. En la página de configuración, toque **[!UICONTROL Crear]** para crear la configuración de Adobe Sign en AEM Forms.
1. En la ficha **[!UICONTROL General]** de la página **[!UICONTROL Crear configuración]** de Adobe Sign, especifique un **[!UICONTROL nombre]** para la configuración y toque **[!UICONTROL Siguiente]**. Opcionalmente, puede especificar un título y examinar para seleccionar una miniatura para la configuración.

   Copie la URL en la ventana actual del explorador. Es necesario configurar la aplicación Adobe Sign con AEM Forms.

1. Configure la configuración de OAuth para la aplicación Adobe Sign:

   1. Abra una ventana del explorador e inicie sesión en la cuenta de desarrollador de Adobe Sign.
   1. Seleccione la aplicación configurada para AEM Forms y toque Configurar OAuth para la aplicación.
   1. En el cuadro URL **[!UICONTROL de]** redirección, agregue la URL HTTPS copiada en el paso anterior y haga clic en **[!UICONTROL Guardar]**.
   1. Habilite la siguiente configuración de OAuth para la aplicación Adobe Sign y haga clic en **[!UICONTROL Guardar]**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Para obtener información paso a paso sobre la configuración de OAuth para una aplicación de Adobe Sign y obtener las claves, consulte [Configuración de autenticación para la documentación del desarrollador de la aplicación](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) .

   ![Configuración de OAuth](assets/oauth_config.png)

1. Vuelva a la página **[!UICONTROL Crear configuración]** de Adobe Sign. En la ficha **[!UICONTROL Configuración]** , el campo URL **[!UICONTROL de]** OAuth menciona la siguiente dirección URL predeterminada:

   `https://secure.na1.echosign.com/public/oauth`

   donde:

   **na1** hace referencia al uso compartido predeterminado de la base de datos.

   Puede modificar el valor del uso compartido de la base de datos. Reinicie el servidor para poder usar el nuevo valor para el uso compartido de la base de datos.

1. Especifique el ID **[!UICONTROL de]** cliente (también denominado ID de aplicación) y el secreto **[!UICONTROL de cliente]**. Seleccione la opción **[!UICONTROL Activar Adobe Sign para archivos adjuntos también]** para anexar archivos adjuntos a un formulario adaptable al documento de Adobe Sign correspondiente enviado para firmar.

   Tap **[!UICONTROL Connect to Adobe Sign]**. Cuando se le soliciten las credenciales, especifique el nombre de usuario y la contraseña de la cuenta utilizada al crear la aplicación Adobe Sign.

   Toque **[!UICONTROL Crear]** para crear la configuración de Adobe Sign.

1. Abra AEM consola web. La dirección URL es `https://[server]:[port]/system/console/configMgr`
1. Abra **[!UICONTROL Forms Common Configuration Service]**.
1. En el campo **[!UICONTROL Permitir]** , seleccione **[!UICONTROL Todos los usuarios]** : todos los usuarios, anónimos o conectados, pueden previsualización de archivos adjuntos, comprobar y firmar formularios y hacer clic en **[!UICONTROL Guardar]**. La instancia de autor está configurada para usar Adobe Sign.
1. En la instancia de [publicación](/help/sites-deploying/deploy.md) , inicie sesión y abra la siguiente URL:

   `https://<server-name>:<port>/libs/granite/configurations/content/view.html/conf`

1. Repita los pasos del 1 al 12 para configurar Adobe Sign con AEM Forms. Utilice el mismo título para la configuración (como se especifica en el paso 3) y el mismo nombre (como se especifica en el paso 6) para replicar la configuración configurada en la instancia de Autor.

   Ahora, Adobe Sign está integrado con AEM Forms y listo para su uso en formularios adaptables. Para [utilizar el servicio Adobe Sign en un formulario](/help/forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)adaptable, especifique el contenedor de configuración creado anteriormente en las propiedades del formulario adaptable.

## Configurar el Planificador de Adobe Sign para sincronizar el estado de firma {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un formulario adaptable habilitado para Adobe Sign solo se envía después de que todos los firmantes hayan completado el proceso de firma. De forma predeterminada, los servicios de Adobe Sign Planificador están programados para comprobar la respuesta del firmante (encuesta) cada 24 horas. Puede cambiar el intervalo predeterminado del entorno. Realice los siguientes pasos para cambiar el intervalo predeterminado:

1. Inicie sesión en el servidor de AEM Forms con credenciales de administrador y vaya a **[!UICONTROL Herramientas]** > **Operaciones** > Consola **** web.

   También puede abrir la siguiente URL en una ventana del explorador:

   `https://[localhost]:[port]/system/console/configMgr`

1. Busque y abra la opción Servicio **[!UICONTROL de configuración de]** Adobe Sign. Especifique una expresión [](https://en.wikipedia.org/wiki/Cron#CRON_expression) cron en el campo de Expresión **[!UICONTROL del Planificador de actualización]** de estado y haga clic en **[!UICONTROL Guardar]**. Por ejemplo, para ejecutar el servicio de configuración diariamente a las 00:00 a.m., especifique `0 0 0 1/1 * ? *` en el campo de Expresión **[!UICONTROL del Planificador de actualización de]** estado.

El intervalo predeterminado para sincronizar el estado de Adobe Sign ahora cambia.
