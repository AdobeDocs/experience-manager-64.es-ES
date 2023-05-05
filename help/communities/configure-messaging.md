---
title: Función de mensajería
seo-title: Messaging Feature
description: Configuración de componentes de mensajería
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 1%

---

# Función de mensajería {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Además de las interacciones públicamente visibles que se producen en los foros y comentarios, la función de mensajería de AEM Communities permite a los miembros de la comunidad interactuar entre sí de forma más privada.

Esta función se puede incluir cuando [sitio de la comunidad](overview.md#communitiessites) se crea.

Las funciones de mensajería permiten:

* Enviar un mensaje a uno o varios miembros de la comunidad
* Enviar un mensaje a un grupo de miembros de la comunidad
* Enviar un mensaje con archivos adjuntos
* Reenviar un mensaje
* Responder a un mensaje
* Eliminar un mensaje
* Restaurar un mensaje eliminado

Para habilitar y modificar la función de mensajería, visite

* [Configuración de mensajería](messaging.md) para administradores
* [Elementos básicos de mensajería](essentials-messaging.md) para desarrolladores

>[!NOTE]
>
>No se puede añadir `Compose Message, Message, or Message List` componentes (encontrados en `Communities`grupo de componentes) a una página en modo de edición de autor.

## Configuración de componentes de mensajería {#configuring-messaging-components}

Cuando la mensajería está habilitada para un sitio de comunidad, se configura completamente sin necesidad de ninguna configuración adicional. Esta información se proporciona si es necesario cambiar la configuración predeterminada.

### Configuración de la lista de mensajes (messagebox) {#configuring-message-list-messagebox}

Para modificar la configuración de la lista de mensajes para **Bandeja de entrada**, **Elementos enviados** y **Papelera** páginas de la función de mensajería, abra el sitio en [modo de edición de autor](sites-console.md#authoring-site-content).

En `Preview` seleccione **[!UICONTROL Mensajes]** para abrir la página de mensajería principal. A continuación, seleccione **[!UICONTROL Bandeja de entrada, elementos enviados o Papelera]** para configurar el componente de esa lista de mensajes.

En `Edit` seleccione el componente en la página.

Para acceder al cuadro de diálogo de configuración, es necesario cancelar la herencia seleccionando la opción `link`icono.

Una vez completada la configuración, es necesario restaurar la herencia seleccionando la opción `broken link` icono.

![chlimage_1-396](assets/chlimage_1-396.png)

Una vez cancelada la herencia, es posible seleccionar la variable `configure` para abrir el cuadro de diálogo de configuración.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Pestaña Básicos {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Selector de servicio]**
(*Requerido*) Establezca este valor en el valor de la propiedad . `serviceSelector.name` de la variable [Servicio de operaciones de mensajería de AEM Communities](messaging.md#messaging-operations-service).

* **[!UICONTROL Componer página]**
(*Requerido*) La página que se abrirá cuando un miembro haga clic en la variable `Reply` botón. La página de destino debe contener la variable **[!UICONTROL Componer mensaje]** formulario.

* **[!UICONTROL Responder/Ver como recurso]**
Si se selecciona, la URL de respuesta y la URL de vista hacen referencia a un recurso; de lo contrario, los datos se pasan como parámetros de consulta en la URL.

* **[!UICONTROL Formulario de visualización de perfil]**
El formulario de perfil que se utiliza para mostrar el perfil de los remitentes.

* **[!UICONTROL Carpeta de papelera]**
Si se selecciona, este componente Lista de mensajes solo muestra los mensajes marcados como eliminados (papelera).

* **[!UICONTROL Rutas de carpeta]**
(*Requerido*) Referencia a los valores configurados para `inbox.path.name` y `sentitems.path.name` en el [Servicio de operaciones de mensajería de AEM Communities](messaging.md#messaging-operations-service). Al configurar un `Inbox`, agregue una entrada con el valor de `inbox.path.name`. Al configurar un `Outbox`, agregue una entrada con el valor de `sentitems.path.name`. Al configurar para `Trash`, agregue dos entradas con ambos valores.

#### Ficha Mostrar {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Marcar como botón de lectura]**
Si se selecciona, muestra una 
`Read`que permite marcar un mensaje como leído.

* **[!UICONTROL Marcar botón no leído]**
Si se selecciona, muestra una 
`Mark Unread` que permite marcar un mensaje como leído.

* **[!UICONTROL Botón Eliminar]**
Si se selecciona, muestra una 
`Delete`que permite marcar un mensaje como leído. Duplicará la funcionalidad de eliminación si **`Message Options`** también está marcado.

* **[!UICONTROL Opciones de mensaje]**
Si está marcado, muestra 
**`Reply`**, **`Reply All`**, **`Forward`** y **`Delete`** botones que permiten enviar o eliminar un mensaje. Duplicará la funcionalidad de eliminación si **`Delete Button`** también está marcado.

* **[!UICONTROL Mensajes por página]**
El número especificado es el número máximo de mensajes mostrados por página en un esquema de paginación. Si no se especifica ningún número (se deja en blanco), todos los mensajes se muestran y no hay paginación.

* **[!UICONTROL Patrones de marca de tiempo]**
Proporcione patrones de marca de hora para uno o más idiomas. El valor predeterminado es para en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Mostrar usuario]**
Elija una de las opciones siguientes: 
**`Sender`** o **`Recipients`** para determinar si desea mostrar el remitente o los destinatarios.

### Configuración del mensaje compuesto {#configuring-compose-message}

Para modificar la configuración de la página de mensajes de composición, abra el sitio en [modo de edición de autor](sites-console.md#authoring-site-content).

En `Preview`seleccione **[!UICONTROL Mensajes]** para abrir la página de mensajería principal. A continuación, seleccione el botón Nuevo mensaje para abrir el `Compose Message` página..

En `Edit` seleccione el componente principal de la página que contiene el cuerpo del mensaje.

Para acceder al cuadro de diálogo de configuración, es necesario cancelar la herencia seleccionando la opción `link`icono.

Una vez completada la configuración, es necesario restaurar la herencia seleccionando la opción `broken link` icono.

![chlimage_1-400](assets/chlimage_1-400.png)

Una vez cancelada la herencia, es posible seleccionar la variable `configure` para abrir el cuadro de diálogo de configuración.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Pestaña Básicos {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL Dirección URL de redireccionamiento]**
Introduzca la dirección URL de la página que se muestra después de enviar el mensaje. Por ejemplo, 
`../messaging.html`.

* **[!UICONTROL Cancelar URL]**
Introduzca la dirección URL de la página mostrada si el remitente cancela el mensaje. Por ejemplo, 
`../messaging.html`.

* **[!UICONTROL Longitud máxima del asunto del mensaje]**
El número máximo de caracteres permitidos en el campo Asunto. Por ejemplo, 500. El valor predeterminado no es límite.

* **[!UICONTROL Longitud máxima del cuerpo del mensaje]**
El número máximo de caracteres permitidos en el campo Contenido . Por ejemplo, 10 000. El valor predeterminado no es límite.

* **[!UICONTROL Selector de servicio]**
(*Requerido*) Establezca este valor en el valor de la propiedad . **`serviceSelector.name`** de la variable [Servicio de operaciones de mensajería de AEM Communities](messaging.md#messaging-operations-service).

#### Ficha Mostrar {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostrar campo de asunto]**
Si está marcado, muestre la variable 
`Subject` y permiten añadir un asunto al mensaje. El valor predeterminado no está seleccionado.

* **[!UICONTROL Etiqueta del asunto]**
Escriba el texto que se mostrará junto al 
`Subject` field. El valor predeterminado es `Subject`.

* **[!UICONTROL Mostrar campo de archivo adjunto]**
Si está marcado, muestre la variable 
`Attachment` y permiten agregar archivos adjuntos al mensaje. El valor predeterminado no está seleccionado.

* **[!UICONTROL Adjuntar etiqueta de archivo]**
Escriba el texto que se mostrará junto al 
`Attachment` field. El valor predeterminado es **`Attach File`**.

* **[!UICONTROL Mostrar campo de contenido]**
Si está marcado, muestre la variable 
`Content` y habilite la adición de un cuerpo de mensaje. El valor predeterminado no está seleccionado.

* **[!UICONTROL Etiqueta de contenido]**
Escriba el texto que se mostrará junto al 
`Content` field. El valor predeterminado es **`Body`**.

* **[!UICONTROL Con editor de texto enriquecido]**
Si se selecciona, indica el uso de un cuadro de texto de contenido personalizado con su propio editor de texto enriquecido. El valor predeterminado no está seleccionado.

* **[!UICONTROL Patrones de marca de tiempo]**
Proporcione patrones de marca de hora para uno o más idiomas. El valor predeterminado es para en, de, fr, it, es, ja, zh_CN, ko_KR.
