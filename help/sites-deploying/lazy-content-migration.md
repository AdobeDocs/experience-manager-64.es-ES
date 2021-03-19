---
title: Migración de contenido diferido
seo-title: Migración de contenido diferido
description: Obtenga información sobre la migración de contenido diferido en AEM 6.4.
seo-description: Obtenga información sobre la migración de contenido diferido en AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Actualización
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 6%

---


# Migración de contenido diferido{#lazy-content-migration}

En aras de la compatibilidad con versiones anteriores, el contenido y la configuración de **/etc** y **/content** que empiecen por AEM 6.3 no se tocará ni transformará inmediatamente con la actualización. Esto se hace para garantizar que las dependencias de las aplicaciones de los clientes en esas estructuras permanezcan intactas. La funcionalidad relacionada con estas estructuras de contenido sigue siendo la misma aunque el contenido de una versión predeterminada AEM 6.4 se alojaría en otro lugar.

Aunque no todas esas ubicaciones se pueden transformar automáticamente, también se hace referencia a algunas `CodeUpgradeTasks` retrasadas como Migración de contenido diferida. Esto permite a los clientes almacenar en déclencheur esas transformaciones automáticas reiniciando la instancia con esta propiedad del sistema:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Esto hará que el `CodeUpgradeTasks` se ejecute durante la migración.

Aunque el objetivo es una ejecución eficiente, este proceso de actualización es sincrónico y, por lo tanto, incluye un tiempo de inactividad en función de la cantidad de contenido que debe procesarse. Se recomienda evaluar los tiempos de ejecución en un entorno de ensayo antes de un sistema de producción para planificar una ventana de mantenimiento adecuada.

Como esto generalmente también requiere ajustar la aplicación, esta actividad debe realizarse junto con la implementación de la aplicación correspondiente.

A continuación se muestra la lista completa de `CodeUpgradeTasks` introducida en la versión 6.4:

| **Nombre** | **Relevante para versiones de AEM anteriores a** | **Tipo de migración** | **Detalles** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5=&quot;&quot;> | Inmediato |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Inmediato | Detecta todos los `LiveRelationShips` de `VersionStorage` que se han eliminado y agrega la propiedad de exclusión a parent |
| `Cq61CloudServicesContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Reestructura cloudservices para una configuración segura de forma predeterminada |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Inmediato | Quita la vinculación basada en propiedades de **/content** a **/conf** (reemplazada por el mecanismo OSGi), genera la configuración OSGi correspondiente |
| `Cq62FormsContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Debido a que merge_preserve gestiona el seguro de forma predeterminada, deniega las anulaciones de reglas dados permisos que llevan a la necesidad de reordenar al actualizar |
| `CQ62Html5SmartFileUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Detecta los componentes que utilizan el widget Html5SmartFile, busca los usos del componente en el contenido y reestructura la persistencia, moviendo efectivamente el binario un nivel hacia abajo y no almacenarlo en el nivel de componente. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Mueve proyectos de estilo antiguo de **/etc/projects** a **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Introduce una capa de contenedor en la jerarquía (Áreas) y ajusta las referencias. |
| `Cq62TargetContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Define nombres de ubicación fijos para los componentes de destino. |
| `Cq62WorkflowContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Transformación compleja de los modelos de flujo de trabajo anteriores a la versión 6.2 de estructuras, instancias, notificaciones y, a continuación, combinación desde la ubicación de copia de seguridad desde **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Inmediato | Mueve recursos, esquemas de metadatos personalizados y perfiles de procesamiento de **/apps** a **/conf** y traduce el esquema de metadatos y los formularios de perfiles de metadatos de coral2 a coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6=&quot;&quot;> | Inmediato | Mueve los recursos y las facetas de búsqueda personalizadas de **/apps** a **/conf** y traduce los formularios de esquema de metadatos y perfiles de metadatos de coral2 a coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Actualiza la Bandeja de entradaElementos para ordenar los elementos de la bandeja de entrada (ajustando los metadatos para una ordenación eficiente) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6=&quot;&quot;> | Inmediato | Ajusta la propiedad metadataSchema en la carpeta reemplazando las rutas relativas a **/conf** en lugar de **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Ajuste de la estructura de navegación |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6=&quot;&quot;> | Inmediato | Mueve las configuraciones personalizadas para los paneles de monitorización de **/libs** y **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6=&quot;&quot;> | Inmediato | Traduce la propiedad processingProfile (utilizada hasta la versión 6.1) en Assets para que coincida con la estructura 6.3 y posteriores. También ajusta las rutas relativas del perfil a **/conf** en lugar de **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6=&quot;&quot;> | Inmediato | Tarea de actualización que elimina las entradas de menú del CRXDE Lite y la consola web obsoletas en caso de una actualización. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6=&quot;&quot;> | Retrasado | Moviendo configuraciones de nube SRP, configuraciones de palabras clave de la comunidad, limpia **/etc/social** y **/etc/enablement** (cualquier referencia y datos debe ajustarse cuando se ejecuta la migración diferida - ninguna parte de la aplicación debe depender de esta estructura). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Retrasado | Limpia **/etc/cloudsettings** (que contiene la configuración de ContextHub). La configuración se migra automáticamente en el primer acceso. En caso de que la migración de contenido diferida se inicie junto con la actualización, este contenido en **/etc/cloudsettings** debe conservarse mediante paquete antes de la actualización y reinstalarse para que se inicie la transformación implícita, junto con la posterior desinstalación del paquete después de la finalización. |
| `CQ64UsersTitleFixTask` | &lt; 6=&quot;&quot;> | Retrasado | Ajusta la estructura de título heredada al título en el nodo de perfil de usuario. |
| `CQ64CommerceMigrationTask` | &lt; 6=&quot;&quot;> | Retrasado | Migrar el contenido comercial de **/etc/commerce** a **/var/commerce**. Durante la migración del contenido se mueve y las referencias al contenido movido se actualizan para reflejar la nueva ubicación. |
