---
title: Minificación de los archivos JavaScript
seo-title: Minification of the JavaScript files
description: Instrucciones para generar código minificado después de las personalizaciones de AEM Forms Workspace para optimizar los archivos JS para la web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 87%

---

# Minificación de los archivos JavaScript {#minification-of-the-javascript-files}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La minificación elimina del código fuente los caracteres redundantes, como los espacio en blanco, las líneas nuevas y los comentarios. Esto mejora el rendimiento al reducir el tamaño del código. Aunque la minificación no afecta a la funcionalidad, reduce la legibilidad del código.

Para generar código minificado para cambios semánticos, siga los siguientes pasos.

1. Copie `client-html/src/main/webapp/js` desde src-package en el sistema de archivos.

   >[!NOTE]
   >
   >Consulte [Introducción a la personalización de AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md) para obtener más información sobre los paquetes.

1. Actualice las rutas de `main.js`, ubicado en client-html/src/main/webapp/js, para obtener modelos o vistas agregados o actualizados.

   Por ejemplo, si se agrega un nuevo modelo de Sharequeue, por ejemplo, mySharequeue, cambie lo siguiente:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Actualice `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` en el caso de que haya algún cambio o adición de alias en `main.js`.

   Por ejemplo, si se agrega un nuevo modelo de Sharequeue, por ejemplo, mySharequeue, cambie lo siguiente:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Ejecute el siguiente comando en client-html/src/main/webapp/js/minifier:

   ```shell
   mvn clean install
   ```

   Este comando genera una carpeta de archivos minificados en client-html/src/main/webapp/js en la que main.js y register.js están minificados.

>[!NOTE]
>
>La minificación solo es compatible con JVM de 64 bits.

>[!NOTE]
>
>Si utiliza la minificación, la actualización se verá afectada.
