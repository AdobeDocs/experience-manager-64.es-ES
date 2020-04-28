---
title: Compare las funciones disponibles en Recursos AEM y Biblioteca de medios AEM
description: Preguntas más frecuentes sobre Recursos AEM y Biblioteca de medios AEM, incluidas las diferencias.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968

---


# AEM Assets y Biblioteca de medios de AEM {#aem-assets-vs-aem-medialibrary}

Recursos Adobe Experience Manager (AEM) es una parte integral de la plataforma AEM. Esta integración suave se considera una ventaja importante de AEM y garantiza la coherencia en el gestor de contenido y la alta productividad de los creadores de contenido.

## Preguntas frecuentes {#frequently-asked-questions}

### ¿Qué es AEM Assets? {#what-is-aem-assets}

AEM Assets es una aplicación de la plataforma AEM que permite a los clientes gestionar sus recursos digitales (imágenes, vídeos, documentos y clips de audio) en un repositorio basado en web. Recursos AEM incluye compatibilidad con metadatos, representaciones, el buscador de Digital Asset Management y la interfaz de usuario de AEM Assets Administration.

### ¿Qué es AEM Media Library? {#what-is-the-aem-media-library}

AEM Media Library es una parte designada del repositorio de contenido de AEM WCM, donde se almacenan imágenes y otros recursos compartidos. La biblioteca de medios utiliza las funciones de administración de recursos digitales de AEM WCM.

### ¿Qué puedo obtener de Recursos AEM que no forman parte de AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Las funciones únicas que solo están disponibles para los clientes de Recursos AEM son:

1. la capacidad para extraer y editar metadatos que no sean título, etiquetas y descripción.
1. el administrador de AEM Assets, disponible en la pantalla de bienvenida haciendo clic en el segundo botón situado junto al `siteadmin`.
1. Todos los pasos del flujo de trabajo relacionados con la administración de recursos digitales, a saber, la ingestión de recursos AEM, la eliminación de recursos AEM, la gestión de subrecursos de AEM Assets y la extracción de metadatos de AEM Assets.
1. bibliotecas, incluido `dam` el espacio del paquete im.

El uso de estas funciones requiere una licencia válida de Recursos AEM.

### ¿AEM Assets está disponible como paquete independiente? {#is-aem-assets-available-as-a-separate-package}

No. Para facilitar la instalación y la implementación, todas las aplicaciones y complementos de AEM se entregan en un único paquete con todas las funciones incluidas. Esto no implica que tenga permiso para utilizar todas las funciones del paquete.

#### Quiero editar metadatos de recursos digitales. ¿Necesito Recursos AEM? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Si tiene previsto editar metadatos que no sean título, descripción y etiquetas, deberá obtener una licencia de Recursos AEM.

#### Deseo cambiar automáticamente el tamaño de las imágenes al importarlas. ¿Necesito Recursos AEM? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

No. El cambio de tamaño y la transformación automática de imágenes estáticas basada en el flujo de trabajo, así como la capacidad de gestionar representaciones, forman parte de la biblioteca de medios de AEM. Estas funciones no requieren una licencia de Recursos AEM.

### Quiero cambiar el tamaño de las imágenes con un componente de imagen personalizado. ¿Necesito Recursos AEM? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

El componente de imagen forma parte de AEM WCM. La biblioteca de gráficos que utiliza el componente de imagen (pero también AEM Assets) forma parte de la plataforma AEM y no requiere una licencia de Recursos AEM.

### ¿Cómo puedo evitar que mis usuarios utilicen Recursos AEM si no he otorgado licencias de Recursos AEM? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Puede eliminar todos los flujos de trabajo, componentes, taxonomías, opciones específicos de Recursos AEM y el administrador de Recursos AEM de AEM. De este modo, evita que los usuarios utilicen accidentalmente las funciones de Recursos AEM que no obtuvo la licencia.

### Quiero añadir imágenes a una página y recortar y cambiar el tamaño de estas imágenes. ¿Necesito Recursos AEM? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

En este caso de uso no es necesario comprar Recursos AEM, incluso el uso de la biblioteca de medios no es necesario para utilizar imágenes en un sitio web, ya que el componente de imagen inteligente permite cargar imágenes directamente en la página.

>[!MORELIKETHIS]
>
>* [lista detallada de las diferencias de características](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

