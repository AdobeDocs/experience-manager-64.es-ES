---
title: Configurar un escenario estándar con Autodesk Maya y Mental Ray
seo-title: Configurar un escenario estándar con Autodesk Maya y Mental Ray
description: Cómo configurar un escenario estándar con Autodesk Maya y Mental Ray
seo-description: Cómo configurar un escenario estándar con Autodesk Maya y Mental Ray
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 85%

---


# Configurar un escenario estándar con Autodesk Maya y Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

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

   Configure las opciones de procesamiento con las sugerencias siguientes:

   * **** Comúnmente

      Anule la selección de la casilla de verificación **[!UICONTROL canal alfa (máscara)]** para todas las cámaras procesables.

   * **[!UICONTROL Ficha Calidad]**

      * **[!UICONTROL Calidad total o]** `- 0.5` inferior
      * **[!UICONTROL Modo]**  de difusión indirecta (GI):  `Final Gather`
      * **[!UICONTROL Tamaño]**  del filtro-  `2.0`,  `2.0`
   * Procese la escena con los tamaños de imagen típicos que tenga previsto utilizar. Si es necesario, perfeccione las luces, procese las configuraciones o realice ambas acciones para conseguir los resultados que desea.

      Tenga en cuenta que el procesamiento con Mental Ray, mediante la iluminación basada en imagen es muy lento y consume muchos recursos de la CPU. Adobe recomienda que configure las opciones de menor calidad que tengan capacidad para producir la calidad de procesamiento deseada.


1. Quite la referencia que ha creado en la etapa 2. 

1. Guarde la escena y salga de Autodesk Maya.
1. Cargue la escena en AEM y espere a que se complete el proceso de carga.

   Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

   Si Autodesk® Maya® no se configura en el servidor de AEM, exporte un FBX de Maya y cárguelo en AEM.

1. Abra Propiedades del recurso en AEM. Establezca **[!UICONTROL Título]** en una cadena adecuada que aparecerá en la lista desplegable **[!UICONTROL Selector de etapa]**. Compruebe que el valor **[!UICONTROL Clase]** esté establecido en **[!UICONTROL Escenario 3D]**. Guarde y salga.
1. Abra un recurso 3D, seleccione el nuevo escenario y verifique que su vista previa y procesamiento sean los esperados.

