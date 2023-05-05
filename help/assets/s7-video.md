---
title: Vídeo
description: Obtenga información sobre la administración centralizada de recursos de vídeo, donde puede cargar vídeos para Experience Manager Assets para la codificación automática en Dynamic Media Classic. También puede acceder a los vídeos de Dynamic Media Classic directamente desde Experience Manager Assets. La integración de vídeo de Dynamic Media Classic amplía el alcance del vídeo optimizado a todas las pantallas con detección automática de dispositivos y ancho de banda automático.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 1%

---

# Vídeo {#video}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los recursos permiten la administración centralizada de recursos de vídeo, donde puede cargar vídeos directamente en Assets para la codificación automática en Dynamic Media Classic. También puede acceder a los vídeos de Dynamic Media Classic directamente desde Assets para la creación de páginas.

La integración de vídeo de Dynamic Media Classic amplía el alcance del vídeo optimizado a todas las pantallas (detección automática de dispositivos y ancho de banda).

La variable **[!UICONTROL Vídeo de Scene7]** realiza automáticamente la detección de dispositivos y ancho de banda para reproducir el formato y la calidad de vídeo correctos en equipos de escritorio, tabletas y dispositivos móviles.

Puede incluir conjuntos de vídeos adaptables en lugar de solo recursos de vídeo únicos. Un conjunto de vídeos adaptables es un contenedor para todas las representaciones de vídeo necesarias para reproducir vídeo sin problemas en varias pantallas. Un conjunto de vídeos adaptables agrupa versiones del mismo vídeo codificadas con diferentes velocidades de bits y formatos. Por ejemplo, 400 kbps, 800 kbps y 1000 kbps. Se utiliza un conjunto de vídeos adaptables, junto con el componente de vídeo S7, para el flujo de vídeo adaptable en varios tipos de pantalla. Por ejemplo, dispositivos móviles de escritorio, iOS, Android, BlackBerry y Windows.

Consulte [Documentación de Dynamic Media Classic sobre conjuntos de vídeos adaptables para obtener más información](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## Acerca de FFMPEG y Dynamic Media Classic {#about-ffmpeg-and-scene}

El proceso de codificación de vídeo predeterminado se basa en el uso de la integración basada en FFMPEG con perfiles de vídeo. Por lo tanto, el flujo de trabajo de ingesta de DAM incorporado contiene los dos pasos siguientes de flujo de trabajo basados en FFMP:

* Miniaturas de FFMPEG
* Codificación FFMPEG

Al habilitar y configurar la integración de Dynamic Media Classic, no se eliminan ni desactivan automáticamente estos dos pasos de flujo de trabajo del flujo de trabajo de ingesta de DAM integrado. Si ya utiliza codificación de vídeo basada en FFMPEG en el Experience Manager, es probable que tenga FFMPEG instalado en los entornos de creación. En este caso, un nuevo vídeo ingestado con DAM se codificaría dos veces: una desde el codificador FFMPEG y otra desde la integración con Dynamic Media Classic.

Si tiene instalada la codificación de vídeo basada en FFMPEG en AEM y FFMPEG, puede eliminar los dos flujos de trabajo FFMPEG de los flujos de trabajo de ingesta de DAM.

## Formatos admitidos {#supported-formats}

El componente Vídeo de Scene7 admite los siguientes formatos:

* F4V H.264
* MP4 H.264

## Decidir dónde cargar el vídeo {#deciding-where-to-upload-your-video}

Decidir dónde cargar los recursos de vídeo depende de lo siguiente:

* ¿Necesita un flujo de trabajo para el recurso de vídeo?
* ¿Necesita control de versiones para el recurso de vídeo?

Si la respuesta es &quot;sí&quot; a una o ambas preguntas, cargue el vídeo directamente en DAM de Adobe. Si la respuesta a ambas preguntas es &quot;no&quot;, cargue el vídeo directamente en Dynamic Media Classic. El flujo de trabajo de cada escenario se describe en las secciones siguientes.

### Si está cargando el vídeo directamente en Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Si necesita un flujo de trabajo o crear versiones de los recursos, primero cargue en Adobe DAM . El siguiente es el flujo de trabajo recomendado:

1. Cargue el recurso de vídeo en DAM de Adobe y codifique y publique automáticamente en Dynamic Media Classic.
1. En Experience Manager, acceda a los recursos de vídeo de WCM en la **[!UICONTROL Películas]** del Buscador de contenido.
1. Autor con **[!UICONTROL Vídeo de Scene7]** o **[!UICONTROL Vídeo base]** componente.

### Si está cargando el vídeo en Scene7 {#if-you-are-uploading-your-video-to-scene}

Si no necesita un flujo de trabajo o crear versiones de los recursos, cárguelos a Scene7. El siguiente es el flujo de trabajo recomendado:

1. En Dynamic Media Classic, [configurar una carga y codificación de FTP programadas en Scene7 (sistema automatizado)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. En Experience Manager, acceda a los recursos de vídeo de WCM en la **[!UICONTROL Scene7]** del Buscador de contenido.
1. Autor con el **[!UICONTROL Vídeo de Scene7]** componente.

## Configuración de la integración con Scene7 Video {#configuring-integration-with-scene-video}

Para configurar ajustes preestablecidos universales:

1. En **[!UICONTROL Cloud Services]**, vaya a su **[!UICONTROL Scene7]** configuración y haga clic en **[!UICONTROL Editar]**.
1. Seleccione el **[!UICONTROL Vídeo]** pestaña .

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >La variable **[!UICONTROL Vídeo]** no aparece si la página no tiene una configuración de nube.

1. Seleccione el perfil de codificación de vídeo adaptable, un perfil de codificación de vídeo único incorporado o un perfil de codificación de vídeo personalizado.

   >[!NOTE]
   >
   >Para obtener más información sobre el significado de los ajustes preestablecidos de vídeo, consulte la [Documentación de Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe recomienda seleccionar ambos conjuntos de vídeos adaptables al configurar los ajustes preestablecidos universales o seleccionar la opción **[!UICONTROL Codificación de vídeo adaptable]** .

1. Los perfiles de codificación seleccionados se aplican automáticamente a todos los vídeos cargados en la carpeta de destino de CQ DAM configurada para esta configuración de nube de Scene7. Puede configurar varias configuraciones de nube de Scene7 con diferentes carpetas de destino para aplicar distintos perfiles de codificación según sea necesario.

## Actualización de ajustes preestablecidos de visor y codificación {#updating-viewer-and-encoding-presets}

Es necesario actualizar los ajustes preestablecidos de visor y codificación para vídeo en Experience Manager si los ajustes preestablecidos se actualizaron en Scene7. En estos casos, vaya a la configuración de Scene7 en la configuración de nube y haga clic en **[!UICONTROL Actualizar los ajustes preestablecidos de visor y codificación]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Carga del vídeo maestro en Scene7 desde Adobe DAM {#uploading-your-master-video}

1. Vaya a la carpeta de destino de CQ DAM donde ha configurado la configuración de nube con perfiles de codificación de Scene7.
1. Haga clic en **[!UICONTROL Cargar]** para cargar el vídeo maestro. La carga y codificación de vídeo se completan una vez finalizado el flujo de trabajo de recursos de actualización de DAM y **[!UICONTROL Publicar en Scene7]** tiene una marca de verificación.

   >[!NOTE]
   >
   >Las miniaturas de vídeo tardan algún tiempo en generarse.

   Arrastrar el vídeo maestro de DAM a los accesos al componente de vídeo *all* las representaciones proxy codificadas de Scene7 para su entrega.

## Componente de vídeo base frente a componente de vídeo de Scene7 {#foundation-video-component-versus-scene-video-component}

Al utilizar Experience Manager, tiene acceso al componente Vídeo disponible en Sitios y al componente de vídeo de Scene7. Estos componentes no son intercambiables.

El componente de vídeo de Scene7 solo funciona para vídeos de Scene7. El componente base funciona con vídeos almacenados desde el Experience Manager (mediante ffmpeg) y vídeos de Scene7.

La siguiente matriz explica cuándo utilizar cada componente:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>De serie, el componente de vídeo S7 utiliza el perfil de vídeo universal. Sin embargo, puede obtener el reproductor de vídeo basado en HTML5 en Experience Manager. Copie el código incrustado del reproductor de vídeo HTML5 listo para usar y colóquelo en la página Experience Manager.

## Componente de vídeo de Experience Manager {#aem-video-component}

Incluso si se recomienda utilizar el componente de vídeo de Scene7 para ver vídeos de Scene7, utilice vídeos de Scene7 con el componente de vídeo base para que sea más completo.

### Comparación de vídeo de Experience Manager y vídeo de Scene7 {#aem-video-and-scene-video-comparison}

La siguiente tabla ofrece una comparación de alto nivel de las funciones admitidas entre el componente de vídeo base de Experience Manager y el componente de vídeo de Scene7:

|  | Vídeo de base de Experience Manager | Vídeo de Scene7 |
|---|---|---|
| Enfoque | primer enfoque de HTML5. El Flash solo se utiliza para la reserva que no es de HTML5. | Flash en la mayoría de los escritorios. HTML5 se utiliza para móviles y tabletas. |
| Entrega | Progresivo | Transmisión adaptable |
| Seguimiento | Sí | Sí |
| Extensibilidad | Sí | Sí (con [Documentación de la API del SDK del visor HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Vídeo móvil | Sí | Sí |

### Configuración {#setting-up}

#### Creación de perfiles de vídeo {#creating-video-profiles}

Las distintas codificaciones de vídeo se crean según los ajustes preestablecidos de codificación de Scene7 seleccionados en la configuración de nube de Scene7. Para que el componente Vídeo base los utilice, se debe crear un perfil de vídeo para cada ajuste preestablecido de codificación de Scene7 seleccionado. Este método permite que el componente de vídeo seleccione las representaciones de DAM según corresponda.

>[!NOTE]
>
>Los nuevos perfiles de vídeo y los cambios que se realicen en ellos deben activarse para poder publicarse.

1. En el Experience Manager, pulse **[!UICONTROL Herramientas] > [!UICONTROL Consola de configuración]**.
1. En el **[!UICONTROL Consola de configuración]** vaya a **[!UICONTROL Herramientas > DAM > Perfiles de vídeo]** en el árbol de navegación.
1. Crear un perfil de vídeo de Scene7. En el **[!UICONTROL Nuevo...]** lista desplegable, seleccione **[!UICONTROL Crear página]** y, a continuación, seleccione la plantilla Perfil de vídeo de Scene7 . Asigne un nombre a la nueva página de perfil de vídeo y haga clic en **[!UICONTROL Crear]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Edite el nuevo perfil de vídeo. Seleccione primero la configuración de nube. A continuación, seleccione el mismo ajuste preestablecido de codificación que el seleccionado en la configuración de nube.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Propiedad | Descripción |
   |---|---|
   | Configuración de nube de Scene7 | La configuración de nube que se utilizará para los ajustes preestablecidos de codificación. |
   | Ajuste preestablecido de codificación de Scene7 | El ajuste preestablecido de codificación con el que asignar este perfil de vídeo. |
   | Tipo de vídeo HTML5 | Esta propiedad permite establecer el valor de la propiedad type del elemento de origen de vídeo HTML5. Esta información no se proporciona en los ajustes preestablecidos de codificación de S7, sino que es necesaria para procesar correctamente los vídeos mediante el elemento de vídeo HTML5. Se proporciona una lista para formatos comunes, pero se puede sobrescribir para otros formatos. |

   Repita este paso para todos los ajustes preestablecidos de codificación seleccionados en la configuración de nube que desee utilizar en el componente de vídeo.

#### Configuración del diseño {#configuring-design}

La variable **[!UICONTROL Vídeo base]** debe saber qué perfiles de vídeo utilizar para crear la lista de fuentes de vídeo. Abra el cuadro de diálogo de diseño de componentes de vídeo y configure el diseño de componentes para utilizar los nuevos perfiles de vídeo.

>[!NOTE]
>
>Si usa la variable **[!UICONTROL Vídeo base]** en una página móvil, repita estos pasos en el diseño de la página móvil.

>[!NOTE]
>
>Los cambios realizados en el diseño requieren la activación del diseño para que tengan efecto en la publicación.

1. Abra el **[!UICONTROL Vídeo base]** cuadro de diálogo de diseño del componente y cambie a **[!UICONTROL Perfiles]** pestaña . A continuación, elimine los perfiles predeterminados y añada los nuevos perfiles de vídeo de S7. El orden de la lista de perfiles en el cuadro de diálogo de diseño define el orden del elemento de orígenes de vídeo al realizar la representación.
1. En los navegadores que no admiten HTML5, el componente de vídeo permite configurar una reserva de Flash. Abra el cuadro de diálogo de diseño de componentes de vídeo y cambie a **[!UICONTROL Flash]** pestaña . Configure los ajustes del Flash Player y asigne un perfil de reserva para el Flash Player.

#### Lista de comprobación {#checklist}

1. Crear una configuración de nube de S7. Asegúrese de que los ajustes preestablecidos de codificación de vídeo estén configurados y de que el importador se esté ejecutando.
1. Cree un perfil de vídeo S7 para cada ajuste preestablecido de codificación de vídeo seleccionado en la configuración de nube.
1. Los perfiles de vídeo deben activarse.
1. Configure el diseño de la variable **[!UICONTROL Vídeo base]** en la página.
1. Active el diseño una vez que haya terminado con los cambios de diseño.
