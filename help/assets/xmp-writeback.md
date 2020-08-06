---
title: Reescritura XMP en representaciones
description: Descubra cómo la función de reescritura XMP propaga los cambios de metadatos de un recurso en todas las representaciones del recurso o en determinadas representaciones.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 4%

---


# Reescritura XMP en representaciones {#xmp-writeback-to-renditions}

Esta función de reescritura XMP en Recursos Adobe Experience Manager (AEM) replica los cambios de metadatos de los recursos en las representaciones del recurso.

Al cambiar los metadatos de un recurso desde AEM Assets o al cargarlo, los cambios se almacenan inicialmente en el nodo de recurso en Crx-De.

La función de reescritura XMP propaga los cambios de metadatos en todas las representaciones o en determinadas representaciones del recurso.

Considere un escenario en el que modifique la propiedad [!UICONTROL Title] del recurso `Classic Leather` al que se denomina `Nylon`.

![metadata](assets/metadata.png)

En este caso, AEM Assets guarda los cambios en la propiedad **[!UICONTROL Title]** en el `dc:title` parámetro de los metadatos del recurso almacenados en la jerarquía de recursos.

![metadata_stored](assets/metadata_stored.png)

Sin embargo, AEM Assets no propaga automáticamente ningún cambio de metadatos en las representaciones de un recurso.

La función de reescritura XMP permite propagar los cambios de metadatos a todas las representaciones del recurso o a determinadas representaciones del recurso. Sin embargo, los cambios no se almacenan en el nodo de metadatos de la jerarquía de recursos. En su lugar, esta función incrusta los cambios en los archivos binarios para las representaciones.

## Habilitar reescritura XMP {#enabling-xmp-writeback}

Para permitir que los cambios de metadatos se propaguen a las representaciones del recurso al cargarlo, modifique la configuración de **Adobe CQ DAM Rendition Maker** en Configuration Manager.

1. Abra Configuration Manager desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración de **[!UICONTROL Adobe CQ DAM Rendition Maker]** .
1. Seleccione la **[!UICONTROL opción Propagar XMP]** y, a continuación, guarde los cambios.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Habilitar reescritura XMP para representaciones específicas {#enabling-xmp-writeback-for-specific-renditions}

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
>Para XMP problemas de escritura en Linux de 64 bits, consulte [Cómo habilitar XMP escritura en RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)de 64 bits.
>
>Para obtener más información acerca de las plataformas admitidas, consulte [XMP requisitos previos](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)de eliminación de metadatos.

## Filtrar metadatos XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] admite el filtrado de propiedades y nodos de lista de bloqueados y lista de permitidos para XMP metadatos que se leen desde binarios de recursos y se almacenan en JCR cuando se ingestan recursos.

El filtrado mediante una lista de bloqueados permite importar todas las propiedades de metadatos de XMP, excepto las propiedades especificadas para la exclusión. Sin embargo, para tipos de recursos como archivos INDD que tienen grandes cantidades de metadatos de XMP (por ejemplo, 1000 nodos con 10.000 propiedades), los nombres de los nodos que se van a filtrar no siempre se conocen por adelantado. Si el filtrado mediante una lista de bloqueados permite importar un gran número de recursos con numerosos metadatos de XMP, la instancia de AEM o el clúster pueden encontrar problemas de estabilidad, por ejemplo, colas de observación obstruidas.

El filtrado de metadatos de XMP mediante la lista de permitidos resuelve este problema permitiéndole definir las propiedades de XMP que se van a importar. De este modo, se omiten todas las demás propiedades de XMP o desconocidas. Para la compatibilidad con versiones anteriores, puede agregar algunas de estas propiedades al filtro que utiliza una lista de bloqueados.

>[!NOTE]
>
>El filtrado solo funciona para las propiedades derivadas de orígenes de XMP en los binarios de recursos. Para las propiedades derivadas de orígenes no XMP, como los formatos EXIF e IPTC, el filtrado no funciona. Por ejemplo, la fecha de creación de recursos se almacena en la propiedad denominada `CreateDate` en TIFF EXIF. AEM almacena este valor en el campo de metadatos denominado `exif:DateTimeOriginal`. Como el origen no es un origen XMP, el filtrado no funciona en esta propiedad.

1. Abra Configuration Manager desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración de **[!UICONTROL Adobe CQ DAM XmpFilter]** .
1. To apply filtering via an allowed list, select **[!UICONTROL Apply Allowlist to XMP Properties]**, and specify the properties to be imported in the **[!UICONTROL Allowed XML Names for XMP filtering]** box.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Para filtrar las propiedades de XMP bloqueadas después de aplicar el filtrado mediante lista de permitidos, especifique las que aparecen en el cuadro Nombres XML **[!UICONTROL bloqueados para XMP filtrado]** . Guarde los cambios.

   >[!NOTE]
   >
   >La opción **[!UICONTROL Aplicar Lista de bloqueados a propiedades]** XMP está seleccionada de forma predeterminada. En otras palabras, el filtrado mediante una lista de bloqueados está activado de forma predeterminada. Para desactivar este filtrado, anule la selección de la opción **[!UICONTROL Aplicar Lista de bloqueados a propiedades]** de XMP.
