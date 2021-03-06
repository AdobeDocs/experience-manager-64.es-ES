---
title: Uso de "Me gusta"
seo-title: Uso de "Me gusta"
description: Añadir y configurar el componente "Me gusta"
seo-description: Añadir y configurar el componente "Me gusta"
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---


# Uso de &quot;Me gusta&quot; {#using-liking}

El componente `Liking`es una herramienta útil que permite a los usuarios expresar una opinión sobre un contenido determinado, como un comentario dentro de un foro. Con el componente `Liking`, los miembros seleccionan el icono del corazón para indicar una opinión positiva.

## Añadir &quot;Me gusta&quot; a una página {#adding-liking-to-a-page}

Para agregar un componente `Liking` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Liking`

y arrástrelo a su lugar en una página, como una posición relativa a la función que los usuarios deseen.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de comunidades](basics.md).

Cuando se incluyen las [bibliotecas requeridas del lado del cliente](essentials-liking.md#essentials-for-client-side), así es como aparecerá el componente `Liking`.

![chlimage_1-93](assets/chlimage_1-93.png)

## Configuración de &quot;Me gusta&quot; {#configuring-liking}

Seleccione el componente `Liking` colocado para acceder y seleccione el icono `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-94](assets/chlimage_1-94.png)

En la ficha **[!UICONTROL Textos y etiquetas]**, especifique las propiedades utilizadas para registrar &quot;Me gusta&quot;.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Etiqueta de respuesta positiva]**
(
*Requerido*) El nombre de la propiedad para una respuesta positiva.

* **[!UICONTROL Etiqueta de respuesta negativa]**
(
*Requerido*) El nombre de la propiedad para una respuesta negativa.

* **[!UICONTROL Nombre de recuento]**
(
*Requerido*) El nombre de propiedad interno identificable para esta instancia de un componente de votación.

## Experiencia de Visitante del sitio {#site-visitor-experience}

### Miembros {#members}

Los Miembros pueden cambiar su estilo en cualquier momento.

### Anónimo {#anonymous}

No se admite el &quot;Me gusta&quot; anónimo. Los visitantes del sitio deben registrarse (convertirse en miembros) e iniciar sesión para participar en el &quot;Me gusta&quot;.

## Información adicional {#additional-information}

Puede encontrar más información en la página [&quot;Me gusta esencial](essentials-liking.md)&quot; para desarrolladores.
