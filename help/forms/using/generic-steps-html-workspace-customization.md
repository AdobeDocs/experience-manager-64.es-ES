---
title: Pasos genéricos para la personalización del espacio de trabajo de AEM Forms
seo-title: Pasos genéricos para la personalización del espacio de trabajo de AEM Forms
description: Cómo empezar a personalizar la interfaz de usuario del espacio de trabajo de AEM Forms.
seo-description: Cómo empezar a personalizar la interfaz de usuario del espacio de trabajo de AEM Forms.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---


# Pasos genéricos para la personalización del espacio de trabajo de AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

Los pasos genéricos para realizar cualquier personalización son:

1. Inicie sesión en el CRXDE Lite accediendo a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Cree una carpeta con el nombre `ws`en `/apps`, si no existe. Haga clic en **[!UICONTROL Guardar todo]**.
1. Vaya a `/apps/ws` y vaya a la ficha **[!UICONTROL Control de acceso]**.
1. En la lista **[!UICONTROL Control de acceso]**, haga clic en **[!UICONTROL +]** para agregar una nueva entrada. Vuelva a hacer clic en **[!UICONTROL +]**.
1. Busque y seleccione la **[!UICONTROL entidad de seguridad PERM_WORKSPACE_USER]**.

   ![Seleccione el principal PERM_WORKSPACE_USER como parte de los pasos genéricos para personalizar HTML Workspace](assets/perm_workspace_user.png)

1. Otorgue `jcr:read` privilegios al director.
1. Haga clic en **[!UICONTROL Guardar todo]**.
1. Copie los archivos `GET.jsp` y `html.jsp`de la carpeta `/libs/ws`a la carpeta `/apps/ws`.
1. Copie la carpeta `/libs/ws/locales` en la carpeta `/apps/ws`. Haga clic en **[!UICONTROL Guardar todo]**.
1. Actualice las referencias y las rutas relativas en el archivo `GET.jsp`, como se muestra a continuación, y haga clic en **[!UICONTROL Guardar todo]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Para las personalizaciones de CSS, haga lo siguiente:

   1. Vaya a la carpeta `/apps/ws` y cree una nueva carpeta con el nombre `css`.
   1. En la carpeta `css`, cree un nuevo archivo con el nombre `newStyle.css`.
   1. Abra `/apps/ws/html`.jsp y cambie de

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   hasta

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Coloque la entrada del archivo CSS definido por el usuario después de la entrada de newStyle.css, como se muestra arriba.

1. En el archivo /apps/ws/html.jsp, cambie de

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   hasta

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Haga lo siguiente:

   1. Cree una carpeta con el nombre `js`en `/apps/ws`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Cree una carpeta con el nombre `libs`en `/apps/ws/js`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Cree una carpeta con el nombre `jqueryui`en `/apps/ws/js/libs`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Copie `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` en `/apps/ws/js/libs/jqueryui`. Haga clic en **[!UICONTROL Guardar todo]**.

1. Para las personalizaciones de HTML, haga lo siguiente:

   1. En `/apps/ws/js`, cree una carpeta con el nombre `runtime`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. En `/apps/ws/js/runtime`, cree una carpeta con el nombre `templates`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Copie `/libs/ws/js/main.js` en `/apps/ws/js/main.js`.
   1. Copie /libs/ws/js/registry.js en `/apps/ws/js/registry.js`.

1. Haga clic en **[!UICONTROL Guardar todo]**, borre la caché y actualice el espacio de trabajo de AEM Forms.

   Acceda a la dirección URL `https://[server]:[port]/lc/ws` e inicie sesión con credenciales de administrador/contraseña. El explorador redirige a `https://[server]:[port]/lc/apps/ws/index.html`.

