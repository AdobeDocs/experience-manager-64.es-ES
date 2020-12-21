---
title: Convenciones de nomenclatura
seo-title: Convenciones de nomenclatura
description: Guiones en el nombre del paquete Java
seo-description: Guiones en el nombre del paquete Java
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Convenciones de nombres {#naming-conventions}

## Guiones en el nombre del paquete Java {#hyphens-in-java-package-name}

Al crear una ubicación para una clase Java, tenga en cuenta que el nombre del paquete debe coincidir con el de la ubicación de la carpeta del repositorio con cualquier guión de la ruta de acceso que haya escapado correctamente.

Aunque el uso de guiones en los nombres de los elementos del repositorio es una práctica recomendada en el desarrollo de AEM, los guiones no son válidos en los nombres de paquetes de Java.

La plataforma CRX subyacente debe poder distinguir entre un guión bajo real &#39;_&#39; y un guión &#39;-&#39;. Por lo tanto, en JCR, el guión debe reemplazarse por su valor Unicode (u002d) y escaparse con un guión bajo &#39;_&#39;.

Por ejemplo, si la ruta del repositorio es **/apps/my-example/component/info/Info.java**, el nombre del paquete debe ser `java package apps.my_002dexample.component.info;`

Tenga en cuenta que un subrayado debe tener un carácter de escape similar, de modo que `_` se convierta en `_005f`.
