---
title: Adición de fuentes para la renderización gráfica
seo-title: Adding Fonts for Graphic-Rendering
description: AEM le permite generar gráficos que incorporen texto tomado dinámicamente del contenido
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 4%

---

# Adición de fuentes para la renderización gráfica{#adding-fonts-for-graphic-rendering}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM permite generar gráficos que incorporen texto de forma dinámica tomado del contenido.

Para ello, también puede cargar y utilizar sus propias fuentes.

Actualmente, todas las implementaciones de la plataforma Java son compatibles [TrueType](https://en.wikipedia.org/wiki/Truetype) fuentes.

1. Abra el CRXDE Lite y vaya a la carpeta de la aplicación del proyecto:

   `/apps/<your-project>/`

1. En `/apps/<your-project>/` cree un nuevo nodo:

   * **Nombre**: `fonts`
   * **Tipo**: `sling:Folder`

   Guarde todos los cambios.

1. Copie los archivos de fuente en esta carpeta; por ejemplo, usando WebDAV.

   >[!NOTE]
   >
   >Los archivos de fuente del repositorio deben tener el sufijo `*.ttf` o `*.TTF`.

1. Actualice el [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) de [Ayudante de fuentes GFX de Day Commons](/help/sites-deploying/osgi-configuration-settings.md). Añada la ruta a la carpeta de fuentes; es decir, `/apps/<your-project>/fonts`.

1. Vuelva al CRXDE Lite. Ahora debería ver un `.fontlist` en la carpeta que contiene el nombre de las fuentes importadas.

   Estas fuentes ya están listas para utilizarse en la API de Java.

Para obtener más información sobre cómo utilizar las fuentes con la API de Java, consulte la [documentación para la clase Font de la API Java](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
