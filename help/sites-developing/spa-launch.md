---
title: Integración de SPA y Adobe Experience Platform Launch
seo-title: SPA and Adobe Experience Platform Launch Integration
description: Adobe Experience Platform Launch es la forma recomendada de implementar Analytics, Target y Audience Manager en SPA.
seo-description: Adobe Experience Platform Launch is the recommended way to implement Analytics, Target, and Audience Manager within SPAs.
uuid: 8535a911-2863-4e3b-a3fb-414a0e7e9a4e
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: spa
discoiquuid: a458cc95-cd94-4f3f-9e7b-d6a5780ec4d5
exl-id: 1af29921-7c24-49b5-9f4c-60671641d4e4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---

# Integración de SPA y Launch{#spa-and-launch-integration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Platform Launch es la forma recomendada de implementar Analytics, Target y Audience Manager en aplicaciones de una sola página (SPA).

>[!NOTE]
>
>La función Editor de aplicaciones de una sola página (SPA) requiere AEM 6.4 service pack 2 o posterior.
>
>El Editor de SPA es la solución recomendada para proyectos que requieren SPA procesamiento del lado del cliente basado en el marco de trabajo (por ejemplo, React o Angular).

## Tutorial {#tutorial}

Para comprender cómo integrar su SPA con Adobe Experience Platform Launch, consulte [este artículo y tutorial de la base de conocimientos](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html), que le guiará a través de la configuración de Launch, así como a través de la implementación del Experience Cloud integrado con Angular o React.

>[!NOTE]
>
>La base de conocimiento a la que se hace referencia se creó para habilitar la integración de Adobe Experience Platform Launch con SPA que no aprovechan el AEM SPA Editor. Estos métodos también deberían permitir que la integración de Adobe Experience Platform Launch coexista con SPA que se hayan creado para utilizar el SPA Editor.
>
>No se ha explorado completamente el uso de Redux junto con las bibliotecas de SPA de Javascript. Está previsto que se admita Redux en una versión futura del SPA Editor.
