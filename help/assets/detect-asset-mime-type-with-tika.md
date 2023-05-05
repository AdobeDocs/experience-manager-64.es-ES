---
title: Utilice Apache Tika para detectar el tipo MIME de los recursos digitales
description: Habilitar Apache Tika para ayudar [!DNL Experience Manager] Los recursos detectan el tipo MIME de los recursos del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 6%

---

# Utilice Apache Tika para detectar el tipo MIME de los recursos digitales {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Normalmente, Adobe Experience Manager Assets detecta el tipo MIME de los recursos que se cargan desde su extensión de archivo. Si utiliza Apache Tika para cargar recursos, [!DNL Experience Manager] Assets detecta su tipo MIME del flujo de contenido durante la operación de carga en lugar de la extensión del archivo.

Esta función está deshabilitada de forma predeterminada. Para habilitar la función, configure la variable **Tipo de Mime de Day CQ DAM** desde Configuration Manager.

>[!NOTE]
>
>La detección de tipo MIME que utiliza la biblioteca Apache Tika es una operación intensiva en recursos.

1. Vaya a `https://[AEM_server]:[port]/system/console/configMgr` para abrir la consola web de Configuration Manager.
1. En la lista de servicios, busque **[!UICONTROL Servicio Day CQ DAM Mime Type]** y pulse o haga clic en el botón **[!UICONTROL Editar]** junto a él para abrirlo en el modo de edición.

1. Seleccione el **[!UICONTROL Detectar MIME del contenido]** para habilitar el análisis de los recursos cargados para determinar su tipo MIME e ignorar las extensiones de archivo. De forma predeterminada, esta opción no está seleccionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Pulse o haga clic en **[!UICONTROL Guardar]** para almacenar los cambios.
