---
title: Función de tabla de clasificación
seo-title: Función de tabla de clasificación
description: Añadir un componente de tabla de clasificación en una página
seo-description: Añadir un componente de tabla de clasificación en una página
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 6%

---


# Función de tabla de clasificación {#leaderboard-feature}

## Introducción {#introduction}

El `Leaderboard` componente proporciona la capacidad de obtener una idea de cómo interactúan los miembros dentro de la comunidad mediante la clasificación de los miembros según los puntos ganados (puntuación básica) o su experiencia (puntuación avanzada).

Antes de incluir el componente de la tabla de clasificación en una página, es necesario configurar la Puntuación de [comunidades y los distintivos](implementing-scoring.md).

Esta sección de la documentación describe

* Añadir el `Leaderboard` componente en un sitio [de comunidad](overview.md#community-sites)

* Configuración del `Leaderboard` componente

## Adding a Leaderboard to a Page {#adding-a-leaderboard-to-a-page}

Para agregar un `Leaderboard` componente a una página en modo de autor, ubique el componente

* `Communities / Leaderboard`

y arrástrelo a su lugar en una página.

Para obtener la información necesaria, visite [Communities Components Basics](basics.md)(Conceptos básicos de componentes de comunidades).

Cuando se coloca por primera vez en una página de un sitio de comunidad, así es como aparece el componente:

![chlimage_1-8](assets/chlimage_1-8.png)

## Configuración de la tabla de clasificación {#configuring-leaderboard}

Seleccione el componente colocado al que desea acceder y seleccione el `Leaderboard` `Configure` icono que abre el cuadro de diálogo de edición.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Ficha Configuración {#settings-tab}

En la ficha **[!UICONTROL Configuración]** , especifique la información relacionada con el miembro que se muestra:

* **[!UICONTROL Nombre para mostrar]** Un nombre descriptivo que se mostrará para el tablero, que refleja las reglas seleccionadas para mostrar distintivos y puntuaciones.

   El valor predeterminado es `Leaderboard`si no se ha introducido nada.

* **[!UICONTROL Distintivo]** Si está marcado, se incluye una columna para los iconos de distintivo en la tabla de clasificación.

   El valor predeterminado no está marcado.

* **[!UICONTROL Nombre]** del distintivo Si se selecciona, se incluye una columna para el nombre del distintivo en la tabla de clasificación.

   El valor predeterminado no está marcado.

* **[!UICONTROL Use Avatar]** Si está marcado, la imagen de avatar del miembro se incluye en el panel de control, junto al vínculo de nombre del perfil del miembro.

   El valor predeterminado no está marcado.

### Ficha Reglas {#rules-tab}

Bajo la ficha **[!UICONTROL Reglas]** , el sitio de la comunidad y sus reglas de puntuación y de distintivo

* **[!UICONTROL Ubicación]** de la regla (obligatoria) Ubicación en la que está configurada la regla de puntuación/distintivo.

* **[!UICONTROL Regla]** de puntuación (obligatoria) Regla específica que genera las puntuaciones que se van a mostrar.

* **[!UICONTROL Regla]** de asignación de distintivos (obligatoria) Regla específica que genera el distintivo que se va a mostrar.

* **[!UICONTROL Límite]** de visualización Número de miembros que se mostrarán por página.

   El valor predeterminado es 10.

## Ejemplo: Mesa de liderazgo de los participantes {#example-participants-leaderboard}

Este marcador de posición indica los resultados de la aplicación de reglas de puntuación básicas.

Configuración del componente de la tabla de clasificación:

* **[!UICONTROL Ficha Configuración]** :

   * Nombre para mostrar = `Participation Board`
   * `checked`:

      * Distintivo
      * Nombre de distintivo
      * Usar avatar

* **[!UICONTROL Ficha Reglas]** :

   * Ubicación de la regla = `/content/sites/communities/jcr:content`
   * Regla de puntuación = `/etc/community/scoring/rules/forums-scoring`
   * Regla de creación de distintivos = `/etc/community/badging/rules/reference-badging`
   * Límite de visualización = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Ejemplo: Panel de liderazgo de expertos {#example-experts-leaderboard}

Este marcador de posición indica los resultados de la aplicación de reglas de puntuación avanzadas.

Configuración del componente de la tabla de clasificación:

* **[!UICONTROL Ficha Configuración]** :

   * Nombre para mostrar = `Expertise Board`
   * `checked`:

      * Distintivo
      * Usar avatar

* **[!UICONTROL Ficha Reglas]** :

   * Ubicación de la regla = `/content/sites/communities/jcr:content`
   * Regla de puntuación = `/etc/community/scoring/rules/adv-forums-scoring`
   * Regla de creación de distintivos = `/etc/community/badging/rules/adv-forums-badging`
   * Límite de visualización = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Información adicional {#additional-information}

Puede encontrar más información en la página [Leaderboard Essentials](leaderboard.md) para desarrolladores.

Las instrucciones para crear reglas se proporcionan en la página Puntuación de [comunidades y distintivos](implementing-scoring.md) para administradores.
