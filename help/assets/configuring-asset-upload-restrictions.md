---
title: Configurar restricciones de carga de recursos
description: Obtenga información sobre cómo configurar Recursos Adobe Experience Manager para restringir el tipo de recursos (archivos) que los usuarios pueden cargar.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 31%

---

# Configurar restricciones de carga de recursos {#configuring-asset-upload-restrictions}

Puede configurar Recursos Adobe Experience Manager para restringir el tipo de recursos (archivos) que los usuarios pueden cargar. Esta función le ayuda a eliminar la posibilidad de que los usuarios carguen recursos en un formato no deseado o carguen archivos dañinos. El servicio `Day CQ DAM Asset Upload Restriction` permite controlar el tipo de archivos que los usuarios pueden cargar. De forma predeterminada, [!DNL Experience Manager] Assets permite a los usuarios cargar recursos de todos los tipos MIME. Sin embargo, puede configurar el servicio para restringir el acceso de los usuarios solo a archivos de tipos MIME específicos.

1. Para abrir la consola web de Configuration Manager, acceda a `https://[AEM_server]:[port]/system/console/configMgr`.
1. Abra el servicio **[!UICONTROL Day CQ DAM Asset Upload Restriction]** en el modo de edición. De forma predeterminada, la opción **Allow all MIME** está seleccionada, lo que permite a los usuarios cargar archivos de todos los tipos MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Para restringir el acceso de los usuarios solo a archivos de ciertos tipos de MIME, desactive la opción **[!UICONTROL Permitir todos los MIME]** y especifique los tipos de MIME permitidos en los campos **[!UICONTROL Recursos de MIME permitidos (regex)]** mediante expresiones regulares.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Pulse o haga clic en **[!UICONTROL Guardar]** para almacenar los cambios. Si especifica cadenas MIME para los tipos de MIME permitidos, la operación de carga falla con cualquier recurso que tenga un tipo de MIME que no coincida con las cadenas MIME configuradas en estos campos.
