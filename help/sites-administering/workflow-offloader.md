---
title: Descarga del flujo de trabajo de recursos
seo-title: Descarga del flujo de trabajo de recursos
description: Obtenga información sobre la descarga del flujo de trabajo de recursos.
seo-description: Obtenga información sobre la descarga del flujo de trabajo de recursos.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 0%

---


# Descarga del flujo de trabajo de recursos{#assets-workflow-offloader}

El cargador de flujo de trabajo de recursos permite activar varias instancias de Recursos Adobe Experience Manager (AEM) para reducir la carga de procesamiento en la instancia principal (directriz). La carga de procesamiento se distribuye entre la instancia de encabezado y las distintas instancias de descargador (trabajador) que se le agregan. La distribución de la carga de procesamiento de los recursos aumenta la eficacia y la velocidad con que AEM Assets procesa los recursos. Además, ayuda a asignar recursos dedicados para procesar recursos de un tipo MIME concreto. Por ejemplo, puede asignar un nodo específico de la topología para procesar solo recursos de InDesign.

## Configurar la topología de descarga {#configure-offloader-topology}

Utilice Configuration Manager para agregar la dirección URL de la instancia de encabezado y los nombres de host de las instancias de descarga para las solicitudes de conexión en la instancia de encabezado.

1. Toque o haga clic en el logotipo de AEM y elija **Herramientas** > **Operaciones** > **Consola Web** para abrir Configuration Manager.
1. En la consola web, seleccione **Sling** > **Administración de topología**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. En la página Administración de topología, toque o haga clic en el vínculo **Configurar Discovery.Oak Service**.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. En la página Configuración de Discovery Service, especifique la dirección URL del conector para la instancia de encabezado en el campo **Direcciones URL del conector de topología**.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. En el campo **Lista blanca del conector de topología**, especifique la dirección IP o los nombres de host de las instancias de descarga que pueden conectarse con la instancia de encabezado. Toque o haga clic en **Guardar**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Para ver las instancias de descarga conectadas a la instancia de líder, vaya a **Herramientas** > **Implementación** > **Topología** y toque o haga clic en la vista de clúster.

## Deshabilitar descarga {#disable-offloading}

1. Toque o haga clic en el logotipo de AEM y elija **Herramientas** > **Implementación** > **Descarga**. La página **Descarga del explorador** muestra temas y las instancias del servidor que pueden consumir los temas.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Deshabilite el tema *com/adobe/granite/workflow/offloading* en las instancias de encabezado con las que los usuarios interactúan para cargar o cambiar recursos AEM.

   ![chlimage_1-49](assets/chlimage_1-49.png)

## Configurar los lanzadores de flujo de trabajo en la instancia de líder {#configure-workflow-launchers-on-the-leader-instance}

Configure los iniciadores de flujo de trabajo para utilizar el flujo de trabajo **Descarga de recursos de actualización de DAM** en la instancia de líder en lugar del flujo de trabajo **Recurso de actualización de DAM**.

1. Toque o haga clic en el logotipo de AEM y elija **Herramientas** > **Flujo de trabajo** > **Lanzadores** para abrir la consola **Iniciadores de flujo de trabajo**.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Busque las dos configuraciones del iniciador con tipo de evento **Nodo creado** y **Nodo modificado** respectivamente, que ejecutan el flujo de trabajo **Recurso de actualización de DAM**.
1. Para cada configuración, seleccione la casilla de verificación que hay antes y toque o haga clic en el icono **Propiedades de la Vista** de la barra de herramientas para mostrar el cuadro de diálogo **Propiedades del iniciador**.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. En la lista **Workflow**, elija **Descarga de recursos de actualización de DAM** y toque o haga clic **Guardar**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Toque o haga clic en el logotipo de AEM y elija **Herramientas** > **Flujo de trabajo** > **Modelos** para abrir la página **Modelos de flujo de trabajo**.
1. Seleccione el flujo de trabajo **Descarga de recursos de actualización de DAM** y toque/haga clic **Editar** en la barra de herramientas para mostrar sus detalles.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Muestre el menú contextual para el paso **Descarga de flujo de trabajo de DAM** y elija **Editar**. Compruebe la entrada en el campo **Tema del trabajo** de la ficha **Argumentos genéricos** del cuadro de diálogo de configuración.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## Deshabilitar los iniciadores de flujo de trabajo en las instancias de descargador {#disable-the-workflow-launchers-on-the-offloader-instances}

Deshabilite los iniciadores de flujo de trabajo que ejecutan el flujo de trabajo **Recurso de actualización de DAM** en la instancia de líder.

1. Toque o haga clic en el logotipo de AEM y elija **Herramientas** > **Flujo de trabajo** > **Lanzadores** para abrir la consola **Iniciadores de flujo de trabajo**.

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. Busque las dos configuraciones del iniciador con tipo de evento **Nodo creado** y **Nodo modificado** respectivamente, que ejecutan el flujo de trabajo **Recurso de actualización de DAM**.
1. Para cada configuración, seleccione la casilla de verificación que hay antes y toque o haga clic en el icono **Propiedades de la Vista** de la barra de herramientas para mostrar el cuadro de diálogo **Propiedades del iniciador**.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. En la sección **Activar **, arrastre el control deslizante para desactivar el iniciador del flujo de trabajo y toque/haga clic **Guardar** para deshabilitarlo.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Cargue cualquier recurso de tipo imagen en la instancia de encabezado. Compruebe las miniaturas generadas y devueltas para el recurso por la instancia descargada.

