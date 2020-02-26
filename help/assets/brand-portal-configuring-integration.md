---
title: Configuración de la integración de AEM Assets con Brand Portal
description: 'Descubra cómo integrar Recursos AEM con Brand Portal para publicar recursos y colecciones en Brand Portal. '
contentOwner: VG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Configure AEM Assets integration with Brand Portal {#configure-aem-assets-integration-with-brand-portal}

Descubra cómo integrar Recursos AEM con Brand Portal para publicar recursos y colecciones en Brand Portal.

Si es cliente de Adobe Experience Manager (AEM) Assets Brand Portal, puede integrar Recursos AEM con Brand Portal para permitir la publicación de recursos en Brand Portal. Puede configurar esta integración mediante la interfaz Adobe.io.

> [!Note]
>
>Adobe recomienda actualizar a AEM 6.4.1.0 o posterior para garantizar que AEM Assets Brand Portal esté integrado con Recursos AEM. Una limitación en AEM 6.4 produce un error al configurar la integración con Brand Portal y la replicación falla.

En primer lugar, cree una aplicación, que incluya un mecanismo de autenticación, en la puerta de enlace pública de Marketing Cloud. A continuación, cree un perfil en la instancia de Recursos AEM con el ID de la aplicación que obtiene de la puerta de enlace.

Utilice esta configuración para publicar recursos de Recursos AEM en Brand Portal. En segundo plano, el servidor de AEM autentica su perfil con la puerta de enlace y, a continuación, integra Recursos AEM con Brand Portal.

>[!NOTE]
>
>La interfaz de usuario para configurar integraciones de autenticación está alojada en [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/), que antes estaba alojada en [https://marketing.adobe.com/developer/](https://marketing.adobe.com/developer/).

## Crear aplicación JWT {#create-jwt-application}

1. Inicie sesión en [https://legacy-oauth.cloud.adobe.io/](https://legacy-oauth.cloud.adobe.io/) con su Adobe ID. Llega a la página Aplicaciones  JWT.

   >[!NOTE]
   >
   >Solo puede crear un ID de aplicación si es el administrador del sistema de su organización. Inquilino es el nombre técnico de su organización que está registrada en Adobe Marketing Cloud.

2. Seleccione **[!UICONTROL Agregar aplicación]** para crear una aplicación.
3. Especifique un nombre **[!UICONTROL de aplicación]** y una **[!UICONTROL descripción]** opcional.
4. En la lista **[!UICONTROL Organización]** , seleccione la organización para la que desea sincronizar los recursos.
5. En la lista **[!UICONTROL Ámbito]** , seleccione **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** y **[!UICONTROL cc-share]**.
6. Toque o haga clic en **[!UICONTROL Agregar]**. Se crea una aplicación de servicio JWT. Puede editar la aplicación y Guardar.
7. Copie el ID de aplicación que se genera para la nueva aplicación.

   >[!NOTE]
   >
   >Asegúrese de no copiar inadvertidamente el secreto de la aplicación en lugar del ID de la aplicación.

## Crear una nueva configuración de nube {#create-a-new-cloud-configuration}

1. En la página **[!UICONTROL Navegación]** de la instancia local de Recursos AEM, toque o haga clic en el icono **[!UICONTROL Herramientas]** de la izquierda.

   ![chlimage_1-252](assets/chlimage_1-252.png)

2. Navigate to **[!UICONTROL Cloud Services > Legacy Cloud Services]**.

   ![cloudservices](assets/cloudservices.png)

3. En la página Servicios [!UICONTROL de] Cloud, busque el servicio **[!UICONTROL Assets Brand Portal]** en **[!UICONTROL Adobe Experience Cloud]**.

   ![bpcloudservices](assets/bpcloudservices.png)

4. Toque o haga clic en el vínculo **[!UICONTROL Configurar ahora]** debajo del servicio para mostrar el cuadro de diálogo [Crear configuración] .
5. En el cuadro de diálogo [!UICONTROL Crear configuración] , especifique un título y un nombre para la nueva configuración y toque o haga clic en **[!UICONTROL Crear]**.

   ![bp-config](assets/bp-config.png)

6. En el cuadro de diálogo Replicación [!UICONTROL de Brand Portal de Recursos] AEM, especifique la dirección URL de su organización en el campo URL [!UICONTROL del] inquilino.
7. En el campo ID de [!UICONTROL cliente] , pegue el ID de aplicación que ha copiado al final del procedimiento [Crear una aplicación](#create-jwt-application). Haga clic en **[!UICONTROL Aceptar]**.

   ![public-folder-publish](assets/public-folder-publish.png)

8. Para que los recursos (publicados desde AEM) estén disponibles para los usuarios generales de Brand Portal, active la casilla de verificación Publicación **[!UICONTROL de carpetas]** públicas.

   >[!NOTE]
   >
   >La opción para activar Publicación **[!UICONTROL de carpetas]** públicas está disponible en AEM 6.3.2.1 y versiones posteriores.

9. En la página Configuración [!UICONTROL de] Brand Portal, toque o haga clic en **[!UICONTROL Mostrar clave]** pública para mostrar la clave pública generada para su instancia.

   ![display-public-key](assets/display-public-key.png)

   Como alternativa, haga clic en **[!UICONTROL Descargar clave pública para OAuth Gateway]** para descargar el archivo que contiene la clave pública. A continuación, abra el archivo para mostrar la clave pública.

## Habilitar la integración {#enable-integration}

1. Muestre la clave pública utilizando uno de los siguientes métodos mencionados en el último paso del procedimiento [Agregue una nueva configuración a Marketing Cloud](#create-a-new-cloud-configuration).

   * Haga clic en el botón **[!UICONTROL Mostrar clave]** pública para mostrar la clave.
   * Abra el archivo descargado que contiene la clave.

2. Abra la interfaz de Marketing Cloud Developer Connection y haga clic en la aplicación que ha creado en [Crear una aplicación](#create-jwt-application).
3. Pegue la clave pública en el campo Clave **[!UICONTROL pública]** de la interfaz de configuración
4. Tap/click **[!UICONTROL Save]**. Un mensaje confirma que la aplicación se ha actualizado.

## Probar la integración {#test-the-integration}

1. En la página **[!UICONTROL Navegación]** de la instancia local de Recursos AEM, haga clic en el icono **[!UICONTROL Herramientas]** de la izquierda.

   ![chlimage_1-253](assets/chlimage_1-253.png)

2. Vaya a **[!UICONTROL Implementación > Replicación]**.

   ![implementación, replicación](assets/deploymentreplication.png)

3. En la página [!UICONTROL Replicación] , toque o haga clic en **[!UICONTROL Agentes en el autor]**.

   ![agent_on_author](assets/agents_on_author.png)

4. Para verificar la conexión entre AEM Author y Brand Portal, abra cualquiera de los cuatro agentes de replicación y haga clic en **[!UICONTROL Probar conexión]**.

   >[!NOTE]
   >
   >Los agentes de replicación trabajan en paralelo y comparten la distribución del trabajo por igual, aumentando así la velocidad de publicación en cuatro veces la velocidad original. Una vez configurado el servicio en la nube, no se requiere una configuración adicional para habilitar los agentes de replicación activados de forma predeterminada para habilitar la publicación en paralelo de varios recursos.

   >[!NOTE]
   >
   >Evite desactivar cualquiera de los agentes de replicación, ya que puede provocar errores en la replicación de algunos de los recursos.

   ![aem_assets_paralelpublishing](assets/aem_assets_parallelpublishing.png)

5. Observe la parte inferior de los resultados de la prueba para verificar que la replicación se realizó correctamente.

   ![Replication_success](assets/replication_succeeded.png)

Después de que la replicación se realice correctamente, puede publicar recursos, carpetas y colecciones en Brand Portal. Para obtener más información, consulte:

* [Publicación de recursos y carpetas en Brand Portal](brand-portal-publish-folder.md)
* [Publicar colecciones en Brand Portal](brand-portal-publish-collection.md)

## Publish assets to Brand Portal {#publish-assets-to-brand-portal}

Después de que la replicación se realice correctamente, puede publicar recursos, carpetas y colecciones en Brand Portal. Para publicar recursos en Brand Portal, siga estos pasos:

>[!NOTE]
>
>Adobe recomienda la publicación escalonada, preferiblemente durante las horas no pico, para que el autor de AEM no ocupe recursos excesivos.

1. Desde la consola Recursos, pase el ratón sobre los recursos deseados y seleccione la opción **[!UICONTROL Publicar]** en las acciones rápidas.

   También puede seleccionar los recursos que desea publicar en Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Para publicar los recursos en Brand Portal, hay dos opciones disponibles:
   * [Publicación inmediata de recursos](#publish-now)
   * [Publicar recursos más tarde](#publish-later)

### Publicar recursos ahora {#publish-now}

Para publicar los recursos seleccionados en Brand Portal, realice una de las acciones siguientes:

* En la barra de herramientas, seleccione **[!UICONTROL Publicación]** rápida. A continuación, en el menú, seleccione **[!UICONTROL Publicar en Brand Portal]**.

* En la barra de herramientas, seleccione **[!UICONTROL Administrar publicación]**.

   1. A continuación, en la **[!UICONTROL acción]** , seleccione **[!UICONTROL Publicar en Brand Portal]** y, en **[!UICONTROL Programación]** , seleccione **[!UICONTROL Ahora]**. Tap/ click **[!UICONTROL Next].**

   2. En **[!UICONTROL Ámbito]**, confirme la selección y toque o haga clic en **[!UICONTROL Publicar en Brand Portal]**.

Aparece un mensaje que indica que los recursos se han puesto en cola para su publicación en Brand Portal. Inicie sesión en la interfaz de Brand Portal para ver los recursos publicados.

### Publicar recursos más tarde {#publish-later}

Para programar la publicación de recursos en Brand Portal para una fecha u hora posterior:

1. Una vez que haya seleccionado los recursos o las carpetas que desea publicar, seleccione **[!UICONTROL Administrar publicación]** en la barra de herramientas de la parte superior.
2. En la página **[!UICONTROL Administrar publicación]** , seleccione **[!UICONTROL Publicar en Brand Portal]** en **[!UICONTROL Acción]** y seleccione **[!UICONTROL Más adelante]** en **[!UICONTROL Programación]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Seleccione una fecha **[!UICONTROL de]** activación y especifique la hora. Tap/ click **[!UICONTROL Next]**.
4. Seleccione una fecha **[!UICONTROL de]** activación y especifique la hora. Tap/ click **[!UICONTROL Next]**.
5. Especifique un título de flujo de trabajo en **[!UICONTROL Flujos de trabajo]**. Toque o haga clic en **[!UICONTROL Publicar posteriormente]**.

   ![publishworkflow](assets/publishworkflow.png)

Ahora, inicie sesión en Brand Portal para ver si los recursos publicados están disponibles en la interfaz de Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
