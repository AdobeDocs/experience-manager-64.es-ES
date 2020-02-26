---
title: Integración de Adobe Analytics con AEM Screens
seo-title: Integración de Adobe Analytics con AEM Screens
description: Siga esta página para obtener información sobre la integración de AEM Screens de forma predeterminada con Adobe Analytics y le proporcionará una prueba de reproducción.
seo-description: Siga esta página para obtener información sobre la integración de AEM Screens de forma predeterminada con Adobe Analytics y le proporcionará una prueba de reproducción.
uuid: f4f71c85-ab6b-4e4d-94d3-5ba55ec0a246
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 2784b590-3402-492f-94a6-36fe16633e89
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Integración de Adobe Analytics con AEM Screens{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidad de AEM Screens solo está disponible si ha instalado AEM 6.4.2 Feature Pack 2 y AEM 6.3.3 Feature Pack 4.

>Para obtener acceso a cualquiera de estos paquetes de funciones, debe ponerse en contacto con la asistencia de Adobe y solicitar acceso. Cuando disponga de los permisos necesarios, puede descargarlo desde Uso compartido de paquetes.
>
Esta sección abarca los siguientes temas:

* **Información general**
* **Detalles de arquitectura**
* **Configuración de las propiedades**

## Información general {#overview}

***AEM Screens*** aprovecha Adobe Analytics y, con ello, puede conseguir algo único en el mercado: análisis multicanal que ayuda a correlacionar el contenido mostrado en la ubicación con otras fuentes de datos.

AEM Screens proporciona una integración lista para usar con Adobe Analytics y proporciona una prueba de reproducción.

En esta sección se describe la siguiente funcionalidad relacionada con la conexión de un proyecto de AEM Screens con Adobe Analytics:

* Permite realizar informes de prueba de reproducción por dispositivo
* Permite la prueba de reproducción de informes por recurso
* Garantiza que todos los eventos de reproductor se capturen y marquen la hora
* Garantiza que todos los eventos del reproductor se almacenen localmente si la reproducción no está conectada a una red

La integración de Adobe Analytics con AEM Screens impone los siguientes *objetivos*:

* Habilitar el ROI de las implementaciones de publicidad dinámica
* Integrar Analytics como base para la futura habilitación de la recopilación y el análisis de información de uso

## Detalles de arquitectura {#architectural-details}

El siguiente diagrama arquitectónico explica la integración de Adobe Analytics con AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Activación de Adobe Analytics en AEM Screens {#enabling-adobe-analytics-in-aem-screens}

La configuración de Adobe Analytics se puede configurar desde la consola OSGi.

Vaya a la Configuración **de la consola web de** Adobe Experience Manager para configurar Adobe Analytics para pantallas AEM, como se muestra en la figura siguiente:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

### Configuración de las propiedades {#configuring-the-properties}

>[!CAUTION]
Antes de configurar las propiedades, póngase en contacto con el administrador de relaciones de Adobe para crear un ticket con el fin de obtener una clave **de API de** Analytics y un proyecto **de** Analytics para utilizarlo con AEM Screens.

La siguiente tabla resalta las propiedades con su descripción para configurar Adobe Analytics para pantallas AEM:

<table> 
 <tbody>
  <tr>
   <td><strong>Propiedad</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr>
  <tr>
   <td><strong>URL de Analytics</strong></td> 
   <td>Dirección URL para publicar datos de análisis desde el reproductor<br /> </td> 
  </tr>
  <tr>
   <td><strong>Clave de API de Analytics</strong></td> 
   <td>Clave de API para autenticarse en el servidor de Adobe Analytics (proporcionada por el Administrador de cuentas)</td> 
  </tr>
  <tr>
   <td><strong>Proyecto de Analytics</strong></td> 
   <td>Proyecto de AEM Screens configurado en el análisis para recibir datos (proporcionado por el Administrador de cuentas)</td> 
  </tr>
  <tr>
   <td><strong>creación</strong></td> 
   <td><p>Entorno de fase o producción.</p> <p><em>
   Para desarrollo/etapa</em> : https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Para Producción</em> - https://cc-api-data.adobe.io/ingest/</p> </td> 
  </tr>
  <tr>
   <td><strong>Frecuencia de envío de Analytics</strong></td> 
   <td>Frecuencia en minutos para enviar datos de análisis desde los reproductores. De forma predeterminada, se establece en 15 minutos.</td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
De forma predeterminada, la **Frecuencia de envío de Analytics **es de 15 minutos.

#### Uso de Adobe Analytics Service en AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Este escenario invoca la API de Analytics a través de llamadas REST desde un servicio de análisis en el firmware y en los componentes principales de pantallas de instrumentos para crear y enviar de forma explícita eventos específicos de un caso de uso concreto, permitiendo al mismo tiempo la extensibilidad de los mensajes personalizados que se pueden enviar a Analytics desde un canal desarrollado personalizado.

Los eventos de Analytics se almacenan sin conexión en la base de datos indexada y, posteriormente, se fragmentan y se envían a la nube.

>[!NOTE]
Para obtener más información sobre las ***secuencias*** y los ***modelos de datos estándar para eventos***, consulte [Configuración de Adobe Analytics para pantallas](configuring-adobe-analytics-aem-screens.md) AEM en la sección de AEM Screens para desarrolladores.

