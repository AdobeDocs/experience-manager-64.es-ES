---
title: Acerca de la carga y el procesamiento de los recursos 3D en AEM
seo-title: Acerca de la carga y el procesamiento de los recursos 3D en AEM
description: Adobe recomienda cargar todos los archivos a los que se hace referencia en el mismo momento (o antes) de cargar el archivo de modelo 3D principal. Cuando se haya completado la carga, los archivos 3D se convierten y se aplica un proceso adicional para preparar el recurso para la visualización y el procesamiento.
seo-description: Adobe recomienda cargar todos los archivos a los que se hace referencia en el mismo momento (o antes) de cargar el archivo de modelo 3D principal. Cuando se haya completado la carga, los archivos 3D se convierten y se aplica un proceso adicional para preparar el recurso para la visualización y el procesamiento.
uuid: 82ccfbf8-1f82-4960-b9e5-3ce65c16435a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 0be4a856-951b-4cb6-8103-8004052c63a0
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 81%

---


# Acerca de la carga y el procesamiento de los recursos 3D en AEM{#about-the-uploading-and-processing-of-d-assets-in-aem}

Utilice mecanismos estándar de carga o sincronización para insertar los recursos 3D y sus archivos de referencia asociados en AEM Assets.

Consulte [Carga de recursos](/help/assets/managing-assets-touch-ui.md#uploading-assets).

Adobe recomienda cargar todos los archivos a los que se hace referencia antes de cargar el archivo de modelo 3D principal o al mismo tiempo. Sin embargo, esto no es un requisito.

Cuando se haya completado la carga, los archivos 3D se convierten y se aplica un proceso adicional para preparar el recurso para la visualización y el procesamiento.

## Prácticas recomendadas para cargar recursos 3D {#best-practices-for-uploading-d-assets}

* Por lo general, no hay restricciones en dónde se carga el contenido 3D en la jerarquía de carpetas de AEM Assets. Sin embargo, la resolución de dependencias de archivos automatizada de AEM 3D tiene limitaciones de intervalo para controlar el tiempo necesario para buscar en repositorios de recursos de gran tamaño. Por lo tanto, Adobe recomienda que la carga de recursos 3D y sus dependientes de archivo se realice con una proximidad razonable a cada archivo (carpeta maestra común). Después de que se hayan resuelto las dependencias de archivo, puede mover libremente tanto el recurso 3D como sus archivos dependientes a cualquier lugar dentro del repositorio, sin perder las relaciones establecidas.
* Adobe recomienda que decida una estructura de carpetas coherente para el contenido 3D *antes de realizar la carga. A continuación se presentan algunos planteamientos sugeridos que puede aplicar:

   * **Mantener una carpeta independiente para cada recurso 3D que se cargue**.

      La carpeta que contiene el archivo principal del modelo 3D y todos sus archivos dependientes. Si bien colocar todos los recursos y archivos dependientes en una carpeta es un proceso fácil de implementar, resulta engorroso buscar contenido. También complica el uso compartido de los archivos dependientes (mapas de textura) entre los modelos.

   * **Mantener los modelos en una carpeta y los archivos dependientes en una carpeta del mismo nivel o una subcarpeta**.

      Este método facilita el uso compartido de dependientes entre los modelos. Sin embargo, puede resultar difícil localizar dependientes específicos si existe un gran número de recursos.

   * **Mantener jerarquías de carpetas independientes y paralelas para los modelos y los dependientes**.

      Este método se puede personalizar según el modo de almacenamiento preferido de las aplicaciones de creación 3D, como por ejemplo Autodesk Maya.

* Los recursos dependientes no deben eliminarse, a menos que los recursos 3D asociados que hacen referencia a ellos también se eliminen. Sin embargo, puede eliminar libremente los recursos 3D sin tener que eliminar sus recursos dependientes. Si se pierde una dependencia accidentalmente, puede resolverla fácilmente para restaurarla.

   Consulte [Resolución de dependencias de archivo](/help/assets/resolve-file-dependencies.md).

## Consideraciones de rendimiento al cargar archivos 3D {#performance-considerations-when-uploading-d-files}

La conversión y el procesamiento de archivos 3D suelen utilizar gran cantidad de recursos de CPU y memoria en un servidor. También tardan una importante cantidad de tiempo. Los tiempos de procesamiento a menudo varían significativamente en función del tamaño del modelo y las funciones del servidor. Por ejemplo, un modelo pequeño típico con menos que 100 000 caras normalmente está listo para su visualización en menos de un minuto. Se procesan por completo en 2 a 3 minutos. En cambio, el procesamiento de un modelo de gran tamaño con más de un millón de caras puede tardar diez minutos en completarse.

Los trabajos de conversión, proceso y procesamiento se ponen en cola según las necesidades para evitar que se ralentice en exceso el servidor. Mensaje &quot;Esperando procesamiento...&quot; a veces se muestra en la **[!UICONTROL Vista de tarjeta]** en el momento en que cargó los recursos. Este estado indica que el otros trabajos de procesamiento o proceso deben finalizar antes de que se procese el recurso actual. 

## Supervisión del estado de procesamiento de los archivos 3D cargados {#monitoring-the-processing-status-of-your-uploaded-d-files}

Solo en **[!UICONTROL Vista de tarjetas]**, el estado y la progresión del procesamiento se muestran como una pancarta de progreso en la tarjeta del recurso. Cada modelo 3D cargado suele pasar por las siguientes 4 a 6 etapas de procesamiento ordenado:

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
   <td>Creación de mapas de iluminación</td> 
   <td>Opcional. Permite mejorar la calidad de la vista previa interactiva y acelerar el procesamiento con el procesador predeterminado.</td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>Creación de animaciones</td> 
   <td>Opcional. Permite generar una animación sencilla que luego se utiliza como miniatura visual en la vista de tarjeta.</td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>Esperando procesamiento</td> 
   <td>Se muestra cuando otros recursos 3D tienen prioridad de procesamiento. Por ejemplo, los recursos cargados anteriormente, pero que aún no han finalizado el procesamiento.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Puede realizar la vista de un recurso 3D en **[!UICONTROL Vista de detalles]** o procesarlo una vez finalizada la etapa de creación de previsualizaciones. No es necesario esperar a que se completen todas las etapas de procesamiento.

