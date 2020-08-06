---
title: Resumen de las nuevas funciones | AEM 6.4 Forms
seo-title: Resumen de las nuevas funciones | AEM 6.4 Forms
description: Resumen de las nuevas funciones y mejoras de AEM 6.4 Forms.
seo-description: Resumen de las nuevas funciones y mejoras de AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 0%

---


# Resumen de las nuevas funciones | AEM 6.4 Forms {#new-features-summary-aem-forms}

Resumen de las nuevas funciones y mejoras de AEM 6.4 Forms.

AEM Forms incluye varias funciones y mejoras nuevas que simplifican aún más la creación, la gestión y las experiencias de los usuarios con formularios adaptables y comunicaciones interactivas.

Continúe leyendo para obtener una introducción rápida a las nuevas funciones y mejoras. Visite la documentación de recursos para obtener detalles. Consulte también las notas de [la versión](/help/release-notes/forms.md)de Forms de AEM 6.4. Para obtener la documentación completa de AEM 6.4 para Forms, visite [AEM Guía](/help/forms/home.md)del usuario de Forms 6.4.

## Comunicaciones interactivas {#interactive-communications}

![gestión de correspondencia](assets/correspondence-management.png)

Interactive Communications centraliza y gestiona la creación, el ensamblaje y el envío de correspondencia segura, personalizada e interactiva, como correspondencia comercial, cartas, documentos, declaraciones, avisos de beneficios, prospectos de gestión patrimonial, correos electrónicos de marketing, facturas y kits de bienvenida.

Interactive Communications utiliza la misma tecnología, procesos y componentes subyacentes que los formularios adaptables para crear comunicaciones interactivas de varios canales, como los formularios adaptables interactivos.

ofertas de comunicación interactiva ventajas significativas:

* Proporciona integración de OOTB con el modelo de datos de formulario para permitir un acceso fácil y optimizado a las bases de datos back-end y a otros sistemas CRM como MS Dynamics
* Proporciona una interfaz de creación integrada para canales web e impresos
* Proporciona una interfaz de creación basada en la función de arrastrar y soltar, similar a la creación de Forms adaptable, tanto para canales web como de impresión.

La comunicación interactiva es el método predeterminado y recomendado para crear comunicaciones con los clientes. Para seguir utilizando las letras de AEM 6.3 Forms y AEM 6.2 Forms, debe instalar un paquete de compatibilidad.

### Creación de comunicaciones interactivas con varios canales {#multi-channel-interactive-communication-authoring}

Mediante la comunicación interactiva, puede crear y editar documentos impresos y Web desde un único editor de documento. Al utilizar los mismos fragmentos de documento para generar representaciones de ambos canales, puede eliminar la duplicación de esfuerzos.
![printweb_2](assets/printweb_2.png)

Para obtener más información, consulte Información general sobre comunicaciones [interactivas](/help/forms/using/interactive-communications-overview.md).

### Editor de Documentos WYSIWYG {#wysiwyg-document-editor}

El editor de documentos de arrastrar y soltar WYSIWYG es práctico para el negocio. La interfaz intuitiva, la funcionalidad de arrastrar y soltar, los componentes estándar, los modelos de datos y el repositorio integrado para los recursos facilitan la creación rápida y sencilla de comunicaciones interactivas.

Para crear una comunicación interactiva o editar una existente, los usuarios empresariales pueden utilizar los siguientes componentes: Canales, Contenido, Propiedades, Recursos, Componentes y Fuentes de datos.

![arrastrar-n-soltar-lf](assets/drag-n-drop-lf.png)

Para obtener más información, consulte [Introducción a la creación de comunicación](/help/forms/using/introduction-interactive-communication-authoring.md)interactiva.

### Generar automáticamente una versión web a partir de contenido impreso en comunicación interactiva {#auto-generate-web-version-from-print-content-in-interactive-communication}

Los autores pueden generar automáticamente contenido de documento web desde documentos de impresión hasta creación, previsualización y edición de documentos impresos y web en el mismo editor. Los autores de comunicaciones interactivas pueden crear una sola vez y publicar en todos los canales. Los autores de comunicaciones interactivas pueden utilizar los mismos fragmentos de documento en la impresión y el canal web para evitar la duplicación de esfuerzos.

Para obtener más información, consulte [Imprimir canal y canal](/help/forms/using/web-channel-print-channel.md)web.

### Usar temáticas para aplicar estilo al canal web de comunicación interactiva {#use-themes-to-style-web-channel-of-interactive-communication}

La comunicación interactiva admite temáticas. Puede crear temáticas y aplicarlas a la comunicación interactiva. Un tema contiene detalles de estilo para componentes y paneles. Puede reutilizar un tema en diferentes comunicaciones interactivas para darles un aspecto y una marca comunes y coherentes.

AEM Forms incluye un tema inicial para las comunicaciones interactivas. Con un tema, también puede personalizar el aspecto de una comunicación interactiva en un dispositivo.

Para obtener más información, consulte [Temáticas en AEM Forms](/help/forms/using/themes.md).

### Interfaz de agente mejorada {#enhanced-agent-interface}

La interfaz de usuario del agente ahora admite la impresión y la previsualización web de la comunicación interactiva. Desde la misma interfaz de usuario del agente, puede elegir editar el canal de impresión y el canal web de previsualización de la comunicación interactiva de varios canales. Los campos, variables, elementos FDM y fragmentos de documento del canal de impresión se pueden configurar para que el agente los modifique en la interfaz de usuario del agente. La compatibilidad del modelo de datos de formulario le permite generar previsualizaciones con datos de ejemplo rellenados previamente.

Para obtener más información, consulte [Preparación y envío de comunicación interactiva mediante la interfaz de usuario](/help/forms/using/prepare-send-interactive-communication.md)del agente.

### Presentar información en gráficos {#present-information-in-charts}

La comunicación interactiva admite gráficos en la Web y el canal de impresión para comunicaciones más enriquecidas. Mediante gráficos como circular, circular, barra y columna, puede condensar y presentar visualmente grandes cantidades de información para facilitar la interpretación y la análisis.

![gráfico 2](assets/chart-2.png) ![gráfico](assets/chart.png)

Para obtener más información, consulte [Uso de gráficos en Interactive Communications](/help/forms/using/chart-component-interactive-communications.md).

### Conectores de datos listos para usar para rellenar documentos {#out-of-the-box-data-connectors-to-prefill-documents}

La comunicación interactiva proporciona integración de datos con herramientas empresariales para conectarse con varios sistemas empresariales, incluidos sistemas CRM, y personalizar datos en documentos.

![fdm_ad](assets/fdm_ad.png)

Para obtener más información, consulte [Uso del modelo](/help/forms/using/using-form-data-model.md)de datos de formulario.

### Editor de fragmentos de documento mejorado {#enhanced-document-fragment-editor}

Ahora puede utilizar elementos y reglas FDM dentro de fragmentos de documento de comunicación interactiva.

* Compatibilidad con elementos del modelo de datos de formulario
* Mostrar u ocultar un recurso o fragmento de texto mediante reglas
* Validar el valor de un elemento o variable
* Ejecutar funciones para calcular el valor de una expresión matemática

Para obtener más información, consulte:

* [Textos en comunicaciones interactivas](/help/forms/using/texts-interactive-communications.md)
* [Condiciones de las comunicaciones interactivas](/help/forms/using/conditions-interactive-communications.md)

### Paquete de compatibilidad para recursos existentes {#compatibility-package-for-existing-assets}

De forma predeterminada, los recursos de letras de las versiones anteriores de AEM Forms no son compatibles con esta versión. Si desea seguir utilizando las letras de AEM 6.3 Forms y AEM 6.2 Forms, debe instalar el paquete de compatibilidad.

## Integración de datos {#data-integration}

![](do-not-localize/data-integeration-1.png)

[La integración](/help/forms/using/data-integration.md) de datos de AEM Forms permite configurar orígenes de datos dispares; como bases de datos, servicios web basados en RESTful o SOAP y servicios OData; para crear un modelo de datos de formulario que puede utilizar para enlazar datos, rellenar previamente e invocar servicios en formularios y documentos adaptables.

Esta versión incorpora varias funciones y mejoras nuevas en la integración de datos.

### Crear modelo de datos de formulario sin origen de datos {#create-form-data-model-without-data-source}

Los usuarios empresariales y los autores de formularios ahora pueden crear un modelo de datos de formulario que incluya sus entidades y propiedades sin configurar un origen de datos, y se puede utilizar para crear formularios y documentos adaptables. Puede enlazar el modelo de datos de formulario a orígenes de datos más adelante. Elimina la dependencia de los orígenes de datos para crear formularios y documentos mediante el modelo de datos de formulario.

Del mismo modo, puede crear entidades y propiedades secundarias en un modelo de datos de formulario existente y enlazarlas a las entidades y propiedades correspondientes en un origen de datos más adelante.

Para obtener más información, consulte [Creación de un modelo](/help/forms/using/create-form-data-models.md)de datos de formulario.

### Crear propiedades calculadas {#create-computed-properties}

Los autores y desarrolladores de Forms pueden crear propiedades calculadas en el modelo de datos de formulario. Permiten calcular un valor para la propiedad mediante la creación de reglas o lógica en los datos disponibles en orígenes de datos configurados. Una regla es una expresión que se evalúa cuando los datos se cargan en el modelo de datos de formulario o cuando cambian los valores de las propiedades de la expresión. Por ejemplo, una propiedad calculada denominada Installments calcula el importe mensual que se pagará por un préstamo según el tipo de interés especificado en el origen de datos y el importe y la tenencia del préstamo especificados por el usuario en el formulario.

Una propiedad calculada reside localmente en un modelo de datos de formulario y no existe en un origen de datos. Puede utilizar propiedades calculadas en formularios adaptables y comunicaciones interactivas.

Para obtener más información, consulte [Trabajo con el modelo](/help/forms/using/work-with-form-data-model.md)de datos de formulario.

### formularios y documentos de Previsualización con datos de ejemplo {#preview-forms-and-documents-with-sample-data}

El modelo de datos de formulario permite generar datos de ejemplo para propiedades de todas las entidades en un modelo de datos de formulario. Los datos generados corresponden a los tipos de datos configurados para las propiedades. Cuando se previsualización un formulario o un documento adaptable asociado al modelo de datos de formulario, se procesa con datos de ejemplo rellenados previamente.

Los datos de ejemplo son un conjunto de valores aleatorios que cambian cada vez que se generan. Sin embargo, puede editar y guardar los datos de ejemplo que persisten incluso si los vuelve a generar. Por ejemplo, si edita y guarda los datos de ejemplo para las propiedades Nombre y Apellido y posteriormente agrega otra propiedad o entidad en el modelo de datos de formulario y vuelve a generar los datos de ejemplo, las propiedades Nombre y Apellido mostrarán los valores guardados mientras se regeneran los valores de otras propiedades.

Para obtener más información, consulte [Uso del modelo](/help/forms/using/using-form-data-model.md)de datos de formulario.

### Refresh data source definitions {#refresh-data-source-definitions}

Cualquier actualización en propiedades o entidades de origen de datos no se refleja automáticamente en los modelos de datos de formulario asociados. El editor de modelos de datos de formulario ahora incluye ![refresh_forms_di](assets/refresh_forms_di.png) (Actualizar definiciones de fuentes de datos) que invalida la caché del servidor y obtiene el esquema actualizado del origen de datos para que se refleje inmediatamente en el modelo de datos de formulario.

### Configuración de fuentes de datos mediante la interfaz de usuario táctil {#configure-data-sources-using-touch-user-interface}

Con esta versión, la configuración de servicios en la nube para fuentes de datos está disponible en la interfaz de usuario táctil. Además, la ubicación para configurar los servicios en la nube ha cambiado a **[!UICONTROL Herramientas > Cloud Services > Fuentes]** de datos. See [Configure data sources](/help/forms/using/configure-data-sources.md).

## Formularios adaptables {#adaptive-forms}

![simplificación-de-creación-formularios-y-documentos_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### Mejorar el rendimiento de los formularios adaptables con una carga diferida mejorada {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

La funcionalidad de carga diferida en formularios adaptables retrasa la inicialización de fragmentos de formulario hasta que se necesitan. Mejora el rendimiento de los formularios grandes al minimizar el tiempo necesario para procesar un formulario, lo que mejora la experiencia del usuario.

Esta versión incorpora varias mejoras en la función de carga diferida:

* Los componentes Datos adjuntos de archivo y Términos y condiciones se admiten en fragmentos de formulario con la carga diferida activada.
* Los fragmentos de formulario adaptables con la carga diferida activada se admiten en los paneles repetitivos.
* Los formularios adaptables con fragmentos habilitados para la carga diferida son compatibles con la aplicación de AEM Forms.

## Flujos de trabajo de AEM centrados en Forms {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Con la funcionalidad de Flujos de trabajo de AEM centrados en Forms, puede crear e implementar rápidamente flujos de trabajo para diversas tareas en la pila OSGi. Ya no es necesario instalar la capacidad de administración de procesos disponible en la pila JEE, lo que simplifica la implementación y elimina los costos de infraestructura y servidor de aplicaciones. Para obtener más información, consulte flujos de trabajo centrados en [Forms en OSGi](/help/forms/using/aem-forms-workflow.md).

Las siguientes son las mejoras en los Flujos de trabajo de AEM centrados en Forms: ・

* El editor de modelos de flujo de trabajo está disponible en la interfaz de usuario táctil. Ayuda a reducir el tiempo necesario para crear Flujos de trabajo de AEM centrados en el formulario.
* Paso del flujo de trabajo para enviar correos electrónicos. Por ejemplo, puede utilizar el paso de correo electrónico para enviar un documento de registro al finalizar un flujo de trabajo.
* Paso del flujo de trabajo para utilizar los servicios del modelo de datos de formulario en un modelo de flujo de trabajo. Este paso le permite invocar servicios de integración de datos sin escribir ningún código personalizado. Por ejemplo, puede invocar un servicio de GET para obtener los detalles de un empleado de los archivos de una base de datos sin escribir ningún código personalizado.

## Aplicación de AEM Forms {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

La aplicación de AEM Forms permite a los trabajadores de campo sincronizar sus dispositivos móviles con un servidor AEM Forms y trabajar en sus formularios. La aplicación funciona perfectamente cuando el dispositivo está sin conexión, al guardar datos localmente en el dispositivo y sincronizar los datos con el servidor cuando el dispositivo vuelve a estar en línea. Para obtener más información, consulte Aplicación [AEM Forms](/help/forms/using/aem-forms-app.md).

A continuación se indican las mejoras en la aplicación de AEM Forms:

* Los formularios adaptables con fragmentos habilitados para la carga diferida son compatibles con la aplicación de AEM Forms.
* Los formularios adaptables con modelo de datos de formulario son compatibles con la aplicación de AEM Forms.

## :Seguridad de los documentos{#document-security}

![aem-forms-documento-security-](assets/aem-forms-document-security-.png)

Con la seguridad de documento, puede distribuir con seguridad cualquier información que haya guardado en un formato compatible. La seguridad de Documento garantiza que solo los usuarios autorizados puedan utilizar sus documentos. A continuación se indican los principales cambios en la seguridad de los documentos:

* La seguridad de Documento proporciona una biblioteca de protección [portátil (PPL)](/help/forms/using/document-security-offerings.md) para proteger un documento localmente, sin enviar el documento al servidor de AEM Forms. Sólo las credenciales de seguridad y los detalles de directivas se desplazan por la red al servidor de AEM Forms. AEM 6.4 Forms ha introducido Portable Protection Library (PPL) en un formato de paquete OSGi. Ahora, puede instalar directamente la biblioteca PPL en un servidor AEM Forms y utilizar las capacidades de AEM y PPL en conjunto.
* El SDK de seguridad de Documento C++ y la biblioteca PPL de C++ se pueden compilar con Microsoft Visual Studio 2013. La versión admitida anteriormente era Microsoft Visual Studio 2010.

## Plataformas compatibles {#supported-platforms}

AEM Forms se puede configurar mediante cualquier combinación de sistemas operativos admitidos, servidores de aplicaciones, bases de datos, controladores de base de datos, JDK, servidores LDAP y servidores de correo electrónico. Los siguientes son los principales cambios en las plataformas admitidas:

<table> 
 <tbody> 
  <tr> 
   <td>Componente</td> 
   <td>Compatibilidad Añadida</td> 
   <td>Compatibilidad eliminada</td> 
  </tr> 
  <tr> 
   <td>Sistemas operativos</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Oracle Linux 7 Actualización 3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores de aplicaciones<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Bases de datos</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 y posterior</li> 
     <li>IBM DB2 11.1</li> 
     <li>Arquitectura multiinquilina de Oracle</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores LDAP</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle Directory Server Enterprise Edition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Servidores de correo electrónico</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Conectores</td> 
   <td> 
    <ul> 
     <li>Conector para Microsoft Sharepoint 2016</li> 
     <li>Connector for EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Conector para Microsoft Sharepoint 2007</li> 
     <li>Conector para Microsoft Sharepoint 2010</li> 
     <li>Conector para IBM Filenet 5.0</li> 
     <li>Connector for EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Exploradores</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x en macOS</li> 
     <li>Apple Safari 11.x en iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Navegador Blackberry para dispositivos Blackberry Z30 y Q10</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms app<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 o superior</li> 
     <li>Apple iOS 10 o superior</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. Los sistemas operativos AIX y Solaris solo están disponibles para clientes de actualización.
