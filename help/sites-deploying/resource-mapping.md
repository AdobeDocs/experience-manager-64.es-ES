---
title: Asignación de recursos
seo-title: Resource Mapping
description: Aprenda a definir redirecciones, direcciones URL de vanidad y hosts virtuales para AEM mediante la asignación de recursos.
seo-description: Learn how to define redirects, vanity URLs and virtual hosts for AEM by using resource mapping.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 6%

---

# Asignación de recursos{#resource-mapping}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La asignación de recursos se utiliza para definir redirecciones, direcciones URL de vanidad y hosts virtuales para AEM.

Por ejemplo, puede utilizar estas asignaciones para:

* Agregue a todas las solicitudes el prefijo `/content` de modo que la estructura interna se oculte a los visitantes del sitio web.
* Defina una redirección para que todas las solicitudes a la variable `/content/en/gateway` se redireccionan a `https://gbiv.com/`.

Una posible asignación HTTP [prefiere todas las solicitudes a localhost:4503 con /content](#configuring-an-internal-redirect-to-content). Una asignación como esta podría utilizarse para ocultar la estructura interna de los visitantes al sitio web, ya que permite:

`localhost:4503/content/geometrixx/en/products.html`

para acceder a través de:

`localhost:4503/geometrixx/en/products.html`

ya que la asignación agregará automáticamente el prefijo `/content` a `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Las URL mnemónicas no admiten patrones regex.

>[!NOTE]
>
>Consulte la documentación de Sling y [Asignaciones para la resolución de recursos](https://sling.apache.org/site/resources.html) y [Recursos](https://sling.apache.org/site/mappings-for-resource-resolution.html) para obtener más información.

## Visualización de definiciones de asignación {#viewing-mapping-definitions}

Las asignaciones forman dos listas que el JCR Resource Resolver evalúa (de arriba abajo) para encontrar una coincidencia.

Estas listas se pueden ver (junto con la información de configuración) en la sección **JCR ResourceResolver** de la consola Felix; por ejemplo, `https://<host>:<port>/system/console/jcrresolver`:

* Configuración

   Muestra la configuración actual (tal como se define para la variable [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Prueba de configuración

   Esto le permite introducir una dirección URL o una ruta de recurso. Haga clic en **Resolver** o **Mapa** para confirmar cómo el sistema transformará la entrada.

* **Resolver entradas de mapa**
La lista de entradas que utilizan los métodos ResourceResolver.resolve para asignar direcciones URL a los recursos.

* **Asignación de entradas de mapa**
Lista de entradas que utilizan los métodos ResourceResolver.map para asignar rutas de recursos a direcciones URL.

Las dos listas muestran varias entradas, incluidas las definidas como predeterminadas por las aplicaciones. A menudo tienen como objetivo simplificar las direcciones URL del usuario.

El par de listas a **Patrón**, una expresión regular que coincide con la solicitud, con un **Sustitución** que define la redirección que se va a imponer.

Por ejemplo, el:

**Patrón** `^[^/]+/[^/]+/welcome$`

déclencheur de:

**Sustitución** `/libs/cq/core/content/welcome.html`.

para redirigir una solicitud:

`http://localhost:4503/welcome`

hasta:

`http://localhost:4503/libs/cq/core/content/welcome.html`

Se crean nuevas definiciones de asignación dentro del repositorio.

>[!NOTE]
>
>Hay muchos recursos disponibles que ayudan a explicar cómo definir expresiones regulares; por ejemplo [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Creación de definiciones de asignación en AEM {#creating-mapping-definitions-in-aem}

En una instalación estándar de AEM puede encontrar la carpeta :

`/etc/map/http`

Esta es la estructura que se utiliza al definir asignaciones para el protocolo HTTP. Otras carpetas ( `sling:Folder`) se puede crear en `/etc/map` para cualquier otro protocolo que desee asignar.

### Configuración de una redirección interna a /content {#configuring-an-internal-redirect-to-content}

Para crear la asignación que prefiere cualquier solicitud a http://localhost:4503/ con `/content`:

1. Con CRXDE, vaya a `/etc/map/http`.

1. Cree un nuevo nodo:

   * **Tipo** `sling:Mapping`

      Este tipo de nodo está diseñado para estas asignaciones, aunque su uso no es obligatorio.

   * **Nombre** `localhost_any`

1. Haga clic en **Guardar todo**.
1. **Agregar** las siguientes propiedades para este nodo:

   * **Nombre** `sling:match`

      * **Tipo** `String`
      * **Valor** `localhost.4503/`
   * **Nombre** `sling:internalRedirect`

      * **Tipo** `String`
      * **Valor** `/content/`


1. Haga clic en **Guardar todo**.

Esto administrará una solicitud como:\
`localhost:4503/geometrixx/en/products.html`\
como si:\
`localhost:4503/content/geometrixx/en/products.html`\
se ha solicitado.

>[!NOTE]
>
>Consulte [Recursos](https://sling.apache.org/site/mappings-for-resource-resolution.html) en la documentación de Sling para obtener más información sobre las propiedades de Sling disponibles y cómo se pueden configurar.

>[!NOTE]
>
>Puede usar `/etc/map.publish` para guardar las configuraciones del entorno de publicación. Estos deben replicarse y la nueva ubicación ( `/etc/map.publish`) configurado para la variable **Ubicación de asignación** del [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) del entorno de publicación.
