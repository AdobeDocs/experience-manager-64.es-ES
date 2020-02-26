---
title: Secuencias integradas
seo-title: Secuencias integradas
description: Siga esta página para obtener más información sobre las secuencias integradas de canales que permiten al usuario añadir componentes en el canal principal y reutilizar el contenido de otro canal e integrarlo en el canal principal.
seo-description: Siga esta página para obtener más información sobre las secuencias integradas de canales que permiten al usuario añadir componentes en el canal principal y reutilizar el contenido de otro canal e integrarlo en el canal principal.
uuid: 3ffbe937-6b60-4eea-acfb-633270b4ded3
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 76be4cc1-4b34-4f1d-b2d3-754a84105dec
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Secuencias integradas{#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## Añadir secuencias integradas {#adding-embedded-sequences}

Tiene la opción de añadir los componentes siguientes al canal de secuencia:

* Secuencia integrada
* Secuencia integrada dinámica

>[!NOTE]
>
>Para obtener más información sobre el uso de otros componentes en el proyecto de Screens, consulte [Añadir componentes a un canal](/help/screens/adding-components-to-a-channel.md).

### Añadir una secuencia integrada {#adding-an-embedded-sequence}

Puede añadir una secuencia integrada al canal. Una secuencia integrada en otro canal que incluye recursos como imágenes o vídeos. Al añadir una secuencia integrada, el usuario puede añadir la secuencia a un canal según la ***ruta de acceso del canal***.

>[!NOTE]
>
>***Ruta de canal ***define una referencia explícita al canal.
>
>Para obtener más información sobre la *Ruta de acceso del canal*, consulte [Asignación de canales](/help/screens/channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una página. For example, **We.Retail In-Store** --> **Channels** -->** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la página integrada. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Seleccione la **ruta de acceso al canal** del canal.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. Si el usuario especifica una duración, se interrumpe la secuencia secundaria (es decir, se limita) en el tiempo especificado.

1. Establezca la estrategia **de reproducción** con contador en **normal**.

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

En el siguiente ejemplo se muestra la forma de añadir una secuencia integrada (**Canal inactivo - noche**) a un canal ya existente (**Canal inactivo**).

![new2](assets/new2.gif)

### Añadir una secuencia integrada dinámica {#adding-a-dynamic-embedded-sequence}

Puede añadir una secuencia integrada dinámica al canal. Una secuencia integrada de forma dinámica es similar a una secuencia integrada, pero permite que el usuario siga una jerarquía en la cual los cambios o actualizaciones que se hicieron en el canal se propagan a otro canal relacionado. Rastrea la jerarquía principal-secundaria e incluye recursos como imágenes o vídeos. Al añadir secuencia dinámica, el usuario puede añadir un canal según el rol de canal.

>[!NOTE]
>
>***Rol del canal*** define el rol del canal que define a su vez el contexto de la visualización.
>
>Para obtener más información acerca de los *Roles de canales*, consulte [Asignación de canales](/help/screens/channel-assignment.md) en Creación de Screens.

Siga los pasos a continuación para añadir una secuencia integrada al canal:

1. Seleccione el canal en el que desee insertar una secuencia dinámica. For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Haga clic en el icono de componentes de la barra izquierda para añadir la secuencia integrada dinámica. Drag and drop the **Dynamic Embedded Sequence** to the editor.

1. Double-click the **Dynamic Embedded Sequence** component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. Establezca la estrategia **de reproducción** con contador en **normal**. By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** *(Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![más reciente](assets/latest.gif)

