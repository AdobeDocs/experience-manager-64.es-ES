---
title: Alojar dos instancias de espacio de trabajo de AEM Forms en un servidor
seo-title: Hosting two AEM Forms workspace instances on one server
description: Cómo los administradores de LC pueden personalizar HTML WS para alojar dos instancias en un único servidor accesible mediante distintas URL.
seo-description: How LC administrators can customize HTML WS to host two instances on a single server accessible via different URLs.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
exl-id: ef2ad8e1-5007-4587-97ca-cf21070be9a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 91%

---

# Alojar dos instancias de espacio de trabajo de AEM Forms en un servidor {#hosting-two-aem-forms-workspace-instances-on-one-server}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La instalación y configuración predeterminadas de AEM Forms permiten que solo haya un espacio de trabajo de AEM Forms disponible en el servidor. Sin embargo, puede que necesite alojar dos instancias diferentes de AEM Forms Workspace en un único servidor de AEM Forms. Las dos instancias son accesibles desde direcciones URL diferentes.

Los administradores de AEM Forms personalizan el espacio de trabajo para crear dos direcciones URL diferentes y hacer que dos espacios de trabajo estén disponibles en el mismo servidor. En este artículo de personalización, asumimos que los dos espacios de trabajo son accesibles en `https://[server]:[port]/lc/ws` y `https://[server]:[port]:/lc/ws2`.

Siga estos pasos para configurar AEM Forms Workspace.

1. Instale el paquete dev de AEM Forms Workspace en su servidor. Consulte el [paquete dev](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) para obtener instrucciones sobre cómo crearlo.
1. Inicie sesión en CRXDE Lite como administrador al acceder a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Copie el nodo ws en /content y pegue en /content. Cambie el nombre del nodo a ws2. Haga clic en **[!UICONTROL Guardar todo]**. En las propiedades de este nodo, cambie el valor de `sling:resourceType` a ws2. Haga clic en **[!UICONTROL Guardar todo]**.

1. Copie la carpeta ws de /libs y péguela en /apps. Cambie el nombre de la carpeta a ws2. Haga clic en **[!UICONTROL Guardar todo]**.
1. En `GET.jsp`, en `/apps/ws2`, realice los siguientes cambios en el código. Sustituya lo siguiente

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   con el siguiente código

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. En `registry.js`, en `/apps/ws2/js`, cambie la ruta de las plantillas para hacer referencia a las plantillas en `/apps/ws2/js/runtime/templates`. Reemplace el siguiente código

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   con el siguiente código

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. En `userinfo.js`, en `/apps/ws2/js/runtime/models` y `/apps/ws2/js/runtime/views`, cambie la cadena `/lc/content/ws` a `lc/content/ws2`.

1. En `/apps/ws2/js/runtime/services/service.js`, cambie la ruta en la función `getLocalizationData` para que señale `/lc/apps/ws2/Locale.html`.

1. Para consultar `pdf.html` del nuevo espacio de trabajo, cambie la ruta de `pdf.html` en `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Para consultar `pdf.html` del nuevo espacio de trabajo, cambie las rutas de `pdf.html` y `WsNextAdapter.swf` en `startprocess.html`, `taskdetails.html` y `processinstancehistory.html`, en `/apps/ws2/js/runtime/templates`.

1. Copie la carpeta `/etc/map/ws` y péguela en `/etc/map`. Cambie el nombre de la nueva carpeta a ws2. Haga clic en Guardar todo.

1. En propiedades de `ws2`, cambie el valor de `sling:redirect` a `content/ws2`.

1. Cambie el valor de `sling:match` a `^[^/\||]/[^/\||]/ws2$`.
