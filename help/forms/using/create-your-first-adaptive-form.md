---
title: Creación de su primer formulario adaptable
seo-title: Create your first adaptive form
description: Aprenda a crear formularios interactivos, adaptables y de clase empresarial.
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 74%

---

# Creación de su primer formulario adaptable {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Introducción {#introduction}

Si busca una **experiencia de formularios** adaptada a dispositivos móviles que simplifique la inscripción, aumente la participación y reduzca el tiempo de respuesta, los **formularios adaptables** son perfectos para usted. Los formularios adaptables proporcionan una experiencia adaptada para móviles, automatizada y analítica. Puede crear fácilmente formularios que sean interactivos e interactivos, utilizar procesos automatizados para reducir las tareas administrativas y repetitivas y utilizar el análisis de datos para mejorar y personalizar la experiencia que los clientes tienen con sus formularios.

Este tutorial proporciona un marco de trabajo completo para crear un formulario adaptable. El tutorial está organizado en un caso de uso y en varias guías. Cada guía le ayuda a aprender y agregar nuevas características al formulario adaptable que cree en este tutorial. Después de cada guía, tendrá un formulario adaptable operativo. La guía para crear un formulario adaptable está disponible. Próximamente habrá más guías disponibles. Al final de este tutorial, podrá:

* Crear un formulario adaptable y un modelo de datos de formulario.
* Establecer el estilo de su formulario adaptable.
* Utilizar el editor de reglas de formulario adaptable para crear reglas empresariales.
* Probar y publicar un formulario adaptable.

![create-dynamic-form-workflow](assets/create-daptive-form-workflow.png)

El recorrido comienza con el aprendizaje del caso de uso:

Un sitio web ofrece una amplia gama de productos para diversos clientes. Los clientes examinan el portal, seleccionan y solicitan los productos. Cada cliente crea una cuenta y proporciona direcciones de envío y de facturación. Una cliente, Sara Rose, quiere agregar su dirección de envío al sitio web. El sitio web proporciona un formulario en línea para agregar y actualizar las direcciones de envío.

El sitio web se ejecuta en Adobe Experience Manager (AEM) y utiliza AEM Forms para la captura y el procesamiento de datos. El formulario de adición y actualización de direcciones es un formulario adaptable. El sitio web almacena los detalles del cliente en una base de datos. Se utiliza el formulario de adición y actualización de direcciones para recuperar y mostrar las direcciones disponibles. También se utiliza el formulario adaptable para aceptar direcciones nuevas y actualizadas.

### Requisitos previos {#prerequisite}

* Configurar una instancia de autor de AEM.
* Instalar el [Complemento de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) en la instancia de autor.
* Obtenga el controlador de base de datos JDBC (archivo JAR) del proveedor de la base de datos. Los ejemplos del tutorial se basan en la base de datos MySQL y utilizan el [Controlador de la base de datos JDBC de MySQL](https://dev.mysql.com/downloads/connector/j/5.1.html) de Oracle.

* Configure una base de datos que contenga datos de clientes con los campos que se muestran a continuación. Una base de datos no es esencial para crear un formulario adaptable. Este tutorial utiliza una base de datos para mostrar el modelo de datos de formulario y las capacidades de persistencia de AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Paso 1: Crear un formulario adaptable {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Los formularios adaptables son de nueva generación, atractivos, interactivos, dinámicos y adaptables. Gracias a los formularios adaptables, puede ofrecer experiencias personalizadas y segmentadas. AEM Forms proporciona un editor WYSIWYG de arrastrar y soltar para crear formularios adaptables. Para obtener más información sobre los formularios adaptables, consulte [Introducción a la creación de formularios adaptables](/help/forms/using/introduction-forms-authoring.md).

Objetivos:

* Crear un formulario adaptable que permita a un cliente agregar una dirección de envío
* Diseñar campos de un formulario adaptable para mostrar y aceptar información de un cliente
* Crear una acción de envío para enviar un correo electrónico que contenga contenido de formulario
* Previsualizar y enviar un formulario adaptable

[ ](create-adaptive-form.md)

## Paso 2: Crear un modelo de datos de formulario {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Un modelo de datos de formulario permite conectar un formulario adaptable a distintas fuentes de datos. Por ejemplo, un perfil de usuario de AEM, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Un modelo de datos de formulario es un esquema de representación de datos unificado de entidades y servicios empresariales disponibles en fuentes de datos conectadas. Puede utilizar el modelo de datos de formulario con un formulario adaptable para recuperar, actualizar, eliminar y agregar datos a fuentes de datos conectadas.

Objetivos:

* Configurar la instancia de base de datos del sitio web (base de datos MySQL) como fuente de datos
* Crear el modelo de datos de formulario con la base de datos MySQL como fuente de datos
* Agregar objetos del modelo de datos al modelo de datos de formulario
* Configurar servicios de lectura y escritura para el modelo de datos de formulario
* Probar el modelo de datos de formulario y los servicios configurados con datos de prueba

[ ](create-form-data-model.md)

## Paso 3: Aplicar reglas a campos de formulario adaptables {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Los formularios adaptables proporcionan un editor para escribir reglas sobre objetos de formulario adaptables. Estas reglas definen las acciones que se deben habilitar en los objetos del formulario en función de los ajustes preestablecidos, las entradas del usuario y las acciones del usuario en el formulario. Ayuda a garantizar la precisión y acelera la experiencia de cumplimentación de formularios.

Objetivos:

* Crear y aplicar reglas en campos de formularios adaptables
* Utilice reglas para habilitar servicios del modelo de datos de formulario para actualizar los datos a la base de datos

## Paso 4: Estilo del formulario adaptable {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

Los formularios adaptables proporcionan temáticas y un [editor](/help/forms/using/themes.md) para crear temáticas para los formularios adaptables. Una temática contiene detalles de estilo para componentes y paneles y se puede reutilizar el mismo en distintos formularios. Los estilos incluyen propiedades como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar la temática al formulario, el estilo especificado se reflejará en los componentes correspondientes del formulario. Los formularios adaptables también admiten el estilo en línea para estilos específicos de un formulario.

Objetivos:

* Aplicar una temática predeterminada a un formulario adaptable
* Crear una temática para un formulario adaptable mediante el editor de temáticas
* Usar fuentes web en una temática personalizada

[ ](style-your-adaptive-form.md)

## Paso 5: Probar el formulario adaptable {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Los formularios adaptables son integrales en las interacciones de los clientes. Es importante probar los formularios adaptables con cada cambio que realice en ellos. La prueba de cada campo de un formulario es tediosa. AEM Forms proporciona un SDK (SDK de Calvin) para automatizar las pruebas de formularios adaptables. Calvin le permite automatizar las pruebas de sus formularios adaptables en el explorador web.

Objetivos:

* Instalación del SDK de Calvin
* Crear grupo de pruebas y formularios de prueba para cambiar dirección

Para obtener más información sobre SDK, consulte [Uso de pruebas automatizadas con AEM formulario adaptable](/help/forms/using/calvin.md).

## Paso 6: Publicar el formulario adaptable {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Puede publicar formularios adaptables como un formulario independiente (aplicación de una sola página), incluido en AEM [página Sitios](/help/forms/using/embed-adaptive-form-aem-sites.md)o una lista en un sitio AEM usando [Portal de Forms](/help/forms/using/introduction-publishing-forms.md).

Objetivos:

* Publicar el formulario adaptable como una aplicación de una sola página
