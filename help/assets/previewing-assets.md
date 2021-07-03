---
title: Vista previa de recursos de Dynamic Media
seo-title: Vista previa de recursos de Dynamic Media
description: Obtenga información sobre cómo previsualizar recursos en Dynamic Media
seo-description: Obtenga información sobre cómo previsualizar recursos en Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Administración de recursos,Representaciones
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 5%

---

# Vista previa de recursos de Dynamic Media {#previewing-assets}

Puede utilizar **[!UICONTROL Preview]** para ver el aspecto de un recurso digital de Dynamic Media cuando lo ve un cliente en su propio explorador web. El visor predeterminado integrado entre dispositivos asignado al recurso se utiliza para la **[!UICONTROL Vista previa]**.

Un visor es una colección de varias configuraciones o &quot;ajustes preestablecidos&quot;, como el tamaño de visualización del visor, el comportamiento de zoom, los esquemas de color, los bordes, las fuentes, etc., que determinan cómo ven los usuarios los recursos de medios enriquecidos en sus pantallas de equipos y dispositivos móviles.

Además de utilizar la función de vista previa dedicada para vídeo, conjuntos de giros y conjuntos de imágenes, también puede obtener una vista previa de un recurso mediante los ajustes preestablecidos de visor que ha creado. O bien, utilice ajustes preestablecidos de imagen para previsualizar las representaciones de imágenes.

* [Aplicación de ajustes preestablecidos de imagen](image-presets.md)
* [Aplicación de ajustes preestablecidos de visor](viewer-presets.md)

>[!NOTE]
>
>Cuando se encuentra en una página web (Sites) en AEM, no puede obtener una vista previa de los recursos en el modo de **[!UICONTROL edición]**. Debe ir al modo **[!UICONTROL Vista previa]** haciendo clic en **Vista previa** en la esquina superior derecha.

**Para previsualizar recursos**:

1. Desde **Adobe Experience Manager**, en la página **[!UICONTROL Navegación]**, pulse **[!UICONTROL Recurso]s** y, a continuación, pulse **[!UICONTROL Archivos]** para acceder a los recursos.
1. Cerca de la esquina superior derecha de la página, en la lista desplegable **[!UICONTROL Ver]**, pulse **[!UICONTROL Vista de lista]**.
1. (Opcional) Utilice la columna **[!UICONTROL Type]** para ordenar los recursos por el tipo de vista previa.
1. En la columna **[!UICONTROL Title]** , haga clic en el nombre del título (no en la imagen en miniatura) del recurso cuya vista previa desea ver.
1. En función del tipo de recurso en el que haya hecho clic, realice una de las siguientes acciones:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo de recurso que tocó</strong><br /> </td> 
   <td><strong>¿Es posible obtener una vista previa del recurso en una representación determinada?</strong></td> 
   <td><strong>¿Se puede previsualizar el recurso en un visor determinado?</strong></td> 
  </tr>
  <tr>
   <td><p>Imagen</p> </td> 
   <td>Sí</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa del recurso en una representación concreta</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Representaciones </strong>en la lista y, a continuación, seleccione una representación concreta que desee previsualizar.</li> 
    </ul> <p><strong>Para previsualizar recursos en un visor determinado</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visualizadores</strong> en la lista y, a continuación, seleccione un visualizador que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los iconos <strong>+</strong> y <strong>- </strong>para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si se encuentra en un dispositivo móvil, toque dos veces la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, vuelva a tocar dos veces la imagen para restablecer el estado del zoom. Arrastre la imagen hasta la panorámica.</p> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimedia</td> 
   <td>Sí</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa del recurso en una representación concreta</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Representaciones </strong>en la lista y, a continuación, seleccione una representación concreta que desee previsualizar.</li> 
    </ul> <p>Si se selecciona una representación de vídeo de mayor resolución para previsualizar, es posible que el vídeo aparezca truncado. Esto se debe a que la vista previa de la representación muestra la resolución exacta que los clientes verán, todo en el contexto del visor integrado que se utiliza para la vista previa.</p> <p>Al previsualizar un conjunto de vídeos adaptables en el nivel de recurso, las representaciones se agrupan en una experiencia de reproducción. Es decir, el vídeo adaptable tiene un tamaño adecuado para visualizarlo y reproducirlo con la mejor resolución en el contexto del dispositivo de visualización y la velocidad de conexión.<br /> </p> <p><strong>Para obtener una vista previa de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visualizadores</strong> en la lista y, a continuación, seleccione un visualizador que desee aplicar al recurso.</li> 
    </ul> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de imágenes</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visualizadores</strong> en la lista y, a continuación, seleccione un visualizador que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los iconos <strong>+</strong> y <strong>- </strong>para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si se encuentra en un dispositivo móvil, toque dos veces la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, vuelva a tocar dos veces la imagen para restablecer el estado del zoom. Arrastre la imagen hasta la panorámica.</p> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de giros</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visualizadores</strong> en la lista y, a continuación, seleccione un visualizador que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los iconos <strong>+</strong> y <strong>- </strong>para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si se encuentra en un dispositivo móvil, toque dos veces la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, vuelva a tocar dos veces la imagen para restablecer el estado del zoom. Arrastre la imagen hasta la panorámica.</p> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de medios mixtos</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Haga clic en <strong>Visualizadores</strong> en la lista y, a continuación, seleccione un visualizador que desee aplicar al recurso.</li> 
    </ul> <p>Utilice los iconos <strong>+</strong> y <strong>- </strong>para aumentar o reducir el zoom de la imagen seleccionada, respectivamente. Haga clic en <strong>Restablecer</strong> para devolver la imagen al zoom original.<br /> Si se encuentra en un dispositivo móvil, toque dos veces la imagen para acercarla mediante pasos. Cuando alcance el zoom máximo, vuelva a tocar dos veces la imagen para restablecer el estado del zoom. Arrastre la imagen hasta la panorámica.</p> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de carrusel</td> 
   <td>No</td> 
   <td>Sí</td> 
   <td><p><strong>Para obtener una vista previa de un recurso en un visor concreto</strong></p> 
    <ul> 
     <li>Cerca de la esquina superior izquierda de la página, haga clic en el icono para que aparezca la lista desplegable. Seleccione un visor que desee aplicar al recurso.</li> 
    </ul> <p>Para habilitar o deshabilitar los ajustes preestablecidos de visualizador en la interfaz de usuario, consulte <a href="/help/assets/managing-viewer-presets.md">Administración de ajustes preestablecidos de visualizador</a>.</p> </td> 
  </tr>
 </tbody>
</table>
