---
title: Elementos básicos de mensajería
seo-title: Messaging Essentials
description: Información general del componente Mensajería
seo-description: Messaging component overview
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 4%

---

# Elementos básicos de mensajería {#messaging-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página documenta los detalles de cómo trabajar con el componente Mensajería para incluir una función de mensajería en un sitio web.

## Elementos esenciales para el cliente {#essentials-for-client-side}

**Componer mensaje**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemmessage</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>propiedades</strong></td> 
   <td>see <a href="configure-messaging.md">Configuración de mensajería</a></td> 
  </tr> 
  <tr> 
   <td><strong>configuración de administración</strong></td> 
   <td><a href="messaging.md">Configuración de mensajería</a></td> 
  </tr> 
 </tbody> 
</table>

**Lista de mensajes** (para Bandeja de entrada, Enviado y Papelera)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>propiedades</strong></td> 
   <td>Consulte <a href="configure-messaging.md">Configuración de mensajería</a></td> 
  </tr> 
  <tr> 
   <td><strong>configuración de administración</strong></td> 
   <td><a href="messaging.md">Configuración de mensajería</a></td> 
  </tr> 
 </tbody> 
</table>

Consulte también [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [Configuración de mensajería](configure-messaging.md)

* [API de cliente de mensajería](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) para componentes SCF

* [API de mensajería](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) para el servicio

* [Puntos finales de mensajería](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

>[!CAUTION]
>
>El parámetro String *no *debe contener una barra diagonal &quot;/&quot; para los siguientes métodos de MessageBuilder:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>Por ejemplo:
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Sitio de la comunidad {#community-site}

Una estructura de sitio de comunidad, creada con el asistente, incluirá la función de mensajería cuando se seleccione. Consulte `User Management` configuración de [Consola Sitios de la comunidad](sites-console.md#user-management).

### Código de ejemplo: Notificación de mensaje recibido {#sample-code-message-received-notification}

La función Mensajería social lanza eventos para operaciones, por ejemplo `send`, `marking read`, `marking delete`. Estos eventos se pueden capturar y se pueden realizar acciones con los datos contenidos en el evento.

El siguiente ejemplo es de un controlador de eventos que escucha el `message sent` y envía un correo electrónico a todos los destinatarios de mensajes utilizando la variable `Day CQ Mail Service`.

Para probar el script de ejemplo del lado del servidor, necesitará un entorno de desarrollo y la capacidad de crear un paquete OSGi.

1. Inicie sesión como administrador para ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. Cree un `bundle node`en `/apps/engage/install` con nombres arbitrarios, como

   * **[!UICONTROL Nombre simbólico]**: com.comprometer.media.social.messaging.MessagingNotification
   * **[!UICONTROL Nombre]**: Notificación de mensaje de tutorial de introducción
   * **[!UICONTROL Descripción]**: un servicio de ejemplo para enviar una notificación por correo electrónico a los usuarios cuando reciban un mensaje
   * **[!UICONTROL Paquete]**: `com.engage.media.social.messaging.notification`

1. Navegue hasta `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. Elimine el `Activator.java` clase creada automáticamente
   1. Crear clase `MessageEventHandler.java`
   1. Copie/pegue el código siguiente en `MessageEventHandler.java`

1. Haga clic en **[!UICONTROL Guardar todo]**
1. Vaya a `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` y añada todas las instrucciones de importación tal como se han escrito en la variable `MessageEventHandler.java` código.
1. Crear el paquete
1. Asegúrese `Day CQ Mail Service`El servicio OSGi está configurado
1. Inicie sesión como un usuario de demostración y envíe un correo electrónico a otro
1. El destinatario debe recibir un correo electrónico con respecto a un nuevo mensaje

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
