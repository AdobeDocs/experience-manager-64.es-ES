---
title: Configurar orígenes de datos
seo-title: Configurar orígenes de datos
description: Obtenga información sobre cómo configurar distintos tipos de fuentes de datos y aprovechar para crear modelos de datos de formulario.
seo-description: Obtenga información sobre cómo configurar distintos tipos de fuentes de datos y aprovechar para crear modelos de datos de formulario.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---


# Configurar orígenes de datos {#configure-data-sources}

Obtenga información sobre cómo configurar distintos tipos de fuentes de datos y aprovechar para crear modelos de datos de formulario.

![](do-not-localize/data-integeration.png)

La integración de datos de AEM Forms le permite configurar y conectar fuentes de datos dispares. Los siguientes tipos son compatibles de forma predeterminada. Sin embargo, con poca personalización, también puede integrar otras fuentes de datos.

* Bases de datos relacionales: MySQL, Microsoft SQL Server, IBM DB2 y Oracle RDBMS
* perfil del usuario de AEM
* Servicios web RESTful
* Servicios Web basados en SOAP
* Servicios OData

La integración de datos admite los tipos de autenticación OAuth2.0, Basic Authentication y API Key predeterminados, y permite implementar la autenticación personalizada para acceder a los servicios Web. Mientras que los servicios RESTful, basados en SOAP y OData están configurados en los servicios de nube de AEM, JDBC para bases de datos relacionales y conector para AEM perfil de usuarios están configurados en AEM consola web.

## Configurar base de datos relacional {#configure-relational-database}

Puede configurar bases de datos relacionales mediante AEM Configuración de consola web. Haga lo siguiente:

1. Vaya a AEM consola web en `https://[server]:[host]/system/console/configMgr`.
1. Busque la configuración de **[!UICONTROL Apache Sling Connection Pooled DataSource]** . Toque para abrir la configuración en modo de edición.
1. En el cuadro de diálogo de configuración, especifique los detalles de la base de datos que desea configurar, como:

   * Nombre del origen de datos
   * Propiedad del servicio de origen de datos que almacena el nombre del origen de datos
   * Nombre de clase Java para el controlador JDBC
   * URI de conexión JDBC
   * Nombre de usuario y contraseña para establecer la conexión con el controlador JDBC

   >[!NOTE]
   >
   >Asegúrese de cifrar información confidencial como contraseñas antes de configurar el origen de datos. Para cifrar:
   >
   >1. Ir a `https://[server]:[port]/system/console/crypto`.
   >1. En el campo **[!UICONTROL Texto]** sin formato, especifique la contraseña o cualquier cadena que desee cifrar y haga clic en **[!UICONTROL Protect]**.

   >
   >El texto cifrado aparece en el campo Texto protegido que puede especificar en la configuración.

1. Habilite **[!UICONTROL Prueba a la Obtención]** o **[!UICONTROL Prueba a la Devolución]** para especificar que los objetos se validen antes de ser tomados en préstamo o devueltos al grupo, respectivamente.
1. Especifique una consulta SQL SELECT en el campo Consulta **[!UICONTROL de]** validación para validar las conexiones del grupo. La consulta debe devolver al menos una fila. En función de la base de datos, especifique una de las siguientes opciones:

   * SELECT 1 (MySQL y MS SQL)
   * SELECT 1 from dual (Oracle)

1. Toque **[!UICONTROL Guardar]** para guardar la configuración.

## Configurar AEM perfil de usuario {#configure-aem-user-profile}

Puede configurar AEM perfil del usuario mediante la configuración del conector de Perfil del usuario en AEM consola web. Haga lo siguiente:

1. Vaya a AEM consola web en `https://[server]:[host]/system/console/configMgr`.
1. Busque Integraciones de datos de **[!UICONTROL AEM Forms: Configuración]** del conector de Perfil de usuario y toque para abrir la configuración en modo de edición.
1. En el cuadro de diálogo Configuración del conector de Perfil de usuario, puede agregar, quitar o actualizar las propiedades del perfil de usuario. Las propiedades especificadas estarán disponibles para su uso en el modelo de datos de formulario. Utilice el siguiente formato para especificar las propiedades de perfil del usuario:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Ejemplos:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&amp;ast;** en el ejemplo anterior indica todos los nodos bajo el `profile/empLocation/` nodo en AEM perfil del usuario en la estructura CRXDE. Significa que el modelo de datos de formulario puede acceder a la `city` propiedad de tipo `string` presente en cualquier nodo bajo el `profile/empLocation/` nodo. Sin embargo, los nodos que contienen la propiedad especificada deben seguir una estructura coherente.

1. Toque **[!UICONTROL Guardar]** para guardar la configuración.

## Configurar carpeta para configuraciones de servicio en la nube {#cloud-folder}

>[!NOTE]
>
>La configuración de la carpeta de servicios en la nube es necesaria para configurar los servicios en la nube para los servicios RESTful, SOAP y OData.

Todas las configuraciones de servicios en la nube en AEM se consolidan en la `/conf` carpeta en AEM repositorio. De forma predeterminada, la `conf` carpeta contiene la `global` carpeta en la que puede crear configuraciones de servicio en la nube. Sin embargo, debe habilitarlo manualmente para las configuraciones de nube. También puede crear carpetas adicionales en `conf` para crear y organizar configuraciones de servicios en la nube.

Para configurar la carpeta para las configuraciones del servicio en la nube:

1. Vaya a **[!UICONTROL Herramientas > General > Navegador]** de configuración.
   * See the [Configuration Browser documentation](/help/sites-administering/configurations.md) for more information.
1. Haga lo siguiente para habilitar la carpeta global para las configuraciones de nube o omita este paso para crear y configurar otra carpeta para las configuraciones de servicio en la nube.

   1. En el Explorador **[!UICONTROL de]** configuración, seleccione la `global` carpeta y toque **[!UICONTROL Propiedades]**.
   1. En el cuadro **[!UICONTROL de diálogo Propiedades]** de configuración, habilite Configuraciones **[!UICONTROL de nube]**.
   1. Toque **[!UICONTROL Guardar y cerrar]** para guardar la configuración y salir del cuadro de diálogo.

1. En el Explorador **[!UICONTROL de]** configuración, toque **[!UICONTROL Crear]**.
1. En el cuadro de diálogo **[!UICONTROL Crear configuración]** , especifique un título para la carpeta y habilite **[!UICONTROL Cloud Configurations]**.
1. Toque **[!UICONTROL Crear]** para crear la carpeta habilitada para las configuraciones de servicio en la nube.

## Configuración de los servicios web RESTful {#configure-restful-web-services}

El servicio web RESTful se puede describir usando las especificaciones [](https://swagger.io/specification/) Swagger en formato JSON o YAML en un archivo de definición Swagger. Para configurar el servicio web RESTful en los servicios en la nube de AEM, asegúrese de que tiene el archivo Swagger en el sistema de archivos o la URL en la que se aloja el archivo.

Para configurar los servicios RESTful, haga lo siguiente:

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes]** de datos. Toque para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpeta para configuraciones](/help/forms/using/configure-data-sources.md#cloud-folder) de servicios en la nube para obtener información sobre cómo crear y configurar una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el cuadro de diálogo **** Crear configuración de fuente de datos. Especifique un nombre y, si lo desea, un título para la configuración, seleccione **[!UICONTROL RESTful Service]** en la lista desplegable Tipo **[!UICONTROL de]** servicio, si lo desea, busque y seleccione una imagen en miniatura para la configuración y toque **[!UICONTROL Siguiente]**.
1. Especifique los siguientes detalles para el servicio RESTful:

   * Seleccione URL o archivo en la lista desplegable Origen de Swagger y, en consecuencia, especifique la URL de Swagger al archivo de definición de Swagger o cargue el archivo Swagger desde el sistema de archivos local.
   * Seleccione el tipo de autenticación — Ninguno, OAuth2.0, Autenticación básica, Clave de API o Autenticación personalizada — para acceder al servicio RESTful y, en consecuencia, proporcionar detalles para la autenticación.

1. Toque **[!UICONTROL Crear]** para crear la configuración de nube para el servicio RESTful.

## Configuración de servicios web SOAP {#configure-soap-web-services}

Los servicios Web basados en SOAP se describen mediante especificaciones [del lenguaje de descripción de servicios](https://www.w3.org/TR/wsdl)Web (WSDL). Para configurar el servicio web basado en SOAP en los servicios de nube de AEM, asegúrese de que dispone de la URL WSDL para el servicio web y haga lo siguiente:

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes]** de datos. Toque para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpeta para configuraciones](/help/forms/using/configure-data-sources.md#cloud-folder) de servicios en la nube para obtener información sobre cómo crear y configurar una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el cuadro de diálogo **** Crear configuración de fuente de datos. Especifique un nombre y, si lo desea, un título para la configuración, seleccione Servicio **[!UICONTROL Web]** SOAP en la lista desplegable Tipo **[!UICONTROL de]** servicio, si lo desea, busque y seleccione una imagen en miniatura para la configuración y toque **[!UICONTROL Siguiente]**.
1. Especifique lo siguiente para el servicio web SOAP:

   * URL WSDL para el servicio Web.
   * Punto final de servicio. Especifique un valor en este campo para anular el extremo de servicio mencionado en WSDL.
   * Seleccione el tipo de autenticación — Ninguno, OAuth2.0, Autenticación básica, Autenticación personalizada o Token X509 — para acceder al servicio SOAP y, en consecuencia, proporcionar los detalles para la autenticación.

      Si selecciona el token X509 como tipo de autenticación, configure el certificado X509. Para obtener más información, consulte [Configuración de certificados](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Especifique el alias KeyStore para el certificado X509 en el campo Alias **[!UICONTROL de]** clave. Especifique el tiempo, en segundos, hasta que la solicitud de autenticación siga siendo válida en el campo **[!UICONTROL Tiempo de vida]** . Si lo desea, seleccione firmar el encabezado de la marca de tiempo o el cuerpo del mensaje o ambos.

1. Toque **[!UICONTROL Crear]** para crear la configuración de nube para el servicio web SOAP.

## Configurar servicios OData {#config-odata}

Un servicio OData se identifica mediante su URL raíz de servicio. Para configurar un servicio OData en los servicios en la nube de AEM, asegúrese de que dispone de una URL raíz de servicio para el servicio y haga lo siguiente:

>[!NOTE]
>
>Para obtener una guía paso a paso sobre la configuración de Microsoft Dynamics 365, en línea o local, consulte Configuración [de OData de](/help/forms/using/ms-dynamics-odata-configuration.md)Microsoft Dynamics.

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes]** de datos. Toque para seleccionar la carpeta en la que desea crear una configuración de nube.

   Consulte [Configurar carpeta para configuraciones](/help/forms/using/configure-data-sources.md#cloud-folder) de servicios en la nube para obtener información sobre cómo crear y configurar una carpeta para configuraciones de servicios en la nube.

1. Toque **[!UICONTROL Crear]** para abrir el cuadro de diálogo **** Crear configuración de fuente de datos. Especifique un nombre y, si lo desea, un título para la configuración, seleccione **[!UICONTROL OData Service]** en la lista desplegable Tipo **[!UICONTROL de]** servicio, si lo desea, busque y seleccione una imagen en miniatura para la configuración y toque **[!UICONTROL Siguiente]**.
1. Especifique los siguientes detalles para el servicio OData:

   * URL de raíz de servicio para el servicio OData que se va a configurar.
   * Seleccione el tipo de autenticación — Ninguno, OAuth2.0, Autenticación básica o Autenticación personalizada — para acceder al servicio OData y, en consecuencia, proporcionar los detalles para la autenticación.

   >[!NOTE]
   >
   >Debe seleccionar el tipo de autenticación OAuth 2.0 para conectarse con los servicios de Microsoft Dynamics mediante el extremo OData como raíz del servicio.

1. Toque **Crear** para crear la configuración de nube para el servicio OData.

## Pasos siguientes {#next-steps}

Ha configurado las fuentes de datos. A continuación, puede crear un modelo de datos de formulario o, si ya ha creado un modelo de datos de formulario sin un origen de datos, puede asociarlo a los orígenes de datos que acaba de configurar. Consulte [Creación de un modelo](/help/forms/using/create-form-data-models.md) de datos de formulario para obtener más información.
