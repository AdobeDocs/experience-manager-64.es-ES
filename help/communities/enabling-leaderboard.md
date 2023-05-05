---
title: Función de portapapeles
seo-title: Leaderboard Feature
description: Adición de un componente de panel de encabezado a una página
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 8%

---

# Función de portapapeles {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La variable `Leaderboard` proporciona la capacidad de obtener una idea de cómo interactúan los miembros dentro de la comunidad mediante la clasificación de los miembros según los puntos ganados (puntuación básica) o su experiencia (puntuación avanzada).

Antes de incluir el componente de panel de encabezado en una página, es necesario configurar [Puntuación y distintivos de comunidades](implementing-scoring.md).

Esta sección de la documentación describe

* Adición de la variable `Leaderboard` componente a un [sitio de la comunidad](overview.md#community-sites)

* Ajustes de configuración para `Leaderboard` componente

## Adición de un tablero de vanguardia a una página {#adding-a-leaderboard-to-a-page}

Para agregar un `Leaderboard` a una página en modo de autor, busque el componente

* `Communities / Leaderboard`

y arrástrela a su lugar en una página.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando se coloca por primera vez en una página de un sitio de comunidad, así es como aparece el componente:

![Chlimage_1-8](assets/chlimage_1-8.png)

## Configuración del panel de clientes {#configuring-leaderboard}

Seleccione la colocación `Leaderboard` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![Chlimage_1-9](assets/chlimage_1-9.png) ![imagen_1-10](assets/chlimage_1-10.png)

### Ficha Configuración {#settings-tab}

En el **[!UICONTROL Configuración]** especifique qué información relacionada con el miembro se muestra:

* **[!UICONTROL Nombre para mostrar]**
Un nombre descriptivo para mostrar para el tablero, que refleja las reglas seleccionadas para mostrar distintivos y puntuaciones.

   El valor predeterminado es `Leaderboard`, si no se ha introducido nada.

* **[!UICONTROL Distintivo]**
Si se selecciona, se incluye una columna para los iconos de distintivo en el panel de mandos.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Nombre del distintivo]**
Si se selecciona, se incluye una columna para el nombre del distintivo en el panel de control.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Usar Avatar]**
Si se selecciona, la imagen de avatar del miembro se incluye en el panel de control, junto al vínculo de nombre a su perfil de miembro.

   El valor predeterminado no está seleccionado.

### Ficha Reglas {#rules-tab}

En el **[!UICONTROL Reglas]** , el sitio de la comunidad y sus reglas de puntuación y de distintivo

* **[!UICONTROL Ubicación de regla]**
(obligatorio) Ubicación en la que está configurada la regla Puntuación/Distintivo.

* **[!UICONTROL Regla de puntuación]**
(obligatorio) Regla específica que genera las puntuaciones que se van a mostrar.

* **[!UICONTROL Regla de asignación]**
(obligatorio) Regla específica que genera el distintivo que se va a mostrar.

* **[!UICONTROL Límite de visualización]**
Número de miembros que se mostrarán por página.

   El valor predeterminado es 10.

## Ejemplo: Placa de encabezado de los participantes {#example-participants-leaderboard}

Este panel de liderazgo informa de los resultados de la aplicación de reglas de puntuación básicas.

Configuración de componentes del panel de vanguardia:

* **[!UICONTROL Configuración]** pestaña:

   * Nombre para mostrar = `Participation Board`
   * `checked`:

      * Distintivo
      * Nombre de distintivo
      * Usar Avatar

* **[!UICONTROL Reglas]** pestaña:

   * Ubicación de la regla = `/content/sites/communities/jcr:content`
   * Regla de puntuación = `/etc/community/scoring/rules/forums-scoring`
   * Regla de creación de distintivos = `/etc/community/badging/rules/reference-badging`
   * Límite de visualización = `10`

![imagen_1-11](assets/chlimage_1-11.png)

## Ejemplo: Panel de expertos {#example-experts-leaderboard}

Este panel de control resulta de la aplicación de reglas de puntuación avanzadas.

Configuración de componentes del panel de vanguardia:

* **[!UICONTROL Configuración]** pestaña:

   * Nombre para mostrar = `Expertise Board`
   * `checked`:

      * Distintivo
      * Usar Avatar

* **[!UICONTROL Reglas]** pestaña:

   * Ubicación de la regla = `/content/sites/communities/jcr:content`
   * Regla de puntuación = `/etc/community/scoring/rules/adv-forums-scoring`
   * Regla de creación de distintivos = `/etc/community/badging/rules/adv-forums-badging`
   * Límite de visualización = `10`

![imagen_1-12](assets/chlimage_1-12.png)

## Información adicional {#additional-information}

Puede encontrar más información en la [Elementos esenciales del panel de control](leaderboard.md) para desarrolladores.

Las instrucciones para crear reglas se proporcionan en la [Puntuación y distintivos de comunidades](implementing-scoring.md) para administradores.
