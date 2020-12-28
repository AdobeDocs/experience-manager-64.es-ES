---
title: AEM Foundation y repositorio
seo-title: AEM Foundation y repositorio
description: Notas de versión específicas de la plataforma y repositorio de Adobe Experience Manager 6.3 AEM.
seo-description: Notas de versión específicas de la plataforma y repositorio de Adobe Experience Manager 6.3 AEM.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 14%

---


# AEM Foundation y repositorio {#aem-foundation-repository}

## Lista de cambios {#list-of-changes}

### Repositorio {#repository}

* MicroKernel de barra de segmentos Oak

   * Modo de compactación rápida (compactación de cola) para la limpieza de revisión en línea
   * Tasas de escritura mejoradas
   * Estadísticas de operaciones de segmentos expuestas mediante JMXBean
   * Estimación de duración para la limpieza de revisión sin conexión

* Oak Mongo Microkernel

   * Limpieza continua de revisión para MongoMK reemplaza el mantenimiento de limpieza programado

* Mejora de la eficacia de la limpieza de revisión en las novelas de Documento
* Consulte [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) y [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) para obtener una visión general completa de los problemas solucionados.

>[!CAUTION]
>
>* La nueva versión de Oak Segment Tar disponible a partir de la versión 6.3 de AEM requiere realizar una migración del repositorio. Este paso es obligatorio si está actualizando desde una versión anterior de TarMK o desea cambiar la nueva barra de segmentos de otro tipo de persistencia. Para obtener más información sobre los beneficios de la nueva barra de segmentos, consulte las [Preguntas más frecuentes sobre la migración a la barra de segmentos Oak](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

>



### Búsqueda e indexación {#search-amp-indexing}

* Soporte mejorado para operaciones de indexación mediante la ejecución en roble (CLI):

   * Comprobación de la coherencia del índice
   * Estadísticas de indexación
   * Configuración de índice Im/Export
   * Reindexación

* Reducción del crecimiento del repositorio relacionado con Lucene para mejorar el rendimiento general del sistema
* Índices de propiedades de Lucene sincrónicos [(Más información)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explicar la Consulta en el Administrador de índices ahora es compatible con AEM sintaxis de QueryBuilder
* El Administrador de índices está exponiendo ahora las métricas de índice: tamaño, última actualización y comprobación de coherencia

### Interfaz de usuario {#user-interface}

* Se han realizado varias mejoras en la interfaz de usuario para que sea más productiva y fácil de usar.
* Nuevo carril del árbol de contenido para navegar rápidamente por una jerarquía. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica.
* Se ha mejorado el desplazamiento en la vista de tarjetas y listas de carpetas grandes.
* Se mejoró la interacción con los resultados de búsqueda: el botón Atrás restaura el resultado de búsqueda anterior.
* Métodos abreviados de teclado adicionales, para las acciones más comunes, como abrir un carril concreto, editar, mover y eliminar elementos o abrir propiedades.
* Posibilidad de desactivar los métodos abreviados de teclado (activar/desactivar en Preferencias).
* Dejar de mostrar marcas de hora en toda la interfaz de usuario en relación después de 7 días (opción predeterminada en Preferencias).

>[!CAUTION]
>
>* Adobe no tiene previsto realizar más mejoras en la interfaz de usuario clásica. AEM 6.4 tiene la interfaz de usuario clásica incluida y los clientes que actualicen desde versiones anteriores pueden seguir utilizándola. Tenga en cuenta que la IU clásica sigue siendo totalmente compatible mientras se encuentra en desuso [Más información](/help/sites-deploying/ui-recommendations.md).

>



### Distribución de contenido {#content-distribution}

* Rendimiento de replicación mejorado para admitir publicaciones de recursos de gran volumen
* Compatibilidad con la autenticación OAuth 2.0 en el transporte de distribución
* Rendimiento mejorado para paquetes VLT

### Monitoreo {#monitoring}

* Una nueva información general del sistema proporciona una vista instantánea de todos los estados y actividades del sistema relacionados con el rendimiento
* Nuevas comprobaciones de estado:

   * Detectar índices Lucene grandes
   * Estado de indexación asincrónica
   * Índices grandes de Lucene
   * Rendimiento de consultas
   * Límites de recorrido de la consulta
   * Relojes sincronizados
   * Mantenimiento del sistema - Limpieza de revisión
   * Mantenimiento del sistema - DataStore GC
   * Mantenimiento del sistema - Revisión continua GC

* Ahora el usuario puede definir el ámbito de la descarga status.zip

### Mantenimiento {#maintenance}

* Eliminación activa de los binarios de Lucene mediante una tarea de mantenimiento
* La tarea de mantenimiento de RevisionGC para MongoDB ahora está deshabilitada en favor de la limpieza de revisión continua, consulte la sección Repositorio de arriba.
* La configuración de depuración de versiones permite conservar un número mínimo de versiones
* La depuración de versiones se detiene al final de una ventana de mantenimiento. También se puede iniciar y detener manualmente y continuará de forma incremental con el siguiente inicio.

### Actualización {#upgrade}

* Compatibilidad con versiones anteriores: Las funciones compatibles con versiones anteriores de 6.4 ayudan a que el código personalizado siga siendo compatible en la mayoría de los casos y reducen el esfuerzo de actualización.
* Evaluación de la complejidad de la actualización: Nueva herramienta de detección de patrones para evaluar la complejidad de las actualizaciones.
* Actualizaciones sostenibles: La superficie de API y la clasificación de contenido se han introducido para ayudarle a seguir fácilmente las optimizaciones a fin de lograr una actualización eficaz y sin fisuras a la siguiente versión durante todo el ciclo de desarrollo.
* Reestructuración del repositorio: Reestructuración significativa (principalmente /etc) para facilitar las actualizaciones y promover las mejores prácticas de implementación. [Obtener más información.](/help/sites-deploying/repository-restructuring.md)
* Consulte la [documentación de actualización](/help/sites-deploying/upgrade.md) para obtener más detalles sobre estas funciones.

### Cloud Services{#cloud-services}

* Muchos Cloud Services ahora se pueden configurar mediante la IU táctil; el resto se puede configurar en la tarjeta Cloud Services heredados.
* Las carpetas Sitios y Recursos se pueden configurar con Cloud Services cargados según el contexto.

### Seguridad {#security}

* Se ha mejorado y simplificado la interfaz de usuario para la creación de usuarios con compatibilidad con varios perfiles de usuarios.
* Se ha mejorado el rendimiento de los miembros de grupos grandes para los usuarios.

### Proyectos y flujos de trabajo {#projects-and-workflows}

* Toque el Editor de flujo de trabajo basado en la interfaz de usuario para administrar los modelos de flujo de trabajo de forma más sencilla.
* Soporte para purgar tareas de proyectos en tareas de mantenimiento.

