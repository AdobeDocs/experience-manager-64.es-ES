---
title: NO PUBLICAR Cree el primer documento adaptable
seo-title: NO PUBLICAR Cree el primer documento adaptable
description: nulo
seo-description: nulo
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# NO PUBLICAR Cree el primer documento adaptable {#do-not-publish-create-your-first-adaptive-document}

## Caso práctico  {#use-case}

We Finance es una organización líder en el ámbito de los servicios financieros que ofrece soluciones financieras completas y personalizadas para satisfacer las necesidades de los distintos perfiles de los clientes.

Una de las pólizas de seguro automático de sus clientes está caducando y le están enviando un recordatorio, que es interactivo e incluye un PDF, con el presupuesto de renovación. La comunicación también incluye otra información, como recompensas por lealtad y ofertas de descuentos.

El portal se ejecuta en Adobe AEM. La salida del canal de bienvenida web e impresa se crea utilizando las funciones multicanal de Documento adaptable.

Al final del tutorial tendrá un documento adaptable similar al siguiente:
[ ad-1 ![](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf) ad-2 [ ![](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)La creación del primer tutorial de documento adaptable se categoriza en pasos. Cada paso es un artículo completo en sí mismo.

<table> 
 <tbody>
  <tr>
   <th>Aprenderá</th> 
   <th>
    <ul> 
     <li>Creación de un documento adaptable y un modelo de datos de formulario.</li> 
     <li>Creación de plantillas y temas para documentos adaptables.</li> 
     <li>Uso del editor de reglas para crear reglas comerciales.<br /> </li> 
     <li>Publicación de un documento adaptable. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>Requisitos previos</td> 
   <td>
    <ul> 
     <li>Configure la instancia de creación de AEM. </li> 
     <li>Instale los complementos para AEM Forms. Para obtener información detallada, consulte <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Instalación y configuración de AEM Forms</a>.</li> 
     <li>Obtenga el controlador de base de datos JDBC (archivo JAR) del proveedor de base de datos. Los ejemplos del tutorial se basan en la base de datos MySQL y utilizan el controlador de base de datos JDBC MySQL de Oracle. </li> 
     <li>Configure una base de datos que contenga datos del cliente. Una base de datos es esencial para crear un documento adaptable. Este tutorial utiliza una base de datos para mostrar el modelo de datos de formulario y las capacidades de persistencia de AEM Forms. </li> 
     <li>Cree/importe y habilite <a href="/help/forms/using/web-channel-print-channel.md">Plantillas para impresión y canal</a>web.</li> 
     <li>Asegúrese de que tiene los fragmentos <a href="/help/forms/using/document-fragments.md">de documento basados en FDM</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Step 1: Create Form Data Model {#step-create-form-data-model}

Un modelo de datos de formulario permite conectar un documento adaptable a orígenes de datos dispares. Por ejemplo, perfil de usuario de AEM, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Un modelo de datos de formulario es un esquema de representación de datos unificado de entidades comerciales y servicios disponibles en orígenes de datos conectados. Puede utilizar el modelo de datos de formulario con un documento adaptable para recuperar datos de orígenes de datos conectados. Para obtener más información sobre el modelo de datos de formulario, consulte Integración [de datos de formularios](/help/forms/using/data-integration.md)AEM.

Objetivos:

* Configurar instancia de base de datos (Microsoft Dynamics) como fuente de datos
* Crear el modelo de datos de formulario con Microsoft Dynamics como origen de datos
* Agregar objetos de modelo de datos al modelo de datos de formulario
* Configuración de servicios de lectura y escritura para el modelo de datos de formulario
* Probar el modelo de datos de formulario y los servicios configurados con datos de prueba

## Paso 2: Creación de un documento adaptable {#step-create-an-adaptive-document}

Las comunicaciones con el cliente centralizan y gestionan la creación, el montaje y la entrega de correspondencia segura, personalizada e interactiva, como correspondencia comercial, cartas, documentos, declaraciones, avisos de beneficios, folleto de gestión de riqueza, correos electrónicos de marketing, facturas y kits de bienvenida.

Mediante documentos adaptables, puede crear comunicaciones con los clientes que sean atractivas, adaptables, dinámicas y adaptables. AEM Forms proporciona un editor WYSIWYG de arrastrar y soltar para crear documentos adaptables.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Objetivos:

* Crear impresión y salida web de un documento adaptable basado en un modelo de datos de formulario.
* Campos de diseño de un formulario adaptable para mostrar información al cliente
* Cree reglas para recuperar y mostrar información del modelo de datos de formulario a un documento adaptable.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Paso 3: Aplicación de reglas a campos de documento adaptables (solo canal Web) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

El documento adaptable proporciona un editor para escribir reglas en objetos de documento adaptables. Estas reglas definen acciones para activar objetos de documento en función de las condiciones preestablecidas y las acciones del usuario en el documento. Ayuda a garantizar la precisión y acelera la experiencia del usuario en la versión web del documento adaptable. Para obtener más información sobre las reglas de documentos adaptables y el editor de reglas, consulte [Editor](/help/forms/using/rule-editor.md)de reglas.

Objetivos:

* Crear y aplicar reglas a los campos de canal web de un documento adaptable
* Usar reglas para activar servicios de modelo de datos de documentos en el canal web

## Paso 4: Estilo del documento adaptable (solo canal Web) {#step-style-the-adaptive-document-web-channel-only}

Los documentos adaptables proporcionan un editor para crear temas para los documentos adaptables y el estilo en línea. Un tema contiene detalles de estilo para componentes y paneles, y puede reutilizar un tema en canales web de diferentes documentos. Los estilos incluyen propiedades como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar el tema al documento, el estilo especificado se refleja en los componentes correspondientes del documento. For more information, see [Themes](/help/forms/using/themes.md).

Objetivos:

* Crear tema para el canal web de documentos adaptables
* Aplicar tema al canal web de documentos adaptables
* Validar la apariencia del canal web de documentos adaptables en dispositivos móviles y equipos de escritorio

## Paso 5: Publicación del documento adaptable {#step-publish-the-adaptive-document}

Una vez creado el documento adaptable, debe publicarlo para que esté disponible en la instancia de publicación, donde los agentes podrían utilizar el documento adaptable para crear las instancias de comunicación basadas en él.

Para publicar el documento adaptable, los autores de los documentos deben tener los permisos necesarios.
