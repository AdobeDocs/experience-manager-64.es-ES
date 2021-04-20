---
title: Uso de AEM recursos 3D
description: Aprenda a trabajar con recursos 3D en AEM 3D
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
exl-id: 3cee9b4f-c4be-4ffc-970c-5680c8ebba47
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 5%

---

# Uso de AEM activos 3D {#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 3D en AEM 6.4 ya no es compatible. Adobe recomienda utilizar la función de recursos 3D en [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

AEM 3D (Adobe Experience Manager 3D) permite cargar, administrar, visualizar y procesar contenido 3D. La compatibilidad para la visualización y el procesamiento se optimiza para objetos individuales.

Consulte también [Notas de la versión de AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulte también [Instalación y configuración de AEM 3D](install-config-3d.md).

## Acerca de los modelos y escenarios en AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D le permite ver y procesar modelos 3D estáticos independientes de alta calidad en entornos predefinidos denominados escenarios. Básicamente, un escenario proporciona &quot;iluminación&quot; para la escena 3D y la configuración para la representación en una aplicación nativa como Autodesk® Maya® o Autodesk 3ds Max®. Además, el escenario puede incluir, opcionalmente, cámaras predefinidas, fondos y geometría de plano de tierra.

Se supone que los archivos 3D cargados que contienen luces son un escenario. Puede revertir estos recursos para que sean simples objetos 3D abriendo el recurso en la página de detalles del recurso. Pulse **[!UICONTROL Ver propiedades]** y, a continuación, pulse la pestaña **[!UICONTROL Básico]**. En el encabezado Metadatos, en la lista desplegable Clase de recurso , seleccione **[!UICONTROL Objeto 3D]**.

Cuando cree modelos 3D para utilizarlos en AEM 3D, tenga en cuenta lo siguiente:

* Los archivos del modelo 3D deben contener un solo objeto, sin fondos, planos de tierra, iluminación de escenas o cámaras.
* Coloque el modelo sobre el plano de tierra. Este posicionamiento es especialmente importante cuando se visualiza o procesa con escenarios que proporcionan un plano de tierra. Hay disponible una configuración (y habilitada de forma predeterminada) que hace que el objeto se mueva sobre el plano de tierra al obtener una vista previa o procesarlo con Rapid Refine. Esta configuración no afecta al procesamiento con procesadores de terceros (por ejemplo, a través de Maya) y, por lo tanto, los objetos que no se encuentran encima del plano de tierra pueden estar parcialmente ocultos.
* Coloque el modelo de manera que esté razonablemente centrado lateralmente alrededor del origen del sistema de coordenadas (0,0,0). Al hacerlo, se garantiza una buena experiencia de visualización interactiva.
* Aparte de los mapas de textura, se admiten las referencias de archivos externos. Por lo tanto, debe incrustar cualquier contenido referenciado en el archivo del modelo principal antes de cargarlo en AEM.

   Consulte [Acerca de la carga y el procesamiento de los recursos 3D en AEM](upload-processing-3d-assets.md).

* El escenario proporciona una iluminación general. Como tal, el Adobe no recomienda incluir luces con archivos de modelo 3D. Puede incluir luces en el modelo. Sin embargo, solo deben ser específicos del modelo. Por ejemplo, puede ser necesario incluir iluminación adicional para iluminar una parte del objeto que queda oscurecida por otras partes. Por lo tanto, no sería lo suficientemente visible con solo las luces del escenario.

## Archivos compatibles con AEM 3D {#supported-files-in-aem-d}

Un recurso 3D típico tiene un archivo de modelo principal y ninguno o varios archivos a los que se hace referencia. Los archivos a los que se hace referencia incluyen elementos como mapas de textura o imágenes **IBL (Iluminación basada en imágenes)**.

### Acerca del archivo de modelo 3D principal {#about-the-primary-d-model-file}

El fichero del modelo 3D principal contiene la geometría real del modelo 3D y las definiciones de los materiales (por defecto) que se aplican a las superficies del modelo. AEM 3D admite los siguientes formatos de archivo del modelo 3D principal:

* Formato de archivo OBJ de Wavefront (`.obj`)

   El formato OBJ requiere uno o más archivos MTL externos independientes (Biblioteca de plantillas de material) (`.mtl`).

* Formato de archivo FBX (Filmbox) de Autodesk (`.fbx`)

   El formato de intercambio de archivos 3D de Autodesk; formatos binario y ASCII.

   Cuando crea archivos FBX en aplicaciones de terceros, Adobe recomienda los siguientes ajustes de configuración (consulte la tabla siguiente). Estos ajustes pueden ayudarle a obtener los mejores resultados para los archivos 3D que desea utilizar en AEM. Los nombres de las opciones se toman del cuadro de diálogo **[!UICONTROL Opciones de exportación de Autodesk Maya FBX]**.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opción en el cuadro de diálogo Exportación de Autodesk Maya FBX</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>Conservar referencias<br /> </td> 
   <td><p>Anular selección.</p> <p>AEM 3D no admite actualmente referencias externas.</p> </td> 
  </tr> 
  <tr> 
   <td>Malla lisa<br /> </td> 
   <td>Seleccione.</td> 
  </tr> 
  <tr> 
   <td>Convertir superficies NURBS a</td> 
   <td><strong>Malla de procesamiento de software</strong></td> 
  </tr> 
  <tr> 
   <td>Animación</td> 
   <td><p>Seleccione o anule la selección.</p> <p>Si elige esta opción, AEM 3D ignora la información de animación del archivo.</p> </td> 
  </tr> 
  <tr> 
   <td>Cámaras</td> 
   <td><p>Seleccione para <strong>etapas 3D</strong>.</p> <p>Anule la selección de los modelos 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luces</td> 
   <td><p>Seleccione para <strong>etapas 3D</strong>.</p> <p>Anule la selección para <strong>modelos 3D</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>Unidades - Automático</td> 
   <td>Seleccione. AEM 3D se convierte en importación.</td> 
  </tr> 
  <tr> 
   <td>Conversión de eje: eje ascendente</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up proporciona resultados coherentes al exportar desde Maya y es el sistema de coordenadas preferido para los archivos FBX en esta versión 3D de AEM.</p> </td> 
  </tr> 
  <tr> 
   <td>Incrustar medios</td> 
   <td>Ambas opciones son compatibles. Si se selecciona incrustado, AEM 3D extrae el contenido incrustado en una carpeta adyacente que tenga el mismo nombre que el archivo de modelo con <code>.fbm</code> añadido a él.</td> 
  </tr> 
  <tr> 
   <td>Formato de archivo FBX: Tipo</td> 
   <td>Tanto <strong>Binary </strong>como <strong>ASCII </strong>son compatibles.</td> 
  </tr> 
  <tr> 
   <td>Formato de archivo FBX: versión</td> 
   <td>Se recomienda FBX 2014/2015. Otras versiones también pueden funcionar bien.</td> 
  </tr> 
 </tbody> 
</table>

Se admiten los siguientes formatos de archivo adicionales si Autodesk Maya está instalado y configurado en AEM servidores de creación:

* Autodesk Maya

   Los formatos ASCII `.ma` y binario `.mb`.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Un formato de intercambio de datos CAD estándar de la industria, colaboración y visualización de productos.

### Compatibilidad con archivos de mapa de textura {#support-for-texture-map-files}

Las definiciones de material en archivos de modelo 3D pueden incluir referencias a archivos de imagen externos que proporcionan mapas de textura. AEM 3D admite los siguientes tipos de archivos de mapa de textura:

* Texturas de color difusas
* Texturas de color especular
* Texturas de color ambiente
* Documentos de desplazamiento (también llamados mapas de burbujas)
* Mapas normales
* Mapas de opacidad
* Mapas de rugosidad (también llamados Mapas de Gloss, Reflectivity o Cosine Power)

Los materiales en el archivo principal del modelo 3D pueden hacer referencia a otros tipos de mapas que son ignorados por AEM 3D.

### Imágenes de IBL (iluminación basada en imágenes) {#ibl-image-based-lighting-images}

Un archivo de modelo 3D que define un escenario puede hacer referencia a una sola imagen de entorno IBL. Actualmente, AEM 3D solo admite imágenes TIFF de 32 bits en formato de latitud/longitud para IBL difuso y para reflejos. Para el fondo de la escena esférica, también se admiten imágenes RGB de 8 bits.

Consulte [Acerca del trabajo con etapas de IBL](working-with-ibl-stages.md).

>[!NOTE]
>
>Las referencias a archivos (que no sean las descritas anteriormente) presentes en el archivo del modelo 3D principal se ignoran actualmente. AEM 3D no admite referencias a archivos de modelo 3D secundarios.
Y-up es el sistema de coordenadas preferido para los archivos FBX de esta versión.

## Sombreado de material en un archivo de modelo 3D principal {#material-shading-in-a-primary-d-model-file}

El archivo original del modelo nativo puede contener definiciones materiales que se utilizan con sombreadores como Blinn, Lambert o con sombreadores de procedimiento. Estos materiales potencialmente complejos solo se admiten cuando se procesa utilizando la aplicación nativa correspondiente (como Autodesk Maya).

Para fines de visualización o cuando se procesa utilizando el procesador Rapid Refine™ predeterminado, todos los materiales se simplifican, sustituyen o ambos para que se puedan utilizar con un sombreado tipo Phong. Este sombreado admite un conjunto limitado de atributos. Se omiten otros atributos de la definición del material.

Consulte [Ver recursos 3D](viewing-3d-assets.md).

Consulte [Procesamiento de recursos 3D](rendering-3d-assets.md).

## Materiales de nomenclatura en un archivo de modelo 3D principal {#naming-materials-in-a-primary-d-model-file}

Una *superficie* se define como la superficie de un modelo 3D cubierto por el mismo material. Este material también proporciona el nombre de la superficie. Como tal, Adobe recomienda nombrar los materiales incluidos en los archivos del modelo 3D principal según corresponda. Por ejemplo, se prefiere el uso de nombres específicos como &quot;Cuerpo&quot;, &quot;Ventanas&quot;, &quot;Neumáticos&quot; o &quot;Rims&quot; a nombres vagos como &quot;Rojo&quot;, &quot;Vidrio&quot;, &quot;Caucho&quot;, &quot;Aluminio&quot;.
