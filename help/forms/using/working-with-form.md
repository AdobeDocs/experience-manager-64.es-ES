---
title: Trabajar con un formulario
seo-title: Working with a Form
description: Ver y actualizar el formulario asociado a una tarea o punto de inicio en la aplicación de AEM Forms
seo-description: View and update the form associated with a task or Startpoint in the AEM Forms app
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
exl-id: ae565dbd-2631-4364-89f7-675700b43320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 89%

---

# Trabajar con un formulario {#working-with-a-form}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Si un formulario está habilitado para la sincronización en la aplicación de Forms, este se descarga y puede trabajar con él directamente.

Los formularios se descargan en la aplicación y están disponibles sin conexión. Por ejemplo, ejecuta una empresa bancaria y un cliente rellena una solicitud en su sitio. La solicitud es un formulario adaptable que acepta información de sus clientes y la almacena para revisarla. El administrador revisa el formulario y crea un formulario de verificación en la instancia de autor de AEM. El administrador habilita la sincronización del formulario con la aplicación de AEM Forms. Si el formulario de verificación está disponible en la aplicación de AEM Forms, su agente de campo puede utilizar un dispositivo móvil para comprobar los detalles del cliente. El dispositivo móvil se sincroniza con el servidor y el formulario de verificación se carga en la aplicación. Su agente de campo puede visitar a su cliente, comprobar los detalles, guardar datos como borrador o enviar el formulario de verificación. El formulario se sincroniza con el servidor cada vez que la aplicación está en línea.

Para sincronizar su formulario en la aplicación de AEM Forms:

1. En la instancia de autor, seleccione un formulario y haga clic en **Ver propiedades**.

1. En la página Propiedades, haga clic en **Avanzadas**.
1. En Avanzadas, habilite la opción: **Sincronizar con la aplicación de AEM Forms** y pulse **Guardar**.

Para sincronizar varios formularios, en la instancia de autor, seleccione varios formularios en el administrador de formularios y pulse **Sincronizar con la aplicación de AEM Forms**. Cuando se publica el formulario, la aplicación de AEM Forms puede conectarse al servidor de publicación y recuperar los formularios.

>[!NOTE]
>
>Formularios admitidos:
>
>* Formularios adaptables (sin carga diferida)
>* Mobile Forms
>
>Los archivos adjuntos de nivel de formulario no son compatibles con los formularios adaptables recuperados en la aplicación de AEM Forms sincronizados con el servidor OSGi de AEM Forms. Los usuarios pueden adjuntar archivos en un campo si el autor ha habilitado los archivos adjuntos de nivel de campo en el momento de crear el formulario.

**Para abrir y actualizar un formulario**

1. Para abrir un formulario, pulse el formulario en la pantalla principal.
1. Puede actualizar los campos del formulario, agregar archivos adjuntos, guardar como borrador y enviarlo.
