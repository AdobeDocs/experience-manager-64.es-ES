---
title: '“Tutorial: Crear un modelo de datos de formulario”'
seo-title: Create Form Data Model Tutorial
description: El módulo de integración de datos de AEM Forms le permite crear un modelo de datos de formulario a partir de fuentes de datos backend dispares, como un perfil de usuario de AEM, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Obtenga información sobre cómo configurar la base de datos MySQL como fuente de datos, crear, configurar y probar un modelo de datos de formulario.
seo-description: AEM Forms data integration module allows you to create a form data model from disparate backend data sources such as AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. Learn how to configure MySQL database as data source, create, configure, and test a form data model.
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: Adaptive Forms
exl-id: 2f83e853-2468-4ea2-85f6-8cf7fe9de6a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 86%

---

# Tutorial: Crear un modelo de datos de formulario  {#tutorial-create-form-data-model}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Este tutorial es un paso en la serie [Crear su primer formulario adaptable](/help/forms/using/create-your-first-adaptive-form.md). Se recomienda seguir la serie en orden cronológico para comprender, realizar y mostrar el caso de uso del tutorial completo.

## Información sobre el tutorial {#about-the-tutorial}

El módulo de integración de datos de AEM Forms le permite crear un modelo de datos de formulario a partir de fuentes de datos backend dispares, como un perfil de usuario de AEM, servicios web RESTful, servicios web basados en SOAP, servicios OData y bases de datos relacionales. Puede configurar objetos y servicios del modelo de datos en un modelo de datos de formulario y asociarlo a un formulario adaptable. Los campos de formularios adaptables están enlazados a las propiedades del objeto del modelo de datos. Los servicios permiten rellenar previamente el formulario adaptable y escribir los datos de formulario enviados en el objeto del modelo de datos.

Para obtener más información sobre la integración y el modelo de datos de formulario, consulte [Integración de datos de AEM Forms](/help/forms/using/data-integration.md).

Este tutorial lo acompañará durante los pasos para preparar, crear, configurar y asociar un modelo de datos de formulario con un formulario adaptable. Al final de este tutorial, podrá:

* [Configurar la base de datos MySQL como fuente de datos](#config-database)
* [Crear un modelo de datos de formulario mediante la base de datos MySQL](#create-fdm)
* [Configurar un modelo de datos de formulario](#config-fdm)
* [Probar un modelo de datos de formulario](#test-fdm)

El modelo de datos de formulario tendrá un aspecto similar al siguiente:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Fuentes de datos configuradas **B.** Esquemas de fuentes de datos **C.** Servicios disponibles **D.** Objetos del modelo de datos **E.** Servicios configurados

## Requisitos previos {#prerequisites}

Antes de empezar, asegúrese de que dispone de lo siguiente:

* Base de datos MySQL con datos de ejemplo como se indica en la sección Requisitos previos de [Cree su primer formulario adaptable](/help/forms/using/create-your-first-adaptive-form.md)
* Un paquete OSGi para el controlador JDBC MySQL como se explica en [Empaquetar un controlador de base de datos JDBC](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* Formulario adaptable, tal como se explica en el primer tutorial [Crear un formulario adaptable](/help/forms/using/create-adaptive-form.md)

## Paso 1: Configurar la base de datos MySQL como fuente de datos {#config-database}

Puede configurar distintos tipos de fuentes de datos para crear un modelo de datos de formulario. Para este tutorial, configuraremos la base de datos MySQL que ha configurado y rellenado con datos de ejemplo. Para obtener información sobre otras fuentes de datos compatibles y cómo configurarlas, consulte [Integración de datos de AEM Forms](/help/forms/using/data-integration.md).

Haga lo siguiente para configurar la base de datos MySQL:

1. Instale el controlador JDBC para la base de datos MySQL como un paquete OSGi:

   1. Inicie sesión en la instancia de autor de AEM Forms como administrador y vaya a los paquetes de la consola web de AEM. La dirección URL predeterminada es [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

   1. Pulse **Instalar/actualizar**. Aparecerá el cuadro de diálogo **Cargar e instalar paquetes**.

   1. Pulse **Elegir archivo** para buscar y seleccionar el paquete OSGi del controlador JDBC de MySQL. Seleccione **Iniciar paquete** y **Actualizar paquetes** y pulse **Instalar o actualizar**. Asegúrese de que el controlador JDBC de Oracle Corporation para MySQL esté activo. El controlador está instalado.

1. Configurar la base de datos MySQL como fuente de datos:

   1. Vaya a AEM consola web en [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. Localice la configuración **Apache Sling Connection Pooled DataSource**. Pulse para abrir la configuración en modo de edición.
   1. En el cuadro de diálogo de configuración, especifique los siguientes detalles:

      * **Nombre del Datasource:** puede especificar cualquier nombre. Por ejemplo, especifique **WeRetailMySQL**.
      * **Nombre de propiedad del servicio DataSource**: especifique el nombre de la propiedad de servicio que contiene el nombre del DataSource. Se especifica al registrar la instancia de fuente de datos como servicio OSGi. Por ejemplo, **datasource.name**.
      * **Clase del controlador JDBC**: especifique el nombre de clase Java del controlador JDBC. Para la base de datos MySQL, especifique **com.mysql.jdbc.Driver**.
      * **URI de conexión JDBC**: especifique la dirección URL de conexión de la base de datos. Para la base de datos MySQL que se ejecuta en el puerto 3306 y el esquema weretail, la URL es: `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Nombre de usuario:** nombre de usuario de la base de datos. Debe permitir que el controlador JDBC establezca una conexión con la base de datos.
      * **Contraseña:** contraseña de la base de datos. Debe permitir que el controlador JDBC establezca una conexión con la base de datos.
      * **Probar en el préstamo:** habilita la opción **Probar en el préstamo**.
      * **Probar en la devolución:** habilita la opción **Probar en la devolución**.
      * **Consulta de validación:** especifica una consulta SQL SELECT para validar conexiones desde el grupo. La consulta debe devolver al menos una fila. Por ejemplo, **seleccionar &amp;último; de detalles del cliente**.
      * **Aislamiento de transacciones**: establezca el valor en **READ_COMMITTED**.

      Deje las demás propiedades con los [valores](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) predeterminados  y pulse **Guardar**.
   Se creará una configuración similar a la siguiente.

   ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Paso 2: Crear un modelo de datos de formulario {#create-fdm}

AEM Forms proporciona una interfaz de usuario intuitiva para [crear un modelo de datos de formulario](data-integration.md) desde fuentes de datos configuradas. Puede utilizar varias fuentes de datos en un modelo de datos de formulario. Para nuestro caso de uso, utilizaremos la fuente de datos MySQL configurada.

Para crear el modelo de datos de formulario, haga lo siguiente:

1. En AEM instancia de autor, vaya a **Forms** >  **Integración de datos** s.
1. Pulse **Crear** > **Modelo de datos de formulario**.
1. En el cuadro de diálogo Crear un modelo de datos de formulario, especifique un **nombre** para el modelo de datos de formulario. Por ejemplo, **customer-shipping-billing-details**. Pulse **Siguiente**.
1. La pantalla Seleccionar fuente de datos enumera todas las fuentes de datos configuradas. Seleccione la fuente de datos **WeRetailMySQL** y pulse **Crear**.

   ![data-source-selection](assets/data-source-selection.png)

Se creará el modelo de datos de formulario **customer-shipping-billing-details**.

## Paso 3: Configurar el modelo de datos de formulario {#config-fdm}

La configuración del modelo de datos de formulario implica:

* agregar objetos y servicios del modelo de datos
* configurar servicios de lectura y escritura para objetos del modelo de datos

Para configurar el modelo de datos de formulario, haga lo siguiente:

1. En la instancia de autor de AEM, navegue hasta **Formularios > Integraciones de datos**. La dirección URL predeterminada es [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. El modelo de datos de formulario **customer-shipping-billing-details** que ha creado anteriormente se muestra aquí. Ábralo en el modo de edición.

   La fuente de datos seleccionada **WeRetailMySQL** se configura en el modelo de datos de formulario.

   ![default-fdm](assets/default-fdm.png)

1. Expanda el árbol de fuentes de datos WeRailMySQL. Seleccione los siguientes objetos y servicios del esquema **weretail** > **customerdetails** para el modelo de datos de formulario:

   * **Objetos del modelo de datos**:

      * id
      * name
      * ShippingAddress
      * ciudad
      * estado
      * código postal
   * **Servicios:**

      * conseguir
      * actualizar

   Pulse **Agregar selección** para agregar los objetos y servicios seleccionados al modelo de datos de formulario.

   ![weretail-schema](assets/weretail-schema.png)

   >[!NOTE]
   >
   >Los servicios predeterminados de obtener, actualizar e insertar para fuentes de datos JDBC se proporcionan ya preparados con el modelo de datos de formulario.

1. Configure los servicios de lectura y escritura para el objeto del modelo de datos.

   1. Seleccione el objeto del modelo de datos **customerdetails** y pulse **Editar propiedades**.
   1. Seleccione **obtener** de la lista desplegable Servicio de lectura. El argumento **id**, que es la clave principal del objeto del modelo de datos customerdetails, se agrega automáticamente. Pulse ![aem_6_3_edit](assets/aem_6_3_edit.png) y configure el argumento como se indica a continuación.

      ![read-default](assets/read-default.png)

   1. Del mismo modo, seleccione **actualizar** como servicio de escritura. El objeto **customerdetails** se agrega automáticamente como argumento. El argumento se configura de la siguiente manera.

      ![write-default](assets/write-default.png)

      Agregue y configure el argumento **id** como se indica a continuación.

      ![id-arg](assets/id-arg.png)

   1. Pulse **Listo** para guardar las propiedades del objeto del modelo de datos. Luego, pulse **Guardar** para guardar el modelo de datos de formulario.

      Los servicios **obtener** y **actualizar** se agregan como servicios predeterminados para el objeto del modelo de datos.

      ![data-model-object](assets/data-model-object.png)

1. Vaya a la pestaña **Servicios** y configure los servicios **obtener** y **actualizar**.

   1. Seleccione el servicio **conseguir** y pulse **Editar propiedades**. Se abrirá el cuadro de diálogo Propiedades.
   1. Especifique lo siguiente en el cuadro de diálogo Editar propiedades:

      * **Título**: especifique el título del servicio. Por ejemplo: Recuperar dirección de envío.
      * **Descripción**: especifique la descripción que contiene el funcionamiento detallado del servicio. Por ejemplo:

         Este servicio recupera la dirección de envío y otros detalles del cliente de la base de datos MySQL

      * **Objeto de modelo de salida**: seleccione el esquema que contiene los datos del cliente. Por ejemplo:

         customerdetail schema
      * **Devolver matriz**: deshabilite la opción **Devolver matriz**.
      * **Argumentos**: seleccione el argumento llamado **Id.**.

      Pulse **Listo**. El servicio para recuperar los detalles del cliente de la base de datos MySQL está configurado.

      ![shiiping-address-retrieval](assets/shiiping-address-retrieval.png)

   1. Seleccione el servicio **actualizar** y pulse **Editar propiedades**. Se abrirá el cuadro de diálogo Propiedades.

   1. Especifique lo siguiente en el cuadro de diálogo Editar propiedades:

      * **Título**: especifique el título del servicio. Por ejemplo, Actualizar dirección de envío.

      * **Descripción**: especifique la descripción que contiene el funcionamiento detallado del servicio. Por ejemplo:

         Este servicio actualiza la dirección de envío y los campos relacionados en la base de datos MySQL

      * **Objeto del modelo de entrada**: seleccione el esquema que contiene los datos del cliente. Por ejemplo:

         customerdetail schema

      * **Tipo de salida**: seleccione **BOOLEANO**.
      * **Argumentos**: seleccione el argumento llamado **ID** y **customerdetails**.

      Pulse **Listo**. La variable **actualizar** para actualizar los detalles del cliente en la base de datos MySQL está configurada.

      ![shiiping-address-update](assets/shiiping-address-update.png)



Se configuran el objeto y los servicios del modelo de datos de formulario. Ahora puede probar el modelo de datos de formulario.

## Paso 4: Probar el modelo de datos de formulario {#test-fdm}

Puede probar el objeto y los servicios del modelo de datos para comprobar que está configurado correctamente.

Haga lo siguiente para ejecutar la prueba:

1. Vaya a la pestaña **Modelo**, seleccione el modelo de datos de formulario **customerdetails** y pulse **Objeto del modelo de prueba**.
1. En la ventana **Modelo/servicio de prueba**, seleccione **Objeto del modelo de lectura** de la lista desplegable **Seleccionar modelo/servicio**.
1. En el **detalles del cliente** , especifique un valor para **id** argumento que existe en la base de datos MySQL configurada y pulse **Prueba**.

   Los detalles del cliente asociados con el ID especificado se recuperan y se muestran en la sección **Salida** como se muestra a continuación.

   ![test-read-model](assets/test-read-model.png)

1. Del mismo modo, puede probar el objeto y los servicios del modelo de escritura.

   En el siguiente ejemplo, el servicio de actualización actualiza correctamente los detalles de dirección del ID 7102715 de la base de datos.

   ![test-write-model](assets/test-write-model.png)

   Si vuelve a probar el servicio de modelo de lectura para el ID 7107215, recuperará y mostrará los detalles actualizados del cliente como se muestra a continuación.

   ![read-updated](assets/read-updated.png)
