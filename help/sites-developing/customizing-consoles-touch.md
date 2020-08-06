---
title: Personalización de las consolas
seo-title: Personalización de las consolas
description: AEM proporciona varios mecanismos que le permiten personalizar las consolas de la instancia de creación
seo-description: AEM proporciona varios mecanismos que le permiten personalizar las consolas de la instancia de creación
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
translation-type: tm+mt
source-git-commit: 1dc15f323dc30d5730e2af6c0e762d623523870d
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 1%

---


# Personalización de las consolas{#customizing-the-consoles}

>[!CAUTION]
>
>En este documento se describe cómo personalizar consolas en la IU táctil moderna y no se aplica a la IU clásica.

AEM proporciona varios mecanismos que le permiten personalizar las consolas (y la funcionalidad [de creación de](/help/sites-developing/customizing-page-authoring-touch.md)páginas) de la instancia de creación.

* Clientlibs

   Las bibliotecas de clientes permiten ampliar la implementación predeterminada para obtener una nueva funcionalidad, al mismo tiempo que se reutilizan las funciones, los objetos y los métodos estándar. Al personalizar, puede crear su propia clientlib en `/apps.` Por ejemplo, puede contener el código necesario para el componente personalizado.

* Superposiciones

   Las superposiciones se basan en definiciones de nodos y permiten superponer la funcionalidad estándar (en `/libs`) con su propia funcionalidad personalizada (en `/apps`). Al crear una superposición, no se requiere una copia 1:1 del original, ya que la fusión de recursos de sling permite la herencia.

Estos pueden utilizarse de muchas maneras para ampliar las consolas de AEM. A continuación se incluye una pequeña selección (de alto nivel).

>[!NOTE]
>
>Para obtener más información, consulte:
>
>* Usar y crear [clientlibs](/help/sites-developing/clientlibs.md).
>* Uso y creación de [superposiciones](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)

>
>
Este tema también se trata en la sesión [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html) - Personalización de la interfaz [de usuario para AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).

>[!CAUTION]
>
>No ***debe*** cambiar nada en la `/libs` ruta.
>
>Esto se debe a que el contenido de `/libs` se sobrescribe la próxima vez que actualice la instancia (y es posible que se sobrescriba al aplicar una revisión o un paquete de funciones).
>
>El método recomendado para la configuración y otros cambios es:
>
>1. Volver a crear el elemento requerido (es decir, tal como existe en `/libs`) en `/apps`
   >
   >
1. Realice los cambios en `/apps`

>



Por ejemplo, se pueden superponer las siguientes ubicaciones dentro de la `/libs` estructura:

* consolas (cualquier consola basada en páginas de la interfaz de usuario de Granite); por ejemplo:

   * `/libs/wcm/core/content`

<!-- Needs a review by Engineering -->
<!--
* secondary (inner) rails; for example:

    * `/libs/wcm/core/content/search`

* toolbar(s) (dependent on console; for example sites):

    * default 

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/default`

    * selection mode

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/selection`

* help menu options (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/help`

* information shown on the card view (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/content/content/items/childpages`

-->
>[!NOTE]
>
>Consulte el artículo de la Base de conocimiento, [Resolución de problemas AEM problemas](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)de la IU táctil, para obtener más sugerencias y herramientas.

<!-- Needs a review by Engineering -->
<!--
## Code Samples {#code-samples}

Various packages have been made available on Github. These provide code samples related to the tasks covered on this page.

### aem-admin-extension-new-console {#aem-admin-extension-new-console}

`aem-admin-extension-new-console` is a sample package showing how to [create a new AEM 6 console](#create-a-custom-console). This package provides a UI for managing [Launches](/help/sites-authoring/launches.md) and adds a link in the navigation:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)

### aem-admin-extension-customize-sites {#aem-admin-extension-customize-sites}

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Create a Custom Console {#create-a-custom-console}

1. You can create a custom console with related actions; for example, Launches at the top level (below Sites):

   This involves:

    * creating the root space definition of your new console ``; for example:

        * `/apps/<yourProject>/admin/ext/launches`

    * this can contain (according to requirements):

        * the corresponding [clientlibs](/help/sites-developing/clientlibs.md) for custom actions and `less`/ `css` definitions

            * `/apps/<yourProject>/admin/ext/launches/clientlibs`

        * components that need to be redefined/adjusted; for example, the breadcrumbs, datasource and the launch

            * `/apps/<yourProject>/admin/ext/launches/components`

        * the Granite UI page resource:

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content`

              property: `sling:resourceType`

        * the page definition of the console

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/head`
            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body`

   ![chlimage_1-236](assets/chlimage_1-236.png)

   To use the new console (for example in the [rail for navigation](#add-new-navigation-option-to-rail)) an ID is used, so that it can be explicitly referenced. The ID is used to connect the console and its navigation definition. The ID is defined in the `rail` node of the page; for example, for the Sites console:

    * the rail node is: 

      `/libs/wcm/core/content/sites/jcr:content/body/rail`

        * here the `currentId` property is defined: 

          `currentId` = `cq-sites`

   For the Launches console example:

    * the node is:

        * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`

    * with the following properties:

        * `currentId` = `cq-launches`
        * `sling:resourceType` = `granite/ui/components/endor/navcolumns`
        * `srcPath` = `cq/core/content/nav`
-->

## Personalización de la Vista predeterminada para una consola {#customizing-the-default-view-for-a-console}

Puede personalizar la vista predeterminada (columna, tarjeta, lista) para una consola:

1. Puede reordenar las vistas superponiendo la entrada requerida desde:

   `/libs/wcm/core/content/sites/jcr:content/views`

   La primera entrada será la predeterminada.

   Los nodos disponibles se correlacionan con las opciones de vista disponibles:

   * `column`
   * `card`
   * `list`

1. Por ejemplo, en una superposición para lista:

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Defina la siguiente propiedad:

   * **Nombre**: `sling:orderBefore`
   * **Tipo**: `String`
   * **Valor**: `column`

<!-- Needs a review by Engineering -->
<!--
`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
### Add New Navigation Option to Rail {#add-new-navigation-option-to-rail}

1. You can add a navigation entry in the rail (for example, a [custom console](#create-a-custom-console) such as Launches).

   To do this, you create an overlay of:

   `/libs/cq/core/content/nav`

   In the `/apps` overlay:

   `/apps/cq/core/content/nav`

   Create the new nodes and properties:

   ![chlimage_1-237](assets/chlimage_1-237.png)

    * Extend navigation:

        * `/apps/cq/core/content/nav/launches`

    * Specify location in the tree:

        * property: `sling:orderBefore`

    * To create the connection, the `id` property references (i.e. must be the same as) the `currentID` property [for the appropriate console](#create-a-custom-console):

        * property: `id`
        * value: same as for your console (e.g. `cq-launches`) 

          for example: the same value as the `currentId` property on:

          `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`
-->

## Añadir nueva acción en la barra de herramientas {#add-new-action-to-the-toolbar}

1. Puede crear sus propios componentes e incluir las bibliotecas de cliente correspondientes para acciones personalizadas. Por ejemplo, una acción **Promocionar a Twitter** en:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Esto se puede conectar a un elemento de la barra de herramientas de la consola:

   `/apps/<yourProject>/admin/ext/launches`

   Por ejemplo, en el modo de selección:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## Restringir una acción de la barra de herramientas a un grupo específico {#restrict-a-toolbar-action-to-a-specific-group}

1. Puede utilizar una condición de procesamiento personalizada para superponer la acción estándar e imponer condiciones específicas que deben cumplirse antes de procesarse.

   Por ejemplo, cree un componente para controlar las condiciones de procesamiento según el grupo:

   `/apps/myapp/components/renderconditions/group`

1. Para aplicarlas a la acción Crear sitio en la consola Sitios:

   `/libs/wcm/core/content/sites`

   Cree la superposición:

   `/apps/wcm/core/content/sites`

1. A continuación, agregue la condición de procesamiento para la acción:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Mediante las propiedades de este nodo puede definir el `groups` permiso para realizar la acción específica; por ejemplo, `administrators`

<!-- Needs a review by Engineering -->
<!--
## Remove Access to Navigation Option on Rail {#remove-access-to-navigation-option-on-rail}

1. You can rename a navigation entry in the rail by overlaying the required entry from under:

   `/libs/cq/core/content/nav`

   The nodes available correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`

1. For example, on a overlay at:

   `/apps/cq/core/content/nav/sites`

   Define the following property:

    * **Name**: `sling:hideResource`
    * **Type**: `String` 
    * **Value**: `true`

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Restrict Access to Navigation Option on Rail {#restrict-access-to-navigation-option-on-rail}

You can restrict access to a navigation option using ACLs:

1. Open the [user and/or group management](/help/sites-administering/security.md) and select the user/group you want to restrict access for.

   >[!NOTE]
   >
   >Avoid assigning/restricting permissions on a user-by-user basis. It is [recommended to use groups](/help/sites-administering/security.md#best-practices).

1. Remove access [permissions](/help/sites-administering/security.md#permissions) to the appropriate node(s) under `/libs/cq/core/content/nav/sites`. These correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`
-->

## Personalización de columnas en la Vista Lista {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Esta función está optimizada para columnas de campos de texto; para otros tipos de datos es posible superponer `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` en `/apps`.

<!-- Needs a review by Engineering -->
<!--
CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-sites-extension-listview-columns project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns/archive/master.zip)
-->

Para personalizar las columnas de la vista de lista:

1. Superponga la lista de las columnas disponibles.

   * En el nodo:

      `/apps/wcm/core/content/common/availablecolumns`

   * Añada las nuevas columnas o elimine las existentes.
   Consulte [Uso de superposiciones (y fusión de recursos de Sling)](/help/sites-developing/overlays.md) para obtener más información.

1. De forma opcional:

   * Si desea conectar datos adicionales, debe escribir un ` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)` con un

      `pageInfoProviderType` propiedad.
   Por ejemplo, consulte la clase o paquete adjunto (de GitHub) a continuación.

1. Ahora puede seleccionar la columna en el configurador de columnas de la vista de lista.

## Filtrado de recursos {#filtering-resources}

Cuando se utiliza una consola, un caso de uso común es cuando el usuario debe seleccionar entre los recursos (p. ej. páginas, componentes, recursos, etc.). Esto puede adoptar la forma de una lista, por ejemplo, desde la cual el autor debe elegir un elemento.

Para mantener la lista a un tamaño razonable y también relevante para el caso de uso, se puede implementar un filtro en forma de predicado personalizado. Consulte [este artículo](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) para obtener más información.
