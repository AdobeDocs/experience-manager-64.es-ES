---
title: Desarrollar aplicación de espacio aislado
seo-title: Develop Sandbox Application
description: Desarrollo de aplicaciones mediante secuencias de comandos de base
seo-description: Develop application using foundation scripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: cd036e4a-0884-4ba0-83e9-7013583bbbae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 7%

---

# Desarrollar aplicación de espacio aislado {#develop-sandbox-application}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta sección, ahora que la plantilla se ha configurado en la variable [aplicación inicial](initial-app.md) y las páginas iniciales establecidas en la [contenido inicial](initial-content.md) , la aplicación se puede desarrollar utilizando secuencias de comandos de base, incluida la capacidad de permitir la creación con componentes de Communities. Al final de esta sección, el sitio web funcionará.

## Uso de scripts de página base {#using-foundation-page-scripts}

La secuencia de comandos predeterminada, creada cuando se agregó el componente que procesa la plantilla de página de reproducción, se modifica para incluir el head.jsp de la página de base y un body.jsp local.

### Tipo de recurso superior {#super-resource-type}

El primer paso es agregar una propiedad de supertipo de recurso al `/apps/an-scf-sandbox/components/playpage` para que herede las secuencias de comandos y propiedades del supertipo.

Uso del CRXDE Lite:

<!--Resolve steps below-->

* Nombre: `sling:resourceSuperType`
* Tipo: `String`
* Valor: `foundation/components/page`

1. Haga clic en el icono verde **[!UICONTROL [+] Agregar]**
1. Haga clic en **[!UICONTROL Guardar todo]**

![chlimage_1-231](assets/chlimage_1-231.png)

### Secuencias de comandos de cabezal y cuerpo {#head-and-body-scripts}

1. En **CRXDE Lite** panel explorador, vaya a `/apps/an-scf-sandbox/components/playpage` y haga doble clic en el archivo `playpage.jsp` para abrirlo en el panel de edición.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp}

```xml
<%--

  An SCF Sandbox Play Component component.

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %><%
%><%
 // TODO add your code here
%>
```

1. Teniendo en cuenta las etiquetas de script abiertas/cercanas, sustituya &quot; // TODO ...&quot; con incluye secuencias de comandos para las partes del encabezado y del cuerpo de &lt;html>.

   Con un supertipo de `foundation/components/page`, cualquier script no definido en esta misma carpeta se convertirá en un script de `/apps/foundation/components/page` carpeta (si existe), de lo contrario, a una secuencia de comandos en `/libs/foundation/components/page` carpeta.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp-1}

```xml
<%--

    An SCF Sandbox Play Component component: playpage.jsp

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %>
<html>
  <cq:include script="head.jsp"/>
  <cq:include script="body.jsp"/>
</html>
```

1. El script base `head.jsp` no es necesario superponer la secuencia de comandos base `body.jsp` está vacío.

   Para configurar la creación, superponga `body.jsp` con una secuencia de comandos local e incluir un sistema de párrafos (parsys) en el cuerpo:

   1. vaya a `/apps/an-scf-sandbox/components`
   1. seleccione `playpage`node
   1. haga clic con el botón derecho y seleccione `Create > Create File...`

      * Nombre: **body.jsp**
   1. Haga clic en **[!UICONTROL Guardar todo]**

   Apertura `/apps/an-scf-sandbox/components/playpage/body.jsp` y pegue el siguiente texto:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Haga clic en **[!UICONTROL Guardar todo]**

**Vea la página en un explorador en modo de edición:**

* IU estándar: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

No solo debería ver el encabezado **Reproducción de la comunidad**, pero también la IU para editar el contenido de la página.

El panel lateral Recursos/Componente se ve cuando se abre de forma alternada el panel lateral y la ventana es lo suficientemente ancha como para que se muestre tanto el contenido lateral como el contenido de la página.

![chlimage_1-232](assets/chlimage_1-232.png)

* IU clásica: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

A continuación, se muestra cómo aparece la página de reproducción en la IU clásica, incluso con el buscador de contenido (cf):

![chlimage_1-233](assets/chlimage_1-233.png)

## Componentes de Communities {#communities-components}

Para habilitar los componentes de Communities para la creación, comience por seguir estas instrucciones:

* [Acceso a componentes de Communities](basics.md#accessing-communities-components)

Para los fines de este simulador de pruebas, comience con estos **Comunidades** componentes (activar marcando la casilla ):

* Comentarios
* Foro
* Clasificación
* Repasos
* Resumen de críticas (visualización)
* Votación

Además, elija **[!UICONTROL General]** componentes como

* Imagen
* Tabla
* Texto
* Título (Foundation)

>[!NOTE]
>
>Los componentes habilitados para la página par se almacenan en el repositorio como el valor de la variable `components` propiedad de la variable\
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` node.

## Página de aterrizaje {#landing-page}

En un entorno de varios idiomas, la página raíz incluiría una secuencia de comandos que analizaría la solicitud del cliente para determinar el idioma preferido.

En este ejemplo sencillo, la página raíz se está configurando de forma estática para redirigir a la página en inglés, que puede desarrollarse en el futuro para ser la página de aterrizaje principal con un vínculo a la página de reproducción.

Cambie la URL del explorador a la página raíz: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Seleccione el icono Información de página
* Select **[!UICONTROL Abrir propiedades]**
* En la ficha AVANZADO

   * Para la entrada de redirección, vaya a **[!UICONTROL Sitios web > Sitio de espacio aislado de SCF > Espacio aislado de SCF]**
   * Haga clic en **[!UICONTROL Aceptar]**

* Haga clic en **[!UICONTROL Aceptar]**

Una vez publicado el sitio, la navegación a la página raíz de una instancia de publicación se redirigirá a la página en inglés.

El último paso antes de jugar con los componentes SCF de comunidades es añadir una carpeta de biblioteca de clientes (clientlibs) .... **[Archivadores](add-clientlibs.md)**
