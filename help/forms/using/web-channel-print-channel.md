---
title: Imprimir canal y canal web
seo-title: Imprimir canal y canal web
description: Importación de plantillas de canal de impresión y creación y activación de plantillas de canal web
seo-description: Importación de plantillas de canal de impresión y creación y activación de plantillas de canal web
uuid: 19e6ffab-00d2-4084-9ee7-9643b11eb6c6
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 71bba66a-3cac-445b-9941-aa4bcf9b2160
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---


# Imprimir canal y canal Web {#print-channel-and-web-channel}

Importación de plantillas de canal de impresión y creación y activación de plantillas de canal web

Interactive Communications puede entregarse a través de dos canales: impresión y web. El canal de impresión se utiliza para crear documentos PDF y comunicaciones en papel, como una carta impresa como recordatorio del pago de primas de seguro, mientras que el canal web se utiliza para ofrecer experiencias en línea, como un extracto de tarjetas de crédito en un sitio web.

Los autores de comunicación interactiva pueden reutilizar recursos como fragmentos de documento e imágenes para crear tanto versiones de impresión como de web de comunicación interactiva.

Uno de los requisitos previos para [Crear una comunicación interactiva](/help/forms/using/create-interactive-communication.md) es tener las plantillas para impresión y/o canal Web disponibles en el servidor. Mientras los creadores de plantillas crean la plantilla de canal web en AEM, la plantilla de canal de impresión XDP se crea en Adobe Forms Designer y se carga en el servidor.

## Imprimir canal {#printchannel}

El canal de impresión de una comunicación interactiva utiliza una plantilla de formulario XFA, XDP. Un XDP está diseñado en Adobe Forms Designer. Para obtener más información sobre la creación de plantillas de canal de impresión, consulte [Diseño de maquetación](/help/forms/using/layout-design-details.md). Para utilizar una plantilla de canal de impresión en Interactive Communication, debe cargar la plantilla en el servidor de AEM Forms.

### Cargar plantilla de canal de impresión de Interactive Communication {#upload-interactive-communication-print-channel-template}

Para cargar la plantilla, debe ser miembro del grupo de usuarios de formularios. Siga los pasos siguientes para cargar la plantilla de canal de impresión (XDP) en AEM Forms:

1. Seleccione **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documentos]**.

1. Toque **[!UICONTROL Crear]** > **[!UICONTROL Carga de archivo]**.

   Desplácese y seleccione la plantilla de canal de impresión (XDP) adecuada y toque **[!UICONTROL Abrir]**.

## Canal Web {#web-channel}

Los creadores y administradores de plantillas pueden crear, editar y habilitar plantillas web. Para permitir que otros usuarios creen plantillas web, debe otorgarles derechos. Para obtener más información, consulte [Administración de derechos de usuario, grupo y acceso](/help/sites-administering/user-group-ac-admin.md).

### Creación de plantillas de Canal Web {#authoring-web-channel-template}

Para crear una plantilla de canal web, primero debe crear una carpeta de plantilla. Una vez que cree una plantilla web dentro de una carpeta de plantilla, debe activar la plantilla para permitir que los usuarios de los formularios creen un canal web de una comunicación interactiva basada en la plantilla.

Para crear una plantilla de canal web Complete los siguientes pasos:

1. Cree una carpeta Plantilla para mantener las plantillas web de comunicación interactiva, si aún no dispone de una. Para obtener más información, consulte Carpetas de plantilla en [Plantillas de página - Editable](/help/sites-developing/page-templates-editable.md).

   1. Toque **[!UICONTROL Herramientas]** ![herramientas-1](assets/tools-1.png) > **[!UICONTROL Navegador de configuración]**.
      * Consulte la [documentación del explorador de configuración](/help/sites-administering/configurations.md) para obtener más información.
   1. En la página Navegador de configuración, toque **[!UICONTROL Crear]**.
   1. En el cuadro de diálogo Crear configuración, especifique un título para la carpeta, marque **[!UICONTROL Plantillas editables]** y toque **[!UICONTROL Crear]**.

      La carpeta se crea y se enumera en la página Navegador de configuración.

1. Vaya a la carpeta de plantillas adecuada y cree una plantilla web.

   1. Vaya a la carpeta de plantillas adecuada seleccionando **[!UICONTROL Herramientas]** > **[!UICONTROL Plantillas > Carpeta]**.
   1. Toque **[!UICONTROL Crear]**.
   1. Seleccione **[!UICONTROL Comunicación interactiva - Canal Web]** y toque **[!UICONTROL Siguiente]**.
   1. Escriba un título y una descripción de plantilla y, a continuación, toque **[!UICONTROL Crear]**.

      Se crea la plantilla y aparece un cuadro de diálogo.

   1. Toque **[!UICONTROL Abrir]** para abrir la plantilla que ha creado en el editor de plantillas.

      Aparecerá el Editor de plantillas.

      ![webchanneltemplate](assets/webchanneltemplate.png)

      Al crear o editar una plantilla, puede definir varios aspectos que puede definir un autor de la plantilla. La creación o edición de una plantilla es similar a la creación de páginas. Para obtener más información, consulte Edición de plantillas - Autores de plantillas en [Creación de plantillas de página](/help/sites-authoring/templates.md).

1. Para permitir el uso de esta plantilla para la creación de comunicación interactiva, habilite la plantilla.

   1. Toque **[!UICONTROL Herramientas]** ![herramientas-1](assets/tools-1.png) > **[!UICONTROL Plantillas]**.
   1. Vaya a la plantilla adecuada, selecciónela y toque **[!UICONTROL Habilitar]** y, en el mensaje de alerta, toque **[!UICONTROL Habilitar]**.

      La plantilla está habilitada y su estado se muestra como Habilitada. Ahora puede crear una comunicación interactiva en la que puede utilizar la plantilla de canal web recién creada.

### Imprimir canal como maestro para canal Web {#print-channel-as-master-for-web-channel}

Durante la creación de una comunicación interactiva, los autores pueden seleccionar esta opción para crear el canal web en sincronización con el canal de impresión. El uso del canal de impresión como maestro para el canal web garantiza que el contenido, la herencia y el enlace de datos del canal web se deriven del canal de impresión y que los cambios realizados en el canal de impresión se puedan reflejar en el canal web. Sin embargo, los autores de la comunicación interactiva pueden romper la herencia de componentes específicos del canal web, según sea necesario.

![printweb_2-2](assets/printweb_2-2.png)

