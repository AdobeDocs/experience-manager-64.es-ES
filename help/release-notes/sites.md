---
title: Notas de la versión de AEM Sites
seo-title: AEM Sites
description: Notas de la versión específicas de Adobe Experience Manager 6.4 Sites.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# Notas de la versión de AEM Sites {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Sites {#sites}

Consulte las siguientes mejoras para AEM Sites 6.4 en detalle:

### Administración del sitio {#site-administration}

* Nuevo carril del árbol de contenido para desplazarse rápidamente por la jerarquía de un sitio. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica para examinar un sitio.
* Se ha mejorado el desplazamiento en la vista de tarjeta y lista de carpetas grandes.
* Se ha mejorado la interacción con los resultados de búsqueda: el botón de retroceso restaura el resultado de la búsqueda anterior.
* Métodos abreviados de teclado adicionales, para las acciones más comunes, como abrir un carril concreto, editar, mover y eliminar páginas o abrir propiedades.
* Posibilidad de desactivar los métodos abreviados del teclado (habilitar/deshabilitar en Preferencias).
* Deje de mostrar marcas de hora en todas las IU relativas después de 7 días (opción predeterminada en Preferencias).

### Editor de página {#page-editor}

* Lista de dispositivos actualizada para la vista previa del sitio adaptable, que ahora incluye Apple iPhone 8, 8 Plus y X, y Samsung S7
* Se ha movido la ubicación predeterminada para la información de diseño de plantilla de /etc/design para admitir configuraciones específicas de sitios en /conf. Los clientes que actualizan desde versiones AEM anteriores pueden seguir usando /etc/design.

### Desarrollo de componentes y plantillas {#component-amp-template-development}

* Tipo de archivo del proyecto 13+, consulte [Github para notas de la versión](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL versión 1.3.1, consulte [Github para notas de la versión](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componentes principales 2.0.4+, consulte [Github para notas de la versión](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema de estilos

   * Se ha agregado un concepto completamente nuevo para asignar clases CSS a componentes y permitir que los usuarios del Editor de páginas seleccionen entre un subconjunto de estilos a través de la interfaz de usuario
   * Se ha añadido la capacidad de definir el nombre del elemento HTML representado alrededor del componente, por ejemplo &lt;main>, &lt;aside>

* Sistema de cuadrícula para contenedor de diseño, consulte [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor de plantillas y políticas

   * Las políticas ahora admiten configuraciones del sistema de estilos por componente, por contenedor y por plantilla.
   * Compatibilidad mejorada para definir el diseño en plantillas de componentes editables

* Sitio de referencia We.Retail 3.0, consulte [Github para notas de la versión](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM incluye la versión 1.12.4 de la biblioteca jQuery para proporcionar la máxima compatibilidad con el código personalizado existente. El Adobe ha realizado modificaciones para abordar problemas de seguridad conocidos.

### Fragmentos de contenido y editor {#content-fragments-amp-editor}

* Se han introducido los modelos de contenido estructurados como base para los fragmentos de contenido

   * IU del editor de modelo
   * Elementos de datos preconfigurados para modelos de fragmento de contenido (texto de una sola línea, texto multilínea, número, booleano, fecha y hora, enumeración, referencia de contenido, etiquetas)

* Se ha mejorado la facilidad de uso del editor de fragmentos de contenido AEM

   * Información general sobre la vista de todos los elementos
   * Edición en pantalla completa para elementos individuales
   * Funciones mejoradas de edición de texto enriquecido (listas con viñetas, listas numeradas, sangría, hipervínculos, tablas, buscar&amp;reemplazar, revisión ortográfica)

* Se han añadido opciones de salida mejoradas para AEM fragmentos de contenido

   * Nuevo componente Fragmento de contenido, como parte de los componentes principales. [Consulte código en GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Compatibilidad con Content Services con la salida JSON a través de Sling Model Exporter

### Fragmentos de experiencias {#experience-fragments}

* Se han introducido los bloques de creación de fragmentos de experiencia para facilitar el reuso del contenido entre variaciones de fragmentos de experiencias mediante la agrupación de componentes y la fácil referencia dentro de variaciones.
* Se ha añadido la capacidad de añadir fragmentos de experiencia a proyectos de traducción mediante el carril de referencia
* Se ha añadido la capacidad de iniciar flujos de trabajo con fragmentos de experiencias a través del carril de la cronología
* El carril de referencia ahora muestra dónde se está utilizando un fragmento de experiencia en AEM
* La configuración de las ubicaciones de plantillas ahora permite a los autores definir a nivel global o de carpeta qué plantillas de fragmento de experiencia se pueden utilizar
* La búsqueda por facetas ahora admite filtros avanzados, como publicado/no publicado, exportado a medios sociales y Adobe Target
* Se ha añadido un inicio de sesión único en medios sociales al exportar fragmentos de experiencias a Pinterest o Facebook
* Fragmentos de experiencia AEM integrados con Adobe Target. Al sincronizar fragmentos de experiencias con Target se crearán ofertas en Adobe Target que se podrán usar con el Compositor de experiencias visuales de Target para incrustarlas en cualquier experiencia habilitada para Target.

### Traducción {#translation}

* Se ha mejorado la facilidad de uso de AEM proyectos de traducción:

   * Compatibilidad con varios idiomas de destino en un proyecto
   * Opción para promocionar y eliminar automáticamente los lanzamientos de traducción
   * Opción para programar la ejecución recurrente de proyectos de traducción (diaria, semanal, mensual, anual)
   * mosaicos de proyecto de traducción mejorados con información de estado más detallada

* Se ha introducido la actualización de memoria de traducción inversa, para actualizar la memoria de traducción en el sistema de administración de traducción de terceros después de las ediciones de contenido local en AEM
* Los flujos de trabajo de traducción ahora admiten raíces de idioma agrupadas
* Se ha agregado la capacidad de asignar nombres arbitrarios a raíces de idioma y usar la propiedad JCR para asignar al código ISO
* Las actualizaciones de traducción inteligente ahora reconocen nuevas páginas que se agregaron a una rama maestra de idioma
* Se ha introducido la creación de informes de estado de traducción en la vista de lista Administración de sitios

### Administración de varios sitios (MSM) {#multi-site-management-msm}

* Mejora de la escalabilidad de MSM mediante el uso de un índice basado en Oak frente a memoria (LiveCopyIndex)

### Lanzamientos {#launches}

* Se ha mejorado el rendimiento de los lanzamientos que contienen un árbol de sitios grande y si hay muchos lanzamientos activos
* Se ha mejorado la promoción automática y la publicación de lanzamientos con varias páginas raíz.
* Se ha corregido un problema que impedía que la vista previa del dispositivo interactivo funcionara con páginas editadas en el contexto de un lanzamiento.

### Simulación y segmentación de contenido {#content-targeting-simulation}

* Carpetas de soporte para organizar segmentos basados en el sitio/contexto (CQ-94620)
* Se ha movido la ubicación predeterminada de los segmentos a /conf para tener listas de segmentos específicas del sitio/contexto.

### AEM y Adobe Target  {#aem-amp-adobe-target-nbsp}

* Fragmentos de experiencia AEM integrados con Adobe Target. Al sincronizar fragmentos de experiencias con Target se crearán ofertas en Adobe Target que se podrán usar con el Compositor de experiencias visuales de Target para incrustarlas en cualquier experiencia habilitada para Target.
* Ahora se incluye la versión 63 de mbox.js de Adobe Target. Adobe recomienda cambiar la implementación a at.js.
* Ahora se incluye la versión 1.2.2 de at.js. Adobe recomienda utilizar Dynamic Tag Management (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para aprovisionar at.js en el sitio.

### AEM y Adobe Analytics {#aem-amp-adobe-analytics}

* Ahora se incluye s_code.js H.27.5. Adobe recomienda cambiar la implementación a AppMeasurement.js
* Ahora se incluye AppMeasurement.js 1.8.0. Adobe recomienda utilizar Dynamic Tag Management (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para aprovisionar AppMeasurement.js en el sitio.

## Complemento de Communities {#communities-add-on}

Consulte [Página Notas de la versión de Communities](/help/release-notes/communities-release-notes.md)

## Complemento Screens {#screens-add-on}

* Se ha agregado compatibilidad para que los reproductores de Screens se conecten a AEM servidores de publicación para el comando y control y las descargas de canal (en lugar de hacerlo directamente a AEM autor).
* Se ha agregado la capacidad de agrupar asignaciones de canal en Programas
* Las asignaciones de canal ahora tienen fecha de inicio y finalización
* El panel del dispositivo ahora muestra la versión del shell del reproductor y el firmware
* La lista del panel de dispositivos muestra el estado de conexión del reproductor
* Se ha agregado compatibilidad con Google Chrome OS para AEM Screens Player
* Se ha añadido Microsoft Windows 10 para AEM Screens Player
