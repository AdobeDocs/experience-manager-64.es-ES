---
title: Activación de la detección de Duplicado
description: Obtenga información sobre cómo activar la detección de recursos de duplicado en AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Activación de la detección de Duplicado {#enabling-duplicate-detection}

Si intenta cargar un recurso que existe en Adobe Experience Manager (AEM) Assets, la función de detección de duplicado lo identifica como duplicado. La detección de Duplicados está deshabilitada de forma predeterminada. Para habilitar la función, realice los siguientes pasos:

1. Abra la página Configuración **[!UICONTROL de la consola web de]** Adobe Experience Manager en `https://[server]:[port]/system/console/configMgr`.
1. Edite la configuración del servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Seleccione la opción **[!UICONTROL Detectar duplicado]** y toque o haga clic en **[!UICONTROL Guardar]**.

   ![Seleccione la opción Detectar duplicado en el servlet](assets/chlimage_1-377.png)

La función de detección de duplicado ahora está activada en AEM Assets. Cuando un usuario intenta cargar un recurso que existe en AEM, el sistema comprueba si hay conflictos y lo indica. Los recursos se identifican mediante hash SHA-1 almacenado en `jcr:content/metadata/dam:sha1`, lo que significa que se detectan los recursos de duplicado independientemente de los nombres de archivo.

>[!MORELIKETHIS]
>
>* [Duplicado de recursos en un repositorio existente (un tutorial de un miembro de la comunidad)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

