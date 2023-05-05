---
title: Externalización de direcciones URL
seo-title: Externalizing URLs
description: Externalizer es un servicio OSGI que le permite transformar mediante programación una ruta de recurso en una URL externa y absoluta
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# Externalización de direcciones URL{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En AEM, la variable **Externalizador** es un servicio OSGI que le permite transformar mediante programación una ruta de recursos (p. ej. `/path/to/my/page`) en una dirección URL externa y absoluta (por ejemplo, `https://www.mycompany.com/path/to/my/page`) añadiendo un prefijo a la ruta con un DNS preconfigurado.

Dado que una instancia no puede conocer su URL visible externamente si se está ejecutando detrás de una capa web y porque a veces se debe crear un vínculo fuera del ámbito de la solicitud, este servicio proporciona un lugar central para configurar esas URL externas y crearlas.

Esta página explica cómo configurar la variable **Externalizador** y cómo utilizarlo. Para obtener más información, consulte la [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configuración del servicio externalizador {#configuring-the-externalizer-service}

La variable **Externalizador** permite definir de forma centralizada varios dominios que se pueden utilizar para prefijar programáticamente las rutas de recursos. Cada dominio se identifica con un nombre único que se utiliza para hacer referencia al dominio mediante programación.

Para definir una asignación de dominio para la variable **Externalizador** servicio:

1. Vaya al administrador de configuración a través de **Herramientas**, luego **Consola web** o introduzca `https://<host>:<port>/system/console/configMgr.`
1. Haga clic en **Externalizador de vínculos de CQ de día** para abrir el cuadro de diálogo de configuración.

   >[!NOTE]
   >
   >El vínculo directo a la configuración es `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![imagen_1-44](assets/chlimage_1-44.png)

1. Defina una asignación de dominio: una asignación consiste en un nombre único que puede utilizarse en el código para hacer referencia al dominio, un espacio y el dominio:

   `<unique-name> [scheme://]server[:port][/contextpath]`, donde:

   * **esquema** generalmente es http o https, pero también puede ser ftp, etc.; utilice https para aplicar los vínculos https si lo desea; se utilizará si el código de cliente no anula el esquema al solicitar la externalización de una URL.
   * **server** es el nombre de host (puede ser un nombre de dominio o una dirección ip).
   * **puerto** (opcional) es el número de puerto.
   * **contextpath** (opcional) solo se establece si AEM está instalado como una aplicación web en una ruta de contexto diferente.

   Por ejemplo: `production https://my.production.instance`

   Los siguientes nombres de asignación están predefinidos y siempre deben configurarse como AEM dependen de ellos:

   * **local** : la instancia local
   * **author** - el DNS del sistema de creación
   * **publicar** - el sitio web DNS de cara al público

   >[!NOTE]
   >
   >Una configuración personalizada le permite agregar una nueva categoría, como &quot;producción&quot;, &quot;ensayo&quot; o incluso sistemas externos que no sean AEM, como &quot;my-internal-webservice&quot;, y resulta útil para evitar codificar dichas direcciones URL en diferentes lugares de la base de código de un proyecto.

1. Haga clic en **Guardar** para guardar los cambios.

>[!NOTE]
>
>Adobe recomienda que [añadir la configuración al repositorio](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Uso del servicio externalizador {#using-the-externalizer-service}

Esta sección muestra algunos ejemplos de cómo se usa la variable **Externalizador** se puede utilizar.

**Para obtener el servicio externalizador en un JSP:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Para externalizar una ruta con el dominio &quot;publicar&quot;:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Asumiendo la asignación de dominios &quot; `publish https://www.website.com`&quot;, myExternalizedUrl termina con el valor &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Para externalizar una ruta con el dominio &quot;autor&quot;:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Asumiendo la asignación de dominios &quot; `author https://author.website.com`&quot;, myExternalizedUrl termina con el valor &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Para externalizar una ruta con el dominio &quot;local&quot;:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Asumiendo la asignación de dominios &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl termina con el valor &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Puede encontrar más ejemplos en la sección [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
