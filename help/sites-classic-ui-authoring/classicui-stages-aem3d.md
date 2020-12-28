---
title: Acerca del uso de escenarios en AEM 3D
seo-title: Acerca del uso de escenarios en AEM 3D
description: Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico (luces, fondos, planos de tierra u otra geometría fija), cámaras predefinidas opcionales y opciones de configuración de procesamiento para procesadores de otros fabricantes.
seo-description: Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico (luces, fondos, planos de tierra u otra geometría fija), cámaras predefinidas opcionales y opciones de configuración de procesamiento para procesadores de otros fabricantes.
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 91%

---


# Acerca del uso de escenarios en AEM 3D{#about-the-use-of-stages-in-aem-d}

Los escenarios son archivos de escena 3D ligeros que proporcionan el entorno de visualización básico (luces, fondos, planos de tierra u otra geometría fija), cámaras predefinidas opcionales y opciones de configuración de procesamiento para procesadores de otros fabricantes.

>[!NOTE]
>
>El formato 3D de OBJ no admite luces. Por lo tanto, no se puede utilizar para proporcionar a escenarios AEM 3D.

El formato de archivo del escenario determina qué procesador puede utilizar con dicho escenario. Por ejemplo, si Autodesk® Maya® se utiliza para una representación de alta calidad, la etapa debe estar en formato `.ma` o `.mb`. Si tiene previsto utilizar únicamente el procesador Rapid Refine™ predeterminado, se acepta cualquier formato de archivo de escenario.

Todas las opciones de configuración de AEM 3D, excepto el tipo y tamaño de imagen de salida, se deben preconfigurar y guardar en el archivo de escenario antes de la carga a AEM.

