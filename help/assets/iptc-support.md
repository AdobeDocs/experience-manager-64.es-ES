---
title: Compatibilidad con metadatos IPTC
description: Descubra cómo Adobe Experience Manager Assets admite los metadatos IPTC, las clasificaciones creativas y las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas.
contentOwner: AG
feature: Metadata
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 8%

---

# Compatibilidad con metadatos IPTC {#support-for-iptc-metadata}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Descubra cómo Adobe Experience Manager Assets admite los metadatos IPTC, las clasificaciones creativas y las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas.

Adobe Experience Manager Assets es compatible con el estándar de metadatos IPTC que se utiliza ampliamente para describir los recursos. De esta manera, [!DNL Experience Manager Assets] mejora la aceptación de sus imágenes entre varias partes, incluidos fotógrafos, agencias creativas, bibliotecas, museos, etc.

El esquema de metadatos predeterminado para los recursos ahora incorpora los esquemas de metadatos principales de IPTC y extensión IPTC para definir propiedades de metadatos completas que permitan a los usuarios añadir datos precisos y fiables sobre las personas, las ubicaciones y los productos mostrados en una imagen. También admite fechas, nombres e identificadores relacionados con la creación de la imagen, y una forma flexible de expresar información de derechos.

La página Propiedades de los recursos ahora incluye fichas independientes para mostrar los metadatos principales de IPTC y de la extensión IPTC en campos editables.

1. En la interfaz de usuario de Assets, seleccione una imagen.
1. Toque o haga clic en **[!UICONTROL Propiedades]** de la barra de herramientas.
1. En la página Propiedades , toque o haga clic en el **[!UICONTROL IPTC]** para ver los metadatos IPTC del recurso.
1. Edite las propiedades de los metadatos IPTC según sea necesario.

   ![iptc_tab](assets/iptc_tab.png)

1. Pulse o haga clic en la pestaña **[!UICONTROL Extensión IPTC]** para ver los metadatos de la extensión IPTC para el recurso.
1. Edite las propiedades de metadatos de la extensión ITPC, según sea necesario.
1. Toque o haga clic **[!UICONTROL Guardar y cerrar]** para guardar los cambios.

## Compatibilidad con la clasificación creativa {#creative-rating-support}

Además de mostrar las clasificaciones de usuarios individuales y las clasificaciones agregadas, la página Propiedades ahora muestra las clasificaciones asignadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas

Estas clasificaciones están disponibles en la sección **[!UICONTROL Clasificación creativa]** de la pestaña **[!UICONTROL Avanzado]**.

Esta clasificación es una propiedad de solo lectura e incluye entre 1 y 5. Puede buscar recursos en función de su clasificación creativa desde el panel Buscar .

Sin embargo, esta propiedad no está indexada actualmente para evitar conflictos con los cambios personalizados realizados por los usuarios.

## Compatibilidad con palabras clave {#keyword-support}

La variable **[!UICONTROL IPTC]** en la página Propiedades también muestra las palabras clave agregadas a los recursos a través de Adobe Bridge y otras aplicaciones creativas. También puede editar estas palabras clave y agregar más palabras clave desde **[!UICONTROL IPTC]** pestaña .

![keywords](assets/keywords.png)
