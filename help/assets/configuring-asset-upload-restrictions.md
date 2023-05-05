---
title: Configurar restricciones de carga de recursos
description: Obtenga información sobre cómo configurar Recursos Adobe Experience Manager para restringir el tipo de recursos (archivos) que los usuarios pueden cargar.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 32%

---

# Configurar restricciones de carga de recursos {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede configurar Recursos Adobe Experience Manager para restringir el tipo de recursos (archivos) que los usuarios pueden cargar. Esta función le ayuda a eliminar la posibilidad de que los usuarios carguen recursos en un formato no deseado o carguen archivos dañinos. La variable `Day CQ DAM Asset Upload Restriction` permite controlar el tipo de archivos que los usuarios pueden cargar. De forma predeterminada, [!DNL Experience Manager] Recursos permite a los usuarios cargar recursos de todos los tipos MIME. Sin embargo, puede configurar el servicio para restringir el acceso de los usuarios solo a archivos de tipos MIME específicos.

1. Para abrir la consola web de Configuration Manager, acceda a `https://[AEM_server]:[port]/system/console/configMgr`.
1. Abra el **[!UICONTROL Restricción de carga de recursos de CQ DAM de día]** en el modo de edición. De forma predeterminada, la variable **Permitir todos los MIME** está seleccionada, lo que permite a los usuarios cargar archivos de todos los tipos MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Para restringir el acceso de los usuarios solo a archivos de ciertos tipos de MIME, desactive la opción **[!UICONTROL Permitir todos los MIME]** y especifique los tipos de MIME permitidos en los campos **[!UICONTROL Recursos de MIME permitidos (regex)]** mediante expresiones regulares.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Pulse o haga clic en **[!UICONTROL Guardar]** para almacenar los cambios. Si especifica cadenas MIME para los tipos de MIME permitidos, la operación de carga falla con cualquier recurso que tenga un tipo de MIME que no coincida con las cadenas MIME configuradas en estos campos.
