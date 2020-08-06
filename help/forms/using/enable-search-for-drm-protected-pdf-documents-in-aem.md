---
title: Habilitar AEM para buscar documentos PDF protegidos por seguridad de documento
seo-title: Habilitar AEM para buscar documentos PDF protegidos por seguridad de documento
description: 'Obtenga información sobre cómo habilitar la búsqueda de AEM nativa para realizar búsquedas de texto completo en documentos PDF protegidos con DRM.  '
seo-description: 'Obtenga información sobre cómo habilitar la búsqueda de AEM nativa para realizar búsquedas de texto completo en documentos PDF protegidos con DRM.  '
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 1%

---


# Habilitar AEM para buscar documentos PDF protegidos por seguridad de documento {#enable-aem-to-search-document-security-protected-pdf-documents}

AEM búsqueda permite buscar y localizar AEM recursos y realizar búsquedas de texto en diversos formatos de documento utilizados con frecuencia, como archivos de texto sin formato, documentos de Microsoft Office y documentos PDF. También puede ampliar la búsqueda nativa para realizar búsquedas de texto completo en Documentos [PDF protegidos con AEM seguridad](/help/forms/using/admin-help/document-security.md)de Documento. Para permitir que AEM realice búsquedas de texto completo en dichos documentos, lleve a cabo los siguientes pasos:

1. Establecimiento de una conexión segura
1. Indexar un documento PDF de muestra protegido por una política

## Requisitos previos {#prerequisites}

* Si está utilizando AEM Forms en OSGi:

   * Instale el paquete [](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) AEM Forms Documento Security Indexer en el servidor AEM Forms.
   * Asegúrese de que un AEM Forms en el servidor JEE esté activo y en ejecución y de que la seguridad de documento esté instalada en el AEM Forms correspondiente en el servidor JEE. El formulario AEM en el servidor JEE es necesario para indexar el documento protegido.

* Si solo utiliza AEM Forms en el servidor JEE, el paquete de indizador ya está instalado.
* Asegúrese de que todos los paquetes estén en funcionamiento. Si todos los paquetes no están activos, espere hasta que todos los paquetes estén en funcionamiento.

   * Para AEM Forms en OSGi, los paquetes se enumeran en `https://[server]:[port]/system/console/bundles`.
   * Para AEM Forms en JEE, los paquetes se muestran en `https://[server]:[port]/[context-path]/system/console/bundles`. Por ejemplo `http://localhost:8080/lc/system/console/bundles`.

* Añada el paquete *sun.util.calendar* a la lista de permitidos. Para agregar el paquete a la lista de permitidos, realice los siguientes pasos:

   1. Abra AEM consola web. La dirección URL es `https://[server]:[port]/system/console/configMgr`.
   1. Localice y abra **Deserialization Firewall Configuration**.
   1. Añada el paquete sun.util.calendar al campo Clases o prefijos de paquete de la lista blanca y haga clic en **Guardar**.

## Establecimiento de una conexión segura entre las pilas AEM Forms JEE y OSGi {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Puede utilizar uno de los siguientes métodos para establecer la conexión segura:

* Configurar el paquete SDK de Adobe LiveCycle Client con AEM Forms en las credenciales de administrador de JEE
* Configurar el paquete SDK del cliente de Adobe LiveCycle mediante autenticación mutua

### Configurar el paquete SDK de Adobe LiveCycle Client con AEM Forms en las credenciales de administrador de JEE {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Abra AEM consola web. La dirección URL es `https://[server]:[port]/system/console/configMgr`.
1. Busque y abra el paquete **SDK del cliente de LiveCycle de** Adobe. Especifique un valor para los campos siguientes:

   * **URL del servidor:** Especifique la URL HTTPS de AEM Forms en el servidor JEE. Para habilitar la comunicación sobre https, reinicie el servidor con el parámetro -Djavax.net.ssl.trustStore=&lt;ruta de AEM Forms en el archivo de almacén de claves JEE>.
   * **Nombre** del servicio: Añada RightsManagementService a la lista de los servicios especificados.
   * **Nombre de usuario:** Especifique el nombre de usuario de la cuenta de AEM Forms en JEE que se va a utilizar para iniciar llamadas desde AEM servidor. La cuenta especificada debe tener permisos para servicios de inicio documento en AEM Forms en el servidor JEE.
   * **Contraseña**: Especifique la contraseña del AEM Forms en la cuenta JEE mencionada en el campo Nombre de usuario.

   Haga clic en **Guardar.** AEM está habilitado para buscar documentos PDF protegidos por seguridad de documento.

### Configurar el paquete SDK del cliente de Adobe LiveCycle mediante autenticación mutua {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Habilite la autenticación mutua para AEM Forms en JEE. Para obtener información detallada, consulte [CAC y Autenticación](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html)mutua.
1. Abra AEM consola web. La dirección URL es `https://[server]:[port]/system/console/configMgr`.
1. Busque y abra el paquete SDK **del cliente de LiveCycle de** Adobe. Especifique un valor para las siguientes propiedades:

   * **URL** del servidor: Especifique la URL HTTPS de AEM Forms en el servidor JEE. Para habilitar la comunicación sobre https, reinicie el servidor de AEM con el parámetro -Djavax.net.ssl.trustStore=&lt;ruta de AEM Forms en el archivo de almacén de claves JEE>.
   * **Habilitar SSL** bidireccional: Active la opción Activar SSL bidireccional.
   * **URL** del archivo KeyStore: Especifique la dirección URL del archivo de almacén de claves.
   * **URL** de la carpeta TrustStore: Especifique la dirección URL del archivo de almacén de confianza.
   * **Contraseña** de KeyStore: Especifique la contraseña del archivo de almacén de claves.
   * **TrustStorePassword**: Especifique la contraseña del archivo de almacén de confianza.
   * **Nombre** del servicio: Añada RightsManagementService a la lista de los servicios especificados.

   Haga clic en **Guardar.** AEM está habilitado para buscar documentos PDF protegidos por seguridad de documento

## Indexar un documento PDF de muestra protegido por una política {#index-a-sample-policy-protected-pdf-document}

1. Inicie sesión en AEM Assets como administrador.
1. Cree una carpeta en AEM Administrador de recursos digitales y cargue los documentos PDF protegidos por políticas en la carpeta recién creada.

   Ahora puede buscar los documentos protegidos por políticas mediante AEM búsqueda.

