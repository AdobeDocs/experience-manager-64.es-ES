---
title: Agregar, activar, modificar o eliminar puntos finales
seo-title: Adding, enabling, modifying, or removing endpoints
description: Aprenda a añadir, habilitar, modificar y eliminar puntos finales.
seo-description: Learn how to add, enable, modify and remove endpoints.
uuid: c53f225b-3d55-42f6-8982-0cd7dde0c4f5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7d0d4f96-fc72-4e2b-a2cc-5741b0a30f74
exl-id: 8aed1439-aa39-4f75-909b-6a7ad7840a08
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 5%

---

# Agregar, activar, modificar o eliminar puntos finales {#adding-enabling-modifying-or-removing-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Añadir un extremo a un servicio {#add-an-endpoint-to-a-service}

Los puntos de conexión solo se pueden agregar a servicios. Un punto final no puede existir solo; debe estar asociado a un servicio.

>[!NOTE]
>
>Se recomienda utilizar nombres únicos al añadir extremos.

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de servicios.
1. En la página Administración de servicios , haga clic en el servicio para configurarlo.
1. En la lista de la ficha Extremos , seleccione el tipo de extremo que desea agregar y haga clic en Agregar.
1. Dependiendo del tipo de extremo, configure ajustes de extremo adicionales.

[Configuración de extremo de carpeta vigilada](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[Configuración de extremo de correo electrónico](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Configurar los extremos del Administrador de tareas](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Configuración de extremo remoto](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Haga clic en Agregar.

## Habilitar o deshabilitar un punto final {#enable-or-disable-an-endpoint}

De forma predeterminada, los nuevos extremos se activan automáticamente. Pero si ha deshabilitado un punto final, tendrá que habilitarlo para que funcione.

Si tiene problemas con los servicios, deshabilite los extremos asociados para solucionar mejor el problema. También es posible que desee deshabilitar los extremos durante el mantenimiento regular del sistema o al actualizar un servicio.

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de extremos.
1. En la página Administración de puntos de conexión, active la casilla de verificación del punto final para habilitar o deshabilitar y haga clic en Habilitar o Deshabilitar.

## Modificación de un punto final {#modify-an-endpoint}

>[!NOTE]
>
>Los cambios que realice en una configuración de extremo mediante la consola de administración no se reflejarán en las copias en tiempo de diseño de las aplicaciones. Si vuelve a implementar una aplicación, se perderá cualquier cambio que haya realizado en sus puntos finales mediante la consola de administración.

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de extremos.
1. En la página Administración de puntos finales , haga clic en el punto final para modificarlo.
1. En la página Actualizar extremo , modifique el nombre del extremo, la descripción y la configuración.

   >[!NOTE]
   >
   >No incluya un carácter &lt; en el nombre o la descripción porque truncará el nombre o la descripción mostrados en Workspace.

1. Para guardar los cambios, haga clic en Actualizar.

También puede realizar esta tarea desde la página Administración de servicios seleccionando un servicio y luego haciendo clic en la pestaña Puntos de conexión .

## Eliminar un punto final {#remove-an-endpoint}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de extremos.
1. En la página Administración de puntos de conexión, active la casilla de verificación del punto final que desea eliminar y haga clic en Quitar. El punto final ya no se muestra.
