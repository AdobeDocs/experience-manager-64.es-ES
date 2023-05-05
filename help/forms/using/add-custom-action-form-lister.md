---
title: Agregar acciones personalizadas a elementos de lista de formularios
seo-title: Adding custom action on form lister items
description: Los desarrolladores de formularios pueden agregar más acciones a la lista de formularios de la página del portal de formularios. De forma predeterminada, la lista de formularios le permite acceder al formulario, rellenarlo y enviarlo.
seo-description: Form developers can add more actions to the listing of forms on the forms portal page. By default, the form listing allows you to access the form, fill it, and submit it.
uuid: 02c64f7d-f726-4a5b-a303-ec96934e9c01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 0e0a9b6b-fd2f-4cec-b233-500c940ee4d5
exl-id: d8f60be3-474a-4dd1-aaa5-7b6a97e1a9bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 90%

---

# Agregar acciones personalizadas a elementos de lista de formularios {#adding-custom-action-on-form-lister-items}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En AEM Forms, puede crear una página del portal que enumere los formularios disponibles. De forma predeterminada, puede buscar y mostrar formularios en una página del portal. Puede abrir formularios para rellenar y enviar la información. Solo se proporcionan las acciones de procesamiento predeterminadas para los formularios enumerados en una página del portal. Para obtener más información sobre las acciones disponibles en una página del portal, consulte [Crear una página de portal de formularios](/help/forms/using/creating-form-portal-page.md).

Puede agregar otras opciones a la página del portal. Estas opciones o acciones se pueden personalizar si personaliza la plantilla del portal de formularios.

Este artículo muestra cómo crear un botón para enviar el vínculo de un formulario, directamente desde una página del portal de formularios. Esta personalización requiere la actualización de la plantilla para el componente Buscar y listar.

El código requerido para agregar la acción a la plantilla está disponible a continuación. El atributo `onclick` del fragmento de código tiene un script para enviar un vínculo de un formulario por correo electrónico.

```mxml
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

Puede agregar acciones similares en la plantilla personalizada. Para definir una función de JavaScript, agregue la función en un script de nivel de página y vincúlelo con el elemento HTML requerido. En el ejemplo anterior, la expresión `onclick` es la función vinculada.

Después de realizar las ediciones en la plantilla, la página del portal de muestra contiene un botón para enviar el vínculo del formulario por correo electrónico, como se muestra a continuación.

![correo electrónico](assets/email.png)
