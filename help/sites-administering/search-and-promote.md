---
title: Integración con Adobe Search&Promote
seo-title: Integración con Adobe Search&Promote
description: Obtenga información sobre cómo integrarse con Adobe Search&Promote.
seo-description: Obtenga información sobre cómo integrarse con Adobe Search&Promote.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Integrating with Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Para llamar al servicio Adobe Search&amp;Promote desde su sitio web, realice las siguientes tareas:

1. Especifique la dirección URL de la nube.
1. Configure la conexión con el servicio Search&amp;Promote.
1. Agregue componentes de Search&amp;Promote a la [!UICONTROL barra de tareas].
1. Utilice los componentes para crear el contenido. (Consulte [Adición de funciones de Search&amp;Promote a una página](/help/sites-authoring/search-and-promote.md)Web).
1. Agregue letreros a las páginas. Las imágenes de pancarta son sensibles a los datos de Search&amp;Promote.
1. Genere un mapa del sitio para que lo consuma el servicio Search&amp;Promote.

>[!NOTE]
>
>Si utiliza Search&amp;Promote con una configuración proxy personalizada, debe configurar ambas configuraciones proxy del cliente HTTP, ya que algunas funcionalidades de AEM están usando las API 3.x y otras las API 4.x:
>
>* 3.x está configurado con [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x está configurado con [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



## Cambio de la dirección URL del servicio de Search&amp;Promote {#changing-the-search-promote-service-url}

La dirección URL predeterminada configurada para el servicio Search&amp;Promote es `https://searchandpromote.omniture.com/px/`. Para utilizar un servicio diferente, utilice la consola OSGi para especificar una dirección URL diferente.

**Para cambiar la dirección URL** del servicio de Search&amp;Promote:

1. Abra la consola [!UICONTROL OSGi] y toque la ficha **[!UICONTROL Configuración]** . ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Haga clic en el elemento Configuración **[!UICONTROL de]** Day CQ Search&amp;Promote.
1. En el campo de texto URI **[!UICONTROL de servidor]** remoto, introduzca la URL y, a continuación, toque **[!UICONTROL Guardar]**.

## Configuración de la conexión con Search&amp;Promote {#configuring-the-connection-to-search-promote}

Configure una o más conexiones a Search&amp;Promote para que las páginas Web puedan interactuar con el servicio. Para conectarse, necesita la identificación de miembros y el número de cuenta de su cuenta de Search&amp;Promote.

**Para configurar la conexión con Search&amp;Promote**:

1. En el icono **[!UICONTROL Herramientas]** > **[!UICONTROL Implementación]**, seleccione **[!UICONTROL Cloud Services]**.

   Esto lo lleva al panel de servicios de nube. Si se encuentra en un equipo local, la dirección URL del tablero tendrá este aspecto:

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. En la página Servicios [!UICONTROL de] nube, toque el vínculo de **[!UICONTROL Adobe Search&amp;Promote]** o el icono de **[!UICONTROL Search&amp;Promote]** .

1. Si es la primera vez que configura Adobe Search&amp;Promote, toque **[!UICONTROL Configurar ahora]** para abrir el panel [!UICONTROL Crear configuración] .

   Si desea obtener más información sobre Search&amp;Promote, haga clic en **[!UICONTROL Más]** información.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. Escriba un **[!UICONTROL Título]** reconocible para los autores de la página, escriba un **[!UICONTROL Nombre]**&#x200B;único y, a continuación, toque **[!UICONTROL Crear]**.

   Además, la configuración recién creada aparece debajo de Configuraciones **** disponibles en el elemento de lista del panel **[!UICONTROL Servicios de]** nube de Adobe Search&amp;Promote.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. En el cuadro de diálogo [!UICONTROL Editar componente] , agregue lo siguiente a los campos:

   * **[!UICONTROL ID de miembro]**
   * **[!UICONTROL Número de cuenta]**
   >[!NOTE]
   >
   >Para obtener esta información usted mismo, inicie sesión en lo siguiente:
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >con sus credenciales válidas de Search&amp;Promote (correo electrónico/contraseña).
   >
   >Observe la dirección URL en la barra de direcciones del explorador. Debería tener un aspecto similar al siguiente:
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >Donde **XXXXXXXX** corresponde a su identificación **[!UICONTROL de]** Miembro y **[!UICONTROL spYYYYYY]** corresponde a su número de cuenta.

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   Cuando aparezca el mensaje de éxito de la conexión, toque **[!UICONTROL Aceptar]**.

   (Tras la conexión, el texto del botón cambia a **[!UICONTROL Volver a conectar con Search&amp;Promote]**).

1. Toque **[!UICONTROL Aceptar]**. Aparece la página Configuración de Search&amp;Promote para la configuración que acaba de crear.

## Configuración del centro de datos {#configuring-the-data-center}

Si su cuenta de Search&amp;Promote está en Asia o Europa, debe cambiar el centro de datos predeterminado para que apunte al correcto (el centro de datos predeterminado es para cuentas de Norteamérica).

**Para configurar el centro** de datos:

1. Vaya a la consola web en `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. Según la ubicación del servidor, cambie el URI a uno de los siguientes:

   * Norteamérica: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Toque **[!UICONTROL Guardar]**.

## Adición de componentes de Search&amp;Promote a la barra de tareas {#adding-search-promote-components-to-sidekick}

En el modo [!UICONTROL Diseño] , edite un componente **[!UICONTROL par]** para permitir los componentes de Search&amp;Promote en la [!UICONTROL barra de tareas]. (See the [Components](/help/sites-developing/components.md) documentation for more information.)

Para obtener información sobre el uso de los componentes, consulte [Adición de funciones de Search&amp;Promote a una página](/help/sites-authoring/search-and-promote.md)Web.

## Especificación del servicio Search&amp;Promote que utilizan las páginas {#specifying-the-search-promote-service-that-your-pages-use}

Configure las páginas web para que utilicen un servicio Search&amp;Promote específico. Los componentes de Search&amp;Promote utilizan automáticamente el servicio de la página de host.

Al configurar las propiedades de Search&amp;Promote para una página, todas las páginas secundarias heredan la configuración. Si es necesario, puede configurar las páginas secundarias para anular la configuración heredada.

>[!NOTE]
>
>La conexión de servicio ya debe estar configurada. Consulte [Configuración de la conexión a Search&amp;Promote](#configuring-the-connection-to-search-promote).

1. Abra el cuadro de diálogo Propiedades **[!UICONTROL de la página]** . Por ejemplo, en la página **[!UICONTROL Sitios]** web, haga clic con el botón secundario en la página y haga clic en **[!UICONTROL Propiedades]**.

1. Haga clic en la ficha Servicios **[!UICONTROL de]** nube.

1. Para desactivar la herencia de las configuraciones de servicios en la nube desde una página principal, haga clic en el icono de cerrojo situado junto a la ruta de herencia.

   ![sandpinheritpadlock](assets/sandpinheritpadlock.png)

1. Haga clic en **[!UICONTROL Agregar servicio]**, seleccione **[!UICONTROL Adobe Search&amp;Promote]** y, a continuación, haga clic en **[!UICONTROL Aceptar]**.

1. Seleccione la configuración de conexión de su cuenta de Search&amp;Promote y haga clic en **[!UICONTROL Aceptar]**.

## Product Feed {#product-feed}

La integración de Search&amp;Promote permite hacer lo siguiente:

* Utilice la API de [!UICONTROL comercio] electrónico, independientemente de la estructura de repositorio subyacente y la plataforma de comercio.
* Aproveche la función [!UICONTROL Conector] de índice de Search&amp;Promote para proporcionar una fuente de producto en formato XML.
* Aproveche la función de control  remoto de Search&amp;Promote para realizar solicitudes programadas o bajo demanda de la fuente de productos.
* Generación de fuentes para distintas cuentas de Search&amp;Promote, configuradas como configuraciones de servicios en la nube.

Para obtener más información, consulte [Alimentación](/help/sites-administering/product-feed.md)de productos.
