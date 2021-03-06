---
title: Información general sobre comunicaciones interactivas
seo-title: Información general sobre comunicaciones interactivas
description: Este artículo incluye información general, casos de uso de muestra, flujo de trabajo de creación y diferencias entre la comunicación interactiva y la carta.
seo-description: Funciones clave de comunicación interactiva, casos de uso de muestra, flujo de trabajo de creación y diferencias entre la comunicación interactiva y la administración de correspondencia
uuid: a06b4ac7-ca20-4d6d-b2b7-87b21e2f5cf9
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 67b03098-c58d-4a57-90e0-e4ddd78e5d99
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 5%

---


# Información general sobre comunicaciones interactivas {#interactive-communications-overview}

Este artículo incluye información general, casos de uso de muestra, flujo de trabajo de creación y diferencias entre la comunicación interactiva y la carta.

![](do-not-localize/correspondence-management.png)

Interactive Communications centraliza y administra la creación, el ensamblaje y el envío de correspondencia segura, personalizada e interactiva, como correspondencia comercial, documentos, declaraciones, avisos de beneficios, correos de marketing, facturas y kits de bienvenida.

## Capacidades clave {#key-capabilities}

A continuación se describen las funciones clave de Interactive Communications:

* Integración lista para usar con el modelo de datos de formulario para permitir un acceso fácil y simplificado a las bases de datos back-end y otros sistemas CRM, como MS® Dynamics
* Interfaz de creación integrada para canales web e impresos con capacidad para generar automáticamente canales web a partir del canal de impresión
* Gráficos para presentar información en formatos visuales fáciles de entender en impresión y Web
* Los fragmentos de documento admiten el editor de reglas y el modelo de datos de formulario
* La interfaz de usuario del agente muestra la impresión y la previsualización web de la comunicación interactiva
* Arrastrar y soltar componentes para construir rápidamente canales de impresión y Web

## Ejemplo de caso de uso {#sample-use-case}

El [kit de bienvenida para un cliente de tarjeta de crédito](/help/forms/using/finance-reference-site-walkthrough.md#credit-card-application-walkthrough) muestra las capacidades de una comunicación interactiva.

## Creación de comunicación interactiva {#interactive-communication-creation}

![interactive_Communication-01](assets/interactive_communication-01.jpg)

### Flujo de trabajo {#workflow}

Para crear una comunicación interactiva, tenga los [bloques de creación](#buildingblocks) para la comunicación interactiva listos y complete los siguientes pasos:

1. Elija [crear una comunicación interactiva](/help/forms/using/create-interactive-communication.md).

1. Especifique el [modelo de datos de formulario](/help/forms/using/data-integration.md), el servicio de cumplimentación previa y las [plantillas de impresión y canal Web](/help/forms/using/web-channel-print-channel.md). Puede elegir generar canal web desde el canal de impresión.

1. Mediante la [interfaz de arrastrar y soltar](/help/forms/using/introduction-interactive-communication-authoring.md), agregue fragmentos de documento, imágenes, componentes para imprimir y canal web de la comunicación interactiva según sea necesario.
1. Configure las propiedades de los componentes insertados, como por ejemplo:

   1. Imágenes
   1. [Tablas](/help/forms/using/create-interactive-communication.md#tables)  (incluidos los fragmentos de diseño)
   1. [Gráficos](/help/forms/using/chart-component-interactive-communications.md)
   1. [Fragmentos de documento](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. Imprima previsualización y canales web y, si es necesario, edite la Comunicación interactiva.
1. El agente utiliza la interfaz de usuario del agente para [preparar la comunicación interactiva](/help/forms/using/prepare-send-interactive-communication.md) para enviarla al proceso de destinatario/anuncio.

### Componentes {#buildingblocks}

A continuación se indican los componentes necesarios para crear una comunicación interactiva:

* [Modelo de datos de formulario](/help/forms/using/data-integration.md)
* [Plantillas de impresión y canal web](/help/forms/using/web-channel-print-channel.md)
* [Fragmentos de documento](/help/forms/using/document-fragments.md)
* Imágenes
* [](/help/forms/using/themes.md) Temas para el canal Web

## Administración De Correspondencia Y Comunicaciones Interactivas {#interactive-communications-vs-correspondence-management}

Interactive Communication es el método predeterminado y recomendado para crear comunicaciones con los clientes. Para seguir utilizando las letras que se crean en AEM 6.3 Forms y AEM 6.2 Forms, debe [instalar un paquete de compatibilidad](/help/forms/using/compatibility-package.md). A continuación se muestra una comparación entre las capacidades de la comunicación interactiva y la carta.

<table> 
 <tbody>
  <tr>
   <td><strong>Capacidad</strong></td> 
   <td><strong>Comunicación interactiva</strong></td> 
   <td><strong>Carta</strong></td> 
  </tr>
  <tr>
   <td>Salida</td> 
   <td>Imprimir y Web</td> 
   <td>Imprimir</td> 
  </tr>
  <tr>
   <td>Esquema</td> 
   <td>Modelo de datos de formulario </td> 
   <td>Diccionario de datos </td> 
  </tr>
  <tr>
   <td>Localización</td> 
   <td>No se admite en el modelo de datos de formulario</td> 
   <td>Compatible con el diccionario de datos</td> 
  </tr>
  <tr>
   <td>Editor de reglas</td> 
   <td>
    <ul> 
     <li>Editor de reglas de compatibilidad de texto y condición para crear condiciones en línea</li> 
     <li>El editor de comunicaciones interactivas admite la aplicación de reglas en componentes del canal web</li> 
    </ul> </td> 
   <td>No hay IU para la creación de expresión condicional</td> 
  </tr>
  <tr>
   <td>Creación  </td> 
   <td>Interfaz de arrastrar y soltar para la construcción de impresión y canal web</td> 
   <td>Sin mecanismo de arrastrar y soltar </td> 
  </tr>
  <tr>
   <td>Gráficos</td> 
   <td>Gráficos admitidos en impresión y canal web</td> 
   <td>No se admite</td> 
  </tr>
  <tr>
   <td>Temas</td> 
   <td>Utiliza temáticas para aplicar estilo al canal web</td> 
   <td>No admite temáticas</td> 
  </tr>
  <tr>
   <td>Auditoría y control de versiones</td> 
   <td>No se admite</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Borra y gestiona instancias</td> 
   <td>No se admite</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Procesamiento por lotes</td> 
   <td>Compatible </td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Firma del agente</td> 
   <td>No se admite</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Funciones remotas</td> 
   <td>No se admite</td> 
   <td>Compatible</td> 
  </tr>
 </tbody>
</table>

