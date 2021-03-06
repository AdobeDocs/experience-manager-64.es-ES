---
title: Probar fragmentos de contenido en We.Retail
seo-title: Probar fragmentos de contenido en We.Retail
description: Probar fragmentos de contenido en We.Retail
seo-description: nulo
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 21%

---


# Probar fragmentos de contenido en We.Retail{#trying-out-content-fragments-in-we-retail}

Los fragmentos de contenido le permiten crear contenido neutro con respecto al canal, además de variaciones (posiblemente específicas del canal). **We.Retail**  (como disponible en una instancia predeterminada de AEM) proporciona el fragmento  **Arctic Surfing in** Lofotenas como una muestra básica. Esto ilustra que:

* Los fragmentos de contenido de Adobe Experience Manager (AEM) se [crean y administran como recursos independientes de la página](/help/assets/content-fragments.md). Permiten crear contenido neutro con respecto al canal, así como variaciones (posiblemente específicas del canal). 

   * Consulte [Dónde encontrar los activos de fragmento de contenido en We.Retail](#where-to-find-content-fragments-in-we-retail)

* A continuación, puede [utilizar estos fragmentos, y sus variaciones, al crear](/help/sites-authoring/content-fragments.md) las páginas de contenido.

   * Consulte [Dónde se utilizan los fragmentos de contenido en We.Retail](#where-content-fragments-are-used-in-we-retail)

Para obtener toda la documentación sobre la creación, administración, uso y desarrollo de fragmentos de contenido:

* Consulte [Más información](#further-information)

>[!NOTE]
>
>Los **fragmentos de contenido** y los **[fragmentos de experiencias](/help/sites-authoring/experience-fragments.md)** son funciones distintas de AEM:
>
>* Los **fragmentos de contenido** son contenido editorial, principalmente texto e imágenes relacionadas. Se trata de contenido puro, sin diseño ni maquetación.
>* Los **fragmentos de experiencia** son contenido plenamente diseñado; un fragmento de una página web. 

>
>
Los fragmentos de experiencias pueden incluir contenido en forma de fragmentos de contenido, pero no lo contrario.

## Dónde encontrar los fragmentos de contenido en We.Retail {#where-to-find-content-fragments-in-we-retail}

Hay varios fragmentos de contenido de muestra en We.Retail; vaya a través de **Assets**, **Files**, **We.Retail**, **English**, **Experiencias**.

Estos incluyen **Arctic Surfing in Lofoten**, un fragmento junto con activos visuales relacionados:

* Navegue por **Assets**, **Files**, **We.Retail**, **English**, **Experiencias**, **Surfing ártico en Lofoten**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![cf-44](assets/cf-44.png)

Puede seleccionar y editar el fragmento **Arctic Surfing in Lofoten**:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Aquí puede [editar y administrar](/help/assets/content-fragments.md) el fragmento mediante las pestañas (panel izquierdo):

![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png)

* **[](/help/assets/content-fragments-variations.md)** Variaciones, incluido  [Markdown](/help/assets/content-fragments-markdown.md)

* **[Contenido asociado](/help/assets/content-fragments-assoc-content.md)**
* **[Metadatos](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Dónde se utilizan los fragmentos de contenido en We.Retail {#where-content-fragments-are-used-in-we-retail}

Para ilustrar la [creación de páginas con un fragmento de contenido](/help/sites-authoring/content-fragments.md), se proporcionan varios ejemplos de páginas en, por ejemplo:

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Por ejemplo, se hace referencia al fragmento de contenido **Arctic Surfing in Lofoten** en la página Sitios :

* Navegue por **Sites**, **We.Retail**, **Language Masters**, **English**, **Experience**. A continuación, abra **Arctic Surfing in Lofoten** para editarlo:

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## Información adicional {#further-information}

Para obtener más información, consulte:

* [Trabajar con fragmentos de contenido](/help/assets/content-fragments.md)

   * Obtenga información sobre cómo crear, editar y administrar los recursos de fragmentos de contenido.

* [Creación de páginas con fragmentos de contenido](/help/sites-authoring/content-fragments.md)

   * Utilice el fragmento de contenido al crear una página.

* [Desarrollo de AEM: componentes para fragmentos de contenido](/help/sites-developing/components-content-fragments.md)

   * Información general sobre los componentes de los fragmentos de contenido.

* [Desarrollo y ampliación de fragmentos de contenido](/help/sites-developing/customizing-content-fragments.md)

   * Información para ayudarle a desarrollar y ampliar fragmentos de contenido.

