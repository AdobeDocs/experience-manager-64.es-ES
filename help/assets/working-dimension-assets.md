---
title: Uso de recursos de Adobe Dimension
description: Uso de recursos de Adobe Dimension en AEM 3D.
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: Recursos 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Uso de recursos de Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>Ya no se admite el paquete de funciones 3D de AEM en AEM 6.4. Adobe recomienda utilizar la función Recursos 3D en [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) al trabajar con recursos de Adobe Dimension.

El paquete de funciones 3D de AEM proporciona compatibilidad con activos de Adobe Dimension (archivos `.dn`) en AEM Assets , AEM Sites y AEM Screens.

Un nuevo visor 3D basado en el estándar abierto glTF proporciona funciones de vista previa y de vista de Sites y Screens para los recursos de Adobe Dimension.

## Acerca del servicio de conversión basado en la nube {#about-the-cloud-based-conversion-service}

Cuando se carga un recurso de Dimension en AEM, se reenvía una copia del archivo a un servicio basado en la nube administrado por Adobe alojado en Amazon AWS. Este servicio convierte del formato de archivo Dimension propietario del Adobe al formato glTF estándar abierto. El modelo 3D convertido está empaquetado como un glTF binario (`.glb`). AEM almacena el modelo convertido con el recurso del Dimension principal como una representación.

Puede configurar el formato de conversión `.glb` de una de las dos maneras siguientes (consulte [Instalación y configuración de AEM 3D](install-config-3d.md) para obtener instrucciones):

* Incluya extensiones específicas del Adobe para maximizar la calidad visual al utilizar el visor de Adobe glTF para ver los recursos del Dimension en AEM Assets, AEM Sites o AEM Screens. Esto hace que las `.glb` representaciones sean incompatibles con la mayoría de las aplicaciones de terceros.
* Excluya las extensiones específicas del Adobe para lograr la compatibilidad de la representación `.glb` con aplicaciones de terceros. Esto limita la calidad visual al visualizarla en AEM Assets, AEM Sites o AEM Screens (por ejemplo, sin iluminación de IBL) para simular la calidad de las aplicaciones de terceros típicas.

La transferencia de los archivos Dimension/glTF a o desde Amazon AWS y su almacenamiento temporal en AWS están totalmente protegidos. Estos archivos persisten en Amazon AWS durante una cantidad mínima de tiempo; normalmente, no más de unos minutos durante operaciones normales.

Para habilitar la compatibilidad con recursos de Dimension, debe obtener las credenciales de Adobe para acceder al servicio de conversión. Consulte [Instalación y configuración AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Si instala y utiliza las credenciales proporcionadas, comprende y acepta que los recursos Adobe Dimension 3D se transferirán al servicio de conversión gestionado por Adobes y basado en la nube alojado en Amazon AWS, y que este los procesará.

### Visualización en AEM Assets {#viewing-on-aem-assets}

El paquete de funciones 3D de AEM incluye un nuevo visor basado en el estándar abierto glTF que se utiliza para ver los recursos de Adobe Dimension. Este visor se selecciona automáticamente al abrir un archivo Dimension o un glTF comprimido en la vista de detalles en AEM Assets o con el componente 3D en AEM Sites.

Tenga en cuenta que la interfaz de usuario del visor de glTF es algo diferente del visor 3D estándar que se utiliza para todos los demás tipos de recursos 3D.

#### Consulte también lo siguiente: {#see-also-the-following}

* [AEM notas de la versión 3D ](/help/release-notes/aem3d-release-notes.md) para restricciones y limitaciones aplicables a los recursos Dn y al visor de glTF.
* [Uso del ](using-the-3d-sites-component.md) componente Sitios 3D para propiedades de componentes específicas de los recursos de Adobe Dimension.
* [Instalación y configuración de AEM 3](install-config-3d.md) de datos para configurar el servicio de conversión basado en la nube.
