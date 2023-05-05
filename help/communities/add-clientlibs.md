---
title: Agregar Clientlibs
seo-title: Add Clientlibs
description: Agregar una carpeta ClientLibrary
seo-description: Add a ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
exl-id: 9b8c3d1c-a9b1-4dde-9044-46c8f2b22c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 7%

---

# Agregar Clientlibs {#add-clientlibs}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Agregar una ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Crear una ClientLibraryFolder denominada `clientlibs`que contendrán los JS y CSS utilizados para procesar las páginas del sitio.

La variable `categories`el valor de propiedad dado a esta biblioteca de cliente es el identificador utilizado para incluir directamente esta clientlib desde una página de contenido o para incrustarla en otras clientlibs.

1. Uso **[!UICONTROL CRXDE Lite]**, expandir `/etc/designs`

1. Haga clic con el botón derecho en `an-scf-sandbox` y seleccione `Create Node`

   * Nombre: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Haga clic en **[!UICONTROL Aceptar]**

![chlimage_1-220](assets/chlimage_1-220.png)

En el **[!UICONTROL Propiedades]** para la nueva `clientlibs` , introduzca el **`categories`** propiedad:

* Nombre:**[!UICONTROL categories]**
* Tipo:**[!UICONTROL cadena]**
* Valor: **[!UICONTROL apps.an-scf-sandbox]**
* Haga clic en **[!UICONTROL Agregar]**
* Haga clic en **[!UICONTROL Guardar todo]**

Nota: anteponer el valor de categorías a &quot;apps&quot;. es una convención para identificar la &quot;aplicación propietaria&quot; como si estuviera en la carpeta /apps, no en /libs.  IMPORTANTE: Agregar marcador de posición `js.txt` y `css.txt` archivos. (No es oficialmente un cq:ClientLibraryFolder sin ellos).


1. Haga clic con el botón derecho en **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Select **[!UICONTROL Crear archivo...]**
1. Entrar **[!UICONTROL Nombre]**: `css.txt`

1. Select **[!UICONTROL Crear archivo...]**
1. Entrar **[!UICONTROL Nombre]**: `js.txt`

1. Haga clic en **[!UICONTROL Guardar todo]**

![chlimage_1-221](assets/chlimage_1-221.png)

La primera línea de css.txt y js.txt identifica la ubicación base desde la que se encuentran las siguientes listas de archivos.

Intente establecer el contenido de css.txt en:

```
#base=.
 style.css
```

A continuación, cree un archivo en clientlibs llamado style.css y establezca el contenido en:

`body {`

`background-color: #b0c4de;`

`}`

## Incrustar Clientlibs SCF {#embed-scf-clientlibs}

En el **[!UICONTROL Propiedades]** para la variable `clientlibs` , introduzca la propiedad String de varios valores. **[!UICONTROL embed]**. Esto incorporará lo necesario [bibliotecas del lado del cliente (clientlibs) para componentes SCF](client-customize.md#clientlibs-for-scf). Para este tutorial, agregaremos muchos de los clientlibs necesarios para los componentes de Communities.

**Nota** que este puede ser o no el método deseado para usar en un sitio de producción, ya que existen consideraciones de comodidad en comparación con el tamaño/velocidad de los clientlibs descargados para cada página.

Si solo utiliza una función en una página, puede incluir la clientlib completa de esa característica directamente en la página, por ejemplo, &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

En este caso, los incluimos a todos, por lo que preferiríamos los clientlibs de SCF más básicos, que son los clientlibs de autor:

* Nombre: **`embed`**
* Tipo: **`String`**

* Haga clic **`Multi`**
* Valor: **`cq.social.scf`**

   *&lt;enter> se abrirá un cuadro de diálogo*

   *Haga clic en **[+]**después de cada entrada para añadir las siguientes categorías clientlib:*

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

## Incluir Clientlibs en la plantilla de PlayPage {#include-clientlibs-in-playpage-template}

Sin incluir el `apps.an-scf-sandbox` categoría ClientLibraryFolder en la página; los componentes SCF no funcionarán ni se diseñarán, ya que los Javascript y los estilos necesarios no estarán disponibles.

Por ejemplo, sin incluir clientlibs, el componente de comentarios de SCF aparece sin estilo:

![chlimage_1-224](assets/chlimage_1-224.png)

Una vez que se incluye apps.an-scf-sandbox clientlibs , el componente de comentarios de SCF aparece con estilo:

![chlimage_1-225](assets/chlimage_1-225.png)

La sentencia include pertenece al grupo `<head>` de la sección `<html>` secuencia de comandos. El valor predeterminado **`foundation head.jsp`** incluye una secuencia de comandos que se puede superponer: **`headlibs.jsp`**.

**Copie headlibs.jsp e incluya clientlibs:**

1. Uso **[!UICONTROL CRXDE Lite]**, seleccione **`/libs/foundation/components/page/headlibs.jsp`**
1. Haga clic con el botón derecho y seleccione **[!UICONTROL Copiar]** (o seleccione Copiar en la barra de herramientas)
1. Seleccionar **`/apps/an-scf-sandbox/components/playpage`**
1. Haga clic con el botón derecho y seleccione **[!UICONTROL Pegar]** (o seleccione Pegar en la barra de herramientas)
1. Haga doble clic en **`headlibs.jsp`** para abrirlo
1. Añada la línea siguiente al final del archivo

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

Cargue el sitio web en el explorador y compruebe si el fondo no está a la sombra de azul.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Guardar su trabajo hasta ahora {#saving-your-work-so-far}

En este punto, existe un simulador de pruebas minimalista y puede que valga la pena guardarlo como paquete para que, mientras se reproduce, si el repositorio se daña y desea volver a empezar, puede desactivar el servidor, cambiar el nombre o eliminar la carpeta crx-quickstart/, activar el servidor, cargar e instalar este paquete guardado y no tener que repetir estos pasos más básicos.

Este paquete existe en la variable [Crear una página de muestra](create-sample-page.md) tutorial para aquellos que no pueden esperar para simplemente saltar y comenzar a jugar!...

Para crear un paquete:


* De **[!UICONTROL CRXDE Lite]**, haga clic en [Icono de paquete](http://localhost:4502/crx/packmgr/)
* Haga clic en **[!UICONTROL Crear paquete]**

   * Nombre del paquete: `an-scf-sandbox-minimal-pkg`
   * Versión: `0.1`
   * Grupo: &lt;leave as=&quot;&quot; default=&quot;&quot;>
   * Haga clic en **[!UICONTROL Aceptar]**

* Haga clic en **[!UICONTROL Editar]**

   * Select **[!UICONTROL Filtros]** ficha

      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/apps/an-scf-sandbox`
      * Haga clic en **[!UICONTROL Listo]**
      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/etc/designs/an-scf-sandbox`
      * Haga clic en **[!UICONTROL Listo]**
      * Haga clic en **[!UICONTROL Añadir filtro]**
      * Ruta raíz: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/content/an-scf-sandbox`
      * Haga clic en **[!UICONTROL Listo]**
   * Haga clic en **[!UICONTROL Guardar]**


* Haga clic en **[!UICONTROL Generar]**

Ahora puede seleccionar **[!UICONTROL Descargar]** para guardarlo en disco y **[!UICONTROL Cargar paquete]** en cualquier otra parte, así como seleccionar **[!UICONTROL Más > Replicar]** para insertar el simulador de pruebas en una instancia de publicación de localhost para expandir el dominio del simulador de pruebas.
