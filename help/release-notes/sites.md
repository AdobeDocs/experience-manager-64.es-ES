---
title: Notas de versión de AEM Sites
seo-title: AEM Sites
description: Notas de versión específicas de Adobe Experience Manager 6.4 Sites.
seo-description: Notas de versión específicas de Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 13%

---


# AEM Sites Notas de la versión {#aem-sites-release-notes}

## Sites {#sites}

Consulte las siguientes mejoras de AEM Sites 6.4 detalladamente:

### Administración de sitios {#site-administration}

* Nuevo carril del árbol de contenido para navegar rápidamente por la jerarquía del sitio. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica para explorar un sitio.
* Se ha mejorado el desplazamiento en la vista de tarjetas y listas de carpetas grandes.
* Se mejoró la interacción con los resultados de búsqueda: el botón Atrás restaura el resultado de búsqueda anterior.
* Métodos abreviados de teclado adicionales, para las acciones más comunes, como abrir un carril concreto, editar, mover y eliminar páginas o abrir propiedades.
* Posibilidad de desactivar los métodos abreviados de teclado (activar/desactivar en Preferencias).
* Dejar de mostrar marcas de hora en toda la interfaz de usuario en relación después de 7 días (opción predeterminada en Preferencias).

### Editor de página {#page-editor}

* Lista de dispositivos actualizada para la previsualización de sitios adaptable, que ahora incluye Apple iPhone 8, 8 Plus y X, y Samsung S7
* Se ha movido la ubicación predeterminada de la información de diseño de plantilla de /etc/design para admitir configuraciones específicas de sitios en /conf. Los clientes que actualizan desde versiones anteriores de AEM pueden seguir usando /etc/design.

### Desarrollo de componentes y plantillas {#component-amp-template-development}

* Project Archetype 13+, consulte [Github para obtener las notas de la versión](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* Versión 1.3.1 de HTL; consulte [Github para ver las notas de versión](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componentes principales 2.0.4 (o superior); consulte [Github para ver las notas de versión](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema de estilos

   * Se ha añadido un concepto completamente nuevo para asignar clases CSS a componentes y permitir que los usuarios del Editor de páginas seleccionen un subconjunto de estilos mediante la interfaz de usuario
   * Capacidad añadida para definir el nombre del elemento HTML representado alrededor del componente, por ejemplo: &lt;main>, &lt;aside>

* Sistema de cuadrícula para contenedores de diseño; consulte [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor de plantillas y políticas

   * Las políticas ahora admiten configuraciones de sistema de estilo por componente, por contenedor y por plantilla.
   * Se ha mejorado la compatibilidad con la definición del diseño en plantillas de componentes editables

* Sitio de referencia We.Retail 3.0; consulte [Github para ver las notas de versión](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM incluye la versión 1.12.4 de la biblioteca jQuery para proporcionar la máxima compatibilidad con el código personalizado existente. Adobe ha realizado varias modificaciones para solucionar problemas de seguridad conocidos.

### Fragmentos de contenido y editor {#content-fragments-amp-editor}

* Se han presentado modelos de contenido estructurado como base para los fragmentos de contenido

   * IU del editor de modelos
   * Elementos de datos preconfigurados para modelos de fragmento de contenido (texto de una sola línea, texto de varias líneas, número, booleano, fecha y hora, lista desglosada, referencia de contenido, etiquetas)

* Se ha mejorado el uso del editor de fragmentos de contenido de AEM

   * Información general sobre la vista de todos los elementos
   * Edición a pantalla completa para elementos únicos
   * Funciones mejoradas de edición de texto enriquecido (listas con viñetas, listas numeradas, sangría, hipervínculos, tablas, buscar&amp;reemplazar, revisión ortográfica)

* Opciones de salida mejoradas añadidas para fragmentos de contenido AEM

   * Nuevo componente Fragmento de contenido, como parte de Componentes principales. [Consulte código en GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Compatibilidad con Content Services con la salida JSON mediante Sling Model Exporter

### Fragmentos de experiencias {#experience-fragments}

* Se han introducido bloques de creación de fragmentos de experiencia para facilitar el reuso del contenido entre las variaciones de fragmentos de experiencia agrupando componentes y permitiendo una referencia sencilla dentro de las variaciones.
* Se añadió la capacidad de añadir fragmentos de experiencia a proyectos de traducción mediante el carril de referencia
* Se añadió la capacidad de inicio de flujos de trabajo con fragmentos de experiencia mediante el carril de la línea de tiempo
* El carril de referencia ahora muestra dónde se está utilizando un fragmento de experiencia en AEM
* La configuración de las ubicaciones de plantilla ahora permite a los autores definir en un nivel global o de carpeta qué plantillas de fragmento de experiencia pueden utilizar
* La búsqueda con facetas ahora admite filtros avanzados, como publicados o no publicados, exportados a medios sociales y Adobe Target
* Inicio de sesión añadido en un solo medio social al exportar fragmentos de experiencia a Pinterest o Facebook
* Fragmentos de experiencia AEM integrados con Adobe Target. La sincronización de fragmentos de experiencia con Destinatario creará ofertas en Adobe Target que se pueden utilizar con el Compositor de experiencias visuales de Destinatario para incrustarlas en cualquier experiencia habilitada para Destinatario.

### Traducción {#translation}

* Se ha mejorado el uso de AEM proyectos de traducción:

   * Compatibilidad con varios idiomas de destinatario en un proyecto
   * Opción para promocionar y eliminar automáticamente lanzamientos de traducción
   * Opción de programar la ejecución periódica de proyectos de traducción (diaria, semanal, mensual, anual)
   * Mosaico de proyectos de traducción mejorado con información de estado más detallada

* Se ha introducido la actualización de memoria de traducción inversa para actualizar la memoria de traducción en el sistema de administración de traducción de terceros después de editar el contenido local en AEM
* Los flujos de trabajo de traducción ahora admiten raíces de idiomas agrupadas
* Capacidad añadida para asignar nombres arbitrarios a raíces de idioma y utilizar la propiedad JCR para asignar al código ISO
* Las actualizaciones de traducción inteligente ahora reconocen las nuevas páginas agregadas a una rama maestra de idioma
* Sistema de informes de estado de traducción introducido en la vista de lista de administración de sitios

### Administración de varios sitios (MSM) {#multi-site-management-msm}

* Escalabilidad de MSM mejorada mediante el uso de un índice basado en Oak frente a una memoria (LiveCopyIndex)

### Lanzamientos {#launches}

* Se ha mejorado el rendimiento de los lanzamientos que contienen un árbol de sitios grande y si hay muchos lanzamientos activos
* Se ha mejorado la promoción automática y la publicación de inicios con varias páginas raíz.
* Se ha corregido un problema que impedía que la previsualización del dispositivo interactivo funcionara con páginas editadas en el contexto de un inicio.

### Simulación y segmentación de contenido {#content-targeting-simulation}

* Carpetas de soporte para organizar segmentos en función del sitio o contexto (CQ-94620)
* Se ha movido la ubicación predeterminada de los segmentos a /conf para que tengan listas de segmentos específicas del sitio o contexto.

### AEM y Adobe Target  {#aem-amp-adobe-target-nbsp}

* Fragmentos de experiencia AEM integrados con Adobe Target. La sincronización de fragmentos de experiencia con Destinatario creará ofertas en Adobe Target que se pueden utilizar con el Compositor de experiencias visuales de Destinatario para incrustarlas en cualquier experiencia habilitada para Destinatario.
* Se ha incluido la versión 63 de Adobe Target mbox.js. Adobe recomienda cambiar la implementación a at.js.
* Ahora se incluye la versión 1.2.2 de at.js. Adobe recomienda utilizar la administración dinámica de etiquetas (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para aprovisionar at.js en el sitio.

### AEM y Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ahora se incluye. Adobe recomienda cambiar la implementación a AppMeasurement.js
* Ahora se incluye AppMeasurement.js 1.8.0. Adobe recomienda utilizar la administración dinámica de etiquetas (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para aprovisionar AppMeasurement.js en el sitio.

## Complemento de Communities {#communities-add-on}

Consulte la [página de las notas de versión de Communities](/help/release-notes/communities-release-notes.md)

## Complemento de pantallas {#screens-add-on}

* Se ha añadido la compatibilidad con que los reproductores de pantallas se conecten a AEM servidores de publicación para descargas de comandos y control y canales (en lugar de hacerlo directamente a AEM autor).
* Capacidad añadida para agrupar asignaciones de canales en programaciones
* Las asignaciones de canales ahora tienen inicios y fecha de finalización
* El Panel del dispositivo ahora muestra la versión del shell del reproductor y del firmware
* La lista del Panel del dispositivo muestra el estado de la conexión del reproductor
* Compatibilidad añadida con el sistema operativo Google Chrome para AEM Screens Player
* Microsoft Windows 10 añadido para AEM Screens Player
