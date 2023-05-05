---
title: Base de AEM y repositorio
seo-title: AEM Foundation & Repository
description: Notas de versión específicas de Adobe Experience Manager 6.3 AEM Platform y Repositorio.
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# Base de AEM y repositorio {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Lista de cambios {#list-of-changes}

### Repositorio {#repository}

* MicroKernel de Tar de Segmento Oak

   * Modo de compactación rápida (compactación de cola) para limpieza de revisión en línea
   * Mejoras en las tasas de escritura
   * Estadísticas de operaciones de segmentos expuestas mediante JMXBean
   * Estimación de duración para la limpieza de revisión sin conexión

* Oak Mongo Microkernel

   * La limpieza continua de revisión para MongoMK reemplaza el mantenimiento de limpieza programado

* Mayor eficiencia para la limpieza de revisión en nodos de documento
* Consulte [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) y [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) para obtener una descripción general completa de los problemas corregidos.

>[!CAUTION]
>
>* La nueva versión de Oak Segment Tar presente desde AEM 6.3 requiere una migración del repositorio. Este paso es obligatorio si actualiza desde una versión anterior de TarMK o si desea cambiar la nueva Tar de segmento de otro tipo de persistencia. Para obtener más información sobre las ventajas de la nueva barra de segmentos, consulte la [Preguntas frecuentes sobre la migración a Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### Buscar e indexar {#search-amp-indexing}

* Soporte mejorado para operaciones de indexación mediante oak-run (CLI):

   * Comprobación de coherencia del índice
   * Estadísticas de indexación
   * Configuración de índice Im/Export
   * Reindexación

* Reducción del crecimiento de repositorios relacionados con Lucene para un rendimiento general del sistema mejorado
* Índices de propiedades de Lucene sincrónicas [(Más información)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explicar la consulta en el Administrador de índices ahora admite AEM sintaxis de QueryBuilder
* El Administrador de índices ahora expone las métricas de índice: tamaño, última actualización y comprobación de coherencia

### Interfaz de usuario {#user-interface}

* Se han realizado varias mejoras en la interfaz de usuario para que sea más productiva y fácil de usar.
* Nuevo carril del árbol de contenido para desplazarse rápidamente por una jerarquía. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica.
* Se ha mejorado el desplazamiento en la vista de tarjeta y lista de carpetas grandes.
* Se ha mejorado la interacción con los resultados de búsqueda: el botón de retroceso restaura el resultado de la búsqueda anterior.
* Métodos abreviados de teclado adicionales, para las acciones más comunes, como abrir un carril concreto, editar, mover y eliminar un elemento o abrir propiedades.
* Posibilidad de desactivar los métodos abreviados del teclado (habilitar/deshabilitar en Preferencias).
* Deje de mostrar marcas de hora en todas las IU relativas después de 7 días (opción predeterminada en Preferencias).

>[!CAUTION]
>
>* Adobe no tiene previsto realizar más mejoras en la IU clásica. AEM 6.4 incluye la IU clásica, y los clientes que actualicen desde versiones anteriores pueden seguir utilizándola tal cual. Tenga en cuenta que la IU clásica sigue siendo totalmente compatible mientras esté en desuso [Más información](/help/sites-deploying/ui-recommendations.md).
>


### Distribución de contenido {#content-distribution}

* Rendimiento de replicación mejorado para admitir publicaciones de recursos de gran volumen
* Compatibilidad con la autenticación OAuth 2.0 en el transporte de distribución
* Rendimiento mejorado para paquetes VLT

### Monitoreo {#monitoring}

* Una nueva Información general del sistema proporciona una vista instantánea de todas las actividades y estados del sistema relacionados con el rendimiento
* Nuevas comprobaciones de estado:

   * Detectar índices Lucene grandes
   * Estado de indexación asíncrono
   * Índices grandes de Lucene
   * Rendimiento de consultas
   * Límites de recorrido de la consulta
   * Relojes sincronizados
   * Mantenimiento del sistema - Limpieza de revisión
   * Mantenimiento del sistema: DataStore GC
   * Mantenimiento del sistema - Revisión continua GC

* El usuario ahora puede definir el ámbito de la descarga de status.zip

### Mantenimiento {#maintenance}

* Eliminación activa de los binarios de Lucene mediante una tarea de mantenimiento
* La tarea de mantenimiento de RevisionGC para MongoDB ahora está deshabilitada en favor de la Limpieza de Revisión Continua, por favor vea la sección Repositorio más arriba.
* La configuración de purga de versión permite mantener un número mínimo de versiones
* La purga de la versión se detiene al final de una ventana de mantenimiento. También se puede iniciar y detener manualmente, y continuará incrementándose con el siguiente inicio.

### Actualización {#upgrade}

* Compatibilidad con versiones anteriores: Las funciones compatibles con versiones anteriores de la versión 6.4 ayudan a que el código personalizado siga siendo compatible en la mayoría de los casos y reducen los esfuerzos de actualización.
* Evaluación de la complejidad de la actualización: Nueva herramienta de detección de patrones para evaluar la complejidad de las actualizaciones.
* Actualizaciones sostenibles: Se han introducido la superficie de la API y la clasificación de contenido para ayudarle a seguir fácilmente las prácticas recomendadas y lograr una actualización eficaz y sin problemas a la siguiente versión durante todo el ciclo de desarrollo.
* Reestructuración del repositorio: Reestructuración significativa (principalmente /etc) para facilitar las actualizaciones y promover las mejores prácticas de implementación. [Más información.](/help/sites-deploying/repository-restructuring.md)
* Consulte la [Documentación de actualización](/help/sites-deploying/upgrade.md) para obtener más información sobre estas funciones.

### Cloud Services {#cloud-services}

* Muchos Cloud Services ahora se pueden configurar mediante la IU táctil; el resto se puede configurar en la tarjeta Cloud Services heredados .
* Las carpetas Sitios y Recursos se pueden configurar con Cloud Services que se cargan según el contexto.

### Seguridad {#security}

* Interfaz de usuario de creación de usuarios mejorada y simplificada compatible con varios perfiles de usuario.
* Se ha mejorado el rendimiento de las suscripciones a grupos grandes para los usuarios.

### Proyectos y flujos de trabajo {#projects-and-workflows}

* Utilice el Editor de flujo de trabajo basado en la interfaz de usuario táctil para administrar los modelos de flujo de trabajo de forma más sencilla.
* Compatibilidad con depuración de tareas de proyecto en tareas de mantenimiento.
