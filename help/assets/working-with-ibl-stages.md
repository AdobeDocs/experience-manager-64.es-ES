---
title: Sobre el trabajo con los escenarios de IBL
seo-title: Sobre el trabajo con los escenarios de IBL
description: AEM 3D admite la iluminación basada en imágenes (IBL) para la visualización interactiva y el procesamiento con el procesador incorporado Adobe Rapid Refine™ y con procesadores de terceros.
seo-description: AEM 3D admite la iluminación basada en imágenes (IBL) para la visualización interactiva y el procesamiento con el procesador incorporado Adobe Rapid Refine™ y con procesadores de terceros.
uuid: 495ba9cc-02f5-4ce5-9503-9f61ca5482db
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 658ff671-16b9-41bd-ba24-b77a32b3346b
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 54%

---


# Sobre el trabajo con los escenarios de IBL {#about-working-with-ibl-stages}

AEM 3D admite la iluminación basada en imágenes (IBL) para la visualización interactiva y el procesamiento con el procesador incorporado Adobe Rapid Refine™ y con procesadores de terceros. Puede crear etapas IBL con herramientas de creación comunes como Autodesk® Maya® o Autodesk® 3ds Max®.

## Imágenes para IBL {#images-for-ibl}

Las imágenes utilizadas para la iluminación basada en imágenes deben tener HDR (Rango Dinámico Alto) para conseguir los mejores resultados. Deben tener un formato latitud/longitud con una asignación esférica que proporcione cobertura total del entorno.

Actualmente, AEM 3D solo admite archivos TIFF de 32 bits. Si es necesario, utilice Adobe Photoshop o una herramienta similar para convertir la imagen HDR a TIFF mediante la configuración siguiente en el cuadro de diálogo Exportar TIFF de Adobe Photoshop:

* **[!UICONTROL Profundidad]**  de bits: 32 bits (flotante)
* **[!UICONTROL Orden]**  de píxeles: intercalado (RGBRGB)
* **[!UICONTROL Compresión]**  de imágenes: LZW
* **[!UICONTROL Byte Order]** - IBM PC

Si bien una sola imagen HDR suele ser suficiente para los escenarios de IBL, AEM 3D proporciona un control adicional sobre los efectos de IBL y permite hasta tres imágenes independientes:

* **Imagen**  de Entorno de iluminación difusa: este tipo de imagen debe ser una imagen HDR, pero puede ser relativamente pequeña, ya que la imagen se filtrará mucho antes de usarla para iluminación difusa.
* **Imagen**  de Entorno de reflejo: este tipo de imagen se utiliza para crear reflejos en superficies de objeto. Puede ser una imagen RGB de 8 bits estándar de un tamaño y una resolución que proporcione la calidad y el enfoque deseados de los reflejos. Si se especifica una imagen HDR, AEM 3D la convierte a RGB de 8 bits antes de usar un algoritmo privado.
* **Imagen**  de Entorno de fondo: este tipo de imagen se utiliza como fondo. Puede ser una imagen RGB de 8 bits estándar y debe tener el tamaño, la resolución o el nivel de detalle deseados para el fondo del escenario. Si se especifica una imagen HDR, AEM 3D la convierte a RGB de 8 bits mediante un algoritmo privado.

>[!NOTE]
>
>El algoritmo de conversión puede tener dificultades con ciertas imágenes IBL. Esta dificultad puede dar lugar a fondos que sean demasiado brillantes o saturados en exceso en Vista previa o al procesarlos con Rapid Refine. En estas situaciones, Adobe recomienda utilizar Photoshop o una herramienta similar para convertir manualmente la imagen de IBL a una imagen RGB de 8 bits. Cargue esta imagen por separado y adjúntela al escenario como imagen del entorno de fondo. Las imágenes de entorno de reflejo e iluminación difusa deben ser siempre TIFF de 32 bits.

## Ajuste del aspecto del escenario de IBL {#adjusting-the-ibl-stage-appearance}

Puede ajustar el aspecto del escenario de IBL con las siguientes propiedades de escenario:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propiedad</strong><br /> </td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>Detalles de IBL Sun</td> 
   <td><p>Permite ajustar la dirección y la intensidad de la fuente de luz suplementaria que simula el sol. <span class="diff-html-added">Esta fuente de luz aumenta el brillo de la iluminación y hace que el objeto proyecte una sombra paralela sobre el plano de tierra. Se admite la proyección de sombras al realizar el procesamiento con Rapid Refine y para acceder a una vista previa con Google Chrome; sin embargo, actualmente, otros navegadores no admiten esta opción.</span></p> 
    <ul> 
     <li><strong>lat</strong> - Posición vertical de la fuente de luz solar (<code>0.0</code>-<code>1.0</code>).<br /> Un ajuste de  <code>0.0</code> está en el horizonte (centro vertical de la imagen del Entorno de iluminación difusa);  <code>1.0</code> se encuentra en el cenit (borde superior de la imagen del Entorno de iluminación difusa).</li> 
     <li><strong>long</strong> - Posición horizontal de la fuente de luz solar (<code>0.0</code>-<code>1.0</code>).<br /> Un valor de 0,0 corresponde a la izquierda; 1,0 corresponde al borde derecho de la imagen de entorno de iluminación difusa.<br /> </li> 
     <li><strong>luminoso</strong> - El brillo de la fuente de luz solar. Aumente este valor para aclarar el origen de luz solar; reduzca este valor para oscurecerlo. <br /> Un ajuste de  <code>0</code> desactiva la iluminación suplementaria y deshabilita las sombras proyectadas. El parámetro no afecta a los reflejos de entorno.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Altura de la cámara IBL</td> 
   <td>Si el fondo IBL aparece distorsionado cerca del horizonte, es posible reducir o eliminar la distorsión ajustando esta propiedad. <br /> </td> 
  </tr> 
  <tr> 
   <td>Iluminación de entorno</td> 
   <td><p><span class="diff-html-added">Permite controlar la iluminación difusa. Es posible que tenga que ajustar esta propiedad manualmente para corregir el brillo de la iluminación si la imagen de entorno de iluminación difusa es inusualmente clara u oscura (por ejemplo, escenas nocturnas).</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - Actualmente no se utiliza.</li> 
     <li><strong>luminoso</strong> : multiplicador  <span class="diff-html-added">de brillo. El aumento o la disminución de este valor aumenta o disminuye la intensidad global de la iluminación (iluminación básica de IBL y el brillo del origen de luz solar).</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Aumento del diámetro de fondo esférico de una etapa de IBL {#increasing-the-spherical-background-diameter-of-an-ibl-stage}

Las etapas de IBL utilizan imágenes de fondo esférico de 20 metros de diámetro de forma predeterminada. Estas etapas funcionan bien para objetos de hasta 10 metros. Sin embargo, si muestra objetos más grandes, puede aumentar el diámetro de fondo esférico de una etapa de IBL.

**Para aumentar el diámetro de fondo esférico de una etapa** de IBL:

1. En CRXDE Lite, desplácese hasta el escenario cuyo diámetro de fondo esférico desee aumentar. Por ejemplo,

   `/content/dam/test3d/stage-helipad.fbx`

1. Expanda el nodo de escenario a `jcr:content/metadata`.
1. Establezca la propiedad `dam:gPlaneRadius` en el valor de milímetro deseado.

   Para mejorar la eficiencia del procesamiento, Adobe recomienda limitar este valor a aproximadamente la dimensión más grande del objeto más grande que se va a mostrar en el escenario.

   Por ejemplo, un modelo de plano jet de 20 metros de largo se muestra bien si `dam:gPlaneRadius=20000`.

1. Cerca de la esquina superior izquierda de la página CRXDE Lite, toque **[!UICONTROL Guardar todo]**.

