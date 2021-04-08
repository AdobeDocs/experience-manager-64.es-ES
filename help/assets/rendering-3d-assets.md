---
title: Procesar recursos 3D
seo-title: Procesar recursos 3D
description: Aprenda a procesar recursos 3D que manipule y guardó en AEM para crear imágenes 2D para sus páginas web.
seo-description: Aprenda a procesar recursos 3D que manipule y guardó en AEM para crear imágenes 2D para sus páginas web.
uuid: ee4d669c-72b1-4f7a-9a68-a7c6d59c7856
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5b044519-d034-4f05-98c5-f1b299a3ea37
exl-id: 3eecec53-0b39-4783-8730-f08705183941
feature: Recursos 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 72%

---

# Procesar recursos 3D {#rendering-d-assets}

Puede procesar los recursos 3D que haya manipulado y guardado en AEM para crear imágenes 2D que se usarán en las páginas de contenido web.

Consulte [Edición del contenido de la página](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content).

## Consideraciones de rendimiento al procesar los recursos 3D {#performance-considerations-when-rendering-d-assets}

El procesamiento de contenido 3D consume importantes recursos del servidor, como la CPU y la memoria. Como tal, el procesamiento puede llevar a menudo una gran cantidad de tiempo. El procesamiento de horas varía sustancialmente según diversos factores, incluyendo además el tamaño de modelo y el hardware de servidor obvios:

* **Selección de procesador**.

    El procesador Rapid Refine™ predeterminado en AEM 3D baja un poco el nivel de calidad para conseguir tiempos de procesamiento más breves. Sin embargo, produce resultados de alta calidad en muchas aplicaciones. Los procesadores que proporcionan las aplicaciones de terceros (por ejemplo, V-Ray™ o NVIDIA® Mental Ray® que se implementan en Autodesk® Maya® o Autodesk® 3ds Max®) son extremadamente configurables y la compensación entre el rendimiento y la calidad se realiza cuando se ha diseñado el escenario.

* **IBL frente a la iluminación tradicional**.

   Si bien este factor es de menor importancia en lo referente al procesador predeterminado Rapid Refine, los procesadores de terceros como Mental Ray son sustancialmente más lentos a la hora de realizar operaciones de procesamiento si usan etapas IBL que cuando utilizan puntos tradicionales o luces focales.

El procesador de Rapid Refine suele tardar unos minutos en procesar imágenes más grandes. Sin embargo, los procesadores de terceros a menudo tardan varios minutos, horas incluso, cuando están configurados para la máxima calidad.

Los procesos para convertir, procesar y representar trabajos se ponen en cola en el servidor según sea necesario para evitar la sobrecarga del servidor. El mensaje &quot;Esperando procesamiento…&quot; se muestra en recursos cargados recientemente en la vista de tarjetas. Este estado indica que otras tareas de procesamiento deben terminar antes de que el trabajo actual de procesamiento pueda comenzar.

>[!NOTE]
>
>Un recurso 3D siempre se procesa con los materiales originales, independientemente de qué materiales se muestran en la vista interactiva de AEM 3D. Esta funcionalidad se aplica al procesador integrado Rapid Refine y a todos los procesadores nativos.

**Para procesar los recursos 3D**:

1. Abra un recurso 3D para ver el contenido.

   Consulte [Ver recursos 3D](viewing-3d-assets.md).

1. En Adobe Experience Manager, en la página **[!UICONTROL Navegación]**, pulse **[!UICONTROL Recursos]**.
1. Cerca de la esquina superior derecha de la página, en la lista desplegable **[!UICONTROL Ver]**, pulse **[!UICONTROL Vista de tarjeta]**.
1. Busque el objeto 3D que desea procesar.
1. Pulse la tarjeta del objeto 3D para abrirlo en la página de detalles del recurso.
1. Cerca de la esquina superior izquierda de la página, pulse la lista desplegable y, a continuación, seleccione **[!UICONTROL Procesar]**.

   ![chlimage_1-369](assets/chlimage_1-369.png)

1. Cerca de la esquina superior derecha de la página de detalles del recurso, pulse el icono **[!UICONTROL Selector de escenario]** (punto destacado) y, a continuación, seleccione un nombre de escenario con el fondo y la iluminación que desea aplicar al objeto 3D.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   ![chlimage_1-370](assets/chlimage_1-370.png)

   **[!UICONTROL Icono del selector de escenario]**

1. En la lista desplegable **[!UICONTROL Render]** situada en la parte izquierda de la página de detalles del recurso, seleccione un procesador.

   El procesador predeterminado **Rapid Refine** siempre está disponible. Si el escenario que ha seleccionado es un formato nativo, el procesador de terceros correspondiente también estará disponible en la lista que seleccione.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Haga lo siguiente:

   * En los campos **[!UICONTROL Width]** y **[!UICONTROL Height]**, introduzca la anchura y la altura en píxeles que desea que se procese la imagen.
   * En el campo **[!UICONTROL Image Name]**, introduzca el nombre de la imagen representada.
   * En el campo **[!UICONTROL Export Path]**, introduzca la ruta en la que desea almacenar la imagen procesada. O bien, pulse el icono **[!UICONTROL Examinar]** y vaya a una ubicación.
   * (Opcional) Seleccione o anule la selección de la casilla **[!UICONTROL Sobrescribir imagen existente]e**.

1. Cerca de la esquina superior derecha de la página de detalles del recurso, pulse el icono **[!UICONTROL Selector de cámara]**. Seleccione la vista de cámara que desea aplicar a la imagen procesada.

   Las barras de la izquierda y la derecha o las barras superiores e inferiores son un indicador visual con respecto al cual las partes de la vista se procesarán. Cuando el escenario seleccionado proporciona la cámara, puede seleccionar una cámara predefinida.

   ![chlimage_1-371](assets/chlimage_1-371.png)

   **[!UICONTROL Icono del selector de cámara]**

1. Pulse **[!UICONTROL Iniciar procesamiento]** para iniciar el procesamiento.

   Se muestra un mensaje temporalmente para indicar que el procesamiento se ha iniciado. Para su comodidad, este mensaje también incluye un vínculo a la carpeta de salida seleccionada para que pueda acceder a ella directamente.
