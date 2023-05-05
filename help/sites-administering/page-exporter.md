---
title: El Exportador de páginas
seo-title: The Page Exporter
description: Aprenda a utilizar el Exportador de páginas AEM.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# El Exportador de páginas{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM permite exportar una página como una página web completa que incluye imágenes, archivos .js y .css.

Una vez configurada la exportación, solo tiene que solicitar una página en el navegador reemplazando `html` con `export.zip` en la dirección URL y obtendrá una descarga de archivo zip que contiene la página representada en formato html y los recursos a los que se hace referencia. Todas las rutas de la página, como las rutas a las imágenes, se reescriben para que apunten a los archivos incluidos en el archivo zip o a los recursos del servidor.

## Exportación de una página {#exporting-a-page}

Los siguientes pasos describen cómo exportar una página y suponen que existe una plantilla de configuración de exportación para el sitio. Una plantilla de configuración define la forma en que se exporta una página y es específica del sitio. Para crear una plantilla de configuración, consulte [Creación de una configuración del exportador de páginas para su sitio](#creating-a-page-exporter-configuration-for-your-site) para obtener más información.

Para exportar una página:

1. En el explorador, abra la página . Por ejemplo:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Abra el cuadro de diálogo de propiedades de página y seleccione la opción **Avanzadas** y expanda la **Exportar** conjunto de campos.

1. Haga clic en el icono de lupa y seleccione una plantilla de configuración. Seleccione el **geometrixx** plantilla, ya que es la predeterminada para el sitio de Geometrixx. Haga clic en **Aceptar**.

1. Haga clic en **OK** para cerrar el cuadro de diálogo de propiedades de la página.
1. Solicite la página reemplazando `html` con `export.zip` en la dirección URL.

1. Descargue el `<page-name>.export.zip` al sistema de archivos.

1. En su sistema de archivos, descomprima el archivo:

   * el archivo html de la página ( `<page-name>.html`) está disponible a continuación `<unzip-dir>/<page-path>`
   * otros recursos ( archivos .js, archivos .css, imágenes, ...) se encuentran según la configuración de la plantilla de exportación. En este ejemplo, algunos recursos se encuentran a continuación `<unzip-dir>/etc`, algunos más abajo `<unzip-dir>/<page-path>`.

1. Abra el archivo html de la página ( `<unzip-dir>/<page-path>.html`) en el navegador para comprobar la renderización.

## Creación de una configuración del exportador de páginas para su sitio {#creating-a-page-exporter-configuration-for-your-site}

El exportador de páginas se basa en el marco de sincronización de contenido. Las configuraciones disponibles en el cuadro de diálogo de propiedades de página son plantillas de configuración. Definen todas las dependencias necesarias para una página. Cuando se activa una exportación de página, se utiliza la plantilla de configuración y tanto la ruta de página como la ruta de diseño se aplican de forma dinámica a la configuración. A continuación, el archivo zip se crea mediante la funcionalidad estándar de sincronización de contenido.

AEM incrusta algunas plantillas, entre ellas:

* Una predeterminada en `/etc/contentsync/templates/default`. Esta plantilla:

   * Es la plantilla de reserva cuando no se encuentra ninguna plantilla de configuración en el repositorio.
   * Puede servir de base para una nueva plantilla de configuración.

* Una que esté dedicada al **Geometrixx** sitio, en `/etc/contentsync/templates/geometrixx`. Esta plantilla se puede utilizar como ejemplo para crear una nueva.

Para crear una plantilla de configuración de exportador de páginas:

1. En **CRXDE Lite**, cree un nodo a continuación `/etc/contentsync/templates`:

   * Nombre: p. ej. `mysite`. El nombre aparece en el cuadro de diálogo de propiedades de la página al elegir la plantilla de exportador de páginas.
   * Tipo: `nt:unstructured`

1. Debajo del nodo de plantilla, llamado aquí `mysite`, cree una estructura de nodos utilizando los nodos de configuración que se describen a continuación.

### Nodos de configuración del Exportador de páginas {#page-exporter-configuration-nodes}

La plantilla de configuración consta de una estructura de nodos. Cada nodo tiene un `type` que define una acción específica en el proceso de creación del archivo zip. Para obtener más información sobre la propiedad type , consulte la sección Información general sobre los tipos de configuración en la página del marco de sincronización de contenido .

Los siguientes nodos se pueden utilizar para crear una plantilla de configuración de exportación:

**nodo de página** El nodo de página se utiliza para copiar el html de la página en el archivo zip. Tiene las siguientes características:

* Es un nodo obligatorio.
* Se encuentra a continuación `/etc/contentsync/templates/<sitename>`.
* Su nombre es `page`.
* Su tipo de nodo es `nt:unstructured`

La variable `page` tiene las siguientes propiedades:

* A `type` propiedad establecida con el valor `pages`.

* No tiene un `path` como la ruta de página actual se copia dinámicamente en la configuración.

* Las demás propiedades se describen en la sección Información general sobre tipos de configuración del marco de sincronización de contenido .

**nodo de reescritura** El nodo de reescritura define cómo se reescriben los vínculos en la página exportada. Los vínculos reescritos pueden apuntar a los archivos incluidos en el archivo zip o a los recursos del servidor.

Consulte la página Sincronización de contenido para obtener una descripción completa del `rewrite` nodo .

**nodo de diseño** El nodo de diseño se utiliza para copiar el diseño utilizado para la página exportada. Tiene las siguientes características:

* Es opcional.
* Se encuentra a continuación `/etc/contentsync/templates/<sitename>`.
* Su nombre es `design`.
* Su tipo de nodo es `nt:unstructured`.

La variable `design` tiene las siguientes propiedades:

* A `type` propiedad establecida en el valor `copy`.

* No tiene un `path` como la ruta de página actual se copia dinámicamente en la configuración.

**nodo genérico** Se utiliza un nodo genérico para copiar recursos como los archivos clientlibs.js o .css en el archivo zip. Tiene las siguientes características:

* Es opcional.
* Se encuentra a continuación `/etc/contentsync/templates/<sitename>`.
* No tiene un nombre específico.
* Su tipo de nodo es `nt:unstructured`.
* Tiene un `type` propiedad y `type` propiedades relacionadas, tal como se definen en la sección Información general sobre tipos de configuración del marco de sincronización de contenido.

Por ejemplo, el siguiente nodo de configuración copia los archivos clientlibs.js de geometrixx en el archivo zip:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

La variable **Geometrixx** la plantilla de configuración de exportación de página muestra cómo se puede configurar una exportación de página. Para ver la estructura de nodos de la plantilla en el explorador como formato json, solicite la siguiente URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementación de una configuración personalizada**

Como puede haber notado en la estructura de nodos, la variable **Geometrixx** la plantilla de configuración de exportación de página tiene un `logo` nodo con un `type` propiedad establecida en `image`. Se trata de un tipo de configuración especial que se ha creado para copiar el logotipo de la imagen en el archivo zip. Para satisfacer algunos requisitos específicos, es posible que necesite implementar una variable `type` propiedad: para ello, consulte la sección Implementación de un controlador de actualización personalizado en la página Sincronización de contenido .

## Exportación mediante programación de una página {#programmatically-exporting-a-page}

Para exportar una página mediante programación, puede usar la variable [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) Servicio OSGI. Este servicio le permite:

* Exporte una página y escriba la respuesta del servlet HTTP.
* Exporte una página y guarde el archivo zip en una ubicación específica.

El servlet que está enlazado al `export` y `zip` utiliza el servicio PageExporter.

## Solución de problemas {#troubleshooting}

Si tiene algún problema con la descarga del archivo zip, puede eliminar la variable `/var/contentsync` en el repositorio y vuelva a enviar la solicitud de exportación.
