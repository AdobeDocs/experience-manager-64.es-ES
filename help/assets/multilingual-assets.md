---
title: Recursos multilingües
description: Aprenda a automatizar los flujos de trabajo para traducir recursos, incluidos binarios, metadatos y etiquetas a varios idiomas.
contentOwner: AG
feature: Asset Management
role: Admin
exl-id: 8e065137-3599-48af-a040-6923b7b5e1d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 6%

---

# Recursos multilingües {#multilingual-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager (AEM) Assets permite automatizar los flujos de trabajo de traducción en recursos (incluidos binarios, metadatos y etiquetas) para generar recursos en otros idiomas y utilizarlos en proyectos multilingües.

Para automatizar los flujos de trabajo de traducción, debe integrar los proveedores de servicios de traducción con [!DNL Experience Manager] y crear proyectos para traducir recursos a varios idiomas. [!DNL Experience Manager] admite flujos de trabajo de traducción automática y humana.

Traducción humana: Los recursos traducidos se devuelven y se importan en AEM. Cuando el proveedor de traducción está integrado con AEM, los recursos se envían automáticamente entre [!DNL Experience Manager] y el proveedor de traducción.

Traducción automática: El servicio de traducción automática traduce inmediatamente los metadatos y las etiquetas de los recursos.

La traducción de recursos incluye lo siguiente:

1. [Conexión [!DNL Experience Manager] con el proveedor de servicios de traducción](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creación de configuraciones del marco de integración de traducción](/help/sites-administering/tc-tic.md)
1. [Preparación de recursos para su traducción](preparing-assets-for-translation.md)
1. [Aplicación de servicios de nube de traducción a carpetas](transition-cloud-services.md)
1. [Crear proyectos de traducción](translation-projects.md)

Si el proveedor de servicios de traducción no proporciona un conector para integrarlo con AEM, utilice un [proceso alternativo](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Consulte también [Creación de proyectos de traducción para fragmentos de contenido](creating-translation-projects-for-content-fragments.md).
