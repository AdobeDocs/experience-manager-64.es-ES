---
title: Función de mensajería
seo-title: Función de mensajería
description: Configuración de componentes de mensajería
seo-description: Configuración de componentes de mensajería
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# Función de mensajería {#messaging-feature}

Además de las interacciones públicamente visibles que se producen en los foros y comentarios, la función de mensajería de AEM Communities permite a los miembros de la comunidad interactuar entre sí de forma más privada.

Esta característica puede incluirse cuando se crea un [sitio de comunidad](overview.md#communitiessites).

Las funciones de mensajería permiten:

* Envío de un mensaje a uno o varios miembros de la comunidad
* Envío de un mensaje a un grupo de miembros de la comunidad
* Envío de un mensaje con datos adjuntos
* Reenviar un mensaje
* Responder a un mensaje
* Eliminar un mensaje
* Restaurar un mensaje eliminado

Para habilitar y modificar la función de mensajería, visite

* [Configuración de ](messaging.md) mensajes para administradores
* [Messaging ](essentials-messaging.md) Essentials para desarrolladores

>[!NOTE]
>
>No se admite la adición de `Compose Message, Message, or Message List` componentes (que se encuentra en `Communities`grupo de componentes) a una página en modo de edición de autor.

## Configuración de componentes de mensajería {#configuring-messaging-components}

Cuando se habilita la mensajería para un sitio de comunidad, se configura completamente sin necesidad de realizar ninguna otra configuración. Esta información se proporciona si es necesario cambiar la configuración predeterminada.

### Configuración de la Lista de mensajes (messagebox) {#configuring-message-list-messagebox}

Para modificar la configuración de la lista de mensajes para las páginas **Bandeja de entrada**, **Elementos enviados** y **Papelera** de la función de mensajería, abra el sitio en [modo de edición del autor](sites-console.md#authoring-site-content).

En el modo `Preview`, seleccione el vínculo **[!UICONTROL Mensajes]** para abrir la página de mensajería principal. A continuación, seleccione **[!UICONTROL Bandeja de entrada, Elementos enviados o Papelera]** para configurar el componente para esa lista de mensajes.

En el modo `Edit`, seleccione el componente en la página.

Para acceder al cuadro de diálogo de configuración, es necesario cancelar la herencia seleccionando el icono `link`.

Una vez completada la configuración, es necesario restaurar la herencia seleccionando el icono `broken link`.

![chlimage_1-396](assets/chlimage_1-396.png)

Una vez cancelada la herencia, será posible seleccionar el icono `configure` para abrir el cuadro de diálogo de configuración.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Ficha básica {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Selector]**
 de servicio (*obligatorio*) Establezca este valor en el valor de la propiedad  `serviceSelector.name` del servicio [ de operaciones de mensajería de ](messaging.md#messaging-operations-service)AEM Communities.

* **[!UICONTROL Página]**
 de composición (*obligatoria*) La página que se abrirá cuando un miembro haga clic en el  `Reply` botón. La página de destinatario debe contener el formulario **[!UICONTROL Redactar mensaje]**.

* **[!UICONTROL Responder/Vista como]**
recursoSi se selecciona, la URL de respuesta y la URL de Vista harán referencia a un recurso; de lo contrario, los datos se pasarán como parámetros de consulta en la dirección URL.

* **[!UICONTROL Formulario para mostrar perfil]**
Formulario de perfil que se utiliza para mostrar el perfil de los remitentes.

* **[!UICONTROL Carpeta]**
de papeleraSi está activada, este componente de Lista de mensajes solo muestra los mensajes marcados como eliminados (papelera).

* **[!UICONTROL Rutas]**
 de carpeta (*obligatorio*) Referencia a los valores establecidos para  `inbox.path.name` y  `sentitems.path.name` en el servicio [ de operaciones de mensajería de ](messaging.md#messaging-operations-service)AEM Communities. Al configurar para un `Inbox`, agregue una entrada usando el valor de `inbox.path.name`. Al configurar para un `Outbox`, agregue una entrada usando el valor de `sentitems.path.name`. Al configurar para `Trash`, agregue dos entradas con ambos valores.

#### Mostrar ficha {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Marcar]**
botón de lecturaSi está marcado, muestra un 
`Read`que permite marcar un mensaje como leído.

* **[!UICONTROL Marcar]**
botón sin leerSi está marcado, muestra un 
`Mark Unread` que permite marcar un mensaje como leído.

* **[!UICONTROL Eliminar]**
botónSi está marcado, muestra un 
`Delete`que permite marcar un mensaje como leído. Duplicado la funcionalidad de eliminación si también se selecciona **`Message Options`**.

* **[!UICONTROL Opciones de]**
mensajeSi se selecciona, se muestra 
**`Reply`**,  **`Reply All`**,  **`Forward`** y  **`Delete`** botones que permiten que un mensaje se vuelva a enviar o se elimine. Duplicado la funcionalidad de eliminación si también se selecciona **`Delete Button`**.

* **[!UICONTROL Mensajes por]**
página El número especificado es el número máximo de mensajes que se muestran por página en un esquema de paginación. Si no se especifica ningún número (se deja en blanco), se muestran todos los mensajes y no hay paginación.

* **[!UICONTROL Patrones]**
de marca de horaProporcione patrones de marca de hora para uno o más idiomas. El valor predeterminado es en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Mostrar]**
usuarioElija una de estas opciones 
**`Sender`** o  **`Recipients`** para determinar si desea mostrar el remitente o los Destinatarios.

### Configuración del mensaje de composición {#configuring-compose-message}

Para modificar la configuración de la página de mensaje de composición, abra el sitio en [modo de edición del autor](sites-console.md#authoring-site-content).

En el modo `Preview`seleccione el vínculo **[!UICONTROL Mensajes]** para abrir la página de mensajería principal. A continuación, seleccione el botón Nuevo mensaje para abrir la página `Compose Message`.

En el modo `Edit`, seleccione el componente principal en la página que contiene el cuerpo del mensaje.

Para acceder al cuadro de diálogo de configuración, es necesario cancelar la herencia seleccionando el icono `link`.

Una vez completada la configuración, es necesario restaurar la herencia seleccionando el icono `broken link`.

![chlimage_1-400](assets/chlimage_1-400.png)

Una vez cancelada la herencia, será posible seleccionar el icono `configure` para abrir el cuadro de diálogo de configuración.

![chlimage_1-481](assets/chlimage_1-401.png)

#### Ficha básica {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL Dirección]**
URL de redirecciónIntroduzca la dirección URL de la página que se muestra después de enviar el mensaje. Por ejemplo, 
`../messaging.html`.

* **[!UICONTROL Cancelar]**
URLntroduzca la dirección URL de la página que se muestra si el remitente cancela el mensaje. Por ejemplo, 
`../messaging.html`.

* **[!UICONTROL Longitud máxima del]**
asunto del mensajeEl número máximo de caracteres permitidos en el campo Asunto. Por ejemplo, 500. El valor predeterminado no es límite.

* **[!UICONTROL Longitud máxima del]**
cuerpo del mensaje El número máximo de caracteres permitidos en el campo Contenido. Por ejemplo, 10000. El valor predeterminado no es límite.

* **[!UICONTROL Selector]**
 de servicio (*obligatorio*) Establezca este valor en el valor de la propiedad  **`serviceSelector.name`** del servicio [ de operaciones de mensajería de ](messaging.md#messaging-operations-service)AEM Communities.

#### Mostrar ficha {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostrar]**
campo AsuntoSi está marcado, muestre la variable 
`Subject` y habilitar la adición de un asunto al mensaje. El valor predeterminado no está marcado.

* **[!UICONTROL Etiqueta]**
de asuntoIntroduzca el texto que desea mostrar junto a la variable 
`Subject` field. El valor predeterminado es `Subject`.

* **[!UICONTROL Mostrar]**
campo Adjuntar archivoSi está marcado, muestre la variable 
`Attachment` y activar la adición de archivos adjuntos al mensaje. El valor predeterminado no está marcado.

* **[!UICONTROL Adjuntar]**
etiqueta de archivoIntroduzca el texto que desea mostrar junto a la variable 
`Attachment` , seleccione una de las siguientes opciones. El valor predeterminado es **`Attach File`**.

* **[!UICONTROL Mostrar]**
campo de contenidoSi está marcado, muestre la variable 
`Content` y activar la adición de un cuerpo de mensaje. El valor predeterminado no está marcado.

* **[!UICONTROL Etiqueta de]**
contenidoIntroduzca el texto que se mostrará junto a la variable 
`Content` , seleccione una de las siguientes opciones. El valor predeterminado es **`Body`**.

* **[!UICONTROL Con el]**
Editor de texto enriquecidoSi está activado, indica el uso de un cuadro de texto de contenido personalizado con su propio editor de texto enriquecido. El valor predeterminado no está marcado.

* **[!UICONTROL Patrones]**
de marca de horaProporcione patrones de marca de hora para uno o más idiomas. El valor predeterminado es en, de, fr, it, es, ja, zh_CN, ko_KR.

