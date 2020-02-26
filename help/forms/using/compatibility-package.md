---
title: Paquete de compatibilidad
seo-title: Paquete de compatibilidad
description: 'La instalación del paquete de compatibilidad en AEM Forms 6.4 le permite utilizar los recursos de gestión de correspondencia de AEM Forms 6.3 y las páginas y plantillas de formularios adaptables obsoletas '
seo-description: La instalación del paquete de compatibilidad en AEM Forms 6.4 le permite utilizar los recursos de gestión de correspondencia de AEM Forms 6.3 y las páginas y plantillas de formularios adaptables obsoletas
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: 9a2ebded0068213903020d2c5633a05b6ffb07ef

---


# Instalar paquete de compatibilidad {#compatibility-package}

La instalación del paquete de compatibilidad en AEM Forms 6.4 le permite utilizar los recursos de gestión de correspondencia de AEM Forms 6.3 y las páginas y plantillas de formularios adaptables obsoletas

## Información general {#overview}

La comunicación interactiva es el método predeterminado y recomendado para crear comunicaciones con los clientes en AEM Forms 6.4. Para seguir utilizando las cartas de AEM 6.3 Forms y AEM 6.2 Forms, debe instalar el paquete [de compatibilidad con](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)AEMFD.

El paquete de compatibilidad con AEMFD le permite utilizar los siguientes recursos de AEM Forms 6.3 y 6.2 en AEM Forms 6.4:

* Fragmentos de documento creados en AEM Forms 6.3 y 6.2
* Cartas
* Diccionarios de datos
* Plantillas y páginas obsoletas de formularios adaptables

Para obtener más información, consulte [Recursos compatibles con AEM Forms 6.4 mediante la instalación del paquete](/help/forms/using/compatibility-package.md#assetsmadecompatible)Compatibilidad.

## Añadir compatibilidad con recursos de AEM Forms 6.3 y 6.2 en AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Después de realizar una actualización, haga lo siguiente para instalar el paquete de compatibilidad con AEMFD y hacer que sus recursos sean compatibles con 6.4:

Asegúrese de tener el paquete [de compatibilidad con](/help/sites-deploying/backward-compatibility.md) AEM preinstalado.

1. Instale el paquete [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)compatibilidad.

   Para obtener más información sobre cómo cargar e instalar el paquete, consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md).

1. Después de estabilizar los registros, reinicie el servidor.
1. Utilice la utilidad de migración para hacer que los recursos sean compatibles con 6.4.

   Para obtener más información, consulte Utilidad [de migración](/help/forms/using/migration-utility.md).

## Recursos compatibles con AEM Forms 6.4 mediante la instalación del paquete de compatibilidad {#assetsmadecompatible}

Al instalar el paquete Compatibilidad, puede hacer que los siguientes recursos y plantillas sean compatibles con AEM Forms 6.4:

* Recursos de gestión de correspondencia de AEM 6.3 y versiones anteriores

   * [Cartas](/help/forms/using/create-letter.md)
   * [Diccionarios de datos](/help/forms/using/data-dictionary.md)
   * Fragmentos de documento

* Plantillas de formularios adaptables obsoletas

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnregistrationTemplate
   * /libs/fd/af/templates/simpleEnregistrationTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnregistrationTemplate
   * /libs/fd/af/templates/tabbedEnregistrationTemplate2
   * /libs/fd/afaddon/templates/advancedEnregistrationTemplate
   * /libs/fd/afaddon/templates/advancedEnregistrationTemplate2

* Páginas en desuso de formularios adaptables:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenregistration
   * /libs/fd/afaddon/components/page/Advancedenregistration

