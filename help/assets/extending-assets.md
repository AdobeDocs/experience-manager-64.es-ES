---
title: Personalización y ampliación de recursos
description: Conozca las formas en que puede personalizar y ampliar Asset Share y Asset Editor, que presentan a los usuarios una interfaz y un conjunto de funciones específicos.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Personalización y ampliación de recursos {#customizing-and-extending-assets}

El Editor de recursos es el punto de acceso principal que los usuarios de un sitio web de Enterprise Manager de Adobe utilizarán para encontrar, ver y manipular los recursos digitales de su repositorio.

Como [!DNL Experience Manager] desarrollador, puede personalizar y ampliar el Editor de recursos de varias maneras, para que los usuarios tengan una interfaz y un conjunto de funciones específicos.

Se pueden personalizar o mejorar los siguientes aspectos de la funcionalidad:

* [Ampliación del Editor de recursos](asseteditorx.md)
* [Ampliación de la búsqueda de recursos](searchx.md)
* [Processing Assets Using Media Handlers and Workflows](media-handlers.md)
* [Integración de recursos con el flujo de actividad](extending-activity-stream.md)
* [Desarrollo de proxy de recursos](proxy.md)
* [Prácticas recomendadas para configurar ImageMagick](best-practices-for-imagemagick.md)

## Personalización del aspecto {#customizing-the-look-and-feel}

Los siguientes aspectos del aspecto del Editor de recursos se pueden personalizar:

* Logotipo: Puede añadir el logotipo de su propia organización a la interfaz.
* Colores y fuentes: Puede cambiar los colores y las fuentes utilizados en la interfaz.
* Código HTML: Para una personalización más completa, puede cambiar el código HTML subyacente que define las interfaces.

## Personalización de representaciones {#customizing-renditions}

En la terminología [!DNL Experience Manager Assets], una representación es la forma en que se presenta un recurso. En general, un recurso concreto puede tener varias representaciones. Por ejemplo, la imagen de color completo puede tener una representación en su tamaño original, otra en un tamaño reducido y otra que se reduzca y se convierta a escala de grises.

Las representaciones en las que está disponible un recurso en particular se pueden personalizar y crear nuevas representaciones.
