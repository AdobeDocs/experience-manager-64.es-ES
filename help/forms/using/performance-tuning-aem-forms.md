---
title: Ajuste del rendimiento del servidor AEM Forms
seo-title: Ajuste del rendimiento del servidor AEM Forms
description: Para que AEM Forms funcione de forma óptima, puede ajustar la configuración de caché y los parámetros de JVM. Además, el uso de un servidor web puede mejorar el rendimiento de la implementación de AEM Forms.
seo-description: Para que AEM Forms funcione de forma óptima, puede ajustar la configuración de caché y los parámetros de JVM. Además, el uso de un servidor web puede mejorar el rendimiento de la implementación de AEM Forms.
uuid: 77eaeecc-ca52-4d3d-92e6-1ab4d91b9edd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 5d672b56-00c4-46a0-974b-e174fbdf07d6
role: Admin
exl-id: bc750571-08a5-414c-aed5-4e839f6695ae
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 2%

---

# Ajuste del rendimiento del servidor AEM Forms {#performance-tuning-of-aem-forms-server}

Este artículo analiza las estrategias y prácticas recomendadas que puede implementar para reducir los cuellos de botella y optimizar el rendimiento de su implementación de AEM Forms.

## Configuración de caché {#cache-settings}

Puede configurar y controlar la estrategia de almacenamiento en caché para AEM Forms mediante el componente **Configuraciones móviles de Forms** en AEM consola de configuración web en:

* (AEM Forms en OSGi) `https://[server]:[port]/system/console/configMgr`
* (AEM Forms en JEE) `https://[server]:[port]/lc/system/console/configMgr`

Las opciones disponibles para el almacenamiento en caché son las siguientes:

* **Ninguno**: Fuerza que no almacene en caché ningún artefacto. Esto, en la práctica, ralentiza el rendimiento y requiere una alta disponibilidad de memoria debido a la ausencia de caché.
* **Conservador**: Dicta para almacenar en caché solo los artefactos intermedios que se generan antes de procesar el formulario, como una plantilla que contenga fragmentos e imágenes en línea.
* **Agresivo**: Impone almacenar en caché casi todo lo que se pueda almacenar en caché, incluido el contenido HTML procesado además de todos los artefactos del nivel de almacenamiento en caché conservador. Produce el mejor rendimiento, pero también consume más memoria para almacenar artefactos en caché. Una estrategia agresiva de almacenamiento en caché significa que obtendrá un rendimiento de tiempo constante al procesar un formulario a medida que el contenido procesado se almacene en caché.

Es posible que la configuración de caché predeterminada para AEM Forms no sea lo suficientemente buena como para lograr un rendimiento óptimo. Por lo tanto, se recomienda utilizar la siguiente configuración:

* **Estrategia** de caché: Agresivo
* **Tamaño de caché**  (en términos del número de formularios): Como requerido
* **Tamaño** máximo del objeto: Como requerido

![Configuraciones de Forms móvil](assets/snap.png)

>[!NOTE]
>
>Si utiliza AEM Dispatcher para almacenar en caché los formularios adaptables, también almacena en caché el formulario adaptable que contiene formularios con datos precargados. Si estos formularios se proporcionan desde AEM caché de Dispatcher, puede dar lugar a que se proporcionen datos precargados o antiguos a los usuarios. Por lo tanto, utilice AEM Dispatcher para almacenar en caché formularios adaptables que no utilicen datos precargados. Además, una caché de Dispatcher no invalida automáticamente los fragmentos en caché. Por lo tanto, no lo utilice para almacenar en caché los fragmentos de formulario. Para estos formularios y fragmentos, utilice [la caché de formularios adaptables](/help/forms/using/configure-adaptive-forms-cache.md).

## Parámetros de JVM {#jvm-parameters}

Para obtener un rendimiento óptimo, se recomienda utilizar los siguientes argumentos de JVM `init` para configurar los `Java heap` y `PermGen`.

```java
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>La configuración recomendada es para JDK de Windows 2008 R2 8 Core y Oracle HotSpot 1.7 (64 bits) y debe ampliarse o reducirse según la configuración del sistema.

## Uso de un servidor web {#using-a-web-server}

Los formularios adaptables y los formularios HTML5 se representan en formato HTML5. El resultado resultante podría ser grande en función de factores como el tamaño del formulario y las imágenes del formulario. Para optimizar la transferencia de datos, el método recomendado es comprimir la respuesta HTML mediante el servidor web desde el que se suministra la solicitud. Este método reduce el tamaño de respuesta, el tráfico de red y el tiempo necesario para transmitir datos entre equipos cliente y servidor.

Por ejemplo, realice los siguientes pasos para habilitar la compresión en Apache Web Server 2.0 de 32 bits con JBoss:

>[!NOTE]
>
>Las siguientes instrucciones no se aplican a ningún servidor que no sea Apache Web Server 2.0 de 32 bits. Para ver los pasos específicos de cualquier otro servidor, consulte la documentación del producto correspondiente.

Los siguientes pasos muestran los cambios necesarios para habilitar la compresión con Apache Web Server

**Obtenga el software de servidor web Apache aplicable a su sistema operativo**

* Windows: descargue el servidor web Apache desde el sitio del proyecto Apache HTTP Server.
* Solaris de 64 bits: descargue el servidor web Apache desde el sitio web de Sunfreeware para Solaris.
* Linux: el servidor web Apache está preinstalado en un sistema Linux.

Apache puede comunicarse con CRX usando el protocolo HTTP. Las configuraciones están destinadas a la optimización mediante HTTP.

1. Descomente las siguientes configuraciones de módulo en el archivo `APACHE_HOME/conf/httpd.conf`.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Para Linux, el `APACHE_HOME` predeterminado es `/etc/httpd/`.

1. Configure el proxy en el puerto 4502 de crx.

   Añada la siguiente configuración en el archivo de configuración `APACHE_HOME/conf/httpd.conf`.

   ```java
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Active Compresión. Añada la siguiente configuración en el archivo de configuración `APACHE_HOME/conf/httpd.conf`.

   **Para formularios HTML5**

   ```java
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Para formularios adaptables**

   ```java
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Para acceder al servidor crx, utilice `https://[server]:80`, donde `server` es el nombre del servidor en el que se está ejecutando el servidor Apache.

## Uso de un antivirus en un servidor que ejecuta AEM Forms {#using-an-antivirus-on-server-running-aem-forms}

Puede experimentar un rendimiento lento en los servidores que ejecutan un software antivirus. Un software siempre en antivirus (análisis en tiempo real) analiza todos los archivos de un sistema. Puede ralentizar el servidor y el rendimiento de AEM Forms se ve afectado.

Para mejorar el rendimiento, puede dirigir el software antivirus para que excluya los siguientes archivos y carpetas de AEM Forms del análisis siempre activo (en tiempo real):

* AEM de instalación. Si no es posible excluir el directorio completo, excluya lo siguiente:

   * [AEM directorio de instalación]\crx-repository\temp
   * [AEM directorio de instalación]\crx-repository\repository
   * [AEM directorio de instalación]\crx-repository\launchpad

* Directorio temporal del servidor de aplicaciones. La ubicación predeterminada es:

   * (Jboss) [AEM directorio de instalación]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Solo AEM Forms en JEE)** Directorio Global Document Storage (GDS). La ubicación predeterminada es:

   * (JBoss) `[appserver root]/server/[server]/svcnative/DocumentStorage`
   * (WebLogic) `[appserverdomain]/[server]/adobe/LiveCycleServer/DocumentStorage`
   * (WebSphere) `[appserver root]/installedApps/adobe/[server]/DocumentStorage`

* **(Solo AEM Forms en JEE)** Registros del servidor de AEM Forms y directorio temporal. La ubicación predeterminada es:

   * Registros de servidor: `[AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs`
   * Directorio temporal: [Directorio de instalación de AEM Forms]\temp

>[!NOTE]
>
>* Si utiliza una ubicación diferente para GDS y un directorio temporal, abra AdminUI en `https://[server]:[port]/adminui)`, vaya a **Inicio > Configuración > Configuración del sistema principal > Configuraciones principales** para confirmar la ubicación en uso.

* Si el servidor AEM Forms funciona lentamente incluso después de excluir los directorios sugeridos, excluya también el archivo ejecutable Java (java.exe).


