---
title: Estado de la función de IU táctil
seo-title: Touch UI Feature Status
description: Notas de la versión específicas de la IU táctil de Adobe Experience Manager 6.3.
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 15%

---

# Estado de la función de IU táctil {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Con la versión 6.4 de AEM, la variable [La IU clásica está en desuso](/help/release-notes/deprecated-removed-features.md). Adobe no tiene previsto realizar más mejoras en la IU clásica y se recomienda a los usuarios que aprovechen las nuevas y potentes funciones disponibles en la IU táctil.

A partir de la versión 6.0, AEM introdujo una nueva interfaz de usuario denominada &quot;IU táctil&quot; (también conocida como &quot;IU táctil&quot;) que se alinea con Adobe Marketing Cloud y con las directrices generales de la interfaz de usuario de Adobe. Al alcanzarse casi la partición de funciones, esta se ha convertido en la IU estándar en AEM con la interfaz heredada orientada al escritorio denominada &quot;IU clásica&quot;.

Aunque la mayoría de las funciones están presentes en la IU táctil, hay funciones que aún no se han completado y que se añadirán en futuras versiones.

La siguiente lista muestra el estado actual de las capacidades tal como se implementan en la AEM 6.4.

Para obtener recomendaciones para clientes que actualizan a AEM 6.4, consulte [Interfaz de usuario de Recommendations para clientes](/help/sites-deploying/ui-recommendations.md) para obtener más información.

>[!NOTE]
>
>Tenga en cuenta que esta página solo cubre la paridad de características con la IU clásica.
>
>Las funciones añadidas y exclusivas a la IU táctil que no están presentes en la IU clásica no aparecen en la lista.

>[!NOTE]
>
>Esta lista se esfuerza por ser completa, pero no debe considerarse exhaustiva.

## Leyenda {#legend}

* **Completar**: La función está totalmente disponible en la IU táctil
* **Principalmente**: La función está disponible principalmente en la IU táctil.
* **Falta**: La función no está presente en la IU táctil; la IU clásica debe utilizarse para realizar esta acción.
* **Reemplazado**: La función se reemplazó con una nueva implementación que funciona de forma diferente.
* **Eliminado**: La función ya no existe en la IU táctil y no se reemplazará.

## Estado de la función: Administrador de sitios {#feature-status-sites-admin}

Esta es una lista de funcionalidades de la IU clásica Administrador del sitio ( `/siteadmin`) tiene y el estado en la IU táctil ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funcionalidad<br /> </strong></td> 
   <td><strong>Estado<br /> </strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Navegar por la jerarquía del sitio</td> 
   <td>Completar<br /> </td> 
   <td>AEM 6.4 introduce una <a href="/help/sites-authoring/basic-handling.md#content-tree">vista de árbol de contenido</a>.</td> 
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
   <td>Búsqueda</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiar/pegar página (Duplicar)</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mover páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar páginas</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar páginas sin derechos de replicación</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicar posteriormente</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Árbol de publicación</td> 
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
   <td>Bloquear/desbloquear</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ver/editar propiedades</td> 
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
   <td>Acciones de Livecopy (lanzamiento)</td> 
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

## Estado de la función: Editor de página {#feature-status-page-editor}

Esta es una lista de funciones del editor de páginas de la IU clásica ( `/cf#`) tiene y el estado en la opción táctil ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funcionalidad</strong></td> 
   <td><strong>Estado</strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Editar páginas web</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar páginas web móviles<br /> </td> 
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
   <td>Editar ofertas</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editar modelos de flujos de trabajo<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Código: Editar y previsualizar</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Vista previa interactiva<br /> </td> 
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
   <td>Desplegar página</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Iniciar y mostrar flujo de trabajo</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Gestión de paquetes de flujo de trabajo</td> 
   <td>Principalmente</td> 
   <td>Completamente accesible en la IU táctil. La carga útil de varios flujos de trabajo se sigue mostrando en la IU clásica.<br /> </td> 
  </tr>
  <tr>
   <td>Bloquear/desbloquear página</td> 
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
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mover página</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">mover páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Eliminar página</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">eliminar páginas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostrar referencias</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/author-environment-tools.md#references">consulte la lista de referencia detallada</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Registro de auditorías</td> 
   <td>Eliminado</td> 
   <td>Usar el administrador del sitio y <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">abrir carril de actividad</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Crear versión</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">crear nuevas versiones</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Restaurar versión</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">restaurar versiones</a>.</td> 
  </tr>
  <tr>
   <td>Cambiar lanzamientos</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-authoring/launches-promoting.md">cambiar entre lanzamientos</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traducir página</td> 
   <td>Eliminado</td> 
   <td>Utilice el administrador del sitio para <a href="/help/sites-administering/tc-manage.md">añadir página a proyectos de traducción</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Deformación de tiempo (elija fecha/hora y busque el sitio tal y como se vio)<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Definir permisos</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaz de usuario de Client Context<br /> </td> 
   <td>Reemplazado</td> 
   <td>Utilice la variable <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> IU en adelante.</td> 
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
   <td>Lista de componentes del portapapeles</td> 
   <td>Falta</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Deshacer, Rehacer</td> 
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

Esta es una lista de las funciones que tienen la IU clásica Texto, Tabla y Editor de imágenes, así como el estado en la IU táctil.

<table> 
 <tbody>
  <tr>
   <td><strong>Funcionalidad</strong></td> 
   <td><strong>Estado </strong></td> 
   <td><strong>Comentar<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor de texto enriquecido</td> 
   <td>Completar</td> 
   <td>Se puede utilizar in situ, en el cuadro de diálogo y en pantalla completa.</td> 
  </tr>
  <tr>
   <td>Habilitar/deshabilitar complementos RTE</td> 
   <td>Completar<br /> </td> 
   <td>Se puede realizar utilizando la variable <a href="/help/sites-authoring/templates.md">Editor de plantillas</a>.</td> 
  </tr>
  <tr>
   <td>Usar RTE para texto sin formato</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Vínculos y anclaje</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Mapa de caracteres</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento RTE: Copiar/pegar</td> 
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
   <td>Complemento RTE: Listas (viñetas/números)</td> 
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
   <td>Complemento RTE: Editor de origen (HTML de edición)<br /> </td> 
   <td>Completar<br /> </td> 
   <td>Solo disponible en el cuadro de diálogo y en la pantalla completa.<br /> </td> 
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
   <td>Editor de tabla</td> 
   <td>Completar</td> 
   <td>Se puede utilizar in situ, en el cuadro de diálogo y en pantalla completa.<br /> </td> 
  </tr>
  <tr>
   <td>Arrastrar y soltar imagen en celda de tabla<br /> </td> 
   <td>Completar</td> 
   <td>Utilizable en línea</td> 
  </tr>
  <tr>
   <td>Editor de imágenes<br /> </td> 
   <td>Completar</td> 
   <td>Se puede utilizar in situ, en el cuadro de diálogo y en pantalla completa.<br /> </td> 
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
   <td>Complemento IPE: Girar</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Deshacer/Rehacer</td> 
   <td>Completar<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Complemento IPE: Mapa de imágenes</td> 
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

Esta es una lista de las distintas herramientas que la IU clásica tiene y el estado en la IU táctil.

<table> 
 <tbody>
  <tr>
   <td><strong>Funcionalidad<br /> </strong></td> 
   <td><strong>Estado<br /> </strong></td> 
   <td><strong>Comentar</strong></td> 
  </tr>
  <tr>
   <td>Administración de tareas</td> 
   <td>Reemplazado</td> 
   <td>6,0 introducidos <a href="/help/sites-authoring/projects.md">Proyectos y tareas</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Bandeja de entrada del flujo de trabajo<br /> </td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configuración de flujo de trabajo a plantilla de página (<code>/etc/workflow/wcm/templates.html</code>)</td> 
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
   <td>Interfaz de usuario del Administrador de modelos</td> 
   <td>Completar</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaz de usuario de configuración de lanzamiento</td> 
   <td>Falta</td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
  <tr>
   <td>Interfaz de usuario, grupos y permisos<br /> </td> 
   <td>Finalizado principalmente<br /> </td> 
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
   <td>Utilice la IU clásica.<br /> </td> 
  </tr>
  <tr>
   <td>Editor masivo (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Falta<br /> </td> 
   <td>Utilice la IU clásica.</td> 
  </tr>
 </tbody>
</table>
