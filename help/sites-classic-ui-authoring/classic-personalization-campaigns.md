---
title: Campaign Management
seo-title: Campaign Management
description: La administración de campañas ofrece a los especialistas en marketing digital la oportunidad de ofrecer contenido personalizado y así crear experiencias dedicadas para los visitantes. Le permite organizar sus campañas de marketing en la web, el correo electrónico y los servicios móviles, para atraer a los visitantes.
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: 2980ec6d-cdd4-4fbd-b4a4-5e45e4508903
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 3%

---

# Campaign Management{#campaign-management}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La administración de campañas ofrece a los especialistas en marketing digital la oportunidad de ofrecer contenido personalizado y así crear experiencias dedicadas para los visitantes.

Le permite organizar sus campañas de marketing en la web, el correo electrónico y los servicios móviles, para atraer a los visitantes. Puede crear contenido, segmentar visitantes, insertar y promocionar contenido orientado para perfiles de usuario específicos y administrar campañas en varios canales.

Este documento describe los distintos elementos que componen las campañas. Encontrará información más detallada en los siguientes documentos:

* [Teasers y estrategias](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [Marketing por correo electrónico](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Páginas de destino](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Ofertas de Target](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Uso del administrador de campañas de marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Información acerca de la segmentación](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Configuración de la campaña](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

La administración de campañas consta de varios elementos:

* **Marcas**
En AEM, las marcas son la unidad de nivel superior y forman una colección de 
**Campañas**.

* **Campañas**
Una campaña es una colección de individuos 
**Experiencias**.

* **Experiencias**
El contenido centrado forma las distintas experiencias, presentadas al visitante en 
**Puntos de contacto**. Hay varios tipos de experiencia disponibles:

   * **Teasers**
      [Páginas o párrafos de teaser](#teasers) se utilizan para dirigir visitantes específicos **Segmentos** a contenido centrado en sus intereses.

      Las páginas de teaser pueden:

      * presentar una gama de opciones para que el visitante elija
      * mostrar solo un párrafo de teaser basado en el segmento específico del visitante; por ejemplo, el párrafo de teaser mostrado puede depender de la edad del visitante.

      Normalmente, una página de teaser es una acción temporal que dura un período de tiempo específico, hasta que se reemplaza por la siguiente página de teaser.

   * **Newsletters**

      [Comunicaciones por correo electrónico](#emailmarketing) se utilizan para atraer usuarios y animarlos a que visiten su sitio web. Normalmente toman la forma de un boletín, que se envía a su **Posibles clientes** (que normalmente se agrupan en **Listas**). **Nota:** El Adobe no tiene previsto seguir mejorando esta capacidad. La recomendación es [aproveche Adobe Campaign y la integración para AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

      Esto permite la integración con Adobe Target (anteriormente Test&amp;Target), que proporciona a los especialistas en marketing una herramienta de optimización de sitio web de conversión con las capacidades necesarias para que el contenido en línea y las ofertas sean más relevantes para sus clientes, lo que resulta en buenas conversiones. Adobe Target proporciona una interfaz intuitiva para diseñar y ejecutar pruebas, crear segmentos de audiencia y contenido de segmentación, todo ello desde una sola aplicación.


* **Puntos de contacto**

   Estos son puntos de contacto entre el visitante y la campaña. Los puntos de contacto están conectados a las experiencias que ha creado.

   Por ejemplo, para los teasers, es la página de contenido donde se encuentra el párrafo de teaser; para un boletín, es la lista de correo.

* **posibles clientes**

   La información recopilada sobre los visitantes y cómo ponerse en contacto con ellos forma la base de los posibles clientes. **Nota:** El Adobe no tiene previsto seguir mejorando esta capacidad.

   La recomendación es [aproveche Adobe Campaign y la integración para AEM](/help/sites-administering/campaign.md).

* **Listas**

   Normalmente, los posibles clientes se agrupan en listas para que pueda aplicar una acción colectiva. Nota: **Nota:** El Adobe no tiene previsto seguir mejorando esta capacidad.

   La recomendación es [aproveche Adobe Campaign y la integración para AEM.](/help/sites-administering/campaign.md)

* **Segmentos**

   Los visitantes del sitio tienen diferentes intereses y objetivos cuando acceden al sitio. Analizar esto según factores como la actividad en el sitio web, la información de perfil registrada y la actividad en otros sitios web le ayuda a definir segmentos. A continuación, el contenido se puede dirigir específicamente a las necesidades e intereses del visitante según los segmentos con los que coincida.

* **MCM**

   Marketing Campaign Manager (MCM) es una consola que le permite acceder a toda la funcionalidad necesaria para crear y controlar sus campañas, marcas, experiencias, touchpoints, posibles clientes, listas, segmentos e informes.

   Se puede acceder a él desde varias ubicaciones (etiquetadas como **Campañas**) o con, por ejemplo, la dirección URL:

   `http://localhost:4502/libs/mcm/content/admin.html`
