---
title: Notas de versión de AEM Assets
seo-title: AEM Assets
description: Notas de la versión específicas de Adobe Experience Manager 6.4 Assets.
seo-description: Notas de la versión específicas de Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
translation-type: tm+mt
source-git-commit: 55e904cb24bac68c0b1bbea59786cb4c0c711d61
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 3%

---

# Notas de versión de AEM Assets {#aem-assets-release-notes}

Las funciones clave, los aspectos destacados y las mejoras realizadas en AEM 6.4 Assets se describen en estas notas de la versión. Para obtener información detallada, siga los vínculos proporcionados.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link en Creative Cloud para empresas optimiza la colaboración entre creativos y especialistas en marketing en el proceso de creación de contenido. Es una nueva funcionalidad nativa en Creative Cloud para empresas que proporciona una conexión a AEM Assets directamente desde Adobe Photoshop, Adobe Illustrator o Adobe InDesign, sin abandonar estas herramientas.

Para obtener más información sobre la capacidad, los requisitos previos y cómo acceder a él, consulte la página [Adobe Asset Link](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html).

## Etiquetas inteligentes mejoradas (con tecnología Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 introduce la funcionalidad Etiquetas inteligentes mejoradas basada en inteligencia artificial, además de las etiquetas inteligentes que se lanzaron en AEM 6.3.

* El servicio de contenido inteligente obtiene información sobre la taxonomía empresarial del cliente y la utiliza para etiquetar automáticamente los recursos digitales con etiquetas relevantes del cliente, además de etiquetas genéricas. Mejora significativamente la capacidad de detección de activos y reduce el tiempo de comercialización.
* Adobe Sensei alimenta el servicio de contenido inteligente, que le permite entrenar el algoritmo de reconocimiento de imágenes en su taxonomía empresarial. A continuación, esta inteligencia de contenido se utiliza para aplicar etiquetas relevantes en recursos similares.

Para utilizar las etiquetas inteligentes mejoradas de AEM Assets, instale el [Service Pack más reciente de AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=es).

## Búsqueda de traducción inteligente (con tecnología Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 presenta la función de búsqueda de traducción inteligente para admitir escenarios de búsqueda multilingües. Los clientes con equipos distribuidos globalmente en varias configuraciones regionales ahora tienen acceso a búsquedas en diferentes idiomas sin tener que pasar por flujos de trabajo de traducción costosos y laboriosos.

* La consulta de búsqueda se traduce sin intervención manual.
* Las etiquetas inteligentes se generan en inglés y se traducen automáticamente a otros idiomas.
* La búsqueda multilingüe se ha creado utilizando la biblioteca de código abierto Apache Joshua, que admite más de 50 idiomas.

## Experiencia del usuario {#user-experience}

AEM 6.4 ofrece mejoras significativas en la experiencia del usuario en áreas de exploración, búsqueda, recursos de varias páginas y herramientas de administración. Detalles a continuación:

Mejoras en la exploración

* Nuevo carril del árbol de contenido para desplazarse rápidamente por la jerarquía de recursos. En combinación con la vista de lista, esto restaura el modelo de interacción de IU clásica para examinar las jerarquías de recursos.
* Nuevos métodos abreviados del teclado, como m para mover recursos, p para abrir la página de propiedades, Ctrl + C para copiar la operación y muchos más.
* Se ha mejorado el desplazamiento y la experiencia de carga diferida en la vista de tarjeta y lista para explorar un gran número de recursos.
* Se ha mejorado la vista de tarjeta con compatibilidad con tarjetas de distintos tamaños en función de la configuración de la vista.
* Se ha mejorado la experiencia de detalles de recursos con la capacidad de ver, navegar hasta el recurso &quot;anterior&quot; o &quot;siguiente&quot; junto con el número de recursos, el recurso actual.

Mejoras de búsqueda

* Nuevo botón Buscar hacia atrás con la capacidad de desplazarse a un elemento de búsqueda y volver a la misma posición en los resultados de búsqueda sin volver a ejecutar la consulta de búsqueda.
* Los nuevos resultados de la búsqueda muestran el número de resultados de la búsqueda.
* Se ha mejorado el filtro de búsqueda de tipo de archivo con la capacidad de filtrar los resultados de búsqueda en función de tipos de mime detallados como JPG, PNG y PSD, en comparación con las opciones anteriores de imagen, documento y multimedia.
* Se han mejorado los filtros de búsqueda con marcas de hora precisas en lugar de la funcionalidad del control deslizante de tiempo anterior.

Mejoras en los recursos de varias páginas

* Experiencia de exploración de recursos de varias páginas mejorada con un número reducido de clics.
* Se ha mejorado la compatibilidad de comentarios y anotaciones con todos ellos recopilados en el nivel de recurso en lugar de en el nivel de página.

Mejoras en las herramientas de administración

* Selector de propiedades mejorado en las herramientas de administración de metadatos, búsqueda e informes con paso a paso Tipo y capacidad de exploración para simplificar la experiencia de administración.

Catálogos

* Se ha mejorado la experiencia del usuario y la alineación con la interfaz de usuario de Plantillas. Para obtener más información, consulte [Productor de catálogos](../sites-administering/catalog-producer.md).

## Metadatos {#metadata}

AEM 6.4 incluye varias funciones avanzadas de administración de metadatos para administrar los metadatos a escala y aplicar la integridad de los metadatos mediante reglas y validaciones. Estas son las funcionalidades clave:

* La nueva función de exportación masiva de metadatos para exportar metadatos (todos, selectivos) de un gran número de recursos en formato CSV para editarlos, compartirlos e integrarlos de terceros.
* Nueva función de importación masiva de metadatos para importar archivos CSV para agregar nuevos metadatos, actualizar los metadatos existentes para varios recursos de una sola vez. Esta operación es asincrónica y no obstaculiza el rendimiento del sistema. Una vez finalizado, se notifica al usuario mediante AEM sistema de notificaciones.
* Nuevos metadatos en cascada y contextuales mediante la herramienta Esquema de metadatos. Ahora es posible definir cadenas de dependencias y asignaciones de valor entre campos. También puede definir el contexto en el que se muestran u ocultan los campos de formulario de metadatos. De este modo, solo puede mostrar campos relevantes en cualquier momento según los valores de otros campos.

## Informes {#reports}

AEM 6.4 ofrece mejoras significativas en la creación de informes de activos:

* El nuevo marco de informes escalable (para repositorios grandes) de nivel empresarial que aplica trabajos de Sling para el procesamiento asincrónico de solicitudes de informes. Puede programar el informe en una fecha y hora específicas. También puede agregar columnas personalizadas a un informe.
* Los nuevos informes de OOTB que suelen solicitar los clientes, como Uso del disco, Archivos, Compartidos en vínculos, Publicar en Brand Portal y Formación sobre etiquetas inteligentes.
* Nueva interfaz de usuario de creación y administración de informes con opciones específicas, capacidad para acceder a informes archivados, ver estado de ejecución de informes (éxito, error, cola, etc.).

## Brand Portal {#brand-portal}

* **6.3 Actualización** de plataforma: Brand Portal se ha actualizado de AEM 6.0 a AEM 6.3, con nuevas funciones y mejoras de rendimiento.
* **Publicación paralela**: Pueden producirse hasta réplicas entre AEM Assets y Brand Portal (anteriormente 1), lo que mejora significativamente el rendimiento de la publicación
* **Publicación** de facetas de búsqueda y esquema: Posibilidad de publicar esquemas de metadatos y facetas de búsqueda personalizadas en Brand Portal, lo que elimina la duplicación de esfuerzos.
* **Publicación de etiquetas masivas**: Posibilidad de publicar taxonomía (junto con jerarquía) en Brand Portal, lo que elimina la duplicación de esfuerzos.
* **Registro propio o Solicitud de acceso**: Flujo de trabajo para usuarios no registrados en Brand Portal.
* **Notificación de mantenimiento en la aplicación (en pantalla)**: Las notificaciones se muestran con bastante antelación para evitar interrupciones en el negocio.
* **Mejoras en los informes**: Hay tres informes de OOTB disponibles: descargas, publicar y compartir vínculos.
* **Restricciones** basadas en DRM: Una vez caducado un recurso con licencia, ya no estará disponible para su descarga desde Brand Portal.

## Aplicación de escritorio de AEM {#aem-desktop-app}

AEM aplicación de escritorio se ha actualizado a la versión 1.8, que es compatible con la AEM 6.4. La lista completa de cambios para AEM aplicación de escritorio se proporciona en un documento dedicado [AEM notas de la versión de la aplicación de escritorio](https://docs.adobe.com/content/help/es-ES/experience-manager-desktop-app/using/release-notes.html).\
A continuación se muestra una lista de AEM aspectos destacados de la aplicación de escritorio desde que se publicó AEM 6.3:

* Capacidad para cargar carpetas jerárquicas en segundo plano.
* IU para supervisar las cargas de recursos en segundo plano.
* Mejoras en el almacenamiento en caché, incluida una interfaz de usuario para administrar los parámetros de almacenamiento en caché.
* Soporte más amplio para configuraciones de autenticación AEM (SAML/SSO) y proxy de red.
* Compatibilidad: fácil acceso a los registros desde la interfaz de usuario.
* Se han mejorado la estabilidad y las correcciones para los problemas de los clientes.

Para acceder más fácilmente a la documentación y a las prácticas recomendadas, existe la siguiente documentación:

* [Guía del usuario](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html), dirigida a los usuarios finales que trabajan con la aplicación.
* [Guía](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html) de instalación, dirigida a los administradores que configuran AEM y AEM aplicación de escritorio para trabajar juntos

## Almacenamiento de información en niveles {#tiered-storage}

AEM 6.4 incluye un conjunto de funcionalidades que soportan diversas preferencias de almacenamiento de información en niveles e implementan reglas de ciclo vital. Las opciones de almacenamiento también admiten (pero no están limitadas) nubes públicas: AWS o Azure.

* La capacidad para que los usuarios seleccionen y luego cambien la clase de almacenamiento a voluntad y definan las reglas para el almacenamiento de los activos de una clase a otra o administran el ciclo de vida de sus activos.
* La capacidad de los usuarios para reducir su coste de almacenamiento seleccionando un AWS o Azure diferente.

Para obtener una descripción general de las plataformas admitidas, consulte la [Documentación de requisitos técnicos](../sites-deploying/technical-requirements.md).

## Grupo de usuarios cerrado {#closed-user-group}

* En AEM 6.4, Closed User Group (Grupo de usuarios cerrado) o CUG (CUG) proporciona una forma de restringir el acceso a carpetas en instancias de publicación, es una opción de IU táctil para agregar entidades principales a través de la página de propiedades de carpetas en el nivel de carpeta y se aplican a todas las carpetas y subcarpetas/recursos que hay dentro.
* En el modo de publicación, si se configura un CUG y se habilita la autorización en una carpeta, se redirige a los usuarios a una página de inicio de sesión cuando intentan acceder a la carpeta. Por lo tanto, los usuarios autorizados solo pueden acceder a la carpeta y a sus recursos después de iniciar sesión correctamente. Por lo tanto, CUG restringe el acceso de lectura a un árbol determinado en el repositorio de contenido para todos excepto para los principales seleccionados.

## Complemento de Dynamic Media {#dynamic-media-add-on}

Dynamic Media en la versión 6.4 es compatible con un nuevo modo: el recurso maestro se carga y administra con la interfaz de usuario web de AEM Assets, mientras que el servicio de envío en la nube de Dynamic Media gestiona las representaciones dinámicas y otras funciones de Dynamic Media.

En este modo (introducido primero con el lanzamiento de los [AEM 6.3 Feature Packs 14410 y 18912](https://helpx.adobe.com/es/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), los usuarios se benefician de las funciones de administración de recursos de extremo a extremo y de Dynamic Media que utilizan la moderna interfaz de usuario web de AEM Assets y siguen aprovechando los servicios de envío compatibles con Dynamic Media Classic (Scene7), incluidas las direcciones URL de envío, que no cambian.

Además, AEM 6.4 presenta nuevas funciones con tecnología Adobe Sensei, mejoras para medios emergentes como VR y 3D, visores de Dynamic Media y compatibilidad con fragmentos de experiencias en imágenes interactivas y banners de carrusel.

### Recorte inteligente (con tecnología Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* El recorte inteligente proporciona automáticamente un recorte no destructivo de imágenes para preservar el punto de interés para el diseño interactivo. Puede obtener una vista previa de las sugerencias recortadas y ajustarlas manualmente, si es necesario.
* Esta función también permite la generación automatizada de muestras para imágenes de productos. La generación automatizada de muestras ayuda a agregar automáticamente muestras de color, muestras de patrones o ambas a imágenes de productos.

Consulte la documentación [Perfiles de imagen](../assets/image-profiles.md) para obtener más información.

Consulte también la documentación [Añadir recursos de Dynamic Media a páginas](../assets/adding-dynamic-media-assets-to-pages.md) para obtener más información sobre el uso del Recorte inteligente con el componente Dynamic Media.

### Imágenes inteligentes {#smart-imaging}

* Las imágenes inteligentes aprovechan las características de visualización únicas de cada usuario para ofrecer automáticamente imágenes optimizadas para su experiencia, lo que resulta en un mejor rendimiento y participación.
* Las imágenes se convierten automáticamente a diferentes formatos según las capacidades del explorador.
* La configuración de calidad de imagen se determina en el explorador y se aplica respectivamente. Esta inteligencia mantiene el rendimiento de carga de imágenes aceptable para ancho de banda limitado y velocidades de conexión lentas.

Consulte la documentación [Imágenes inteligentes](../assets/imaging-faq.md) para obtener más información.

### Mejoras emergentes en los medios y el visualizador {#emerging-media-amp-viewer-enhancements}

* Se admiten nuevos visualizadores, que proporcionan al usuario experiencias mejores e inmersivas.
* El visor panorámico le ayuda a interactuar con el usuario y le ofrece la posibilidad de experimentar mejor las escenas, propiedades, ubicaciones y paisajes de la sala. Consulte la documentación [Imágenes panorámicas](../assets/panoramic-images.md) para obtener más información.

* El visor de VR proporciona una experiencia inmersiva para propiedades, ubicaciones y paisajes.
* Visor de imágenes verticales optimizado para imágenes de productos.
* Mejoras en la accesibilidad del teclado.
