---
title: Uso de recursos de Adobe Dimension
seo-title: Uso de recursos de Adobe Dimension
description: Uso de recursos de Adobe Dimension en AEM 3D.
seo-description: Uso de recursos de Adobe Dimension en AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---


# Uso de recursos de Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>El paquete de funciones AEM 3D de AEM 6.4 ya no es compatible. Adobe recomienda utilizar la función de recursos 3D en [AEM como Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html) al trabajar con recursos de Adobe Dimension.

El paquete de funciones AEM 3D ofrece compatibilidad con recursos (`.dn` archivos) de Adobe Dimension en AEM Assets, AEM Sites y AEM Screens.

Un nuevo visor 3D basado en el estándar abierto glTF ofrece funciones de visualización de previsualización y Sitios y pantallas para los recursos de Adobe Dimension.

## Acerca del servicio de conversión basado en la nube {#about-the-cloud-based-conversion-service}

Cuando se carga un recurso de Dimension en AEM, se reenvía una copia del archivo a un servicio en la nube gestionado por Adobe alojado en Amazon AWS. Este servicio convierte el formato de archivo Dimension propiedad del Adobe al formato glTF estándar abierto. El modelo 3D convertido se empaqueta como un glTF binario (`.glb`). AEM almacena el modelo convertido con el recurso de Dimension principal como una representación.

Puede configurar el formato de `.glb` conversión de una de las dos formas siguientes (consulte [Instalación y configuración de AEM 3D](install-config-3d.md) para obtener instrucciones):

* Incluya extensiones específicas del Adobe para maximizar la calidad visual al utilizar el visor glTF de Adobe para vista de recursos Dimension en AEM Assets, AEM Sites o AEM Screens. Esto hace que las `.glb` representaciones sean incompatibles con la mayoría de las aplicaciones de terceros.
* Excluya las extensiones específicas del Adobe para lograr la compatibilidad de la `.glb` representación con aplicaciones de terceros. Esto limita la calidad visual al visualizarla en AEM Assets, AEM Sites o AEM Screens (por ejemplo, sin iluminación IBL) para simular la calidad de las aplicaciones típicas de terceros.

La transferencia de los archivos Dimension/glTF a o desde Amazon AWS y su almacenamiento temporal en AWS están totalmente protegidos. Estos archivos persisten en Amazon AWS durante un período de tiempo mínimo; normalmente, no más de unos minutos durante operaciones normales.

Para habilitar la compatibilidad con los recursos de Dimension, debe obtener las credenciales de Adobe para acceder al servicio de conversión. See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Si instala y utiliza las credenciales proporcionadas, comprenderá y aceptará que los recursos de Adobe Dimension 3D se transferirán al servicio de conversión basado en la nube gestionado por Adobe y procesado por él, alojado en Amazon AWS.

### Ver en AEM Assets {#viewing-on-aem-assets}

El paquete de funciones 3D de AEM incluye un nuevo visor basado en el estándar abierto glTF que se utiliza para la vista de recursos de Adobe Dimension. Este visor se selecciona automáticamente al abrir un archivo Dimension o un glTF comprimido en la vista de detalles en AEM Assets o con el componente 3D en AEM Sites.

Tenga en cuenta que la interfaz de usuario del visor de GlTF es algo diferente del visor 3D estándar que se utiliza para todos los demás tipos de recursos 3D.

#### See also the following: {#see-also-the-following}

* [AEM notas](/help/release-notes/aem3d-release-notes.md) de la versión 3D para restricciones y limitaciones aplicables a los recursos Dn y al visor glTF.
* [Uso del componente](using-the-3d-sites-component.md) Sitios 3D para propiedades de componentes específicas de recursos de Adobe Dimension.
* [Instalación y configuración de AEM 3D](install-config-3d.md) para configurar el servicio de conversión basado en la nube.

