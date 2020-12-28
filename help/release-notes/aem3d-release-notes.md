---
title: Notas de la versión de AEM 3D
seo-title: Notas de la versión de AEM 3D
description: Notas de la versión específicas del contenido 3D en Adobe Experience Manager Assets.
seo-description: Notas de la versión específicas del contenido 3D en Adobe Experience Manager Assets.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes, 3D
content-type: reference
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 9710c9931b4f17073c712f5869a1843c1d99ee8e
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 0%

---


# Notas de la versión de AEM 3D {#aem-d-release-notes}

>[!IMPORTANT]
>
>El paquete de funciones AEM 3D de AEM 6.4 ya no es compatible. Adobe recomienda utilizar la función de recursos 3D en [AEM como Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM-6.4-DynamicMedia-3D versión 3.1.0 (10 de octubre de 2018)

El paquete de funciones AEM 3D permite la compatibilidad con contenido 3D en AEM Assets. Proporciona funciones para cargar, gestionar, previsualización y procesar recursos 3D. La compatibilidad con la visualización y el procesamiento está optimizada para objetos individuales (en lugar de escenas complejas con varios objetos).

AEM 3D admite tipos de recursos Adobe Dimension (Dn) y glTF. La implementación para estos tipos de recursos es sustancialmente diferente a la de los tipos 3D tradicionales descritos en esta documentación. Consulte [Uso de recursos de Adobe Dimension](/help/assets/working-dimension-assets.md).

También se incluyen integraciones del lado del servidor con Autodesk® Maya® (solo Windows). Al instalar y configurar Maya en el mismo servidor que AEM, se habilita la compatibilidad con formatos de archivo Maya nativos, incluida la representación de alta calidad con el complemento independiente NVIDIA® de rayos mentales para Maya. La instalación y configuración de 3ds Max en el servidor permite la compatibilidad con el formato de archivo nativo .max.

Consulte [Integración con Autodesk Maya](/help/assets/integrate-maya-with-3d.md).

Consulte también [Instalación y configuración de AEM 3D Assets](/help/assets/install-config-3d.md) y [Configuración avanzada](/help/assets/advanced-config-3d.md).

Consulte también [Uso de recursos 3D](/help/assets/assets-3d.md).

## Requisitos del sistema {#system-requirements}

**Requisitos previos**

* AEM 6.4.2 (AEM 6.4 con Service Pack 2)
* Autodesk® FBX® SDK 2016.1.2

**Sistemas operativos admitidos**

* Microsoft Windows 2012 Server o posterior
* Apple OS X El Capitan 10.6 o posterior
* RedHat Enterprise Linux 7.3

**Navegadores web admitidos para AEM Assets**

* Google Chrome 53 o posterior (recomendado).
* Apple Safari 9.1 o posterior.
* Firefox 48 o posterior.
* Microsoft Edge 25.10586 o posterior.

Es posible que otros exploradores no admitan la visualización interactiva de contenido 3D en AEM. Solo Google Chrome admite sombras proyectadas en la Previsualización.

**Requisitos y recomendaciones de hardware**

* CPU: el procesamiento y procesamiento 3D es muy exigente en la CPU de un equipo. Como tal, se recomienda un servidor contemporáneo con un mínimo de ocho núcleos de CPU.
* Memoria: se recomienda un mínimo de 32 GB.
* Almacenamiento masivo: se recomienda el almacenamiento SSD de gran ancho de banda.

   Durante la carga, los recursos 3D se convierten a un formato propio para una visualización rápida e interactiva. Según el tipo de recurso 3D, se requiere un espacio de almacenamiento de 2 a 3 veces el tamaño del recurso 3D cargado.

Consulte también [Uso de recursos 3D](/help/assets/assets-3d.md).

## Instalación y configuración de AEM 3D {#installing-and-configuring-aem-d}

Consulte [Instalación y configuración de AEM 3D](/help/assets/install-config-3d.md).

Consulte también [Integración de AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md) y [Integración de AEM 3D con Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## Formatos de archivo 3D admitidos {#supported-d-file-formats}

| Formato | Descripción | Plataformas | Notas |
|--- |--- |--- |--- |
| DN | Adobe Dimension | Todos | Requiere acceso a un servicio de conversión basado en la nube. |
| GLTZ | Zipped gITF | Todos |  |
| GLB | Binary gITF | Todos | Descargar solamente (las representaciones de GLB se crean para recursos DN). |
| OBJ | Wavefront OBJ 3D | Todos |  |
| FBX | Autodesk FBX (Kaydara Filmbox) | Todos | El SDK de Autodesk FBX debe estar instalado en el nodo Autor. |
| MA, MB | Autodesk nativo Maya | Solo Windows | Se requiere Autodesk Maya en el nodo Autor para habilitar estos formatos de archivo. Consulte [Integración de AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| JT | CAD abierto de Siemens PLM | Solo Windows | Se requiere Autodesk Maya en el nodo Autor para habilitar estos formatos de archivo. Consulte [Integración de AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| * | Pueden habilitarse formatos de entrada 3D adicionales compatibles con Autodesk Maya. Consulte [Activación de formatos adicionales admitidos por Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya). | Solo Windows | Se requiere Autodesk Maya en el nodo Autor para habilitar estos formatos de archivo. Consulte [Integración de AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| MÁXIMO | Máx. 3d de Autodesk nativo | Solo Windows | Autodesk 3ds Max es necesario en el nodo de creación para habilitar este formato de archivo. Consulte [Integración de AEM 3D con Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md). |

## Mejoras y nuevas funciones {#enhancements-and-new-features}

Versión 3.0

* Compatibilidad con el formato de archivo nativo máximo de Autodesk 3ds.
* Varios cambios y correcciones de errores para mejorar la estabilidad, la calidad y la experiencia del usuario.
* Configuración movida a `/libs/settings/dam/v3d/`

Versión 3.1

* Compatibilidad limitada con el formato de archivo nativo de Adobe Dimension (.dn).
* Un nuevo visor 3D para recursos GlTF.
* Una nueva interfaz para un servicio de conversión basado en la nube y gestionado por Adobe alojado en Amazon AWS. Inicialmente, este servicio solo convierte de Dn a glTF.

## Restricciones y problemas conocidos {#restrictions-and-known-issues}

### Soporte de Adobe Dimension {#adobe-dimension-support}

* Esta versión de AEM3D tiene compatibilidad limitada con archivos .dn creados con Adobe Dimension.
* Durante el procesamiento de la carga, AEM aprovecha un servicio de conversión alojado en Adobe y basado en la nube para crear una representación glTF a partir del archivo .dn nativo. Se requiere acceso al servicio de conversión y selección de los extremos de Amazon AWS.
* Se proporciona un nuevo visor de GlTF que admite la visualización de recursos Dn en AEM Assets y en Sitios/Pantallas. La compatibilidad con las fases en el visor aún no está disponible.
* Los modelos Dn pueden incrustar luces y fondos IBL que se muestran, si están presentes. Como alternativa, el visor aplica una iluminación predeterminada, un color de fondo predeterminado o ambos.
* La representación de alta calidad para los recursos Dn aún no está disponible.
* Las dependencias como los mapas de textura están incrustadas en los recursos Dn y no se pueden administrar explícitamente en AEM.

### Compatibilidad {#compatibility}

* **No se puede ejecutar como un servicio de Windows (solo Windows)** : esto puede funcionar pero no se ha probado.
* **Dynamic Media** (  `dynamicmedia-scene7` modo): La compatibilidad de AEM3D con la nueva solución Dynamic Media lanzada con AEM 6.4 aún no se ha verificado completamente. Si Dynamic Media y AEM3D se implementan juntos, se recomienda colocar los recursos 3D y sus dependencias solo en un área del repositorio de AEM Assets que no esté asignada a Dynamic Media. Esta recomendación es especialmente importante para los archivos TIFF de 32 bits que son necesarios para las fases 3D pero no son compatibles con Dynamic Media.

### General {#general}

* **Método abreviado**  Resolver dependencias: este método abreviado está disponible en la Vista de tarjetas de recursos 3D. Las tarjetas de recursos de la Vista de tarjetas muestran la pancarta &quot;Dependencias no resueltas&quot;. El acceso directo abre la ficha **Propiedades básicas** en lugar de la ficha **Dependencias**. Solución: navegue manualmente a la ficha Dependencias.

* **Selector de escenario no disponible** : los recursos 3D que incluyen luces se etiquetan automáticamente mediante AEM como etapas 3D. No hay ningún selector de etapas disponible para las etapas de la vista de detalles. Para marcar un recurso 3D como un objeto 3D, navegue hasta **Propiedades básicas**, cambie **Clase de recurso** a **Objeto 3D** y, a continuación, haga clic en **Guardar**.

* **Descarga de recursos 3D con dependientes y representaciones** : al descargar recursos 3D de AEM con  **** Dependencias y  **Representaciones** seleccionadas, la descarga incluye no sólo las representaciones del recurso 3D principal, sino también las representaciones de todas las personas dependientes.

* **Integración**  máxima de Autodesk 3ds: no se admite el procesamiento con 3ds Max en este momento.

### Restricciones de tipo de archivo {#file-type-restrictions}

* **Archivos**  de Mathematica (.ma): los archivos de Mathematica utilizan el mismo sufijo de archivo que los archivos Maya nativos. Cuando se instala el Feature Pack y se activa el formato de archivo Maya .ma, falla el intento de AEM3D de ingestar archivos de Mathematica como archivos Maya. Estos recursos muestran una pancarta de error en la vista de tarjetas.

* **Archivos**  de imagen Targa (.tga): los archivos de modelo 3D anteriores pueden incluir referencias a archivos TGA. Este formato no es compatible con AEM. Adobe recomienda convertir estos archivos a un formato diferente antes de cargar los recursos 3D en AEM.
* **Imágenes**  HDR: las imágenes HDR se utilizan en etapas con iluminación basada en imágenes (IBL). Actualmente, solo se admiten imágenes TIFF de 32 bits con este fin.
* **Imágenes**  TIFF de 32 bits: las imágenes TIFF de 32 bits se utilizan para las fases con iluminación basada en imágenes. AEM no admite la creación de representaciones para estos recursos, lo que resulta en miniaturas en blanco y no es posible la previsualización. El recurso sigue funcionando correctamente cuando se utiliza con una fase IBL.
* **Archivos**  máximos (.max) de Autodesk 3ds: si Autodesk 3ds Max está instalado y configurado en los nodos Autor, AEM admite la ingestión y conversión de archivos .max. En este momento no se admite el uso de archivos .max como etapas.

### Resolución de dependencia automática {#automatic-dependency-resolution}

* **Dependencias de archivos sin resolver después de la carga** : cuando los recursos 3D y sus dependientes se cargan con la misma operación de carga, es posible que algunos dependientes no se resuelvan automáticamente. Es más probable que este problema se produzca si los archivos dependientes son grandes. Para corregir este problema, acceda a la página **Propiedades/Dependencias** del recurso que muestra los dependientes sin resolver después de la carga. Ahora deben mostrarse los dependientes no resueltos anteriormente. Haga clic en **Guardar** para finalizar el recurso. Para evitar este problema en el futuro, puede cargar todos los dependientes en una transacción independiente antes de cargar los objetos 3D.

* **Distinción entre mayúsculas y minúsculas** : la resolución de dependencia automática intenta hacer coincidir los nombres de archivo de una manera que distingue entre mayúsculas y minúsculas. Por ejemplo, si la dependencia original encontrada en el recurso 3D es `image.jpg`, la dependencia se resuelve en un recurso denominado `Image.jpg`, `image.JPG` o cualquier otra variación de caso.

### Fases 3D {#d-stages}

* **Miniaturas para etapas** : es posible que las miniaturas generadas automáticamente para las etapas no representen el escenario con precisión.
* **Geometría del escenario para etapas**  no IBL: el procesador de refinado rápido no procesa la geometría de las etapas con iluminación no IBL, incluidos los fondos y planos de tierra. Esta geometría sigue mostrándose razonablemente en la vista de detalles del recurso (previsualización 3D).

* **FBX estadios con iluminación**  IBL: Puede cargar las etapas de FBX con iluminación IBL. Sin embargo, el formato FBX no incluye disposiciones para transferir el nombre de la imagen IBL. Como tal, la resolución de dependencia de archivos falla. La imagen IBL debe asignarse manualmente al escenario después de la carga. Puede asignar la misma imagen TIFF de 32 bits a las tres dependencias que son **Imagen de Entorno de iluminación difusa**, **Imagen de Entorno de reflejo** y **Imagen de Entorno de fondo**, o se pueden asignar diferentes imágenes.

* **Imagen de fondo de las etapas**  de IBL: en algunas escenas de IBL, la imagen de fondo puede tener una calidad deficiente, como ser demasiado brillante o demasiado borrosa. Para maximizar la calidad visual del fondo de la imagen de las etapas de IBL, Adobe recomienda que prepare una imagen JPEG de alta resolución de 8 bits independiente y la adjunte al escenario de IBL como **Imagen de Entorno de fondo**.

* **Imagen en negro cuando se procesa con Maya utilizando un escenario**  IBL: este problema probablemente se deba a que Maya no encuentra la dependencia de imagen IBL porque la imagen IBL original a la que hace referencia el escenario se reemplazó por una imagen con un nombre diferente. Para evitar este problema, asegúrese de que al menos una de las tres dependencias a las que hace referencia la etapa Maya IBL tiene el mismo nombre que la referencia del archivo IBL original en el archivo Maya.
* **Imagen de fondo invertida para el escenario**  IBL: las imágenes para las etapas IBL se voltean horizontalmente intencionadamente para coincidir con el comportamiento del procesador de rayos mentales NVIDIA que se proporciona con Autodesk Maya. Solución: Gire las imágenes utilizadas para las etapas de IBL en Photoshop antes de cargarlas.
* **Brillo de las etapas**  de IBL: la análisis automática de la imagen IBL puede resultar en una escena demasiado oscura o brillante. Para ajustar el brillo de la iluminación de las etapas de IBL, navegue hasta **Propiedades básicas** y ajuste el valor **luminoso** de **Iluminación de Entorno** según sea necesario.

### Componente 3D de AEM Sites {#aem-sites-d-component}

* **Un componente 3D por página** : en este momento, solo se permite una instancia del componente 3D en cada página web. Si se agrega más de un componente 3D a la misma página, ninguno de los componentes 3D funcionará correctamente.
* **Falta la Vista 3D al obtener una vista previa en Sitios** : cuando se utiliza  **** Vista previa de sitios, la página debe volver a cargarse en el explorador para inicializar completamente el visor 3D. No se trata de un problema que se produzca cuando se vista la página web directamente (es decir, cuando `edit.html` se elimina de la ruta) en los nodos Autor o Publicar.

* **Modo de pantalla completa no disponible en dispositivos**  iOS: el botón de pantalla completa no está disponible en dispositivos iOS, independientemente del explorador que se utilice.

### Publicación de contenido 3D {#publishing-d-content}

* **Configuración**  de componentes 3D: debe instalar el paquete de funciones 3D en todos los nodos activos de Publish y cada nodo debe configurarse con  **CRXDE** Liteto con las mismas opciones de configuración en  `/libs/settings/dam/v3D/WebGLSites`.

* **Faltan texturas, fondo o iluminación después de la publicación** : el mecanismo  **** Publicación de AEM Sites publica automáticamente las dependencias principales de la página, incluidos el modelo 3D y la fase 3D a la que hace referencia el componente 3D. Las etapas 3D y los modelos 3D suelen depender de los recursos secundarios para las imágenes IBL y los mapas de textura, que el mecanismo Publicación de sitios no publica automáticamente. Solución: publicar todos los recursos 3D de Recursos antes de publicar la página web desde Sitios. De este modo, se garantiza que todas las dependencias de los recursos 3D estén disponibles en los nodos Publicar.
