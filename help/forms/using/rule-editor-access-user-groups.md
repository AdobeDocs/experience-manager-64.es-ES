---
title: Conceder acceso al Editor de reglas a determinados grupos de usuarios
seo-title: Grant rule editor access to select user groups
description: Conceder acceso restringido al editor de reglas a grupos de usuarios seleccionados.
seo-description: Grant restricted access to rule editor to select user groups.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
feature: Adaptive Forms
exl-id: 5e2960f2-b172-48a7-bba3-4561a5f9c7bc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 40%

---

# Conceder acceso al Editor de reglas a determinados grupos de usuarios {#grant-rule-editor-access-to-select-user-groups}

## Información general {#overview}

Puede tener diferentes tipos de usuarios con diversas habilidades que trabajan con Adaptive Forms. Aunque los usuarios expertos pueden tener los conocimientos adecuados para trabajar con secuencias de comandos y reglas complejas, puede haber usuarios de nivel básico que solo necesiten trabajar con la presentación y las propiedades básicas de los formularios adaptables.

AEM Forms le permite limitar el acceso al editor de reglas a los usuarios en función de su función o función. En los ajustes del servicio de configuración de los formularios adaptables, puede especificar los [grupos de usuarios](/help/sites-administering/security.md) que pueden ver y acceder al Editor de reglas.

## Especificar qué grupos de usuarios pueden acceder al Editor de reglas {#specify-user-groups-that-can-access-rule-editor}

1. Inicie sesión en AEM Forms como administrador.
1. En la instancia de autor, haga clic en ![adobeexperiencemanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Herramientas ![martillo](assets/hammer.png) > Operaciones > Consola web. La consola web se abre en una nueva ventana.

   ![1](assets/1.png)

1. En la ventana de la consola web, busque y haga clic en **[!UICONTROL Configuración del canal web de comunicaciones interactivas y formularios adaptables]**. **[!UICONTROL Configuración del canal web de comunicaciones interactivas y formularios adaptables]** se abre. No cambie ningún valor y haga clic en **[!UICONTROL Guardar]**.

   Crea un archivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config en el repositorio CRX.

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
