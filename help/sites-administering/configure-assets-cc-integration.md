---
title: Configuración de la integración de AEM Assets con Experience Cloud
description: Obtenga información sobre cómo configurar la integración de AEM Assets con Experience Cloud.
feature: Asset Management
role: User, Architect, Admin
exl-id: f8629c30-1901-4b6e-b5a6-e46ee3c72fba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 3%

---

# Configuración de la integración de AEM Assets con Experience Cloud {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Si es cliente de Adobe Experience Cloud, puede sincronizar los recursos dentro de Adobe Experience Manager Assets con Adobe Creative Cloud y viceversa. También puede sincronizar los recursos con el Experience Cloud y viceversa. Puede configurar esta sincronización mediante [!DNL Adobe I/O]. El nombre actualizado de [!DNL Adobe Marketing Cloud] es [!DNL Adobe Experience Cloud].

El flujo de trabajo para configurar esta integración es:

1. Cree una autenticación en [!DNL Adobe I/O] uso de una puerta de enlace pública y obtención de un ID de aplicación.
1. Cree un perfil en la instancia de AEM Assets con el ID de la aplicación.
1. Utilice esta configuración para sincronizar los recursos.

En el servidor back-end, el servidor AEM autentica el perfil con la puerta de enlace y, a continuación, sincroniza los datos entre Assets y el Experience Cloud.

>[!NOTE]
>
>Esta función está en desuso en AEM Assets. Busque reemplazos en [Prácticas recomendadas de integración de AEM y Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). Si tiene alguna consulta, [póngase en contacto con el servicio de asistencia al cliente de Adobe](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-287.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Creación de una aplicación {#create-an-application}

1. Acceda a la interfaz de la puerta de enlace de Adobe Developer iniciando sesión en [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/).

   >[!NOTE]
   >
   >Se necesitan privilegios de administrador para crear un ID de aplicación.

1. En el panel izquierdo, vaya a **[!UICONTROL Herramientas para desarrolladores]** > **[!UICONTROL Aplicaciones]** para ver una lista de aplicaciones.
1. Haga clic en **[!UICONTROL Agregar]** ![aem_assets_addcírculo_icon](assets/aem_assets_addcircle_icon.png) para crear una aplicación.
1. En el **[!UICONTROL Credenciales del cliente]** lista, seleccionar **[!UICONTROL Cuenta de servicio (JWT Assertion)]**, que es un servicio de comunicación servidor a servidor para la autenticación de servidor.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Especifique un nombre para la aplicación y una descripción opcional.
1. En el **[!UICONTROL Organización]** , seleccione la organización para la que desea sincronizar los recursos.
1. En el **[!UICONTROL Ámbito]** lista, seleccionar **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** y **[!UICONTROL cc-share]**.
1. Haga clic en **[!UICONTROL Crear]**. Un mensaje notifica que se ha creado la aplicación.

   ![Notificación de creación correcta de la aplicación para integrar AEM Assets con Adobe Creative Cloud](assets/chlimage_1-289.png)

1. Copie el **[!UICONTROL ID de aplicación]** que se genera para la nueva aplicación.

   >[!CAUTION]
   >
   >Asegúrese de que no copia el **[!UICONTROL Secreto de la aplicación]** en lugar de **[!UICONTROL ID de aplicación]**.

## Agregar una nueva configuración al Experience Cloud {#add-a-new-configuration}

1. Haga clic en el logotipo de AEM en la interfaz de usuario de la instancia local de AEM Assets y vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Cloud Services heredados]**.

1. Busque la variable **[!UICONTROL Adobe Experience Cloud]** servicio. Si no existen configuraciones, haga clic en **[!UICONTROL Configurar ahora]**. Si existen configuraciones, haga clic en **[!UICONTROL Mostrar configuraciones]** y haga clic en `+` para agregar una configuración nueva.

   >[!NOTE]
   >
   >Utilice una cuenta de Adobe ID con privilegios de administrador para la organización.

1. En el **[!UICONTROL Crear configuración]** , especifique un título y un nombre para la nueva configuración y haga clic en **[!UICONTROL Crear]**.

   ![Asigne un nombre a una nueva configuración para integrar AEM Assets y Creative Cloud](assets/cloudservices_configure_mc.png)

1. En el **[!UICONTROL URL del inquilino]** especifique la URL para AEM Assets. En el pasado, si la dirección URL se definió como `https://<tenant_id>.marketing.adobe.com`, cambie a `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Vaya a **Herramientas > Cloud Services > Servicios de nube heredados**. En Adobe Experience Cloud, haga clic en **Mostrar configuraciones**.
   1. Seleccione la configuración existente que desea editar. Edite la configuración y reemplace `marketing.adobe.com` a `experiencecloud.adobe.com`.
   1. Guarde la configuración. Pruebe los agentes de replicación MAC-sync.

1. En el **[!UICONTROL ID de cliente]** , pegue el ID de aplicación que ha copiado al final del procedimiento. [crear una aplicación](#create-an-application).

   ![Proporcione los valores de ID de aplicación necesarios para integrar AEM Assets y el Creative Cloud](assets/cloudservices_tenant_info.png)

1. En **[!UICONTROL Sincronización]** select **[!UICONTROL Habilitado]** para activar la sincronización y haga clic en **[!UICONTROL OK]**. Si selecciona **disabled**, la sincronización funciona en una sola dirección.

1. En la página de configuración, haga clic en **[!UICONTROL Mostrar clave pública]** para mostrar la clave pública generada para la instancia. También puede hacer clic en **[!UICONTROL Descargar clave pública para la puerta de enlace OAuth]** para descargar el archivo que contiene la clave pública. A continuación, abra el archivo para mostrar la clave pública.

## Habilitar sincronización {#enable-synchronization}

1. Mostrar la clave pública mediante uno de los siguientes métodos mencionados en el último paso del procedimiento [agregar una nueva configuración al Experience Cloud](#add-a-new-configuration). Haga clic en **[!UICONTROL Mostrar clave pública]**.

1. Copie la clave pública y péguela en el **[!UICONTROL Clave pública]** campo de interfaz de configuración de la aplicación que ha creado en [crear una aplicación](#create-an-application).

   ![chlimage_1-293](assets/chlimage_1-293.png)

1. Haga clic en **[!UICONTROL Actualizar]**. Sincronice los recursos con la instancia de AEM Assets ahora.

## Probar la sincronización {#test-the-synchronization}

1. Haga clic en el logotipo de AEM en la interfaz de usuario de la instancia local de AEM Assets y vaya a **[!UICONTROL Herramientas]**> **[!UICONTROL Implementación]**> **[!UICONTROL Replicación]**para localizar los perfiles de replicación creados para la sincronización.
1. En el **[!UICONTROL Replicación]** página, haga clic en **[!UICONTROL Agentes en autor]**.
1. En la lista de perfiles, haga clic en el perfil de replicación predeterminado para que su organización lo abra.
1. En el cuadro de diálogo, haga clic en **[!UICONTROL Probar conexión]**.

   ![Probar la conexión y establecer el perfil de replicación predeterminado para su organización](assets/chlimage_1-294.png)

1. Cuando se complete el resto de la replicación, compruebe si aparece un mensaje de éxito al final de los resultados de la prueba.

## Agregar usuarios al Experience Cloud {#add-users-to-experience-cloud}

1. Inicie sesión en el Experience Cloud con las credenciales del administrador.
1. Desde los carriles, vaya a **[!UICONTROL Administración]** y haga clic en **[!UICONTROL Iniciar Enterprise Dashboard]**.
1. En el carril , haga clic en **[!UICONTROL Usuarios]** para abrir el **[!UICONTROL Administración de usuarios]** página.
1. En la barra de herramientas, haga clic en **Agregar** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Agregue uno o varios usuarios para poder compartir recursos con el Creative Cloud.

   >[!NOTE]
   >
   >Solo los usuarios que agregue al Experience Cloud pueden compartir recursos de AEM Assets con el Creative Cloud.

## Intercambiar recursos entre AEM Assets y Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Inicie sesión en AEM Assets.
1. En la consola Recursos, cree una carpeta y cargue algunos recursos en ella. Por ejemplo, crear una carpeta **mc-demo** y cargue un recurso en él.
1. Seleccione la carpeta y haga clic en **Compartir** ![assets_share](assets/assets_share.png).
1. En el menú , seleccione **[!UICONTROL Adobe Experience Cloud]** y haga clic en **[!UICONTROL Compartir]**. Un mensaje notifica que la carpeta se comparte con el Experience Cloud.

   ![chlimage_1-295](assets/chlimage_1-295.png)

   >[!NOTE]
   >
   >Uso compartido de una carpeta de recursos del tipo `sling:OrderedFolder`, no es compatible en el contexto del uso compartido en Adobe Experience Cloud. Si desea compartir una carpeta, al crearla en AEM Assets, no seleccione la opción **[!UICONTROL Pedido]** .

1. Actualice la interfaz de usuario de AEM Assets. La carpeta que ha creado en la consola Recursos de la instancia local de AEM Assets se copia en la interfaz de usuario del Experience Cloud. El recurso que se carga en la carpeta en AEM Assets aparece en la copia de la carpeta en el Experience Cloud después de que el servidor de AEM lo procese.
1. También puede cargar un recurso en la copia duplicada de la carpeta en el Experience Cloud . Una vez procesado, el recurso aparece en la carpeta compartida de AEM Assets.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.
## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Prácticas recomendadas para la integración de recursos y Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)
>* [Prácticas recomendadas de uso compartido de recursos en carpetas de Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

