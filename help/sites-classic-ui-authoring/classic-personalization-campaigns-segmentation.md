---
title: Información acerca de la segmentación
seo-title: Understanding Segmentation
description: La segmentación es una consideración clave al crear una campaña. En la mayoría de los casos, tendrá que tener segmentos ya definidos antes de iniciar la campaña.
seo-description: Segmentation is a key consideration when creating a campaign. In most cases, you will need to have segments already defined before starting your campaign.
uuid: 609d83b3-df0e-44ad-8e27-90b676d2666b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bb75f4ab-d983-45f6-98a3-da8bd9b63751
exl-id: 441cf983-e1dc-4343-9c2c-e5ed5891e84b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 30%

---

# Información acerca de la segmentación{#understanding-segmentation}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La segmentación es una consideración clave al crear una campaña. En la mayoría de los casos, tendrá que tener segmentos ya definidos antes de iniciar la campaña.

Los visitantes del sitio tienen diferentes intereses y objetivos cuando acceden al sitio. Entender estos objetivos y cumplir las expectativas es un factor de éxito importante para el marketing en línea.

La segmentación ayuda a conseguirlo analizando y caracterizando los siguientes aspectos de un visitante:

* actividad en el sitio web
* perfil
* actividad en otros sitios web

El contenido se puede dirigir específicamente a las necesidades y los intereses del visitante, según los segmentos con los que coincida.

## Uso de la segmentación {#using-segmentation}

Los segmentos se definen en [Configuración de la segmentación](/help/sites-administering/campaign-segmentation.md). Se utilizan para dirigir el contenido real que visualiza un público objetivo concreto.

## Terminología de segmentación {#segmentation-terminology}

Al analizar la segmentación, se emplea la siguiente terminología:

**Visitante** Un visitante es una persona que visita un sitio web. La visita de esa persona suele comenzar desde una página de referencia y luego pasa a una o más vistas de página en su propio sitio web. Se puede crear un perfil de comportamiento a partir de los detalles de la visita de esa persona.

**Usuario** Un usuario es un visitante que se registra con el sitio web para recibir un perfil de cuenta. Para generar su perfil, proporcionan una identificación adicional, como una dirección de correo electrónico y el sexo, entre otros. También se puede recopilar información adicional, incluida la actividad de la comunidad y los patrones de compra, entre otros. En función de la información proporcionada en el perfil, se puede crear un perfil demográfico.

**Característica** Un rasgo es una característica o propiedad de un visitante que se puede usar para determinar la pertenencia a un segmento específico.

**Segmento** Un segmento es una colección de visitantes que comparten ciertas características. Los segmentos deben ser distintivos, con un mínimo de superposición con otros segmentos.

**Características de comportamiento** Las características de comportamiento son aquellas que se relacionan con el comportamiento de un visitante en el sitio web. Entre estas características se incluyen:

* Interés en el sitio web, incluyendo las páginas y los productos comprados.
* Interés en el sitio web de referencia, incluyendo los términos de búsqueda utilizados o los anuncios en los que se ha hecho clic.
* Interés en otros sitios; se determina con herramientas como Spyjax.
* Lealtad del visitante; duración de la visita, frecuencia de las visitas.

**Características demográficas** Estas son características de población seleccionadas, entre las que se incluyen:

* Edad
* Ingresos
* Tamaño familiar
* Estado civil
* Sexo
* Lugar de residencia

**Características derivadas**

Algunas características demográficas son difíciles de determinar sin registro, pero se pueden derivar combinando características demográficas y de comportamiento.

Por ejemplo, la combinación de la dirección URL de referencia (como característica de comportamiento) con datos demográficos (adquiridos con herramientas como [Google Ad Planner](https://www.google.com/adplanner/)) permite que los propietarios del sitio obtengan características demográficas de los visitantes.

**Subsegmento** Un segmento se puede subdividir en varios subsegmentos. Esto se lleva a cabo definiendo características adicionales.

**Página Teaser** Una página de teaser está dirigida a una audiencia específica. Incluye contenido reutilizable que se puede emplear en el párrafo de teaser.

**Campaign** Una campaña es una colección de páginas de teaser y páginas de marketing por correo electrónico, como newsletters o invitaciones. Normalmente, una campaña se ejecuta durante un periodo limitado y es reemplazada por otra campaña.

**Párrafo de teaser** Se trata de un párrafo que extrae contenido de otra página en función de una estrategia de selección. Esta estrategia de selección puede tener en cuenta segmentos y campañas.

**Lista** Una lista se extrae de un segmento de usuarios registrados. Por ejemplo, la ubicación se utiliza para dirigir los contenidos del párrafo de teaser.

>[!NOTE]
>
>Consulte [Segmentación](/help/sites-administering/campaign-segmentation.md) para obtener más información sobre los segmentos de AEM.
