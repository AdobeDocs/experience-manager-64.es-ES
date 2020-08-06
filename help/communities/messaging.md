---
title: Configuración de mensajes
seo-title: Configuración de mensajes
description: Mensajería de las comunidades
seo-description: Mensajería de las comunidades
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Configuración de mensajes {#configuring-messaging}

## Información general {#overview}

La función de mensajería de AEM Communities permite que los visitantes del sitio (miembros) con sesión iniciada envíen mensajes entre sí a los que se puede acceder al iniciar sesión en el sitio.

La mensajería está habilitada para un sitio de comunidad marcando una casilla durante la creación [del sitio de](sites-console.md)comunidad.

En esta página encontrará información sobre la configuración predeterminada y los posibles ajustes.

Para obtener información adicional para desarrolladores, consulte [Messaging Essentials](essentials-messaging.md).

## Servicio de operaciones de mensajería {#messaging-operations-service}

El servicio [de operaciones de mensajería de](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities identifica el punto final que gestiona las solicitudes relacionadas con los mensajes, las carpetas que el servicio debe utilizar para almacenar mensajes y, si los mensajes pueden incluir archivos adjuntos, qué tipos de archivos están permitidos.

Para los sitios de comunidad creados con la consola [Sitios de](sites-console.md)comunidades, ya existe una instancia del servicio, con la bandeja de entrada configurada en `/mail/community/inbox`.

### Servicio de operaciones de mensajería de la comunidad {#community-messaging-operations-service}

Como se muestra a continuación, existe una configuración del servicio para los sitios creados con el asistente [de creación del](sites-console.md)sitio. La configuración se puede ver o editar seleccionando el icono de lápiz junto a la configuración:

![chlimage_1-63](assets/chlimage_1-63.png)

### New Configuration {#new-configuration}

Para agregar una nueva configuración, seleccione el icono más &#39;**+**&#39; junto al nombre del servicio:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Lista de permitidos]** Campos de mensaje Especifica las propiedades del componente Componer mensaje que los usuarios pueden editar y mantener. Si se agregan nuevos elementos de formulario, se deberá agregar la identificación del elemento si se desea almacenar en SRP. El valor predeterminado es dos entradas: 
*asunto* y *contenido*.

* **[!UICONTROL Límite]** de tamaño del cuadro de mensaje El número máximo de bytes en el cuadro de mensaje de cada usuario. El valor predeterminado es 
*1073741824* (1 GB).

* **[!UICONTROL Límite]** de recuento de mensajes El número total de mensajes permitidos por usuario. Un valor de -1 indica que se permite un número ilimitado de mensajes, con sujeción al límite de tamaño del cuadro de mensaje. El valor predeterminado es 
*10000* (10 k).

* **[!UICONTROL Error]** de notificación de envío Si está activado, notifique al remitente si el envío de mensajes falla en algunos destinatarios. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL Error en el envío del id. de remitente]** Nombre del remitente que aparece en el mensaje de error de envío. El valor predeterminado es 
*failNotifier*.

* **[!UICONTROL Ruta]** de la plantilla de mensaje de error La ruta absoluta de la plantilla de mensaje de envío falló. El valor predeterminado es 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]** Número de veces que se intenta reenviar el mensaje que no se puede entregar. El valor predeterminado es 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]** Número de segundos de espera entre los intentos de reenviar el mensaje si no se pudo enviar. El valor predeterminado es *100 *(segundos).

* **[!UICONTROL Tamaño]** del grupo de actualización de recuento Número de subprocesos simultáneos utilizados para la actualización de recuento. El valor predeterminado es 
*10*.

* **[!UICONTROL inbox.path.name]**(
*Requerido*) La ruta, relativa al nodo del usuario (/home/users/*username*), que se utilizará para la **`inbox`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**(
*Requerido*) La ruta, relativa al nodo del usuario (/home/users/*username*), que se utilizará para la **`senditems`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/sentiitems* .

* **[!UICONTROL supportAttachments.name]** Si se selecciona, los usuarios pueden agregar datos adjuntos a sus mensajes. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL batchSize.name]** Número de mensajes que se van a agrupar para un envío al enviar a un grupo grande de destinatarios. El valor predeterminado es 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** Si se comprueba supportAttachments, este valor especifica el tamaño total máximo permitido (en bytes) de todos los archivos adjuntos. El valor predeterminado es 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]** Una lista de bloqueados de extensiones de archivo, con el prefijo &#39;
**.**&#39;, que será rechazado por el sistema. Si no está incluida en la lista de bloqueados, se permite la extensión. Las extensiones pueden agregarse o eliminarse mediante los iconos &#39;**+**&#39; y &#39;**-**&#39;. El valor predeterminado es *PREDETERMINADO*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Acción requerida*)** Una lista de permitidos de extensiones de archivo, lo contrario de la lista de bloqueados. Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el icono &#39;**-**&#39; para eliminar la única entrada vacía.

* **[!UICONTROL serviceSelector.name]**(*Requerido*) Una ruta absoluta (extremo) a través de la cual se invoca el servicio (recurso virtual). La raíz de la ruta elegida debe estar incluida en la configuración de rutas *de* ejecución de la configuración de OSGi [`Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/`y `/services/`. Para seleccionar esta configuración para la función de mensajería de un sitio, este extremo se proporciona como el **`Service selector`** valor para la `Message List and Compose Message components` (consulte Función [de](configure-messaging.md)mensaje). El valor predeterminado es */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]** Use 
**Lista de permitidos** Campos de mensaje.

>[!CAUTION]
>
>Cada vez que se abre una `Messaging Operations Service` configuración para editarla, si `allowedAttachmentTypes.name` se ha eliminado, se vuelve a agregar una entrada vacía para que la propiedad se pueda configurar. Una sola entrada vacía deshabilita los archivos adjuntos de forma efectiva.
>
>Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el icono &#39;**-**&#39; para (de nuevo) eliminar la única entrada vacía antes de hacer clic en **[!UICONTROL Guardar]**.

## Solución de problemas {#troubleshooting}

Una manera de solucionar problemas es habilitar los mensajes de [depuración en el registro.](../../help/sites-administering/troubleshooting.md)

Consulte también [Registros y escritores para servicios](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)individuales.

El paquete que se debe supervisar es `com.adobe.cq.social.messaging`.
