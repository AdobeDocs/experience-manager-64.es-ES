---
title: Varios alquileres para colecciones, fragmentos y plantillas de fragmentos
description: Segregar contenido en el repositorio CRX en función de la organización del cliente para evitar el acceso no autorizado.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 4%

---

# Varios alquileres para colecciones, fragmentos y plantillas de fragmentos {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La función de inquilinos múltiples le permite segregar contenido en CRX en función del prefijo de organización y el ID de organización para proteger el contenido del acceso no autorizado por parte de los usuarios de otras organizaciones.

Adobe Experience Manager (AEM) Assets almacena datos de cada organización en una ruta diferente. Cada ruta específica de la organización se identifica mediante el prefijo de organización y el ID de organización.
que se incluye en la ubicación tradicional donde se almacenan distintos tipos de activos en CRX.

Por ejemplo, si crea una carpeta con el nombre `Demo`, AEM activos de forma predeterminada almacena la carpeta en `../content/dam/Demo` ubicación en CRX. Con la función de inquilino múltiple habilitada, puede almacenar los datos en `../content/dam/<organization prefix>/<organization id>Demo`.

Por ejemplo, para los usuarios de Adobe Marketing Cloud de AEM Assets (On Demand) asignados a `aodpremium` organización, puede utilizar la función de varios alquileres para configurar la siguiente ruta a `../content/dam/mac/aodpremiumDemo`, separe el contenido. En este ejemplo `mac` es el prefijo de la organización y `aodpremium` es el ID de organización.

En función de la organización y el ID del usuario, esta ruta cualificada se muestra en la interfaz de AEM Assets y en varios asistentes, incluidos los asistentes de creación Mover y Fragmentar para aplicar la agregación.

La función de inquilino múltiple permite segmentar los siguientes tipos de activos y componentes:

* Colecciones
* Colecciones públicas
* Catálogos (incluido el asistente Agregar/Seleccionar página )
* Plantillas
* Plantillas de recorte
* Lightbox
