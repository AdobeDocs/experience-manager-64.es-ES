---
title: Utilice Apache Tika para detectar el tipo MIME de los recursos digitales
description: Active Apache Tika para ayudar a AEM Assets a detectar el tipo MIME de los recursos del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 3%

---


# Utilice Apache Tika para detectar el tipo MIME de los recursos digitales {#detecting-mime-type-of-assets-using-apache-tika}

Normalmente, Recursos Adobe Experience Manager (AEM) detecta el tipo MIME de los recursos que se cargan desde su extensión de archivo. Si utiliza Apache Tika para cargar recursos, AEM Assets detecta su tipo MIME del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.

Esta función está deshabilitada de forma predeterminada. Para habilitar la función, configure el servicio **Day CQ DAM Mime Type** desde Configuration Manager.

>[!NOTE]
>
>La detección de tipo MIME mediante la biblioteca Apache Tika es una operación que utiliza muchos recursos.

1. Vaya a `https://[AEM_server]:[port]/system/console/configMgr` para abrir la consola web de Configuration Manager.
1. En la lista de servicios, localice el servicio **[!UICONTROL Day CQ DAM Mime Type y toque o haga clic en el icono]** Editar **** que hay junto a él para abrirlo en el modo de edición.

1. Seleccione la opción **[!UICONTROL Detectar MIME del contenido]** para permitir el análisis de los recursos cargados para determinar su tipo MIME mientras se omiten las extensiones de archivo. De forma predeterminada, esta opción no está seleccionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Pulse o haga clic en **[!UICONTROL Guardar]** para almacenar los cambios.
