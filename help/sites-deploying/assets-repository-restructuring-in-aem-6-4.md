---
title: Reestructuración del repositorio de activos en AEM 6.4
seo-title: Assets Repository Restructuring in AEM 6.4
description: Aprenda a realizar los cambios necesarios para migrar a la nueva estructura de repositorios en AEM 6.4 para Assets.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Assets.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
feature: Upgrading
exl-id: 3d5bbf95-bd1e-453b-b487-517a56fe727f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 3%

---

# Reestructuración del repositorio de activos en AEM 6.4{#assets-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Tal como se describe en el elemento principal [Reestructuración de repositorios en AEM 6.4](/help/sites-deploying/repository-restructuring.md) , los clientes que actualicen a AEM 6.4 deben utilizar esta página para evaluar el esfuerzo de trabajo asociado con los cambios en el repositorio que afectan a la solución de AEM Assets. Algunos cambios requieren un esfuerzo de trabajo durante el proceso de actualización de AEM 6.4, mientras que otros se pueden aplazar hasta una actualización de 6.5.

**Con actualización a la versión 6.4**

* [Misc](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc)

**Antes de la actualización a la versión 6.5**

* [Plantilla de notificación de correo electrónico de Evento de recurso/colección](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#asset-collection-event-e-mail-notification-template)
* [Diseños de uso compartido de recursos clásicos](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#classic-asset-share-designs)
* [Descargar plantilla de notificación de correo electrónico de recursos](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#download-asset-e-mail-notification-template)
* [Ejemplo de licencias DRM](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#example-drm-licenses)

* [Plantilla de notificación para compartir correo electrónico de vínculo](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#link-share-e-mail-notification-template)
* [Scripts de flujo de trabajo de InDesign](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#indesign-workflow-scripts)
* [Configuraciones de transcodificación de vídeo](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#video-transcoding-configurations)
* [Misc](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc2)

## Con actualización a la versión 6.4 {#with-upgrade}

### Misc {#misc}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td>/etc/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td>/var/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Si algún código personalizado depende de esta ubicación (por ejemplo, el código se basa explícitamente en esta ruta), entonces el código debe actualizarse para utilizar la nueva ubicación antes de la actualización; Idealmente, las API de Java se utilizan cuando están disponibles para reducir las dependencias en cualquier ruta específica del JCR.</p> <p>Ubicación temporal para guardar el archivo zip para que el cliente lo descargue. No es necesario actualizar desde que el cliente solicita descargar el recurso. Generará un archivo en la nueva ubicación.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr> 
 </tbody> 
</table>

## Antes de la actualización a la versión 6.5 {#prior-to-upgrade}

### Plantilla de notificación de correo electrónico de Evento de recurso/colección {#asset-collection-event-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/notification/email/default</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Si el cliente modificó las plantillas de correo electrónico, realice las siguientes acciones para alinearse con la nueva estructura del repositorio:</p> 
    <ol> 
     <li>La variable <code>/libs/settings/dam/notification</code> la plantilla de correo electrónico debe copiarse de <strong><code>/etc/notification/email/default</code></strong> a <strong><code>/apps/settings/notification/email/default</code></strong> 
      <ol> 
       <li>Porque el destino está en<strong> <code>/apps</code></strong> este cambio debe mantenerse en SCM.</li> 
      </ol> </li> 
     <li>Elimine la carpeta : <strong><code>/etc/dam/notification/email/default</code></strong> después de que se hayan movido las plantillas de correo electrónico incluidas en él.<br /> 
      <ol> 
       <li>Si no se han realizado actualizaciones en la plantilla de correo electrónico de<strong> <code>/etc/notification/email/default</code></strong>, la carpeta se puede eliminar porque la plantilla de correo electrónico original existe en <strong><code>/libs/settings/notification/email/default</code></strong> como parte de AEM instalación de 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Diseños de uso compartido de recursos clásicos {#classic-asset-share-designs}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/designs/assetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Para los diseños administrados en SCM y no escritos en tiempo de ejecución mediante los cuadros de diálogo de diseño, realice las siguientes acciones para alinearse con el modelo más reciente:</p> 
    <ol> 
     <li>Copie los diseños de la ubicación anterior a la nueva ubicación en <code>/apps</code>.</li> 
     <li>Convierta cualquier recurso CSS, JavaScript y estático del diseño en un <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Biblioteca de clientes</a> con <code>allowProxy = true</code>.</li> 
     <li>Actualizar referencias a la ubicación anterior en la <code>cq:designPath</code> propiedad mediante <strong>AEM &gt; Administración de DAM &gt; Página de uso compartido de recursos &gt; Propiedades de página &gt; Pestaña Avanzado &gt; Campo de diseño</strong>.</li> 
     <li>Actualice las páginas que hagan referencia a la ubicación anterior para utilizar la nueva categoría Biblioteca de clientes . Esto requiere actualizar el código de implementación de página.</li> 
     <li>Actualice las reglas de Dispatcher para permitir el servicio de bibliotecas de cliente a través de la variable <code>/etc.clientlibs/</code> proxy servlet.</li> 
    </ol> <p>Para los diseños que no se administran en SCM y que se modifican en tiempo de ejecución a través de los cuadros de diálogo de diseño, no salga de los diseños legibles <code>/etc</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Descargar plantilla de notificación de correo electrónico de recursos {#download-asset-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Si las plantillas de correo electrónico (<strong>downloadasset</strong> o <strong>transientworkflowcomplete</strong>) se han modificado, siga el siguiente procedimiento para alinearse con la nueva estructura:</p> 
    <ol> 
     <li>La plantilla de correo electrónico actualizada debe copiarse de <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> a <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong> 
      <ol> 
       <li>Porque el destino está en<strong> <code>/apps</code></strong> este cambio debe mantenerse en SCM.</li> 
      </ol> </li> 
     <li>Elimine la carpeta : <code>/etc/dam/workflow/notification/email/downloadasset </code>después de que se hayan movido las plantillas de correo electrónico incluidas en él.<br /> 
      <ol> 
       <li>Si no se han realizado actualizaciones en la plantilla de correo electrónico de<strong> <code>/etc</code></strong>, la carpeta se puede eliminar porque la plantilla de correo electrónico original existe en <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> como parte de AEM instalación de 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>While <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> es técnicamente compatible con la búsqueda (tiene prioridad antes de /apps a través de la búsqueda habitual de Sling CAConfig, pero después de <code>/etc</code>) la plantilla podría colocarse en <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Sin embargo, esto no se recomienda ya que no hay ninguna interfaz de usuario de tiempo de ejecución para facilitar la edición de la plantilla de correo electrónico.</td> 
  </tr> 
 </tbody> 
</table>

### Ejemplo de licencias DRM {#example-drm-licenses}

| **Ubicación anterior** | `/etc/dam/drm/licenses/` |
|---|---|
| **Nuevas ubicaciones** | `/libs/settings/dam/drm` |
| **Directrices de reestructuración** | N/D |
| **Notas** | N/D |

### Plantilla de notificación para compartir correo electrónico de vínculo {#link-share-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/adhocassetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Si el cliente modificó la plantilla de correo electrónico, entonces para alinearla con la nueva estructura del repositorio:</p> 
    <ol> 
     <li>La plantilla de correo electrónico actualizada debe copiarse de <strong><code>/etc/dam/adhocassetshare</code></strong> a <strong><code>/apps/settings/dam/adhocassetshare</code></strong> 
      <ol> 
       <li>Porque el destino está en<strong> <code>/apps</code></strong> este cambio debe mantenerse en SCM.</li> 
      </ol> </li> 
     <li>Elimine la carpeta : <strong><code>/etc/dam/adhocassetshare</code></strong> después de que se hayan movido las plantillas de correo electrónico incluidas en él.<br /> 
      <ol> 
       <li>Si no se han realizado actualizaciones en la plantilla de correo electrónico de<strong> <code>/etc</code></strong>, la carpeta se puede eliminar porque la plantilla de correo electrónico original existe en <strong><code>/libs/settings/dam/adhocassetshare</code></strong> como parte de AEM instalación de 6.4.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>While <code>/conf/global/settings/dam/adhocassetshare</code> es técnicamente compatible con la búsqueda (tiene prioridad antes de <code>/apps</code> mediante la búsqueda habitual de CAConfig de Sling, pero después de <code>/etc</code>), la plantilla se puede colocar en <code>/conf/global/settings/dam/adhocassetshare</code>. Sin embargo, esto no se recomienda ya que no hay ninguna interfaz de usuario de tiempo de ejecución para facilitar la edición de la plantilla de correo electrónico</td> 
  </tr> 
 </tbody> 
</table>

### Scripts de flujo de trabajo de InDesign {#indesign-workflow-scripts}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/indesign/scripts</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Para alinearse con la nueva estructura del repositorio:</p> 
    <ol> 
     <li>Copiar todos los scripts personalizados o modificados de <strong><code>/etc/dam/indesign/scripts</code></strong> a <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br /> 
      <ol> 
       <li>Solo está disponible la copia de scripts nuevos o modificados como scripts no modificados proporcionados por AEM mediante <strong><code>/libs/settings</code></strong> en AEM 6.4</li> 
      </ol> </li> 
     <li>Busque todos los modelos de flujo de trabajo que utilizan el paso WF del proceso de extracción de medios y 
      <ol> 
       <li>Para cada instancia del paso de flujo de trabajo, actualice las rutas en configuración para que apunten explícitamente a las secuencias de comandos adecuadas en<strong> <code>/apps/settings/dam/indesign/scripts</code></strong> o <strong><code>/libs/settings/dam/indesign/scripts</code></strong> según proceda.</li> 
      </ol> </li> 
     <li>Eliminar<strong> <code>/etc/dam/indesign/scripts</code></strong> completamente.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>Se recomienda almacenar los scripts personalizados en <code>/apps</code>, ya que es la ubicación donde se debe almacenar el código.</td> 
  </tr> 
 </tbody> 
</table>

### Configuraciones de transcodificación de vídeo {#video-transcoding-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/video</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Las personalizaciones de nivel de proyecto deben cortarse y pegarse en equivalente <code>/apps</code> o <code>/conf</code> rutas según corresponda.</p> <p>Para alinearse con la estructura del repositorio AEM 6.4:</p> 
    <ol> 
     <li>Copiar las configuraciones de vídeo modificadas de <code>/etc/dam/video</code> a <code>/apps/settings/dam/video</code></li> 
     <li>Quitar <code>/etc/dam/video</code></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr> 
 </tbody> 
</table>

### Configuraciones de ajustes preestablecidos de visor {#viewer-preset-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/presets/viewer</code></td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Para el ajuste preestablecido de visor predeterminado, solo estará disponible en la nueva ubicación.</p> <p>Para el ajuste preestablecido de visor personalizado:</p> 
    <ul> 
     <li>tendrá que ejecutar una secuencia de comandos de migración para mover el nodo de <code>/etc</code> a <code>/conf</code>. La secuencia de comandos se encuentra en <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>o puede editar la configuración y se guardarán automáticamente en la nueva ubicación.</li> 
    </ul> <p>Tenga en cuenta que no tiene que ajustar su código de copyURL/embed para que apunte a <code>/conf</code>. La solicitud existente a <code>/etc</code> se redirigirá al contenido correcto desde <code>/conf</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr> 
 </tbody> 
</table>

### Misc {#misc2}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ubicación anterior</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/libs/dam/clientlibs</code></td> 
  </tr> 
  <tr> 
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Ajuste las referencias para que apunten a los nuevos recursos en <code>/libs</code> usando la variable <code>/etc.clientlibs/</code> permitir prefijo de proxy.</p> <p>Finalmente, limpie eliminando las carpetas de la clientlibs migrada <code>/etc/clientlibs/foundation/</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr> 
 </tbody> 
</table>
