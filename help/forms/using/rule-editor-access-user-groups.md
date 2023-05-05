---
title: Conceder acceso al Editor de reglas a determinados grupos de usuarios
seo-title: Grant rule editor access to select user groups
description: Conceder acceso restringido al editor de reglas para seleccionar grupos de usuarios.
seo-description: Grant restricted access to rule editor to select user groups.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
feature: Adaptive Forms
exl-id: 5e2960f2-b172-48a7-bba3-4561a5f9c7bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 82%

---

# Conceder acceso al Editor de reglas a determinados grupos de usuarios {#grant-rule-editor-access-to-select-user-groups}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Existen diferentes tipos de usuarios con diversas aptitudes que trabajan con formularios adaptables. Aunque es posible que los usuarios expertos tengan los conocimientos necesarios para trabajar con scripts y reglas complejas, puede haber usuarios de nivel básico que únicamente necesiten trabajar con el diseño y las propiedades básicas de los formularios adaptables.

AEM Forms permite limitar el acceso de los usuarios al Editor de reglas en función de su rol o función. En los ajustes del servicio de configuración de los formularios adaptables, puede especificar los [grupos de usuarios](/help/sites-administering/security.md) que pueden ver y acceder al Editor de reglas.

## Especificar qué grupos de usuarios pueden acceder al Editor de reglas {#specify-user-groups-that-can-access-rule-editor}

1. Inicie sesión en AEM Forms como administrador.
1. En la instancia de autor, haga clic en ![adobeexperiencemanager](assets/adobeexperiencemanager.png) Adobe Experience Manager > Herramientas ![hammer](assets/hammer.png) > Operaciones > Consola web. La consola web se abre en una nueva ventana.

   ![1](assets/1.png)

1. En la ventana de la consola web, busque y haga clic en **[!UICONTROL Configuración del canal Web de comunicaciones interactivas y formularios adaptables]**. La **[!UICONTROL Configuración del canal Web de comunicaciones interactivas y formularios adaptables]** se abre. No cambie ningún valor y haga clic en **[!UICONTROL Guardar]**.

   Crea el archivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config en el repositorio CRX.

1. Inicie sesión en CRXDE como administrador. Abra el archivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config para editarlo.
1. Utilice la siguiente propiedad para especificar el nombre de un grupo que puede acceder al Editor de reglas (por ejemplo, RuleEditorsUserGroup) y haga clic en **Guardar todo**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Para habilitar el acceso para varios grupos, especifique una lista de valores separados por comas:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Ahora, cuando un usuario que no forma parte del grupo de usuarios especificado (en este caso RuleEditorsUserGroup) toca un campo, aparece el icono Editar regla ( ![edit-rules1](assets/edit-rules1.png)) no está disponible para ella en la barra de herramientas de componentes:

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   Barra de herramientas de componentes visible para un usuario con acceso al Editor de reglas

   ![componentstoolbarwithoutre](assets/componentstoolbarwithoutre.png)

   Barra de herramientas de componentes visible para un usuario sin acceso al Editor de reglas

   Para obtener instrucciones sobre cómo agregar usuarios a grupos, consulte [Administración de usuarios y seguridad](/help/sites-administering/security.md).
