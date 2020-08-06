---
title: Configuración de un escenario de IBL con Autodesk Maya y Mental Ray
seo-title: Configuración de un escenario de IBL con Autodesk Maya y Mental Ray
description: Aprenda a configurar un escenario de IBL con Autodesk Maya y Mental Ray.
seo-description: Aprenda a configurar un escenario de IBL con Autodesk Maya y Mental Ray.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 84%

---


# Configuración de un escenario de IBL con Autodesk Maya y Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. En Maya, cree una nueva escena vacía.

1. Cree una referencia (temporal) a un modelo representativo. De este modo, se facilita la evaluación de la iluminación, la configuración de las cámaras y la configuración del procesador.
1. Establezca la iluminación basada en imágenes.

   1. En Configuración de procesamiento, seleccione **[!UICONTROL Procesar mediante: Mental Ray]** y abra la ficha Escena.****
   1. Open the **[!UICONTROL Environment]** accordion, then click **[!UICONTROL Create Image Based Lighting]**.
   1. Haga clic en el icono de la casilla que tiene una flecha derecha en la parte izquierda del cuadro para seleccionar el nodo `mentalRayIblShape1`[!UICONTROL  de IBL y cierre Configuración de procesamiento].
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.

   1. Set the [!UICONTROL Scale] of the node to make the environment sphere significantly larger than the largest 3D object to be shown with this stage (for example, `10000,10000,10000`).
   1. Seleccione el nodo `AdobeIblShape` y configúrelo como sigue:

      * **[!UICONTROL Asignación]**: esférica
      * **[!UICONTROL Tipo]**: archivo de imagen
      * **[!UICONTROL Emitir luz]**: verdadero
   1. Attach the desired 32-bit TIFF image to the `AdobeIbl` node.


1. Configure el plano de tierra.

   * Cree un plano adecuado para utilizar como plano de tierra y establezca su tamaño de modo que quepa razonablemente en la esfera IBL, pasándolo por el origen de coordenadas.
   * Adjunte un material **[!UICONTROL Usar fondo]** al plano de tierra, asígnele el nombre `AdobeUseBackground` y adjúntelo al objeto plano de tierra.

1. (Opcional) Cree y configure las cámaras.

   Coloque las cámaras de modo que miren hacia el centro de la escena donde se insertará el recurso. Asegúrese de que las cámaras se pueden procesar.

1. Configure el procesamiento con Mental Ray.

   Configure the [!UICONTROL Render Settings] with the following suggestions.

   * **[!UICONTROL Ficha Común]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Ficha Calidad]**

      * **[!UICONTROL Calidad global]**: `0.5` o menos
      * **[!UICONTROL Modo]** de difusión indirecta (GI) - `Final Gather`
      * **[!UICONTROL Tamaño]** del filtro - `2.0`, `2.0`
   * Procese la escena con los tamaños de imagen típicos que tenga previsto utilizar. Si fuera necesario, ajuste las luces, la configuración de procesamiento o ambas opciones para conseguir los resultados deseados.

      Tenga en cuenta que el procesamiento con Mental Ray, mediante la iluminación basada en imagen es muy lento y consume muchos recursos de la CPU. Adobe recomienda que configure las opciones de menor calidad que tengan capacidad para producir la calidad de procesamiento deseada.


1. Quite la referencia que ha creado en la etapa 2. 

1. Guarde la escena y salga de Autodesk Maya.

1. Cargue la escena y el archivo IBL PTIFF en AEM, y espere a que se complete el procesamiento de la carga.

   Consulte [Carga de recursos](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Resuelva las dependencias del archivo.

   Consulte [Resolución de dependencias de archivo](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   Es posible que AEM 3D no pueda detectar la imagen de IBL configurada en el escenario. En estas situaciones, debe resolver manualmente las dependencias que faltan. Puede asignar la misma imagen IBL PTIFF cargada anteriormente para cada una de las dependencias que faltan. O bien, puede asignar diferentes imágenes para controlar aún más los efectos de IBL. Después de resolver las dependencias, asegúrese de pulsar en **Guardar** para iniciar el reprocesamiento. 

1. Abra Propiedades del recurso en AEM. Defina el título con una cadena adecuada para que aparezca en la lista desplegable Selector de escenarios. Compruebe que el valor **[!UICONTROL Clase]** esté establecido en **[!UICONTROL Escenario 3D]**. Guarde y salga.

1. Abra un recurso 3D, seleccione el nuevo escenario y verifique que su vista previa y procesamiento sean los esperados.

