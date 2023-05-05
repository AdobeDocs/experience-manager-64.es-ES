---
title: Especificar la configuración de seguridad
seo-title: Specify security settings
description: Obtenga información sobre cómo especificar la configuración de seguridad.
seo-description: Learn how to specify security settings.
uuid: c86ba195-010d-40d6-9f9d-4cb4c364d104
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3c017f9a-aa7f-4d12-ba8b-9fd92c029157
exl-id: 3cc39a24-dbdf-4a4c-9c96-4d39d8cff20d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 14%

---

# Especificar la configuración de seguridad {#specify-security-settings}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Output permite controlar si se resuelven las entidades externas en las entradas XML. De forma predeterminada, se resuelven, pero puede cambiar este comportamiento para aumentar la seguridad del sistema de formularios AEM.

**Impedir el procesamiento de archivos de datos XML que contienen referencias a entidades externas**

1. En la consola de administración, haga clic en Servicios > salida.
1. Desactive la casilla de verificación Resolver entidades externas .
1. Haga clic en Guardar.
