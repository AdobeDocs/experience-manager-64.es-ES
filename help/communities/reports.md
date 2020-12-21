---
title: Consola de informes
seo-title: Consola de informes
description: Obtenga información sobre cómo acceder a los informes
seo-description: Obtenga información sobre cómo acceder a los informes
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---


# Consola de informes {#reports-console}

## Información general {#overview}

Para AEM Communities, existen varios informes a los que se puede acceder de varias formas desde el entorno de creación.

En general, los diversos informes son los siguientes:

* [Informe](#assignments-report)  de asignaciones: para una comunidad [ de ](overview.md#enablement-community)habilitación, proporciona una visión general del progreso de los alumnos en sus asignaciones, incluida una puntuación asociada si se implementa el estándar SCORM
* [Informe](#views-report)  vistas: proporciona un gráfico de vistas de contenido por miembros de la comunidad y visitantes del sitio para cualquier sitio de la comunidad
* [Informe](#posts-report)  Publicaciones: proporciona un gráfico de los distintos tipos de anuncios de los miembros de la comunidad en cualquier sitio de la comunidad

Cuando [Adobe Analytics está habilitado](sites-console.md#analytics), los informes incluirán el número de vistas, reproducciones, comentarios y clasificaciones de cada recurso de habilitación a lo largo del tiempo

Los informes tabulares se pueden exportar en formato .csv para su procesamiento posterior.

## Consolas de sistema de informes {#reporting-consoles}

### Informes para sitios de la comunidad {#reports-for-community-sites}

* Desde la navegación global: **[!UICONTROL Navegación > Comunidades > Informes]**
* Elija entre
   * **[!UICONTROL Informe de asignaciones]**
      * Generar un informe para el sitio, el usuario o el grupo de la comunidad y la asignación seleccionados
   * **[!UICONTROL Informe de anuncios]**
      * Generar un informe para el sitio de la comunidad, el tipo de contenido y el período de tiempo seleccionados
   * **[!UICONTROL Informe de vistas]**
      * Generar un informe para el sitio de la comunidad, el tipo de contenido y el período de tiempo seleccionados
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Informes para recursos de habilitación y rutas de aprendizaje {#reports-for-enablement-resources-and-learning-paths}

* Desde la navegación global: **[!UICONTROL Navegación > Comunidades > Recursos]**
* Seleccionar un sitio de comunidad de habilitación existente
   * Seleccione el icono **[!UICONTROL Informe]** para generar informes que cubran todos los recursos de habilitación
   * Seleccione una ruta de aprendizaje de habilitación
   * Seleccione el icono **[!UICONTROL Informe]** para generar informes
      * Los recursos de habilitación incluidos
      * Los alumnos asignados a la ruta de aprendizaje
* Estos informes proporcionan:
   * Datos de tabla, descargables como CSV
      * Identificación del alumno
      * Su situación
      * Si se asigna o se accede a través del catálogo
      * Número de observaciones formuladas
      * Calificación de estrella dada

Para obtener más información, consulte la [sección Informes](resources.md#report) de la consola Recursos.

## Informe de asignaciones {#assignments-report}

La consola Asignaciones permite que los informes se filtren mediante la habilitación de sitios de la comunidad, usuarios o grupos, y la asignación.

En el informe se proporciona información sobre su progreso, así como sobre las observaciones o calificaciones que se hayan proporcionado.

![chlimage_1-157](assets/chlimage_1-157.png)

Seleccione los criterios para el informe:

* ****
SitioSeleccione un sitio de comunidad de habilitación
* **[!UICONTROL Usuario o grupo]**
   * Seleccione Usuario para generar un informe para un alumno
   * Seleccione Grupo para generar un informe para un grupo de alumnos
El servicio de túnel tendrá acceso a los miembros y grupos de miembros desde el entorno de publicación
* ****
AsignaciónElija entre los recursos de habilitación asignados a los alumnos seleccionados

Seleccione **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-158](assets/chlimage_1-158.png)

## Informe de vistas {#views-report}

La consola Vistas permite generar informes en vistas de página según las características de la comunidad durante un período de tiempo determinado.

![chlimage_1-159](assets/chlimage_1-159.png)

Seleccione los criterios para el informe:

* ****
SitioSeleccionar un sitio de comunidad
* ****
Tipo de contenidoPuede elegir Todo el contenido o seleccionar una de las funciones presentes en el sitio
* Lapso de tiempo
Seleccione uno de los siguientes:
   * Últimos 7 días
   * Últimos 30 días
   * Últimos 90 días
   * Año pasado

Seleccione **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-160](assets/chlimage_1-160.png)

## Informe de anuncios {#posts-report}

La consola Anuncios permite generar informes en función del número de anuncios de las funciones de la comunidad durante un período de tiempo determinado.

![chlimage_1-161](assets/chlimage_1-161.png)

Seleccione los criterios para el informe:

* ****
SitioSeleccionar un sitio de comunidad
* ****
Tipo de contenidoPuede elegir Todo el contenido o seleccionar una de las funciones presentes en el sitio
* Lapso de tiempo
Seleccione uno de los siguientes:
   * Últimos 7 días
   * Últimos 30 días
   * Últimos 90 días
   * Año pasado

Seleccione **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-162](assets/chlimage_1-162.png)

## Solución de problemas {#troubleshooting}

### No hay sitios de comunidad enumerados {#no-community-sites-listed}

Si no aparece ningún sitio de comunidad, asegúrese de que Adobe Analytics esté habilitado para un sitio. Si elige informes en las asignaciones, asegúrese de que la función de asignaciones se encuentra en la estructura del sitio de la comunidad.
