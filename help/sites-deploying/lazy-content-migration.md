---
title: Migración de contenido diferido
seo-title: Lazy Content Migration
description: Obtenga información sobre la migración de contenido diferido en AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 7%

---

# Migración de contenido diferido{#lazy-content-migration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para la compatibilidad con versiones anteriores, el contenido y la configuración en **/etc** y **/content** a partir de AEM 6.3 no se tocará ni transformará inmediatamente con la actualización. Esto se hace para garantizar que las dependencias de las aplicaciones de los clientes en esas estructuras permanezcan intactas. La funcionalidad relacionada con estas estructuras de contenido sigue siendo la misma aunque el contenido de una versión predeterminada AEM 6.4 se alojaría en otro lugar.

Aunque no todas esas ubicaciones se pueden transformar automáticamente, hay algunas que se retrasan `CodeUpgradeTasks` también se denomina Migración de contenido diferido. Esto permite a los clientes almacenar en déclencheur esas transformaciones automáticas reiniciando la instancia con esta propiedad del sistema:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Esto hará que la variable `CodeUpgradeTasks` que se ejecutará durante la migración.

Aunque el objetivo es una ejecución eficiente, este proceso de actualización es sincrónico y, por lo tanto, incluye un tiempo de inactividad en función de la cantidad de contenido que debe procesarse. Se recomienda evaluar los tiempos de ejecución en un entorno de ensayo antes de un sistema de producción para planificar una ventana de mantenimiento adecuada.

Como esto generalmente también requiere ajustar la aplicación, esta actividad debe realizarse junto con la implementación de la aplicación correspondiente.

A continuación se muestra la lista completa de `CodeUpgradeTasks` introducido en la versión 6.4:

| **Nombre** | **Relevante para versiones de AEM anteriores a** | **Tipo de migración** | **Detalles** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Inmediato |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Inmediato | Detecta todo `LiveRelationShips` from `VersionStorage` que se han eliminado y agregar la propiedad de exclusión a parent |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Inmediato | Reestructura cloudservices para una configuración segura de forma predeterminada |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Inmediato | Quita la vinculación basada en propiedades de **/content** a **/conf** (reemplazado por el mecanismo OSGi), genera la configuración OSGi correspondiente |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Inmediato | Debido a que merge_preserve gestiona el seguro de forma predeterminada, deniega las anulaciones de reglas dados permisos que llevan a la necesidad de reordenar al actualizar |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Inmediato | Detecta los componentes que utilizan el widget Html5SmartFile, busca los usos del componente en el contenido y reestructura la persistencia, moviendo efectivamente el binario un nivel hacia abajo y no almacenarlo en el nivel de componente. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Inmediato | Mueve los proyectos de estilo antiguo de **/etc/projects** a **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Inmediato | Introduce una capa de contenedor en la jerarquía (Áreas) y ajusta las referencias. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Inmediato | Define nombres de ubicación fijos para los componentes de destino. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Inmediato | Transformación compleja de los modelos de flujo de trabajo anteriores a la versión 6.2 de estructuras, instancias, notificaciones y, a continuación, combinación desde la ubicación de copia de seguridad desde **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Inmediato | Mueve recursos, esquemas de metadatos personalizados y perfiles de procesamiento de **/apps** a **/conf** y traduce los formularios de esquema de metadatos y perfiles de metadatos de coral2 a coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Inmediato | Mueve los recursos y las facetas de búsqueda personalizadas de **/apps** a **/conf** y traduce los formularios de esquema de metadatos y perfiles de metadatos de coral2 a coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Inmediato | Actualiza la Bandeja de entradaElementos para ordenar los elementos de la bandeja de entrada (ajustando los metadatos para una ordenación eficiente) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Inmediato | Ajusta la propiedad metadataSchema en la carpeta reemplazando las rutas relativas a **/conf** en lugar de **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Inmediato | Ajuste de la estructura de navegación |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Inmediato | Mueve las configuraciones personalizadas para los paneles de monitorización de **/libs** y **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Inmediato | Traduce la propiedad processingProfile (utilizada hasta la versión 6.1) en Assets para que coincida con la estructura 6.3 y posteriores. También ajusta las rutas relativas del perfil a **/conf** en lugar de **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Inmediato | Tarea de actualización que elimina las entradas de menú del CRXDE Lite y la consola web obsoletas en caso de una actualización. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Retrasado | Moviendo configuraciones de nube SRP, configuraciones de palabras clave de la comunidad, limpia **/etc/social** y **/etc/enablement** (las referencias y los datos deben ajustarse cuando se ejecute la migración diferida; ninguna parte de la aplicación debe depender de esta estructura). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Retrasado | Limpia **/etc/cloudsettings** (que contiene la configuración de ContextHub). La configuración se migra automáticamente en el primer acceso. En caso de que se inicie la migración de contenido diferido junto con la actualización de este contenido en **/etc/cloudsettings** debe conservarse mediante paquete antes de la actualización y reinstalarse para que se inicie la transformación implícita, junto con una desinstalación posterior del paquete después de la finalización. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Retrasado | Ajusta la estructura de título heredada al título en el nodo de perfil de usuario. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Retrasado | Migrar contenido comercial de **/etc/commerce** a **/var/commerce**. Durante la migración del contenido se mueve y las referencias al contenido movido se actualizan para reflejar la nueva ubicación. |
