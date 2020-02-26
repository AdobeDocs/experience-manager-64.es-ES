---
title: Actualización a AEM 6.4 Forms
seo-title: Actualización a AEM 6.4 Forms
description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
seo-description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: d2657bc364b7a814fac9228afdec60f96faaf175

---


# Actualización a AEM 6.4 Forms en OSGi {#upgrade-to-aem-forms-osgi}

Utilice una de las siguientes rutas de actualización, según corresponda para su entorno.

## AEM 6.2 Forms o AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Puede realizar una actualización directa de AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms. Haga lo siguiente:

1. Actualice la instancia de AEM existente a AEM 6.4. Los pasos se enumeran a continuación:

   1. Instale el Service Pack y los parches más recientes para AEM 6.2 Forms o AEM 6.3 Forms. Para obtener más información, consulte:

      * [Notas de la versión de AEM 6.2](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
      * [Notas de la versión de AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [AEM Sustenance Hub](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)
   1. Prepare la instancia de origen para la actualización. Para ver los pasos detallados, consulte [Actualización a AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Descargue [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Solo instalaciones basadas en Unix/Linux)** Si utiliza UNIX o Linux como sistema operativo subyacente, abra la ventana de terminal, navegue a la carpeta que contenga crx-quickstart y ejecute el siguiente comando:

      `chmod -R 755 ../crx-quickstart`

   1. Actualice su instancia de AEM a AEM 6.3. Para obtener instrucciones paso a paso, consulte [Actualización a AEM 6.4](/help/sites-deploying/upgrade.md).

      Antes de continuar con los siguientes pasos, espere hasta que los mensajes ServiceEvent REGISTERED y ServiceEvent UNREGISTER dejen de aparecer en el archivo &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Una vez que el servidor está en funcionamiento, algunos paquetes de AEM Forms permanecen en estado de instalación. El número de paquetes puede variar para cada instalación. Puede ignorar con seguridad el estado de estos paquetes. Los paquetes están enumerados en `https://[server]:[port]/system/console/`.


1. Instale el paquete de complementos de AEM Forms.  Los pasos se enumeran a continuación:

   1. Inicie sesión en el servidor de AEM como administrador y abra el recurso compartido de paquetes. La dirección URL predeterminada del recurso compartido de paquetes es `https://[server]:[port]/crx/packageshare`.
   1. En el uso compartido de paquetes, busque paquetes **[!UICONTROL de AEM 6.4 Forms, haga clic en el paquete aplicable a su sistema operativo y, a continuación, haga clic en]** Descargar ****. Lea y acepte el contrato de licencia y haga clic en **[!UICONTROL Aceptar]**. Se inicia la descarga. Una vez descargado, la palabra **[!UICONTROL Descargado]** aparece junto al paquete.

      También puede utilizar los hipervínculos enumerados en las versiones [de](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) AEM Forms para descargar manualmente un paquete.

   1. Una vez completada la descarga, haga clic en **[!UICONTROL Descargado]**. Se le redirige al administrador de paquetes. En el administrador de paquetes, busque el paquete descargado y haga clic en **[!UICONTROL Instalar]**.

      Si descarga manualmente el paquete mediante el vínculo directo que aparece en las versiones [de](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)AEM Forms, abra el Administrador de paquetes de AEM, haga clic en **[!UICONTROL Cargar paquete]**, seleccione el paquete descargado y haga clic en Cargar. Después de cargar el paquete, haga clic en el nombre del paquete y, a continuación, en **[!UICONTROL Instalar]**.

      >[!NOTE]
      >
      >Después de instalar el paquete, se le pedirá que reinicie la instancia de AEM. **No detenga inmediatamente el servidor.** Antes de detener el servidor de AEM Forms, espere hasta que los mensajes ServiceEvent REGISTRARED y ServiceEvent UNREGISTERED dejen de aparecer en el archivo &lt;crx-repository>/error.log y el registro sea estable. Además, algunos paquetes pueden permanecer en el estado de instalación. Puede ignorar con seguridad el estado de estos paquetes.

   1. Detenga la instancia de AEM y elimine los siguientes archivos:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Inicie la instancia de AEM.


1. Realizar actividades posteriores a la instalación.

   * **Ejecutar la utilidad de migración**

      La utilidad de migración hace que los formularios adaptables y los recursos de gestión de correspondencia de versiones anteriores sean compatibles con los formularios de AEM 6.4. Puede descargar la utilidad desde el recurso compartido de paquetes de AEM. Para obtener información paso a paso sobre cómo configurar y utilizar la utilidad de migración, consulte Utilidad [de](/help/forms/using/migration-utility.md)migración.

      Si utiliza [Sample para integrar borradores y componentes](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) de envíos con la base de datos y actualizar desde una versión anterior, ejecute las siguientes consultas SQL después de realizar la actualización:

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

      Si tenía Adobe Sign configurado en la versión anterior de AEM Forms, vuelva a configurar Adobe Sign desde los servicios de AEM Cloud. Para obtener más información, consulte [Integración de Adobe Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Si solo se actualiza desde AEM 6.2 Forms o versiones anteriores) Vuelva a configurar los análisis y los informes**

      En AEM 6.4 Forms, no están disponibles las variables de tráfico para el origen y el evento de éxito para impresión. Por lo tanto, al actualizar desde AEM 6.2 Forms o versiones anteriores, AEM Forms deja de enviar datos al servidor de Adobe Analytics y los informes de análisis para formularios adaptables no están disponibles. Además, AEM 6.4 Forms introduce la variable de tráfico para la versión del análisis de formularios y el evento de éxito para la cantidad de tiempo empleado en un campo. Por lo tanto, vuelva a configurar los análisis y los informes para su entorno de AEM Forms. Para ver los pasos detallados, consulte [Configuración de análisis e informes](/help/forms/using/configure-analytics-forms-documents.md).

1. Compruebe que el servidor se ha actualizado correctamente, que todos los datos también se han migrado correctamente y que puede funcionar con normalidad.

   * **** Compruebe el estado de los paquetes: Asegúrese de que todos los paquetes están en estado activo.
   * **** Verificar replicación y replicación inversa: Publique, rellene y envíe algunos formularios migrados. Compruebe también los datos enviados.
   * **** Verificar el acceso a las interfaces de usuario de administrador y desarrollador: Inicie sesión en una instancia de AEM desde una cuenta de administrador y compruebe que tiene acceso a las siguientes direcciones URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a formularios AEM 6.4, utilice las rutas cambiadas para la personalización que vuelva a crear. Para obtener la lista completa de las rutas modificadas, consulte Reestructuración de [repositorios de formularios en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms y AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

No está disponible la ruta de actualización directa de los formularios **de** AEM 6.0 y **AEM 6.1 Forms** a AEM 6.4 Forms. Realice una [actualización intermedia a AEM 6.2 Forms](/help/forms/using/upgrade.md) o [actualice a AEM 6.3 Forms](/help/forms/using/upgrade.md) y, a continuación, actualice AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms.
