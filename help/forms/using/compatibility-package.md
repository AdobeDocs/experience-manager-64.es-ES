---
title: Paquete de compatibilidad
seo-title: Compatibility Package
description: La instalación del paquete de compatibilidad en AEM Forms 6.4 le permite utilizar los recursos de gestión de correspondencia de AEM Forms 6.3 y las páginas y plantillas de formularios adaptables obsoletas
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 59%

---

# Instalación del paquete de compatibilidad {#compatibility-package}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La instalación del paquete de compatibilidad en AEM Forms 6.4 le permite utilizar los recursos de gestión de correspondencia de AEM Forms 6.3 y las páginas y plantillas de formularios adaptables obsoletas

## Información general {#overview}

La comunicación interactiva es el método predeterminado y recomendado para crear comunicaciones con los clientes en AEM Forms 6.4. Para seguir utilizando las cartas de AEM 6.3 Forms y AEM 6.2 Forms, debe instalar el [Paquete de compatibilidad de AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=es).

El paquete Compatibilidad con AEMFD le permite utilizar los siguientes recursos de AEM Forms 6.3 y 6.2 en AEM Forms 6.4:

* Fragmentos de documento creados en AEM Forms 6.3 y 6.2
* Cartas
* Diccionarios de datos
* Plantillas y páginas obsoletas de formularios adaptables

Para obtener más información, consulte [Recursos compatibles con AEM Forms 6.4 mediante la instalación del paquete Compatibilidad](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Añada compatibilidad con los recursos de AEM Forms 6.3 y 6.2 en AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Después de realizar una actualización, haga lo siguiente para instalar el paquete de compatibilidad de AEMFD y hacer que sus recursos sean compatibles con la versión 6.4:

Asegúrese de que tiene preinstalado el [paquete de compatibilidad de AEM](/help/sites-deploying/backward-compatibility.md).

1. Instale el [Paquete de compatibilidad](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=es).

   Para obtener más información sobre cómo cargar e instalar el paquete, consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md).

1. Una vez estabilizados los registros, reinicie el servidor.
1. Utilice la utilidad de migración para hacer que los recursos sean compatibles con la versión 6.4.

   Para obtener más información, consulte [utilidad de migración](/help/forms/using/migration-utility.md).

## Recursos compatibles con AEM Forms 6.4 mediante la instalación del paquete Compatibilidad {#assetsmadecompatible}

Al instalar el paquete Compatibilidad, puede hacer que los siguientes recursos y plantillas sean compatibles con AEM Forms 6.4:

* Recursos de Administración de correspondencia de AEM 6.3 y anteriores

   * [Cartas](/help/forms/using/create-letter.md)
   * [Diccionarios de datos](/help/forms/using/data-dictionary.md)
   * Fragmentos de documento

* Plantillas de formularios adaptables obsoletas

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Páginas obsoletas de formularios adaptables:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
