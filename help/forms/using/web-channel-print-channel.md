---
title: Canal de impresión y canal web
seo-title: Print channel and web channel
description: Importar plantillas del canal de impresión y crear y activar plantillas del canal web
seo-description: Importing print channel templates and creating and enabling web channel templates
uuid: 19e6ffab-00d2-4084-9ee7-9643b11eb6c6
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 71bba66a-3cac-445b-9941-aa4bcf9b2160
feature: Interactive Communication
exl-id: cb7a8e96-4440-47ec-b506-275d5acc774e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 93%

---

# Canal de impresión y canal web {#print-channel-and-web-channel}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Importar plantillas del canal de impresión y crear y activar plantillas del canal web

Las comunicaciones interactivas se pueden entregar mediante dos canales: impresión y web. El canal de impresión se utiliza para crear PDF y comunicaciones en papel, como una carta impresa como recordatorio de pago de primas de seguro, mientras que el canal web se utiliza para ofrecer experiencias en línea, como un extracto de tarjeta de crédito en un sitio web.

Los autores de comunicaciones interactivas pueden reutilizar recursos como fragmentos de documento e imágenes para crear versiones impresas y web de la comunicación interactiva.

Uno de los requisitos previos para [Crear una comunicación interactiva](/help/forms/using/create-interactive-communication.md) es tener las plantillas para impresión y/o canal web disponibles en el servidor. Mientras los autores de plantillas crean la plantilla del canal web en AEM, la plantilla de canal de impresión XDP se crea en Adobe Forms Designer y se carga en el servidor.

## Canal de impresión {#printchannel}

El canal de impresión de una comunicación interactiva utiliza la plantilla de formulario XFA, XDP. Los XDP se diseñan en Adobe Forms Designer. Para obtener más información sobre la creación de plantillas de canal de impresión, consulte [Diseño](/help/forms/using/layout-design-details.md). Para utilizar una plantilla de canal de impresión en la comunicación interactiva, debe cargar la plantilla en el servidor de AEM Forms.

### Cargar plantilla del canal de impresión de comunicación interactiva {#upload-interactive-communication-print-channel-template}

Para cargar la plantilla, debe ser miembro del grupo de usuarios de formularios. Siga los siguientes pasos para cargar la plantilla del canal de impresión (XDP) en AEM Forms:

1. Seleccione **[!UICONTROL Forms]** > **[!UICONTROL Formularios y documentos]**.

1. Pulse **[!UICONTROL Crear]** > **[!UICONTROL Cargar archivo]**.

   Desplácese, seleccione la plantilla de canal de impresión (XDP) adecuada y pulse **[!UICONTROL Abrir]**.

## Canal web {#web-channel}

Los autores y administradores de plantillas pueden crear, editar y habilitar plantillas web. Para permitir que otros usuarios creen plantillas web, debe otorgarles derechos. Para obtener más información, consulte [Administración de derechos de usuario, grupo y acceso](/help/sites-administering/user-group-ac-admin.md).

### Crear plantillas de canal web {#authoring-web-channel-template}

Para crear una plantilla de canal web, primero debe crear una carpeta de plantilla. Una vez que haya creado una plantilla web dentro de una carpeta de plantilla, debe habilitar la plantilla para permitir a los usuarios de los formularios crear un canal web de comunicación interactiva basada en la plantilla.

Para crear una plantilla de canal web, complete los siguientes pasos:

1. Cree una carpeta de plantilla para mantener las plantillas web de comunicación interactiva, si todavía no dispone de una. Para obtener más información, consulte Carpetas de plantilla en [Plantillas de página: editables](/help/sites-developing/page-templates-editable.md).

   1. Toque **[!UICONTROL Herramientas]** ![herramientas-1](assets/tools-1.png) > **[!UICONTROL Explorador de configuración]**.
      * Consulte la documentación del [](/help/sites-administering/configurations.md)Explorador de configuración para obtener más información.
   1. En la página Explorador de configuración, pulse **[!UICONTROL Crear]**.
   1. En el cuadro de diálogo Crear configuración, especifique un título para la carpeta, marque **[!UICONTROL Plantillas editables]** y pulse **[!UICONTROL Crear]**.

      La carpeta se crea y se enumera en la página Explorador de configuración.

1. Vaya a la carpeta de plantillas adecuada y cree una plantilla web.

   1. Vaya a la carpeta de plantillas adecuada seleccionando **[!UICONTROL Herramientas]** > **[!UICONTROL Plantillas > Carpeta]**.
   1. Pulse **[!UICONTROL Crear]**.
   1. Seleccione **[!UICONTROL Comunicación interactiva: canal web]** y pulse **[!UICONTROL Siguiente]**.
   1. Especifique un título y una descripción de plantilla y, a continuación, pulse **[!UICONTROL Crear]**.

      La plantilla se crea y aparece un cuadro de diálogo.

   1. Pulse **[!UICONTROL Abrir]** para abrir la plantilla que ha creado en el editor de plantillas.

      Aparecerá el editor de plantillas.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Al crear o editar una plantilla, hay distintos aspectos que el autor de plantillas pueden definir. Crear o editar una plantilla es similar a crear páginas. Para obtener más información, consulte Editar plantillas: autores de plantillas en [Crear plantillas de página](/help/sites-authoring/templates.md).

1. Para permitir el uso de esta plantilla para la creación de comunicaciones interactivas, habilite la plantilla.

   1. Toque **[!UICONTROL Herramientas]** ![herramientas-1](assets/tools-1.png) > **[!UICONTROL Plantillas]**.
   1. Vaya a la plantilla adecuada, selecciónela y pulse **[!UICONTROL Habilitar]** y en el mensaje de alerta, pulse **[!UICONTROL Habilitar]**.

      La plantilla está habilitada y su estado se muestra como Habilitada. Ahora puede continuar creando una comunicación interactiva en la que puede utilizar la plantilla de canal web recién creada.

### Imprimir canal como principal para el canal web {#print-channel-as-master-for-web-channel}

Durante la creación de una comunicación interactiva, los autores pueden seleccionar esta opción para crear el canal web sincronizado con el canal de impresión. Utilizar el canal de impresión como principal para el canal web garantiza que el contenido, la herencia y el enlace de datos del canal web se deriven del canal de impresión y que los cambios realizados en el canal de impresión se puedan reflejar en el canal web. Sin embargo, los autores de la comunicación interactiva pueden romper la herencia de componentes específicos del canal web, según sea necesario.

![printweb_2-2](assets/printweb_2-2.png)
