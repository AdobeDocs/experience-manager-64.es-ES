---
title: Configuración de notificaciones por correo electrónico
seo-title: Configuring Email Notification
description: Obtenga información sobre cómo configurar la notificación de correo electrónico en AEM.
seo-description: Learn how to configure Email Notification in AEM.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
exl-id: ea12035c-09b6-4197-ab23-c27fe71e7432
source-git-commit: 3a206c2fa8c18876b6e1481e2feb86857b5219c4
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 1%

---

# Configuración de notificaciones por correo electrónico{#configuring-email-notification}

AEM envía notificaciones por correo electrónico a los usuarios que:

* Se han suscrito a eventos de página, por ejemplo modificación o replicación. La sección [Bandeja de entrada de notificaciones](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) describe cómo suscribirse a estos eventos.

* Se han suscrito a eventos de foro.
* Debe realizar un paso en un flujo de trabajo. En la sección [Participant Step](/help/sites-developing/workflows-step-ref.md#participant-step) se describe cómo almacenar en déclencheur las notificaciones por correo electrónico en un flujo de trabajo.

Requisitos previos:

* Los usuarios deben tener una dirección de correo electrónico válida definida en su perfil.
* El **Servicio de correo de CQ de día** debe configurarse correctamente.

Cuando se notifica a un usuario, recibe un correo electrónico en el idioma definido en su perfil. Cada idioma tiene su propia plantilla que se puede personalizar. Se pueden añadir nuevas plantillas de correo electrónico para los nuevos idiomas.

>[!NOTE]
>
>Al trabajar con AEM hay varios métodos para administrar los ajustes de configuración de dichos servicios; consulte [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

## Configuración del servicio de correo {#configuring-the-mail-service}

Para AEM poder enviar correos electrónicos, el **Day CQ Mail Service** debe configurarse correctamente. Puede ver la configuración en la consola web. Al trabajar con AEM hay varios métodos para administrar los ajustes de configuración de dichos servicios; consulte [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) para obtener más información y las prácticas recomendadas.

Se aplican las siguientes restricciones:

* El **puerto del servidor SMTP** debe ser de 25 o superior.

* El **nombre de host del servidor SMTP** no debe estar en blanco.
* La dirección **&quot;From&quot;** no debe estar en blanco.

Para ayudarle a depurar un problema con el **Day CQ Mail Service**, puede ver los registros del servicio:

`com.day.cq.mailer.DefaultMailService`

La configuración tiene el siguiente aspecto en la consola web:

![chlimage_1-276](assets/chlimage_1-276.png)

## Configuración del canal de notificación de correo electrónico {#configuring-the-email-notification-channel}

Al suscribirse a las notificaciones de eventos de página o foro, la dirección de correo electrónico de se establece en `no-reply@acme.com` de forma predeterminada. Puede cambiar este valor configurando el servicio **Notification Email Channel** en la consola web.

Para configurar la dirección de correo electrónico, agregue un nodo `sling:OsgiConfig` al repositorio. Utilice el siguiente procedimiento para añadir el nodo directamente mediante el CRXDE Lite :

1. En el CRXDE Lite, agregue una carpeta denominada `config` debajo de la carpeta de la aplicación.
1. En la carpeta de configuración, añada un nodo denominado:

   `com.day.cq.wcm.notification.email.impl.EmailChannel` de tipo  `sling:OsgiConfig`

1. Agregue una propiedad `String` al nodo llamado `email.from`. Para el valor, especifique la dirección de correo electrónico que desea utilizar.

1. Haga clic en **Guardar todo**.

Utilice el siguiente procedimiento para definir el nodo en las carpetas de origen del paquete de contenido:

1. En `jcr_root/apps/*app_name*/config folder`, cree un archivo con el nombre `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`

1. Añada el siguiente XML para representar el nodo :

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. Reemplace el valor del atributo `email.from` ( `name@server.com`) por su dirección de correo electrónico.

1. Guarde el archivo.

## Configuración del servicio de notificación de correo electrónico del flujo de trabajo {#configuring-the-workflow-email-notification-service}

Cuando recibe notificaciones por correo electrónico del flujo de trabajo, tanto la dirección de correo electrónico como el prefijo de URL del host se establecen en valores predeterminados. Puede cambiar estos valores configurando el **Day CQ Workflow Email Notification Service** en la consola web. Si lo hace, se recomienda mantener el cambio en el repositorio.

La configuración predeterminada tiene el siguiente aspecto en la consola web:

![chlimage_1-277](assets/chlimage_1-277.png)

### Plantillas de correo electrónico para notificaciones de página {#email-templates-for-page-notification}

A continuación se describen las plantillas de correo electrónico para las notificaciones de página:

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

La plantilla predeterminada en inglés ( `en.txt`) se define de la siguiente manera:

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Personalización de plantillas de correo electrónico para notificaciones de página {#customizing-email-templates-for-page-notification}

Para personalizar la plantilla de correo electrónico en inglés para la notificación de página:

1. En CRXDE, abra el archivo :

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. Modifique el archivo según sus necesidades.
1. Guarde los cambios.

La plantilla debe tener el siguiente formato:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Donde &lt;text_x> puede ser una mezcla de texto estático y variables de cadena dinámicas. En la plantilla de correo electrónico para las notificaciones de página se pueden usar las siguientes variables:

* `${time}`, la fecha y hora del evento.

* `${userFullName}`, el nombre completo del usuario que activó el evento.

* `${userId}`, el ID del usuario que activó el evento.
* `${modifications}`, describe el tipo de evento de página y la ruta de página en formato :

   &lt;page event=&quot;&quot; type=&quot;&quot;> =>  &lt;page path=&quot;&quot;>

   Por ejemplo:

   PageModified => /content/geometrixx/en/products

### Plantillas de correo electrónico para la notificación del foro {#email-templates-for-forum-notification}

Las plantillas de correo electrónico para las notificaciones del foro se encuentran en:

`/etc/notification/email/default/com.day.cq.collab.forum`

La plantilla predeterminada en inglés ( `en.txt`) se define de la siguiente manera:

```xml
subject=[CQ Forum Notification]

header=-------------------------------------------------------------------------------------\n \
Time: Time: ${time}\n \
Forum Page Path: ${forum.path}\n \
-------------------------------------------------------------------------------------\n\n

message=Page: ${host.prefix}${forum.path}.html\n

footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Personalización de plantillas de correo electrónico para notificaciones de foro {#customizing-email-templates-for-forum-notification}

Para personalizar la plantilla de correo electrónico en inglés para la notificación del foro:

1. En CRXDE, abra el archivo :

   `/etc/notification/email/default/com.day.cq.collab.forum/en.txt`

1. Modifique el archivo según sus necesidades.
1. Guarde los cambios.

La plantilla debe tener el siguiente formato:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Donde `<text_x>` puede ser una mezcla de texto estático y variables de cadena dinámicas.

En la plantilla de correo electrónico para las notificaciones del foro se pueden utilizar las siguientes variables:

* `${time}`, la fecha y hora del evento.

* `${forum.path}`, la ruta a la página del foro.

### Plantillas de correo electrónico para notificación de flujo de trabajo {#email-templates-for-workflow-notification}

La plantilla de correo electrónico para las notificaciones de flujo de trabajo (en inglés) se encuentra en:

`/libs/settings/workflow/notification/email/default/en.txt`

Se define de la siguiente manera:

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Personalización de plantillas de correo electrónico para notificación de flujo de trabajo {#customizing-email-templates-for-workflow-notification}

Para personalizar la plantilla de correo electrónico en inglés para la notificación de eventos de flujo de trabajo:

1. En CRXDE, abra el archivo :

   `/libs/settings/workflow/notification/email/default/en.txt`

1. Modifique el archivo según sus necesidades.
1. Guarde los cambios.

La plantilla debe tener el siguiente formato:

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>Donde `<text_x>` puede ser una mezcla de texto estático y variables de cadena dinámicas. Cada línea de un elemento `<text_x>` debe terminar con una barra invertida ( `\`), excepto la última instancia, cuando la ausencia de la barra invertida indica el final de la variable de cadena `<text_x>`.
>
>Puede encontrar más información sobre el formato de la plantilla en los [javadocs del método Properties.load()](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-).

El método `${payload.path.open}` revela la ruta a la carga útil del elemento de trabajo. Por ejemplo, para una página en Sitios, entonces `payload.path.open` sería similar a `/bin/wcmcommand?cmd=open&path=…`.; esto no tiene el nombre del servidor, por lo que la plantilla antepone esto a `${host.prefix}`.

En la plantilla de correo electrónico se pueden utilizar las siguientes variables:

* `${event.EventType}`, tipo de evento
* `${event.TimeStamp}`, fecha y hora del evento
* `${event.User}`, el usuario que activó el evento
* `${initiator.home}`, la ruta del nodo iniciador

* `${initiator.name}`, el nombre del iniciador

* `${initiator.email}`, dirección de correo electrónico del iniciador
* `${item.id}`, el id del elemento de trabajo
* `${item.node.id}`, id del nodo en el modelo de flujo de trabajo asociado a este elemento de trabajo
* `${item.node.title}`, título del elemento de trabajo
* `${participant.email}`, dirección de correo electrónico del participante
* `${participant.name}`, nombre del participante
* `${participant.familyName}`, apellido del participante
* `${participant.id}`, id del participante
* `${participant.language}`, el idioma del participante
* `${instance.id}`, el id del flujo de trabajo
* `${instance.state}`, el estado del flujo de trabajo
* `${model.title}`, título del modelo de flujo de trabajo
* `${model.id}`, el id del modelo de flujo de trabajo

* `${model.version}`, la versión del modelo de flujo de trabajo
* `${payload.data}`, la carga útil

* `${payload.type}`, el tipo de carga útil
* `${payload.path}`, ruta de la carga útil
* `${host.prefix}`, prefijo de host, por ejemplo: http://localhost:4502

### Adición de una plantilla de correo electrónico para un nuevo idioma {#adding-an-email-template-for-a-new-language}

Para añadir una plantilla para un nuevo idioma:

1. En CRXDE, añada un archivo `<language-code>.txt` a continuación:

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page` : para notificaciones de página
   * `/etc/notification/email/default/com.day.cq.collab.forum` : para notificaciones de foro
   * `/libs/settings/workflow/notification/email/default` : para notificaciones de flujo de trabajo

1. Adapte el archivo al idioma.
1. Guarde los cambios.

>[!NOTE]
>
>El `<language-code>` utilizado como nombre de archivo para la plantilla de correo electrónico debe ser un código de idioma en minúsculas de dos letras que AEM reconozca. Para códigos de idioma, AEM se basa en ISO-639-1.

## Configuración de las notificaciones por correo electrónico de AEM Assets {#assetsconfig}

Cuando se comparten o dejan de compartir colecciones en AEM Assets, los usuarios pueden recibir notificaciones por correo electrónico de AEM. Para configurar las notificaciones por correo electrónico, siga estos pasos.

1. Configure el servicio de correo electrónico, tal como se describe anteriormente en [Configuración del servicio de correo](/help/sites-administering/notification.md#configuring-the-mail-service).
1. Inicie sesión en AEM como administrador. Haga clic en **Herramientas** > **Operaciones** > **Consola web** para abrir la Configuración de la consola web.
1. Edite **Day CQ DAM Resource Collection Servlet**. Seleccione **enviar correo electrónico**. Haga clic en **Guardar**.
