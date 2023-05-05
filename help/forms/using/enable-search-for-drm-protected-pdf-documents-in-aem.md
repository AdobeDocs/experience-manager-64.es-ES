---
title: Habilitar AEM para buscar documentos PDF protegidos mediante Seguridad de documentos
seo-title: Enable AEM to search document security protected PDF documents
description: Aprenda a habilitar la búsqueda nativa de AEM para realizar búsquedas de texto completo en documentos PDF protegidos por DRM.
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: Document Security
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 90%

---

# Habilitar AEM para buscar documentos PDF protegidos mediante Seguridad de documentos {#enable-aem-to-search-document-security-protected-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La búsqueda de AEM puede buscar y localizar AEM Assets y realizar búsquedas de texto en varios formatos de documento de uso común, como archivos de texto sin formato, documentos de Microsoft Office y documentos PDF. También puede ampliar la búsqueda nativa para realizar búsquedas de texto completo en [documentos PDF protegidos con seguridad de documentos de AEM](/help/forms/using/admin-help/document-security.md). Para permitir que AEM realice búsquedas de texto completo en dichos documentos, realice los siguientes pasos:

1. Establezca una conexión segura
1. Indexe un documento PDF de ejemplo protegido por directivas

## Requisitos previos {#prerequisites}

* Si utiliza AEM Forms en OSGi:

   * Instale el [Paquete del indexador de seguridad de documentos de AEM Forms](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) en el servidor de AEM Forms.
   * Asegúrese de que haya AEM Forms en el servidor JEE en funcionamiento y de que la seguridad de los documentos esté instalada en AEM Forms correspondiente del servidor JEE. Necesita AEM Forms del servidor JEE para indexar el documento protegido.

* Si solo utiliza AEM Forms en el servidor JEE, el paquete del indexador ya estará instalado.
* Asegúrese de que todos los paquetes estén en funcionamiento. Si no todos los paquetes están activos, espere hasta que todos los paquetes estén en funcionamiento.

   * Para AEM Forms en OSGi, los paquetes se enumeran en `https://[server]:[port]/system/console/bundles`.
   * Para AEM Forms en JEE, los paquetes se enumeran en `https://[server]:[port]/[context-path]/system/console/bundles`. Por ejemplo, `http://localhost:8080/lc/system/console/bundles`.

* Agregue el paquete *sun.util.calendar* a la lista de permitidos. Para agregar el paquete a la lista de permitidos, realice los siguientes pasos:

   1. Abra la consola web de AEM. La URL es `https://[server]:[port]/system/console/configMgr`. .
   1. Localice y abra **Configuración del firewall de deserialización**.
   1. Agregue el paquete sun.util.calendar al campo Clases permitidas o prefijos de paquete y haga clic en **Guardar**.

## Establezca una conexión segura entre las pilas de AEM Forms JEE y OSGi {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Puede utilizar uno de los siguientes métodos para establecer la conexión segura:

* Configurar el paquete del SDK del cliente de LiveCycle de Adobe con AEM Forms en las credenciales de administrador de JEE
* Configurar el paquete del SDK del cliente de LiveCycle de Adobe mediante la autenticación mutua

### Configurar el paquete del SDK del cliente de LiveCycle de Adobe con AEM Forms en las credenciales de administrador de JEE {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Abra la consola web de AEM. La URL es `https://[server]:[port]/system/console/configMgr`. .
1. Busque y abra el paquete **SDK de cliente de LiveCycle de Adobe**. Especifique un valor para los siguientes campos:

   * **URL del servidor:** especifique la URL HTTPS de AEM Forms en el servidor JEE. Para habilitar la comunicación sobre https, reinicie el servidor con el parámetro -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Nombre del servicio**: agregue RightsManagementService a la lista de servicios especificados.
   * **Nombre de usuario:** especifique el nombre de usuario de AEM Forms en la cuenta JEE que se utilizará para iniciar llamadas desde el servidor de AEM. La cuenta especificada debe tener permisos para iniciar los servicios de documentos en AEM Forms en el servidor JEE.
   * **Contraseña**: especifique la contraseña de AEM Forms en la cuenta JEE mencionada en el campo Nombre de usuario.

   Haga clic en **Guardar**. AEM está habilitado para buscar documentos PDF protegidos.

### Configurar el paquete del SDK del cliente de LiveCycle de Adobe mediante la autenticación mutua {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Habilite la autenticación mutua para AEM Forms en JEE. Para obtener información detallada, consulte [CAC y autenticación mutua](https://helpx.adobe.com/es/livecycle/kb/cac-mutual-authentication.html).
1. Abra la consola web de AEM. La URL es `https://[server]:[port]/system/console/configMgr`. .
1. Busque y abra el paquete **SDK de cliente de LiveCycle de Adobe**. Especifique un valor para las siguientes propiedades:

   * **URL del servidor**: especifique la URL HTTPS de AEM Forms en el servidor JEE. Para habilitar la comunicación sobre https, reinicie el servidor AEM con el parámetro -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Habilite SSL bidireccional**: active la opción Enable 2-way SSL.
   * **URL del archivo KeyStore**: especifique la dirección URL del archivo keystore.
   * **URL de la interfaz de TrustStore**: especifique la dirección URL del archivo truststore.
   * **Contraseña de KeyStore**: especifique la contraseña del archivo keystore.
   * **TrustStorePassword**: especifique la contraseña del archivo truststore.
   * **Nombre del servicio**: agregue RightsManagementService a la lista de servicios especificados.

   Haga clic en **Guardar**. AEM está habilitado para buscar documentos PDF protegidos

## Indexe un documento PDF de ejemplo protegido por directivas {#index-a-sample-policy-protected-pdf-document}

1. Inicie sesión en AEM Assets como administrador.
1. Cree una carpeta en el administrador de recursos digitales de AEM y cargue los documentos PDF protegidos por directivas en la carpeta recién creada.

   Ahora puede buscar los documentos protegidos por directivas mediante la búsqueda de AEM.
