---
title: Reescritura XMP en representaciones
description: Descubra cómo la función de reescritura XMP propaga los cambios de metadatos de un recurso en todas las representaciones del recurso o en determinadas representaciones.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 77c62a8f2ca50f8aaff556a6848fabaee71017ce
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 4%

---


# Reescritura XMP en representaciones {#xmp-writeback-to-renditions}

Esta función de reescritura XMP en Recursos Adobe Experience Manager (AEM) replica los cambios de metadatos de recursos en las representaciones del recurso.

Al cambiar los metadatos de un recurso desde Recursos AEM o al cargar el recurso, los cambios se almacenan inicialmente en el nodo de recurso en Crx-De.

La función de reescritura XMP propaga los cambios de metadatos en todas las representaciones del recurso o en determinadas representaciones.

Considere un escenario en el que modifique la propiedad [!UICONTROL Title] del recurso `Classic Leather` al que se denomina `Nylon`.

![metadata](assets/metadata.png)

En este caso, Recursos AEM guarda los cambios realizados en la propiedad **[!UICONTROL Title]** en el parámetro `dc:title` de los metadatos del recurso almacenados en la jerarquía de recursos.

![metadata_stored](assets/metadata_stored.png)

Sin embargo, Recursos AEM no propaga automáticamente ningún cambio de metadatos en las representaciones de un recurso.

La función de reescritura XMP le permite propagar los cambios de metadatos en todas las representaciones del recurso o en determinadas representaciones. Sin embargo, los cambios no se almacenan en el nodo de metadatos de la jerarquía de recursos. En su lugar, esta función incrusta los cambios en los archivos binarios para las representaciones.

## Habilitar reescritura XMP {#enabling-xmp-writeback}

Para permitir que los cambios de metadatos se propaguen a las representaciones del recurso al cargarlo, modifique la configuración de **Adobe CQ DAM Rendition Maker** en Configuration Manager.

1. Abra Configuration Manager desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración de **[!UICONTROL Adobe CQ DAM Rendition Maker]** .
1. Seleccione la opción **[!UICONTROL Propagar XMP]** y, a continuación, guarde los cambios.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Habilitar la reescritura XMP para representaciones específicas {#enabling-xmp-writeback-for-specific-renditions}

Para permitir que la función de reescritura XMP propague los cambios de metadatos para seleccionar las representaciones, especifique estas representaciones en el paso de flujo de trabajo del proceso de reescritura XMP del flujo de trabajo de escritura de metadatos DAM. De forma predeterminada, este paso se configura con la representación original.

Para que la función de reescritura XMP propague metadatos a las miniaturas de representación 140.100.png y 319.319.png, lleve a cabo estos pasos.

1. En Experience Manager, vaya a **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. En la página [!UICONTROL Modelos] , abra el modelo de flujo de trabajo de reescritura **[!UICONTROL de metadatos]** DAM.
1. En la página de **[!UICONTROL propiedades de escritura de metadatos DAM]**, abra el paso **[!UICONTROL Proceso de escritura XMP]**.
1. En el cuadro de diálogo **[!UICONTROL Propiedades del paso]**, pulse o haga clic en la pestaña **[!UICONTROL Proceso]**.
1. En el cuadro **[!UICONTROL Argumentos]** , agregue `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. To regenerate the pyramid TIFF renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata Writeback workflow.
Las representaciones PTIFF solo se crean y almacenan localmente en el modo Dynamic Media Hybrid. Guarde el flujo de trabajo.

Los cambios en los metadatos se propagan a las representaciones `thumbnail.140.100.png` y `thumbnail.319.319.png` al recurso, y no a los demás.

>[!NOTE]
>
>Para los problemas de escritura XMP en Linux de 64 bits, consulte [Cómo habilitar la escritura de retorno XMP en RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)de 64 bits.
>
>Para obtener más información sobre las plataformas admitidas, consulte Requisitos previos para la devolución de [metadatos XMP](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrar metadatos XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] admite tanto la lista bloqueada como el filtrado de listas permitido de propiedades/nodos para metadatos XMP que se leen desde binarios de recursos y se almacenan en JCR cuando se ingestan recursos.

El filtrado mediante una lista bloqueada permite importar todas las propiedades de metadatos XMP, excepto las propiedades especificadas para la exclusión. Sin embargo, para tipos de recursos como archivos INDD que tienen grandes cantidades de metadatos XMP (por ejemplo, 1000 nodos con 10.000 propiedades), los nombres de los nodos que se van a filtrar no siempre se conocen por adelantado. Si el filtrado mediante una lista bloqueada permite importar un gran número de recursos con numerosos metadatos XMP, la instancia de AEM o el clúster pueden tener problemas de estabilidad, por ejemplo, colas de observación obstruidas.

El filtrado de metadatos XMP mediante la lista permitida resuelve este problema permitiéndole definir las propiedades XMP que se van a importar. De este modo, se omiten todas las demás propiedades XMP o desconocidas. Para la compatibilidad con versiones anteriores, puede agregar algunas de estas propiedades al filtro que utiliza una lista bloqueada.

<!-- TBD: The instructions don't seem to match the UI. I see com.day.cq.dam.commons.metadata.XmpFilterBlackWhite.description
in Config Manager. And the settings are,
com.day.cq.dam.commons.metadata.XmpFilterBlackWhite.xmp.filter.apply_whitelist.name
com.day.cq.dam.commons.metadata.XmpFilterBlackWhite.xmp.filter.whitelist.name
com.day.cq.dam.commons.metadata.XmpFilterBlackWhite.xmp.filter.apply_blacklist.name
com.day.cq.dam.commons.metadata.XmpFilterBlackWhite.xmp.filter.blacklist.name
 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>El filtrado solo funciona para las propiedades derivadas de orígenes XMP en los binarios de recursos. Para las propiedades derivadas de orígenes no XMP, como los formatos EXIF e IPTC, el filtrado no funciona. Por ejemplo, la fecha de creación de recursos se almacena en la propiedad denominada `CreateDate` en TIFF EXIF. AEM almacena este valor en el campo de metadatos denominado `exif:DateTimeOriginal`. Como el origen es un origen que no es XMP, el filtrado no funciona en esta propiedad.

1. Abra Configuration Manager desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración de **[!UICONTROL Adobe CQ DAM XmpFilter]** .
1. To apply filtering via an allowed list, select **[!UICONTROL Apply Whitelist to XMP Properties]**, and specify the properties to be imported in the **[!UICONTROL Whitelisted XML Names for XMP filtering]** box.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. To filter out blocked XMP properties after applying filtering via allowed list, specify those in the **[!UICONTROL Blacklisted XML Names for XMP filtering]** box. Guarde los cambios.

   >[!NOTE]
   >
   >La opción **[!UICONTROL Aplicar lista negra a propiedades]** XMP está seleccionada de forma predeterminada. En otras palabras, el filtrado mediante una lista bloqueada está habilitado de forma predeterminada. Para desactivar este filtrado, anule la selección de la opción **[!UICONTROL Aplicar lista negra a propiedades]** XMP.
