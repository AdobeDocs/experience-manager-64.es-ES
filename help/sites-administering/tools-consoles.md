---
title: Consolas de herramientas
description: Obtenga información sobre las distintas consolas de herramientas en Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
exl-id: 7566e1bc-8571-4b3c-b420-4324026bd4dd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 20%

---

# Consolas de herramientas{#tools-consoles}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las consolas de **herramientas** permiten acceder a toda una serie de herramientas especializadas que le ayudan a administrar sus sitios web, recursos digitales y otros aspectos de su repositorio de contenido. Actualmente hay dos sabores del **Herramientas** consola en función de la IU que utilice:

* [Herramientas: IU clásica](#tools-classic-ui)
* [Herramientas: IU táctil](#tools-touch-optimized-ui)

## Herramientas: IU clásica {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Página o carpeta</th> 
   <th> </th> 
   <th>Función</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">Centro de control de MSM</a></td> 
   <td> </td> 
   <td>Punto centralizado para administrar varios sitios.</td> 
  </tr> 
  <tr> 
   <td>Configuraciones de Client Context<br /> </td> 
   <td> </td> 
   <td>La variable <a href="/help/sites-developing/client-context.md">ClientContext</a> representa una colección ensamblada dinámicamente de datos de usuario. Las configuraciones predeterminadas y de marketing cloud se incluyen aquí.<br /> </td> 
  </tr> 
  <tr> 
   <td>Configuración de servicios de nube<br /> </td> 
   <td> </td> 
   <td>Configuraciones de tenencias relacionadas con <a href="/help/sites-administering/marketing-cloud.md">Integración con Adobe Marketing Cloud</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">Comercio</a></td> 
   <td> </td> 
   <td>Proporciona acceso a importadores y a varios datos de productos.</td> 
  </tr> 
  <tr> 
   <td>DAM: Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>Proporciona acceso a información y licencias de derechos digitales.</td> 
  </tr> 
  <tr> 
   <td>DAM - Comprobador de coherencia<br /> </td> 
   <td> </td> 
   <td>Comparaciones <code>/var/dam</code> y <code>/content/dam</code> y comprobaciones<br /> cualquier inconsistencia. A continuación, se pueden sincronizar o eliminar todos los archivos o carpetas enumerados. Los tipos de nodos para la comparación de carpetas se pueden configurar en la consola web.</td> 
  </tr> 
  <tr> 
   <td>DAM - Indesign de Adobe<br /> </td> 
   <td> </td> 
   <td>Secuencias de comandos para su uso junto con Indesign de Adobe.</td> 
  </tr> 
  <tr> 
   <td>DAM: Perfiles de vídeo<br /> </td> 
   <td> </td> 
   <td>Perfiles configurables para transcodificaciones ffmpeg.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">Tableros</a></td> 
   <td> </td> 
   <td>Permite crear tableros de informes; proporcionan una forma personalizable de definir páginas que muestran datos consolidados.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">Diseños</a></td> 
   <td> </td> 
   <td>Contiene la lista de diseños definidos, incluidos los gráficos y los archivos css que se van a utilizar.</td> 
  </tr> 
  <tr> 
   <td>Documentación personalizada</td> 
   <td> </td> 
   <td>Se utiliza al ampliar la documentación y la ayuda en línea.</td> 
  </tr> 
  <tr> 
   <td>Envíos de formularios</td> 
   <td> </td> 
   <td>Contiene la lista de envíos de formularios recibidos.</td> 
  </tr> 
  <tr> 
   <td>Importadores: <a href="/help/sites-administering/bulk-editor.md">Editor por lotes</a></td> 
   <td> </td> 
   <td>Permite buscar elementos y editarlos de forma masiva. También puede exportar e importar contenido (de forma masiva) en el repositorio.</td> 
  </tr>
  <tr> 
   <td>Importador: Importador de fuentes</td> 
   <td> </td> 
   <td><p>Feed Importer es un marco para importar repetidamente contenido de fuentes externas en su repositorio. La idea de Feed Importer es sondear un recurso remoto a un intervalo especificado, analizarlo y crear nodos en el repositorio de contenido que representen el contenido del recurso remoto.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">Comprobador de vínculos externos</a></td> 
   <td> </td> 
   <td>Analiza todas las páginas de contenido de la instancia de AEM y comprueba los vínculos externos. Se muestra una lista de vínculos válidos y no válidos.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">Móvil</a></td> 
   <td> </td> 
   <td>Ayuda a crear sitios web diseñados para dispositivos móviles.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>Gestiona el contenido multilingüe y multinacional, lo que le ayuda a equilibrar la promoción de marca centralizada con el contenido localizado.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">Notificación</a></td> 
   <td> </td> 
   <td>Plantillas de notificación.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">Paquetes</a></td> 
   <td> </td> 
   <td>Un vínculo alternativo al Administrador de paquetes que muestra los paquetes que se han cargado para AEM WCM. Similar a la información mostrada en el Administrador de paquetes de CRX.</td> 
  </tr> 
  <tr> 
   <td>Replicación - <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">Agentes de replicación</a></td> 
   <td> </td> 
   <td>Se utiliza para replicar datos del autor para publicarlos al publicar páginas, o con replicación inversa para devolver comentarios del usuario del entorno de publicación al autor.</td> 
  </tr> 
  <tr> 
   <td>Importadores: <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">Activar árbol</a></td> 
   <td> </td> 
   <td>Desde la ficha Sitios web puede activar las páginas individuales. Cuando haya introducido o actualizado una cantidad considerable de páginas de contenido (todas ellas residentes dentro de la misma página raíz), puede ser más fácil activar todo el árbol en una sola acción. También puede realizar un ensayo para emular una activación y resaltar qué páginas se activarían.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">Informes</a></td> 
   <td> </td> 
   <td>AEM ofrece una amplia gama de informes personalizados, le permite crear informes personalizados y/o desarrollar sus propios informes.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">Andamiaje de página predeterminada</a></td> 
   <td> </td> 
   <td>Con scaffolding, puede crear un formulario (un scaffold) con campos que reflejen la estructura que desee para sus páginas y luego usar este formulario para crear fácilmente páginas basadas en esta estructura.</td> 
  </tr> 
  <tr> 
   <td>Seguridad - <a href="/help/sites-administering/notification.md">Configuración de autoservicio </a> </td> 
   <td> </td> 
   <td>Permite configurar los correos electrónicos que los usuarios reciben automáticamente cuando crean una cuenta o restablecen una contraseña y confirmar una contraseña que se haya restablecido.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentación</a></td> 
   <td> </td> 
   <td>Los visitantes del sitio tienen diferentes intereses y objetivos cuando acceden al sitio. Entender estos objetivos y cumplir las expectativas es un factor de éxito importante para el marketing en línea. La segmentación ayuda a conseguirlo mediante el análisis y la caracterización de los detalles de un visitante.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>Configuración de SRP predeterminada. Consulte <a href="/help/communities/srp-config.md">Configuración de almacenamiento</a> consola.</td> 
  </tr> 
  <tr> 
   <td>administración de tareas</td> 
   <td> </td> 
   <td>No hay ninguna funcionalidad activa relacionada con esta entrada.</td> 
  </tr> 
  <tr> 
   <td>inquilinos</td> 
   <td> </td> 
   <td>No hay ninguna funcionalidad activa relacionada con esta entrada.</td> 
  </tr> 
  <tr> 
   <td>Versiones - <a href="/help/sites-deploying/version-purging.md">Purgar versiones</a></td> 
   <td> </td> 
   <td>Permite depurar las versiones de la página según sea necesario.</td> 
  </tr> 
  <tr> 
   <td>Repositorios virtuales</td> 
   <td> </td> 
   <td>Puede configurar un repositorio virtual mediante la función de montaje del espacio de trabajo para proporcionar a las aplicaciones de contenido con JCR acceso simplificado a la infraestructura de contenido JCR basada en CRX y los conectores JCR.</td> 
  </tr> 
  <tr> 
   <td>palabras clave</td> 
   <td> </td> 
   <td>Obsoleto. Consulte <a href="/help/communities/moderate-ugc.md#watchwords">Moderación del contenido de la comunidad</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">Flujo de trabajo</a></td> 
   <td> </td> 
   <td>Los flujos de trabajo controlan una serie de acciones en páginas o recursos digitales que admiten cualquier proceso editorial.</td> 
  </tr> 
 </tbody> 
</table>

## Herramientas: IU táctil {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Sección</th> 
   <th>Opción</th> 
   <th>Función</th> 
  </tr> 
  <tr> 
   <td>Creación</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">Campañas</a></td> 
   <td>Gestionar sus campañas de marketing.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">Lanzamientos</a></td> 
   <td>Administrar los lanzamientos de marketing</td> 
  </tr> 
  <tr> 
   <td>Tareas</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">Bandeja de entrada</a></td> 
   <td>Administre los elementos de la bandeja de entrada.</td> 
  </tr> 
  <tr> 
   <td>Operaciones</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">Usuarios y grupos </a></td> 
   <td>Administrar usuarios y grupos.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">Administración de etiquetas</a></td> 
   <td>Organizar sus etiquetas y espacios de nombres.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">Cloud Services</a></td> 
   <td>Conectar con Adobe Marketing Cloud.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">Flujos de trabajo</a></td> 
   <td>Modelar y administrar flujos de trabajo.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">Replicación</a></td> 
   <td>Cree y administre varios sitios web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">Informes</a></td> 
   <td>Crear y supervisar informes personalizados.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">Pruebas</a></td> 
   <td>Ejecutar pruebas definidas para su aplicación.</td> 
  </tr> 
  <tr> 
   <td>Operaciones de Granite</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>Desarrollar aplicaciones con IDE basado en web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">Paquetes</a></td> 
   <td>Empaquetar y agrupar aplicaciones.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">Uso compartido de paquetes</a></td> 
   <td>Descargar aplicaciones de Adobe y la comunidad.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">Explorador de topología</a></td> 
   <td>Ver la topología de instancias.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">Descargando explorador</a></td> 
   <td>Administre la descarga.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">Copia de seguridad</a></td> 
   <td>Realizar tareas de copia de seguridad.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Consola web<br /> </td> 
   <td>Configurar y administrar la plataforma de la aplicación.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Volcado de configuración de la consola web<br /> </td> 
   <td>Descargue el estado de configuración desde la consola web.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Usuarios</td> 
   <td>Administrar los usuarios.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Grupos</td> 
   <td>Administrar sus grupos.</td> 
  </tr> 
  <tr> 
   <td>Medios externos<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Documentación</td> 
   <td>Ver la documentación de Web Experience Management.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Medios del desarrollador</td> 
   <td>Descargas y medios del desarrollador.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Algunas de las opciones anteriores están vinculadas a la IU clásica.
