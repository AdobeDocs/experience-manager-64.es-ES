---
title: Tareas de mantenimiento previas a la actualización
seo-title: Pre-Upgrade Maintenance Tasks
description: Obtenga información sobre las tareas previas a la actualización en AEM.
seo-description: Learn about the pre-upgrade tasks in AEM.
uuid: 6c0d4b31-6464-470b-9e40-1fc2abb9b2a6
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 899ea120-c96d-4dbf-85da-e5d25959d10a
feature: Upgrading
exl-id: f146cb2f-ee77-4c99-8dff-446cdb3a7797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2204'
ht-degree: 1%

---

# Tareas de mantenimiento previas a la actualización{#pre-upgrade-maintenance-tasks}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Antes de comenzar la actualización, es importante seguir estas tareas de mantenimiento para asegurarse de que el sistema está listo y se puede revertir si se producen problemas:

* [Garantizar suficiente espacio en disco](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [AEM de copia de seguridad completa](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Haga una copia de seguridad de los cambios en /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Generar el archivo quickstart.properties](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configurar el flujo de trabajo y la depuración del registro de auditoría](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Instalación, configuración y ejecución de las tareas previas a la actualización](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Desactivar módulos de inicio de sesión personalizados](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Quitar Actualizaciones Del Directorio /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Detener Cualquier Instancia En Espera Fría](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Desactivar trabajos programados personalizados](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Ejecutar limpieza de revisión sin conexión](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Ejecutar colección de residuos del almacén de datos](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Actualizar el esquema de base de datos si es necesario](pre-upgrade-maintenance-tasks.md#upgrade-the-database-schema-if-needed)
* [Eliminar usuarios que podrían obstaculizar la actualización](pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)
* [Rotar archivos de registro](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Garantizar suficiente espacio en disco {#ensure-sufficient-disk-space}

Al ejecutar la actualización, además de las actividades de actualización de contenido y código, será necesario realizar una migración del repositorio. La migración creará una copia del repositorio en el nuevo formato Segment Tar . Como resultado, necesitará suficiente espacio en disco para conservar una segunda versión, potencialmente más grande, del repositorio.

## AEM de copia de seguridad completa {#fully-back-up-aem}

AEM debe realizar una copia de seguridad completa antes de comenzar la actualización. Asegúrese de realizar una copia de seguridad del repositorio, la instalación de la aplicación, el almacén de datos y las instancias de Mongo, si corresponde. Para obtener más información sobre cómo realizar copias de seguridad y restaurar una instancia de AEM, consulte [Copia de seguridad y restauración](/help/sites-administering/backup-and-restore.md).

## Haga una copia de seguridad de los cambios en /etc {#backup-changes-etc}

El proceso de actualización realiza un buen trabajo al mantener y combinar el contenido y las configuraciones existentes desde el `/apps` y `/libs` rutas en el repositorio. Para los cambios realizados en la variable `/etc` , incluidas las configuraciones de Context Hub, a menudo es necesario volver a aplicar estos cambios después de la actualización. Mientras la actualización realiza una copia de seguridad de los cambios en los que no se puede combinar `/var`, recomendamos realizar una copia de seguridad de estos cambios manualmente antes de comenzar la actualización.

## Generar el archivo quickstart.properties {#generate-quickstart-properties}

Al iniciar AEM desde el archivo jar, una `quickstart.properties` se generará en `crx-quickstart/conf`. Si AEM se ha iniciado con el script de inicio en el pasado, este archivo no estará presente y la actualización fallará. Asegúrese de comprobar la existencia de este archivo y reinicie AEM desde el archivo jar si no está presente.

## Configurar el flujo de trabajo y la depuración del registro de auditoría {#configure-wf-audit-purging}

La variable `WorkflowPurgeTask` y `com.day.cq.audit.impl.AuditLogMaintenanceTask` las tareas requieren configuraciones OSGi independientes y no funcionarán sin ellas. Si fallan durante la ejecución de tareas previas a la actualización, la razón más probable es que falten configuraciones. Por lo tanto, asegúrese de agregar configuraciones OSGi para estas tareas o eliminarlas por completo de la lista de tareas de optimización previas a la actualización si no desea ejecutarlas. La documentación para configurar las tareas de depuración de flujos de trabajo se encuentra en [Administración de instancias de flujo de trabajo](/help/sites-administering/workflows-administering.md) y la configuración de la tarea de mantenimiento del registro de auditoría se encuentra en [Mantenimiento del registro de auditoría en AEM 6](/help/sites-administering/operations-audit-log.md).

Para ver el flujo de trabajo y el registro de auditoría purgando en CQ 5.6, así como el registro de auditoría purgando en AEM 6.0, consulte [Purga del flujo de trabajo y los nodos de auditoría](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).

## Instalación, configuración y ejecución de las tareas previas a la actualización {#install-configure-run-pre-upgrade-tasks}

Debido al nivel de personalización que AEM permite, los entornos no suelen adherirse a una forma uniforme de realizar actualizaciones. Esto dificulta la creación de un procedimiento estandarizado para las actualizaciones.

En versiones anteriores, también resultaba difícil realizar actualizaciones AEM que se detuvieron o que no se reanudaron de forma segura. Esto llevaba a situaciones en las que era necesario reiniciar el procedimiento de actualización completo o en las que se realizaban actualizaciones defectuosas sin activar ninguna advertencia.

Para solucionar estos problemas, Adobe ha añadido varias mejoras al proceso de actualización, lo que lo hace más flexible y fácil de usar. Las tareas de mantenimiento previas a la actualización que antes tenían que realizarse manualmente se están optimizando y automatizando. Además, se han añadido informes posteriores a la actualización para que el proceso pueda examinarse en profundidad con la esperanza de que se encuentren más fácilmente todos los problemas.

Las tareas de mantenimiento previas a la actualización se distribuyen actualmente en varias interfaces que se realizan de forma manual o parcial. La optimización de mantenimiento previa a la actualización introducida en AEM 6.3 permite una forma unificada de déclencheur de estas tareas y poder inspeccionar su resultado bajo demanda.

Todas las tareas incluidas en el paso de optimización previo a la actualización son compatibles con todas las versiones a partir de AEM 6.0.

### Cómo configurarlo {#how-to-set-it-up}

En AEM 6.3 y posteriores, las tareas de optimización de mantenimiento previas a la actualización se incluyen en el jar de inicio rápido. Si está actualizando desde una versión anterior de AEM 6, están disponibles a través de paquetes separados que puede descargar desde el Administrador de paquetes.

Puede encontrar los paquetes en estas ubicaciones:

* [Para actualizar desde AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [Para actualizar desde AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [Para actualizar desde AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62)

### Cómo utilizarlo {#how-to-use-it}

La variable `PreUpgradeTasksMBean` El componente OSGI viene preconfigurado con una lista de tareas de mantenimiento previas a la actualización que se pueden ejecutar todas a la vez. Puede configurar las tareas siguiendo el procedimiento siguiente:

1. Vaya a la consola web navegando hasta `https://serveraddress:serverport/system/console/configMgr`

1. Buscar &quot;**preupgradetasks**&quot; y, a continuación, haga clic en el primer componente coincidente. El nombre completo del componente es `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Modifique la lista de tareas de mantenimiento que deben ejecutarse como se muestra a continuación:

   ![1487758925984](assets/1487758925984.png)

La lista de tareas difiere según el modo de ejecución que se esté utilizando para iniciar la instancia. A continuación se muestra una descripción del modo de ejecución para el que se ha diseñado cada tarea de mantenimiento.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tarea</strong></td> 
   <td><strong>Modo de ejecución</strong></td> 
   <td><strong>Notas</strong></td> 
  </tr> 
  <tr> 
   <td><code>TarIndexMergeTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>DataStoreGarbageCollectionTask</code></td> 
   <td>crx2</td> 
   <td>Ejecutará mark y sweep. Para los almacenes de datos compartidos, elimine este paso y ejecute<br /> prepare las instancias de forma manual o correcta antes de ejecutarlas.</td> 
  </tr> 
  <tr> 
   <td><code>ConsistencyCheckTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>WorkflowPurgeTask</code></td> 
   <td>crx2/crx3</td> 
   <td>Debe configurar el OSGi de configuración de purga del flujo de trabajo de Granite de Adobe antes de ejecutarse.</td> 
  </tr> 
  <tr> 
   <td><code>GenerateBundlesListFileTask</code></td> 
   <td>crx2/crx3</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>RevisionCleanupTask</code></td> 
   <td>crx3</td> 
   <td>En el caso de instancias de TarMK de AEM 6.0 a 6.2, ejecute manualmente la limpieza de revisión sin conexión en su lugar.</td> 
  </tr> 
  <tr> 
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td> 
   <td>crx3</td> 
   <td>Debe configurar la configuración OSGi del Programador de purga de registros de auditoría antes de ejecutar.</td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` llama a una operación de colección de residuos del almacén de datos con la fase de marca y barrido si se utiliza. Para implementaciones que utilizan un almacén de datos compartido, asegúrese de reconfigurarlo o de preparar correctamente la instancia para evitar la eliminación de elementos a los que hace referencia otra instancia. Esto puede requerir la ejecución manual de la fase de marca en todas las instancias antes de activar esta tarea de preactualización.

### Configuración predeterminada de las comprobaciones de estado previas a la actualización {#default-configuration-of-the-pre-upgrade-health-checks}

La variable `PreUpgradeTasksMBeanImpl` El componente OSGI viene preconfigurado con una lista de etiquetas de comprobación de estado previas a la actualización para ejecutarse cuando el `runAllPreUpgradeHealthChecks` se llama método:

* **sistema** - la etiqueta utilizada por los controles de mantenimiento de granito

* **actualización previa** - esta es una etiqueta personalizada que podría agregarse a todas las comprobaciones de estado que puede configurar para ejecutar antes de una actualización

La lista es editable. Puede utilizar el signo más **(+)** y menos **(-)** además de las etiquetas para agregar más etiquetas personalizadas o quitar las predeterminadas.

**Métodos MBean**

Se puede acceder a la funcionalidad de bean administrado mediante la variable [Consola JMX](/help/sites-administering/jmx-console.md).

Puede acceder a los MBeans mediante:

1. Ir a la consola JMX en *https://serveraddress:serverport/system/console/jmx*
1. Buscar **PreUpgradeTasks** y haga clic en el resultado

1. Seleccione cualquier método de **Operaciones** y seleccione **Invocar** en la siguiente ventana.

A continuación se muestra una lista de todos los métodos disponibles que la variable `PreUpgradeTasksMBeanImpl` expone:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nombre del método</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeTasksNames()</code></td> 
   <td>INFORMACIÓN</td> 
   <td>Muestra la lista de nombres de tareas de mantenimiento previas a la actualización disponibles.</td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td> 
   <td>INFORMACIÓN</td> 
   <td>Muestra la lista de nombres de etiquetas de comprobaciones de estado previas a la actualización.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeTasks()</code></td> 
   <td>ACCIÓN</td> 
   <td>Ejecuta todas las tareas de mantenimiento previas a la actualización en la lista.</td> 
  </tr> 
  <tr> 
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td> 
   <td>ACCIÓN</td> 
   <td>Ejecuta la tarea de mantenimiento previa a la actualización con el nombre dado como parámetro.</td> 
  </tr> 
  <tr> 
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Comprueba si la variable <code>runAllPreUpgradeTasksmaintenance</code> está ejecutándose la tarea.</td> 
  </tr> 
  <tr> 
   <td><code>getAnyPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Comprueba si hay alguna tarea de mantenimiento previa a la actualización actualmente en ejecución y<br /> devuelve una matriz que contiene los nombres de las tareas que se están ejecutando actualmente.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td> 
   <td>ACCIÓN</td> 
   <td>Muestra el tiempo de ejecución exacto de la tarea de mantenimiento anterior a la actualización con el nombre dado como parámetro.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td> 
   <td>ACCIÓN</td> 
   <td>Muestra el último estado en ejecución de la tarea de mantenimiento anterior a la actualización con el nombre dado como parámetro.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td> 
   <td>ACCIÓN</td> 
   <td><p>Ejecuta todas las comprobaciones de estado previas a la actualización y guarda su estado en un archivo denominado <code>preUpgradeHCStatus.properties</code> que se encuentra en la ruta principal de sling. Si la variable <code>shutDownOnSuccess</code> se establece en <code>true</code>, la instancia de AEM se cerrará, pero solo si todas las comprobaciones de estado previas a la actualización tienen el estado OK.</p> <p>El archivo de propiedades se utilizará como condición previa para cualquier actualización futura<br /> y el proceso de actualización se detendrá si se realiza la comprobación de estado previa a la actualización<br /> error de ejecución. Si desea ignorar el resultado de la actualización previa<br /> comprueba el estado e inicia la actualización de todos modos, puede eliminar el archivo.</p> </td> 
  </tr> 
  <tr> 
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td> 
   <td>ACCIÓN</td> 
   <td>Enumera todos los paquetes importados que ya no se satisfarán cuando<br /> actualizando a la versión de AEM especificada. La versión de AEM de destino debe ser<br /> dado como parámetro.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Los métodos MBean se pueden invocar mediante:
>
>* La consola JMX
>* Cualquier aplicación externa que se conecte a JMX
>* cURL
>


## Desactivar módulos de inicio de sesión personalizados {#disable-custom-login-modules}

>[!NOTE]
>
>Este paso solo es necesario si está actualizando desde una versión AEM 5. Se puede omitir por completo para las actualizaciones de versiones anteriores AEM 6.

El modo personalizado `LoginModules` están configurados para la autenticación a nivel de repositorio ha cambiado fundamentalmente en Apache Oak.

En AEM versiones que usaban la configuración CRX2 se colocaron en la variable `repository.xml` , mientras que a partir de AEM 6 se hace en el servicio Apache Felix JAAS Configuration Factory a través de la Consola Web.

Por lo tanto, cualquier configuración existente tendrá que ser deshabilitada y recreada para Apache Oak después de la actualización.

Para desactivar los módulos personalizados definidos en la configuración de JAAS de `repository.xml`, debe modificar la configuración para utilizar el valor predeterminado `LoginModule`, como en este ejemplo:

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>Para obtener más información, consulte [Autenticación con el módulo de inicio de sesión externo](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>Para ver un ejemplo de `LoginModule` configuración en AEM 6, consulte [Configuración de LDAP con AEM 6](/help/sites-administering/ldap-config.md).

## Quitar Actualizaciones Del Directorio /install {#remove-updates-install-directory}

>[!NOTE]
>
>Elimine paquetes del directorio crx-quickstart/install DESPUÉS de cerrar la instancia de AEM. Este será uno de los últimos pasos antes de iniciar el procedimiento de actualización in situ.

Elimine cualquier paquete de servicio, paquete de características o revisión que se haya implementado a través de la `crx-quickstart/install` en el sistema de archivos local. Esto evitará la instalación involuntaria de revisiones y service packs antiguos sobre la nueva versión de AEM una vez finalizada la actualización.

## Detener Cualquier Instancia En Espera Fría {#stop-tarmk-coldstandby-instance}

Si utiliza el modo de espera en frío TarMK, detenga las instancias en espera en frío. Esto garantizará una forma eficaz de volver a conectarse en caso de problemas en la actualización. Una vez que la actualización se haya completado correctamente, las instancias en espera en frío deberán reconstruirse a partir de las instancias principales actualizadas.

## Desactivar trabajos programados personalizados {#disable-custom-scheduled-jobs}

Deshabilite cualquier trabajo programado de OSGi que esté incluido en el código de la aplicación.

## Ejecutar limpieza de revisión sin conexión {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Este paso solo es necesario para las instalaciones TarMK

Si utiliza TarMK, debe ejecutar la limpieza de revisión sin conexión antes de la actualización. Esto hará que el paso de migración del repositorio y las tareas de actualización subsiguientes se ejecuten mucho más rápido y ayudará a garantizar que la limpieza de revisión en línea se pueda ejecutar correctamente una vez completada la actualización. Para obtener información sobre cómo ejecutar la limpieza de revisión sin conexión, consulte [Realización de limpieza de revisión sin conexión](https://helpx.adobe.com/experience-manager/6-2/sites-deploying/storage-elements-in-aem-6.html#performing-offline-revision-cleanup).

## Ejecutar colección de residuos del almacén de datos {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Este paso solo es necesario para instancias que ejecutan crx3

Después de ejecutar la limpieza de revisión en instancias CRX3, debe ejecutar la Colección de residuos del almacén de datos para eliminar cualquier blobs no referenciado en el almacén de datos. Para obtener instrucciones, consulte la documentación de [Colección de residuos del almacén de datos](/help/sites-administering/data-store-garbage-collection.md).

## Eliminar usuarios que podrían obstaculizar la actualización {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>Esta tarea de mantenimiento previa a la actualización solo es necesaria si:
>
>* Está actualizando desde AEM versiones anteriores a AEM 6.3
>* Se encuentra con cualquiera de los errores mencionados a continuación durante la actualización.


Hay casos excepcionales en los que los usuarios de servicios podrían terminar en versiones de AEM antiguas etiquetadas incorrectamente como usuarios normales.

Si esto sucede, la actualización fallará con un mensaje como este:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Para solucionar este problema, asegúrese de hacer lo siguiente:

Para solucionar este problema, asegúrese de hacer lo siguiente:

* Desasociar la instancia del tráfico de producción
* Cree una copia de seguridad de los usuarios que causen el problema. Puede hacerlo a través del Administrador de paquetes. Para obtener más información, consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md).
* Elimine los usuarios que están causando el problema. A continuación se muestra una lista de usuarios que podrían pertenecer a esta categoría:
   * dynamic-media-replication
   * communities-ugc-writer
   * communities-utilidad-reader
   * communities-user-admin
   * oauthservice
   * sling-scripting

## Actualizar el esquema de base de datos si es necesario {#upgrade-the-database-schema-if-needed}

Normalmente, la pila subyacente de Apache Oak que utiliza AEM para la persistencia se encargará de actualizar el esquema de la base de datos si es necesario.

Sin embargo, pueden surgir casos en los que el esquema no se pueda actualizar automáticamente. Estos son, en su mayoría, entornos de alta seguridad en los que la base de datos se ejecuta bajo un usuario con privilegios muy limitados. Si esto sucede, AEM seguirá utilizando el esquema antiguo.

Para evitar que esto ocurra, debe actualizar el esquema siguiendo el siguiente procedimiento:

1. Apague la instancia de AEM que debe actualizarse.
1. Actualice el esquema de la base de datos. Consulte la documentación del tipo de base de datos para ver qué herramientas necesita utilizar para conseguirlo.

   Para obtener más información sobre cómo Oak gestiona las actualizaciones de esquema, consulte [esta página en el sitio web de Apache](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. Continúe con la AEM de actualización.

## Rotar archivos de registro {#rotate-log-files}

Se recomienda archivar los archivos de registro actuales antes de comenzar la actualización. Esto facilitará la supervisión y el análisis de los archivos de registro durante y después de la actualización para identificar y resolver cualquier problema que pueda producirse.
