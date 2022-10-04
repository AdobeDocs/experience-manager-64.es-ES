---
title: Propiedades de configuración de Interactive Communications
seo-title: Interactive Communication configuration properties
description: Editar propiedades de configuración predeterminadas para Interactive Communications
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 7%

---

# Propiedades de configuración de Interactive Communications {#interactive-communications-configuration-properties}

Editar propiedades de configuración predeterminadas para Interactive Communications

Interactive Communications incluye propiedades que se configuran automáticamente después de instalar el [Complemento de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) paquete. Los autores de Interactive Communication pueden editar estas propiedades de configuración predeterminadas mediante el **Configuración de la consola web de Adobe Experience Manager** página.

Abra el **Configuración de la consola web de Adobe Experience Manager** con la siguiente dirección URL:

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

Las propiedades de configuración incluyen:

* [Configuración de fragmentos de documento](#document-fragments-configuration)
* [Crear configuración de correspondencia](#create-correspondence-configuration)
* [Configuración del canal web de comunicaciones interactivas y formularios adaptables](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuración del tema del canal web de comunicaciones interactivas y formularios adaptables](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuración de fragmentos de documento {#document-fragments-configuration}

Toque **Configuración de fragmentos de documento** en el **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración de los fragmentos de documento.

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Descripción</td> 
   <td>Predeterminado</td> 
   <td>Valores aceptables</td> 
  </tr> 
  <tr> 
   <td>Formatos de visualización de datos</td> 
   <td>Formato de visualización específico de la configuración regional para campos, variables y elementos del modelo de datos de formulario disponibles al crear una comunicación interactiva para canales impresos y web.</td> 
   <td> 
    <ul> 
     <li>configuración regional = en_US, de_DE, fr_FR y ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Sangría</td> 
   <td>La anchura de una unidad de sangría aplicada al texto de la lista de fragmentos de documento.</td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Anchura mínima de los números romanos</td> 
   <td>Ancho mínimo que se aplicará al campo de viñeta o número, al utilizar números romanos en fragmentos de documento de lista. </td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Ancho mínimo de número</td> 
   <td>Ancho mínimo que se aplicará a la viñeta o al campo numérico, al utilizar listas numeradas separadas de números romanos en fragmentos de documentos de lista.</td> 
   <td>8,0 mm</td> 
   <td>Número</td> 
  </tr> 
 </tbody> 
</table>

## Crear configuración de correspondencia {#create-correspondence-configuration}

Toque **Crear configuración de correspondencia** en el **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración de la interfaz de usuario del agente.

| Propiedad | Descripción | Predeterminado | Valores aceptables |
|---|---|---|---|
| Mostrar contenido resuelto para editarlo | Seleccione la casilla de verificación para mostrar el contenido resuelto (valores reales en lugar de marcadores de posición) mientras edita el módulo de texto en la interfaz de usuario del agente. | No seleccionado | No aplicable |
| Aplicar marca de agua durante la vista previa | Seleccione la casilla de verificación para aplicar una marca de agua al canal de impresión de comunicación interactiva en el modo de vista previa. | No seleccionado | No aplicable |

## Configuración del canal web de comunicaciones interactivas y formularios adaptables {#adaptive-form-and-interactive-communication-web-channel-configuration}

Toque **Configuración del canal web de comunicaciones interactivas y formularios adaptables** en el **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración del canal web de comunicaciones interactivas y Forms adaptable. En la tabla siguiente se describen las propiedades relacionadas con las comunicaciones interactivas:

| Propiedad | Descripción | Predeterminado | Valores aceptables |
|---|---|---|---|
| Mostrar marcador de posición | Seleccione la casilla de verificación para activar la visualización de marcadores de posición para los campos incluidos en formularios adaptables y comunicaciones interactivas. | Seleccionado | No aplicable |
| Máximo de entradas de caché | Establezca el número máximo de formularios adaptables y comunicaciones interactivas que se pueden recuperar mediante la memoria caché. | 100 | Número |
| Convertir el nombre de archivo en único | Seleccione la casilla de verificación para incluir nombres únicos para los archivos como archivos adjuntos en Adaptive Forms y Comunicaciones interactivas. | No seleccionado | No aplicable |

## Configuración del tema del canal web de comunicaciones interactivas y formularios adaptables {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Toque **Configuración del tema del canal web de comunicaciones interactivas y formularios adaptables** en el **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración de los temas del canal web Adaptive Forms e Interactive Communications.

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad</td> 
   <td>Descripción</td> 
   <td>Predeterminado</td> 
   <td>Valores aceptables</td> 
  </tr> 
  <tr> 
   <td>Nombre de la lista de fuentes</td> 
   <td>Lista de fuentes disponibles para usar durante la creación de Forms adaptable y comunicaciones interactivas.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impacto</p> <p>Palatino Linotype</p> </td> 
   <td>Todas las fuentes válidas del servidor de Adobe</td> 
  </tr> 
 </tbody> 
</table>
