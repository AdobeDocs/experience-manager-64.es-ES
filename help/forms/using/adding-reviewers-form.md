---
title: Asociación de revisores de envío con un formulario
seo-title: Asociación de revisores de envío con un formulario
description: Aprenda a asociar revisores de envío con un formulario en AEM Forms. Los revisores asociados revisan un formulario enviado a través del portal de formularios.
seo-description: Aprenda a asociar revisores de envío con un formulario en AEM Forms. Los revisores asociados revisan un formulario enviado a través del portal de formularios.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Asociación de revisores de envío con un formulario {#associating-submission-reviewers-with-a-form}

Cuando cree un formulario, puede especificar usuarios que revisen los envíos a través del portal de formularios y proporcionar comentarios. Su organización puede recopilar comentarios y rediseñar los formularios enviados.

AEM Forms permite asociar un grupo de revisores a un formulario. Los usuarios agregados a un grupo de revisión de un formulario ven los envíos de este formulario y proporcionan sus comentarios.

Los grupos de revisores asignados a un formulario solo pueden revisar los envíos del formulario especificado.

## Requisitos previos {#prerequisite}

### Habilitar la propiedad de grupos del revisor de envío para formularios adaptables mediante el editor de esquemas de metadatos {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Para asociar un grupo de revisores a un formulario, edite el esquema de metadatos de los formularios adaptables. De forma predeterminada, no se puede agregar un grupo de revisores a un formulario enviado.

Para editar el esquema de metadatos:

1. En el modo de creación, en Experience Manager, haga clic en **[!UICONTROL Herramientas > Assets > Esquemas de metadatos]**.
1. En la página Esquema de Forms, vaya a **[!UICONTROL Forms > Forms Authored in AEM]**.

   La dirección URL de la página es:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Seleccione **[!UICONTROL Formulario adaptable]** y haga clic en **[!UICONTROL Editar]**.
1. En la página Editar formulario, haga clic en **[!UICONTROL Avanzado]**.
1. En la ficha Avanzado , arrastre y suelte el componente **[!UICONTROL Texto de una sola línea]** disponible en Generar formulario.
1. Seleccione el componente de texto añadido para ver su configuración.

   En Configuración, escriba `./jcr:content/metadata/form-submission-reviewer-group` en el campo Asignar a propiedad .

   El campo de grupo del revisor de envío de las Propiedades avanzadas del formulario adaptable se activa con el nombre especificado en Etiqueta de campo.

## Asociación de revisores de envío con un formulario {#associating-submission-reviewers-with-a-form-1}

Para asociar revisores de envío con un formulario adaptable, cree un grupo de revisores y agréguele usuarios. Agregue el grupo de revisores creado en el campo revisor de envío de formulario de las propiedades avanzadas del formulario.\
Los grupos de usuarios permiten asociar diferentes conjuntos de revisores de envío con diferentes formularios adaptables. Esta función evita que un usuario no autorizado revise el envío.

Antes de realizar los siguientes pasos, consulte [Requisito previo](/help/forms/using/adding-reviewers-form.md#prerequisite).

Para crear un grupo y agregarle miembros, vaya a **[!UICONTROL Herramientas > Operaciones > Seguridad > Grupos]**.\
Para obtener más información, consulte [Administración de usuarios y servicios](/help/sites-administering/security.md).\
Asegúrese de agregar el grupo que crea como miembro del grupo de usuarios integrado: **forms-submit-reviewers**. Este grupo de usuarios se envía con AEM Forms y garantiza que los usuarios se añadan como revisores de envío.

Para asociar grupos de usuarios con un formulario adaptable:

1. En el modo de creación, vaya a **[!UICONTROL Forms > Forms &amp; Documents]**.
1. Utilice la opción **[!UICONTROL Select]** para seleccionar un formulario adaptable y haga clic en **[!UICONTROL Ver propiedades]**.
1. En la ventana Propiedades del formulario, haga clic en **[!UICONTROL Edit]** y, a continuación, haga clic en **[!UICONTROL ADVANCED]**.
1. Introduzca el grupo en el campo del grupo del revisor de envío y haga clic en **[!UICONTROL Listo]**.

   El campo de grupo del revisor de envío aparece con el nombre especificado en el esquema de metadatos editado de los formularios adaptables.

>[!NOTE]
>
>Repita usuarios y formularios para garantizar la disponibilidad de los usuarios y formularios en la implementación remota de AEM Forms.
>
>Asegúrese de que todos los usuarios estén duplicados como miembros revisores de los grupos de usuarios en la implementación remota.

