---
title: Traducción de contenido para sitios multilingües
seo-title: Traducción de contenido para sitios multilingües
description: Aprenda a traducir contenido para sitios multilingües.
seo-description: Aprenda a traducir contenido para sitios multilingües.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Traducción de contenido para sitios multilingües{#translating-content-for-multilingual-sites}

Automatice la traducción del contenido de la página, los recursos y el contenido generado por el usuario para crear y mantener sitios web multilingües. Para automatizar los flujos de trabajo de traducción, integre proveedores de servicio de traducción con AEM y cree proyectos para traducir contenido a varios idiomas. AEM admite flujos de trabajo de traducción humana y automática.

* Traducción humana: El contenido se envía a su proveedor de traducción y es traducido por traductores profesionales. Una vez completado, el contenido traducido se devuelve e importa en AEM. Cuando su proveedor de traducción está integrado con AEM, el contenido se envía automáticamente entre AEM y el proveedor de traducción.
* Traducción automática: El servicio de traducción automática traduce inmediatamente su contenido.

La traducción de contenido implica los siguientes pasos:

1. [Conecte AEM con su proveedor de servicio](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) de traducción y [cree configuraciones](/help/sites-administering/tc-tic.md)del marco de integración de traducción.

1. [Asocie las páginas del maestro](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) de idioma con el servicio de traducción y las configuraciones del marco.
1. [Identifique el tipo de contenido](/help/sites-administering/tc-rules.md) que traducir.
1. [Para preparar el contenido para la traducción](/help/sites-administering/tc-prep.md) , cree el maestro de idioma y las páginas raíz de las copias de idioma.
1. [Cree proyectos](/help/sites-administering/tc-manage.md) de traducción para reunir el contenido que traducir y preparar el proceso de traducción.
1. Utilice los proyectos de traducción para [administrar el proceso](/help/sites-administering/tc-manage.md)de traducción de contenido.

Si el proveedor de servicio de traducción no proporciona un conector para la integración con AEM, AEM admite la extracción manual y la reinserción de contenido de traducción en formato XML.

>[!NOTE]
>
>El usuario debe ser miembro del grupo de administradores de proyectos para utilizar las funciones de copia de idioma.

## Prácticas recomendadas   {#best-practices}

La página [Prácticas recomendadas](/help/sites-administering/tc-bp.md) de traducción contiene información importante sobre la implementación.
