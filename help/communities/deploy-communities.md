---
title: Implementación de comunidades
seo-title: Implementación de comunidades
description: Cómo implementar AEM Communities
seo-description: Cómo implementar AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 2%

---


# Implementación de comunidades {#deploying-communities}

## Requisitos previos {#prerequisites}

* [Plataforma AEM 6.4](../../help/sites-deploying/deploy.md)

* Licencia de AEM Communities

* Licencias opcionales para:

   * [Funciones de Adobe Analytics para Comunidades](analytics.md)
   * [MongoDB para MSRP](msrp.md)
   * [Adobe Cloud para ASRP](asrp.md)

## Lista de comprobación de instalación {#installation-checklist}

**Para la plataforma[AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Instalar las últimas actualizaciones de [AEM 6.4](#aem-updates)

* Si no utiliza los puertos predeterminados (4502, 4503), [configure los agentes de replicación](#replication-agents-on-author)
* [replicar la clave criptográfica](#replicate-the-crypto-key)
* Si soporta la globalización, [configure la traducción automatizada](../../help/sites-administering/translation.md)

   (la configuración de muestra se proporciona para el desarrollo)

**Para la capacidad de[Comunidades](overview.md)**

* Si implementa un conjunto de servidores [de](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)publicación, [identifique al editor principal](#primary-publisher)

* [Habilitar el servicio de túnel](#tunnel-service-on-author)
* [Habilitar inicio de sesión social](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configurar Adobe Analytics](analytics.md)
* Configurar un servicio de correo electrónico [predeterminado](email.md)
* Identifique la opción para el almacenamiento [UGC](working-with-srp.md) compartido (**SRP**)

   * Si MongoDB SRP [(MSRP)](msrp.md)

      * [Instalar y configurar MongoDB](msrp.md#mongodb-configuration)
      * [Configurar Solr](solr.md)
      * [Seleccionar MSRP](srp-config.md)
   * Si la base de datos relacional es SRP [(DSRP)](dsrp.md)

      * [Instalación del controlador JDBC para MySQL](#jdbc-driver-for-mysql)
      * [Instalar y configurar MySQL para DSRP](dsrp-mysql.md)
      * [Configurar Solr](solr.md)
      * [Seleccionar DSRP](srp-config.md)
   * Si Adobe SRP [(ASRP)](asrp.md)

      * Trabajar con el representante de cuentas para aprovisionar
      * [Seleccionar ASRP](srp-config.md)
   * Si JCR SRP [(JSRP)](jsrp.md)

      * No es una tienda UGC compartida:

         * UGC nunca se replica
         * UGC solo visible en AEM instancia o clúster en el que se introdujo
      * El valor predeterminado es JSRP

   Para la función de **[habilitación](overview.md#enablement-community)**

   * [Instalar y configurar FFmpeg](ffmpeg.md)
   * [Instalación del controlador JDBC para MySQL](#jdbc-driver-for-mysql)
   * [Instalación del motor AEM Communities SCORM](#scorm-package)
   * [Instalar y configurar MySQL para la habilitación](mysql.md)






## Latest Releases {#latest-releases}

AEM 6.4 Buques GA de Comunidades con paquete Communities. Para conocer las actualizaciones de AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities), consulte [AEM Notas](/help/release-notes/release-notes.md#release-information)de la versión 6.4.

### Actualizaciones de AEM 6.4 {#aem-updates}

A partir de AEM 6.3, las actualizaciones a las comunidades se entregan como parte de AEM paquetes de correcciones acumulativas y Service Packs.

Para obtener las últimas actualizaciones de AEM 6.4, asegúrese de comprobar los paquetes de correcciones acumulativas de [Adobe Experience Manager 6.4 y los Service Packs](https://helpx.adobe.com/es/experience-manager/aem-releases-updates.html).

### Historial de versiones {#version-history}

Al igual que en AEM 6.4 y versiones posteriores, las funciones y revisiones de AEM Communities forman parte de los paquetes de correcciones y los Service Packs acumulativos de AEM Communities. Por lo tanto, no hay paquetes de funciones independientes.

### Controlador JDBC para MySQL {#jdbc-driver-for-mysql}

Dos funciones de Communities utilizan una base de datos MySQL:

* Para [la habilitación](enablement.md): grabación de actividades y alumnos SCORM
* Para [DSRP](dsrp.md): almacenamiento de contenido generado por el usuario (UGC)

El conector MySQL debe obtenerse e instalarse por separado.

Los pasos necesarios son:

1. Descargue el archivo ZIP de [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La versión debe ser >= 5.1.38

1. Extraer mysql-Connector-java-&lt;version>-bin.jar (paquete) del archivo

1. Utilice la consola web para instalar y inicio del paquete:

   * Por ejemplo, http://localhost:4502/system/console/bundles
   * Seleccione **`Install/Update`**
   * Examinar... para seleccionar el paquete extraído del archivo ZIP descargado
   * Compruebe que el controlador JDBC de *Oracle Corporation para MySQLcom.mysql.jdbc* está activo y inicio si no (o compruebe los registros)

1. Si realiza la instalación en una implementación existente después de haber configurado JDBC, vuelva a conectar JDBC al nuevo conector al volver a guardar la configuración JDBC desde la consola web:

   * Por ejemplo, http://localhost:4502/system/console/configMgr
   * Localizar `Day Commons JDBC Connections Pool` configuración
   * Seleccionar para abrir
   * Seleccione `Save`

1. Repita los pasos 3 y 4 en todas las instancias de creación y publicación

Encontrará más información sobre la instalación de paquetes en la página Consola [](/help/sites-deploying/web-console.md#bundles) web.

#### Ejemplo: Paquete de conector MySQL instalado {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Paquete SCORM {#scorm-package}

El Modelo de referencia de objetos de contenido compartido (SCORM) es una colección de estándares y especificaciones para el aprendizaje electrónico. SCORM también define cómo se puede empaquetar el contenido en un archivo ZIP transferible.

El motor AEM Communities SCORM es necesario para la [función de habilitación](overview.md#enablement-community) . Los paquetes de Scorm admitidos en la versión 6.4 de AEM Communities son:

* **[cq -social- scorm -package, versión 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Este paquete SCORM es compatible con todas las versiones de comunidades AEM 6.4.

* **[cq -social- scorm -package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)**incluye el motor[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/). Este paquete SCORM es compatible AEM comunidades 6.4.2.x y posteriores.

Para una nueva instalación del motor SCORM, debe utilizarse el paquete que contiene [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (que es [ cq -social- scorm -package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)). Para que pueda reproducir recursos de aprendizaje compatibles con SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para instalar un paquete SCORM por primera vez

1. Instale el **[paquete cq-social-scorm-package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Descargue **`/libs/social/config/scorm/database_scormengine_data.sql`** de la instancia cq y ejecútela en el servidor mysql para crear un esquema de scormEngineDB actualizado.
1. Añada `/content/communities/scorm/RecordResults` en la propiedad Rutas excluidas en el filtro CSRF desde `https://<hostname>;:<port>/system/console/configMgr` los editores.

Las instalaciones SCORM existentes se pueden actualizar a [**cq-social-scorm-package, versión 2.2.2 **](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)(que utiliza[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), si el contenido del curso creado requiere SCORM 2017.1.

>[!NOTE]
>
>La actualización al paquete SCORM 2017.1 requiere la migración de la base de datos existente (como se explica más adelante).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para actualizar la versión del motor SCORM

1. Haga una copia de seguridad del esquema ScormEngineDB.
1. Instale el **[paquete cq-social-scorm-package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Descargue el paquete `/libs/social/config/scorm/ScormEngine.zip` y extraiga el mismo.
1. Vaya a la carpeta **del instalador** del directorio extraído.
1. Actualice `SystemDatabaseConnectionString` con el `scorm db connection url` archivo **[!UICONTROL EngineInstall.xml]**.
1. Ejecute la herramienta de actualización de esquema mysql en la carpeta del instalador con el comando:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Monitoree `engine_upgrade.log` el archivo para cualquier tipo de error y estado de actualización de esquema.
1. Añada `/content/communities/scorm/RecordResults` en la propiedad Rutas **** excluidas en el filtro CSRF desde `https://<hostname>:<port>/system/console/configMgr` los editores.

### Registro SCORM {#scorm-logging}

Como instalado, toda la actividad de habilitación se registra de forma incorrecta en la consola del sistema.

Si lo desea, el nivel de registro se puede establecer en WARN para el `RusticiSoftware.*` paquete.

Para trabajar con registros, consulte [Uso de registros de auditoría y archivos](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)de registro.

### MLS AEM avanzado {#aem-advanced-mls}

Para que la colección SRP (MSRP o DSRP) admita la búsqueda multilingüe avanzada (MLS), se necesitan nuevos complementos Solr además de una configuración personalizada de esquema y Solr. Todos los elementos necesarios se empaquetan en un archivo zip descargable.

La descarga avanzada de MLS (también conocida como &#39;phasetwo&#39;) está disponible en el repositorio de Adobe:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Versión 1.2.40, 6 de abril de 2016
   * Descargue AEM-SOLR-MLS-phasetwo-1.2.40.zip

Para obtener información detallada y sobre la instalación, visite [Solr Configuration](solr.md) for SRP.

### Acerca de los vínculos para compartir paquetes {#about-links-to-package-share}

**Paquetes visibles en Adobe AEM Cloud**

Los vínculos a los paquetes de esta página no requieren ninguna instancia de AEM en ejecución, ya que son para el uso compartido de paquetes en `adobeaemcloud.com`. Mientras los paquetes son visibles, el `Install`botón es para instalar los paquetes en un sitio alojado de Adobe. Si desea realizar la instalación en una instancia de AEM local, la selección `Install`producirá un error.

**Cómo instalar en una instancia de AEM local**

Para instalar los paquetes visibles en `adobeaemcloud.com` una instancia de AEM local, el paquete debe descargarse primero en un disco local:

* Select the **[!UICONTROL Assets]** tab
* Seleccione **[!UICONTROL descargar en disco]**

En la instancia de AEM local, utilice el administrador de paquetes (por ejemplo, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)) para cargar en el repositorio de paquetes de AEM local.

Como alternativa, si accede al paquete mediante el uso compartido de paquetes desde la instancia de AEM local (por ejemplo, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), el `Download`botón se descargará en el repositorio de paquetes de la instancia de AEM local.

Una vez en el repositorio de paquetes de la instancia de AEM local, utilice el administrador de paquetes para instalar el paquete.

Para obtener más información, visite [Cómo trabajar con paquetes](../../help/sites-administering/package-manager.md#package-share).

## Implementaciones recomendadas {#recommended-deployments}

En AEM Communities, un almacén común se utiliza para almacenar contenido generado por el usuario (UGC) y se le suele llamar proveedor de recursos de [almacenamiento (SRP)](working-with-srp.md). La implementación recomendada se centra en elegir una opción de SRP para la tienda común.

El almacén común admite moderación y análisis de UGC en el entorno de publicación, al tiempo que elimina la necesidad de [replicación](sync.md) de UGC.

* [Almacenamiento](working-with-srp.md)de contenido de la comunidad: analiza las opciones de almacenamiento de SRP para las comunidades AEM

* [Topologías](topologies.md)recomendadas: analiza la topología que se va a usar en función del caso de uso y la opción de SRP

## Actualización {#upgrading}

Al actualizar a la plataforma AEM 6.4 desde versiones anteriores de AEM, es importante leer Actualización a AEM 6.4.

Además de actualizar la plataforma, lea [Actualización a AEM Communities 6.4](upgrade.md) para conocer los cambios de las comunidades.

## Configuraciones {#configurations}

### Editor principal {#primary-publisher}

Cuando la implementación elegida es un conjunto de servidores [de](topologies.md#tarmk-publish-farm)publicación, una instancia de publicación AEM debe identificarse como la **`primary publisher`** de actividades que no deben producirse en todas las instancias, como las funciones que dependen de **las notificaciones** o **Adobe Analytics**.

De forma predeterminada, la configuración de `AEM Communities Publisher Configuration` OSGi se configura con la casilla de verificación **`Primary Publisher`** activada, de modo que todas las instancias de publicación de un conjunto de servidores de publicación se identificarán como principales.

Por lo tanto, es necesario **editar la configuración en todas las instancias** de publicación secundarias para desmarcar la **`Primary Publisher`** casilla de verificación.

![chlimage_1-411](assets/chlimage_1-411.png)

Para el resto de instancias de publicación (secundarias) en un conjunto de servidores de publicación:

* Iniciar sesión con privilegios de administrador
* Acceso a la consola [web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localice la variable `AEM Communities Publisher Configuration`
* Seleccione el icono de edición
* Desmarcar la casilla Publicador **** principal
* Seleccione **[!UICONTROL Guardar]**

### Agentes de replicación en el autor {#replication-agents-on-author}

La replicación se utiliza para el contenido del sitio creado en el entorno de publicación, como grupos de la comunidad, así como para administrar miembros y grupos de miembros desde el entorno de creación mediante el servicio [de](#tunnel-service-on-author)túnel.

Para el publicador principal, asegúrese de que la configuración [del agente de](../../help/sites-deploying/replication.md) replicación identifique correctamente al servidor de publicación y al usuario autorizado. El usuario autorizado predeterminado `admin,` ya tiene los permisos adecuados (es miembro de `Communities Administrators`).

Para que algún otro usuario tenga los permisos adecuados, debe agregarse como miembro al grupo de `administrators` usuarios (también como miembro de `Communities Administrators`).

Hay dos agentes de replicación en el entorno de creación que necesitan configurar correctamente la configuración de transporte.

* Acceso a la consola de replicación en el autor

   * Desde la navegación global: **[!UICONTROL Herramientas > Implementación > Replicación > Agentes en el autor]**

* Siga el mismo procedimiento para ambos agentes:

   * **Agente predeterminado (publicación)**
   * **Agente de replicación inversa (publicar inversa)**

      1. Seleccione el agente
      1. Select **[!UICONTROL edit]**
      1. Select the **[!UICONTROL Transport]** tab
      1. Si no es un puerto `4503`, edite el **[!UICONTROL URI]** para especificar el puerto correcto
      1. Si no es usuario `admin`, edite el **[!UICONTROL usuario]** y la **[!UICONTROL contraseña]** para especificar un miembro del grupo de `administrators` usuarios

Las siguientes imágenes muestran los resultados de cambiar el puerto de 4503 a 6103 por:

#### Agente predeterminado (publicación) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agente de replicación inversa (publicar inversa) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Servicio de túnel en el autor {#tunnel-service-on-author}

Al utilizar el entorno de autor para [crear sitios](sites-console.md), [modificar propiedades](sites-console.md#modifying-site-properties) del sitio o [administrar miembros](members.md)de la comunidad, es necesario acceder a los miembros (usuarios) registrados en el entorno de publicación, no a los usuarios registrados en el autor.

El servicio de túnel proporciona este acceso mediante el agente de replicación del autor.

Para habilitar el servicio de túnel:

* En **autor**
* Iniciar sesión con privilegios administrativos
* Si publisher no es localhost:4503 o el usuario de transporte no lo es `admin`,

   A continuación, [configure el agente de replicación](#replication-agents-on-author)

* Acceso a la consola [web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Localice la variable `AEM Communities Publish Tunnel Service`
* Seleccione el icono de edición
* Marque la casilla **[!UICONTROL habilitar]** .
* Seleccione **[!UICONTROL Guardar]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Replicar la clave de cifrado {#replicate-the-crypto-key}

Existen dos funciones de AEM Communities que requieren que todas las instancias de servidor AEM utilicen las mismas claves de cifrado. Son [Analytics](analytics.md) y [ASRP](asrp.md).

A partir de AEM 6.3, el material clave se almacena en el sistema de archivos y ya no en el repositorio.

Para copiar el material clave del autor en todos los demás casos, es necesario:

* Acceda a la instancia de AEM, normalmente una instancia de autor, que contiene el material clave que copiar

   * Localizar el `com.adobe.granite.crypto.file` paquete en el sistema de archivos local

      Por ejemplo,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * El `bundle.info` archivo identificará el paquete
   * Navegar a la carpeta de datos

      Por ejemplo,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copiar los archivos hmac y principal del nodo



* Para cada instancia de AEM destinatario

   * Navegar a la carpeta de datos

      Por ejemplo,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Pegar los 2 archivos copiados anteriormente
   * Es necesario [actualizar el paquete](#refresh-the-granite-crypto-bundle) Granite Crypto si la instancia de destinatario AEM se está ejecutando en ese momento


>[!CAUTION]
>
>Si ya se ha configurado otra característica de seguridad basada en claves criptográficas, replicar las claves criptográficas podría dañar la configuración. Para obtener ayuda, [póngase en contacto con el servicio de atención](https://helpx.adobe.com/es/marketing-cloud/contact-support.html)al cliente.

#### Replicación del repositorio {#repository-replication}

El hecho de tener el material clave almacenado en el repositorio, como ocurrió con AEM 6.2 y versiones anteriores, se puede conservar especificando la siguiente propiedad del sistema en el primer inicio de cada instancia de AEM (que crea el repositorio inicial):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es importante verificar que el agente de [replicación del autor](#replication-agents-on-author) esté correctamente configurado.

Con el material clave almacenado en el repositorio, la manera de replicar la clave criptográfica de autor a otras instancias es la siguiente:

Uso del [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* vaya a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* select `/etc/key`
* abrir `Replication` , ficha
* select `Replicate`

* [actualizar el paquete Granite Crypto](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Actualizar el paquete de criptografía de granito {#refresh-the-granite-crypto-bundle}

* En cada instancia de publicación, acceda a la consola [web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [https://&lt;servidor>:&lt;puerto>/sistema/consola/paquetes](http://localhost:4503/system/console/bundles)

* Localizar `Adobe Granite Crypto Support` paquete (com.adobe.granite.crypto)
* Seleccionar **[!UICONTROL actualización]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Después de un momento, debería aparecer un diálogo de **éxito** :

   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Si utiliza el servidor Apache HTTP, asegúrese de utilizar el nombre de servidor correcto para todas las entradas relevantes.

En particular, tenga cuidado de utilizar el nombre de servidor correcto, no `localhost`, en el `RedirectMatch`.

#### muestra de httpd.conf {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site:
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Si utiliza un despachante, consulte:

* Documentación de AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)
* [Instalación de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configuración de Dispatcher para Comunidades](dispatcher.md)
* [Problemas conocidos](troubleshooting.md#dispatcher-refetch-fails)

## Documentación de comunidades relacionadas {#related-communities-documentation}

* Visite [Administración de sitios](administer-landing.md) de comunidades para obtener información sobre cómo crear un sitio de comunidad, configurar plantillas de sitio de comunidad, moderar contenido de comunidad, administrar miembros y configurar mensajes.

* Visite [Desarrollar comunidades](communities.md) para conocer el marco de componentes sociales (SCF) y personalizar componentes y características de Comunidades.

* Visite [Creación de componentes](author-communities.md) de comunidades para obtener información sobre cómo crear y configurar componentes de comunidades.

