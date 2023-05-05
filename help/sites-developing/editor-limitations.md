---
title: Limitaciones del editor
seo-title: Editor Limitations
description: El editor de la IU táctil utiliza superposiciones para interactuar con contenido limitado en un iframe. Esta interacción crea algunas limitaciones en el uso del editor y también para los desarrolladores.
seo-description: The editor in the touch-enabled UI makes use of overlays to interact with content confined in an iframe. This interaction creates some limitations in both usage of the editor and also for developers.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
exl-id: ce860880-5954-4f72-8ec6-60209c1ec659
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 11%

---

# Limitaciones del editor{#editor-limitations}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El editor de la IU táctil utiliza superposiciones para interactuar con contenido limitado en un iframe. Esta interacción crea algunas limitaciones en el uso del editor y también para los desarrolladores. Esta página resume estas limitaciones y proporciona soluciones o soluciones alternativas siempre que es posible.

## Limitaciones funcionales {#functional-limitations}

Un autor puede encontrar las siguientes limitaciones funcionales al utilizar el editor para crear páginas.

### Vínculos no activos {#links-not-active}

When [edición de una página](/help/sites-authoring/editing-content.md), los vínculos no están activos.

* [Cambie a **Vista previa** mode](/help/sites-authoring/editing-content.md#preview-mode) para navegar mediante los vínculos del contenido.

### Páginas de estructura {#structure-pages}

Las páginas no pueden tener nombres `structure`. Páginas con nombre `structure` no se puede editar en el editor de páginas.

## Limitaciones de CSS {#css-limitations}

Un desarrollador puede encontrar las siguientes limitaciones con las interacciones del editor con CSS.

### Elementos con posición absoluta {#absolutely-positioned-elements}

Los elementos con posición absoluta pueden causar problemas en la posición de su superposición.

* Si esto sucede, asegúrese de que las dimensiones del elemento con posición absoluta sean correctas, ya que el editor creará una superposición con las mismas dimensiones.

### unidades vh {#vh-units}

`vh` no se admiten unidades porque la altura del iframe debe ajustarse automáticamente por AEM.

### Imágenes de fondo fijas {#fixed-background-images}

Es posible que las imágenes de fondo fijas no se muestren como fijas al desplazarse debido al hecho de que están incrustadas dentro de un iframe.

* Selección **Ver página tal y como aparece publicado** en la barra de encabezado, las acciones muestran la página correctamente.

### Altura del 100 % {#height}

La altura del 100 % no se admite en el elemento de cuerpo de una página.

* Es posible una solución alternativa para implementar un cuerpo de pantalla completa al &quot;estirar&quot; el elemento de cuerpo de la siguiente manera:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Contraer margen {#margin-collapsing}

Se pueden ver problemas de colapso del margen si el primer elemento secundario del elemento de cuerpo tiene un margen.

* La solución es agregar una corrección en el nivel del elemento de cuerpo como la siguiente:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
