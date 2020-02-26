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
source-git-commit: 901a923b6ab2b6bee1738d2b8f1928571c8019cb

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

* Se ha actualizado la lista de dispositivos para la vista previa del sitio adaptable, que ahora incluye Apple iPhone 8, 8 Plus y X, y Samsung S7
* Se ha movido la ubicación predeterminada de la información de diseño de plantilla de /etc/design para admitir configuraciones específicas de sitios en /conf. Los clientes que realizan la actualización desde versiones anteriores de AEM pueden seguir utilizando /etc/design.

### Desarrollo de componentes y plantillas {#component-amp-template-development}

* Antecedentes del proyecto 13+, consulte [Github para ver las notas](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)de la versión.
* Versión 1.3.1 de HTL; consulte [Github para ver las notas de versión](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componentes principales 2.0.4 (o superior); consulte [Github para ver las notas de versión](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema de estilos

   * Se ha agregado un concepto completamente nuevo para asignar clases CSS a componentes y permitir que los usuarios del Editor de páginas seleccionen entre un subconjunto de estilos mediante la interfaz de usuario
   * Se ha agregado la capacidad de definir el nombre del elemento HTML representado alrededor del componente, por ejemplo: &lt;main>, &lt;aside>

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
   * Elementos de datos preconfigurados para modelos de fragmento de contenido (texto de una sola línea, texto de varias líneas, número, booleano, fecha y hora, enumeración, referencia de contenido, etiquetas)

* Se ha mejorado el uso del editor de fragmentos de contenido de AEM

   * Información general sobre la visualización de todos los elementos
   * Edición a pantalla completa para elementos únicos
   * Funciones mejoradas de edición de texto enriquecido (listas con viñetas, listas numeradas, sangría, hipervínculos, tablas, buscar&amp;reemplazar, revisión ortográfica)

* Se han añadido opciones de salida mejoradas para los fragmentos de contenido de AEM

   * Nuevo componente Fragmento de contenido, como parte de Componentes principales. [Consulte código en GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Compatibilidad con Content Services con la salida JSON mediante Sling Model Exporter

### Fragmentos de experiencias {#experience-fragments}

* Se han introducido bloques de creación de fragmentos de experiencia para facilitar el reuso del contenido entre las variaciones de fragmentos de experiencia agrupando componentes y permitiendo una referencia sencilla dentro de las variaciones.
* Se ha agregado la capacidad de agregar fragmentos de experiencia a proyectos de traducción mediante el carril de referencia
* Permite iniciar flujos de trabajo con fragmentos de experiencia mediante el carril de la línea de tiempo
* El carril de referencia ahora muestra dónde se está utilizando un fragmento de experiencia en AEM
* La configuración de las ubicaciones de plantilla ahora permite a los autores definir en un nivel global o de carpeta qué plantillas de fragmento de experiencia pueden utilizar
* La búsqueda con facetas ahora admite filtros avanzados, como publicados o no publicados, exportados a medios sociales y Adobe Target
* Se agregó un inicio de sesión único en los medios sociales al exportar fragmentos de experiencias a Pinterest o Facebook
* Fragmentos de experiencia AEM integrados con Adobe Target. Al sincronizar fragmentos de experiencia con Target se crearán ofertas en Adobe Target que se podrán utilizar con el Compositor de experiencias visuales de Target para incrustarlas en cualquier experiencia habilitada para Target.

### Traducción {#translation}

* Se ha mejorado el uso de los proyectos de traducción de AEM:

   * Compatibilidad con varios idiomas de destino en un proyecto
   * Opción para promocionar y eliminar automáticamente lanzamientos de traducción
   * Opción de programar la ejecución periódica de proyectos de traducción (diaria, semanal, mensual, anual)
   * Mosaico de proyectos de traducción mejorado con información de estado más detallada

* Se ha introducido la actualización de memoria de traducción inversa para actualizar la memoria de traducción en el sistema de administración de traducción de terceros después de editar el contenido local en AEM
* Los flujos de trabajo de traducción ahora admiten raíces de idiomas agrupadas
* Se ha agregado la capacidad de asignar nombres arbitrarios a raíces de idioma y utilizar la propiedad JCR para asignar al código ISO
* Las actualizaciones de traducción inteligente ahora reconocen las nuevas páginas agregadas a una rama maestra de idioma
* Se han introducido informes de estado de traducción en la vista de lista Administración de sitios

### Administración de varios sitios (MSM) {#multi-site-management-msm}

* Escalabilidad de MSM mejorada mediante el uso de un índice basado en Oak frente a una memoria (LiveCopyIndex)

### Lanzamientos {#launches}

* Se ha mejorado el rendimiento de los lanzamientos que contienen un árbol de sitios grande y si hay muchos lanzamientos activos
* Se ha mejorado la promoción automática y la publicación de inicios con varias páginas raíz.
* Se ha corregido un problema que impedía que la vista previa del dispositivo interactivo funcionara con páginas editadas en el contexto de un inicio.

### Simulación y segmentación de contenido {#content-targeting-simulation}

* Carpetas de soporte para organizar segmentos en función del sitio o contexto (CQ-94620)
* Se ha movido la ubicación predeterminada de los segmentos a /conf para que tengan listas de segmentos específicas de sitio/contexto.

### AEM y Adobe Target  {#aem-amp-adobe-target-nbsp}

* Fragmentos de experiencia AEM integrados con Adobe Target. Al sincronizar fragmentos de experiencia con Target se crearán ofertas en Adobe Target que se podrán utilizar con el Compositor de experiencias visuales de Target para incrustarlas en cualquier experiencia habilitada para Target.
* Ya se incluye la versión 63 de mbox.js de Adobe Target. Adobe recomienda cambiar la implementación a at.js.
* Ahora se incluye la versión 1.2.2 de at.js. Adobe recomienda utilizar la administración dinámica de etiquetas (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para aprovisionar at.js en el sitio.

### AEM y Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ahora se incluye. Adobe recomienda cambiar la implementación a AppMeasurement.js
* Ahora se incluye AppMeasurement.js 1.8.0. Adobe recomienda utilizar Administración dinámica de etiquetas (DTM) o Inicio [de plataforma de](https://www.adobe.com/enterprise/cloud-platform/launch.html) Adobe Experience para aprovisionar AppMeasurement.js en el sitio.

## Complemento de Communities {#communities-add-on}

Consulte la [página de las notas de versión de Communities](/help/release-notes/communities-release-notes.md)

## Complemento de pantallas {#screens-add-on}

* Se ha añadido compatibilidad para que los reproductores de pantallas se conecten a los servidores de publicación de AEM para las descargas de comandos y controles y de canales (en lugar de hacerlo directamente al autor de AEM).
* Se ha agregado la capacidad de agrupar asignaciones de canal en programaciones
* Las asignaciones de canal ahora tienen fecha de inicio y finalización
* El panel del dispositivo ahora muestra la versión del shell del reproductor y el firmware
* La lista de tableros de dispositivos muestra el estado de la conexión del reproductor
* Se ha añadido la compatibilidad con el sistema operativo Google Chrome para AEM Screens Player
* Se agregó Microsoft Windows 10 para AEM Screens Player

