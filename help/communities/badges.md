---
title: Consola de distintivos
seo-title: Consola de distintivos
description: La consola Distintivos de comunidades permite agregar distintivos personalizados que se pueden mostrar para los miembros cuando se ganan (se otorgan) o cuando asumen una función específica en la comunidad (se asignan)
seo-description: La consola Distintivos de comunidades permite agregar distintivos personalizados que se pueden mostrar para los miembros cuando se ganan (se otorgan) o cuando asumen una función específica en la comunidad (se asignan)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# Consola de distintivos {#badges-console}

## Acerca de los distintivos {#about-badges}

La consola Distintivos de comunidades permite agregar distintivos personalizados que se pueden mostrar para un miembro cuando se ganan (se otorgan) o cuando asumen una función específica en la comunidad (se asignan).

### Visibilidad del distintivo {#badge-visibility}

Actualmente, las insignias que un miembro de la comunidad obtiene o se asigna aparecerán junto con su nombre y avatar en las siguientes ubicaciones:

* Perfiles
* [Foros](forum.md)
* [P y R](working-with-qna.md)
* [Foros](enabling-leaderboard.md)
* [Ideación](ideation-feature.md)

En el entorno del autor, para llegar a la consola Badges

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Distintivos]**

Esta consola muestra las insignias disponibles actualmente y desde las cuales se pueden agregar nuevas insignias.

![chlimage_1-242](assets/chlimage_1-242.png)

## Crear distintivo {#create-badge}

Para crear un distintivo, cargue una imagen pequeña adecuada (72 ppp con una altura de entre 26 y 32 píxeles) y proporcione un nombre. La imagen del distintivo se almacena en el repositorio en `/etc/community/badging/images` y se replica automáticamente en el entorno de publicación.

Si el entorno de publicación es un conjunto de editores, es necesario configurar la sincronización [de](sync.md)usuarios.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Cargar imagen]**

   (*Requerido*) Imagen de un distintivo con un tamaño recomendado de 32 x 32 píxeles a 72 ppp en formato JPEG o PNG.

* **[!UICONTROL Nombre]**

   (*Requerido*) El nombre del distintivo. Es el nombre predeterminado `Display Name` así como el nombre del nodo del repositorio. Si el nombre `Name` no es un nombre de nodo de repositorio válido, se modificará.

* **[!UICONTROL Nombre para mostrar]**

   (*Opcional*) El nombre que se mostrará para el distintivo en la interfaz de usuario. El valor predeterminado es el texto sin modificar introducido para el `Name`.

* **[!UICONTROL Descripción]**

   (*Opcional*) Descripción del distintivo.

## Información adicional {#additional-information}

Para obtener más información sobre la configuración de las reglas de puntuación y marca, consulte [Puntuación y distintivos](implementing-scoring.md).

Para administrar distintivos para miembros, consulte Consola [](members.md)de miembros.
