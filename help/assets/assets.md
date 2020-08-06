---
title: Acerca de AEM Assets
description: Conozca qué es la administración de recursos digitales, sus casos de uso y la oferta de activos AEM Adobe.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 077cc39c5ed47371a4e3fae1e991209c7bfe6b80
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 49%

---


# Acerca de AEM Assets {#about-assets}

Assets es una herramienta de administración de activos digitales (DAM) que está totalmente integrada con la plataforma AEM y permite a su empresa compartir y distribuir recursos digitales. Los usuarios de una organización pueden administrar y almacenar imágenes, vídeos, documentos, clips de audio o medios enriquecidos tales como archivos Flash, así como acceder a ellos, a fin de utilizarlos en Internet, para imprimirlos o para distribuirlos de forma digital.

## What is Digital Asset Management (DAM)? {#what-is-digital-asset-management}

Assets proporciona un método de uso compartido y distribución en toda la empresa de los activos digitales clave de una organización. Los usuarios de una organización pueden almacenar, administrar y acceder a recursos digitales como imágenes, gráficos, audio, vídeo y documentos a través de una interfaz web (o una carpeta CIFS o WebDAV).

AEM Assets está completamente integrado en AEM y permite hacer lo siguiente:

* Añadir y compartir imágenes, documentos, audio y vídeo en diversos formatos de archivo.
* Administrar activos agrupándolos por etiquetas, cuadros o estrellas (sus favoritos). Añadir anotaciones a los recursos.
* Buscar recursos por nombres de archivo, texto completo de documentos, fechas, tipo de documento y etiquetas.
* Añadir o editar información de metadatos para los activos. Automáticamente, se genera una versión de los metadatos junto con el activo correspondiente. Los metadatos de activos se pueden importar o exportar.
* Realizar funciones de edición de imágenes, como escalar y añadir filtros de imagen. Importar y exportar varios activos digitales de forma simultánea mediante una carpeta WebDAV o CIFS.
* Usar los flujos de trabajo y las notificaciones para permitir el procesamiento y la descarga de forma conjunta de cualquier grupo de activos y administrar los derechos de acceso a los activos.

### AEM Assets está completamente integrado con AEM funciones WCM {#aem-assets-fully-integrated-in-cq-wcm}

AEM Assets está totalmente integrado con CQ WCM y la funcionalidad está disponible mediante el icono DAM:

<!-- TBD: Update image for branding -->

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

A continuación, se puede acceder a los recursos administrados en CQ DAM mediante el buscador de contenido de WCM:

<!-- TBD: Update image for branding -->

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png)

>[!NOTE]
>
>La navegación básica de la interfaz de usuario es la misma que el resto de AEM: consulte [Visión General de la Consola](/help/sites-authoring/qg-page-authoring.md) GUI para obtener más detalles.

### Administración de recursos digitales frente al componente de imagen {#digital-asset-management-versus-image-component}

Al determinar si desea colocar una imagen en AEM Assets o utilizar el componente Imagen, tenga en cuenta el ciclo vital de la imagen:

* Si la imagen tiene el mismo ciclo de vida que la página, utilice el componente Imagen.
* Si la imagen tiene un ciclo de vida independiente, por ejemplo, si utiliza la imagen dos veces o fuera de WCM, emplee AEM Assets.

## What are digital assets? {#what-are-digital-assets}

Un recurso es un documento digital, una imagen, un vídeo o audio (o parte del mismo) que puede tener varias representaciones y subrecursos (por ejemplo, capas en un archivo de Photoshop, diapositivas en un archivo de PowerPoint, páginas en un PDF o archivos en un ZIP).

Un activo es, en esencia, un binario más metadatos, representaciones y subactivos. Consulte la [Guía de rendimiento de DAM](/help/sites-deploying/assets-performance-sizing.md) para obtener información detallada.

>[!CAUTION]
>
>La carga y/o edición de un gran volumen de recursos (especialmente imágenes) puede afectar al rendimiento de la instancia de CQ.

### AEM Assets terminology {#aem-assets-terminology}

Cuando se trabaja con activos digitales en AEM, debe conocer los siguientes términos:

* **Colección:** Colección de recursos, ya sea en función de la ubicación física (carpeta), las propiedades comunes (carpeta de búsqueda guardada) o la selección de usuarios (carpetas de caja de luz).

* **Metadatos:** Los recursos tienen metadatos; por ejemplo, autor, fecha de caducidad, Información de DRM (Digital Rights Management), etc. Los metadatos están sujetos a control de acceso. AEM Assets admite los siguientes esquemas comunes de metadatos predefinidos:

   * **Dublin Core**: incluyendo autor, descripción, fecha, asunto, etc.
   * **IPTC**: incluyendo evento, modelo, ubicación, etc.
   * **WCM**: incluyendo las propiedades de la página, en tiempo y fuera de tiempo, etc.

* **Etiquetado:** Los recursos se pueden etiquetar y clasificar. Consulte Utilización de etiquetas y Administración de etiquetas.

* **Representaciones:** Una representación es la representación binaria de un recurso. Los recursos siempre tienen una representación principal, que es la del archivo cargado. Pueden tener una multitud de representaciones adicionales que se crean, por ejemplo, por medio de flujos de trabajo personalizados o al cargar un recurso. Las representaciones pueden tener tamaños y resoluciones distintas, y tener agregadas marcas de agua o cualquier otra característica modificada.

* **Versiones:** Al generar una versión, se crea una instantánea de los recursos digitales en un momento específico. Los activos se pueden restaurar a versiones anteriores. See [versioning in AEM Assets](managing-assets-touch-ui.md#asset-versioning).

* **Subrecursos:** Los subrecursos son recursos que conforman un recurso, por ejemplo, capas en un archivo Adobe Photoshop o páginas en un archivo PDF. En AEM Assets, puede administrar los subactivos igual que los activos.

### Cómo trabajar con activos {#how-to-work-with-assets}

Las acciones se realizan sobre activos o colecciones. Sirven para crear o modificar activos, colecciones y representaciones. Muchas de las acciones básicas que se realizan en los activos (cargar, eliminar, actualizar o guardar subactivos) desencadenan flujos de trabajo preconfigurados. Estos se activan automáticamente en AEM Assets y se describen en detalle en los controladores de medios de AEM Assets.

Las tareas que puede realizar con estos flujos de trabajo preconfigurados son las siguientes:

* Guarde el recurso en el repositorio o elimínelo.
* Extraer y guardar metadatos para el recurso; los elementos de metadatos individuales se guardan como XMP.
* Generar representaciones y miniaturas del recurso; incluido el cambio de tamaño y el recorte automáticos cuando sea necesario.
* Transcodificar el recurso cuando sea necesario. Por ejemplo, los vídeos para uso en móviles e Internet se transcodifican con 24 fotogramas por segundo y se descargan con 30 fotogramas por segundo. El audio para uso en móviles e Internet se transcodifica con 128 kbp y se descarga con 192 kbp.

Los flujos de trabajo también se pueden aplicar manualmente. Consulte en [Controladores de medios de AEM Assets](media-handlers.md) la lista de flujos de trabajo predeterminados.

## AEM DAM y AEM MediaLibrary {#cq-dam-vs-cq-medialibrary}

See [AEM DAM and AEM MediaLibrary](medialibrary.md) for information on the differences.
