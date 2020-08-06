---
title: Seguridad
seo-title: Seguridad
description: inicios de seguridad de las aplicaciones durante la fase de desarrollo
seo-description: inicios de seguridad de las aplicaciones durante la fase de desarrollo
uuid: efd5f3bc-da07-4fc8-a6ce-f1e6f5084c9e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: d2267663-6c1d-413c-9862-e82e21ae6906
translation-type: tm+mt
source-git-commit: 0fb4d181b700e223becfee8e3e68a84d6f964c1d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Seguridad{#security}

inicios de seguridad de la aplicación durante la fase de desarrollo. Adobe recomienda aplicar las siguientes optimizaciones de seguridad.

## Usar sesión de solicitud {#use-request-session}

Siguiendo el principio de privilegios de leas, Adobe recomienda que cada acceso al repositorio se realice utilizando la sesión vinculada a la solicitud del usuario y el control de acceso adecuado.

## Protect contra scripts entre sitios (XSS) {#protect-against-cross-site-scripting-xss}

La secuencia de comandos entre sitios (XSS) permite a los atacantes insertar código en páginas web vistas por otros usuarios. Esta vulnerabilidad de seguridad puede ser aprovechada por usuarios web malintencionados para evitar controles de acceso.

AEM aplica el principio de filtrar todo el contenido proporcionado por el usuario durante la salida. La prevención de XSS recibe la máxima prioridad durante el desarrollo y las pruebas.

El mecanismo de protección XSS proporcionado por AEM se basa en la biblioteca [Java](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) AntiSamy proporcionada por [OWASP (Proyecto de seguridad de Aplicación web abierta)](https://www.owasp.org/). La configuración predeterminada de AntiSamy se encuentra en

`/libs/cq/xssprotection/config.xml`

Es importante adaptar esta configuración a sus propias necesidades de seguridad mediante la superposición del archivo de configuración. La documentación [oficial de](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) AntiSamy le proporcionará toda la información necesaria para implementar sus requisitos de seguridad.

>[!NOTE]
>
>Le recomendamos encarecidamente que siempre acceda a la API de protección XSS mediante el uso del [XSSAPI proporcionado por AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html).

Además, un servidor de seguridad de aplicaciones web, como [mod_security para Apache](https://www.modsecurity.org), puede proporcionar un control centralizado y fiable sobre la seguridad del entorno de implementación y protegerse contra ataques de secuencias de comandos entre sitios no detectados previamente.

## Acceso a la información del Cloud Service {#access-to-cloud-service-information}

>[!NOTE]
>
>Las ACL para la información del Cloud Service, así como la configuración de OSGi necesaria para proteger la instancia, se automatizan como parte del modo [de preparación para la](/help/sites-administering/production-ready.md)producción. Aunque esto significa que no necesita realizar los cambios de configuración manualmente, se recomienda revisarlos antes de empezar a implementar la implementación.

Al [integrar la instancia de AEM con el Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md) , se utilizan configuraciones [de](/help/sites-developing/extending-cloud-config.md)Cloud Service. La información sobre estas configuraciones, junto con las estadísticas recopiladas, se almacenan en el repositorio. Recomendamos que, si utiliza esta funcionalidad, revise si la seguridad predeterminada de esta información coincide con sus necesidades.

El módulo webservicesupport escribe estadísticas e información de configuración en:

`/etc/cloudservices`

Con los permisos predeterminados:

* entorno del autor: `read` for `contributors`

* entorno de publicación: `read` for `everyone`

## Protect contra ataques de falsificación de solicitudes entre sitios {#protect-against-cross-site-request-forgery-attacks}

Para obtener más información sobre los mecanismos de seguridad que AEM emplea para mitigar los ataques de CSRF, consulte la sección Filtro [de Remitente del reenvío](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) Sling de la lista de comprobación de seguridad y la documentación [del](/help/sites-developing/csrf-protection.md)CSRF sobre el marco de protección.