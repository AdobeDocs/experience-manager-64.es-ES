---
title: Pasos genéricos para la personalización de AEM Forms Workspace
seo-title: Generic steps for AEM Forms workspace customization
description: Introducción a la personalización de la interfaz de usuario de AEM Forms Workspace.
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 80%

---

# Pasos genéricos para la personalización de AEM Forms Workspace {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los pasos genéricos para realizar cualquier personalización son:

1. Inicie sesión en CRXDE Lite accediendo a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Cree una carpeta  denominada `ws` en `/apps`, en el caso de que no exista. Haga clic en **[!UICONTROL Guardar todo]**.
1. Vaya a `/apps/ws` y desplácese hasta la pestaña **[!UICONTROL Control de acceso]**.
1. En la lista **[!UICONTROL Control de acceso]**, haga clic en **[!UICONTROL +]** para agregar una nueva entrada. Vuelva a hacer clic en **[!UICONTROL +]**.
1. Busque y seleccione el principal **[!UICONTROL PERM_WORKSPACE_USER]**.

   ![Seleccione el principal PERM_WORKSPACE_USER como parte de los pasos genéricos para personalizar HTML Workspace](assets/perm_workspace_user.png).

1. Otorgue el privilegio `jcr:read` al principal.
1. Haga clic en **[!UICONTROL Guardar todo]**.
1. Copie el `GET.jsp` y `html.jsp`los archivos de `/libs/ws`a la `/apps/ws` carpeta.
1. Copie la carpeta `/libs/ws/locales` en la carpeta `/apps/ws`. Haga clic en **[!UICONTROL Guardar todo]**.
1. Actualice las referencias y las rutas relativas del archivo `GET.jsp`, como se muestra a continuación, y haga clic en **[!UICONTROL Guardar todo]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Siga los siguientes pasos para llevar a cabo las personalizaciones de CSS:

   1. Vaya a la carpeta `/apps/ws` y cree una nueva carpeta con el nombre `css`.
   1. En el `css`carpeta, cree un nuevo archivo con el nombre `newStyle.css`.
   1. Abra `/apps/ws/html`.jsp y cambie

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   a

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Coloque la entrada del archivo CSS definido por el usuario después de la entrada de newStyle.css, como se muestra arriba.

1. En el archivo /apps/ws/html.jsp, cambie

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   a

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Haga lo siguiente:

   1. Cree una carpeta con el nombre `js` en `/apps/ws`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Cree una carpeta con el nombre `libs` en `/apps/ws/js`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Cree una carpeta con el nombre `jqueryui` en `/apps/ws/js/libs`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Copie `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` en `/apps/ws/js/libs/jqueryui`. Haga clic en **[!UICONTROL Guardar todo]**.

1. Siga los siguientes pasos para llevar a cabo las personalizaciones de HTML:

   1. Cree una carpeta con el nombre `runtime` en `/apps/ws/js`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Cree una carpeta con el nombre `templates` en `/apps/ws/js/runtime`. Haga clic en **[!UICONTROL Guardar todo]**.
   1. Copie `/libs/ws/js/main.js` en `/apps/ws/js/main.js`.
   1. Copie /libs/ws/js/registry.js en `/apps/ws/js/registry.js`.

1. Haga clic en **[!UICONTROL Guardar todo]**, borre la caché y actualice AEM Forms Workspace.

   Acceda a la dirección URL `https://[server]:[port]/lc/ws` e inicie sesión con las credenciales de administrador/contraseña. El explorador le redirigirá a `https://[server]:[port]/lc/apps/ws/index.html`.
