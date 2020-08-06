---
title: Añadir Clientlibs
seo-title: Añadir Clientlibs
description: Añadir una ClientLibraryFolder
seo-description: Añadir una ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---


# Añadir Clientlibs {#add-clientlibs}

## Añadir una ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Cree una ClientLibraryFolder con el nombre `clientlibs`que contendrá el JS y CSS utilizados para procesar las páginas del sitio.

El valor de `categories`propiedad proporcionado a esta biblioteca de cliente es el identificador utilizado para incluir directamente esta clientlib desde una página de contenido o para incrustarla en otros clientes.

1. Con **[!UICONTROL CRXDE Lite]**, expanda `/etc/designs`

1. Haga clic con el botón derecho `an-scf-sandbox` y seleccione `Create Node`

   * Nombre: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Haga clic en **[!UICONTROL Aceptar]**

![chlimage_1-220](assets/chlimage_1-220.png)

En la ficha **[!UICONTROL Propiedades]** del nuevo `clientlibs` nodo, introduzca la **`categories`** propiedad:

* Nombre: **[!UICONTROL categorías]**
* Tipo: **[!UICONTROL Cadena]**
* Valor: **[!UICONTROL apps.an-scf-sandbox]**
* Haga clic en **[!UICONTROL Agregar]**
* Haga clic en **[!UICONTROL Guardar todo]**

Nota: anteponer el valor de categorías con &#39;aplicaciones&#39;. es una convención para identificar la &#39;aplicación propietaria&#39; como una carpeta /apps, no como /libs.  IMPORTANTE: Añada los marcadores `js.txt` de posición y `css.txt` los archivos. (No es oficialmente un cq:ClientLibraryFolder sin ellos).


1. Haga clic con el botón derecho en **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Seleccione **[!UICONTROL Crear archivo...]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. Seleccione **[!UICONTROL Crear archivo...]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. Haga clic en **[!UICONTROL Guardar todo]**

![chlimage_1-221](assets/chlimage_1-221.png)

La primera línea de css.txt y js.txt identifica la ubicación base desde la que se encuentran las siguientes listas de archivos.

Intente establecer el contenido de css.txt en:

```
#base=.
 style.css
```

A continuación, cree un archivo en clientlibs llamado style.css y defina el contenido en:

`body {`

`background-color: #b0c4de;`

`}`

## Incrustar clientes SCF {#embed-scf-clientlibs}

En la ficha **[!UICONTROL Propiedades]** del `clientlibs` nodo, introduzca la propiedad String de varios valores **[!UICONTROL embed]**. Esto incorporará las bibliotecas del lado del [cliente (clientlibs) necesarias para los componentes](client-customize.md#clientlibs-for-scf)SCF. Para este tutorial, agregaremos muchos de los clientlibs necesarios para los componentes Communities.

**Tenga en cuenta** que este puede ser o no el método deseado para usar en un sitio de producción, ya que existen consideraciones de conveniencia en comparación con el tamaño y la velocidad de los clientes descargados para cada página.

Si solo utiliza una función en una página, puede incluir la clientlib completa de esa característica directamente en la página, por ejemplo: &lt;% ui:includeClientLib categorías=cq.social.hbs.forum&quot; %>

En este caso, los incluimos a todos, por lo que preferiríamos a los clientes más básicos de SCF, que son los clientes autores:

* Nombre: **`embed`**
* Tipo: **`String`**

* Haga clic **`Multi`**
* Value: **`cq.social.scf`**

   *&lt;enter> abrirá un cuadro de diálogo*

   *Haga clic **[+]**después de cada entrada para agregar las siguientes categorías clientlib:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Haga clic en **[!UICONTROL Aceptar]**

* Haga clic en **[!UICONTROL Guardar todo]**

![chlimage_1-222](assets/chlimage_1-222.png)

Así es como `/etc/designs/an-scf-sandbox/clientlibs` debería aparecer en el repositorio:

![chlimage_1-223](assets/chlimage_1-223.png)

## Incluir Clientlibs en la plantilla PlayPage {#include-clientlibs-in-playpage-template}

Sin incluir la categoría `apps.an-scf-sandbox` ClientLibraryFolder en la página, los componentes SCF no funcionarán ni se les aplicará estilo, ya que no estarán disponibles los JavaScript y los estilos necesarios.

Por ejemplo, sin incluir clientlibs, el componente de comentarios de SCF no tiene estilo:

![chlimage_1-224](assets/chlimage_1-224.png)

Una vez que se incluye apps.an-scf-sandbox clientlibs, el componente de comentarios de SCF aparece con estilo:

![chlimage_1-225](assets/chlimage_1-225.png)

La instrucción include pertenece al <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> de la sección <html> script. El valor predeterminado **`foundation head.jsp`** incluye una secuencia de comandos que se puede superponer: **`headlibs.jsp`**.

**Copie headlibs.jsp e incluya clientlibs:**

1. Con **[!UICONTROL CRXDE Lite]**, seleccione **`/libs/foundation/components/page/headlibs.jsp`**
1. Haga clic con el botón derecho y seleccione **[!UICONTROL Copiar]** (o seleccione Copiar en la barra de herramientas)
1. Seleccione **`/apps/an-scf-sandbox/components/playpage`**
1. Haga clic con el botón derecho y seleccione **[!UICONTROL Pegar]** (o seleccione Pegar en la barra de herramientas)
1. Haga clic en el Doble **`headlibs.jsp`** para abrirlo
1. Anexe la línea siguiente al final del archivo

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Haga clic en **[!UICONTROL Guardar todo]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Cargue el sitio web en el navegador y vea si el fondo no es azul.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Guardar su trabajo hasta ahora {#saving-your-work-so-far}

En este punto, existe un simulador de pruebas minimalista y puede que valga la pena guardarlo como paquete para que, mientras se reproduce, si el repositorio se daña y desea pasar el inicio, pueda desactivar el servidor, cambiar el nombre o eliminar la carpeta crx-quickstart/, activar el servidor, cargar e instalar este paquete guardado y no tener que repetir estos pasos más básicos.

Este paquete existe en el tutorial [Crear una página](create-sample-page.md) de muestra para aquellos que no pueden esperar para simplemente saltar y reproducir el inicio!...

Para crear un paquete:


* En el **[!UICONTROL CRXDE Lite]**, haga clic en el icono [Paquete](http://localhost:4502/crx/packmgr/)
* Haga clic en **[!UICONTROL Crear paquete]**

   * Nombre del paquete: `an-scf-sandbox-minimal-pkg`
   * Versión: `0.1`
   * Grupo: &lt;dejar como predeterminado>
   * Haga clic en **[!UICONTROL Aceptar]**

* Haga clic en **[!UICONTROL Editar]**

   * Ficha Seleccionar **[!UICONTROL Filtros]**

      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;examinar a `/apps/an-scf-sandbox`>
      * Haga clic en **[!UICONTROL Finalizado]**
      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;examinar a `/etc/designs/an-scf-sandbox`>
      * Haga clic en **[!UICONTROL Finalizado]**
      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;examinar a `/content/an-scf-sandbox`>
      * Haga clic en **[!UICONTROL Finalizado]**
   * Haga clic en **[!UICONTROL Guardar]**


* Haga clic en **[!UICONTROL Generar]**

Ahora puede seleccionar **[!UICONTROL Descargar]** para guardarlo en el disco y **[!UICONTROL Cargar paquete]** en otra parte, así como seleccionar **[!UICONTROL Más > Replicar]** para insertar el simulador de pruebas en una instancia de publicación local host para expandir el dominio del simulador de pruebas.
