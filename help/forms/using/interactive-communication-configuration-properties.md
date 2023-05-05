---
title: Propiedades de configuración de comunicaciones interactivas
seo-title: Interactive Communication configuration properties
description: Editar propiedades de configuración predeterminadas para comunicaciones interactivas
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 90%

---

# Propiedades de configuración de comunicaciones interactivas {#interactive-communications-configuration-properties}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Editar propiedades de configuración predeterminadas para comunicaciones interactivas

Comunicaciones interactivas incluye propiedades que se configuran automáticamente después de instalar el paquete de [complementos de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Los autores de comunicaciones interactivas pueden editar estas propiedades de configuración predeterminadas mediante la página **Configuración de la consola web de Adobe Experience Manager**.

Abra la página **Configuración de la consola web de Adobe Experience Manager** con la siguiente URL:

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

Entre las propiedades de configuración se incluyen:

* [Configuración de fragmentos de documento](#document-fragments-configuration)
* [Configuración de Crear correspondencia](#create-correspondence-configuration)
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
   <td>El formato de visualización específico de la configuración regional para los campos, las variables y los elementos del modelo de datos de formulario disponibles al crear una comunicación interactiva para los canales impreso y web.</td> 
   <td> 
    <ul> 
     <li>configuración regional = en_US, de_DE, fr_FR y ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>--</p> </td> 
  </tr> 
  <tr> 
   <td>Sangría</td> 
   <td>La anchura de una unidad de sangría aplicada al texto de los fragmentos de documento de lista.</td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Anchura mínima de los números romanos</td> 
   <td>La anchura mínima que se aplicará al campo de viñeta o número al utilizar números romanos en fragmentos de documento de lista. </td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Anchura mínima de número</td> 
   <td>La anchura mínima que se aplicará a la viñeta o al campo numérico al utilizar listas numeradas separadas por números que no sean números romanos en fragmentos de documento de lista.</td> 
   <td>8,0 mm</td> 
   <td>Número</td> 
  </tr> 
 </tbody> 
</table>

## Configuración de Crear correspondencia {#create-correspondence-configuration}

Pulse **Configuración de Crear correspondencia** en la **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración de la interfaz de usuario del agente.

| Propiedad | Descripción | Predeterminado | Valores aceptables |
|---|---|---|---|
| Mostrar contenido resuelto para editarlo | Seleccione la casilla de verificación para mostrar el contenido resuelto (valores reales en lugar de marcadores de posición) mientras edita el módulo de texto de la interfaz de usuario del agente. | No seleccionado | No aplicable |
| Aplicar marca de agua durante la vista previa | Seleccione la casilla de verificación para aplicar una marca de agua al canal de impresión de una comunicación interactiva en el modo de vista previa. | No seleccionado | No aplicable |

## Configuración del canal web de comunicaciones interactivas y formularios adaptables {#adaptive-form-and-interactive-communication-web-channel-configuration}

Pulse **Configuración del canal web de comunicaciones interactivas y formularios adaptables** en la página **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración del canal web de las comunicaciones interactivas y los formularios adaptables. En la siguiente tabla se describen las propiedades relacionadas con Interactive Communications:

| Propiedad | Descripción | Predeterminado | Valores aceptables |
|---|---|---|---|
| Mostrar marcador de posición | Seleccione la casilla de verificación para activar la visualización de los marcadores de posición de los campos incluidos en los formularios adaptables y las comunicaciones interactivas. | Seleccionado | No aplicable |
| Número máximo de entradas de caché | Establezca el número máximo de formularios adaptables y comunicaciones interactivas que se pueden recuperar mediante la memoria caché. | 100 | Número |
| Convertir el nombre de archivo en único | Seleccione la casilla de verificación para asignar un nombre único a los archivos agregados como archivos adjuntos en los formularios adaptables y las comunicaciones interactivas. | No seleccionado | No aplicable |

## Configuración del tema del canal web de comunicaciones interactivas y formularios adaptables {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Pulse **Configuración del tema del canal web de comunicaciones interactivas y formularios adaptables** en la página **Configuración de la consola web de Adobe Experience Manager** para ver las propiedades de configuración de los temas del canal web de las comunicaciones interactivas y los formularios adaptables.

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
   <td>La lista de fuentes disponibles para usar durante la creación de los formularios adaptables y las comunicaciones interactivas.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impacto</p> <p>Palatino Linotype</p> </td> 
   <td>Todas las fuentes válidas del servidor de Adobe</td> 
  </tr> 
 </tbody> 
</table>
