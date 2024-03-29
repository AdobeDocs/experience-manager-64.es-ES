---
title: Creación de una nueva aplicación de AEM Mobile mediante el asistente de creación
seo-title: Creating a new AEM Mobile app using create wizard
description: Las aplicaciones de AEM Mobile se basan en un modelo que define una estructura y propiedades de página. Siga esta página para obtener información sobre cómo crear una nueva aplicación basada en una plantilla de aplicación.
seo-description: AEM Mobile apps are based on a blueprint that defines a page structure and properties. Follow this page to learn about how to create a new app based on an app template.
uuid: c2bd63a5-3dff-4a72-b1fb-0c776e0afa33
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 27605eb7-59b2-42d4-8cc5-02cfa52b4491
exl-id: 79d2dbfb-5e44-4a96-ab9b-ba5d93fc3aae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 2%

---

# Creación de una nueva aplicación de AEM Mobile mediante el asistente de creación{#creating-a-new-aem-mobile-app-using-create-wizard}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe recomienda utilizar el Editor de SPA para proyectos que requieren una representación del lado del cliente basada en el marco de aplicaciones de una sola página (por ejemplo, React). [Más información](/help/sites-developing/spa-overview.md).

Las aplicaciones de AEM Mobile se basan en un modelo que define una estructura y propiedades de página. Puede configurar las siguientes propiedades de aplicación:

* **Título:** El título de la aplicación.
* **Ruta de destino:** Ubicación en el repositorio donde se almacena la aplicación. Deje el valor predeterminado para crear una ruta basada en el nombre de la aplicación.

* **Nombre:** El valor predeterminado es el valor de la propiedad Título con caracteres de espacio eliminados. El nombre se utiliza en AEM para hacer referencia a la aplicación, por ejemplo para el nodo del repositorio que representa la aplicación.
* **Descripción:** Descripción de la aplicación.
* **URL del servidor:** La URL que proporciona actualizaciones de contenido de OTA a la aplicación. El valor predeterminado es la URL del servidor de publicación de la instancia que se utiliza para crear una aplicación (tomada del servicio externalizador). Tenga en cuenta que debe ser una instancia de servidor de publicación en lugar de un autor, que requiere autenticación.

También puede proporcionar un archivo de imagen para utilizarlo como miniatura de la aplicación, seleccionar la configuración de PhoneGap Build que desea utilizar y seleccionar la configuración de análisis de aplicaciones móviles que desea utilizar. Esta imagen solo se utiliza como miniatura para representar la aplicación móvil en la consola de aplicaciones móviles en Experience Manager.

Existen pestañas adicionales (y opcionales) para crear el servicio de nube e integrar el complemento SDK de Adobe Mobile Services en la aplicación.

* Generar: Haga clic en administrar configuraciones y configure el servicio de compilación build.phonegap.com aquí. A continuación, desde la lista desplegable podrá seleccionar el servicio en la nube PhoneGap recién creado.
* Analytics: Haga clic en administrar configuraciones y configure su [SDK de Adobe Mobile Services](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/download-sdk.html) servicio en la nube. A continuación, desde la lista desplegable podrá seleccionar los servicios móviles recién creados para integrarlos en su aplicación móvil.

## Uso de plantillas de aplicación {#using-app-templates}

Las plantillas de aplicación proporcionan una manera sencilla de aprovechar los diseños existentes creados por los desarrolladores y utilizados para la creación de nuevas aplicaciones en AEM.

¿Qué es una plantilla de aplicación? Piense en ella como una colección de plantillas de página y componentes que representan una línea de base o una base de una aplicación.
Al crear una aplicación nueva basada en la plantilla de otra aplicación, obtendrá una aplicación que tenga un punto de partida representativo de la aplicación desde la que se creó.

Debe tener una plantilla de aplicación móvil existente (o una aplicación instalada que tenga una plantilla de aplicación) para poder usar esta función.

El último paquete de ejemplos de aplicaciones de AEM incluye una versión actualizada de la aplicación de Geometrixx con una plantilla de aplicación. También puede instalar el [StarterKit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) que también proporciona una plantilla.

Pasos para crear una aplicación nueva basada en una plantilla de aplicación:

1. Vaya al catálogo de aplicaciones de AEM Mobile: &lt;*server-url*>aem/apps.html/content/mobileapps
1. Select **Crear** y, a continuación, elija **Aplicación** como se muestra a continuación

![chlimage_1-158](assets/chlimage_1-158.png)

Seleccione una plantilla de aplicación que haya puesto a su disposición un desarrollador de AEM. Consulte [Estructura de una aplicación de AEM Mobile](/help/mobile/phonegap-structure-an-app.md) para obtener ayuda al desarrollador.

![chlimage_1-159](assets/chlimage_1-159.png)

Complete los detalles de la nueva aplicación según sea necesario, incluido el cambio opcional de su imagen en miniatura. Estos valores se pueden editar posteriormente desde la **Administrar aplicación** mosaico.

![chlimage_1-160](assets/chlimage_1-160.png)

## Pasos siguientes {#the-next-steps}

Consulte los siguientes recursos para obtener más información sobre otras funciones de creación:

* [El mosaico Administrar aplicación](/help/mobile/phonegap-app-details-tile.md)
* [Edición de metadatos de aplicaciones](/help/mobile/phonegap-editmetadata.md)
* [Definiciones de aplicaciones](/help/mobile/phonegap-app-definitions.md)
* [Importar una aplicación híbrida existente](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

## Recursos adicionales {#additional-resources}

Para obtener más información sobre las funciones y responsabilidades de un administrador y desarrollador, consulte los siguientes recursos:

* [Desarrollo para Adobe PhoneGap Enterprise con AEM](/help/mobile/developing-in-phonegap.md)
* [Administración de contenido para Adobe PhoneGap Enterprise con AEM](/help/mobile/administer-phonegap.md)
