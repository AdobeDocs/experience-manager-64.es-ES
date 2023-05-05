---
title: Exportar a CSV
seo-title: Export to CSV
description: Exportar información sobre las páginas a un archivo CSV en el sistema local
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 51%

---

# Exportar a CSV  {#export-to-csv}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

**Crear exportación de CSV** permite exportar información sobre las páginas a un archivo CSV en el sistema local.

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

   * Ruta principal
   * Solo elementos secundarios directos
   * Niveles adicionales de elementos secundarios
   * Niveles

El archivo `export.csv` resultante se puede abrir en Excel o en cualquier otra aplicación compatible.

![chlimage_1-58](assets/chlimage_1-58.png)

El creador **Exportación de CSV** está disponible al examinar la **Sitios** consola (en la vista de lista): es una opción del **Crear** menú desplegable:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Para crear una exportación de CSV: 

1. Abra la consola **Sitios** y vaya hasta la ubicación deseada.
1. En la barra de herramientas, seleccione **Crear** then **Exportación de CSV** para abrir el asistente:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Seleccione las propiedades necesarias para exportar.
1. Seleccione **Crear**.
