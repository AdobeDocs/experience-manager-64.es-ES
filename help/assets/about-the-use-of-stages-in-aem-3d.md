---
title: Acerca del uso de escenarios en AEM 3D
seo-title: Acerca del uso de escenarios en AEM 3D
description: Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico.
seo-description: Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
exl-id: 6d82fec0-608e-4eaa-aebd-b3ce2f7d8088
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 55%

---

# Acerca del uso de escenarios en AEM 3D {#about-the-use-of-stages-in-aem-d}

Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico (luces, fondos, planos de tierra u otra geometría fija), cámaras predefinidas opcionales y opciones de configuración de procesamiento para procesadores de otros fabricantes.

>[!NOTE]
>
>El formato **[!UICONTROL OBJ 3D]** no admite luces. Por lo tanto, no se puede utilizar para proporcionar a escenarios AEM 3D.

El formato de archivo del escenario determina qué procesador puede utilizar con dicho escenario. Por ejemplo, si Autodesk® Maya® se utiliza para el procesamiento de alta calidad, el escenario debe estar en formato `.ma` o `.mb`. Si tiene previsto utilizar únicamente el procesador Rapid Refine™ predeterminado, se acepta cualquier formato de archivo de escenario.

Todos los ajustes de procesamiento en AEM 3D, excepto el tipo y tamaño de imagen de salida, deben preconfigurarse y guardarse en el archivo de escenario antes de cargarse en AEM.
