---
title: Personalización y targeting de contenido
seo-title: Personalization and Content Targeting
description: Descubra cómo AEM puede crear contenido personalizado
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 34%

---

# Personalización y targeting de contenido {#personalization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Personalización y segmentación de contenido {#personalization-and-content-targeting}

AEM ofrece un marco de herramientas para crear contenido dirigido y presentar experiencias personalizadas.

## Modo Targeting {#targeting-mode}

[Contenido orientado por el autor mediante el modo de Orientación de AEM. ](/help/sites-authoring/content-targeting-touch.md) En el modo segmentación y el componente de Target se proporcionan las herramientas necesarias para crear contenido para las experiencias de las actividades de marketing.

## Actividades {#activities}

Las actividades definen y organizan sus esfuerzos de marketing. Las actividades comprenden las audiencias a las que se dirige y el período de tiempo en el que se aplica la segmentación.

Por ejemplo, el catálogo de productos We.Retail incluye teasers que centran la atención en productos de temporada. La actividad de deportes de verano define los segmentos de marketing a los que se dirigen los teasers durante los meses de verano.

Las actividades también identifican [motor de targeting](/help/sites-authoring/personalization.md#targeting-engine) que utilizan sus páginas.

Utilice la variable [Consola Actividades](/help/sites-authoring/activitylib.md) para crear y administrar las actividades de sus marcas. También puede crear actividades a medida que [crea contenido de destino](/help/sites-authoring/content-targeting-touch.md).

## Experiencias {#experiences}

Para cada actividad, se definen una o más experiencias que identifican las audiencias a las que se va a dirigir. AEM permite controlar el contenido de que consta cada experiencia.

Las audiencias se basan en segmentos de marketing creados en AEM o Adobe Target. Cuando un visitante abre una página web, la lógica de página determina la audiencia a la que pertenece y muestra el contenido que ha creado para esa audiencia.

Por ejemplo, una actividad define las experiencias para dos audiencias independientes: mujeres mayores de 30 años y mujeres menores de 30 años. La página Mujer del sitio web de We.Retail muestra diferentes productos para cada experiencia.

Las experiencias se definen para una actividad. Puede usar la variable [Consola de actividades](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) o [Modo de Orientación](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) para añadir experiencias a una actividad.

## Ofertas {#offers}

Una oferta es el contenido que aparece en una ubicación de una página para una experiencia. Utilice diferentes ofertas para diferentes experiencias para maximizar la eficacia del contenido para sus audiencias.

Por ejemplo, la página Mujer del sitio web de muestra de We.Retail puede utilizar ofertas como la imagen de teaser que aparece en la parte superior de la página. Se utiliza una oferta diferente como teaser para la experiencia de mujeres mayores de 30 años y para la experiencia de mujeres menores de 30 años.

Utilice la variable [Consola de ofertas](/help/sites-authoring/offerlib.md) para crear ofertas que se puedan usar en varias experiencias. Cree ofertas de un solo uso o agregue ofertas de una biblioteca de ofertas cuando [creación de contenido de destino](/help/sites-authoring/content-targeting-touch.md).

## Motor de segmentación {#targeting-engine}

El motor de orientación es el mecanismo que impulsa la lógica del contenido de destino. Las [actividades](/help/sites-authoring/activitylib.md) se configuran para utilizar uno de estos dos motores de segmentación disponibles: AEM y Adobe Target.

### AEM {#aem}

AEM proporciona un motor de targeting integrado que procesa las solicitudes de página y determina el contenido que se va a mostrar. Al utilizar el motor de segmentación de AEM, el uso se limita a los segmentos que se crean en AEM para definir las audiencias de las experiencias.

### Adobe Target {#adobe-target}

El motor de segmentación de Adobe Target provoca que la información recopilada de las visitas a la página sean rastreadas en Adobe Target.

* Cuando utilice este motor de targeting, utilice los segmentos que importe desde Adobe Target para definir las audiencias de las experiencias.
* Las actividades que utilizan el motor de Adobe Target son [sincronizado con Target](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Puede utilizar este motor cuando se haya [integrado con Adobe Target](/help/sites-administering/opt-in.md).
