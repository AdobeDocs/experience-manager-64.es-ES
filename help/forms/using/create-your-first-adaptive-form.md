---
title: Cree su primer formulario adaptable
seo-title: Cree su primer formulario adaptable
description: 'Aprenda a crear formularios interactivos, interactivos y de clase empresarial. '
seo-description: 'Aprenda a crear formularios interactivos, interactivos y de clase empresarial. '
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---


# Cree su primer formulario adaptable {#do-not-publish-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Introducción {#introduction}

¿Está buscando una experiencia de **formularios** fácil de usar para móviles que simplifique la inscripción, aumente la participación y reduzca el tiempo de respuesta, **formularios adaptables** es la solución perfecta para usted. Los formularios adaptables proporcionan una experiencia de formularios adaptable para móviles, de automatización y de análisis. Puede crear fácilmente formularios que sean interactivos e interactivos, utilizar procesos automatizados para reducir las tareas administrativas y repetitivas y utilizar el análisis de datos para mejorar y personalizar la experiencia que los clientes tienen con sus formularios.

Este tutorial proporciona un marco de trabajo completo para crear un formulario adaptable. El tutorial está organizado en un caso de uso y en varias guías. Cada guía le ayuda a aprender y añadir nuevas funciones al formulario adaptable que se crea en este tutorial. Después de cada guía, tiene un formulario adaptable en funcionamiento. La guía para crear un formulario adaptable está disponible. Próximamente habrá guías disponibles. Al final de este tutorial, podrá:

* Cree un formulario adaptable y un modelo de datos de formulario.
* Establezca el estilo de su formulario adaptable.
* Utilice el editor de reglas de formulario adaptable para crear reglas comerciales.
* Prueba y publicación de un formulario adaptable.

![create-dynamic-form-workflow](assets/create-daptive-form-workflow.png)

El recorrido comienza con el aprendizaje del caso de uso:

Un sitio web ofrece una amplia gama de productos para diversos clientes. Los clientes navegan por el portal, seleccionan y solicitan los productos. Cada cliente crea una cuenta y proporciona direcciones de envío y facturación. Una cliente existente, Sara Rose, está buscando añadir su dirección de envío al sitio web. El sitio web proporciona un formulario en línea para agregar y actualizar las direcciones de envío.

El sitio web se ejecuta en Adobe Experience Manager (AEM) y utiliza AEM Forms para la captura y el procesamiento de datos. El formulario de adición y actualización de direcciones es un formulario adaptable. El sitio web almacena los detalles del cliente en una base de datos. Utilizan el formulario de adición y actualización de direcciones para recuperar y mostrar las direcciones disponibles. También utilizan el formulario adaptable para aceptar direcciones nuevas y actualizadas.

### Requisitos previos {#prerequisite}

* Configure una instancia de autor AEM.
* Instale [Complemento de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) en la instancia de autor.
* Obtenga el controlador de base de datos JDBC (archivo JAR) del proveedor de la base de datos. Algunos ejemplos del tutorial se basan en la base de datos MySQL y utilizan el [controlador de base de datos JDBC de MySQL](https://dev.mysql.com/downloads/connector/j/5.1.html) del Oracle.

* Configure una base de datos que contenga datos de clientes con los campos que se muestran a continuación. Una base de datos no es esencial para crear un formulario adaptable. Este tutorial utiliza una base de datos para mostrar el modelo de datos de formulario y las capacidades de persistencia de AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Paso 1: Crear un formulario adaptable {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Los formularios adaptables son de nueva generación, atractivos, interactivos, dinámicos y adaptables. Con los formularios adaptables, puede ofrecer experiencias personalizadas y segmentadas. AEM Forms proporciona un editor WYSIWYG de arrastrar y soltar para crear formularios adaptables. Para obtener más información sobre los formularios adaptables, consulte [Introducción a la creación de formularios adaptables](/help/forms/using/introduction-forms-authoring.md).

Objetivos:

* Crear un formulario adaptable que permita a un cliente añadir una dirección de envío
* Diseño de campos de un formulario adaptable para mostrar y aceptar información de un cliente
* Cree una acción de envío para enviar un correo electrónico que contenga contenido de formulario
* Vista previa y envío de un formulario adaptable

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](create-adaptive-form.md)

## Paso 2: Crear modelo de datos de formulario {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Un modelo de datos de formulario permite conectar un formulario adaptable a distintos orígenes de datos. Por ejemplo, AEM perfil de usuario, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Un modelo de datos de formulario es un esquema de representación de datos unificado de entidades y servicios empresariales disponibles en fuentes de datos conectadas. Puede utilizar el modelo de datos de formulario con un formulario adaptable para recuperar, actualizar, eliminar y agregar datos a orígenes de datos conectados.

Objetivos:

* Configurar la instancia de base de datos del sitio web (base de datos MySQL) como fuente de datos
* Crear el modelo de datos de formulario utilizando la base de datos MySQL como origen de datos
* Agregar objetos del modelo de datos al modelo de datos de formulario
* Configuración de servicios de lectura y escritura para el modelo de datos de formulario
* Probar el modelo de datos de formulario y los servicios configurados con datos de prueba

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](create-form-data-model.md)

## Paso 3: Aplicar reglas a campos de formulario adaptables {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Los formularios adaptables proporcionan un editor para escribir reglas sobre objetos de formulario adaptables. Estas reglas definen las acciones que se deben realizar en el déclencheur de los objetos de formulario en función de las condiciones preestablecidas, las entradas del usuario y las acciones del usuario en el formulario. Ayuda a garantizar la precisión y acelera la experiencia de cumplimentación de formularios.

Objetivos:

* Creación y aplicación de reglas en campos de formulario adaptables
* Utilice reglas para el déclencheur de los servicios del modelo de datos de formulario para actualizar los datos a la base de datos

## Paso 4: Estile el formulario adaptable {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

Los formularios adaptables proporcionan temas y un [editor](/help/forms/using/themes.md) para crear temas para los formularios adaptables. Un tema contiene detalles de estilo para componentes y paneles, y se puede reutilizar un tema en distintos formularios. Los estilos incluyen propiedades como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar el tema al formulario, el estilo especificado se refleja en los componentes correspondientes del formulario. Los formularios adaptables también admiten el estilo en línea para estilos específicos de un formulario.

Objetivos:

* Aplicar un tema preestablecido a un formulario adaptable
* Creación de un tema para un formulario adaptable mediante el editor de temas
* Usar fuentes web en un tema personalizado

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Paso 5: Pruebe el formulario adaptable {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Los formularios adaptables son integrales en las interacciones de los clientes. Es importante probar los formularios adaptables con cada cambio que realice en ellos. La prueba de cada campo de un formulario es tediosa. AEM Forms proporciona un SDK (SDK de Calvin) para automatizar las pruebas de formularios adaptables. Calvin le permite automatizar las pruebas de sus formularios adaptables en el explorador web.

Objetivos:

* Instalación del SDK de Calvin
* Crear grupo de pruebas y formularios de prueba para cambiar dirección

Para obtener más información sobre el SDK, consulte [Uso de pruebas automatizadas con AEM formulario adaptable](/help/forms/using/calvin.md).

## Paso 6: Publicar el formulario adaptable {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Puede publicar formularios adaptables como un formulario independiente (aplicación de una sola página), incluir en AEM [página de sitios](/help/forms/using/embed-adaptive-form-aem-sites.md) o enumerar en un sitio AEM utilizando [Forms Portal](/help/forms/using/introduction-publishing-forms.md).

Objetivos:

* Publicar el formulario adaptable como una aplicación de una sola página

