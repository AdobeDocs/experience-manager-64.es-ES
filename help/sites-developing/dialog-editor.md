---
title: Editor de cuadro de diálogo
seo-title: Dialog Editor
description: El editor de cuadro de diálogo proporciona una interfaz gráfica para crear y editar fácilmente cuadros de diálogo y scaffolds
seo-description: The dialog editor provides a graphical interface for easily creating and editing dialog boxes and scaffolds
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
exl-id: ee57a0c5-261e-4ffd-92ca-4804a9e1d132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# Editor de cuadro de diálogo{#dialog-editor}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El editor de cuadro de diálogo proporciona una interfaz gráfica para crear y editar fácilmente cuadros de diálogo y scaffolds.

Para ver cómo funciona, vaya a CRXDE Lite y abra el árbol del explorador a `/libs/foundation/components/chart` y haga doble clic en el nodo `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

El nodo de diálogo se abrirá en la variable **editor de cuadro de diálogo**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Información general sobre la interfaz de usuario {#user-interface-overview}

La interfaz del editor de cuadro de diálogo está compuesta por cuatro paneles:

* La variable **paleta**, en la esquina superior izquierda. Este panel contiene los widgets disponibles para crear un cuadro de diálogo, como paneles de fichas, campos de texto, listas de selección y botones. Puede expandir las diferentes categorías dentro de la paleta haciendo clic en la barra divisoria deseada.
* La variable **estructura** , en la esquina inferior izquierda. Este panel muestra la estructura jerárquica de los nodos que conforman la definición del cuadro de diálogo. Puede ver la misma estructura expandiendo el nodo de diálogo en CRXDE Lite o en el Explorador de contenido CRX.
* La variable **render** , en el centro de la ventana. Este panel muestra cómo se representará la definición de cuadro de diálogo definida en el panel de estructura como un cuadro de diálogo real.
* La variable **propiedades** panel. Este panel muestra las propiedades del nodo que está resaltado en el panel de estructura.

### Uso del Editor de cuadro de diálogo {#using-the-dialog-editor}

Para crear un cuadro de diálogo, el usuario arrastra y suelta los elementos de la paleta al panel de estructura en su posición dentro de la jerarquía de definición del cuadro de diálogo.

Una vez completada la estructura deseada, el usuario hace clic en **Guardar**, en la parte superior del panel de procesamiento.

>[!CAUTION]
>
>Tenga en cuenta que el editor de cuadro de diálogo está diseñado para la creación de cuadros de diálogo relativamente sencillos y es posible que no pueda editar definiciones de cuadro de diálogo más complejas. En los casos en los que el editor de cuadro de diálogo no permita la edición de una estructura de cuadro de diálogo, la definición de cuadro de diálogo debe crearse o editarse manualmente editando directamente la estructura del nodo utilizando, por ejemplo, CRXDE Lite o CRX Content Explorer.

### Creación de un nuevo cuadro de diálogo {#creating-a-new-dialog}

Para crear un nuevo cuadro de diálogo, debe seleccionar el componente requerido, haga clic en **Crear...** y luego **Crear cuadro de diálogo...**.

Introduzca los detalles necesarios y haga clic en **Guardar todo** - ahora puede hacer doble clic en el cuadro de diálogo para abrirlo con el editor.

### Uso del Editor de cuadro de diálogo para scaffolds {#using-the-dialog-editor-for-scaffolds}

Un scaffold es una página especial que contiene un formulario que se puede rellenar y enviar en un solo paso. Esto le permite crear rápidamente una página con el contenido introducido.

El formulario que constituye un scaffold se define mediante una definición de cuadro de diálogo, al igual que un cuadro de diálogo normal, aunque aparezca en la página de scaffolding de forma distinta. Dado que las definiciones de cuadro de diálogo se utilizan para definir scaffolds, los scaffolds se pueden diseñar utilizando el editor de cuadro de diálogo. Tenga en cuenta que cuando utilice el editor de cuadro de diálogo de este modo, el panel de procesamiento seguirá mostrando la definición del cuadro de diálogo en forma de cuadro de diálogo y no como un scaffold.

Consulte [Andamiaje](/help/sites-authoring/scaffolding.md) para obtener más información sobre el uso del editor de cuadro de diálogo para crear scaffolds.
