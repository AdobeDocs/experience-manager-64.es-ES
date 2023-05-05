---
title: Administre recursos compuestos y genere subrecursos.
description: Aprenda a crear referencias a [!DNL Experience Manager] recursos desde archivos de InDesign, Adobe Illustrator y Photoshop. Aprenda también a utilizar la función Visualizador de páginas para ver páginas individuales de archivos de varias páginas.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 1%

---

# Administrar recursos compuestos con subrecursos {#managing-compound-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets puede identificar si un archivo cargado contiene referencias a recursos que ya existen en el repositorio. Esta función solo está disponible para formatos de archivo compatibles. Si el recurso cargado contiene referencias a [!DNL Experience Manager] , se crea un vínculo bidireccional entre los recursos cargados y referenciados.

Además de eliminar la redundancia, haga referencia a [!DNL Experience Manager] en las aplicaciones de Adobe Creative Cloud, mejora la colaboración y la eficacia y productividad de los usuarios.

[!DNL Experience Manager] Recursos compatibles **referencia bidireccional**. Puede encontrar los recursos a los que se hace referencia en la página de detalles del recurso del archivo cargado. Además, puede ver los archivos de referencia para [!DNL Experience Manager] recursos en la página de detalles del recurso del recurso al que se hace referencia.

Las referencias se resuelven en función de la ruta, el ID del documento y el ID de instancia de los recursos a los que se hace referencia.

## Adobe Illustrator: Agregar recursos como referencias {#refai}

Puede hacer referencia a [!DNL Experience Manager] recursos de un archivo Adobe Illustrator.

1. Uso [[!DNL Experience Manager] aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=es), montaje [!DNL Experience Manager] Repositorio de recursos como una unidad en el equipo local. Dentro de la unidad montada, vaya a la ubicación del recurso al que desea hacer referencia.
1. Arrastre el recurso desde la unidad montada hasta el archivo Illustrator.
1. Guarde el archivo Illustrator en la unidad montada o [cargar](managing-assets-touch-ui.md#uploading-assets) a [!DNL Experience Manager] repositorio.
1. Una vez finalizado el flujo de trabajo, vaya a la página de detalles del recurso para el recurso. Las referencias a [!DNL Experience Manager] los recursos se enumeran en **[!UICONTROL Dependencias]** en el **[!UICONTROL Referencias]** para abrir el Navegador.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Los recursos a los que se hace referencia que aparecen en **[!UICONTROL Dependencias]** también se puede hacer referencia a archivos que no sean el actual. Para ver una lista de archivos de referencia para un recurso, haga clic en el recurso en la parte inferior **[!UICONTROL Dependencias]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Haga clic en el **[!UICONTROL Ver propiedades]** de la barra de herramientas. En la página de propiedades, la lista de archivos que hacen referencia al recurso actual aparece en la sección **[!UICONTROL Referencias]** en la columna **[!UICONTROL Básico]** pestaña .

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: Agregar recursos como referencias {#add-aem-assets-as-references-in-adobe-indesign}

Para hacer referencia a [!DNL Experience Manager] activos desde un archivo de InDesign, arrastre [!DNL Experience Manager] recursos al archivo de InDesign o exportar el archivo de InDesign como archivo ZIP.

Los recursos a los que se hace referencia ya existen en [!DNL Experience Manager] Recursos. Puede extraer subrecursos mediante [configurar servidor de InDesign](indesign.md). Los recursos incrustados en un archivo de InDesign se extraen como subrecursos.

>[!NOTE]
>
>Si el servidor de InDesign es proxy, la vista previa de los archivos de InDesign se incrusta en sus metadatos XMP. En este caso, la extracción de miniaturas no es explícitamente necesaria. Sin embargo, si el servidor de InDesign no se procesa como proxy, las miniaturas deben extraerse explícitamente para los archivos de InDesign.

Cuando se carga un archivo INDD, las referencias se recuperan consultando los recursos que tienen `xmpMM:InstanceID` y `xmpMM:DocumentID` en el repositorio.

### Crear referencias arrastrando recursos {#create-references-by-dragging-aem-assets}

Este procedimiento es similar a [Añadir recursos como referencias en Adobe Illustrator](#refai).

### Crear referencias a recursos exportando un archivo ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Siga los pasos indicados en [Creación de modelos de flujo de trabajo](/help/sites-developing/workflows-models.md) para crear un nuevo flujo de trabajo.
1. Utilice la variable [Función de paquete de Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) para exportar el documento. Adobe InDesign puede exportar un documento y los recursos vinculados como un paquete. En este caso, la carpeta exportada contiene un `Links` carpeta que contiene subrecursos en el archivo de InDesign. La variable `Links` está presente en la misma carpeta que el archivo INDD.
1. Cree un archivo ZIP y cárguelo en el [!DNL Experience Manager] repositorio.
1. Inicie el flujo de trabajo de Unarchiver.
1. Cuando se completa el flujo de trabajo, se hace referencia automáticamente a las referencias de la carpeta Links como subactivos. Para ver una lista de los recursos referidos, vaya a la página de detalles del recurso de InDesign y cierre la [Carril](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: Agregar recursos como referencias {#refps}

1. Uso de un cliente WebDav, montaje [!DNL Experience Manager] Recursos como unidad.
1. Para crear referencias a [!DNL Experience Manager] en un archivo Photoshop, navegue hasta los recursos correspondientes de la unidad montada mediante la función Colocar vinculada en Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Guarde en el archivo Photoshop en la unidad montada o [cargar](managing-assets-touch-ui.md#uploading-assets) a [!DNL Experience Manager] repositorio.
1. Una vez finalizado el flujo de trabajo, las referencias a [!DNL Experience Manager] los recursos se muestran en la página de detalles de recursos.

   Para ver los recursos a los que se hace referencia, cierre la [Carril](/help/sites-authoring/basic-handling.md#rail-selector) en la página de detalles del recurso.

1. Los recursos a los que se hace referencia también contienen la lista de recursos desde los que se hace referencia. Para ver una lista de los recursos a los que se hace referencia, vaya a la página de detalles del recurso y cierre la [carril](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>También se puede hacer referencia a los recursos incluidos en los recursos compuestos en función de su ID de documento y su ID de instancia. Esta funcionalidad solo está disponible con las versiones Adobe Illustrator y Adobe Photoshop. Para otros, la referencia se realiza sobre la base de la ruta relativa de los recursos vinculados en el activo compuesto principal, como se hace en versiones anteriores de AEM.

## Crear subrecursos {#generate-subassets}

Para los recursos compatibles con formatos de varias páginas: archivos de PDF, archivos de IA, archivos de Microsoft PowerPoint y Apple Keynote y archivos de Adobe InDesign, [!DNL Experience Manager] puede generar subrecursos que se correspondan con cada página individual del recurso original. Estos subrecursos están vinculados al *parent* y facilitar la vista de varias páginas. Para todos los demás fines, los subactivos se tratan como activos normales en AEM.

La generación de subconjuntos está deshabilitada de forma predeterminada. Para habilitar la generación de subrecursos, siga estos pasos:

1. Inicie sesión en Experience Manager como administrador. Acceso **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. Select **[!UICONTROL Recurso de actualización DAM]** flujo de trabajo y haga clic en **[!UICONTROL Editar]**.
1. Haga clic en **[!UICONTROL Alternar panel lateral]** y busque la variable **[!UICONTROL Crear subrecurso]** paso a paso. Añada el paso al flujo de trabajo. Haga clic en **[!UICONTROL Sincronizar]**.

Para generar los subrecursos, realice una de las siguientes acciones:

* Nuevos recursos: La variable [!UICONTROL Recursos de actualización DAM] el flujo de trabajo se ejecuta en cualquier recurso nuevo que se cargue en AEM. Los subrecursos se generan automáticamente para los nuevos recursos de varias páginas.
* Recursos existentes de varias páginas: Ejecute manualmente el [!UICONTROL Recursos de actualización DAM] flujo de trabajo siguiendo cualquiera de los pasos:

   * Seleccione un recurso y haga clic en [!UICONTROL Cronología] para abrir el panel izquierdo. Alternativamente, utilice la combinación de teclas `alt + 3`. Haga clic en [!UICONTROL Iniciar flujo de trabajo], seleccione [!UICONTROL Recurso de actualización DAM], haga clic en [!UICONTROL Inicio]y haga clic en [!UICONTROL Continuar].
   * Seleccione un recurso y haga clic en [!UICONTROL Crear > Flujo de trabajo] en la barra de herramientas. En el cuadro de diálogo emergente, seleccione [!UICONTROL Recurso de actualización DAM] flujo de trabajo, haga clic en [!UICONTROL Inicio]y haga clic en [!UICONTROL Continuar].

Específicamente para documentos de Microsoft Word, ejecute el **[!UICONTROL Documentos de Word de análisis DAM]** flujo de trabajo. Genera un `cq:Page` del contenido del documento de Microsoft Word. Se hace referencia a las imágenes extraídas del documento desde el `cq:Page` componente. Estas imágenes se extraen incluso si la generación de subrecursos está deshabilitada.

## Ver subrecursos {#viewing-subassets}

Los subrecursos solo se muestran si se generan los subrecursos y están disponibles para el recurso de varias páginas seleccionado. Para ver los subrecursos generados, abra el recurso de varias páginas. En el área superior izquierda de la página, haga clic en ![Icono de raíl izquierdo](assets/do-not-localize/aem_leftrail_contentonly.png) y haga clic en **[!UICONTROL Subrecursos]** de la lista. Al seleccionar **[!UICONTROL Subrecursos]** de la lista. Alternativamente, utilice la combinación de teclas `alt + 5`.

![Ver subrecursos de un recurso de varias páginas](assets/view_subassets_simulation.gif)

## Ver páginas de un archivo de varias páginas {#view-pages-of-a-multi-page-file}

Puede ver un archivo de varias páginas, como PDF, INDD, PPT, PPTX y AI, mediante la función Visualizador de páginas de [!DNL Experience Manager] Recursos. Abra un recurso de varias páginas y haga clic en **[!UICONTROL Ver páginas]** en la esquina superior izquierda de la página. El Visor de páginas que se abre muestra las páginas del recurso y los controles para examinar y ampliar cada página.

![Ver y ver páginas de un recurso de varias páginas](assets/view_multipage_asset_fmr.gif)

Para el InDesign, puede extraer páginas mediante el servidor de InDesign. Si las vistas previas de las páginas se guardan durante la creación del archivo de InDesign, no es necesario el InDesign Server para la extracción de páginas.

Las siguientes opciones están disponibles en la barra de herramientas, en el carril izquierdo y en los controles Visualizador de páginas :

* **[!UICONTROL Acciones de escritorio]** para abrir o mostrar un subrecurso específico mediante [!DNL Experience Manager] aplicación de escritorio. Consulte cómo [configurar acciones de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) si está utilizando [!DNL Experience Manager] aplicación de escritorio.

* **[!UICONTROL Propiedades]** abre el [!UICONTROL Propiedades] del subrecurso específico.

* **[!UICONTROL Anotar]** permite anotar el subrecurso específico. Las anotaciones que utilice en subrecursos independientes se recopilan y se muestran juntas cuando se abre para su visualización el recurso principal.

* **[!UICONTROL Información general de página]** muestra todos los subrecursos simultáneamente.

* **[!UICONTROL Cronología]** del carril izquierdo después de hacer clic en ![Icono de raíl izquierdo](assets/do-not-localize/aem_leftrail_contentonly.png) muestra el flujo de actividad del archivo.

## Prácticas recomendadas y limitación {#best-practice-limitation-tips}

* La generación de subconjuntos puede requerir muchos recursos en cualquier implementación de Experience Manager. Si está generando subrecursos cuando se cargan recursos complejos, agregue el paso en el flujo de trabajo de recursos de actualización de DAM . Si está generando subrecursos bajo demanda, cree un flujo de trabajo independiente para generar subrecursos. Un flujo de trabajo dedicado le permite omitir los demás pasos del flujo de trabajo de recursos de actualización de DAM y guardar recursos de computación.

>[!MORELIKETHIS]
>
>* [Uso de la aplicación de escritorio de Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

