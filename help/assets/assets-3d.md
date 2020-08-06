---
title: Uso de recursos 3D
seo-title: Uso de recursos 3D
description: Aprenda a trabajar con recursos 3D en AEM 3D
seo-description: Aprenda a trabajar con recursos 3D en AEM 3D
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 6%

---


# Uso de recursos 3D {#working-with-d-assets}

AEM 3D (Adobe Experience Manager 3D) permite cargar, administrar, visualizar y procesar contenido 3D. La compatibilidad para la visualización y el procesamiento se optimiza para objetos individuales.

Consulte también [Notas de la versión de AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulte también [Instalación y configuración de AEM 3D](install-config-3d.md).

## Acerca de los modelos y las etapas en AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D le permite realizar vistas y procesar modelos 3D estáticos independientes de alta calidad en entornos predefinidos denominados Fases. Básicamente, un escenario proporciona &quot;iluminación&quot; para la escena 3D y la configuración para el procesamiento en una aplicación nativa como Autodesk® Maya® o Autodesk 3ds Max®. Además, el escenario puede incluir, opcionalmente, cámaras predefinidas, fondos y geometría de plano de tierra.

Los archivos 3D cargados que contienen luces se consideran un escenario. Puede revertir estos recursos para que sean objetos 3D simples si abre el recurso en la página de detalles del recurso. Toque Propiedades **[!UICONTROL de]** Vista y, a continuación, toque la ficha **[!UICONTROL Básico]** . En el encabezado Metadatos, en la lista desplegable Clase de recurso, seleccione un objeto **** 3D.

Cuando cree modelos 3D para su uso en AEM 3D, tenga en cuenta lo siguiente:

* Los archivos del modelo 3D deben contener un solo objeto, sin fondos, planos de tierra, iluminación de escenas o cámaras.
* Coloque el modelo sobre el plano de masa. Este posicionamiento es especialmente importante cuando se realiza una vista o representación con etapas que proporcionan un plano de tierra. Hay una configuración disponible (y habilitada de forma predeterminada) que hace que el objeto se mueva por encima del plano de tierra al obtener una vista previa o al procesarlo con una precisión rápida. Esta configuración no afecta al procesamiento con procesadores de terceros (por ejemplo, a través de Maya) y, por tanto, los objetos que no están ubicados por encima del plano de tierra pueden estar parcialmente ocultos.
* Sitúe el modelo de modo que esté razonablemente centrado lateralmente alrededor del origen del sistema de coordenadas (0,0,0). De este modo, se garantiza una buena experiencia de visualización interactiva.
* Aparte de los mapas de textura, se admiten las referencias de archivo externas. Por lo tanto, debe incrustar cualquier contenido al que se haga referencia en el archivo del modelo principal antes de cargarlo en AEM.

   Consulte [Acerca de la carga y el procesamiento de los recursos 3D en AEM](upload-processing-3d-assets.md).

* La iluminación general de la escena la proporciona el escenario. Como tal, Adobe no recomienda incluir luces con archivos de modelo 3D. Puede incluir luces en el modelo. Sin embargo, solo deben ser específicos del modelo. Por ejemplo, puede que sea necesario incluir iluminación adicional para iluminar una parte del objeto que está oscurecida por otras partes. Por lo tanto, no sería suficientemente visible con sólo las luces del escenario.

## Archivos admitidos en AEM 3D {#supported-files-in-aem-d}

Un recurso 3D típico tiene un archivo de modelo principal y ninguno o más archivos a los que se hace referencia. Los archivos a los que se hace referencia incluyen, por ejemplo, mapas de textura o imágenes **IBL (Iluminación basada en imágenes)** .

### Acerca del archivo de modelo 3D principal {#about-the-primary-d-model-file}

El fichero del modelo 3D principal contiene la geometría real del modelo 3D y las definiciones de los materiales (predeterminados) que se aplican a las superficies del modelo. AEM 3D admite los siguientes formatos de archivo de modelo 3D principal:

* Formato de archivo OBJ de Wavefront (`.obj`)

   El formato OBJ requiere uno o más archivos MTL externos independientes (Biblioteca de plantillas de material) (`.mtl`).

* Formato de archivo FBX (Filmbox) de Autodesk (`.fbx`)

   Formato de intercambio de archivos 3D de Autodesk; formatos binario y ASCII.

   Al crear archivos FBX en aplicaciones de terceros, Adobe recomienda los siguientes ajustes de configuración (consulte la tabla siguiente). Esta configuración puede ayudarle a obtener los mejores resultados para los archivos 3D que desea utilizar en AEM. Los nombres de las opciones se toman del cuadro de diálogo Opciones **** de exportación de Autodesk Maya FBX.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opción en el cuadro de diálogo Autodesk Maya FBX Export</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>Conservar referencias<br /> </td> 
   <td><p>Anular selección.</p> <p>AEM 3D no admite actualmente referencias externas.</p> </td> 
  </tr> 
  <tr> 
   <td>Malla suave<br /> </td> 
   <td>Seleccione.</td> 
  </tr> 
  <tr> 
   <td>Convertir superficies NURBS en</td> 
   <td><strong>Malla de procesamiento de software</strong></td> 
  </tr> 
  <tr> 
   <td>Animación</td> 
   <td><p>Seleccione o anule la selección.</p> <p>Si selecciona esta opción, AEM 3D ignora la información de animación del archivo.</p> </td> 
  </tr> 
  <tr> 
   <td>Cámaras</td> 
   <td><p>Seleccione para las etapas <strong></strong>3D.</p> <p>Anule la selección de los modelos 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luces</td> 
   <td><p>Seleccione para las etapas <strong></strong>3D.</p> <p>Anule la selección para modelos <strong></strong>3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Unidades - Automático</td> 
   <td>Seleccione. AEM 3D se convierte en la importación.</td> 
  </tr> 
  <tr> 
   <td>Conversión de eje - Eje ascendente</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up proporciona resultados coherentes al exportar desde Maya y es el sistema de coordenadas preferido para archivos FBX en esta versión AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incrustar medios</td> 
   <td>Ambas opciones son compatibles. Si se selecciona incrustado, AEM 3D extrae el medio incrustado en una carpeta adyacente que tenga el mismo nombre que el archivo de modelo con <code>.fbm</code> anexo.</td> 
  </tr> 
  <tr> 
   <td>Formato de archivo FBX: Tipo</td> 
   <td>Tanto <strong>binario </strong>como <strong>ASCII </strong>son compatibles.</td> 
  </tr> 
  <tr> 
   <td>Formato de archivo FBX: versión</td> 
   <td>Se recomienda FBX 2014/2015. Otras versiones también pueden funcionar bien.</td> 
  </tr> 
 </tbody> 
</table>

Se admiten los siguientes formatos de archivo adicionales si Autodesk Maya está instalado y configurado en servidores de creación de AEM:

* Autodesk Maya

   Formatos ASCII `.ma` y `.mb` binarios.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Formato de intercambio de datos CAD, colaboración y visualización de productos estándar del sector.

### Compatibilidad con archivos de mapa de textura {#support-for-texture-map-files}

Las definiciones de material en archivos de modelos 3D pueden incluir referencias a archivos de imagen externos que proporcionan mapas de textura. AEM 3D admite los siguientes tipos de archivos de mapas de textura:

* Texturas de color difusas
* Texturas de color especular
* Texturas de color ambiente
* Papeles de desplazamiento (también llamados mapas de relieve)
* Mapas normales
* Mapas de opacidad
* Mapas de rugosidad (también llamados Mapas de brillo, reflectividad o potencia de coseno)

Los materiales del archivo de modelo 3D principal pueden hacer referencia a otros tipos de mapas que AEM 3D ignora.

### Imágenes de IBL (iluminación basada en imágenes) {#ibl-image-based-lighting-images}

Un archivo de modelo 3D que define un escenario puede hacer referencia a una única imagen de entorno IBL. Actualmente, AEM 3D solo admite imágenes TIFF de 32 bits en formato de latitud/longitud para IBL difuso y para reflejos. También se admiten imágenes RGB de 8 bits para el fondo de escena esférica.

See [About working with IBL stages](working-with-ibl-stages.md).

>[!NOTE]
>
>Las referencias de archivo (distintas de las descritas anteriormente) presentes en el archivo de modelo 3D principal se ignoran en este momento. AEM 3D no admite referencias a archivos de modelo 3D secundarios.
Y-up es el sistema de coordenadas preferido para los archivos FBX de esta versión.

## Sombreado de material en un archivo de modelo 3D principal {#material-shading-in-a-primary-d-model-file}

El archivo original del modelo nativo puede contener definiciones materiales que se utilizan con sombreadores como Blinn, Lambert o sombreadores de procedimiento. Estos materiales potencialmente complejos solo se admiten cuando se procesa con la aplicación nativa correspondiente (como Autodesk Maya).

Para fines de visualización o cuando se procesa con el procesador Rapid Refine™ predeterminado, todos los materiales se simplifican, sustituyen o ambos para que se puedan utilizar con un sombreado Phong. Este sombreado admite un conjunto limitado de atributos. Se omiten otros atributos de la definición de material.

Consulte [Ver recursos 3D](viewing-3d-assets.md).

Consulte [Procesamiento de recursos 3D](rendering-3d-assets.md).

## Asignación de nombres a materiales en un archivo de modelo 3D principal {#naming-materials-in-a-primary-d-model-file}

Una *superficie* se define como la superficie de un modelo 3D cubierto por el mismo material. Este material también proporciona el nombre de la superficie. Como tal, Adobe recomienda que asigne un nombre adecuado a los materiales incluidos en los archivos del modelo 3D principal. Por ejemplo, el uso de nombres específicos como &quot;Cuerpo&quot;, &quot;Ventanas&quot;, &quot;Neumáticos&quot; o &quot;Rims&quot; es preferible al uso de nombres vagos como &quot;Rojo&quot;, &quot;Cristal&quot;, &quot;Caucho&quot;, &quot;Aluminio&quot;.

