---
title: Consola Distintivos
seo-title: Badges Console
description: La consola Distintivos de comunidades le permite añadir distintivos personalizados que se pueden mostrar para los miembros cuando se ganan (se conceden) o cuando asumen una función específica en la comunidad (se asignan)
seo-description: The Communities Badges console lets you add custom badges that can be displayed for members when earned (awarded) or when they take on a specific role in the community (assigned)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 6%

---

# Consola Distintivos {#badges-console}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de los distintivos {#about-badges}

La consola Distintivos de comunidades permite agregar distintivos personalizados que se pueden mostrar para un miembro cuando se ganan (se conceden) o cuando asumen una función específica en la comunidad (se asignan).

### Visibilidad del distintivo {#badge-visibility}

Actualmente, los distintivos que un miembro de la comunidad gana o es asignado aparecerán junto con su nombre y avatar en las siguientes ubicaciones:

* Perfiles
* [Foros](forum.md)
* [P y R](working-with-qna.md)
* [Paneles](enabling-leaderboard.md)
* [Ideación](ideation-feature.md)

En el entorno de creación, para llegar a la consola Distintivos

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Distintivos]**

Esta consola muestra los distintivos actualmente disponibles y desde los que se pueden añadir nuevos distintivos.

![chlimage_1-242](assets/chlimage_1-242.png)

## Crear distintivo {#create-badge}

Se crea un distintivo cargando una imagen suficientemente pequeña (72 ppp con una altura que oscila entre 26 y 32 píxeles) y proporcionando un nombre. La imagen del distintivo se almacena en el repositorio en `/etc/community/badging/images` y se duplica automáticamente en el entorno de publicación.

Si el entorno de publicación es un conjunto de editores, es necesario configurar [sincronización de usuarios](sync.md).

![imagen_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Cargar imagen]**

   (*Requerido*) Una imagen de distintivo con un tamaño recomendado de 32 x 32 píxeles a 72 ppp en formato JPEG o PNG.

* **[!UICONTROL Nombre]**

   (*Requerido*) El nombre del distintivo. Es el valor predeterminado `Display Name` así como el nombre del nodo del repositorio. Si la variable `Name` no es un nombre de nodo de repositorio válido, se modificará.

* **[!UICONTROL Nombre para mostrar]**

   (*Opcional*) Nombre que se mostrará para el distintivo en la interfaz de usuario. El valor predeterminado es el texto sin modificar introducido para la variable `Name`.

* **[!UICONTROL Descripción]**

   (*Opcional*) Descripción del distintivo.

## Información adicional {#additional-information}

Para obtener más información sobre la configuración de reglas de puntuación y de distintivo, consulte [Puntuación y distintivos](implementing-scoring.md).

Para administrar distintivos para miembros, consulte [Consola Miembros](members.md).
