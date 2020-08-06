---
title: Personalización y ampliación de recursos
description: Conozca las formas en que puede personalizar y ampliar el uso compartido de recursos y el editor de recursos, que ofrece a los usuarios una interfaz y un conjunto de funciones específicos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Personalización y ampliación de recursos {#customizing-and-extending-assets}

El Editor de recursos es el principal punto de acceso que los usuarios de un sitio web de Adobe Enterprise Manager (AEM) utilizarán para buscar, vista y manipulación de los recursos digitales de su repositorio.

Como desarrollador AEM, puede personalizar y ampliar el Editor de recursos de varias formas, ofreciendo a los usuarios una interfaz y un conjunto de funciones específicos.

Se pueden personalizar o mejorar los siguientes aspectos de la funcionalidad:

* [Ampliación del Editor de recursos](asseteditorx.md)
* [Ampliación de la búsqueda de recursos](searchx.md)
* [Processing Assets Using Media Handlers and Workflows](media-handlers.md)
* [Integración de recursos con el flujo de actividades](extending-activity-stream.md)
* [Desarrollo de proxy de recursos](proxy.md)
* [Prácticas recomendadas para configurar ImageMagick](best-practices-for-imagemagick.md)

## Personalización del aspecto {#customizing-the-look-and-feel}

Se pueden personalizar los siguientes aspectos del aspecto del Editor de recursos:

* Logotipo: Puede agregar el logotipo de su propia organización a la interfaz.
* Colores y fuentes: Puede cambiar los colores y las fuentes utilizados en la interfaz.
* Código HTML: Para una personalización más completa, puede cambiar el código HTML subyacente que define las interfaces.

## Personalización de representaciones {#customizing-renditions}

En la terminología de AEM Assets, una representación es la forma en que se presenta un recurso. En general, un recurso concreto puede tener varias representaciones. Por ejemplo, la imagen a color completo puede tener una representación en su tamaño original, otra en un tamaño reducido y otra que se reduzca y se convierta a escala de grises.

Las representaciones en las que está disponible un recurso concreto se pueden personalizar y crear nuevas representaciones.
