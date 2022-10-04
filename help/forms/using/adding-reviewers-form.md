---
title: Asociar revisores de envío con un formulario
seo-title: Associating submission reviewers with a form
description: Aprenda a asociar revisores de envío con un formulario en AEM Forms. Los revisores asociados revisan un formulario enviado a través del portal de Forms.
seo-description: Learn how to associate submission reviewers with a form in AEM Forms. Associated reviewers review a form submitted via forms portal.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Adaptive Forms
exl-id: b45d844e-acf9-4da2-b54e-08c67aa183a3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 61%

---

# Asociar revisores de envío con un formulario  {#associating-submission-reviewers-with-a-form}

Cuando crea un formulario, puede especificar usuarios que revisen los envíos del formulario a través del portal de Forms y proporcionen comentarios. Su organización puede recopilar comentarios y volver a diseñar los formularios enviados.

AEM Forms permite asociar un grupo de revisores a un formulario. Los usuarios agregados al grupo de revisión de un formulario ven los envíos de este formulario y proporcionan comentarios.

Los grupos de revisores asignados a un formulario solo pueden revisar los envíos del formulario especificado.

## Requisitos previos {#prerequisite}

### Habilitar la propiedad de grupos del revisor de envío para formularios adaptables mediante el editor de esquemas de metadatos {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Para asociar un grupo de revisores a un formulario, edite el esquema de metadatos de los formularios adaptables. De forma predeterminada, no se puede agregar un grupo de revisores a un formulario enviado.

Para editar el esquema de metadatos:

1. En el modo Autor, en Experience Manager, haga clic en **[!UICONTROL Herramientas > Recursos > Esquemas de metadatos]**.
1. En la página Formularios de esquema, vaya a **[!UICONTROL Formularios > Formularios creados en AEM]**.

   La dirección URL de la página es:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Seleccione **[!UICONTROL Formulario adaptable]** y haga clic en **[!UICONTROL Editar]**.
1. En la página Editar formulario, haga clic en **[!UICONTROL Avanzadas]**.
1. En la pestaña Avanzadas, arrastre y suelte el componente **[!UICONTROL Texto de una línea]** disponible en Generar formulario.
1. Seleccione el componente de texto agregado para ver su configuración.

   En Configuración, introduzca `./jcr:content/metadata/form-submission-reviewer-group` en el campo Asignar a propiedad.

   El campo de grupo del revisor de envío de las Propiedades avanzadas del formulario adaptable se activa con el nombre especificado en Etiqueta de campo.

## Asociar revisores de envío con un formulario {#associating-submission-reviewers-with-a-form-1}

Para asociar revisores de envío con un formulario adaptable, cree un grupo de revisores y agréguele usuarios. Agregue el grupo de revisores creado en el campo del revisor de envío de las propiedades avanzadas del formulario. 
\
Los grupos de usuarios permiten asociar diferentes conjuntos de revisores de envío con diferentes formularios adaptables. Esta función evita que un usuario no autorizado revise el envío.

Antes de realizar los siguientes pasos, consulte [Requisito previo](/help/forms/using/adding-reviewers-form.md#prerequisite).

Para crear un grupo y agregarle miembros, vaya a **[!UICONTROL Herramientas > Operaciones > Seguridad > Grupos]**.\
Para obtener más información, consulte [Administración de usuarios y servicios](/help/sites-administering/security.md). 
\
Asegúrese de agregar el grupo que crea como miembro del grupo de usuarios predeterminado: **forms-submit-reviewers**. Este grupo de usuarios se envía con AEM Forms y garantiza que los usuarios se añadan como revisores de envío.

Para asociar grupos de usuarios con un formulario adaptable:

1. En el modo Autor, vaya a **[!UICONTROL Formularios > Formularios y documentos]**.
1. Utilice la variable **[!UICONTROL Select]** para seleccionar un formulario adaptable y haga clic en **[!UICONTROL Ver propiedades]**.
1. En la ventana Propiedades del formulario, haga clic en **[!UICONTROL Editar]** y, a continuación, haga clic en **[!UICONTROL AVANZADAS]**.
1. Introduzca el grupo en el campo del grupo de revisores de envío y haga clic en **[!UICONTROL Listo]**.

   El campo de grupo del revisor de envío aparece con el nombre especificado en el esquema de metadatos editado de los formularios adaptables.

>[!NOTE]
>
>Repita usuarios y formularios para garantizar la disponibilidad de los usuarios y formularios en la implementación remota de AEM Forms.
>
>Asegúrese de que todos los usuarios están replicados como miembros revisores de los grupos de usuarios en la implementación remota.
