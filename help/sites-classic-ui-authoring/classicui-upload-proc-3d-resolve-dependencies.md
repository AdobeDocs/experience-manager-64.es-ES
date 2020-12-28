---
title: Resolución de dependencias de archivo
seo-title: Resolución de dependencias de archivo
description: Las dependencias principales de archivo de modelo 3D, como archivos de mapa de textura, se resuelven automáticamente en la medida de lo posible. Para conseguir esta funcionalidad, AEM debe buscar en carpetas de Assets cercanas archivos con los mismos nombres que los que se encuentran en el archivo 3D.
seo-description: Las dependencias principales de archivo de modelo 3D, como archivos de mapa de textura, se resuelven automáticamente en la medida de lo posible. Para conseguir esta funcionalidad, AEM debe buscar en carpetas de Assets cercanas archivos con los mismos nombres que los que se encuentran en el archivo 3D.
uuid: b1b83cb7-b6e5-4417-9a53-b6d8bcf8d2e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 14754023-e7c4-4dc5-a9d8-408b81861d95
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 61%

---


# Resolución de dependencias de archivo{#resolving-file-dependencies}

Las dependencias principales de archivo de modelo 3D, como archivos de mapa de textura, se resuelven automáticamente en la medida de lo posible. Para conseguir esta funcionalidad, AEM debe buscar en carpetas de Assets cercanas archivos con los mismos nombres que los que se encuentran en el archivo 3D. Si una o varias dependencias no se pueden resolver durante la etapa de procesamiento de la creación de previsualizaciones, la tarjeta del recurso muestra el siguiente mensaje de letrero rojo en la [!UICONTROL Vista de tarjetas]:

![chlimage_1-189](assets/chlimage_1-189.png)

**Para resolver dependencias de archivo**:

1. En la **[!UICONTROL Vista de tarjeta]**, pase el puntero sobre el mensaje de la pancarta **[!UICONTROL Dependencias no resueltas]** de la tarjeta y, a continuación, toque el icono del signo de exclamación.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. En la página Propiedades de metadatos, toque la pestaña **[!UICONTROL Dependencias]**.

   Los archivos que AEM no ha podido resolver automáticamente se muestran debajo de la columna Rutas de acceso originales, en rojo.

1. Realice una o varias de las acciones siguientes:

   * **[!UICONTROL Busque y seleccione las dependencias]**. (Esta opción da por hecho que ya ha cargado los archivos de dependencia).

      1. Toque el icono **[!UICONTROL Examinar archivo]** a la izquierda de la ruta roja.
      1. En la página **[!UICONTROL Seleccionar contenido]**, desplácese hasta el archivo que falta y toque la tarjeta del archivo para seleccionarlo.
      1. En la esquina superior izquierda de la página **[!UICONTROL Seleccionar contenido]**, toque **[!UICONTROL Cerrar]** (icono X) para volver a la página **[!UICONTROL Propiedades de la Vista]**.
   * **[!UICONTROL Cargue las dependencias]**. (Esta opción da por hecho que todavía no ha cargado los archivos no disponibles).

      1. Tenga en cuenta las rutas de acceso y los nombres de archivo no disponibles.
      1. Cerca de la esquina superior derecha de la página Propiedades, toque **[!UICONTROL Cerrar]**.

   Después de cargar los archivos, vuelva a la página **[!UICONTROL Propiedades de la Vista > Dependencias]**. El recurso recién cargado se muestra ahora correctamente como recurso al que se hace referencia.

   * **[!UICONTROL Ignore las dependencias]**.

      Si ya no necesita una dependencia que falta, en la columna **[!UICONTROL Recurso al que se hace referencia]**, en el campo de texto a la izquierda del archivo que falta, escriba `n/a` para que AEM 3D ignore el archivo.



1. Cerca de la esquina superior derecha de la página **[!UICONTROL Propiedades de la Vista]**, toque **[!UICONTROL Guardar]**.
1. Toque **[!UICONTROL Cerrar]****[!UICONTROL para volver a la vista de tarjeta]**.

   El recurso se vuelve a procesar automáticamente con las dependencias recién resueltas.

