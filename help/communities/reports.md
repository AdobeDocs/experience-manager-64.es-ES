---
title: Consola Informes
seo-title: Reports Console
description: Obtenga información sobre cómo acceder a los informes
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 6%

---

# Consola Informes {#reports-console}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Para AEM Communities, existen varios informes a los que se puede acceder de varias formas desde el entorno de creación.

En general, los diversos informes son:

* [Informe de asignaciones](#assignments-report) - para [comunidad de habilitación](overview.md#enablement-community), proporciona una descripción general del progreso de los estudiantes en sus asignaciones, incluida una puntuación asociada si se implementa el estándar SCORM
* [Informe de vistas](#views-report) : proporciona un gráfico de las vistas de contenido por los miembros de la comunidad y los visitantes del sitio para cualquier sitio de la comunidad.
* [Informe de anuncios](#posts-report) - proporciona un gráfico de varios tipos de anuncios de los miembros de la comunidad en cualquier sitio de la comunidad

When [Adobe Analytics está habilitado](sites-console.md#analytics), los informes incluirán el número de vistas, reproducciones, comentarios y clasificaciones de cada recurso de habilitación a lo largo del tiempo

Los informes tabulares se pueden exportar en formato .csv para su procesamiento posterior.

## Consolas de informes {#reporting-consoles}

### Informes para sitios de la comunidad {#reports-for-community-sites}

* Desde la navegación global: **[!UICONTROL Navegación > Comunidades > Informes]**
* Elija entre
   * **[!UICONTROL Informe de asignaciones]**
      * Generar un informe para el Sitio, Usuario o Grupo de la Comunidad y Asignación seleccionados
   * **[!UICONTROL Informe de anuncios]**
      * Generar un informe para el sitio de la comunidad, el tipo de contenido y el período de tiempo seleccionados
   * **[!UICONTROL Informe de vistas]**
      * Generar un informe para el sitio de la comunidad, el tipo de contenido y el período de tiempo seleccionados
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Informes para recursos de habilitación y rutas de aprendizaje {#reports-for-enablement-resources-and-learning-paths}

* Desde la navegación global: **[!UICONTROL Navegación > Comunidades > Recursos]**
* Seleccionar un sitio de comunidad de habilitación existente
   * Select **[!UICONTROL Informe]** para generar informes que cubran todos los recursos de habilitación
   * Seleccionar una ruta de aprendizaje de habilitación
   * Select **[!UICONTROL Informe]** icono para generar informes para
      * Los recursos de habilitación incluidos
      * Los estudiantes asignados a la ruta de aprendizaje
* Estos informes proporcionan:
   * Datos de tabla, descargables como CSV
      * Identificación del alumno
      * Su situación
      * Si se asigna o se accede a través del catálogo
      * Número de observaciones formuladas
      * Clasificación por estrellas

Para obtener más información, consulte [Sección Informes](resources.md#report) de la consola Recursos.

## Informe de asignaciones {#assignments-report}

La consola Asignaciones permite filtrar los informes por sitio de la comunidad de habilitación, usuarios o grupos y asignación.

El informe proporciona información sobre su progreso, así como cualquier comentario o calificación que se haya proporcionado.

![chlimage_1-157](assets/chlimage_1-157.png)

Seleccione los criterios del informe:

* **[!UICONTROL Sitio]**
Seleccionar un sitio de comunidad de habilitación
* **[!UICONTROL Usuario o grupo]**
   * Seleccionar usuario para generar un informe para un alumno
   * Seleccionar grupo para generar un informe para un grupo de estudiantes El servicio de túnel accederá a los miembros y grupos de miembros desde el entorno de publicación
* **[!UICONTROL Asignación]**
Elija entre los recursos de habilitación asignados a los alumnos seleccionados

Select **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-158](assets/chlimage_1-158.png)

## Informe de vistas {#views-report}

La consola Vistas permite que las funciones de la comunidad generen informes sobre las vistas de página durante un período de tiempo determinado.

![chlimage_1-159](assets/chlimage_1-159.png)

Seleccione los criterios del informe:

* **[!UICONTROL Sitio]**
Seleccionar un sitio de comunidad
* **[!UICONTROL Tipo de contenido]**
Puede elegir Todo el contenido o seleccionar una de las funciones presentes en el sitio
* Lapso de tiempo Seleccione uno de:
   * Últimos 7 días
   * Últimos 30 días
   * Últimos 90 días
   * Año pasado

Select **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-160](assets/chlimage_1-160.png)

## Informe de anuncios {#posts-report}

La consola Anuncios permite generar informes sobre el número de anuncios a las funciones de la comunidad durante un período de tiempo determinado.

![chlimage_1-161](assets/chlimage_1-161.png)

Seleccione los criterios del informe:

* **[!UICONTROL Sitio]**
Seleccionar un sitio de comunidad
* **[!UICONTROL Tipo de contenido]**
Puede elegir Todo el contenido o seleccionar una de las funciones presentes en el sitio
* Lapso de tiempo Seleccione uno de:
   * Últimos 7 días
   * Últimos 30 días
   * Últimos 90 días
   * Año pasado

Select **[!UICONTROL Generar]** para crear el informe:

![chlimage_1-162](assets/chlimage_1-162.png)

## Solución de problemas {#troubleshooting}

### No hay sitios de la comunidad enumerados {#no-community-sites-listed}

Si no aparece ningún sitio de la comunidad, asegúrese de que Adobe Analytics esté habilitado para un sitio. Si elige informes sobre asignaciones, asegúrese de que la función de asignaciones esté en la estructura del sitio de la comunidad.
