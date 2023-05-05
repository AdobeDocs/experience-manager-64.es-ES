---
title: Plantillas de grupo
seo-title: Group Templates
description: Acceso a la consola Plantillas de grupo
seo-description: How to access the Group Templates console
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 3%

---

# Plantillas de grupo {#group-templates}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La consola Plantillas de grupo es muy similar a la del [Plantillas de sitio](sites.md) consola. Ambos son modelos para un conjunto de páginas precableadas y características que forman un sitio de comunidad. La diferencia es que una plantilla de sitio es para la comunidad principal y una plantilla de grupo es para un grupo de comunidad, una subcomunidad anidada dentro de la comunidad principal.

Un grupo de la comunidad se incorpora a una plantilla de sitio al incluir la variable [Función de grupos](functions.md#groups-function) (que puede no ser la primera ni la única función de la plantilla).

Como comunidades [paquete de características 1](deploy-communities.md#latestfeaturepack), es posible anidar grupos incluyendo la función Grupos dentro de una plantilla de grupo.

En el momento en que se realiza la acción para crear un nuevo grupo de comunidad, se selecciona la plantilla (estructura) del grupo. La selección depende de cómo se configuró la función Grupos al agregarla al sitio o a la plantilla de grupo.

>[!NOTE]
>
>Las consolas para la creación de [sitios de la comunidad](sites-console.md), [plantillas de sitio de la comunidad](sites.md), [plantillas de grupo de la comunidad](tools-groups.md) y [funciones de la comunidad](functions.md) solo se utilizan en el entorno de creación.

## Consola Plantillas de grupo {#group-templates-console}

En el entorno de creación, para llegar a la consola de plantillas de grupos

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Plantillas de grupo]**

Esta consola muestra las plantillas desde las que se muestra un [sitio de la comunidad](sites-console.md) se puede crear y permite crear nuevas plantillas de grupo.

![groupstemplate](assets/groupstemplate.png)

## Crear plantilla de grupo {#create-goup-template}

Para empezar a crear una plantilla de grupo nueva, seleccione **[!UICONTROL Crear]**

De este modo, aparecerá el panel Editor del sitio que contiene 3 subpaneles:

### Información básica {#basic-info}

![imagen_1-96](assets/chlimage_1-96.png)

En el panel Información básica , se configura un nombre, una descripción y si la plantilla está habilitada o deshabilitada:

* **[!UICONTROL Nuevo nombre de plantilla de grupo]**
ID del nombre de la plantilla

* **[!UICONTROL Descripción]**
La descripción de la plantilla

* **[!UICONTROL Deshabilitado/Habilitado]**
Un interruptor de alternancia que controla si la plantilla es referenciable

### Miniatura    {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Opcional) Seleccione el icono Cargar imagen para mostrar una miniatura junto con el nombre y la descripción a los creadores de los sitios de la comunidad.

### Estructura {#structure}

>[!CAUTION]
>
>Si trabaja con AEM 6.1 Communities FP4 o anterior, no agregue una función de grupo a una plantilla de grupo.
>
>La función de grupos anidados está disponible en Communities [FP1](communities.md#latestfeaturepack).
>
>Aún no se permite agregar una función Grupos como la primera o única función de una plantilla.

![grptemplateeditor](assets/grptemplateeditor.png)

Para agregar funciones de comunidad, arrastre desde la derecha a la izquierda en el orden en que deberían aparecer los vínculos de menú del sitio. Los estilos se aplicarán a la plantilla durante la creación del sitio.

Por ejemplo, si desea un foro, arrastre la función de foro desde la biblioteca y suéltela debajo del generador de plantillas. Esto hará que se abra el cuadro de diálogo de configuración del foro. Consulte la [consola funciones](functions.md) para obtener información sobre los cuadros de diálogo de configuración.

Continúe arrastrando y soltando cualquier otra función de la comunidad que desee para un sitio de subcomunidad (grupo) basado en esta plantilla.

![dragfunctions](assets/dragfunctions.png)

Una vez que todas las funciones deseadas se hayan colocado en el área del generador de plantillas y se hayan configurado, seleccione **[!UICONTROL Guardar]** en la esquina superior derecha.

## Editar plantilla del grupo {#edit-group-template}

Al ver los grupos de la comunidad en la variable principal [Consola Plantillas de grupo](#group-templates-console), es posible seleccionar una plantilla de grupo existente para editarla.

La edición de una plantilla de grupo no afectará a los sitios de la comunidad que ya se hayan creado a partir de la plantilla. Es posible [editar un sitio de la comunidad](sites-console.md#modify-structure)en su lugar, la estructura de .

Este proceso proporciona los mismos paneles que [creación de una plantilla de grupo](#create-goup-template).
