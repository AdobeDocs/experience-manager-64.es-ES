---
title: Integración de páginas de aterrizaje con Adobe Analytics
seo-title: Integrating Landing Pages with Adobe Analytics
description: Aprenda a integrar páginas de aterrizaje con Adobe Analytics.
seo-description: Learn how to integrate landing pages with Adobe Analytics.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
exl-id: 2923ae94-375a-4c44-a08f-f992eb08000a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 2%

---

# Integración de páginas de aterrizaje con Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM ha integrado la solución de páginas de aterrizaje con [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) mediante los siguientes componentes de llamada a acción:

1. Componente de pulsaciones
1. Componente de vínculo gráfico

Estos componentes exponen ciertos atributos que se pueden asignar mediante variables de Adobe Analytics (tráfico, variables de conversión) y eventos de éxito para enviar información a Adobe Analytics.

## Requisitos previos {#prerequisites}

Adobe recomienda pasar por el [integración AEM-Adobe Analytics existente](/help/sites-administering/adobeanalytics.md) para comprender cómo funciona esta integración.

## Componentes disponibles para asignación {#components-available-for-mapping}

En AEM, la variable **Llamada a acción** componentes - **ClickThroughLink** y **GraphicalLink** - mostrado aquí en la barra de tareas, se puede asignar a variables de Adobe Analytics.

![imagen_1-21](assets/chlimage_1-21.jpeg)

### Asignación de componentes de la página de aterrizaje a Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

Para asignar componentes de página de aterrizaje a Adobe Analytics:

1. Después de crear la configuración de Adobe Analytics y crear una nueva estructura, seleccione el grupo de informes correspondiente en el menú desplegable. Esto hace que se recuperen las variables de Adobe Analytics y se muestren en el buscador de contenido.
1. Arrastre y suelte los componentes de Llamada a acción (CTA) de la barra de tareas en el área de asignación en medio de la página, según corresponda.

<table> 
 <tbody>
  <tr>
   <td><strong>Nombre del componente</strong></td> 
   <td><strong>Atributos expuestos</strong></td> 
   <td><strong>Significado del atributo</strong></td> 
  </tr>
  <tr>
   <td><strong>Llamada a acción: vínculo de pulsaciones</strong></td> 
   <td><i>eventdata.clickthroughLinkLabel</i> <br /> </td> 
   <td>Etiqueta del vínculo o el texto del vínculo </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td> 
   <td>Destino al que se dirigirá cuando haga clic en el vínculo </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clickLinkClick</i> <br /> </td> 
   <td>El evento de clic </td> 
  </tr>
  <tr>
   <td><strong>Llamada a acción: vínculo gráfico</strong></td> 
   <td><i>eventdata.clicktroughImageLabel</i> <br /> </td> 
   <td>Título de la imagen de llamada a acción </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageTarget</i> <br /> </td> 
   <td>Destino al que se dirigirá cuando haga clic en la imagen que contiene un vínculo</td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageAsset</i> <br /> </td> 
   <td>Ruta al recurso de imagen en el repositorio </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clicktroughImageClick</i> <br /> </td> 
   <td>El evento de clic</td> 
  </tr>
 </tbody>
</table>

1. Asigne estos atributos expuestos con cualquier variable de Adobe Analytics desde Content Finder. El marco ya está listo para utilizarse.
1. Ahora puede crear una nueva página de aterrizaje o abrir una página de aterrizaje existente con componentes de llamada a acción existentes y hacer clic en **Cloud Services** en **Propiedades de página** en la barra de tareas (en la IU táctil, seleccione **Abrir propiedades** y haga clic en **Cloud Services**) y configure el marco que se utilizará con la página de aterrizaje. Seleccione el marco en la lista desplegable.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Después de configurar la estructura con la página de aterrizaje, ahora puede utilizar los componentes instrumentados y cualquier clic en CTA se registra en Adobe Analytics.
