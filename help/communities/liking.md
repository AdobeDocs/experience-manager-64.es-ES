---
title: Uso de "Me gusta"
seo-title: Using Liking
description: Adición y configuración del componente "Me gusta"
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 7%

---

# Uso de &quot;Me gusta&quot; {#using-liking}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La variable `Liking`es una herramienta útil que permite a los usuarios expresar una opinión sobre un contenido determinado, como un comentario dentro de un foro. Con la variable `Liking`, los miembros seleccionan el icono del corazón para indicar una opinión positiva.

## Adición de &quot;Me gusta&quot; a una página {#adding-liking-to-a-page}

Para agregar un `Liking` a una página en modo de autor, utilice el navegador de componentes para localizar

* `Communities / Liking`

y arrástrela a su lugar en una página, por ejemplo, una posición relativa a la función que desee para los usuarios.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](essentials-liking.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Liking` aparecerá el componente.

![imagen_1-93](assets/chlimage_1-93.png)

## Configuración de &quot;Me gusta&quot; {#configuring-liking}

Seleccione la colocación `Liking` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![imagen_1-94](assets/chlimage_1-94.png)

En el **[!UICONTROL Textos y etiquetas]** especifique las propiedades utilizadas para registrar &quot;Me gusta&quot;.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Etiqueta de respuesta positiva]**
(
*Requerido*) El nombre de propiedad para una respuesta positiva.

* **[!UICONTROL Etiqueta de respuesta negativa]**
(
*Requerido*) El nombre de la propiedad para una respuesta negativa.

* **[!UICONTROL Nombre de recuento]**
(
*Requerido*) El nombre de propiedad interno identificable para esta instancia de un componente de votación.

## Experiencia del visitante del sitio {#site-visitor-experience}

### Miembros {#members}

Los miembros podrán cambiar de forma similar en cualquier momento.

### Anónimo {#anonymous}

No se admite &quot;Me gusta&quot; anónimo. Los visitantes del sitio deben registrarse (convertirse en miembros) e iniciar sesión para participar en el &quot;Me gusta&quot;.

## Información adicional {#additional-information}

Puede encontrar más información en la [&quot;Me gusta&quot; de Essentials](essentials-liking.md) para desarrolladores.
