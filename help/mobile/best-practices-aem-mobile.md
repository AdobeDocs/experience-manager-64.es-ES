---
title: Prácticas recomendadas
seo-title: Best Practices
description: Siga esta página para conocer las prácticas recomendadas y las directrices que ayudarán a los desarrolladores experimentados de AEM para sitios, que desean crear plantillas y componentes para aplicaciones móviles.
seo-description: Follow this page to  learn best practices and guidelines that will help experienced AEM developers for sites, who want to build mobile app templates and components.
uuid: 7733c8b1-a88c-455c-8080-f7add4205b92
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a0647696-72c3-409b-85ba-9275d8f99cff
exl-id: 042974ee-2c0a-411d-accf-6a17b8e95f90
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 2%

---

# Prácticas recomendadas {#best-practices}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe recomienda utilizar el Editor de SPA para proyectos que requieren una representación del lado del cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

La creación de una aplicación de AEM Mobile On-demand Services es diferente a la creación de una aplicación que se ejecuta directamente en el shell de Cordova (o PhoneGap). Los desarrolladores deben estar familiarizados con lo siguiente:

* Los complementos compatibles de serie, así como los complementos específicos de AEM Mobile.

>[!NOTE]
>
>Para obtener información detallada sobre los complementos, consulte los siguientes recursos:
>
>* [Uso de complementos de Cordova en AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [Uso de complementos específicos de AEM Mobile habilitados para Cordova](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>


* Las plantillas que utilizan la funcionalidad de complemento deben escribirse de forma que puedan seguir utilizándose en el explorador, sin que el puente del complemento esté presente.

   * Por ejemplo, asegúrese de esperar a que *deviceready* antes de intentar acceder a la API de un complemento.

## Directrices para desarrolladores de AEM {#guidelines-for-aem-developers}

Las siguientes directrices ayudarán a los desarrolladores experimentados de AEM para sitios que deseen crear plantillas y componentes de aplicaciones móviles:

**Estructura AEM plantillas de sitios para fomentar la reutilización y la extensibilidad**

* Preferir varios archivos de script de componente sobre uno solo y monolítico

   * Se proporcionan varios puntos de extensión vacíos, como *customheaderlibs.html* y *customfooterlibs.html*, que permiten al desarrollador cambiar la plantilla de página duplicando el menor código principal posible
   * Las plantillas se pueden ampliar y personalizar mediante Sling *sling:resourceSuperType* mecanismo

* Preferir Sightly/HTL sobre JSP como idioma de plantilla

   * El uso de esto fomenta una separación del código del marcado, ofrece una protección XSS integrada y tiene una sintaxis más familiar

**Optimizar para el rendimiento en dispositivos**

* La secuencia de comandos específica del artículo y las hojas de estilo deben incluirse en la carga útil del artículo, utilizando la plantilla contentsync dps-article
* Las hojas de estilo y el script compartidos por más de un artículo deben incluirse en los recursos compartidos, a través de la plantilla dps-HTMLResources contentsync
* No haga referencia a ninguna secuencia de comandos externa que sea un bloqueo de procesamiento

>[!NOTE]
>
>Puede obtener más información detallada sobre los scripts externos de bloqueo de renderización [here](https://developers.google.com/speed/docs/insights/BlockingJS).

**Prefiera las bibliotecas JS y CSS específicas de la aplicación sobre las específicas de la web**

* Para evitar sobrecargas en bibliotecas como jQuery Mobile para gestionar una gran variedad de dispositivos y navegadores
* Cuando una plantilla se ejecuta en la vista web de una aplicación, usted tiene control sobre las plataformas y versiones que la aplicación va a admitir, así como también el conocimiento de que estará presente el soporte de JavaScript. Por ejemplo, prefiera Ionic (quizá solo el CSS) sobre la interfaz de usuario de jQuery Mobile y Onsen en lugar del Bootstrap.

>[!NOTE]
>
>Para obtener más información sobre jQuery mobile, haga clic en [here](https://jquerymobile.com/browser-support/1.4/).

**Preferir microbibliotecas sobre pilas completas**

* El tiempo que tarda en poner el contenido en la copa del dispositivo se verá ralentizado por cada biblioteca de la que dependan sus artículos. Esta ralentización se agrava cuando se utiliza una nueva vista web para procesar cada artículo, por lo que cada biblioteca debe volver a inicializarse desde cero
* Si los artículos no se crean como SPA (aplicaciones de una sola página), probablemente no necesite incluir una biblioteca de pila completa como Angular
* Prefiera bibliotecas de un solo propósito más pequeñas para ayudar a agregar la interactividad que requiere su página, como [Fastclick](https://github.com/ftlabs/fastclick) o [Velocity.js](https://velocityjs.org)

**Minimizar el tamaño de la carga útil del artículo**

* Utilice los recursos más pequeños posibles que puedan cubrir eficazmente la ventanilla más grande que admita, con una resolución razonable
* Utilice una herramienta como *ImageOptim* en las imágenes para eliminar cualquier exceso de metadatos

## Cómo avanzar {#getting-ahead}

Para obtener más información sobre las otras dos funciones y responsabilidades, consulte los recursos siguientes:

* [Administrador](/help/mobile/aem-mobile.md)
* [Autor](/help/mobile/aem-mobile-on-demand.md)
