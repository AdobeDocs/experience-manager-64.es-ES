---
title: Configurar un escenario estándar con Autodesk Maya y Mental Ray
seo-title: Configurar un escenario estándar con Autodesk Maya y Mental Ray
description: Aprenda a configurar un escenario estándar con Autodesk Maya y Mental Ray.
seo-description: Aprenda a configurar un escenario estándar con Autodesk Maya y Mental Ray.
uuid: 05c4858b-6261-4de3-a87a-03dd6bc519a4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f30c4039-3bbf-4d02-a9b5-bda6ccce16b9
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 88%

---


# Configurar un escenario estándar con Autodesk Maya y Mental Ray{#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. En Maya, cree una nueva escena vacía.
1. Cree una referencia (temporal) a un modelo representativo. De este modo, se facilita la evaluación de la iluminación, la configuración de las cámaras y la configuración del procesador.

1. Añada la iluminación como de costumbre. Actualmente, AEM 3D admite los tipos de luz siguientes:

   * Iluminación direccional
   * Luces focales
   * Apuntar luces 

   Otros tipos de iluminación se ignoran o se convierten en uno de los tipos compatibles anteriores cuando el escenario se carga en AEM 3D. Los tipos convertidos se usan cuando consulta el recurso y cuando lo procesa mediante el procesador integrado Rapid Refine. Se utilizan los tipos iluminación originales cuando se realizan operaciones de procesamiento con Maya.

1. Cree un plano del fondo si es necesario y aplique un material adecuado.

   Adobe le recomienda que configure un plano de fondo con un solo lado. Así se asegurará de que puede ver el recurso subyacente en AEM 3D sin que el plano de fondo lo oculte.

1. (Opcional) Cree y configure las cámaras.

   Coloque las cámaras de modo que miren hacia el centro de la escena donde se insertará el recurso. Asegúrese de que las cámaras se pueden procesar.

1. Configure el procesamiento con Mental Ray.

   Configure la **[!UICONTROL Configuración de procesamiento]** con las siguientes sugerencias:

   * **** Comúnmente

      Anule la selección de la casilla de verificación **[!UICONTROL canal alfa (máscara)]** para todas las [!UICONTROL Cámaras procesables].

   * **[!UICONTROL Ficha Calidad]**

      * **[!UICONTROL Calidad total o]** `- 0.5` inferior
      * **[!UICONTROL Modo]**  de difusión indirecta (GI):  `Final Gather`
      * **[!UICONTROL Tamaño]**  del filtro-  `2.0`,  `2.0`
   * Procese la escena con los tamaños de imagen típicos que tenga previsto utilizar. Si es necesario, ajuste las luces o [!UICONTROL Configuración de procesamiento], o haga ambas cosas para obtener los resultados deseados.

      Tenga en cuenta que el procesamiento con Mental Ray, mediante la iluminación basada en imagen es muy lento y consume muchos recursos de la CPU. Adobe recomienda que configure las opciones de menor calidad que tengan capacidad para producir la calidad de procesamiento deseada.


1. Quite la referencia que ha creado en la etapa 2. 
1. Guarde la escena y salga de Autodesk Maya.
1. Cargue la escena en AEM y espere a que se complete el proceso de carga.

   Consulte [Carga de recursos](/help/assets/managing-assets-touch-ui.md#uploading-assets).

   Si Autodesk® Maya® no se configura en el servidor de AEM, exporte un FBX de Maya y cárguelo en AEM.

1. Abra Propiedades del recurso en AEM. Defina el título con una cadena adecuada para que aparezca en la lista desplegable Selector de escenarios. Compruebe que el valor **[!UICONTROL Clase]** esté establecido en **[!UICONTROL Escenario 3D]**. Guarde y salga.
1. Abra un recurso 3D, seleccione el nuevo escenario y verifique que su vista previa y procesamiento sean los esperados.

