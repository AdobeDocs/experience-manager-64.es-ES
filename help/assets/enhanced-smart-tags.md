---
title: Etiquetas inteligentes mejoradas
description: Etiquetas inteligentes mejoradas
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Smart Tags,Search
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 15%

---

# Etiquetas inteligentes mejoradas {#enhanced-smart-tags}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Descripción general de las etiquetas inteligentes mejoradas {#overview-of-enhanced-smart-tags}

Las organizaciones que se ocupan de los recursos digitales utilizan cada vez más el vocabulario controlado por taxonomía en los metadatos de los recursos. Básicamente, incluye una lista de palabras clave que los empleados, socios y clientes suelen utilizar para referirse a recursos digitales de una clase en particular y buscar dichos recursos. El etiquetado de recursos con vocabulario controlado por taxonomía garantiza que se puedan identificar y recuperar fácilmente mediante búsquedas basadas en etiquetas.

En comparación con los vocabularios de lenguaje natural, etiquetar recursos digitales en función de la taxonomía empresarial ayuda a alinearlos con el negocio de una empresa y garantiza que los activos más relevantes aparezcan en las búsquedas.

Por ejemplo, un fabricante de coches puede etiquetar imágenes de coches con nombres de modelos, de modo que solo aparecen imágenes relevantes cuando se buscan imágenes de varios modelos para diseñar una campaña de promoción.

Para que el servicio de contenido inteligente aplique las etiquetas correctas, debe formarlo para que reconozca su taxonomía. Para formar el servicio, primero debe depurar un conjunto de recursos y etiquetas que describan mejor estos recursos. Aplique estas etiquetas en los recursos y ejecute un flujo de trabajo de formación para ayudar al servicio a aprender.

Una vez que una etiqueta está preparada y lista, el servicio ahora puede aplicar estas etiquetas en los recursos a través de un flujo de trabajo de etiquetado.

En segundo plano, el servicio de contenido inteligente utiliza el marco de IA de Adobe Sensei para entrenar su algoritmo de reconocimiento de imágenes en la estructura de etiquetas y la taxonomía empresarial. A continuación, esta inteligencia de contenido se utiliza para aplicar etiquetas relevantes en un conjunto diferente de recursos.

El servicio de contenido inteligente es un servicio en la nube alojado en [!DNL Adobe I/O]. Para utilizarlo en Adobe Experience Manager, el administrador del sistema debe integrar su [!DNL Experience Manager] instancia con [!DNL Adobe I/O].

En resumen, estos son los pasos principales para utilizar el servicio de contenido inteligente:

* Incorporación
* Revisión de recursos y etiquetas (definición de taxonomía)
* Formación del servicio de contenido inteligente
* Etiquetado automático

![diagrama de flujo](assets/flowchart.gif)

## Requisitos previos {#prerequisites}

Antes de utilizar el servicio de contenido inteligente, asegúrese de lo siguiente para crear una integración en [!DNL Adobe I/O]:

* Cuenta de Adobe ID que tiene privilegios de administrador para la organización.
* El servicio de contenido inteligente está habilitado para su organización.

## Incorporación {#onboarding}

El servicio de contenido inteligente está disponible para su compra como complemento de [!DNL Experience Manager] . Después de realizar la compra, se envía un correo electrónico al administrador de la organización con un vínculo a [!DNL Adobe I/O].

El administrador puede seguir el vínculo para integrar el servicio de contenido inteligente con [!DNL Experience Manager] . Para integrar el servicio con [!DNL Experience Manager] Recursos, consulte [Configuración de etiquetas inteligentes](config-smart-tagging.md).

El proceso de incorporación se completa cuando el administrador configura el servicio y añade usuarios en [!DNL Experience Manager] .

## Revisión de recursos y etiquetas {#reviewing-assets-and-tags}

Una vez que esté integrado, lo primero que desea hacer es identificar un conjunto de etiquetas que describan mejor estas imágenes en el contexto de su negocio.

A continuación, revise las imágenes para identificar un conjunto de imágenes que represente mejor su producto para un requisito comercial determinado. Asegúrese de que los recursos del conjunto depurado se ajustan a [Directrices de formación del servicio de contenido inteligente](smart-tags-training-guidelines.md).

Agregue los recursos a una carpeta y aplique las etiquetas a cada recurso desde la página de propiedades. A continuación, ejecute el flujo de trabajo de formación en esta carpeta. El conjunto depurado de recursos permite que el servicio de contenido inteligente imparta formación a más recursos mediante las definiciones de taxonomía.

>[!NOTE]
>
>1. La formación es un proceso irrevocable. Adobe recomienda revisar las etiquetas del conjunto depurado de recursos antes de entrenar el servicio de contenido inteligente en las etiquetas.
>1. Por favor, lea [Directrices de formación del servicio de contenido inteligente](smart-tags-training-guidelines.md) antes de iniciar la formación para cualquier etiqueta.
>1. Cuando entrena el servicio de contenido inteligente por primera vez, Adobe recomienda que lo entrene en al menos dos etiquetas diferentes.

>


## Formación del servicio de contenido inteligente {#training-the-smart-content-service}

Para que el servicio de contenido inteligente reconozca su taxonomía empresarial, ejecútelo en un conjunto de recursos que ya incluyen etiquetas que son relevantes para su negocio. Después de la formación, el servicio puede aplicar la misma taxonomía en un conjunto de activos similar.

Puede entrenar el servicio varias veces para mejorar su capacidad de aplicar etiquetas relevantes. Después de cada ciclo de formación, ejecute un flujo de trabajo de etiquetado y compruebe si los recursos están etiquetados correctamente.

Puede entrenar el servicio de contenido inteligente de forma periódica o según sus necesidades.

>[!NOTE]
>
>El flujo de trabajo de formación solo se ejecuta en carpetas.

### Formación periódica {#periodic-training}

Puede permitir que el servicio de contenido inteligente imparta formación periódicamente sobre los recursos y las etiquetas asociadas de una carpeta. Abra la página de propiedades de la carpeta de recursos y seleccione **[!UICONTROL Habilitar etiquetas inteligentes]** en el **[!UICONTROL Detalles]** y guarde los cambios.

![enable_smart_tags](assets/enable_smart_tags.png)

Una vez seleccionada esta opción para una carpeta, [!DNL Experience Manager] ejecuta un flujo de trabajo de formación automáticamente para formar el servicio de contenido inteligente en las carpetas y sus etiquetas. De forma predeterminada, el flujo de trabajo de formación se ejecuta de forma semanal a las 12:30 AM de los sábados.

### Capacitación a pedido {#on-demand-training}

Puede entrenar el servicio de contenido inteligente siempre que sea necesario desde la consola Flujo de trabajo.

1. Toque o haga clic en el botón [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. En la página **[!UICONTROL Modelos de flujo de trabajo]**, seleccione el flujo de trabajo de **[!UICONTROL formación de etiquetas inteligentes]** y, a continuación, pulse o haga clic en **[!UICONTROL Iniciar flujo de trabajo]** en la barra de herramientas.
1. En el **[!UICONTROL Ejecutar flujo de trabajo]** , vaya a la carpeta de carga útil que incluye los recursos etiquetados para entrenar el servicio.
1. Especifique un título para el flujo de trabajo y un comentario. A continuación, toque o haga clic en **[!UICONTROL Ejecutar]**. Los recursos y las etiquetas se envían para formación.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Una vez que los recursos de una carpeta se procesan para formación, solo los recursos modificados se procesan en ciclos de formación posteriores.

### Visualización de informes de formación {#viewing-training-reports}

Para comprobar si el servicio de contenido inteligente ha recibido formación sobre las etiquetas en el conjunto de recursos de formación, revise el informe del flujo de trabajo de formación desde la consola Informes .

1. Toque o haga clic en el botón [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas > Assets > Informes]**.
1. En la página **[!UICONTROL Informes de recursos]**, pulse o haga clic en **[!UICONTROL Crear]**.
1. Seleccione el informe **[!UICONTROL Formación sobre etiquetas inteligentes]** y, a continuación, pulse o haga clic en **[!UICONTROL Siguiente]** en la barra de herramientas.
1. Especifique un título y una descripción para el informe. En **[!UICONTROL Programar informe]**, deje seleccionada la opción **[!UICONTROL Ahora]**. Si desea programar el informe para más adelante, seleccione **[!UICONTROL Más adelante]** e indique una fecha y una hora. A continuación, pulse o haga clic en **[!UICONTROL Crear]** desde la barra de herramientas.
1. En la página **[!UICONTROL Informes de recursos]**, seleccione el informe que ha generado. Para ver el informe, pulse o haga clic en el icono **[!UICONTROL Ver]** de la barra de herramientas.
1. Revise los detalles del informe.

   El informe muestra el estado de la formación de las etiquetas que ha entrenado. El color verde de la columna **[!UICONTROL Estado de formación]** indica que el servicio de contenido inteligente ha recibido formación para la etiqueta. El color amarillo indica que el servicio no está completamente entrenado para una etiqueta en particular. En este caso, agregue más imágenes con la etiqueta en concreto y ejecute el flujo de trabajo de formación para que el servicio se imparta completamente en la etiqueta.

   Si no ve las etiquetas en este informe, ejecute de nuevo el flujo de trabajo de formación para estas etiquetas.

1. Para descargar el informe, selecciónelo en la lista y toque o haga clic en el botón **[!UICONTROL Descargar]** de la barra de herramientas. El informe se descarga como archivo de Excel.

## Etiquetado de recursos automáticamente {#tagging-assets-automatically}

Una vez que haya formado el servicio de contenido inteligente, puede almacenar en déclencheur el flujo de trabajo de etiquetado para aplicar automáticamente las etiquetas adecuadas en un conjunto diferente de recursos similares.

Puede ejecutar el flujo de trabajo de etiquetado periódicamente o siempre que sea necesario.

>[!NOTE]
>
>El flujo de trabajo de etiquetado se ejecuta tanto en los recursos como en las carpetas.

### Etiquetado periódico {#periodic-tagging}

Puede habilitar el servicio de contenido inteligente para que etiquete periódicamente los recursos de una carpeta. Abra la página de propiedades de la carpeta de recursos y seleccione **[!UICONTROL Habilitar etiquetas inteligentes]** en el **[!UICONTROL Detalles]** y guarde los cambios.

Una vez seleccionada esta opción para una carpeta, el servicio de contenido inteligente etiqueta automáticamente los recursos de la carpeta. De forma predeterminada, el flujo de trabajo de etiquetado se ejecuta todos los días a las 12:00.

### Etiquetado a petición {#on-demand-tagging}

Puede almacenar en déclencheur el flujo de trabajo de etiquetado desde lo siguiente para etiquetar los recursos al instante:

* Consola de flujo de trabajo
* Escala de cronología

>[!NOTE]
>
>Si ejecuta el flujo de trabajo de etiquetado desde la línea de tiempo, puede aplicar etiquetas en un máximo de 15 recursos a la vez.

#### Etiquetado de recursos desde la consola Flujo de trabajo {#tagging-assets-from-the-workflow-console}

1. Toque o haga clic en el botón [!DNL Experience Manager] y vaya a **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**.
1. En la página **[!UICONTROL Modelos de flujo de trabajo]**, seleccione el flujo de trabajo **[!UICONTROL Recursos de etiquetas inteligentes DAM]** y, a continuación, pulse o haga clic en **[!UICONTROL Iniciar flujo de trabajo]** en la barra de herramientas.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. En el **[!UICONTROL Ejecutar flujo de trabajo]** , vaya a la carpeta de carga útil que contiene los recursos en los que desea aplicar las etiquetas automáticamente.
1. Especifique un título para el flujo de trabajo y un comentario opcional. A continuación, toque o haga clic en **[!UICONTROL Ejecutar]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Vaya a la carpeta de recursos y revise las etiquetas para comprobar si el servicio de contenido inteligente ha etiquetado los recursos correctamente. Para obtener más información, consulte [Administración de etiquetas inteligentes](managing-smart-tags.md).

#### Etiquetado de recursos desde la línea de tiempo {#tagging-assets-from-the-timeline}

1. En la interfaz de usuario de Assets, seleccione la carpeta que contiene recursos o recursos específicos a los que desea aplicar etiquetas inteligentes.
1. Pulse o haga clic en el icono de navegación global y abra la línea de tiempo.
1. Toque o haga clic en la flecha situada en la parte inferior y, a continuación, toque o haga clic en **[!UICONTROL Iniciar flujo de trabajo]**.

   ![start_workflow](assets/start_workflow.png)

1. Seleccione el **[!UICONTROL Recursos de etiquetas inteligentes DAM]** flujo de trabajo y especifique un título para el flujo de trabajo.
1. Toque o haga clic **[!UICONTROL Inicio]**. El flujo de trabajo aplica las etiquetas a los recursos. Vaya a la carpeta de recursos y revise las etiquetas para comprobar si el servicio de contenido inteligente ha etiquetado los recursos correctamente. Para obtener más información, consulte [Administración de etiquetas inteligentes](managing-smart-tags.md).

>[!NOTE]
>
>En los ciclos de etiquetado posteriores, solo los recursos modificados se etiquetan de nuevo con etiquetas recién formadas.
>
>Sin embargo, incluso los recursos sin modificar se etiquetan si el espacio entre los ciclos de etiquetado último y actual para el flujo de trabajo de etiquetado supera las 24 horas.
>
>Para los flujos de trabajo de etiquetado periódicos, los recursos sin modificar se etiquetan cuando el lapso supera los 6 meses.
