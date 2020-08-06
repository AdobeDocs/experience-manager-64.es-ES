---
title: Representaciones de vídeo
description: Representaciones de vídeo
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Video renditions {#video-renditions}

Adobe Experience Manager (AEM) Assets genera representaciones de vídeo para recursos de vídeo de varios formatos, incluidos OGG, FLV, etc.

AEM Assets admite representaciones estáticas y dinámicas (representaciones con codificación DM) para recursos multimedia.

Las representaciones estáticas se generan de forma nativa utilizando FFMPEG (instalado y disponible en la ruta del sistema) y se almacenan en el repositorio de contenido.

Las representaciones con codificación DM se almacenan en el servidor proxy y se sirven en tiempo de ejecución.

Los recursos de AEM permiten reproducir estas representaciones en el lado del cliente.

Para vista de las representaciones de un recurso de vídeo concreto, abra su página de recursos y toque el icono Navegación global. A continuación, elija **[!UICONTROL Representaciones]** en la lista.

![chlimage_1-478](assets/chlimage_1-478.png)

La lista de las representaciones de vídeo se muestra en el panel **[!UICONTROL Representaciones]** .

![chlimage_1-479](assets/chlimage_1-479.png)

Para configurar el servidor proxy para las representaciones con codificación DM, [configure los servicios de Dynamic Media Cloud.](config-dynamic.md)

Para generar representaciones de vídeo con parámetros deseados, [cree un perfil](video-profiles.md)de vídeo correspondiente.

Después de configurar el servidor proxy y crear perfiles de vídeo, puede incluir este ajuste preestablecido de vídeo en un perfil de procesamiento y aplicar el perfil de procesamiento a una carpeta.

>[!NOTE]
>
>La reproducción de audio no funciona con archivos OGG y WAV en Internet Explorer 11. Se muestra un error &quot;Origen no válido&quot; en la página de detalles del recurso para los recursos con la extensión OGG o WAV.
>
>En MS Edge y iPad, los archivos OGG no se reproducen y generan un error de formato no admitido.
