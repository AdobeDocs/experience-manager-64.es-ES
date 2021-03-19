---
title: Configuración de mensajería
seo-title: Configuración de mensajería
description: Mensajería de comunidades
seo-description: Mensajería de comunidades
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Administrador
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 1%

---


# Configuración de la mensajería {#configuring-messaging}

## Información general {#overview}

La función de mensajería para AEM Communities permite a los visitantes del sitio (miembros) con sesión iniciada enviar mensajes entre sí a los que se puede acceder desde la sesión iniciada en el sitio.

La mensajería está habilitada para un sitio de la comunidad marcando una casilla durante la [creación del sitio de la comunidad](sites-console.md).

En esta página hay información sobre la configuración predeterminada y los posibles ajustes.

Para obtener información adicional para desarrolladores, consulte [Messaging Essentials](essentials-messaging.md).

## Servicio de operaciones de mensajería {#messaging-operations-service}

El [Servicio de operaciones de mensajería de AEM Communities](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica el punto final que gestiona las solicitudes relacionadas con la mensajería, las carpetas que debe utilizar el servicio para almacenar mensajes y, si los mensajes pueden incluir archivos adjuntos, qué tipos de archivo están permitidos.

Para los sitios de la comunidad creados con la consola [Communities Sites](sites-console.md), ya existe una instancia del servicio, con la bandeja de entrada configurada como `/mail/community/inbox`.

### Servicio de operaciones de mensajería de la comunidad {#community-messaging-operations-service}

Como se muestra a continuación, existe una configuración del servicio para los sitios creados con el [asistente de creación de sitios](sites-console.md). La configuración se puede ver o editar seleccionando el icono de lápiz junto a la configuración:

![imagen_1-63](assets/chlimage_1-63.png)

### Nueva configuración {#new-configuration}

Para agregar una nueva configuración, seleccione el icono &quot;**+**&quot; junto al nombre del servicio:

![imagen_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Lista de]**
permitidos de campos de mensajeEspecifica las propiedades del componente Mensaje de composición que los usuarios pueden editar y mantener. Si se añaden nuevos elementos de formulario, sería necesario añadir el id de elemento si se desea almacenar en SRP. El valor predeterminado son dos entradas: 
** asunto y  *contenido*.

* **[!UICONTROL Límite de tamaño del cuadro de mensajeEl número máximo de bytes en el cuadro de mensaje de cada usuario.]**
El valor predeterminado es 
*1073741824*  (1 GB).

* **[!UICONTROL Número total de mensajes permitidos]**
por usuario. El valor -1 indica que se permite un número ilimitado de mensajes, sujeto al límite de tamaño del cuadro de mensaje. El valor predeterminado es 
*1000*  (10k).

* **[!UICONTROL Notificar]**
error de entregaSi está activado, notifique al remitente si la entrega de mensajes falla en algunos destinatarios. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL Error en la entrega del remitente]**
idName del remitente que aparece en el mensaje de error de la entrega. El valor predeterminado es 
*failureNotifier*.

* **[!UICONTROL La ruta de la plantilla de mensaje de error]**
ruta absoluta a la raíz de la plantilla de mensaje de error de la entrega. El valor predeterminado es 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNúmero de veces que se intenta reenviar el mensaje que no se puede entregar. El valor predeterminado es 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNúmero de segundos que hay que esperar entre los intentos de reenviar el mensaje si no se envía. El valor predeterminado es *100 *(segundos).

* **[!UICONTROL Recuento del]**
tamaño del grupo de actualizaciónNúmero de subprocesos simultáneos utilizados para la actualización del recuento. El valor predeterminado es 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obligatorio*) La ruta, relativa al nodo del usuario (/home/users/*username*), que se utilizará para la  **`inbox`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/inbox* .

* **[!UICONTROL sentiitems.path.name]**
(
*Obligatorio*) La ruta, relativa al nodo del usuario (/home/users/*username*), que se utilizará para la  **`senditems`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/sentiitems* .

* **[!UICONTROL supportAttachments.]**
nameSi se selecciona, los usuarios pueden agregar archivos adjuntos a sus mensajes. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL batchSize.]**
nameNumber de los mensajes que se van a agrupar para un envío al enviarlos a un grupo grande de destinatarios. El valor predeterminado es 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSi se marca supportAttachments , este valor especifica el tamaño total máximo permitido (en bytes) de todos los archivos adjuntos. El valor predeterminado es 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
namelista de bloqueados de extensiones de archivo con el prefijo &#39;
**.**&#39;, que será rechazado por el sistema. Si no está incluida en la lista de bloqueados, se permite la extensión. Las extensiones se pueden añadir o eliminar utilizando los iconos &#39;**+**&#39; y &#39;**-**&#39;. El valor predeterminado es *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Acción requerida*)** Una lista de permitidos de extensiones de archivo, lo contrario de la lista de bloqueados. Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el icono &#39;**-**&#39; para eliminar la única entrada vacía.

* **[!UICONTROL serviceSelector.name]**
(*Obligatorio*) Una ruta absoluta (extremo) a través de la cual se invoca el servicio (recurso virtual). La raíz de la ruta elegida debe estar incluida en la configuración *Rutas de ejecución* de la configuración OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/` y `/services/`. Para seleccionar esta configuración para la función de mensajería de un sitio, este extremo se proporciona como el valor **`Service selector`** para `Message List and Compose Message components` (consulte [Función del mensaje](configure-messaging.md)). El valor predeterminado es */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Lista de permitidos** Campos del mensaje.

>[!CAUTION]
>
>Cada vez que se abre una configuración `Messaging Operations Service` para su edición, si se ha eliminado `allowedAttachmentTypes.name`, se vuelve a añadir una entrada vacía para que la propiedad se pueda configurar. Una sola entrada vacía deshabilita los archivos adjuntos.
>
>Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el icono &#39;**-**&#39; para eliminar (de nuevo) la única entrada vacía antes de hacer clic en **[!UICONTROL Guardar]**.

## Solución de problemas {#troubleshooting}

Una manera de solucionar los problemas es habilitar los [mensajes de depuración en el registro.](../../help/sites-administering/troubleshooting.md)

Consulte también [Loggers and Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

El paquete a monitorizar es `com.adobe.cq.social.messaging`.
