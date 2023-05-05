---
title: Uso de la votación
seo-title: Using Voting
description: Adición del componente Votación a una página
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: 660a7106-0c21-4073-8319-4d6d20b9bc49
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 7%

---

# Uso de la votación {#using-voting}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La variable `Voting` es una herramienta útil que permite a los miembros de la comunidad clasificar un contenido determinado, como una respuesta dentro de un componente QnA. Con la variable `Voting` , los miembros seleccionan flechas arriba o abajo para indicar su opinión.

## Adición de votos a una página {#adding-voting-to-a-page}

Para agregar un `Voting` a una página en modo de autor, utilice el navegador de componentes para localizar `Communities / Voting` y arrástrela a su lugar en una página, como una posición relativa a la función para que los usuarios voten.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](essentials-voting.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Voting` aparecerá el componente.

![chlimage_1-307](assets/chlimage_1-307.png)

## Configuración del voto {#configuring-voting}

Seleccione la colocación `Voting` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-308](assets/chlimage_1-308.png)

En el **[!UICONTROL Textos y etiquetas]** especifique las propiedades utilizadas para registrar votos.

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL Etiqueta de respuesta positiva]**
(
*Requerido*) El nombre de propiedad interno para una respuesta positiva.

* **[!UICONTROL Etiqueta de respuesta negativa]**
(
*Requerido*) El nombre de propiedad interna para una respuesta negativa.

* **[!UICONTROL Nombre de recuento]**
(
*Requerido*) El nombre de propiedad interno identificable para esta instancia de un componente de votación.

## Experiencia del visitante del sitio {#site-visitor-experience}

### Miembros {#members}

Los Miembros sólo podrán votar una vez, pero podrán modificarlo en cualquier momento.

### Anónimo {#anonymous}

No se admite la votación anónima. Los visitantes del sitio deben registrarse (convertirse en miembros) e iniciar sesión para participar en la votación una vez.

## Información adicional {#additional-information}

Puede encontrar más información en la [Esenciales de votación](essentials-voting.md) para desarrolladores.
