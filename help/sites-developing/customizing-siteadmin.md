---
title: Personalización de la consola Sitios web (IU clásica)
seo-title: Customizing the Websites Console (Classic UI)
description: La consola Administración de sitios web se puede ampliar para mostrar columnas personalizadas
seo-description: The Websites Administration console can be extended to display custom columns
uuid: 7587d026-f974-46fe-bac3-3872d3a083ab
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 73e57f20-4022-46ab-aa5c-ec866298b645
exl-id: c7e37599-0712-44cf-8191-d444d12f95c4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 1%

---

# Personalización de la consola Sitios web (IU clásica){#customizing-the-websites-console-classic-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Adición de una columna personalizada a la consola Siteadmin (Siteadmin) {#adding-a-custom-column-to-the-websites-siteadmin-console}

La consola Administración de sitios web se puede ampliar para mostrar columnas personalizadas. La consola se basa en un objeto JSON que se puede ampliar creando un servicio OSGI implementando el `ListInfoProvider` interfaz. Este servicio modifica el objeto JSON que se envía al cliente para crear la consola.

Este tutorial paso a paso explica cómo mostrar una nueva columna en la consola de administración de sitios web implementando el `ListInfoProvider` interfaz. Consiste en los siguientes pasos:

1. [Creación del servicio OSGI](#creating-the-osgi-service) e implementación del paquete que lo contiene en el servidor AEM.
1. (opcional) [Prueba del nuevo servicio](#testing-the-new-service) emitiendo una llamada JSON para solicitar el objeto JSON que se utiliza para crear la consola.
1. [Visualización de la nueva columna](#displaying-the-new-column) ampliando la estructura de nodos de la consola en el repositorio.

>[!NOTE]
>
>Este tutorial también se puede utilizar para ampliar las siguientes consolas de administración:
>
>* la consola Recursos digitales
>* la consola Community
>


### Creación del servicio OSGI {#creating-the-osgi-service}

La variable `ListInfoProvider` La interfaz define dos métodos:

* `updateListGlobalInfo`, para actualizar las propiedades globales de la lista,
* `updateListItemInfo`, para actualizar un solo elemento de lista.

Los argumentos para ambos métodos son:

* `request`, el objeto de solicitud HTTP de Sling asociado,
* `info`, el objeto JSON que se va a actualizar, que es, respectivamente, la lista global o el elemento de lista actual,
* `resource`, un recurso de Sling.

La implementación de muestra a continuación:

* Añade un *starred* para cada elemento, que es `true` si el nombre de la página empieza por un *e* y `false` en caso contrario.

* Añade un *starredCount* , que es global para la lista y contiene el número de elementos de la lista de inicio.

Para crear el servicio OSGI:

1. En CRXDE Lite, [crear un paquete](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
1. Agregue el código de muestra siguiente.
1. Construya el paquete.

El nuevo servicio está funcionando.

```java
package com.test;

import com.day.cq.commons.ListInfoProvider;
import com.day.cq.i18n.I18n;
import com.day.cq.wcm.api.Page;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

@Component(metatype = false)
@Service(value = ListInfoProvider.class)
public class StarredListInfoProvider implements ListInfoProvider {

    private int count = 0;

    public void updateListGlobalInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        info.put("starredCount", count);
        count = 0; // reset for next execution
    }

    public void updateListItemInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        Page page = resource.adaptTo(Page.class);
        if (page != null) {
            // Consider starred if page name starts with 'e'
            boolean starred = page.getName().startsWith("e");
            if (starred) {
                count++;
            }
            I18n i18n = new I18n(request);
            info.put("starred", starred ? i18n.get("Yes") : i18n.get("No"));
        }
    }

}
```

>[!CAUTION]
>
>* Su implementación debe decidir, según la solicitud o el recurso proporcionados, si debe añadir o no la información al objeto JSON.
>* Si su `ListInfoProvider` la implementación define una propiedad que ya existe en el objeto Response, cuyo valor será sobrescrito por el que proporcione.\
   >  Puede usar [clasificación del servicio](https://www.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) para administrar el orden de ejecución de varios `ListInfoProvider` implementaciones de .
>


### Prueba del nuevo servicio {#testing-the-new-service}

Cuando abre la consola Administración de sitios web y navega por su sitio, el explorador emite una llamada ajax para obtener el objeto JSON utilizado para crear la consola. Por ejemplo, al navegar hasta el `/content/geometrixx` , se envía la siguiente solicitud al servidor de AEM para crear la consola:

[http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Para asegurarse de que el nuevo servicio se esté ejecutando después de haber implementado el paquete que lo contiene:

1. Apunte el navegador a la siguiente URL:

   [http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](http://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. La respuesta debe mostrar las nuevas propiedades de la siguiente manera:

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### Visualización de la nueva columna {#displaying-the-new-column}

El último paso consiste en adaptar la estructura de nodos de la consola Administración de sitios web para mostrar la nueva propiedad de todas las páginas de Geometrixx superponiendo `/libs/wcm/core/content/siteadmin`. Proceda de la siguiente manera:

1. En el CRXDE Lite, cree la estructura de nodos `/apps/wcm/core/content` con nodos de tipo `sling:Folder` para reflejar la estructura `/libs/wcm/core/content`.

1. Copiar el nodo `/libs/wcm/core/content/siteadmin` y péguelo a continuación `/apps/wcm/core/content`.

1. Copiar el nodo `/apps/wcm/core/content/siteadmin/grid/assets` a `/apps/wcm/core/content/siteadmin/grid/geometrixx` y cambia sus propiedades:

   * Eliminar **pageText**
   * Establezca **pathRegex** a `/content/geometrixx(/.*)?`

      Esto hará que la configuración de cuadrícula esté activa para todos los sitios web de geometrixx.

   * Establezca **storeProxySuffix** a `.pages.json`
   * Edite el **storeReaderFields** propiedad multivalor y agregue la variable `starred` valor.
   * Para activar la funcionalidad MSM, agregue los siguientes parámetros MSM a la propiedad multi-String **storeReaderFields**:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Agregue un `starred` nodo (de tipo **nt:unstructured**) debajo `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` con las siguientes propiedades:

   * **dataIndex**: `starred` de tipo String
   * **header**: `Starred` de tipo String
   * **xtype**: `gridcolumn` de tipo String

1. (opcional) Suelte las columnas que no desee mostrar en `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` es una ruta de vanidad que, de forma predeterminada, señala a `/libs/wcm/core/content/siteadmin`.

   Para redirigir esto a su versión de siteadmin en `/apps/wcm/core/content/siteadmin` definir la propiedad `sling:vanityOrder` tener un valor superior al definido en `/libs/wcm/core/content/siteadmin`. El valor predeterminado es 300, por lo que es adecuado cualquier valor superior.

1. Vaya a la consola Administración de sitios web y vaya al sitio de Geometrixx:

   [http://localhost:4502/siteadmin#/content/geometrixx](http://localhost:4502/siteadmin#/content/geometrixx).

1. La nueva columna denominada **Starred** está disponible y muestra la información personalizada de la siguiente manera:

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Si varias configuraciones de cuadrícula coinciden con la ruta solicitada definida por la variable **pathRegex** , se utilizará la primera, y no la más específica, lo que significa que el orden de las configuraciones es importante.

### Paquete de muestra {#sample-package}

El resultado de este tutorial está disponible en la [Personalización de la consola de administración de sitios web](http://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) paquete en Package Share.
