---
title: Especificar la configuración de seguridad
seo-title: Specifying security settings
description: Obtenga información sobre cómo especificar la configuración de seguridad.
seo-description: Learn how to specify security settings.
uuid: 63ba7819-e4eb-4d28-8463-142ff4233a1e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 36a7e16f-d09d-4cc5-babd-1ccadba76e16
exl-id: 0bda2e58-9470-48fa-a60b-04a1a32689bb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 14%

---

# Especificar la configuración de seguridad {#specifying-security-settings}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Forms permite controlar si se resuelven las entidades externas en las entradas XML. De forma predeterminada, se resuelven, pero puede cambiar este comportamiento para aumentar la seguridad del sistema de formularios AEM.

**Impedir el procesamiento de archivos de datos XML que contienen referencias a entidades externas**

1. En la consola de administración, haga clic en **[!UICONTROL Servicios > Forms]**.
1. Desactive la casilla de verificación Resolver entidades externas .
1. Haga clic en **[!UICONTROL Guardar]**.
