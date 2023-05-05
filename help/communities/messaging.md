---
title: Configuración de mensajería
seo-title: Configuring Messaging
description: Mensajería de comunidades
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# Configuración de mensajería {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

La función de mensajería para AEM Communities permite a los visitantes del sitio (miembros) con sesión iniciada enviar mensajes entre sí a los que se puede acceder desde la sesión iniciada en el sitio.

La mensajería está habilitada para un sitio de la comunidad marcando una casilla durante [creación de sitios de comunidad](sites-console.md).

En esta página hay información sobre la configuración predeterminada y los posibles ajustes.

Para obtener información adicional para desarrolladores, consulte [Elementos básicos de mensajería](essentials-messaging.md).

## Servicio de operaciones de mensajería {#messaging-operations-service}

La variable [Servicio de operaciones de mensajería de AEM Communities](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica el punto final que gestiona las solicitudes relacionadas con la mensajería, las carpetas que debe utilizar el servicio para almacenar mensajes y, si los mensajes pueden incluir archivos adjuntos, qué tipos de archivos están permitidos.

Para sitios de comunidad creados con el [Consola Sitios de Communities](sites-console.md), ya existe una instancia del servicio, con la bandeja de entrada configurada como `/mail/community/inbox`.

### Servicio de operaciones de mensajería de la comunidad {#community-messaging-operations-service}

Como se muestra a continuación, existe una configuración del servicio para los sitios creados con la variable [asistente de creación de sitios](sites-console.md). La configuración se puede ver o editar seleccionando el icono de lápiz junto a la configuración:

![imagen_1-63](assets/chlimage_1-63.png)

### Nueva configuración {#new-configuration}

Para añadir una configuración nueva, seleccione el signo más **+** junto al nombre del servicio:

![imagen_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Lista de permitidos de campos del mensaje]**
Especifica las propiedades del componente Componer mensaje que los usuarios pueden editar y mantener. Si se añaden nuevos elementos de formulario, sería necesario añadir el id de elemento si se desea almacenar en SRP. El valor predeterminado son dos entradas: 
*subject* y *contenido*.

* **[!UICONTROL Límite de tamaño del cuadro de mensaje]**
Número máximo de bytes en el cuadro de mensaje de cada usuario. El valor predeterminado es 
*1073741824* (1 GB).

* **[!UICONTROL Límite de recuento de mensajes]**
El número total de mensajes permitidos por usuario. El valor -1 indica que se permite un número ilimitado de mensajes, sujeto al límite de tamaño del cuadro de mensaje. El valor predeterminado es 
*10000* (10 k).

* **[!UICONTROL Notificar el error de entrega]**
Si está activado, notifique al remitente si la entrega de mensajes falla en algunos destinatarios. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL Id. del remitente del envío de error]**
Nombre del remitente que aparece en el mensaje de error de entrega. El valor predeterminado es 
*failureNotifier*.

* **[!UICONTROL Ruta de la plantilla del mensaje de error]**
La ruta absoluta a la entrega produjo un error en la raíz de la plantilla de mensaje. El valor predeterminado es 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
Número de veces que se intenta reenviar el mensaje que no se puede entregar. El valor predeterminado es 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
Número de segundos que hay que esperar entre los intentos de reenviar el mensaje si no se ha enviado. El valor predeterminado es *100 *(segundos).

* **[!UICONTROL Recuento del tamaño del grupo de informes de actualización]**
Número de subprocesos simultáneos utilizados para la actualización del recuento. El valor predeterminado es 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Requerido*) La ruta, relativa al nodo del usuario (/home/users/*username*), para usar con la variable **`inbox`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/inbox* .

* **[!UICONTROL sentiitems.path.name]**
(
*Requerido*) La ruta, relativa al nodo del usuario (/home/users/*username*), para usar con la variable **`senditems`** carpeta. La ruta NO debe terminar con una barra diagonal final &#39;/&#39;. El valor predeterminado es */mail/sentiitems* .

* **[!UICONTROL supportAttachments.name]**
Si se selecciona, los usuarios pueden añadir archivos adjuntos a sus mensajes. El valor predeterminado es 
*comprobado*.

* **[!UICONTROL batchSize.name]**
Número de mensajes que se van a agrupar para un envío al enviarlos a un grupo grande de destinatarios. El valor predeterminado es 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
Si se selecciona supportAttachments , este valor especifica el tamaño total máximo permitido (en bytes) de todos los archivos adjuntos. El valor predeterminado es 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**
Una lista de bloqueados de extensiones de archivo con el prefijo &quot;
**.**&#39;, que será rechazado por el sistema. Si no está incluida en la lista de bloqueados, se permite la extensión. Las extensiones pueden agregarse o eliminarse utilizando la función **+**&#39; y &#39;**-**&#39;. El valor predeterminado es *PREDETERMINADO*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Acción requerida*)** Una lista de permitidos de extensiones de archivo, lo contrario de la lista de bloqueados. Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el **-** para eliminar la única entrada vacía.

* **[!UICONTROL serviceSelector.name]**
(*Requerido*) Una ruta absoluta (extremo) a través de la cual se invoca el servicio (recurso virtual). La raíz de la ruta elegida debe estar incluida en el *Rutas de ejecución* configuración de la configuración OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/`y `/services/`. Para seleccionar esta configuración para la función de mensajería de un sitio, este punto final se proporciona como la variable **`Service selector`** para la variable `Message List and Compose Message components` (consulte [Función de mensaje](configure-messaging.md)). El valor predeterminado es */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Uso 
**Lista de permitidos de campos del mensaje**.

>[!CAUTION]
>
>Cada vez que se `Messaging Operations Service` la configuración se abre para su edición, si `allowedAttachmentTypes.name` se ha eliminado, se vuelve a añadir una entrada vacía para que la propiedad se pueda configurar. Una sola entrada vacía deshabilita los archivos adjuntos.
>
>Para permitir todas las extensiones de archivo, excepto las incluidas en la lista de bloqueados, utilice el **-**&#39; para (de nuevo) quitar la única entrada vacía antes de hacer clic en **[!UICONTROL Guardar]**.

## Solución de problemas {#troubleshooting}

Una forma de solucionar problemas es habilitar [depuración de mensajes en el registro.](../../help/sites-administering/troubleshooting.md)

Consulte también [Registradores y escritores para servicios individuales](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

El paquete a monitorizar es `com.adobe.cq.social.messaging`.
