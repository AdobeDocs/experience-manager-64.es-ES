---
title: Creación de proyectos de traducción
description: Aprenda a crear proyectos de traducción en AEM.
contentOwner: AG
feature: Translation
role: Architect,Admin
exl-id: 1b931fef-eed0-4758-993d-cdf8d478fb6f
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '1939'
ht-degree: 23%

---

# Creación de proyectos de traducción {#creating-translation-projects}

Para crear una copia de idioma, asigne un déclencheur a uno de los siguientes flujos de trabajo de copia de idioma disponibles en el carril Referencias de la interfaz de usuario de Assets:

**Crear y traducir**

En este flujo de trabajo, los recursos que se van a traducir se copian en la raíz del idioma al que se desea traducir. Además, según las opciones que elija, se crea un proyecto de traducción para los recursos en la consola Proyectos . Según la configuración, el proyecto de traducción se puede iniciar manualmente o se le puede permitir que se ejecute automáticamente en cuanto se cree el proyecto de traducción.

**Actualizar copias de idioma**

Ejecute este flujo de trabajo para traducir un grupo adicional de recursos e incluirlos en una copia de idioma para una configuración regional concreta. En este caso, los recursos traducidos se añaden a la carpeta de destino que ya contiene recursos traducidos anteriormente.

>[!NOTE]
>
>Los binarios de recursos solo se traducen si el proveedor de servicios de traducción admite la traducción de binarios.

>[!NOTE]
>
>Si inicia un flujo de trabajo de traducción para recursos complejos, como archivos PDF y archivos InDesign, sus subrecursos o representaciones (si hay) no se envían para su traducción.

## Creación y traducción de flujos de trabajo {#create-and-translate-workflow}

El flujo de trabajo Crear y traducir se utiliza para generar textos de idiomas para un idioma en particular por primera vez. El flujo de trabajo ofrece las siguientes opciones:

* Crear solo una estructura
* Crear un nuevo proyecto de traducción
* Añadir a un proyecto de traducción existente

### Crear solo una estructura {#create-structure-only}

Utilice la opción **Crear solo estructura** para diseñar una jerarquía de carpetas de destino dentro de la raíz del idioma de destino para que coincida con la jerarquía de la carpeta de origen dentro de la raíz del idioma de origen. En este caso, los recursos de origen se copian en la carpeta de destino. Sin embargo, no se genera ningún proyecto de traducción.

1. En la interfaz de usuario de Assets, seleccione la carpeta de origen para la que desea crear una estructura en la raíz del idioma de destino.
1. Abra el panel **[!UICONTROL Referencias]** y pulse o haga clic en **[!UICONTROL Textos en idiomas]** en **[!UICONTROL Textos]**.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Pulse o haga clic en **[!UICONTROL Crear y traducir]** en la parte inferior.

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. En la lista **[!UICONTROL Idiomas de destino]**, seleccione el idioma para el que desea crear una estructura de carpetas.

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. En la lista **[!UICONTROL Proyecto]**, seleccione **[!UICONTROL Crear estructura únicamente]**.

   ![imagen_1-60](assets/chlimage_1-60.png)

1. Pulse o haga clic en **[!UICONTROL Crear]**. La nueva estructura para el idioma de destino se muestra en **[!UICONTROL Textos en idiomas]**.

   ![climage_1-61](assets/chlimage_1-61.png)

1. Pulse o haga clic en la estructura de la lista y, a continuación, pulse o haga clic en **[!UICONTROL Mostrar en recursos]** para desplazarse a la estructura de carpetas dentro del idioma de destino.

   ![imagen_1-62](assets/chlimage_1-62.png)

### Crear un nuevo proyecto de traducción {#create-a-new-translation-project}

Si utiliza esta opción, los recursos que desea traducir se copian en la raíz del idioma al que desea traducir. Según las opciones que elija, se crea un proyecto de traducción para los recursos en la consola Proyectos . Según la configuración, el proyecto de traducción se puede iniciar manualmente o se ejecuta automáticamente en cuanto se crea el proyecto de traducción.

1. En la interfaz de usuario de Assets, seleccione la carpeta de origen para la que desea crear una copia de idioma.
1. Abra el panel **[!UICONTROL Referencias]** y pulse o haga clic en **[!UICONTROL Textos en idiomas]** en **[!UICONTROL Textos]**.

   ![imagen_1-63](assets/chlimage_1-63.png)

1. Pulse o haga clic en **[!UICONTROL Crear y traducir]** en la parte inferior.

   ![imagen_1-64](assets/chlimage_1-64.png)

1. En la lista **[!UICONTROL Idiomas de destino]**, seleccione los idiomas para los que desea crear una estructura de carpetas.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. En la lista **[!UICONTROL Proyecto]**, seleccione **[!UICONTROL Crear un nuevo proyecto de traducción]**.

   ![imagen_1-66](assets/chlimage_1-66.png)

1. En el campo **[!UICONTROL Título del proyecto]**, introduzca un título.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Toque o haga clic en **[!UICONTROL Crear]**. Los recursos de la carpeta de origen se copian en las carpetas de destino para las configuraciones regionales seleccionadas en el paso 4.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Para desplazarse a la carpeta, seleccione la copia de idioma y haga clic en **[!UICONTROL Mostrar en Assets]**.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Vaya a la consola Proyectos . La carpeta de traducción se copia en la consola Proyectos .

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Abra la carpeta para ver el proyecto de traducción.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Toque o haga clic en el proyecto para abrir la página de detalles.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Para ver el estado del trabajo de traducción, haga clic en los puntos suspensivos en la parte inferior del mosaico **[!UICONTROL Trabajo de traducción]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   Para obtener más información sobre los estados del trabajo, consulte [Monitorización del estado de un trabajo de traducción](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Vaya a la interfaz de usuario de Assets y abra la página Propiedades de cada uno de los recursos traducidos para ver los metadatos traducidos.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   >[!NOTE]
   >
   >Esta función está disponible tanto para recursos como para carpetas. Cuando se selecciona un recurso en lugar de una carpeta, se copia toda la jerarquía de carpetas hasta la raíz del idioma para crear una copia de idioma para el recurso.

### Añadir a un proyecto de traducción existente {#add-to-existing-translation-project}

Si utiliza esta opción, el flujo de trabajo de traducción se ejecuta para los recursos que agregue a la carpeta de origen después de ejecutar un flujo de trabajo de traducción anterior. Solo los recursos recién añadidos se copian en la carpeta de destino que contiene recursos traducidos anteriormente. En este caso no se crea ningún proyecto de traducción nuevo.

1. En la interfaz de usuario de Assets, vaya a la carpeta de origen que contiene recursos sin traducir.
1. Seleccione un recurso que desee traducir y abra el **[!UICONTROL panel Referencias]**. La sección **[!UICONTROL Textos en idiomas]** muestra el número de traducciones disponibles en ese momento.
1. Pulse o haga clic en **[!UICONTROL Textos en idiomas]** en **[!UICONTROL Textos]**. Se muestra una lista de las traducciones disponibles.
1. Pulse o haga clic en **[!UICONTROL Crear y traducir]** en la parte inferior.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. En la lista **[!UICONTROL Idiomas de destino]**, seleccione los idiomas para los que desea crear una estructura de carpetas.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. En la lista **[!UICONTROL Proyecto]**, seleccione **[!UICONTROL Agregar a proyecto de traducción]** existente para ejecutar el flujo de trabajo de traducción en la carpeta.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Si elige la opción **[!UICONTROL Add to existing translation project]** , el proyecto de traducción se agregará a un proyecto preexistente solo si la configuración del proyecto coincide exactamente con la configuración del proyecto preexistente. De lo contrario, se crea un nuevo proyecto.

1. En la lista **[!UICONTROL Existing translation project]**, seleccione un proyecto para agregar el recurso para su traducción.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Pulse o haga clic en **[!UICONTROL Crear]**. Los recursos que se van a traducir se agregan a la carpeta de destino. La carpeta actualizada se muestra en la sección **[!UICONTROL Textos en idiomas]**.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Vaya a la consola Proyectos y abra el proyecto de traducción existente que ha agregado a.
1. Toque o haga clic en el proyecto de traducción para ver la página de detalles del proyecto.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Pulse o haga clic en los puntos suspensivos en la parte inferior del mosaico **Trabajo de traducción** para ver los recursos en el flujo de trabajo de traducción. En la lista de trabajos de traducción también se muestran las entradas para los metadatos y las etiquetas de los recursos. Estas entradas indican que los metadatos y las etiquetas de los recursos también se traducen.

   >[!NOTE]
   >
   >Si elimina la entrada de etiquetas o metadatos, no se traducirá ninguna etiqueta ni metadatos para ninguno de los recursos.

   >[!NOTE]
   >
   >Si utiliza la traducción automática, los binarios de recursos no se traducen.

   >[!NOTE]
   >
   >Si el recurso que agrega al trabajo de traducción incluye subrecursos, selecciónelos y elimínelos para que la traducción continúe sin problemas.

1. Para iniciar la traducción de los recursos, toque o haga clic en la flecha del mosaico **[!UICONTROL Trabajo de traducción]** y seleccione **[!UICONTROL Inicio]** en la lista.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   Un mensaje notifica el inicio del trabajo de traducción.

   ![chlimage_1-82](assets/chlimage_1-82.png)

1. Para ver el estado del trabajo de traducción, toque o haga clic en los puntos suspensivos en la parte inferior del mosaico **[!UICONTROL Trabajo de traducción]**.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   Para obtener más información, consulte [Monitorización del estado de un trabajo de traducción](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Una vez finalizada la traducción, el estado cambia a Listo para revisión. Vaya a la interfaz de usuario de Assets y abra la página Propiedades de cada uno de los recursos traducidos para ver los metadatos traducidos.

## Actualizar copias de idioma {#update-language-copies}

Ejecute este flujo de trabajo para traducir cualquier conjunto adicional de recursos e incluirlo en una copia de idioma para una configuración regional concreta. En este caso, los recursos traducidos se añaden a la carpeta de destino que ya contiene recursos traducidos anteriormente. Según la elección de opciones, se crea un proyecto de traducción o se actualiza un proyecto de traducción existente para los nuevos recursos. El flujo de trabajo Update language Copies incluye las siguientes opciones:

* Crear un nuevo proyecto de traducción
* Añadir a un proyecto de traducción existente

### Crear un nuevo proyecto de traducción {#create-a-new-translation-project-1}

Si utiliza esta opción, se crea un proyecto de traducción para el conjunto de recursos para el que desea actualizar una copia de idioma.

1. En la interfaz de usuario de Assets, seleccione la carpeta de origen en la que añadió un recurso.
1. Abra el panel **[!UICONTROL Referencias]** y pulse o haga clic en **[!UICONTROL Textos en idiomas]**, situado en el apartado **[!UICONTROL Textos]** para mostrar la lista de textos en diferentes idiomas.
1. Seleccione la casilla de verificación antes de **[!UICONTROL Textos en idiomas]** y, a continuación, seleccione la carpeta de destino correspondiente a la configuración regional adecuada.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Toque o haga clic en **[!UICONTROL Actualizar copias de idioma]** en la parte inferior.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. En la lista **[!UICONTROL Proyecto]**, elija **[!UICONTROL Crear un nuevo proyecto de traducción]**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. En el campo **[!UICONTROL Título del proyecto]**, introduzca un título.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Pulse o haga clic en **[!UICONTROL Iniciar]**.
1. Vaya a la consola Proyectos . La carpeta de traducción se copia en la consola Proyectos .

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Abra la carpeta para ver el proyecto de traducción.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Toque o haga clic en el proyecto para abrir la página de detalles.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Para iniciar la traducción de los recursos, haga clic en la flecha del mosaico **[!UICONTROL Trabajo de traducción]** y seleccione **[!UICONTROL Inicio]** en la lista.

   ![imagen_1-91](assets/chlimage_1-91.png)

   Un mensaje notifica el inicio del trabajo de traducción.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Para ver el estado del trabajo de traducción, toque o haga clic en los puntos suspensivos en la parte inferior del mosaico **[!UICONTROL Trabajo de traducción]**.

   ![imagen_1-93](assets/chlimage_1-93.png)

   Para obtener más información sobre los estados del trabajo, consulte [Monitorización del estado de un trabajo de traducción](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Vaya a la interfaz de usuario de Assets y abra la página Propiedades de cada uno de los recursos traducidos para ver los metadatos traducidos.

### Añadir a un proyecto de traducción existente {#add-to-existing-translation-project-1}

Si utiliza esta opción, el conjunto de recursos se agregará a un proyecto de traducción existente para actualizar la copia de idioma para la configuración regional que elija.

1. En la interfaz de usuario de Assets, seleccione la carpeta de origen en la que ha añadido una carpeta de recursos.
1. Abra el **[!UICONTROL panel Referencias]** y pulse o haga clic en **[!UICONTROL Textos en idiomas]**, situado en el apartado **[!UICONTROL Textos]** para mostrar la lista de textos en diferentes idiomas.

   ![imagen_1-94](assets/chlimage_1-94.png)

1. Seleccione la casilla de verificación que se encuentra delante de **[!UICONTROL Textos en idiomas]**, de esta forma, selecciona los textos disponibles en diferentes idiomas. Anule la selección de otros textos excepto el texto (textos) en el idioma correspondiente a las configuraciones regionales a las que desea traducir.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Toque o haga clic en **[!UICONTROL Actualizar copias de idioma]** en la parte inferior.

   ![imagen_1-96](assets/chlimage_1-96.png)

1. En la lista **[!UICONTROL Proyecto]**, elija **[!UICONTROL Agregar al proyecto de traducción existente]**.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. En la lista **[!UICONTROL Existing translation project]**, seleccione un proyecto para agregar el recurso para su traducción.

   ![imagen_1-98](assets/chlimage_1-98.png)

1. Pulse o haga clic en **[!UICONTROL Iniciar]**.
1. Consulte los pasos 9-14 de [Agregar al proyecto de traducción existente](translation-projects.md#add-to-existing-translation-project) para completar el resto del procedimiento.

## Creación de copias de idioma temporales {#creating-temporary-language-copies}

Cuando se ejecuta un flujo de trabajo de traducción para actualizar una copia de idioma con versiones editadas de los recursos originales, la copia de idioma existente se conserva hasta que se aprueban los recursos traducidos. [!DNL Experience Manager] Assets almacena los recursos recién traducidos en una ubicación temporal y actualiza la copia de idioma existente después de aprobar explícitamente los recursos. Si rechaza los recursos, la copia de idioma permanece sin cambios.

1. Pulse o haga clic en la carpeta raíz de origen de **[!UICONTROL Textos en idiomas]** para la que ya ha creado un texto en un idioma y, a continuación, pulse o haga clic en **[!UICONTROL Mostrar en recursos]** para abrir la carpeta en Assets.[!DNL Experience Manager]

   ![imagen_1-99](assets/chlimage_1-99.png)

1. En la interfaz de usuario de Assets, seleccione un recurso que ya haya traducido y pulse o haga clic en el icono **[!UICONTROL Editar]** de la barra de herramientas para abrir el recurso en modo de edición.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Edite el recurso y, a continuación, guarde los cambios.
1. Realice los pasos 2-14 del procedimiento [Add to existing translation project](#add-to-existing-translation-project) para actualizar la copia de idioma.
1. Pulse o haga clic en los puntos suspensivos en la parte inferior del mosaico **[!UICONTROL Trabajo de traducción]**. Desde la lista de recursos de la página **[!UICONTROL Trabajo de traducción]**, puede ver claramente la ubicación temporal en la que se almacena la versión traducida del recurso.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Seleccione la casilla de verificación situada junto a **[!UICONTROL Title]**.
1. En la barra de herramientas, pulse o haga clic en **[!UICONTROL Aceptar traducción]** y, a continuación, pulse o haga clic en **[!UICONTROL Aceptar]** en el cuadro de diálogo para sobrescribir el recurso traducido en la carpeta de destino con la versión traducida del recurso editado.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   >[!NOTE]
   >
   >Para permitir que el flujo de trabajo de traducción actualice los recursos de destino, acepte el recurso y los metadatos.

   Pulse o haga clic en **[!UICONTROL Rechazar traducción]** para conservar la versión traducida originalmente del recurso en la raíz de configuración regional de destino y rechace la versión editada.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Vaya a la consola Recursos y abra la página Propiedades de cada uno de los recursos traducidos para ver los metadatos traducidos.

Para obtener sugerencias sobre la traducción eficaz de metadatos para recursos, consulte esta página archivada sobre [5 pasos para traducir metadatos de forma eficaz](https://web.archive.org/web/20181217033517/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).
