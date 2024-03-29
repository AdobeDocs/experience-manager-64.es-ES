---
title: Optimizar formularios HTML5
seo-title: Optimizing HTML5 forms
description: Puede optimizar el tamaño de salida de los formularios HTML5.
seo-description: You can optimize the output size of the HTML5 forms.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
exl-id: 8d2b5294-9763-4348-b927-706ebac90b95
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 86%

---

# Optimizar formularios HTML5 {#optimizing-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los formularios HTML5 procesan los formularios en formato HTML5. Dependiendo de factores como el tamaño del formulario y las imágenes que este contiene, la salida resultante puede tener un gran tamaño. El método recomendado para optimizar la transferencia de datos es comprimir la respuesta del HTML mediante el servidor web desde el que se suministra la solicitud. Este método reduce el tamaño de la respuesta, el tráfico de red y el tiempo necesario para transmitir los datos entre los equipos cliente y servidor.

Este artículo describe los pasos necesarios para habilitar la compresión en Apache Web Server 2.0 de 32 bits con JBoss.

*Nota: Las siguientes instrucciones no se aplican a servidores que no sean Apache Web Server 2.0 de 32 bits.*

Obtenga el software del servidor web Apache aplicable a su sistema operativo:

* En Windows, descargue el servidor web de Apache del sitio del proyecto Apache HTTP Server.
* En Solaris de 64 bits, descargue el servidor web Apache desde el sitio web de Sunfreeware para Solaris.
* En Linux, el servidor web Apache está preinstalado en el sistema.

Apache puede comunicarse con JBoss mediante HTTP o el protocolo AJP.

1. Elimine los comentarios de las siguientes configuraciones de módulo en el archivo *APACHE_HOME/conf/httpd.conf*.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >En Linux, el directorio APACHE_HOME predeterminado es /etc/httpd/.

1. Configure el proxy en el puerto 8080 de JBoss.

   Agregue la siguiente configuración al archivo de configuración *APACHE_HOME/conf/httpd.conf*.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Cuando utiliza un proxy, se requieren los siguientes cambios de configuración:
   > 
   >* Acceso: *https://&lt;server>:&lt;port>/system/console/configMgr*.
   * Edite la configuración del Filtro de referente de Apache Sling.
   * En Permitir hosts, añada la entrada para el servidor proxy.


1. Habilite la Compresión.

   Agregue la siguiente configuración al archivo de configuración *APACHE_HOME/conf/httpd.conf*.

   ```java
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Para acceder al servidor de AEM, utilice https://[Apache_server]:80.
