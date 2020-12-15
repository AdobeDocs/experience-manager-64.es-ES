---
title: Aplicación de servicios de nube de traducción a carpetas
description: Aplicación de servicios de nube de traducción a carpetas
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 54%

---


# Aplicación de servicios de nube de traducción a carpetas {#applying-translation-cloud-services-to-folders}

Adobe Experience Manager (AEM) le permite utilizar los servicios de traducción basados en la nube del proveedor de traducción que elija para garantizar que los recursos se traducen según sus necesidades.

Puede aplicar el servicio de traducción en la nube directamente a la carpeta de recursos para que se puedan utilizar durante los flujos de trabajo de traducción.

## Aplicación de los servicios de traducción {#applying-the-translation-services}

La aplicación de servicios de traducción en la nube directamente a la carpeta de recursos elimina la necesidad de configurar servicios de traducción al crear o actualizar flujos de trabajo de traducción.

1. En la interfaz de usuario de Recursos, seleccione la carpeta a la que desea aplicar los servicios de traducción.
1. En la barra de herramientas, pulse o haga clic en el icono **[!UICONTROL Propiedades]** para mostrar la página **[!UICONTROL Propiedades de la carpeta]**.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Vaya a la pestaña **[!UICONTROL Cloud Services]**.
1. En la lista Configuraciones de Cloud Service, elija el proveedor de traducción deseado. Por ejemplo, si desea utilizar los servicios de traducción de Microsoft, elija **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Elija el conector para el proveedor de traducción.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Guardar]** y, a continuación, haga clic en **[!UICONTROL Aceptar]** para cerrar el cuadro de diálogo. El servicio de traducción se aplica a la carpeta.

## Aplicación del conector de traducción personalizada {#applying-custom-translation-connector}

Si desea aplicar un conector personalizado para los servicios de traducción que desea utilizar en los flujos de trabajo de traducción. Para aplicar un conector personalizado, primero instale el conector desde el Administrador de paquetes. A continuación, configure el conector desde la consola de Cloud Services. Después de configurar el conector, estará disponible en la lista de conectores de la pestaña Cloud Services que se describe en [Aplicación de los serviciosde traducción](transition-cloud-services.md#applying-the-translation-services). Después de aplicar el conector personalizado y ejecutar los flujos de trabajo de traducción, el mosaico **[!UICONTROL Resumen de traducción]** del proyecto de traducción muestra los detalles del conector en los encabezados **[!UICONTROL Proveedor]** y **[!UICONTROL Método]**.

1. Instale el conector desde el Administrador de paquetes.
1. Toque o haga clic en el logotipo de AEM y vaya a **[!UICONTROL Herramientas > Implementación > Cloud Services]**.
1. Coloque el conector que instaló en **[!UICONTROL Servicios de terceros]** en la página **[!UICONTROL Cloud Services]**.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Toque o haga clic en el vínculo **[!UICONTROL Configurar ahora]** para abrir el cuadro de diálogo **[!UICONTROL Crear configuración]**.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Especifique un título y un nombre para el conector y, a continuación, pulse o haga clic en **[!UICONTROL Crear]**. El conector personalizado está disponible en la lista de conectores de la pestaña **[!UICONTROL Cloud Services]** que se describe en el paso 5 de [Aplicación de los servicios de traducción](#applying-the-translation-services).
1. Ejecute cualquier flujo de trabajo de traducción descrito en [Creación de proyectos de traducción](translation-projects.md) después de aplicar el conector personalizado. Compruebe los detalles del conector en el mosaico **[!UICONTROL Resumen de traducción]** del proyecto de traducción en la consola **[!UICONTROL Proyectos]**.

   ![chlimage_1-220](assets/chlimage_1-220.png)
