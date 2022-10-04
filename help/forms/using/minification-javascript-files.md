---
title: Minificación de los archivos JavaScript
seo-title: Minification of the JavaScript files
description: Instrucciones para generar código minificado después de las personalizaciones del espacio de trabajo de AEM Forms para optimizar los archivos JS para la web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Minificación de los archivos JavaScript {#minification-of-the-javascript-files}

La minificación elimina del código fuente los caracteres redundantes, como espacio en blanco, nueva línea y comentarios. Esto mejora el rendimiento al reducir el tamaño del código. Aunque la minificación no afecta a la funcionalidad, reduce la legibilidad del código.

Para generar código minificado para cambios semánticos, siga estos pasos.

1. Copiar `client-html/src/main/webapp/js` desde src-package en el sistema de archivos.

   >[!NOTE]
   >
   >Consulte [Introducción a la personalización del espacio de trabajo de AEM Forms](/help/forms/using/introduction-customizing-html-workspace.md) para obtener más información sobre los paquetes.

1. Actualizar rutas en `main.js` ubicado en client-html/src/main/webapp/js, para obtener modelos/vistas agregados/actualizados.

   Por ejemplo, si se agrega un nuevo modelo de Sharequeue, por ejemplo, mySharequeue, cambie:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Actualizar `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` en caso de que haya un cambio/adición de alias en `main.js`.

   Por ejemplo, si se agrega un nuevo modelo de Sharequeue, por ejemplo, mySharequeue, cambie:

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

1. En client-html/src/main/webapp/js/minifier, ejecute el comando:

   ```shell
   mvn clean install
   ```

   Genera una carpeta de archivos minificados, en client-html/src/main/webapp/js con main.js y register.js minificados.

>[!NOTE]
>
>La minificación solo funcionará en JVM de 64 bits.

>[!NOTE]
>
>Si minimiza, la actualización se verá afectada.
