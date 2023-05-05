---
title: Resolución de problemas de AEM durante la creación
seo-title: Troubleshooting AEM when Authoring
description: La sección siguiente trata ciertos problemas que pueden producirse al utilizar AEM, así como sugerencias para solucionarlos.
seo-description: The following section covers some issues that you might encounter when using AEM, together with suggestions on how to troubleshoot them.
uuid: eb95e5ba-1eed-4ffb-80c1-9b8468820c22
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9b492b17-9029-46ae-9dc0-bb21e6b484df
exl-id: 09409631-c579-4b1f-9193-1348896f6a09
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 29%

---

# Resolución de problemas de AEM durante la creación{#troubleshooting-aem-when-authoring}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La sección siguiente trata ciertos problemas que pueden producirse al utilizar AEM, así como sugerencias para solucionarlos.

>[!NOTE]
>
>Cuando experimenta problemas, también vale la pena comprobar la lista de [Problemas conocidos](/help/release-notes/known-issues.md) para su instancia (versión y service packs).

>[!NOTE]
>
>Los usuarios que tengan privilegios de administrador y que deseen solucionar problemas con AEM, pueden utilizar los métodos de resolución de problemas descritos en [Solución de problemas de AEM (para administradores)](/help/sites-administering/troubleshoot.md). Si no dispone de suficientes privilegios, consulte con el administrador del sistema sobre la resolución de problemas AEM.

## La versión anterior de la página sigue en el sitio publicado {#old-page-version-still-on-published-site}

* **Problema**:

   * Ha realizado cambios en una página y replicado la página en el sitio de publicación, pero la variable *old* la versión de la página sigue mostrándose en el sitio de publicación.

* **Motivo**:

   * Esto puede tener varias causas, la mayoría de las veces la caché (su navegador local o Dispatcher), aunque a veces puede ser un problema con la cola de replicación.

* **Soluciones**:

   * Aquí hay varias posibilidades:
   * Confirme que la página se haya replicado correctamente. Compruebe el estado de la página y, si es necesario, el estado de la cola de replicación.
   * Borre la caché del navegador local y vuelva a acceder a la página.
   * Añada `?` al final de la URL de la página. Por ejemplo:

      `http://localhost:4502/sites.html/content?`

      Esta acción solicitará la página directamente desde AEM y omitirá a Dispatcher. Si recibe la página actualizada quiere decir que debe borrar la caché de Dispatcher.

   * Póngase en contacto con el administrador del sistema si hay problemas con las colas de replicación.

## Barra de tareas no visible {#sidekick-not-visible}

* **Problema**:

   * La barra de tareas no está visible al editar una página de contenido en el entorno de creación.

* **Motivo**:

   * En casos excepcionales, es posible que haya colocado el encabezado de la barra de tareas fuera del ámbito de la ventana actual. Esto significa que no puede volver a colocarlo.

* **Solución**:

   * Cierre la sesión actual y vuelva a iniciarla. La barra de tareas volverá a la posición predeterminada.

## Buscar y reemplazar: no se reemplazan todas las instancias {#find-replace-not-all-instances-are-replaced}

* **Problema:**

   * Al usar la variable **Buscar y reemplazar** puede suceder que no todas las instancias de la variable `find` en una página.

* **Motivo**:

   * La capacidad de **Buscar y reemplazar** depende de cómo se guarde el contenido y de si se puede buscar. Por ejemplo, un texto de blog se almacena en `jcr:text` que no está configurada para ser buscada. El ámbito predeterminado para el servlet de buscar y reemplazar cubre las siguientes propiedades:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Solución**:

   * Estas definiciones se pueden cambiar con la configuración de **Servlet Find Replace Day CQ WCM** usando la variable **Consola web**; por ejemplo, en

      `http://localhost:4502/system/console/configMgr`
