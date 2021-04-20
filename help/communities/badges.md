---
title: Consola Distintivos
seo-title: Consola Distintivos
description: La consola Distintivos de comunidades le permite añadir distintivos personalizados que se pueden mostrar para los miembros cuando se ganan (se conceden) o cuando asumen una función específica en la comunidad (se asignan)
seo-description: La consola Distintivos de comunidades le permite añadir distintivos personalizados que se pueden mostrar para los miembros cuando se ganan (se conceden) o cuando asumen una función específica en la comunidad (se asignan)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 4%

---


# Consola Distintivos {#badges-console}

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

Si el entorno de publicación es un conjunto de editores, es necesario configurar la [sincronización de usuarios](sync.md).

![imagen_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Cargar imagen]**

   (*Requerido*) Una imagen de distintivo con un tamaño recomendado de 32 x 32 píxeles a 72 ppp en formato JPEG o PNG.

* **[!UICONTROL Nombre]**

   (*Obligatorio*) El nombre del distintivo. Es el `Display Name` predeterminado, así como el nombre del nodo del repositorio. Si el `Name` no es un nombre de nodo de repositorio válido, se modificará.

* **[!UICONTROL Nombre para mostrar]**

   (*Opcional*) El nombre que se mostrará para el distintivo en la interfaz de usuario. El valor predeterminado es el texto sin modificar introducido para `Name`.

* **[!UICONTROL Descripción]**

   (*Opcional*) Una descripción para el distintivo.

## Información adicional {#additional-information}

Para obtener más información sobre la configuración de las reglas de puntuación y distintivo, consulte [Puntuación y distintivos](implementing-scoring.md).

Para administrar distintivos para miembros, consulte [Consola de miembros](members.md).
