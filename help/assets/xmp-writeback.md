---
title: Reescritura XMP en representaciones
description: Descubra cómo la función XMP reescritura propaga los cambios de metadatos de un recurso a todas las representaciones del recurso o a algunas de ellas.
contentOwner: AG
feature: Metadatos
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 4%

---

# Reescritura XMP en representaciones {#xmp-writeback-to-renditions}

Esta función XMP reescritura en [!DNL Adobe Experience Manager Assets] duplica los cambios de metadatos en las representaciones del recurso original. Al cambiar los metadatos de un recurso desde Assets o al cargarlo, los cambios se almacenan inicialmente en el nodo de metadatos de la jerarquía de recursos.

La función XMP reescritura permite propagar los cambios de metadatos a todas las representaciones del recurso o a algunas de ellas. La función solo recupera las propiedades de metadatos que utilizan el espacio de nombres `jcr`, es decir, una propiedad denominada `dc:title` se vuelve a escribir, pero no una propiedad denominada `mytitle`.

Considere un escenario en el que modifique la propiedad [!UICONTROL Title] del recurso titulada `Classic Leather` a `Nylon`.

![metadata](assets/metadata.png)

En este caso, AEM Assets guarda los cambios en la propiedad **[!UICONTROL Title]** en el parámetro `dc:title` para los metadatos de recurso almacenados en la jerarquía de recursos.

![metadata_stored](assets/metadata_stored.png)

Sin embargo, [!DNL Experience Manager Assets] no propaga automáticamente ningún cambio en los metadatos de las representaciones de un recurso. Consulte [cómo habilitar XMP reescritura](#enabling-xmp-writeback).

## Habilitar reescritura XMP {#enabling-xmp-writeback}

Para permitir que los cambios en los metadatos se propaguen a las representaciones del recurso al cargarlo, modifique la configuración **Adobe CQ DAM Rendition Maker** en Configuration Manager.

1. Abra el Administrador de configuración desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Seleccione la opción **[!UICONTROL Propagate XMP]** y, a continuación, guarde los cambios.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Habilitar XMP escritura para representaciones específicas {#enabling-xmp-writeback-for-specific-renditions}

Para permitir que la función XMP de reescritura propague los cambios de metadatos para seleccionar representaciones, especifique estas representaciones en el paso de flujo de trabajo XMP proceso de reescritura del flujo de trabajo de reescritura de metadatos DAM. De forma predeterminada, este paso se configura con la representación original.

Para que la función de escritura XMP propague metadatos a las miniaturas de representación 140.100.png y 319.319.png, realice estos pasos.

1. En el Experience Manager, vaya a **[!UICONTROL Tools > Workflow > Models]**.
1. En la página [!UICONTROL Modelos], abra el modelo de flujo de trabajo **[!UICONTROL reescritura de metadatos DAM]**.
1. En la página de **[!UICONTROL propiedades de escritura de metadatos DAM]**, abra el paso **[!UICONTROL Proceso de escritura XMP]**.
1. En el cuadro de diálogo **[!UICONTROL Propiedades del paso]**, pulse o haga clic en la pestaña **[!UICONTROL Proceso]**.
1. En el cuadro **[!UICONTROL Argumentos]**, añada `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Toque o haga clic en **[!UICONTROL Aceptar]**.

   ![step_properties](assets/step_properties.png)

1. Para volver a generar las representaciones TIFF piramidales para imágenes Dynamic Media con los nuevos atributos, agregue el paso **[!UICONTROL Dynamic Media Process Image Assets]** al flujo de trabajo de escritura de metadatos DAM.
Las representaciones PTIFF solo se crean y almacenan localmente en un modo híbrido de Dynamic Media. Guarde el flujo de trabajo.

Los cambios en los metadatos se propagan a las representaciones `thumbnail.140.100.png` y `thumbnail.319.319.png` del recurso, y no a las demás.

>[!NOTE]
>
>Para XMP problemas de escritura en Linux de 64 bits, vea [Cómo habilitar XMP escritura en RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) de 64 bits.
>
>Para obtener más información sobre las plataformas admitidas, consulte [XMP requisitos previos de reescritura de metadatos](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrar XMP metadatos {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] admite el filtrado de listas de permitidos y listas de bloqueados de propiedades/nodos para XMP metadatos que se leen desde binarios de recursos y se almacenan en JCR cuando se introducen recursos.

El filtrado mediante una lista de bloqueados permite importar todas las propiedades de metadatos XMP, excepto las propiedades especificadas para la exclusión. Sin embargo, para tipos de recursos como archivos INDD que tienen grandes cantidades de metadatos XMP (por ejemplo, 1000 nodos con 10 000 propiedades), los nombres de los nodos que se van a filtrar no siempre se conocen de antemano. Si el filtrado mediante una lista de bloqueados permite importar un gran número de recursos con numerosos metadatos de XMP, la instancia de AEM o el clúster pueden encontrar problemas de estabilidad, por ejemplo, colas de observación obstruidas.

El filtrado de metadatos de XMP mediante lista de permitidos resuelve este problema ya que permite definir las propiedades de XMP que se van a importar. De este modo, se ignorarán todas las demás propiedades de XMP o desconocidas. Para la compatibilidad con versiones anteriores, puede añadir algunas de estas propiedades al filtro que utiliza una lista de bloqueados .

>[!NOTE]
>
>El filtrado solo funciona para las propiedades derivadas de XMP orígenes en los binarios de recursos. Para las propiedades derivadas de orígenes no XMP, como los formatos EXIF e IPTC, el filtrado no funciona. Por ejemplo, la fecha de creación del recurso se almacena en la propiedad denominada `CreateDate` en el TIFF EXIF. AEM almacena este valor en el campo de metadatos denominado `exif:DateTimeOriginal`. Como el origen no es un origen XMP, el filtrado no funciona en esta propiedad.

1. Abra el Administrador de configuración desde `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra la configuración **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Para aplicar el filtrado a través de una lista de permitidos, seleccione **[!UICONTROL Aplicar Lista de permitidos a XMP Propiedades]** y especifique las propiedades que desea importar en el cuadro **[!UICONTROL Nombres XML permitidos para XMP filtrado]**.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Para filtrar las propiedades de XMP bloqueadas después de aplicar el filtrado mediante lista de permitidos, especifique las que aparecen en el cuadro **[!UICONTROL Nombres XML bloqueados para XMP filtrado]**. Guarde los cambios.

   >[!NOTE]
   >
   >La opción **[!UICONTROL Aplicar Lista de bloqueados a XMP propiedades]** está seleccionada de forma predeterminada. En otras palabras, el filtrado mediante una lista de bloqueados está habilitado de forma predeterminada. Para desactivar este filtro, anule la selección de la opción **[!UICONTROL Aplicar Lista de bloqueados a XMP propiedades]**.
