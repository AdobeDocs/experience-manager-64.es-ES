---
title: Instalar [!DNL Workfront for Experience Manager enhanced connector]
description: Instalar [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 967391db-e7ba-4cf8-af9e-28c28d2d96d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 3%

---

# Instalar [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Un usuario con acceso de administrador en [!DNL Adobe Experience Manager] instala el conector mejorado. Antes de realizar la instalación, revise el soporte de plataforma y otros [requisitos previos para el conector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!TIP]
>
>¿Está buscando la variable [!DNL Workfront for Experience Manager enhanced connector] documentación para AEM as a Cloud Service? Haga clic en [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-install.html?lang=en).

>[!IMPORTANT]
>
>* El Adobe requiere la implementación y la configuración del [!DNL Adobe Workfront for Experience Manager enhanced connector] solo a través de socios certificados o [!DNL Adobe Professional Services]. Si se implementa y se configura sin un socio certificado o [!DNL Adobe Professional Services], no es compatible con Adobe.
>
>* Adobe puede publicar actualizaciones en [!DNL Adobe Workfront] y [!DNL Adobe Experience Manager] que hacen que este conector sea redundante; si esto ocurre, es posible que se requiera a los clientes que pasen del uso de este conector.
>
>* Adobe admite las versiones 1.7.4 y posteriores del conector mejorado. No se admiten versiones anteriores y personalizadas. Para comprobar la versión del conector mejorado, vaya a la `digital.hoodoo` grupo disponible en el panel izquierdo de [Administrador de paquetes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=es).
>
>* Consulte [Examen de certificación de socios para conector mejorado de Workfront para Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Para obtener información acerca del examen, consulte [Guía de examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


Para instalar el conector, siga estos pasos:

1. Descargue el conector desde [[!DNL Software Distribution] vínculo](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [Configuración del cortafuegos](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html).

1. En Dispatcher, permita encabezados HTTP con el nombre `authorization`, `username`y `apikey`. Permitir `GET`, `POST`y `PUT` solicitudes a `/bin/workfront-tools`.

1. Asegúrese de que las rutas siguientes no existan en [!DNL Experience Manager] repositorio:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Instale el paquete utilizando [!UICONTROL Administrador de paquetes]. Para saber cómo instalar paquetes, consulte [Documentación del Administrador de paquetes](/help/sites-administering/package-manager.md).

1. Crear `wf-workfront-users` en [!DNL Experience Manager] Grupo de usuarios y asignar el permiso `jcr:all` a `/content/dam`.

Un usuario del sistema `workfront-tools` se crea automáticamente y los permisos necesarios se administran automáticamente. Todos los usuarios de [!DNL Workfront] que utilizan el conector se añaden automáticamente como parte de este grupo.

## Configurar la conexión entre [!DNL Experience Manager] y [!DNL Workfront] {#configure-connection}

Para crear una conexión con Workfront, siga estos pasos:

1. En [!DNL Experience Manager], seleccione **[!UICONTROL Herramientas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuración de herramientas de Workfront]**.

1. Select `workfront-tools` en el panel izquierdo y seleccione **[!UICONTROL Crear]** en el área superior derecha de la página.

1. En el **[!UICONTROL Conexión de Workfront]** , proporcione los detalles requeridos del [!DNL Workfront] implementación y seleccione **[!UICONTROL Conectarse a Workfront]** . Una vez que se haya conectado correctamente, la variable [!DNL Workfront] la integración personalizada de documento se crea automáticamente en la variable [!DNL Workfront] entorno.

   ![Connect [!DNL Experience Manager] y [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Para verificar la conexión, acceda a ella en [!DNL Workfront] y compruebe que la clave de API es la misma y que la conexión es **[!UICONTROL Habilitado]**. Para ello, seleccione **[!UICONTROL Configuración]** > **[!UICONTROL Documentos]** > **[!UICONTROL Integraciones personalizadas]** en [!DNL Workfront].

## Actualizar [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

Experience Manager Assets le permite actualizar el [!DNL Workfront for Experience Manager enhanced connector] de una versión anterior a la más reciente.

Para actualizar el [!DNL Workfront for Experience Manager enhanced connector] a la versión más reciente:

1. Descargue la versión más reciente del conector mejorado desde [[!DNL Software Distribution] vínculo](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. Instale el paquete utilizando [!UICONTROL Administrador de paquetes]. Para saber cómo instalar paquetes, consulte [Documentación del Administrador de paquetes](/help/sites-administering/package-manager.md).
