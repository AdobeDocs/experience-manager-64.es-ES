---
title: Uso de la nube de etiquetas social
seo-title: Using Social Tag Cloud
description: Adición de un componente de Social Tag Cloud a una página
seo-description: Adding a Social Tag Cloud component to a page
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
exl-id: 3f55a02c-2733-4f69-8112-7c6c4c98938c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 2%

---

# Uso de la nube de etiquetas social {#using-social-tag-cloud}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

La variable `Social Tag Cloud` el componente resalta las etiquetas aplicadas por los miembros de la comunidad al publicar contenido. Es una forma de identificar los temas de tendencia y permitir a los visitantes del sitio localizar rápidamente el contenido etiquetado.

Para obtener otro medio de identificar las tendencias actuales, visite [Tendencias de actividad](trends.md).

Esta página documenta el `Social Tag Cloud` configuración del cuadro de diálogo de componentes y describe la experiencia del usuario.

Para obtener información detallada para los desarrolladores, consulte [Aspectos básicos de las etiquetas](tag.md).

Consulte [Administración de etiquetas](../../help/sites-administering/tags.md) para obtener información sobre la creación y administración de etiquetas, así como sobre las etiquetas de contenido que se han aplicado.

## Adición de una nube de etiquetas de Social {#adding-a-social-tag-cloud}

Para agregar un `Social Tag Cloud` a una página en modo de autor, utilice el navegador de componentes para localizar `Communities / Social Tag Cloud` y arrástrela a su lugar en una página en la que debería aparecer la nube de etiquetas.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](tag.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Social Tag Cloud` aparecerá el componente:

![chlimage_1-303](assets/chlimage_1-303.png)

## Configuración de Social Tag Cloud {#configuring-social-tag-cloud}

Seleccione la colocación `Social Tag Cloud` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-304](assets/chlimage_1-304.png)

En el **[!UICONTROL Nube de etiquetas sociales]** , especifique qué etiquetas mostrar y, si las etiquetas son vínculos activos, la ubicación de la página para los resultados de la búsqueda.

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL Etiquetas sociales para mostrar]**
Identifique qué etiquetas UGC mostrar. Las opciones desplegables son

   * `From page and child pages`
   * `All tags`

   El valor predeterminado es `From page and child pages`, donde &quot;página&quot; hace referencia a la variable **Página** a continuación.

* **[!UICONTROL Página]**
(obligatorio si no 
`All tags)` Ruta al UGC de una página. El valor predeterminado es la página actual si se deja en blanco.

* **[!UICONTROL No hay vínculos en las etiquetas]**
Si se selecciona, las etiquetas se muestran en la nube de etiquetas como texto sin formato. Si está desactivada, las etiquetas se muestran como vínculos activos que buscan todo el contenido al que se aplica esa etiqueta. El valor predeterminado no está marcado y requiere la variable **[!UICONTROL Ruta de resultados de búsqueda]** para configurar.

* **[!UICONTROL Ruta de resultados de búsqueda]**
La ruta a una página en la que una 
`Search Result` se ha colocado el componente, configurado para hacer referencia a UGC, que incluye la ruta UGC especificada por el **Página** configuración.

## Cambiar la visualización de la nube de etiquetas sociales {#change-display-of-social-tag-cloud}

Para editar la visualización de la variable **Nube de etiquetas sociales**, introduzca [Modo de diseño](../../help/sites-authoring/default-components-designmode.md) y haga doble clic en la `Social Tag Cloud` para abrir un cuadro de diálogo con una pestaña adicional.

Al usar la variable **[!UICONTROL Social Tag Cloud (diseño)]** especifique cómo se muestran las etiquetas. Una etiqueta puede ser una etiqueta simple, una palabra simple en el espacio de nombres predeterminado o una taxonomía jerárquica:

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL Mostrar rutas de título completas]**
Si se selecciona, muestra los títulos de las etiquetas principales y el espacio de nombres para cada etiqueta aplicada.

   Por ejemplo:

   * Comprobado: `Geometrixx Media: Gadgets / Cars`
   * Desactivado: `Cars`

   No hay diferencia para una etiqueta simple.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Mostrar solo las etiquetas de hoja]**
Si se selecciona, solo muestra las etiquetas aplicadas que no contienen otras etiquetas.

   Por ejemplo, dado el TagID de

   `Geometrixx Media: Gadgets / Cars`

   Se pueden aplicar tres etiquetas: `Geometrixx Media (the namespace)`, `Gadgets`y `Cars`

   * Comprobado: only `Cars` se muestra, si se aplica
   * Desmarcado: `Geometrixx Media` y `Gadgets`así como `Cars` se muestra, si se aplica

   Una etiqueta simple es una etiqueta de hoja.

   El valor predeterminado no está seleccionado.

* **[!UICONTROL Plantilla de vínculo]**
Una plantilla, que no sea la predeterminada, se utiliza para mostrar los vínculos en una nube de etiquetas, cuando los vínculos se habilitan mediante el cuadro de diálogo de edición de componentes.

* **[!UICONTROL El mismo tamaño para todas las etiquetas]**
Si se selecciona, todas las palabras de la nube de etiquetas tienen el mismo estilo. Si no está marcada, las palabras tienen un estilo diferente según su uso. El valor predeterminado no está seleccionado.

## Información adicional {#additional-information}

Puede encontrar más información en la [Aspectos básicos de las etiquetas](tag.md) para desarrolladores.

Consulte [Etiquetado del contenido generado por el usuario](tag-ugc.md) (UGC) para obtener información sobre la creación y administración de etiquetas.
