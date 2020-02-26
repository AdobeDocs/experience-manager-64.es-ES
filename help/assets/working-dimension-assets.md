---
title: Uso de recursos de Adobe Dimension
seo-title: Uso de recursos de Adobe Dimension
description: Uso de recursos de dimensión de Adobe en AEM 3D.
seo-description: Uso de recursos de dimensión de Adobe en AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Uso de recursos de Adobe Dimension {#working-with-adobe-dimension-assets}

El paquete de funciones AEM 3D es compatible con los recursos (`.dn` archivos) de dimensión de Adobe en Recursos AEM, Sitios AEM y Pantallas AEM.

Un nuevo visor 3D basado en el estándar abierto glTF proporciona funciones de vista previa y de vista de sitios y pantallas para los recursos de dimensión de Adobe.

## Acerca del servicio de conversión basado en la nube {#about-the-cloud-based-conversion-service}

Cuando se carga un recurso de dimensión en AEM, se reenvía una copia del archivo a un servicio en la nube gestionado por Adobe alojado en Amazon AWS. Este servicio convierte el formato de archivo Dimension propiedad de Adobe al formato glTF estándar abierto. El modelo 3D convertido se empaqueta como un glTF binario (`.glb`). AEM almacena el modelo convertido con el recurso de dimensión principal como una representación.

Puede configurar el formato de `.glb` conversión de una de las dos formas siguientes (consulte [Instalación y configuración de AEM 3D](install-config-3d.md) para obtener instrucciones):

* Incluya extensiones específicas de Adobe para maximizar la calidad visual al utilizar el visor glTF de Adobe para ver los recursos de dimensión en Recursos AEM, Sitios AEM o Pantallas AEM. Esto hace que las `.glb` representaciones sean incompatibles con la mayoría de las aplicaciones de terceros.
* Excluya extensiones específicas de Adobe para lograr la compatibilidad de la `.glb` representación con aplicaciones de terceros. Esto limita la calidad visual cuando se visualiza en Recursos AEM, Sitios AEM o Pantallas AEM (por ejemplo, sin iluminación IBL) para simular la calidad de las aplicaciones típicas de terceros.

La transferencia de los archivos Dimension/glTF a o desde Amazon AWS y su almacenamiento temporal en AWS están totalmente protegidos. Estos archivos persisten en Amazon AWS durante un tiempo mínimo; normalmente, no más de unos minutos durante operaciones normales.

Para habilitar la compatibilidad con los recursos de dimensión, debe obtener las credenciales de Adobe para acceder al servicio de conversión. See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Si instala y utiliza las credenciales proporcionadas, comprenderá y acepta que los recursos de Adobe Dimension 3D se transferirán y procesarán en el servicio de conversión gestionado por Adobe y basado en la nube alojado en Amazon AWS.

### Visualización en AEM Assets {#viewing-on-aem-assets}

El paquete de funciones AEM 3D incluye un nuevo visor basado en el estándar abierto glTF que se utiliza para ver los recursos de Adobe Dimension. Este visor se selecciona automáticamente al abrir un archivo Dimension o un glTF comprimido en la vista de detalles en Recursos AEM o con el componente 3D en Sitios AEM.

Tenga en cuenta que la interfaz de usuario del visor de GlTF es algo diferente del visor 3D estándar que se utiliza para todos los demás tipos de recursos 3D.

#### See also the following: {#see-also-the-following}

* [Notas](/help/release-notes/aem3d-release-notes.md) de la versión de AEM 3D para restricciones y limitaciones aplicables a los recursos Dn y al visor GlTF.
* [Uso del componente](using-the-3d-sites-component.md) Sitios 3D para propiedades de componentes específicas de los recursos de dimensión de Adobe.
* [Instalación y configuración de AEM 3D](install-config-3d.md) para configurar el servicio de conversión basado en la nube.

