---
title: 'Exportar a CSV  '
seo-title: 'Exportar a CSV  '
description: Permite exportar información sobre las páginas a un archivo CSV en el sistema local
seo-description: Permite exportar información sobre las páginas a un archivo CSV en el sistema local
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 78%

---


# Exportar a CSV  {#export-to-csv}

**Al crear una exportación de CSV** puede exportar información sobre las páginas a un archivo CSV en el sistema local.

* El archivo descargado se llama `export.csv`.
* El contenido depende de las propiedades que seleccione.
* Puede definir la ruta de la exportación, así como la profundidad.

>[!NOTE]
>
>Se utiliza la función de descarga (y el destino predeterminado) de su navegador.

El asistente para crear exportaciones de CSV permite seleccionar lo siguiente:

* Propiedades para exportar

   * Metadatos

      * Modificado
      * Publicado
   * Análisis

      * Vistas de la página
      * Visitantes únicos
      * Tiempo empleado en la página


* Profundidad

   * Ruta de acceso principal
   * Solo elementos secundarios directos
   * Niveles adicionales de elementos secundarios
   * Niveles

El archivo `export.csv` resultante se puede abrir en Excel o en cualquier otra aplicación compatible.

![chlimage_1-58](assets/chlimage_1-58.png)

La opción crear **exportación de CSV** está disponible al explorar la consola **Sitios** (en vista de Lista): es una opción del menú desplegable **Crear**:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Para crear una exportación de CSV: 

1. Abra la consola **Sitios** y vaya hasta la ubicación deseada.
1. En la barra de herramientas, seleccione **Crear** y luego **Exportación de CSV** para abrir el asistente:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Seleccione las propiedades oportunas para la exportación.
1. Seleccione **Crear**.

