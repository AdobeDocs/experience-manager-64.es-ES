---
title: Activación de la detección de duplicados
description: Obtenga información sobre cómo habilitar la detección de recursos duplicados en AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# Activación de la detección de duplicados {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Si intenta cargar un recurso que existe en Adobe Experience Manager Assets, la función de detección de duplicados lo identificará como duplicado. La detección de duplicados está deshabilitada de forma predeterminada. Para habilitar la función, siga estos pasos:

1. Abra el **[!UICONTROL Configuración de la consola web de Adobe Experience Manager]** página en `https://[server]:[port]/system/console/configMgr`.
1. Editar la configuración del servlet **[!UICONTROL Recurso de creación de DAM CQ de día]**.
1. Seleccione el **[!UICONTROL detectar duplicado]** y pulse o haga clic en **[!UICONTROL Guardar]**.

   ![Seleccione la opción Detectar duplicado en el servlet](assets/chlimage_1-377.png)

La función Detectar duplicado está ahora habilitada en [!DNL Experience Manager] Recursos. Cuando un usuario intenta cargar un recurso que existe en AEM, el sistema comprueba si hay conflictos e lo indica. Los recursos se identifican utilizando el hash SHA-1 almacenado en `jcr:content/metadata/dam:sha1`, lo que significa que los recursos duplicados se detectan independientemente de los nombres de archivo.

>[!MORELIKETHIS]
>
>* [Duplicar recursos en un repositorio existente (un tutorial de un miembro de la comunidad)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

