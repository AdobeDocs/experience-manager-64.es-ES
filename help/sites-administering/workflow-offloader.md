---
title: Descarga del flujo de trabajo de recursos
seo-title: Assets Workflow Offloader
description: Obtenga información sobre el Descargador de flujo de trabajo de recursos.
seo-description: Learn about the Assets Workflow Offloader.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
exl-id: 2ca8e786-042b-44f6-ac60-834eca64f79f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---

# Descarga del flujo de trabajo de recursos{#assets-workflow-offloader}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La descarga del flujo de trabajo de recursos permite habilitar varias instancias de Adobe Experience Manager (AEM) Assets para reducir la carga de procesamiento en la instancia principal (líder). La carga de procesamiento se distribuye entre la instancia de encabezado y las distintas instancias de descarga (trabajador) que se le agregan. La distribución de la carga de procesamiento de los recursos aumenta la eficacia y la velocidad con que AEM Assets procesa los recursos. Además, ayuda a asignar recursos dedicados para procesar recursos de un tipo MIME en particular. Por ejemplo, puede asignar un nodo específico en la topología para procesar solo los recursos de InDesign.

## Configuración de la topología de descarga {#configure-offloader-topology}

Utilice el Administrador de configuración para añadir la URL de la instancia de encabezado y los nombres de host de las instancias de descarga para las solicitudes de conexión en la instancia de encabezado.

1. Pulse o haga clic en el logotipo de AEM y elija **Herramientas** > **Operaciones** > **Consola web** para abrir Configuration Manager.
1. En la consola web, seleccione **Sling** >  **Administración de topología**.

   ![imagen_1-44](assets/chlimage_1-44.png)

1. En la página Administración de topología , toque o haga clic en el botón **Configurar el servicio Discovery.Oak** vínculo.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. En la página Configuración de Discovery Service , especifique la dirección URL del conector para la instancia de encabezado en la **Direcciones URL del conector de topología** campo .

   ![imagen_1-46](assets/chlimage_1-46.png)

1. En el **Lista blanca del conector de topología** especifique la dirección IP o los nombres de host de las instancias de descarga que pueden conectarse con la instancia de encabezado. Toque o haga clic **Guardar**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Para ver las instancias de descarga conectadas a la instancia de encabezado, vaya a **Herramientas** > **Implementación** > **Topología** y pulse o haga clic en la vista Cluster.

## Deshabilitar descarga {#disable-offloading}

1. Pulse o haga clic en el logotipo de AEM y elija **Herramientas** > **Implementación** > **Descarga**. La variable **Descarga del explorador** muestra los temas y las instancias del servidor que pueden consumir los temas.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Desactive el *com/adobe/granite/workflow/offloating* sobre las instancias de encabezado con las que los usuarios interactúan para cargar o cambiar AEM recursos.

   ![imagen_1-49](assets/chlimage_1-49.png)

## Configuración de lanzadores de flujo de trabajo en la instancia de encabezado {#configure-workflow-launchers-on-the-leader-instance}

Configure los iniciadores de flujo de trabajo para que utilicen la variable **Descarga de recursos de actualización DAM** flujo de trabajo en la instancia de encabezado en lugar del **Recurso de actualización de DAM** flujo de trabajo.

1. Toque o haga clic en el logotipo de AEM y elija, **Herramientas** > **Flujo de trabajo** > **Lanzadores** para abrir el **Iniciadores de flujo de trabajo** consola.

   ![imagen_1-50](assets/chlimage_1-50.png)

1. Localizar las dos configuraciones del iniciador con el tipo de evento **Nodo creado** y **Nodo modificado** respectivamente, que ejecutan el **Recurso de actualización DAM** flujo de trabajo.
1. Para cada configuración, seleccione la casilla de verificación antes de ella y toque o haga clic en el botón **Ver propiedades** de la barra de herramientas para mostrar el **Propiedades del iniciador** diálogo.

   ![imagen_1-51](assets/chlimage_1-51.png)

1. En el **Flujo de trabajo** lista, elija **Descarga de recursos de actualización DAM** y toque o haga clic **Guardar**.

   ![imagen_1-52](assets/chlimage_1-52.png)

1. Toque o haga clic en el logotipo de AEM y elija, **Herramientas** > **Flujo de trabajo** > **Modelos** para abrir el **Modelos de flujo de trabajo** página.
1. Seleccione el **Descarga de recursos de actualización DAM** flujo de trabajo y pulsar o hacer clic **Editar** de la barra de herramientas para mostrar sus detalles.

   ![imagen_1-53](assets/chlimage_1-53.png)

1. Mostrar el menú contextual para la variable **Descarga del flujo de trabajo DAM** paso y elija **Editar**. Compruebe la entrada en el **Tema de trabajo** del campo **Argumentos genéricos** del cuadro de diálogo de configuración.

   ![imagen_1-54](assets/chlimage_1-54.png)

## Desactivación de los iniciadores de flujo de trabajo en las instancias de descarga {#disable-the-workflow-launchers-on-the-offloader-instances}

Desactivar los iniciadores del flujo de trabajo que ejecutan el **Recurso de actualización DAM** flujo de trabajo en la instancia de encabezado.

1. Toque o haga clic en el logotipo de AEM y elija, **Herramientas** > **Flujo de trabajo** > **Lanzadores** para abrir el **Iniciadores de flujo de trabajo** consola.

   ![imagen_1-55](assets/chlimage_1-55.png)

1. Localizar las dos configuraciones del iniciador con el tipo de evento **Nodo creado** y **Nodo modificado** respectivamente, que ejecutan el **Recurso de actualización DAM** flujo de trabajo.
1. Para cada configuración, seleccione la casilla de verificación antes de ella y toque o haga clic en el botón **Ver propiedades** de la barra de herramientas para mostrar el **Propiedades del iniciador** diálogo.

   ![imagen_1-56](assets/chlimage_1-56.png)

1. En la sección **Activar **, arrastre el control deslizante para desactivar el iniciador del flujo de trabajo y pulse o haga clic en **Guardar** para desactivarlo.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Cargue cualquier recurso de tipo imagen en la instancia de encabezado. Compruebe las miniaturas generadas y devueltas para el recurso por la instancia descargada.
