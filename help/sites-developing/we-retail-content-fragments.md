---
title: Probar fragmentos de contenido en We.Retail
seo-title: Trying out Content Fragments in We.Retail
description: Probar fragmentos de contenido en We.Retail
seo-description: null
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
exl-id: d93bec03-c651-4329-b220-4ac1ea189de1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 18%

---

# Probar fragmentos de contenido en We.Retail{#trying-out-content-fragments-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los fragmentos de contenido permiten crear contenido neutro con respecto al canal, así como variaciones (posiblemente específicas del canal). **We.Retail** (como está disponible en una instancia predeterminada de AEM) proporciona el fragmento **Surfing Ártico en Lofoten** como muestra básica. Esto ilustra que:

* Los fragmentos de contenido de Adobe Experience Manager (AEM) se [crean y administran como recursos independientes de la página](/help/assets/content-fragments.md). Permiten crear contenido neutro con respecto al canal, así como variaciones (posiblemente específicas del canal).

   * Consulte [Dónde encontrar los activos de fragmentos de contenido en We.Retail](#where-to-find-content-fragments-in-we-retail)

* Entonces puede [utilice estos fragmentos y sus variaciones al crear](/help/sites-authoring/content-fragments.md) las páginas de contenido.

   * Consulte [Dónde se utilizan los fragmentos de contenido en We.Retail](#where-content-fragments-are-used-in-we-retail)

Para obtener toda la documentación sobre la creación, administración, uso y desarrollo de fragmentos de contenido:

* Consulte [Información adicional](#further-information)

>[!NOTE]
>
>Los **fragmentos de contenido** y los **[fragmentos de experiencias](/help/sites-authoring/experience-fragments.md)** son funciones distintas de AEM:
>
>* **Fragmentos de contenido** son contenido editorial, principalmente texto e imágenes relacionadas. Son contenido puro, sin diseño ni diseño.
>* Los **fragmentos de experiencias** son contenidos plenamente diseñados; un fragmento de una página web. 
>
>Los fragmentos de experiencias pueden incluir contenido en forma de fragmentos, pero no lo contrario.

## Dónde encontrar los fragmentos de contenido en We.Retail {#where-to-find-content-fragments-in-we-retail}

Hay varios fragmentos de contenido de muestra en We.Retail; navegar por **Recursos**, **Archivos**, **We.Retail**, **Inglés**, **Experiencias**.

Estas incluyen **Surfing Ártico en Lofoten**, un fragmento junto con recursos visuales relacionados:

* Navegar por **Recursos**, **Archivos**, **We.Retail**, **Inglés**, **Experiencias**, **Surfing ártico en Lofoten**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![cf-44](assets/cf-44.png)

Puede seleccionar y editar la variable **Surfing Ártico en Lofoten** fragmento:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Aquí puede [editar y administrar](/help/assets/content-fragments.md) el fragmento mediante las pestañas (panel izquierdo):

![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png)

* **[Variaciones](/help/assets/content-fragments-variations.md)** incluido [Markdown](/help/assets/content-fragments-markdown.md)

* **[Contenido asociado](/help/assets/content-fragments-assoc-content.md)**
* **[Metadatos](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Dónde se utilizan los fragmentos de contenido en We.Retail {#where-content-fragments-are-used-in-we-retail}

Para ilustrar [creación de páginas con un fragmento de contenido](/help/sites-authoring/content-fragments.md) hay varios ejemplos de páginas que se proporcionan en, por ejemplo:

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Por ejemplo, la variable **Surfing Ártico en Lofoten** se hace referencia al fragmento de contenido en la página Sitios :

* Navegar por **Sitios**, **We.Retail**, **Maestros de idiomas**, **Inglés**, **Experiencia**. A continuación, abra **Surfing Ártico en Lofoten** para edición:

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
