---
title: Markdown
seo-title: Markdown
description: Cuando se crea, el editor de fragmentos de contenido utiliza la sintaxis Markdown para permitirle escribir contenido fácilmente.
seo-description: When you are authoring, the content fragment editor uses markdown syntax to allow you to easily write content.
uuid: 12b185a5-3d87-4d7c-8d09-8cc2726009a8
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: bde54663-9050-4a5a-93cb-7cd84ac7f071
exl-id: 209f0e02-b883-4104-8358-01cab15e5db2
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 86%

---

# Markdown {#markdown}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

Cuando [creación](content-fragments-variations.md#authoring-your-content), el editor de fragmentos de contenido utiliza *markdown* sintaxis para permitir escribir contenido fácilmente:

![Editor de Markdown](/help/assets/assets/cfm-6420-08.png)

Puede definir lo siguiente:

* [Anotación de encabezado](/help/assets/content-fragments-markdown.md#heading-notation)
* [Párrafos y saltos de línea](/help/assets/content-fragments-markdown.md#paragraphs-and-line-breaks)
* [Vínculos](/help/assets/content-fragments-markdown.md#links)
* [Imágenes](/help/assets/content-fragments-markdown.md#images)
* [Comillas de bloque](/help/assets/content-fragments-markdown.md#block-quotes)
* [Listas](/help/assets/content-fragments-markdown.md#lists)
* [Énfasis](/help/assets/content-fragments-markdown.md#emphasis)
* [Bloques de código](/help/assets/content-fragments-markdown.md#code-blocks)
* [Escapes de barra invertida](/help/assets/content-fragments-markdown.md#backslash-escapes)

## Anotación de encabezado {#heading-notation}

Para crear un encabezado, coloque una almohadilla (#) delante del encabezado. Se utiliza una almohadilla (#) para un H1, dos (##) para un H2, etc. Se pueden usar hasta seis almohadillas. Por ejemplo:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

De forma opcional, puede crear un H1 subrayando el texto en signos iguales y un H2 subrayando el texto en signos menos. Por ejemplo:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Párrafos y saltos de línea {#paragraphs-and-line-breaks}

Un párrafo es simplemente una o más líneas consecutivas de texto, separadas por una o más líneas en blanco. Una línea en blanco es una que contiene únicamente espacios o tabulaciones. Los párrafos normales no deben tener sangría con espacios o tabulaciones.

Un salto de línea se crea terminando una línea con dos o más espacios y un retorno.

## Vínculos {#links}

Puede crear vínculos en línea y de referencia.

En ambos estilos, el texto del vínculo está delimitado por corchetes `[]`.

Estos son ejemplos de vínculos en línea:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Un vínculo de referencia tiene la siguiente sintaxis:

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Imágenes {#images}

La sintaxis de las imágenes es similar a los vínculos. Puede crear imágenes en línea y referenciadas.

Por ejemplo, una imagen en línea tiene la siguiente sintaxis:

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

La sintaxis incluye lo siguiente:

* Un signo de exclamación: !;
* seguido de un conjunto de corchetes, que contienen el texto del atributo alternativo de la imagen;
* seguido de un conjunto de paréntesis, que contiene la dirección URL o la ruta a la imagen, y de un atributo de título opcional entre comillas dobles o simples.

Una imagen de estilo de referencia tiene la siguiente sintaxis:

    `![Alt text][id]`

Donde “id” es el nombre de una referencia de imagen definida. Las referencias de imagen se definen con una sintaxis idéntica a las referencias de vínculo:

    `[id]: url/to/image "Optional title attribute"`

## Comillas de bloque {#block-quotes}

Puede citar texto añadiendo el símbolo > antes del texto. Por ejemplo:

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

Puede tener citas de bloque anidadas. Por ejemplo:

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Listas {#lists}

Puede crear listas ordenadas y desordenadas.

Para crear una lista desordenada, utilice el símbolo &amp;ast; antes de los elementos de la lista. Por ejemplo:

    `* item in list`

    `* item in list`

    `* item in list`

Para crear una lista ordenada, añada los números, seguidos de un punto, antes de cada elemento de la lista. Por ejemplo:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Énfasis {#emphasis}

Puede añadir estilos de cursiva o negrita a su texto.

Se agrega cursiva de la siguiente manera:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

Puede aplicar negrita al texto de la siguiente manera:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Para indicar un intervalo de código, encapsúlelo con acentos graves (&grave;). A diferencia de los bloques de código con formato previo, un intervalo de código indica el código dentro de un párrafo normal.

Por ejemplo:

    ``Use the `printf()` function.``

## Bloques de código {#code-blocks}

Los bloques de código suelen emplearse para ilustrar el código fuente. Puede crear bloques de código sangrándolos con una tabulación o con un mínimo de cuatro espacios. Por ejemplo:

    `This is a normal paragraph.`

        `This is a code block.`

## Escapes de barra invertida {#backslash-escapes}

Se pueden utilizar secuencias de escape de barra invertida para generar caracteres literales que tengan un significado especial en la sintaxis de formato. Por ejemplo, si desea rodear una palabra con asteriscos literales (en lugar de una &lt;em> etiqueta HTML), puede utilizar barras invertidas antes de los asteriscos, de esta manera:

    `\\*literal asterisks\\*`

Las secuencias de escape de barra invertida están disponibles para los siguientes caracteres:

    ` \ backslash`

    `` ` backtick``

    ` * asterisk`

    ` _ underscore`

    ` {} curly braces`

    ` [] square brackets`

    ` () parentheses`

    ` # hash mark`

    ` + plus sign`

    ` - minus sign (hyphen)`

    ` . dot`
