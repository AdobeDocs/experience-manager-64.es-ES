---
title: Ejecutar AEM Forms en modo de mantenimiento
seo-title: Running AEM forms in maintenance mode
description: El modo de mantenimiento es útil cuando se realizan tareas como parchear un DSC, actualizar AEM formularios o aplicar un Service Pack. Obtenga más información sobre la ejecución de AEM formularios en el modo de mantenimiento.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 11%

---

# Ejecutar AEM Forms en modo de mantenimiento {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El modo de mantenimiento es útil cuando se realizan tareas como parchear un DSC, actualizar AEM formularios o aplicar un Service Pack.

Evite invocar procesos mientras el servidor está en modo de mantenimiento. Esto es lo que sucede si se invoca un proceso mientras el servidor está en modo de mantenimiento:

* Si el proceso dura mucho tiempo, se agrega a la base de datos de trabajos, pero no se inicia. Al salir del modo de mantenimiento, AEM forms procesa los trabajos de larga duración en su cola, incluso si el servidor se reinició en el modo de mantenimiento.
* Si el proceso es de corta duración, se procesa de inmediato.

**Poner AEM formularios en modo de mantenimiento**

1. En un explorador web, introduzca:

   `https://`*[hostname ]*`:`*[puerto]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[nombre de usuario del administrador ]*`&password=`*[password]*

   Se muestra un mensaje &quot;ahora en pausa&quot; en la ventana del explorador.

   >[!NOTE]
   >
   >Si apaga el servidor mientras está en modo de mantenimiento, seguirá en modo de mantenimiento cuando se reinicie. Debe desactivar el modo de mantenimiento cuando haya terminado sus tareas de mantenimiento.

**Comprobar si AEM formularios se están ejecutando en el modo de mantenimiento**

1. En un explorador web, introduzca:

   `https://`*[hostname]:[puerto ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[nombre de usuario del administrador]* `&password=`*[password ]*

   El estado se muestra en la ventana del explorador. El estado &quot;true&quot; indica que el servidor se está ejecutando en modo de mantenimiento y &quot;false&quot; indica que el servidor no está en modo de mantenimiento.

**Desactivar modo de mantenimiento**

1. En un explorador web, introduzca:

   `https://`*[hostname]:[puerto ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[nombre de usuario del administrador]* `&password=`*[password ]*

   Se muestra un mensaje &quot;ahora en ejecución&quot; en la ventana del explorador.
