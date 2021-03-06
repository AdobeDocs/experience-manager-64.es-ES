---
title: Descarga de componentes
seo-title: Descarga de componentes
description: La transferencia de componentes de comunidades resulta útil cuando una página web está diseñada como una aplicación de una sola página simple que modifica dinámicamente lo que se muestra en función de lo que seleccione el visitante del sitio
seo-description: La transferencia de componentes de comunidades resulta útil cuando una página web está diseñada como una aplicación de una sola página simple que modifica dinámicamente lo que se muestra en función de lo que seleccione el visitante del sitio
uuid: 8c9a5fde-26a3-4610-bc14-f8b665059015
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9cb5294-e5ab-445b-b7c2-ffeecda91c50
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Descarga del componente {#component-sideloading}

## Información general {#overview}

La transferencia de componentes de comunidades resulta útil cuando una página web está diseñada como una aplicación de una sola página simple que modifica dinámicamente lo que se muestra en función de lo que seleccione el visitante del sitio.

Esto se logra cuando los componentes de Comunidades no existen en la plantilla de página, sino que se agregan dinámicamente siguiendo la selección de un visitante del sitio.

Dado que el marco de componentes sociales (SCF) tiene una presencia ligera, solo se registran los componentes de SCF que existen en el momento de la carga de página inicial. Para que un componente SCF agregado dinámicamente se registre después de cargar la página, se debe invocar SCF para &quot;transferir&quot; el componente.

Cuando una página está diseñada para transferir componentes de Communities, es posible almacenar en caché toda la página.

Los pasos para agregar componentes SCF dinámicamente son:

1. [Añadir el componente al DOM](#dynamically-add-component-to-dom)

1. [Cargue el ](#sideload-by-invoking-scf) componente en el equipo mediante uno de los dos métodos siguientes:

* [Inclusión dinámica](#dynamic-inclusion)
   * Boostrap de todos los componentes agregados dinámicamente
* [Carga dinámica](#dynamic-loading)
   * Añadir un componente específico a petición

>[!NOTE]
>
>No se admite la transferencia de [recursos no existentes](scf.md#add-or-include-a-communities-component).

## Añadir dinámicamente el componente a DOM {#dynamically-add-component-to-dom}

Tanto si el componente se incluye dinámicamente como si se carga dinámicamente, primero debe agregarse al DOM.

Al agregar el componente SCF, la etiqueta más común que se debe utilizar es la etiqueta DIV, pero también se pueden utilizar otras etiquetas. Dado que SCF solo examina el DOM cuando la página se carga inicialmente, esta adición al DOM pasará desapercibida hasta que se invoque SCF de forma explícita.

Cualquiera que sea la etiqueta que se utilice, como mínimo, el elemento debe cumplir con el patrón de elementos raíz SCF normal al contener estos dos atributos:

* **data-component-**
idRuta efectiva al componente agregado

* **data-scf-**
componentEl resourceType del componente

A continuación se muestra un ejemplo de un componente de comentarios agregado:

```xml
<div
    class="scf-commentsystem scf translation-commentsystem" 
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## Carga en el sitio invocando SCF {#sideload-by-invoking-scf}

### Inclusión dinámica {#dynamic-inclusion}

La inclusión dinámica utiliza una solicitud de refuerzo que resulta en que SCF examine el DOM y ejecute todos los componentes de SCF que se encuentran en la página.

Para inicializar los componentes SCF en cualquier momento después de cargar la página, simplemente active un evento de JQuery como este:

$(documento).déclencheur(SCF.eventos.BOOTSTRAP_REQUEST);

### Carga dinámica {#dynamic-loading}

La carga dinámica proporciona control sobre la carga de componentes SCF.

En lugar de arrancar todos los componentes SCF que se encuentran en el DOM, es posible especificar un componente SCF específico para cargar con este método JavaScript:

SCF.addComponent(documento.getElementById(*someId*));

Donde *someId* es el valor del atributo **data-component-id**.
