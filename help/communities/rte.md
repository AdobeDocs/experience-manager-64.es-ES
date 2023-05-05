---
title: Elementos básicos del editor de texto enriquecido
seo-title: Rich Text Editor Essentials
description: Descripción general de la función Editor de texto enriquecido
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 6%

---

# Elementos básicos del editor de texto enriquecido {#rich-text-editor-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Un editor de texto enriquecido (RTE) permite introducir texto con marcado.

Para los componentes de Communities, mientras que es similar a la variable [editor de texto enriquecido en el entorno de creación](../../help/sites-authoring/rich-text-editor.md), afecta al texto introducido en el entorno de publicación.

![chlimage_1-410](assets/chlimage_1-410.png)

## Habilitación del editor de texto enriquecido {#enabling-rich-text-editor}

Los componentes de Communities que permiten el contenido generado por el usuario (UGC) pueden habilitarse para permitir RTE. Dependiendo de si el componente se agregó a una página o se incluyó dentro de un [function](functions.md), RTE puede o no estar habilitado de forma predeterminada.

Si no está activada, simplemente introduzca [modo de edición de autor](sites-console.md#authoring-site-content), seleccione el componente para editar y el `Rich Text Editor` casilla de verificación.

RTE está disponible para los siguientes componentes de Communities:

* [Blog](blog-feature.md)
* [Calendario](calendar.md)
* [Comentarios](comments.md)
* [Filelibrary](file-library.md)
* [Foro](forum.md)
* [Mensajes](configure-messaging.md)
* [P y R](working-with-qna.md)
* [Repasos](reviews.md)

## Personalización {#customization}

La personalización del editor de texto enriquecido es posible, ya que la implementación se basa en [CKEditor](https://www.ckeditor.com/).

La configuración actual de los componentes de Communities se encuentra en la `cq.social.  scf   clientlib`, ubicado en el repositorio en

`/libs/clientlibs/social/commons/scf/ckrte.js`

No se recomienda modificar la clientlib cq.social.scf, ya que las futuras actualizaciones pueden anular cualquier edición.

### Personalización de ejemplo: Vínculos en línea {#example-customization-inline-links}

Debido a problemas de seguridad, las opciones de hipervínculo no se incluyen en el conjunto de iconos de texto enriquecido que se presentan a los miembros de forma predeterminada. La capacidad para cometer delitos es amplia cuando se permiten hrefs en UGC.

Para agregar las opciones de hipervínculo a la barra de herramientas:

* Agregar una barra de herramientas denominada &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Select **[!UICONTROL Guardar todo]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
