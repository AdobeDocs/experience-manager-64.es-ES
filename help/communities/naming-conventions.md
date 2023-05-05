---
title: Convenciones de nomenclatura
seo-title: Naming Conventions
description: Guiones en nombre de paquete Java
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Convenciones de nomenclatura {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Guiones en nombre de paquete Java {#hyphens-in-java-package-name}

Al crear una ubicación para una clase Java, tenga en cuenta que el nombre del paquete debe coincidir con el de la ubicación de la carpeta del repositorio con los guiones de la ruta de acceso que se hayan escapado correctamente.

Aunque el uso de guiones en los nombres de elementos del repositorio es una práctica recomendada en AEM desarrollo, los guiones son ilegales en los nombres de paquetes Java.

La plataforma CRX subyacente debe ser capaz de distinguir entre un guión bajo real &quot;_&#39; y un guión &#39;-&#39;. Por lo tanto, en JCR, el guión debe reemplazarse por su valor Unicode (u002d) y evitarse con un guión bajo &quot;_&#39;.

Por ejemplo, si la ruta del repositorio es **/apps/my-example/component/info/Info.java**, el nombre del paquete debe ser `java package apps.my_002dexample.component.info;`

Observe que se debe escapar un guión bajo de forma similar, de modo que `_` se convierte `_005f`.
