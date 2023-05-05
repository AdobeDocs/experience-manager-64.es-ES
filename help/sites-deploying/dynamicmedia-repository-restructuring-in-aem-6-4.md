---
title: Reestructuración de repositorios de Dynamic Media en AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Aprenda a realizar los cambios necesarios para migrar a la nueva estructura de repositorios en AEM 6.4 para Dynamic Media.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# Reestructuración de repositorios de Dynamic Media en AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Tal como se describe en el elemento principal [Reestructuración de repositorios en AEM 6.4](/help/sites-deploying/repository-restructuring.md) , los clientes que actualicen a AEM 6.4 deben utilizar esta página para evaluar el esfuerzo de trabajo asociado con los cambios en el repositorio que afectan a la solución de Dynamic Media. Algunos cambios requieren un esfuerzo de trabajo durante el proceso de actualización de AEM 6.4, mientras que otros se pueden aplazar hasta una actualización de 6.5.

**Antes de la actualización a la versión 6.5**

* [Configuraciones personalizadas de codificación de vídeo adaptable](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configuración de nube de Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configuración del Cloud Service Dynamic Media (híbrido DM)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media: Configuración de Cloud Service de YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Misc](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Antes de la actualización a la versión 6.5 {#prior-to-upgrade}

### Configuraciones personalizadas de codificación de vídeo adaptable  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Puede ejecutar el siguiente script de migración para migrar a la nueva ubicación:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Como alternativa, puede editar la configuración en AEM interfaz de usuario y los cambios se guardarán en la nueva ubicación.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Configuración de nube de Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>El cliente puede ejecutar una secuencia de comandos de migración en esta ubicación:<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Reinicie el paquete OSGi de Dynamic Media.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

### Configuración del Cloud Service Dynamic Media (DM Hybrid) {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>Puede ejecutar la secuencia de comandos de migración siguiente para alinearla con el modelo más reciente:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media: configuración del Cloud Service de YouTube  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>1. Cancelar la publicación de todos los vídeos de YouTube<br /> 2. Cree la configuración de YouTube mediante la nueva interfaz de usuario táctil (desde <code>/conf</code>), incluida la copia de todos los canales de la ubicación antigua<br /> 3. Vuelva a publicar todos los vídeos en YouTube.</p> <p>Este flujo de trabajo resulta en nuevas URL de YouTube. Si no cancela la publicación antes de crear una nueva configuración de TouchUI YouTube, tendrá varias URL de YouTube en Propiedades, ya que los canales recreados volverán a publicar si se le da la oportunidad. Esto significa que tendrá direcciones URL inútiles enumeradas en Propiedades.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Misc {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>El cliente puede ejecutar el siguiente script de migración.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Como alternativa, puede editar la configuración en AEM interfaz de usuario y los cambios se guardarán en la nueva ubicación.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>Ubicación anterior</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Nuevas ubicaciones</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Directrices de reestructuración</strong></td> 
   <td><p>El cliente puede ejecutar el siguiente script de migración.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>
