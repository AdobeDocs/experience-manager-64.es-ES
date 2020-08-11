---
title: Acerca de la carga y el procesamiento de los recursos 3D en AEM
seo-title: Acerca de la carga y el procesamiento de los recursos 3D en AEM
description: Prácticas recomendadas para cargar y procesar recursos 3D.
seo-description: Prácticas recomendadas para cargar y procesar recursos 3D.
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 68%

---


# Acerca de la carga y el procesamiento de los recursos 3D en AEM {#about-the-uploading-and-processing-of-d-assets-in-aem}

>[!IMPORTANT]
>
>Ya no se admite AEM 3D en AEM 6.4. Adobe recomienda utilizar la función de recursos 3D en [AEM como Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html).

Utilice mecanismos estándar de carga o sincronización para insertar los recursos 3D y sus archivos de referencia asociados en AEM Assets.

Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

Adobe recomienda cargar todos los archivos a los que se hace referencia antes de cargar el archivo de modelo 3D principal o al mismo tiempo. Sin embargo, esto no es un requisito.

Cuando se haya completado la carga, los archivos 3D se convierten y se aplica un proceso adicional para preparar el recurso para la visualización y el procesamiento.

## Prácticas recomendadas para cargar recursos 3D {#best-practices-for-uploading-d-assets}

* Por lo general, no hay restricciones en dónde se carga el contenido 3D en la jerarquía de carpetas de AEM Assets. Sin embargo, la resolución de dependencias de archivos automatizada de AEM 3D tiene limitaciones de intervalo para controlar el tiempo necesario para buscar en repositorios de recursos de gran tamaño. Por lo tanto, Adobe recomienda que la carga de recursos 3D y sus dependientes de archivo se realice con una proximidad razonable a cada archivo (carpeta maestra común). Después de que se hayan resuelto las dependencias de archivo, puede mover libremente tanto el recurso 3D como sus archivos dependientes a cualquier lugar dentro del repositorio, sin perder las relaciones establecidas.
* Adobe recomienda que elija una estructura de carpetas constante para el contenido 3D *antes* de realizar cargas. A continuación se presentan algunos planteamientos sugeridos que puede aplicar:

   * **Mantener una carpeta independiente para cada recurso 3D que se cargue**.

      La carpeta que contiene el archivo principal del modelo 3D y todos sus archivos dependientes. Si bien colocar todos los recursos y archivos dependientes en una carpeta es un proceso fácil de implementar, resulta engorroso buscar contenido. También complica el uso compartido de los archivos dependientes (mapas de textura) entre los modelos.

   * **Mantener los modelos en una carpeta y los archivos dependientes en una carpeta del mismo nivel o una subcarpeta**.

      Este método facilita el uso compartido de dependientes entre los modelos. Sin embargo, puede resultar difícil localizar dependientes específicos si existe un gran número de recursos.

   * **Mantener jerarquías de carpetas independientes y paralelas para los modelos y los dependientes**.

      Este método se puede personalizar según el modo de almacenamiento preferido de las aplicaciones de creación 3D, como por ejemplo Autodesk Maya.

* Los recursos dependientes no deben eliminarse, a menos que los recursos 3D asociados que hacen referencia a ellos también se eliminen. Sin embargo, puede eliminar libremente los recursos 3D sin tener que eliminar sus recursos dependientes. Si se pierde una dependencia accidentalmente, puede resolverla fácilmente para restaurarla.

   Consulte Resolución de dependencias de archivo.

## Consideraciones de rendimiento al cargar archivos 3D {#performance-considerations-when-uploading-d-files}

La conversión y el procesamiento de archivos 3D suelen utilizar gran cantidad de recursos de CPU y memoria en un servidor. También tardan una importante cantidad de tiempo. Los tiempos de procesamiento a menudo varían significativamente en función del tamaño del modelo y las funciones del servidor. Por ejemplo, un modelo pequeño típico con menos que 100 000 caras normalmente está listo para su visualización en menos de un minuto. Se procesan por completo en 2 a 3 minutos. En cambio, el procesamiento de un modelo de gran tamaño con más de un millón de caras puede tardar diez minutos en completarse.

Los trabajos de conversión, proceso y procesamiento se ponen en cola según las necesidades para evitar que se ralentice en exceso el servidor. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Este estado indica que el otros trabajos de procesamiento o proceso deben finalizar antes de que se procese el recurso actual. 

Hay mecanismos disponibles para restringir el uso de CPU para el procesamiento de ingestión y el procesamiento. Consulte Configuración [avanzada](advanced-config-3d.md) para obtener información sobre cómo configurar los límites de CPU.

## Supervisión del estado de procesamiento de los archivos 3D cargados {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. Cada modelo 3D cargado suele pasar por las siguientes 4 a 6 etapas de procesamiento ordenado:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Fase de procesamiento</strong><br /> </td> 
   <td><strong>Nombres de procesamiento</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Procesando</td> 
   <td>Procesamiento inicial básico y extracción de metadatos.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Convirtiendo formato</td> 
   <td>El modelo 3D se está convirtiendo de un formato nativo (Autodesk® Maya® o Autodesk® 3ds Max®) a un formato intermedio (FBX).</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Creación de previsualización</td> 
   <td>El archivo FBX u OBJ se ingesta y se procesa. Las dependencias de archivo se evalúan y se resuelven como referencias de recurso, en la medida de lo posible.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Creación de sombra en tierra</td> 
   <td>Opcional. Permite generar una sombra paralela de oclusión ambiental en el plano de tierra debajo del objeto 3D. Consulte Configuración <a href="/help/assets/advanced-config-3d.md">avanzada</a> para habilitar o deshabilitar este procesamiento.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>Creación de mapas de iluminación</td> 
   <td>Opcional. Permite mejorar la calidad de la vista previa interactiva y acelerar el procesamiento con el procesador predeterminado. Consulte Configuración <a href="/help/assets/advanced-config-3d.md">avanzada</a> para habilitar o deshabilitar este procesamiento.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>Creación de animaciones</td> 
   <td>Opcional. Permite generar una animación sencilla que luego se utiliza como miniatura visual en la vista de tarjeta. Consulte Configuración <a href="/help/assets/advanced-config-3d.md">avanzada</a> para habilitar o deshabilitar este procesamiento.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>Esperando procesamiento</td> 
   <td>Se muestra cuando otros recursos 3D tienen prioridad de procesamiento. Por ejemplo, los recursos cargados anteriormente, pero que aún no han finalizado el procesamiento.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. No es necesario esperar a que se completen todas las etapas de procesamiento.

