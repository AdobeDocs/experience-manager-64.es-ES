---
title: Representaciones de vídeo
description: Representaciones de vídeo
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---

# Representaciones de vídeo {#video-renditions}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets genera representaciones de vídeo para recursos de vídeo de varios formatos, incluidos OGG, FLV, etc.

AEM Assets admite representaciones estáticas y dinámicas (representaciones con codificación DM) para recursos multimedia.

Las representaciones estáticas se generan de forma nativa utilizando FFMPEG (instalado y disponible en la ruta del sistema) y se almacenan en el repositorio de contenido.

Las representaciones con codificación DM se almacenan en el servidor proxy y se proporcionan durante la ejecución.

AEM recursos proporcionan compatibilidad con la reproducción de estas representaciones en el lado del cliente.

Para ver las representaciones de un recurso de vídeo en particular, abra su página de recursos y pulse el icono Navegación global . A continuación, elija **[!UICONTROL Representaciones]** de la lista.

![chlimage_1-478](assets/chlimage_1-478.png)

La lista de representaciones de vídeo se muestra en la **[!UICONTROL Representaciones]** panel.

![chlimage_1-479](assets/chlimage_1-479.png)

Para configurar el servidor proxy para representaciones con codificación DM, [configure los servicios de Dynamic Media Cloud.](config-dynamic.md)

Para generar representaciones de vídeo con los parámetros deseados, [crear un perfil de vídeo correspondiente](video-profiles.md).

Después de configurar el servidor proxy y crear perfiles de vídeo, puede incluir este ajuste preestablecido de vídeo en un perfil de procesamiento y aplicar el perfil de procesamiento a una carpeta.

>[!NOTE]
>
>La reproducción de audio no funciona para archivos OGG y WAV en Internet Explorer 11. El error &quot;Fuente no válida&quot; aparece en la página de detalles del recurso para los recursos con la extensión OGG o WAV.
>
>En MS Edge y iPad , los archivos OGG no se reproducen y generan un error de formato no admitido.
