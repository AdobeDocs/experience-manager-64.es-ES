---
title: Directrices de codificación
seo-title: Coding Guidelines
description: Directrices, sugerencias y trucos para desarrolladores de Communities
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: 022043cd-35ed-49b1-b5b4-5cc92d29cef4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 4%

---

# Directrices de codificación {#coding-guidelines}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Pautas, consejos y trucos {#guidelines-tips-and-tricks}

El trabajo con AEM Communities ha pasado de depender en gran medida de las páginas del servidor Java a depender de la flexibilidad de la elección de los lenguajes de secuencias de comandos en los que la lógica empresarial, el estilo y el contenido de la página son distintos entre sí.

La mayor flexibilidad para trabajar con contenido generado por el usuario (UGC, por sus siglas en inglés) es a través de la API de SocialResourceProvider , que elimina la necesidad de tener en cuenta cuál es [SRP](srp.md) para la implementación.

A continuación se indican varias directrices de codificación y prácticas recomendadas para los desarrolladores de AEM Communities:

### Código  {#code}

* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - cómo evitar escribir una aplicación que solo funcione cuando UGC se almacena en JCR (JSRP).
* [Refactorización de SocialUtils](socialutils.md) - métodos de utilidad para SRP que reemplazan a SocialUtils.
* [Convenciones de nomenclatura](naming-conventions.md) : convenciones de nomenclatura para clases de Java personalizadas.

### Scripts {#scripts}

* [Carga de componentes de Communities](sideloading.md) : cómo añadir dinámicamente un componente después de que se cargue la página.
* [Elementos básicos del editor de texto enriquecido](rte.md) : cómo personalizar la IU de texto enriquecido que se proporciona a los miembros para publicar contenido.

### IDE {#ide}

* [Uso de Maven para comunidades](maven.md) - cómo incluir el jar de la API de Communities.
* [Refactorización de SocialUtils](socialutils.md) - métodos de utilidad para SRP que reemplazan a SocialUtils.
