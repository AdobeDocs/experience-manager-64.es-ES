---
title: Actualizar a AEM 6.4 Forms
seo-title: Actualizar a AEM 6.4 Forms
description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
seo-description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 9%

---

# Actualización a AEM 6.4 Forms en OSGi {#upgrade-to-aem-forms-osgi}

Utilice una de las siguientes rutas de actualización, según corresponda para su entorno.

## AEM 6.2 Forms o AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Puede realizar una actualización directa de AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms. Haga lo siguiente:

1. Actualice la instancia de AEM existente a AEM 6.4. Los pasos se enumeran a continuación:

   1. Instale el Service Pack y los parches más recientes para AEM 6.2 Forms o AEM 6.3 Forms. Para obtener más información, consulte:

      * [Notas de la versión de AEM 6.2](https://helpx.adobe.com/es/experience-manager/6-2/release-notes.html)
      * [Notas de la versión de AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [Centro de soporte AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=es)
   1. Prepare la instancia de origen para la actualización. Para ver los pasos detallados, consulte [Actualización a AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Descargue el [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Solo instalaciones basadas en Unix/Linux)**  Si está utilizando UNIX o Linux como sistema operativo subyacente, abra la ventana de terminal, vaya a la carpeta que contiene crx-quickstart y ejecute el siguiente comando:

      `chmod -R 755 ../crx-quickstart`

   1. Actualice la instancia de AEM a AEM 6.3. Para obtener instrucciones paso a paso, consulte [Actualización a AEM 6.4](/help/sites-deploying/upgrade.md).

      Antes de continuar con los siguientes pasos, espere hasta que los mensajes ServiceEvent REGISTER y ServiceEvent UNREGISTER dejen de aparecer en el archivo &lt;crx-repository>/error.log .

      >[!NOTE]
      >
      >Una vez que el servidor está en funcionamiento, algunos paquetes de AEM Forms permanecen en estado de instalación. El número de paquetes puede variar para cada instalación. Puede ignorar de forma segura el estado de estos paquetes. Los paquetes se enumeran en `https://[server]:[port]/system/console/`.


1. Instale el paquete de complementos de AEM Forms. Los pasos se enumeran a continuación:

   1. Abra [Distribución de software](https://experience.adobe.com/downloads). Necesitará un Adobe ID para iniciar sesión en la distribución de software.
   1. Pulse **[!UICONTROL Adobe Experience Manager]**, disponible en el menú del encabezado.
   1. En la sección **[!UICONTROL Filters]**:
      1. Seleccione **[!UICONTROL Forms]** en la lista desplegable **[!UICONTROL Solución]**.
      1. Seleccione la versión y el tipo del paquete. También puede utilizar la opción **[!UICONTROL Search Downloads]** para filtrar los resultados.
   1. Pulse el nombre del paquete aplicable a su sistema operativo, seleccione **[!UICONTROL Aceptar términos EULA]** y pulse **[!UICONTROL Descargar]**.
   1. Abra [Administrador de paquetes](https://docs.adobe.com/content/help/es-ES/experience-manager-65/administering/contentmanagement/package-manager.html) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.
   1. Seleccione el paquete y haga clic en **[!UICONTROL Install]**.

      También puede descargar el paquete utilizando el enlace directo que aparece en el artículo [AEM Forms releases](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html).

      >[!NOTE]
      >
      >Una vez instalado el paquete, se le pedirá que reinicie la instancia de AEM. **No detenga el servidor inmediatamente.** Antes de detener el servidor de AEM Forms, espere hasta que los mensajes ServiceEvent REGISTER y ServiceEvent UNREGISTER dejen de aparecer en el archivo  &lt;crx-repository>/error.log y el registro sea estable. Tenga en cuenta también que algunos paquetes pueden permanecer en el estado instalado. Puede ignorar de forma segura el estado de estos paquetes.

   1. Detenga la instancia de AEM y elimine los siguientes archivos:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Inicie la instancia de AEM.


1. Realizar actividades posteriores a la instalación.

   * **Ejecución de la utilidad de migración**

      La utilidad de migración hace que los formularios adaptables y los activos de gestión de correspondencia de versiones anteriores sean compatibles con los formularios AEM 6.4. Puede descargar la utilidad desde AEM Distribución de software. Para obtener información paso a paso sobre cómo configurar y utilizar la utilidad de migración, consulte [utilidad de migración](/help/forms/using/migration-utility.md).

      Si está utilizando [Sample para integrar el componente ](integrate-draft-submission-database.md) de borradores y envíos con la base de datos y actualizar desde una versión anterior, ejecute las siguientes consultas SQL después de realizar la actualización:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Si solo se actualiza desde AEM 6.2 Forms o versiones anteriores) Vuelva a configurar Adobe Sign**

      Si tenía Adobe Sign configurado en la versión anterior de AEM Forms, vuelva a configurar Adobe Sign desde AEM Cloud Services. Para obtener más información, consulte [Integrar Adobe Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Si solo se actualiza desde AEM 6.2 Forms o versiones anteriores) Vuelva a configurar los análisis y los informes**

      En AEM 6.4 Forms, la variable de tráfico para la fuente y el evento de éxito para la impresión no están disponibles. Por lo tanto, al actualizar desde AEM 6.2 Forms o versiones anteriores, AEM Forms deja de enviar datos al servidor de Adobe Analytics y los informes de análisis para los formularios adaptables no están disponibles. Además, AEM 6.4 Forms introduce una variable de tráfico para la versión del análisis de formularios y el evento de éxito para la cantidad de tiempo invertido en un campo. Por lo tanto, vuelva a configurar los análisis y los informes para su entorno de AEM Forms. Para ver los pasos detallados, consulte [Configuración de análisis e informes](/help/forms/using/configure-analytics-forms-documents.md).

1. Compruebe que el servidor se ha actualizado correctamente, que todos los datos también se han migrado correctamente y que puede funcionar con normalidad.

   * **Compruebe el estado de los paquetes:** asegúrese de que todos los paquetes están en estado activo.
   * **Verificar la replicación y la replicación inversa:** publique, rellene y envíe algunos formularios migrados. Compruebe también los datos enviados.
   * **Verifique el acceso a las interfaces de usuario de administrador y desarrollador:** inicie sesión en AEM instancia desde una cuenta de administrador y verifique que tiene acceso a las siguientes direcciones URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a AEM formularios 6.4, utilice las rutas modificadas para la personalización que cree de nuevo. Para obtener la lista completa de las rutas cambiadas, consulte [Reestructuración del repositorio de Forms en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms y AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

La ruta de actualización directa de **AEM 6.0 Forms** y **AEM 6.1 Forms** a AEM 6.4 Forms no está disponible. Realice una [actualización intermedia a AEM 6.2 Forms](/help/forms/using/upgrade.md) o [actualización a AEM 6.3 Forms](/help/forms/using/upgrade.md) y, a continuación, actualice de AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms.
