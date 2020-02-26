---
title: Notas de versión de AEM Assets
seo-title: AEM Assets
description: Notas de la versión específicas de Recursos Adobe Experience Manager 6.4.
seo-description: Notas de la versión específicas de Recursos Adobe Experience Manager 6.4.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: 2411f1aa2853a161603d15917102d5cf1a8139b6

---


# Notas de versión de AEM Assets {#aem-assets-release-notes}

Estas notas de la versión incluyen las funciones clave, los aspectos destacados y las mejoras realizadas en Recursos AEM 6.4. Para obtener información detallada, siga los vínculos proporcionados.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link en Creative Cloud para empresas optimiza la colaboración entre creativos y especialistas en marketing en el proceso de creación de contenido. Es una nueva función nativa en Creative Cloud para empresas que ofrece una conexión a Recursos AEM directamente desde Adobe Photoshop, Adobe Illustrator o Adobe InDesign: sin dejar estas herramientas.

Para obtener más información sobre la capacidad, los requisitos previos y cómo acceder a ellos, consulte la página de [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) .

## Etiquetas inteligentes mejoradas (con tecnología Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 incorpora la funcionalidad de etiquetas inteligentes mejoradas basadas en inteligencia artificial, además de las etiquetas inteligentes que se lanzaron en AEM 6.3.

* Smart Content Service aprende la taxonomía comercial del cliente y la utiliza para etiquetar automáticamente los recursos digitales con etiquetas relevantes del cliente, además de etiquetas genéricas. Mejora significativamente la capacidad de detección de activos y reduce el tiempo de salida al mercado.
* Adobe Sensei potencia el servicio de contenido inteligente, que le permite formar el algoritmo de reconocimiento de imágenes en su taxonomía comercial. A continuación, esta inteligencia de contenido se utiliza para aplicar etiquetas relevantes a recursos similares.

Para utilizar etiquetas inteligentes mejoradas de AEM Assets, instale el [último Service Pack de AEM 6.4](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Búsqueda de traducción inteligente (con tecnología Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 incorpora la capacidad de búsqueda de traducción inteligente para admitir escenarios de búsqueda multilingües. Los clientes con equipos distribuidos globalmente en varias configuraciones regionales ahora tienen acceso a la búsqueda en diferentes idiomas sin tener que pasar por flujos de trabajo de traducción costosos y lentos.

* La consulta de búsqueda se traduce sin intervención manual.
* Las etiquetas inteligentes se generan en inglés y se traducen automáticamente a otros idiomas.
* La búsqueda multilingüe se construye con la biblioteca de código abierto Apache Joshua que admite más de 50 idiomas.

## Experiencia del usuario {#user-experience}

AEM 6.4 ofrece mejoras significativas en la experiencia del usuario en áreas de exploración, búsqueda, recursos de varias páginas y herramientas de administración. Detalles a continuación:

Mejoras en la exploración

* Nuevo carril del árbol de contenido para navegar rápidamente por una jerarquía de recursos. En combinación con la vista de lista, esto restaura el modelo de interacción de la IU clásica para examinar las jerarquías de recursos.
* Nuevos métodos abreviados de teclado como m para mover recursos, p para abrir la página de propiedades, Ctrl + C para copiar la operación y muchos más.
* Se ha mejorado el desplazamiento y la experiencia de carga diferida en la vista de tarjeta y lista para explorar un gran número de recursos.
* Se mejoró la vista de tarjeta con compatibilidad con tarjetas de distintos tamaños según la configuración de la vista.
* Se ha mejorado la experiencia de detalles de recursos con la posibilidad de ver, navegar hasta el recurso &quot;anterior&quot; o &quot;siguiente&quot; junto con el número de recursos, el recurso actual.

Mejoras de búsqueda

* Nuevo botón Buscar hacia atrás con capacidad para desplazarse a un elemento de búsqueda y volver a la misma posición en los resultados de búsqueda sin volver a ejecutar la consulta de búsqueda.
* El recuento de resultados de la nueva búsqueda muestra el número de resultados de la búsqueda.
* Se mejoró el filtro de búsqueda de tipo de archivo con la capacidad de filtrar los resultados de búsqueda en función de tipos de MIME detallados como JPG, PNG y PSD, en comparación con las opciones anteriores de imagen, documento y multimedia.
* Se mejoraron los filtros de búsqueda con marcas de hora precisas en lugar de la funcionalidad del deslizador de tiempo anterior.

Mejoras en los recursos de varias páginas

* Se mejoró la experiencia de exploración de recursos de varias páginas con un número reducido de clics.
* Se ha mejorado la compatibilidad de comentarios y anotaciones con todos ellos recopilados en el nivel de recurso en lugar de en el nivel de página.

Mejoras en las herramientas de administración

* Se mejoró el selector de propiedades en las herramientas de administración para metadatos, búsqueda e informes con la función de avance de tipo y exploración para simplificar la experiencia de administración.

Catálogos

* Se ha mejorado la experiencia del usuario y la alineación con la interfaz de usuario de Plantillas. Para obtener más información, consulte [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadatos {#metadata}

AEM 6.4 incluye varias funciones avanzadas de administración de metadatos para administrar los metadatos a escala y garantizar la integridad de los metadatos mediante reglas y validaciones. Estas son las funciones clave:

* Nueva capacidad de exportación masiva de metadatos para exportar (todos, selectivos) metadatos para un gran número de recursos en formato CSV para editarlos, compartirlos e integrarlos de terceros.
* Nueva función de importación masiva de metadatos para importar archivos CSV para agregar nuevos metadatos, actualizar los metadatos existentes para varios recursos de una sola vez. Esta operación es asincrónica y no obstaculiza el rendimiento del sistema. Una vez finalizado, el usuario recibe una notificación a través del sistema de notificaciones de AEM.
* Nuevos metadatos contextuales y en cascada mediante la herramienta Esquema de metadatos. Ahora es posible definir cadenas de dependencias y asignaciones de valor entre campos. También puede definir el contexto en el que se muestran u ocultan los campos de formulario de metadatos. De este modo, solo puede mostrar los campos relevantes en cualquier momento, según los valores de otros campos.

## Informes {#reports}

AEM 6.4 ofrece mejoras significativas en la generación de informes de activos:

* Nuevo marco de informes escalable (para repositorios grandes) de nivel empresarial que aplica trabajos de Sling para el procesamiento asincrónico de solicitudes de informes. Puede programar el informe en una fecha y hora específicas. También puede agregar columnas personalizadas a un informe.
* Los nuevos informes OOTB más solicitados por clientes como Uso del disco, Archivos, Uso compartido de vínculos, Publicar en el portal de marcas y Capacitación de etiquetas inteligentes.
* Nueva interfaz de usuario de creación y administración de informes con opciones específicas, capacidad para acceder a informes archivados, ver el estado de ejecución del informe (éxito, error, cola, etc.).

## Brand Portal {#brand-portal}

* **6.3 Actualización** de plataforma: Brand Portal se ha actualizado de AEM 6.0 a AEM 6.3 con nuevas funciones y mejoras de rendimiento.
* **Publicación** paralela: Pueden producirse hasta replicaciones entre Recursos AEM y Brand Portal (anteriormente 1), lo que mejora significativamente el rendimiento de publicación
* **Publicación** de esquemas y facetas de búsqueda: Posibilidad de publicar esquemas de metadatos y facetas de búsqueda personalizadas en Brand Portal, lo que elimina la duplicación de esfuerzos.
* **Publicación** masiva de etiquetas: Posibilidad de publicar taxonomía (junto con jerarquía) en Brand Portal, lo que elimina la duplicación de esfuerzos.
* **Registro propio o Solicitud de acceso**: Flujo de trabajo para usuarios no registrados en Brand Portal.
* **Notificación** de mantenimiento en la aplicación (en pantalla): Las notificaciones se muestran con bastante antelación para evitar interrupciones en el negocio.
* **Mejoras** en los informes: Hay tres informes de OOTB disponibles: descargas, publicación y recursos compartidos de vínculos.
* **Restricciones** basadas en DRM: Una vez caducado un recurso con licencia, ya no estará disponible para su descarga desde Brand Portal.

## Aplicación de escritorio de AEM {#aem-desktop-app}

La aplicación de escritorio de AEM se ha actualizado a la versión 1.8, que es compatible con AEM 6.4. La lista completa de cambios para la aplicación de escritorio de AEM se incluye en un documento dedicado de notas [de la versión de la aplicación de escritorio de](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html) AEM.\
A continuación se muestra una lista de los aspectos destacados de la aplicación de escritorio de AEM desde el lanzamiento de AEM 6.3:

* Capacidad para cargar carpetas jerárquicas en segundo plano.
* IU para controlar las cargas de recursos en segundo plano.
* Mejoras en el almacenamiento en caché, incluida una interfaz de usuario para administrar los parámetros de almacenamiento en caché.
* Compatibilidad más amplia con las configuraciones de autenticación AEM (SAML/SSO) y el proxy de red.
* Compatibilidad: fácil acceso a los registros desde la interfaz de usuario.
* Se ha mejorado la estabilidad y las correcciones para problemas con los clientes.

Para facilitar el acceso a la documentación y a las prácticas recomendadas, se dispone de la siguiente documentación:

* [Guía](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)del usuario, dirigida a los usuarios finales que trabajan con la aplicación
* [Guía](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)de prácticas recomendadas, dirigida a usuarios finales y administradores
* [Guía](https://helpx.adobe.com/experience-manager/desktop-app/install-configure-aem-desktop-app.html)de instalación, dirigida a los administradores que configuran la aplicación de escritorio AEM y AEM para trabajar juntos

## Almacenamiento de información en niveles {#tiered-storage}

AEM 6.4 incluye un conjunto de funciones que admiten diversas preferencias de almacenamiento de información en niveles e implementan reglas de ciclo vital. Las opciones de almacenamiento también admiten (pero no están limitadas) nubes públicas: AWS o Azure.

* La capacidad de los usuarios para seleccionar y cambiar posteriormente la clase de almacenamiento a voluntad y definir reglas para el almacenamiento de recursos de una clase a otra o administrar el ciclo vital de sus activos.
* Capacidad para que los usuarios reduzcan el costo de almacenamiento seleccionando un AWS o Azure diferente.

Para obtener una descripción general de las plataformas admitidas, consulte la Documentación de requisitos [técnicos](../sites-deploying/technical-requirements.md).

## Grupo de usuarios cerrado {#closed-user-group}

* En AEM 6.4, Closed User Group o CUG permite restringir el acceso a las carpetas en las instancias de publicación. Se trata de una opción táctil de la interfaz de usuario para añadir entidades de seguridad a través de la página de propiedades de carpetas en el nivel de carpeta y se aplican a todas las carpetas y subcarpetas o recursos que se encuentren dentro.
* En el modo de publicación, si se configura un CUG y se habilita la autorización en una carpeta, se redirige a los usuarios a una página de inicio de sesión cuando intentan acceder a la carpeta. Por lo tanto, los usuarios autorizados solo pueden acceder a la carpeta y a sus recursos después de iniciar sesión correctamente. Por lo tanto, CUG restringe el acceso de lectura a un árbol determinado en el repositorio de contenido para todos los usuarios excepto los principales seleccionados.

## Dynamic Media add-on {#dynamic-media-add-on}

Dynamic Media en 6.4 es compatible con un nuevo modo: el recurso principal se carga y gestiona con la interfaz de usuario web de AEM Assets, mientras que las representaciones dinámicas y otras funciones de Dynamic Media se gestionan en segundo plano mediante el servicio de distribución en la nube de Dynamic Media.

En este modo (introducido en primer lugar con el lanzamiento de los paquetes de funciones de [AEM 6.3 14410 y 18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), los usuarios se benefician de la administración de recursos de extremo a extremo y de las funciones de medios dinámicos mediante la moderna interfaz de usuario web de Recursos AEM, y siguen aprovechando los servicios de entrega compatibles con Dynamic Media Classic (Scene7), incluidas las URL de entrega que no cambian.

Además, AEM 6.4 incorpora nuevas funciones con Adobe Sensei, mejoras para medios emergentes como VR y 3D, visores de Dynamic Media y compatibilidad con fragmentos de experiencia en imágenes interactivas y pancartas de carrusel.

### Smart Crop (con tecnología Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* El recorte inteligente proporciona automáticamente recorte no destructivo de imágenes para preservar el punto de interés para un diseño interactivo. Puede obtener una vista previa de las sugerencias recortadas y ajustarlas manualmente, si es necesario.
* Esta función también permite la generación automatizada de muestras para imágenes de productos. La generación automatizada de muestras ayuda a añadir muestras de color, muestras de patrones o ambas a las imágenes de productos automáticamente.

Consulte la documentación de perfiles [de imagen](../assets/image-profiles.md) para obtener más información.

Consulte también [Adición de recursos de medios dinámicos a páginas](../assets/adding-dynamic-media-assets-to-pages.md) para obtener más información sobre el uso de Recorte inteligente con el componente de medios dinámicos.

### Imágenes inteligentes {#smart-imaging}

* Las imágenes inteligentes aprovechan las características de visualización únicas de cada usuario para ofrecer automáticamente imágenes optimizadas para su experiencia, lo que resulta en un mejor rendimiento y participación.
* Las imágenes se convierten automáticamente a diferentes formatos según las capacidades del navegador.
* La configuración de calidad de imagen se determina en el navegador y se aplica respectivamente. Esta inteligencia mantiene el rendimiento de carga de imágenes aceptable para un ancho de banda limitado y velocidades de conexión lentas.

Consulte la documentación de imágenes [inteligentes](../assets/imaging-faq.md) para obtener más información.

### Mejoras en los nuevos medios y visores {#emerging-media-amp-viewer-enhancements}

* Se admiten nuevos visores, que proporcionan al usuario experiencias mejores y envolventes.
* El visor panorámico ayuda al usuario a interactuar con él y permite disfrutar mejor de las escenas, propiedades, ubicaciones y paisajes de la sala. Consulte la documentación [de imágenes](../assets/panoramic-images.md) panorámicas para obtener más información.

* El visor de VR ofrece una experiencia inmersiva para propiedades, ubicaciones y paisajes.
* Visor de imágenes vertical optimizado para imágenes de producto.
* Mejoras en la accesibilidad del teclado.

### 3D e integración con Dimension CC {#d-and-integration-with-dimension-cc}

Se ha introducido la integración con [Adobe Dimension CC](https://www.adobe.com/products/dimension.html) para un flujo de trabajo 3D más fluido. Para obtener más información, consulte [Uso de la documentación de recursos](../assets/assets-3d.md) 3D.