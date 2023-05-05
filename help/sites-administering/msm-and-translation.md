---
title: Administración de sitios web
seo-title: Website Administration
description: Aprenda a administrar sitios web multilingües en AEM.
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: e8f83d21-b55e-4415-a581-8df1b71a84b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 40%

---

# Administración de sitios web{#website-administration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las siguientes herramientas de administración están disponibles para administrar sitios web y páginas:

* Multi Site Manager (MSM) le permite usar el mismo contenido del sitio en varias ubicaciones, a la vez que permite variaciones:

   * [Reutilización del contenido: administrador de varios sitios y Live Copy](/help/sites-administering/msm.md)

* La traducción le permite automatizar la traducción del contenido de la página, los recursos y el contenido generado por el usuario para crear y mantener sitios web multilingües:

   * [Traducción de contenido para sitios multilingües](/help/sites-administering/translation.md)

* Estas dos funciones se pueden combinar para adaptarse a los sitios web que son [Multinacional y multilingüe](#multinational-and-multilingual-sites).

## Sitios multinacionales y multilingües {#multinational-and-multilingual-sites}

Puede crear contenido de forma eficaz para sitios multinacionales y multilingües mediante el uso combinado de Administrador de varios sitios y el flujo de trabajo de traducción. Cree una ubicación maestra en un idioma, para un país específico, y luego use ese contenido como base para otros sitios, utilizando la traducción donde sea necesario:

* [Traducir](/help/sites-administering/translation.md) el sitio principal a diferentes idiomas.

* Use [Administrador de varios sitios](/help/sites-administering/msm.md) para lo siguiente:

   * Vuelva a utilizar el contenido del sitio maestro y las traducciones para crear sitios para otros países y culturas.
   * Asegúrese de limitar el uso de Multi Site Manager al contenido en un idioma, por ejemplo: inglés maestro -> inglés ramas en sitios de países, francés maestro -> francés en sitios de países.
   * Cuando sea necesario, desasocie los elementos de las Live Copies para añadir detalles de localización.

El diagrama siguiente ilustra cómo se cruzan los conceptos principales (pero no muestra todos los niveles/elementos implicados):

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>En este escenario, y en otros comparables, MSM no gestiona las diferentes versiones lingüísticas como tal.
>
>* [MSM](/help/sites-administering/msm.md) administra la implementación del contenido traducido de un modelo (por ejemplo, un maestro global) a las copias en vivo (por ejemplo, los sitios locales), dentro de los límites de un idioma.
>* Las funciones de integración de [traducciones](/help/sites-administering/translation.md) de AEM, junto con los servicios de administración de traducciones de terceros, gestionan los diferentes idiomas y traducen el contenido a estos.
>
>Para casos de uso más avanzados, también se pueden usar MSM entre idiomas principales.

>[!NOTE]
>
>Para todos los casos de uso, se recomienda leer las siguientes prácticas recomendadas:
>
>* [Prácticas recomendadas para MSM](/help/sites-administering/msm-best-practices.md); en particular:
   >
   >   * [Crear sitio](/help/sites-administering/msm-best-practices.md#create-site)
   >   * [MSM y sitios web multilingües](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Prácticas recomendadas para la traducción](/help/sites-administering/tc-bp.md)

