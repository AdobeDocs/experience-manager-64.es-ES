---
title: Configurar fuentes de datos
seo-title: Configure data sources
description: Aprenda a configurar diferentes tipos de fuentes de datos y aproveche para crear modelos de datos de formulario.
seo-description: Learn how to configure different types of data sources and leverage to create form data models.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1399'
ht-degree: 42%

---

# Configurar fuentes de datos {#configure-data-sources}

Aprenda a configurar diferentes tipos de fuentes de datos y aproveche para crear modelos de datos de formulario.

![](do-not-localize/data-integeration.png)

La integración de datos de AEM Forms le permite configurar y conectarse a fuentes de datos diferentes. Los siguientes tipos son compatibles de forma predeterminada. Sin embargo, con poca personalización, también puede integrar otras fuentes de datos.

* Bases de datos relacionales: MySQL, Microsoft SQL Server, IBM DB2 y RDBMS de Oracle
* AEM perfil de usuario
* Servicios web RESTful
* Servicios web basados en SOAP
* Servicios OData

La integración de datos es compatible con los tipos de autenticación de forma predeterminada OAuth2.0, autenticación básica y clave del API, y permite implementar la autenticación personalizada para acceder a servicios web. Mientras que los servicios RESTful, SOAP y OData están configurados en AEM Cloud Services, JDBC para bases de datos relacionales y conector para AEM perfil de usuario están configurados en AEM consola web.

## Configuración de la base de datos relacional {#configure-relational-database}

Puede configurar bases de datos relacionales mediante AEM Configuración de la consola web. Haga lo siguiente:

1. Vaya a AEM consola web en `https://[server]:[host]/system/console/configMgr`.
1. Buscar **[!UICONTROL Fuente de datos obtenida de una conexión Apache Sling]** configuración. Pulse para abrir la configuración en modo de edición.
1. En el cuadro de diálogo de configuración, especifique los detalles de la base de datos que desea configurar, como:

   * Nombre de la fuente de datos
   * Propiedad del servicio de fuente de datos que almacena el nombre del origen de datos
   * Nombre de clase Java para el controlador JDBC
   * URI de conexión JDBC
   * Nombre de usuario y contraseña para establecer conexión con el controlador JDBC

   >[!NOTE]
   >
   >Asegúrese de cifrar información confidencial como contraseñas antes de configurar el origen de datos. Para cifrar:
   >
   >1. Vaya a `https://[server]:[port]/system/console/crypto`.
   >1. En el **[!UICONTROL Texto sin formato]** , especifique la contraseña o cualquier cadena que desee cifrar y haga clic en **[!UICONTROL Protect]**.

   >
   >El texto cifrado aparece en el campo Texto protegido que puede especificar en la configuración.

1. Habilitar **[!UICONTROL Prueba a la vista previa]** o **[!UICONTROL Prueba a la vuelta]** para especificar que los objetos se validan antes de ser tomados en préstamo o devueltos al grupo, respectivamente.
1. Especifique una consulta SQL SELECT en la **[!UICONTROL Consulta de validación]** para validar conexiones desde el grupo. La consulta debe devolver al menos una fila. En función de la base de datos, especifique una de las siguientes opciones:

   * SELECT 1 (MySQL y MS SQL)
   * SELECT 1 from dual (Oracle)

1. Toque **[!UICONTROL Guardar]** para guardar la configuración.

## Configuración AEM perfil de usuario {#configure-aem-user-profile}

Puede configurar AEM perfil de usuario mediante la configuración del conector de perfil de usuario en AEM consola web. Haga lo siguiente:

1. Vaya a AEM consola web en `https://[server]:[host]/system/console/configMgr`.
1. Buscar **[!UICONTROL Integraciones de datos de AEM Forms: configuración del conector de perfil de usuario]** y pulse para abrir la configuración en modo de edición.
1. En el cuadro de diálogo Configuración del conector de perfil de usuario, puede agregar, quitar o actualizar las propiedades del perfil de usuario. Las propiedades especificadas estarán disponibles para su uso en el modelo de datos de formulario. Utilice el siguiente formato para especificar las propiedades del perfil del usuario:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Ejemplos:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >La variable **&amp;ast;** en el ejemplo anterior indica todos los nodos bajo la variable `profile/empLocation/` en AEM perfil de usuario en la estructura CRXDE. Significa que el modelo de datos de formulario puede acceder al `city` propiedad de tipo `string` presentes en cualquier nodo bajo la variable `profile/empLocation/` nodo . Sin embargo, los nodos que contienen la propiedad especificada deben seguir una estructura coherente.

1. Toque **[!UICONTROL Guardar]** para guardar la configuración.

## Configurar carpetas para configuraciones de servicios en la nube {#cloud-folder}

>[!NOTE]
>
>La configuración de la carpeta de servicios en la nube es necesaria para configurar los servicios en la nube para los servicios RESTful, SOAP y OData.

Todas las configuraciones de servicios en la nube en AEM se consolidan en la variable `/conf` en AEM repositorio. De forma predeterminada, la carpeta `conf` contiene la carpeta `global`, donde puede crear configuraciones de servicios en la nube. Sin embargo, debe habilitarlo manualmente para las configuraciones de nube. También puede crear carpetas adicionales en `conf` para crear y organizar configuraciones de servicios en la nube.

Para configurar la carpeta para las configuraciones de servicios en la nube:

1. Vaya a **[!UICONTROL Herramientas > General > Explorador de configuración]**.
   * Consulte la documentación del [](/help/sites-administering/configurations.md)Explorador de configuración para obtener más información.
1. Haga lo siguiente para habilitar la carpeta global para configuraciones de nube u omita este paso para crear y configurar otra carpeta para configuraciones de servicios en la nube.

   1. En el **[!UICONTROL Explorador de configuración]**, seleccione la carpeta `global` y pulse **[!UICONTROL Propiedades]**.
   1. En el cuadro de diálogo **[!UICONTROL Propiedades de configuración]**, habilite **[!UICONTROL Configuraciones de nube]**.
   1. Pulse **[!UICONTROL Guardar y cerrar]** para guardar la configuración y salir del cuadro de diálogo.

1. En el **[!UICONTROL Explorador de configuración]**, pulse **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]**, especifique un título para la carpeta y habilite **[!UICONTROL Configuraciones de nube]**.
1. Pulse **[!UICONTROL Crear]** para crear la carpeta habilitada para las configuraciones del servicio en la nube.

## Configurar servicios web de RESTful {#configure-restful-web-services}

El servicio web RESTful se puede describir mediante [Especificaciones de Swagger](https://swagger.io/specification/) en formato JSON o YAML en un archivo de definición Swagger. Para configurar el servicio web RESTful en los servicios en la nube de AEM, asegúrese de que tiene el archivo Swagger en el sistema de archivos o la URL donde está alojado el archivo.

Haga lo siguiente para configurar los servicios RESTful:

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes de datos]**. Pulse para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpetas para configuraciones de servicios en la nube](/help/forms/using/configure-data-sources.md#cloud-folder) para obtener información sobre la creación y configuración de una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el **[!UICONTROL Cuadro de diálogo Crear configuración de fuente de datos]**. Especifique un nombre y, opcionalmente, un título para la configuración, seleccione **[!UICONTROL Servicio RESTful]** en la lista desplegable **[!UICONTROL Tipo de servicio]**; opcionalmente puede examinar y seleccionar una imagen de miniatura para la configuración, y pulsar **[!UICONTROL Siguiente]**.
1. Especifique los siguientes detalles para el servicio RESTful:

   * Seleccione URL o Archivo de la lista desplegable Origen del Swagger y, en consecuencia, especifique la URL del Swagger al archivo de definición Swagger o cargue el archivo Swagger desde su sistema de archivos local.
   * Seleccione el tipo de autenticación (ninguna, OAuth2.0, autenticación básica, clave del API o autenticación personalizada) para acceder al servicio RESTful y facilitar los detalles correspondientes para la autenticación.

1. Pulse **[!UICONTROL Crear]** para crear la configuración de nube para el servicio RESTful.

## Configurar servicios web SOAP {#configure-soap-web-services}

Los servicios web basados en SOAP se describen utilizando [Especificaciones del lenguaje de descripción de servicios web (WSDL)](https://www.w3.org/TR/wsdl). Para configurar el servicio web basado en SOAP en los servicios en la nube de AEM, asegúrese de que dispone de la URL WSDL para el servicio web y haga lo siguiente:

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes de datos]**. Pulse para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpetas para configuraciones de servicios en la nube](/help/forms/using/configure-data-sources.md#cloud-folder) para obtener información sobre la creación y configuración de una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el **[!UICONTROL Cuadro de diálogo Crear configuración de fuente de datos]**. Especifique un nombre y, opcionalmente, un título para la configuración, seleccione **[!UICONTROL Servicio web SOAP]** en la lista desplegable **[!UICONTROL Tipo de servicio]**. También puede examinar y seleccionar una imagen en miniatura para la configuración y pulsar **[!UICONTROL Siguiente]**.
1. Especifique lo siguiente para el servicio web SOAP:

   * URL de WSDL para el servicio web.
   * Punto final de servicio. Especifique un valor en este campo para anular el punto final de servicio mencionado en WSDL.
   * Seleccione el tipo de autenticación (Ninguno, OAuth2.0, Autenticación básica, Autenticación personalizada o Token X509) para acceder al servicio SOAP y proporcione los detalles correspondientes para la autenticación.

      Si selecciona Token X509 como tipo de Autenticación, configure el certificado X509. Para obtener más información, consulte [Configuración de certificados](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Especifique el alias KeyStore para el certificado X509 en la variable **[!UICONTROL Alias de clave]** campo . Especifique el tiempo, en segundos, hasta que la solicitud de autenticación siga siendo válida en la variable **[!UICONTROL Tiempo de vida]** campo . De forma opcional, seleccione para firmar el cuerpo del mensaje, el encabezado de la marca de tiempo o ambos.

1. Pulse **[!UICONTROL Crear]** para crear la configuración de nube para el servicio web SOAP.

## Configurar servicios OData {#config-odata}

Un servicio OData se identifica mediante su URL raíz de servicio. Para configurar un servicio OData en los servicios en la nube de AEM, asegúrese de que tiene una URL raíz de servicio para el servicio y haga lo siguiente:

>[!NOTE]
>
>Para obtener una guía paso a paso sobre la configuración de Microsoft Dynamics 365, en línea o local, consulte [Configuración de OData de Microsoft Dynamics](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes de datos]**. Pulse para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpetas para configuraciones de servicios en la nube](/help/forms/using/configure-data-sources.md#cloud-folder) para obtener información sobre la creación y configuración de una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el **[!UICONTROL Cuadro de diálogo Crear configuración de fuente de datos]**. Especifique un nombre y, opcionalmente, un título para la configuración, seleccione **[!UICONTROL Servicio OData]** en la lista desplegable **[!UICONTROL Tipo de servicio]**. También puede examinar y seleccionar una imagen en miniatura para la configuración y pulsar **[!UICONTROL Siguiente]**.
1. Especifique los siguientes detalles para el servicio OData:

   * URL raíz del servicio para configurar el servicio OData.
   * Seleccione el tipo de autenticación (Ninguno, OAuth2.0, Autenticación básica o Autenticación personalizada) para acceder al servicio OData y proporcione los detalles para la autenticación.

   >[!NOTE]
   >
   >Debe seleccionar el tipo de autenticación de OAuth 2.0 para conectarse con los servicios de Microsoft Dynamics mediante el extremo OData como raíz del servicio.

1. Pulse **Crear** para crear la configuración de nube para el servicio OData.

## Pasos siguientes {#next-steps}

Ha configurado las fuentes de datos. A continuación, puede crear un modelo de datos de formulario o, si ya ha creado un modelo de datos de formulario sin un origen de datos, puede asociarlo a los orígenes de datos que acaba de configurar. Consulte [Crear modelo de datos de formulario](/help/forms/using/create-form-data-models.md) para obtener más información.
