---
title: Acerca del uso de escenarios en AEM 3D
seo-title: Acerca del uso de escenarios en AEM 3D
description: Las fases son archivos de escena 3D de peso claro que proporcionan el entorno de visualización básico.
seo-description: Las fases son archivos de escena 3D de peso claro que proporcionan el entorno de visualización básico.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 56%

---


# Acerca del uso de escenarios en AEM 3D {#about-the-use-of-stages-in-aem-d}

Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico (luces, fondos, planos de tierra u otra geometría fija), cámaras predefinidas opcionales y opciones de configuración de procesamiento para procesadores de otros fabricantes.

>[!NOTE]
>
>The **[!UICONTROL OBJ 3D]** format does not support lights. Por lo tanto, no se puede utilizar para proporcionar a escenarios AEM 3D.

El formato de archivo del escenario determina qué procesador puede utilizar con dicho escenario. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Si tiene previsto utilizar únicamente el procesador Rapid Refine™ predeterminado, se acepta cualquier formato de archivo de escenario.

Todos los ajustes de procesamiento en AEM 3D, excepto el tipo y tamaño de la imagen de salida, deben preconfigurarse y guardarse en el archivo del escenario antes de cargarlo en AEM.