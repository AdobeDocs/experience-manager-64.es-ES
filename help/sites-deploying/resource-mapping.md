---
title: Asignación de recursos
seo-title: Asignación de recursos
description: Obtenga información sobre cómo definir redirecciones, direcciones URL personales y hosts virtuales para AEM mediante la asignación de recursos.
seo-description: Obtenga información sobre cómo definir redirecciones, direcciones URL personales y hosts virtuales para AEM mediante la asignación de recursos.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
translation-type: tm+mt
source-git-commit: c4ac10736c937198aa0c81ecf547dd489ef93366
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---


# Asignación de recursos{#resource-mapping}

La asignación de recursos se utiliza para definir redirecciones, direcciones URL personales y hosts virtuales para AEM.

Por ejemplo, puede utilizar estas asignaciones para:

* Prefijo todas las solicitudes con `/content` el fin de que la estructura interna esté oculta de los visitantes al sitio web.
* Defina un redireccionamiento para que todas las solicitudes a la `/content/en/gateway` página del sitio web se redirijan a `https://gbiv.com/`.

Una asignación HTTP posible [antepone todas las solicitudes a localhost:4503 con /content](#configuring-an-internal-redirect-to-content). Una asignación como esta podría utilizarse para ocultar la estructura interna de los visitantes al sitio web, ya que permite:

`localhost:4503/content/geometrixx/en/products.html`

para acceder a ellos mediante:

`localhost:4503/geometrixx/en/products.html`

ya que la asignación agregará automáticamente el prefijo `/content` a `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Las direcciones URL de vanidad no admiten patrones regex.

>[!NOTE]
>
>Consulte la documentación de Sling y [Asignaciones para Resolución](https://sling.apache.org/site/resources.html) de recursos y [Recursos](https://sling.apache.org/site/mappings-for-resource-resolution.html) para obtener más información.

## Visualización de definiciones de asignación {#viewing-mapping-definitions}

Las asignaciones forman dos listas que el Resueltor de recursos JCR evalúa (de arriba abajo) para encontrar una coincidencia.

Estas listas se pueden ver (junto con la información de configuración) en la opción **JCR ResourceResolver** de la consola Félix; por ejemplo, `https://<host>:<port>/system/console/jcrresolver`:

* Configuración

   Muestra la configuración actual (tal como se define para [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Prueba de configuración

   Esto le permite introducir una dirección URL o ruta de recursos. Haga clic en **Resolver** o **Mapa** para confirmar cómo el sistema transformará la entrada.

* **Entradas** de asignación de resoluciónLa lista de entradas utilizadas por los métodos ResourceResolver.resolve para asignar direcciones URL a recursos.

* **Asignación de Entradas** de Mapalista de las entradas utilizadas por los métodos ResourceResolver.map para asignar rutas de recursos a direcciones URL.

Las dos listas muestran varias entradas, incluidas las definidas como predeterminadas por las aplicaciones. Estos suelen tener como objetivo simplificar las direcciones URL del usuario.

Las listas emparejan un **patrón**, una expresión regular que coincide con la solicitud, con un **reemplazo** que define la redirección que se va a imponer.

Por ejemplo:

**Patrón** `^[^/]+/[^/]+/welcome$`

activará el:

**Reemplazo** `/libs/cq/core/content/welcome.html`.

para redirigir una solicitud:

`http://localhost:4503/welcome`

hasta:

`http://localhost:4503/libs/cq/core/content/welcome.html`

Se crean nuevas definiciones de asignación dentro del repositorio.

>[!NOTE]
>
>Hay muchos recursos disponibles que ayudan a explicar cómo definir las expresiones ordinarias; por ejemplo, [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Creación de definiciones de asignación en AEM {#creating-mapping-definitions-in-aem}

En una instalación estándar de AEM puede encontrar la carpeta:

`/etc/map/http`

Esta es la estructura que se utiliza al definir asignaciones para el protocolo HTTP. Se pueden crear otras carpetas ( `sling:Folder`) en `/etc/map` para cualquier otro protocolo que desee asignar.

### Configuración de una redirección interna a /content {#configuring-an-internal-redirect-to-content}

Para crear la asignación que prefiera cualquier solicitud a http://localhost:4503/ con `/content`:

1. Con CRXDE vaya a `/etc/map/http`.

1. Crear un nuevo nodo:

   * **Tipo** `sling:Mapping`

      Este tipo de nodo está diseñado para estas asignaciones, aunque su uso no es obligatorio.

   * **Nombre** `localhost_any`

1. Haga clic en **Guardar todo**.
1. **Añada** las siguientes propiedades a este nodo:

   * **Nombre** `sling:match`

      * **Tipo** `String`
      * **Valor** `localhost.4503/`
   * **Nombre** `sling:internalRedirect`

      * **Tipo** `String`
      * **Valor** `/content/`


1. Haga clic en **Guardar todo**.

Esto gestionará una solicitud como:\
`localhost:4503/geometrixx/en/products.html`\
como si:\
`localhost:4503/content/geometrixx/en/products.html`\
se ha solicitado.

>[!NOTE]
>
>Consulte [Recursos](https://sling.apache.org/site/mappings-for-resource-resolution.html) en la documentación de Sling para obtener más información sobre las propiedades de sling disponibles y cómo se pueden configurar.

>[!NOTE]
>
>Puede utilizar `/etc/map.publish` para mantener las configuraciones del entorno de publicación. Estos deben replicarse y la nueva ubicación ( `/etc/map.publish`) debe configurarse para la ubicación **de** asignación de la resolución [de recursos de sling de](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) Apache del entorno de publicación.

