---
title: Configuración de un escenario de IBL con Autodesk Maya y Mental Ray
seo-title: Configuración de un escenario de IBL con Autodesk Maya y Mental Ray
description: Cómo configurar un escenario IBL con Autodesk Maya y Mental Ray
seo-description: Cómo configurar un escenario IBL con Autodesk Maya y Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: 5964edfadf597652f754ca3c64343b0b90e40796
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 73%

---


# Configuración de un escenario de IBL con Autodesk Maya y Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. En Maya, cree una nueva escena vacía.

1. Cree una referencia (temporal) a un modelo representativo. De este modo, se facilita la evaluación de la iluminación, la configuración de las cámaras y la configuración del procesador.
1. Establezca la iluminación basada en imágenes.

   1. In **[!UICONTROL Render Settings]**, select **[!UICONTROL Render Render Using: mental ray]**, and open the Scene tab.
   1. Open the **[!UICONTROL Render Environment]** accordion and click **[!UICONTROL Render Create Image Based Lighting**.
   1. Click the box icon that has a right arrow on the left side of the box to select the IBL node `mentalRayIblShape1`, then exit **[!UICONTROL Render Settings]**.
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.
   1. Establezca la escala del nodo para hacer que la esfera del entorno sea significativamente más grande que el objeto 3D de mayor tamaño que se mostrará con este escenario (por ejemplo, `10000,10000,10000`).
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

   Configure the **[!UICONTROL Render Settings]** with the following suggestions.

   * **[!UICONTROL Ficha Común]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all **[!UICONTROL Renderable Cameras]**.

   * **[!UICONTROL Ficha Calidad]**

      * **Calidad global**: `0.5` o menos
      * **Modo** de difusión indirecta (GI) - `Final Gather`
      * **Tamaño** del filtro - `2.0`, `2.0`
   * Procese la escena con los tamaños de imagen típicos que tenga previsto utilizar. Si fuera necesario, ajuste las luces, la configuración de procesamiento o ambas opciones para conseguir los resultados deseados.

      Tenga en cuenta que el procesamiento con Mental Ray, mediante la iluminación basada en imagen es muy lento y consume muchos recursos de la CPU. Adobe recomienda que configure las opciones de menor calidad que tengan capacidad para producir la calidad de procesamiento deseada.


1. Quite la referencia que ha creado en la etapa 2. 

1. Guarde la escena y salga de Autodesk Maya.

1. Cargue la escena y el archivo IBL PTIFF en AEM, y espere a que se complete el procesamiento de la carga.

   Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

1. Resuelva las dependencias del archivo.

   Consulte [Resolución de dependencias de archivo](resolve-file-dependencies.md).

   Es posible que AEM 3D no pueda detectar la imagen de IBL configurada en el escenario. En estas situaciones, debe resolver manualmente las dependencias que faltan. Puede asignar la misma imagen IBL PTIFF cargada anteriormente para cada una de las dependencias que faltan. O bien, puede asignar diferentes imágenes para controlar aún más los efectos de IBL. Después de resolver las dependencias, asegúrese de pulsar en **[!UICONTROL Guardar]** para iniciar el reprocesamiento. 

1. Abra Propiedades del recurso en AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Compruebe que el valor **[!UICONTROL Clase]** esté establecido en **[!UICONTROL Escenario 3D]**. Guarde y salga.

1. Abra un recurso 3D, seleccione el nuevo escenario y verifique que su vista previa y procesamiento sean los esperados.

