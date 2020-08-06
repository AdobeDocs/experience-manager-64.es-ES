---
title: Integración con ExactTarget
seo-title: Integración con ExactTarget
description: Descubra cómo integrar AEM con ExactTarget.
seo-description: Descubra cómo integrar AEM con ExactTarget.
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Integración con ExactTarget{#integrating-with-exacttarget}

La integración de AEM con Exact Destinatario le permite administrar y enviar correos electrónicos creados en AEM mediante Exact Destinatario. También le permite utilizar las funciones de administración de posibles clientes de Exact Destinatario a través de formularios AEM en páginas AEM.

La integración proporciona las siguientes funciones:

* La capacidad de crear correos electrónicos en AEM y publicarlos en Exact Destinatario para su distribución.
* La capacidad de definir la acción de un formulario AEM para crear un suscriptor de Exact Destinatario.

Una vez configurado ExactTarget, puede publicar newsletters o correos electrónicos en ExactTarget. Consulte [Publicación de newsletters en un servicio](/help/sites-authoring/personalization.md)de correo electrónico.

## Creación de una configuración de ExactTarget {#creating-an-exacttarget-configuration}

Las configuraciones de ExactTarget se pueden agregar mediante Cloudservices o Herramientas. Ambos métodos se describen en esta sección.

### Configuración de ExactTarget a través de Cloudservices {#configuring-exacttarget-via-cloudservices}

Para crear una configuración de ExactTarget en Cloud Services:

1. En la página de bienvenida, haga clic en **Cloud Services**. (Or directly access at `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Haga clic en **ExactTarget** y, a continuación, en **Configurar**. Se abre la ventana de configuración de ExactTarget.

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. Enter a title and optionally, a name and click **Create**. Se abre la ventana de configuración** ExactTarget Settings**.

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. Introduzca el nombre de usuario, la contraseña y seleccione un punto final de API (por ejemplo, **https://webservice.exacttarget.com/Service.asmx**).
1. Haga clic en **Conectar con ExactTarget.** Cuando se ha conectado correctamente, se muestra un cuadro de diálogo de éxito. Haga clic en **Aceptar** para salir de la ventana.

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. Seleccione una cuenta, si está disponible. La cuenta es para clientes de Enterprise 2.0. Haga clic en **Aceptar**.

   ExactTarget se ha configurado. Puede editar la configuración haciendo clic en **Editar**. Puede ir a ExactTarget haciendo clic en **Ir a ExactTarget**.

1. AEM ahora proporciona una función de extensión de datos. Puede importar columnas de extensión de datos de ExactTarget. Esto se puede configurar haciendo clic en el signo &quot;+&quot; que aparece además de crear correctamente la configuración de ExactTarget. Se puede seleccionar cualquiera de las extensiones de datos existentes en la lista desplegable. Para obtener más información sobre cómo configurar extensiones de datos, consulte la documentación de [ExactTarget](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   Las columnas de extensión de datos importadas se pueden utilizar posteriormente a través del componente **Texto y Personalización** .

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### Configuración de ExactTarget a través de las herramientas {#configuring-exacttarget-via-tools}

Para crear una configuración de ExactTarget en Herramientas:

1. En la página de bienvenida, haga clic en **Herramientas**. O navegue allí directamente yendo a `https://<hostname>:<port>/misadmin#/etc`.
1. Seleccione **Herramientas**, luego **Cloud Services Configuraciones,** luego **ExactTarget**.
1. Click **New** to open the **Create Page **window.

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. Introduzca el **Título** y, opcionalmente, el **Nombre** y haga clic en **Crear**.
1. Introduzca la información de configuración como se indica en el paso 4 del procedimiento anterior. Siga ese procedimiento para finalizar la configuración de ExactTarget.

### Añadir varias configuraciones {#adding-multiple-configurations}

Para agregar varias configuraciones:

1. En la página de bienvenida, haga clic en **Cloud Services** y en **ExactTarget**. Haga clic en el botón **Mostrar configuraciones** que aparece si hay una o más configuraciones de ExactTarget disponibles. Se enumeran todas las configuraciones disponibles.
1. Haga clic en el signo **+** junto a Configuraciones disponibles. Se abre la ventana **Crear configuraciones** . Siga el procedimiento de configuración anterior para crear una nueva configuración.

