---
title: Compatibilidad con metadatos IPTC
description: Descubra cómo Adobe Experience Manager (AEM) Assets admite los metadatos IPTC, las clasificaciones creativas y las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 7%

---


# Compatibilidad con metadatos IPTC {#support-for-iptc-metadata}

Descubra cómo Adobe Experience Manager (AEM) Assets admite los metadatos IPTC, las clasificaciones creativas y las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas.

Recursos Adobe Experience Manager (AEM) es compatible con el estándar de metadatos IPTC que se utiliza ampliamente para describir recursos. De esta manera, AEM Assets mejora la aceptación de sus imágenes entre varias partes, incluyendo fotógrafos, agencias creativas, bibliotecas, museos, etc.

El esquema de metadatos predeterminado para los recursos ahora incorpora los esquemas de metadatos IPTC Core y IPTC Extension para definir propiedades de metadatos completas que permiten a los usuarios agregar datos precisos y fiables sobre las personas, ubicaciones y productos que se muestran en una imagen. También admite fechas, nombres e identificadores relacionados con la creación de la imagen, y una forma flexible de expresar información sobre derechos.

La página Propiedades de los recursos ahora incluye fichas independientes para mostrar los metadatos IPTC Core y Extensión IPTC en campos editables.

1. En la interfaz de usuario de Recursos, seleccione una imagen.
1. Toque o haga clic en el icono **[!UICONTROL Propiedades]** de la barra de herramientas.
1. En la página Propiedades, toque o haga clic en la ficha **[!UICONTROL IPTC]** para vista de metadatos IPTC para el recurso.
1. Edite las propiedades de metadatos IPTC según sea necesario.

   ![iptc_tab](assets/iptc_tab.png)

1. Pulse o haga clic en la pestaña **[!UICONTROL Extensión IPTC]** para ver los metadatos de la extensión IPTC para el recurso.
1. Edite las propiedades de metadatos de ITPC Extension según sea necesario.
1. Toque o haga clic **[!UICONTROL Guardar y cerrar]** para guardar los cambios.

## Compatibilidad con clasificación creativa {#creative-rating-support}

Además de mostrar clasificaciones de usuarios individuales y clasificaciones acumuladas, la página Propiedades ahora muestra las clasificaciones asignadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas

Estas clasificaciones están disponibles en la sección **[!UICONTROL Clasificación creativa]** de la pestaña **[!UICONTROL Avanzado]**.

Esta clasificación es una propiedad de sólo lectura e incluye entre 1 y 5. Puede buscar recursos en función de su clasificación creativa en el panel de búsqueda.

Sin embargo, esta propiedad no está indizada actualmente para evitar conflictos con los cambios personalizados realizados por los usuarios.

## Compatibilidad con palabras clave {#keyword-support}

La ficha **[!UICONTROL IPTC]** de la página Propiedades también muestra las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas. También puede editar estas palabras clave y agregar más palabras clave desde la ficha **[!UICONTROL IPTC]**.

![keywords](assets/keywords.png)

