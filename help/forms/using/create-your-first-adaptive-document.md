---
title: NO PUBLICAR Crear su primer documento adaptable
seo-title: DO NOT PUBLISH Create your first adaptive document
description: NO PUBLICAR
seo-description: DO NOT PUBLISH
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 17%

---


# NO PUBLICAR Crear su primer documento adaptable {#do-not-publish-create-your-first-adaptive-document}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Caso práctico {#use-case}

We Finance es una organización líder en el ámbito de los servicios financieros que ofrece soluciones financieras completas y personalizadas que se adaptan a las necesidades de diversos perfiles de clientes.

Una de las pólizas de seguro automático de sus clientes caduca y le envían un recordatorio, que es interactivo e incluye un PDF, con el presupuesto de renovación. La comunicación también incluye otra información, como recompensas por lealtad y ofertas de descuentos.

El portal funciona en AEM de Adobe. La salida del canal de bienvenida web e print se crea utilizando las capacidades multicanal de Adaptive Document.

Al final del tutorial, tendrá un documento adaptable similar al siguiente:
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)La creación del primer tutorial de documento adaptable se clasifica en pasos. Cada paso es un artículo completo en sí mismo.

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
     <li>Configuración AEM instancia de autor. </li> 
     <li>Instale los complementos para AEM Forms. Para obtener información detallada, consulte <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Instalación y configuración de AEM Forms</a>.</li> 
     <li>Obtenga el controlador de base de datos JDBC (archivo JAR) del proveedor de la base de datos. Los ejemplos del tutorial se basan en la base de datos MySQL y utilizan el Controlador de la base de datos JDBC de MySQL de Oracle. </li> 
     <li>Configure una base de datos que contenga datos de clientes. Una base de datos es esencial para crear un documento adaptable. Este tutorial utiliza una base de datos para mostrar el modelo de datos de formulario y las capacidades de persistencia de AEM Forms. </li> 
     <li>Crear/importar y habilitar <a href="/help/forms/using/web-channel-print-channel.md">Plantillas para impresión y canal web</a>.</li> 
     <li>Asegúrese de que tiene la variable <a href="/help/forms/using/document-fragments.md">Fragmentos de documento basados en FDM</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Paso 1: Crear un modelo de datos de formulario {#step-create-form-data-model}

Un modelo de datos de formulario permite conectar un documento adaptable a distintos orígenes de datos. Por ejemplo, un perfil de usuario de AEM, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Un modelo de datos de formulario es un esquema de representación de datos unificado de entidades y servicios empresariales disponibles en fuentes de datos conectadas. Puede utilizar el modelo de datos de formulario con un documento adaptable para recuperar datos de orígenes de datos conectados. Para obtener información sobre el modelo de datos de formulario, consulte [Integración de datos de AEM Forms](/help/forms/using/data-integration.md).

Objetivos:

* Configurar la instancia de base de datos (Microsoft Dynamics) como fuente de datos
* Creación del modelo de datos de formulario con Microsoft Dynamics como origen de datos
* Agregar objetos del modelo de datos al modelo de datos de formulario
* Configurar servicios de lectura y escritura para el modelo de datos de formulario
* Probar el modelo de datos de formulario y los servicios configurados con datos de prueba

## Paso 2: Creación de un documento adaptable {#step-create-an-adaptive-document}

Customer Communications centraliza y administra la creación, el ensamblaje y la entrega de correspondencia segura, personalizada e interactiva, como correspondencia comercial, cartas, documentos, declaraciones, avisos de beneficios, prospectos de gestión de riqueza, correos de marketing, facturas y kits de bienvenida.

Mediante documentos adaptables, puede crear comunicaciones con los clientes que sean atractivas, interactivas, dinámicas y adaptables. AEM Forms proporciona un editor WYSIWYG de arrastrar y soltar para crear documentos adaptables.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Objetivos:

* Cree impresión y salida web de un documento adaptable basado en el modelo de datos de formulario.
* Diseño de campos de un formulario adaptable para mostrar información al cliente
* Cree reglas para recuperar y mostrar información del modelo de datos de formulario a un documento adaptable.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Paso 3: Aplicación de reglas a campos de documento adaptables (solo canal web) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

El documento adaptable proporciona un editor para escribir reglas sobre objetos de documento adaptables. Estas reglas definen las acciones que se deben realizar en el déclencheur de los objetos de documento en función de las condiciones preestablecidas y las acciones que realice el usuario en el documento. Ayuda a garantizar la precisión y acelera la experiencia del usuario en la versión web del documento adaptable. Para obtener más información sobre las reglas de documentos adaptables y el editor de reglas, consulte [editor de reglas](/help/forms/using/rule-editor.md).

Objetivos:

* Creación y aplicación de reglas en los campos de canal web de un documento adaptable
* Usar reglas para el déclencheur de los servicios del modelo de datos de documentos en el canal web

## Paso 4: Estilo del documento adaptable (solo canal web) {#step-style-the-adaptive-document-web-channel-only}

Los documentos adaptables proporcionan un editor para crear temas para los documentos adaptables y el estilo en línea. Un tema contiene detalles de estilo para componentes y paneles, y puede reutilizar un tema en canales web de diferentes documentos. Los estilos incluyen propiedades como colores de fondo, colores de estado, transparencia, alineación y tamaño. Al aplicar el tema al documento, el estilo especificado se refleja en los componentes correspondientes del documento. Para obtener más información, consulte [Temáticas](/help/forms/using/themes.md).

Objetivos:

* Crear tema para el canal web del documento adaptable
* Aplicar tema al canal web del documento adaptable
* Validar la apariencia del canal web del documento adaptable en dispositivos móviles y equipos de escritorio

## Paso 5: Publicar el documento adaptable {#step-publish-the-adaptive-document}

Una vez que haya terminado de crear el documento adaptable, debe publicarlo para que esté disponible en la instancia de publicación, donde los agentes puedan utilizar el documento adaptable para crear las instancias de comunicación basadas en él.

Para publicar el documento adaptable, los autores de los documentos deben tener los permisos necesarios.
