---
title: Crear una nueva pantalla de inicio de sesión
seo-title: Creating a new login screen
description: Modificar la página de inicio de sesión de los módulos de LiveCycle, por ejemplo, de AEM Forms Workspace o de Forms Manager.
seo-description: How-to modify the login page of LiveCycle modules, for example of AEM Forms workspace or Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
exl-id: caa4f835-c353-49d5-b18c-4d0538c1136f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 93%

---

# Crear una nueva pantalla de inicio de sesión {#creating-a-new-login-screen}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede modificar la pantalla de inicio de sesión de todos los módulos de AEM Forms que utilizan la pantalla de inicio de sesión de AEM Forms. Por ejemplo, las modificaciones afectan a la pantalla de inicio de sesión de Forms Manager y de AEM Forms Workspace.

## Requisitos previos {#prerequisite}

1. Iniciar sesión en `/lc/crx/de` con permisos de administrador.
1. Realice las siguientes acciones:

   1. Duplique la estructura jerárquica: de `/libs/livecycle/core/content` en `/apps/livecycle/core/content`. Mantenga las mismas propiedades (nodo/carpeta) y control de acceso.
   1. Copie la carpeta de contenido: from `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimine el contenido de la carpeta `/apps/livecycle/core`.

1. Realice estas acciones:

   1. Duplique la estructura jerárquica: de `/libs/livecycle/core/components/login` en `/apps/livecycle/core/components/login`. Mantenga las mismas propiedades (nodo/carpeta) y control de acceso.
   1. Copie la carpeta de componentes: de `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimine el contenido de la carpeta: `/apps/livecycle/core/components/login`.

## Agregue una configuración regional nueva  {#adding-a-new-locale}

1. Copie la carpeta `i18n`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Elimine todas las carpetas dentro de `i18n` excepto una, digamos `en`.
1. En la carpeta `en`, realice estas acciones:

   1. Cambie el nombre de la carpeta por el nombre de la configuración regional que desee admitir. Por ejemplo, `ar`.
   1. Cambie la propiedad `jcr:language` valor a `ar` (para la carpeta `ar`).

   >[!NOTE]
   >
   >Si la configuración regional es una combinación de código de país e idioma, por ejemplo, `ar-DZ`, cambie el nombre de la carpeta y el valor de la propiedad a `ar-DZ`.

1. Copie `login.jsp`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Modifique el siguiente fragmento de código por `/apps/livecycle/core/components/login/login.jsp`:

   ***La configuración regional es el código de idioma***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***La configuración regional es código de país de idioma***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Para cambiar la configuración regional predeterminada***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## Agregar texto nuevo o modificar texto existente {#adding-new-text-or-modifying-existing-text}

1. Copie la carpeta `i18n`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Ahora modifique el valor de la propiedad `sling:message` del nodo (en la carpeta de código de configuración regional deseada) para el que desea cambiar el texto. La traducción se realiza mediante la clave mencionada en el valor de la propiedad `sling:key` del nodo.
1. Para agregar un nuevo par clave-valor, realice las siguientes acciones. Mire el ejemplo en la siguiente captura de pantalla.

   1. Cree un nodo de tipo `sling:MessageEntry` o copie un nodo existente y renómbrelo, en todas las carpetas de configuración regional.
   1. Copie `login.jsp` :

      * de `/libs/livecycle/core/components/login`
      * hasta `/apps/livecycle/core/components/login`
   1. Modifique `/apps/livecycle/core/components/login/login.jsp` para incorporar el texto agregado recientemente.

   ![captura](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## Agregar un estilo nuevo o modificar uno existente {#adding-new-style-or-modifying-existing-style}

1. Copie el nodo `login`:

   * de `/libs/livecycle/core/content`
   * hasta `/apps/livecycle/core/content`

1. Elimine los archivos `login.js` y `jquery-1.8.0.min.js`, desde el nodo `/apps/livecycle/core/content/login.`
1. Modifique los estilos del archivo CSS.
1. Para agregar nuevos estilos:

   1. Agregue nuevos estilos a `/apps/livecycle/core/content/login/login.css`
   1. Copie `login.jsp`

      * de `/libs/livecycle/core/components/login`
      * hasta `/apps/livecycle/core/components/login`
   1. Modifique `/apps/livecycle/core/components/login/login.jsp` para incorporar los estilos recién agregados.


1. Por ejemplo:

   * Agregue lo siguiente a `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Modifique lo siguiente en /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Si se quitan las imágenes existentes en `/apps/livecycle/core/content/login` (copiado de `/libs/livecycle/core/content/login`) se quitarán las referencias correspondientes en CSS.

## Agregar imágenes nuevas {#add-new-images}

1. Siga los pasos para agregar un estilo nuevo o modificar uno existente (documentados anteriormente).
1. Agregar imágenes nuevas en `/apps/livecycle/core/content/login`. Para agregar una imagen:

   1. Instale el cliente WebDAV.
   1. Navegue hasta la carpeta `/apps/livecycle/core/content/login`, mediante el cliente webDAV. Para obtener más información, consulte: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/es/crx/current/how_to/webdav_access.html).
   1. Agregar imágenes nuevas.

1. Agregar estilos nuevos en `/apps/livecycle/core/content/login/login.css,` correspondiente a las imágenes nuevas agregadas en `/apps/livecycle/core/content/login`.
1. Utilice los nuevos estilos en `login.jsp` en `/apps/livecycle/core/components`.
1. Por ejemplo:

   * Agregue lo siguiente a `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Modifique lo siguiente en /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
