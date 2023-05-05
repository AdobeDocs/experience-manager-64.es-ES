---
title: Filtro Disposición de contenido
seo-title: Content Disposition Filter
description: Aprenda a utilizar el Filtro de disposición de contenido para evitar ataques XSS.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---

# Filtro Disposición de contenido {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El filtro de disposición de contenido es una función de seguridad contra los ataques XSS en archivos SVG.

Una vez instalado, el filtro bloquea el acceso a todos los recursos. Por ejemplo, no se pudo ver un PDF en línea. En esta sección se describe cómo configurar el filtro según sus necesidades.

## Configurar el filtro de disposición de contenido {#configure-content-disposition-filter}

Puede ver la [Filtro de disposición de contenido Apache Sling en GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

Las opciones del Filtro de disposición de contenido proporcionan las siguientes funciones:

* **Rutas de disposición de contenido:** una lista de rutas en las que se aplicará el filtro seguida de una lista de tipos de mime que se excluirán en esa ruta. Esta ruta debe ser una ruta absoluta y puede contener un comodín (`*`) al final, para que coincida con cada ruta de recurso con el prefijo de ruta dado. Por ejemplo: `/content/*:image/jpeg,image/svg+xml` aplicará el filtro a cada nodo de `/content` excepto imágenes jpg y svg

* **Rutas de recurso excluidas:** una lista de recursos excluidos, cada ruta de recurso debe proporcionarse como ruta absoluta y completa. No se admiten caracteres comodín/coincidentes de prefijo.

* **Habilitar para todas las rutas de recursos:** este indicador controla si se habilita este filtro para todas las rutas, excepto para las rutas excluidas definidas por las rutas de recursos excluidas. Si se establece en &quot;true&quot;, se ignorarán las rutas de disposición del contenido. Independientemente de la configuración, solo se cubren las rutas de recursos que contienen una propiedad denominada `jcr:data` o
   `jcr:content jcr:data`.
