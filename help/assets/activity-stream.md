---
title: Flujo de actividad en la cronología
description: Este artículo describe cómo mostrar los registros de actividad de los recursos en la cronología.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 24%

---

# Flujo de actividad en la cronología {#activity-stream-in-timeline}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta función muestra los registros de actividad de los recursos en la cronología. Si realiza cualquiera de las siguientes operaciones relacionadas con activos en [!DNL Adobe Experience Manager Assets], la función Flujo de actividad actualiza la cronología para reflejar la actividad.

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

Además, la actividad de la cronología se registra cuando se cargan nuevos recursos o cuando se modifican y se registran en el Experience Manager los recursos existentes mediante [Vínculo de recurso de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) o [[!DNL Experience Manager] aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=es).

>[!NOTE]
>
>Los flujos de trabajo transitorios no se muestran en la cronología, ya que no se guarda información de historial para estos flujos de trabajo.

Para ver el flujo de actividad, realice una o varias operaciones en el recurso, seleccione el recurso y, a continuación, elija **[!UICONTROL Cronología]** de la lista de navegación global.

![línea de tiempo-3](assets/timeline-3.png)

La cronología muestra el flujo de actividad de las operaciones que realiza en los recursos.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>La ubicación de almacenamiento de registro predeterminada para las tareas **Publicar** y **Cancelar la publicación** es `/var/audit/com.day.cq.replication/content`. Para las tareas **Mover**, la ubicación predeterminada es `/var/audit/com.day.cq.wcm.core.page`.
