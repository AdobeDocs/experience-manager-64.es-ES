---
title: Estado de la función de IU táctil
seo-title: Estado de la función de IU táctil
description: Notas de la versión específicas de la IU táctil de Adobe Experience Manager 6.3.
seo-description: Notas de la versión específicas de la IU táctil de Adobe Experience Manager 6.3.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 14%

---


# Estado de la función de IU táctil {#touch-ui-feature-status}

>[!CAUTION]
>
>Con la versión 6.4 de AEM, la [IU clásica está en desuso](/help/release-notes/deprecated-removed-features.md). Adobe no tiene pensado realizar más mejoras en la IU clásica y se recomienda a los usuarios que aprovechen las nuevas y potentes funciones disponibles en la IU táctil.

A partir de la versión 6.0, AEM ha introducido una nueva interfaz de usuario denominada &quot;IU táctil&quot; (también conocida como &quot;IU táctil&quot;) que se alinea con el Adobe Marketing Cloud y con las directrices generales de la interfaz de usuario de Adobe. Al alcanzarse casi la partición de funciones, esta se ha convertido en la IU estándar en AEM con la interfaz heredada orientada al escritorio denominada &quot;IU clásica&quot;.

Aunque la mayoría de las funciones están presentes en la IU táctil, hay funciones que aún no se han completado y que se añadirán en versiones futuras.

La siguiente lista muestra el estado actual de las capacidades tal como se implementaron en la AEM 6.4.

Si desea conocer las recomendaciones para clientes que actualizan a AEM 6.4, consulte [Interfaz de usuario de Recommendations para clientes](/help/sites-deploying/ui-recommendations.md) para obtener más detalles.

>[!NOTE]
>
>Tenga en cuenta que esta página solo cubre la paridad de funciones con la IU clásica.
>
>Las funciones agregadas y exclusivas de la IU táctil que no están presentes en la IU clásica no se muestran en la lista.

>[!NOTE]
>
>Esta lista se esfuerza por ser completa, pero no debe considerarse exhaustiva.

## Leyenda {#legend}

* **Completar**: La función está totalmente disponible en la IU táctil
* **Principalmente**: La función está disponible principalmente en la IU táctil.
* **Falta**: La función no está presente en la IU táctil, la IU clásica debe utilizarse para realizar esta acción.
* **Reemplazado**: La función se reemplazó con una nueva implementación que funciona de manera diferente.
* **Eliminado**: La función ya no existe en la IU táctil y no se reemplazará.

## Estado de la función: Administración de sitios {#feature-status-sites-admin}

Es una lista de las capacidades que tiene la IU clásica Administración de sitios ( `/siteadmin`) y el estado en la IU táctil ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Función<br /> </strong></td> 
   <td><strong>Estado<br /> </strong></td> 
   <td><strong>Comentario</strong></td> 
  </tr>
  <tr>
   <td>Navegar por la jerarquía del sitio</td> 
   <td>Completar<br /> </td> 
   <td>AEM 6.4 introdujo una <a href="/help/sites-authoring/basic-handling.md#content-tree">vista de árbol de contenido</a>.</td> 
  </tr>
  <tr>
   <td>Iniciar flujo de trabajo</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crear nueva página</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crear nuevo sitio</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crear nuevo lanzamiento</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crear nueva Live Copy <br /> </td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crear carpeta</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mostrar estado de publicación</td> 
   <td>Principalmente</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Búsqueda  </td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiar/Pegar página (Duplicado)</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mover páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicación de páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicación de páginas sin derechos de replicación</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar posteriormente</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Árbol de publicaciones</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cancelar la publicación de páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cancelar la publicación de páginas sin derechos de replicación</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cancelar la publicación posteriormente</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Eliminar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Bloquear/Desbloquear</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Vista/Editar propiedades</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permisos en páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Historial de versiones</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurar versión</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Restaurar árbol y restaurar páginas eliminadas</td> 
   <td>Falta</td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Mostrar diferencia entre la versión antigua y la actual<br /> </td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Acciones de Live Copy (despliegue)</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ver copias de idioma</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Buscar y reemplazar</td> 
   <td>Falta<br /> </td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Bandeja de entrada de notificaciones (eventos JCR)</td> 
   <td>Falta</td> 
   <td>Utilice la IU clásica. Se reemplazará con una implementación diferente.</td> 
  </tr>
  <tr>
   <td>Referencias</td> 
   <td>Principalmente</td> 
   <td>La visualización de los vínculos de página entrantes se agregará en la versión de 2019 de AEM.</td> 
  </tr>
 </tbody>
</table>

## Estado de la función: Editor de páginas {#feature-status-page-editor}

Es una lista de las capacidades que tiene el Editor de páginas de la IU clásica ( `/cf#`) y el estado en la IU táctil ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Función</strong></td> 
   <td><strong>Estado</strong></td> 
   <td><strong>Comentario</strong></td> 
  </tr>
  <tr>
   <td>Editar páginas Web</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar páginas Web móviles<br /> </td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar contenido importado mediante el importador de diseños<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar correos electrónicos</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar aplicaciones móviles</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar Forms</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar Ofertas</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar modelos de Flujos de trabajo<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ode: Editar y Previsualización</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Previsualización adaptable<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Editar diseño</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Andamiaje</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modo: Estado de Live Copy<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Añadir anotaciones</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar propiedades<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Página de despliegue</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Inicio y mostrar flujo de trabajo</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Gestión de paquetes de workflow</td> 
   <td>Principalmente</td> 
   <td>Totalmente accesible en la IU táctil. La carga útil de varios flujos de trabajo se sigue presentando en la IU clásica.<br /> </td> 
  </tr>
  <tr>
   <td>Bloquear/Desbloquear página</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar página <br /> </td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cancelar la publicación de la página</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiar página</td> 
   <td>Eliminado<br /> </td> 
   <td>Utilice Administración del sitio para <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mover página</td> 
   <td>Eliminado</td> 
   <td>Utilice Administración del sitio para <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">mover páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Eliminar página</td> 
   <td>Eliminado</td> 
   <td>Use Administración del sitio para <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">eliminar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostrar referencias</td> 
   <td>Eliminado</td> 
   <td>Use Administración del sitio para <a href="/help/sites-authoring/author-environment-tools.md#references">ver la lista de referencia detallada</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Registro de auditorías</td> 
   <td>Eliminado</td> 
   <td>Utilice Administración del sitio y <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">carril de actividad abierto</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Crear versión</td> 
   <td>Eliminado</td> 
   <td>Utilice Administración del sitio para <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">crear nuevas versiones</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Restaurar versión</td> 
   <td>Eliminado</td> 
   <td>Utilice Administración del sitio para <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">restaurar versiones</a>.</td> 
  </tr>
  <tr>
   <td>Interruptores de inicio</td> 
   <td>Eliminado</td> 
   <td>Use Administración del sitio para <a href="/help/sites-authoring/launches-promoting.md">cambiar entre inicios</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traducir página</td> 
   <td>Eliminado</td> 
   <td>Use Administración del sitio para <a href="/help/sites-administering/tc-manage.md">agregar página a proyectos de traducción</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Deformación de tiempo (elija la fecha y hora y el sitio de navegación tal y como se vio)<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permisos</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaz de usuario de ClientContext<br /> </td> 
   <td>Reemplazado</td> 
   <td>Utilice la interfaz de usuario <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> a partir de ahora.</td> 
  </tr>
  <tr>
   <td>Buscador de contenido para los distintos tipos de medios<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Lista de componentes</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiar y pegar componentes<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Lista de componentes en el portapapeles</td> 
   <td>Falta</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Deshacer/Rehacer</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Arrastrar y soltar contenido en el marcador de posición de componente</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Arrastre y suelte el contenido directamente en el marcador de posición parsys con la creación automática de componentes<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Estado de la función: Editores de texto, tabla e imagen {#feature-status-text-table-and-image-editors}

Es una lista de las funciones que tienen el texto, la tabla y el editor de imágenes de la IU clásica, así como el estado en la IU táctil.

<table> 
 <tbody>
  <tr>
   <td><strong>Función</strong></td> 
   <td><strong>Estado </strong></td> 
   <td><strong>Comentario<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor de texto enriquecido</td> 
   <td>Completar</td> 
   <td>Se puede utilizar in-situ, en cuadro de diálogo y en pantalla completa.</td> 
  </tr>
  <tr>
   <td>Habilitar/deshabilitar complementos RTE</td> 
   <td>Completar<br /> </td> 
   <td>Se puede hacer con el <a href="/help/sites-authoring/templates.md">Editor de plantillas</a>.</td> 
  </tr>
  <tr>
   <td>Usar RTE para texto sin formato</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Vínculos y delimitador</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Mapa de caracteres</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Copiar/Pegar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Pegar desde Microsoft Word<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Buscar y reemplazar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Formatos de texto (negrita, ...)</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Subíndice y superíndice</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Justificar</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Listas (viñetas / números)</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Formato de párrafo</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Estilos de texto</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Editor de origen (Editar HTML)<br /> </td> 
   <td>Completar<br /> </td> 
   <td>Solo disponible en cuadro de diálogo y pantalla completa.<br /> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Corrector ortográfico</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Tabla (Editor de tablas incrustado)</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Deshacer/Rehacer<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Permitir imágenes en línea</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editor de tablas</td> 
   <td>Completar</td> 
   <td>Se puede utilizar in-situ, en cuadro de diálogo y en pantalla completa.<br /> </td> 
  </tr>
  <tr>
   <td>Arrastrar y soltar imagen en celda de tabla<br /> </td> 
   <td>Completar</td> 
   <td>Utilizable en línea</td> 
  </tr>
  <tr>
   <td>Editor de imágenes<br /> </td> 
   <td>Completar</td> 
   <td>Se puede utilizar in-situ, en cuadro de diálogo y en pantalla completa.<br /> </td> 
  </tr>
  <tr>
   <td>Habilitar/deshabilitar complementos IPE</td> 
   <td>Completar</td> 
   <td>Ahora hay una interfaz de usuario en el <a href="/help/sites-authoring/templates.md">Editor de plantillas</a>.</td> 
  </tr>
  <tr>
   <td>Complemento IPE: Recortar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Voltear</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Deshacer/Rehacer</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Mapa de imagen</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Rotar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Zoom</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Estado de la función: Herramientas {#feature-status-tools}

Esta es una lista de varias herramientas que tiene la IU clásica y del estado de la IU táctil.

<table> 
 <tbody>
  <tr>
   <td><strong>Función<br /> </strong></td> 
   <td><strong>Estado<br /> </strong></td> 
   <td><strong>Comentario</strong></td> 
  </tr>
  <tr>
   <td>Administración de tareas</td> 
   <td>Reemplazado</td> 
   <td>6.0 ha introducido <a href="/help/sites-authoring/projects.md">Proyectos y Tareas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Bandeja de entrada de workflow<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configuración de plantilla de flujo de trabajo a página (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Falta<br /> </td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Etiquetado de la IU de administración<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Centro de control de MSM/modelo</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IU del Administrador de modelos</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaz de usuario de configuración de despliegue</td> 
   <td>Falta</td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Interfaz de usuario, grupos y permisos<br /> </td> 
   <td>Principalmente completado<br /> </td> 
   <td>Para editar permisos avanzados, utilice la IU clásica.<br /> </td> 
  </tr>
  <tr>
   <td>Purgar versiones (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Falta</td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Comprobador de vínculos externos (<code>/etc/linkchecker.html</code>)</td> 
   <td>Falta</td> 
   <td>Usar IU clásica.<br /> </td> 
  </tr>
  <tr>
   <td>Editor masivo (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Falta<br /> </td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
 </tbody>
</table>

