---
title: Plantillas de sitios
seo-title: Site Templates
description: Cómo acceder a la consola Plantillas de sitio
seo-description: How to access the Site Templates console
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---

# Plantillas de sitios {#site-templates}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La consola Plantillas de sitio es muy similar a la del [Plantillas de grupo](tools-groups.md) consola, que se centra en funciones de interés para los grupos comunitarios.

>[!NOTE]
>
>Las consolas para la creación de [sitios de la comunidad](sites-console.md), [plantillas de sitio de la comunidad](sites.md), [plantillas de grupo de la comunidad](tools-groups.md) y [funciones de la comunidad](functions.md) solo se utilizan en el entorno de creación.

## Consola Plantillas del sitio {#site-templates-console}

En el entorno de creación, para llegar a la consola Sitios de comunidad

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Plantillas de sitio]**

Esta consola muestra las plantillas desde las que se muestra un [sitio de la comunidad](sites-console.md) se puede crear y permite crear nuevas plantillas de sitio.

![chlimage_1-18](assets/chlimage_1-18.png)

## Crear plantilla del sitio {#create-site-template}

Para empezar a crear una plantilla de sitio nueva, seleccione `Create`.

De este modo, aparecerá el panel Editor del sitio que contiene 3 subpaneles:

### Información básica {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

En el panel Información básica , se configura un nombre, una descripción y si la plantilla está habilitada o deshabilitada:

* **[!UICONTROL Nombre de plantilla del sitio de la comunidad]**
ID del nombre de la plantilla

* **[!UICONTROL Descripción de la plantilla del sitio de la comunidad]**
La descripción de la plantilla

* **[!UICONTROL Deshabilitado/Habilitado]**
Un interruptor de alternancia que controla si la plantilla es referenciable

### Miniatura    {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Opcional) Seleccione el icono Cargar imagen para mostrar una miniatura junto con el nombre y la descripción a los creadores de los sitios de la comunidad.

### Estructura {#structure}

![imagen_1-21](assets/chlimage_1-21.png)

Para agregar funciones de comunidad, arrastre desde la derecha a la izquierda en el orden en que deberían aparecer los vínculos de menú del sitio. Los estilos se aplicarán a la plantilla durante la creación del sitio.

Por ejemplo, si desea una página de inicio, arrastre la función Página de la biblioteca y suéltela debajo del generador de plantillas. Esto hará que se abra el cuadro de diálogo de configuración de la página. Consulte la [consola funciones](functions.md) para obtener información sobre los cuadros de diálogo de configuración.

Continúe arrastrando y soltando cualquier otra función de la comunidad que desee para un sitio de la comunidad basada en esta plantilla.

La función page proporciona una página vacía. La función de grupos permite crear un sitio de grupo (subcomunidad) dentro del sitio de la comunidad.

>[!CAUTION]
>
>La función de grupos debe *not* sea el *primero ni único* en la estructura del sitio.
>
>Cualquier otra función, como la [función de página](functions.md#page-function), debe incluirse y aparecer en primer lugar en la lista.

![imagen_1-22](assets/chlimage_1-22.png)

### Plantillas de grupo para la función Grupos {#group-templates-for-groups-function}

Al incluir una función de grupos en la plantilla de sitio, la configuración requiere la especificación de las opciones de plantilla de grupo permitidas cuando se crea un nuevo grupo en el entorno de publicación.

>[!CAUTION]
>
>La función Grupos debe *not* sea el *primero ni único* en la estructura del sitio.

![imagen_1-23](assets/chlimage_1-23.png)

Al seleccionar dos o más plantillas de grupo de comunidad, se proporciona una opción al administrador del grupo al crear realmente un nuevo grupo en la comunidad.

![imagen_1-24](assets/chlimage_1-24.png)

## Editar plantilla del sitio {#edit-site-template}

Al ver las plantillas del sitio en la variable principal [Consola Plantillas de sitio](#site-templates-console), es posible seleccionar una plantilla de sitio existente para editarla.

Este proceso proporciona los mismos paneles que [creación de una plantilla de sitio](#create-site-template).
