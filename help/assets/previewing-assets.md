---
title: Vista previa de recursos de Dynamic Media
seo-title: Vista previa de recursos de Dynamic Media
description: Obtenga información sobre la previsualización de recursos en Dynamic Media
seo-description: Obtenga información sobre la previsualización de recursos en Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 5%

---


# Vista previa de recursos de Dynamic Media {#previewing-assets}

Puede utilizar la **[!UICONTROL Previsualización]** para ver el aspecto que tendrá un recurso digital de Dynamic Media cuando lo vea un cliente en su propio navegador web. El visor predeterminado incrustado entre dispositivos asignado al recurso se utiliza para la **[!UICONTROL Previsualización]**.

Un visor es una colección de varios ajustes o &quot;ajustes preestablecidos&quot;, como el tamaño de visualización del visor, el comportamiento de zoom, las combinaciones de colores, los bordes, las fuentes, etc., que determinan la forma en que los usuarios vista los recursos de medios enriquecidos en las pantallas de sus equipos y en los dispositivos móviles.

Además de utilizar la función de previsualización dedicada para vídeo, conjuntos de giros y conjuntos de imágenes, también puede realizar la previsualización de un recurso mediante los ajustes preestablecidos de visor que ha creado. O bien, utilice ajustes preestablecidos de imagen para previsualización de representaciones de imágenes.

* [Aplicación de ajustes preestablecidos de imagen](image-presets.md)
* [Aplicación de ajustes preestablecidos de visor](viewer-presets.md)

>[!NOTE]
>
>Cuando se encuentra en una página web (Sites) en AEM, no puede obtener una vista previa de los recursos en el modo de **[!UICONTROL edición]**. Debe ir al modo **[!UICONTROL Vista previa]** haciendo clic en **Vista previa** en la esquina superior derecha.

**Para previsualización de recursos**:

1. From **Adobe Experience Manager**, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Asset]s **, then**[!UICONTROL Files ]**to access assets.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL List View]**.
1. (Opcional) Utilice la columna **[!UICONTROL Tipo]** para ordenar los recursos según el tipo de previsualización.
1. En la columna **[!UICONTROL Título]** , haga clic en el nombre del título (no en la imagen en miniatura) del recurso que desea previsualización.
1. Según el tipo de recurso en el que haya hecho clic, realice una de las siguientes acciones:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo de recurso que tocó</strong><br /> </td> 
   <td><strong>¿Se puede realizar la previsualización de recursos en una representación concreta?</strong></td> 
   <td><strong>¿Se puede previsualización de recursos en un visor concreto?</strong></td> 
  </tr>
  <tr>
   <td><p>Imagen</p> </td> 
   <td>Sí</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de recursos en una representación concreta</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Representaciones </strong>en la lista y, a continuación, seleccione una representación concreta que desee previsualización.</li> 
    </ul> <p><strong>previsualización de recursos en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visores</strong> en la lista y, a continuación, seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los <strong>+</strong> y <strong>- </strong>iconos para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si está en un dispositivo móvil, toque con el doble la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, toque con el doble la imagen de nuevo para restablecer el estado de zoom. Arrastre la imagen para desplazarse.</p> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimedia</td> 
   <td>Sí</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de recursos en una representación concreta</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Representaciones </strong>en la lista y, a continuación, seleccione una representación concreta que desee previsualización.</li> 
    </ul> <p>La selección de una representación de vídeo de mayor resolución en la previsualización puede hacer que el vídeo aparezca truncado. Esto se debe a que la previsualización de representación muestra la resolución exacta que verán los clientes, todo en el contexto del visor integrado que se utiliza para la previsualización.</p> <p>Cuando se previsualización un conjunto de vídeos adaptables en el nivel de recurso, las representaciones se agrupan en una única experiencia de reproducción. Es decir, el tamaño del vídeo adaptable es correcto para su visualización y reproducción con la mejor resolución en el contexto del dispositivo de visualización y la velocidad de conexión.<br /> </p> <p><strong>previsualización de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visores</strong> en la lista y, a continuación, seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de imágenes</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visores</strong> en la lista y, a continuación, seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los <strong>+</strong> y <strong>- </strong>iconos para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si está en un dispositivo móvil, toque con el doble la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, toque con el doble la imagen de nuevo para restablecer el estado de zoom. Arrastre la imagen para desplazarse.</p> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de giros</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visores</strong> en la lista y, a continuación, seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los <strong>+</strong> y <strong>- </strong>iconos para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si está en un dispositivo móvil, toque con el doble la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, toque con el doble la imagen de nuevo para restablecer el estado de zoom. Arrastre la imagen para desplazarse.</p> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de medios mixtos</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visores</strong> en la lista y, a continuación, seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los <strong>+</strong> y <strong>- </strong>iconos para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si está en un dispositivo móvil, toque con el doble la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, toque con el doble la imagen de nuevo para restablecer el estado de zoom. Arrastre la imagen para desplazarse.</p> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de carruseles</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>previsualización de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Para activar o desactivar ajustes preestablecidos de visor en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Gestión de ajustes preestablecidos</a>de visor.</p> </td> 
  </tr>
 </tbody>
</table>

