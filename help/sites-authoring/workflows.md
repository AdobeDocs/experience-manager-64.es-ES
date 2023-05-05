---
title: Uso de flujos de trabajo
seo-title: Working with Workflows
description: Los flujos de trabajo de AEM permiten automatizar una serie de pasos que se realizan en una página o un recurso.
seo-description: Workflows in AEM allow you to automate a series of steps that are performed on a page or asset.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 41%

---

# Uso de flujos de trabajo{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Flujos de trabajo permite automatizar una serie de pasos que se realizan en (una o más) páginas o recursos.

Por ejemplo, al publicar, un editor debe revisar el contenido antes de que un administrador del sitio active la página. Un flujo de trabajo que automatiza este ejemplo notifica a cada participante cuándo es el momento de realizar el trabajo necesario:

1. El autor aplica el flujo de trabajo a la página.
1. El editor recibe un elemento de trabajo que indica que es necesario para revisar el contenido de la página. Una vez finalizado, indican que el elemento de trabajo ha finalizado.
1. El administrador del sitio recibe un elemento de trabajo que solicita la activación de la página. Una vez finalizado, indican que el elemento de trabajo ha finalizado.

Normalmente:

* Los autores de contenido aplican flujos de trabajo a las páginas, así como participan en flujos de trabajo.
* Los flujos de trabajo que utiliza son específicos de los procesos empresariales de su organización.

Las páginas siguientes tratan:

* [Aplicación de flujos de trabajo a páginas](/help/sites-authoring/workflows-applying.md)
* [Participación en flujos de trabajo](/help/sites-authoring/workflows-participating.md)
