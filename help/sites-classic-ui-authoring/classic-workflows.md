---
title: Uso de flujos de trabajo
seo-title: Working with Workflows
description: AEM Flujos de trabajo permite automatizar una serie de pasos que se realizan en una página o un recurso. Por ejemplo, al publicar, un editor debe revisar el contenido antes de que un administrador del sitio active la página. Un flujo de trabajo que automatiza este ejemplo notifica a cada participante cuándo es el momento de realizar el trabajo necesario.
seo-description: AEM Workflows allows you to automate a series of steps that are performed on a page or asset. For example, when publishing, an editor has to review the content - before a site administrator activates the page. A workflow that automates this example notifies each participant when it is time to perform their required work.
uuid: 3eb6e790-6589-414a-8e51-33c358f47a73
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: b11f0e4c-4dec-4b66-9f54-a0aa13ac77b9
exl-id: 843cf933-d8a1-407d-9468-1a6409110f81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 50%

---

# Uso de flujos de trabajo{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Flujos de trabajo permite automatizar una serie de pasos que se realizan en una página o un recurso. Por ejemplo, al publicar, un editor debe revisar el contenido antes de que un administrador del sitio active la página. Un flujo de trabajo que automatiza este ejemplo notifica a cada participante cuándo es el momento de realizar el trabajo necesario:

1. El autor aplica el flujo de trabajo a la página.
1. El editor recibe un elemento de trabajo que indica que es necesario para revisar el contenido de la página. Una vez finalizado, indican que el elemento de trabajo ha finalizado.
1. El administrador del sitio recibe un elemento de trabajo que solicita la activación de la página. Una vez finalizado, indican que el elemento de trabajo ha finalizado.

Normalmente:

* Los autores de contenido aplican flujos de trabajo a las páginas, así como participan en flujos de trabajo.
* Los flujos de trabajo que utiliza son específicos de los procesos empresariales de su organización.

Las páginas siguientes tratan:

* [Aplicación de flujos de trabajo a páginas](/help/sites-classic-ui-authoring/classic-workflows-applying.md)
* [Participación en flujos de trabajo](/help/sites-classic-ui-authoring/classic-workflows-participating.md)
