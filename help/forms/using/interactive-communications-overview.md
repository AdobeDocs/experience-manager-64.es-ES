---
title: Información general sobre Interactive Communications
seo-title: Interactive Communications Overview
description: Este artículo contiene información general, casos de uso de ejemplo, el flujo de trabajo de creación y las diferencias entre una comunicación interactiva y una carta.
seo-description: Interactive Communication key capabilities, sample use cases, creation workflow, and differences between Interactive Communication and Correspondence Management
uuid: a06b4ac7-ca20-4d6d-b2b7-87b21e2f5cf9
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 67b03098-c58d-4a57-90e0-e4ddd78e5d99
exl-id: 386fc8b2-c92d-4731-8445-1bb6af54fd98
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 89%

---

# Información general sobre Interactive Communications {#interactive-communications-overview}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Este artículo contiene información general, casos de uso de ejemplo, el flujo de trabajo de creación y las diferencias entre una comunicación interactiva y una carta.

![](do-not-localize/correspondence-management.png)

Interactive Communications centraliza y administra la creación, el ensamblado y el envío de correspondencia segura, personalizada e interactiva, como correspondencia comercial, documentos, declaraciones, avisos de beneficios, correos de marketing, facturas y kits de bienvenida.

## Capacidades clave {#key-capabilities}

A continuación, se muestran las capacidades clave de Interactive Communications:

* Integración predeterminada con el modelo de datos de formulario para permitir un acceso fácil y sencillo a las bases de datos back-end y a otros sistemas CRM, como MS® Dynamics
* Interfaz de creación integrada para los canales web y de impresión con capacidad para generar automáticamente el canal web a partir del canal de impresión
* Gráficos para presentar la información en formatos visuales fácilmente comprensibles de forma impresa y web
* Los fragmentos de documento admiten el editor de reglas y el modelo de datos de formulario
* La interfaz de usuario del agente muestra la vista previa impresa y web de la comunicación interactiva
* Arrastre y suelte los componentes para crear rápidamente los canales impreso y web

## Ejemplo de caso de uso {#sample-use-case}

La variable [Kit de bienvenida para un cliente con tarjeta de crédito](/help/forms/using/finance-reference-site-walkthrough.md#credit-card-application-walkthrough) ejemplo de uso muestra las capacidades de una comunicación interactiva.

## Creación de una comunicación interactiva  {#interactive-communication-creation}

![comunicación_interactiva-01](assets/interactive_communication-01.jpg)

### Flujo de trabajo {#workflow}

Para crear una comunicación interactiva, prepare los [componentes básicos](#buildingblocks) de la comunicación interactiva y, a continuación, complete los siguientes pasos:

1. Elija [Crear una comunicación interactiva](/help/forms/using/create-interactive-communication.md).

1. Especifique el [modelo de datos de formulario](/help/forms/using/data-integration.md), el servicio de relleno previo y las [plantillas de los canales impreso y web](/help/forms/using/web-channel-print-channel.md). Si lo desea, puede generar el canal web a partir del canal de impresión.

1. Usando la [interfaz de arrastrar y soltar](/help/forms/using/introduction-interactive-communication-authoring.md), añada fragmentos de documento, imágenes y componentes al canal impreso y web de la comunicación interactiva, según sea necesario.
1. Configure las propiedades de los componentes insertados, como, por ejemplo, los siguientes:

   1. Imágenes
   1. [Tablas](/help/forms/using/create-interactive-communication.md#tables) (incluidos fragmentos de diseño)
   1. [Gráficos](/help/forms/using/chart-component-interactive-communications.md)
   1. [Fragmentos de documento](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. Obtenga una vista previa de los canales impreso y web y, si es necesario, edite la comunicación interactiva.
1. El agente utiliza la interfaz de usuario del agente para [preparar la comunicación interactiva](/help/forms/using/prepare-send-interactive-communication.md) para enviarla al destinatario/proceso de publicación.

### Componentes {#buildingblocks}

A continuación se indican los componentes básicos necesarios para crear una comunicación interactiva:

* [Modelo de datos de formulario](/help/forms/using/data-integration.md)
* [Plantillas de los canales impreso y web](/help/forms/using/web-channel-print-channel.md)
* [Fragmentos de documento](/help/forms/using/document-fragments.md)
* Imágenes
* [Temas](/help/forms/using/themes.md) para el canal web

## Interactive Communications frente a Administración de correspondencia {#interactive-communications-vs-correspondence-management}

La comunicación interactiva es la forma predeterminada y recomendada de crear comunicaciones con los clientes. Para seguir utilizando las cartas que se crean en AEM 6.3 Forms y AEM 6.2 Forms, debe [instalar un paquete de compatibilidad](/help/forms/using/compatibility-package.md). A continuación se muestra una comparación entre las funcionalidades de una comunicación interactiva y una carta.

<table> 
 <tbody>
  <tr>
   <td><strong>Capacidad</strong></td> 
   <td><strong>Comunicación interactiva</strong></td> 
   <td><strong>Carta</strong></td> 
  </tr>
  <tr>
   <td>Salida</td> 
   <td>Impresa y web</td> 
   <td>Impresa</td> 
  </tr>
  <tr>
   <td>Esquema</td> 
   <td>Modelo de datos de formulario </td> 
   <td>Diccionario de datos </td> 
  </tr>
  <tr>
   <td>Localización</td> 
   <td>No compatible con el modelo de datos de formulario</td> 
   <td>Compatible con el diccionario de datos</td> 
  </tr>
  <tr>
   <td>Editor de reglas</td> 
   <td>
    <ul> 
     <li>Un Editor de reglas compatible con texto y condiciones para crear condiciones en línea</li> 
     <li>El Editor de comunicaciones interactivas admite la aplicación de reglas en los componentes del canal web</li> 
    </ul> </td> 
   <td>No hay interfaz de usuario para la creación de expresiones condicionales</td> 
  </tr>
  <tr>
   <td>Creación  </td> 
   <td>Interfaz de arrastrar y soltar para crear los canales web e impreso</td> 
   <td>No hay mecanismo de arrastrar y soltar </td> 
  </tr>
  <tr>
   <td>Gráficos</td> 
   <td>Gráficos admitidos tanto en el canal impreso como en el canal web</td> 
   <td>No compatible</td> 
  </tr>
  <tr>
   <td>Temas</td> 
   <td>Utiliza temas para aplicar estilo al canal web</td> 
   <td>No admite temas</td> 
  </tr>
  <tr>
   <td>Auditoría y control de versiones</td> 
   <td>No compatible</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Borradores y administrar instancias</td> 
   <td>No compatible</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Procesamiento por lotes</td> 
   <td>Compatible </td> 
   <td>Compatible </td> 
  </tr>
  <tr>
   <td>Firma del agente</td> 
   <td>No compatible</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Funciones remotas</td> 
   <td>No compatible</td> 
   <td>Compatible</td> 
  </tr>
 </tbody>
</table>
