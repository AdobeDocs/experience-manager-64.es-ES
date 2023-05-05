---
title: Anotaciones al editar una página
seo-title: Annotations when Editing a Page
description: Muchos componentes directamente relacionados con contenido le permiten añadir una anotación
seo-description: Many components directly related to content allow you to add an annotation
uuid: 157be55c-8ab8-472e-be32-0dcc02bfa41d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: aa89326a-ad33-4b0b-8d09-c68c5a5c790a
exl-id: 65e534ec-7f73-4333-b225-7adf082f66d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 41%

---

# Anotaciones al editar una página{#annotations-when-editing-a-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La adición de contenido a las páginas de su sitio web suele someterse a análisis antes de publicarse. Para ayudarle, muchos componentes directamente relacionados con el contenido (en lugar de, por ejemplo, el diseño) permiten añadir una anotación.

Una anotación coloca un marcador o nota adhesiva de color en la página. La anotación le permite (a usted o a otros usuarios) dejar comentarios o preguntas para otros autores o revisores.

>[!NOTE]
>
>La definición de un tipo de componente individual determina si se puede añadir una anotación o no en instancias de dicho componente.

>[!NOTE]
>
>Las anotaciones creadas en la IU clásica se mostrarán en la IU táctil. Sin embargo, los bocetos son específicos de la IU y solo se muestran en la IU en la que se crearon.

>[!CAUTION]
>
>Al eliminar un recurso (p. ej. un párrafo), se eliminan todas las anotaciones y bocetos relacionados con ese recurso, independientemente de su posición en la página en general.

>[!NOTE]
>
>En función de sus necesidades, también puede desarrollar un flujo de trabajo para enviar notificaciones cuando estas se añadan, actualicen o eliminen.

## Anotaciones {#annotations}

Se utiliza un modo [especial](/help/sites-authoring/author-environment-tools.md#page-modes) para crear y ver anotaciones.

>[!NOTE]
>
>No olvide que también dispone de los [comentarios](/help/sites-authoring/basic-handling.md#timeline) para ofrecer opiniones sobre una página.

>[!NOTE]
>
>Puede realizar anotaciones en varios recursos:
>
>* [Anotación de recursos](/help/assets/managing-assets-touch-ui.md#annotating)
>* [Anotación de recursos de vídeo](/help/assets/managing-video-assets.md#annotating-video-assets)
>


### Anotación de un componente {#annotating-a-component}

El modo Anotar permite crear, editar, mover o eliminar anotaciones en el contenido:

1. Puede acceder al modo Anotar mediante el icono de la barra de herramientas (parte superior derecha) al editar una página:

   ![](do-not-localize/screen_shot_2018-03-22at110414.png)

   Ahora puede ver todas las anotaciones existentes.

   >[!NOTE]
   >
   >Para salir del modo Anotación , pulse o haga clic en el icono Anotar (símbolo x) situado a la derecha de la barra de herramientas superior.

1. Haga clic o toque el icono Añadir anotación (símbolo &quot;+&quot; a la izquierda de la barra de herramientas) para empezar a añadir anotaciones.

   >[!NOTE]
   >
   >Para dejar de añadir anotaciones (y volver a la visualización), toque o haga clic en el icono Cancelar (símbolo x en un círculo blanco) situado a la izquierda de la barra de herramientas superior.

1. Toque o haga clic en el componente requerido (los componentes que se pueden anotar se resaltarán con un borde azul) para añadir la anotación y abrir el cuadro de diálogo:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Aquí puede utilizar el campo o icono apropiado para:

   * Introduzca el texto de la anotación.
   * Crear un boceto (líneas y formas) para resaltar un área del componente.

      El cursor cambiará a una cruz cuando esté creando un boceto. Puede dibujar varias líneas distintas. Las líneas del boceto reflejan el color de la anotación y pueden ser una flecha, un círculo u ovaladas.
   ![](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Elegir o cambiar el color:

   ![](do-not-localize/chlimage_1-19.png)

   * Eliminar la anotación.

   ![](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Para cerrar el cuadro de diálogo de anotaciones, toque o haga clic fuera del mismo. Se muestra una vista truncada (la primera palabra) de la anotación, junto con los bocetos, si los hay:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Cuando haya terminado de editar una anotación concreta, puede hacer lo siguiente:

   * Hacer clic en el marcador de texto, o tocarlo, para abrir la anotación. Una vez abierto, puede ver el texto completo, realizar cambios o eliminar la anotación.

      * Los bocetos no se pueden eliminar independientemente de la anotación.
   * Cambiar la posición del marcador de texto.
   * Tocar o hacer clic en una línea de un boceto para seleccionar el boceto y arrastrarlo a la posición deseada.
   * Mover o copiar un componente

      * Las anotaciones relacionadas y sus bocetos también se moverán o copiarán, y su posición en relación con el párrafo seguirá siendo la misma.


1. Para salir del modo Anotación y volver al modo utilizado anteriormente, toque o haga clic en el icono Anotar (símbolo x) en la parte derecha de la barra de herramientas superior.

>[!NOTE]
>Las anotaciones no se pueden agregar a una página que otro usuario haya bloqueado.

### Indicador de anotaciones {#annotation-indicator}

Las anotaciones no aparecen en el modo de edición, pero el distintivo de la esquina superior derecha de la barra de herramientas mostrará el número de anotaciones de la página actual. Este distintivo sustituye al icono Anotaciones predeterminado, y además funciona como vínculo rápido que le permite acceder al modo de anotación y salir de él:

![chlimage_1-242](assets/chlimage_1-242.png)
