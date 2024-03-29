---
title: Content Services
seo-title: Content Services
description: Content Services
seo-description: null
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
exl-id: e900d93e-f7cd-4a0d-a866-7fc6c7882797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 7%

---

# Content Services{#content-services}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe recomienda utilizar el Editor de SPA para proyectos que requieren una representación del lado del cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>La función Servicios de contenido está documentada únicamente con fines de vista previa.
>
>Está sujeto a cambios con el lanzamiento de 6.3 GA Service Pack 1.

Los servicios de contenido de AEM Mobile son una característica sencilla y sencilla para solicitar contenido administrado por AEM. Esto proporciona a todos los desarrolladores de aplicaciones una forma de alto rendimiento de recuperar contenido sin tener que tener conocimientos profundos de AEM repositorio de contenido (JCR) y marco web (Sling). Permite que las aplicaciones solicitantes se desvinculen del repositorio de contenido.

Content Services introduce varias construcciones de AEM nuevas que permiten a un desarrollador acceder AEM contenido administrado sin conocer la estructura del repositorio de dicho contenido.

Estas construcciones son necesarias para mantener la flexibilidad y permitir una futura expansión al proporcionar una capa de abstracción entre el contenido administrado AEM y las aplicaciones móviles que consumen el contenido. Esto permite que AEM Content Services funcione como una capa de abstracción entre los requisitos de contenido de la aplicación nativa y el repositorio de contenido de AEM.

Los servicios de contenido pueden entregar el contenido como recursos, como HTML empaquetado (HTML/CSS/JS) o como contenido independiente del canal.

>[!CAUTION]
>
>**Requisitos previos:**
>
>Antes de empezar a usar los servicios de contenido, asegúrese de habilitar el indicador Servicios de contenido . Para habilitar la creación y administración de modelos en la aplicación, debe habilitar los modelos de datos en el Explorador de configuración.
>
>Consulte **[Administración de servicios de contenido](/help/mobile/developing-content-services.md)** para obtener más información.
>
>Consulte la documentación del [](/help/sites-administering/configurations.md)Explorador de configuración para obtener más información.

![chlimage_1-143](assets/chlimage_1-143.png)

Una vez que haya establecido el indicador de servicios de contenido y habilitado los modelos de datos en el navegador de configuración, consulte los recursos siguientes para empezar a usar los servicios de contenido de AEM Mobile, familiarícese con los conceptos de servicios de contenido, como la administración de modelos, la administración de entidades y el envío/procesamiento de contenido para los servicios de contenido de AEM Mobile.

* Modelos en el repositorio
* Renderización y entrega
