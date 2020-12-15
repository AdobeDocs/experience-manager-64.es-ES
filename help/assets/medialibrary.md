---
title: Compare las funciones disponibles en AEM Assets y AEM Media Library
description: Preguntas más frecuentes sobre AEM Assets y AEM Media Library, incluidas las diferencias.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---


# AEM Assets y Biblioteca de medios de AEM {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM) Assets es una parte integral de la plataforma AEM. Esta integración suave se considera una ventaja importante de la AEM y garantiza la consistencia en gestor de contenido y alta productividad para los autores de contenido.

## Preguntas frecuentes {#frequently-asked-questions}

### ¿Qué es AEM Assets? {#what-is-aem-assets}

AEM Assets es una aplicación de la Plataforma de AEM que permite a nuestros clientes gestionar sus recursos digitales (imágenes, vídeos, documentos y clips de audio) en un repositorio basado en web. AEM Assets incluye compatibilidad con metadatos, representaciones, el buscador de administración de recursos digitales y la interfaz de usuario de administración de AEM Assets.

### ¿Qué es la biblioteca de medios AEM? {#what-is-the-aem-media-library}

La biblioteca de medios de AEM es una parte designada del repositorio de contenido de WCM AEM donde se almacenan las imágenes y otros recursos compartidos. La biblioteca de medios utiliza las funciones de administración de recursos digitales de AEM WCM.

### ¿Qué obtengo de AEM Assets que no forma parte de AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Las funciones únicas que solo están disponibles para los clientes de AEM Assets son:

1. la capacidad para extraer y editar metadatos que no sean título, etiquetas y descripción.
1. el administrador de AEM Assets, disponible en la pantalla de bienvenida, haciendo clic en el segundo botón al lado de `siteadmin`.
1. Todos los pasos del flujo de trabajo relacionados con la administración de recursos digitales, a saber, la ingestión de recursos AEM, la eliminación de AEM Assets, el manejo de subrecursos de AEM Assets y la extracción de metadatos de AEM Assets.
1. bibliotecas que incluyen `dam` espacio de paquete im.

El uso de estas funciones requiere una licencia válida de AEM Assets.

### ¿AEM Assets está disponible como paquete independiente? {#is-aem-assets-available-as-a-separate-package}

No. Para facilitar la instalación e implementación, todas las aplicaciones y complementos AEM se entregan en un único paquete con todas las funcionalidades incluidas. Esto no implica que tenga permiso para utilizar todas las funciones del paquete.

#### Quiero editar metadatos de recursos digitales. ¿Necesito AEM Assets? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Si planea editar metadatos que no sean título, descripción y etiquetas, es necesario otorgar licencias de AEM Assets.

#### Deseo cambiar automáticamente el tamaño de las imágenes al importarlas. ¿Necesito AEM Assets? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

No. El cambio de tamaño y la transformación automática de imágenes estáticas basada en el flujo de trabajo, así como la capacidad de administrar representaciones, forman parte de AEM biblioteca de medios. Estas funciones no requieren una licencia de AEM Assets.

### Quiero cambiar el tamaño de las imágenes con un componente de imagen personalizado. ¿Necesito AEM Assets? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

El componente de imagen forma parte de AEM WCM. La biblioteca de gráficos que utiliza el componente de imagen (pero también AEM Assets) forma parte de la plataforma de AEM y no requiere una licencia de AEM Assets.

### ¿Cómo puedo evitar que mis usuarios utilicen AEM Assets si no he obtenido la licencia de AEM Assets? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Puede eliminar todos los flujos de trabajo, componentes, taxonomías, opciones específicos de AEM Assets y el administrador de AEM Assets de AEM. Al hacerlo, evita que los usuarios utilicen accidentalmente las funciones de AEM Assets que no obtuvo la licencia.

### Quiero añadir imágenes a una página y recortar y cambiar el tamaño de estas imágenes. ¿Necesito AEM Assets? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

En este caso de uso no es necesario comprar AEM Assets, incluso el uso de la biblioteca de medios no es necesario para utilizar imágenes en un sitio web, ya que el componente de imagen inteligente permite cargar imágenes directamente en la página.

>[!MORELIKETHIS]
>
>* [Lista detallada de las diferencias de características](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

