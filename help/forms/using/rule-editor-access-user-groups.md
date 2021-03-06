---
title: Conceder acceso al editor de reglas a determinados grupos de usuarios
seo-title: Conceder acceso al editor de reglas a determinados grupos de usuarios
description: Conceder acceso restringido al editor de reglas a grupos de usuarios seleccionados.
seo-description: Conceder acceso restringido al editor de reglas a grupos de usuarios seleccionados.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 8%

---


# Conceder acceso al editor de reglas a determinados grupos de usuarios {#grant-rule-editor-access-to-select-user-groups}

## Información general {#overview}

Puede tener diferentes tipos de usuarios con diversas habilidades que trabajan con Adaptive Forms. Aunque los usuarios expertos pueden tener los conocimientos adecuados para trabajar con secuencias de comandos y reglas complejas, puede haber usuarios de nivel básico que solo necesiten trabajar con la presentación y las propiedades básicas de los formularios adaptables.

AEM Forms le permite limitar el acceso al editor de reglas a los usuarios en función de su función o función. En la configuración del Servicio de configuración de Forms adaptable, puede especificar los [grupos de usuarios](/help/sites-administering/security.md) que pueden ver y acceder al editor de reglas.

## Especificar grupos de usuarios que pueden acceder al editor de reglas {#specify-user-groups-that-can-access-rule-editor}

1. Inicie sesión en AEM Forms como administrador.
1. En la instancia de autor, haga clic en ![adobeexperiencemanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Herramientas ![martillo](assets/hammer.png) > Operaciones > Consola web. La consola web se abre en una nueva ventana.

   ![1](assets/1.png)

1. En la ventana de la consola web, localice y haga clic en **[!UICONTROL Configuración del canal web del formulario adaptable y la comunicación interactiva]**. **[!UICONTROL Aparece el cuadro de diálogo]** Configuración del canal web de formularios adaptables y comunicaciones interactivas. No cambie ningún valor y haga clic en **[!UICONTROL Guardar]**.

   Crea un archivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config en el repositorio CRX.

1. Inicie sesión en CRXDE como administrador. Abra el archivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config para editarlo.
1. Utilice la siguiente propiedad para especificar el nombre de un grupo que puede acceder al editor de reglas (por ejemplo, RuleEditorsUserGroup) y haga clic en **Guardar todo**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Para habilitar el acceso para varios grupos, especifique una lista de valores separados por comas:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Ahora, cuando un usuario que no forma parte del grupo de usuarios especificado (aquí RuleEditorsUserGroup) toca un campo, el icono Editar regla ( ![edit-rules1](assets/edit-rules1.png)) no está disponible para él en la barra de herramientas de componentes:

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   Barra de herramientas de componentes visible para un usuario con acceso al editor de reglas

   ![componentstoolbarwithoutre](assets/componentstoolbarwithoutre.png)

   Barra de herramientas de componentes visible para el usuario sin acceso al editor de reglas

   Para obtener instrucciones sobre cómo agregar usuarios a grupos, consulte [Administración de usuarios y seguridad](/help/sites-administering/security.md).

