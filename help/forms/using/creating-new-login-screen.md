---
title: Creación de una nueva pantalla de inicio de sesión
seo-title: Creación de una nueva pantalla de inicio de sesión
description: Cómo modificar la página de inicio de sesión de los módulos de LiveCycle, por ejemplo, el espacio de trabajo de AEM Forms o Forms Manager.
seo-description: Cómo modificar la página de inicio de sesión de los módulos de LiveCycle, por ejemplo, el espacio de trabajo de AEM Forms o Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---


# Creación de una nueva pantalla de inicio de sesión {#creating-a-new-login-screen}

Puede modificar la pantalla de inicio de sesión de todos los módulos de AEM Forms que utilizan la pantalla de inicio de sesión de AEM Forms. Por ejemplo, las modificaciones afectan a la pantalla de inicio de sesión del área de trabajo de Forms Manager y AEM Forms.

## Requisitos previos {#prerequisite}

1. Inicie sesión en `/lc/crx/de` con permisos de administrador.
1. Realice las siguientes acciones:

   1. Replicar la estructura jerárquica: de `/libs/livecycle/core/content` a `/apps/livecycle/core/content`. Mantenga las mismas propiedades (nodo/carpeta) y el mismo control de acceso.
   1. Copie la carpeta de contenido: de `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimine el contenido de la carpeta `/apps/livecycle/core`.

1. Realice estas acciones:

   1. Replicar la estructura jerárquica: de `/libs/livecycle/core/components/login` a `/apps/livecycle/core/components/login`. Mantenga las mismas propiedades (nodo/carpeta) y el mismo control de acceso.
   1. Copie la carpeta components: de `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimine el contenido de la carpeta: `/apps/livecycle/core/components/login`.

## Añadir una nueva configuración regional {#adding-a-new-locale}

1. Copie la carpeta `i18n`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Elimine todas las carpetas dentro de `i18n` excepto una, digamos `en`.
1. En la carpeta `en`, realice las siguientes acciones:

   1. Cambie el nombre de la carpeta por el nombre de configuración regional que desee admitir. Por ejemplo, `ar`.
   1. Cambie el valor de la propiedad `jcr:language` a `ar` (para la carpeta `ar`).

   >[!NOTE]
   >
   >Si locale es una combinación de código de país-idioma, por ejemplo, `ar-DZ`, cambie el nombre de la carpeta y el valor de la propiedad a `ar-DZ`.

1. Copiar `login.jsp`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Modifique el siguiente fragmento de código para `/apps/livecycle/core/components/login/login.jsp`:

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

   ***La configuración regional es un código de país de idioma***

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

## Añadir texto nuevo o modificar texto existente {#adding-new-text-or-modifying-existing-text}

1. Copiar carpeta `i18n`:

   * de `/libs/livecycle/core/components/login`
   * hasta `/apps/livecycle/core/components/login`

1. Ahora modifique el valor de la propiedad `sling:message` del nodo (debajo de la carpeta de código de configuración regional deseada) para la que desea cambiar el texto. La traducción se realiza mediante la clave mencionada en el valor de la propiedad `sling:key` del nodo.
1. Para agregar un nuevo par clave-valor, realice las siguientes acciones. Compruebe un ejemplo en la captura de pantalla siguiente.

   1. Cree un nodo de tipo `sling:MessageEntry` o copie un nodo existente y cambie su nombre en todas las carpetas de configuración regional.
   1. Copiar `login.jsp` :

      * de `/libs/livecycle/core/components/login`
      * hasta `/apps/livecycle/core/components/login`
   1. Modifique `/apps/livecycle/core/components/login/login.jsp` para incorporar el texto recientemente agregado.

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

## Añadir estilo nuevo o modificar estilo existente {#adding-new-style-or-modifying-existing-style}

1. Copiar nodo `login`:

   * de `/libs/livecycle/core/content`
   * hasta `/apps/livecycle/core/content`

1. Eliminar archivos `login.js` y `jquery-1.8.0.min.js` del nodo `/apps/livecycle/core/content/login.`
1. Modifique los estilos del archivo CSS.
1. Para agregar nuevos estilos:

   1. Añadir nuevos estilos a `/apps/livecycle/core/content/login/login.css`
   1. Copiar `login.jsp`

      * de `/libs/livecycle/core/components/login`
      * hasta `/apps/livecycle/core/components/login`
   1. Modifique `/apps/livecycle/core/components/login/login.jsp` para incorporar los estilos recién agregados.


1. Por ejemplo:

   * Añada lo siguiente a `/apps/livecycle/core/content/login/login.css`.

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
>Si se eliminan las imágenes existentes en `/apps/livecycle/core/content/login` (copiadas de `/libs/livecycle/core/content/login`), elimine las referencias correspondientes en CSS.

## Añadir nuevas imágenes {#add-new-images}

1. Siga los pasos para Añadir un nuevo estilo o modificar un estilo existente (documentados anteriormente).
1. Añada nuevas imágenes en `/apps/livecycle/core/content/login`. Para agregar una imagen:

   1. Instale el cliente WebDAV.
   1. Navegue a la carpeta `/apps/livecycle/core/content/login` mediante el cliente webDAV. Para obtener más información, consulte: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Añadir imágenes nuevas.

1. Añada nuevos estilos en `/apps/livecycle/core/content/login/login.css,` correspondientes a las nuevas imágenes agregadas en `/apps/livecycle/core/content/login`.
1. Utilice los nuevos estilos en `login.jsp` en `/apps/livecycle/core/components`.
1. Por ejemplo:

   * Añada lo siguiente a `/apps/livecycle/core/content/login/login.css`

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
