---
title: Activación de la detección de duplicados
description: Obtenga información sobre cómo habilitar la detección de recursos duplicados en AEM.
contentOwner: AG
feature: Administración de activos,Informes de activos
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Activación de la detección de duplicados {#enabling-duplicate-detection}

Si intenta cargar un recurso que existe en Adobe Experience Manager (AEM) Assets, la función de detección de duplicados lo identificará como duplicado. La detección de duplicados está deshabilitada de forma predeterminada. Para habilitar la función, siga estos pasos:

1. Abra la página **[!UICONTROL Configuración de la consola web de Adobe Experience Manager]** en `https://[server]:[port]/system/console/configMgr`.
1. Edite la configuración del servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Seleccione la opción **[!UICONTROL detect duplicate]** y pulse o haga clic en **[!UICONTROL Save]**.

   ![Seleccione la opción Detectar duplicado en el servlet](assets/chlimage_1-377.png)

La función Detectar duplicado ahora está habilitada en AEM Assets. Cuando un usuario intenta cargar un recurso que existe en AEM, el sistema comprueba si hay conflictos e lo indica. Los recursos se identifican utilizando el hash SHA-1 almacenado en `jcr:content/metadata/dam:sha1`, lo que significa que se detectan activos duplicados independientemente de los nombres de archivo.

>[!MORELIKETHIS]
>
>* [Duplicar recursos en un repositorio existente (un tutorial de un miembro de la comunidad)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

