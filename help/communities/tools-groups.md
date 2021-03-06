---
title: Plantillas de grupos
seo-title: Plantillas de grupos
description: Acceso a la consola Plantillas de grupo
seo-description: Acceso a la consola Plantillas de grupo
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# Plantillas de grupos {#group-templates}

La consola Plantillas de grupo es muy similar a la consola [Plantillas de sitio](sites.md). Ambos son modelos para un conjunto de páginas precableadas y características que forman un sitio de comunidad. La diferencia es que una plantilla de sitio es para la comunidad principal y una plantilla de grupo es para un grupo de comunidad, una subcomunidad anidada dentro de la comunidad principal.

Un grupo de comunidad se incorpora a una plantilla de sitio al incluir la función [Groups](functions.md#groups-function) (que puede no ser la primera ni la única función de la plantilla).

En Communities [feature pack 1](deploy-communities.md#latestfeaturepack), es posible anidar grupos incluyendo la función Grupos dentro de una plantilla de grupo.

En el momento en que se realiza la acción para crear un nuevo grupo de comunidad, se selecciona la plantilla (estructura) del grupo. La selección depende de cómo se configuró la función Grupos al agregarla al sitio o a la plantilla de grupo.

>[!NOTE]
>
>Las consolas para la creación de [sitios de la comunidad](sites-console.md), [plantillas de sitios de la comunidad](sites.md), [plantillas de grupos de la comunidad](tools-groups.md) y [funciones de la comunidad](functions.md) solo se deben usar en el entorno de creación.

## Consola Plantillas de grupo {#group-templates-console}

En el entorno de creación, para llegar a la consola de plantillas de grupos

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Plantillas de grupo]**

Esta consola muestra las plantillas desde las que se puede crear un [sitio de la comunidad](sites-console.md) y permite crear nuevas plantillas de grupo.

![groupstemplate](assets/groupstemplate.png)

## Crear plantilla de grupo {#create-goup-template}

Para empezar a crear una nueva plantilla de grupo, seleccione **[!UICONTROL Crear]**

De este modo, aparecerá el panel Editor del sitio que contiene 3 subpaneles:

### Información básica {#basic-info}

![imagen_1-96](assets/chlimage_1-96.png)

En el panel Información básica , se configura un nombre, una descripción y si la plantilla está habilitada o deshabilitada:

* **[!UICONTROL Nuevo]**
nombre de plantilla de grupoEl ID del nombre de la plantilla

* ****
DescripciónLa descripción de la plantilla

* **[!UICONTROL Deshabilitado/]**
HabilitadoUn conmutador que controla si se puede hacer referencia a la plantilla

### Miniatura    {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Opcional) Seleccione el icono Cargar imagen para mostrar una miniatura junto con el nombre y la descripción a los creadores de los sitios de la comunidad.

### Estructura {#structure}

>[!CAUTION]
>
>Si trabaja con AEM 6.1 Communities FP4 o anterior, no agregue una función de grupo a una plantilla de grupo.
>
>La función de grupos anidados está disponible desde Communities [FP1](communities.md#latestfeaturepack).
>
>Aún no se permite agregar una función Grupos como la primera o única función de una plantilla.

![grptemplateeditor](assets/grptemplateeditor.png)

Para agregar funciones de comunidad, arrastre desde la derecha a la izquierda en el orden en que deberían aparecer los vínculos de menú del sitio. Los estilos se aplicarán a la plantilla durante la creación del sitio.

Por ejemplo, si desea un foro, arrastre la función de foro desde la biblioteca y suéltela debajo del generador de plantillas. Esto hará que se abra el cuadro de diálogo de configuración del foro. Consulte la [consola de funciones](functions.md) para obtener información sobre los cuadros de diálogo de configuración.

Continúe arrastrando y soltando cualquier otra función de la comunidad que desee para un sitio de subcomunidad (grupo) basado en esta plantilla.

![dragfunctions](assets/dragfunctions.png)

Una vez que todas las funciones deseadas se hayan colocado en el área del generador de plantillas y se hayan configurado, seleccione **[!UICONTROL Guardar]** en la esquina superior derecha.

## Editar plantilla del grupo {#edit-group-template}

Al ver los grupos de la comunidad en la [Consola de plantillas de grupo](#group-templates-console) principal, es posible seleccionar una plantilla de grupo existente para editarla.

La edición de una plantilla de grupo no afectará a los sitios de la comunidad que ya se hayan creado a partir de la plantilla. Es posible editar directamente [la estructura de un sitio de la comunidad](sites-console.md#modify-structure) en su lugar.

Este proceso proporciona los mismos paneles que [crear una plantilla de grupo](#create-goup-template).
