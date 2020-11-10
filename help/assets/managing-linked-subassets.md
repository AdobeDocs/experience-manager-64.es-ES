---
title: Administre recursos compuestos y genere subrecursos.
description: Obtenga información sobre cómo crear referencias a AEM recursos desde archivos de InDesign, Adobe Illustrator y Photoshop. Aprenda también a utilizar la función Visor de páginas para la vista de páginas individuales de archivos de varias páginas, incluidos archivos PDF, INDD, PPT, PPTX y AI.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---


# Administrar recursos compuestos con subrecursos {#managing-compound-assets}

Los recursos de Adobe Experience Manager (AEM) pueden identificar si un archivo cargado contiene referencias a recursos que ya existen en el repositorio. Esta función solo está disponible para los formatos de archivo admitidos. Si el recurso cargado contiene referencias a AEM recursos, se crea un vínculo bidireccional entre los recursos cargados y los a los que se hace referencia.

Además de eliminar la redundancia, hacer referencia a los recursos AEM en las aplicaciones de Adobe Creative Cloud mejora la colaboración y aumenta la eficiencia y la productividad de los usuarios.

AEM Assets admite referencias **bidireccionales**. Los recursos a los que se hace referencia se encuentran en la página de detalles del recurso del archivo cargado. Además, puede realizar la vista de los archivos de referencia de AEM recursos en la página de detalles del recurso del recurso al que se hace referencia.

Las referencias se resuelven en función de la ruta de acceso, el ID de documento y el ID de instancia de los recursos a los que se hace referencia.

## Añadir AEM Assets como referencias en Adobe Illustrator {#refai}

Puede hacer referencia a recursos de AEM existentes desde un archivo Adobe Illustrator.

1. Mediante [AEM aplicación](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)de escritorio, monte el repositorio de AEM Assets como unidad en el equipo local. En la unidad montada, navegue a la ubicación del recurso al que desee hacer referencia.
1. Arrastre el recurso desde la unidad montada al archivo Illustrator.
1. Guarde el archivo Illustrator en la unidad montada o [cárguelo](managing-assets-touch-ui.md#uploading-assets) en el repositorio de AEM.
1. Una vez finalizado el flujo de trabajo, vaya a la página de detalles del recurso. Las referencias a los recursos AEM existentes se enumeran en **[!UICONTROL Dependencias]** en la columna **[!UICONTROL Referencias]** .

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Los recursos a los que se hace referencia y que aparecen en **[!UICONTROL Dependencias]** también pueden ser referenciados por otros archivos que no sean el actual. Para vista de una lista de archivos de referencia para un recurso, haga clic en el recurso en la sección **[!UICONTROL Dependencias]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Haga clic en el icono Propiedades **[!UICONTROL de la]** Vista de la barra de herramientas. En la página de propiedades, la lista de archivos que hacen referencia al recurso actual aparece en la columna **[!UICONTROL Referencias]** de la ficha **[!UICONTROL Básico]** .

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Añadir AEM recursos como referencias en Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Para hacer referencia a AEM recursos desde dentro de un archivo de InDesign, arrastre AEM recursos al archivo de InDesign o exporte el archivo de InDesign como archivo ZIP.

Los recursos a los que se hace referencia ya existen en AEM Assets. Puede extraer subrecursos [configurando el servidor](indesign.md)de InDesign. Los recursos incrustados en un archivo InDesign se extraen como subrecursos.

>[!NOTE]
>
>Si se procesa como proxy el servidor InDesign, los archivos InDesign tienen su previsualización incrustada en sus metadatos XMP. En este caso, la extracción de miniaturas no es obligatoria explícitamente. Sin embargo, si el servidor InDesign no se procesa como proxy, las miniaturas deben extraerse explícitamente para los archivos InDesign.

### Crear referencias arrastrando recursos AEM {#create-references-by-dragging-aem-assets}

Este procedimiento es similar a [Añadir AEM recursos como referencias en Adobe Illustrator](#refai).

### Creación de referencias a AEM recursos mediante la exportación de un archivo ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Siga los pasos que se describen en [Creación de modelos](/help/sites-developing/workflows-models.md) de flujo de trabajo para crear un nuevo flujo de trabajo.
1. Utilice la función Empaquetar de Adobe InDesign para exportar el documento.
Adobe InDesign puede exportar un documento y los recursos vinculados como un paquete. En este caso, la carpeta exportada contiene una carpeta Links que contiene subrecursos en el archivo InDesign.
1. Cree un archivo ZIP y cárguelo en el repositorio de AEM.
1. Inicio del flujo de trabajo de Unarchiver.
1. Cuando se completa el flujo de trabajo, se hace referencia automáticamente a las referencias de la carpeta Vínculos como subrecursos. Para realizar la vista de una lista de los recursos referidos, navegue a la página de detalles del recurso de InDesign y cierre el [raíl](/help/sites-authoring/basic-handling.md#rail-selector).

## Añadir AEM recursos como referencias en Adobe Photoshop {#refps}

1. Con un cliente WebDav, monte AEM Assets como unidad.
1. Para crear referencias a AEM recursos en un archivo Photoshop, navegue a los recursos correspondientes en la unidad montada utilizando la función Colocar vínculo en Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Guarde el archivo en Photoshop en la unidad montada o [cárguelo](managing-assets-touch-ui.md#uploading-assets) en el repositorio de AEM.
1. Una vez completado el flujo de trabajo, las referencias a los recursos de AEM existentes se muestran en la página de detalles del recurso.

   Para vista de los recursos a los que se hace referencia, cierre el [raíl](/help/sites-authoring/basic-handling.md#rail-selector) en la página de detalles del recurso.

1. Los recursos a los que se hace referencia también contienen la lista de los recursos desde los que se hace referencia. Para vista de una lista de recursos a los que se hace referencia, vaya a la página de detalles del recurso y cierre el [carril](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>También se puede hacer referencia a los recursos dentro de los recursos compuestos en función de su ID de Documento y su ID de instancia. Esta funcionalidad solo está disponible en las versiones de Adobe Illustrator y Adobe Photoshop. Para otros, la referencia se realiza en función de la ruta relativa de los recursos vinculados en el activo compuesto principal, como se hacía en versiones anteriores de AEM.

## Creación de subrecursos {#generate-subassets}

Para los recursos admitidos con formatos de varias páginas: archivos PDF, archivos AI, archivos Keynote de Microsoft PowerPoint y Apple y archivos Adobe InDesign: AEM generar subrecursos que corresponden a cada página individual del recurso original. Estos subrecursos están vinculados al recurso *principal* y facilitan la vista de varias páginas. Para todos los demás fines, los subactivos se tratan como activos normales en AEM.

La generación de subconjuntos está deshabilitada de forma predeterminada. Para habilitar la generación de subrecursos, siga estos pasos:

1. Inicie sesión en Experience Manager como administrador. Acceda a **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. Seleccione **[!UICONTROL Flujo de trabajo de recursos]** de actualización de DAM y haga clic en **[!UICONTROL Editar]**.
1. Haga clic en **[!UICONTROL Alternar panel]** lateral y busque el paso **[!UICONTROL Crear subrecurso]** . Añada el paso al flujo de trabajo. Haga clic en **[!UICONTROL Sincronizar]**.

Para generar los subrecursos, realice una de las siguientes acciones:

* Nuevos recursos: El flujo de trabajo de recursos [!UICONTROL de actualización de] DAM se ejecuta en cualquier recurso nuevo que se cargue en AEM. Los subrecursos se generan automáticamente para los nuevos recursos de varias páginas.
* Recursos existentes de varias páginas: Ejecute manualmente el flujo de trabajo de Recursos [!UICONTROL de actualización de] DAM siguiendo uno de los pasos siguientes:

   * Seleccione un recurso y haga clic en [!UICONTROL Línea de tiempo] para abrir el panel izquierdo. Como alternativa, utilice el método abreviado de teclado `alt + 3`. Haga clic en Flujo de trabajo [!UICONTROL de]Inicio, seleccione [!UICONTROL DAM Update Asset], haga clic en [!UICONTROL Inicio]y, a continuación, en [!UICONTROL Continuar].
   * Seleccione un recurso y haga clic en [!UICONTROL Crear > Flujo de trabajo] en la barra de herramientas. En el cuadro de diálogo emergente, seleccione [!UICONTROL DAM Update Asset] workflow, haga clic en [!UICONTROL Inicio]y, a continuación, en [!UICONTROL Continuar].

Específicamente para documentos de Microsoft Word, ejecute el flujo de trabajo de Documentos **[!UICONTROL de Word de análisis de]** DAM. Genera un `cq:Page` componente a partir del contenido del documento de Microsoft Word. Se hace referencia a las imágenes extraídas del documento desde el `cq:Page` componente. Estas imágenes se extraen aunque la generación de subrecursos esté desactivada.

## View subassets {#viewing-subassets}

Los subrecursos solo se muestran si se generan y están disponibles para el recurso de varias páginas seleccionado. Para vista de los subrecursos generados, abra el recurso de varias páginas. En el área superior izquierda de la página, haga clic en el icono ![del carril](assets/do-not-localize/aem_leftrail_contentonly.png) izquierdo y haga clic en **[!UICONTROL Subrecursos]** en la lista. Al seleccionar **[!UICONTROL Subrecursos]** en la lista. Como alternativa, utilice el método abreviado de teclado `alt + 5`.

![Subrecursos de vista para un recurso de varias páginas](assets/view_subassets_simulation.gif)

## Vista de páginas de un archivo de varias páginas {#view-pages-of-a-multi-page-file}

Puede realizar la vista de un archivo de varias páginas, como un archivo PDF, INDD, PPT, PPTX y AI, mediante la función Visor de páginas de AEM Assets. Abra un recurso de varias páginas y haga clic en **[!UICONTROL Vista Páginas]** en la esquina superior izquierda de la página. El visor de páginas que se abre muestra las páginas del recurso y los controles para examinar y aplicar zoom en cada página.

![Vista y visualización de páginas de un recurso de varias páginas](assets/view_multipage_asset_fmr.gif)

Para InDesign, puede extraer páginas mediante el servidor de InDesign. Si las previsualizaciones de las páginas se guardan durante la creación del archivo de InDesign, no es necesario el InDesign Server para la extracción de páginas.

Las siguientes opciones están disponibles en la barra de herramientas, en el carril izquierdo y en los controles del visor de páginas:

* **[!UICONTROL Acciones]** de escritorio para abrir o mostrar un subrecurso específico mediante AEM aplicación de escritorio. Consulte cómo [configurar acciones](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2) de escritorio si utiliza AEM aplicación de escritorio.

* **[!UICONTROL La opción Propiedades]** abre la página [!UICONTROL Propiedades] del subrecurso específico.

* **[!UICONTROL La opción Anotar]** le permite anotar el subrecurso específico. Las anotaciones que se utilizan en subrecursos independientes se recopilan y muestran juntas cuando se abre el recurso principal para su visualización.

* **[!UICONTROL La opción Información general]** de página muestra todos los subrecursos simultáneamente.

* **[!UICONTROL La opción Línea de tiempo]** del carril izquierdo después de hacer clic en el icono ![del carril](assets/do-not-localize/aem_leftrail_contentonly.png) izquierdo muestra el flujo de actividad del archivo.

## Prácticas recomendadas y limitación {#best-practice-limitation-tips}

* La generación de subrecursos puede requerir muchos recursos en cualquier implementación de Experience Manager. Si está generando subrecursos al cargar recursos complejos, agregue el paso en el flujo de trabajo de recursos de actualización de DAM. Si está generando subrecursos a petición, cree un flujo de trabajo independiente para generar subrecursos. Un flujo de trabajo dedicado le permite omitir los demás pasos del flujo de trabajo de recursos de actualización de DAM y guardar los recursos computacionales.

>[!MORELIKETHIS]
>
>* [Uso de la aplicación de escritorio de Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

