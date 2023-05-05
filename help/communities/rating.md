---
title: Uso de clasificaciones
seo-title: Using Ratings
description: Adición de un componente Clasificación a una página
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 4%

---

# Uso de clasificaciones {#using-ratings}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La variable `Rating`se utiliza de forma independiente o junto con otras funciones de Communities. Este componente permite a los miembros de la comunidad que han iniciado sesión expresar sus opiniones clasificando el contenido.

## Adición de una clasificación a una página {#adding-a-rating-to-a-page}

Para agregar un `Rating`a una página en modo de autor, busque el componente `Communities / Rating` y arrástrela a su lugar en una página, como una posición relativa a la función que deben clasificar los miembros.

Para obtener la información necesaria, visite [Conceptos básicos de los componentes de Communities](basics.md).

Cuando la variable [bibliotecas requeridas del lado del cliente](rating-basics.md#essentials-for-client-side) se incluyen, así es como se muestra la variable `Rating` aparecerá el componente.

![chlimage_1-493](assets/chlimage_1-493.png)

## Configuración de la clasificación {#configuring-rating}

Seleccione la colocación `Rating` para acceder y seleccionar el componente `Configure` que abre el cuadro de diálogo de edición.

![chlimage_1-494](assets/chlimage_1-494.png)

En el **[!UICONTROL Textos y etiquetas]** especifique el identificador interno de la clasificación.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Nombre Tally]**
(*Requerido*) Un nombre sencillo para el `Rating`que identifica de forma exclusiva esta instancia. Debe ser un nombre de nodo válido para el repositorio.

## Experiencia del visitante del sitio {#site-visitor-experience}

### Miembros {#members}

Solo se permite una clasificación por miembro. El miembro podrá cambiar su calificación en cualquier momento.

### Anónimo {#anonymous}

No se admite la publicación anónima de una clasificación. Los visitantes del sitio deben registrarse (convertirse en miembros) e iniciar sesión para participar.

## Información adicional {#additional-information}

Puede encontrar más información en la [Aspectos básicos de la clasificación](rating-basics.md) para desarrolladores.
