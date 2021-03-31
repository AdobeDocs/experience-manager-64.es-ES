---
title: Utilice Apache Tika para detectar el tipo MIME de los recursos digitales
description: Habilite Apache Tika para ayudar a AEM Assets a detectar el tipo MIME de los recursos del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.
contentOwner: AG
feature: Metadatos,Herramientas para desarrolladores,Administración de recursos
role: Administrador,Arquitecto
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 3%

---


# Utilice Apache Tika para detectar el tipo MIME de los recursos digitales {#detecting-mime-type-of-assets-using-apache-tika}

Normalmente, Adobe Experience Manager (AEM) Assets detecta el tipo MIME de los recursos que se cargan desde su extensión de archivo. Si utiliza Apache Tika para cargar recursos, AEM Assets detecta su tipo MIME del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.

Esta función está deshabilitada de forma predeterminada. Para habilitar la función, configure el servicio **Day CQ DAM Mime Type** desde Configuration Manager.

>[!NOTE]
>
>La detección de tipo MIME que utiliza la biblioteca Apache Tika es una operación intensiva en recursos.

1. Vaya a `https://[AEM_server]:[port]/system/console/configMgr` para abrir la consola web de Configuration Manager.
1. En la lista de servicios, busque **[!UICONTROL Day CQ DAM Mime Type Service]** y pulse o haga clic en el icono **[!UICONTROL Editar]** que está junto a él para abrirlo en el modo de edición.

1. Seleccione la opción **[!UICONTROL Detect MIME from content]** para habilitar el análisis de los recursos cargados para determinar su tipo MIME e ignorar las extensiones de archivo. De forma predeterminada, esta opción no está seleccionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Pulse o haga clic en **[!UICONTROL Guardar]** para almacenar los cambios.
