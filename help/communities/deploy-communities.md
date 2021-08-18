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
exl-id: 0b7496f0-0b3c-4d12-a659-d95744157f14
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '2145'
ht-degree: 2%

---

# Implementación de comunidades {#deploying-communities}

## Requisitos previos {#prerequisites}

* [Plataforma de AEM 6.4](../../help/sites-deploying/deploy.md)

* Licencia de AEM Communities

* Licencias opcionales para:

   * [Funciones de Adobe Analytics para Communities](analytics.md)
   * [MongoDB para MSRP](msrp.md)
   * [Adobe Cloud para ASRP](asrp.md)

## Lista de comprobación de instalación {#installation-checklist}

**Para la plataforma de  [AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Instale las últimas [AEM 6.4 Actualizaciones](#aem-updates)

* Si no utiliza los puertos predeterminados (4502, 4503), [configure los agentes de replicación](#replication-agents-on-author)
* [replicar la clave criptográfica](#replicate-the-crypto-key)
* Si se admite la globalización, [configure la traducción automatizada](../../help/sites-administering/translation.md)

   (la configuración de muestra se proporciona para el desarrollo)

**Para la capacidad  [Comunidades](overview.md)**

* Si se implementa un [conjunto de servidores de publicación](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), [identifique al editor principal](#primary-publisher)

* [Habilitar el servicio de túnel](#tunnel-service-on-author)
* [Habilitar inicio de sesión social](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configuración de Adobe Analytics](analytics.md)
* Configurar un [servicio de correo electrónico predeterminado](email.md)
* Identifique la opción para [almacenamiento UGC compartido](working-with-srp.md) (**SRP**)

   * Si MongoDB SRP [(MSRP)](msrp.md)

      * [Instalar y configurar MongoDB](msrp.md#mongodb-configuration)
      * [Configurar Solr](solr.md)
      * [Seleccionar MSRP](srp-config.md)
   * Si la base de datos relacional SRP [(DSRP)](dsrp.md)

      * [Instale el controlador JDBC para MySQL](#jdbc-driver-for-mysql)
      * [Instalar y configurar MySQL para DSRP](dsrp-mysql.md)
      * [Configurar Solr](solr.md)
      * [Seleccionar DSRP](srp-config.md)
   * Si el Adobe SRP [(ASRP)](asrp.md)

      * Póngase en contacto con su representante de cuentas para realizar el aprovisionamiento
      * [Seleccionar ASRP](srp-config.md)
   * Si JCR SRP [(JSRP)](jsrp.md)

      * No es una tienda UGC compartida:

         * UGC nunca se replica
         * UGC solo visible en AEM instancia o clúster en el que se introdujo
      * El valor predeterminado es JSRP

   Para la **[función de habilitación](overview.md#enablement-community)**

   * [Instalar y configurar FFmpeg](ffmpeg.md)
   * [Instale el controlador JDBC para MySQL](#jdbc-driver-for-mysql)
   * [Instalación del motor AEM Communities SCORM](#scorm-package)
   * [Instalar y configurar MySQL para la habilitación](mysql.md)






## Últimas versiones {#latest-releases}

AEM 6.4 Communities GA incluye el paquete Communities. Para obtener información sobre las actualizaciones de AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities), consulte [AEM Notas de la versión 6.4](/help/release-notes/release-notes.md#release-information).

### Actualizaciones de AEM 6.4 {#aem-updates}

A partir de AEM 6.3, las actualizaciones para las comunidades se entregan como parte de AEM paquetes de correcciones acumulativas y Service Packs.

Para las últimas actualizaciones de AEM 6.4, asegúrese de comprobar [Paquetes de correcciones acumulativas y Service Packs de Adobe Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=es).

### Historial de versiones {#version-history}

Al igual que en AEM 6.4 y versiones posteriores, las funciones y revisiones de AEM Communities forman parte de los paquetes fijos y los service packs acumulativos de AEM Communities. Por lo tanto, no hay paquetes de funciones independientes.

### Controlador JDBC para MySQL {#jdbc-driver-for-mysql}

Dos funciones de Communities utilizan una base de datos MySQL:

* Para [habilitación](enablement.md): grabación de actividades y estudiantes SCORM
* Para [DSRP](dsrp.md): almacenamiento del contenido generado por el usuario (UGC)

El conector MySQL debe obtenerse e instalarse por separado.

Los pasos necesarios son:

1. Descargue el archivo ZIP desde [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La versión debe ser >= 5.1.38

1. Extraiga mysql-connector-java-&lt;version>-bin.jar (paquete) del archivo

1. Utilice la consola web para instalar e iniciar el paquete:

   * Por ejemplo, http://localhost:4502/system/console/bundles
   * Seleccione **`Install/Update`**
   * Examinar... para seleccionar el paquete extraído del archivo ZIP descargado
   * Compruebe que el controlador JDBC de *Oracle Corporation para MySQLcom.mysql.jdbc* esté activo, e inícielo si no (o compruebe los registros)

1. Si realiza la instalación en una implementación existente después de haber configurado JDBC, vuelva a conectar JDBC al nuevo conector y vuelva a guardar la configuración JDBC desde la consola web:

   * Por ejemplo, http://localhost:4502/system/console/configMgr
   * Localizar la configuración `Day Commons JDBC Connections Pool`
   * Seleccione para abrir
   * Seleccione `Save`

1. Repita los pasos 3 y 4 en todas las instancias de autor y publicación

Encontrará más información sobre la instalación de paquetes en la página [Consola Web](/help/sites-deploying/web-console.md#bundles).

#### Ejemplo: Paquete de conector MySQL instalado {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Paquete SCORM {#scorm-package}

El Modelo de referencia de objetos de contenido compartible (SCORM) es una colección de estándares y especificaciones para el aprendizaje electrónico. SCORM también define cómo el contenido puede empaquetarse en un archivo ZIP transferible.

El motor AEM Communities SCORM es necesario para la función [habilitación](overview.md#enablement-community). Los paquetes de valoración compatibles con la versión 6.4 de AEM Communities son:

* **[cq -social- scorm -package, versión 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Este paquete SCORM es compatible con todas las versiones de AEM 6.4 Communities.

* **[cq -social-scorm -package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)** incluye motor  [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) . Este paquete SCORM es compatible con AEM comunidades 6.4.2.x en adelante.

Para una nueva instalación del motor SCORM, se debe utilizar el paquete que contiene [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (que es [ cq -social-scorm -package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)). Para poder reproducir recursos de aprendizaje compatibles con SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para instalar un paquete SCORM por primera vez

1. Instale el **[cq-social-scorm-package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Descargue **`/libs/social/config/scorm/database_scormengine_data.sql`** de la instancia cq y ejecútela en el servidor mysql para crear un esquema de scormEngineDB actualizado.
1. Agregue `/content/communities/scorm/RecordResults` en la propiedad Rutas excluidas del filtro CSRF de `https://<hostname>;:<port>/system/console/configMgr` a los editores.

Las instalaciones existentes de SCORM se pueden actualizar a [**cq-social-scorm-package, versión 2.2.2**](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg) (que utiliza [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), si el contenido del curso creado requiere SCORM 2017.1.

>[!NOTE]
>
>La actualización al paquete SCORM 2017.1 requiere la migración de la base de datos existente (como se explica más adelante).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para actualizar la versión del motor SCORM

1. Haga una copia de seguridad del esquema ScormEngineDB.
1. Instale el **[cq-social-scorm-package, versión 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Descargue el paquete de `/libs/social/config/scorm/ScormEngine.zip` y extraiga el mismo.
1. Vaya a la carpeta **Installer** del directorio extraído.
1. Actualice `SystemDatabaseConnectionString` con su `scorm db connection url` en el archivo **[!UICONTROL EngineInstall.xml]**.
1. Ejecute la herramienta de actualización de esquema mysql en la carpeta del instalador con el comando:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Supervise el archivo `engine_upgrade.log` para cualquier tipo de error y estado de actualización del esquema.
1. Agregue `/content/communities/scorm/RecordResults` en la propiedad **[!UICONTROL Rutas excluidas]** en el filtro CSRF de `https://<hostname>:<port>/system/console/configMgr` en los editores.

### Registro de SCORM {#scorm-logging}

Como instalado, toda la actividad de habilitación se registra de forma incorrecta en la consola del sistema.

Si lo desea, el nivel de registro se puede configurar como WARN para el paquete `RusticiSoftware.*`.

Para trabajar con registros, consulte [Trabajo con registros de auditoría y archivos de registro](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### MLS AEM Advanced {#aem-advanced-mls}

Para que la colección SRP (MSRP o DSRP) admita la búsqueda multilingüe avanzada (MLS), se necesitan nuevos complementos Solr además de un esquema personalizado y una configuración Solr. Todos los elementos necesarios se empaquetan en un archivo zip descargable.

La descarga avanzada de MLS (también conocida como &#39;phasetwo&#39;) está disponible en el repositorio de Adobe:

* AEM-SOLR-MLS-phasetwo
Para obtener el paquete MLS avanzado, consulte [AEM Advanced MLS](deploy-communities.md#aem-advanced-mls) en la sección de implementación de la documentación.

   * Versión 1.2.40, 6 de abril de 2016
   * Descargue AEM-SOLR-MLS-phasetwo-1.2.40.zip

Para obtener más información sobre la instalación, visite [Solr Configuration](solr.md) para SRP.

### Acerca de los vínculos a Package Share {#about-links-to-package-share}

**Paquetes visibles en Adobe AEM Cloud**

Los vínculos a paquetes en esta página no requieren ninguna instancia de AEM en ejecución, ya que son para el uso compartido de paquetes en `adobeaemcloud.com`. Mientras los paquetes son visibles, el botón `Install`es para instalar los paquetes en un sitio alojado en Adobe. Si se pretende instalar en una instancia de AEM local, seleccionar `Install`producirá un error.

**Instalación en una instancia de AEM local**

Para instalar los paquetes visibles en `adobeaemcloud.com` en una instancia de AEM local, el paquete debe descargarse primero en un disco local:

* Seleccione la pestaña **[!UICONTROL Assets]**
* Seleccione **[!UICONTROL descargar al disco]**

En la instancia de AEM local, utilice el administrador de paquetes (por ejemplo [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)) para cargar en el repositorio de paquetes de AEM local.

Alternativamente, al acceder al paquete utilizando el paquete compartido desde la instancia de AEM local (por ejemplo, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), el botón `Download`se descargará en el repositorio de paquetes de la instancia de AEM local.

Una vez en el repositorio de paquetes de la instancia de AEM local, utilice el administrador de paquetes para instalar el paquete.

Para obtener más información, visite [Cómo trabajar con paquetes](../../help/sites-administering/package-manager.md#package-share).

## Implementaciones recomendadas {#recommended-deployments}

En AEM Communities, un almacén común se utiliza para almacenar contenido generado por el usuario (UGC) y a menudo se denomina [proveedor de recursos de almacenamiento (SRP)](working-with-srp.md). La implementación recomendada se centra en elegir una opción de SRP para el almacén común.

El almacén común admite la moderación y el análisis de UGC en el entorno de publicación, a la vez que elimina la necesidad de [replicación](sync.md) de UGC.

* [Almacenamiento de contenido de la comunidad](working-with-srp.md): analiza las opciones de almacenamiento de SRP para comunidades AEM

* [Topologías](topologies.md) recomendadas: analiza la topología que se va a usar en función del caso de uso y la elección de SRP

## Actualización {#upgrading}

Al actualizar a la plataforma AEM 6.4 desde versiones anteriores de AEM, es importante leer Actualización a AEM 6.4.

Además de actualizar la plataforma, lea [Actualización a AEM Communities 6.4](upgrade.md) para obtener más información sobre los cambios de Communities.

## Configuraciones {#configurations}

### Editor principal {#primary-publisher}

Cuando la implementación elegida es una [granja de publicación](topologies.md#tarmk-publish-farm), entonces una instancia de publicación AEM debe identificarse como la **`primary publisher`** para las actividades que no deben producirse en todas las instancias, como las funciones que dependen de **notificaciones** o **Adobe Analytics**.

De forma predeterminada, la configuración OSGi `AEM Communities Publisher Configuration` se configura con la casilla **`Primary Publisher`** marcada, de modo que todas las instancias de publicación en un conjunto de servidores de publicación se autoidentificarán como el principal.

Por lo tanto, es necesario **editar la configuración en todas las instancias de publicación secundarias** para desmarcar la casilla de verificación **`Primary Publisher`**.

![chlimage_1-411](assets/chlimage_1-411.png)

Para todas las demás instancias de publicación (secundarias) en un conjunto de servidores de publicación:

* Iniciar sesión con privilegios de administrador
* Acceda a la [consola web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Busque el `AEM Communities Publisher Configuration`
* Seleccione el icono de edición
* Desmarque la casilla **[!UICONTROL Primary Publisher]**
* Seleccione **[!UICONTROL Guardar]**

### Agentes de replicación en Author {#replication-agents-on-author}

La replicación se utiliza para el contenido del sitio creado en el entorno de publicación, como los grupos de comunidades, así como para administrar miembros y grupos de miembros del entorno de creación mediante el [servicio de túnel](#tunnel-service-on-author).

Para el editor principal, asegúrese de que [Replication Agent Config](../../help/sites-deploying/replication.md) identifica correctamente el servidor de publicación y el usuario autorizado. El usuario autorizado predeterminado, `admin,` ya tiene los permisos adecuados (es miembro de `Communities Administrators`).

Para que algún otro usuario tenga los permisos adecuados, debe agregarlos como miembro del grupo de usuarios `administrators` (también miembro de `Communities Administrators`).

Hay dos agentes de replicación en el entorno de creación que necesitan que la configuración del transporte sea correcta.

* Acceso a la consola Replicación en el autor

   * Desde la navegación global: **[!UICONTROL Herramientas > Implementación > Replicación > Agentes en author]**

* Siga el mismo procedimiento para ambos agentes:

   * **Agente predeterminado (publicar)**
   * **Agente de replicación inversa (publicar inversa)**

      1. Seleccione el agente
      1. Seleccione **[!UICONTROL editar]**
      1. Seleccione la pestaña **[!UICONTROL Transport]**
      1. Si no es el puerto `4503`, edite el **[!UICONTROL URI]** para especificar el puerto correcto
      1. Si no es el usuario `admin`, edite **[!UICONTROL Usuario]** y **[!UICONTROL Contraseña]** para especificar un miembro del grupo de usuarios `administrators`

Las siguientes imágenes muestran los resultados de cambiar el puerto de 4503 a 6103 mediante:

#### Agente predeterminado (publicar) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agente de replicación inversa (publicar inversa) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Servicio de túnel en Author {#tunnel-service-on-author}

Al utilizar el entorno de creación para [crear sitios](sites-console.md), [modificar propiedades del sitio](sites-console.md#modifying-site-properties) o [administrar miembros de la comunidad](members.md), es necesario acceder a los miembros (usuarios) registrados en el entorno de publicación, no a los usuarios registrados en el autor.

El servicio de túnel proporciona este acceso mediante el agente de replicación en el autor.

Para habilitar el servicio de túnel:

* En **autor**
* Iniciar sesión con privilegios administrativos
* Si publisher no es localhost:4503 o el usuario de transporte no es `admin`,

   A continuación [configure el agente de replicación](#replication-agents-on-author)

* Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Busque el `AEM Communities Publish Tunnel Service`
* Seleccione el icono de edición
* Marque la casilla **[!UICONTROL enable]**
* Seleccione **[!UICONTROL Guardar]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Replicar la clave criptográfica {#replicate-the-crypto-key}

Existen dos funciones de AEM Communities que requieren que todas las instancias de servidor AEM utilicen las mismas claves de cifrado. Son [Analytics](analytics.md) y [ASRP](asrp.md).

A partir de AEM 6.3, el material clave se almacena en el sistema de archivos y ya no en el repositorio.

Para copiar el material clave del autor en todas las demás instancias, es necesario:

* Acceda a la instancia de AEM, normalmente una instancia de autor, que contiene el material clave que desea copiar

   * Localice el paquete `com.adobe.granite.crypto.file` en el sistema de archivos local

      Por ejemplo,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * El archivo `bundle.info` identificará el paquete
   * Vaya a la carpeta de datos

      Por ejemplo,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copiar los archivos de nodo principal y hmac



* Para cada instancia de AEM de destino

   * Vaya a la carpeta de datos

      Por ejemplo,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Pegar los 2 archivos copiados anteriormente
   * Es necesario [actualizar el paquete Granite Crypto](#refresh-the-granite-crypto-bundle) si la instancia de AEM de destino se está ejecutando actualmente


>[!CAUTION]
>
>Si ya se ha configurado otra función de seguridad basada en las claves criptográficas, replicar las claves criptográficas podría dañar la configuración. Para obtener ayuda, [póngase en contacto con el servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html).

#### Replicación del repositorio {#repository-replication}

Tener el material clave almacenado en el repositorio, como ocurrió con AEM 6.2 y anteriores, se puede conservar especificando la siguiente propiedad del sistema en el primer inicio de cada instancia de AEM (que crea el repositorio inicial):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Es importante verificar que el [agente de replicación del autor](#replication-agents-on-author) está configurado correctamente.

Con el material clave almacenado en el repositorio, la manera de replicar la clave criptográfica de autor a otras instancias es la siguiente:

Uso del [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* vaya a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* select `/etc/key`
* abrir la pestaña `Replication`
* seleccione `Replicate`

* [actualizar el paquete Granite Crypto](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Actualizar el paquete de criptografía de Granite {#refresh-the-granite-crypto-bundle}

* En cada instancia de publicación, acceda a la [Consola web](../../help/sites-deploying/configuring-osgi.md)

   * Por ejemplo, [https://&lt;server>:&lt;port>/system/console/bundles](http://localhost:4503/system/console/bundles)

* Busque el paquete `Adobe Granite Crypto Support` (com.adobe.granite.crypto)
* Seleccione **[!UICONTROL Actualizar]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Después de un momento, debería aparecer un cuadro de diálogo **Success**:

   `Operation completed successfully.`

### Servidor HTTP Apache {#apache-http-server}

Si utiliza el servidor HTTP Apache, asegúrese de utilizar el nombre de servidor correcto para todas las entradas relevantes.

En particular, tenga cuidado de usar el nombre de servidor correcto, no `localhost`, en el `RedirectMatch`.

#### ejemplo de httpd.conf {#httpd-conf-sample}

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

Si utiliza un Dispatcher, consulte:

* Documentación de AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)
* [Instalación de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configuración de Dispatcher para Communities](dispatcher.md)
* [Problemas conocidos](troubleshooting.md#dispatcher-refetch-fails)

## Documentación de Communities relacionadas {#related-communities-documentation}

* Visite [Administración de sitios de comunidades](administer-landing.md) para obtener información sobre cómo crear un sitio de comunidad, configurar las plantillas de sitio de la comunidad, moderar el contenido de la comunidad, administrar miembros y configurar mensajes.

* Visite [Desarrollo de comunidades](communities.md) para obtener más información sobre el marco de componentes sociales (SCF) y la personalización de componentes y características de Communities.

* Visite [Creación de componentes de comunidades](author-communities.md) para aprender a crear y configurar componentes de Communities.
