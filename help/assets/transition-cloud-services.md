---
title: Aplicación de servicios de nube de traducción a carpetas
description: Aplicación de servicios de nube de traducción a carpetas
contentOwner: AG
feature: Translation
role: Admin
exl-id: 87883a3f-db95-41f4-b0aa-cdaeb7e6f555
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 52%

---

# Aplicación de servicios de nube de traducción a carpetas {#applying-translation-cloud-services-to-folders}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager le permite utilizar los servicios de traducción basados en la nube del proveedor de traducción que elija para garantizar que sus recursos se traduzcan según sus necesidades.

Puede aplicar el servicio de nube de traducción directamente a la carpeta de recursos para que se puedan utilizar durante los flujos de trabajo de traducción.

## Aplicación de los servicios de traducción {#applying-the-translation-services}

La aplicación de servicios de traducción en la nube directamente a la carpeta de recursos elimina la necesidad de configurar servicios de traducción al crear o actualizar flujos de trabajo de traducción.

1. En la interfaz de usuario de Assets, seleccione la carpeta a la que desea aplicar los servicios de traducción.
1. En la barra de herramientas, pulse o haga clic en el icono **[!UICONTROL Propiedades]** para mostrar la página **[!UICONTROL Propiedades de la carpeta]**.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Vaya a la pestaña **[!UICONTROL Cloud Services]**.
1. En la lista Configuraciones del Cloud Service , elija el proveedor de traducción deseado. Por ejemplo, si desea utilizar los servicios de traducción de Microsoft, elija **[!UICONTROL Traductor de Microsoft]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Seleccione el conector para el proveedor de traducción.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Guardar]** y, a continuación, haga clic en **[!UICONTROL Aceptar]** para cerrar el cuadro de diálogo. El servicio de traducción se aplica a la carpeta.

## Aplicación de conector de traducción personalizado  {#applying-custom-translation-connector}

Si desea aplicar un conector personalizado para los servicios de traducción que desea utilizar en los flujos de trabajo de traducción. Para aplicar un conector personalizado, primero instale el conector desde el Administrador de paquetes. A continuación, configure el conector desde la consola de Cloud Services. Después de configurar el conector, estará disponible en la lista de conectores de la pestaña Cloud Services que se describe en [Aplicación de los serviciosde traducción](transition-cloud-services.md#applying-the-translation-services). Después de aplicar el conector personalizado y ejecutar los flujos de trabajo de traducción, el mosaico **[!UICONTROL Resumen de traducción]** del proyecto de traducción muestra los detalles del conector en los encabezados **[!UICONTROL Proveedor]** y **[!UICONTROL Método]**.

1. Instale el conector desde el Administrador de paquetes.
1. Toque o haga clic en [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas > Implementación > Cloud Services]**.
1. Coloque el conector que instaló en **[!UICONTROL Servicios de terceros]** en la página **[!UICONTROL Cloud Services]**.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Toque o haga clic en **[!UICONTROL Configurar ahora]** para abrir el **[!UICONTROL Crear configuración]** diálogo.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Especifique un título y un nombre para el conector y, a continuación, pulse o haga clic en **[!UICONTROL Crear]**. El conector personalizado está disponible en la lista de conectores de la pestaña **[!UICONTROL Cloud Services]** que se describe en el paso 5 de [Aplicación de los servicios de traducción](#applying-the-translation-services).
1. Ejecute cualquier flujo de trabajo de traducción descrito en [Creación de proyectos de traducción](translation-projects.md) después de aplicar el conector personalizado. Compruebe los detalles del conector en el mosaico **[!UICONTROL Resumen de traducción]** del proyecto de traducción en la consola **[!UICONTROL Proyectos]**.

   ![chlimage_1-220](assets/chlimage_1-220.png)
