---
title: Secuencia de comandos de análisis de solicitud
seo-title: Request Analysis Script
description: La secuencia de comandos de análisis de solicitudes se realiza para facilitar el análisis de los archivos access.log que producen un informe legible para su procesamiento posterior
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Secuencia de comandos de análisis de solicitud{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Descargar {#download}

Esta secuencia de comandos se realiza para facilitar el análisis de la variable `access.log` archivos que generan un informe legible para su procesamiento posterior.

[Obtener archivo](assets/analyse-access.sh)

## Descripción {#description}

Esta secuencia de comandos se realiza para facilitar el análisis de la variable `access.log` archivos que generan un informe legible para su procesamiento posterior.

Genera el número total de solicitudes, GET frente a POST, y la distribución de solicitudes a lo largo del tiempo y más.

El resultado está en la sintaxis Markdown, por lo que será más fácil convertirla a PDF con herramientas como pandoc o mostrarla en un navegador con complementos como el visor Markdown.

Puede analizar una ruta personalizada que se proporciona en la línea de comandos.

Tomando del comentario dentro del archivo que le indica cómo ejecutarlo:

Analizar CQ `access.log` extrapolación de varias informaciones y producción de un resultado de Markdown en `stdout`.

## Uso {#usage}

`./analyse-access.sh access.log.2013-&ast;`

puede proporcionar rutas personalizadas adicionales para analizar en la línea de comandos

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

puede guardar la salida utilizando una sencilla tubería

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
