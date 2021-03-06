---
title: Flujo de actividad en la cronología
description: 'Este artículo describe cómo mostrar los registros de actividad de los recursos en la cronología. '
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 21%

---

# Flujo de actividad en la cronología {#activity-stream-in-timeline}

Esta función muestra los registros de actividad de los recursos en la cronología. Si realiza cualquiera de las siguientes operaciones relacionadas con recursos en [!DNL Adobe Experience Manager Assets], la función Flujo de actividad actualiza la cronología para reflejar la actividad.

Las siguientes operaciones se registran en el flujo de actividad:

* Crear
* Eliminar
* Descargar (incluidas las representaciones)
* Publicación
* Cancelar publicación
* Aprobar
* Rechazar
* Mover

Los registros de actividad que se mostrarán en la cronología se recuperan de la ubicación `/var/audit/com.day.cq.dam/content/dam` en CRX, donde se almacenan los archivos de registro. 

Además, la actividad de la cronología se registra cuando se cargan nuevos recursos o cuando se modifican y se registran en el Experience Manager los recursos existentes mediante [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) o [[!DNL Experience Manager] Desktop App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>Los flujos de trabajo transitorios no se muestran en la cronología, ya que no se guarda información de historial para estos flujos de trabajo.

Para ver el flujo de actividad, realice una o más de las operaciones en el recurso, seleccione el recurso y, a continuación, elija **[!UICONTROL Línea de tiempo]** en la lista Navegador global.

![línea de tiempo-3](assets/timeline-3.png)

La cronología muestra el flujo de actividad de las operaciones que realiza en los recursos.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>La ubicación de almacenamiento de registro predeterminada para las tareas **Publicar** y **Cancelar la publicación** es `/var/audit/com.day.cq.replication/content`. Para las tareas **Mover**, la ubicación predeterminada es `/var/audit/com.day.cq.wcm.core.page`.
