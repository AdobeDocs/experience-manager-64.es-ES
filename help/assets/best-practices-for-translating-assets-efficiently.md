---
title: Prácticas recomendadas para traducir recursos de forma eficiente
description: Prácticas recomendadas para una administración eficiente de los recursos con el fin de sincronizar varias versiones traducidas y optimizar los flujos de trabajo de traducción.
contentOwner: AG
feature: Traducción
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---

# Prácticas recomendadas para traducir recursos de forma eficaz {#best-practices-for-translating-assets-efficiently}

Adobe Experience Manager (AEM) Assets admite flujos de trabajo multilingües para traducir binarios, metadatos y etiquetas para recursos digitales a varias configuraciones regionales y administrar los recursos traducidos. Para obtener más información, consulte [Recursos multilingües](multilingual-assets.md).

Para una administración eficiente de los recursos y garantizar que las distintas versiones traducidas permanezcan sincronizadas, cree [copias de idioma](preparing-assets-for-translation.md) de los recursos antes de ejecutar los flujos de trabajo de traducción.

Una copia de idioma de un recurso o de un grupo de recursos es un elemento del mismo nivel de idioma (o una versión de los recursos en un idioma distinto) con una jerarquía de contenido similar.

Cada copia de idioma es un recurso independiente. Por lo tanto, la traducción de recursos en varias configuraciones regionales puede aumentar drásticamente el tamaño del repositorio CRX. Por ejemplo, la traducción de recursos con un tamaño combinado de 10 GB a dos idiomas puede aumentar el tamaño del repositorio en aproximadamente 20 GB (10 GB por cada idioma).

Los binarios de recursos ocupan un espacio de almacenamiento mucho mayor comparado con los metadatos y las etiquetas. Por lo tanto, si la traducción de metadatos y etiquetas solo cumple con su propósito, omita traducir los binarios. Puede conservar la copia original de los binarios en el repositorio para asociarla con metadatos y etiquetas traducidos a diferentes configuraciones regionales. El mantenimiento de una sola copia de binarios, en lugar de varias versiones traducidas, minimiza el impacto en el tamaño del repositorio.

El almacén de datos de archivos y el almacén de datos Amazon S3 proporcionan una infraestructura de almacenamiento que es más adecuada para estos escenarios. Estos repositorios de almacenamiento almacenan una sola copia de los binarios de recursos (incluidas las representaciones) que pueden compartirse mediante metadatos y etiquetas en varias configuraciones regionales. Por lo tanto, la creación de copias de idiomas de recursos y la traducción de metadatos y etiquetas no afectan al tamaño del repositorio.

También puede realizar algunos cambios en la configuración de un par de flujos de trabajo y del marco de integración de la traducción para racionalizar aún más el proceso.

1. Realice una de las acciones siguientes:

   * [Configuración del almacén de datos de archivos](/help/sites-deploying/data-store-config.md)
   * [Configuración del almacén de datos de Amazon S3](/help/sites-deploying/data-store-config.md)

1. Desactive el flujo de trabajo [DAM MetaData Writeback](/help/sites-administering/workflow-offloader.md#disable-offloading)

   Como su nombre indica, el flujo de trabajo *DAM Metadata Writeback* reescribe los metadatos en el archivo binario. Como los metadatos cambian después de la traducción, volver a escribirlos en el archivo binario genera un binario diferente para una copia de idioma.

   >[!NOTE]
   >
   >Al desactivar el flujo de trabajo *DAM MetaData Writeback*, se desactiva XMP reescritura de metadatos en los binarios de recursos. Por lo tanto, los cambios futuros en los metadatos ya no se guardan en los recursos. Evalúe las consecuencias antes de desactivar este flujo de trabajo.

1. Habilite el flujo de trabajo *Set last modified date* .

   El flujo de trabajo *DAM MetaData Writeback* configura la última fecha de modificación de un recurso. Como este flujo de trabajo se desactiva en el paso 2, AEM Assets ya no puede mantener actualizada la última fecha de modificación de los recursos. Por lo tanto, habilite el flujo de trabajo *Set last modified date* para garantizar que las fechas de las últimas modificaciones de los recursos estén actualizadas. Los recursos con fechas de última modificación obsoletas pueden causar errores.

1. [Configure el ](/help/sites-administering/tc-tic.md) marco de integración de traducción para detener la traducción de binarios de recursos. Anule la selección de la opción &quot;Traducir recursos&quot; en la pestaña Activos para detener la traducción de los binarios de recursos.
1. Traduzca metadatos/etiquetas de recursos mediante [Flujos de trabajo de recursos multilingües](multilingual-assets.md).
